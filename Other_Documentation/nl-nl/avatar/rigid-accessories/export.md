<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/rigid-accessories/export -->

Exporteer rigide accessoires | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Accessories and clothing
6. /
7. Stijve accessoires

# Exporteer rigide accessoires

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Wanneer je klaar bent om een rigide accessoiremodel te exporteren dat voldoet aan de [rigide accessoire specificaties](/docs/nl-nl/avatar/rigid-accessories/specifications)  van Roblox, is het belangrijk om de volgende vereiste informatie en stapsgewijze instructies voor de .fbx  of .gltf  exportbestanden te bekijken, zodat je creatie gebruikmaakt van alle [Importer](/docs/nl-nl/studio/importer)  functies van Studio.

Dit is vooral belangrijk voor rigide accessoiremodellen omdat ze alle mesh-, textuur- en bevestigingsgegevens bevatten die essentieel zijn voor rigide accessoires om correct aan de lichamen van personages te worden bevestigd.

Als je modifiers op je mesh of projectobjecten hebt, zorg er dan voor dat je ze toepast of verwijdert voordat je exporteert.

Voor andere soorten 3D-modellen:

-

[Algemene mesh](/docs/nl-nl/art/modeling/export-requirements)  exportinstellingen.

-

[Gelaagde accessoire](/docs/nl-nl/avatar/layered-accessories/export)  exportinstellingen.

## [Blender exportinstellingen](#blender-exportinstellingen)[](#blender-exportinstellingen)

Blender stelt je in staat om je rigide accessoire te exporteren als een .fbx  of .gltf  bestand. Als je het als een .fbx  bestand exporteert, maak je dan vertrouwd met [Blender's FBX-schaal](/docs/nl-nl/art/blender#schaal-aanpassen-fbx)  om ervoor te zorgen dat je het model met de juiste schaal in Studio importeert.

Om je rigide accessoire in Blender als een .fbx  bestand te exporteren:

1.

Klik in de bovenbalk op Bestand  > Exporteren  > FBX (.fbx) . Het Blender Bestandsweergave  venster wordt weergegeven.

2.

Stel aan de rechterkant Padmodus  in op Kopie , en schakel de knop Texturen insluiten  in.

3.

Stel in de sectie Transformeren  Toepassen Schalen  in op FBX Eenheidsschaal . Als je problemen ondervindt met schalen bij het importeren, zie dan [Blender FBX-schaal](/docs/nl-nl/art/blender#schaal-aanpassen-fbx)  voor alternatieve benaderingen.

4.

Klik op de knop Exporteer FBX  en sla de .fbx  op in de directory van jouw keuze.

 ![Screenshot van Blender exportinstellingen](https://prod.docsiteassets.roblox.com/assets/accessories/rigid-accessory-blender.png)

Je hebt nu een .fbx  bestand dat je kunt [importeren in Studio](/docs/nl-nl/avatar/rigid-accessories/import)  als een [Model](/docs/nl-nl/reference/engine/classes/Model)  rigide accessoire. Zodra het rigide accessoire in Studio is, kun je de [Accessoire Pasvorm Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  gebruiken om het model om te zetten in een accessoire.

## [Maya exportinstellingen](#maya-exportinstellingen)[](#maya-exportinstellingen)

Om je rigide accessoire in Maya als een .fbx  bestand te exporteren:

1.

Klik in de bovenbalk op Bestand  > Exporteer Alles . Het Exporteer Alles  venster wordt weergegeven.

2.

Klik onderaan het venster op de dropdown Bestanden van type , en selecteer FBX-export .

3.

Navigeer aan de rechterkant van het venster naar de sectie Opties... .

4.

Schakel in de sectie Geometrie  Vloeiende Mesh  en Gerefereerde Asset Inhoud  in.

5.

Schakel in de sectie Animatie  Animatie  uit.

6.

Als je texturen als een .png  moet importeren, schakel dan in de sectie Media insluiten  Media insluiten  in.

7.

In de sectie Geavanceerde Opties ,

-

Navigeer naar Eenheden , en schakel Automatisch  in.

-

Navigeer naar Asconversie , en stel de eigenschap Opwaartse As  in op Y .

8.

Klik op de knop Exporteer Alles  en sla de .fbx  op in de directory van jouw keuze.

 ![Screenshot van Maya exportinstellingen](https://prod.docsiteassets.roblox.com/assets/accessories/lc-requirements-maya-settings.png)

Je hebt nu een .fbx  bestand dat je kunt [importeren in Studio](/docs/nl-nl/avatar/rigid-accessories/import)  als een [Model](/docs/nl-nl/reference/engine/classes/Model)  rigide accessoire. Zodra het rigide accessoire in Studio is, kun je de [Accessoire Pasvorm Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  gebruiken om het model om te zetten in een accessoire.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
