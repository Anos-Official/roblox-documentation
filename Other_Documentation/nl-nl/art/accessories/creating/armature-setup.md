<!-- Source: https://create.roblox.com/docs/nl-nl/art/accessories/creating/armature-setup -->

Armatuurinstelling | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Armatuurinstelling

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Rigging  is het proces dat het kledingobject in staat stelt om te bewegen en te vervormen met de rigging-armatuur van een Roblox-personage. In deze tutorial koppel je het t-shirt aan de door Roblox geleverde [standaard R15-rig](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  en controleer je de gegevens voor Automatische Huidoverdracht. Zorg ervoor dat je na het riggen enkele basisposes test om te controleren of je kleding correct beweegt en uitrekt met elk personage.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Texturing-Complete.png) Kledingmesh zonder rigginggegevens

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Rigging-Pose-Tests.png) Kledingmesh met rigginggegevens die pose-tests uitvoert

De volgende twee riggingsecties behandelen de volgende processen:

1.

Het downloaden en toevoegen van een standaard R15-armatuur aan je project.

2.

Het koppelen van de rig met de automatische gewichten van Blender.

3.

Het testen van poses.

## [Armatuur overdragen](#armatuur-overdragen)[](#armatuur-overdragen)

Roblox biedt basis rigging-armaturen die je in je eigen project kunt importeren. Hoewel het mogelijk is om je eigen rigs te maken, bespaart het importeren van een kant-en-klare rig met de juiste configuratie je tijd en vermindert het de kans op fouten.

Om een standaard R15-rig in je bestand te importeren:

1.

Download Roblox's [Rig_and_Attachments_Template.blend](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Rig_and_Attachments_Templates.zip) , maar open dit project niet.

2.

Ga in je huidige kledingproject terug naar de Object -modus.

3.

Navigeer naar Bestand  > Toevoegen , en selecteer het opgeslagen Rig_And_Attachments_Template.blend -bestand. Een extra mappenstructuur verschijnt.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Rigging-Append-Browser.png)

4.

Selecteer Armature  > Armature  en druk op Toevoegen . Een armatuurobject wordt aan je werkruimte toegevoegd.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Rigging-Armature-Appended.png)

5.

Heroriënteer de armatuur:

1.

Met de armatuur actief, open de zijbalk van de Item-tool .

2.

Pas de rotatie aan zodat de armatuur correct is uitgelijnd met je mesh.

3.

Na de uitlijning, navigeer naar Object  > Toepassen  > Alle Transformaties  om je nieuwe rotatiewaarden vast te leggen.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Rigging-Freeze-Transforms.png)

## [Armatuur koppelen](#armatuur-koppelen)[](#armatuur-koppelen)

Met de armatuur rig op zijn plaats, kun je de functionaliteit Koppelen met Automatische Gewichten  van Blender gebruiken om snel je t-shirtmesh als kind van de armatuur in te stellen. Deze functie past ook automatisch vertexgewicht toe, of skinning , op je mesh, wat je aanzienlijke tijd kan besparen in vergelijking met het handmatig skinnen van je kleding.

Om het t-shirt aan de rig te koppelen:

1.

Selecteer LongSleeve , houd vervolgens Shift  ingedrukt en klik op het Armature -object. Zorg ervoor dat het armatuurobject het laatste geselecteerde object is.

2.

Klik met de rechtermuisknop in de viewport en selecteer Koppelen  > Met Automatische Gewichten  in het contextmenu.

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Rigging-Auto-Weights.png)

[Volgende](/docs/nl-nl/art/accessories/creating/test-poses)[Vorige](/docs/nl-nl/art/accessories/creating/texture-painting)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
