<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/fading-trap -->

Vervagende valstrik | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Scripting
6. /
7. Basisspel

# Vervagende valstrik

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In [Dodelijke Lava](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava)  heb je geleerd hoe je code kunt activeren op basis van gebruikersgedrag. Deze tutorial laat je zien hoe je een platform maakt dat vervaagt wanneer een gebruiker erop staat.

## [Opzetten](#opzetten)[](#opzetten)

Als je [Dodelijke Lava](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava)  hebt gevolgd, kun je je vervagende platform boven de lavavloer plaatsen waar gebruikers niet overheen kunnen springen.

1.

Voeg een onderdeel toe en verplaats het op zijn plaats in je wereld. Noem het VervagendPlatform .

2.

Verander de grootte zodat een gebruiker erop kan springen.

3.

Zorg ervoor dat het Verankerd  is.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/fading-trap/partInPlace.jpg)

4.

Voeg een Script  toe aan het onderdeel, hernoem het naar VervagenBijAanraking , en verwijder de standaardcode.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/fading-trap/scriptInPlace.png)

5.

Maak een variabele voor het platform en een lege functie die is verbonden met het Aangeraakt -evenement van het platform.

```

local platform = script.Parent

local function vervagen()

end

platform.Touched:Connect(vervagen)

```

## [Vervag het platform](#vervag-het-platform)[](#vervag-het-platform)

Als het platform in één keer zou verdwijnen, zou dat helemaal niet leuk zijn, omdat gebruikers het onmogelijk zouden vinden om de kloof over te steken. In plaats daarvan zou het platform moeten vervagen  voordat gebruikers erdoor vallen, zodat ze de kans krijgen om eraf te springen.

Je zou de Transparantie -eigenschap kunnen veranderen en een zeer korte tijd herhaaldelijk kunnen wachten om dit effect te krijgen, maar een geleidelijke vervaging zou minstens 10 veranderingen tussen 0 en 1 vereisen. Dat zijn 20 regels zeer repetitieve code.

Dit kan veel effectiever worden bereikt met een for -lus die code een specifiek aantal keren herhaalt. Elke lus van de code staat bekend als een iteratie . Een for-lus wordt gedefinieerd met drie dingen, gescheiden door komma's:

