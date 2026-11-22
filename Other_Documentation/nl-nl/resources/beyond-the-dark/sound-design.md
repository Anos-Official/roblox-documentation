<!-- Source: https://create.roblox.com/docs/nl-nl/resources/beyond-the-dark/sound-design -->

Geluidsontwerp | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)
4. /
5. [Beyond The Dark](/docs/nl-nl/resources/beyond-the-dark)

# Geluidsontwerp

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

![Geluidsontwerp Banner](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/sound-design/Sound-Banner.jpeg)

De aanpak die we hebben gebruikt om het ruimtevaartuig met audio te vullen, was het implementeren van een 2D alomtegenwoordige geluidsbed als onze basisgeluid en het gebruik van 3D-geluiden die aan objecten zijn gekoppeld (spot-omgevingen) om het oor van de gebruiker in verschillende richtingen te trekken terwijl ze het schip verkennen. We hebben veel gefocust op onderdompeling en het zo realistisch mogelijk laten aanvoelen van het schip bij het creëren en plaatsen van deze geluiden. Het resultaat is een levendige omgeving die vol zit met sonische diversiteit en zakken van leuke audio-ontdekking.

Het DSR-14 ruimteschip bevat de volgende audio die door een aangepaste mixhiërarchie zijn gestuurd die het volume van elke geluidsgroep dynamisch verlaagt en verhoogt:

-

Eén 2D-geluidbed

-

Twee dialoogtracks

-

Drie aangepaste muziektracks

-

10 gescripte audio-evenementen

-

50 3D-geluiden

## [Ontwerp geluidsassets en effecten](#ontwerp-geluidsassets-en-effecten)[](#ontwerp-geluidsassets-en-effecten)

Het aquarium van het ruimtevaartuig geeft enkele van onze favoriete geluiden in het spel weer. Het is een perfecte belichaming van de ontwerpfilosofie die we hebben toegepast, waarbij we spot-omgevingen gebruiken om de ruimte dynamisch en fris te laten aanvoelen elke keer dat je een onderscheidend gebied binnenkomt of verlaat. Andere plaatsen waar we dit deden, omvatten neonlicht zoemen, ventilatoren en het gerommel van het zwarte gat.

Zoals te zien is in de volgende screenshot, is het herhalende aquariumgeluid een kind van een onderdeel binnen het aquarium om het een locatie in de scène te geven om vanuit te spelen.

 ![Geluidsontwerp In-Studio Locatie Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/sound-design/In-Studio-Sound.jpeg)

Het aquariumgeluid gebruikt twee hoofdlagen: een zaag-golf synthesizerloop en een opname van een rivier in de Catskill Mountains in New York. Dit creëerde het gevoel van een high-tech motor die water door het aquarium duwt. We hebben een [EqualizerSoundEffect](/docs/nl-nl/reference/engine/classes/EqualizerSoundEffect)  toegepast op het riviergeluid om hoge frequenties te elimineren en het een meer "onderwater" gevoel te geven.

 ![Geluidsontwerp In-Studio Locatie Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/sound-design/In-Explorer-Sound.png)

We hebben een [ChorusSoundEffect](/docs/nl-nl/reference/engine/classes/ChorusSoundEffect)  toegepast op de synthesizerloop om het een meer buitenaards geluid te geven. Deze chorus voegt een wobbly de-tuned effect toe aan elke inhoud die je erdoorheen laat gaan. Het is een geweldige manier om iets vreemd of onnatuurlijk te laten klinken, en het is ook een veelgebruikte effect in muziek. Hier hebben we een snelheid van 16 cycli per seconde gekozen, en een vrij milde chorusdiepte van 0.21. Met deze instellingen komt een deel van het oorspronkelijke karakter van het geluid nog steeds naar voren.

 ![Geluidsontwerp In-Studio Locatie Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/sound-design/Sound-Properties.png)

