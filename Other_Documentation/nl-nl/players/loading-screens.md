<!-- Source: https://create.roblox.com/docs/nl-nl/players/loading-screens -->

Laadschermen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelers](/docs/nl-nl/players)

# Laadschermen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox toont een standaard laadscherm wanneer gebruikers verbinding maken met een spel, maar je kunt je spel personaliseren met een aangepast laadscherm dat statische of geanimeerde inhoud bevat.

Dit artikel behandelt de laadschermen die worden weergegeven wanneer een gebruiker aanvankelijk een spel betreedt. Om laadschermen aan te passen die worden weergegeven wanneer een gebruiker tussen plaatsen teleporteert, zie [Teleport tussen plaatsen](/docs/nl-nl/projects/teleport#maak-aangepaste-teleportschermen) .

## [Implementatie](#implementatie)[](#implementatie)

Om een aangepast laadscherm weer te geven, kun je ofwel een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  instantie ontwerpen binnen een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) , of je kunt een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  object in je plaats hiërarchie refereren. Beide opties maken gebruik van [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst) , aangezien deze service instanties naar clients repliceert voordat iets anders wordt gerepliceerd. Dit zorgt ervoor dat je laadscherm het eerste is dat gebruikers zien wanneer ze je spel binnenkomen.

### [Vanuit script](#vanuit-script)[](#vanuit-script)

Om een aangepast laadscherm volledig vanuit een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  te ontwerpen en weer te geven:

1.

Maak in [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) .

2.

Plak de volgende codevoorbeeld om een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  object te maken en aan te passen. Je kunt de volgende code aanpassen met je eigen waarden om je ontwerp te creëren.

Script-Gemaakt Laadscherm

```

local Players = game:GetService("Players")

local ReplicatedFirst = game:GetService("ReplicatedFirst")

local player = Players.LocalPlayer

local playerGui = player:WaitForChild("PlayerGui")

local loadingScreen = Instance.new("ScreenGui")

loadingScreen.IgnoreGuiInset = true

loadingScreen.Parent = playerGui

-- Vervang ScreenGui-waarden door je eigen

local textLabel = Instance.new("TextLabel")

textLabel.Size = UDim2.new(1, 0, 1, 0)

textLabel.BackgroundColor3 = Color3.fromRGB(0, 20, 40)

textLabel.Font = Enum.Font.DenkOne

textLabel.TextColor3 = Color3.new(0.8, 0.8, 0.8)

textLabel.Text = "Laden"

textLabel.TextSize = 32

textLabel.Parent = loadingScreen

-- Verwijder het standaard laadscherm

ReplicatedFirst:RemoveDefaultLoadingScreen()

task.wait(5)  -- Dwing het aangepaste laadscherm om minimaal een bepaalde tijd zichtbaar te zijn

if not game:IsLoaded() then

	game.Loaded:Wait()

end

loadingScreen:Destroy()

```

### [Vanuit bestaande GUI](#vanuit-bestaande-gui)[](#vanuit-bestaande-gui)

