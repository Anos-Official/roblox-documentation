<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/prismatic -->

Prismatic | Documentatie - Roblox Creator Hub

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

# Prismatic

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het creëren, visualiseren en simuleren van mechanische beperkingen, inclusief [PrismaticConstraint](/docs/nl-nl/reference/engine/classes/PrismaticConstraint) , zie [Mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints) . Zie ook [Roblox eenheden](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

Een [PrismaticConstraint](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  creëert een stijve verbinding tussen twee attachments, waardoor ze langs één as kunnen schuiven maar niet kunnen draaien. De beperking kan ook [krachtig](#lineaire-kracht)  zijn voor mechanismen zoals schuifdeuren en liftplatforms.

De oriëntatie van de attachments van een prismatic beïnvloedt hoe deze zal bewegen. Om ervoor te zorgen dat de beweging plaatsvindt langs de gewenste as, moet de [Axis](/docs/nl-nl/reference/engine/classes/Attachment#Axis)  van elke attachment, weergegeven door de gele pijl, in dezelfde richting wijzen.

## [Lineaire kracht](#lineaire-kracht)[](#lineaire-kracht)

Als de [ActuatorType](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  van een prismatic is ingesteld op [Motor](/docs/nl-nl/reference/engine/enums/ActuatorType) , probeert deze de attachments te vertalen met als doel [Velocity](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  te bereiken. Je kunt deze vertaling verder controleren via zowel [MotorMaxAcceleration](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  als [MotorMaxForce](/docs/nl-nl/reference/engine/classes/PrismaticConstraint) .

Als de [ActuatorType](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  van een prismatic is ingesteld op [Servo](/docs/nl-nl/reference/engine/enums/ActuatorType) , probeert deze de attachments te vertalen naar een vaste scheiding die is gespecificeerd door [TargetPosition](/docs/nl-nl/reference/engine/classes/PrismaticConstraint) . Deze vertaling wordt gecontroleerd door [Speed](/docs/nl-nl/reference/engine/classes/PrismaticConstraint) , [LinearResponsiveness](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  en [ServoMaxForce](/docs/nl-nl/reference/engine/classes/PrismaticConstraint) .

ActuatorType = Motor

ActuatorType = Servo

## [Limieten](#limieten)[](#limieten)

Je kunt limieten instellen om het schuifbereik van een prismatic te beperken. Het inschakelen van de [LimitsEnabled](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  eigenschap maakt de waarden [LowerLimit](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  en [UpperLimit](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  zichtbaar, evenals [Restitution](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  die de elasticiteit van de attachments definieert wanneer ze een van de limieten bereiken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
