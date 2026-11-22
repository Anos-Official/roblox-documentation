<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/Selection -->

Selection | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/Selection.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [Selection](/docs/en-us/reference/engine/classes/Selection)

English

Feedback

Engine Class

Selection

Not Creatable

Service

---

## Summary

Properties

|

[SelectionThickness](#SelectionThickness) :[number](/docs/en-us/luau/numbers)

 |
| --- | --- |

Methods

|

[Add](#Add) (instancesToAdd :  Instances ) : ()

 |
|

[Get](#Get) () : Instances

 |
|

[Remove](#Remove) (instancesToRemove :  Instances ) : ()

 |
|

[Set](#Set) (selection :  Instances ) : ()

 |

Events

|

[SelectionChanged](#SelectionChanged) () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Selection

```

local Selection = game:GetService("Selection")

for _, object in pairs(Selection:Get()) do

	if object:IsA("BasePart") then

		object.CFrame = object.CFrame * CFrame.Angles(0, math.pi / 2, 0)

	end

end

```

---

API Reference

Properties

SelectionThickness

Read Only

Not Replicated

Read Parallel

Capabilities: Basic

Selection.SelectionThickness :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Methods

Add

Plugin Security

Capabilities: Basic

Selection:Add (instancesToAdd : Instances ) : ()

Parameters

|

instancesToAdd : Instances

 |

Returns

()

Provide feedback

---

Get

Plugin Security

Capabilities: Basic

Selection:Get () : Instances

Returns

Instances

Code Samples

Selection

```

local Selection = game:GetService("Selection")

for _, object in pairs(Selection:Get()) do

	if object:IsA("BasePart") then

		object.CFrame = object.CFrame * CFrame.Angles(0, math.pi / 2, 0)

	end

end

```

Selection.SelectionChanged

```

local selection = game:GetService("Selection")

selection.SelectionChanged:Connect(function()

	print("Selection contains " .. #selection:Get() .. " items.")

end)

```

Provide feedback

---

Remove

Plugin Security

Capabilities: Basic

Selection:Remove (instancesToRemove : Instances ) : ()

Parameters

|

instancesToRemove : Instances

 |

Returns

()

Provide feedback

---

Set

Plugin Security

Capabilities: Basic

Selection:Set (selection : Instances ) : ()

Parameters

|

selection : Instances

 |

Returns

()

Code Samples

Selection Set

```

local Selection = game:GetService("Selection")

local newSelection = {}

for _, object in pairs(workspace:GetDescendants()) do

	if object:IsA("BasePart") and object.BrickColor == BrickColor.new("Bright red") then

		table.insert(newSelection, object)

	end

end

Selection:Set(newSelection)

```

Set

```

local selected = Selection:Get()

table.insert(selected, object)

Selection:Set(selected)

```

Provide feedback

---

Events

SelectionChanged

Capabilities: Basic

Selection.SelectionChanged () :[RBXScriptSignal](/docs/en-us/reference/engine/datatypes/RBXScriptSignal)

Code Samples

Selection.SelectionChanged

```

local selection = game:GetService("Selection")

selection.SelectionChanged:Connect(function()

	print("Selection contains " .. #selection:Get() .. " items.")

end)

```

Provide feedback

---

Jump to

▼

Selection

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[SelectionThickness](#SelectionThickness)

[Methods](#methods)

[Add()](#Add)

[Get()](#Get)

[Remove()](#Remove)

[Set()](#Set)

[Events](#events)

[SelectionChanged](#SelectionChanged)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
