<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava -->

Dodelijke lava | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Scripting
6. /
7. Basisspel

# Dodelijke lava

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In [Inleiding tot scripting](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/intro-to-scripting)  heb je geleerd hoe je veranderingen in een spel in een loop over tijd kunt aanbrengen. Wat als je veranderingen wilt aanbrengen op basis van gebruikersgedrag? In deze tutorial leer je hoe je een dodelijke lavavloer maakt die gebruikers doodt wanneer ze erop staan.

## [Opzetten](#opzetten)[](#opzetten)

Je hebt een plek in je wereld nodig om de dodelijke lava te plaatsen. Als je de [Inleiding tot scripting](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/intro-to-scripting)  cursus hebt gevolgd, zou de lavavloer mooi passen in de ruimte die wordt bedekt door de verdwijnende platforms.

1.

Voeg een Part  toe en verplaats deze naar de juiste plek in je wereld. Noem het LavaFloor .

2.

Verander de grootte zodat het de vloer van de omringende ruimte bedekt.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/deadly-lava/partInserted.jpg)

3.

Laat de vloer meer op lava lijken door de Material  eigenschap in te stellen op Neon  en de Color  op een oranje tint.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/deadly-lava/propertiesSet.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/deadly-lava/lavaProperties.jpg)

4.

Voeg een Script  toe aan het LavaFloor  onderdeel en hernoem het naar Kill .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/deadly-lava/scriptExplorer.png)

5.

Verwijder de standaardcode en maak een variabele voor de lava.

```

local lava = script.Parent

```

## [Verbinden met een gebeurtenis](#verbinden-met-een-gebeurtenis)[](#verbinden-met-een-gebeurtenis)

Gebruik een gebeurtenis  om te detecteren wanneer een gebruiker de lava aanraakt. Elk onderdeel heeft een Touched  gebeurtenis die wordt geactiveerd wanneer iets het aanraakt. Je kunt verbinden  met deze gebeurtenis om een functie uit te voeren wanneer deze wordt geactiveerd.

1.

Declareer een nieuwe functie genaamd kill .

2.

Toegang tot de Touched  gebeurtenis op het lava-object met een punt, net als bij een eigenschap: lava.Touched .

3.

Roep de Connect  functie aan op de Touched  gebeurtenis, waarbij je kill()  doorgeeft als de functie die moet worden aangeroepen wanneer het onderdeel wordt aangeraakt.

```

local lava = script.Parent

local function kill()

end

lava.Touched:Connect(kill)

```

Elke code die je in de kill  functie schrijft, zal nu worden uitgevoerd telkens wanneer iets de lavavloer aanraakt. Merk op dat een dubbele punt  wordt gebruikt voor de Connect  functie, niet  een punt - maak je op dit moment geen zorgen over waarom, onthoud gewoon het verschil.

## [Verkrijg het aangeraakte onderdeel](#verkrijg-het-aangeraakte-onderdeel)[](#verkrijg-het-aangeraakte-onderdeel)

Om de gebruiker te doden, heeft de functie een object nodig dat aan die gebruiker is gekoppeld. De Touched  gebeurtenis van een onderdeel kan het "andere onderdeel" dat het aanraakte bieden — maar alleen als je het opvraagt door het een parameter  van de functie te maken.

Parameters zijn definities van wat een functie verwacht te ontvangen wanneer deze wordt aangeroepen. Een parameter kan in een functie worden gebruikt zoals elke andere variabele. Je kunt informatie aan een parameter doorgeven door deze in de haakjes op te nemen wanneer een functie wordt aangeroepen. Parameters worden gedefinieerd in de haakjes op de eerste regel van een functie. Maak een parameter  genaamd otherPart  voor de kill  functie.

```

local lava = script.Parent

local function kill(otherPart)

end

lava.Touched:Connect(kill)

```

Wanneer de kill  functie wordt aangeroepen, zal de otherPart  parameter het onderdeel vertegenwoordigen dat de lavavloer heeft aangeraakt, en de code die je in de functie schrijft, zal het kunnen gebruiken.

## [Character en humanoïde](#character-en-humanoïde)[](#character-en-humanoïde)

