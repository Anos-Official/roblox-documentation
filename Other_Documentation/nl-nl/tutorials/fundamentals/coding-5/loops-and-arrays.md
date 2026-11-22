<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-5/loops-and-arrays -->

Lussen en arrays | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Woordenboeken en arrays](/docs/nl-nl/tutorials/fundamentals/coding-5/landing)

# Lussen en arrays

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Arrays  kunnen worden gecombineerd met lussen, zoals while  en for , om dezelfde code voor elke geïndexeerde waarde te herhalen. Bijvoorbeeld, het teleporteren van elke speler in een array naar een nieuwe plek of het laten vlammen van een array van onderdelen.

Om te verkennen hoe je door arrays kunt lussen, maak je een verdwijnende brugpad waar onderdelen in een array worden geplaatst en vervolgens één voor één laten verdwijnen.

## [Loop door een array](#loop-door-een-array)[](#loop-door-een-array)

Voor het project, vind of maak een set van drie onderdelen die moeten verdwijnen. De onderdelen moeten allemaal verankerd zijn.

1.

Maak drie onderdelen. Noem de onderdelen in de volgorde waarin ze moeten verdwijnen, Deel1, Deel2, Deel3.

2.

In ServerScriptService, voeg een nieuw script in en maak een array om de onderdelen op te slaan.

```

local pathArray = {

}

```

3.

Typ op een enkele regel elk van de onderdelen in de volgorde waarin ze moeten verdwijnen. Een nieuwe regel voor elke waarde maakt het gemakkelijker te lezen.

```

local pathArray = {

	workspace.Deel1,

	workspace.Deel2,

	workspace.Deel3,

}

```

### [Gebruik een for-lus met een array](#gebruik-een-for-lus-met-een-array)[](#gebruik-een-for-lus-met-een-array)

Gebruik een for-lus om door de array te gaan en te controleren hoe snel de onderdelen moeten verdwijnen in de volgorde waarin de onderdelen zijn geïndexeerd binnen de array.

1.

Om te controleren hoe vaak een onderdeel in seconden verdwijnt, maak je een variabele genaamd VANISH_RATE . Voor testen is het het beste om het op een klein getal te houden.

```

local VANISH_RATE = 1.5

local pathArray = {

	workspace.Deel1,

	workspace.Deel2,

	workspace.Deel3

}

```

Constanten  zijn variabelen die niet door andere code in het script mogen worden gewijzigd. Ze moeten waarschijnlijk worden aangepast en worden bovenaan het script in ALL_CAPS  geplaatst om ze gemakkelijk te herkennen.

2.

Maak een for-lus met het volgende: Start:  partIndex = 1 , de index van de eerste waarde in de array. Einde:  #pathArray , de grootte van die array.

```

for partIndex = 1, #pathArray  do

end

```

3.

