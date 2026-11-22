<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/rigid -->

Rigid | Documentatie - Roblox Creator Hub

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

# Rigid

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een [RigidConstraint](/docs/nl-nl/reference/engine/classes/RigidConstraint)  verbindt twee [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  of [Bones](/docs/nl-nl/reference/engine/classes/Bone)  en zorgt ervoor dat ze in dezelfde relatieve positie/orientatie ten opzichte van elkaar blijven. Deze flexibiliteit biedt extra functionaliteit bovenop [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint) , zoals het bevestigen van accessoires aan [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  op een karakter rig.

Om twee [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  aan elkaar te bevestigen, in plaats van twee [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  of [Bones](/docs/nl-nl/reference/engine/classes/Bone) , zie [WeldConstraint](/docs/nl-nl/physics/constraints/weld) .

Bij het maken van een [RigidConstraint](/docs/nl-nl/reference/engine/classes/RigidConstraint)  met de [Constraint](/docs/nl-nl/physics/mechanical-constraints#create-constraints)  knop in Studio, gedraagt de tool zich anders, afhankelijk van of je op bestaande [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart) , [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  of [Bones](/docs/nl-nl/reference/engine/classes/Bone)  klikt nadat de tool is geactiveerd:

-

Klikken op een bestaande [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  creëert een nieuwe [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  daarop als de bedoelde [RigidConstraint.Attachment0](/docs/nl-nl/reference/engine/classes/RigidConstraint#Attachment0)  of [RigidConstraint.Attachment1](/docs/nl-nl/reference/engine/classes/RigidConstraint#Attachment1) .

-

Klikken op een bestaande [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  of [Bone](/docs/nl-nl/reference/engine/classes/Bone)  gebruikt die instantie als de bedoelde [RigidConstraint.Attachment0](/docs/nl-nl/reference/engine/classes/RigidConstraint#Attachment0)  of [RigidConstraint.Attachment1](/docs/nl-nl/reference/engine/classes/RigidConstraint#Attachment1) .

Na de tweede geldige klik wordt er een nieuwe [RigidConstraint](/docs/nl-nl/reference/engine/classes/RigidConstraint)  aangemaakt om de twee nieuwe attachments te verbinden. Als de eerste of tweede klik niet  wordt gemaakt op een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  of [Bone](/docs/nl-nl/reference/engine/classes/Bone) , wordt de workflow geannuleerd en wordt er geen constraint aangemaakt.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
