<!-- Source: https://create.roblox.com/docs/nl-nl/production/analytics/journey-events -->

Reis evenementen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)
4. /
5. Evenementtypes

# Reis evenementen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Reis evenementen helpen je de verschillende paden te begrijpen die spelers door je ervaring nemen. In tegenstelling tot een lineaire trechter kan een reis vertakken in verschillende knooppunten en later weer samenkomen.

Je kunt reis evenementen gebruiken om stromen te analyseren, zoals:

-

Inwerken met meerdere keuzes

-

Open wereld of quest voortgang

-

Winkels met verschillende browse- en aankooppaden

-

Kenmerken die spelers in verschillende volgordes kunnen voltooien

Nadat je een reis hebt geconfigureerd en begint met het loggen van evenementen, kun je de resultaten bekijken op de Reizen  pagina in Creator Hub.

## [Configureer een reis](#configureer-een-reis)[](#configureer-een-reis)

Om een reis in Creator Hub te maken:

1.

Selecteer je ervaring.

2.

Ga naar Analytics  → Reizen . Selecteer Maak .

3.

Voer een naam voor de reis in.

4.

Voeg fasen en de knooppunten die bij elke fase horen toe.

5.

Selecteer Volgende , selecteer vervolgens Bevestigen  om de configuratie op te slaan en te publiceren.

6.

Kopieer in de stap Toevoegen aan code  de gegenereerde Luau snippet in je ervaring, selecteer vervolgens Klaar  om de reis te bekijken.

 ![De reiseditor in Creator Hub toont fasen en knooppunten die aan een reis worden toegevoegd.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Journey-Configure-Stages.png)

Een fase kan meerdere knooppunten bevatten. Knooppunten in dezelfde fase vertegenwoordigen alternatieve acties die gelijkwaardige voortgang aangeven.

De reiseditor in Creator Hub ondersteunt:

-

2–10 geconfigureerde fasen per reis

-

1–10 knooppunten per fase

-

Reisnamen die letters, cijfers, . , - , en _  bevatten, tot 50 tekens

-

Knooppuntnamen tot 50 tekens

Reisnamen mogen niet beginnen met _ . Knooppuntnamen mogen niet beginnen met __  of komma's, dubbele aanhalingstekens, apostrofs, regeleinden of NUL-tekens bevatten. Knooppuntnamen moeten uniek zijn binnen een fase, maar dezelfde naam kan in verschillende fasen worden gebruikt.

### [Automatische invoerfase](#automatische-invoerfase)[](#automatische-invoerfase)

Roblox voegt __entry__  toe als fase 0 aan het begin van elke reis. Je configureert of logt dit knooppunt niet. De 2–10 fasen die je configureert zijn genummerd van 1–10 en omvatten niet de automatische invoerfase.

### [Creator Config representatie](#creator-config-representatie)[](#creator-config-representatie)

Reisconfiguraties gebruiken het JourneysConfig  Creator Config repository type. Elke invoersleutel is de reisnaam, en de waarde bevat de fasen en knooppunten van de reis.

Bijvoorbeeld, een invoer genaamd StoreCheckout  kan deze waarde gebruiken:

JourneysConfig voorbeeld voor een StoreCheckout reis

```

{

  "stages": [

    {

      "stage_index": 1,

      "nodes": [

        { "node_name": "OpenedStore" }

      ]

    },

    {

      "stage_index": 2,

      "nodes": [

        { "node_name": "ViewedSword" },

        { "node_name": "ViewedArmor" }

      ]

    },

    {

      "stage_index": 3,

      "nodes": [

        { "node_name": "PurchasedItem" }

      ]

    }

  ]

}

```

Fase-indexen moeten sequentieel zijn en beginnen bij 1. Je sluit een fase-index niet in wanneer je een evenement logt. Roblox bepaalt de fase op basis van de gepubliceerde configuratie van het knooppunt.

## [Volg reis evenementen](#volg-reis-evenementen)[](#volg-reis-evenementen)

