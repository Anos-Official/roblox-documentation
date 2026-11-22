<!-- Source: https://create.roblox.com/docs/nl-nl/studio/network-simulator -->

Netwerksimulator | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)
4. /
5. [Device Simulator](/docs/nl-nl/studio/device-simulator)

# Netwerksimulator

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Netwerksimulator  is een testtool in Studio die latentie, jitter en pakketverlies toevoegt aan de verbinding tussen een playtest-client en server. Gebruik het om de omstandigheden te reproduceren die spelers tegenkomen op bedrade, Wi-Fi- en mobiele verbindingen zonder een extern netwerkbeperkingshulpmiddel te configureren.

Testen onder beperkte omstandigheden kan interacties onthullen die responsief lijken op een snelle ontwikkelingsverbinding, maar vertraagd, verwarrend of onbetrouwbaar worden voor sommige spelers. Gebruik Netwerksimulator om server-bevestigde acties, gerepliceerde status, streaminggedrag, voorspelling en correctie te evalueren, en hoe jouw ervaring omgaat met incidenteel pakketverlies.

Netwerksimulator beïnvloedt alleen Studio playtests. Het verandert jouw gepubliceerde ervaring of de verbindingen van live spelers niet.

Netwerksimulator is in [beta](https://devforum.roblox.com/t/studio-beta-new-device-simulator-toolbar-and-network-simulator/4861695) , en de functionaliteit kan veranderen. Om het in te schakelen, open Bestand  en selecteer Beta-functies , schakel vervolgens Nieuwe Apparaatsimulator  in en herstart Studio.

 ![Netwerksimulator toont een mobiel voorinstelling en aparte invoer- en uitvoerlatentie, pakketverlies en jitterbesturing.](https://prod.docsiteassets.roblox.com/assets/studio/device-simulator/network-simulator-controls.png)

## [Hoe Netwerksimulator werkt](#hoe-netwerksimulator-werkt)[](#hoe-netwerksimulator-werkt)

De simulator past voorwaarden onafhankelijk in elke richting toe:

-

Inkomend  verkeer reist van de server naar de client. Het omvat gerepliceerde serverstatus en server-naar-client externe communicatie.

-

Uitgaand  verkeer reist van de client naar de server. Het omvat clientverzoeken en client-naar-server externe communicatie.

 ![Diagram dat uitgaand verkeer van de playtest-client naar de server en inkomend verkeer van de server naar de client toont.](https://prod.docsiteassets.roblox.com/assets/studio/device-simulator/network-simulator-traffic-directions.png)

Elke richting heeft de volgende besturingselementen:

| Besturingselement | | Wat het simuleert | | Wat te observeren |
| --- | --- |
| Latentie | | Minimale eenrichtingsvertraging toegevoegd aan elk pakket. | | Langzame serverbevestiging, vertraagde statusupdates en UI die vast lijkt te zitten terwijl er gewacht wordt. |
| Jitter | | Variatie toegevoegd bovenop de minimale vertraging. | | Ongelijke update-timing, zichtbare correctie, animatie of bewegingsinstabiliteit, en volgorde aannames. |
| Pakketverlies | | De kans dat een individueel pakket wordt verloren. | | Hertransmissievertragingen voor betrouwbare verkeer en ontbrekende updates voor verkeer dat is ontworpen om verlies te tolereren. |

Netwerk-ping is een meting van de heen-en-terug tijd, dus toegevoegde inkomende en uitgaande vertraging dragen beide bij. Bijvoorbeeld, 10 ms inkomende latentie en 10 ms uitgaande latentie voegen ongeveer 20 ms toe aan de bestaande heen-en-terug tijd van de verbinding.

De geconfigureerde waarden worden toegevoegd aan de werkelijke omstandigheden van de verbinding. Dit is vooral belangrijk tijdens een [Team Test](/docs/nl-nl/studio/testing-modes#samenwerkend-testen) , waar geografie en het openbare internet al bijdragen aan latentie en pakketverlies.

## [Open Netwerksimulator](#open-netwerksimulator)[](#open-netwerksimulator)

Om de tool te openen:

1.

Schakel Apparaatsimulator  in via het Test -menu.

2.

Selecteer in de werkbalk boven het 3D-venster de Netwerk -pil.

De pil geeft het type en de kwaliteit van de gestage of toegepaste verbinding weer. Open het om de exacte voorinstelling en alle zes richtingswaarden te zien.

## [Pas een voorinstelling toe](#pas-een-voorinstelling-toe)[](#pas-een-voorinstelling-toe)

Ingebouwde voorinstellingen bieden herhaalbare startpunten voor veelvoorkomende verbindingstypen. Waarden in de volgende tabel zijn vermeld als latentie / jitter / pakketverlies .

| Voorinstelling | | Pil | | Inkomend | | Uitgaand |
| Ideale Glasvezel | | LAN | | 8 ms / 0 ms / 0.00% | | 8 ms / 0 ms / 0.00% |
| Bedrade Breedband | | LAN | | 25 ms / 3 ms / 0.00% | | 25 ms / 3 ms / 0.00% |
| Thuis Wi-Fi | | Wifi | | 30 ms / 12 ms / 0.20% | | 30 ms / 15 ms / 0.30% |
| Standaard Mobiel (4G/LTE) | | 4G | | 45 ms / 20 ms / 0.40% | | 55 ms / 30 ms / 0.50% |
| Slechte Verbinding (3G) | | 3G | | 150 ms / 70 ms / 0.50% | | 180 ms / 90 ms / 0.50% |

De voorinstellingen vertegenwoordigen nuttige testomstandigheden, geen garanties over elke verbinding van dat type. Echte netwerken variëren per apparaat, locatie, provider, congestie en tijd.

Om een voorinstelling toe te passen:

1.

Selecteer een voorinstelling uit Voorinstelling .

2.

Bekijk de weergegeven Inkomende  en Uitgaande  waarden. De pil wordt ook bijgewerkt om de selectie weer te geven.

3.

Selecteer Toepassen .

4.

Start of ga verder met een [playtest](/docs/nl-nl/studio/testing-modes#spelen-testen)  en oefen een client-server interactie uit.

Het selecteren van een voorinstelling stelt alleen de waarden in. De actieve playtestverbinding verandert niet totdat je Toepassen  selecteert. Als je de popover eerst afwijst, verwerpt Netwerksimulator de gestage wijzigingen en keert het zijn besturingselementen en pil terug naar de toegepaste staat.

Nadat je Toepassen  hebt geselecteerd, gebruikt een actieve playtest onmiddellijk de nieuwe waarden. Je hoeft de sessie niet opnieuw te starten.

Ideale Glasvezel  is de standaard en minst aangetaste ingebouwde voorinstelling, maar het is niet hetzelfde als het uitschakelen van simulatie. Het voegt 8 ms in elke richting toe. Voor een vergelijking zonder toegevoegde vertraging, stel elke waarde in op 0  als een aangepaste configuratie en pas deze toe.

## [Configureer aangepaste voorwaarden](#configureer-aangepaste-voorwaarden)[](#configureer-aangepaste-voorwaarden)

Vouw Inkomend  of Uitgaand  uit om één richting te wijzigen zonder de andere te veranderen. Dit is nuttig om problemen in het client-naar-server verzoekpad te scheiden van problemen in het server-naar-client antwoordpad.

| Besturingselement | | Bereik | | Weergaveprecisie |
| Latentie | | 0–1000 ms | | 0.1 ms |
| Jitter | | 0–1000 ms | | 0.1 ms |
| Pakketverlies | | 0.00–0.50% | | 0.01% |

Pakketverlies wordt weergegeven als een percentage. Een waarde van 0.50%  betekent de helft van één procent, niet 50%.

Het bewerken van een numerieke waarde verandert Voorinstelling  in Aangepast . De bewerkingen blijven gestage totdat je Toepassen  selecteert.

Netwerksimulator gebruikt dezelfde onderliggende emulatie-instellingen als het Netwerk -tabblad van [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing) . Als die instellingen elders veranderen terwijl de simulator gestage bewerkingen heeft, hebben de externe waarden voorrang en wordt de gestage transactie verworpen.

### [Sla een aangepaste voorinstelling op](#sla-een-aangepaste-voorinstelling-op)[](#sla-een-aangepaste-voorinstelling-op)

Om een aangepaste configuratie opnieuw te gebruiken:

1.

Bewerk een of meer waarden.

2.

Selecteer Opslaan .

3.

Voer een unieke naam voor de voorinstelling in.

4.

Selecteer Opslaan & Toepassen .

 ![Opslaan Netwerk voorinstelling dialoog voor het benoemen en toepassen van een aangepaste netwerkconfiguratie.](https://prod.docsiteassets.roblox.com/assets/studio/device-simulator/network-simulator-custom-preset.png)

De opgeslagen voorinstelling wordt beschikbaar in het Voorinstelling -menu in verschillende plaatsen en latere Studio-sessies. Als je de naam van een bestaande opgeslagen voorinstelling invoert, verandert de actie in Vervangen & Toepassen . Ingebouwde voorinstellingnamen en Aangepast  zijn gereserveerd.

Wanneer een opgeslagen voorinstelling is geselecteerd, vervangt Verwijderen  Reset . Het verwijderen ervan verwijdert de opgeslagen voorinstelling en past onmiddellijk Ideale Glasvezel  toe. Toegepaste netwerkwaarden zelf worden niet bewaard na een volledige herstart van Studio.

Reset  stelt Ideale Glasvezel  in en vereist nog steeds Toepassen . Dit stelt je in staat om de geresette waarden te inspecteren voordat je de playtestverbinding wijzigt.

## [Configureer netwerkinstellingen met een script](#configureer-netwerkinstellingen-met-een-script)[](#configureer-netwerkinstellingen-met-een-script)

Elk Netwerksimulator-besturingselement komt overeen met een [NetworkSettings](/docs/nl-nl/reference/engine/classes/NetworkSettings) -eigenschap, zodat je dezelfde voorwaarden vanuit een plugin of geautomatiseerde test kunt aansteken in plaats van de werkbalk.

| Besturingselement | | Eigenschap | | Beschrijving |
| Inkomende Latentie | | [InboundNetworkMinDelayMs](/docs/nl-nl/reference/engine/classes/NetworkSettings#InboundNetworkMinDelayMs) | | Voegt latentie toe aan playtestverbindingen in de server-naar-client richting. |
| Uitgaande Latentie | | [OutboundNetworkMinDelayMs](/docs/nl-nl/reference/engine/classes/NetworkSettings#OutboundNetworkMinDelayMs) | | Voegt latentie toe aan playtestverbindingen in de client-naar-server richting. |
| Inkomende Jitter | | [InboundNetworkJitterMs](/docs/nl-nl/reference/engine/classes/NetworkSettings#InboundNetworkJitterMs) | | Voegt jitter toe aan playtestverbindingen in de server-naar-client richting. |
| Uitgaande Jitter | | [OutboundNetworkJitterMs](/docs/nl-nl/reference/engine/classes/NetworkSettings#OutboundNetworkJitterMs) | | Voegt jitter toe aan playtestverbindingen in de client-naar-server richting. |
| Inkomend Pakketverlies | | [InboundNetworkLossPercent](/docs/nl-nl/reference/engine/classes/NetworkSettings#InboundNetworkLossPercent) | | Stelt de kans in dat pakketten op playtestverbindingen van server naar client worden verloren. |
| Uitgaand Pakketverlies | | [OutboundNetworkLossPercent](/docs/nl-nl/reference/engine/classes/NetworkSettings#OutboundNetworkLossPercent) | | Stelt de kans in dat pakketten op playtestverbindingen van client naar server worden verloren. |

Het rechtstreeks instellen van een van deze eigenschappen houdt de werkbalk en pil van Netwerksimulator in sync, aangezien beide van dezelfde onderliggende instellingen lezen.

## [Test een netwerkgevoelige workflow](#test-een-netwerkgevoelige-workflow)[](#test-een-netwerkgevoelige-workflow)

Gebruik dezelfde herhaalbare interactie onder verschillende omstandigheden, zodat verschillen kunnen worden toegeschreven aan het netwerk in plaats van aan een ander codepad of scène.

1.

Kies een spelersreis die de client-servergrens overschrijdt, zoals het activeren van een server-autorisatieve mogelijkheid, het ontvangen van een inventarisupdate of het observeren van gerepliceerde beweging.

2.

Definieer hoe succes eruitziet. Registreer responstijd, zichtbare feedback, time-outgedrag, correcties, dubbele verzoeken en herstel.

3.

Pas Ideale Glasvezel  toe en voer de reis uit als basislijn.

4.

Pas een representatieve voorwaarde toe, zoals Thuis Wi-Fi  of Standaard Mobiel (4G/LTE)  en herhaal dezelfde acties.

5.

Pas Slechte Verbinding (3G)  toe als een veerkracht test. Bevestig dat de ervaring begrijpelijk blijft, zelfs wanneer updates vertraagd of ongelijk zijn.

6.

Wijzig alleen inkomende of uitgaande waarden om te isoleren welke richting het probleem blootlegt.

7.

Na het aanbrengen van een oplossing, herhaal dezelfde runs en vergelijk de resultaten.

Nuttige vragen zijn onder andere:

-

Ontvangt de speler onmiddellijke lokale feedback terwijl hij wacht op serverbevestiging?

-

Kan herhaald invoer dezelfde actie meer dan eens indienen?

-

Onderscheiden laad- en voortgangstoestanden langzaam werk van een fout?

-

Bieden time-outs een veilige retry-pad?

-

Blijft gerepliceerde beweging begrijpelijk wanneer updates ongelijk aankomen?

-

Kunnen onbetrouwbare updates worden overgeslagen zonder verouderde status op het scherm achter te laten?

-

Herstelt de ervaring na terugkeer naar een betere verbinding?

Voor grote vergelijkingen, pas de voorwaarde toe voordat je met de interactie begint. Grote latentie veranderingen tijdens een lopende test kunnen de congestiecontrole beïnvloeden, dus een nieuwe run biedt een schonere vergelijking.

## [Meet en diagnoseer resultaten](#meet-en-diagnoseer-resultaten)[](#meet-en-diagnoseer-resultaten)

Netwerksimulator verandert testomstandigheden; andere tools helpen de resultaten te verklaren:

-

De [Ontwikkelaarsconsole](/docs/nl-nl/studio/developer-console)  toont gemiddelde ping en logs, die kunnen bevestigen dat de verbinding is veranderd en fouten in hertransmissie- of time-outcode onthullen.

-

Een [MicroProfiler netwerkcapture](/docs/nl-nl/performance-optimization/microprofiler/network)  toont verzonden en ontvangen engineverkeer per frame. Gebruik het om verkeerspieken te identificeren en te bepalen of de aangetaste stroom wordt gedomineerd door replicatie, fysica of andere netwerkgegevens.

-

De [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler)  kan helpen een netwerkgevoelige vertraging te onderscheiden van een gelijktijdig frame-tijdprobleem.

Houd het scenario, de playtestmodus en de observatiemethode consistent bij het vergelijken van captures. Een enkele run onder een slechte verbinding kan een symptoom onthullen, maar herhaalde basislijn- en aangetaste runs zijn nuttiger om te meten of een wijziging heeft geholpen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
