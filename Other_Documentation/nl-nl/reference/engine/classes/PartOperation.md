<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/PartOperation -->

PartOperation | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [PVInstance](/docs/nl-nl/reference/engine/classes/PVInstance)
8. /
9. [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)
10. /
11. [TriangleMeshPart](/docs/nl-nl/reference/engine/classes/TriangleMeshPart)
12. /
13. [PartOperation](/docs/nl-nl/reference/engine/classes/PartOperation)

Nederlands

Feedback

Engine-klasse

PartOperation

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/PartOperation)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[RenderFidelity](#RenderFidelity) :[Enum.RenderFidelity](/docs/nl-nl/reference/engine/enums/RenderFidelity)

 |
| --- | --- |
|

[SmoothingAngle](#SmoothingAngle) :[number](/docs/nl-nl/luau/numbers)

 |
|

[TriangleCount](#TriangleCount) :[number](/docs/nl-nl/luau/numbers)

 |
|

[UsePartColor](#UsePartColor) :[boolean](/docs/nl-nl/luau/booleans)

 |

Methoden

|

[SubstituteGeometry](#SubstituteGeometry) (source :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

 |

Overgenomen leden

4  overgenomen van [TriangleMeshPart](/docs/nl-nl/reference/engine/classes/TriangleMeshPart)

106  overgenomen van [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)

4  overgenomen van [PVInstance](/docs/nl-nl/reference/engine/classes/PVInstance)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Overgenomen door

[IntersectOperation](/docs/nl-nl/reference/engine/classes/IntersectOperation) , [NegateOperation](/docs/nl-nl/reference/engine/classes/NegateOperation) , [UnionOperation](/docs/nl-nl/reference/engine/classes/UnionOperation)

---

API-referentie

Eigenschappen

RenderFidelity

Parallel lezen

Mogelijkheden: Basic, CSG

PartOperation.RenderFidelity :[Enum.RenderFidelity](/docs/nl-nl/reference/engine/enums/RenderFidelity)

Feedback geven

---

SmoothingAngle

Parallel lezen

Mogelijkheden: Basic, CSG

PartOperation.SmoothingAngle :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

TriangleCount

Roblox Security

Parallel lezen

Mogelijkheden: Basic, CSG

PartOperation.TriangleCount :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

UsePartColor

Parallel lezen

Mogelijkheden: Basic, CSG

PartOperation.UsePartColor :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Methoden

SubstituteGeometry

Mogelijkheden: Basic, CSG

PartOperation:SubstituteGeometry (source :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) ) : ()

Parameters

|

source :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |

Teruggaves

()

Codevoorbeelden

Substitutie Geometrie en Verwijder Constraints

```

local GeometryService = game:GetService("GeometryService")

local mainPart = workspace.PurpleBlock

local otherParts = { workspace.BlueBlock }

local options = {

	CollisionFidelity = Enum.CollisionFidelity.Default,

	RenderFidelity = Enum.RenderFidelity.Automatic,

	SplitApart = false,

}

local constraintOptions = {

	tolerance = 0.1,

	weldConstraintPreserve = Enum.WeldConstraintPreserve.All,

}

-- Voer de unie-operatie uit in pcall() omdat het asynchroon is

local success, newParts = pcall(function()

	return GeometryService:UnionAsync(mainPart, otherParts, options)

end)

if success and #newParts > 0 and mainPart:IsA("PartOperation") then

	-- Stel het eerste deel in de resulterende operatie in als deel om te gebruiken voor substitutie

	-- Het eerste deel is gewoon een optie; dit kan elke PartOperation zijn

	local substitutePart = newParts[1]

	-- Verplaats het deel naar de positie van het hoofddeel

	substitutePart.CFrame = mainPart.CFrame

	-- Bereken constraints/attachments die ofwel bewaard of verwijderd moeten worden

	local recommendedTable = GeometryService:CalculateConstraintsToPreserve(mainPart, newParts, constraintOptions)

	-- Vervang de geometrie van het hoofddeel met de substitutie geometrie

	mainPart:SubstituteGeometry(substitutePart)

	-- Verwijder constraints/attachments die niet automatisch worden bewaard met substitutie

	for _, item in pairs(recommendedTable) do

		if item.Attachment then

			if item.ConstraintParent == nil then

				item.Constraint.Parent = nil

			end

			if item.AttachmentParent == nil then

				item.Attachment.Parent = nil

			end

		elseif item.WeldConstraint then

			if item.Parent == nil then

				item.WeldConstraint.Parent = nil

			end

		end

	end

	-- Vernietig andere delen

	for _, otherPart in pairs(otherParts) do

		otherPart.Parent = nil

		otherPart:Destroy()

	end

end

```

Feedback geven

---

Ga naar

▼

PartOperation

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[RenderFidelity](#RenderFidelity)

[SmoothingAngle](#SmoothingAngle)

[TriangleCount](#TriangleCount)

[UsePartColor](#UsePartColor)

[Methoden](#methods)

[SubstituteGeometry()](#SubstituteGeometry)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
