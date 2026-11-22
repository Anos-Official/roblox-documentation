<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/hinge -->

Scharnier | Documentatie - Roblox Creator Hub

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

# Scharnier

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mechanische beperkingen, inclusief [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint) , zie [Mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints) . Zie ook [Roblox eenheden](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

Een [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  stelt zijn twee bevestigingen in staat om rond één as te draaien, waardoor ze in dezelfde positie en X  as-alignment worden gedwongen. Deze beperking kan ook kracht krijgen om zich te gedragen als een [motor](#hoekkracht)  of [servo](#hoekkracht) , en je kunt limieten instellen om het rotatiebereik van het scharnier te beperken.

De oriëntatie van de bevestigingen van een scharnier beïnvloedt hoe het draait. Om ervoor te zorgen dat de rotatie rond de gewenste as plaatsvindt, moet de [Axis](/docs/nl-nl/reference/engine/classes/Attachment#Axis)  van elke bevestiging, weergegeven door de gele pijl, in dezelfde richting wijzen.

### [Hoekkracht](#hoekkracht)[](#hoekkracht)

Als de [ActuatorType](/docs/nl-nl/reference/engine/classes/HingeConstraint#ActuatorType)  van een scharnier is ingesteld op [Motor](/docs/nl-nl/reference/engine/enums/ActuatorType) , probeert het de bevestigingen te draaien met als doel zijn [AngularVelocity](/docs/nl-nl/reference/engine/classes/HingeConstraint#AngularVelocity)  te bereiken. Je kunt deze rotatie verder regelen via zowel [MotorMaxAcceleration](/docs/nl-nl/reference/engine/classes/HingeConstraint#MotorMaxAcceleration)  als [MotorMaxTorque](/docs/nl-nl/reference/engine/classes/HingeConstraint#MotorMaxTorque) .

Als de [ActuatorType](/docs/nl-nl/reference/engine/classes/HingeConstraint#ActuatorType)  van een scharnier is ingesteld op [Servo](/docs/nl-nl/reference/engine/enums/ActuatorType) , probeert het te draaien naar een hoek die is gespecificeerd door [TargetAngle](/docs/nl-nl/reference/engine/classes/HingeConstraint#TargetAngle) . Deze rotatie wordt geregeld door zowel [AngularSpeed](/docs/nl-nl/reference/engine/classes/HingeConstraint#AngularSpeed)  als [ServoMaxTorque](/docs/nl-nl/reference/engine/classes/HingeConstraint#ServoMaxTorque) .

ActuatorType = Motor

ActuatorType = Servo

### [Limieten](#limieten)[](#limieten)

Je kunt limieten instellen om de rotatie van een scharnier te beperken, nuttig voor mechanismen zoals deuren die alleen binnen een bepaalde range open of dicht moeten kunnen zwaaien. Het inschakelen van de [LimitsEnabled](/docs/nl-nl/reference/engine/classes/HingeConstraint#LimitsEnabled)  eigenschap maakt de [LowerAngle](/docs/nl-nl/reference/engine/classes/HingeConstraint#LowerAngle)  en [UpperAngle](/docs/nl-nl/reference/engine/classes/HingeConstraint#UpperAngle)  limieten zichtbaar, evenals [Restitution](/docs/nl-nl/reference/engine/classes/HingeConstraint#Restitution)  die de elasticiteit van de bevestigingen definieert wanneer ze een van de limieten bereiken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
