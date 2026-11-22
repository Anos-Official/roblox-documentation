<!-- Source: https://create.roblox.com/docs/nl-nl/production/localization/add-translations -->

Vertalingen toevoegen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Lokalisatie
6. /
7. Handmatige vertalingen

# Vertalingen toevoegen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt vertalingen toevoegen aan broninvoeren in de lokalisatietabel van je game met behulp van het [vertalerportaal](#in-vertalerportaal)  of [met een .csv -bestandsupload](#met-bestandsupload) .

In sommige gevallen kunnen strings real-time vertaling vereisen tijdens het spelen, zoals een timer, het gebruik van meeteenheden of wanneer spelersnamen worden weergegeven. Je kunt vertaalparameters aan de lokalisatietabel toevoegen als tijdelijke aanduidingen voor dit soort inhoud. Zie [Dynamische inhoud vertalen](/docs/nl-nl/production/localization/translate-dynamic-content)  voor implementatiedetails.

### [In Vertalerportaal](#in-vertalerportaal)[](#in-vertalerportaal)

Het [Vertalerportaal](/docs/nl-nl/production/localization#lokalisatie-instellingen)  van je game biedt een directe manier om vertalingen voor de verzamelde strings te bieden. Gebruikers die als vertalers voor je game zijn toegevoegd, kunnen toegang krijgen tot het Vertalerportaal.

#### [Voeg stringvertalingen toe](#voeg-stringvertalingen-toe)[](#voeg-stringvertalingen-toe)

Om tekst via de lokalisatiepagina te vertalen:

1.

Klik op de pagina met lokalisatie-instellingen op de Vertalen -knop rechtsboven.

2.

Selecteer in het menu Doeltalen  aan de linkerkant de doeltaal waarvoor je een vertaling wilt toevoegen.

3.

Selecteer het tabblad Strings  bovenaan de pagina.

4.

Selecteer in de kolom Strings de string die je wilt vertalen.

5.

Voer in het veld Te vertalen tekst  de gewenste vertaling in en klik op Opslaan .

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Adding-String.png)

Je kunt geen wijzigingen aanbrengen in de bestaande bronvelden ** Sleutel** , ** Context**  of ** Voorbeeld**  via de pagina met lokalisatie-instellingen. Om een bron's ** Sleutel** , ** Context**  of ** Voorbeeld**  velden toe te voegen of te bewerken, kun je de invoer op de pagina Lokalisatie verwijderen en opnieuw toevoegen met deze velden inbegrepen, of de wijzigingen direct aanbrengen met [bestandsupload](#met-bestandsupload) .

#### [Voeg locale-specifieke vertalingen toe](#voeg-locale-specifieke-vertalingen-toe)[](#voeg-locale-specifieke-vertalingen-toe)

Sommige talen kunnen regionale verschillen in termen of spelling hebben, zoals "soccer" en "football". Deze worden beschouwd als locales binnen talen. Momenteel ondersteunt Roblox het toevoegen van vertalingen voor de volgende locales:

| Locale Naam | | Locale ID |
| --- | --- |
| Engels (Verenigde Staten) | | en-us |
| Engels (Verenigd Koninkrijk) | | en-gb |
| Frans (Frankrijk) | | fr-fr |
| Frans (Canada) | | fr-ca |
| Portugees (Brazilië) | | pt-br |
| Portugees (Portugal) | | pt-pt |
| Spaans (Spanje) | | es-es |
| Spaans (Mexico) | | es-mx |

Voor talen die Roblox-ondersteunde locales hebben, zie je subkoppen onder de hoofdtaal voor wereldwijde en locale-specifieke vertalingen.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Locale-Left-Nav.png)

Voeg vertalingen toe die universeel zijn voor die taal (niet specifiek voor een locale) aan de sectie "Globaal", en voeg locale-specifieke vertalingen toe aan de bijbehorende secties. Als er een locale-specifieke vertaling aanwezig is, overschrijft deze wat er in de sectie "Globaal" staat voor gebruikers in die locale.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Locale-Translation.png)

