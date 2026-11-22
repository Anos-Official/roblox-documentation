<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/core/building/apply-polished-assets -->

Pas gepolijste assets toe | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Pas gepolijste assets toe

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Gepolijste assets toepassen  is de laatste stap in het bouwen van je uiteindelijke omgeving, waarin je je grijsdoosplaatsvervangers vervangt door hoogwaardige gepolijste assets om te voldoen aan de esthetische doelen en ontwerpeisen van je spel. Dit spannende gedeelte van het curriculum is waar je ziet dat je wereld tot leven komt in een samenhangende omgeving die compleet en klaar voor publicatie is.

Met behulp van het [Island Jump - Final](https://www.roblox.com/games/14238807008/Island-Jump-Completed-Sample)  bestand als referentie, leert dit gedeelte van de tutorial je hoe je de Creator Store kunt gebruiken om een voorbeeld assetbibliotheek aan je project toe te voegen, je organisatie structuur voort te zetten om je nieuwe assets in betekenisvolle categorieën te sorteren, en de assetbibliotheek toe te passen op de 3D-ruimte.

Dit hoofdstuk omvat veel nauwkeurige positionering en eigenschapsconfiguratie. Elke sectie bevat een Bouw met Assistent  optie die assets plaatst met de exacte CFrame.Position  en Scale  waarden uit de tutorial, evenals een Pas je eigen  optie als je liever je eigen indeling maakt.

Assistent is bijzonder effectief bij dit soort repetitieve, deterministische opstellingen, waardoor het een nuttige manier is om het bouwproces te versnellen.

## [Verkrijg assetbibliotheek](#verkrijg-assetbibliotheek)[](#verkrijg-assetbibliotheek)

De Creator Store  is een tabblad van de Toolbox  dat je kunt gebruiken om alle assets te vinden die zijn gemaakt door Roblox en de Roblox-gemeenschap voor gebruik binnen je projecten, inclusief model-, afbeelding-, mesh-, audio-, plugin-, video- en lettertype-assets. Je kunt de Creator Store gebruiken om een individuele asset of assetbibliotheek rechtstreeks in een open spel toe te voegen.

Assetbibliotheken zijn verzamelingen van assets die je in een centrale locatie van je spel kunt plaatsen voor gemakkelijke toegang en hergebruik. De assetbibliotheek die je voor je project uit de Creator Store zult gebruiken, bevat zes 3D-assets, twee aangepaste [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  materialen, en de laatste deeleffecten van [Maak basis visuele effecten](/docs/nl-nl/tutorials/curriculums/core/building/create-basic-visual-effects) . De zes meshes zijn als volgt:

![Een mesh die een grasachtige, ronde platform is met beton rondom de randen.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Platform-A-Model.jpg) PlatformA

![Een mesh die een grasachtige, ronde platform is met rots eronder.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Platform-B-Model.jpg) PlatformB

![Een mesh die een glanzende gouden munt is met een Roblox-logo in het midden.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Coin-Mesh.jpg) Munt

![Een mesh die een grote rots zee-stapel is.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Sea-Stack-Mesh.jpg) ZeeStapMesh

![Een mesh die een grote rots zee-stapel is met een holle tunnel in het midden.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Sea-Stack-Cave-Mesh.jpg) ZeeStapGrotMesh

![Een mesh die een grote besneeuwde berg is.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Mountain-Mesh.jpg) BergMesh

Deze assets zijn ofwel enkele [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten of [Model](/docs/nl-nl/reference/engine/classes/Model)  objecten die meerdere meshes bevatten. Ze gebruiken aangepaste materialen en fysiek-gebaseerde rendering (PBR) texturen voor realistische schaduwen. Voor meer informatie, zie [Materialen - Aangepaste Materialen](/docs/nl-nl/parts/materials#aangepaste-materialen)  en [PBR Textures](/docs/nl-nl/art/modeling/surface-appearance) .

Om de assetbibliotheek uit je inventaris in je spel te krijgen:

1.

Open de [detailpagina](https://create.roblox.com/store/asset/14238769242)  van de assetbibliotheek in de Creator Store en klik op Model Krijgen  in de rechterbovenhoek. De bibliotheek is nu in je inventaris, en je kunt deze assets in elk project op het platform hergebruiken.

2.

Terug in Studio, klik op Toolbox  in de Home  werkbalk, schakel over naar het Inventaris  tabblad, en klik op de tegel Kern Bouwen en Scripting . De bibliotheek verschijnt in de viewport.

 ![Alle meshes uit de assetbibliotheek zweven boven het water. Sommige van de meshes missen hun texturen, zodat ze grijs verschijnen.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Asset-Library-Complete.jpg)

3.

Een paar meshes kunnen grijs lijken in plaats van getextureerd omdat hun materialen verwijzen naar [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  objecten die nog niet zijn geïnstalleerd. Om dit op te lossen, sleep Moss_Lumpy_A  en Moss_Strata_Noisy_A  uit de assetbibliotheek naar de MaterialService  container in de Explorer. De texturen klikken op hun plaats.

 ![Alle meshes uit de assetbibliotheek zweven boven het water, nu compleet met al hun texturen.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Asset-Library-Complete-With-Materials.jpg)

## [Ga door met de organisatie structuur](#ga-door-met-de-organisatie-structuur)[](#ga-door-met-de-organisatie-structuur)

Voordat je assets plaatst, breid de mappenstructuur uit die je begon in [Greybox een speelbare ruimte](/docs/nl-nl/tutorials/curriculums/core/building/greybox-a-playable-area) :

1.

In de Explorer , voeg twee nieuwe mappen toe binnen World  en noem ze Platforms  en Mountains .

2.

Binnen Platforms , voeg een [Model](/docs/nl-nl/reference/engine/classes/Model)  toe voor elk zee-stapel niveau en noem ze om overeen te komen met je grijsdoos niveaus. Bijvoorbeeld, het voorbeeldspel heeft 18 individuele modelcontainers voor elk platform in de omgeving.

 ![Het Explorer venster van Studio met al de niveau modelobjecten onder de Platforms map.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/ApplyAssetLibrary/Organization-Structure.jpg)

## [Pas assetbibliotheek toe](#pas-assetbibliotheek-toe)[](#pas-assetbibliotheek-toe)

Plaats nu de gepolijste assets over je grijsdoos. Elke sectie geeft je drie paden: Bouw met Assistent  (die het de Assistent toestaat om elke asset op de exacte coördinaten van het voorbeeld te plaatsen), Pas je eigen platforms toe  (waar je assets plaatst om je eigen aangepaste indeling te passen), en Recreëer het voorbeeld  (waar je ze met de hand plaatst op de exacte coördinaten van het voorbeeld).

De screenshots maken de placeholder assets semi-transparant zodat je je voortgang tussen de stappen kunt zien.

Grijsdoos Versie Gepolijste Assets

![Een versie van het voorbeeld Island Jump spel met grijsdoos geometrie.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Pre-Polished-Assets.jpg)

### [Platforms](#platforms)[](#platforms)

De bibliotheek bevat twee platform [Model](/docs/nl-nl/reference/engine/classes/Model)  objecten (elk gemaakt van twee [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  kinderen):

-

PlatformA  — Bevat een metalen cirkelvormige basis, gebruikt voor de eerste en laatste platforms.

-

PlatformB  — Bevat een basis terrein cap, gebruikt voor de tussenliggende platforms.

 ![Platform A en Platform B staan naast elkaar, en zijn gemarkeerd met hun platformtype.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Platform-Types.jpg)

Bouw met Assistent Pas je eigen platforms toe Recreëer het voorbeeld

Plaats alle platforms

```

Voor elke rij hieronder, kopieer de bijpassende mesh uit de assetbibliotheek genaamd "Kern Bouwen en Scripting" in Workspace > World > Platforms > <Parent Model> en stel zijn Origin.Position en Scale in.

PlatformA assets:

- Level_1: Origin.Position -30, 3, 9; Scale 2.2

- Level_2: Origin.Position -24, 11, 24; Scale 1.4

- Level_3a: Origin.Position 34, 31, 9.5; Scale 0.7

- Level_3b: Origin.Position 79, 31, 2; Scale 0.6

- Level_7: Origin.Position 402, 312, 79; Scale 1.1

PlatformB assets:

- Level_3c: Origin.Position 89, 31, 48; Scale 0.8

- Level_4a: Origin.Position 104, 65.5, 46.5; Scale 0.6

- Level_4b: Origin.Position 127, 66, 67.5; Scale 0.6

- Level_4b: Origin.Position 133.5, 164.5, 70.5; Scale 0.7

- Level_4c: Origin.Position 152, 65.5, 91; Scale 1

- Level_4d: Origin.Position 200, 66, 107; Scale 0.5

- Level_4e: Origin.Position 238.5, 66, 81; Scale 0.8

- Level_5a: Origin.Position 262, 120, 57.5; Scale 0.7

- Level_5b: Origin.Position 245, 122, 15; Scale 0.4

- Level_5c: Origin.Position 271, 122.5, -5.5; Scale 0.4

- Level_5d: Origin.Position 318, 121, -22; Scale 0.9

- Level_6a: Origin.Position 363, 201, -52.5; Scale 1.2

- Level_6b: Origin.Position 381, 201, 11; Scale 0.4

- Level_6c: Origin.Position 389, 201, 47; Scale 0.6

```

![Een weergave van het voorbeeld laser tag spel met alle platforms zichtbaar met de gepolijste assets.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/ApplyAssetLibrary/Platforms-5.jpg)

### [Zee-stapels](#zee-stapels)[](#zee-stapels)

De voorbeeld assetbibliotheek bevat twee soorten zee-stapel rotsformaties die je op creatieve manieren kunt stapelen om de pilaren van je zee-stapel platforms te vormen:

-

ZeeStapMesh  – Bevat een solide rotsformatie.

-

ZeeStapGrotMesh  – Bevat een tunnel en een solide bovenkant.

Beide platformtypes zijn [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten.

![Een vergelijking van een enkele zee-stapel naast meerdere zee-stapels die op elkaar zijn gestapeld.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Sea-Stacks.jpg)

![Een demonstratie van een ZeeStapGrotMesh gestapeld op een PlatformB bovenop een ZeeStapMesh.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Completed-Sea-Stack.jpg)

Bouw met Assistent Pas je eigen zee-stapels toe Recreëer het voorbeeld

Plaats alle zee-stapels

```

Voor elke rij hieronder, kopieer de bijpassende mesh uit de assetbibliotheek genaamd "Kern Bouwen en Scripting" in Workspace > World > Platforms > <Parent Model> en stel zijn Size, CFrame.Position, en CFrame.Orientation in. Alle meshes zijn ZeeStapMesh tenzij anders vermeld.

Level_3a:

- Size 31, 31, 34; CFrame.Position 31, 14, 15.5; CFrame.Orientation 0, 72, 0

- Size 32, 37, 34; CFrame.Position 39, 11, 6; CFrame.Orientation 0, 162, 0

- Size 32, 36, 34; CFrame.Position 31, 13, 7.5; CFrame.Orientation 0, 68, 0

Level_3b:

- Size 35, 47, 36; CFrame.Position 80, 7, 4; CFrame.Orientation 0, -18, 0

Level_3c:

- Size 52, 69, 53; CFrame.Position 90, -4, 48; CFrame.Orientation 0, -18, 0

Level_4a:

- Size 43, 49, 43; CFrame.Position 103, 5, 48; CFrame.Orientation 0, -119, 0

- Size 37, 49, 38; CFrame.Position 104, 41, 47; CFrame.Orientation 0, -18, 0

Level_4b:

- ZeeStapGrotMesh; Size 54, 67, 53; CFrame.Position 131, 88, 71; CFrame.Orientation 0, -111, 0

- Size 66, 85, 65; CFrame.Position 133, 23, 71; CFrame.Orientation 0, 87, 0

- Size 46, 55, 47; CFrame.Position 133, 136, 71; CFrame.Orientation 0, -79, 0

Level_4c:

- Size 63, 81, 62; CFrame.Position 151, 25, 91; CFrame.Orientation 0, -50, 0

Level_4d:

- Size 35, 39, 35; CFrame.Position 198, -4, 108; CFrame.Orientation 0, -44, 0

- Size 33, 36, 32; CFrame.Position 199, 21, 108; CFrame.Orientation 0, -119, 0

- Size 27, 36, 28; CFrame.Position 199, 48, 108; CFrame.Orientation 0, -18, 0

Level_4e:

- Size 57, 65, 57; CFrame.Position 239, -14, 82; CFrame.Orientation 0, -63, 0

- Size 48, 65, 50; CFrame.Position 239, 34, 81; CFrame.Orientation 0, 39, 0

Level_5a:

- Size 56, 62, 54; CFrame.Position 264, 11, 55; CFrame.Orientation 0, 150, 0

- Size 50, 57, 50; CFrame.Position 263, 50, 57; CFrame.Orientation 0, 75, 0

- Size 43, 57, 44; CFrame.Position 262, 92, 57; CFrame.Orientation 0, 176, 0

Level_5b:

- Size 47, 36, 40; CFrame.Position 245, -16, 15; CFrame.Orientation 0, 0, 0

- Size 38, 38, 41; CFrame.Position 245, 11, 14; CFrame.Orientation 0, 100, 0

- Size 36, 38, 34; CFrame.Position 243, 34, 15; CFrame.Orientation 0, -164, 0

- Size 31, 34, 30; CFrame.Position 244, 62, 16; CFrame.Orientation 0, -45, 0

- Size 28, 32, 28; CFrame.Position 244, 83, 15; CFrame.Orientation 0, -120, 0

- Size 24, 32, 24; CFrame.Position 244, 106, 15; CFrame.Orientation 0, -18, 0

Level_5c:

- Size 45, 34, 38; CFrame.Position 270, -8, -6; CFrame.Orientation 0, 180, 0

- Size 36, 35, 38; CFrame.Position 270, 17, -5; CFrame.Orientation 0, -80, 0

- Size 34, 35, 32; CFrame.Position 272, 40, -5; CFrame.Orientation 0, 16, 0

- Size 29, 32, 29; CFrame.Position 271, 65, -7; CFrame.Orientation 0, 136, 0

- Size 26, 30, 26; CFrame.Position 271, 86, -6; CFrame.Orientation 0, 61, 0

- Size 22, 30, 23; CFrame.Position 270, 108, -6; CFrame.Orientation 0, 162, 0

Level_5d:

- Size 65, 71, 63; CFrame.Position 315, -5, -27; CFrame.Orientation 0, -161, 0

- Size 58, 66, 58; CFrame.Position 315, 39, -25; CFrame.Orientation 0, 124, 0

- Size 50, 66, 51; CFrame.Position 315, 89, -24; CFrame.Orientation 0, -134, 0

Level_6a:

- Size 94, 104, 92; CFrame.Position 358, 32, -56; CFrame.Orientation 0, -123, 0

- Size 85, 96, 84; CFrame.Position 360, 97, -54; CFrame.Orientation 0, 162, 0

- Size 72, 71, 74; CFrame.Position 361, 165, -52; CFrame.Orientation 0, -79, 0

Level_6b:

- Size 44, 65, 47; CFrame.Position 380, 17, 9; CFrame.Orientation 0, -143, 0

- Size 46, 44, 39; CFrame.Position 380, 61, 11; CFrame.Orientation 0, -78, 0

- Size 37, 37, 40; CFrame.Position 381, 92, 11; CFrame.Orientation 0, 22, 0

- Size 35, 37, 33; CFrame.Position 381, 115, 10; CFrame.Orientation 0, 118, 0

- Size 30, 33, 30; CFrame.Position 379, 141, 10; CFrame.Orientation 0, -123, 0

- Size 27, 31, 27; CFrame.Position 380, 162, 10; CFrame.Orientation 0, 162, 0

- Size 23, 31, 24; CFrame.Position 380, 185, 11; CFrame.Orientation 0, -96, 0

Level_6c:

- Size 68, 52, 57; CFrame.Position 387, 3, 48; CFrame.Orientation 0, -4, 0

- Size 54, 54, 58; CFrame.Position 388, 41, 47; CFrame.Orientation 0, 96, 0

- Size 52, 54, 48; CFrame.Position 385, 75, 47; CFrame.Orientation 0, -168, 0

- Size 44, 49, 43; CFrame.Position 385, 114, 49; CFrame.Orientation 0, -49, 0

- Size 40, 45, 40; CFrame.Position 386, 145, 48; CFrame.Orientation 0, -124, 0

- Size 34, 45, 35; CFrame.Position 387, 178, 48; CFrame.Orientation 0, -22, 0

Level_7a:

- Size 96, 98, 102; CFrame.Position 406, 19, 82; CFrame.Orientation 0, -41, 0

- Size 92, 98, 84; CFrame.Position 407, 81, 82; CFrame.Orientation 0, -19, 0

- Size 81, 90, 79; CFrame.Position 407, 152, 80; CFrame.Orientation 0, 90, 0

- Size 73, 83, 73; CFrame.Position 404, 208, 80; CFrame.Orientation 0, 15, 0

- Size 62, 83, 64; CFrame.Position 403, 270, 79; CFrame.Orientation 0, 116, 0

Nadat je alle zee-stapels hebt geplaatst, verwijder je de placeholder grijsdoos cilinders binnen elk niveau model.

```

![Een weergave van het voorbeeld laser tag spel met alle platforms en zee-stapels zichtbaar met de gepolijste assets.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/ApplyAssetLibrary/SeaStacks-18.jpg)

### [Munten](#munten)[](#munten)

De voorbeeld assetbibliotheek bevat een enkele Munt  asset, die een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  is met een kind [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  die het een glanzende metalen afwerking geeft. Plaats er een waar je een placeholder munt hebt toegevoegd, en pas vervolgens de positie en oriëntatie aan zoals nodig.

 ![Een close-up weergave van een glanzende gouden munt met een Roblox icoon in het midden. De munt zweeft boven een grasachtige pad van het eiland.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Final-Coin.jpg)

Bouw met Assistent Pas je eigen munten toe Recreëer het voorbeeld

Plaats alle munten

```

Voor elke rij hieronder, kopieer de Coin-mesh uit de assetbibliotheek genaamd "Core Building and Scripting" naar Workspace > World > Coins en stel zijn CFrame.Position en CFrame.Orientation in:

- CFrame.Position -121, 3, 6; CFrame.Orientation 0, -105, 0

- CFrame.Position -107, 3, 10; CFrame.Orientation 0, -105, 0

- CFrame.Position -104, 3, 35; CFrame.Orientation 0, 120, 0

- CFrame.Position -86, 3, 61; CFrame.Orientation 0, 30, 0

- CFrame.Position -101, 3, -12; CFrame.Orientation 0, -15, 0

- CFrame.Position -22, 6, -39; CFrame.Orientation 0, 120, 0

- CFrame.Position -48, 6, -26; CFrame.Orientation 0, 75, 0

- CFrame.Position -65, 6, -6; CFrame.Orientation 0, 75, 0

- CFrame.Position -74, 6, 19; CFrame.Orientation 0, 75, 0

- CFrame.Position -67, 6, 46; CFrame.Orientation 0, 75, 0

- CFrame.Position -38, 14, 28; CFrame.Orientation 0, 75, 0

- CFrame.Position -8, 14, 8; CFrame.Orientation 0, 75, 0

- CFrame.Position -3, 14, 34; CFrame.Orientation 0, 75, 0

- CFrame.Position 35, 33, 9; CFrame.Orientation 0, -105, 0

- CFrame.Position 59, 39, 6; CFrame.Orientation 0, 90, 0

- CFrame.Position 78, 33, 4; CFrame.Orientation 0, -75, 0

- CFrame.Position 83, 39, 22; CFrame.Orientation 0, -165, 0

- CFrame.Position 113, 70, 56; CFrame.Orientation 0, -135, 0

- CFrame.Position 134, 70, 76; CFrame.Orientation 0, -135, 0

- CFrame.Position 175, 70, 103; CFrame.Orientation 0, 75, 0

- CFrame.Position 197, 70, 107; CFrame.Orientation 0, 105, 0

- CFrame.Position 214, 81, 95; CFrame.Orientation 0, 120, 0

- CFrame.Position 235, 99, 78; CFrame.Orientation 0, 135, 0

- CFrame.Position 258, 125, 54; CFrame.Orientation 0, 135, 0

- CFrame.Position 251, 132, 11; CFrame.Orientation 0, 135, 0

- CFrame.Position 260, 140, 4; CFrame.Orientation 0, 135, 0

- CFrame.Position 270, 132, -5; CFrame.Orientation 0, 135, 0

- CFrame.Position 312, 162, -19; CFrame.Orientation 0, 105, 0

- CFrame.Position 360, 206, -40; CFrame.Orientation 0, 69, 0

- CFrame.Position 377, 260, -4; CFrame.Orientation 0, -145, 0

- CFrame.Position 380, 206, 13; CFrame.Orientation 0, 12, 0

- CFrame.Position 386, 260, 27; CFrame.Orientation 0, -145, 0

- CFrame.Position 391, 206, 45; CFrame.Orientation 0, 12, 0

Nadat je alle munten hebt geplaatst, verwijder je de tijdelijke munten.

```

![Een uitzicht op glanzende gouden munten die boven elk niveau van het zee-stapelplatform zweven.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/ApplyAssetLibrary/Coins-Final.jpg)

### [Bergen](#bergen)[](#bergen)

De enkele MountainMesh  uit de assetbibliotheek siert de achtergrond, verbergt de rand van je waterterrain en omsluit je speelgebied. Het draaien en schalen van elke instantie doorbreekt de herhaling, zodat spelers niet opmerken dat je dezelfde mesh keer op keer gebruikt.

 ![Verschillende berg-meshes met verschillende schalen en rotatiewaarden overlappen elkaar om eruit te zien als een bergketen. Elke mesh heeft een lichtblauwe omtrek.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Mountain-Meshes-Stacked.jpg)

Bouw met Assistent Pas je eigen bergen toe Recreëer het voorbeeld

Plaats alle bergen

```

Voor elke rij hieronder, kopieer de MountainMesh uit de assetbibliotheek genaamd "Core Building and Scripting" naar Workspace > World > Mountains en stel zijn Size, CFrame.Position en CFrame.Orientation in:

- Size 2048, 334, 2048; CFrame.Position -1243, 115, -1402; CFrame.Orientation 0, 46, 0

- Size 2048, 212, 2048; CFrame.Position -326, 230, -1614; CFrame.Orientation -15, -155, 0

- Size 2048, 416, 1871; CFrame.Position 434, 160, -1543; CFrame.Orientation 0, -2, 0

- Size 2048, 400, 2048; CFrame.Position 1200, 147, -1534; CFrame.Orientation -15, -155, 0

- Size 2048, 540, 1488; CFrame.Position 1726, 220, -1139; CFrame.Orientation 0, -95, 0

- Size 2044, 442, 2044; CFrame.Position 2344, 174, -413; CFrame.Orientation 0, 5, 0

- Size 2048, 458, 2048; CFrame.Position 2267, 157, 1084; CFrame.Orientation 0, -81, 0

- Size 2048, 678, 2048; CFrame.Position 1662, 221, 1804; CFrame.Orientation 0, 9, 0

- Size 2043, 352, 1467; CFrame.Position 1025, 147, 2462; CFrame.Orientation 0, 54, 0

- Size 1980, 531, 1742; CFrame.Position 361, 180, 2119; CFrame.Orientation 0, 21, 0

- Size 2048, 415, 2048; CFrame.Position -580, 160, 1961; CFrame.Orientation 0, -122, 0

- Size 2048, 415, 2048; CFrame.Position -900, 160, 1652; CFrame.Orientation 0, 24, 0

- Size 1321, 403, 1321; CFrame.Position -1303, 133, 770; CFrame.Orientation 0, 55, 0

- Size 2048, 335, 2048; CFrame.Position -1653, 114, 161; CFrame.Orientation 0, -20, 0

- Size 2048, 249, 2048; CFrame.Position -1928, 79, -674; CFrame.Orientation 0, 24, 0

- Size 2048, 450, 2048; CFrame.Position -1426, 73, -895; CFrame.Orientation 0, -20, 0

```

![Een uitzicht op de gepolijste zee-stapels, platform en munten, met een bergketen op de achtergrond.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/ApplyAssetLibrary/Mountains-Final.jpg)

## [Speeltest](#speeltest)[](#speeltest)

Gepolijste assets kunnen de vorm van een zee-stapel net genoeg veranderen om een sprongetje dat werkte in de grijsdoosversie van het niveau te beïnvloeden. Maak een laatste ronde door het spel om eventuele problemen te identificeren en op te lossen voordat je publiceert.

Selecteer Test  in de dropdown en klik op Speel . Klim naar de flare bovenop de stapels; als een sprongetje plotseling vreemd aanvoelt, duw dan de betreffende mesh en probeer het opnieuw. Klik op Stop  wanneer je klaar bent.

Gefeliciteerd met het voltooien van de Core Curriculum! Vanaf hier kun je je project uitbreiden met nieuwe gameplay-functies of niveaus, de volledige [functieset](/docs/nl-nl/platform)  van Studio doorbladeren, of doorgaan naar een ander curriculum zoals [Milieu kunst](/docs/nl-nl/tutorials/curriculums/environmental-art) . Veel plezier met creëren!

[Vorige](/docs/nl-nl/tutorials/curriculums/core/building/customize-global-lighting)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
