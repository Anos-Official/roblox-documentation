<!-- Source: https://create.roblox.com/docs/nl-nl/sound/dynamic-effects -->

Dynamische effecten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Meer informatie](/docs/nl-nl/learn)

# Dynamische effecten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Er is een nieuwere set audio-effecten die meer controle bieden en robuuste gebruiksscenario's aanpakken. Voor meer informatie, zie [Audio-effecten](/docs/nl-nl/audio/effects) .

Dynamische effecten passen de audio van individuele [Sound](/docs/nl-nl/reference/engine/classes/Sound)  objecten of een hele [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  aan of verbeteren deze. Je kunt deze effecten toepassen om je audio meeslepender te maken binnen je game, zoals het gebruik van [ReverbSoundEffect](/docs/nl-nl/reference/engine/classes/ReverbSoundEffect)  in grote kamers om ze massief te laten aanvoelen.

## [Dynamische effecten toepassen](#dynamische-effecten-toepassen)[](#dynamische-effecten-toepassen)

Elk dynamisch effect dat je toepast heeft extra eigenschappen die je kunt aanpassen totdat je het gewenste geluid hebt bereikt. Voor meer informatie over deze eigenschappen, zie de API-pagina van elk dynamisch effect.

Om een dynamisch effect toe te passen:

1.

In het Explorer -venster, voeg een nieuw dynamisch effect toe aan een [Sound](/docs/nl-nl/reference/engine/classes/Sound)  of [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  object.

1.

Beweeg de muis over het object en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu een dynamisch effect .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/SoundService-SoundGroup-ReverbSoundEffect.png)

2.

OPTIONEEL

 In het Eigenschappen -venster, selecteer het nieuwe dynamische effect en pas de eigenschappen aan.

 ![](https://prod.docsiteassets.roblox.com/assets/audio/sound-groups/Dynamic-Effect-Properties.png)

## [Typen](#typen)[](#typen)

### [Equalizer](#equalizer)[](#equalizer)

De [EqualizerSoundEffect](/docs/nl-nl/reference/engine/classes/EqualizerSoundEffect)  stelt je in staat om de volume van verschillende frequentiebereiken te regelen. Dit dynamische effect is nuttig om bepaalde elementen van audio te benadrukken of te minimaliseren, zoals het dempen van alle audio in je game wanneer een speler onder water gaat.

|  | |  |
| --- | --- |
| Audio zonder effect | | Audio met equalizer |

### [Compressor](#compressor)[](#compressor)

De [CompressorSoundEffect](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect)  vermindert het dynamische bereik van audio door het volume van de hoogste delen van een bron te verlagen terwijl het algehele volume tegelijkertijd wordt verhoogd. Dit dynamische effect is nuttig om een consistent volume in te stellen zodat gebruikers het kunnen horen, zelfs als je audio opneemt terwijl je fluistert of luid spreekt. Je kunt dit dynamische effect ook gebruiken om geluiden van de ene [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  boven een andere te prioriteren via het proces van ducking. Voor meer informatie, zie [Ducking](/docs/nl-nl/sound/groups#ducking) .

|  | |  |
| Audio zonder effect | | Audio met compressor |

### [Reverb](#reverb)[](#reverb)

De [ReverbSoundEffect](/docs/nl-nl/reference/engine/classes/ReverbSoundEffect)  simuleert het effect van geluiden die van verschillende oppervlakken weerkaatsen. Dit dynamische effect is nuttig om realistischere reflecties van geluiden in binnenruimtes te simuleren, zoals het weerkaatsen van een basketbal in een gymzaal, of het afspelen van rockmuziek in een stadion.

|  | |  |
| Audio zonder effect | | Audio met reverb |

### [Chorus](#chorus)[](#chorus)

De [ChorusSoundEffect](/docs/nl-nl/reference/engine/classes/ChorusSoundEffect)  simuleert het effect van meerdere vocalen of instrumenten die gelijktijdig spelen door het originele geluid te nemen en kopieën met lichte variaties in toonhoogte te overlappen. Dit dynamische effect is nuttig om een robotachtige of futuristische kwaliteit aan je audio te simuleren.

|  | |  |
| Audio zonder effect | | Audio met chorus |

### [Distortion](#distortion)[](#distortion)

De [DistortionSoundEffect](/docs/nl-nl/reference/engine/classes/DistortionSoundEffect)  simuleert het effect dat zou optreden bij het overdrijven van oudere audioapparatuur. Dit dynamische effect veroorzaakt clipping in het geluid en voegt een algemene "fuzziness" toe, wat nuttig is om intensiteit en karakter aan muziekinstrumenten toe te voegen.

|  | |  |
| Audio zonder effect | | Audio met distortion |

### [Echo](#echo)[](#echo)

De [EchoSoundEffect](/docs/nl-nl/reference/engine/classes/EchoSoundEffect)  zorgt ervoor dat een geluid met een vertraging herhaald wordt met afnemend volume, wat het echte effect van een echo simuleert die weerkaatst van harde oppervlakken, zoals muren en grotten.

|  | |  |
| Audio zonder effect | | Audio met echo |

### [Flange](#flange)[](#flange)

De [FlangeSoundEffect](/docs/nl-nl/reference/engine/classes/FlangeSoundEffect)  creëert een veeg- of suizend effect door het originele audiosignaal te kopiëren en het iets verschoven en gemoduleerd bovenop het origineel af te spelen. Dit dynamische effect is nuttig om een vreemde, andere wereld digitale kwaliteit aan je audio toe te voegen. Je kunt het bijvoorbeeld gebruiken op een opname van een airconditioner om het te laten klinken als het gebrom van een sci-fi ruimteschip.

|  | |  |
| Audio zonder effect | | Audio met flange |

### [Pitch Shift](#pitch-shift)[](#pitch-shift)

De [PitchShiftSoundEffect](/docs/nl-nl/reference/engine/classes/PitchShiftSoundEffect)  verhoogt of verlaagt de toonhoogte zonder de afspeelsnelheid te veranderen. Dit dynamische effect is nuttig om de schaal van je geluiden te veranderen. Je kunt het gebruiken om kleine geluiden groot te laten aanvoelen door ze naar beneden te stemmen of omgekeerd geluiden omhoog te stemmen om een explosiegeluid meer als een ballon te laten klinken.

|  | |  |
| Audio zonder effect | | Audio met pitch shift |

### [Tremolo](#tremolo)[](#tremolo)

De [TremoloSoundEffect](/docs/nl-nl/reference/engine/classes/TremoloSoundEffect)  creëert een trillend effect op een geluid door het volume omhoog en omlaag te variëren. Dit dynamische effect is nuttig om instrumentgeluiden te transformeren in een golvende, dromerige kwaliteit, of om zwellingen en dalingen in weergerelateerde audio te creëren.

|  | |  |
| Audio zonder effect | | Audio met tremolo |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
