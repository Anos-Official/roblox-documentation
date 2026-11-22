<!-- Source: https://create.roblox.com/docs/reference/engine/classes/HapticService -->

HapticService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/HapticService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [HapticService](/docs/reference/engine/classes/HapticService)

English

Feedback

Engine Class

HapticService

Deprecated

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[GetMotor](#GetMotor) (inputType :  [Enum.UserInputType](/docs/reference/engine/enums/UserInputType) , vibrationMotor :  [Enum.VibrationMotor](/docs/reference/engine/enums/VibrationMotor) ) :[Tuple](/docs/luau/tuples)

 |
| --- | --- |
|

[IsMotorSupported](#IsMotorSupported) (inputType :  [Enum.UserInputType](/docs/reference/engine/enums/UserInputType) , vibrationMotor :  [Enum.VibrationMotor](/docs/reference/engine/enums/VibrationMotor) ) :[boolean](/docs/luau/booleans)

 |
|

[IsVibrationSupported](#IsVibrationSupported) (inputType :  [Enum.UserInputType](/docs/reference/engine/enums/UserInputType) ) :[boolean](/docs/luau/booleans)

 |
|

[SetMotor](#SetMotor) (inputType :  [Enum.UserInputType](/docs/reference/engine/enums/UserInputType) , vibrationMotor :  [Enum.VibrationMotor](/docs/reference/engine/enums/VibrationMotor) , vibrationValues :  [Tuple](/docs/luau/tuples) ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

GetMotor

Capabilities: Input

HapticService:GetMotor (

inputType :[Enum.UserInputType](/docs/reference/engine/enums/UserInputType) , vibrationMotor :[Enum.VibrationMotor](/docs/reference/engine/enums/VibrationMotor)

) :[Tuple](/docs/luau/tuples)

Parameters

|

inputType :[Enum.UserInputType](/docs/reference/engine/enums/UserInputType)

 |
|

vibrationMotor :[Enum.VibrationMotor](/docs/reference/engine/enums/VibrationMotor)

 |

Returns

[Tuple](/docs/luau/tuples)

Provide feedback

---

IsMotorSupported

Capabilities: Input

HapticService:IsMotorSupported (

inputType :[Enum.UserInputType](/docs/reference/engine/enums/UserInputType) , vibrationMotor :[Enum.VibrationMotor](/docs/reference/engine/enums/VibrationMotor)

) :[boolean](/docs/luau/booleans)

Parameters

|

inputType :[Enum.UserInputType](/docs/reference/engine/enums/UserInputType)

 |
|

vibrationMotor :[Enum.VibrationMotor](/docs/reference/engine/enums/VibrationMotor)

 |

Returns

[boolean](/docs/luau/booleans)

Provide feedback

---

IsVibrationSupported

Capabilities: Input

HapticService:IsVibrationSupported (inputType :[Enum.UserInputType](/docs/reference/engine/enums/UserInputType) ) :[boolean](/docs/luau/booleans)

Parameters

|

inputType :[Enum.UserInputType](/docs/reference/engine/enums/UserInputType)

 |

Returns

[boolean](/docs/luau/booleans)

Provide feedback

---

SetMotor

Capabilities: Input

HapticService:SetMotor (

inputType :[Enum.UserInputType](/docs/reference/engine/enums/UserInputType) , vibrationMotor :[Enum.VibrationMotor](/docs/reference/engine/enums/VibrationMotor) , vibrationValues :[Tuple](/docs/luau/tuples)

) : ()

Parameters

|

inputType :[Enum.UserInputType](/docs/reference/engine/enums/UserInputType)

 |
|

vibrationMotor :[Enum.VibrationMotor](/docs/reference/engine/enums/VibrationMotor)

 |
|

vibrationValues :[Tuple](/docs/luau/tuples)

 |

Returns

()

Code Samples

HapticService:SetMotor()

```

local UserInputService = game:GetService("UserInputService")

local HapticService = game:GetService("HapticService")

local cachedInputs = {}

local keyToVibration = {

	[Enum.KeyCode.ButtonL2] = Enum.VibrationMotor.Small,

	[Enum.KeyCode.ButtonR2] = Enum.VibrationMotor.Large,

}

local function onInputChanged(property)

	if property == "Position" then

		HapticService:SetMotor(inputType, vibrationMotor, input.Position.Z)

	end

end

local function onInputBegan(input)

	if not cachedInputs[input] then

		local inputType = input.UserInputType

		if inputType.Name:find("Gamepad") then

			local vibrationMotor = keyToVibration[input.KeyCode]

			if vibrationMotor then

				-- Watch this input manually to accurately update the vibration motor

				cachedInputs[input] = input.Changed:Connect(onInputChanged)

			end

		end

	end

end

UserInputService.InputBegan:Connect(onInputBegan)

```

Provide feedback

---

Jump to

▼

HapticService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetMotor()](#GetMotor)

[IsMotorSupported()](#IsMotorSupported)

[IsVibrationSupported()](#IsVibrationSupported)

[SetMotor()](#SetMotor)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
