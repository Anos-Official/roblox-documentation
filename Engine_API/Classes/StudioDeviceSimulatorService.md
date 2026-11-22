<!-- Source: https://create.roblox.com/docs/reference/engine/classes/StudioDeviceSimulatorService -->

StudioDeviceSimulatorService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/StudioDeviceSimulatorService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [StudioDeviceSimulatorService](/docs/reference/engine/classes/StudioDeviceSimulatorService)

English

Feedback

Engine Class

StudioDeviceSimulatorService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[CreateDeviceAsync](#CreateDeviceAsync) (config :  [Dictionary](/docs/luau/tables#dictionaries) ) :[string](/docs/luau/strings)

 |
| --- | --- |
|

[GetDeviceAsync](#GetDeviceAsync) () :[string](/docs/luau/strings)

 |
|

[GetDeviceInfoAsync](#GetDeviceInfoAsync) (deviceId :  [string](/docs/luau/strings) ) :[Dictionary](/docs/luau/tables#dictionaries)

 |
|

[GetDeviceListAsync](#GetDeviceListAsync) () :[{any}](/docs/luau/tables#arrays)

 |
|

[GetOrientationAsync](#GetOrientationAsync) () :[Enum.ScreenOrientation](/docs/reference/engine/enums/ScreenOrientation)

 |
|

[GetPixelDensityAsync](#GetPixelDensityAsync) () :[number](/docs/luau/numbers)

 |
|

[GetResolutionAsync](#GetResolutionAsync) () :[Vector2](/docs/reference/engine/datatypes/Vector2)

 |
|

[GetScalingModeAsync](#GetScalingModeAsync) () :[Enum.DeviceSimulatorScalingMode](/docs/reference/engine/enums/DeviceSimulatorScalingMode)

 |
|

[RemoveDeviceAsync](#RemoveDeviceAsync) (deviceId :  [string](/docs/luau/strings) ) : ()

 |
|

[SetDeviceAsync](#SetDeviceAsync) (deviceId :  [string](/docs/luau/strings) ) : ()

 |
|

[SetOrientationAsync](#SetOrientationAsync) (orientation :  [Enum.ScreenOrientation](/docs/reference/engine/enums/ScreenOrientation) ) : ()

 |
|

[SetPixelDensityAsync](#SetPixelDensityAsync) (density :  [number](/docs/luau/numbers) ) : ()

 |
|

[SetResolutionAsync](#SetResolutionAsync) (width :  [number](/docs/luau/numbers) , height :  [number](/docs/luau/numbers) ) : ()

 |
|

[SetScalingModeAsync](#SetScalingModeAsync) (mode :  [Enum.DeviceSimulatorScalingMode](/docs/reference/engine/enums/DeviceSimulatorScalingMode) ) : ()

 |
|

[StopSimulationAsync](#StopSimulationAsync) () : ()

 |
|

[UpdateDeviceAsync](#UpdateDeviceAsync) (deviceId :  [string](/docs/luau/strings) , config :  [Dictionary](/docs/luau/tables#dictionaries) ) : ()

 |

Events

|

[ConfigurationChanged](#ConfigurationChanged) () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

CreateDeviceAsync

Yields

Plugin Security

StudioDeviceSimulatorService:CreateDeviceAsync (config :[Dictionary](/docs/luau/tables#dictionaries) ) :[string](/docs/luau/strings)

Parameters

|

config :[Dictionary](/docs/luau/tables#dictionaries)

 |

Returns

[string](/docs/luau/strings)

Code Samples

Create Device example

```

local id = Simulator:CreateDeviceAsync({

    Name = "My Custom Tablet",

    Width = 2560,

    Height = 1600,

    PixelDensity = 300,

    DeviceForm = Enum.DeviceForm.Tablet,

})

```

Provide feedback

---

GetDeviceAsync

Yields

Plugin Security

StudioDeviceSimulatorService:GetDeviceAsync () :[string](/docs/luau/strings)

Returns

[string](/docs/luau/strings)

Provide feedback

---

GetDeviceInfoAsync

Yields

Plugin Security

StudioDeviceSimulatorService:GetDeviceInfoAsync (deviceId :[string](/docs/luau/strings) ) :[Dictionary](/docs/luau/tables#dictionaries)

Parameters

|

deviceId :[string](/docs/luau/strings)

 |

Returns

[Dictionary](/docs/luau/tables#dictionaries)

Provide feedback

---

GetDeviceListAsync

Yields

Plugin Security

StudioDeviceSimulatorService:GetDeviceListAsync () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Code Samples

Get device list example

```

local Simulator = game:GetService("StudioDeviceSimulatorService")

local devices = Simulator:GetDeviceListAsync()

for _, deviceId in devices do

    print(deviceId)

end

```

Provide feedback

---

GetOrientationAsync

Yields

Plugin Security

StudioDeviceSimulatorService:GetOrientationAsync () :[Enum.ScreenOrientation](/docs/reference/engine/enums/ScreenOrientation)

Returns

[Enum.ScreenOrientation](/docs/reference/engine/enums/ScreenOrientation)

Provide feedback

---

GetPixelDensityAsync

Yields

Plugin Security

StudioDeviceSimulatorService:GetPixelDensityAsync () :[number](/docs/luau/numbers)

Returns

[number](/docs/luau/numbers)

Provide feedback

---

GetResolutionAsync

Yields

Plugin Security

StudioDeviceSimulatorService:GetResolutionAsync () :[Vector2](/docs/reference/engine/datatypes/Vector2)

Returns

[Vector2](/docs/reference/engine/datatypes/Vector2)

Provide feedback

---

GetScalingModeAsync

Yields

Plugin Security

StudioDeviceSimulatorService:GetScalingModeAsync () :[Enum.DeviceSimulatorScalingMode](/docs/reference/engine/enums/DeviceSimulatorScalingMode)

Returns

[Enum.DeviceSimulatorScalingMode](/docs/reference/engine/enums/DeviceSimulatorScalingMode)

Provide feedback

---

RemoveDeviceAsync

Yields

Plugin Security

StudioDeviceSimulatorService:RemoveDeviceAsync (deviceId :[string](/docs/luau/strings) ) : ()

Parameters

|

deviceId :[string](/docs/luau/strings)

 |

Returns

()

Provide feedback

---

SetDeviceAsync

Yields

Plugin Security

StudioDeviceSimulatorService:SetDeviceAsync (deviceId :[string](/docs/luau/strings) ) : ()

Parameters

|

deviceId :[string](/docs/luau/strings)

 |

Returns

()

Provide feedback

---

SetOrientationAsync

Yields

Plugin Security

StudioDeviceSimulatorService:SetOrientationAsync (orientation :[Enum.ScreenOrientation](/docs/reference/engine/enums/ScreenOrientation) ) : ()

Parameters

|

orientation :[Enum.ScreenOrientation](/docs/reference/engine/enums/ScreenOrientation)

 |

Returns

()

Provide feedback

---

SetPixelDensityAsync

Yields

Plugin Security

StudioDeviceSimulatorService:SetPixelDensityAsync (density :[number](/docs/luau/numbers) ) : ()

Parameters

|

density :[number](/docs/luau/numbers)

 |

Returns

()

Provide feedback

---

SetResolutionAsync

Yields

Plugin Security

StudioDeviceSimulatorService:SetResolutionAsync (

width :[number](/docs/luau/numbers) , height :[number](/docs/luau/numbers)

) : ()

Parameters

|

width :[number](/docs/luau/numbers)

 |
|

height :[number](/docs/luau/numbers)

 |

Returns

()

Provide feedback

---

SetScalingModeAsync

Yields

Plugin Security

StudioDeviceSimulatorService:SetScalingModeAsync (mode :[Enum.DeviceSimulatorScalingMode](/docs/reference/engine/enums/DeviceSimulatorScalingMode) ) : ()

Parameters

|

mode :[Enum.DeviceSimulatorScalingMode](/docs/reference/engine/enums/DeviceSimulatorScalingMode)

 |

Returns

()

Provide feedback

---

StopSimulationAsync

Yields

Plugin Security

StudioDeviceSimulatorService:StopSimulationAsync () : ()

Returns

()

Provide feedback

---

UpdateDeviceAsync

Yields

Plugin Security

StudioDeviceSimulatorService:UpdateDeviceAsync (

deviceId :[string](/docs/luau/strings) , config :[Dictionary](/docs/luau/tables#dictionaries)

) : ()

Parameters

|

deviceId :[string](/docs/luau/strings)

 |
|

config :[Dictionary](/docs/luau/tables#dictionaries)

 |

Returns

()

Code Samples

Update Device example

```

Simulator:UpdateDeviceAsync(id, {

    Name = "My Custom Tablet",

    Width = 2732,

    Height = 2048,

    PixelDensity = 264,

    DeviceForm = Enum.DeviceForm.Tablet,

})

```

Provide feedback

---

Events

ConfigurationChanged

Plugin Security

StudioDeviceSimulatorService.ConfigurationChanged () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Code Samples

Configuration changed example

```

Simulator.ConfigurationChanged:Connect(function()

    local deviceId = Simulator:GetDeviceAsync()

    if deviceId ~= "default" then

        local res = Simulator:GetResolutionAsync()

        print(string.format("Active: %s @ %dx%d", deviceId, res.X, res.Y))

    end

end)

```

Provide feedback

---

Jump to

▼

StudioDeviceSimulatorService

[Summary](#summary)

[Methods](#summary-methods)

[Events](#summary-events)

[Methods](#methods)

[CreateDeviceAsync()](#CreateDeviceAsync)

[GetDeviceAsync()](#GetDeviceAsync)

[GetDeviceInfoAsync()](#GetDeviceInfoAsync)

[GetDeviceListAsync()](#GetDeviceListAsync)

[GetOrientationAsync()](#GetOrientationAsync)

[GetPixelDensityAsync()](#GetPixelDensityAsync)

[GetResolutionAsync()](#GetResolutionAsync)

[GetScalingModeAsync()](#GetScalingModeAsync)

[RemoveDeviceAsync()](#RemoveDeviceAsync)

[SetDeviceAsync()](#SetDeviceAsync)

[SetOrientationAsync()](#SetOrientationAsync)

[SetPixelDensityAsync()](#SetPixelDensityAsync)

[SetResolutionAsync()](#SetResolutionAsync)

[SetScalingModeAsync()](#SetScalingModeAsync)

[StopSimulationAsync()](#StopSimulationAsync)

[UpdateDeviceAsync()](#UpdateDeviceAsync)

[Events](#events)

[ConfigurationChanged](#ConfigurationChanged)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
