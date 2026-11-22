<!-- Source: https://create.roblox.com/docs/nl-nl/performance-optimization/microprofiler/network -->

Netwerkgebruik | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization)
6. /
7. [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler)

# Netwerkgebruik

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De MicroProfiler laat je ook netwerkverkeer vastleggen en bekijken, wat je kan helpen om de oorzaken van hoge latentie en laadproblemen in je games te identificeren.

Netwerkgegevens zijn alleen beschikbaar in frame-dumps van de desktopclient of Studio , niet in de realtime-overlay. Als je lag of andere problemen tegenkomt waarvan je vermoedt dat ze netwerkgerelateerd zijn, is dat een uitstekend moment om [MicroProfiler-gegevens op te slaan](/docs/nl-nl/performance-optimization/microprofiler#sla-framegegevens-op) .

## [Netwerkgegevens vastleggen](#netwerkgegevens-vastleggen)[](#netwerkgegevens-vastleggen)

1.

Open de MicroProfiler met Ctrl Alt F6  of ⌘ ⌥ F6 .

2.

Kies in het Netwerk -menu voor Hoog , Laag  of Uit .

-

Hoog  bevat aanvullende informatie over de items binnen een batchgegevenspakket, de taak die het pakket heeft gedeserialiseerd en de asset-ID voor eventuele assets in het verzoek of antwoord.

-

Laag  legt minder gegevens vast en is minder rekenintensief. Afhankelijk van je computer kan het selecteren hiervan helpen om je dumps een groter aantal frames te laten bevatten. Dit is het standaardniveau en het niveau dat de MicroProfiler gebruikt wanneer je [een mobiel apparaat profileert](/docs/nl-nl/performance-optimization/microprofiler#profile-mobile-devices) .

-

Uit  betekent dat netwerkgegevens niet zijn opgenomen in frame-dumps.

3.

[Sla MicroProfiler-framegegevens op](/docs/nl-nl/performance-optimization/microprofiler#sla-framegegevens-op)  en open het gegenereerde HTML-bestand.

## [Basisnavigatie](#basisnavigatie)[](#basisnavigatie)

Nadat je de MicroProfiler-dump in een webbrowser hebt geopend, selecteer je X-Ray  / Netwerk . Er verschijnen twee extra rijen onder de grafiek van de frame-tijd:

-

De bovenste rij is ontvangen verkeer (downloads).

-

De onderste rij is verzonden verkeer (uploads).

 ![Overzicht van de netwerkgrafieken.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-network.png)

Omdat netwerkverkeer dramatisch kan variëren tussen frames, kun je een paar pieken zien en verder schijnbaar heel weinig anders. In dit geval kun je Opties  / Logaritmische schaalgrafiek  selecteren om de schaal van de balken te wijzigen, zodat ze logaritmisch in plaats van lineair schalen, wat kleine balken prominenter maakt.

De gestapelde balken zijn niet gekleurd op basis van ernst, maar op basis van type verkeer: fysica in het blauw, gegevens in het groen en assets in het rood. Beweeg de muis over een balk om de hoeveelheid ontvangen of verzonden verkeer voor dat frame te krijgen. Klik met de rechtermuisknop om het venster Netwerkevenementen  weer te geven, dat veel gedetailleerdere informatie toont.

## [Venster met netwerkevenementen](#venster-met-netwerkevenementen)[](#venster-met-netwerkevenementen)

Het venster Netwerkevenementen  toont individuele evenementen binnen de scope van het frame. Klik op een evenement voor meer gedetailleerde informatie.

 ![Overzicht van de netwerkgrafieken.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-network-events.png)

Beschikbare informatie hangt af van het type pakket en het niveau van gedetailleerdheid:

-

Engine netwerk batchgegevens  omvat verkeer door streaming, updates van instantie-eigenschappen en evenementen. Als je hoge gedetailleerdheid hebt gekozen, wordt de batchgegevens uitgebreid om individuele items te tonen. Bij lage gedetailleerdheid krijg je alleen de samenvatting.

-

Bij hoge gedetailleerdheid, klik op een Engine-netwerkpakket om in te zoomen op de taak die het pakket heeft gedeserialiseerd.

-

Ongeacht het niveau van gedetailleerdheid, klik op elk ander Engine-netwerkevenement om informatie zoals grootte, richting en type weer te geven.

-

In vergelijking met Engine-netwerkevenementen, toont HTTP-assetlevering  enkele aanvullende informatie, waaronder batchgrootte (als het verzoek was gebundeld) en het aantal in de wachtrij staande HTTP-verzoeken (indien van toepassing). Als je hoge gedetailleerdheid hebt gekozen, bevat het ook asset-ID's voor eventuele assets in het verzoek.

-

Klik op de asset-ID om in te zoomen op de taak waar de volgende stap in het ophalen van die asset plaatsvond.

-

Klik op de +  om de asset in de Creator Store te bekijken.

 ![Overzicht van de netwerkgrafieken.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-network-asset.png)

## [Aanvullende grafieken](#aanvullende-grafieken)[](#aanvullende-grafieken)

Afhankelijk van de gegevens die zijn opgenomen in de frame-dump, kun je aanvullende grafieken onder de standaard download- en uploadgrafieken bekijken:

-

Asset ophalen

-

Gegevens

-

Grote replicatorgegevens (asynchrone en chunked gegevens)

-

Fysica

-

Terrein

Klik op een categorie in de legenda om deze grafieken toe te voegen, die specifieke weergaven van elk pakkettype bieden. Elke grafiek toont standaard ontvangen verkeer (Rx), maar je kunt het label in de linkerbovenhoek van een van de drie grafieken gebruiken om over te schakelen naar verzonden verkeer (Tx).

 ![Overzicht van de netwerkgrafieken.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-network-extra.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
