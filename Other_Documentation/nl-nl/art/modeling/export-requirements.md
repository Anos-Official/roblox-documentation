<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/export-requirements -->

Exportinstellingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Modellering

# Exportinstellingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Exporteer je mesh of model als een .fbx  om te profiteren van alle 3D-importfuncties van Studio. Bij het riggen of skinnen van een model bevat een .fbx -export zowel de rig als de invloedgegevens die je later nodig hebt om te [importeren](/docs/nl-nl/parts/meshes#importeren-van-meshes)  in Studio.

Controleer of je model voldoet aan de [modelleerspecificaties](/docs/nl-nl/art/modeling/specifications)  van Roblox voordat je exporteert om compatibiliteit met Studio te waarborgen. Specifieke soorten activa, zoals personages en accessoires, hebben aanvullende specificaties:

Als je andere soorten 3D-modellen maakt:

-

Voor stijve accessoires, zie [accessoirespecificaties](/docs/nl-nl/avatar/rigid-accessories/specifications)  en [exportinstellingen voor accessoires](/docs/nl-nl/avatar/rigid-accessories/export) .

-

Voor gelaagde accessoires, zie [specificaties voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications)  en [exportinstellingen voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/export) .

-

Voor avatarpersonages, zie [avatarspecificaties](/docs/nl-nl/avatar/character-bodies/specifications)  en [exportinstellingen voor avatars](/docs/nl-nl/avatar/character-bodies/export) .

## [Blender](#blender)[](#blender)

Om het .fbx -bestand in Blender te exporteren:

1.

Klik in de bovenbalk op Bestand . Een pop-upmenu verschijnt.

2.

Selecteer Exporteren , vervolgens FBX (.fbx) . Het Blender Bestandsweergave -venster verschijnt.

3.

Aan de rechterkant, wijzig Padmodus  in Kopie , en schakel de knop Inbedden van texturen  in.

 ![Blender export zijbalk die Padmodus toont ingesteld op Kopie en de knop Inbedden van texturen ingeschakeld.](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Export-Settings-1.png)

4.

Stel Transformeren  > Schaal toepassen  in op FBX Eenheidsschaal . Als je problemen ondervindt met schaling bij importeren, zie [Blender FBX-schaal](/docs/nl-nl/art/blender#schaal-aanpassen-fbx)  voor alternatieve benaderingen.

 ![Blender export zijbalk die Schaal toepassen toont ingesteld op FBX Eenheidsschaal.](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Export-Settings-5.png)

5.

Onder de sectie Armature , schakel Voeg bladbeenderen toe  uit.

 ![Blender export zijbalk die Transformeer Schaal toont ingesteld op .01](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Export-Settings-3.png)

6.

Tenzij je inhoud met animatiesleutels exporteert, zoals een loopcyclus of een personage met [gezichtsanimatiegegevens](/docs/nl-nl/avatar/dynamic-heads) , schakel Bake Animatie  uit.

 ![Blender export zijbalk die Voeg bladbeenderen toe als uitgevinkt toont](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Export-Settings-4.png)

7.

Klik op de knop Exporteer FBX .

## [Maya](#maya)[](#maya)

Om een mesh in Maya als een .fbx -bestand te exporteren:

1.

Klik in de bovenbalk op Bestand . Een pop-upmenu verschijnt.

2.

Selecteer Alles exporteren . Het Alles exporteren -venster verschijnt.

3.

Klik onderaan het venster op de dropdown Bestanden van type , en selecteer FBX-export .

4.

Aan de rechterkant van het venster, navigeer naar de sectie Opties... .

5.

In de sectie Geometrie , schakel Vloeiende Mesh  en Gereferenceerde Activa-inhoud  in.

6.

In de sectie Animatie , schakel Animatie  uit, tenzij je een animatie naar Studio moet importeren. Sommige avataractiva vereisen animatie.

1.

Als je animatie exporteert, schakel dan Bake Animatie  in.

7.

Als je texturen als een .png  moet importeren, schakel dan in de sectie Inbedden van media  Inbedden van media  in.

8.

In de sectie Geavanceerde opties ,

-

Navigeer naar Eenheden , en schakel Automatisch  in.

-

Navigeer naar Asconversie , en stel de eigenschap Opwaartse As  in op Y .

9.

Klik op de knop Alles exporteren .

 ![Maya export zijbalk die Bake Animatie als uitgevinkt toont](https://prod.docsiteassets.roblox.com/assets/accessories/lc-requirements-maya-settings.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