Je kunt ook locale-specifieke vertalingen voor de brontaal van je game toevoegen als ze worden ondersteund.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Locale-Source.png)

Als de brontaal van je game Engels, Frans, Portugees of Spaans is, zijn locale-specifieke vertalingen voor gamenamen en beschrijvingen momenteel niet beschikbaar voor deze locales:

-

Engels (Verenigde Staten)

-

Frans (Frankrijk)

-

Portugees (Brazilië)

-

Spaans (Spanje)

#### [Voeg vertalingen voor game-informatie toe](#voeg-vertalingen-voor-game-informatie-toe)[](#voeg-vertalingen-voor-game-informatie-toe)

Je kunt game-informatie, zoals de naam, beschrijving, pictogram en miniaturen, wijzigen door de lokalisatietabel bij te werken:

1.

Klik op de pagina met lokalisatie-instellingen op de Vertalen -knop rechtsboven.

2.

Selecteer in het menu Doeltalen  aan de linkerkant de doeltaal waarvoor je een vertaling wilt toevoegen.

3.

Selecteer het tabblad Informatie  bovenaan de pagina.

1.

Voor de velden Naam en Beschrijving voer je de gewenste vertaling in en klik je op Opslaan . Houd er rekening mee dat als je hier een lege string opslaat, deze wordt opgeslagen als een handmatige bewerking die aangeeft dat de tekst niet moet worden vertaald. In dit geval zien gebruikers in de doeltaal de brontstring.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Adding-Information.png)

2.

Voor Pictogram en Miniaturen gebruik je de Upload- of Verwijderknoppen om je gelokaliseerde afbeeldingen te wijzigen. Je kunt tot 10 miniaturen per game uploaden. Klik op Opslaan  wanneer je klaar bent.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Adding-Information-Thumbnail.png)

#### [Voeg vertalingen voor gameproducten toe](#voeg-vertalingen-voor-gameproducten-toe)[](#voeg-vertalingen-voor-gameproducten-toe)

Je kunt de details van gameproducten wijzigen, zoals ontwikkelaar [producten](/docs/nl-nl/production/monetization/developer-products) , [passen](/docs/nl-nl/production/monetization/passes)  en [badges](/docs/nl-nl/production/publishing/badges) :

1.

Klik op de pagina met lokalisatie-instellingen op de Vertalen -knop rechtsboven.

2.

Selecteer in het menu Doeltalen  aan de linkerkant de doeltaal waarvoor je een vertaling wilt toevoegen.

3.

Selecteer het tabblad Producten  bovenaan de pagina.

4.

Voer de gewenste vertalingen voor je gameproduct in en klik op Opslaan .

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Adding-Product.png)

### [Met bestandsupload](#met-bestandsupload)[](#met-bestandsupload)

Met Studio of Creator Hub kun je je lokalisatietabel downloaden, bewerken en opnieuw uploaden als een .csv -spreadsheet. Dit is handig wanneer je meerdere vertalingen tegelijk wilt bewerken of wanneer je samenwerkt met vertalers buiten Roblox.

