<!-- Source: https://create.roblox.com/docs/nl-nl/resources/the-mystery-of-duvall-drive/design-dark-soundscapes -->

Ontwerp donkere geluidslandschappen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)
4. /
5. [Het mysterie van Duvall Drive](/docs/nl-nl/resources/the-mystery-of-duvall-drive)

# Ontwerp donkere geluidslandschappen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Om ervoor te zorgen dat The Mystery of Duvall Drive authentiek en geloofwaardig aanvoelt, hebben we ervoor gezorgd dat de ambiance op elke fase van de ontwikkeling koning was. We hebben gescripte audio-evenementen, muziek, karaktersounds en puntgeluid opgenomen om onze "het gras is altijd groener" benadering te ondersteunen, wat betekent dat we altijd wilden dat er een intrigerender geluid in de verte was, ongeacht waar de speler zich in het huis bevond, zodat ze elke kamer verder wilden onderzoeken. Deze geluiden varieerden van een radio die muziek speelde in een slaapkamer, de keuken die druppelde, regen die op het dak van de zolder viel, tot de oscillerende rituele orb in het midden van het huis.

Geluidontwerp voor een spel met horror-thema's is een evenwichtsoefening tussen het integreren van zowel realistische als abstracte audio. Terwijl realistische audio een gevoel van onderdompeling en authenticiteit aan de wereld biedt, trekt abstracte audio de aandacht van de speler naar de anderewereldse elementen die het verhaal vooruit duwen. Beide audiotypen hebben afzonderlijk hun sterke punten, maar samen kunnen ze een donker geluidslandschap creëren dat authentiek, geloofwaardig en angstaanjagend aanvoelt. In deze sectie laten we je zien hoe en waarom we volumetrische audio en geneste [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  mixing hebben gebruikt om ons donkere geluidslandschap in balans te brengen en leven te brengen in onze 3D-ruimte.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/overview.png)

## [Volumetrische audio](#volumetrische-audio)[](#volumetrische-audio)

[Volumetrische audio](/docs/nl-nl/sound/objects#volumetrisch)  is de meest realistische audio-optie in Studio voor hoe mensen geluid waarnemen, afhankelijk van de afstand tot hun oren. Dit type audio stelt je in staat om een [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object op een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  te plaatsen, en vervolgens die [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  te gebruiken om een heel gebied te dekken waar je wilt dat die audio wordt afgespeeld. Het is zeer nuttig voor grote objecten die geluid maken, zoals watervallen, voertuigen en grote steden. Wanneer een speler zich binnen een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  bevindt die een kind [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object heeft met volumetrische audio ingeschakeld, speelt de audio rondom de speler, vergelijkbaar met muziek in hoofdtelefoons die op hetzelfde volume in elke luidspreker speelt. Wanneer de gebruiker het object verlaat, neemt het volume geleidelijk af en wordt het meer directioneel per luidspreker, waarbij het geluid rondom het hoofd van de gebruiker beweegt wanneer hun luisteraar draait. Dit betekent dat als het geluid naar links van je luisteraar wordt uitgezonden, het geluid luider speelt in je linkerluidspreker dan in je rechterluidspreker.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/audio-volume.png) Voorbeeld van een audiovolume dat intermitterende creepy menselijke fluisteringen afspeelt. Dit versterkt een donker geluidslandschap en zet de toon voor de sfeer binnen het huis.

De ervaring van een speler met audio is niet alleen afhankelijk van welke geluiden ze kunnen horen, maar ook uit welke richting  die geluiden komen. In de echte wereld klinkt iemand die je naam van de andere kant van een veld roept veel meer directioneel dan iets als het zachte gezoem van de airconditioning in een kamer of de galm in een grot. Dit komt omdat geluidsgolven stuiteren, en wanneer ze vaste objecten zoals muren, asfalt en bomen raken, verstrooien ze en weerkaatsen ze terug naar je oren vanuit verschillende richtingen. In feite kunnen geluidsgolven zelfs om objecten zoals je eigen hoofd heen buigen!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/volumetric-audio-immersive.png) In dit gedeelte van het huis stelt volumetrische audio je in staat om jezelf onder te dompelen in de geluiden van regen die tegen nabijgelegen ramen slaat, het knisperen van een open haard, en een zacht deuntje dat door een oude radio in de buurt wordt afgespeeld.

