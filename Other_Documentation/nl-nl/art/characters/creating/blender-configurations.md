<!-- Source: https://create.roblox.com/docs/nl-nl/art/characters/creating/blender-configurations -->

Blender-configuratie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Blender-configuratie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Blender-projectbestanden van elk sjabloon bevatten aanvullende hulpprogramma-configuraties die niet zijn opgenomen in de ruwe .fbx  sjabloonbestanden. Als je van plan bent om Blender te gebruiken voor je proces van het maken van personages, is het belangrijk om de toevoegingen in de .blend  versies van het sjabloon en wat ze doen te begrijpen.

## [Hiërarchie](#hiërarchie)[](#hiërarchie)

Het volgende is een overzicht van wat er in elk Blender-sjabloonbestand is opgenomen:

-

Cage : Bevat de 15 buitenste lichaamshulpmiddelen van het personage.

-

Joints : Het bovenliggende armatuurobject bevat de volgende objecten:

-

Bones  die het rigging-armatuur van het personage vormen.

-

_Geo  mesh-objecten die het uiterlijk van de avatar vormen.

-

_Att  bijlage-objecten die definiëren waar accessoires worden bevestigd wanneer ze zijn uitgerust.

-

Animatiedata  voor het opslaan van gezichtsanimatiedata en poses.

-

Fill  en Sun : Deze objecten worden gebruikt om verlichting te bieden, zodat je je personages kunt bekijken in neutrale verlichting, vergelijkbaar met een Studio-basisplaat. Deze maken geen  deel uit van het avatar-personage.

![Hoofd-gerelateerde Meshes](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Blender-Project-Objects.png) Blender Project Hiërarchie

## [Uitgeschakelde objecten](#uitgeschakelde-objecten)[](#uitgeschakelde-objecten)

Wanneer je de sjabloonprojectbestanden voor Blender gebruikt, merk je misschien dat sommige objecten, zoals bijlage-objecten, permanent verborgen zijn in de Viewport, zelfs wanneer je het pictogram Verbergen in Viewport  ![](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Visibility-Icon.png)  schakelt. Aangezien bijlage-objecten vaak pas aan het einde van het proces van het maken van personages worden gewijzigd, hebben deze objecten Uitschakelen in Viewport  ![](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Disabled-Icon.png)  ingeschakeld om de organisatie van je project efficiënter te maken, vooral bij het bulkgewijs schakelen van de zichtbaarheid van objecten.

Als je toegang nodig hebt tot uitgeschakelde objecten, gebruik dan de volgende instructies om de Uitschakelen in Viewport  schakelaar te openen:

1.

Klik in je Outliner op de Filter  dropdown.

 ![](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Outliner-Filter.png)

2.

Schakel de Uitschakelen in Viewport  filter in.

 ![](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Outliner-Menu.png)

3.

Het Uitschakelen in Viewport  pictogram ![](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Disabled-Icon.png)  verschijnt nu naast elk object in de Outliner. Schakel het pictogram om de uitgeschakelde status voor je objecten te wijzigen.

 ![](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Outliner-Disabled-Enabled.png)

## [Aangepaste huidtinten](#aangepaste-huidtinten)[](#aangepaste-huidtinten)

De Blender-projectbestanden bevatten een shaderconfiguratie waarmee je aangepaste huidtinten kunt bekijken, vergelijkbaar met hoe ze worden weergegeven in Roblox als gebruikers hun huidtinten aanpassen.

