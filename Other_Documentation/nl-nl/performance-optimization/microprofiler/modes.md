<!-- Source: https://create.roblox.com/docs/nl-nl/performance-optimization/microprofiler/modes -->

MicroProfiler-modus | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization)
6. /
7. [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler)

# MicroProfiler-modus

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De MicroProfiler bevat verschillende modi die je kunnen helpen de prestatiekenmerken van je game op verschillende manieren te visualiseren. Na het openen van de MicroProfiler, gebruik je het Modi -menu om tussen hen te schakelen.

Frame-modus  en gedetailleerde modus  worden behandeld in [MicroProfiler-basisprincipes](/docs/nl-nl/performance-optimization/microprofiler#microprofiler-basisprincipes) .

## [Timers-modus](#timers-modus)[](#timers-modus)

Timers-modus  is een alternatieve manier om de gegevens in de gedetailleerde weergave te visualiseren: als een lijst van labels met verwerkingstijden en aanroepcounts. Horizontale staafdiagrammen in sommige kolommen helpen je de drukste taken te spotten.

 ![Timers-modus.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-timers-mode.png)

De bedieningselementen zijn vergelijkbaar met de gedetailleerde weergave:

-

Klik met de linkermuisknop en houd vast om omhoog en omlaag te pannen.

-

Klik met de linkermuisknop op een label om het toe te voegen aan de lijngrafiek rechtsonder.

-

Gebruik het Groepen -menu om de lijst te filteren.

-

Gebruik het Timers -menu om de kolommen aan te passen.

Alle informatie in deze weergave is zichtbaar wanneer je met de muis over een label in de gedetailleerde weergave beweegt.

## [Counters-modus](#counters-modus)[](#counters-modus)

Counters-modus is een lange lijst van categorieën en statistieken, inclusief het aantal instanties en het geheugengebruik (in bytes) voor de verschillende taken.

 ![Counters-modus met een enkele grafiek.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-counters-mode.png)

-

Net als in de gedetailleerde weergave, klik met de linkermuisknop en houd vast om omhoog en omlaag te pannen.

-

Klik met de linkermuisknop in de Grafiek -kolom om een kleine gebruiksgrafiek met minimum- en maximumwaarden toe te voegen. Klik opnieuw op de grafiek om deze uit te vouwen.

-

Klik met de rechtermuisknop op een grafiek om deze te sluiten.

-

Je kunt deze weergave niet filteren, maar je kunt met de linkermuisknop op een categorie (bijvoorbeeld geheugen ) klikken om deze in te klappen.

Hoewel de counters-modus nuttig kan zijn, is de [Ontwikkelaarsconsole](/docs/nl-nl/studio/optimization/memory-usage)  de beste manier om [geheugenproblemen te identificeren](/docs/nl-nl/performance-optimization/identify#clientgeheugen) . Je kunt ook de [Röntgenweergave](/docs/nl-nl/performance-optimization/microprofiler#web-only-functies)  nuttig vinden om te identificeren wanneer problematische geheugentoewijzing plaatsvindt.

## [Groepen-modus](#groepen-modus)[](#groepen-modus)

Alleen beschikbaar in de web-UI. Vergelijkbaar met de timers-modus, biedt de groepen-modus gemiddelde, maximale en totale taak tijden voor elke groep, uitgesplitst per thread, om je te helpen identificeren hoe brede categorieën van taken je frame-tijden beïnvloeden.

 ![MicroProfiler web-UI die groepen-modus toont.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-groups-mode.png)

## [Threads-modus](#threads-modus)[](#threads-modus)

Alleen beschikbaar in de web-UI. Vergelijkbaar met de timers-modus, biedt de threads-modus gemiddelde en totale taak tijden voor elke thread, uitgesplitst per groep, om je te helpen identificeren hoe je game taken over threads verdeelt.

 ![MicroProfiler web-UI die threads-modus toont.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-threads-mode.png)

## [Verborgen modus](#verborgen-modus)[](#verborgen-modus)

Alleen beschikbaar in de desktop-UI. Verborgen modus houdt het MicroProfiler-menu open, maar verbergt de staafgrafiek. Het is nuttig om visuele rommel te verminderen, [framegegevens op te slaan](/docs/nl-nl/performance-optimization/microprofiler#sla-framegegevens-op) , en te pauzeren en weer te hervatten terwijl je de lijngrafiek observeert.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