Om een vertraging toe te voegen voordat een onderdeel verdwijnt, voeg je in de lus een [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  toe met VANISH_RATE .

```

for partIndex = 1, #pathArray  do

   task.wait(VANISH_RATE)

end

```

4.

Om een onderdeel te laten verdwijnen, maak je een nieuwe variabele genaamd whichPart  en stel je deze gelijk aan pathArray[partIndex] . Stel vervolgens om dat onderdeel te laten verdwijnen, de eigenschap CanCollide  in op false en Transparency  op 1.

```

for partIndex = 1, #pathArray  do

   task.wait(VANISH_RATE)

   local whichPart = pathArray[partIndex]

   whichPart.CanCollide = false

   whichPart.Transparency = 1

end

```

5.

Controleer of de onderdelen van het pad in de loop van de tijd verdwijnen.

### [Probleemoplossing tips](#probleemoplossing-tips)[](#probleemoplossing-tips)

Als de brug niet verdwijnt, controleer dan de mogelijke problemen hieronder:

Probleem:  Onderdelen verdwijnen te snel of zijn allemaal aan het begin verdwenen.

-

Afhankelijk van hoe snel je karakter in het spel laadt, kunnen de eerste onderdelen al onzichtbaar zijn. Om dit aan te pakken, voeg je een kleine wachtperiode toe, zoals task.wait(2) , aan het begin van het script.

### [Code de tweede lus](#code-de-tweede-lus)[](#code-de-tweede-lus)

Op dit moment verdwijnen de onderdelen voor altijd. Om ze weer te laten verschijnen, maak je een tweede for-lus die door elk onderdeel gaat en elk stuk onmiddellijk weer begaanbaar maakt.

1.

Voeg na de eerste lus een [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  toe om een korte vertraging te creëren voordat het pad weer verschijnt.

```

for partIndex = 1, #pathArray  do

	task.wait(VANISH_RATE)

	local whichPart = pathArray[partIndex]

	whichPart.CanCollide = false

	whichPart.Transparency = 1

end

task.wait(1)

```

2.

Op je eigen , probeer een tweede for-lus te coderen die het pad weer bruikbaar maakt door de eigenschap CanCollide van elk onderdeel op true en Transparency op 0 te zetten. Controleer je werk tegen de onderstaande code wanneer je klaar bent.

```

-- Reset het pad door alle onderdelen weer begaanbaar te maken

for partIndex = 1, #pathArray do

   local whichPart = pathArray[partIndex]

   whichPart.CanCollide = true

   whichPart.Transparency = 0

end

```

Onverankerde onderdelen zullen door de basisplaat vallen wanneer CanCollide false is. Als de onderdelen niet weer verschijnen, en er zijn geen Output-fouten, veranker de onderdelen en test opnieuw.

3.

Test het project om te bevestigen dat zodra alle onderdelen verdwijnen, ze weer terugkomen.

## [Herhaal met een while-lus](#herhaal-met-een-while-lus)[](#herhaal-met-een-while-lus)

De onderdelen verdwijnen en verschijnen weer, maar slechts één keer. Om de code te laten blijven herhalen, nest je alle code binnen een while-lus.

1.

Maak onderaan het script een nieuwe while true do-lus. Verplaats vervolgens beide  for-lussen in de while-lus.

```

while true do

   -- Laat een onderdeel in volgorde uit de array verdwijnen

	for partIndex = 1, #pathArray  do

		task.wait(VANISH_RATE)

		local whichPart = pathArray[partIndex]

		whichPart.CanCollide = false

		whichPart.Transparency = 1

	end

	-- Wacht een seconde voordat je het pad weer laat verschijnen

	task.wait(1)

	-- Reset het pad door alle onderdelen weer begaanbaar te maken

	for partIndex = 1, #pathArray do

		local whichPart = pathArray[partIndex]

		whichPart.CanCollide = true

		whichPart.Transparency = 0

	end

end

```

2.

Controleer of zodra alle onderdelen verdwijnen, ze weer verschijnen.

Een voltooide versie van het project kan worden gedownload.

Voltooid script

```

local VANISH_RATE = 1.0

local pathArray = {

	workspace.Deel1,

	workspace.Deel2,

	workspace.Deel3,

}

while true do

	-- Laat een onderdeel in volgorde uit de array verdwijnen

	for partIndex = 1, #pathArray  do

		task.wait(VANISH_RATE)

		local whichPart = pathArray[partIndex]

		whichPart.CanCollide = false

		whichPart.Transparency = 1

	end

	-- Wacht een seconde voordat je het pad weer laat verschijnen

	task.wait(1.0)

	-- Reset het pad door alle onderdelen weer begaanbaar te maken

	for partIndex = 1, #pathArray do

		local whichPart = pathArray[partIndex]

		whichPart.CanCollide = true

		whichPart.Transparency = 0

	end

end

```

## [Arrays en ipairs()](#arrays-en-ipairs)[](#arrays-en-ipairs)

ipairs()  wordt gebruikt met arrays . De "i" in ipairs()  staat voor "index." ipairs() kan worden gebruikt om snel een bewerking op veel objecten te herhalen, zoals bijvoorbeeld een map vol onderdelen.

Dit zal worden gedemonstreerd door snel deeltjes toe te voegen aan een hele map van onderdelen.

1.

Maak in Workspace een map genaamd PartsFolder. Voeg zoveel onderdelen toe als je wilt.

2.

In ServerScriptService, maak een nieuw script en verwijs naar de map.

3.

Gebruik GetChildren() om automatisch een array te krijgen met een lijst van alle objecten in de map.

```

local partsFolder = workspace.PartsFolder

-- Krijgt een array met een lijst van de onderdelen in PartsFolder

local partsArray = partsFolder:GetChildren()

```

4.

Gebruik in ipairs(ArrayToUse)  met de for-lus om door partsArray te gaan en deeltjes toe te voegen.

Voltooid script

```

-- Krijgt een array met een lijst van de onderdelen in PartsFolder

local partsArray = partsFolder:GetChildren()

-- Voegt deeltjes toe aan elk onderdeel in de array

for index, part in ipairs(partsArray) do

	local particles = Instance.new("ParticleEmitter")

	particles.Parent = part

end

```

Speel en kijk hoe de deeltjes van elk onderdeel in de map omhoog zweven.

## [Samenvatting](#samenvatting)[](#samenvatting)

Lussen kunnen worden gecombineerd met arrays om snel met een willekeurig aantal waarden te werken. Als je exacte controle wilt hebben over wat er met een paar onderdelen gebeurt en in welke volgorde, moet een array hard-coded worden met specifieke waarden.

Om met veel onderdelen te werken waar de volgorde er niet toe doet, kan GetChildren() een array van de kinderen van een object creëren. Door gebruik te maken van ipairs() , kan de lijst snel worden doorlopen zonder de grootte van de array te kennen.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-5/make-changes-to-arrays)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-5/intro-to-arrays)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
