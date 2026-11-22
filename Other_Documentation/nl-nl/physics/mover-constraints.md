<!-- Source: https://create.roblox.com/docs/nl-nl/physics/mover-constraints -->

Mover beperkingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Fysica](/docs/nl-nl/physics)
8. /
9. [Beperkingen van verplaatser](/docs/nl-nl/physics/mover-constraints)

# Mover beperkingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De fysica-engine bevat de volgende [Constraints](/docs/nl-nl/reference/engine/classes/Constraint)  die kracht of koppel toepassen om een of meer assemblages te verplaatsen. Daarnaast zijn er verschillende [mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints)  beschikbaar die zich gedragen als conceptuele mechanische verbindingen, waaronder scharnieren, veren, touwen en meer.

[Lineaire Snelheid](/docs/nl-nl/physics/constraints/linear-velocity)

[LinearVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity)  past kracht toe op een assemblage om een constante snelheid langs een 3D-vector, lijn of 2D-vlak te behouden

[Hoek Snelheid](/docs/nl-nl/physics/constraints/angular-velocity)

[AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity)  past koppel toe op een assemblage om een constante hoeksnelheid te behouden

[Positie Uitlijnen](/docs/nl-nl/physics/constraints/align-position)

[AlignPosition](/docs/nl-nl/reference/engine/classes/AlignPosition)  past kracht toe om twee bevestigingen samen te bewegen, of om een bevestiging naar een doelpositie te verplaatsen

[Oriëntatie Uitlijnen](/docs/nl-nl/physics/constraints/align-orientation)

[AlignOrientation](/docs/nl-nl/reference/engine/classes/AlignOrientation)  past koppel toe om twee bevestigingen uit te lijnen, of om een bevestiging met een doeloriëntatie uit te lijnen

[Vector Kracht](/docs/nl-nl/physics/constraints/vector-force)

[VectorForce](/docs/nl-nl/reference/engine/classes/VectorForce)  past constante lineaire kracht toe op een assemblage

[Koppel](/docs/nl-nl/physics/constraints/torque)

[Torque](/docs/nl-nl/reference/engine/classes/Torque)  past constant koppel toe op een assemblage vanuit het zwaartepunt

[Lijn Kracht](/docs/nl-nl/physics/constraints/line-force)

[LineForce](/docs/nl-nl/reference/engine/classes/LineForce)  past kracht toe langs de theoretische lijn die zijn twee bevestigingen verbindt

[Animatie Beperking](/docs/nl-nl/physics/constraints/animation)