In plaats van een laadscherm [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  volledig via een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  te maken, kun je ook een bestaande [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  in je plaats hiërarchie refereren. Zorg ervoor dat je spel de gerefereerde [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  binnen [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  bevat en dat de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  UI-elementen zoals [TextLabels](/docs/nl-nl/reference/engine/classes/TextLabel)  en [ImageLabels](/docs/nl-nl/reference/engine/classes/ImageLabel)  bevat.

Om dit proces te demonstreren, verwijst de volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  naar een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  genaamd LoadingScreen  binnen [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst) , en verwijdert vervolgens het standaard laadscherm zodat het enige laadscherm dat een speler kan zien jouw eigen aangepaste laadscherm is.

Vergeet niet dat je je laadscherm [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  binnen de [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  container kunt ontwerpen om het voorvertonen, en het vervolgens naar [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  kunt verplaatsen zodra je tevreden bent met het resultaat.

Referentie Bestaand Laadscherm

```

local Players = game:GetService("Players")

local ReplicatedFirst = game:GetService("ReplicatedFirst")

local player = Players.LocalPlayer

local playerGui = player:WaitForChild("PlayerGui")

local loadingScreen = ReplicatedFirst:FindFirstChild("LoadingScreen")

if loadingScreen then

	loadingScreen.IgnoreGuiInset = true

	loadingScreen.Parent = playerGui

	-- Verwijder het standaard laadscherm

	ReplicatedFirst:RemoveDefaultLoadingScreen()

	task.wait(5)  -- Dwing het scherm om minimaal een aantal seconden zichtbaar te zijn

	if not game:IsLoaded() then

		game.Loaded:Wait()

	end

	loadingScreen:Destroy()

end

```

## [Voeg animaties toe](#voeg-animaties-toe)[](#voeg-animaties-toe)

Naast statische aangepaste laadschermen, kun je animaties toevoegen om het laadscherm te verbeteren en de voortgang van het laden aan te geven. De eenvoudigste manier om dit te doen is door een UI-element te maken, zoals een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  of [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel) , en deze vervolgens te animeren met [TweenService](/docs/nl-nl/reference/engine/classes/TweenService) . Bijvoorbeeld, de volgende codevoorbeeld maakt een nieuwe [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  met een kind [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel) , verwijdert het standaard laadscherm, en laat vervolgens [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  de centrale elementen vervagen en draaien totdat het spel is geladen.

Script-Gemaakt Laadscherm (Geanimeerd)

```

local Players = game:GetService("Players")

local ReplicatedFirst = game:GetService("ReplicatedFirst")

local TweenService = game:GetService("TweenService")

local player = Players.LocalPlayer

local playerGui = player:WaitForChild("PlayerGui")

local loadingScreen = Instance.new("ScreenGui")

loadingScreen.IgnoreGuiInset = true

loadingScreen.Parent = playerGui

local textLabel = Instance.new("TextLabel")

textLabel.Size = UDim2.new(1, 0, 1, 0)

textLabel.BackgroundColor3 = Color3.fromRGB(0, 20, 40)

textLabel.Font = Enum.Font.DenkOne

textLabel.TextColor3 = Color3.new(0.8, 0.8, 0.8)

textLabel.Text = "Laden"

textLabel.TextSize = 32

textLabel.TextTransparency = 1

textLabel.Parent = loadingScreen

local loadingRing = Instance.new("ImageLabel")

loadingRing.Size = UDim2.new(0, 256, 0, 256)

loadingRing.BackgroundTransparency = 1

loadingRing.Image = "rbxassetid://4965945816"

loadingRing.AnchorPoint = Vector2.new(0.5, 0.5)

loadingRing.Position = UDim2.new(0.5, 0, 0.5, 0)

loadingRing.ImageTransparency = 1

loadingRing.Parent = loadingScreen

-- Verwijder het standaard laadscherm

ReplicatedFirst:RemoveDefaultLoadingScreen()

-- Start en initieer fade-in tweens

local fadeTweenInfo = TweenInfo.new(1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out, 0, false, 2)

local fadeTween1 = TweenService:Create(textLabel, fadeTweenInfo, {TextTransparency = 0})

local fadeTween2 = TweenService:Create(loadingRing, fadeTweenInfo, {ImageTransparency = 0})

fadeTween1:Play()

fadeTween2:Play()

-- Start en initieer rotatie tween

local tweenInfo = TweenInfo.new(4, Enum.EasingStyle.Linear, Enum.EasingDirection.In, -1)

local tween = TweenService:Create(loadingRing, tweenInfo, {Rotation = 360})

tween:Play()

task.wait(5)  -- Dwing het scherm om minimaal een aantal seconden zichtbaar te zijn

if not game:IsLoaded() then

	game.Loaded:Wait()

end

loadingScreen:Destroy()

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
