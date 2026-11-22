<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/datatypes/Collection -->

Collection | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/datatypes/Collection.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Data types](/docs/en-us/reference/engine/datatypes)
2. /
3. [Collection](/docs/en-us/reference/engine/datatypes/Collection)

English

Feedback

Engine Data Type

Collection

---

## Summary

Properties

|

[Enabled](#Enabled) :[boolean](/docs/en-us/luau/booleans)

 |
| --- | --- |
|

[Query](#Query) :[string](/docs/en-us/luau/strings)

 |
|

[Root](#Root) :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Methods

|

[Destroy](#Destroy) ()

 |
|

[ForEach](#ForEach) (callback :  [function](/docs/en-us/luau/functions) )

 |
|

[GetCount](#GetCount) () :[number](/docs/en-us/luau/numbers)

 |

Code Samples

Collection Lifecycle and Events

```

local CollectionService = game:GetService("CollectionService")

-- A live collection of parts tagged "MapleLeaf" that are direct children of a model tagged "MapleTree"

local mapleLeaves: Collection = CollectionService:CreateCollection("Model.MapleTree > Part.MapleLeaf")

local function sway(leaf: Part, deltaTime: number)

	leaf.CFrame *= CFrame.fromEulerAnglesXYZ(0, math.rad(20) * deltaTime, 0)

end

local function fall(leaf: Part)

	leaf.Anchored = false

end

-- OnAdded fires once for every leaf already matching, then for each new match

function mapleLeaves.OnAdded(leaf: Part)

	leaf.Material = Enum.Material.Neon

end

-- OnRemoved fires when a leaf stops matching (untagged, reparented out of the tree, or destroyed)

function mapleLeaves.OnRemoved(leaf: Part)

	leaf.Material = Enum.Material.Plastic

end

-- RunService callback: fires once per heartbeat for each leaf in the collection

function mapleLeaves.OnHeartbeat(leaf: Part, deltaTime: number)

	sway(leaf, deltaTime)

end

-- Event callback: connects to BasePart.Touched on each leaf

function mapleLeaves.OnTouched(leaf: Part, other: BasePart)

	fall(leaf)

end

-- Property callback: fires when a leaf's Color changes

function mapleLeaves.OnPropertyChanged.Color(leaf: Part)

	if leaf.Color == Color3.fromRGB(124, 92, 70) then

		fall(leaf)

	end

end

-- Set every leaf currently in the collection green

mapleLeaves:ForEach(function(leaf: Part)

	leaf.Color = Color3.fromRGB(0, 255, 0)

end)

```

---

API Reference

Properties

Enabled

Collection.Enabled :[boolean](/docs/en-us/luau/booleans)

Provide feedback

---

Query

Collection.Query :[string](/docs/en-us/luau/strings)

Provide feedback

---

Root

Collection.Root :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Provide feedback

---

Methods

Destroy

Collection:Destroy ()

Provide feedback

---

ForEach

Collection:ForEach (callback :[function](/docs/en-us/luau/functions) )

Parameters

|

callback :[function](/docs/en-us/luau/functions)

 |

Provide feedback

---

GetCount

Collection:GetCount () :[number](/docs/en-us/luau/numbers)

Returns

[number](/docs/en-us/luau/numbers)

Provide feedback

---

Jump to

▼

Collection

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Properties](#properties)

[Enabled](#Enabled)

[Query](#Query)

[Root](#Root)

[Methods](#methods)

[Destroy()](#Destroy)

[ForEach()](#ForEach)

[GetCount()](#GetCount)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
