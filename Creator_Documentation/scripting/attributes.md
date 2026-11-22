<!-- Source: https://create.roblox.com/docs/en-us/scripting/attributes -->

Properties and attributes | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/scripting/attributes.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/en-us/scripting)

# Properties and attributes

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/scripting/attributes.md)

Making games interactive often means manipulating object properties and attributes:

-

Properties are part of the object class. For example, the [BasePart.Anchored](/docs/en-us/reference/engine/classes/BasePart#Anchored)  property controls physics for the part. In a track and field game, you might want to anchor a discus or javelin the instant it lands so that players have a visual indicator of how far it traveled.

-

Attributes are essentially custom properties that you define. For example, the [Plant](/docs/en-us/resources/plant-reference-project)  reference project uses attributes to set the purchase price for seeds and the maximum plant size that a pot can hold.

## [Replication order](#replication-order)[](#replication-order)

Before you begin retrieving and manipulating objects, you must have an understanding of replication order.

The Roblox Engine doesn't guarantee the order in which objects (and changes to objects) are replicated from the server to the client, which makes the [Instance:WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild)  method essential for accessing objects in client scripts, particularly objects in the [Workspace](/docs/en-us/reference/engine/classes/Workspace) .

For example, if a server script changes a property of some instance in the Workspace and then calls [RemoteEvent:FireAllClients()](/docs/en-us/reference/engine/classes/RemoteEvent#FireAllClients) , the property change might replicate to the client before or after [RemoteEvent.OnClientEvent](/docs/en-us/reference/engine/classes/RemoteEvent#OnClientEvent)  fires. Use the available methods and events to [detect changes](#detect-changes)  rather than assuming a change has replicated. Changes of the same type, such as two attribute changes, generally do  arrive in order.

When clients first launch a game, some aspects of replication and script execution are predictable:

1.

The client loads the contents of [ReplicatedFirst](/docs/en-us/reference/engine/classes/ReplicatedFirst) , such as a loading screen, assets, and scripts.

2.

[LocalScripts](/docs/en-us/reference/engine/classes/LocalScript)  (and [Scripts](/docs/en-us/reference/engine/classes/Script)  with a [RunContext](/docs/en-us/reference/engine/classes/Script#RunContext)  of [Client](/docs/en-us/reference/engine/enums/RunContext#Client) ) in [ReplicatedFirst](/docs/en-us/reference/engine/classes/ReplicatedFirst)  run. These scripts can safely get objects from [ReplicatedFirst](/docs/en-us/reference/engine/classes/ReplicatedFirst)  without using [Instance:WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild) :

```

-- Safe

local ReplicatedFirst = game:GetService("ReplicatedFirst")

local LoadingScreen = require(ReplicatedFirst.LoadingScreen)

```

These scripts can't  safely get objects from other [services](/docs/en-us/scripting/services) , because they might not have loaded yet:

```

-- Not safe

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local PickupManager = require(ReplicatedStorage.PickupManager)

```

You can  use [WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild)  in these scripts to get objects from other services, but doing so negates the benefits of using [ReplicatedFirst](/docs/en-us/reference/engine/classes/ReplicatedFirst) .

3.

The client continues loading the rest of the game.

4.

When it finishes, the [Loaded](/docs/en-us/reference/engine/classes/DataModel#Loaded)  event fires and [IsLoaded()](/docs/en-us/reference/engine/classes/DataModel#IsLoaded)  returns true.

5.

[LocalScripts](/docs/en-us/reference/engine/classes/LocalScript)  in Players.[Player].PlayerScripts  (copied from [StarterPlayerScripts](/docs/en-us/reference/engine/classes/StarterPlayerScripts) ) run, as well as client [Scripts](/docs/en-us/reference/engine/classes/Script)  in [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage) . These scripts can safely get objects from [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage)  without using [WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild) .

6.

The player's [Character](/docs/en-us/reference/engine/classes/Player#Character)  model spawns in the game.

7.

[LocalScripts](/docs/en-us/reference/engine/classes/LocalScript)  in Workspace.[Character]  (copied from [StarterCharacterScripts](/docs/en-us/reference/engine/classes/StarterCharacterScripts) ) run.

If your game uses [instance streaming](/docs/en-us/workspace/streaming)  ([Workspace.StreamingEnabled](/docs/en-us/reference/engine/classes/Workspace#StreamingEnabled) ), some or most objects might not have loaded into the workspace, so using [WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild)  to access workspace objects becomes an even more important safety measure. In particular, see [stream in](/docs/en-us/workspace/streaming#stream-in)  and [per-model streaming controls](/docs/en-us/workspace/streaming#per-model-streaming-controls)  for additional information on loading and tuning streaming behavior.

## [Get objects](#get-objects)[](#get-objects)

The first step to modifying object properties and attributes is to get a reference to the object. The simplest solution is to make the script a child of the object in the Explorer  and use script.Parent  to reference the object.

 ![A script parented to a model in the Explorer.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Script-Parent-Model.png)

```

local sign = script.Parent

```

The more universal solution is to get the object from a [service](/docs/en-us/scripting/services)  using methods like [Instance:FindFirstChild()](/docs/en-us/reference/engine/classes/Instance#FindFirstChild)  or [Instance:WaitForChild()](/docs/en-us/reference/engine/classes/Instance#WaitForChild) .

 ![A Model within a Folder in ReplicatedStorage.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Script-Parent-ReplicatedStorage.png)

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local signsFolder = ReplicatedStorage:WaitForChild("Signs")

local sign = signsFolder:WaitForChild("InteractiveSign")

```

## [Modify properties](#modify-properties)[](#modify-properties)

Properties are straightforward to access — just use a .  after the object reference — although if you're working with a model, you might need to choose an individual part rather than the model itself.

 ![A Model within ReplicatedStorage.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-Model.png)

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local chair = ReplicatedStorage:WaitForChild("Chair")

chair.LeftArmRest.Size = Vector3.new(10, 1, 10)

```

## [Create attributes](#create-attributes)[](#create-attributes)

Although you can create attributes programmatically, the more common solution is to create them with default values in the Studio user interface. Then you can use scripts to modify their values in response to player actions.

 ![A script within a folder in ReplicatedStorage.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Attributes-Example.png)

For information on creating attributes in Studio, see [instance attributes](/docs/en-us/studio/properties#instance-attributes) .

## [Set attributes](#set-attributes)[](#set-attributes)

To modify an attribute's value, call [Instance:SetAttribute()](/docs/en-us/reference/engine/classes/Instance#SetAttribute)  with a name and value.

Create or Modify Attribute

```

local cabbage = script.Parent

cabbage:SetAttribute("Harvestable", true)

```

If the attribute doesn't already exist, this method creates it.

## [Get attribute values](#get-attribute-values)[](#get-attribute-values)

To get the value of one existing attribute, call [Instance:GetAttribute()](/docs/en-us/reference/engine/classes/Instance#GetAttribute)  on the instance.

Get Attribute Value

```

local cabbage = script.Parent

cabbage:SetAttribute("Harvestable", true)

local isHarvestable = cabbage:GetAttribute("Harvestable")

print(isHarvestable) --> true

```

Similarly, you can get all attributes by calling [Instance:GetAttributes()](/docs/en-us/reference/engine/classes/Instance#GetAttributes) . This method returns a dictionary of key-value pairs.

Get All Attributes

```

local cabbage = script.Parent

local cabbageAttributes = cabbage:GetAttributes()

print(cabbageAttributes.GrowthRate) --> 2

for k, v in cabbageAttributes do

	print(k, v)

end

```

## [Delete attributes](#delete-attributes)[](#delete-attributes)

To delete an attribute, set its value to nil .

Delete Attribute

```

local cabbage = script.Parent

cabbage:SetAttribute("GrowthRate", nil)

```

## [Detect changes](#detect-changes)[](#detect-changes)

There are several ways to listen for changes to properties and attributes:

-

The [Instance.AttributeChanged](/docs/en-us/reference/engine/classes/Instance#AttributeChanged)  event listens for changes to any attribute and passes the name of the changed attribute as a parameter.

-

The [Instance:GetPropertyChangedSignal()](/docs/en-us/reference/engine/classes/Instance#GetPropertyChangedSignal)  method lets you listen for changes to one property and passes no parameters.

-

The [Instance:GetAttributeChangedSignal()](/docs/en-us/reference/engine/classes/Instance#GetAttributeChangedSignal)  method lets you listen for changes to one attribute and passes no parameters.

Due to the minimal information that these events and methods pass as parameters, all of them are a good fit for anonymous functions, particularly [Instance:GetPropertyChangedSignal()](/docs/en-us/reference/engine/classes/Instance#GetPropertyChangedSignal)  and [Instance:GetAttributeChangedSignal()](/docs/en-us/reference/engine/classes/Instance#GetAttributeChangedSignal) . To learn more about anonymous functions and working with events, see [Events](/docs/en-us/scripting/events) .

Listen for Changes

```

local cabbage = script.Parent

-- Local functions

local function onAnyPropertyChange(property)

	-- Ignore changes to attributes

	if property ~= "Attributes" then

		print(property) --> Name

		print(cabbage[property]) --> Cabbage1

	end

end

local function onAnyAttributeChange(attribute)

	print(attribute) --> Grow, GrowthRate

	print(cabbage:GetAttribute(attribute)) --> false, 3

end

-- Listen for changes and connect to local functions

cabbage.Changed:Connect(onAnyPropertyChange)

cabbage.AttributeChanged:Connect(onAnyAttributeChange)

-- Listen for changes and connect to anonymous functions

cabbage:GetPropertyChangedSignal("Name"):Connect(function()

	print(cabbage.Name) --> Cabbage1

end)

cabbage:GetAttributeChangedSignal("GrowthRate"):Connect(function()

	print(cabbage:GetAttribute("GrowthRate")) --> 3

end)

-- Fires Changed and GetPropertyChangedSignal()

cabbage.Name = "Cabbage1"

-- Fires Changed and AttributeChanged

cabbage:SetAttribute("Grow", false)

-- Fires Changed, AttributeChanged, and GetAttributeChangedSignal()

cabbage:SetAttribute("GrowthRate", 3)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
