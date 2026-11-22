<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-5/intro-to-dictionaries -->

Introductie tot woordenboeken | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Woordenboeken en arrays](/docs/nl-nl/tutorials/fundamentals/coding-5/landing)

# Introductie tot woordenboeken

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Woordenboeken zijn tabellen die namen of sleutels  aan een waarde associëren in plaats van aan een index.

Voorbeeld:

Gebruik woordenboeken wanneer je waarden moet labelen, niet alleen in volgorde zoals een array dat doet. Oefen met het gebruik van woordenboeken in deze tutorial door waarden te manipuleren die aan een speler zijn gekoppeld.

## [Woordenboek syntaxis](#woordenboek-syntaxis)[](#woordenboek-syntaxis)

Net als arrays worden woordenboeken aan een variabele toegewezen met accolades {} . Sleutel-waarde paren  worden op aparte regels opgeslagen, gevolgd door een komma. Sleutels en waarden kunnen elk datatype zijn, inclusief strings, getallen en variabelen.

Om delen of andere geïnstantieerde objecten als sleutels te verwijzen, gebruik je haakjes.

```

local groeneDeel = workspace.GroeneDeel

local rodeDeel = workspace.RodeDeel

local deelLijst = {

    [groeneDeel] = true,

    [rodeDeel] = false,

}

print(deelLijst[rodeDeel])

```

Gebruik consistente datatypes voor woordenboek sleutels. Het mengen van datatypes, zoals het gebruik van zowel strings als variabelen voor sleutels, kan leiden tot inconsistente resultaten bij het manipuleren van de array en andere programmeurs in verwarring brengen.

## [Maak een woordenboek](#maak-een-woordenboek)[](#maak-een-woordenboek)

Een alledaags gebruik van woordenboeken is het organiseren van speler- of karakterinformatie. Deze stappen verkennen hoe de informatie van een theoretisch vijandelijk karakter kan worden opgeslagen en benaderd.

1.

Maak in een nieuw script een woordenboek genaamd vijand .

```

local vijand = {

}

```

2.

De eerste sleutel in het woordenboek zal de naam van de vijand bijhouden met een variabele genaamd Naam .

```

local vijand = {

    Naam

}

```

3.

Wijs een vijandsnaam toe aan de sleutel, gevolgd door een komma.

```

local vijand = {

    Naam = "Spike",

}

```

4.

Voeg een tweede sleutel-waarde paar toe voor hoeveel gezondheid de vijand zou moeten hebben. Vergeet niet, sleutels moeten altijd hetzelfde datatype gebruiken, maar waarden hoeven dat niet.

```

local vijand = {

    Naam = "Spike",

    Gezondheid = 1000,

}

```

### [Gebruik woordenboekwaarden](#gebruik-woordenboekwaarden)[](#gebruik-woordenboekwaarden)

Er zijn twee manieren om woordenboekwaarden te benaderen:

-

tabelNaam["sleutelNaam"]  (let op de aanhalingstekens)

-

tabelNaam.sleutelNaam

Welke stijl te gebruiken hangt meestal af van het doel van de tabel. Voor tabellen die een verzameling waarden bevatten, zoals een lijst van spelers op een server, zullen programmeurs meestal tabelNaam["sleutelNaam"]  gebruiken. Voor een woordenboek dat wordt gebruikt om een object te beschrijven, zullen programmeurs waarschijnlijk tabelNaam.sleutelNaam  gebruiken.

## [Wijzig een woordenboekwaarde](#wijzig-een-woordenboekwaarde)[](#wijzig-een-woordenboekwaarde)

Het wijzigen van de waarde van een sleutel is hetzelfde als bij elke andere variabele; gebruik de gelijkheidsoperator = .

1.

Onder de vijand  tabel, stel de naam van de vijand in op iets anders.

2.

Speeltest en controleer het uitvoervenster.

## [Bestaande variabelen als sleutels](#bestaande-variabelen-als-sleutels)[](#bestaande-variabelen-als-sleutels)

Woordenboeken kunnen interactie hebben met bestaande variabelen die in andere delen van een script zijn gedeclareerd. Het volgende codevoorbeeld gebruikt een variabele om de naam van een speler als sleutel toe te voegen wanneer ze het spel betreden en stelt vervolgens hun puntenwaarde in op 0.

1.

Maak in ServerScriptService  een nieuw script genaamd PlayerPoints. In het script, haal de Players Service op en maak een leeg woordenboek genaamd spelerPunten .

```

local Spelers = game:GetService("Players")

local spelerPunten = {

}

```

2.

Codeer een lokale functie voor het instellen van spelerpunten met een parameter voor een nieuwe speler variabele. Verbind de functie met het [Players.PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded)  evenement.

```

local spelerPunten = {

}

local function stelPuntenIn(nieuweSpeler)

end

Spelers.PlayerAdded:Connect(stelPuntenIn)

```

3.

In de functie, voeg een variabele toe om de Naam  van de speler op te halen, een eigenschap in elk Player  object, en een printstatement voor testdoeleinden.

