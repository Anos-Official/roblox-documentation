<!-- Source: https://create.roblox.com/docs/reference/engine/classes/UserSettings -->

UserSettings | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/UserSettings.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [ServiceProvider](/docs/reference/engine/classes/ServiceProvider)
8. /
9. [GenericSettings](/docs/reference/engine/classes/GenericSettings)
10. /
11. [UserSettings](/docs/reference/engine/classes/UserSettings)

English

Feedback

Engine Class

UserSettings

Not Creatable

---

## Summary

Methods

|

[IsUserFeatureEnabled](#IsUserFeatureEnabled) (name :  [string](/docs/luau/strings) ) :[boolean](/docs/luau/booleans)

 |
| --- | --- |
|

[Reset](#Reset) () : ()

 |

Inherited Members

7  inherited from [ServiceProvider](/docs/reference/engine/classes/ServiceProvider)

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

IsUserFeatureEnabled Sample

```

if UserSettings():IsUserFeatureEnabled("UserNoCameraClickToMove") then

	print("'ClickToMove' should no longer be loaded from the CameraScript!")

else

	print("'ClickToMove' is still loaded from the CameraScript!")

end

```

Full Screen Mode Detection

```

local gameSettings = UserSettings().GameSettings

local function checkFullScreenMode()

	local inFullscreen = gameSettings:InFullScreen()

	if inFullscreen then

		print("Full Screen mode enabled!")

	else

		print("Full Screen mode disabled!")

	end

end

checkFullScreenMode()

gameSettings.FullscreenChanged:Connect(checkFullScreenMode)

```

UserGameSettings Listener

```

local gameSettings = UserSettings().GameSettings

local function onGameSettingChanged(nameOfSetting)

	-- Fetch the value of this setting through a pcall to make sure we can retrieve it.

	-- Sometimes the event fires with properties that LocalScripts can't access.

	local canGetSetting, setting = pcall(function()

		return gameSettings[nameOfSetting]

	end)

	if canGetSetting then

		print("Your " .. nameOfSetting .. " has changed to: " .. tostring(setting))

	end

end

gameSettings.Changed:Connect(onGameSettingChanged)

```

---

API Reference

Methods

IsUserFeatureEnabled

Capabilities: Players

UserSettings:IsUserFeatureEnabled (name :[string](/docs/luau/strings) ) :[boolean](/docs/luau/booleans)

Parameters

|

name :[string](/docs/luau/strings)

 |

Returns

[boolean](/docs/luau/booleans)

Code Samples

IsUserFeatureEnabled Sample

```

if UserSettings():IsUserFeatureEnabled("UserNoCameraClickToMove") then

	print("'ClickToMove' should no longer be loaded from the CameraScript!")

else

	print("'ClickToMove' is still loaded from the CameraScript!")

end

```

Provide feedback

---

Reset

Capabilities: Players

UserSettings:Reset () : ()

Returns

()

Provide feedback

---

Jump to

▼

UserSettings

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[IsUserFeatureEnabled()](#IsUserFeatureEnabled)

[Reset()](#Reset)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
