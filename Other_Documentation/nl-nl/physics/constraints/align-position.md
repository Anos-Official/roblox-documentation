<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/align-position -->

AlignPosition | Documentatie - Roblox Creator Hub

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

# AlignPosition

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mover constraints, inclusief [AlignPosition](/docs/nl-nl/reference/engine/classes/AlignPosition) , zie [mover constraints](/docs/nl-nl/physics/mover-constraints) . Zie ook [Roblox units](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

Een [AlignPosition](/docs/nl-nl/reference/engine/classes/AlignPosition)  constraint past force toe om twee attachments samen te bewegen, of om één attachment naar een doelpositie te verplaatsen. Zoals de naam al aangeeft, beïnvloedt het alleen de positie  van de attachments, niet hun oriëntatie (om attachments op oriëntatie  uit te lijnen, zie [AlignOrientation](/docs/nl-nl/physics/constraints/align-orientation) ).

Standaard past de constraint alleen force toe op [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0) , hoewel dit gedrag kan worden gecontroleerd via de [reactieve kracht](#reactieve-kracht)  van de constraint.

## [Krachtlocatie](#krachtlocatie)[](#krachtlocatie)

Standaard wordt de kracht toegepast op de ouder van [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0)  op de locatie van die attachment, wat betekent dat als het zwaartepunt van de ouder niet is uitgelijnd met de richting van de kracht, er ook koppel zal worden toegepast naast de kracht. Alternatief kan de kracht op het zwaartepunt van de ouders worden toegepast door [ApplyAtCenterOfMass](/docs/nl-nl/reference/engine/classes/AlignPosition#ApplyAtCenterOfMass)  in te schakelen.

## [Krachtgrootte](#krachtgrootte)[](#krachtgrootte)

Je kunt de [AlignPosition](/docs/nl-nl/reference/engine/classes/AlignPosition)  constraint configureren om de maximale kracht toe te passen die constraints toestaan via de [RigidityEnabled](/docs/nl-nl/reference/engine/classes/AlignPosition#RigidityEnabled)  eigenschap. Wanneer true , reageert de fysica-oplosser zo snel mogelijk om de uitlijning te voltooien. Wanneer false , wordt de kracht bepaald door [MaxForce](/docs/nl-nl/reference/engine/classes/AlignPosition#MaxForce) , [MaxVelocity](/docs/nl-nl/reference/engine/classes/AlignPosition#MaxVelocity) , en [Responsiveness](/docs/nl-nl/reference/engine/classes/AlignPosition#Responsiveness) .

## [Reactieve kracht](#reactieve-kracht)[](#reactieve-kracht)

Standaard past de constraint alleen force toe op [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0)  terwijl [Attachment1](/docs/nl-nl/reference/engine/classes/Constraint#Attachment1)  onaangetast blijft. Indien gewenst, kan force op beide  attachments in gelijke en tegengestelde richtingen  worden toegepast door [ReactionForceEnabled](/docs/nl-nl/reference/engine/classes/AlignPosition#ReactionForceEnabled)  in te schakelen.

## [Attachmentmodus](#attachmentmodus)[](#attachmentmodus)

De [Mode](/docs/nl-nl/reference/engine/classes/AlignPosition#Mode)  eigenschap specificeert of de constraint één  of twee  attachments gebruikt bij het berekenen van zijn doel. Standaard is dit [TwoAttachment](/docs/nl-nl/reference/engine/enums/PositionAlignmentMode#TwoAttachment) , wat betekent dat de constraint [Position](/docs/nl-nl/reference/engine/classes/AlignPosition#Position)  negeert en probeert [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0)  naar de positie van [Attachment1](/docs/nl-nl/reference/engine/classes/Constraint#Attachment1)  te verplaatsen. Als ingesteld op [OneAttachment](/docs/nl-nl/reference/engine/enums/PositionAlignmentMode#OneAttachment) , negeert de constraint [Attachment1](/docs/nl-nl/reference/engine/classes/Constraint#Attachment1)  en probeert [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0)  naar [Position](/docs/nl-nl/reference/engine/classes/AlignPosition#Position)  te verplaatsen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
