<!-- Source: https://create.roblox.com/docs/nl-nl/animation/inverse-kinematics -->

Inverse Kinematica | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Animatie](/docs/nl-nl/animation)
6. /
7. Animaties maken

# Inverse Kinematica

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[Inverse Kinematica](https://en.wikipedia.org/wiki/Inverse_kinematics)  (IK) is een veelgebruikte techniek in computeranimatie om efficiënt personages realistisch te laten bewegen en interactie te laten hebben met hun omgeving. Het proces van het creëren van een realistische beweging voor een personage vereist vaak veel iteraties en kleine aanpassingen van de verschillende gewrichten. Met IK kun je meerdere delen van een personage poseren en animeren door een enkel object te poseren of aan te passen.

Deze animatietechniek kan oplossingen bieden voor de volgende voorbeelden:

Pak en poseer de hand van een personage terwijl automatisch de bijbehorende ledematen, zoals de pols, elleboog en schouder, worden aangepast.

Laat de voeten van een personage realistisch interageren met verschillende oppervlakken en hellingen.

Pak en verplaats een enkel doelobject om snel realistische interacties met je personage en rekwisieten te creëren.

## [IKControl](#ikcontrol)[](#ikcontrol)

Je kunt een [IKControl](/docs/nl-nl/reference/engine/classes/IKControl)  gebruiken om IK procedureel toe te voegen aan je personage-rigs buiten de Animatie-editor . Studio stelt je in staat om IK programmatisch toe te passen op alle personages om realistische beweging en interacties in je spel te creëren.

Bij het toevoegen van een [IKControl](/docs/nl-nl/reference/engine/classes/IKControl) , stel je de [vereiste eigenschappen](#vereiste-eigenschappen)  correct in om onverwachte en onnatuurlijke animatieresultaten te voorkomen. Zoals bij alle animatie, [test je IKControls](#test-ikcontrols)  om ervoor te zorgen dat je het gewenste gedrag bereikt.

### [Vereiste eigenschappen](#vereiste-eigenschappen)[](#vereiste-eigenschappen)

Bij het toevoegen van een [IKControl](/docs/nl-nl/reference/engine/classes/IKControl)  aan de [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  of [AnimationController](/docs/nl-nl/reference/engine/classes/AnimationController)  van je personage, moet je de volgende vereiste eigenschappen instellen om IK in te schakelen:

| Eigenschap | | Beschrijving |
| --- | --- |
| [Type](/docs/nl-nl/reference/engine/classes/IKControl#Type) | | Geeft het gedragstype van de IK-control aan. Zie [Enum.IKControlType](/docs/nl-nl/reference/engine/enums/IKControlType)  voor de lijst met gedragsopties. Veelvoorkomende gedragstypen zijn Position  of Transform . |
| [EndEffector](/docs/nl-nl/reference/engine/classes/IKControl#EndEffector) | | Een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  of [Bone](/docs/nl-nl/reference/engine/classes/Bone)  in je personage-rig die naar de [Target](/docs/nl-nl/reference/engine/classes/IKControl#Target)  wijst. Je kunt bijvoorbeeld een LeftHand  bot instellen als een [EndEffector](/docs/nl-nl/reference/engine/classes/IKControl#EndEffector)  om naar een deurknopobject te reiken dat is ingesteld als de [Target](/docs/nl-nl/reference/engine/classes/IKControl#Target) . |
| [Target](/docs/nl-nl/reference/engine/classes/IKControl#Target) | | Het object waar de [EndEffector](/docs/nl-nl/reference/engine/classes/IKControl#EndEffector)  naar reikt of wijst. Een [Target](/docs/nl-nl/reference/engine/classes/IKControl#Target)  kan elk object met een wereldpositie zijn. |
| [ChainRoot](/docs/nl-nl/reference/engine/classes/IKControl#ChainRoot) | | Definieert de keten van [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  of [Bones](/docs/nl-nl/reference/engine/classes/Bone)  die de [IKControl](/docs/nl-nl/reference/engine/classes/IKControl)  beïnvloedt. Alle verbonden delen tussen de [ChainRoot](/docs/nl-nl/reference/engine/classes/IKControl#ChainRoot)  en de [EndEffector](/docs/nl-nl/reference/engine/classes/IKControl#EndEffector)  worden beïnvloed door de [IKControl](/docs/nl-nl/reference/engine/classes/IKControl)  met behulp van het gedefinieerde gedragstype.
 Bijvoorbeeld, als de LeftHand  van je personage is ingesteld als de [Target](/docs/nl-nl/reference/engine/classes/IKControl#Target) , kun je IK toepassen op de hele linkerarm door [ChainRoot](/docs/nl-nl/reference/engine/classes/IKControl#ChainRoot)  in te stellen op de LeftUpperArm . Om IK alleen toe te passen op de delen onder de elleboog, stel je [ChainRoot](/docs/nl-nl/reference/engine/classes/IKControl#ChainRoot)  in op de LeftLowerArm . |

### [Test IKControls](#test-ikcontrols)[](#test-ikcontrols)

Je kunt [IKControl](/docs/nl-nl/reference/engine/classes/IKControl)  programmatisch of rechtstreeks via de Explorer  toevoegen en bewerken. Je kunt zelfs [IKControl](/docs/nl-nl/reference/engine/classes/IKControl)  toevoegen en wijzigingen aanbrengen tijdens een Play-test om snel te controleren hoe verschillende eigenschappen de bewegingen van een personage beïnvloeden.

Om je [IKControl](/docs/nl-nl/reference/engine/classes/IKControl)  snel te testen met een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  als doel:

1.

Start vanuit de mezzanine van Studio een [playtest](/docs/nl-nl/studio/testing-modes#spelen-testen) .

2.

Navigeer in het Explorer -venster naar Workspace  → het [Model](/docs/nl-nl/reference/engine/classes/Model)  van je gebruiker. Deze [Model](/docs/nl-nl/reference/engine/classes/Model)  instantie is genoemd naar je huidige Roblox-account.

3.

Klik op het ⊕ -pictogram naast het HumanoidRootPart  van je personagemodel en voeg een Attachment  toe.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/IK-Add-Attachment.png)

4.

Selecteer de Attachment  en gebruik de Verplaats -tool om het object voor je personage in de viewport te positioneren.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/IK-Move-Attachment.png)

5.

Selecteer in het Explorer -venster het ⊕ -pictogram naast het [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  van je personage en voeg een IKControl  toe.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/IK-Humanoid-Add.png)

6.

Selecteer de [IKControl](/docs/nl-nl/reference/engine/classes/IKControl)  en stel de volgende eigenschapswaarden in het Eigenschappen -venster in:

1.

Type : Selecteer Transform  in de dropdown.

2.

EndEffector : Selecteer het LeftHand  [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  van je model in de Explorer .

3.

Target : Selecteer het nieuw gemaakte Attachment -object in de Explorer .

4.

ChainRoot : Selecteer het LeftUpperArm  [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  van je model in de Explorer .

![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/IK-IKControl-Property.png) IKControl-eigenschappen

![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/IK-Explorer-Humanoid.png) Explorer - Personagemodel

De linkerarm van je personage zou nu naar het doel [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  moeten reiken. Je kunt experimenteren met het verplaatsen van de [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  of het bewerken van de eigenschappen van de [IKControl](/docs/nl-nl/reference/engine/classes/IKControl)  om verschillende resultaten te bereiken.

### [Voeg beperkingen toe](#voeg-beperkingen-toe)[](#voeg-beperkingen-toe)

Je kunt [Constraints](/docs/nl-nl/reference/engine/classes/Constraint)  gebruiken om te beperken hoe gewrichten kunnen bewegen wanneer ze naar hun doel reiken. Beperkingen kunnen ervoor zorgen dat gewrichten zoals de ellebogen en knieën natuurlijk buigen, of om de mechanische gewrichten in een specifieke oriëntatie te laten draaien.

![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/elbow-unnatural-pose.png) Elleboog buigt onnatuurlijk

![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/elbow-natural-pose.png) Elleboog buigt correct

Om beperkingen aan je personage toe te voegen met behulp van [IKControl](/docs/nl-nl/reference/engine/classes/IKControl) , moeten je [IKControl](/docs/nl-nl/reference/engine/classes/IKControl)  en beperking aan de volgende voorwaarden voldoen:

-

De attachments waarnaar wordt verwezen in de eigenschappen [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0) /[Attachment1](/docs/nl-nl/reference/engine/classes/Constraint#Attachment1)  van de beperking zijn bevestigd aan dezelfde delen als de [Motor6D](/docs/nl-nl/reference/engine/classes/Motor6D)  [Part0](/docs/nl-nl/reference/engine/classes/Motor6D#Part0) /[Part1](/docs/nl-nl/reference/engine/classes/Motor6D#Part1) .

-

De relatieve posities van [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0) /[Attachment1](/docs/nl-nl/reference/engine/classes/Constraint#Attachment1)  moeten gelijk zijn aan de overeenkomstige posities van de [Motor6D](/docs/nl-nl/reference/engine/classes/Motor6D)  [C0](/docs/nl-nl/reference/engine/classes/Motor6D#C0) /[C1](/docs/nl-nl/reference/engine/classes/Motor6D#C1)  CFrames.

-

De beperking en de IKControl delen dezelfde bovenliggende [Model](/docs/nl-nl/reference/engine/classes/Model) .

De volgende instructies beschrijven het proces van het toevoegen van een [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  om de rotatie van de elleboog van een personage te beperken en het toevoegen van een [BallSocketConstraint](/docs/nl-nl/reference/engine/classes/BallSocketConstraint)  aan de pols om de rotatiehoek te beperken.

#### [Elleboog](#elleboog)[](#elleboog)

Personages met [R15-rigs](/docs/nl-nl/avatar/character-bodies/specifications#rigging)  bevatten al attachments in hun gewrichten die je kunt gebruiken om de elleboogbeperking toe te passen. Voor de elleboog bevatten zowel de LeftUpperArm als de LeftLowerArm een LeftElbowRigAttachment . Naast het toevoegen van een beperking, moet je ook extra kindattachments aan elke LeftElbowRigAttachment  van elk deel toevoegen om aan te geven over welke as de elleboog kan draaien.

Om de [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  en kindattachments toe te voegen:

1.

Zoek in het Explorer -venster het LeftLowerArm  van je model en klik op de ⊕-knop .

2.

Voeg een HingeConstraint  toe met de naam LeftElbowConstraint .

3.

Navigeer in het Explorer -venster naar de LeftUpperArm.LeftElbowRigAttachment  en voeg een attachment toe:

1.

Klik op de ⊕-knop  om een Attachment  toe te voegen met de naam LeftElbowConstraintAttachment0 .

2.

Selecteer in de viewport de attachment en gebruik de Rotate tool  om de attachment te draaien zodat de gele PrimaryAxis  de as van de verwachte rotatie van je elleboog is.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/elbow-primary-axis.png)

3.

Stel de eigenschap LeftElbowConstraint.Attachment0  in op deze nieuwe attachment.

4.

Navigeer in het Explorer -venster naar de LeftLowerArm.LeftElbowRigAttachment  van je model en voeg een attachment toe:

1.

Klik op de ⊕-knop  en voeg een Attachment  toe met de naam LeftElbowConstraintAttachment1 .

2.

Stel de eigenschap LeftUpperArm.LeftElbowConstraint.Attachment1  in op deze nieuwe attachment.

3.

Kopieer de eigenschap LeftElbowConstraintAttachment0.CFrameOrientation  en plak deze als de waarde voor LeftElbowConstraint.Attachment1.CFrameOrientation .

 ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/elbow-natural-pose.png)

Als je een rode pijl op de visualisatie van de beperking ziet, betekent dit dat de oriëntaties van je attachments de scharnierbeperking schenden. Ga terug en zorg ervoor dat de LeftElbowConstraintAttachment1  dezelfde oriëntatie heeft als de LeftElbowConstraintAttachment0 .

Test je IKControl om te verifiëren dat de elleboog alleen om zijn scharnieras draait:

#### [Polsen](#polsen)[](#polsen)

Zelfs met de elleboogbeperking kan de IKControl nog steeds onrealistische poses met de polsen produceren.

![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/wrist-unnatural-pose.png) De pols buigt onnatuurlijk in bepaalde oriëntaties

Je kunt dit verbeteren door een [BallSocketConstraint](/docs/nl-nl/reference/engine/classes/BallSocketConstraint)  toe te voegen om de rotatie van de pols te beperken. Hoewel dit vergelijkbaar is met het proces voor het toevoegen van een [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  aan de elleboog, kun je de eigenschap [LimitsEnabled](/docs/nl-nl/reference/engine/classes/BallSocketConstraint#LimitsEnabled)  op deze beperking gebruiken om het bewegingsbereik van de pols verder te controleren.

Om een [BallSocketConstraint](/docs/nl-nl/reference/engine/classes/BallSocketConstraint)  voor de pols toe te voegen:

1.

Zoek in het Explorer -venster het LeftHand  van je model en klik op de ⊕-knop .

1.

Voeg een BallSocketConstraint  toe met de naam LeftWristConstraint .

2.

Zoek de LeftLowerArm.LeftWristRigAttachment  van je model en voeg een attachment toe:

1.

Klik op de ⊕-knop  en voeg een Attachment  toe met de naam LeftWristConstraintAttachment0 .

2.

Selecteer in de viewport de attachment en gebruik de Rotate tool  om de attachment te draaien zodat de gele PrimaryAxis naar de vingertoppen van het model wijst.  ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/wrist-primary-axis.png)

3.

Stel de eigenschap LeftWristConstraint.Attachment0  in op de nieuwe LeftWristConstraintAttachment0 .

3.

Zoek de LeftHand.LeftWristRigAttachment  van je model en voeg een attachment toe:

1.

Klik op de ⊕-knop  en voeg een Attachment  toe met de naam LeftWristConstraintAttachment1 .

2.

Kopieer de eigenschap LeftWristConstraintAttachment0.CFrameOrientation  en plak deze als de eigenschap LeftWristConstraintAttachment1.CFrameOrientation .

3.

Stel de eigenschap LeftWristConstraint.Attachment1  in op deze nieuwe LeftWristConstraintAttachment1 .

4.

Selecteer in het Explorer -venster de LeftWristConstraint .

5.

Stel in het Eigenschappen -venster het volgende in:

1.

Schakel LimitsEnabled  in.

2.

Stel UpperAngle  in op 80 . Dit bepaalt hoeveel de as van de beperking kan draaien, en 80 graden is ongeveer hoeveel de pols zou moeten kunnen buigen.

6.

Afhankelijk van je personage wil je misschien de richting waarin de kegel wijst aanpassen. Je kunt dit doen door de Rotate tool  te gebruiken om de Attachment0  van de beperking te draaien.

Wanneer je de LeftWristConstraint  selecteert, verschijnt er een groene kegel die het bewegingsbereik van de pols visualiseert.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/inverse-kinematics/wrist-cone.png)

Met de beperking ingesteld, test je de IKControl met de hand die naar beneden wijst voor het personage en de pols zou realistischer moeten draaien en buigen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
