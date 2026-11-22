<!-- Source: https://create.roblox.com/docs/nl-nl/production/analytics/event-types -->

Evenementtypes | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)
4. /
5. Evenementtypes

# Evenementtypes

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Evenementtypes helpen je kansen te identificeren om je game te laten groeien en te monetiseren. Ze stellen je in staat om evenementtracking in je game te integreren en je in-game economie en spelersgebruikspatronen op het Analytics-dashboard te visualiseren.

Nadat je deze evenementen vanuit je game begint te volgen met [AnalyticsService](/docs/nl-nl/reference/engine/classes/AnalyticsService) , ontgrendel je nieuwe [economie](/docs/nl-nl/production/analytics/economy-events) , [trechter](/docs/nl-nl/production/analytics/funnel-events) , [reis](/docs/nl-nl/production/analytics/journey-events)  en [aangepaste](/docs/nl-nl/production/analytics/custom-events)  dashboards onder Analytics op het Creator Dashboard. Je kunt deze dashboards gebruiken om groeikansen te identificeren en gebruikers te segmenteren op leeftijd, geslacht, platform, besturingssysteem en aangepaste velden. Al deze functies zijn gratis te gebruiken .

 ![Economie- en Trechterdashboardpagina's gevuld met gegevens.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Overview-Economy-Funnels.png)

## [Evenementtypes](#evenementtypes)[](#evenementtypes)

Roblox biedt vier sets van analytische dashboards die je kunt gebruiken om verschillende aspecten van je game te volgen:

1.

Economie-evenementen  stellen je in staat om je in-game economie te volgen, zoals:

-

Top afvoeren  — Waar geven gebruikers in-game middelen aan uit?

-

Top bronnen  — Waar verdienen gebruikers middelen?

-

Gemiddeld saldo  — Hoeveel middelen houden gebruikers vast?

2.

Trechterevenementen  stellen je in staat om de voortgang van je gebruikers door belangrijke fasen van je game te volgen, zoals:

-

Invoering  — Waar haken gebruikers af bij het starten van je game?

-

Voortgang  — Waar stoppen gebruikers met het vorderen in je game?

-

Winkel  — Waar laten gebruikers aankopen achter?

3.

Reisevenementen  stellen je in staat om de voortgang van je gebruikers door een reeks fasen te volgen die kunnen vertakken en opnieuw verbinden, zoals:

-

Invoering  — Waar vertakken gebruikers in verschillende eerste ervaringen?

-

Open-wereld voortgang  — Welke routes nemen gebruikers door niet-lineaire inhoud?

-

Winkelpaden  — Bereiken gebruikers de kassa via meerdere verschillende stromen?

4.

Aangepaste evenementen  stellen je in staat om statistieken die specifiek zijn voor je game te volgen, zoals:

-

Adoptie  — Hoeveel gebruikers klikken op een specifiek UI-component?

-

Gebruikersgedrag  — Wat is de meest gebruikte vaardigheid op elke kaart?

-

Kernloop  — Hoe verhouden kill/death-ratio's zich over verschillende wapens?

Voor meer informatie over het instellen van deze dashboards, zie [Economie-evenementen](/docs/nl-nl/production/analytics/economy-events) , [Trechterevenementen](/docs/nl-nl/production/analytics/funnel-events) , [Reisevenementen](/docs/nl-nl/production/analytics/journey-events)  en [Aangepaste evenementen](/docs/nl-nl/production/analytics/custom-events) .

## [Valideer je evenementtracking](#valideer-je-evenementtracking)[](#valideer-je-evenementtracking)

Zodra je [economie](/docs/nl-nl/production/analytics/economy-events) , [trechter](/docs/nl-nl/production/analytics/funnel-events)  of [aangepaste](/docs/nl-nl/production/analytics/custom-events)  evenementen aan je game toevoegt, duurt het meestal 24 uur voordat de grafieken op de respectieve pagina's verschijnen. In de tussentijd kun je controleren of evenementen correct zijn ingesteld met de Bekijk Evenementen  tool:

1.

Navigeer naar de Economie , Trechter  of Aangepaste  pagina's van je Analytics-dashboard voor je game.

2.

Klik op de Bekijk Evenementen  knop bovenaan elke pagina. Een bijna realtime lijst van de meest recente evenementen wordt weergegeven.

3.

Vernieuw de pagina om de lijst bij te werken.

 ![Bekijk evenementenrapport dat meerdere evenementinvoeren weergeeft, sorteerbaar op evenementtype, gebruikers-ID en trefwoord.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Event-Tracking.png)

Als je meer evenementen ziet dan je had verwacht, controleer dan of je aanroepen naar de [AnalyticsService](/docs/nl-nl/reference/engine/classes/AnalyticsService)  methoden na  een succesvolle operatie plaatsvinden. Bijvoorbeeld, je zou [LogEconomyEvent()](/docs/nl-nl/reference/engine/classes/AnalyticsService#LogEconomyEvent)  moeten aanroepen na een succesvolle aankoop, niet wanneer de gebruiker een aankoop probeert (wat kan mislukken door gebrek aan middelen).

Je kunt ook het [foutrapport](/docs/nl-nl/production/analytics/error-report)  van je game bezoeken om te zien of er fouten zijn met je evenementtracking.

## [Beperkingen van evenementtracking](#beperkingen-van-evenementtracking)[](#beperkingen-van-evenementtracking)

De volgende beperkingen zijn van toepassing bij het volgen van je evenementen met [AnalyticsService](/docs/nl-nl/reference/engine/classes/AnalyticsService) . Beperkingen worden dagelijks gereset. Je kunt de volgende dag nieuwe evenementen verzenden zodra je stopt met het verzenden van eerdere evenementen. Elk evenement blijft zichtbaar op het Creator Dashboard en vervalt automatisch na 90 dagen vanaf de laatste ontvangen gegevens.

Je kunt [aangepaste velden](/docs/nl-nl/production/analytics/custom-fields)  gebruiken om je analytische evenementen verder te filteren.

Bijvoorbeeld, in plaats van WarriorXP , MageXP , PaladinXP  als aparte economievaluta's te volgen, stel je XP  in als één valuta en stel je Warrior , Mage , Paladin , ...  in als Aangepast Veld 1. Dit stelt je in staat om deze waarden op je dashboards te splitsen en niet je valuta-cardinaliteit te gebruiken.

|  | | Beperking | | Maximale waarde | | Voorbeelden |
| --- | --- |
| Globale Snelheidslimiet | | Totaal aantal [AnalyticsService](/docs/nl-nl/reference/engine/classes/AnalyticsService)  verzoeken per minuut | | 120 + (20 * CCU) | |  |
|  | |  | |  | |  |
| Economie-, Trechter- en Aangepaste evenementen | | Aantal [aangepaste velden](/docs/nl-nl/production/analytics/custom-fields) | | 3 | | Class, Niveau, Wapen |
| Unieke waarden per [aangepast veld](/docs/nl-nl/production/analytics/custom-fields) | | Onbeperkt — Na 8.000 gecombineerde waarden over alle aangepaste velden, worden waarden gegroepeerd als "Overig" | | Warrior, Mage, Archer |
| Alleen economie | | Type middelen | | 10 | | Munten, Goud, Credits |
| transactionTypes | | Onbeperkt — Na 20 worden waarden gegroepeerd als "Overig" | | IAP, Gameplay |
| itemSkus | | Onbeperkt — Na 100 worden waarden gegroepeerd als "Overig" | |  |
| Alleen trechter | | Aantal trechters | | 10 | | Invoering, Winkel |
| Stappen per trechter | | 100 | | Stap 1, Stap 2, Stap 3 |
| Alleen aangepast | | eventNames | | 100 | | MonsterVerslagen, KillDeathRatio, HuisdierAdoptie |

## [Instrumenteer evenementen met Studio MCP](#instrumenteer-evenementen-met-studio-mcp)[](#instrumenteer-evenementen-met-studio-mcp)

Je kunt de /rbx-instrument-analytics  vaardigheid gebruiken met [Studio MCP](/docs/nl-nl/studio/mcp)  of [Assistant](/docs/nl-nl/assistant/guide)  om analytische evenementen aan je game toe te voegen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
