<!-- Source: https://create.roblox.com/docs/nl-nl/workspace -->

3D-werkruimte | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)

# 3D-werkruimte

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  is een container service die objecten bevat die je wilt dat de Roblox Engine in de 3D-wereld weergeeft. Je voegt deze objecten meestal toe aan de werkruimte:

-

[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  objecten, die zowel [Part](/docs/nl-nl/reference/engine/classes/Part)  als [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten omvatten.

-

[Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten, die je kunt bevestigen aan speciale effectgeneratoren zoals een [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter) , UI-objecten zoals een [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui) , fysieke [Constraints](/docs/nl-nl/reference/engine/classes/Constraint) , en meer.

-

[Model](/docs/nl-nl/reference/engine/classes/Model)  objecten die geometrische groeperingen organiseren.

-

[Script](/docs/nl-nl/reference/engine/classes/Script)  objecten die door andere objecten in de werkruimte zijn geparent. Scripts worden niet weergegeven, maar kunnen de weergave van een ander object beïnvloeden.

## [Onderdelen](#onderdelen)[](#onderdelen)

[Part](/docs/nl-nl/reference/engine/classes/Part)  objecten vertegenwoordigen de primitieve bouwstenen in Roblox. Standaard hebben alle onderdelen hun fysica gesimuleerd en worden ze weergegeven als ze in de 3D-werkruimte verschijnen. Onderdelen kunnen de vorm hebben van blokken, bollen, cilinders, wiggen of hoekenwiggen. Daarnaast fungeert [TrussPart](/docs/nl-nl/reference/engine/classes/TrussPart)  als een truss-balk waar karakters op kunnen klimmen als een ladder.

![Een enkele blok onderdeel.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Block.png) Blok

![Een enkele bol onderdeel.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Sphere.png) Bol

![Een enkele cilinder onderdeel.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Cylinder.png) Cilinder

![Een enkele wig onderdeel.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Wedge.png) Wig

![Een enkele hoekwig onderdeel.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Corner-Wedge.png) Hoekwig

Je kunt ook [solide modellering](/docs/nl-nl/parts/solid-modeling)  bewerkingen op onderdelen toepassen, zoals unie of negatie, om ze te combineren tot iets complexers zoals kommen of holle buizen.

## [Meshes](#meshes)[](#meshes)

Een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  is een object dat een mesh vertegenwoordigt (een verzameling van vertices, randen en vlakken die een 3D-object vormen). Je maakt meestal meshes met behulp van software van derden zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) , en importeert ze vervolgens als een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  met behulp van Studio.

Meshes kunnen veel meer detail bevatten dan enige solide modellering die je in Studio kunt doen. Ze kunnen ook interne rigs en texturen hebben, waardoor je levensachtige objecten kunt creëren die je kunt poseren en animeren.

![Een hoogwaardige schatkist mesh met een textuur.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Mesh-Textured.jpg) Mesh met textuur

![Een realistisch uitziende bladachtige struik met schaduwen en diepte.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Mesh-SurfaceAppearance.jpg) Mesh met SurfaceAppearance

## [Terrains](#terrains)[](#terrains)

Het [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  object stelt je in staat om gedetailleerde en realistische terreinomgevingen te genereren en te sculpten, zoals bergen, waterlichamen, met gras bedekte heuvels of een vlakke woestijn. Met de [Terrain Editor](/docs/nl-nl/studio/terrain-editor)  kun je eenvoudig grote gebieden van terrein genereren en wijzigen.

 ![Een viewportweergave van woestijnlandschap met bergen in de verte.](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Showcase.jpg)

## [Modellen](#modellen)[](#modellen)

Een [Model](/docs/nl-nl/reference/engine/classes/Model)  is een containerobject voor geometrische groeperingen , zoals [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , [Motor6D](/docs/nl-nl/reference/engine/classes/Motor6D)  objecten en andere modellen. Modellen kunnen eenvoudige groeperingen zijn of je kunt een primair onderdeel binnen het model instellen, zodat het functioneert als een assemblage, die de fysica-engine behandelt als een enkel rigide lichaam. Modellen kunnen ook scripts bevatten die op de individuele objecten van het model werken.

![Een humanoïde model van een creepy meisje met vier rode ogen in een A-houding. Ze draagt een kastanjebruine jurk met spinnenwebben en felrode kousen.](https://prod.docsiteassets.roblox.com/assets/modeling/model-objects/Model-Example-3D.jpg) Een model genaamd Octavia

![Een close-up weergave van de kinderen van het model in het Explorer-venster die het model vormen.](https://prod.docsiteassets.roblox.com/assets/modeling/model-objects/Model-Example-Hierarchy.png) De groeperingen die het model vormen

## [Toegang tot de werkruimte in scripts](#toegang-tot-de-werkruimte-in-scripts)[](#toegang-tot-de-werkruimte-in-scripts)

Binnen een script kun je de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  van een plaats op drie verschillende manieren benaderen, die allemaal geldig zijn.

-

game:GetService("Workspace")

-

workspace

-

game.Workspace

Van daaruit kun je een groot aantal gebruiksscenario's uitvoeren om logica voor je games te scripten en dynamische werelden en interacties te creëren. Bijvoorbeeld:

-

Verkrijg een referentie naar elk object in de werkruimte om de eigenschappen ervan tijdens runtime te wijzigen.

-

Verkrijg een referentie naar het [Camera](/docs/nl-nl/reference/engine/classes/Camera)  object van een gebruiker om hun [weergave](/docs/nl-nl/workspace/camera)  van de werkruimte te manipuleren.

-

Luister naar gebeurtenissen op objecten in de werkruimte om logica op specifieke momenten uit te voeren, zoals wanneer een speelbaar karakter van een gebruiker [een object aanraakt](/docs/nl-nl/workspace/collisions) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
