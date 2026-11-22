<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/spring -->

Lente | Documentatie - Roblox Creator Hub

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

# Lente

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mechanische beperkingen, inclusief [SpringConstraint](/docs/nl-nl/reference/engine/classes/SpringConstraint) , zie [Mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints) . Zie ook [Roblox eenheden](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

Een [SpringConstraint](/docs/nl-nl/reference/engine/classes/SpringConstraint)  past een kracht toe op zijn bevestigingen op basis van veer- en dempergedrag. Je kunt de [demping](#demping)  en [stijfheid](#stijfheid)  van een veer aanpassen, evenals minimum en maximum [limieten](#limieten)  instellen voor de lengte van de veer.

## [Vrije lengte](#vrije-lengte)[](#vrije-lengte)

[FreeLength](/docs/nl-nl/reference/engine/classes/SpringConstraint#FreeLength)  definieert de natuurlijke rustlengte van de veer. Als de bevestigingen verder uit elkaar staan dan de vrije lengte, worden ze naar elkaar toe gedwongen; als de bevestigingen dichter bij elkaar staan dan de vrije lengte, worden ze van elkaar af gedwongen.

## [Demping](#demping)[](#demping)

De [Damping](/docs/nl-nl/reference/engine/classes/SpringConstraint#Damping)  waarde controleert hoe snel de oscillatie van de veer afneemt. Een waarde van 0 laat de veer eindeloos oscilleren, terwijl hogere waarden de veer sneller tot rust brengen.

## [Stijfheid](#stijfheid)[](#stijfheid)

[Stiffness](/docs/nl-nl/reference/engine/classes/SpringConstraint#Stiffness)  stelt de sterkte van de veer in. Hogere waarden creëren een veer die met meer kracht reageert wanneer de bevestigingen dichter bij elkaar of verder uit elkaar staan dan [FreeLength](/docs/nl-nl/reference/engine/classes/SpringConstraint#FreeLength) .

Stijfheid = 25

Stijfheid = 500

## [Limieten](#limieten)[](#limieten)

Het inschakelen van de [LimitsEnabled](/docs/nl-nl/reference/engine/classes/SpringConstraint#LimitsEnabled)  eigenschap maakt de [MinLength](/docs/nl-nl/reference/engine/classes/SpringConstraint#MinLength)  en [MaxLength](/docs/nl-nl/reference/engine/classes/SpringConstraint#MaxLength)  waarden toegankelijk voor het instellen van de minimum en maximum lengte van de veer. Als de bevestigingen van de veer deze limieten bereiken, stoppen ze met bewegen van elkaar zonder restitutie.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
