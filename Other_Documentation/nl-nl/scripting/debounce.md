<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/debounce -->

Debounce patronen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Meer informatie](/docs/nl-nl/learn)

# Debounce patronen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een debounce  patroon is een programmeertechniek die voorkomt dat een functie te vaak wordt uitgevoerd of dat een invoer meerdere keren wordt geactiveerd. De volgende scriptscenario's illustreren debounce als een beste praktijk.

## [Detecteer botsingen](#detecteer-botsingen)[](#detecteer-botsingen)

Stel dat je een gevaarlijk valstrikonderdeel wilt maken dat 10 schade toebrengt bij aanraking. Een initiële implementatie zou een basis [BasePart.Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  verbinding en een damagePlayer  functie kunnen gebruiken zoals deze:

Script - Schade Speler

```

local part = script.Parent

local function damagePlayer(otherPart)

	print(part.Name .. " botste tegen " .. otherPart.Name)

	local humanoid = otherPart.Parent:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.Health -= 10  -- Verminder de gezondheid van de speler

	end

end

part.Touched:Connect(damagePlayer)

```

Hoewel logisch op het eerste gezicht, zal testen aantonen dat de [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  gebeurtenis meerdere keren snel achter elkaar wordt geactiveerd op basis van subtiele fysieke botsingen.

 ![](https://prod.docsiteassets.roblox.com/assets/scripting/scripts/Touched-Event-No-Debounce.png)

Om te voorkomen dat er overmatige schade wordt toegebracht bij de eerste aanraking, kun je een debounce-systeem toevoegen dat een cooldown-periode afdwingt op schade via een [instantie-attribuut](/docs/nl-nl/studio/properties#instantie-attributen) .

Script - Schade Speler Met Debounce

```

local part = script.Parent

local RESET_TIME = 1

local function damagePlayer(otherPart)

	print(part.Name .. " botste tegen " .. otherPart.Name)

	local humanoid = otherPart.Parent:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		if not part:GetAttribute("Touched") then

			part:SetAttribute("Touched", true)  -- Zet attribuut op true

			humanoid.Health -= 10  -- Verminder de gezondheid van de speler

			task.wait(RESET_TIME)  -- Wacht op resetduur

			part:SetAttribute("Touched", false)  -- Reset attribuut

		end

	end

end

part.Touched:Connect(damagePlayer)

```

## [Trigger geluiden](#trigger-geluiden)[](#trigger-geluiden)

Debounce is ook nuttig bij het werken met geluidseffecten, zoals het afspelen van een geluid wanneer twee onderdelen botsen ([Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched) ), of het afspelen van een geluid bij de [Activated](/docs/nl-nl/reference/engine/classes/GuiButton#Activated)  gebeurtenis wanneer een gebruiker interactie heeft met een knop op het scherm. In beide gevallen start het aanroepen van [Sound:Play()](/docs/nl-nl/reference/engine/classes/Sound#Play)  de afspeeltijd vanaf het begin van zijn track en — zonder een debounce-systeem — kan het geluid meerdere keren snel achter elkaar worden afgespeeld.

Om geluidsoverlap te voorkomen, kun je debounce gebruiken met de [IsPlaying](/docs/nl-nl/reference/engine/classes/Sound#IsPlaying)  eigenschap van het [Sound](/docs/nl-nl/reference/engine/classes/Sound)  object:

Script - Speel Botsing Geluid Met Debounce

```

local projectile = script.Parent

local function playSound()

	-- Vind het kindgeluid op het onderdeel

	local sound = projectile:FindFirstChild("Impact")

	-- Speel het geluid alleen als het nog niet speelt

	if sound and not sound.IsPlaying then

		sound:Play()

	end

end

projectile.Touched:Connect(playSound)

```

Script - Speel Knop Klik Geluid Met Debounce

```

local button = script.Parent

local function onButtonActivated()

	-- Vind het kindgeluid op de knop

	local sound = button:FindFirstChild("Click")

	-- Speel het geluid alleen als het nog niet speelt

	if sound and not sound.IsPlaying then

		sound:Play()

	end

end

button.Activated:Connect(onButtonActivated)

```

## [Pickup-effecten](#pickup-effecten)[](#pickup-effecten)

Spellen bevatten vaak verzamelbare pickups in de 3D-wereld, zoals medkits, munitiepakketten en meer. Als je deze pickups ontwerpt om in de wereld te blijven zodat spelers ze keer op keer kunnen oppakken, moet er een "cooldown"-tijd worden toegevoegd voordat de pickup ververst en opnieuw activeert.

Vergelijkbaar met [het detecteren van botsingen](#detecteer-botsingen) , kun je de debounce-status beheren met een [instantie-attribuut](/docs/nl-nl/studio/properties#instantie-attributen) , en de cooldown-periode visualiseren door de [Transparency](/docs/nl-nl/reference/engine/classes/BasePart#Transparency)  van het onderdeel te veranderen.

Script - Gezondheids Pickup Met Debounce

```

local part = script.Parent

part.Anchored = true

part.CanCollide = false

local COOLDOWN_TIME = 5

local function healPlayer(otherPart)

	local humanoid = otherPart.Parent:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		if not part:GetAttribute("CoolingDown") then

			part:SetAttribute("CoolingDown", true)  -- Zet attribuut op true

			humanoid.Health += 25  -- Verhoog de gezondheid van de speler

			part.Transparency = 0.75  -- Maak onderdeel semi-transparant om cooldown-status aan te geven

			task.wait(COOLDOWN_TIME)  -- Wacht op cooldown-duur

			part.Transparency = 0  -- Reset onderdeel naar volledig ondoorzichtig

			part:SetAttribute("CoolingDown", false)  -- Reset attribuut

		end

	end

end

part.Touched:Connect(healPlayer)

```

Dit cooldown-concept kan ook op andere scenario's worden toegepast, zoals het creëren van een "herlaadtijd" voor een raketwerper om te beperken hoe vaak spelers raketten kunnen afvuren.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
