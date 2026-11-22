<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/UserSettings -->

UserSettings | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [ServiceProvider](/docs/nl-nl/reference/engine/classes/ServiceProvider)
8. /
9. [GenericSettings](/docs/nl-nl/reference/engine/classes/GenericSettings)
10. /
11. [UserSettings](/docs/nl-nl/reference/engine/classes/UserSettings)

Nederlands

Feedback

Engine-klasse

UserSettings

Niet maakbaar

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/UserSettings)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[IsUserFeatureEnabled](#IsUserFeatureEnabled) (name :  [string](/docs/nl-nl/luau/strings) ) :[boolean](/docs/nl-nl/luau/booleans)

 |
| --- | --- |
|

[Reset](#Reset) () : ()

 |

Overgenomen leden

7  overgenomen van [ServiceProvider](/docs/nl-nl/reference/engine/classes/ServiceProvider)

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

Codevoorbeelden

IsUserFeatureEnabled Voorbeeld

```

if UserSettings():IsUserFeatureEnabled("UserNoCameraClickToMove") then

	print("'ClickToMove' zou niet langer geladen moeten worden vanuit de CameraScript!")

else

	print("'ClickToMove' wordt nog steeds geladen vanuit de CameraScript!")

end

```

Detectie van Volledig Schermmodus

```

local gameSettings = UserSettings().GameSettings

local function checkFullScreenMode()

	local inFullscreen = gameSettings:InFullScreen()

	if inFullscreen then

		print("Volledig schermmodus ingeschakeld!")

	else

		print("Volledig schermmodus uitgeschakeld!")

	end

end

checkFullScreenMode()

gameSettings.FullscreenChanged:Connect(checkFullScreenMode)

```

Luisteraar voor Gebruikersspelinstellingen

```

local gameSettings = UserSettings().GameSettings

local function onGameSettingChanged(nameOfSetting)

	-- Haal de waarde van deze instelling op via een pcall om ervoor te zorgen dat we het kunnen ophalen.

	-- Soms wordt het evenement geactiveerd met eigenschappen die LocalScripts niet kunnen benaderen.

	local canGetSetting, setting = pcall(function()

		return gameSettings[nameOfSetting]

	end)

	if canGetSetting then

		print("Je " .. nameOfSetting .. " is veranderd naar: " .. tostring(setting))

	end

end

gameSettings.Changed:Connect(onGameSettingChanged)

```

---

API-referentie

Methoden

IsUserFeatureEnabled

Mogelijkheden: Players

UserSettings:IsUserFeatureEnabled (name :[string](/docs/nl-nl/luau/strings) ) :[boolean](/docs/nl-nl/luau/booleans)

Parameters

|

name :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[boolean](/docs/nl-nl/luau/booleans)

Codevoorbeelden

IsUserFeatureEnabled Voorbeeld

```

if UserSettings():IsUserFeatureEnabled("UserNoCameraClickToMove") then

	print("'ClickToMove' zou niet langer geladen moeten worden vanuit de CameraScript!")

else

	print("'ClickToMove' wordt nog steeds geladen vanuit de CameraScript!")

end

```

Feedback geven

---

Reset

Mogelijkheden: Players

UserSettings:Reset () : ()

Teruggaves

()

Feedback geven

---

Ga naar

▼

UserSettings

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[IsUserFeatureEnabled()](#IsUserFeatureEnabled)

[Reset()](#Reset)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
