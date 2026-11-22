<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/HapticService -->

HapticService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [HapticService](/docs/nl-nl/reference/engine/classes/HapticService)

Nederlands

Feedback

Engine-klasse

HapticService

Verouderd

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/HapticService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GetMotor](#GetMotor) (inputType :  [Enum.UserInputType](/docs/nl-nl/reference/engine/enums/UserInputType) , vibrationMotor :  [Enum.VibrationMotor](/docs/nl-nl/reference/engine/enums/VibrationMotor) ) :[Tuple](/docs/nl-nl/luau/tuples)

 |
| --- | --- |
|

[IsMotorSupported](#IsMotorSupported) (inputType :  [Enum.UserInputType](/docs/nl-nl/reference/engine/enums/UserInputType) , vibrationMotor :  [Enum.VibrationMotor](/docs/nl-nl/reference/engine/enums/VibrationMotor) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[IsVibrationSupported](#IsVibrationSupported) (inputType :  [Enum.UserInputType](/docs/nl-nl/reference/engine/enums/UserInputType) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[SetMotor](#SetMotor) (inputType :  [Enum.UserInputType](/docs/nl-nl/reference/engine/enums/UserInputType) , vibrationMotor :  [Enum.VibrationMotor](/docs/nl-nl/reference/engine/enums/VibrationMotor) , vibrationValues :  [Tuple](/docs/nl-nl/luau/tuples) ) : ()

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

GetMotor

Mogelijkheden: Input

HapticService:GetMotor (

inputType :[Enum.UserInputType](/docs/nl-nl/reference/engine/enums/UserInputType) , vibrationMotor :[Enum.VibrationMotor](/docs/nl-nl/reference/engine/enums/VibrationMotor)

) :[Tuple](/docs/nl-nl/luau/tuples)

Parameters

|

inputType :[Enum.UserInputType](/docs/nl-nl/reference/engine/enums/UserInputType)

 |
|

vibrationMotor :[Enum.VibrationMotor](/docs/nl-nl/reference/engine/enums/VibrationMotor)

 |

Teruggaves

[Tuple](/docs/nl-nl/luau/tuples)

Feedback geven

---

IsMotorSupported

Mogelijkheden: Input

HapticService:IsMotorSupported (

inputType :[Enum.UserInputType](/docs/nl-nl/reference/engine/enums/UserInputType) , vibrationMotor :[Enum.VibrationMotor](/docs/nl-nl/reference/engine/enums/VibrationMotor)

) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

inputType :[Enum.UserInputType](/docs/nl-nl/reference/engine/enums/UserInputType)

 |
|

vibrationMotor :[Enum.VibrationMotor](/docs/nl-nl/reference/engine/enums/VibrationMotor)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

IsVibrationSupported

Mogelijkheden: Input

HapticService:IsVibrationSupported (inputType :[Enum.UserInputType](/docs/nl-nl/reference/engine/enums/UserInputType) ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

inputType :[Enum.UserInputType](/docs/nl-nl/reference/engine/enums/UserInputType)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

SetMotor

Mogelijkheden: Input

HapticService:SetMotor (

inputType :[Enum.UserInputType](/docs/nl-nl/reference/engine/enums/UserInputType) , vibrationMotor :[Enum.VibrationMotor](/docs/nl-nl/reference/engine/enums/VibrationMotor) , vibrationValues :[Tuple](/docs/nl-nl/luau/tuples)

) : ()

Parameters

|

inputType :[Enum.UserInputType](/docs/nl-nl/reference/engine/enums/UserInputType)

 |
|

vibrationMotor :[Enum.VibrationMotor](/docs/nl-nl/reference/engine/enums/VibrationMotor)

 |
|

vibrationValues :[Tuple](/docs/nl-nl/luau/tuples)

 |

Teruggaves

()

Codevoorbeelden

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

				-- Volg deze invoer handmatig om de trillingsmotor nauwkeurig bij te werken

				cachedInputs[input] = input.Changed:Connect(onInputChanged)

			end

		end

	end

end

UserInputService.InputBegan:Connect(onInputBegan)

```

Feedback geven

---

Ga naar

▼

HapticService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GetMotor()](#GetMotor)

[IsMotorSupported()](#IsMotorSupported)

[IsVibrationSupported()](#IsVibrationSupported)

[SetMotor()](#SetMotor)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
