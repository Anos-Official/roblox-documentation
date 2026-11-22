<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/PartOperation -->

PartOperation | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/PartOperation.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [PVInstance](/docs/en-us/reference/engine/classes/PVInstance)
8. /
9. [BasePart](/docs/en-us/reference/engine/classes/BasePart)
10. /
11. [TriangleMeshPart](/docs/en-us/reference/engine/classes/TriangleMeshPart)
12. /
13. [PartOperation](/docs/en-us/reference/engine/classes/PartOperation)

English

Feedback

Engine Class

PartOperation

---

## Summary

Properties

|

[RenderFidelity](#RenderFidelity) :[Enum.RenderFidelity](/docs/en-us/reference/engine/enums/RenderFidelity)

 |
| --- | --- |
|

[SmoothingAngle](#SmoothingAngle) :[number](/docs/en-us/luau/numbers)

 |
|

[TriangleCount](#TriangleCount) :[number](/docs/en-us/luau/numbers)

 |
|

[UsePartColor](#UsePartColor) :[boolean](/docs/en-us/luau/booleans)

 |

Methods

|

[SubstituteGeometry](#SubstituteGeometry) (source :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ()

 |

Inherited Members

4  inherited from [TriangleMeshPart](/docs/en-us/reference/engine/classes/TriangleMeshPart)

106  inherited from [BasePart](/docs/en-us/reference/engine/classes/BasePart)

4  inherited from [PVInstance](/docs/en-us/reference/engine/classes/PVInstance)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Inherited by

[IntersectOperation](/docs/en-us/reference/engine/classes/IntersectOperation) , [NegateOperation](/docs/en-us/reference/engine/classes/NegateOperation) , [UnionOperation](/docs/en-us/reference/engine/classes/UnionOperation)

---

API Reference

Properties

RenderFidelity

Read Parallel

Capabilities: Basic, CSG

PartOperation.RenderFidelity :[Enum.RenderFidelity](/docs/en-us/reference/engine/enums/RenderFidelity)

Provide feedback

---

SmoothingAngle

Read Parallel

Capabilities: Basic, CSG

PartOperation.SmoothingAngle :[number](/docs/en-us/luau/numbers)

Provide feedback

---

TriangleCount

Roblox Security

Read Parallel

Capabilities: Basic, CSG

PartOperation.TriangleCount :[number](/docs/en-us/luau/numbers)

Provide feedback

---

UsePartColor

Read Parallel

Capabilities: Basic, CSG

PartOperation.UsePartColor :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Methods

SubstituteGeometry

Capabilities: Basic, CSG

PartOperation:SubstituteGeometry (source :[Instance](/docs/en-us/reference/engine/datatypes/Instance) ) : ()

Parameters

|

source :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Returns

()

Code Samples

Substitute Geometry and Drop Constraints

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

-- Perform union operation in pcall() since it's asyncronous

local success, newParts = pcall(function()

	return GeometryService:UnionAsync(mainPart, otherParts, options)

end)

if success and #newParts > 0 and mainPart:IsA("PartOperation") then

	-- Set first part in resulting operation as part to use for substitution

	-- First part is simply an option; this can be any PartOperation

	local substitutePart = newParts[1]

	-- Reposition part to the position of main part

	substitutePart.CFrame = mainPart.CFrame

	-- Calculate constraints/attachments to either preserve or drop

	local recommendedTable = GeometryService:CalculateConstraintsToPreserve(mainPart, newParts, constraintOptions)

	-- Substitute main part's geometry with substitution geometry

	mainPart:SubstituteGeometry(substitutePart)

	-- Drop constraints/attachments that are not automatically preserved with substitution

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

	-- Destroy other parts

	for _, otherPart in pairs(otherParts) do

		otherPart.Parent = nil

		otherPart:Destroy()

	end

end

```

Provide feedback

---

Jump to

▼

PartOperation

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[RenderFidelity](#RenderFidelity)

[SmoothingAngle](#SmoothingAngle)

[TriangleCount](#TriangleCount)

[UsePartColor](#UsePartColor)

[Methods](#methods)

[SubstituteGeometry()](#SubstituteGeometry)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