Texturen met volledige of gedeeltelijke transparantie laten de onderliggende [Part.Color](/docs/nl-nl/reference/engine/classes/Part#Color)  door de toegepaste textuur heen zien, waardoor een gebruiker zijn avatar-personage kan personaliseren met aangepaste huidtinten.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/templates/Texture-Map.png)  Een voorbeeld van een textuurkaart die lage opaciteit gebruikt om de onderliggende huidkleur te onthullen en volledige opaciteit om een volledig ondoorzichtige kleur toe te passen op de onderkleding, wenkbrauwen, mond en ogen.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/templates/Custom-Skin-Tones.png) Hetzelfde avatar-personage met dezelfde textuurkaart. Elk model heeft verschillende onderliggende deelkleuren, behalve waar de textuurkaart een volledige kleur toepast.

### [Voorbeeld huidtinten](#voorbeeld-huidtinten)[](#voorbeeld-huidtinten)

Je moet Blender 3.4+  gebruiken om ervoor te zorgen dat de hulpshaderconfiguraties correct worden weergegeven. Als je een eerdere versie van Blender gebruikt, worden texturen mogelijk niet zoals verwacht weergegeven.

Het Blender-projectbestand bevat shaderconfiguraties waarmee je aangepaste huidtinten kunt bekijken, vergelijkbaar met hoe ze verschijnen in Studio. Deze aangepaste kleuren worden niet geëxporteerd met het model, maar kunnen je een snelle visuele referentie bieden voor hoe een aangepaste huidkleur en textuur eruit zou kunnen zien in Roblox.

Voor deze Blender-shaderconfiguratie, houd rekening met de volgende vereisten:

-

Je moet overschakelen naar de Viewport Shading  modus om texturen correct weer te geven.  ![](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Viewport-Shading-Setting.png)

-

Wanneer je texturen verwisselt, keert de kleurenruimte van de normaalmap terug naar SRGB  in plaats van NonColor . Als dit gebeurt, moet je het mogelijk terug veranderen zodat de normaalmap correct wordt weergegeven.

Om de huidtint van je personage in Blender te bekijken:

1.

Selecteer in Layout  een geometrisch object, zoals Head_Geo .

2.

Navigeer naar het tabblad Shading , stel in het node-paneel het dropdownmenu Shader Type  in op Object .

3.

Zoek de PartColor  node die is verbonden met de Mix  node, kies vervolgens een kleur en waarde op de node om een referentie voor een aangepaste huidtint toe te passen.

### [Exportinstellingen](#exportinstellingen)[](#exportinstellingen)

Hoewel de huidtintvoorbeeld een cruciaal element is om de kleur- en tintcompatibiliteit van je sjablonen in Roblox te verifiëren, voorkomt het dat je kleurtextuurkaart automatisch wordt verpakt met het uiteindelijke .fbx  bestand. Er zijn twee manieren om dit op te lossen voordat je je model exporteert:

-

Koppel in het tabblad Shading  de Mix  node los en vervang deze door de ColorMap  node.

-

Exporteer je texturen handmatig als afzonderlijke afbeeldingsbestanden en voeg ze later toe in Studio.

Voor instructies over hoe je een van beide exportwerkstromen kunt uitvoeren, zie [Exporteer texturen](/docs/nl-nl/art/characters/creating/export-textures) .

## [Scalemaat](#scalemaat)[](#scalemaat)

Je kunt deze sectie overslaan als je een downloadbaar Blender-sjabloon gebruikt. De .blend  versies van de sjablonen bevatten al veel van de projectinstellingen die vereist zijn bij het instellen van een Blender-projectconfiguratie.

Bij het maken van Roblox-assets in een modeltoepassing is het belangrijk om ervoor te zorgen dat je .fbx  exports correct schalen. Stel tijdens de export Transform  > Toepassen Schalen  in op FBX Eenheidsschaal .

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Blender-Export-Settings-5.png)

Als je problemen ondervindt met schaling bij import, zie [Blender FBX schaling](/docs/nl-nl/art/blender#schaal-aanpassen-fbx)  voor alternatieve benaderingen.

## [Animatiebereik](#animatiebereik)[](#animatiebereik)

Je kunt deze sectie overslaan als je een downloadbaar Blender-sjabloon gebruikt. De .blend  versies van de sjablonen bevatten al veel van de projectinstellingen die vereist zijn bij het instellen van een Blender-projectconfiguratie.

Voor aangepaste personages met gezichtsanimatie, zorg ervoor dat het tijdlijnbereik is ingesteld tussen 0 en 330:

1.

Klik in de rechterbovenhoek van het Animatiepaneel en stel Start  in op 0 .

2.

Klik in de rechterbovenhoek van het Animatiepaneel en stel Einde  in op 330 .

 ![](https://prod.docsiteassets.roblox.com/assets/art/blender-ui/Timeline-Frames.png)

Nadat je je projectinstellingen hebt gewijzigd, kun je deze instellen als je standaard Blender-projectinstellingen door naar Bestand  > Standaarden  > Opslaan Startup-bestand  te navigeren.

[Volgende](/docs/nl-nl/art/characters/creating/modeling-best-practices)[Vorige](/docs/nl-nl/art/characters/creating/head-objects)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
