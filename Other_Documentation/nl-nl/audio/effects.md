<!-- Source: https://create.roblox.com/docs/nl-nl/audio/effects -->

Audio-effecten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Audio](/docs/nl-nl/audio)

# Audio-effecten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Audio-effecten wijzigen of verbeteren audiostreams op een niet-destructieve manier. Je kunt deze effecten toepassen om je audio meeslepender te maken binnen je game, zoals het gebruik van een [AudioEqualizer](/docs/nl-nl/reference/engine/classes/AudioEqualizer)  object om regen gedempt te laten klinken, een [AudioCompressor](/docs/nl-nl/reference/engine/classes/AudioCompressor)  object om het maximale volume van een geluid te regelen, of [AudioReverb](/docs/nl-nl/reference/engine/classes/AudioReverb)  om realistischere reflecties van geluid in binnenruimtes toe te voegen.

## [Audio-effecten toepassen](#audio-effecten-toepassen)[](#audio-effecten-toepassen)

Je kunt audio-effecten toepassen op je audiostreams door het effect in te stellen binnen je 2D-audio of 3D-audio setup voordat het de oren van de speler bereikt. Bijvoorbeeld, om de installatie-instructies te bekijken in [Audio-objecten](/docs/nl-nl/audio/objects#2d-audio) , vereist 2D-audio een audioplayer om de stream te produceren, een fysiek hardware-apparaat zoals een luidspreker of hoofdtelefoon, en een kabel om de audiostream van de audioplayer naar het uitvoerapparaat te dragen.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/audio-objects/2D-Audio-Diagram.png)

Als je deze setup zo laat, speelt de audiostream van de asset ID af zoals deze oorspronkelijk is opgenomen. Als je echter een audio-effect op deze audiostream wilt toepassen, moet je het audio-effect in het midden van de configuratie introduceren, zodat de audiostream door het effect wordt verzonden voordat het naar het uitvoerapparaat wordt verzonden.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/effects/AudioEffect-Single.png)

De modulaire audio-objecten van Roblox stellen je ook in staat om meerdere audioplayers door een audio-effect te verbinden, wat betekent dat je niet meerdere audio-effectobjecten met dezelfde instellingen hoeft te hebben. Dit biedt veel flexibiliteit in hoe je meerdere audio-bronnen tegelijk kunt aanpassen.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/effects/AudioEffect-Multiple.png)

Bovendien kun je meerdere audio-effecten toepassen op dezelfde audiostream om je audio verder aan te passen. Terwijl de audiostream van de audioplayer naar het uitvoerapparaat wordt verzonden, is het belangrijk op te merken dat de volgorde van de audio-effecten invloed heeft op het aangepaste geluid. Bijvoorbeeld, als je eerst een [AudioChorus](/docs/nl-nl/reference/engine/classes/AudioChorus)  effect zou toepassen en daarna een [AudioDistortion](/docs/nl-nl/reference/engine/classes/AudioDistortion)  effect, kan je aangepaste geluid anders klinken dan een configuratie die het [AudioDistortion](/docs/nl-nl/reference/engine/classes/AudioDistortion)  effect vóór het [AudioChorus](/docs/nl-nl/reference/engine/classes/AudioChorus)  effect toepast.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/effects/AudioEffect-Layered.png)

Elk audio-effect dat je toepast heeft extra eigenschappen die je kunt aanpassen totdat je het gewenste geluid hebt bereikt. Voor meer informatie over deze eigenschappen, zie de API-pagina van elk audio-effect.

## [Typen](#typen)[](#typen)

### [Equalizer](#equalizer)[](#equalizer)

[AudioEqualizer](/docs/nl-nl/reference/engine/classes/AudioEqualizer)  stelt je in staat om de volume van verschillende frequentiebereiken te regelen. Dit audio-effect is nuttig om bepaalde elementen van audio te benadrukken of te minimaliseren, zoals het dempen van alle audio in je game wanneer een speler onder water gaat.

Zonder [AudioEqualizer](/docs/nl-nl/reference/engine/classes/AudioEqualizer)  effect

Met [AudioEqualizer](/docs/nl-nl/reference/engine/classes/AudioEqualizer)  effect

### [Compressor](#compressor)[](#compressor)

[AudioCompressor](/docs/nl-nl/reference/engine/classes/AudioCompressor)  vermindert het dynamische bereik van audio door het volume van de hoogste delen van een bron te verlagen terwijl het tegelijkertijd het algemene volume verhoogt. Dit audio-effect is nuttig om een consistent volume in te stellen zodat spelers het kunnen horen, zelfs als je audio opneemt terwijl je fluistert of luid spreekt. Je kunt dit dynamische effect ook gebruiken om audiostreams boven een andere te prioriteren via het proces van ducking.

Zonder [AudioCompressor](/docs/nl-nl/reference/engine/classes/AudioCompressor)  effect

Met [AudioCompressor](/docs/nl-nl/reference/engine/classes/AudioCompressor)  effect

### [Reverb](#reverb)[](#reverb)

