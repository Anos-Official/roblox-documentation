<!-- Source: https://create.roblox.com/docs/nl-nl/physics/mechanical-constraints -->

Mechanische beperkingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Fysica](/docs/nl-nl/physics)
8. /
9. [Mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints)

# Mechanische beperkingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De fysica-engine bevat de volgende [Constraints](/docs/nl-nl/reference/engine/classes/Constraint)  die fungeren als conceptuele mechanische verbindingen, waaronder scharnieren, veren, touwen en meer. Daarnaast zijn er verschillende [mover-beperkingen](/docs/nl-nl/physics/mover-constraints)  beschikbaar om richtinggevende of roterende kracht uit te oefenen op [assemblages](/docs/nl-nl/physics/assemblies) .

[Balverbinding](/docs/nl-nl/physics/constraints/ball-socket)

[BallSocketConstraint](/docs/nl-nl/reference/engine/classes/BallSocketConstraint)  dwingt zijn twee bevestigingen in dezelfde positie en staat ze toe vrij te draaien om alle drie de assen, met optionele limieten om zowel kanteling als draaiing te beperken

[Scharnier](/docs/nl-nl/physics/constraints/hinge)

[HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  staat zijn twee bevestigingen toe om om één as te draaien, met optionele toegewezen kracht voor motor- of servo-gedrag

[Prismatisch](/docs/nl-nl/physics/constraints/prismatic)

[PrismaticConstraint](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  staat twee bevestigingen toe om langs één as te schuiven maar niet te draaien, met optionele toegewezen kracht voor mechanismen zoals schuifdeuren en liftplatforms

[Cilindrisch](/docs/nl-nl/physics/constraints/cylindrical)

[CylindricalConstraint](/docs/nl-nl/reference/engine/classes/CylindricalConstraint)  staat zijn bevestigingen toe om langs één as te schuiven en om een andere as te draaien, met optionele toegewezen hoek- en/of lineaire kracht

[Veer](/docs/nl-nl/physics/constraints/spring)

[SpringConstraint](/docs/nl-nl/reference/engine/classes/SpringConstraint)  past een kracht toe op zijn bevestigingen op basis van veer- en dempergedrag, met een optionele minimum/maximale lengte

[Torsieveer](/docs/nl-nl/physics/constraints/torsion-spring)

[TorsionSpringConstraint](/docs/nl-nl/reference/engine/classes/TorsionSpringConstraint)  past koppel toe op basis van een relatieve hoek en relatieve hoeksnelheid, in een poging om twee assen van twee delen samen te brengen

[Universeel](/docs/nl-nl/physics/constraints/universal)

[UniversalConstraint](/docs/nl-nl/reference/engine/classes/UniversalConstraint)  zorgt ervoor dat twee assen op twee assemblages loodrecht blijven, nuttig voor toepassingen zoals voertuigkrachttransmissie naar achterste aandrijfas, robotica en meer

[Touw](/docs/nl-nl/physics/constraints/rope)

[RopeConstraint](/docs/nl-nl/reference/engine/classes/RopeConstraint)  voorkomt dat twee bevestigingen verder uit elkaar gaan dan een gedefinieerde lengte, met optioneel gedrag als een uitbreidbare of inkrimpende lier

[Stang](/docs/nl-nl/physics/constraints/rod)

[RodConstraint](/docs/nl-nl/reference/engine/classes/RodConstraint)  houdt twee bevestigingen gescheiden door een gedefinieerde lengte, met optionele limieten op roterende kanteling

[Vlak](/docs/nl-nl/physics/constraints/plane)

[PlaneConstraint](/docs/nl-nl/reference/engine/classes/PlaneConstraint)  verplaatst twee bevestigingen naar een positie/orientatie langs een vlak, en beide bevestigingen blijven vrij om te vertalen en te draaien tenzij anders beperkt

[Las](/docs/nl-nl/physics/constraints/weld)

[WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint)  verbindt twee [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  en zorgt ervoor dat ze in dezelfde relatieve positie en oriëntatie ten opzichte van elkaar blijven, zelfs als ze elkaar niet raken

[Stijf](/docs/nl-nl/physics/constraints/rigid)

[RigidConstraint](/docs/nl-nl/reference/engine/classes/RigidConstraint)  verbindt twee [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  of [Bones](/docs/nl-nl/reference/engine/classes/Bone)  en zorgt ervoor dat ze in dezelfde relatieve positie/orientatie ten opzichte van elkaar blijven, zelfs als ze elkaar niet raken

[Geen Botsing](/docs/nl-nl/physics/constraints/no-collision)

[NoCollisionConstraint](/docs/nl-nl/reference/engine/classes/NoCollisionConstraint)  voorkomt botsingen tussen twee specifieke delen, maar die delen kunnen nog steeds botsingen registreren met de rest van de wereld

## [Beperkingen visualisatie](#beperkingen-visualisatie)[](#beperkingen-visualisatie)

To accurately visualize constraints in Studio, you can toggle the following from the View  menu or through the respective shortcut:

-

Show Welds  (Alt W  of ⌥ W ) — Toon [WeldConstraints](/docs/nl-nl/reference/engine/classes/WeldConstraint)  apart van de visualisatie van andere beperkingen.

-

Show Constraint Details  (Alt D  of ⌥ D ) — Toon volledige visuele details van niet-lasmiddelen.

In aanvulling op de bovenstaande visualisatie, kun je gekleurde omtrekken rond mechanismen (groepen onderdelen die een simulatiestap en [netwerkbezit](/docs/nl-nl/physics/network-ownership) ) delen bekijken door Mechanismen  in te schakelen vanuit de [Visualisatie Opties](/docs/nl-nl/studio/overview#visualization-options)  widget in de rechterbovenhoek van het 3D-venster.

## [Maak beperkingen](#maak-beperkingen)[](#maak-beperkingen)

Alle mechanische beperkingen moeten één of twee [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  of [Bones](/docs/nl-nl/reference/engine/classes/Bone)  verbinden, behalve voor [WeldConstraint](/docs/nl-nl/physics/constraints/weld)  en [NoCollisionConstraint](/docs/nl-nl/physics/constraints/no-collision) . Wanneer verbonden met [Bones](/docs/nl-nl/reference/engine/classes/Bone) , zal de beperking hun geanimeerde positie en oriëntatie gebruiken.

Om een mechanische beperking te maken, kunt u er een invoegen vanuit de Beperkingen  picker/knop of via het [Explorer](/docs/nl-nl/studio/explorer)  venster.

Beperkingen Picker Explorer

1.

Klik in de Model  tabwerkbalk van Studio met de muis op de kleine hoekpijl op een beperkingknop om het picker-menu te openen, en selecteer vervolgens de gewenste beperking.

 ![Beperkingen pickers aangegeven in de werkbalk van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Constraint-Pickers.png)

2.

Beweeg in de 3D-weergave de muis over een [Part](/docs/nl-nl/reference/engine/classes/Part)  of [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  en klik om een nieuwe [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  aan het onderdeel toe te voegen op het gevisualiseerde punt. Beweeg anders over en klik op een bestaande [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  of [Bone](/docs/nl-nl/reference/engine/classes/Bone)  om deze voor de beperking te gebruiken.

3.

De meeste mechanische beperkingen vereisen een secundaire  bevestiging in hun functionaliteit, dus de tool zal u meestal vragen om de vorige stap te herhalen op een andere [Part](/docs/nl-nl/reference/engine/classes/Part) , [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  of [Bone](/docs/nl-nl/reference/engine/classes/Bone) .

![SpringConstraint die twee bevestigingen op aparte blokken verbindt. Eén blok is groen en de andere is blauw.](https://prod.docsiteassets.roblox.com/assets/physics/constraints/Creation-Diagram.jpg) Voltooide [SpringConstraint](/docs/nl-nl/physics/constraints/spring)  die twee bevestigingen verbindt

## [Fysieke simulatie](#fysieke-simulatie)[](#fysieke-simulatie)

Om fysica te simuleren terwijl je [onderdelen verplaatst](/docs/nl-nl/parts#move)  of [roteert](/docs/nl-nl/parts#rotate) , kun je overschakelen van de Geometrische  modus naar de Fysieke  modus in de werkbalk van Studio, waardoor onderdelen gedwongen worden zich aan fysieke beperkingen te houden. Bijvoorbeeld, als twee onderdelen zijn verbonden door een [RopeConstraint](/docs/nl-nl/reference/engine/classes/RopeConstraint)  en je sleept een onderdeel door de scène, zal het andere onderdeel volgen terwijl het touw strak wordt.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Mode-Physical.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
