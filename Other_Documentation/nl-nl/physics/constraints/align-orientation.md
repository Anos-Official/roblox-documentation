<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/align-orientation -->

AlignOrientation | Documentatie - Roblox Creator Hub

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

# AlignOrientation

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mover-constraints, inclusief [AlignOrientation](/docs/nl-nl/reference/engine/classes/AlignOrientation) , zie [mover constraints](/docs/nl-nl/physics/mover-constraints) . Zie ook [Roblox units](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

De [AlignOrientation](/docs/nl-nl/reference/engine/classes/AlignOrientation) -constraint past torque toe om twee attachments uit te lijnen, of om één attachment uit te lijnen met een doeloriëntatie. Zoals de naam al aangeeft, beïnvloedt het alleen de oriëntatie  van de attachments, niet hun positie (om attachments positioneel  uit te lijnen, zie [AlignPosition](/docs/nl-nl/physics/constraints/align-position) ).

Standaard past de constraint alleen torque toe op [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0) , hoewel dit gedrag kan worden gecontroleerd via de [reactionary torque](#reactionary-torque)  van de constraint.

## [Beïnvloede assen](#beïnvloede-assen)[](#beïnvloede-assen)

De assen die door torque worden beïnvloed, worden gecontroleerd via de [AlignType](/docs/nl-nl/reference/engine/classes/AlignOrientation#AlignType) -eigenschap van de constraint. Wanneer ingesteld op [AllAxes](/docs/nl-nl/reference/engine/enums/AlignType#AllAxes)  (standaard), past de constraint torque toe over alle 3 de assen om uitlijning te bereiken. Wanneer ingesteld op [PrimaryAxisParallel](/docs/nl-nl/reference/engine/enums/AlignType#PrimaryAxisParallel) , [PrimaryAxisPerpendicular](/docs/nl-nl/reference/engine/enums/AlignType#PrimaryAxisPerpendicular) , of [PrimaryAxisLookAt](/docs/nl-nl/reference/engine/enums/AlignType#PrimaryAxisLookAt) , zal torque alleen optreden wanneer de primaire  assen niet meer uitgelijnd zijn.

## [Torque-magnitude](#torque-magnitude)[](#torque-magnitude)

Je kunt de [AlignOrientation](/docs/nl-nl/reference/engine/classes/AlignOrientation) -constraint configureren om de maximale torque toe te passen die constraints toestaan via de [RigidityEnabled](/docs/nl-nl/reference/engine/classes/AlignOrientation#RigidityEnabled) -eigenschap. Wanneer true , reageert de fysica-oplosser zo snel mogelijk om de uitlijning te voltooien. Wanneer false , wordt de torque bepaald door [MaxTorque](/docs/nl-nl/reference/engine/classes/AlignOrientation#MaxTorque) , [MaxAngularVelocity](/docs/nl-nl/reference/engine/classes/AlignOrientation#MaxAngularVelocity) , en [Responsiveness](/docs/nl-nl/reference/engine/classes/AlignOrientation#Responsiveness) .

## [Reactionary torque](#reactionary-torque)[](#reactionary-torque)

Standaard past de constraint alleen torque toe op [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0)  terwijl [Attachment1](/docs/nl-nl/reference/engine/classes/Constraint#Attachment1)  onaangetast blijft. Indien gewenst, kan torque worden toegepast op beide  attachments in gelijke en tegengestelde richtingen  door [ReactionTorqueEnabled](/docs/nl-nl/reference/engine/classes/AlignOrientation#ReactionTorqueEnabled)  in te schakelen.

## [Attachment-modus](#attachment-modus)[](#attachment-modus)

De [Mode](/docs/nl-nl/reference/engine/classes/AlignOrientation#Mode) -eigenschap specificeert of de constraint één  of twee  attachments gebruikt bij het berekenen van zijn doel. Standaard is dit [TwoAttachment](/docs/nl-nl/reference/engine/enums/OrientationAlignmentMode#TwoAttachment) , wat betekent dat de constraint probeert de oriëntatie van [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0)  af te stemmen op de oriëntatie van [Attachment1](/docs/nl-nl/reference/engine/classes/Constraint#Attachment1) , waarbij [CFrame](/docs/nl-nl/reference/engine/classes/AlignOrientation#CFrame) , [PrimaryAxis](/docs/nl-nl/reference/engine/classes/AlignOrientation#PrimaryAxis) , en [SecondaryAxis](/docs/nl-nl/reference/engine/classes/AlignOrientation#SecondaryAxis)  worden genegeerd.

Als ingesteld op [OneAttachment](/docs/nl-nl/reference/engine/enums/OrientationAlignmentMode#OneAttachment) , negeert de constraint [Attachment1](/docs/nl-nl/reference/engine/classes/Constraint#Attachment1)  en probeert de oriëntatie van [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0)  af te stemmen op de oriëntatie van [CFrame](/docs/nl-nl/reference/engine/classes/AlignOrientation#CFrame) , of de as van de attachment [Axis](/docs/nl-nl/reference/engine/classes/Attachment#Axis)  en [SecondaryAxis](/docs/nl-nl/reference/engine/classes/Attachment#SecondaryAxis)  af te stemmen op de [PrimaryAxis](/docs/nl-nl/reference/engine/classes/AlignOrientation#PrimaryAxis)  en [SecondaryAxis](/docs/nl-nl/reference/engine/classes/AlignOrientation#SecondaryAxis)  eigenschappen van de constraint respectievelijk.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
