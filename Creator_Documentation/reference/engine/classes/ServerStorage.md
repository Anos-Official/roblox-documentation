<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/ServerStorage -->

ServerStorage | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ServerStorage.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [ServerStorage](/docs/en-us/reference/engine/classes/ServerStorage)

English

Feedback

Engine Class

ServerStorage

Not Creatable

Service

Not Replicated

---

## Summary

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

ServerStorage Map Rotation

```

local ServerStorage = game:GetService("ServerStorage")

local ROUND_TIME = 5

local map1 = Instance.new("Model")

map1.Name = "Map1"

map1.Parent = ServerStorage

local map2 = Instance.new("Model")

map2.Name = "Map2"

map2.Parent = ServerStorage

local map3 = Instance.new("Model")

map3.Name = "Map3"

map3.Parent = ServerStorage

local maps = { map1, map2, map3 }

local RNG = Random.new()

local currentMap = nil

local lastPick = nil

while true do

	print("New map!")

	-- remove current map

	if currentMap then

		currentMap:Destroy()

	end

	-- pick a map

	local randomPick = nil

	if #maps > 1 then

		repeat

			randomPick = RNG:NextInteger(1, #maps)

		until randomPick ~= lastPick

		lastPick = randomPick

	end

	-- fetch new map

	local map = maps[randomPick]

	currentMap = map:Clone()

	currentMap.Parent = workspace

	task.wait(ROUND_TIME)

end

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
