<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/StudioDeviceSimulatorService -->

StudioDeviceSimulatorService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [StudioDeviceSimulatorService](/docs/nl-nl/reference/engine/classes/StudioDeviceSimulatorService)

Nederlands

Feedback

Engine-klasse

StudioDeviceSimulatorService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/StudioDeviceSimulatorService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[CreateDeviceAsync](#CreateDeviceAsync) (config :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[string](/docs/nl-nl/luau/strings)

 |
| --- | --- |
|

[GetDeviceAsync](#GetDeviceAsync) () :[string](/docs/nl-nl/luau/strings)

 |
|

[GetDeviceInfoAsync](#GetDeviceInfoAsync) (deviceId :  [string](/docs/nl-nl/luau/strings) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

[GetDeviceListAsync](#GetDeviceListAsync) () :[{any}](/docs/nl-nl/luau/tables#arrays)

 |
|

[GetOrientationAsync](#GetOrientationAsync) () :[Enum.ScreenOrientation](/docs/nl-nl/reference/engine/enums/ScreenOrientation)

 |
|

[GetPixelDensityAsync](#GetPixelDensityAsync) () :[number](/docs/nl-nl/luau/numbers)

 |
|

[GetResolutionAsync](#GetResolutionAsync) () :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

 |
|

[GetScalingModeAsync](#GetScalingModeAsync) () :[Enum.DeviceSimulatorScalingMode](/docs/nl-nl/reference/engine/enums/DeviceSimulatorScalingMode)

 |
|

[RemoveDeviceAsync](#RemoveDeviceAsync) (deviceId :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[SetDeviceAsync](#SetDeviceAsync) (deviceId :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[SetOrientationAsync](#SetOrientationAsync) (orientation :  [Enum.ScreenOrientation](/docs/nl-nl/reference/engine/enums/ScreenOrientation) ) : ()

 |
|

[SetPixelDensityAsync](#SetPixelDensityAsync) (density :  [number](/docs/nl-nl/luau/numbers) ) : ()

 |
|

[SetResolutionAsync](#SetResolutionAsync) (width :  [number](/docs/nl-nl/luau/numbers) , height :  [number](/docs/nl-nl/luau/numbers) ) : ()

 |
|

[SetScalingModeAsync](#SetScalingModeAsync) (mode :  [Enum.DeviceSimulatorScalingMode](/docs/nl-nl/reference/engine/enums/DeviceSimulatorScalingMode) ) : ()

 |
|

[StopSimulationAsync](#StopSimulationAsync) () : ()

 |
|

[UpdateDeviceAsync](#UpdateDeviceAsync) (deviceId :  [string](/docs/nl-nl/luau/strings) , config :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |

Evenementen

|

[ConfigurationChanged](#ConfigurationChanged) () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

CreateDeviceAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:CreateDeviceAsync (config :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[string](/docs/nl-nl/luau/strings)

Parameters

|

config :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Codevoorbeelden

Voorbeeld van een apparaat maken

```

local id = Simulator:CreateDeviceAsync({

    Name = "Mijn Aangepaste Tablet",

    Width = 2560,

    Height = 1600,

    PixelDensity = 300,

    DeviceForm = Enum.DeviceForm.Tablet,

})

```

Feedback geven

---

GetDeviceAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:GetDeviceAsync () :[string](/docs/nl-nl/luau/strings)

Teruggaves

[string](/docs/nl-nl/luau/strings)

Feedback geven

---

GetDeviceInfoAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:GetDeviceInfoAsync (deviceId :[string](/docs/nl-nl/luau/strings) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Parameters

|

deviceId :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Feedback geven

---

GetDeviceListAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:GetDeviceListAsync () :[{any}](/docs/nl-nl/luau/tables#arrays)

Teruggaves

[{any}](/docs/nl-nl/luau/tables#arrays)

Codevoorbeelden

Voorbeeld van apparaatlijst ophalen

```

local Simulator = game:GetService("StudioDeviceSimulatorService")

local devices = Simulator:GetDeviceListAsync()

for _, deviceId in devices do

    print(deviceId)

end

```

Feedback geven

---

GetOrientationAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:GetOrientationAsync () :[Enum.ScreenOrientation](/docs/nl-nl/reference/engine/enums/ScreenOrientation)

Teruggaves

[Enum.ScreenOrientation](/docs/nl-nl/reference/engine/enums/ScreenOrientation)

Feedback geven

---

GetPixelDensityAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:GetPixelDensityAsync () :[number](/docs/nl-nl/luau/numbers)

Teruggaves

[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

GetResolutionAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:GetResolutionAsync () :[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Teruggaves

[Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)

Feedback geven

---

GetScalingModeAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:GetScalingModeAsync () :[Enum.DeviceSimulatorScalingMode](/docs/nl-nl/reference/engine/enums/DeviceSimulatorScalingMode)

Teruggaves

[Enum.DeviceSimulatorScalingMode](/docs/nl-nl/reference/engine/enums/DeviceSimulatorScalingMode)

Feedback geven

---

RemoveDeviceAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:RemoveDeviceAsync (deviceId :[string](/docs/nl-nl/luau/strings) ) : ()

Parameters

|

deviceId :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Feedback geven

---

SetDeviceAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:SetDeviceAsync (deviceId :[string](/docs/nl-nl/luau/strings) ) : ()

Parameters

|

deviceId :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Feedback geven

---

SetOrientationAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:SetOrientationAsync (orientation :[Enum.ScreenOrientation](/docs/nl-nl/reference/engine/enums/ScreenOrientation) ) : ()

Parameters

|

orientation :[Enum.ScreenOrientation](/docs/nl-nl/reference/engine/enums/ScreenOrientation)

 |

Teruggaves

()

Feedback geven

---

SetPixelDensityAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:SetPixelDensityAsync (density :[number](/docs/nl-nl/luau/numbers) ) : ()

Parameters

|

density :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

()

Feedback geven

---

SetResolutionAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:SetResolutionAsync (

width :[number](/docs/nl-nl/luau/numbers) , height :[number](/docs/nl-nl/luau/numbers)

) : ()

Parameters

|

width :[number](/docs/nl-nl/luau/numbers)

 |
|

height :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

()

Feedback geven

---

SetScalingModeAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:SetScalingModeAsync (mode :[Enum.DeviceSimulatorScalingMode](/docs/nl-nl/reference/engine/enums/DeviceSimulatorScalingMode) ) : ()

Parameters

|

mode :[Enum.DeviceSimulatorScalingMode](/docs/nl-nl/reference/engine/enums/DeviceSimulatorScalingMode)

 |

Teruggaves

()

Feedback geven

---

StopSimulationAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:StopSimulationAsync () : ()

Teruggaves

()

Feedback geven

---

UpdateDeviceAsync

Opbrengst

Plugin-beveiliging

StudioDeviceSimulatorService:UpdateDeviceAsync (

deviceId :[string](/docs/nl-nl/luau/strings) , config :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : ()

Parameters

|

deviceId :[string](/docs/nl-nl/luau/strings)

 |
|

config :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

()

Codevoorbeelden

Voorbeeld van Update Device

```

Simulator:UpdateDeviceAsync(id, {

    Name = "Mijn Aangepaste Tablet",

    Width = 2732,

    Height = 2048,

    PixelDensity = 264,

    DeviceForm = Enum.DeviceForm.Tablet,

})

```

Feedback geven

---

Evenementen

ConfigurationChanged

Plugin-beveiliging

StudioDeviceSimulatorService.ConfigurationChanged () :[RBXScriptSignal](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal)

Codevoorbeelden

Voorbeeld van gewijzigde configuratie

```

Simulator.ConfigurationChanged:Connect(function()

    local deviceId = Simulator:GetDeviceAsync()

    if deviceId ~= "default" then

        local res = Simulator:GetResolutionAsync()

        print(string.format("Actief: %s @ %dx%d", deviceId, res.X, res.Y))

    end

end)

```

Feedback geven

---

Ga naar

▼

StudioDeviceSimulatorService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Evenementen](#summary-events)

[Methoden](#methods)

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

[Evenementen](#events)

[ConfigurationChanged](#ConfigurationChanged)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
