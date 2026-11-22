<!-- Source: https://create.roblox.com/docs/nl-nl/scripting -->

Scripting | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)

# Scripting

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Scripts zijn platte tekstbestanden waarmee je aangepaste, dynamische gedragingen aan je games kunt toevoegen. Je kunt scripts gebruiken om in-game evenementen te activeren, te reageren op spelersinvoer, spelersgegevens op te slaan, ranglijsten te maken, vijanden te spawnen, NPC-gedrag te controleren en nog veel meer.

Deze sectie is voor makers met enige programmeerervaring die de specifics van scripting in Roblox willen weten.

Als je nog nooit code hebt geschreven en een introductie tot programmeren wilt, zie dan [Coding fundamentals](/docs/nl-nl/tutorials/fundamentals/coding-1/coding-fundamentals) , dat concepten behandelt zoals variabelen, functies, conditionals, lussen en arrays. Voor een meer geleide, stapsgewijze aanpak, zie de [Basic gameplay](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/intro-to-scripting)  tutorial.

## [Luau](#luau)[](#luau)

Roblox-scripts gebruiken de [Luau](https://luau.org)  programmeertaal, die is afgeleid van [Lua 5.1](https://www.lua.org/manual/5.1/) .

-

In vergelijking met Lua 5.1 voegt Luau prestatieverbeteringen en veel nuttige functies toe, waaronder een optioneel type-systeem, stringinterpolatie en gegeneraliseerde iteratie voor tabellen.

-

Alle geldige Lua 5.1-code is geldige Luau-code, maar het omgekeerde is niet waar.

De meeste boeken en online bronnen voor Lua zijn nog steeds breed toepasbaar op Luau. Voor een gedetailleerde samenvatting van de verschillen, zie [Compatibility](https://luau.org/compatibility)  in de Luau-documentatie. Voor taalsyntaxis, zie de [Luau reference](/docs/nl-nl/luau) .

### [Luau basisprincipes](#luau-basisprincipes)[](#luau-basisprincipes)

Luau is geleidelijk getypeerd, dus je hoeft geen type op te geven wanneer je een variabele maakt. Je kunt [type()](/docs/nl-nl/reference/engine/globals/LuaGlobals#type)  gebruiken om het objecttype te controleren:

```

logMessage = "De gebruiker heeft meer dan 10 items!"

print(logMessage) --> De gebruiker heeft meer dan 10 items!

print(type(logMessage)) --> string

```

Luau heeft globale en lokale [scopes](/docs/nl-nl/luau/scope) , maar het is bijna altijd beter om variabelen en functies lokaal te declareren met het local  sleutelwoord:

```

local logMessage = "De gebruiker heeft meer dan 10 items!"

local function printMessage()

	print(logMessage)

end

printMessage() --> De gebruiker heeft meer dan 10 items!

```

Luau gebruikt nil  om niet-bestaande of niets te vertegenwoordigen, wat als false  evalueert in conditionele uitspraken:

```

local messageToUser

print(messageToUser) --> nil

print(type(messageToUser)) --> nil

if messageToUser then

	-- uitspraak evalueert naar false

end

```

Zoals je misschien hebt opgemerkt, begint --  een eenregelige opmerking. --[[]]  creëert een blokopmerking:

```

--[[

    Zet de kosmische maanstraal onmiddellijk uit.

    Moet alleen binnen 15 minuten voor middernacht Mountain Standard

    Tijd worden aangeroepen om schade aan de kosmische maanstraal te voorkomen.

]]

local function stopCosmicMoonRay()

	-- voeg dit later toe, het kan belangrijk blijken te zijn

end

```

[Tabellen](/docs/nl-nl/luau/tables)  zijn de algemene term voor arrays en woordenboeken. Arrays zijn één-gebaseerd in plaats van nul-gebaseerd, dus het eerste item is [1] . Je declareert arrays en woordenboeken met een enkele set accolades:

```

local myArray = {"chips", "sprankelend water", "salsa"}

local myDictionary = {

	snack = "chips",

	drank = "sprankelend water",

	dip = "salsa"

}

print(myArray[1]) --> chips

print(myDictionary.dip) --> salsa

```

Je kunt over tabellen itereren met for -lussen met de [ipairs()](/docs/nl-nl/reference/engine/globals/LuaGlobals#ipairs)  functie voor arrays en de [pairs()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pairs)  functie voor woordenboeken, maar Luau laat je ook deze functies weglaten voor een schonere syntaxis:

```

for index, value in ipairs(myArray) do -- standaard Lua

	print(index, value)

end

for key, value in pairs(myDictionary) do -- standaard Lua

	print(key, value)

end

for key, value in myDictionary do -- Luau gegeneraliseerde iteratie

	print(key, value)

end

```

## [Je eerste script](#je-eerste-script)[](#je-eerste-script)

1.

In Roblox Studio, beweeg de muis over ServerScriptService  in het [Explorer](/docs/nl-nl/studio/explorer)  venster en klik op + .

2.

Selecteer Script  om een nieuw script toe te voegen.

3.

Klik met de rechtermuisknop op het script en hernoem het naar HelloScript .

4.

Dubbelklik op het script om het te openen in de [Script Editor](/docs/nl-nl/studio/script-editor) .

5.

Voeg de volgende code toe aan het bestand:

```

local helloArray = {"h", "e", "l", "l", "o"}

local worldArray = {"w", "o", "r", "l", "d"}

for index, value in helloArray do

	print(value)

end

print(table.concat(worldArray))

```

6.

Zorg ervoor dat het [Output](/docs/nl-nl/studio/output)  venster open is.

7.

[Voer je game uit](/docs/nl-nl/studio/testing-modes#spelen-testen)  en let op de output:

```

h

e

l (x2)

o

wereld

```

## [Maak je comfortabel](#maak-je-comfortabel)[](#maak-je-comfortabel)

Een groot deel van het aanpassen aan een nieuwe ontwikkelomgeving is het configureren ervan om aan je behoeften te voldoen en het begrijpen van de tools die je tot je beschikking hebt:

-

De sectie Script Editor  van [Studio Settings](/docs/nl-nl/studio/setup#aanpassing)  laat je kwaliteitsverbeteringen zoals lettertype, kleuren, inspringing, autocompleteren, haakjes en tooltips aanpassen. Je wilt misschien ook de donkere modus inschakelen in de sectie Studio .

-

Door Ctrl  of Command  ingedrukt te houden en op een functie of variabele te klikken, ga je naar de declaratie in je codebase (of de online documentatie). Het gebruik van [Zoeken en Alles Zoeken](/docs/nl-nl/studio/script-editor#zoeken-en-vervangen)  kan je helpen om grotere projecten te navigeren.

-

Het [Output](/docs/nl-nl/studio/output)  venster is het meest basale hulpmiddel om het gedrag van je scripts te begrijpen. Gebruik het ⋯  menu om Show Context  en Show Source  in te schakelen.

-

Het [Script Analysis](/docs/nl-nl/studio/script-editor#scriptanalyse)  venster toont een samenvatting van fouten en waarschuwingen, maar je kunt de bruikbaarheid beperkt vinden; de Script Editor markeert deze problemen al terwijl je typt.

-

Loggingmogelijkheden zijn minimaal, zonder concept van logniveaus zoals DEBUG  of FATAL . Gebruik [print()](/docs/nl-nl/reference/engine/globals/LuaGlobals#print)  en [warn()](/docs/nl-nl/reference/engine/globals/RobloxGlobals#warn) .

Voor meer informatie over het configureren van Studio voor scripting, zie [Script Editor](/docs/nl-nl/studio/script-editor) .

Veel ontwikkelaars geven de voorkeur aan het gebruik van een externe teksteditor en versiebeheersysteem in plaats van de ingebouwde editor. Zie [Script Sync](/docs/nl-nl/scripting/sync)  en [derde partij tools](/docs/nl-nl/projects/external-tools) .

## [Je tweede script](#je-tweede-script)[](#je-tweede-script)

1.

In Roblox Studio, voeg een script toe aan ReplicatedStorage  in het [Explorer](/docs/nl-nl/studio/explorer)  venster en hernoem het naar OhNo .

2.

Voeg de volgende code toe aan het bestand:

```

print("Hallo script types en locaties!")

```

3.

[Voer je game uit](/docs/nl-nl/studio/testing-modes#spelen-testen) .

4.

Let op hoe de output niet anders is dan toen je [je eerste script](#je-eerste-script)  uitvoerde.

Om te begrijpen waarom het script niet werd uitgevoerd, zie [Script Types and Locations](/docs/nl-nl/scripting/locations) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
