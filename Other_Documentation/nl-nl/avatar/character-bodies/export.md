<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/character-bodies/export -->

Exporteer karakterlichamen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Lichamen

# Exporteer karakterlichamen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Wanneer je klaar bent om een karakterlichaam model te exporteren dat voldoet aan Roblox's [specificaties voor karakterlichamen](/docs/nl-nl/avatar/character-bodies/specifications) , is het belangrijk om de volgende vereiste informatie en stapsgewijze instructies voor de .fbx  of .gltf  exportbestanden te bekijken, zodat je creatie gebruikmaakt van alle [Importer](/docs/nl-nl/studio/importer)  functies van Studio.

Dit is vooral belangrijk voor karakterlichaam modellen omdat ze alle mesh- en textuurgegevens bevatten, inclusief de rig- en invloedgegevens die essentieel zijn voor het correct bewegen en animeren van personages op het platform.

Als je de avatar-sjabloonbestanden van Roblox gebruikt, moet je de [opruimstappen](/docs/nl-nl/art/characters/creating/combine-head-geometry)  uitvoeren zodat de assets correct gevalideerd worden.

Voor andere soorten 3D-modellen:

-

[Algemene mesh](/docs/nl-nl/art/modeling/export-requirements)  exportinstellingen.

-

[Stijve accessoire](/docs/nl-nl/avatar/rigid-accessories/export)  exportinstellingen.

-

[Gelaagde accessoire](/docs/nl-nl/avatar/layered-accessories/export)  exportinstellingen.

## [Vereisten](#vereisten)[](#vereisten)

Voordat je je aangepaste karakterlichaam exporteert:

-

Zorg ervoor dat je alleen de door Roblox ondersteunde objecten exporteert die verband houden met je model. Als je modifiers op je mesh of projectobjecten hebt, zorg er dan voor dat je deze toepast of verwijdert voordat je exporteert.

-