![](https://prod.docsiteassets.roblox.com/assets/tutorials/fading-trap/forLoop.jpg)

-

Controlevariabele  - De variabele die is gemaakt en gebruikt om de lussen te tellen. In dit voorbeeld is het count  en de startwaarde is 1.

-

Eindwaarde  - De waarde die het moet bereiken om de lus te stoppen. In dit voorbeeld is het 10.

-

Stapverhoging

OPTIONEEL

 - Bepaalt wat er aan de controlevariabele moet worden toegevoegd bij elke lus. Als deze wordt weggelaten, is de standaardwaarde 1, dus in dit voorbeeld is het niet nodig.

In VervagenBijAanraking :

1.

Maak in de functie een for -lus die begint bij 1  en 10  keer herhaalt.

2.

Stel binnen de for-lus de Transparantie -eigenschap in op de controlevariabele gedeeld door 10 .

3.

Roep de functie [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  aan met een tijd van 0.1 .

```

local platform = script.Parent

local function vervagen()

	for count = 1, 10 do

		platform.Transparantie = count / 10

		task.wait(0.1)

	end

end

platform.Touched:Connect(vervagen)

```

Wanneer de lus draait, neemt count met 1 toe bij elke iteratie. Dit betekent dat de Transparantie  van het platform met 0.1 toeneemt elke 0.1 seconden, en na 1 seconde volledig transparant is.

## [Herappear](#herappear)[](#herappear)

Nadat het platform is verdwenen, zouden gebruikers erdoor moeten vallen. Het platform zou ook een paar seconden moeten terugkomen nadat het is vervaagd - anders zouden gebruikers nooit de kans krijgen om de sprong opnieuw te proberen als ze falen. De CanCollide-eigenschap bepaalt of gebruikers door een onderdeel kunnen vallen.

1.

Stel de CanCollide -eigenschap van het platform in op false  na de for-lus.

2.

Wacht een paar seconden met de functie [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait) .

3.

Stel de CanCollide -eigenschap weer in op true .

4.

Stel de Transparantie -eigenschap weer in op 0 .

```

local platform = script.Parent

local function vervagen()

   for count = 1, 10 do

      platform.Transparantie = count / 10

      task.wait(0.1)

   end

   platform.CanCollide = false

   task.wait(3)

   platform.CanCollide = true

   platform.Transparantie = 0

end

platform.Touched:Connect(vervagen)

```

## [Debounce-variabele](#debounce-variabele)[](#debounce-variabele)

In [Dodelijke Lava](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava)  heb je geleerd dat het Aangeraakt -evenement elke keer wordt uitgevoerd wanneer een lichaamsdeel van een gebruiker in contact komt met het onderdeel. Dit gedrag veroorzaakt problemen wanneer een gebruiker over het vervagende platform rent: de functie wordt meerdere keren uitgevoerd, waardoor de lus elke keer opnieuw wordt ingesteld.

Om ervoor te zorgen dat de code goed werkt, moet de functie slechts één keer worden uitgevoerd wanneer de gebruiker het platform voor de eerste keer aanraakt. Zorgen dat een actie slechts één keer wordt geactiveerd wanneer deze anders meerdere keren zou worden geactiveerd, staat bekend als debouncing .

Om een functie te debouncen, kan een [boolean](/docs/nl-nl/luau/booleans)  variabele worden gebruikt om bij te houden wanneer het platform al is aangeraakt. Booleans kunnen alleen waar  en onwaar  waarden bevatten. Maak een variabele genaamd isTouched  en stel deze in op false .

```

local platform = script.Parent

local isTouched = false

local function vervagen()

	for count = 1, 10 do

		platform.Transparantie = count / 10

		task.wait(0.1)

	end

	platform.CanCollide = false

	task.wait(3)

	platform.CanCollide = true

	platform.Transparantie = 0

end

platform.Touched:Connect(vervagen)

```

## [Controleer de variabele](#controleer-de-variabele)[](#controleer-de-variabele)

Een if-statement kan worden gebruikt om de code in de vervagingsfunctie alleen uit te voeren als de isTouched  debouncing-variabele false is. Wikkel de body van de vervagingsfunctie in een if -statement met de voorwaarde not isTouched .

```

local platform = script.Parent

local isTouched = false

local function vervagen()

	if not isTouched then

		for count = 1, 10 do

            platform.Transparantie = count / 10

            task.wait(0.1)

	    end

		platform.CanCollide = false

		task.wait(3)

		platform.CanCollide = true

		platform.Transparantie = 0

	end

end

platform.Touched:Connect(vervagen)

```

De Luau not  operator keert de waarde om van wat er ook maar volgt. In voorwaardelijke termen betekent dit dat de eerste if-statement zich gedraagt als de statements die volgen.

```

if not isTouched then

end

if isTouched == false then

end

if isTouched == nil then

end

```

## [Toggle de debounce](#toggle-de-debounce)[](#toggle-de-debounce)

Momenteel zal de code in de vervagen  functie altijd worden uitgevoerd omdat isTouched  false is en not isTouched  waar is. Om de debounce-routine te voltooien, moet je de waarde van de variabele op twee plaatsen omzetten.

1.

Stel isTouched  in op true  binnen de if -statement, voordat het platform begint te vervagen.

2.

Zet het terug naar false  zodra het platform weer is verschenen.

```

local function vervagen()

  if not isTouched then

    isTouched = true

    for count = 1, 10 do

      platform.Transparantie = count / 10

      task.wait(0.1)

    end

    platform.CanCollide = false

    task.wait(3)

    platform.CanCollide = true

    platform.Transparantie = 0

    isTouched = false

  end

end

platform.Touched:Connect(vervagen)

```

En dat is het! Test nu je code, en je zou moeten ontdekken dat het platform vervaagt wanneer de gebruiker erop springt en een paar seconden later weer terugkomt.

Je kunt dit platform dupliceren over een bredere kloof om een uitdagend obstakel te creëren en de snelheid waarmee ze vervagen veranderen om de moeilijkheidsgraad in balans te brengen.

## [Eindcode](#eindcode)[](#eindcode)

```

local platform = script.Parent

local isTouched = false

local function vervagen()

	if not isTouched then

		isTouched = true

		for count = 1, 10 do

		    platform.Transparantie = count / 10

		    task.wait(0.1)

	    end

		platform.CanCollide = false

		task.wait(3)

		platform.CanCollide = true

		platform.Transparantie = 0

		isTouched = false

	end

end

platform.Touched:Connect(vervagen)

```

[Volgende](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/score-points)[Vorige](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
