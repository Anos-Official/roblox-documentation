<!-- Source: https://create.roblox.com/docs/nl-nl/performance-optimization/scene-analysis -->

Scene-analyse | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization)

# Scene-analyse

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Scene-analyse tool biedt een reeks weergaven in Roblox Studio die je op een snelle manier vergelijkende informatie geven over hoe je client- en server scènes zijn opgebouwd, welke middelen ze gebruiken en welke instanties verantwoordelijk zijn voor dat middelengebruik. Scene-analyse is ontworpen voor gebruik tijdens speel- en test sessies, en kan zowel de client- als serverdatamodellen inspecteren.

![Overzicht van de Scene-analyse tool](https://prod.docsiteassets.roblox.com/assets/optimization/scene-analysis/overview.png)

## [Scene-analyse inschakelen](#scene-analyse-inschakelen)[](#scene-analyse-inschakelen)

Selecteer in de menubalk Venster  > Prestatieoverzicht  > Scene-analyse .

## [Scene-analyse gebruiken](#scene-analyse-gebruiken)[](#scene-analyse-gebruiken)

Scene-analyse is ontworpen om te worden gebruikt tijdens een speel- of testsessie. Open het Scene-analyse venster en blader door de beschikbare modi. Wanneer een modus actief is, zie je een weergave van vakken—de vierkante treemap-weergave—die de relatieve groottes van de bekeken middelen en de instanties die eraan bijdragen tonen.

-

Onder de vierkante treemap-weergave staat een lijst van alle items in de huidige weergave.

-

Met de rechtermuisklik op een geselecteerd item in Scene-analyse kun je meestal direct naar dat item in de Explorer springen.

-

Je kunt de zoekbalk gebruiken om te filteren op naam in de huidige weergave.

## [Modi](#modi)[](#modi)

Scene-analyse heeft veel verschillende modi, elk gericht op een ander gebruiksdoel.

### [Scriptgeheugen](#scriptgeheugen)[](#scriptgeheugen)

Deze weergave toont hoeveel geheugen elke [Script](/docs/nl-nl/reference/engine/classes/Script) , [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  en [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  gebruikt in de Luau VM. Dit is het geheugen dat wordt gebruikt door tabellen en andere scriptallocaties, niet het geheugen dat wordt gebruikt door middelen zoals animaties, texturen en geluiden. De weergave is verder onderverdeeld in de gebruikelijke locaties van waaruit scripts worden uitgevoerd en door [Script](/docs/nl-nl/reference/engine/classes/Script)  versus [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript) .

### [Niet-geparented instanties](#niet-geparented-instanties)[](#niet-geparented-instanties)

De weergave van niet-geparented instanties toont welke scripts en modules verwijzingen naar instanties vasthouden, als een telling per type.

Scripts die verwijzingen naar instanties vasthouden is normaal en is op zichzelf geen indicatie van een bug of geheugenlek. Als je echter een geheugenlek onderzoekt, maakt deze weergave het gemakkelijk om te zien of een script iets doet wat je niet verwachtte.

Als je nog steeds moeite hebt om de oorzaak van een geheugenlek te vinden, is deze tool aanvullend op de [Luau heap](/docs/nl-nl/studio/optimization/memory-usage#luau-heap)  tool, die je meer informatie kan geven over individuele allocaties.

Rechtermuisklik op een script in deze weergave om het direct in de Explorer te selecteren.

### [Instantiesamenstelling](#instantiesamenstelling)[](#instantiesamenstelling)

De weergave van instantiesamenstelling toont welke instanties momenteel aanwezig zijn op de client of server. Dit is van onschatbare waarde bij het werken aan grote en complexe builds, aangezien elke instantie zowel replicatie- als geheugenkosten heeft.

De categorieën, zoals Personages, Geometrie en Texturen, zijn ontworpen om je te helpen begrijpen hoe je scène in balans is. Misschien had je bijvoorbeeld niet de bedoeling om 25.000 deeltjesemitteren te hebben, maar deze weergave laat het je weten.

Deze weergave maakt het ook gemakkelijk om alle instanties van een bepaald type te selecteren.

### [Audiogeheugen](#audiogeheugen)[](#audiogeheugen)

De weergave van audiogeheugen toont hoeveel geheugen elk audio-middel momenteel verbruikt. Het daadwerkelijke geheugen dat door een bepaald audiotrack wordt gebruikt, is vrij complex, maar in praktische termen, het verwijderen van alle instanties die naar een audiotrack verwijzen, laat dat geheugen ontladen.

Rechtermuisklik op een audio-middel in deze weergave om alle instanties te selecteren die het gebruiken.

### [Animatiegeheugen](#animatiegeheugen)[](#animatiegeheugen)

Animatiemiddelen zijn een van de meest voorkomende bronnen van geheugenlekken in productie. Roblox is agressief in het ontladen van ongebruikte animatiemiddelen, maar het is gebruikelijk dat scripts animaties actief houden nadat hun oudermodel is vernietigd.

Net als bij audiomiddelen, laat het verwijderen van alle instanties die naar een animatiemiddel verwijzen het toe om te ontladen.

Deze weergave, samen met de weergave van niet-geparented instanties, maakt het gemakkelijk om de levenscyclus van animaties te volgen en hoeveel geheugen ze daadwerkelijk gebruiken.

Rechtermuisklik op een animatie in deze weergave om alle instanties te selecteren die het gebruiken.

### [Driehoeksamenstelling](#driehoeksamenstelling)[](#driehoeksamenstelling)

De weergave van driehoeksamenstelling geeft je een gedetailleerdere breakdown van de driehoeken en tekenopdrachten die momenteel in de hoofdweergave worden gerenderd.

Deze breakdowns bevatten tellingen voor Schaduwen, Opaque, Transparant, Terrein, Gras, Deeltjes, Lucht en UI.

Deze samenstellingsinformatie helpt je beter te begrijpen hoe je scènegeometrie is samengesteld en gevallen te identificeren waar de scène onverwachte geometrie bevat.

De statistieken in deze weergave komen niet noodzakelijk overeen met wat spelers op hun apparaten zien. Schaling kan dramatische verschillen veroorzaken tussen een krachtige ontwikkelings-pc en bijvoorbeeld een middenklasse telefoon.

## [Engine API](#engine-api)[](#engine-api)

Je kunt ook programmatic toegang krijgen tot Scene-analyse gegevens via [SceneAnalysisService](/docs/nl-nl/reference/engine/classes/SceneAnalysisService) , dat wordt blootgesteld via de [MCP-server](/docs/nl-nl/studio/mcp) . Elke methode retourneert tabellen met geneste kinderen met dezelfde gegevens die de visuele weergave gebruikt.

| Methode | | Beschrijving |
| --- | --- |
| GetInstanceCompositionAsync | | Retourneert instantie tellingen per categorie en klasse uit de [DataModel](/docs/nl-nl/reference/engine/classes/DataModel)  boom. |
| GetScriptMemoryAsync | | Retourneert per-script Luau VM heap geheugenverbruik in bytes. |
| GetUnparentedInstancesAsync | | Retourneert instanties die door Luau worden vastgehouden maar niet langer in de [DataModel](/docs/nl-nl/reference/engine/classes/DataModel)  zijn, gegroepeerd per hostscript. |
| GetTriangleCompositionAsync | | Retourneert driehoek- en tekenopdracht tellingen per renderpass. |
| GetAnimationMemoryAsync | | Retourneert geladen animatieclip geheugen, gededupliceerd per clip. |
| GetAudioMemoryAsync | | Retourneert geladen audio-middel geheugen, gededupliceerd per middel ID. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
