<!-- Source: https://create.roblox.com/docs/nl-nl/projects/update-games -->

Game-updates uitbrengen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Games and places](/docs/nl-nl/production/publishing/publish-games-and-places)

# Game-updates uitbrengen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Wanneer je een bijgewerkte versie van een game publiceert op Roblox, worden spelers niet onmiddellijk verwijderd van oude versies van de game. In plaats daarvan kun je spelers migreren naar de bijgewerkte versie door al je verouderde servers opnieuw op te starten.

Als je servers niet opnieuw opstart, zullen spelers overgaan naar de nieuwe versie van de game naarmate de servers die oude versies draaien uiteindelijk leeg raken en worden afgesloten. Deze optie is niet verstorend, maar je spelersbasis kan gedurende een langere periode verschillende versies van de game spelen; als je onderliggende spelersgegevensformaat verandert, is het waarschijnlijk beter om servers opnieuw op te starten.

Voor tijdgevoelige updates geef je misschien de voorkeur aan vroeg uitrollen, inhoud achter een [config](/docs/nl-nl/production/configs)  verbergen en vervolgens de config-waarde wijzigen om je nieuwe inhoud vrij te geven.

## [Servers opnieuw opstarten](#servers-opnieuw-opstarten)[](#servers-opnieuw-opstarten)

Om servers opnieuw op te starten voor release-updates:

1.

Ga naar [Creations](https://create.roblox.com/dashboard/creations)  en selecteer de game waarvoor je servers wilt opnieuw opstarten.

2.

Navigeer in de linker navigatie naar Configuraties  > Serverbeheer .

3.

Selecteer de plaatsen die je wilt opnieuw opstarten.

4.

Klik op Servers opnieuw opstarten .

5.

In de dialoog Bevestig serverherstart :

1.

Selecteer een of beide van de volgende herstartopties:

-

Herstart alleen servers met verouderde versies  om te voorkomen dat servers die de nieuwste gepubliceerde plaatsversie draaien opnieuw worden opgestart.

-

Vertraag serverherstart  om de afsluiting van servers te vertragen en spelers een bepaalde tijd tussen 1 en 60 minuten te geven om zelf de game te verlaten in plaats van tijdelijk te worden losgekoppeld. Dit staat ook bekend als server bleed-off.

2.

Klik op Herstart .

Tenzij je een game-updateworkflow hebt die onafhankelijk is van de plaatsversie, wordt aanbevolen om altijd Herstart alleen servers met verouderde versies  te selecteren om onnodig loskoppelen van spelers te voorkomen.

Nadat je servers opnieuw hebt opgestart, doet Roblox het volgende:

1.

Stopt alle matchmaking naar servers die zijn aangewezen voor afsluiting. Spelers die je game betreden door op de Speel -knop te klikken, worden niet aan deze servers gekoppeld, maar ze kunnen er nog steeds bij komen door uitnodigingen te accepteren, te teleporteren of een andere gebruiker vanuit hun profiel te joinen.

2.

Wacht op de geconfigureerde vertragingstijd, als je de optie Vertraag serverherstart  hebt geselecteerd.

3.

Teleporteert automatisch spelers naar de bijgewerkte versie van de game. Alle spelers op dezelfde oude server worden naar dezelfde vervangende server gestuurd die de nieuwe versie draait.

Als je je game volledig wilt afsluiten en spelers niet wilt toestaan om opnieuw verbinding te maken nadat je je servers opnieuw hebt opgestart, moet je de toegang tot je game intrekken vanuit het [publiek](/docs/nl-nl/production/publishing/publish-games-and-places#doelgroep) .

## [Meldingen op servers](#meldingen-op-servers)[](#meldingen-op-servers)

Wanneer je een vertraagde serverherstart lanceert, wordt het [DataModel.ServerRestartScheduled](/docs/nl-nl/reference/engine/classes/DataModel#ServerRestartScheduled) -evenement geactiveerd op de getroffen servers met de volgende argumenten:

-

restartTime  — Een [DateTime](/docs/nl-nl/reference/engine/datatypes/DateTime) . De vroegste tijd waarop de server is gepland om af te sluiten.

-

source  — Dit zal altijd [Enum.CloseReason.DeveloperUpdate](/docs/nl-nl/reference/engine/enums/CloseReason#DeveloperUpdate)  zijn voor je gepubliceerde updates.

-

attributes  — Een optioneel JSON-object dat je kunt gebruiken om aangepaste informatie over de herstart te verstrekken, zoals de reden voor de update, urgentie, enz.

In je server-scripts kun je je abonneren op dit evenement om spelers informatie te geven over de aanstaande herstart. Je kunt ervoor kiezen om een afteltimer in je UI te bieden, spelers te vragen hun voortgang op te slaan, of ze op het meest handige moment naar bijgewerkte servers te teleporteren.

Servers worden ook op de hoogte gesteld wanneer Roblox servers moet opnieuw opstarten om infrastructuuronderhoudsredenen. Hetzelfde [DataModel.ServerRestartScheduled](/docs/nl-nl/reference/engine/classes/DataModel#ServerRestartScheduled) -evenement wordt geactiveerd, met source  als [Enum.CloseReason.RobloxMaintenance](/docs/nl-nl/reference/engine/enums/CloseReason#RobloxMaintenance)  en attributes  als een lege dictionary.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