Roep [LogJourneyEvent()](/docs/nl-nl/reference/engine/classes/AnalyticsService#LogJourneyEvent)  aan nadat een speler een geconfigureerd knooppunt heeft bereikt. Log evenementen vanuit servercode en valideer spelersacties voordat je analytics evenementen verzendt.

De reis- en knooppuntnamen moeten exact overeenkomen met de gepubliceerde configuratie:

Een eenmalig reis knooppunt volgen

```

local AnalyticsService = game:GetService("AnalyticsService")

AnalyticsService:LogJourneyEvent(

    player,

    "StoreCheckout",

    "OpenedStore"

)

```

### [Volg terugkerende reizen](#volg-terugkerende-reizen)[](#volg-terugkerende-reizen)

Gebruik een reis sessie-ID wanneer dezelfde speler een reis kan herhalen, zoals het meerdere keren openen van een winkel:

Een terugkerende reis volgen met een sessie-ID

```

local AnalyticsService = game:GetService("AnalyticsService")

local HttpService = game:GetService("HttpService")

local journeySessionId = HttpService:GenerateGUID(false)

AnalyticsService:LogJourneyEvent(

    player,

    "StoreCheckout",

    "OpenedStore",

    journeySessionId

)

AnalyticsService:LogJourneyEvent(

    player,

    "StoreCheckout",

    "ViewedSword",

    journeySessionId

)

AnalyticsService:LogJourneyEvent(

    player,

    "StoreCheckout",

    "PurchasedItem",

    journeySessionId

)

```

Herbruik dezelfde ID voor elk evenement in één poging, en genereer een nieuwe ID wanneer een andere poging begint. Voor een reis die slechts één keer per speler voorkomt, kun je de sessie-ID weglaten.

Je kunt ook tot drie [aangepaste velden](/docs/nl-nl/production/analytics/custom-fields)  aan reis evenementen toevoegen.

## [Stel reizen in met Open Cloud en Studio MCP](#stel-reizen-in-met-open-cloud-en-studio-mcp)[](#stel-reizen-in-met-open-cloud-en-studio-mcp)

Als je je spel beheert met MCP, hoef je de Creator Hub-editor niet te gebruiken. Reizen worden opgeslagen als Creator Configs, zodat je ze kunt maken met een Open Cloud API-sleutel en de trackingcode kunt toevoegen met de Studio MCP-server.

Reisconfiguraties gebruiken het JourneysConfig  Creator Config repository type.

Om het in te stellen:

1.

Maak een API-sleutel  — Ga naar Creator Hub  > Open Cloud  > API-sleutels , selecteer API-sleutel maken  en geef het de universe:write  scope voor je spel (voeg universe:read  toe als je ook configuraties wilt teruglezen).

2.

Verbind met Studio MCP Server  — Schakel Studio in als een MCP-server, en verbind vervolgens je client met Snelle verbinding . Zodra je verbonden bent, kun je je AI-tool vragen om de reisopstelling van begin tot eind te doen. Bijvoorbeeld:

"Maak een StoreCheckout  reis met fasen OpenedStore , dan ViewedSword  of ViewedArmor , dan PurchasedItem . Hier is de documentatie over Reizen. Gebruik mijn Open Cloud API-sleutel uit de ROBLOX_API_KEY  om de configuratie te maken. Zoek vervolgens waar de winkel opent, waar items worden bekeken en waar aankopen worden bevestigd in mijn server scripts, voeg LogJourneyEvent  aanroepen toe met een reis sessie-ID, en speeltest om te controleren of de evenementen worden geactiveerd."

## [Begrijp reis voortgang](#begrijp-reis-voortgang)[](#begrijp-reis-voortgang)

Reis voortgang beweegt vooruit door de geconfigureerde fasen:

-

Het herhalen van het huidige knooppunt bevordert de voortgang niet.

-

Evenementen van dezelfde of een eerdere fase verplaatsen de voortgang niet achteruit.

-

Direct naar een latere fase gaan registreert de tussenliggende fasen als overgeslagen.

-

Een knooppunt dat niet aanwezig is in de verworven configuratieversie bevordert de reis niet.

-

Het bereiken van elk knooppunt in de geconfigureerde laatste fase telt als het bereiken van de laatste fase.

Als een gebruiker meer dan 180 dagen geen evenementen voor een reis heeft, vervalt hun opgeslagen voortgang, en worden ze als een nieuwe gebruiker voor die reis geteld als ze terugkomen. Hun voortgang begint opnieuw vanaf __entry__ .

Gebruik consistente, gemakkelijk te interpreteren namen en log elk knooppunt op hetzelfde punt in de overeenkomstige spelersactie.

## [Bekijk reis analytics](#bekijk-reis-analytics)[](#bekijk-reis-analytics)

Vanuit Analytics  → Reizen , vind een geconfigureerde reis en selecteer Bekijk .

De pagina biedt aparte Sessies  en Gebruikers  weergaven:

-

De Sessies  weergave evalueert elke reis sessie onafhankelijk.

-

De Gebruikers  weergave toont de voortgang van elke speler bij hun eerste keer over de reis sessies.

Elke weergave bevat:

-

Totaal aantal reisgebruikers of sessies

-

Gebruikers of sessies die de geconfigureerde laatste fase hebben bereikt

-

Grootste afhaak knooppunt en fase

-

Een Sankey-diagram dat paden tussen knooppunten toont

-

Een pad uitsplitsing

-

Uitsplitsingen van churn per knooppunt of fase

 ![De Reizen analytics pagina toont de Sessies en Gebruikers weergaven, totalen, een Sankey-diagram van paden tussen knooppunten, en een pad uitsplitsing.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Journey-Analytics-View.png)

Je kunt de resultaten filteren op:

-

Reisnaam en versie

-

Aangepaste velden 1–3

-

Leeftijdsgroep en geslacht

-

Betaler en nieuwe gebruiker status

-

Besturingssysteem en platform

### [Datumbereiken en cohorten](#datumbereiken-en-cohorten)[](#datumbereiken-en-cohorten)

Het geselecteerde datumbereik definieert de acquisitiecohort:

-

Een gebruiker behoort tot de datum waarop ze voor het eerst de reis binnenkwamen.

-

Een sessie behoort tot de datum waarop die reis sessie begon.

-

Analytics omvat de voortgang van die cohort gedurende 90 dagen na het einde van het geselecteerde bereik.

De voortgang van de gebruiker blijft gekoppeld aan de reisversie die de gebruiker voor het eerst verwierf. Elke nieuw begonnen reis sessie gebruikt de versie die actief was toen die sessie begon.

## [Wijzig een reis](#wijzig-een-reis)[](#wijzig-een-reis)

Vanuit de lijst van Reizen kun je:

-

Selecteer Bekijk  om de analytics pagina te openen

-

Selecteer Bewerken  om de reis te wijzigen

-

Selecteer Verwijderen  om de configuratie permanent te verwijderen

Het opslaan van een bewerking publiceert een nieuwe configuratieversie. De Reisversie  filter toont één versie tegelijk, gelabeld met de datum en tijd waarop deze is gepubliceerd, en standaard op de nieuwste versie die spelers hebben verworven tijdens het geselecteerde datumbereik. Om een andere versie te analyseren, selecteer je deze uit de filter.

Het publiceren van een nieuwe versie migreert geen bestaande voortgang

In de Gebruikers  weergave blijft een speler die de reis al heeft verworven gekoppeld aan die oorspronkelijke versie. De nieuwe versie geldt wanneer een speler de reis nieuw verwerft.

In de Sessies  weergave behoudt elke sessie de versie die het verwierf toen het begon. Een nieuwe reis sessie verwerft de momenteel gepubliceerde versie, zelfs wanneer de speler gebruikersniveau voortgang heeft op een oudere versie.

Reisconfiguraties worden dagelijks verwerkt. Als je meerdere versies op dezelfde dag publiceert, gebruikt analytics de nieuwste versie die die dag beschikbaar is voor nieuw verworven gebruikers en sessies.

## [Zie ook](#zie-ook)[](#zie-ook)

-

[Trechter evenementen](/docs/nl-nl/production/analytics/funnel-events)

-

[Aangepaste velden](/docs/nl-nl/production/analytics/custom-fields)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
