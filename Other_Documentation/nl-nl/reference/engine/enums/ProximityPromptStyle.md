<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/enums/ProximityPromptStyle -->

ProximityPromptStyle | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Enums](/docs/nl-nl/reference/engine/enums)
2. /
3. [ProximityPromptStyle](/docs/nl-nl/reference/engine/enums/ProximityPromptStyle)

Nederlands

Feedback

Engine-enum

ProximityPromptStyle

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/enums/ProximityPromptStyle)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Items

| Naam | | Waarde | | Samenvatting |
| --- | --- |
| Default | | 0 | |  |
| Custom | | 1 | |  |

---

## Verbruik

#### Codevoorbeelden

Een Aangepaste Proximity Prompt Genereren

```

local UserInputService = game:GetService("UserInputService")

local ProximityPromptService = game:GetService("ProximityPromptService")

local TweenService = game:GetService("TweenService")

local RunService = game:GetService("RunService")

local Players = game:GetService("Players")

local LocalPlayer = Players.LocalPlayer

while LocalPlayer == nil do

	Players.ChildAdded:wait()

	LocalPlayer = Players.LocalPlayer

end

local PlayerGui = LocalPlayer:WaitForChild("PlayerGui")

local KeyboardButtonImage = {

	[Enum.KeyCode.Backspace] = "rbxasset://textures/ui/Controls/backspace.png",

	[Enum.KeyCode.Return] = "rbxasset://textures/ui/Controls/return.png",

	[Enum.KeyCode.LeftShift] = "rbxasset://textures/ui/Controls/shift.png",

	[Enum.KeyCode.RightShift] = "rbxasset://textures/ui/Controls/shift.png",

	[Enum.KeyCode.Tab] = "rbxasset://textures/ui/Controls/tab.png",

}

local KeyboardButtonIconMapping = {

	["'"] = "rbxasset://textures/ui/Controls/apostrophe.png",

	[","] = "rbxasset://textures/ui/Controls/comma.png",

	["`"] = "rbxasset://textures/ui/Controls/graveaccent.png",

	["."] = "rbxasset://textures/ui/Controls/period.png",

	[" "] = "rbxasset://textures/ui/Controls/spacebar.png",

}

local KeyCodeToTextMapping = {

	[Enum.KeyCode.LeftControl] = "Ctrl",

	[Enum.KeyCode.RightControl] = "Ctrl",

	[Enum.KeyCode.LeftAlt] = "Alt",

	[Enum.KeyCode.RightAlt] = "Alt",

	[Enum.KeyCode.F1] = "F1",

	[Enum.KeyCode.F2] = "F2",

	[Enum.KeyCode.F3] = "F3",

	[Enum.KeyCode.F4] = "F4",

	[Enum.KeyCode.F5] = "F5",

	[Enum.KeyCode.F6] = "F6",

	[Enum.KeyCode.F7] = "F7",

	[Enum.KeyCode.F8] = "F8",

	[Enum.KeyCode.F9] = "F9",

	[Enum.KeyCode.F10] = "F10",

	[Enum.KeyCode.F11] = "F11",

	[Enum.KeyCode.F12] = "F12",

}

KeyCodeToTextMapping[Enum.KeyCode.PageUp] = "PgUp"

KeyCodeToTextMapping[Enum.KeyCode.PageDown] = "PgDn"

KeyCodeToTextMapping[Enum.KeyCode.Home] = "Home"

KeyCodeToTextMapping[Enum.KeyCode.End] = "End"

KeyCodeToTextMapping[Enum.KeyCode.Insert] = "Ins"

KeyCodeToTextMapping[Enum.KeyCode.Delete] = "Del"

local KeyCodeToFontSize = {

	[Enum.KeyCode.LeftControl] = 12,

	[Enum.KeyCode.RightControl] = 12,

	[Enum.KeyCode.LeftAlt] = 12,

	[Enum.KeyCode.RightAlt] = 12,

	[Enum.KeyCode.F10] = 12,

	[Enum.KeyCode.F11] = 12,

	[Enum.KeyCode.F12] = 12,

	[Enum.KeyCode.PageUp] = 8,

	[Enum.KeyCode.PageDown] = 8,

	[Enum.KeyCode.Home] = 8,

	[Enum.KeyCode.End] = 10,

	[Enum.KeyCode.Insert] = 10,

	[Enum.KeyCode.Delete] = 10,

}

