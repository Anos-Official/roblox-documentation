<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-2/parameters-practice-buttons -->

Parameters oefenen - knoppen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Functies en evenementen](/docs/nl-nl/tutorials/fundamentals/coding-2/functions-and-events)

# Parameters oefenen - knoppen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Knoppen kunnen door spelers worden gebruikt om nieuwe gebieden te ontgrendelen, punten te geven en schatten te onthullen. Wanneer een speler een knop aanraakt, moet er enige feedback worden gegeven om spelers te laten weten dat er interactie is, zoals het veranderen van kleuren of het maken van geluiden.

In dit voorbeeld zal de knop worden gebruikt om een brug te activeren. Wanneer de knop is ingedrukt, wordt deze groen en kunnen spelers de brug gebruiken. Als de speler de knop niet heeft ingedrukt, zal hij door de brug vallen wanneer hij probeert erop te lopen.

## [Maak een brug](#maak-een-brug)[](#maak-een-brug)

Begin met het opzetten van de brug.

1.

Maak een gebied in je omgeving waar spelers een brug nodig hebben.

2.

Maak een onderdeel voor de brug en hernoem het naar Brug.

3.

Selecteer de brug, in het Eigenschappenvenster:

-

Verander Transparantie  naar .5. Voor Transparantie is 0 zichtbaar, 1 is onzichtbaar.

-

Vink Verankerd  aan.

-

Vink KanBotsen  uit.

4.

Wanneer je het spel test, zou de brug mistig moeten lijken en zouden mensen er nog niet op moeten kunnen lopen.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-2/transparent-bridge.jpg)

## [Maak de knop](#maak-de-knop)[](#maak-de-knop)

Nu de brug is ingesteld, maak de knop.

1.

Maak een nieuw onderdeel genaamd * Knop* .

2.

Verander de kleur van de knop naar rood.

3.

Veranker  de knop.

4.

Verplaats de knop zodat deze iets zweeft en niets aanraakt. Dit is om ervoor te zorgen dat het Aangeraakt  evenement niet per ongeluk wordt geactiveerd.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-2/red-button.jpg)

## [Maak de knop interactief](#maak-de-knop-interactief)[](#maak-de-knop-interactief)

Deze keer, in plaats van het [Aangeraakt](/docs/nl-nl/reference/engine/classes/BasePart#Aangeraakt)  evenement te gebruiken om een valstrik te maken, gebruik je het om een knop te maken die de brug bruikbaar maakt. Om de brug botsbaar te maken, gebruik je de code brug.KanBotsen = true  binnen een aangepaste functie die wordt uitgevoerd wanneer een speler de knop aanraakt. Je weet alles wat je nodig hebt om de volgende stappen te voltooien.

Probeer het zelf uit te zoeken voordat je naar de code-oplossing kijkt.

1.

Voeg een nieuwe script  toe aan de knop genaamd * ActiveerBrug* .

2.

Verwijder Hallo Wereld .

3.

Maak variabelen voor de brug en voor de knop.

4.

Maak een lokale functie  die het volgende doet wanneer de knop wordt aangeraakt:

-

Print "knop aangeraakt" .

-

Verander de kleur van de knop van rood naar groen wanneer deze wordt aangeraakt.

-

Verander de transparantie van de brug naar 0 om deze zichtbaar te maken.

-

Maak de brug bruikbaar door de code brug.KanBotsen = true  te gebruiken.

5.

Verbind de functie met het Aangeraakt  evenement van de knop.

6.

Test het script en zorg ervoor dat de brug verschijnt wanneer de knop wordt aangeraakt.

Code Oplossing Hieronder staat een mogelijke code-oplossing

```

-- Voeg dit script toe aan de knop

-- Verandert de knop in groen wanneer iets de knop aanraakt.

local knop = script.Parent

local brug = workspace.Brug

local function knopAangeraakt()

	print("knop aangeraakt")

	knop.Color = Color3.fromRGB(0, 170, 0)

	brug.Transparantie = 0

	brug.KanBotsen = true

end

knop.Aangeraakt:Connect(knopAangeraakt)

```

### [Los je code op](#los-je-code-op)[](#los-je-code-op)

Probleem: De brug is al solide wanneer het spel begint.  Zorg ervoor dat de onderdelen zijn verankerd en niets aanraken. De onderdelen kunnen iets aanraken, zoals terrein of een ander onderdeel, en de functie knopAangeraakt() per ongeluk activeren.

Probleem: Je krijgt een foutmelding in het Uitvoer venster die zegt: "Brug is geen geldig lid van Workspace"  Controleer het volgende:

-

De naamgeving van je brug. De brug in je script moet precies zo genoemd zijn als in de Explorer.

-

Dat onderdeel.Aangeraakt:Connect(knopAangeraakt)  buiten de functie knopAangeraakt() staat.

### [Optionele code-uitdaging](#optionele-code-uitdaging)[](#optionele-code-uitdaging)

Het script in deze les kan ook worden gebruikt om deuren te maken die spelers buiten specifieke gebieden houden. Oefen je programmeervaardigheden en doe het volgende:

-

Maak een deuronderdeel.

-

Maak een knop verder weg van de deur.

-

Verander het script in deze les zodat het de deur transparant maakt en zodat de speler er niet tegenaan kan botsen.

Jouw versie kan er ongeveer zo uitzien:

```

local knop = script.Parent

-- Herinnering: Vervang de naam van het onderdeel, Poort, met degene in jouw project

local poort = workspace.Poort

local function knopAangeraakt()

	print("knop aangeraakt")

	-- Verandert de knop naar rood om de speler feedback te geven

	knop.BrickColor = BrickColor.Red() -- VERANDER DIT

	-- Maak de poort onzichtbaar

	poort.Transparantie = 1

	-- Zorgt ervoor dat de speler door de poort kan lopen

	poort.KanBotsen = false

end

knop.Aangeraakt:Connect(knopAangeraakt)

```

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-2/multiple-parameters-and-arguments)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-2/use-parameters-and-events)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
