<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/GeometryService -->

GeometryService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [GeometryService](/docs/nl-nl/reference/engine/classes/GeometryService)

Nederlands

Feedback

Engine-klasse

GeometryService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/GeometryService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[CalculateConstraintsToPreserve](#CalculateConstraintsToPreserve) (source :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , destination :  [{any}](/docs/nl-nl/luau/tables#arrays) , options :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
| --- | --- |
|

[FragmentAsync](#FragmentAsync) (part :  [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , sites :  [{any}](/docs/nl-nl/luau/tables#arrays) , options :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GenerateFragmentSites](#GenerateFragmentSites) (part :  [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , options :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[IntersectAsync](#IntersectAsync) (part :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , parts :  [{any}](/docs/nl-nl/luau/tables#arrays) , options :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[SubtractAsync](#SubtractAsync) (part :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , parts :  [{any}](/docs/nl-nl/luau/tables#arrays) , options :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[SplitApartAsync](#SplitApartAsync) (parts :  [{any}](/docs/nl-nl/luau/tables#arrays) , options :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[SweepPartAsync](#SweepPartAsync) (part :  [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , cframes :  [{any}](/docs/nl-nl/luau/tables#arrays) , options :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)

 |
|

[UnionAsync](#UnionAsync) (part :  [Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , parts :  [{any}](/docs/nl-nl/luau/tables#arrays) , options :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[{any}](/docs/nl-nl/luau/tables#arrays)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

CalculateConstraintsToPreserve

Mogelijkheden: CSG

GeometryService:CalculateConstraintsToPreserve (

source :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , destination :[{any}](/docs/nl-nl/luau/tables#arrays) , options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

source :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

destination :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Beperkingen Behouden

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

Feedback geven

---

FragmentAsync

Opbrengst

Mogelijkheden: CSG

GeometryService:FragmentAsync (

part :[BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , sites :[{any}](/docs/nl-nl/luau/tables#arrays) , options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

part :[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)

 |
|

sites :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Fragment een Deel

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

Feedback geven

---

GenerateFragmentSites

Mogelijkheden: CSG

GeometryService:GenerateFragmentSites (

part :[BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

part :[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)

 |
|

options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Gepersonaliseerd Fragment

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

Feedback geven

---

IntersectAsync

Opbrengst

Mogelijkheden: CSG

GeometryService:IntersectAsync (

part :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , parts :[{any}](/docs/nl-nl/luau/tables#arrays) , options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

part :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

parts :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Twee delen samenvoegen

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

Feedback geven

---

SubtractAsync

Opbrengst

Mogelijkheden: CSG

GeometryService:SubtractAsync (

part :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , parts :[{any}](/docs/nl-nl/luau/tables#arrays) , options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

part :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

parts :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Trek twee delen af

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

Feedback geven

---

SplitApartAsync

Opbrengst

Mogelijkheden: CSG

GeometryService:SplitApartAsync (

parts :[{any}](/docs/nl-nl/luau/tables#arrays) , options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

parts :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Splitsen van een Unie

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

Feedback geven

---

SweepPartAsync

Opbrengst

Mogelijkheden: CSG

GeometryService:SweepPartAsync (

part :[BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , cframes :[{any}](/docs/nl-nl/luau/tables#arrays) , options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) :[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)

Parameters

|

part :[BasePart](/docs/nl-nl/reference/engine/classes/BasePart)

 |
|

cframes :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

[MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)

Codevoorbeelden

Veeg een Onderdeel

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

Feedback geven

---

UnionAsync

Opbrengst

Mogelijkheden: CSG

GeometryService:UnionAsync (

part :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) , parts :[{any}](/docs/nl-nl/luau/tables#arrays) , options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) :[{any}](/docs/nl-nl/luau/tables#arrays)

Parameters

|

part :[Instance](/docs/nl-nl/reference/engine/datatypes/Instance)

 |
|

parts :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

options :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Twee delen samenvoegen

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

Feedback geven

---

Ga naar

▼

GeometryService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[CalculateConstraintsToPreserve()](#CalculateConstraintsToPreserve)

[FragmentAsync()](#FragmentAsync)

[GenerateFragmentSites()](#GenerateFragmentSites)

[IntersectAsync()](#IntersectAsync)

[SubtractAsync()](#SubtractAsync)

[SplitApartAsync()](#SplitApartAsync)

[SweepPartAsync()](#SweepPartAsync)

[UnionAsync()](#UnionAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
