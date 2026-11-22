<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/character-bodies/import -->

Importeer karakterlichamen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Lichamen

# Importeer karakterlichamen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Studio's Importer stelt je in staat om 3D-assets in je projecten te importeren, zoals avatar kleding, accessoires en karakterlichamen. De volgende instructies beschrijven hoe je een karakterlichaam .fbx  of .gltf  bestand in Studio importeert als een Model  object dat je kunt gebruiken in je games, uploaden naar de Marketplace of delen met andere makers.

Als je .fbx  of .gltf  bestand een enkele mesh is, kun je de [Avatar Setup](/docs/nl-nl/../../avatar-setup)  tool gebruiken om de mesh automatisch op te splitsen in de juiste 15 lichaamsdelen die nodig zijn voor een avatar karakterlichaam.

Hoewel de Importer objectvoorbeelden en foutcontroles biedt om ervoor te zorgen dat je creatie voldoet aan Roblox's [algemene 3D vereisten](/docs/nl-nl/art/modeling/specifications) , is het belangrijk om ervoor te zorgen dat je karaktermodel ook voldoet aan Roblox's [specificaties voor karakterlichamen](/docs/nl-nl/avatar/character-bodies/specifications)  om dit asset te gebruiken of te verkopen als een avatar-klaar karaktermodel, anders kun je op verschillende punten in de workflow fouten tegenkomen.

Om je asset als een karakterlichaam model te importeren:

1.

Klik op de Home  tab en klik op de Import  knop om de 3D Importer te openen. Een bestandsbrowser opent.

2.

Selecteer het .fbx  of .gltf  bestand van je gerigged karakter. De 3D Importer laadt een voorbeeld van het karaktermodel.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Avatar-3D-Importer.png)

-

Als texturen niet laden voor je asset, kun je later handmatig je texturen importeren.

-

Voor aanvullende informatie over importinstellingen en probleemoplossing, zie [Importer](/docs/nl-nl/studio/importer) .

3.

In de sectie Rig General ,

1.

OPTIONEEL

 Als je een [geavanceerd R15 rig](/docs/nl-nl/avatar/character-bodies/specifications#advanced-r15-rigs)  importeert, stel dan Rig Type  in op Custom Humanoid .

2.

Stel Rig Scale  in op de juiste [Body Scale](/docs/nl-nl/avatar/character-bodies/specifications#body-scale)  van je karakter.

3.

Stel Constraint Type  in op Joint Upgrade .

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Rig-General.png)

4.

Selecteer Import . De asset wordt in je werkruimte weergegeven als een [Model](/docs/nl-nl/reference/engine/classes/Model)  met de juiste texturen toegepast als een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  of [MeshPart.TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureID) .

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Avatar-Studio-Example.png)

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Avatar-Data-Model.png)

Texturen zijn niet correct geladen?

Als je texturen niet correct zijn geladen, kun je ze handmatig importeren met de [Asset Manager](/docs/nl-nl/projects/assets/manager) :

1.

Klik in de Asset Manager  op de Import  knop. Als je geen toegang hebt tot de Asset Manager, sla je je game eerst op en publiceer je deze.

2.

Upload je afbeeldingsbestanden.

3.

Nadat de moderatie je afbeeldingen heeft goedgekeurd, selecteer je de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  die binnen je geïmporteerde [Model](/docs/nl-nl/reference/engine/classes/Model)  is geplaatst.

4.

Als je een enkele basis textuur gebruikt, stel dan de [MeshPart.TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureID)  eigenschap in op je geüploade textuurafbeelding.

5.

Als je PBR-texturen gebruikt:

1.

Voeg een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  kind toe aan je [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) .

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Avatar-Surface-Appearance.png)

2.

Klik in de eigenschappen van de [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  op elke eigenschapswaarde en wijs de juiste textuurafbeelding toe vanuit de asset dropdown:

1.

Stel de ColorMap  in op de _ALB  textuurafbeelding.

2.

Stel de MetalnessMap  in op de _MTL  textuurafbeelding.

3.

Stel de NormalMap  in op de _NOR  textuurafbeelding.

4.

Stel de RoughnessMap  in op de _RGH  textuurafbeelding.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Avatar-Roughness-Map.png)

Met dit nieuwe karakter [Model](/docs/nl-nl/reference/engine/classes/Model) , kun je een van de volgende dingen doen:

-

Als je karakter een [geavanceerd R15 rig](/docs/nl-nl/avatar/character-bodies/specifications#advanced-r15-rigs)  bevat, voeg dan [HumanoidRigDescription](/docs/nl-nl/reference/engine/classes/HumanoidRigDescription)  en/of [DigitsRigDescription](/docs/nl-nl/reference/engine/classes/DigitsRigDescription)  objecten toe voor Marketplace en animatievereisten. Je moet mogelijk de [Adaptive Animation](/docs/nl-nl/characters/adaptive-animation)  plugin gebruiken om je gewrichten opnieuw in te stellen en een basis t-pose referentie in te stellen om je animaties beter te ondersteunen.

-

Begin het proces van [uploaden en publiceren](/docs/nl-nl/marketplace/publish-to-marketplace#upload-an-asset)  van het karaktermodel naar de Marketplace. Dit omvat enkele aanvullende validatie- en moderatiestappen.

-

Gebruik het model in je huidige game en wijzig het uiterlijk van het model met [HumanoidDescription](/docs/nl-nl/characters/appearance#manually-modify-appearance) .

-

Speel als het karakter door de [Model](/docs/nl-nl/reference/engine/classes/Model)  te hernoemen naar StarterCharacter  en de [Model](/docs/nl-nl/reference/engine/classes/Model)  naar de [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  map in de Explorer  te verplaatsen voordat je gaat playtesten.

-

Sla het model op in je [Toolbox](/docs/nl-nl/projects/assets/toolbox)  of maak het openbaar op de [Creator Store](/docs/nl-nl/production/creator-store)  om het binnen een van je games te gebruiken of te delen met andere makers.

Het maken van een karakter is een complex proces dat veel testen en iteratie vereist. Voor informatie over het importeren van je karaktermodel in een testplaats en het verifiëren van je avatar en gerelateerde componenten, zie [Test karakterlichamen](/docs/nl-nl/avatar/character-bodies/test) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