Voor volumetrische audio was je beperkt tot het laten uitkomen van je audio vanuit een [enkele punt in de ruimte](/docs/nl-nl/sound/objects#puntbron) , of het [afspelen in beide hoofdtelefoons zoals muziek](/docs/nl-nl/sound/objects#achtergrondaudio) . Omdat we onze audio zo realistisch mogelijk wilden maken terwijl we een breed scala aan geluidssoorten vertegenwoordigden, zouden geen van deze eerdere implementaties voldoende zijn geweest om de meeslepende wereld te creëren die we in dit spel wilden vastleggen. Als gevolg hiervan hebben we volumetrische audio-emitters gebruikt voor de overgrote meerderheid van onze geluidseffecten, inclusief de regen buiten, de interieurgeluiden van kamers, de corrupte zone-ambiance, televisie-statisch, en regen die op verschillende oppervlakken valt. Als we volumetrische audio in het project zouden uitschakelen, zouden al deze geluiden samenvallen tot een enkel uitzendpunt in hun zwaartepunt, en het hele geluidslandschap zou verschuiven tussen de oren van de speler telkens wanneer ze hun camera draaien. Dit zou de hele ruimte onrealistisch en digitaal laten aanvoelen, en de beweging van het geluid zou behoorlijk schokkend en ongewenst zijn voor de speler.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/exterior-audio-hierarchy.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/sound-emitters-hierarchy.png)

Enkele voorbeelden van hoe we volumetrische audio hebben gebruikt om onze buitenambiance te creëren, evenals regen die tegen verschillende materialen in de achtertuin botst.

Volumetrische audio-emitters stelden ons in staat om de directionele eigenschappen van ons geluidslandschap te beheersen om een echt gevoel van beweging door de ruimte te geven. Omdat hun invloed over een groter gebied is verspreid en de audio zich natuurlijk naar beide oren verspreidt, geven ze de algehele geluidsbedekking van het spel, of constante gezoem van audio-activiteit, een veel voorspelbaarder en stabieler volume-niveau. Dit voorkomt dat het spel stil is wanneer het personage van de speler niets doet, en het maakt het spel realistisch, aangezien er in het echte leven zeer weinig ruimtes volledig vrij zijn van geluid!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/volumetric-audio-emitter-greenhouse.png) We hebben een volumetrische audio-emitter op de kas geplaatst om meeslepende ambientgeluiden van de regendruppels die op het glazen dak vallen en door de kamer weerklinken toe te voegen.

Bij het toevoegen van detail aan ons buiten geluidslandschap was het belangrijk om de regen levendig te laten aanvoelen in plaats van een eenvoudig herhalend regen-geluidseffect. Een van de manieren waarop we dit hebben bereikt, was door regengeluiden aan verschillende objecten toe te voegen, zodat je de impact van de storm op je directe omgeving kon horen. In dit project zijn er generieke buiten regengeluiden, maar ook volumetrische audio-emitters voor regen die op objecten zoals ramen, plastic en daken valt. Bijvoorbeeld, we hebben een volumetrische audio-emitter aan een auto toegevoegd via het volgende proces om spelers de indruk te geven dat regendruppels de hele oppervlakte van de auto beïnvloeden in plaats van slechts een enkel punt op de motorkap van de auto:

1.

In het Explorer  venster selecteerden we SoundService .

2.

In het Properties  venster navigeerden we naar de VolumetricAudio  eigenschap en stelden deze in op Enabled . Dit schakelde het volumetrische geluidsgedrag voor het hele project in.

3.

In de viewport maakten we een nieuwe [Part](/docs/nl-nl/reference/engine/classes/Part)  die overeenkwam met de grootte van de auto. Dit definieerde het hele gebied waarvan we wilden dat het geluid zou uitkomen.

4.

In het Properties  venster stelden we de volgende eigenschappen voor het deel in om ervoor te zorgen dat ons deel niet door de grond viel, niet met het automodel botste, of de zichtbaarheid van de auto belemmerde:

-