[AnimationConstraint](/docs/nl-nl/reference/engine/classes/AnimationConstraint)  beperkt zijn [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  door een offset transformatie [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) .

## [Beperkingen visualisatie](#beperkingen-visualisatie)[](#beperkingen-visualisatie)

To accurately visualize constraints in Studio, you can toggle the following from the View  menu or through the respective shortcut:

-

Show Welds  (Alt W  of ⌥ W ) — Toon [WeldConstraints](/docs/nl-nl/reference/engine/classes/WeldConstraint)  apart van de visualisatie van andere beperkingen.

-

Show Constraint Details  (Alt D  of ⌥ D ) — Toon volledige visuele details van niet-lasmiddelen.

In aanvulling op de bovenstaande visualisatie, kun je gekleurde omtrekken rond mechanismen (groepen onderdelen die een simulatiestap en [netwerkbezit](/docs/nl-nl/physics/network-ownership) ) delen bekijken door Mechanismen  in te schakelen vanuit de [Visualisatie Opties](/docs/nl-nl/studio/overview#visualization-options)  widget in de rechterbovenhoek van het 3D-venster.

## [Beperkingen maken](#beperkingen-maken)[](#beperkingen-maken)

Mover beperkingen verbinden doorgaans een of twee [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  of [Bones](/docs/nl-nl/reference/engine/classes/Bone) . Wanneer ze zijn verbonden met [Bones](/docs/nl-nl/reference/engine/classes/Bone) , zal de beperking hun geanimeerde positie en oriëntatie gebruiken.

Om een mechanische beperking te maken, kunt u er een invoegen vanuit de Beperkingen  picker/knop of via het [Explorer](/docs/nl-nl/studio/explorer)  venster.

Beperkingen Picker Explorer

1.

Klik in de Model  tab werkbalk van Studio op de kleine hoekpijl op een beperking knop om het picker menu te openen, en selecteer vervolgens de gewenste beperking.

 ![Beperkingen pickers aangegeven in de werkbalk van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Constraint-Pickers.png)

2.

In de 3D viewport, beweeg de muis over een [Part](/docs/nl-nl/reference/engine/classes/Part)  of [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  en klik om een nieuwe [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  aan het onderdeel toe te voegen op het gevisualiseerde punt. Alternatief, beweeg de muis over en klik op een bestaande [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  of [Bone](/docs/nl-nl/reference/engine/classes/Bone)  om deze voor de beperking te gebruiken.

3.

Sommige mover beperkingen maken gebruik van of ondersteunen een secundaire  bevestiging in hun functionaliteit, dus de tool kan u vragen om de vorige stap te herhalen op een andere [Part](/docs/nl-nl/reference/engine/classes/Part) , [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) , of [Attachment](/docs/nl-nl/reference/engine/classes/Attachment) , of [Bone](/docs/nl-nl/reference/engine/classes/Bone) .

![AngularVelocity met één bevestiging](https://prod.docsiteassets.roblox.com/assets/physics/constraints/Constraint-AngularVelocity-Labeled.jpg)[AngularVelocity](/docs/nl-nl/physics/constraints/angular-velocity)  met één bevestiging

![AlignPosition met twee bevestigingen](https://prod.docsiteassets.roblox.com/assets/physics/constraints/Constraint-AlignPosition-Labeled.jpg)[AlignPosition](/docs/nl-nl/physics/constraints/align-position)  met twee bevestigingen

## [Fysieke simulatie](#fysieke-simulatie)[](#fysieke-simulatie)

Om fysica te simuleren terwijl je [onderdelen verplaatst](/docs/nl-nl/parts#move)  of [roteert](/docs/nl-nl/parts#rotate) , kun je overschakelen van de Geometrische  modus naar de Fysieke  modus in de werkbalk van Studio, waardoor onderdelen gedwongen worden zich aan fysieke beperkingen te houden. Bijvoorbeeld, als twee onderdelen zijn verbonden door een [RopeConstraint](/docs/nl-nl/reference/engine/classes/RopeConstraint)  en je sleept een onderdeel door de scène, zal het andere onderdeel volgen terwijl het touw strak wordt.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Mode-Physical.png)

## [Legacy mover conversie](#legacy-mover-conversie)[](#legacy-mover-conversie)

Als uw spel afhankelijk is van legacy [BodyMover](/docs/nl-nl/reference/engine/classes/BodyMover) -gebaseerde beperkingen, bekijk dan de volgende notities bij het converteren naar moderne mover beperkingen.

BodyPosition  ⟩ AlignPosition

[AlignPosition](/docs/nl-nl/reference/engine/classes/AlignPosition)  voldoet aan de meeste gebruiksgevallen die door de verouderde [BodyPosition](/docs/nl-nl/reference/engine/classes/BodyPosition)  mover worden gedekt. Om te synchroniseren met hoe de legacy mover elke component onafhankelijk behandelde en een andere kracht langs elke dimensie toestond, staat de [ForceLimitMode](/docs/nl-nl/reference/engine/classes/AlignPosition#ForceLimitMode)  eigenschap van [AlignPosition](/docs/nl-nl/reference/engine/classes/AlignPosition)  de beperking toe om te werken in [Magnitude](/docs/nl-nl/reference/engine/enums/ForceLimitMode)  modus of [PerAxis](/docs/nl-nl/reference/engine/enums/ForceLimitMode)  modus:

-

In [Magnitude](/docs/nl-nl/reference/engine/enums/ForceLimitMode)  modus wordt het bestaande gedrag behouden en wordt [MaxForce](/docs/nl-nl/reference/engine/classes/AlignPosition#MaxForce)  geïnterpreteerd als een grootte.

-

In [PerAxis](/docs/nl-nl/reference/engine/enums/ForceLimitMode)  modus kan de kracht langs elke as onafhankelijk worden gespecificeerd. Omdat de maximale kracht als een vector wordt gespecificeerd, kan het referentiekader van de kracht ook worden gespecificeerd via de [ForceRelativeTo](/docs/nl-nl/reference/engine/classes/AlignPosition#ForceRelativeTo)  eigenschap met [World](/docs/nl-nl/reference/engine/enums/ActuatorRelativeTo) , [Attachment0](/docs/nl-nl/reference/engine/enums/ActuatorRelativeTo) , en [Attachment1](/docs/nl-nl/reference/engine/enums/ActuatorRelativeTo)  opties. Bovendien is de formulering voor de interne controller aangepast om overeen te komen met die van [BodyPosition](/docs/nl-nl/reference/engine/classes/BodyPosition) .

BodyGyro  ⟩ AlignOrientation

[AlignOrientation](/docs/nl-nl/reference/engine/classes/AlignOrientation)  voldoet aan de meeste gebruiksgevallen die door de verouderde [BodyGyro](/docs/nl-nl/reference/engine/classes/BodyGyro)  mover worden gedekt. De [AlignType](/docs/nl-nl/reference/engine/classes/AlignOrientation#AlignType)  modi van [AlignOrientation](/docs/nl-nl/reference/engine/classes/AlignOrientation)  bieden voldoende vrijheid voor de meeste toepassingen en de combinatie van meerdere beperkingen kan de vector koppel limiet repliceren. Bovendien dwingt de [PrimaryAxisLookAt](/docs/nl-nl/reference/engine/enums/AlignType)  modus de primaire as van de eerste bevestiging van de beperking ([Attachment0](/docs/nl-nl/reference/engine/classes/AlignOrientation#Attachment0) ) om altijd naar de tweede bevestiging ([Attachment1](/docs/nl-nl/reference/engine/classes/AlignOrientation#Attachment1) ) te wijzen, waardoor het veel gemakkelijker wordt om dingen zoals bewegingsvolgende beveiligingscamera's of geleide raketten toe te voegen.

BodyVelocity  ⟩ LinearVelocity

[LinearVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity)  voldoet aan de meeste gebruiksgevallen die door de verouderde [BodyVelocity](/docs/nl-nl/reference/engine/classes/BodyVelocity)  mover worden gedekt. Hoewel de legacy mover een [MaxForce](/docs/nl-nl/reference/engine/classes/BodyVelocity#MaxForce)  vector toestaat, was de typische toepassing van die vector kracht om een bepaalde component op nul te zetten, waardoor de beperking langs die dimensie kon worden uitgeschakeld. [LinearVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity)  bereikt een vergelijkbaar effect door te werken in verschillende [VelocityConstraintMode](/docs/nl-nl/reference/engine/classes/LinearVelocity#VelocityConstraintMode)  modi die overeenkomen met één ([Line](/docs/nl-nl/reference/engine/enums/VelocityConstraintMode) ), twee ([Plane](/docs/nl-nl/reference/engine/enums/VelocityConstraintMode) ), en drie ([Vector](/docs/nl-nl/reference/engine/enums/VelocityConstraintMode) ) dimensies.

Bovendien biedt de [ForceLimitMode](/docs/nl-nl/reference/engine/classes/LinearVelocity#ForceLimitMode)  eigenschap met de optie van [PerAxis](/docs/nl-nl/reference/engine/enums/ForceLimitMode)  ruimte voor alle toepassingen van de vector kracht met alle niet-nul componenten, zoals een toename van de kracht langs een enkele as om de zwaartekracht tegen te gaan.

BodyAngularVelocity  ⟩ AngularVelocity

Hoewel [AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity)  enkele discrepanties heeft met de verouderde [BodyAngularVelocity](/docs/nl-nl/reference/engine/classes/BodyAngularVelocity)  mover, zijn specifieke gevallen met betrekking tot die discrepanties niet door de gemeenschap of intern benadrukt.

Als een aparte verbetering werkt [AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity)  met [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  en de [RelativeTo](/docs/nl-nl/reference/engine/classes/AngularVelocity#RelativeTo)  eigenschap laat u de [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  specificeren waarin de kracht is gespecificeerd, bijvoorbeeld [World](/docs/nl-nl/reference/engine/enums/ActuatorRelativeTo)  of [Attachment1](/docs/nl-nl/reference/engine/enums/ActuatorRelativeTo) .

BodyForce / BodyThrust  ⟩ VectorForce

[VectorForce](/docs/nl-nl/reference/engine/classes/VectorForce)  voldoet aan alle gebruiksgevallen die worden aangeboden door de verouderde [BodyForce](/docs/nl-nl/reference/engine/classes/BodyForce)  en [BodyThrust](/docs/nl-nl/reference/engine/classes/BodyThrust)  movers. De moderne beperking werkt met [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  en zijn [RelativeTo](/docs/nl-nl/reference/engine/classes/VectorForce#RelativeTo)  eigenschap laat u kracht toepassen op een relatieve offset vanaf het midden, vergelijkbaar met hoe [BodyThrust.Location](/docs/nl-nl/reference/engine/classes/BodyThrust#Location)  werkte.

RocketPropulsion  ⟩ LineForce / AlignOrientation

Een combinatie van [LineForce](/docs/nl-nl/reference/engine/classes/LineForce)  en [AlignOrientation](/docs/nl-nl/reference/engine/classes/AlignOrientation)  voldoet aan de meeste gebruiksgevallen die door de verouderde [RocketPropulsion](/docs/nl-nl/reference/engine/classes/RocketPropulsion)  mover worden gedekt. In het voorbeeld van een geleide raket kan [LineForce](/docs/nl-nl/reference/engine/classes/LineForce)  worden gebruikt om het "volgdoel" gedrag van [RocketPropulsion](/docs/nl-nl/reference/engine/classes/RocketPropulsion)  te controleren, terwijl [AlignOrientation](/docs/nl-nl/reference/engine/classes/AlignOrientation)  en zijn [LookAtPosition](/docs/nl-nl/reference/engine/classes/AlignOrientation#LookAtPosition)  eigenschap kunnen worden gebruikt om het "gezicht doel" gedrag te controleren.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
