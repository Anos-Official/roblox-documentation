<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/weld -->

Lassen | Documentatie - Roblox Creator Hub

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

# Lassen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint)  verbindt twee [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  en zorgt ervoor dat ze in dezelfde relatieve positie en oriëntatie ten opzichte van elkaar blijven. Zelfs als de twee delen elkaar niet raken, kun je ze aan elkaar lassen.

Om twee [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  of [Bones](/docs/nl-nl/reference/engine/classes/Bone)  te verbinden, in plaats van twee [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart) , zie [RigidConstraint](/docs/nl-nl/physics/constraints/rigid) .

Uniek aan [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint)  zijn de lichte gedragsverschillen in hoe Studio de creatie en herpositionering van gelaste delen behandelt.

Lassen van Delen Herpositioneren van Gelaste Delen

Bij het creëren van een [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint)  met de [Constraint](/docs/nl-nl/physics/mechanical-constraints#create-constraints)  knop in Studio, gedraagt de tool zich anders, afhankelijk van hoeveel [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  zijn geselecteerd wanneer de tool wordt geactiveerd:

-

Als er geen [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  zijn geselecteerd, worden de volgende twee [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  die worden aangeklikt verbonden door een nieuwe [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint) . Als hetzelfde [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  twee keer wordt aangeklikt, wordt er geen constraint aangemaakt.

-

Als er al één [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  is geselecteerd, wordt de volgende [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  die wordt aangeklikt verbonden met de geselecteerde met een nieuwe [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint) .

-

Als er meerdere [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  zijn geselecteerd, worden die welke elkaar raken of overlappen automatisch aan elkaar gelast door nieuwe [WeldConstraints](/docs/nl-nl/reference/engine/classes/WeldConstraint) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
