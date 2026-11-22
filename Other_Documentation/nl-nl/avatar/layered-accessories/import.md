<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/layered-accessories/import -->

Laagged accessoires importeren | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Accessories and clothing
6. /
7. Layered accessories

# Laagged accessoires importeren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Importer van Studio stelt je in staat om 3D-assets in je projecten te importeren, zoals karakterlichamen, make-up en laagged accessoires. De volgende instructies beschrijven hoe je een laagged accessoire .fbx  of .gltf  bestand in Studio kunt importeren als een Model  object en het kunt omzetten naar een Accessory  object dat je kunt gebruiken in je games, uploaden naar de Marketplace of delen met andere makers.

Hoewel de Importer objectvoorbeelden en foutcontroles biedt om ervoor te zorgen dat je creatie voldoet aan Roblox's [algemene 3D-vereisten](/docs/nl-nl/art/modeling/specifications) , is het belangrijk om ervoor te zorgen dat je karaktermodel ook voldoet aan Roblox's [specificaties voor laagged accessoires](/docs/nl-nl/avatar/layered-accessories/specifications)  om dit asset te gebruiken of te verkopen als een avatar-klaar laagged accessoire, anders kun je op verschillende punten in de workflow fouten tegenkomen.

## [Accessoires importeren](#accessoires-importeren)[](#accessoires-importeren)

Om je asset als een laagged accessoire te importeren:

1.

Klik op de Home  tab en klik op de Import  knop om de Importer te openen. Een bestandsbrowser opent.

2.

Selecteer het .fbx  of .gltf  bestand van je laagged accessoire. De Importer laadt een voorbeeld van het laagged accessoire.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Import-Layered-Accessory.png)

3.

Selecteer Importeren . Het asset verschijnt in je werkruimte als een [Model](/docs/nl-nl/reference/engine/classes/Model)  met de juiste texturen toegepast als een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  of [MeshPart.TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureID) .

Texturen zijn niet correct geladen?

Als je texturen niet correct zijn geladen, kun je ze handmatig importeren met de [Asset Manager](/docs/nl-nl/projects/assets/manager) :

1.

Klik in de Asset Manager  op de Import  knop. Als je geen toegang hebt tot de Asset Manager, sla je je game eerst op en publiceer je deze.

2.

Upload je afbeeldingsbestanden.

3.

Nadat de moderatie je afbeeldingen heeft goedgekeurd, selecteer je de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  die binnen je geïmporteerde [Model](/docs/nl-nl/reference/engine/classes/Model)  is geplaatst.

4.

Als je een enkele basis textuur gebruikt, stel je de [MeshPart.TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureID)  eigenschap in op je geüploade textuurafbeelding.

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

## [Laagged accessoires converteren](#laagged-accessoires-converteren)[](#laagged-accessoires-converteren)

Nadat je je asset in Studio hebt geïmporteerd, kun je beginnen met het converteren  van het [Model](/docs/nl-nl/reference/engine/classes/Model)  object naar een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  met behulp van de [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  (AFT) zodat avatar karakterlichamen je laagged accessoire kunnen uitrusten.

Voor schoenen moet je de linkerschoen en de rechterschoen als aparte laagged accessoires converteren. Gebruik de volgende instructies voor elke schoen voordat je beide schoenaccessoires groepeert als een [Model](/docs/nl-nl/reference/engine/classes/Model)  wanneer je [opslagt naar Roblox](/docs/nl-nl/marketplace/publish-to-marketplace#upload-een-activum) .

Om je laagged accessoire te genereren:

1.

Klik op de Avatar  tab in de werkbalk en klik op Accessoire  om de AFT te openen. Het Accessory Fitting Tool  paneel wordt weergegeven.

2.

In het paneel:

1.

Selecteer het Part  veld, selecteer vervolgens in het Explorer  venster het laagged accessoire [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  object.

2.

Terug in het paneel, klik op de Volgende  knop. De Asset Type  pagina wordt weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/AFT-Select-Mesh-Pants.png)

3.

Op de Asset Type  pagina:

1.

Stel het assettype in op Kleding , en gebruik vervolgens het dropdownmenu om het kledingtype van je laagged accessoire te kiezen.

2.

Klik op de Volgende  knop. Een voorbeeldpaneel wordt weergegeven met een standaard karakter dat je laagged accessoire draagt.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/AFT-Select-Type-Pants.png)

4.

[Test](/docs/nl-nl/avatar/accessory-fitting-tool#accessoires-testen)  verschillende voorbeeldkarakters en animaties om ervoor te zorgen dat je laagged accessoire correct vervormt en beweegt.

-

Indien nodig, maak kleine aanpassingen aan de cage met behulp van de bewerkingsfuncties. Grotere cage-wijzigingen kunnen vereisen dat je terugkeert naar je derde-partij modelleer software en het asset opnieuw exporteert.

5.

Nadat je je asset hebt bekeken, klik je op de Genereer MeshPart Accessoire  knop. Je 3D-model verschijnt in je project als een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  object.

Met dit [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  object kun je een van de volgende dingen doen:

-

Begin met het proces van [uploaden en publiceren](/docs/nl-nl/marketplace/publish-to-marketplace#upload-een-activum)  van het laagged accessoire naar de Marketplace.

-

Gebruik het laagged accessoire in je huidige game door het uit te rusten op karaktermodellen met [HumanoidDescription](/docs/nl-nl/characters/appearance#handmatig-aangepast-uiterlijk) , of door het laagged accessoire onder het juiste karakter [Model](/docs/nl-nl/reference/engine/classes/Model)  object te slepen en neer te zetten.

-

Sla het laagged accessoire op in je [Toolbox](/docs/nl-nl/projects/assets/toolbox)  of maak het openbaar op de [Creator Store](/docs/nl-nl/production/creator-store)  om het binnen een van je games te gebruiken of te delen met andere makers.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
