<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/StudioTestService -->

StudioTestService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [StudioTestService](/docs/nl-nl/reference/engine/classes/StudioTestService)

Nederlands

Feedback

Engine-klasse

StudioTestService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/StudioTestService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Eigenschappen

|

[EditModeActive](#EditModeActive) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |

Methoden

|

[AddPlayers](#AddPlayers) (numPlayers :  [number](/docs/nl-nl/luau/numbers) ) : ()

 |
|

[CanLeaveTest](#CanLeaveTest) () :[boolean](/docs/nl-nl/luau/booleans)

 |
|

[EndTest](#EndTest) (value :  Variant ) : ()

 |
|

[ExecuteMultiplayerTestAsync](#ExecuteMultiplayerTestAsync) (numPlayers :  [number](/docs/nl-nl/luau/numbers) , args :  Variant ) : Variant

 |
|

[ExecutePlayModeAsync](#ExecutePlayModeAsync) (args :  Variant ) : Variant

 |
|

[ExecuteRunModeAsync](#ExecuteRunModeAsync) (args :  Variant ) : Variant

 |
|

[GetTestArgs](#GetTestArgs) () : Variant

 |
|

[LeaveTest](#LeaveTest) () : ()

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Eigenschappen

EditModeActive

Plugin-beveiliging

Parallel lezen

StudioTestService.EditModeActive :[boolean](/docs/nl-nl/luau/booleans)

Feedback geven

---

Methoden

AddPlayers

StudioTestService:AddPlayers (numPlayers :[number](/docs/nl-nl/luau/numbers) ) : ()

Parameters

|

numPlayers :[number](/docs/nl-nl/luau/numbers)

 |

Teruggaves

()

Codevoorbeelden

Voorbeeld van Spelers Toevoegen

```

local StudioTestService = game:GetService("StudioTestService")

task.wait(5)

StudioTestService:AddPlayers(3)

```

Feedback geven

---

CanLeaveTest

StudioTestService:CanLeaveTest () :[boolean](/docs/nl-nl/luau/booleans)

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

Kan Test verlaten voorbeeld

```

local StudioTestService = game:GetService("StudioTestService")

if StudioTestService:CanLeaveTest() then

    StudioTestService:LeaveTest()

end

```

Feedback geven

---

EndTest

StudioTestService:EndTest (value : Variant ) : ()

Parameters

|

value : Variant

 |

Teruggaves

()

Codevoorbeelden

Eind Test voorbeeld

```

local StudioTestService = game:GetService("StudioTestService")

-- Server-side logica draait hier, wacht op spelers, voert assertions uit, enz.

StudioTestService:EndTest("Succes!")

```

Feedback geven

---

ExecuteMultiplayerTestAsync

Opbrengst

Plugin-beveiliging

StudioTestService:ExecuteMultiplayerTestAsync (

numPlayers :[number](/docs/nl-nl/luau/numbers) , args : Variant

) : Variant

Parameters

|

numPlayers :[number](/docs/nl-nl/luau/numbers)

 |
|

args : Variant

 |

Teruggaves

Variant

Codevoorbeelden

Voer Multiplayer Test voorbeeld uit

```

local StudioTestService = game:GetService("StudioTestService")

local result = StudioTestService:ExecuteMultiplayerTestAsync(4, "LobbySpawnTest")

assert(result == "Succes!")

print("Test voltooid:", result)

```

Feedback geven

---

ExecutePlayModeAsync

Opbrengst

Plugin-beveiliging

StudioTestService:ExecutePlayModeAsync (args : Variant ) : Variant

Parameters

|

args : Variant

 |

Teruggaves

Variant

Feedback geven

---

ExecuteRunModeAsync

Opbrengst

Plugin-beveiliging

StudioTestService:ExecuteRunModeAsync (args : Variant ) : Variant

Parameters

|

args : Variant

 |

Teruggaves

Variant

Feedback geven

---

GetTestArgs

StudioTestService:GetTestArgs () : Variant

Teruggaves

Variant

Codevoorbeelden

Voorbeeld van Get Test Args

```

local StudioTestService = game:GetService("StudioTestService")

local args = StudioTestService:GetTestArgs()

print("Ontvangen argumenten:", args)

```

Feedback geven

---

LeaveTest

StudioTestService:LeaveTest () : ()

Teruggaves

()

Feedback geven

---

Ga naar

▼

StudioTestService

[Samenvatting](#summary)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Eigenschappen](#properties)

[EditModeActive](#EditModeActive)

[Methoden](#methods)

[AddPlayers()](#AddPlayers)

[CanLeaveTest()](#CanLeaveTest)

[EndTest()](#EndTest)

[ExecuteMultiplayerTestAsync()](#ExecuteMultiplayerTestAsync)

[ExecutePlayModeAsync()](#ExecutePlayModeAsync)

[ExecuteRunModeAsync()](#ExecuteRunModeAsync)

[GetTestArgs()](#GetTestArgs)

[LeaveTest()](#LeaveTest)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