[Part.Anchored](/docs/nl-nl/reference/engine/classes/Part#Anchored)  = Enabled

-

[Part.CanCollide](/docs/nl-nl/reference/engine/classes/Part#CanCollide)  = Disabled

-

[Part.Transparency](/docs/nl-nl/reference/engine/classes/Part#Transparency)  = 1

5.

We voegden vervolgens een [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object toe aan het onzichtbare deel en stelden de volgende eigenschappen voor het [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object in, zodat het regengeluid begon te spelen wanneer spelers in het spel zouden laden, continu herhaalde, en hoorbaar werd wanneer een speler 60 studs weg was/bereikte zijn maximale volume op 15 studs afstand:

-

[Sound.SoundId](/docs/nl-nl/reference/engine/classes/Sound#SoundId)  = 9178663282

-

[Sound.Playing](/docs/nl-nl/reference/engine/classes/Sound#Playing)  = Enabled

-

[Sound.Looped](/docs/nl-nl/reference/engine/classes/Sound#Looped)  = Enabled

-

[Sound.RollOffMaxDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMaxDistance)  = 60

-

[Sound.RollOffMinDistance](/docs/nl-nl/reference/engine/classes/Sound#RollOffMinDistance)  = 15

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/car-part-volume.png) De randen van ons deel zijn in het wit te zien die de auto omringen.

Dit proces stelde het geluid in staat om van het hele oppervlak van het onzichtbare deel uit te komen. Als de speler zich binnen het deel bevond, zou de regengeluid rondom het hoofd van de speler spelen. Hoe groter je je eigen volumetrische audio-emitters maakt, hoe meer spreiding en gebied het volumetrische geluid zal dekken, dus experimenteer met verschillende maten en vormen voor je emitter om het geluidslandschap te krijgen dat je wilt voor je eigen spellen!

## [Geneste SoundGroup-mixing](#geneste-soundgroup-mixing)[](#geneste-soundgroup-mixing)

Als mensen denken we graag dat we geweldige multitaskers zijn, maar in werkelijkheid is het vrij moeilijk voor ons om ons op meer dan 2 dingen tegelijk te concentreren, vooral als het gaat om het luisteren naar meerdere audio-bronnen! In The Mystery Of Duvall Drive kunnen er op elk moment een dozijn geluiden spelen, zoals ambiance, muziek, voetstappen, regen of UI-meldingen, maar we hadden een manier nodig om ervoor te zorgen dat het niet voelde alsof ze allemaal om je aandacht streden. Om deze reden besloten we om [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  in kind/ouderrelaties te nestelen, zodat we een audiomix konden creëren om zowel de organisatie als de consistentie van het geluidsontwerp van het project te waarborgen.

[Nesten van SoundGroups](/docs/nl-nl/sound/groups#nest-soundgroups)  is een nieuwe functie die je in staat stelt om [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  samen te organiseren in betekenisvolle categorieën onder een mixboom voor verdere audio-functionaliteit, zoals het fijn afstemmen van het volume van veel audio-bronnen tegelijk, of het toepassen van gemeenschappelijke audio-effecten tegen lagere CPU-kosten. Aangezien we een zeer progressiegerichte benadering van de mix in dit project hebben genomen, wilden we geluiden die direct bijdragen aan de voortgang van de speler in de puzzels (puzzel- en sleutelobjectinteractie-audio) prioriteit geven boven geluiden die niet bijdragen aan hun voortgang (wind, regen, voetstappen, atmosfeer audio). Door kind [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  in ouder [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  van verschillende prioriteitsniveaus te nestelen, konden we vervolgens een [CompressorSoundEffect](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect)  toevoegen die het volume van laagprioritaire [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  in realtime zou verlagen telkens wanneer audio van hoogprioritaire [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  begon te spelen. Dit proces wordt [ducking](/docs/nl-nl/sound/groups#ducking)  genoemd.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/main-audio-mixer.png) Een samengevouwen weergave van onze hoofd audio-mixer voor dit spel.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/designing-dark-soundscapes/compressorsoundeffect-properties.png) Het Properties-venster voor de CompressorSoundEffect die we aan de laagprioritaire SoundGroup hebben toegevoegd.

De [CompressorSoundEffect](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect)  heeft vijf hoofd eigenschappen die we moesten instellen om het volume van laagprioritaire audio te verlagen telkens wanneer hoogprioritaire audio werd afgespeeld:

| Eigenschap | | Beschrijving |
| --- | --- |
| [CompressorSoundEffect.Threshold](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect#Threshold) | | Hoe gevoelig de compressor is voor het inkomende signaal om het volume van een [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  te verlagen. Hoe lager het getal, hoe minder luid het hoogprioritaire geluid moet zijn om effect te hebben. |
| [CompressorSoundEffect.Ratio](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect#Ratio) | | Hoeveel je laagprioritaire geluiden wilt verlagen. Een hoger getal betekent in wezen meer volume ducking! |
| [CompressorSoundEffect.Attack](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect#Attack)  en [CompressorSoundEffect.Release](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect#Release) | | Hoe snel de volumevermindering in- en uitfadeert wanneer geactiveerd. Er zijn hier geen harde en snelle regels, stem ze af om bij je geluidslandschap te passen met je eigen oordeel en oren! |
| [CompressorSoundEffect.Sidechain](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect#Sidechain) | | Welke [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  we willen laten ducken van de laagprioritaire geluiden, aangezien we de compressor op de Laag  [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  hebben geplaatst. Dit is wat de magie laat gebeuren! |

Voor meer informatie over deze eigenschappen en het hele proces van het prioriteren van audio van verschillende [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup) , zie [Nesten van SoundGroups](/docs/nl-nl/sound/groups#nest-soundgroups)  en [Ducking](/docs/nl-nl/sound/groups#ducking) .

[Vorige](/docs/nl-nl/resources/the-mystery-of-duvall-drive/develop-a-moving-world)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
