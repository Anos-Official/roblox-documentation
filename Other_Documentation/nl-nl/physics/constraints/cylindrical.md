<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/cylindrical -->

Cilindrisch | Documentatie - Roblox Creator Hub

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

# Cilindrisch

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mechanische beperkingen, inclusief [CylindricalConstraint](/docs/nl-nl/reference/engine/classes/CylindricalConstraint) , zie [Mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints) . Zie ook [Roblox eenheden](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

Een [CylindricalConstraint](/docs/nl-nl/reference/engine/classes/CylindricalConstraint)  stelt zijn bevestigingen in staat om langs één as te schuiven en rond een andere as te draaien. Deze beperking, samen met een [SpringConstraint](/docs/nl-nl/physics/constraints/spring) , is ideaal voor het bouwen van voertuigophangingen waarbij de schok van het wiel omhoog en omlaag kan schuiven terwijl het wiel zelf draait. Deze beperking kan ook worden aangedreven op zowel een [hoek](#hoekkracht)  als een [lineaire](#lineaire-kracht)  manier.

De oriëntatie van de bevestigingen beïnvloedt hoe het cilindrische aspect zal draaien. Om ervoor te zorgen dat de rotatie rond de gewenste as plaatsvindt, moeten de [Axis](/docs/nl-nl/reference/engine/classes/Attachment#Axis)  en [SecondaryAxis](/docs/nl-nl/reference/engine/classes/Attachment#SecondaryAxis)  van elke bevestiging, weergegeven door de gele en oranje pijlen, in dezelfde richting wijzen.

## [Hoekkracht](#hoekkracht)[](#hoekkracht)

Als de [AngularActuatorType](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#AngularActuatorType)  van een cilinder is ingesteld op [Motor](/docs/nl-nl/reference/engine/enums/ActuatorType) , probeert deze de bevestigingen te draaien met als doel zijn [AngularVelocity](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#AngularVelocity)  te bereiken. Je kunt deze rotatie verder regelen via zowel [MotorMaxAngularAcceleration](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#MotorMaxAngularAcceleration)  als [MotorMaxTorque](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#MotorMaxTorque) .

Als de [AngularActuatorType](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#AngularActuatorType)  van een cilinder is ingesteld op [Servo](/docs/nl-nl/reference/engine/enums/ActuatorType) , probeert deze te draaien naar een hoek die is gespecificeerd door [TargetAngle](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#TargetAngle) . Deze rotatie wordt geregeld door [AngularSpeed](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#AngularSpeed) , [AngularResponsiveness](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#AngularResponsiveness)  en [ServoMaxTorque](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#ServoMaxTorque) .

## [Lineaire kracht](#lineaire-kracht)[](#lineaire-kracht)

Als de [ActuatorType](/docs/nl-nl/reference/engine/classes/CylindricalConstraint)  van een cilinder is ingesteld op [Motor](/docs/nl-nl/reference/engine/enums/ActuatorType) , probeert deze de bevestigingen te vertalen met als doel [Velocity](/docs/nl-nl/reference/engine/classes/CylindricalConstraint)  te bereiken. Je kunt deze vertaling verder regelen via zowel [MotorMaxAcceleration](/docs/nl-nl/reference/engine/classes/CylindricalConstraint)  als [MotorMaxForce](/docs/nl-nl/reference/engine/classes/CylindricalConstraint) .

Als de [ActuatorType](/docs/nl-nl/reference/engine/classes/CylindricalConstraint)  van een cilinder is ingesteld op [Servo](/docs/nl-nl/reference/engine/enums/ActuatorType) , probeert deze de bevestigingen te vertalen naar een bepaalde scheiding die is gespecificeerd door [TargetPosition](/docs/nl-nl/reference/engine/classes/CylindricalConstraint) . Deze vertaling wordt geregeld door [Speed](/docs/nl-nl/reference/engine/classes/CylindricalConstraint) , [LinearResponsiveness](/docs/nl-nl/reference/engine/classes/CylindricalConstraint)  en [ServoMaxForce](/docs/nl-nl/reference/engine/classes/CylindricalConstraint) .

## [Limieten](#limieten)[](#limieten)

Je kunt limieten instellen om zowel het schuifbereik  als de rotatie  van een cilindrische beperking te beperken.

Het inschakelen van de [LimitsEnabled](/docs/nl-nl/reference/engine/classes/CylindricalConstraint)  eigenschap maakt de [LowerLimit](/docs/nl-nl/reference/engine/classes/CylindricalConstraint)  en [UpperLimit](/docs/nl-nl/reference/engine/classes/CylindricalConstraint)  waarden zichtbaar, evenals [Restitution](/docs/nl-nl/reference/engine/classes/CylindricalConstraint)  die de elasticiteit van de bevestigingen definieert wanneer ze een van de limieten bereiken.

Het inschakelen van de [AngularLimitsEnabled](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#AngularLimitsEnabled)  eigenschap maakt de [LowerAngle](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#LowerAngle)  en [UpperAngle](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#UpperAngle)  limieten zichtbaar, evenals [AngularRestitution](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#AngularRestitution)  die de elasticiteit van de bevestigingen definieert wanneer ze een van de limieten bereiken.

LimitsEnabled = true

AngularLimitsEnabled = true

## [Hellingshoek](#hellingshoek)[](#hellingshoek)

[InclinationAngle](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#InclinationAngle)  definieert de richting van de rotatieas als een hoek vanaf de X  as in het X / Y  vlak van [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0) , van -180 tot 180. Dit stelt je in staat om het roterende element te kantelen zonder de schuifas te veranderen.

InclinationAngle = 90

InclinationAngle = 30

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
