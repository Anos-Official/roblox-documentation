<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/CollectionService -->

CollectionService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/CollectionService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [CollectionService](/docs/en-us/reference/engine/classes/CollectionService)

English

Feedback

Engine Class

CollectionService

Not Creatable

Service

---

## Summary

Methods

|

[AddTag](#AddTag) (instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) , tag :  [string](/docs/en-us/luau/strings) ) : ()

 |
| --- | --- |
|

[CreateCollection](#CreateCollection) (query :  [string](/docs/en-us/luau/strings) , root :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[Collection](/docs/en-us/reference/engine/datatypes/Collection)

 |
|

[GetAllTags](#GetAllTags) () :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetCollection](#GetCollection) (class :  [string](/docs/en-us/luau/strings) ) : Instances

Deprecated

 |
|

[GetCollections](#GetCollections) (instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[GetInstanceAddedSignal](#GetInstanceAddedSignal) (tag :  [string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[GetInstanceRemovedSignal](#GetInstanceRemovedSignal) (tag :  [string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[GetTagged](#GetTagged) (tag :  [string](/docs/en-us/luau/strings) ) : Instances

 |
|

[GetTags](#GetTags) (instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
|

[HasTag](#HasTag) (instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) , tag :  [string](/docs/en-us/luau/strings) ) :[boolean](/docs/en-us/luau/booleans)

 |
|

[RemoveTag](#RemoveTag) (instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) , tag :  [string](/docs/en-us/luau/strings) ) : ()

 |

Events

|

[ItemAdded](#ItemAdded) (instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Deprecated

 |
|

[ItemRemoved](#ItemRemoved) (instance :  [Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Deprecated

 |
|

[TagAdded](#TagAdded) (tag :  [string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |
|

[TagRemoved](#TagRemoved) (tag :  [string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

AddTag

Capabilities: Basic

CollectionService:AddTag (

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance) , tag :[string](/docs/en-us/luau/strings)

) : ()

Parameters

|

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

tag :[string](/docs/en-us/luau/strings)

 |

Returns

()

Provide feedback

---

CreateCollection

Capabilities: Basic

CollectionService:CreateCollection (

query :[string](/docs/en-us/luau/strings) , root :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

) :[Collection](/docs/en-us/reference/engine/datatypes/Collection)

Parameters

|

query :[string](/docs/en-us/luau/strings)

 |
|

root :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

Default Value: nil |

Returns

[Collection](/docs/en-us/reference/engine/datatypes/Collection)

Provide feedback

---

GetAllTags

Write Parallel

Capabilities: Basic

CollectionService:GetAllTags () :[{any}](/docs/en-us/luau/tables#arrays)

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetCollection

Deprecated

Show details

---

GetCollections

Capabilities: Basic

CollectionService:GetCollections (instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Provide feedback

---

GetInstanceAddedSignal

Capabilities: Basic

CollectionService:GetInstanceAddedSignal (tag :[string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

tag :[string](/docs/en-us/luau/strings)

 |

Returns

[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Code Samples

Deadly Bricks using CollectionService

```

local CollectionService = game:GetService("CollectionService")

local tag = "Deadly"

local function onDeadlyPartTouched(otherPart)

	if not otherPart.Parent then

		return

	end

	local humanoid = otherPart.Parent:FindFirstChildOfClass("Humanoid")

	if humanoid then

		humanoid.Health = 0

	end

end

-- Save the connections so they can be disconnected when the tag is removed

local connections = {}

local function onInstanceAdded(object)

	-- Confirm that the object with this tag is a BasePart

	if object:IsA("BasePart") then

		connections[object] = object.Touched:Connect(onDeadlyPartTouched)

	end

end

local function onInstanceRemoved(object)

	-- If there is a stored connection on this object, disconnect/remove it

	if connections[object] then

		connections[object]:Disconnect()

		connections[object] = nil

	end

end

-- Listen for this tag being applied to objects

CollectionService:GetInstanceAddedSignal(tag):Connect(onInstanceAdded)

CollectionService:GetInstanceRemovedSignal(tag):Connect(onInstanceRemoved)

-- Also detect any objects that already have the tag

for _, object in pairs(CollectionService:GetTagged(tag)) do

	onInstanceAdded(object)

end

```

Provide feedback

---

GetInstanceRemovedSignal

Capabilities: Basic

CollectionService:GetInstanceRemovedSignal (tag :[string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

tag :[string](/docs/en-us/luau/strings)

 |

Returns

[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Code Samples

Deadly Bricks using CollectionService

```

local CollectionService = game:GetService("CollectionService")

local tag = "Deadly"

local function onDeadlyPartTouched(otherPart)

	if not otherPart.Parent then

		return

	end

	local humanoid = otherPart.Parent:FindFirstChildOfClass("Humanoid")

	if humanoid then

		humanoid.Health = 0

	end

end

-- Save the connections so they can be disconnected when the tag is removed

local connections = {}

local function onInstanceAdded(object)

	-- Confirm that the object with this tag is a BasePart

	if object:IsA("BasePart") then

		connections[object] = object.Touched:Connect(onDeadlyPartTouched)

	end

end

local function onInstanceRemoved(object)

	-- If there is a stored connection on this object, disconnect/remove it

	if connections[object] then

		connections[object]:Disconnect()

		connections[object] = nil

	end

end

-- Listen for this tag being applied to objects

CollectionService:GetInstanceAddedSignal(tag):Connect(onInstanceAdded)

CollectionService:GetInstanceRemovedSignal(tag):Connect(onInstanceRemoved)

-- Also detect any objects that already have the tag

for _, object in pairs(CollectionService:GetTagged(tag)) do

	onInstanceAdded(object)

end

```

Provide feedback

---

GetTagged

Write Parallel

Capabilities: Basic

CollectionService:GetTagged (tag :[string](/docs/en-us/luau/strings) ) : Instances

Parameters

|

tag :[string](/docs/en-us/luau/strings)

 |

Returns

Instances

Code Samples

Deadly Bricks using CollectionService

```

local CollectionService = game:GetService("CollectionService")

local tag = "Deadly"

local function onDeadlyPartTouched(otherPart)

	if not otherPart.Parent then

		return

	end

	local humanoid = otherPart.Parent:FindFirstChildOfClass("Humanoid")

	if humanoid then

		humanoid.Health = 0

	end

end

-- Save the connections so they can be disconnected when the tag is removed

local connections = {}

local function onInstanceAdded(object)

	-- Confirm that the object with this tag is a BasePart

	if object:IsA("BasePart") then

		connections[object] = object.Touched:Connect(onDeadlyPartTouched)

	end

end

local function onInstanceRemoved(object)

	-- If there is a stored connection on this object, disconnect/remove it

	if connections[object] then

		connections[object]:Disconnect()

		connections[object] = nil

	end

end

-- Listen for this tag being applied to objects

CollectionService:GetInstanceAddedSignal(tag):Connect(onInstanceAdded)

CollectionService:GetInstanceRemovedSignal(tag):Connect(onInstanceRemoved)

-- Also detect any objects that already have the tag

for _, object in pairs(CollectionService:GetTagged(tag)) do

	onInstanceAdded(object)

end

```

Provide feedback

---

GetTags

Write Parallel

Capabilities: Basic

CollectionService:GetTags (instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance) ) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

Using Tags and CollectionService

```

local CollectionService = game:GetService("CollectionService")

local Workspace = game:GetService("Workspace")

local object = Workspace.Part

-- Add a tag

CollectionService:AddTag(object, "Deadly")

-- Query for a tag

if CollectionService:HasTag(object, "Deadly") then

	print(object:GetFullName() .. " is deadly")

end

-- List tags on an object

local tags = CollectionService:GetTags(object)

print("The object " .. object:GetFullName() .. " has tags: " .. table.concat(tags, ", "))

-- Remove a tag

CollectionService:RemoveTag(object, "Deadly")

```

Provide feedback

---

HasTag

Write Parallel

Capabilities: Basic

CollectionService:HasTag (

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance) , tag :[string](/docs/en-us/luau/strings)

) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

tag :[string](/docs/en-us/luau/strings)

 |

Returns

[boolean](/docs/en-us/luau/booleans)

Code Samples

Using Tags and CollectionService

```

local CollectionService = game:GetService("CollectionService")

local Workspace = game:GetService("Workspace")

local object = Workspace.Part

-- Add a tag

CollectionService:AddTag(object, "Deadly")

-- Query for a tag

if CollectionService:HasTag(object, "Deadly") then

	print(object:GetFullName() .. " is deadly")

end

-- List tags on an object

local tags = CollectionService:GetTags(object)

print("The object " .. object:GetFullName() .. " has tags: " .. table.concat(tags, ", "))

-- Remove a tag

CollectionService:RemoveTag(object, "Deadly")

```

Provide feedback

---

RemoveTag

Capabilities: Basic

CollectionService:RemoveTag (

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance) , tag :[string](/docs/en-us/luau/strings)

) : ()

Parameters

|

instance :[Instance](/docs/en-us/reference/engine/datatypes/Instance)

 |
|

tag :[string](/docs/en-us/luau/strings)

 |

Returns

()

Code Samples

Using Tags and CollectionService

```

local CollectionService = game:GetService("CollectionService")

local Workspace = game:GetService("Workspace")

local object = Workspace.Part

-- Add a tag

CollectionService:AddTag(object, "Deadly")

-- Query for a tag

if CollectionService:HasTag(object, "Deadly") then

	print(object:GetFullName() .. " is deadly")

end

-- List tags on an object

local tags = CollectionService:GetTags(object)

print("The object " .. object:GetFullName() .. " has tags: " .. table.concat(tags, ", "))

-- Remove a tag

CollectionService:RemoveTag(object, "Deadly")

```

Provide feedback

---

Events

ItemAdded

Deprecated

Show details

---

ItemRemoved

Deprecated

Show details

---

TagAdded

Capabilities: Basic

CollectionService.TagAdded (tag :[string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

tag :[string](/docs/en-us/luau/strings)

 |

Provide feedback

---

TagRemoved

Capabilities: Basic

CollectionService.TagRemoved (tag :[string](/docs/en-us/luau/strings) ) :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Parameters

|

tag :[string](/docs/en-us/luau/strings)

 |

Provide feedback

---

Jump to

▼

CollectionService

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[AddTag()](#AddTag)

[CreateCollection()](#CreateCollection)

[GetAllTags()](#GetAllTags)

[GetCollection()](#GetCollection)

[GetCollections()](#GetCollections)

[GetInstanceAddedSignal()](#GetInstanceAddedSignal)

[GetInstanceRemovedSignal()](#GetInstanceRemovedSignal)

[GetTagged()](#GetTagged)

[GetTags()](#GetTags)

[HasTag()](#HasTag)

[RemoveTag()](#RemoveTag)

[Events](#events)

[ItemAdded](#ItemAdded)

[ItemRemoved](#ItemRemoved)

[TagAdded](#TagAdded)

[TagRemoved](#TagRemoved)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
