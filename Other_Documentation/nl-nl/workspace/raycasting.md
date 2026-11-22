<!-- Source: https://create.roblox.com/docs/nl-nl/workspace/raycasting -->

Raycasting | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. Ruimtelijke gegevens

# Raycasting

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Op het meest basale niveau is raycasting  de handeling van het uitzenden van een onzichtbare straal vanuit een [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  punt in een specifieke richting met een gedefinieerde lengte. Zodra de straal is uitgezonden, kun je detecteren of de straal een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  of [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  cel raakt.

Lasers worden afgevuurd door zwevende bollen, en raycasting bepaalt of een laser een platform raakt. Platforms die door de lasers worden aangeraakt, worden tijdelijk vernietigd.

Je kunt een straal uitzenden met de [WorldRoot:Raycast()](/docs/nl-nl/reference/engine/classes/WorldRoot#Raycast)  methode ([Workspace:Raycast()](/docs/nl-nl/reference/engine/classes/Workspace#Raycast) ) vanuit een [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  oorsprong in een [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  richting.

Basis Raycast

```

local Workspace = game:GetService("Workspace")

local rayOrigin = Vector3.new(0, 0, 0)

local rayDirection = Vector3.new(0, -100, 0)

local raycastResult = Workspace:Raycast(rayOrigin, rayDirection)

```

Bij het uitzenden van een straal moet de richtingsparameter de gewenste lengte van de straal omvatten. Als de grootte van de richting bijvoorbeeld 10 is, zal de resulterende straal ook een lengte van 10 hebben. De maximale lengte is 15.000 studs.

Wanneer van toepassing, kun je een onbekende richtingsvector (rayDirection ) berekenen met een bekende oorsprong  en bestemming . Dit is nuttig wanneer je een straal tussen twee punten wilt uitzenden die kunnen veranderen, zoals van de ene speler naar de andere.

1.

De oorsprong plus een richtingsvector geeft de bestemming van de straal aan:

rayOrigin + rayDirection = rayDestination \text{rayOrigin} + \text{rayDirection} = \text{rayDestination} rayOrigin + rayDirection = rayDestination

2.

Trek rayOrigin \text{rayOrigin} rayOrigin  van beide zijden van de vergelijking af:

rayOrigin + rayDirection − rayOrigin = rayDestination − rayOrigin \text{rayOrigin} + \text{rayDirection} - \text{rayOrigin} = \text{rayDestination} - \text{rayOrigin} rayOrigin + rayDirection − rayOrigin = rayDestination − rayOrigin

3.

De richting van de straal is gelijk aan de bestemming min de oorsprong:

rayDirection = rayDestination − rayOrigin \text{rayDirection} = \text{rayDestination} - \text{rayOrigin} rayDirection = rayDestination − rayOrigin

```

local Workspace = game:GetService("Workspace")

local rayOrigin = Workspace.TestOrigin.Position

local rayDestination = Workspace.TestDestination.Position

local rayDirection = rayDestination - rayOrigin

local raycastResult = Workspace:Raycast(rayOrigin, rayDirection)

```

## [Filteropties](#filteropties)[](#filteropties)

[WorldRoot:Raycast()](/docs/nl-nl/reference/engine/classes/WorldRoot#Raycast)  accepteert een optioneel [RaycastParams](/docs/nl-nl/reference/engine/datatypes/RaycastParams)  object dat de raycast vertelt om selectief bepaalde [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  op te nemen of uit te sluiten, het Water  materiaal voor [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  te negeren, of een [botsingsgroep](/docs/nl-nl/workspace/collisions#botsingsfiltering)  te gebruiken.

| Sleutel | | Beschrijving |
| --- | --- |
| FilterDescendantsInstances | | Array  van objecten waarvan de afstammelingen worden gebruikt bij het filteren van raycasting kandidaten. |
| FilterType | | [Enum.RaycastFilterType](/docs/nl-nl/reference/engine/enums/RaycastFilterType)  enum die bepaalt hoe de FilterDescendantsInstances  array wordt gebruikt in de raycast operatie.
-

[Exclude](/docs/nl-nl/reference/engine/enums/RaycastFilterType)  — Elke [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  wordt beschouwd behalve  die welke afstammelingen zijn van objecten in de array.

-

[Include](/docs/nl-nl/reference/engine/enums/RaycastFilterType)  — Alleen [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  die afstammelingen zijn van objecten in de array worden beschouwd.

 |
| IgnoreWater | | Boolean die bepaalt of het Water  materiaal wordt beschouwd bij raycasting tegen [Terrain](/docs/nl-nl/reference/engine/classes/Terrain) . |
| CollisionGroup | | String naam van de [botsingsgroep](/docs/nl-nl/workspace/collisions#botsingsfiltering)  die wordt gebruikt voor de raycasting operatie. |

Raycast Filtering

```

local Workspace = game:GetService("Workspace")

local rayOrigin = Vector3.zero

local rayDirection = Vector3.new(0, -100, 0)

local raycastParams = RaycastParams.new()

raycastParams.FilterDescendantsInstances = {script.Parent}

raycastParams.FilterType = Enum.RaycastFilterType.Exclude

raycastParams.IgnoreWater = true

local raycastResult = Workspace:Raycast(rayOrigin, rayDirection, raycastParams)

```

## [Botsingsdetectie](#botsingsdetectie)[](#botsingsdetectie)

Als de raycasting operatie een geschikte [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  of [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  cel raakt, wordt een [RaycastResult](/docs/nl-nl/reference/engine/datatypes/RaycastResult)  object geretourneerd met de resultaten. Om te testen op een botsing, bevestig dat het resultaat niet nil  is en gebruik de volgende eigenschappen indien nodig.

| Eigenschap | | Beschrijving |
| [Instance](/docs/nl-nl/reference/engine/classes/Instance) | | De [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  of [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  cel die de straal heeft gekruist. |
| Position | | [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  positie van de intersectie tussen de straal en de [Instance](/docs/nl-nl/reference/engine/classes/Instance) . |
| Distance | | Afstand tussen de straal oorsprong en het intersectiepunt. |
| Material | | De [Enum.Material](/docs/nl-nl/reference/engine/enums/Material)  van de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  of [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  op het intersectiepunt. |
| Normal | | [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  van de normale vector van het gekruiste vlak. |

Wanneer gebruikt in een plaats met [instance streaming](/docs/nl-nl/workspace/streaming)  ingeschakeld, kan een client mogelijk niet verre [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  hebben gestreamd, zodat een raycast mogelijk geen botsing detecteert. Bovendien zijn laag-detail "imposter" [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  en [Models](/docs/nl-nl/reference/engine/classes/Model)  die door het streaming systeem zijn gegenereerd puur visueel en zijn ze geen geschikte raycast-doelen.

Je kunt elke [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  vrijstellen van botsingsdetectie door de [BasePart.CanQuery](/docs/nl-nl/reference/engine/classes/BasePart#CanQuery)  eigenschap in te stellen op false .

Raycast Botsingsdetectie

```

local Workspace = game:GetService("Workspace")

local rayOrigin = Vector3.zero

local rayDirection = Vector3.new(0, -100, 0)

local raycastResult = Workspace:Raycast(rayOrigin, rayDirection)

if raycastResult then

	print("Instance:", raycastResult.Instance)

	print("Position:", raycastResult.Position)

	print("Distance:", raycastResult.Distance)

	print("Material:", raycastResult.Material)

	print("Normal:", raycastResult.Normal)

else

	warn("Geen raycast resultaat!")

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
