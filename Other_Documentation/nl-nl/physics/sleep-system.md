<!-- Source: https://create.roblox.com/docs/nl-nl/physics/sleep-system -->

Slaap systeem | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Fysica](/docs/nl-nl/physics)

# Slaap systeem

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Elk [assemblage](/docs/nl-nl/physics/assemblies)  in de Roblox Engine komt overeen met een enkele rigid body . De positie en snelheid van elk rigid body beschrijven waar het zich bevindt en hoe snel het beweegt, en een van de primaire taken van de engine is om de posities en snelheden van elke assemblage bij te werken.

Assemblages kunnen met elkaar verbonden worden door middel van [mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints)  en [verplaatsingsbeperkingen](/docs/nl-nl/physics/mover-constraints)  om mechanismen zoals auto's of vliegtuigen te vormen. Naarmate het aantal assemblages en beperkingen in een mechanisme toeneemt, neemt ook de tijd die nodig is om het mechanisme te simuleren toe. Gelukkig wordt deze toename gecompenseerd wanneer het slaapsysteem  vaststelt dat de engine de simulatie van niet-bewegende assemblages kan overslaan.

## [Slaaptoestanden](#slaaptoestanden)[](#slaaptoestanden)

Elke assemblage kan zich in een van de drie toestanden bevinden: [wakker](#wakker) , [slapend](#slapend)  of [slaap-controle](#slaap-controle) .

### [Wakker](#wakker)[](#wakker)

Een wakker  assemblage is in beweging of versnelt, en wordt daarom gesimuleerd. Assemblages komen in deze toestand vanuit situaties die zijn uiteengezet in [slapend](#slapend)  en [slaap-controle](#slaap-controle) , evenals [aanvullende wakker situaties](#aanvullende-wakker-situaties) .

### [Slapend](#slapend)[](#slapend)

Een slapende  assemblage beweegt of versnelt niet, en wordt daarom niet gesimuleerd.

Een assemblage wordt als niet-bewegend beschouwd door zijn lineaire snelheid  en rotatiesnelheid  te controleren. Als de lineaire snelheid minder is dan de [Lineaire Snelheid](#drempelreferentie)  drempel en de rotatiesnelheid minder is dan de [Rotational Velocity](#drempelreferentie)  drempel, wordt de assemblage als niet-bewegend beschouwd.

In sommige gevallen zou het simpelweg controleren op niet-beweging ervoor zorgen dat een assemblage onterecht in de slapende toestand komt. Bijvoorbeeld, als een bal recht omhoog wordt gegooid, nadert zijn snelheid nul wanneer hij zijn maximale hoogte bereikt, waardoor het een kandidaat wordt om te slapen en nooit meer naar beneden te vallen. Om dergelijke gevallen te behandelen, beschouwt de engine een assemblage als versnellend als zijn lineaire versnelling  of rotatieversnelling  groter zijn dan de [Lineaire Versnelling](#drempelreferentie)  en [Rotational Acceleration](#drempelreferentie)  drempels, respectievelijk, en voorkomt dat de assemblage in slaap valt.

Als een assemblage in slaap valt wanneer je verwacht dat deze wakker blijft, is het meestal omdat de assemblage te langzaam beweegt. Naast de automatische controles die zijn uiteengezet in [slaap-controle](#slaap-controle)  en [slapend](#slapend) , kun je een assemblage met geweld wakker maken via de voorwaarden die zijn uiteengezet in [aanvullende wakker situaties](#aanvullende-wakker-situaties) .

### [Slaap-controle](#slaap-controle)[](#slaap-controle)

Een niet-bewegende assemblage die een beperking deelt met ten minste één [wakker](#wakker)  buurland wordt in de slaap-controle  toestand geplaatst en wordt niet gesimuleerd. Bij elke wereldstap controleert een slaap-controle assemblage of:

-

Zijn lineaire versnelling  groter is dan de [Wakker Lineaire Versnelling](#drempelreferentie)  drempel.

-

Zijn rotatieversnelling  groter is dan de [Wakker Rotational Acceleration](#drempelreferentie)  drempel.

-

De lineaire snelheid  van een buurland groter is dan de [Buurland Lineaire Snelheid](#drempelreferentie)  drempel.

-

De rotatiesnelheid  van een buurland groter is dan de [Buurland Rotational Velocity](#drempelreferentie)  drempel.

Als een van deze voorwaarden waar is, of onder een van de [aanvullende wakker situaties](#aanvullende-wakker-situaties) , komt de slaap-controle assemblage in de [wakker](#wakker)  toestand.

## [Drempelreferentie](#drempelreferentie)[](#drempelreferentie)

De volgende tabel geeft de verschillende snelheid- en versnellingdrempels weer die worden gebruikt om te bepalen of een assemblage beweegt of versnelt.

| Drempel | | Waarde | | Toestand verandering |
| --- | --- |
| Lineaire Snelheid | | 0.33 studs/s | | [wakker](#wakker)  ⟩ [slapend](#slapend) |
| Rotatiesnelheid | | 0.42 studs/s | | [wakker](#wakker)  ⟩ [slapend](#slapend) |
| Lineaire Versnelling | | 0.24 studs/s² | | [wakker](#wakker)  ⟩ [slapend](#slapend) |
| Rotatieversnelling | | 0.24 studs/s² | | [wakker](#wakker)  ⟩ [slapend](#slapend) |
| Buurland Lineaire Snelheid | | 0.48 studs/s | | [slaap-controle](#slaap-controle)  ⟩ [wakker](#wakker) |
| Buurland Rotatiesnelheid | | 0.59 studs/s | | [slaap-controle](#slaap-controle)  ⟩ [wakker](#wakker) |
| Wakker Lineaire Versnelling | | 16.9 studs/s² | | [wakker](#wakker)  ⟩ [slapend](#slapend) |
| Wakker Rotatieversnelling | | 16.9 studs/s² | | [wakker](#wakker)  ⟩ [slapend](#slapend) |

Rotatiesnelheid en versnellingdrempels weerspiegelen de snelheid en versnelling van een punt dat zich op de assemblage begrenzende bol bevindt (een bol die alle onderdelen in een assemblage bevat) en dat rigide met de assemblage beweegt.

Voor een gegeven hoeksnelheid is de rotatiesnelheid van een assemblage evenredig met de straal van de assemblage begrenzende bol. Dit betekent dat grotere assemblages met een lagere hoeksnelheid kunnen draaien zonder in slaap te vallen.

## [Aangedreven gewrichten](#aangedreven-gewrichten)[](#aangedreven-gewrichten)

Soms willen ontwikkelaars onderdelen heel langzaam verplaatsen met behulp van een aangedreven gewricht , een beperking die kracht of beweging toepast om verbonden onderdelen aan te drijven, zoals een [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  met een [Motor](/docs/nl-nl/reference/engine/enums/ActuatorType#Motor) . Om deze scenario's te ondersteunen, gebruiken assemblages die zijn verbonden met aangedreven gewrichten een strengere slaap snelheid drempel. Dit vertraagt wanneer die assemblages in slaap vallen, waardoor langzame, gecontroleerde beweging mogelijk is zonder dat het fysicasysteem ze voortijdig in slaap brengt.

De volgende worden beschouwd als aangedreven gewrichten:

| Beperking | | Configuratie | | Vereiste niet-nul eigenschappen |
| [AlignOrientation](/docs/nl-nl/reference/engine/classes/AlignOrientation) | | [RigidityEnabled](/docs/nl-nl/reference/engine/classes/AlignOrientation#RigidityEnabled)  = false | |
-

[MaxAngularVelocity](/docs/nl-nl/reference/engine/classes/AlignOrientation#MaxAngularVelocity)

-

[MaxTorque](/docs/nl-nl/reference/engine/classes/AlignOrientation#MaxTorque)

-

[Responsiveness](/docs/nl-nl/reference/engine/classes/AlignOrientation#Responsiveness)

 |
| [AlignPosition](/docs/nl-nl/reference/engine/classes/AlignPosition) | | [RigidityEnabled](/docs/nl-nl/reference/engine/classes/AlignPosition#RigidityEnabled)  = false | |
-

[MaxVelocity](/docs/nl-nl/reference/engine/classes/AlignPosition#MaxVelocity)

-

[Responsiveness](/docs/nl-nl/reference/engine/classes/AlignPosition#Responsiveness)

 |
| [AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity) | | — | |
-

[AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity#AngularVelocity)

-

[MaxTorque](/docs/nl-nl/reference/engine/classes/AngularVelocity#MaxTorque)

 |
| [AnimationConstraint](/docs/nl-nl/reference/engine/classes/AnimationConstraint) | | [IsKinematic](/docs/nl-nl/reference/engine/classes/AnimationConstraint#IsKinematic)  = false | |
-

[MaxForce](/docs/nl-nl/reference/engine/classes/AnimationConstraint#MaxForce)

-

[MaxTorque](/docs/nl-nl/reference/engine/classes/AnimationConstraint#MaxTorque)

 |
| [CylindricalConstraint](/docs/nl-nl/reference/engine/classes/CylindricalConstraint) | | [ActuatorType](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#ActuatorType)  = [Motor](/docs/nl-nl/reference/engine/enums/ActuatorType#Motor) | |
-

[Velocity](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#Velocity)

-

[MotorMaxAcceleration](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#MotorMaxAcceleration)

-

[MotorMaxForce](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#MotorMaxForce)

 |
| [ActuatorType](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#ActuatorType)  = [Servo](/docs/nl-nl/reference/engine/enums/ActuatorType#Servo) | |
-

[Speed](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#Speed)

-

[ServoMaxForce](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#ServoMaxForce)

-

[Responsiveness](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#Responsiveness)

 |
| [CylindricalConstraint](/docs/nl-nl/reference/engine/classes/CylindricalConstraint) | | [AngularActuatorType](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#AngularActuatorType)  = [Motor](/docs/nl-nl/reference/engine/enums/ActuatorType#Motor) | |
-

[AngularVelocity](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#AngularVelocity)

-

[MotorMaxAngularAcceleration](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#MotorMaxAngularAcceleration)

-

[MotorMaxTorque](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#MotorMaxTorque)

 |
| [AngularActuatorType](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#AngularActuatorType)  = [Servo](/docs/nl-nl/reference/engine/enums/ActuatorType#Servo) | |
-

[AngularSpeed](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#AngularSpeed)

-

[ServoMaxTorque](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#ServoMaxTorque)

-

[Responsiveness](/docs/nl-nl/reference/engine/classes/CylindricalConstraint#Responsiveness)

 |
| [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint) | | [ActuatorType](/docs/nl-nl/reference/engine/classes/HingeConstraint#ActuatorType)  = [Motor](/docs/nl-nl/reference/engine/enums/ActuatorType#Motor) | |
-

[AngularVelocity](/docs/nl-nl/reference/engine/classes/HingeConstraint#AngularVelocity)

-

[MotorMaxAcceleration](/docs/nl-nl/reference/engine/classes/HingeConstraint#MotorMaxAcceleration)

-

[MotorMaxTorque](/docs/nl-nl/reference/engine/classes/HingeConstraint#MotorMaxTorque)

 |
| [ActuatorType](/docs/nl-nl/reference/engine/classes/HingeConstraint#ActuatorType)  = [Servo](/docs/nl-nl/reference/engine/enums/ActuatorType#Servo) | |
-

[AngularSpeed](/docs/nl-nl/reference/engine/classes/HingeConstraint#AngularSpeed)

-

[ServoMaxTorque](/docs/nl-nl/reference/engine/classes/HingeConstraint#ServoMaxTorque)

-

[Responsiveness](/docs/nl-nl/reference/engine/classes/HingeConstraint#Responsiveness)

 |
| [LinearVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity) | | [VelocityConstraintMode](/docs/nl-nl/reference/engine/classes/LinearVelocity#VelocityConstraintMode)  = [Line](/docs/nl-nl/reference/engine/enums/VelocityConstraintMode#Line) | |
-

[LineVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity#LineVelocity)

-

Als [ForceLimitsEnabled](/docs/nl-nl/reference/engine/classes/LinearVelocity#ForceLimitsEnabled) , ook [MaxForce](/docs/nl-nl/reference/engine/classes/LinearVelocity#MaxForce)

 |
| [VelocityConstraintMode](/docs/nl-nl/reference/engine/classes/LinearVelocity#VelocityConstraintMode)  = [Plane](/docs/nl-nl/reference/engine/enums/VelocityConstraintMode#Plane) | |
-

[PlaneVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity#PlaneVelocity)

-

Als [ForceLimitsEnabled](/docs/nl-nl/reference/engine/classes/LinearVelocity#ForceLimitsEnabled) :
-

[Magnitude](/docs/nl-nl/reference/engine/enums/ForceLimitMode#Magnitude) : [MaxForce](/docs/nl-nl/reference/engine/classes/LinearVelocity#MaxForce)

-

[PerAxis](/docs/nl-nl/reference/engine/enums/ForceLimitMode#PerAxis) : [MaxPlanarAxesForce](/docs/nl-nl/reference/engine/classes/LinearVelocity#MaxPlanarAxesForce)

 |
| [VelocityConstraintMode](/docs/nl-nl/reference/engine/classes/LinearVelocity#VelocityConstraintMode)  = [Vector](/docs/nl-nl/reference/engine/enums/VelocityConstraintMode#Vector) | |
-

[VectorVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity#VectorVelocity)

-

Als [ForceLimitsEnabled](/docs/nl-nl/reference/engine/classes/LinearVelocity#ForceLimitsEnabled) :
-

[Magnitude](/docs/nl-nl/reference/engine/enums/ForceLimitMode#Magnitude) : [MaxForce](/docs/nl-nl/reference/engine/classes/LinearVelocity#MaxForce)

-

[PerAxis](/docs/nl-nl/reference/engine/enums/ForceLimitMode#PerAxis) : [MaxAxesForce](/docs/nl-nl/reference/engine/classes/LinearVelocity#MaxAxesForce)

 |
| [PrismaticConstraint](/docs/nl-nl/reference/engine/classes/PrismaticConstraint) | | [ActuatorType](/docs/nl-nl/reference/engine/classes/PrismaticConstraint#ActuatorType)  = [Motor](/docs/nl-nl/reference/engine/enums/ActuatorType#Motor) | |
-

[Velocity](/docs/nl-nl/reference/engine/classes/PrismaticConstraint#Velocity)

-

[MotorMaxAcceleration](/docs/nl-nl/reference/engine/classes/PrismaticConstraint#MotorMaxAcceleration)

-

[MotorMaxForce](/docs/nl-nl/reference/engine/classes/PrismaticConstraint#MotorMaxForce)

 |
| [ActuatorType](/docs/nl-nl/reference/engine/classes/PrismaticConstraint#ActuatorType)  = [Servo](/docs/nl-nl/reference/engine/enums/ActuatorType#Servo) | |
-

[Speed](/docs/nl-nl/reference/engine/classes/PrismaticConstraint#Speed)

-

[ServoMaxForce](/docs/nl-nl/reference/engine/classes/PrismaticConstraint#ServoMaxForce)

-

[Responsiveness](/docs/nl-nl/reference/engine/classes/PrismaticConstraint#Responsiveness)

 |
| [RopeConstraint](/docs/nl-nl/reference/engine/classes/RopeConstraint) | | [WinchEnabled](/docs/nl-nl/reference/engine/classes/RopeConstraint#WinchEnabled)  = true | |
-

[WinchForce](/docs/nl-nl/reference/engine/classes/RopeConstraint#WinchForce)

-

[WinchSpeed](/docs/nl-nl/reference/engine/classes/RopeConstraint#WinchSpeed)

 |

## [Aanvullende wakker situaties](#aanvullende-wakker-situaties)[](#aanvullende-wakker-situaties)

Naast de situaties die zijn uiteengezet in [slaap-controle](#slaap-controle)  en [slapend](#slapend) , komt een assemblage in de [wakker](#wakker)  toestand wanneer:

-

Het botst met een andere assemblage die sneller beweegt dan 1 studs/s.

-

Een eigenschap gerelateerd aan de fysica van een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  binnen de assemblage verandert, inclusief:

-

[Anchored](/docs/nl-nl/reference/engine/classes/BasePart#Anchored)

-

[AssemblyLinearVelocity](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyLinearVelocity) /[AssemblyAngularVelocity](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyAngularVelocity)

-

[CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide) /[CanTouch](/docs/nl-nl/reference/engine/classes/BasePart#CanTouch)

-

[CustomPhysicalProperties](/docs/nl-nl/reference/engine/classes/BasePart#CustomPhysicalProperties)

-

[EnableFluidForces](/docs/nl-nl/reference/engine/classes/BasePart#EnableFluidForces)

-

[Massless](/docs/nl-nl/reference/engine/classes/BasePart#Massless)

-

[RootPriority](/docs/nl-nl/reference/engine/classes/BasePart#RootPriority)

-

Een niet-nul impuls wordt toegepast op een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  binnen de assemblage via [ApplyImpulse()](/docs/nl-nl/reference/engine/classes/BasePart#ApplyImpulse) , [ApplyImpulseAtPosition()](/docs/nl-nl/reference/engine/classes/BasePart#ApplyImpulseAtPosition) , of [ApplyAngularImpulse()](/docs/nl-nl/reference/engine/classes/BasePart#ApplyAngularImpulse) .

-

Wijzigingen in eigenschappen gerelateerd aan de fysica op de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  die de assemblage zouden beïnvloeden, inclusief:

-

[Gravity](/docs/nl-nl/reference/engine/classes/Workspace#Gravity)

-

[FluidForces](/docs/nl-nl/reference/engine/classes/Workspace#FluidForces)

-

[GlobalWind](/docs/nl-nl/reference/engine/classes/Workspace#GlobalWind)

-

[AirDensity](/docs/nl-nl/reference/engine/classes/Workspace#AirDensity)

-

Een nieuwe [Constraint](/docs/nl-nl/reference/engine/classes/Constraint)  wordt gemaakt met een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  die is gekoppeld aan een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  binnen de assemblage.

-

Wijzigingen in eigenschappen voor een [Constraint](/docs/nl-nl/reference/engine/classes/Constraint)  met een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  die is gekoppeld aan een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  binnen de assemblage.

-

De [CurrentAngle](/docs/nl-nl/reference/engine/classes/Motor#CurrentAngle)  eigenschap verandert voor een [Motor](/docs/nl-nl/reference/engine/classes/Motor)  die is verbonden met een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  binnen de assemblage.

-

De assemblage bevat een [VehicleSeat](/docs/nl-nl/reference/engine/classes/VehicleSeat)  met een gezeten speler karakter.

-

De assemblage bevindt zich binnen de [BlastRadius](/docs/nl-nl/reference/engine/classes/Explosion#BlastRadius)  van een [Explosion](/docs/nl-nl/reference/engine/classes/Explosion) .

## [Debugvisualisatie](#debugvisualisatie)[](#debugvisualisatie)

Tijdens het playtesten kun je de slaaptoestanden van assemblages visualiseren door Wakker onderdelen  in te schakelen vanuit de [Visualisatie Opties](/docs/nl-nl/studio/overview#visualisatie-opties)  widget in de rechterbovenhoek van het 3D-venster.

 ![Een close-up van het 3D-venster met de Visualisatie Opties knop aangegeven in de rechterbovenhoek.](https://prod.docsiteassets.roblox.com/assets/studio/general/Visualization-Options.png)

Zodra dit is ingeschakeld, worden gesimuleerde onderdelen omrand door hun huidige slaaptoestand, waarbij [wakker](#wakker)  onderdelen in het rood zijn omrand, [slaap-controle](#slaap-controle)  onderdelen in het oranje zijn omrand, en [slapend](#slapend)  onderdelen niet zijn omrand.

Gesimuleerde onderdelen omrand door de kleur die hun huidige slaaptoestand vertegenwoordigt

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