Met het bestandsuploadproces kun je alleen in-game stringinvoeren en vertalingen bewerken. In tegenstelling tot het bewerken van vertalingen via je [Vertalerportaal](#in-vertalerportaal) , stelt het bewerken van de .csv  je in staat om de extra velden Sleutel , Context  en Voorbeeld  te bewerken.

Bij het bewerken of toevoegen van vertalingen met bestandsupload, gelden de volgende gedragingen voor gloednieuwe of bestaande invoeren:

| Bestaat de invoer al in de Cloudlokalisatietabel? | | Wijzigingen aangebracht in CSV | | Verwacht gedrag bij uploaden |
| Nee | | Bronstringrij toegevoegd met een of meer vertalingen | | Invoer wordt toegevoegd, eventuele aanwezige vertalingen worden toegevoegd als een handmatige vertaalinvoer. Eventuele vertalingen die ontbreken voor ondersteunde talen komen in aanmerking voor [automatische vertaling](/docs/nl-nl/production/localization/automatic-translations) . |
| Nee | | Bronstringrij toegevoegd zonder vertalingen | | Invoer wordt toegevoegd en komt in aanmerking voor [automatische vertaling](/docs/nl-nl/production/localization/automatic-translations) . |
| Ja | | Vertaling toegevoegd of gewijzigd. | | Als de vertaling anders is dan die in de bestaande Cloudlokalisatietabel, worden vertaalupdates naar die in het .csv -bestand.
Als de oorspronkelijke vertaling automatisch is gegenereerd, wordt de nieuwe vertaling toegevoegd en vergrendeld als een handmatige vertaling. Je kunt de automatische vertaling voor deze invoer opnieuw genereren door [de invoer in het Vertalerportaal te ontgrendelen.](/docs/nl-nl/production/localization/automatic-translations#automatic-translation-updates) |
| Ja | | Vertaalinvoer voor een bronstring verwijderd. | | Vertaling wordt verwijderd en vergrendeld als een handmatige vertaling. Je kunt de automatische vertaling voor deze invoer opnieuw genereren door [de invoer in het Vertalerportaal te ontgrendelen](/docs/nl-nl/production/localization/automatic-translations#automatic-translation-updates) . |
| Ja | | Bronstring verwijderd | | Geen wijziging - invoer wordt niet verwijderd.
Om een invoer via .csv  te verwijderen, kun je:
 — In Creator Hub, gebruik Tabel verwijderen  en vervolgens CSV uploaden .
 — In Studio, gebruik Geavanceerd  ⟩ Vervangen  in de sectie Cloudlokalisatietabel. |

Om te beginnen met het toevoegen van een nieuwe ondersteunde taal, moet je de landcode handmatig als een nieuwe kolom in de spreadsheet toevoegen. Zie [Taalcodes](/docs/nl-nl/production/localization/language-codes)  voor een lijst van ondersteunde talen en landcodes.

Zorg ervoor dat je spreadsheet aan de volgende vereisten voldoet om upload- of verwerkingsproblemen te voorkomen:

-

Maximaal totaal aantal invoeren: 10.000

-

Maximale .csv -bestandsomvang: 2 MB

-

Maximaal aantal gewijzigde of toegevoegde invoeren per .csv -upload: 1.000

#### [Met Creator Hub](#met-creator-hub)[](#met-creator-hub)

Om tekst te vertalen met de .csv  in Creator Hub:

1.

Navigeer in de Creator Hub naar de instellingenpagina van je game.

2.

Navigeer naar Lokalisatie  en schakel over naar het tabblad Tabelbeheer .

3.

Selecteer CSV downloaden  om het .csv -bestand lokaal op te slaan.

4.

Open de .csv  in je favoriete spreadsheeteditor.

5.

Voeg vertalingen toe op dezelfde rij als de brontekst, onder de kolom met de specifieke landcode waarvoor je lokaliseert. Sla op wanneer je klaar bent.

6.

Selecteer CSV uploaden  en upload de bijgewerkte .csv .

7.

Klik op Bevestigen  in de prompt om de nieuwe invoeren op te slaan in de cloudlokalisatietabel.

#### [Met Studio](#met-studio)[](#met-studio)

Om tekst te vertalen met de .csv  via Studio:

1.

Open in Studio Lokalisatietools  vanuit het menu Venster  ⟩ Lokalisatie .

2.

Selecteer in de sectie Cloudlokalisatietabel  Downloaden  om de .csv  op te slaan.

3.

Open de .csv  in je favoriete spreadsheeteditor.

4.

Voeg vertalingen toe op dezelfde rij als de brontekst, onder de kolom met de specifieke landcode waarvoor je lokaliseert. Sla op  wanneer je klaar bent.

5.

Selecteer in de sectie Cloudlokalisatietabel  Bijwerken  en upload de bijgewerkte .csv .

6.

Klik op Bevestigen  in de prompt om de nieuwe invoeren op te slaan in de cloudlokalisatietabel.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