-- Kleuren

local BackgroundColor = Color3.new(0.07, 0.07, 0.07)

local ContentColor = Color3.new(1, 1, 1)

local SecondaryContentColor = Color3.new(0.7, 0.7, 0.7)

-- TweenInfo presets

local tweenInfoQuick = TweenInfo.new(0.06, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)

local tweenInfoOutHalfSecond = TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)

local tweenInfoFast = TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)

local function getScreenGui()

	local screenGui = PlayerGui:FindFirstChild("ProximityPrompts")

	if screenGui == nil then

		screenGui = Instance.new("ScreenGui")

		screenGui.Name = "ProximityPrompts"

		screenGui.ResetOnSpawn = false

		screenGui.Parent = PlayerGui

		screenGui.IgnoreGuiInset = true

	end

	return screenGui

end

local progressGradientFuzz = 0.01

local function createProgressBarGradient(parent, leftSide, tweensForFadeOut, tweensForFadeIn)

	local frame = Instance.new("Frame")

	frame.Size = UDim2.fromScale(0.5, 1)

	frame.Position = UDim2.fromScale(leftSide and 0 or 0.5, 0)

	frame.BackgroundTransparency = 1

	frame.ClipsDescendants = true

	frame.Visible = false

	frame.Parent = parent

	local image = Instance.new("ImageLabel")

	image.BackgroundTransparency = 1

	image.Size = UDim2.fromScale(2, 1)

	image.Position = UDim2.fromScale(leftSide and 0 or -1, 0)

	image.Image = "rbxasset://textures/ui/Controls/RadialFill.png"

	image.Parent = frame

	local gradient = Instance.new("UIGradient")

	gradient.Transparency = NumberSequence.new {

		NumberSequenceKeypoint.new(0, 0),

		NumberSequenceKeypoint.new(0.5, 0),

		NumberSequenceKeypoint.new(0.5 + progressGradientFuzz, 1),

		NumberSequenceKeypoint.new(1, 1)

	}

	gradient.Rotation = leftSide and 180 or 0

	gradient.Parent = image

	table.insert(tweensForFadeOut, TweenService:Create(image, tweenInfoQuick, { ImageTransparency = 1 }))

	table.insert(tweensForFadeIn, TweenService:Create(image, tweenInfoQuick, { ImageTransparency = 0 }))

	return gradient, frame

end

local function createCircularProgressBar(tweensForFadeOut, tweensForFadeIn)

	local bar = Instance.new("Frame")

	bar.Name = "CircularProgressBar"

	bar.Size = UDim2.fromOffset(58, 58)

	bar.AnchorPoint = Vector2.new(0.5, 0.5)

	bar.Position = UDim2.fromScale(0.5, 0.5)

	bar.BackgroundTransparency = 1

	local leftGradient, leftFrame = createProgressBarGradient(bar, true, tweensForFadeOut, tweensForFadeIn)

	local rightGradient, rightFrame = createProgressBarGradient(bar, false, tweensForFadeOut, tweensForFadeIn)

	local progress = Instance.new("NumberValue")

	progress.Name = "Progress"

	progress.Parent = bar

	progress.Changed:Connect(function(value)

		local angle = math.clamp(value * 360, 0, 360)

		leftFrame.Visible = progress.Value > 0.5

		leftGradient.Rotation = math.clamp(angle, 180, 360)

		rightFrame.Visible = progress.Value > progressGradientFuzz

		rightGradient.Rotation = math.clamp(angle, 0, 180)

	end)

	return bar

end

