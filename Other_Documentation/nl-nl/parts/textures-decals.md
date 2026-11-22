<!-- Source: https://create.roblox.com/docs/nl-nl/parts/textures-decals -->

Texturen en decals | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Delen](/docs/nl-nl/parts)

# Texturen en decals

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een [Texture](/docs/nl-nl/reference/engine/classes/Texture)  is een afbeelding die je op elk vlak van een [deel](/docs/nl-nl/parts)  of [unie](/docs/nl-nl/parts/solid-modeling)  kunt plaatsen en die herhaalt  zowel horizontaal als verticaal op de grootte van het oppervlak. In tegenstelling tot een [Decal](/docs/nl-nl/reference/engine/classes/Decal) , is een afbeelding die uitrekt  om in het gebied van het oppervlak van een deel of unie te passen. Nadat je een [Texture](/docs/nl-nl/reference/engine/classes/Texture)  of [Decal](/docs/nl-nl/reference/engine/classes/Decal)  object aan een deel of unie hebt toegevoegd, kun je:

-

De textuur of decal [Color3](/docs/nl-nl/reference/engine/classes/Decal#Color3)  eigenschap wijzigen om een kleurverloop in te stellen met behulp van RGB-kleurcodes.

-

De textuur of decal [Transparency](/docs/nl-nl/reference/engine/classes/Decal#Transparency)  eigenschap wijzigen naar een waarde tussen de standaard van 0  (volledig zichtbaar) en 1  (onzichtbaar).

-

Voor een textuur, stel de [schaal](#schaal-texturen)  en [offset](#offset-texturen)  in.

![Een voorbeeld van een textuurafbeelding van een lichtblauwe hexagoon op een donkerblauwe achtergrond.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Decal-Texture-Sample-2.png) Textuurafbeelding

![Dezelfde textuur herhaald acht keer op een blokdeel.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-On-Surface.jpg) Textuur toegepast op een deel (herhalend)

![Een voorbeeld van een decalafbeelding van een lichtpaarse hexagoon op een donkerpaarse achtergrond.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Decal-Texture-Sample-1.png) Decal afbeelding

![Dezelfde decal uitgerekt op een blokdeel.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Decal-On-Surface.jpg) Decal toegepast op een deel (uitgerekt)

## [Maak texturen of decals](#maak-texturen-of-decals)[](#maak-texturen-of-decals)

Om een textuur of decal te maken, moet je een [Texture](/docs/nl-nl/reference/engine/classes/Texture)  of [Decal](/docs/nl-nl/reference/engine/classes/Decal)  object aan een deel of unie toevoegen. Je kunt [afbeeldingen importeren](/docs/nl-nl/projects/assets/manager#asset-import)  voor texturen en decals naar Studio voor gebruik tussen games, en ze [distribueren](/docs/nl-nl/production/creator-store)  naar de [Creator Store](/docs/nl-nl/production/creator-store) . Zodra je de afbeelding importeert, wijst Studio een unieke asset-ID toe.

Elke textuur- of decalafbeelding die je maakt en importeert naar Roblox moet voldoen aan de [Gemeenschapsregels](https://en.help.roblox.com/hc/articles/203313410)  en de [Gebruiksvoorwaarden](https://en.help.roblox.com/hc/articles/115004647846) .

Om een textuur of decal aan een [deel](/docs/nl-nl/parts)  of [unie](/docs/nl-nl/parts/solid-modeling)  toe te voegen:

1.

Voeg in het [Explorer](/docs/nl-nl/studio/explorer)  venster een [Texture](/docs/nl-nl/reference/engine/classes/Texture)  of [Decal](/docs/nl-nl/reference/engine/classes/Decal)  toe aan het deel of de unie. Een lege textuur- of decalobject wordt weergegeven op het deel of de unie met een oranje omranding.

2.

Navigeer in het [Properties](/docs/nl-nl/studio/properties)  venster naar de [Face](/docs/nl-nl/reference/engine/classes/FaceInstance#Face)  eigenschap en kies een vlak ([Top](/docs/nl-nl/reference/engine/enums/NormalId) , [Bottom](/docs/nl-nl/reference/engine/enums/NormalId) , [Front](/docs/nl-nl/reference/engine/enums/NormalId) , [Back](/docs/nl-nl/reference/engine/enums/NormalId) , [Left](/docs/nl-nl/reference/engine/enums/NormalId) , of [Right](/docs/nl-nl/reference/engine/enums/NormalId) ).

-

OPTIONEEL

 Om te helpen bij het kiezen van het juiste vlak, klik met de rechtermuisknop op het deel/unie en selecteer Toon Oriëntatie Indicator . Dit toont een cirkel 🅕 , een blauwe lijn die aan de voorkant van het object is bevestigd, en een groene pijl die in de richting van de bovenkant van het object wijst.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Orientation-Indicator.jpg)

3.

Selecteer de [ColorMapContent](/docs/nl-nl/reference/engine/classes/Decal#ColorMapContent)  eigenschap en pas een afbeelding toe via een van de volgende methoden:

-

Selecteer een textuur of decal die je eerder hebt geüpload.

-

Voer een [asset-ID](/docs/nl-nl/projects/assets)  in het veld in.

4.

OPTIONEEL

 Stel een kleurverloop in door op het kleine vakje links van de [Color3](/docs/nl-nl/reference/engine/classes/Decal#Color3)  eigenschap te klikken of door een RGB-kleurcode in te voeren.

![Een close-up van de Color3 eigenschap met het kleine kleurvak gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Appearance-Color3-Picker.png)

![Een close-up van de Color3 eigenschap met de RGB-code gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Appearance-Color3-RGB-Entry.png)

![Een blokdeel met een herhalende blauwe hexagoon textuur op de bovenkant.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-On-Surface.jpg)[Color3](/docs/nl-nl/reference/engine/classes/Decal#Color3) : [255, 255, 255]

![Hetzelfde blokdeel met een herhalende hexagoon textuur op de bovenkant, maar de hexagons zijn roze tegen een donkerpaarse achtergrond.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-Color3-255-0-100.jpg)[Color3](/docs/nl-nl/reference/engine/classes/Decal#Color3) : [255, 0, 100]

5.

OPTIONEEL

 Stel de [Transparency](/docs/nl-nl/reference/engine/classes/Decal#Transparency)  eigenschap in op een waarde tussen de standaard van 0  (volledig zichtbaar) en 1  (onzichtbaar).

![Een blokdeel met een herhalende blauwe hexagoon textuur op de bovenkant.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-On-Surface.jpg)[Transparency](/docs/nl-nl/reference/engine/classes/Decal#Transparency) : 0

![Hetzelfde blokdeel met een herhalende hexagoon textuur op de bovenkant, maar de hexagons zijn semi-transparant.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-Transparency-0.4.jpg)[Transparency](/docs/nl-nl/reference/engine/classes/Decal#Transparency) : 0.6

## [Pas texturen aan](#pas-texturen-aan)[](#pas-texturen-aan)

In tegenstelling tot decals bieden texturen  verdere functionaliteit om de bronafbeelding te schalen, te offsetten en te animeren.

### [Schaal texturen](#schaal-texturen)[](#schaal-texturen)

De grootte van het deel heeft geen invloed op de textuur. In plaats daarvan verhoogt of verlaagt het schalen van een deel alleen het aantal keren dat de textuur herhaalt.

De [StudsPerTileU](/docs/nl-nl/reference/engine/classes/Texture#StudsPerTileU)  en [StudsPerTileV](/docs/nl-nl/reference/engine/classes/Texture#StudsPerTileV)  eigenschappen bepalen de grootte van elke "tegel" in studs. [StudsPerTileU](/docs/nl-nl/reference/engine/classes/Texture#StudsPerTileU)  bepaalt de horizontale grootte van de textuur, terwijl [StudsPerTileV](/docs/nl-nl/reference/engine/classes/Texture#StudsPerTileV)  de verticale grootte van de textuur bepaalt.

StudsPerTileU & StudsPerTileV = 2 StudsPerTileU & StudsPerTileV = 4

![Textuur op een oppervlak van 8x6 studs met een grootte van elke tegel in 2x2.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-Sample-Scale-1.png)

### [Offset texturen](#offset-texturen)[](#offset-texturen)

Als je meer controle wilt over de positie van een textuur, offset je de textuur door de [OffsetStudsU](/docs/nl-nl/reference/engine/classes/Texture#OffsetStudsU)  (horizontaal) en [OffsetStudsV](/docs/nl-nl/reference/engine/classes/Texture#OffsetStudsV)  (verticaal) eigenschappen aan te passen. Dit is ook nuttig voor [animatie](#animeer-texturen) .

OffsetStudsU & OffsetStudsV = 0 OffsetStudsU & OffsetStudsV = 0.5

![2x2 textuur op een oppervlak van 8x6 studs zonder offset.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-Sample-Offset-1.png)

### [Animeer texturen](#animeer-texturen)[](#animeer-texturen)

Met [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  kun je textuureigenschappen zoals [OffsetStudsU](/docs/nl-nl/reference/engine/classes/Texture#OffsetStudsU)  en [StudsPerTileV](/docs/nl-nl/reference/engine/classes/Texture#StudsPerTileV)  tweenen om geanimeerde oppervlakken te bereiken. Als je bijvoorbeeld twee misttexturen op één container toepast en ze animeert met het volgende script, kun je de uitstraling van een gelaagde bewegende mist bereiken.

Twee geanimeerde texturen nabij de vloer om een bewegend misteffect te simuleren

```

local TweenService = game:GetService("TweenService")

local texture1 = script.Parent.Texture1

local texture2 = script.Parent.Texture2

local tweenInfo1 = TweenInfo.new(8, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut, -1)

local tween1 = TweenService:Create(texture1, tweenInfo1, {OffsetStudsV=50})

local tweenInfo2 = TweenInfo.new(7, Enum.EasingStyle.Sine, Enum.EasingDirection.InOut, -1, true)

local tween2 = TweenService:Create(texture2, tweenInfo2, {OffsetStudsU=50, StudsPerTileU=55, StudsPerTileV=45})

tween1:Play()

tween2:Play()

```

## [Textuurstreaming](#textuurstreaming)[](#textuurstreaming)

Textuurstreaming  laadt dynamisch texturen op basis van afstand en camerazicht, waardoor je texturen vrijer kunt gebruiken zonder je zorgen te maken over schaling op verschillende apparaten. De engine laadt eerst texturen van basiskwaliteit, in volgorde van belangrijkheid, en verhoogt vervolgens geleidelijk de kwaliteit van elke textuur tot de beschikbare geheugen op het apparaat. Textuurstreaming is automatisch ingeschakeld, zodat je geen actie hoeft te ondernemen om er voordeel uit te halen.

![Een visualisatie die een game toont met en zonder textuurstreaming.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/texture-streaming.webp) Dezelfde scène met en zonder textuurstreaming

### [Voordelen](#voordelen)[](#voordelen)

-

Snellere waargenomen laadtijden en kleinere downloads : Texturen verschijnen bijna onmiddellijk in een basiskwaliteit, en de engine downloadt alleen de details die het nodig heeft, waarbij het zowel tijdens de overdracht als op de lokale schijfcache wordt gecomprimeerd.

-

Hogere kwaliteit waar het belangrijk is : De engine schat continu hoe belangrijk elk object is, bijvoorbeeld door hoeveel schermruimte het in beslag neemt, en gebruikt het geheugenbudget voor die texturen zodat de meest prominente objecten de hoogste details krijgen.

-

Minder crashes door geheugenproblemen : Omdat de engine binnen een geheugenbudget blijft en de textuurkwaliteit kan verlagen wanneer het geheugen laag is, is de kans veel kleiner dat spelers crashen door pieken in textuurgeheugen.

Textuurstreaming werkt met [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  (gekleed en ongekleed), [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) , [Texture](/docs/nl-nl/reference/engine/classes/Texture) , [Decal](/docs/nl-nl/reference/engine/classes/Decal) , [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant) , [Beam](/docs/nl-nl/reference/engine/classes/Beam) , [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter) , en de basismaterialen die zijn toegepast op [PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation)  en [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  instanties.

### [Beste praktijken](#beste-praktijken)[](#beste-praktijken)

-

Geef de voorkeur aan unieke, individuele texturen boven textuuratlassen, tenzij de atlas is toegepast op batchbare delen; het aanvragen van een hoge resolutie voor één textuur in een atlas streamt de hele atlas in die resolutie.

-

Gebruik bijna uniforme texeldichtheid in je UV-gemapte meshes, zodat de engine de beste resolutie voor elke textuur kan selecteren.

-

Blijf textuurgeheugen zorgvuldig beheren voor instantietypen die textuurstreaming nog niet ondersteunen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