Wanneer we deze geluiden samenvoegen, past het heel goed bij het object en de ruimte. Je vraagt je misschien af waarom we niet vanaf het begin een herhalend geluid hebben geëxporteerd dat zo klinkt en het als één object hebben geïmplementeerd. Er zijn twee belangrijke voordelen aan het laagjesgeluid op deze manier:

-

We krijgen meer gebruik uit dezelfde inhoud door het riviergeluid opnieuw te gebruiken in de regenwoudkamer.

-

We krijgen real-time willekeurigheid die het geluid gevarieerd en interessant houdt over lange tijdsperioden. Twee gelaagde geluidloops worden zo lang als hun kleinste gemene veelvoud. Met andere woorden, een zes seconden loop en een vijf seconden loop blijft uniek voor 30 seconden, waardoor de audio variëteit gratis toeneemt.

Andere geluidsassets zijn gemaakt voor meerdere gescripte sequenties op het schip, bijvoorbeeld het zwarte gat dat het anti-zwaartekracht effect activeert. Deze assets zijn grotendeels gemaakt van opnames van een tosti-oven deur, naar beneden gepitched en door verschillende reverb en EQ-effecten gehaald. Het naar beneden pitchen van dit bronmateriaal impliceert de grote omvang van het schip, en de reverb doet een geweldige job om dat effect te blijven versterken, door het geheel als een grot te laten aanvoelen. Enkele gesynthetiseerde laser-elementen zijn ook gegenereerd en toegevoegd voor extra accent en impact op de evenementen.

## [De mix](#de-mix)[](#de-mix)

De mix gebruikt een geneste busstructuur met geluidsgroepen en twee sidechain-compressoren. Het belangrijkste doel van de mix was om helderheid en luisterinteresse te creëren.

 ![Geluidsontwerp In-Studio Locatie Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/sound-design/Sound-Structure.png)

Bij het creëren van een mix voor een omgeving met zoveel opwinding en ambient activiteit als dit schip, is het belangrijk om te voorkomen dat dingen sonisch uit de hand lopen. Dit betekent het creëren van prioriteit door middel van sidechains. Laten we eens kijken naar een van de sidechain-compressoren op de generieke ambiance [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup) .

 ![Geluidsontwerp In-Studio Locatie Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/sound-design/Sound-Structure-Properties.png)

Een sidechain-compressor laat één audio-bron het volume van een andere verlagen op basis van het huidige volume. Dit is een effect dat vaak wordt gebruikt in podcasts, muziek, games en andere audio-media. Zoals je kunt zien in de bovenstaande afbeelding, ontvangt het Ambience Generic bed compressie van Ambience Local. Dit betekent dat wanneer de speler naar een lokale ambiance zoals de waterval loopt, het generieke ruimteschip-geluidbed wordt verlaagd. Dit creëert een gevoel van audio "versheid" rond het schip. Al deze geluiden en interessante gebieden creëren ruimte voor elkaar om te ademen en de focus van de aandacht te zijn.

De werkelijke instellingen op deze compressor in de afbeelding die wordt getoond, hoewel instructief, zijn zeer specifiek voor deze geluiden en zullen anders zijn, afhankelijk van hoe luid je bronaudio en doel zijn. Ze kunnen niet worden gekopieerd en geplakt en gebruikt met andere inhoud om hetzelfde effect te leveren. Alles is relatief aan het volume van je inhoud!

Een algemeen overzicht van de drie belangrijkste instellingen in de compressor, en hoe ze zich gedragen in de sidechain:

1.

Aanval / Vrijgave  — Dit is hoe snel in seconden de compressor begint met verlagen, en hoe langzaam het terugkeert naar het normale volume nadat het is verlaagd.

2.

Drempel  — Deze waarde bepaalt het minimale volume-niveau waarop de compressor zal beginnen te werken.

3.

Verhouding  — Dit verwijst naar hoe intens het sidechained materiaal zal worden verlaagd; een hogere verhouding geeft aan dat er meer ernstige verlaging plaatsvindt.

[Volgende](/docs/nl-nl/resources/beyond-the-dark/user-interface)[Vorige](/docs/nl-nl/resources/beyond-the-dark/layered-clothing)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