local function createPrompt(prompt, inputType, gui)

	local tweensForButtonHoldBegin = {}

	local tweensForButtonHoldEnd = {}

	local tweensForFadeOut = {}

	local tweensForFadeIn = {}

	local tweenInfoInFullDuration = TweenInfo.new(prompt.HoldDuration, Enum.EasingStyle.Linear, Enum.EasingDirection.Out)

	local promptUI = Instance.new("BillboardGui")

	promptUI.Name = "Prompt"

	promptUI.AlwaysOnTop = true

	local frame = Instance.new("Frame")

	frame.Size = UDim2.fromScale(0.5, 1)

	frame.BackgroundTransparency = 1

	frame.BackgroundColor3 = BackgroundColor

	frame.AnchorPoint = Vector2.new(0.5, 0)

	frame.Position = UDim2.fromScale(0.5, 0)

	frame.Size = UDim2.fromScale(0, 1)

	frame.AutomaticSize = Enum.AutomaticSize.X

	frame.Parent = promptUI

	-- Voeg rechter padding toe

	local padding = Instance.new("UIPadding")

	padding.Parent = frame

	local roundedCorner = Instance.new("UICorner")

	roundedCorner.Parent = frame

	local inputFrame = Instance.new("Frame")

	inputFrame.Name = "InputFrame"

	inputFrame.Size = UDim2.fromScale(1, 1)

	inputFrame.BackgroundTransparency = 1

	inputFrame.SizeConstraint = Enum.SizeConstraint.RelativeYY

	inputFrame.Parent = frame

	local resizeableInputFrame = Instance.new("Frame")

	resizeableInputFrame.Size = UDim2.fromScale(1, 1)

	resizeableInputFrame.Position = UDim2.fromScale(0.5, 0.5)

	resizeableInputFrame.AnchorPoint = Vector2.new(0.5, 0.5)

	resizeableInputFrame.BackgroundTransparency = 1

	resizeableInputFrame.Parent = inputFrame

	local inputFrameScaler = Instance.new("UIScale")

	inputFrameScaler.Parent = resizeableInputFrame

	local inputFrameScaleFactor = inputType == Enum.ProximityPromptInputType.Touch and 1.6 or 1.33

	table.insert(tweensForButtonHoldBegin, TweenService:Create(inputFrameScaler, tweenInfoFast, { Scale = inputFrameScaleFactor }))

	table.insert(tweensForButtonHoldEnd, TweenService:Create(inputFrameScaler, tweenInfoFast, { Scale = 1 }))

	local actionText = Instance.new("TextLabel")

	actionText.Name = "ActionText"

	actionText.Font = Enum.Font.GothamMedium

	actionText.TextSize = 19

	actionText.BackgroundTransparency = 1

	actionText.TextTransparency = 1

	actionText.TextColor3 = ContentColor

	actionText.TextXAlignment = Enum.TextXAlignment.Left

	table.insert(tweensForButtonHoldBegin, TweenService:Create(actionText, tweenInfoFast, { TextTransparency = 1 }))

	table.insert(tweensForButtonHoldEnd, TweenService:Create(actionText, tweenInfoFast, { TextTransparency = 0 }))

	table.insert(tweensForFadeOut, TweenService:Create(actionText, tweenInfoFast, { TextTransparency = 1 }))

	table.insert(tweensForFadeIn, TweenService:Create(actionText, tweenInfoFast, { TextTransparency = 0 }))

	local objectText = Instance.new("TextLabel")

	objectText.Name = "ObjectText"

	objectText.Font = Enum.Font.GothamMedium

	objectText.TextSize = 14

	objectText.BackgroundTransparency = 1

	objectText.TextTransparency = 1

	objectText.TextColor3 = SecondaryContentColor

	objectText.TextXAlignment = Enum.TextXAlignment.Left

	-- Voeg lijstlay-out toe, evenals een tween-out om de oude krimp na te bootsen

	local listLayout = Instance.new("UIListLayout")

	listLayout.FillDirection = Enum.FillDirection.Horizontal

	listLayout.Padding = UDim.new(-0.25, 0)

	listLayout.Parent = frame

	table.insert(tweensForButtonHoldBegin, TweenService:Create(listLayout, tweenInfoFast, { Padding = UDim.new(-0.25, 0) }))

	table.insert(tweensForButtonHoldEnd, TweenService:Create(listLayout, tweenInfoFast, { Padding = UDim.new(0, 0) }))

	table.insert(tweensForFadeOut, TweenService:Create(listLayout, tweenInfoFast, { Padding = UDim.new(-0.25, 0) }))

	table.insert(tweensForFadeIn, TweenService:Create(listLayout, tweenInfoFast, { Padding = UDim.new(0, 0) }))

	-- Voeg container toe voor tekstlabels

	local textFrame = Instance.new("Frame")

	textFrame.Name = "TextFrame"

	textFrame.Size = UDim2.fromScale(0, 1)

	textFrame.AutomaticSize = Enum.AutomaticSize.X

	textFrame.BackgroundTransparency = 1

	textFrame.Parent = frame

	-- ActionText en ObjectText automatische sizing, parent naar textFrame

	actionText.Size = UDim2.fromScale(0, 1)

	actionText.AutomaticSize = Enum.AutomaticSize.X

	actionText.Parent = textFrame

	objectText.Size = UDim2.fromScale(0, 1)

	objectText.AutomaticSize = Enum.AutomaticSize.X

	objectText.Parent = textFrame

	table.insert(tweensForButtonHoldBegin, TweenService:Create(objectText, tweenInfoFast, { TextTransparency = 1 }))

	table.insert(tweensForButtonHoldEnd, TweenService:Create(objectText, tweenInfoFast, { TextTransparency = 0 }))

	table.insert(tweensForFadeOut, TweenService:Create(objectText, tweenInfoFast, { TextTransparency = 1 }))

	table.insert(tweensForFadeIn, TweenService:Create(objectText, tweenInfoFast, { TextTransparency = 0 }))

	table.insert(tweensForButtonHoldBegin, TweenService:Create(frame, tweenInfoFast, { BackgroundTransparency = 1 }))

	table.insert(tweensForButtonHoldEnd, TweenService:Create(frame, tweenInfoFast, { BackgroundTransparency = 0.2 }))

	table.insert(tweensForFadeOut, TweenService:Create(frame, tweenInfoFast, { BackgroundTransparency = 1 }))

	table.insert(tweensForFadeIn, TweenService:Create(frame, tweenInfoFast, { BackgroundTransparency = 0.2 }))

	local roundFrame = Instance.new("Frame")

	roundFrame.Name = "RoundFrame"

	roundFrame.Size = UDim2.fromOffset(48, 48)

	roundFrame.AnchorPoint = Vector2.new(0.5, 0.5)

	roundFrame.Position = UDim2.fromScale(0.5, 0.5)

	roundFrame.BackgroundTransparency = 1

	roundFrame.Parent = resizeableInputFrame

	local roundedFrameCorner = Instance.new("UICorner")

	roundedFrameCorner.CornerRadius = UDim.new(0.5, 0)

	roundedFrameCorner.Parent = roundFrame

	table.insert(tweensForFadeOut, TweenService:Create(roundFrame, tweenInfoQuick, { BackgroundTransparency = 1 }))

	table.insert(tweensForFadeIn, TweenService:Create(roundFrame, tweenInfoQuick, { BackgroundTransparency = 0.5 }))

	if inputType == Enum.ProximityPromptInputType.Gamepad then

		local mappedIconImage = UserInputService:GetImageForKeyCode(prompt.GamepadKeyCode)

		if mappedIconImage then

			local icon = Instance.new("ImageLabel")

			icon.Name = "ButtonImage"

			icon.AnchorPoint = Vector2.new(0.5, 0.5)

			icon.Size = UDim2.fromOffset(24, 24)

			icon.Position = UDim2.fromScale(0.5, 0.5)

			icon.BackgroundTransparency = 1

			icon.ImageTransparency = 1

			icon.Image = mappedIconImage

			icon.Parent = resizeableInputFrame

			table.insert(tweensForFadeOut, TweenService:Create(icon, tweenInfoQuick, { ImageTransparency = 1 }))

			table.insert(tweensForFadeIn, TweenService:Create(icon, tweenInfoQuick, { ImageTransparency = 0 }))

		end

	elseif inputType == Enum.ProximityPromptInputType.Touch then

		local buttonImage = Instance.new("ImageLabel")

		buttonImage.Name = "ButtonImage"

		buttonImage.BackgroundTransparency = 1

		buttonImage.ImageTransparency = 1

		buttonImage.Size = UDim2.fromOffset(25, 31)

		buttonImage.AnchorPoint = Vector2.new(0.5, 0.5)

		buttonImage.Position = UDim2.fromScale(0.5, 0.5)

		buttonImage.Image = "rbxasset://textures/ui/Controls/TouchTapIcon.png"

		buttonImage.Parent = resizeableInputFrame

		table.insert(tweensForFadeOut, TweenService:Create(buttonImage, tweenInfoQuick, { ImageTransparency = 1 }))

		table.insert(tweensForFadeIn, TweenService:Create(buttonImage, tweenInfoQuick, { ImageTransparency = 0 }))

	else

		local buttonImage = Instance.new("ImageLabel")

		buttonImage.Name = "ButtonImage"

		buttonImage.BackgroundTransparency = 1

		buttonImage.ImageTransparency = 1

		buttonImage.Size = UDim2.fromOffset(28, 30)

		buttonImage.AnchorPoint = Vector2.new(0.5, 0.5)

		buttonImage.Position = UDim2.fromScale(0.5, 0.5)

		buttonImage.Image = "rbxasset://textures/ui/Controls/key_single.png"

		buttonImage.Parent = resizeableInputFrame

		table.insert(tweensForFadeOut, TweenService:Create(buttonImage, tweenInfoQuick, { ImageTransparency = 1 }))

		table.insert(tweensForFadeIn, TweenService:Create(buttonImage, tweenInfoQuick, { ImageTransparency = 0 }))

		local buttonTextString = UserInputService:GetStringForKeyCode(prompt.KeyboardKeyCode)

		local buttonTextImage = KeyboardButtonImage[prompt.KeyboardKeyCode]

		if buttonTextImage == nil then

			buttonTextImage = KeyboardButtonIconMapping[buttonTextString]

		end

		if buttonTextImage == nil then

			local keyCodeMappedText = KeyCodeToTextMapping[prompt.KeyboardKeyCode]

			if keyCodeMappedText then

				buttonTextString = keyCodeMappedText

			end

		end

		if buttonTextImage then

			local icon = Instance.new("ImageLabel")

			icon.Name = "ButtonImage"

			icon.AnchorPoint = Vector2.new(0.5, 0.5)

			icon.Size = UDim2.fromOffset(36, 36)

			icon.Position = UDim2.fromScale(0.5, 0.5)

			icon.BackgroundTransparency = 1

			icon.ImageTransparency = 1

			icon.Image = buttonTextImage

			icon.Parent = resizeableInputFrame

			table.insert(tweensForFadeOut, TweenService:Create(icon, tweenInfoQuick, { ImageTransparency = 1 }))

			table.insert(tweensForFadeIn, TweenService:Create(icon, tweenInfoQuick, { ImageTransparency = 0 }))

		elseif buttonTextString ~= nil and buttonTextString ~= '' then

			local buttonText = Instance.new("TextLabel")

			buttonText.Name = "ButtonText"

			buttonText.AutoLocalize = false

			buttonText.Position = UDim2.fromOffset(0, -1)

			buttonText.Size = UDim2.fromScale(1, 1)

			buttonText.Font = Enum.Font.GothamMedium

			local buttonTextSize = KeyCodeToFontSize[prompt.KeyboardKeyCode]

			if buttonTextSize == nil then

				buttonTextSize = 14

			end

			buttonText.TextSize = buttonTextSize

			buttonText.BackgroundTransparency = 1

			buttonText.TextTransparency = 1

			buttonText.TextColor3 = ContentColor

			buttonText.TextXAlignment = Enum.TextXAlignment.Center

			buttonText.Text = buttonTextString

			buttonText.Parent = resizeableInputFrame

			table.insert(tweensForFadeOut, TweenService:Create(buttonText, tweenInfoQuick, { TextTransparency = 1 }))

			table.insert(tweensForFadeIn, TweenService:Create(buttonText, tweenInfoQuick, { TextTransparency = 0 }))

		else

			error("ProximityPrompt '" .. prompt.Name .. "' heeft een niet-ondersteunde keycode voor het renderen van UI: " .. tostring(prompt.KeyboardKeyCode))

		end

	end

	if inputType == Enum.ProximityPromptInputType.Touch of prompt.ClickablePrompt then

		local button = Instance.new("TextButton")

		button.BackgroundTransparency = 1

		button.TextTransparency = 1

		button.Size = UDim2.fromScale(1, 1)

		button.Parent = promptUI

		button.Selectable = false

		local buttonDown = false

		button.InputBegan:Connect(function(input)

			if (input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseButton1) and

				input.UserInputState ~= Enum.UserInputState.Change then

				prompt:InputHoldBegin()

				buttonDown = true

			end

		end)

		button.InputEnded:Connect(function(input)

			if input.UserInputType == Enum.UserInputType.Touch or input.UserInputType == Enum.UserInputType.MouseButton1 then

				if buttonDown then

					buttonDown = false

					prompt:InputHoldEnd()

				end

			end

		end)

		promptUI.Active = true

	end

	if prompt.HoldDuration > 0 then

		local circleBar = createCircularProgressBar(tweensForFadeOut, tweensForFadeIn)

		circleBar.Parent = resizeableInputFrame

		table.insert(tweensForButtonHoldBegin, TweenService:Create(circleBar.Progress, tweenInfoInFullDuration, { Value = 1 }))

		table.insert(tweensForButtonHoldEnd, TweenService:Create(circleBar.Progress, tweenInfoOutHalfSecond, { Value = 0 }))

	end

	local holdBeganConnection

	local holdEndedConnection

	local triggeredConnection

	local triggerEndedConnection

	if prompt.HoldDuration > 0 then

		holdBeganConnection = prompt.PromptButtonHoldBegan:Connect(function()

			for _, tween in ipairs(tweensForButtonHoldBegin) do

				tween:Play()

			end

		end)

		holdEndedConnection = prompt.PromptButtonHoldEnded:Connect(function()

			for _, tween in ipairs(tweensForButtonHoldEnd) do

				tween:Play()

			end

		end)

	end

	triggeredConnection = prompt.Triggered:Connect(function()

		for _, tween in ipairs(tweensForFadeOut) do

			tween:Play()

		end

	end)

	triggerEndedConnection = prompt.TriggerEnded:Connect(function()

		for _, tween in ipairs(tweensForFadeIn) do

			tween:Play()

		end

	end)

	local function updateUIFromPrompt()

		local promptHeight = 72

		local promptWidth = 72

		local textPaddingRight = 24

		local actionTextYOffset = 0

		if prompt.ObjectText ~= nil and prompt.ObjectText ~= '' then

			actionTextYOffset = 9

		end

		actionText.Text = prompt.ActionText

		objectText.Text = prompt.ObjectText

		actionText.AutoLocalize = prompt.AutoLocalize

		actionText.RootLocalizationTable = prompt.RootLocalizationTable

		objectText.AutoLocalize = prompt.AutoLocalize

		objectText.RootLocalizationTable = prompt.RootLocalizationTable

		textPaddingRight = textPaddingRight - actionTextYOffset

		if

			(prompt.ActionText ~= nil and prompt.ActionText ~= '')

			or (prompt.ObjectText ~= nil and prompt.ObjectText ~= '')

		then

			padding.PaddingRight = UDim.new(0, textPaddingRight)

		else

			padding.PaddingRight = UDim.new(0, 0)

		end

		actionText.Position = UDim2.new(0, 0, 0, actionTextYOffset)

		objectText.Position = UDim2.new(0, 0, 0, -10)

		promptUI.Size = UDim2.fromOffset(promptWidth, promptHeight)

		promptUI.SizeOffset = Vector2.new(prompt.UIOffset.X / promptUI.Size.Width.Offset, prompt.UIOffset.Y / promptUI.Size.Height.Offset)

		-- BillboardGuis kunnen niet automatisch worden geschaald, dus we moeten de grootte berekenen

		-- op basis van het automatisch geschaalde prompt frame.

		task.defer(function ()

			-- Automatische sizing duurt ongeveer 2 render cycli om te worden berekend

			RunService.RenderStepped:Wait()

			RunService.RenderStepped:Wait()

			promptWidth = frame.AbsoluteSize.X

			promptUI.Size = UDim2.fromOffset(promptWidth, promptHeight)

			promptUI.SizeOffset = Vector2.new(prompt.UIOffset.X / promptUI.Size.Width.Offset, prompt.UIOffset.Y / promptUI.Size.Height.Offset)

		end)

	end

	local changedConnection = prompt.Changed:Connect(updateUIFromPrompt)

	updateUIFromPrompt()

	promptUI.Adornee = prompt.Parent

	promptUI.Parent = gui

	local function updateUIAncestry()

		promptUI.Adornee = prompt.Parent

	end

	local ancestryConnection = prompt.AncestryChanged:Connect(updateUIAncestry)

	for _, tween in ipairs(tweensForFadeIn) do

		tween:Play()

	end

	local function cleanup()

		if holdBeganConnection then

			holdBeganConnection:Disconnect()

		end

		if holdEndedConnection then

			holdEndedConnection:Disconnect()

		end

		triggeredConnection:Disconnect()

		triggerEndedConnection:Disconnect()

		changedConnection:Disconnect()

		ancestryConnection:Disconnect()

		for _, tween in ipairs(tweensForFadeOut) do

			tween:Play()

		end

		wait(0.2)

		promptUI.Parent = nil

	end

	return cleanup