Wanneer een gebruiker de lava aanraakt, kan Roblox het specifieke lichaamsdeel van de gebruiker detecteren dat het aanraakte, zoals het linkerbeen of de rechtervoet. Dit onderdeel bevindt zich in het Character  model van de gebruiker, dat alle objecten bevat die de avatar van de gebruiker in het spel vormen, inclusief:

-

De individuele lichaamsdelen van de gebruiker zoals het hoofd, ledematen en torso.

-

Kleding en accessoires die door de gebruiker worden gedragen.

-

De [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid) , een speciaal object dat veel eigenschappen bevat die verband houden met de gebruiker, inclusief de gezondheid van de gebruiker.

-

De HumanoidRootPart die de beweging van de gebruiker controleert.

Zoals eerder opgemerkt, is elk lichaamsdeel dat de lava aanraakt een onderdeel van het Character model, dus je kunt een referentie naar dat karakter krijgen met otherPart.Parent . Maak een variabele om de ouder van het onderdeel dat de lavavloer heeft aangeraakt op te slaan.

```

local lava = script.Parent

local function kill(otherPart)

  local partParent = otherPart.Parent

end

lava.Touched:Connect(kill)

```

Vanuit het karaktermodel moet je het Humanoid-object verkrijgen om de gebruiker te doden. Je kunt dit doen met de FindFirstChild()  functie — geef gewoon de naam door van het ding dat je zoekt en het biedt het eerste overeenkomende kind dat het in dat object vindt. Roep FindFirstChild()  aan op de partParent  variabele met "Humanoid"  als het kind dat je wilt vinden, en sla het resultaat op in een nieuwe variabele genaamd humanoid .

```

local lava = script.Parent

local function kill(otherPart)

  local partParent = otherPart.Parent

  local humanoid = partParent:FindFirstChild("Humanoid")

end

lava.Touched:Connect(kill)

```

## [Controleer de humanoïde](#controleer-de-humanoïde)[](#controleer-de-humanoïde)

Je kunt eenvoudig controleren of de Humanoid is gevonden met een if -statement. De code in een if-statement wordt alleen uitgevoerd als de voorwaarde die in de eerste regel is gedefinieerd, waar is.

Er zijn verschillende [operatoren](/docs/nl-nl/luau/operators)  die kunnen worden gebruikt om complexere voorwaarden op te bouwen die je in toekomstige cursussen zult tegenkomen - voor nu, zet gewoon de humanoid  variabele daar. Maak een if -statement met humanoid  als de voorwaarde.

```

local lava = script.Parent

local function kill(otherPart)

  local partParent = otherPart.Parent

  local humanoid = partParent:FindFirstChild("Humanoid")

  if humanoid then

  end

end

lava.Touched:Connect(kill)

```

In Luau wordt elke waarde anders dan false of nil  (een lege waarde) geëvalueerd als waar in een voorwaardelijke verklaring, dus in dit geval kun je humanoid  direct als de voorwaarde gebruiken.

## [Stel de gezondheid van het karakter in](#stel-de-gezondheid-van-het-karakter-in)[](#stel-de-gezondheid-van-het-karakter-in)

Nu de [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  is gecontroleerd, kunnen de eigenschappen worden gewijzigd. Als je de Health  eigenschap op 0  instelt, sterft het bijbehorende Character. In de body van de if-statement, stel de Health  eigenschap van humanoid in op 0.

```

local function kill(otherPart)

    local partParent = otherPart.Parent

    local humanoid = partParent:FindFirstChild("Humanoid")

    if humanoid then

        humanoid.Health = 0

    end

end

lava.Touched:Connect(kill)

```

Met dat is je lavavloer compleet! Test je spel en je zou moeten ontdekken dat je dodelijke lava gebruikers succesvol doodt bij contact. Probeer je lava te gebruiken als een extra uitdaging in een obby, of als een grens voor een wereld.

## [Eindcode](#eindcode)[](#eindcode)

```

local lava = script.Parent

local function kill(otherPart)

    local partParent = otherPart.Parent

    local humanoid = partParent:FindFirstChild("Humanoid")

    if humanoid then

        humanoid.Health = 0

    end

end

lava.Touched:Connect(kill)

```

[Volgende](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/fading-trap)[Vorige](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/intro-to-scripting)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
