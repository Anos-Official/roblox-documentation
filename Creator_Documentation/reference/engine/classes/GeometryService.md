<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/GeometryService -->

GeometryService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/GeometryService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [GeometryService](/docs/en-us/reference/engine/classes/GeometryService)

English

Feedback

Engine Class

GeometryService

Not Creatable

Service

---

## Summary

Methods

|

[CalculateConstraintsToPreserve](#CalculateConstraintsToPreserve) (source :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) , destination :  [{any}](/docs/en-us/luau/tables#arrays) , options :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
| --- | --- |
|

[FragmentAsync](#FragmentAsync) (part :  [BasePart](/docs/en-us/reference/engine/classes/BasePart) , sites :  [{any}](/docs/en-us/luau/tables#arrays) , options :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GenerateFragmentSites](#GenerateFragmentSites) (part :  [BasePart](/docs/en-us/reference/engine/classes/BasePart) , options :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[IntersectAsync](#IntersectAsync) (part :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) , parts :  [{any}](/docs/en-us/luau/tables#arrays) , options :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[SubtractAsync](#SubtractAsync) (part :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) , parts :  [{any}](/docs/en-us/luau/tables#arrays) , options :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[SplitApartAsync](#SplitApartAsync) (parts :  [{any}](/docs/en-us/luau/tables#arrays) , options :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[SweepPartAsync](#SweepPartAsync) (part :  [BasePart](/docs/en-us/reference/engine/classes/BasePart) , cframes :  [{any}](/docs/en-us/luau/tables#arrays) , options :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[MeshPart](/docs/en-us/reference/engine/classes/MeshPart)

 |
|

[UnionAsync](#UnionAsync) (part :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) , parts :  [{any}](/docs/en-us/luau/tables#arrays) , options :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

CalculateConstraintsToPreserve

Capabilities: CSG

GeometryService:CalculateConstraintsToPreserve (

source :[Instance](/docs/en-us/reference/engine/datatypes/Instance) , destination :[{any}](/docs/en-us/luau/tables#arrays) , options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

source :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

destination :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

Preserve Constraints

```

local GeometryService = game:GetService("GeometryService")

local main, other = workspace.Part1, workspace.Part2

local success, newParts = pcall(function()

	return GeometryService:SubtractAsync(main, {other})

end)

if success and newParts then

	for _, p in newParts do p.Parent = workspace end

	for _, rec in GeometryService:CalculateConstraintsToPreserve(main, newParts) do

		if rec.Constraint then

			rec.Constraint.Parent = rec.ConstraintParent

		end

	end

end

main:Destroy()

other:Destroy()

```

Provide feedback

---

FragmentAsync

Yields

Capabilities: CSG

GeometryService:FragmentAsync (

part :[BasePart](/docs/en-us/reference/engine/classes/BasePart) , sites :[{any}](/docs/en-us/luau/tables#arrays) , options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

part :[BasePart](/docs/en-us/reference/engine/classes/BasePart)

 |
|

sites :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

Fragment a Part

```

local GeometryService = game:GetService("GeometryService")

local inputPart = Instance.new("Part")

inputPart.Position = Vector3.new(0, 0.7, 20)

local sites = GeometryService:GenerateFragmentSites(inputPart)

local success, fragments = pcall( function()

	return GeometryService:FragmentAsync(inputPart, sites)

end)

if success and fragments then

	for _, item in fragments do

		local instance = item.Instance

		instance.Parent = workspace

	end

end

```

Provide feedback

---

GenerateFragmentSites

Capabilities: CSG

GeometryService:GenerateFragmentSites (

part :[BasePart](/docs/en-us/reference/engine/classes/BasePart) , options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

part :[BasePart](/docs/en-us/reference/engine/classes/BasePart)

 |
|

options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

Localized Fragment

```

local GeometryService = game:GetService("GeometryService")

local inputPart = workspace.Part

local pos = inputPart.Position + inputPart.Size / 2

local sites = GeometryService:GenerateFragmentSites(inputPart, {Origin = pos, Radius = 1.5})

local success, fragments = pcall( function()

	return GeometryService:FragmentAsync(inputPart, sites)

end)

if success and fragments then

	for _, item in fragments do

		local instance = item.Instance

		instance.Parent = inputPart.Parent

	end

	inputPart:Destroy()

end

```

Provide feedback

---

IntersectAsync

Yields

Capabilities: CSG

GeometryService:IntersectAsync (

part :[Instance](/docs/en-us/reference/engine/datatypes/Instance) , parts :[{any}](/docs/en-us/luau/tables#arrays) , options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

part :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

parts :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

Union two parts

```

local GeometryService = game:GetService("GeometryService")

local mainPart = Instance.new("Part")

local otherPart = Instance.new("Part")

otherPart.Position = Vector3.new(1, 0.5, 1)

local success, newParts = pcall(function()

	return GeometryService:IntersectAsync(mainPart, {otherPart})

end)

if success and newParts then

	for _, newPart in pairs(newParts) do

		newPart.Parent = workspace

	end

end

```

Provide feedback

---

SubtractAsync

Yields

Capabilities: CSG

GeometryService:SubtractAsync (

part :[Instance](/docs/en-us/reference/engine/datatypes/Instance) , parts :[{any}](/docs/en-us/luau/tables#arrays) , options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

part :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

parts :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

Subtract two parts

```

local GeometryService = game:GetService("GeometryService")

local mainPart = Instance.new("Part")

local otherPart = Instance.new("Part")

otherPart.Position = Vector3.new(1, 0.5, 1)

local success, newParts = pcall(function()

	return GeometryService:SubtractAsync(mainPart, {otherPart})

end)

if success and newParts then

	for _, newPart in pairs(newParts) do

		newPart.Parent = workspace

	end

end

```

Provide feedback

---

SplitApartAsync

Yields

Capabilities: CSG

GeometryService:SplitApartAsync (

parts :[{any}](/docs/en-us/luau/tables#arrays) , options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

parts :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

Split Apart a Union

```

local GeometryService = game:GetService("GeometryService")

local blockA = Instance.new("Part")

blockA.Size = Vector3.new(4, 4, 4)

blockA.Position = Vector3.new(0, 2, 20)

blockA.Anchored = true

blockA.Parent = workspace

local blockB = blockA:Clone()

blockB.Position = Vector3.new(10, 2, 20)

blockB.Parent = workspace

local union = GeometryService:UnionAsync(blockA, { blockB }, { SplitApart = false })[1]

union.Parent = workspace

blockA:Destroy()

blockB:Destroy()

local inputs = { union }

local success, pieces = pcall(function()

	return GeometryService:SplitApartAsync(inputs)

end)

if success and pieces then

	for _, item in pieces do

		item.Instance.Parent = inputs[item.Index].Parent

	end

	if #pieces > 0 then

		union:Destroy()

	end

end

```

Provide feedback

---

SweepPartAsync

Yields

Capabilities: CSG

GeometryService:SweepPartAsync (

part :[BasePart](/docs/en-us/reference/engine/classes/BasePart) , cframes :[{any}](/docs/en-us/luau/tables#arrays) , options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) :[MeshPart](/docs/en-us/reference/engine/classes/MeshPart)

Parameters

|

part :[BasePart](/docs/en-us/reference/engine/classes/BasePart)

 |
|

cframes :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

[MeshPart](/docs/en-us/reference/engine/classes/MeshPart)

Code Samples

Sweep a Part

```

local GeometryService = game:GetService("GeometryService")

local inputPart = Instance.new("Part")

inputPart.Shape = Enum.PartType.Ball

local cframeList = {}

for i = 1, 50 do

	local rotation = CFrame.Angles(0, i * 0.2, 0)

	local position = Vector3.new(0, i * 0.1, -1)

	table.insert(cframeList, rotation * CFrame.new(position))

end

local success, sweptPart = pcall( function()

	return GeometryService:SweepPartAsync(inputPart, cframeList)

end)

if success and sweptPart then

	sweptPart.Parent = workspace

end

```

Provide feedback

---

UnionAsync

Yields

Capabilities: CSG

GeometryService:UnionAsync (

part :[Instance](/docs/en-us/reference/engine/datatypes/Instance) , parts :[{any}](/docs/en-us/luau/tables#arrays) , options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

part :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

parts :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

Union two parts

```

local GeometryService = game:GetService("GeometryService")

local mainPart = Instance.new("Part")

local otherPart = Instance.new("Part")

otherPart.Position = Vector3.new(1, 0.5, 1)

local success, newParts = pcall(function()

	return GeometryService:UnionAsync(mainPart, {otherPart})

end)

if success and newParts then

	for _, newPart in pairs(newParts) do

		newPart.Parent = workspace

	end

end

```

Provide feedback

---

Jump to

▼

GeometryService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[CalculateConstraintsToPreserve()](#CalculateConstraintsToPreserve)

[FragmentAsync()](#FragmentAsync)

[GenerateFragmentSites()](#GenerateFragmentSites)

[IntersectAsync()](#IntersectAsync)

[SubtractAsync()](#SubtractAsync)

[SplitApartAsync()](#SplitApartAsync)

[SweepPartAsync()](#SweepPartAsync)

[UnionAsync()](#UnionAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