end

local function createIndicator(prompt, gui)

	local tweensForFadeOut = {}

	local tweensForFadeIn = {}

	local indicatorUI = Instance.new("BillboardGui")

	indicatorUI.Name = "Indicator"

	indicatorUI.Size = UDim2.fromOffset(15, 15)

	indicatorUI.AlwaysOnTop = true

	local frame = Instance.new("Frame")

	frame.Size = UDim2.fromScale(1, 1)

	frame.BackgroundTransparency = 1

	frame.BackgroundColor3 = BackgroundColor

	frame.AnchorPoint = Vector2.new(0.5, 0)

	frame.Position = UDim2.fromScale(0.5, 0)

	frame.Parent = indicatorUI

	local corner = Instance.new("UICorner")

	corner.CornerRadius = UDim.new(1, 0)

	corner.Parent = frame

    local stroke = Instance.new("UIStroke")

	stroke.Color = ContentColor

	stroke.Thickness = 1.5

	stroke.Transparency = 1

	stroke.Parent = frame

	table.insert(tweensForFadeOut, TweenService:Create(frame, tweenInfoQuick, { BackgroundTransparency = 1 }))

	table.insert(tweensForFadeOut, TweenService:Create(stroke, tweenInfoQuick, { Transparency = 1 }))

	table.insert(tweensForFadeIn, TweenService:Create(frame, tweenInfoQuick, { BackgroundTransparency = 0.2 }))

	table.insert(tweensForFadeIn, TweenService:Create(stroke, tweenInfoQuick, { Transparency = 0.2 }))

	indicatorUI.Adornee = prompt.Parent

	indicatorUI.Parent = gui

	local function updateUIAncestry()

		indicatorUI.Adornee = prompt.Parent

	end

	local ancestryConnection = prompt.AncestryChanged:Connect(updateUIAncestry)

	for _, tween in ipairs(tweensForFadeIn) do

		tween:Play()

	end

	local function cleanup()

		ancestryConnection:Disconnect()

		for _, tween in ipairs(tweensForFadeOut) do

			tween:Play()

		end

		wait(0.2)

		indicatorUI.Parent = nil

	end

	return cleanup

