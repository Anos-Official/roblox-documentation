<!-- Source: https://create.roblox.com/docs/nl-nl/production/localization/add-source-content -->

Voeg broninhoud toe | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Lokalisatie
6. /
7. Handmatige vertalingen

# Voeg broninhoud toe

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je moet bronteksten toevoegen om te vertalen naar de lokalisatietabel van de game voordat jij of andere medewerkers vertalingen toevoegen. Je kunt [Automatische Tekstvastlegging](#automatische-tekstvastlegging)  gebruiken om tekststrings automatisch te verzamelen terwijl je game door gebruikers wordt gespeeld of [handmatig tekstbronnen toevoegen](#handmatig-broninhoud-toevoegen) .

Zie [Afbeeldingen en geluiden lokaliseren](/docs/nl-nl/production/localization/localize-with-scripting#afbeeldingen-en-geluiden-lokaliseren)  voor instructies over het lokaliseren van niet-tekstinhoud.

## [Automatische Tekstvastlegging](#automatische-tekstvastlegging)[](#automatische-tekstvastlegging)

De Automatische Tekstvastlegging (ATC)  tool verzamelt tekststrings die gebruikers tegenkomen in je game via GUI-objecten, zoals [TextLabels](/docs/nl-nl/reference/engine/classes/TextLabel)  of [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  en is meestal de snelste manier om vertaalbare tekst uit je game te verzamelen. In veel gevallen is de Automatische Tekstvastlegging-tool al ingeschakeld voor [automatische vertalingen](/docs/nl-nl/production/localization/automatic-translations#automatische-tekstvastlegging-inschakelen) .

## [Handmatig broninhoud toevoegen](#handmatig-broninhoud-toevoegen)[](#handmatig-broninhoud-toevoegen)

Je kunt ook inhoud handmatig toevoegen. Dit wordt aanbevolen als je game tekst bevat die niet verschijnt tijdens typische gameplay, zoals een complex gespreksschema, wat langer kan duren om via ATC te verzamelen. Je kunt items aan de tabel toevoegen [op de lokalisatiepagina](#voeg-bronnen-toe-met-lokalisatie-instellingen)  of [met een .csv -bestandsupload](#voeg-bronnen-toe-met-bestandsupload) . Het wordt aanbevolen om de .csv -upload te gebruiken als je de sleutel, context of voorbeeldvelden van een item wilt specificeren.

Items in de lokalisatietabel zijn hoofdlettergevoelig.

Bijvoorbeeld, wanneer je "hello" als bronwaarde op de lokalisatietabel gebruikt, past Roblox geen vertalingen toe voor "Hello" of "HELLO".

Je kunt handmatig afbeeldings- en geluidsasset-ID's aan de lokalisatietabel toevoegen met een .csv -upload. Voor meer informatie zie [Afbeeldingen en geluiden lokaliseren](/docs/nl-nl/production/localization/localize-with-scripting#afbeeldingen-en-geluiden-lokaliseren) .

### [Voeg bronnen toe met lokalisatie-instellingen](#voeg-bronnen-toe-met-lokalisatie-instellingen)[](#voeg-bronnen-toe-met-lokalisatie-instellingen)

Je kunt broninhoud toevoegen op de [lokalisatiepagina](/docs/nl-nl/production/localization#lokalisatie-instellingen) . Dit is ideaal voor het snel toevoegen van items aan je lokalisatietabel.

Om broninhoud toe te voegen via de lokalisatiepagina:

1.

Klik op de Vertalen  knop rechtsboven op de lokalisatiepagina van je game.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Translate.png)

2.

Selecteer het tabblad Strings .

3.

Klik op Voeg item toe .

4.

Vul in het veld Te vertalen tekst  de brontekst in en klik op Opslaan .

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Add-Source-String.png)

5.

Als je key-based scripting gebruikt om een string te vertalen, vul dan de sleutelnaam in het veld Sleutel  in.

6.

Als de string meerdere betekenissen heeft, zoals de rug van een personage en een terugknop, vul dan het volledige pad van het specifieke tekstobject in het veld Context  in.

7.

Klik op Opslaan .

### [Voeg bronnen toe met bestandsupload](#voeg-bronnen-toe-met-bestandsupload)[](#voeg-bronnen-toe-met-bestandsupload)

Je kunt broninhoud aan je lokalisatietabel toevoegen met een .csv -upload. Je kunt deze optie gebruiken bij het maken van een groot aantal updates aan je lokalisatietabel.

Om broninhoud toe te voegen via de .csv -upload:

1.

Open in Studio Lokalisatietools  vanuit het Venster  ⟩ Lokalisatie

2.

Selecteer in de sectie Cloudlokalisatietabel  Downloaden  om de .csv  op te slaan.

3.

Open de .csv  in je favoriete spreadsheeteditor.

4.

Voeg onder de kolom Bron  brontekst toe en sla op. Je kunt de andere kolommen leeg laten.

| Sleutel | | Context  | | Voorbeeld | | Bron |
| --- | --- |
|  | |  | |  | | Opties |
|  | |  | |  | | Start |

5.

Selecteer in Studio, in de sectie Cloudlokalisatietabel , Bijwerken  en upload het nieuwe .csv -bestand.

6.

Klik op Bevestigen  in de prompt Bevestig upload  om het nieuwe item op te slaan in de cloudlokalisatietabel.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
