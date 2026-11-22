<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/line-force -->

LineForce | Documentatie - Roblox Creator Hub

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

# LineForce

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mover-constraints, inclusief [LineForce](/docs/nl-nl/reference/engine/classes/LineForce) , zie [mover constraints](/docs/nl-nl/physics/mover-constraints) . Zie ook [Roblox units](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

De [LineForce](/docs/nl-nl/reference/engine/classes/LineForce) -constraint past kracht toe langs de theoretische lijn die zijn twee [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  verbindt. Terwijl de eindpunten (bevestigingen) bewegen, zal de richting van de kracht dienovereenkomstig veranderen.

## [Krachtlocatie](#krachtlocatie)[](#krachtlocatie)

Standaard wordt kracht toegepast op een van de ouders op zijn bevestigingslocatie. Indien gewenst, kan de kracht worden gefocust op het zwaartepunt van elke ouder door [ApplyAtCenterOfMass](/docs/nl-nl/reference/engine/classes/LineForce#ApplyAtCenterOfMass)  in te schakelen.

ApplyAtCenterOfMass = false

ApplyAtCenterOfMass = true

## [Inverse kwadratenwet](#inverse-kwadratenwet)[](#inverse-kwadratenwet)

Wanneer [InverseSquareLaw](/docs/nl-nl/reference/engine/classes/LineForce#InverseSquareLaw)  waar is, wordt de krachtgrootte vermenigvuldigd met het inverse kwadraat van de afstand, wat betekent dat de kracht exponentieel zal toenemen naarmate de twee bevestigingen dichter bij elkaar komen, zoals magneten. Bij het gebruik van deze instelling is het aan te raden om een [MaxForce](/docs/nl-nl/reference/engine/classes/LineForce#MaxForce)  drempel in te stellen om oneindige kracht te voorkomen als de bevestigingen precies uitgelijnd zijn.

InverseSquareLaw = false

InverseSquareLaw = true

## [Reactiekracht](#reactiekracht)[](#reactiekracht)

Standaard past de constraint alleen kracht toe op [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0) , terwijl [Attachment1](/docs/nl-nl/reference/engine/classes/Constraint#Attachment1)  onaangetast blijft. Echter, kracht kan op beide bevestigingen worden toegepast in gelijke en tegengestelde richtingen  door [ReactionForceEnabled](/docs/nl-nl/reference/engine/classes/LineForce#ReactionForceEnabled)  in te schakelen.

ReactionForceEnabled = false

ReactionForceEnabled = true

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
