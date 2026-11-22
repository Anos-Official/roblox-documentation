<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/makeup/reassign-textures -->

Herassigneren van texturen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Make-up

# Herassigneren van texturen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Om aangepaste make-up texturen te importeren, gebruik je Blender of Maya om de bestaande texturen op de referentietemplate hoofd te herassigneren naar je eigen aangepaste textuurafbeeldingen. Nadat je de texturen hebt vervangen, exporteer je het hele hoofdmodel en [importeer](/docs/nl-nl/avatar/makeup/import)  je het in Studio.

De volgende informatie is specifiek  voor het toepassen van make-up texturen op Roblox's [template hoofden](/docs/nl-nl/avatar/makeup#sjabloonhoofden)  die al PBR textuurnodes toegewezen hebben. Voor informatie over het toewijzen van texturen vanaf nul, zie [Texturen toewijzen in Blender en Maya](/docs/nl-nl/art/modeling/assign-textures) .

## [Blender](#blender)[](#blender)

De video-presentator kiest ervoor om alle bestaande afbeeldingslinks te wissen door naar Bestand  > Externe Gegevens  > Hulpmiddelen Uitpakken  te navigeren en Verwijder Pack  te selecteren. Dit is een methode om alle afbeeldingen te ontkoppelen in plaats van individueel texturen te ontkoppelen zoals stap #5 in de volgende instructies.

Om texturen in Blender te herassigneren:

1.

Pak het [Blender referentie hoofd bestand](/docs/nl-nl/avatar/makeup#sjabloonhoofden)  uit en open het.

2.

Schakel over naar het Shading  tabblad.

3.

In de Outliner, vouw de Make-up collectie uit en selecteer het gezichtsgedeelte waarvoor je texturen wilt vervangen.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Select-Region.png)

4.

Selecteer in de nodegraf de textuurafbeelding die je wilt bijwerken, zoals Neutral_FaceDecal_ALB.png

5.

Klik op de X  om de bestaande afbeeldingstoewijzing te verwijderen.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Unlink-Image.png)

6.

Klik op het mapicoon om een nieuwe afbeelding te doorbladeren.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Assign-New.png)

7.

Herhaal dit voor alle PBR texturen die je wilt vervangen.

8.

Verwijder eventuele textuurnodes die je niet gebruikt.

9.

Controleer of je uiteindelijke nodegraf er vergelijkbaar uitziet met de originele referentie zonder dat er iets onbedoeld ontbreekt.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Expected-Nodes.png)

Nadat je je PBR texturen hebt vervangen, exporteer je het hele template bestand als een .fbx  of .gltf . Alle 3D-modellering [exportvereisten](/docs/nl-nl/art/modeling/export-requirements)  zijn van toepassing, maar er zijn een paar make-up specifieke instellingen die je moet configureren:

1.

In het exportbestand browser venster, navigeer naar de sectie Inbegrepen , schakel dan de Aangepaste Eigenschappen  toggle in voor make-up UV gegevensoverdracht.

2.

In de sectie Armature , schakel Alleen Deformeren Botten  in om ervoor te zorgen dat je exportbestand skinninggegevens voor wenkbrauwen en wimpers bevat.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Blender-MakeupExport.png) Alle noodzakelijke Blender exportinstellingen voor make-up

## [Maya](#maya)[](#maya)

Om texturen in Maya te herassigneren:

1.

Pak het [Maya referentie hoofd bestand](/docs/nl-nl/avatar/makeup#sjabloonhoofden)  uit en open het.

2.

Klik in de Statusbalk nabij de bovenkant van de standaardlay-out op het Hypershade icoon.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Select-Hypershade.png)

3.

Beweeg je muis over de textuur van het materiaal dat je wilt vervangen.

4.

Klik en houd de rechtermuisknop ingedrukt en sleep de selector naar Graph Network .

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Select-Graph-Network.png)

5.

Klik in de nieuw weergegeven nodegraf op de Textuur Node die je wilt vervangen, zoals Neutral_Eyes_ALB.png .

6.

Navigeer in de rechter Eigenschappen Editor naar Afbeeldingsnaam en klik op het mapicoon. Een bestandsbrowser wordt weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Replace-Texture.png)

1.

Selecteer het afbeeldingsbestand dat je wilt gebruiken als vervanging.

2.

Herhaal dit voor alle PBR texturen die je wilt vervangen.

3.

Verwijder eventuele textuurnodes die je niet gebruikt.

4.

Controleer of je uiteindelijke nodegraf er vergelijkbaar uitziet met de originele referentie zonder dat er iets onbedoeld ontbreekt.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Expected-Nodes.png)

Nadat je je PBR texturen hebt vervangen, exporteer je het hele template bestand als een .fbx  of .gltf . Alle 3D-modellering [exportvereisten](/docs/nl-nl/art/modeling/export-requirements)  zijn van toepassing, maar er zijn een paar make-up specifieke instellingen die je moet configureren:

1.

In het exportbestand browser venster, navigeer naar de sectie Gedeformeerde Modellen .

2.

Schakel de Huid  toggle in om ervoor te zorgen dat je exportbestand skinninggegevens voor wenkbrauwen en wimpers bevat.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Maya-MakeupExport.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