Terwijl je mesh-objecten binnen een armature-object moeten worden geparent, kun je ook je buitenste cage-objecten aan een enkel leeg object parenten om je werkruimte te vereenvoudigen.

 ![Screenshot van een Blender-project Outliner met geparenteerde objecten samengevouwen.](https://prod.docsiteassets.roblox.com/assets/art/avatar/Character-Data-Model-Collapsed.png)

-

Zorg ervoor dat je in het cage-parentobject een [buitenste cage](/docs/nl-nl/avatar/character-bodies/specifications#buitenste-kooien)  hebt voor elk van je 15 lichaamsdelen met de juiste naamgeving.

 ![Screenshot van de 15 buitenste cage-meshes die je moet opnemen bij een karakterexport.](https://prod.docsiteassets.roblox.com/assets/art/avatar/Character-Data-Model-Cages.png)

-

Zorg ervoor dat je in het armature-object alle [15 mesh-objecten](/docs/nl-nl/avatar/character-bodies/specifications#lichaamsdelen)  en [19 bijlagen](/docs/nl-nl/avatar/character-bodies/specifications#bevestigingen)  met de juiste naamgeving opneemt.

 ![Screenshot van 15 kindobjecten die binnen een Armature-object zijn geparent.](https://prod.docsiteassets.roblox.com/assets/art/avatar/Character-Data-Model-Joints.png)

Voor meer informatie over ondersteunde modelobjecten en de juiste configuratie, zie [Karakter specificaties](/docs/nl-nl/avatar/character-bodies/specifications) .

-

Wanneer je karakterlichamen met animatie of FACS-animatie exporteert, zorg er dan voor dat je animatietijdlijn Start  en Eind  het volledige bereik van je animaties omvat.

 ![Inzoomen op de Blender-animatietrack die een Start-waarde van 0 en een Eind-waarde van 308 aangeeft.](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Blender-Animation-Start-End.png)

## [Blender exportinstellingen](#blender-exportinstellingen)[](#blender-exportinstellingen)

Blender stelt je in staat om je karakterlichaam te exporteren als een .fbx  of .gltf  bestand. Als je het exporteert als een .fbx  bestand, maak dan kennis met [Blender's FBX-schaal](/docs/nl-nl/art/blender#schaal-aanpassen-fbx)  om ervoor te zorgen dat je het model op de juiste schaal in Studio importeert.

Om je karakterlichaam in Blender als een .fbx  bestand te exporteren:

1.

Klik in de bovenbalk op Bestand  > Exporteren  > FBX (.fbx) . Het venster Blender-bestandsweergave  wordt weergegeven.

2.

Stel aan de rechterkant Padmodus  in op Kopie , en schakel de knop Inbedden van texturen  in.

3.

In de sectie Inbegrepen , schakel Aangepaste eigenschappen  in.

4.

In de sectie Transformatie , stel Toepassen schalingen  in op FBX-eenheidsschaal . Als je problemen ondervindt met schaling bij import, zie [Blender FBX-schaal](/docs/nl-nl/art/blender#schaal-aanpassen-fbx)  voor alternatieve benaderingen.

5.

In de sectie Armature , schakel Voeg bladbeenderen toe  uit.

6.

Schakel Animatie  in en breid deze uit, en:

1.

Schakel NLA-strips , Alle acties  en Forceer start/eind keyframes  uit.

Zorg ervoor dat de animatietijdlijn van je project het juiste Start  en Eind  bereik van al je keyframes heeft.

2.

Stel Vereenvoudigen  in op 0.0 .

7.

Klik op de knop Exporteer FBX  en sla de .fbx  op in de directory van jouw keuze.

 ![Screenshot van de Blender-exportinstellingen](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Export-Settings.png)

Je hebt nu een .fbx  bestand dat je kunt [importeren in Studio](/docs/nl-nl/avatar/character-bodies/import)  als een [Model](/docs/nl-nl/reference/engine/classes/Model)  karakter. Zodra het karakterlichaam in Studio is, kun je:

-

[Test je karakter](/docs/nl-nl/avatar/character-bodies/test)  met verschillende Studio-tools en workflows.

-

[Upload het karakter](/docs/nl-nl/marketplace/publish-to-marketplace)  naar de Marketplace.

-

Gebruik het karakter in een bestaand gameproject door een [HumanoidDescription](/docs/nl-nl/characters/appearance#handmatig-aangepast-uiterlijk)  toe te passen op het [Model](/docs/nl-nl/reference/engine/classes/Model)  object.

-

[Sla het karakter op](/docs/nl-nl/projects/assets/toolbox)  in je Toolbox  om het binnen een van je games te gebruiken of te delen met andere makers.

## [Maya exportinstellingen](#maya-exportinstellingen)[](#maya-exportinstellingen)

Om je karakterlichaam in Maya als een .fbx  bestand te exporteren:

1.

Klik in de bovenbalk op Bestand  > Exporteer alles . Het venster Exporteer alles  wordt weergegeven.

2.

Klik onderaan het venster op de dropdown Bestanden van type , en selecteer FBX-export .

3.

Navigeer aan de rechterkant van het venster naar de sectie Opties... .

4.

In de sectie Geometrie , schakel Vloeiende mesh  en Gereferentie assetinhoud  in.

5.

In de sectie Animatie , schakel Animatie  in. Avatar-personages met [dynamische hoofden](/docs/nl-nl/avatar/dynamic-heads)  vereisen animatiegegevens.

6.

Schakel Bake animatie  in.

7.

Als je texturen als een .png  moet importeren, schakel dan in de sectie Inbedden van media  Inbedden van media  in.

8.

In de sectie Geavanceerde opties ,

1.

Navigeer naar Eenheden , en schakel Automatisch  in.

2.

Navigeer naar Asconversie , en stel de eigenschap Op-as  in op Y .

9.

Klik op de knop Exporteer alles  en sla de .fbx  op in de directory van jouw keuze.

 ![Screenshot van de Maya-exportinstellingen voor exports met animatie.](https://prod.docsiteassets.roblox.com/assets/accessories/lc-requirements-maya-settings-with-animation.png)

Je hebt nu een .fbx  bestand dat je kunt [importeren in Studio](/docs/nl-nl/avatar/character-bodies/import)  als een [Model](/docs/nl-nl/reference/engine/classes/Model)  karakter. Zodra het karakterlichaam in Studio is, kun je:

-

[Test je karakter](/docs/nl-nl/avatar/character-bodies/test)  met verschillende Studio-tools en workflows.

-

[Upload het karakter](/docs/nl-nl/art/accessories/creating-rigid/publishing)  naar de Marketplace.

-

Gebruik het karakter in een bestaand gameproject door een [HumanoidDescription](/docs/nl-nl/characters/appearance#handmatig-aangepast-uiterlijk)  toe te passen op het [Model](/docs/nl-nl/reference/engine/classes/Model)  object.

-

[Sla het karakter op](/docs/nl-nl/projects/assets/toolbox)  in je Toolbox  om het binnen een van je games te gebruiken of te delen met andere makers.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