[AudioReverb](/docs/nl-nl/reference/engine/classes/AudioReverb)  simuleert het effect van geluiden die van verschillende oppervlakken weerkaatsen. Dit audio-effect is nuttig om realistischere reflecties van geluiden in binnenruimtes te simuleren, zoals het weerkaatsen van een basketbal in een gymzaal, of het spelen van rockmuziek in een stadion.

Zonder [AudioReverb](/docs/nl-nl/reference/engine/classes/AudioReverb)  effect

Met [AudioReverb](/docs/nl-nl/reference/engine/classes/AudioReverb)  effect

### [Chorus](#chorus)[](#chorus)

[AudioChorus](/docs/nl-nl/reference/engine/classes/AudioChorus)  simuleert het effect van meerdere vocalen of instrumenten die gelijktijdig spelen door het originele geluid te nemen en kopieën te overlappen, elk met kleine variaties in toonhoogte. Dit audio-effect is nuttig voor het simuleren van een robotachtige of futuristische kwaliteit aan je audio.

Zonder [AudioChorus](/docs/nl-nl/reference/engine/classes/AudioChorus)  effect

Met [AudioChorus](/docs/nl-nl/reference/engine/classes/AudioChorus)  effect

### [Distortion](#distortion)[](#distortion)

[AudioDistortion](/docs/nl-nl/reference/engine/classes/AudioDistortion)  simuleert het effect dat zou optreden bij het overdrijven van oudere audioapparatuur. Dit audio-effect veroorzaakt clipping in het geluid en voegt een algemene "fuzziness" toe, wat nuttig is om intensiteit en karakter aan muziekinstrumenten toe te voegen.

Zonder [AudioDistortion](/docs/nl-nl/reference/engine/classes/AudioDistortion)  effect

Met [AudioDistortion](/docs/nl-nl/reference/engine/classes/AudioDistortion)  effect

### [Echo](#echo)[](#echo)

[AudioEcho](/docs/nl-nl/reference/engine/classes/AudioEcho)  zorgt ervoor dat een geluid met een vertraging herhaald wordt met afnemend volume, wat het echte effect van een echo simuleert die weerkaatst van harde oppervlakken, zoals muren en grotten.

Zonder [AudioEcho](/docs/nl-nl/reference/engine/classes/AudioEcho)  effect

Met [AudioEcho](/docs/nl-nl/reference/engine/classes/AudioEcho)  effect

### [Flanger](#flanger)[](#flanger)

[AudioFlanger](/docs/nl-nl/reference/engine/classes/AudioFlanger)  creëert een veeg- of whooshing-effect door het originele audiosignaal te kopiëren en het iets verschoven en gemoduleerd bovenop het origineel af te spelen. Dit audio-effect is nuttig om een vreemde, andere wereld digitale kwaliteit aan je audio toe te voegen. Je kunt het bijvoorbeeld gebruiken op een opname van een airconditioner om het geluid van een sci-fi ruimteschipmotor te laten rommelen.

Zonder [AudioFlanger](/docs/nl-nl/reference/engine/classes/AudioFlanger)  effect

Met [AudioFlanger](/docs/nl-nl/reference/engine/classes/AudioFlanger)  effect

### [Pitch Shift](#pitch-shift)[](#pitch-shift)

[AudioPitchShifter](/docs/nl-nl/reference/engine/classes/AudioPitchShifter)  verhoogt of verlaagt de toonhoogte zonder de afspeelsnelheid te veranderen. Dit audio-effect is nuttig voor het veranderen van de schaal van je geluiden. Je kunt het gebruiken om kleine geluiden groot te laten aanvoelen door ze naar beneden te stemmen of omgekeerd geluiden omhoog te stemmen om een explosiegeluid meer als een ballon te laten klinken.

Zonder [AudioPitchShifter](/docs/nl-nl/reference/engine/classes/AudioPitchShifter)  effect

Met [AudioPitchShifter](/docs/nl-nl/reference/engine/classes/AudioPitchShifter)  effect

### [Tremolo](#tremolo)[](#tremolo)

[AudioTremolo](/docs/nl-nl/reference/engine/classes/AudioTremolo)  creëert een trillend effect op een geluid door het volume omhoog en omlaag te variëren. Dit dynamische effect is nuttig om instrumentgeluiden om te zetten in een golvende, dromerige kwaliteit, of om zwellingen en dalingen in weergerelateerde audio te creëren.

Zonder [AudioTremolo](/docs/nl-nl/reference/engine/classes/AudioTremolo)  effect

Met [AudioTremolo](/docs/nl-nl/reference/engine/classes/AudioTremolo)  effect

### [Fader](#fader)[](#fader)

De [AudioFader](/docs/nl-nl/reference/engine/classes/AudioFader)  past het volume van audiostreams aan om hoger of lager te zijn. Dit audio-effect is nuttig om het volume en de audio-effecteigenschappen van meerdere audiostreams tegelijk te regelen.

### [Analyzer](#analyzer)[](#analyzer)

De [AudioAnalyzer](/docs/nl-nl/reference/engine/classes/AudioAnalyzer)  analyseert volume en frequentie-inhoud. Dit audio-effect is nuttig om informatie te verkrijgen om te begrijpen hoe je audio samenwerkt, zowel in volume als frequentie-inhoud.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
