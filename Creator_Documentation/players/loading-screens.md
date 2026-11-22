<!-- Source: https://create.roblox.com/docs/en-us/players/loading-screens -->

Loading screens | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/players/loading-screens.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Players](/docs/en-us/players)

# Loading screens

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/players/loading-screens.md)

Roblox displays a default loading screen when users are connecting to a game, but you can personalize your game with a custom loading screen that contains static or animated content.

This article covers the loading screens that display when a user initially joins a game. To customize loading screens that display when a user teleports between places, see [Teleport between places](/docs/en-us/projects/teleport#create-custom-teleport-screens) .

## [Implementation](#implementation)[](#implementation)

To display a custom loading screen, you can either design a [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  instance directly within a [LocalScript](/docs/en-us/reference/engine/classes/LocalScript) , or you can reference a [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  object in your place hierarchy. Both options utilize [ReplicatedFirst](/docs/en-us/reference/engine/classes/ReplicatedFirst) , as this service that replicates instances to clients before anything else is replicated. This ensures that your loading screen is the first thing users see when they enter your game.

### [From script](#from-script)[](#from-script)

To design and display a custom loading screen entirely from a [LocalScript](/docs/en-us/reference/engine/classes/LocalScript) :

1.

In [ReplicatedFirst](/docs/en-us/reference/engine/classes/ReplicatedFirst) , create a [LocalScript](/docs/en-us/reference/engine/classes/LocalScript) .

2.

Paste in the following code sample to create and customize a [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  object. You can modify the following code with your own values to create your design.

Script-Created Loading Screen

```

local Players = game:GetService("Players")

local ReplicatedFirst = game:GetService("ReplicatedFirst")

local player = Players.LocalPlayer

local playerGui = player:WaitForChild("PlayerGui")

local loadingScreen = Instance.new("ScreenGui")

loadingScreen.IgnoreGuiInset = true

loadingScreen.Parent = playerGui

-- Replace ScreenGui values with your own

local textLabel = Instance.new("TextLabel")

textLabel.Size = UDim2.new(1, 0, 1, 0)

textLabel.BackgroundColor3 = Color3.fromRGB(0, 20, 40)

textLabel.Font = Enum.Font.DenkOne

textLabel.TextColor3 = Color3.new(0.8, 0.8, 0.8)

textLabel.Text = "Loading"

textLabel.TextSize = 32

textLabel.Parent = loadingScreen

-- Remove the default loading screen

ReplicatedFirst:RemoveDefaultLoadingScreen()

task.wait(5)  -- Force custom loading screen to appear for a minimum time

if not game:IsLoaded() then

	game.Loaded:Wait()

end

loadingScreen:Destroy()

```

### [From existing GUI](#from-existing-gui)[](#from-existing-gui)

Instead of creating a loading screen [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  entirely through a [LocalScript](/docs/en-us/reference/engine/classes/LocalScript) , you can also reference an existing [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  in your place hierarchy. Ensure that your game includes the referenced [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  within [ReplicatedFirst](/docs/en-us/reference/engine/classes/ReplicatedFirst)  and that the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  includes UI elements like [TextLabels](/docs/en-us/reference/engine/classes/TextLabel)  and [ImageLabels](/docs/en-us/reference/engine/classes/ImageLabel) .

To demonstrate this process, the following [LocalScript](/docs/en-us/reference/engine/classes/LocalScript)  references a [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  named LoadingScreen  within [ReplicatedFirst](/docs/en-us/reference/engine/classes/ReplicatedFirst) , then it removes the default loading screen so the only loading screen a player can see is your own custom loading screen.

Remember that you can design your loading screen [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  within the [StarterGui](/docs/en-us/reference/engine/classes/StarterGui)  container to preview it, then move it to [ReplicatedFirst](/docs/en-us/reference/engine/classes/ReplicatedFirst)  once you're satisfied with the result.

Reference Existing Loading Screen

```

local Players = game:GetService("Players")

local ReplicatedFirst = game:GetService("ReplicatedFirst")

local player = Players.LocalPlayer

local playerGui = player:WaitForChild("PlayerGui")

local loadingScreen = ReplicatedFirst:FindFirstChild("LoadingScreen")

if loadingScreen then

	loadingScreen.IgnoreGuiInset = true

	loadingScreen.Parent = playerGui

	-- Remove the default loading screen

	ReplicatedFirst:RemoveDefaultLoadingScreen()

	task.wait(5)  -- Force screen to appear for a minimum number of seconds

	if not game:IsLoaded() then

		game.Loaded:Wait()

	end

	loadingScreen:Destroy()

end

```

## [Add animations](#add-animations)[](#add-animations)

In addition to static custom loading screens, you can add animations to enhance the loading screen and indicate loading progress. The easiest way to do this is to create a UI element, such as a [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)  or [ImageLabel](/docs/en-us/reference/engine/classes/ImageLabel) , then to animate it using [TweenService](/docs/en-us/reference/engine/classes/TweenService) . For example, the following code sample creates a new [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  with a child [ImageLabel](/docs/en-us/reference/engine/classes/ImageLabel) , removes the default loading screen, then [TweenService](/docs/en-us/reference/engine/classes/TweenService)  fades in and rotates the central elements until the game loads.

Script-Created Loading Screen (Animated)

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

textLabel.Text = "Loading"

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

-- Remove the default loading screen

ReplicatedFirst:RemoveDefaultLoadingScreen()

-- Initiate and start fade-in tweens

local fadeTweenInfo = TweenInfo.new(1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out, 0, false, 2)

local fadeTween1 = TweenService:Create(textLabel, fadeTweenInfo, {TextTransparency = 0})

local fadeTween2 = TweenService:Create(loadingRing, fadeTweenInfo, {ImageTransparency = 0})

fadeTween1:Play()

fadeTween2:Play()

-- Initiate and start rotation tween

local tweenInfo = TweenInfo.new(4, Enum.EasingStyle.Linear, Enum.EasingDirection.In, -1)

local tween = TweenService:Create(loadingRing, tweenInfo, {Rotation = 360})

tween:Play()

task.wait(5)  -- Force screen to appear for a minimum number of seconds

if not game:IsLoaded() then

	game.Loaded:Wait()

end

loadingScreen:Destroy()

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
