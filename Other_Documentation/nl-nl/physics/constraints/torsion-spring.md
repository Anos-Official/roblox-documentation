<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/torsion-spring -->

Torsieveer | Documentatie - Roblox Creator Hub

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

# Torsieveer

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mechanische beperkingen, inclusief [TorsionSpringConstraint](/docs/nl-nl/reference/engine/classes/TorsionSpringConstraint) , zie [Mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints) . Zie ook [Roblox eenheden](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

Een [TorsionSpringConstraint](/docs/nl-nl/reference/engine/classes/TorsionSpringConstraint)  past torque toe op basis van een relatieve hoek en relatieve hoeksnelheid. Het probeert twee assen van twee onderdelen samen te brengen en is nuttig voor [scharnierende](/docs/nl-nl/physics/constraints/hinge)  swingdeuren met een terugveereffect.

De juiste oriëntatie van de bevestigingen van een torsieveer is belangrijk. De beperking zal proberen de [SecondaryAxis](/docs/nl-nl/reference/engine/classes/Attachment#SecondaryAxis)  van elke bevestiging, weergegeven door de oranje pijlen, op één lijn te brengen. Bij het bouwen van mechanismen zoals swingdeuren, zorg ervoor dat de secundaire assen loodrecht  staan op de beoogde rotatieas.

## [Demping](#demping)[](#demping)

De [Damping](/docs/nl-nl/reference/engine/classes/TorsionSpringConstraint#Damping)  waarde controleert hoe snel de oscillatie van de veer afneemt. Een waarde van 0 laat de veer eindeloos oscilleren, terwijl hogere waarden de veer sneller tot rust brengen.

Damping = 0

Damping = 50

## [Stijfheid](#stijfheid)[](#stijfheid)

[Stiffness](/docs/nl-nl/reference/engine/classes/TorsionSpringConstraint#Stiffness)  stelt de torsionele sterkte van de veer in. Hogere waarden creëren een veer die met meer kracht reageert.

## [Beperkingen](#beperkingen)[](#beperkingen)

Het inschakelen van de [LimitsEnabled](/docs/nl-nl/reference/engine/classes/TorsionSpringConstraint#LimitsEnabled)  eigenschap maakt de [MaxAngle](/docs/nl-nl/reference/engine/classes/TorsionSpringConstraint#MaxAngle)  waarde zichtbaar om het bereik van de veer binnen een kegel te beperken; het maakt ook de [Restitution](/docs/nl-nl/reference/engine/classes/TorsionSpringConstraint#Restitution)  waarde zichtbaar die de elasticiteit van de bevestigingen definieert wanneer ze hun limiet bereiken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
