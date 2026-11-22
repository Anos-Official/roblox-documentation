<!-- Source: https://create.roblox.com/docs/nl-nl/art/accessories/creating/modeling-setup -->

Modellering setup | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Modellering setup

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Modellering, soms bekend als sculpting , is het proces van het creëren en vormen van de 3D-geometrie van een object. In deze tutorial gebruik je een van de sjabloonbestanden van Roblox om de initiële vorm van een t-shirt te creëren, en voeg je unieke en kleding-specifieke aanpassingen toe aan de geometrie voor je eigen ontwerp. Je kunt de technieken en processen in deze tutorial verder toepassen om elk ander type kleding te creëren, zoals broeken, rokken en schoenen.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Modeling-Mannequin-Start.png) Basis Mannequin met door Roblox geleverde cage meshes

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Modeling-Complete-2.png) Gesculpte kledingmesh voor een shirt met lange mouwen

De volgende vier modelleringsecties behandelen de volgende processen:

1.

Je project opzetten en je basismesh creëren.

2.

De gedupliceerde mesh ontdoen van extra attributen.

3.

De vorm bijsnijden om overeen te komen met het gewenste kledingtype.

4.

De vertices van je kledingvorm toevoegen en gladstrijken.

5.

De kleding schalen en positioneren op de mannequin.

6.

Stof en andere details op het meshobject sculpten.

7.

De gaten in je mesh sluiten, zodat deze waterdicht is.

## [Zet mesh op](#zet-mesh-op)[](#zet-mesh-op)

Om je project te starten, download en open je het Clothing_Cage.blend  project van Roblox en begin je met het opzetten van je basisprojectobjecten.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Modeling-Cages-Selected.png) 3D viewport - gedupliceerd cage meshobject

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Modeling-Cage-Copied.png) Outliner - gedupliceerd object genaamd "LongSleeve"

Om je project en je initiële meshobject op te zetten:

1.

Download en open het [Clothing_Cage.blend](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Clothing_Cage_Templates.zip)  project dat de binnen- en buiten-cage mesh bevat die je als tijdelijke mannequins zult gebruiken.

2.

Navigeer naar Bestand  > Opslaan als , en sla het project op met een nieuwe naam. Dit wordt je hoofd Blender-project voor je gelaagde accessoire.

3.

Kopieer en plak het InnerCage  object in de Outliner om het te dupliceren.

4.

Met het gedupliceerde object actief, klik met de rechtermuisknop in de viewport, en selecteer Ouder  > Verwijder en behoud transformatie  in het contextmenu.

5.

Terug in de Outliner,

1.

Klik met de rechtermuisknop en verwijder het extra Clothing Cages.001  object.

2.

Hernoem het gedupliceerde object naar LongSleeve .

3.

Hernoem de originele cages naar LongSleeve_OuterCage  en LongSleeve_InnerCage , respectievelijk, en verberg ze voorlopig.

## [Verwijder extra attributen](#verwijder-extra-attributen)[](#verwijder-extra-attributen)

De cage meshobjecten in de sjabloon bevatten enkele hulpkleur eigenschappen voor vertices die verwijderd moeten worden van je kledingmesh. Als ze blijven staan, kunnen de vertexkleuren in conflict komen met de textuur van het object na importeren in Studio.

Om extra attribuutgegevens te verwijderen:

1.

Met LongSleeve  actief, navigeer naar de Eigenschappen Editor > Objectgegevens eigenschappen  tab > Kleur Attributen .

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating/Modeling-Clear-Vertex-Colors.png)

2.

Met colorSet1  geselecteerd, verwijder het door op de –  knop te drukken.

[Volgende](/docs/nl-nl/art/accessories/creating/trimming)[Vorige](/docs/nl-nl/art/accessories/creating)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
