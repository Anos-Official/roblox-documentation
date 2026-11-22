<!-- Source: https://create.roblox.com/docs/nl-nl/sound/groups -->

Geluidsgroepen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Meer informatie](/docs/nl-nl/learn)

# Geluidsgroepen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup) -objecten worden nu afgeraden ten gunste van de robuustere functionaliteit van audio-objecten. Voor meer informatie, zie [Audio-objecten](/docs/nl-nl/audio/objects) .

Een [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  is een audio-mixer  die meerdere audio-objecten groepeert, zoals [Sound](/docs/nl-nl/reference/engine/classes/Sound) -objecten of aanvullende [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup) , zodat je de volumeregeling en dynamische effecteigenschappen van meerdere audiosignalen tegelijk kunt regelen. Nuttige toepassingen zijn onder andere:

-

[Audio toewijzen](#audio-objecten-toewijzen-aan-geluidsgroepen)  aan SoundEffects  en BackgroundMusic  geluidsgroepen, zodat je het mastervolume van elke groep kunt aanpassen voor optimale audiobalans.

-

[Geluidsgroepen nesten](#geluidsgroepen-nesten)  in betekenisvolle categorieën onder een mixboom.

-

Groeperen van alle geluiden die een specifiek [dynamisch effect](/docs/nl-nl/sound/dynamic-effects)  nodig hebben. Bijvoorbeeld, je kunt alle geluiden binnen een grot groeperen in een Cave  geluidsgroep en vervolgens een [ReverbSoundEffect](/docs/nl-nl/reference/engine/classes/ReverbSoundEffect)  toepassen om de geluiden te simuleren die weerkaatsen tegen de omgeving van de grot.

Bij het maken van [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  is het het beste om ze allemaal op één locatie te houden voor organisatorische doeleinden terwijl je audio binnen je spel blijft toevoegen en bewerken. Het volgende voorbeeld slaat de nieuwe [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  op onder [SoundService](/docs/nl-nl/reference/engine/classes/SoundService) , aangezien deze service bepaalt hoe [Sound](/docs/nl-nl/reference/engine/classes/Sound) -objecten in spellen worden afgespeeld.

## [Geluidsgroepen maken](#geluidsgroepen-maken)[](#geluidsgroepen-maken)

Om een [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  te maken:

1.

In het Explorer -venster, beweeg je de muis boven [SoundService](/docs/nl-nl/reference/engine/classes/SoundService)  en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu een [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  in.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/SoundService-SoundGroup.png)

3.

Drie keer klikken op de nieuwe geluidsgroep en hernoem deze volgens het doel, zoals SoundEffects  of BackgroundMusic .

## [Audio-objecten toewijzen aan geluidsgroepen](#audio-objecten-toewijzen-aan-geluidsgroepen)[](#audio-objecten-toewijzen-aan-geluidsgroepen)

[SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  hebben niet het typische ouder-kind gedrag van andere vormen van objectgroepering zoals [Models](/docs/nl-nl/reference/engine/classes/Model)  en [Folders](/docs/nl-nl/reference/engine/classes/Folder) . In plaats daarvan moet je elk [Sound](/docs/nl-nl/reference/engine/classes/Sound) -object toewijzen  aan het toepasselijke [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup) -object, ongeacht de locatie van elk object in de hiërarchie van de werkruimte, omdat waar je het [Sound](/docs/nl-nl/reference/engine/classes/Sound) -object plaatst verandert waar audio vandaan komt, niet het [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup) -object zelf. Voor meer informatie, zie [geluidobjecten](/docs/nl-nl/sound/objects) .

Om een [Sound](/docs/nl-nl/reference/engine/classes/Sound) -object aan een [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  toe te wijzen:

1.

In het Explorer -venster, selecteer een geluidobject.

2.

In het Properties -venster, klik op het SoundGroup -eigenschapveld. Je cursor verandert.

3.

In het Explorer -venster, klik op het geluidsgroepobject waaraan je je geluidobject wilt toewijzen. De SoundGroup -eigenschap van het geluidobject wordt dienovereenkomstig bijgewerkt.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Sound-SoundGroup.png)

## [Geluidsgroepen nesten](#geluidsgroepen-nesten)[](#geluidsgroepen-nesten)

Je kunt [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  samenvoegen in betekenisvolle categorieën onder een mixboom voor organisatie- en scriptdoeleinden. Wanneer je de ouder-kindrelaties in je mix plant, overweeg dan de verschillende geluidscategorieën in je spel en hoe belangrijk ze moeten zijn voor de luisteraar. Bijvoorbeeld, geluiden van spelersvaardigheden zijn waarschijnlijk veel belangrijker voor de gameplay dan omgevingsgeluiden. Als je ze in aparte ouder [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  groepeert, kun je eenvoudig toegang krijgen tot en [hun volumenniveaus aanpassen](#volume-aanpassen)  terwijl je meer [Sound](/docs/nl-nl/reference/engine/classes/Sound) -objecten aan je spel toevoegt.

Om [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  te nesten:

1.

In het Explorer -venster, klik en sleep een geluidsgroep over de geluidsgroep waaronder je deze wilt nesten. De naam van de geluidsgroep wordt doorschijnend en je cursor verandert in een plusicoon.

2.

Laat de geluidsgroep vallen. Het wordt weergegeven als een kind van de geluidsgroep waaronder je het genest hebt.

## [Volume aanpassen](#volume-aanpassen)[](#volume-aanpassen)

Er zijn twee hoofdmanieren om over het volume van een geluid na te denken: hoe luid het geluid op zichzelf is, en hoe luid het is in verhouding tot andere geluiden. Bijvoorbeeld, een waterval klinkt luid wanneer je deze alleen afspeelt, maar wanneer je deze vergelijkt met andere geluidseffecten zoals screechende banden, klinkt het waarschijnlijk veel stiller. Om ervoor te zorgen dat elk geluid op het juiste volume voor je spel wordt afgespeeld, kun je ofwel [vermenigvuldigers toevoegen](#vermenigvuldigers-toevoegen)  aan [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup) , of audio van de ene [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  prioriteit geven boven een andere door middel van [ducking](#ducking) .

### [Vermenigvuldigers toevoegen](#vermenigvuldigers-toevoegen)[](#vermenigvuldigers-toevoegen)

De [Volume](/docs/nl-nl/reference/engine/classes/SoundGroup#Volume) -eigenschap van een [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  stelt je in staat om een volumevermenigvuldiger  tussen 0  en 10  toe te passen op elk van zijn kindaudio-objecten terwijl ze hun relatieve volumes behouden. Dit betekent dat als een [Sound](/docs/nl-nl/reference/engine/classes/Sound) -object een volume van 0.5  heeft en je het als kind toevoegt aan een [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  die een volumevermenigvuldiger van 0.5  heeft, het effectieve volume van het [Sound](/docs/nl-nl/reference/engine/classes/Sound) -object 0.25  is.

Deze eigenschap is nuttig wanneer je volumeveranderingen wilt testen voor verschillende [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  zonder het volume van elk [Sound](/docs/nl-nl/reference/engine/classes/Sound) -object handmatig te hoeven wijzigen. Bijvoorbeeld, als je wilt controleren hoe het klinkt om het volume van alle muziek in je spel te verhogen, kun je een Music  [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  maken voor elk muzikaal [Sound](/docs/nl-nl/reference/engine/classes/Sound) -object of [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup) , en vervolgens een volumevermenigvuldiger van 2  toepassen.

### [Ducking](#ducking)[](#ducking)

Je kunt audio van de ene [SoundGroup](/docs/nl-nl/reference/engine/classes/SoundGroup)  prioriteit geven boven een andere via de [CompressorSoundEffect](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect) . Dit dynamische effect stelt je in staat om te ducken , of het volume te verlagen, van [Sound](/docs/nl-nl/reference/engine/classes/Sound) -objecten in lage-prioriteit [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  telkens wanneer [Sound](/docs/nl-nl/reference/engine/classes/Sound) -objecten in hoge-prioriteit [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  beginnen te spelen. Dit stelt de luisteraar in staat om zich te concentreren op de specifieke audio waar je wilt dat ze op letten, zonder de audio van lage-prioriteit geluiden volledig abrupt te onderbreken. Wanneer de hoge-prioriteit audio is afgelopen, keert de lage-prioriteit audio terug naar zijn oorspronkelijke volume, waardoor de luisteraar ondergedompeld blijft in je spel.

De geluiden die je kiest om te ducken, hangen af van de behoeften van je specifieke spel. Bijvoorbeeld, een spel kan profiteren van het verlagen van het volume van achtergrondmuziek telkens wanneer een GUI-melding wordt afgespeeld, terwijl andere kunnen profiteren van het verlagen van het volume van GUI-meldingen telkens wanneer dialoog wordt afgespeeld. De volgende referentiemixboom prioriteert [Sound](/docs/nl-nl/reference/engine/classes/Sound) -objecten in de hoge-prioriteit GUI Notifications  en Weapons  [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  terwijl het de-prioriteit geeft aan [Sound](/docs/nl-nl/reference/engine/classes/Sound) -objecten in lage-prioriteit 3D  en 2D Ambience  [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup) .

 ![](https://prod.docsiteassets.roblox.com/assets/audio/sound-groups/Mix-Tree.png)

De [CompressorSoundEffect](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect)  heeft vier hoofd eigenschappen die je moet instellen om audio te ducken telkens wanneer je hoge-prioriteit audio afspeelt:

| Eigenschap | | Beschrijving |
| --- | --- |
| [Threshold](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect#Threshold) | | Het dB-niveau dat Studio toepast voor ducking. Je kunt deze eigenschap instellen op elke waarde tussen -80  (volledige compressie) en 0  (volledig volume). |
| [Attack](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect#Attack) | | De snelheid waarmee je wilt dat audio duckt. Je kunt deze eigenschap instellen op elke waarde tussen 0.001  en 1  seconde. |
| [Release](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect#Release) | | De snelheid waarmee je wilt dat de audio stopt met ducken. Je kunt deze eigenschap instellen op elke waarde tussen 0.001  en 1  seconde. |
| [Ratio](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect#Ratio) | | De verhouding van hoeveel ducking je wilt dat er plaatsvindt tussen het audio-object dat Studio prioriteit geeft en het audio-object dat duckt. Je kunt deze eigenschap instellen op elke waarde tussen 1  (geen compressie) en 50  (vijftig keer de compressie). |

De waarden van elk van deze eigenschappen zijn sterk afhankelijk van je specifieke audio. Elke bronaudio heeft een ander volume, en je moet misschien slechts een minimale hoeveelheid ducken om ervoor te zorgen dat je hoge-prioriteit audio nadruk krijgt in je spel.

Om [SoundGroups](/docs/nl-nl/reference/engine/classes/SoundGroup)  prioriteit te geven via de [CompressorSoundEffect](/docs/nl-nl/reference/engine/classes/CompressorSoundEffect) :

1.

In het Explorer -venster, navigeer naar de SoundGroup die je wilt ducken en voeg een CompressorSoundEffect toe.

1.

Beweeg de muis boven de SoundGroup  en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu een CompressorSoundEffect  in.

2.

Selecteer de CompressorSoundEffect , en navigeer naar het Properties -venster.

3.

Selecteer de SideChain -eigenschap. Je cursor verandert.

4.

Selecteer het Sound  of SoundGroup -object dat je wilt prioriteren wanneer de compressor wordt toegepast. De SideChain -eigenschap wordt dienovereenkomstig bijgewerkt.

5.

Vul in het Threshold property -veld het dB-niveau in waarop je wilt dat het ducken begint.

6.

Vul in het Attack -eigenschapveld in hoe snel je wilt dat audio duckt.

7.

Vul in het Release -eigenschapveld in hoe snel je wilt dat de audio stopt met ducken.

8.

Vul in het Ratio -eigenschapveld in de verhouding in van hoeveel compressie je wilt dat er plaatsvindt tussen het audio-object dat duckt en het audio-object dat Studio prioriteit geeft.

9.

OPTIONAL

 Speel je spel om te zien of de audio correct klinkt. Zo niet, pas dan de eigenschappen van de CompressorSoundEffect  dienovereenkomstig aan.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