end

local function onLoad()

	ProximityPromptService.PromptShown:Connect(function(prompt, inputType)

		if prompt.Style ~= Enum.ProximityPromptStyle.Custom then

			return

		end

		local gui = getScreenGui()

		local cleanupFunction = createPrompt(prompt, inputType, gui)

		-- Wacht op het verbergen of vernietigen van de prompt

		local yield = Instance.new("BindableEvent")

		local con = prompt.PromptHidden:Connect(function()

			yield:Fire()

		end)

		local con2 = prompt.Destroying:Connect(function()

			yield:Fire()

		end)

		yield.Event:Wait()

		con:Disconnect()

		con2:Disconnect()

		cleanupFunction()

    end)

	ProximityPromptService.IndicatorShown:Connect(function(prompt)

		if prompt.Style ~= Enum.ProximityPromptStyle.Custom then

			return

		end

		local gui = getScreenGui()

		local cleanupFunction = createIndicator(prompt, gui)

		-- Wacht op het verbergen van de indicator of de prompt wordt vernietigd

		local yield = Instance.new("BindableEvent")

		local con = prompt.IndicatorHidden:Connect(function()

			yield:Fire()

		end)

		local con2 = prompt.Destroying:Connect(function()

			yield:Fire()

		end)

		yield.Event:Wait()

		con:Disconnect()

		con2:Disconnect()

		cleanupFunction()

	end)

end

onLoad()

```

Ga naar

▼

ProximityPromptStyle

[Samenvatting](#summary)

[Verbruik](#usage)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
