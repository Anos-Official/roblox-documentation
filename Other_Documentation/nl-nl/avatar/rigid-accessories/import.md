<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/rigid-accessories/import -->

Importeer stijve accessoires | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Accessories and clothing
6. /
7. Stijve accessoires

# Importeer stijve accessoires

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Importer van Studio stelt je in staat om 3D-assets in je projecten te importeren, zoals karakterlichamen, make-up en stijve accessoires. De volgende instructies beschrijven hoe je een stijve accessoire .fbx  of .gltf  bestand in Studio kunt importeren als een Model  object en het kunt omzetten naar een Accessory  object dat je kunt gebruiken in je games, uploaden naar de Marketplace of delen met andere makers.

Hoewel de Importer objectvoorbeelden en foutcontroles biedt om ervoor te zorgen dat je creatie voldoet aan Roblox's [algemene 3D-vereisten](/docs/nl-nl/art/modeling/specifications) , is het belangrijk om ervoor te zorgen dat je karaktermodel ook voldoet aan Roblox's [specificaties voor stijve accessoires](/docs/nl-nl/avatar/rigid-accessories/specifications)  om dit asset te gebruiken of te verkopen als een avatar-klaar stijve accessoire, anders kun je op verschillende punten in de workflow fouten tegenkomen.

## [Accessoires importeren](#accessoires-importeren)[](#accessoires-importeren)

Om je asset als een stijve accessoire te importeren:

1.

Klik op de Home  tab en klik op de Import  knop om de Importer te openen. Een bestandsbrowser opent.

2.

Selecteer het .fbx  of .gltf  bestand van je stijve accessoire. De Importer laadt een voorbeeld van de stijve accessoire.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/Import-Rigid-Accessory.png)

3.

Selecteer Importeren . Het asset wordt in je werkruimte weergegeven als een [Model](/docs/nl-nl/reference/engine/classes/Model)  met de juiste texturen toegepast als een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  of [MeshPart.TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureID) .

Texturen zijn niet correct geladen?

Als je texturen niet correct zijn geladen, kun je ze handmatig importeren met de [Asset Manager](/docs/nl-nl/projects/assets/manager) :

1.

Klik in de Asset Manager  op de Import  knop. Als je geen toegang hebt tot de Asset Manager, sla je je game eerst op en publiceer je deze.

2.

Upload je afbeeldingsbestanden.

3.

Nadat de moderatie je afbeeldingen heeft goedgekeurd, selecteer je het [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  dat binnen je geïmporteerde [Model](/docs/nl-nl/reference/engine/classes/Model)  is geplaatst, en voeg je een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  kind toe aan je [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) .

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/Adding-Surface-Appearance-Bow.png)

4.

Selecteer het [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object, en klik in het Properties  venster op elke eigenschapswaarde en wijs de juiste textuurafbeelding toe vanuit de asset dropdown:

1.

Stel de ColorMap  in op de _ALB  textuurafbeelding.

2.

Stel de MetalnessMap  in op de _MTL  textuurafbeelding.

3.

Stel de NormalMap  in op de _NOR  textuurafbeelding.

4.

Stel de RoughnessMap  in op de _RGH  textuurafbeelding.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/Surface-Appearance-Asset-Dropdown-Bow.png)

## [Stijve accessoires converteren](#stijve-accessoires-converteren)[](#stijve-accessoires-converteren)

Nadat je je asset in Studio hebt geïmporteerd, kun je beginnen met passen  van je geïmporteerde object op een mannequin en converteren  van het [Model](/docs/nl-nl/reference/engine/classes/Model)  object naar een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory) . Bij het passen en converteren van je accessoire is het belangrijk om de [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  (AFT) te gebruiken om de plaatsing correct te previewen en de juiste configuraties op je accessoire toe te passen.

Om je stijve accessoire te passen en te genereren:

1.

Klik op de Accessory  knop in de Avatar  tab van de werkbalk om de AFT te openen. Het Accessory Fitting Tool  paneel wordt weergegeven.

2.

In het paneel:

1.

Selecteer het Part  veld, en selecteer in het Explorer  venster het stijve accessoire [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  object.

2.

Klik terug in het paneel op de Volgende  knop. De Asset Type  pagina wordt weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/AFT-Select-Mesh-Bow.png)

3.

In de Asset Type  pagina:

1.

Stel het assettype in op Accessory , en gebruik het dropdownmenu om de locatie te kiezen waar je de stijve accessoire aan het lichaam van een karakter wilt bevestigen.

2.

Stel het lichaamstype in op de [lichaamsverhouding](/docs/nl-nl/avatar/rigid-accessories/specifications#lichaamschaal)  die je hebt bepaald tijdens het sculpten en schalen van het asset tijdens het creatieproces, en klik vervolgens op de Volgende  knop. Een voorbeeldpaneel wordt weergegeven met een standaard karakter dat je stijve accessoire draagt.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/AFT-Select-Type-Bow.png)

4.

Selecteer een van de humanoïde karakters als mannequin:

1.

Selecteer in de Avatars  sectie een humanoïde karakterlichaam.

2.

Deselecteer in het voorbeeldpaneel de vorige selectie. Je karakterlichaamselectie wordt weergegeven in het voorbeeldvenster.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/AFT-Add-Avatar-Panel-Bow.png)

5.

Gebruik zowel het AFT voorbeeldvenster als de viewport om de positie, schaal en rotatie van de stijve accessoire aan te passen.

1.

Gebruik het AFT voorbeeldvenster en je mannequin als een nauwkeurige preview van hoe je asset op het karakter past. De kledingmannequin in de viewport geeft niet nauwkeurig weer hoe stijve accessoires worden bevestigd.

2.

Gebruik in de viewport de Verplaatsen , Schaal  en Roteren  tools om de positionering van je stijve accessoire aan te passen.

3.

Als je per ongeluk iets anders selecteert, klik dan terug in het AFT paneel om de accessoire opnieuw te selecteren en je aanpassingen voort te zetten met de transformatietools.

6.

Nadat je je asset hebt gepreviewd en gepast, klik je op de Genereer MeshPart Accessory  knop. Je 3D-model wordt in je project weergegeven als een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  object.

Met dit [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  object kun je een van de volgende dingen doen:

-

Begin met het proces van [uploaden en publiceren](/docs/nl-nl/marketplace/publish-to-marketplace#upload-een-activum)  van de stijve accessoire naar de Marketplace.

-

Gebruik de stijve accessoire in je huidige game door deze uit te rusten op karaktermodellen met een [HumanoidDescription](/docs/nl-nl/characters/appearance#handmatig-aangepast-uiterlijk) , of door de stijve accessoire onder het juiste karakter [Model](/docs/nl-nl/reference/engine/classes/Model)  object te slepen en neer te zetten.

-

Sla de stijve accessoire op in je [Toolbox](/docs/nl-nl/projects/assets/toolbox)  of maak deze openbaar in de [Creator Store](/docs/nl-nl/production/creator-store)  om deze binnen een van je games te gebruiken of te delen met andere makers.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
