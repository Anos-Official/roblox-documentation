<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/specifications -->

Algemene specificaties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Modellering

# Algemene specificaties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox ondersteunt een breed scala aan meshconfiguraties die zijn gemaakt met software van derden, zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) .

Controleer of je model voldoet aan de volgende modellering specificaties en richtlijnen voordat je exporteert om compatibiliteit met Studio te waarborgen. Specifieke soorten activa, zoals personages en accessoires, hebben aanvullende specificaties:

Als je andere soorten 3D-modellen maakt:

-

Voor rigide accessoires, zie [accessoirespecificaties](/docs/nl-nl/avatar/rigid-accessories/specifications)  en [exportinstellingen voor accessoires](/docs/nl-nl/avatar/rigid-accessories/export) .

-

Voor gelaagde accessoires, zie [specificaties voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications)  en [exportinstellingen voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/export) .

-

Voor avatarpersonages, zie [avatarspecificaties](/docs/nl-nl/avatar/character-bodies/specifications)  en [exportinstellingen voor avatars](/docs/nl-nl/avatar/character-bodies/export) .

Wanneer je klaar bent om te exporteren, zie de [exportinstellingen](/docs/nl-nl/art/modeling/export-requirements)  voor mesh-exportinstellingen voor Blender en Maya.

Als je aan bepaalde accountvereisten voldoet, kun je je aangepaste meshes verkopen als accessoires op de Marketplace. Zie [Rigide accessoires](/docs/nl-nl/avatar/rigid-accessories)  voor een overzicht van het creatieproces voor deze soorten accessoires.

## [Geometrie](#geometrie)[](#geometrie)

Zie de volgende specificaties voor algemene geometrie:

-

Budgetten  - Individuele meshes mogen niet meer dan 20.000 driehoeken bevatten. Avataritems hebben hun eigen individuele budgetvereisten voor [personage-lichaams](/docs/nl-nl/avatar/character-bodies/specifications) , [rigide accessoires](/docs/nl-nl/avatar/rigid-accessories/specifications)  en [gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications) .

-

Waterdicht  - Alle geometrie moet waterdicht zijn zonder blootgestelde gaten of achterkant.

-

Geen N-gons  - Meshes moeten waar mogelijk in quads zijn.

-

Volume  - Meshes mogen geen 0-dikte hebben en moeten een bepaald volume hebben.

## [Rigging en skinning](#rigging-en-skinning)[](#rigging-en-skinning)

Roblox ondersteunt meshes van derden met een interne rig of skeletstructuur die kan worden gebruikt als extra articulatiepunten in je model. Voor meer informatie over de specifieke normen voor R15-rigs, zie [Specificaties voor personage-lichaam - Rigging](/docs/nl-nl/avatar/character-bodies/specifications#rigging) .

![Een cartoonachtige low polygon model van een kogelvis.](https://prod.docsiteassets.roblox.com/assets/animation/importing-custom-3d-rigs/Rig-Custom-Puffer-Blender.png) Algemeen rigmodel.

![De Outliner in Blender van het kogelvismodel, die de armatuur-bone-structuur toont.](https://prod.docsiteassets.roblox.com/assets/animation/importing-custom-3d-rigs/Rig-Hierarchy-Custom-Blender-Bones.png) Algemene rig-bonestructuur (Blender).

Zie de volgende vereisten voor algemene rigging en skinning:

-

Transformaties  - Alle botten (Blender) of gewrichten (Maya) moeten bevroren zijn en de schaalwaarden moeten zijn ingesteld op 1 , 1 , 1  en de rotatiewaarden moeten zijn ingesteld op 0 , 0 , 0 .

-

Symmetrie  - Behoud symmetrie waar mogelijk bij het toepassen van invloeden op een rig.

-

Root joint  - Het rootbot of gewricht moet altijd worden ingesteld op 0 , 0 , 0 .

-

Max invloeden  - Een vertex mag niet door meer dan 4 botten of gewrichten worden beïnvloed.

-

Geen Root invloeden  - Pas geen invloeden toe op het Rootbot of gewricht.

## [Texturen](#texturen)[](#texturen)

-

Roblox ondersteunt basis kleurtexturen en moderne [PBR-texturen](/docs/nl-nl/art/modeling/surface-appearance) .

-

Voor instructies over het toewijzen van textuurafbeeldingen om natively te importeren met je mesh, zie [Texturen toewijzen in modelleringstools](/docs/nl-nl/art/modeling/assign-textures) .

-

Voor technische vereisten en best practices bij het genereren van individuele textuurafbeeldingen, zie [Textuurspecificaties](/docs/nl-nl/art/modeling/texture-specifications) .

## [Animaties](#animaties)[](#animaties)

Een animatie kan worden opgenomen in elke .fbx  mesh-export. Voor informatie over het voorbereiden van een karakteranimatie vanuit een modelleringsoftware voor export, zie [Animaties exporteren vanuit Maya](/docs/nl-nl/art/characters/export-avatar-animations-from-maya) .

Zie de volgende vereisten voor activa met animatie:

-

Enkele trackanimatie  - Slechts één animatietrack kan worden geëxporteerd met een mesh of model. Als je meerdere animaties wilt exporteren, moet je aparte exports maken voor elke animatie die je wilt importeren.

## [Binnen- en buitenkooien](#binnen--en-buitenkooien)[](#binnen--en-buitenkooien)

Binnen- en buitenkooien zijn niet-gerenderde meshes die Roblox gebruikt om de binnen- en buitenoppervlakken van een mesh te definiëren met een [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  of [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  instantie. Deze kooien worden het vaakst gebruikt met personages en accessoires, hoewel je kooimeshes voor elk meshobject kunt gebruiken.

Personagemodellen moeten een buitenkooi bevatten om gelaagde accessoires correct te kunnen uitrusten. Voor meer informatie, zie [Specificaties voor personage-lichaam](/docs/nl-nl/avatar/character-bodies/specifications) .

Voor algemeen gebruik, zie de volgende vereisten voor het toevoegen van binnen- en buitenkooi-meshes aan je model:

-

Naamgevingsconventies  - De binnen- en buitenkooi moeten worden genoemd naar het primaire meshobject met _InnerCage  en _OuterCage  toegevoegd.

 ![De Outliner in Blender toont twee meshobjecten genaamd Tshirt_InnerCage en Tshirt_OuterCage.](https://prod.docsiteassets.roblox.com/assets/accessories/lc-blender-selecting-cage-in-outlier.png)

-

Buitenkooi  - Modellen, zoals een speelbaar personage, die niet worden verwacht te vervormen maar het doel zijn van meshes die eroverheen zullen rekken, vereisen alleen een buitenkooi.

-

Voor meer informatie over het toepassen en implementeren van kooien op niet-Humanoïde doelen, zie [gelaagde accessoires op niet-R15](/docs/nl-nl/characters/appearance#gelaagde-accessoires-op-niet-r15) .

-

Vertices en UV-kaart  - Verwijder geen vertices of wijzig de UV's op de Binnen- of Buitenkooien, aangezien dit fouten kan veroorzaken bij het importeren in Studio of bij het uitrusten op een personage.

-

Symmetrie en consistentie  - Houd elke face (de ruimte tussen vertices) consistent van grootte en behoud symmetrie waar mogelijk. Gebruik symmetrie-tools in je modelleringsoftware waar mogelijk.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
