<!-- Source: https://create.roblox.com/docs/nl-nl/art/accessories/rig-and-cage-existing-models -->

Rigging en caging modellen (Blender) | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Avataritems

# Rigging en caging modellen (Blender)

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt een externe modelleringstool gebruiken, zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) , om een bestaand 3D-object te wijzigen in een gelaagd 3D-model dat je kunt [importeren en omzetten](/docs/nl-nl/avatar/accessory-fitting-tool)  in Studio als een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory) . Om een gelaagd model te maken, moet je een 3D-model parenten  (Blender) of binden  (Maya) aan een mannequin-armatuur en vervolgens twee extra meshes aanpassen zodat ze passen rond het binnenste en buitenste oppervlak van het accessoiremodel.

Deze gids behandelt de basisworkflow voor het omzetten van een 3D-model in een gelaagd model in Blender met de volgende stappen:

1.

[Importeren](#importeren)  van een 3D-asset in een sjabloon Blender-projectbestand.

2.

[Parenten](#parent-en-gewicht)  van het geïmporteerde mesh-object aan de armatuur rig van het projectbestand met de automatische gewichtenfunctie van Blender.

1.

Handmatig skinnen wordt niet behandeld, zie [Skin een eenvoudig mesh](/docs/nl-nl/art/modeling/skin-a-simple-mesh)  voor een overzicht van handmatig skinnen.

3.

[Bewerken](#bewerk-binnenste-en-buitenste-cage-meshes)  van de binnenste en buitenste cage meshes om het binnenste en buitenste oppervlak van het model weer te geven.

Een volledige lijst van assetvereisten voor een gelaagd model is te vinden in [Gelaagde model specificaties](/docs/nl-nl/avatar/rigid-accessories/specifications) .

Deze gids gebruikt [Blender versie 3.0](https://www.blender.org/download/releases/3-0/) . Als je een andere versie van Blender gebruikt, kunnen er kleine verschillen zijn in de gebruikersinterface en instellingen.

## [Importeren](#importeren)[](#importeren)

Stel het project in door het [rig-sjabloonproject](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Rig_and_Attachments_Templates.zip)  te openen en het [voorbeeld accessoiremodel](https://prod.docsiteassets.roblox.com/assets/accessories/reference-files/Tshirt-model.fbx)  te importeren.

Om het accessoiremodel te importeren en te parenten:

1.

Open in Blender het [rig-sjabloonproject](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Rig_and_Attachments_Templates.zip) . Dit bestand bevat de standaard armatuur die nodig is voor gelaagde accessoires.

 ![Blender Mannequin Template Project](https://prod.docsiteassets.roblox.com/assets/accessories/lc-blender-template-opened.png)

2.

Schakel in de Outliner het Verberg-icoon in om visueel alle niet-armatuurobjecten in je werkruimte te verwijderen, zoals Bijlagen.

3.

Selecteer in het Bestandsmenu Importeren  en klik op FBX (.fbx) . Selecteer het accessoiremodelbestand dat je op de mannequin wilt passen. Het accessoire verschijnt in de werkruimte en, afhankelijk van hoe het asset is gemodelleerd, moet het mogelijk worden vergroot of aangepast om op de mannequin te passen.

## [Parent en gewicht](#parent-en-gewicht)[](#parent-en-gewicht)

Voor dit basisaccessoire, parent het geïmporteerde mesh aan de sjabloon mannequin-armatuur met de [Automatische Gewichten](https://docs.blender.org/manual/en/latest/animation/armatures/skinning/parenting.html#with-automatic-weights)  functie van Blender. Het parenten van het accessoiremodelmesh aan de armatuur op deze manier stelt het 3D-model in staat om natuurlijk te bewegen en te vervormen met het karakter in Studio.

Complexe kleding- en accessoire-items met bewegende delen kunnen meer nauwkeurige skinning vereisen met Blender's [Weight Painting](https://docs.blender.org/manual/en/3.5/grease_pencil/modes/weight_paint/introduction.html#weight-paint)  of andere skinning-tools. Zie [Skin een eenvoudig mesh](/docs/nl-nl/art/modeling/skin-a-simple-mesh)  voor een voorbeeld van handmatig skinnen.

Om het mesh-object met de mannequin-armatuur te parenten:

1.

Verberg in de Outliner tijdelijk beide Cage-objecten om de Armatuur zichtbaar te maken door het Verberg-icoon in te schakelen.

2.

Klik in de Werkruimte op het mesh-object, houd Shift  ingedrukt en klik  op de armatuur van de mannequin.

3.

Klik met de rechtermuisknop, of gebruik Ctrl P  (⌘ P ) om het accessoire aan de armatuur te parenten door Automatische Gewichten  te selecteren.

4.

Verminder visuele rommel door alle objecten behalve de cages  en model  te verbergen. Klik op het ![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-blender-hide-symbol.png)  symbool naast het object in het Outliner-paneel.

## [Bewerk binnenste en buitenste cage meshes](#bewerk-binnenste-en-buitenste-cage-meshes)[](#bewerk-binnenste-en-buitenste-cage-meshes)

Nadat je je kledingstuk hebt geparent en gewogen, kun je beginnen met het toevoegen van de cage meshes aan je kleding om de binnenste en buitenste oppervlakken van je kleding aan te geven.

Bij het opzetten van de cages moet het accessoiremodel bovenop de binnenste cage passen en moet de buitenste cage worden aangepast om strak over het modelobject te passen.

Je kunt deze twee full-body meshes snel toevoegen vanuit de [Clothing_Cage_Template.blend](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Clothing_Cage_Templates.zip)  in je bestaande project.

Verwijder geen vertices of wijzig de UV's op de Binnenste of Buitenste Cages, aangezien dit fouten kan veroorzaken bij het importeren in Studio of bij het uitrusten op een karakter.

Om snel kledingcages aan je project toe te voegen:

1.

Download het [Clothing_Cage_Template.blend](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Clothing_Cage_Templates.zip)  project.

2.

Schakel in je huidige Blender-project over naar Objectmodus en navigeer naar Bestand  > Append . Een bestandsbrowser verschijnt.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-blender-append.png)

3.

Klik op het Clothing_Cage_Template.blend-bestand en navigeer naar de Object -map.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-blender-append-cages.png)

4.

Selecteer in de Object-map met Shift  zowel YourClothingName_InnerCage  als YourClothingName_OuterCage  en klik op Append . De twee cage mesh-objecten verschijnen in je project.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-blender-workspace-cages.png)

Om cages voor je accessoiremodel aan te passen:

1.

Hernoem in het Outliner-paneel de _InnerCage  en _OuterCage  meshes zodat ze overeenkomen met het geïmporteerde mesh-object (bijv. Tshirt_InnerCage, Tshirt_OuterCage). Zorg ervoor dat dit exact overeenkomt met de mesh-naam die je hebt geïmporteerd.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/lc-blender-selecting-cage-in-outlier.png)

2.

Selecteer in het Outliner-venster de _OuterCage mesh en schakel over naar Bewerkmodus  Tab .

3.

Schakel in de Viewport de X-Ray -weergave en Materialenweergave  in om de zichtbaarheid en toegang tot de vertices van de buitenste cage mesh te verbeteren.

4.

Pas terwijl je in de Bewerken-modus de vertices aan met de Bewerken-modus-tools zodat de Buitenste Cage de bovenkant van het accessoire volledig bedekt.

Probeer bij het manipuleren van vertices elke face (de ruimte tussen vertices) consistent van grootte te houden en symmetrie waar mogelijk te behouden. Gebruik de symmetrie-schakelaars rechtsboven in de Viewport wanneer van toepassing.

Een voltooide buitenste cage moet het accessoire volledig bedekken met minimale extra ruimte. Ter vergelijking kun je een [voltooid gecaged versie](https://prod.docsiteassets.roblox.com/assets/accessories/reference-files/Tshirt-caged.fbx)  van het Tshirt-model downloaden.

Wanneer je klaar bent met het cagen en modelleren van je asset, zie [Exportvereisten](/docs/nl-nl/art/modeling/export-requirements#blender)  voor details over het exporteren van het model vanuit Blender.

Na het exporteren, zie [Accessoire Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  en [Tutorial voor het omzetten van kledingaccessoires](/docs/nl-nl/art/accessories/creating/converting)  voor instructies over het importeren en omzetten van het model in een bruikbaar accessoire.

## [Tips voor het bewerken van cages](#tips-voor-het-bewerken-van-cages)[](#tips-voor-het-bewerken-van-cages)

De volgende tips kunnen nuttig zijn bij het manipuleren van je cage-vertices:

-

Schakel rechtsboven in de Viewport verschillende [Viewport Shading](https://docs.blender.org/manual/en/latest/editors/3dview/display/shading.html)  opties in, zoals Material Preview  en X-Ray , wanneer nodig om beter toegang te krijgen tot vertices en je caging-voortgang te bekijken.

-

Je kunt vertices die je momenteel niet aanpast verbergen door Verbergen  (H ) en Toon  (Alt H ; ⌥ H ) te gebruiken.

-

Meerdere vertices kunnen tegelijkertijd worden geselecteerd en aangepast. Gebruik Verplaatsen , Schaal , of andere Blender-tools om aanpassingen aan meerdere vertices tegelijk te maken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
