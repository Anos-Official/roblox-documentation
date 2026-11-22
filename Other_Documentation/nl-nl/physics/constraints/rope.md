<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/rope -->

Touw | Documentatie - Roblox Creator Hub

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

# Touw

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mechanische beperkingen, inclusief [RopeConstraint](/docs/nl-nl/reference/engine/classes/RopeConstraint) , zie [Mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints) . Zie ook [Roblox eenheden](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

Een [RopeConstraint](/docs/nl-nl/reference/engine/classes/RopeConstraint)  voorkomt dat twee bevestigingen verder uit elkaar gaan dan een gedefinieerde [Length](/docs/nl-nl/reference/engine/classes/RopeConstraint#Length) . De bevestigingen kunnen dichter bij elkaar komen dan deze lengte en beide kunnen vrij draaien. [Restitution](/docs/nl-nl/reference/engine/classes/RopeConstraint#Restitution)  definieert de elasticiteit van de bevestigingen wanneer ze de scheidingslimiet bereiken die is opgegeven door [Length](/docs/nl-nl/reference/engine/classes/RopeConstraint#Length) .

Deze beperking kan ook worden aangedreven om zich te gedragen als een [gemotoriseerde lier](#lier) .

## [Lier](#lier)[](#lier)

Als de [WinchEnabled](/docs/nl-nl/reference/engine/classes/RopeConstraint#WinchEnabled)  eigenschap van een touw is ingeschakeld, probeert het de bevestigingen te vertalen naar een vaste scheiding die is opgegeven door [WinchTarget](/docs/nl-nl/reference/engine/classes/RopeConstraint#WinchTarget) , effectief de doel lengte van het touw in studs. Deze vertaling wordt gecontroleerd door [WinchSpeed](/docs/nl-nl/reference/engine/classes/RopeConstraint#WinchSpeed) , [WinchResponsiveness](/docs/nl-nl/reference/engine/classes/RopeConstraint#WinchResponsiveness)  en [WinchForce](/docs/nl-nl/reference/engine/classes/RopeConstraint#WinchForce) .

[WinchSpeed](/docs/nl-nl/reference/engine/classes/RopeConstraint#WinchSpeed)  moet een positieve  waarde zijn, die wordt gebruikt om de touwlengte in te krimpen of uit te breiden naar [WinchTarget](/docs/nl-nl/reference/engine/classes/RopeConstraint#WinchTarget) . Het instellen van een negatieve snelheid zal terugkeren naar 0, niet de richting van de lierservo omkeren.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
