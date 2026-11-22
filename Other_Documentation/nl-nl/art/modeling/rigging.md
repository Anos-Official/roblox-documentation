<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/rigging -->

Rigging en skinning | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Modellering

# Rigging en skinning

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Rigging  is het proces van het verbinden van een mesh met een interne poseerbare skeletstructuur en botstructuur. Geriggende meshes stellen de oppervlakken van de mesh in staat om te draaien en te bewegen waar interne botten binnen het model zijn geplaatst tijdens het modelleerproces. Rigging wordt vaak uitgevoerd in combinatie met skinning , wat een natuurlijk uitziende rek en buiging creëert wanneer modellen worden geanimeerd of opnieuw gepositioneerd. Je kunt geriggende meshes maken met software van derden zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) .

Een normaal model kan alleen draaien om zijn draaipunt.

Een geriggd model (of mesh) kan draaien met elk bot van de bijbehorende rig.

Een geriggd model zonder skinninggegevens.

Een geskinnd model dat organisch buigt met de botrotatie.

Zie de volgende bronnen om de basisprincipes en tussenstappen te leren die nodig zijn om modellen in Blender te skinnen:

-

[Rig een eenvoudige mesh](/docs/nl-nl/art/modeling/rig-a-simple-mesh)

-

[Skin een eenvoudige mesh](/docs/nl-nl/art/modeling/skin-a-simple-mesh)

-

[Rig een humanoïde model](/docs/nl-nl/art/modeling/rig-a-humanoid-model)

-

[Skin een humanoïde model](/docs/nl-nl/art/modeling/skin-a-humanoid-model)

## [Rigs en botten](#rigs-en-botten)[](#rigs-en-botten)

De rig , of botstructuur, binnen een geriggd mesh creëert extra poseerbare punten voor het 3D-model in Studio. Door de botten van een mesh te draaien of te verplaatsen, kunnen de delen van de mesh die aan die botten zijn toegewezen onafhankelijk van de rest van de mesh bewegen. De toewijzing van invloed tussen meshes en botten, zoals een LowerLeftArm  bot die de beweging van de LowerLeftArm  geometrie aanstuurt, wordt ingesteld in een applicatie van derden zoals Blender of Maya. Wanneer deze in Studio worden geïmporteerd, slaat Roblox deze invloedstoewijzingsgegevens op in de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  assetgegevens.

Zodra je met succes een [import](/docs/nl-nl/parts/meshes#importeren-van-meshes)  van een geriggd meshmodel in Studio hebt uitgevoerd, vertegenwoordigt Studio deze rigstructuur met [Bone](/docs/nl-nl/reference/engine/classes/Bone)  instanties die je vervolgens kunt poseren en animeren. Je kunt botten in Studio bekijken door Toon Constraint Details  in het Weergave  menu in te schakelen, of wanneer je de [Animatie-editor](/docs/nl-nl/animation/editor)  gebruikt.

Wanneer [Bone](/docs/nl-nl/reference/engine/classes/Bone)  objecten worden gebruikt in animatie, beïnvloeden ze het uiterlijk van de delen maar veranderen ze niet de fysieke vorm in gevallen zoals [botsingsdetectie](/docs/nl-nl/workspace/collisions) .

![Een doorschijnende humanoïde omtrek, die verschillende bolpunten toont waar de beperkingen bestaan.](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Rig-Constraint-Details.jpg) Constraint Details ingeschakeld

![Een doorschijnende humanoïde omtrek, die 15 roze botobjecten over verschillende ledematen toont.](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Rig-Bone-Visualization.jpg) Wanneer de Animatie-editor wordt gebruikt

## [Typen rigs](#typen-rigs)[](#typen-rigs)

Geriggte modellen gebruiken een naamgevingsconventie die begint met "R" en eindigt met het aantal individuele meshes waaruit het model bestaat. Dit wordt gebruikt om snel het type en het aantal meshes dat een model heeft te identificeren. Hoewel R6 en R15 modellen gebruikelijk zijn, kan een model van verschillende onderwerpen, maten zijn en kan het een willekeurig aantal individuele meshes hebben, zoals een R5, R20 of R200.

-

R1  verwijst naar een enkele mesh die is geriggd, of geassocieerd met een interne skeletstructuur. Veel modellen, zoals een boom of accessoire-item, zijn goede kandidaten om in een R1-model te worden omgezet. Zelfs NPC humanoïde karakters kunnen worden gemaakt als R1-modellen, maar ze zullen niet in staat zijn om volledig gebruik te maken van de animatie- en humanoïde opties die beschikbaar zijn voor R15-karakters.

Zie [Rig een eenvoudige mesh](/docs/nl-nl/art/modeling/rig-a-simple-mesh)  voor instructies over het omzetten van een basismesh in een R1-model in Blender.

-

R15  verwijst doorgaans naar humanoïde modellen die worden gebruikt als speler- of avatarpersonages. Een R15-model bestaat uit 15 specifieke meshes die zijn gekoppeld aan een enkele [R15 rig](/docs/nl-nl/avatar/character-bodies/specifications#rigging) . Een R15 karaktermodel bevat vaak skinninggegevens om het model in staat te stellen om natuurlijk te buigen en te poseren. Roblox gebruikt de R15-standaard voor alle avatars en vereist de [technische specificaties](/docs/nl-nl/avatar/character-bodies/specifications)  om universeel gedrag en kwaliteit te waarborgen.

Zie [Rig een humanoïde model](/docs/nl-nl/art/modeling/rig-a-humanoid-model)  voor instructies over het omzetten van een karaktermodel in een R15 humanoïde model in Blender.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
