<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/layered-accessories/export -->

Exporteer gelaagde accessoires | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Accessories and clothing
6. /
7. Layered accessories

# Exporteer gelaagde accessoires

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Wanneer je klaar bent om een model van een gelaagde accessoire te exporteren dat voldoet aan de [specificaties voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications)  van Roblox, is het belangrijk om de volgende vereiste informatie en stapsgewijze instructies voor de exportbestanden .fbx  of .gltf  te bekijken, zodat je creatie gebruikmaakt van alle functies van de [Importer](/docs/nl-nl/studio/importer)  in Studio.

Dit is vooral belangrijk voor modellen van gelaagde accessoires omdat ze alle mesh- en textuurgegevens bevatten, inclusief de rig- en invloedgegevens die essentieel zijn voor accessoires om correct te bewegen en te animeren met karakterlichamen op het platform.

Voor andere soorten 3D-modellen:

-

[Algemene mesh](/docs/nl-nl/art/modeling/export-requirements)  exportinstellingen.

-

[Stijve accessoire](/docs/nl-nl/avatar/rigid-accessories/export)  exportinstellingen.

## [Vereisten](#vereisten)[](#vereisten)

Voordat je je aangepaste gelaagde accessoire exporteert, zorg ervoor dat je alleen de door Roblox ondersteunde objecten die verband houden met je model exporteert. Als je modifiers op je mesh of projectobjecten hebt, zorg er dan voor dat je deze toepast of verwijdert voordat je exporteert.

Je kunt modellen van gelaagde accessoires exporteren met de volgende objectstructuur:

|
-

Armature-ouder
-

Beenderen / gewrichten

-

Primaire mesh-object

-

Cage-ouderobject
-

Inner cage mesh-object

-

Outer cage mesh-object

 | | ![Voorbeeld van een Blender gelaagd accessoire datamodel](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Clothing-Data-Model.png) |
| --- | --- |

Je kunt ook schoenen samen exporteren. Hoewel de linker en rechter schoen aparte gelaagde accessoires zijn, kun je de linker en rechter schoen afzonderlijk exporteren, of beide schoenen tegelijk exporteren met de volgende structuur:

|
-

Armature-ouder
-

Beenderen / gewrichten

-

Linker schoen mesh-object

-

Rechter schoen mesh-object

-

Cage-ouderobject
-

Linker schoen inner cage

-

Linker schoen outer cage

-

Rechter schoen inner cage

-

Rechter schoen outer cage

 | | ![Voorbeeld van een gelaagd accessoire datamodel voor schoenen](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Shoe-Data-Model.png) |

Elke schoen moet zijn eigen inner en outer cage bevatten.

## [Blender exportinstellingen](#blender-exportinstellingen)[](#blender-exportinstellingen)

Blender stelt je in staat om je gelaagde accessoire te exporteren als een .fbx  of .gltf  bestand. Als je het exporteert als een .fbx  bestand, maak jezelf dan vertrouwd met [Blender's FBX-schaal](/docs/nl-nl/art/blender#schaal-aanpassen-fbx)  om ervoor te zorgen dat je het model op de juiste schaal in Studio importeert.

Om je gelaagde accessoire in Blender als een .fbx  bestand te exporteren:

1.

Klik in de bovenbalk op Bestand  > Exporteren  > FBX (.fbx) . Het venster Blender-bestandsweergave  wordt weergegeven.

2.

Stel aan de rechterkant Padmodus  in op Kopie , en schakel de knop Ingebedde texturen  in.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Export-Settings-1.png)

3.

Stel in de sectie Transformeren  Toepassen schalingen  in op FBX-eenheidsschaal . Als je problemen ondervindt met de schaal bij importeren, zie dan [Blender FBX-schaal](/docs/nl-nl/art/blender#schaal-aanpassen-fbx)  voor alternatieve benaderingen.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Export-Settings-5.png)

4.

Schakel in de sectie Armature  Voeg bladbeenderen toe  uit.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Export-Settings-3.png)

5.

Klik op de knop Exporteer FBX  en sla de .fbx  op in de directory van jouw keuze.

Je hebt nu een .fbx  bestand dat je kunt [importeren in Studio](/docs/nl-nl/avatar/layered-accessories/import)  als een [Model](/docs/nl-nl/reference/engine/classes/Model)  gelaagd accessoire. Zodra het gelaagde accessoire in Studio is, kun je de [Accessoire-pasvormtool](/docs/nl-nl/avatar/accessory-fitting-tool)  gebruiken om het model om te zetten in een accessoire.

## [Maya exportinstellingen](#maya-exportinstellingen)[](#maya-exportinstellingen)

Om je gelaagde accessoire in Maya als een .fbx  bestand te exporteren:

1.

Klik in de bovenbalk op Bestand  > Alles exporteren . Het venster Alles exporteren  wordt weergegeven.

2.

Klik onderaan het venster op de dropdown Bestanden van type , en selecteer FBX-export .

3.

Navigeer aan de rechterkant van het venster naar de sectie Opties... .

4.

Schakel in de sectie Geometrie  Vloeiende mesh  en Gereferentie-inhoud  in.

5.

Als je texturen als een .png  moet importeren, schakel dan in de sectie Ingebedde media  Ingebedde media  in.

6.

In de sectie Geavanceerde opties ,

-

Navigeer naar Eenheden , en schakel Automatisch  in.

-

Navigeer naar Asconversie , en stel de eigenschap Op-as  in op Y .

7.

Klik op de knop Alles exporteren  en sla de .fbx  op in de directory van jouw keuze.

 ![Screenshot van de exportinstellingen in Maya voor exports met animatie.](https://prod.docsiteassets.roblox.com/assets/accessories/lc-requirements-maya-settings-with-animation-layeredaccessories.png)

Je hebt nu een .fbx  bestand dat je kunt [importeren in Studio](/docs/nl-nl/avatar/layered-accessories/import)  als een [Model](/docs/nl-nl/reference/engine/classes/Model)  gelaagd accessoire. Zodra het gelaagde accessoire in Studio is, kun je de [Accessoire-pasvormtool](/docs/nl-nl/avatar/accessory-fitting-tool)  gebruiken om het model om te zetten in een accessoire.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