```

local function stelPuntenIn(nieuweSpeler)

    local naam = nieuweSpeler.Naam

    print("hallo " .. naam)

end

```

4.

Voeg naam  toe aan het spelerPunten  woordenboek als sleutel, en stel de waarde, de punten van de speler, in op 0.

```

local function stelPuntenIn(nieuweSpeler)

    local naam = nieuweSpeler.Naam

    print("hallo " .. naam)

    spelerPunten[naam] = 0

end

```

Aangezien naam  als een variabele is gemaakt, kan deze worden benaderd met de werkelijke variabelenaam. Als naam  een sleutelnaam was, zou deze op dezelfde manier als andere strings moeten worden benaderd: spelerPunten["naam"] .

5.

Gebruik naam  om de naam van de speler af te drukken en spelerPunten[naam]  om de waarde van de sleutel die overeenkomt met de variabele af te drukken.

```

local function stelPuntenIn(nieuweSpeler)

    local naam = nieuweSpeler.Naam

    print("hallo " .. naam)

    spelerPunten[naam] = 0

    print(naam .. " heeft " .. spelerPunten[naam] .. " punten.")

end

```

6.

Voer het project uit en observeer de output.

Voltooid script

```

local Spelers = game:GetService("Players")

local spelerPunten = {

}

local function stelPuntenIn(nieuweSpeler)

    local naam = nieuweSpeler.Naam

    print("hallo " .. naam)

    spelerPunten[naam] = 0

    print(naam .. " heeft " .. spelerPunten[naam] .. " punten.")

end

Spelers.PlayerAdded:Connect(stelPuntenIn)

```

### [Optionele uitdagingen](#optionele-uitdagingen)[](#optionele-uitdagingen)

Hieronder staan enkele uitdagingen die van toepassing zijn op het gebruik van woordenboeken op verschillende manieren. Kijk of je de code voor deze kunt uitbreiden.

-

Maak een valdeel dat schade toebrengt in de loop van de tijd aan een speler. Zodra een speler de val aanraakt, breng ze schade toe, wacht, en laat ze dan weer schade oplopen.

-

Maak een functie die controleert welke van de twee spelers de meeste punten heeft door toegang te krijgen tot een woordenboek.

-

Maak een cipher, een systeem van het verwisselen van de ene string voor de andere om een "geheime" code te creëren. Bijvoorbeeld, de letter "A" kan worden verwisseld met "G," of het woord "appel" kan worden verwisseld met "sinaasappel."

## [Woordenboeken en pairs()](#woordenboeken-en-pairs)[](#woordenboeken-en-pairs)

pairs()  is een functie die vaak wordt gebruikt om door woordenboeken  te itereren. Een voorbeeld is hieronder te zien.

pairs()  kan worden gebruikt om met een sleutel, waarde of beide van een woordenboekelement te werken. In de for-lus hieronder is de eerste variabele de sleutel. De tweede variabele is de waarde. Het woordenboek waarmee je wilt werken, wordt doorgegeven aan pairs() .

Wanneer uitgevoerd, zal de code het volgende afdrukken. pairs()  garandeert geen volgorde, dus deze regels kunnen anders worden afgedrukt.

```

Je hebt:

43 Gouden Bakstenen

3 Wortelen

2 Fakkels

```

## [Samenvatting](#samenvatting)[](#samenvatting)

Woordenboeken zijn tabellen die sleutel-waarde paren gebruiken in plaats van geïndexeerde waarden. Woordenboeken en arrays beginnen op een vergelijkbare manier door accolades aan een variabele toe te wijzen. Houd invoer gescheiden met komma's.

Alle sleutels binnen een woordenboek moeten hetzelfde datatype gebruiken, maar de waarden kunnen zonder probleem datatypes mengen.

De manier waarop een woordenboek wordt benaderd kan de bedoeling ervan overbrengen. Een woordenboek van vijandelijke eigenschappen zal waarschijnlijk met de puntoperator worden benaderd, terwijl een lijst van namen waarschijnlijk tabelNaam[sleutelNaam]  zal gebruiken.

Bij het gebruik van haakjes, wees voorzichtig; sleutelnamen die binnen de tabel zijn gemaakt, moeten als strings worden behandeld: tabelNaam["sleutelNaam"] . Echter, bij het verwijzen naar objecten zoals delen, zijn de aanhalingstekens niet nodig: tabelNaam[sleutelNaam] .

Veel scripts moeten door woordenboeken of arrays gaan, maar je weet misschien niet altijd het begin en het einde van deze datastructuren. Bijvoorbeeld, een woordenboek van spelers kan veranderen, of spelers kunnen een array-inventaris van variërende groottes hebben.

In deze situaties kun je pairs()  en ipairs()  in een for -lus gebruiken om door elk element te gaan zonder bekende begin- en eindpunten. Je kunt ook algemene iteratie gebruiken door het in -sleutelwoord om door elementen te lopen zonder de noodzaak voor pairs()  of ipairs() .

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-5/pairs-and-ipairs)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-5/make-changes-to-arrays)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
