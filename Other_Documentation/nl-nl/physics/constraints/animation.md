<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/animation -->

AnimatieConstraint | Documentatie - Roblox Creator Hub

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

# AnimatieConstraint

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mover-constraints, inclusief [AnimationConstraint](/docs/nl-nl/reference/engine/classes/AnimationConstraint) , zie [mover constraints](/docs/nl-nl/physics/mover-constraints) . Zie ook [Roblox eenheden](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

Een [AnimationConstraint](/docs/nl-nl/reference/engine/classes/AnimationConstraint)  beperkt zijn [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  door een offset [transformatie](#transformatie) . Het kan ofwel [kinematisch](#kinematisch)  zijn voor snap‑to gedrag of het kan de doeltraject volgen met behulp van [kracht en koppel](#kracht-en-koppel) , beperkt door [MaxForce](/docs/nl-nl/reference/engine/classes/AnimationConstraint#MaxForce)  en [MaxTorque](/docs/nl-nl/reference/engine/classes/AnimationConstraint#MaxTorque) .

## [Transformatie](#transformatie)[](#transformatie)

De [Transform](/docs/nl-nl/reference/engine/classes/AnimationConstraint#Transform)  van de constraint is de interne [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  die wordt gemanipuleerd wanneer de constraint wordt geanimeerd. Hoe deze transformatie wordt bereikt, hangt af van de [kinematische](#kinematisch)  instelling van de constraint.

## [Kinematisch](#kinematisch)[](#kinematisch)

Wanneer de [IsKinematic](/docs/nl-nl/reference/engine/classes/AnimationConstraint#IsKinematic)  eigenschap van de constraint true  is, springen de verbonden delen onmiddellijk en precies naar de [transformatie](#transformatie)  zonder deel te nemen aan de fysica-simulatie. Wanneer false , volgen de verbonden delen het traject met behulp van [kracht en koppel](#kracht-en-koppel) .

## [Kracht en koppel](#kracht-en-koppel)[](#kracht-en-koppel)

Als de constraint niet  is ingesteld op [kinematisch](#kinematisch) , volgen de verbonden delen een traject naar de [transformatie](#transformatie)  met behulp van een maximale kracht/koppel, beperkt door respectievelijk [MaxForce](/docs/nl-nl/reference/engine/classes/AnimationConstraint#MaxForce)  en [MaxTorque](/docs/nl-nl/reference/engine/classes/AnimationConstraint#MaxTorque) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
