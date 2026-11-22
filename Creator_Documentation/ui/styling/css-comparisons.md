<!-- Source: https://create.roblox.com/docs/en-us/ui/styling/css-comparisons -->

CSS Comparisons | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/styling/css-comparisons.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)
6. /
7. UI styling

# CSS Comparisons

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/styling/css-comparisons.md)

Most CSS concepts map to Roblox styling concepts. The following examples show how CSS and HTML align with Luau and Roblox classes/properties.

To test each of the following Luau script examples:

1.

In the [Explorer](/docs/en-us/studio/explorer) , create the following:

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/CSS-Test-Setup.png)

1.

[StyleSheet](/docs/en-us/reference/engine/classes/StyleSheet)  instance inside [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage) .

2.

[ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  container in [StarterGui](/docs/en-us/reference/engine/classes/StarterGui) .

3.

[LocalScript](/docs/en-us/reference/engine/classes/LocalScript)  instance inside the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui) .

4.

[StyleLink](/docs/en-us/reference/engine/classes/StyleLink)  object inside the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui) .

2.

In the [LocalScript](/docs/en-us/reference/engine/classes/LocalScript) , paste the following supporting code:

LocalScript

```

local CollectionService = game:GetService("CollectionService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = ReplicatedStorage:FindFirstChildWhichIsA("StyleSheet")

local screenGui = script.Parent

local styleLink = screenGui:FindFirstChildWhichIsA("StyleLink")

styleLink.StyleSheet = coreSheet

```

3.

For each example below, paste the Luau  code lines following the supporting lines 1–7.

## [Selectors](#selectors)[](#selectors)

The [Selector](/docs/en-us/reference/engine/classes/StyleRule#Selector)  property of a [StyleRule](/docs/en-us/reference/engine/classes/StyleRule)  specifies which instances the rule should affect. The following selector types map from CSS to Luau and can be used with combinators.

### [Element](#element)[](#element)

Equivalent to CSS element selectors are Roblox class selectors  which select all instances of a given [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  class, for example [Frame](/docs/en-us/reference/engine/classes/Frame) , [ImageLabel](/docs/en-us/reference/engine/classes/ImageLabel) , [TextButton](/docs/en-us/reference/engine/classes/TextButton) , etc.

CSS

```

button {

	background-color: #335FFF;

	color: #E1E1E1;

	width: 15%;

	height: 40px;

	border: none;

}

```

HTML

```

<button>Main Menu</button>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = "TextButton" -- Roblox class selector

rule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	Size = UDim2.new(0.15, 0, 0, 40),

	BorderSizePixel = 0

})

local button = Instance.new("TextButton")

button.Text = "Main Menu"

button.Parent = screenGui

```

### [Class](#class)[](#class)

The Roblox equivalent to CSS class  selectors are tag selectors  which utilize [tags](/docs/en-us/studio/properties#instance-tags)  applied through [CollectionService](/docs/en-us/reference/engine/classes/CollectionService) .

CSS

```

.button-primary {

	background-color: #335FFF;

	color: #E1E1E1;

}

```

HTML

```

<button class="button-primary">Main Menu</button>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = ".ButtonPrimary" -- Roblox tag selector

rule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	AutomaticSize = Enum.AutomaticSize.XY

})

local button = Instance.new("TextButton")

button.Text = "Main Menu"

button.Parent = screenGui

-- Apply tag to button

CollectionService:AddTag(button, "ButtonPrimary")

```

### [Identifier](#identifier)[](#identifier)

The closest Roblox comparison to CSS id  is the #[name]  selector which selects according to the value of [Instance.Name](/docs/en-us/reference/engine/classes/Instance#Name) . Unlike the W3C specification of the id  attribute, names are not expected to be unique.

CSS

```

#modal-frame {

	background-color: #000022;

	opacity: 0.5;

	width: 50%;

	min-height: 100px;

}

```

HTML

```

<div id="modal-frame"></div>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = "#ModalFrame" -- Instance name selector

rule:SetProperties({

	BackgroundColor3 = Color3.fromHex("000022"),

	BackgroundTransparency = 0.5,

	Size = UDim2.new(0.5, 0, 0, 100),

	AutomaticSize = Enum.AutomaticSize.Y

})

local frame = Instance.new("Frame")

frame.Parent = screenGui

-- Rename frame to match selector

frame.Name = "ModalFrame"

```

## [Combinators](#combinators)[](#combinators)

Combinators let you mix basic [selectors](#selectors)  to match deeper hierarchy relationships.

### [Child](#child)[](#child)

The child selector of >  is identical between CSS and Roblox.

CSS

```

.menu-container {

	width: 25%;

}

.menu-container > button {

	background-color: #335FFF;

	color: #E1E1E1;

	width: 80%;

	height: 40px;

	border: none;

}

```

HTML

```

<div class="menu-container">

	<button>Options</button>

</div>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = ".MenuContainer > TextButton" -- Child selector

rule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	Size = UDim2.new(0.8, 0, 0, 40),

	BorderSizePixel = 0

})

-- Create menu container

local menuContainer = Instance.new("Frame")

menuContainer.Size = UDim2.new(0.25, 0, 0, 0)

menuContainer.AutomaticSize = Enum.AutomaticSize.Y

menuContainer.Parent = screenGui

-- Apply tag

CollectionService:AddTag(menuContainer, "MenuContainer")

-- Create button

local button = Instance.new("TextButton")

button.Text = "Options"

-- Set menu container as parent of button

button.Parent = menuContainer

```

### [Descendant](#descendant)[](#descendant)

Unlike the CSS whitespace syntax, for example .menu-container button  seen here, Roblox uses the >>  combinator to indicate a descendant relationship.

CSS

```

.menu-container {

	width: 25%;

}

.sub-container {

	width: 75%;

}

.menu-container button {

	background-color: #335FFF;

	color: #E1E1E1;

	width: 80%;

	height: 40px;

	border: none;

}

```

HTML

```

<div class="menu-container">

	<div class="sub-container">

		<button>Options</button>

	</div>

</div>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = ".MenuContainer >> TextButton" -- Descendant selector

rule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	Size = UDim2.new(0.8, 0, 0, 40),

	BorderSizePixel = 0

})

-- Create menu container

local menuContainer = Instance.new("Frame")

menuContainer.Size = UDim2.new(0.25, 0, 0, 0)

menuContainer.AutomaticSize = Enum.AutomaticSize.Y

menuContainer.Parent = screenGui

-- Apply tag

CollectionService:AddTag(menuContainer, "MenuContainer")

-- Create sub-container

local subContainer = Instance.new("Frame")

subContainer.Size = UDim2.new(0.75, 0, 0, 0)

subContainer.AutomaticSize = Enum.AutomaticSize.Y

-- Set menu container as parent of sub-container

subContainer.Parent = menuContainer

-- Create button

local button = Instance.new("TextButton")

button.Text = "Options"

-- Set sub-container as parent of button

button.Parent = subContainer

```

### [Selector list](#selector-list)[](#selector-list)

Multiple selectors (including selectors with combinators) can be declared with the same property block, separated by commas, to reduce redundancy.

CSS

```

img, p {

	background-color: #FF0033;

}

```

HTML

```

<img src="gear.png" width="100" height="100">

<p>Main Menu</p>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = "ImageLabel, TextLabel" -- Selector for image labels AND text labels

rule:SetProperty("BackgroundColor3", Color3.fromHex("ff0033"))

-- Create image label

local imageLabel = Instance.new("ImageLabel")

imageLabel.Image = "rbxassetid://104919049969988"

imageLabel.Size = UDim2.new(0, 100, 0, 100)

imageLabel.Parent = screenGui

-- Create text label

local textLabel = Instance.new("TextLabel")

textLabel.Size = UDim2.new(1, 0, 0, 0)

textLabel.AutomaticSize = Enum.AutomaticSize.Y

textLabel.TextXAlignment = Enum.TextXAlignment.Left

textLabel.TextYAlignment = Enum.TextYAlignment.Top

textLabel.Text = "Main Menu"

textLabel.Parent = screenGui

```

## [Pseudo-classes](#pseudo-classes)[](#pseudo-classes)

The Roblox equivalent to CSS [pseudo-class](https://developer.mozilla.org/docs/Web/CSS/Pseudo-classes)  selectors are state selectors  which correspond to one of the four [Enum.GuiState](/docs/en-us/reference/engine/enums/GuiState)  values such as [Hover](/docs/en-us/reference/engine/enums/GuiState)  or [Press](/docs/en-us/reference/engine/enums/GuiState) .

CSS

```

img:hover {

	opacity: 0.5;

}

```

HTML

```

<img src="gear.png" width="100" height="100">

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = "ImageLabel:Hover" -- State selector

rule:SetProperty("ImageTransparency", 0.5)

-- Create image label

local imageLabel = Instance.new("ImageLabel")

imageLabel.Image = "rbxassetid://104919049969988"

imageLabel.Size = UDim2.new(0, 100, 0, 100)

imageLabel.BackgroundTransparency = 1

imageLabel.Parent = screenGui

```

## [Pseudo-instances](#pseudo-instances)[](#pseudo-instances)

Similar to how CSS [pseudo-elements](https://developer.mozilla.org/docs/Web/CSS/Pseudo-elements)  can modify specific parts of an element, Roblox can create phantom [UIComponents](/docs/en-us/reference/engine/classes/UIComponent)  through a style rule's [Selector](/docs/en-us/reference/engine/classes/StyleRule#Selector)  property. For example, the following rule effectively creates a [UICorner](/docs/en-us/reference/engine/classes/UICorner)  modifier under every [Frame](/docs/en-us/reference/engine/classes/Frame)  tagged with RoundedCorner20  and sets each modifier's [CornerRadius](/docs/en-us/reference/engine/classes/UICorner#CornerRadius)  to 20  pixels.

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = "Frame.RoundedCorner20::UICorner" -- UI component selector

rule:SetProperty("CornerRadius", UDim.new(0, 20))

-- Create frame

local frame = Instance.new("Frame")

frame.Size = UDim2.new(0.4, 0, 0.2, 0)

frame.Parent = screenGui

-- Apply tag to frame

CollectionService:AddTag(frame, "RoundedCorner20")

```

## [Queries](#queries)[](#queries)

Roblox style queries  bridge the gap between CSS [media queries](https://developer.mozilla.org/docs/Web/CSS/CSS_media_queries)  and [container queries](https://developer.mozilla.org/docs/Web/CSS/CSS_containment/Container_queries) . Using the @  prefix, you can toggle styles based on parent dimensions, input device types, or user accessibility settings.

In CSS, @container  applies styles based on the size of a parent element. In Roblox, you define a pseudo‑instance query using ::StyleQuery  followed by an [identifier](#identifier)  for the condition's [Selector](/docs/en-us/reference/engine/classes/StyleRule#Selector)  property, for example "::StyleQuery #WideContainer" , alongside a [StyleQuery](/docs/en-us/reference/engine/classes/StyleQuery)  condition name like "MinSize"  to evaluate the parent's [GuiObject.AbsoluteSize](/docs/en-us/reference/engine/classes/GuiObject#AbsoluteSize) . Then, to apply styles to the instance or its children when the query is active, create a [StyleRule](/docs/en-us/reference/engine/classes/StyleRule)  with the @[identifier]  prefix as its [Selector](/docs/en-us/reference/engine/classes/StyleRule#Selector) , for example @WideContainer .

CSS

```

.container {

	container-type: inline-size;

	background-color: rgba(0, 0, 34, 0.5);

}

button {

	background-color: #335FFF;

	color: #E1E1E1;

	width: 75%;

	height: 40px;

	border: none;

}

@container (min-width: 400px) {

	button {

		background-color: #cc0033;

	}

}

```

HTML

```

<div class="container" style="width: 80%; height: 200px;">

	<button>Main Menu</button>

</div>

```

Luau

```

-- Container rule

local containerRule = Instance.new("StyleRule")

containerRule.Selector = "Frame" -- Roblox class selector

containerRule:SetProperties({

	BackgroundColor3 = Color3.fromRGB(0, 0, 34),

	BackgroundTransparency = 0.5,

	BorderSizePixel = 0

})

containerRule.Parent = coreSheet

-- Button rule

local buttonRule = Instance.new("StyleRule")

buttonRule.Selector = "TextButton" -- Roblox class selector

buttonRule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	Size = UDim2.new(0.75, 0, 0, 40),

	BorderSizePixel = 0

})

buttonRule.Parent = containerRule -- Child of container rule

-- Query condition (#WideContainer)

local queryCondition = Instance.new("StyleRule")

queryCondition.Selector = "::StyleQuery #WideContainer"

queryCondition:SetProperty("MinSize", Vector2.new(400, 0))

queryCondition.Parent = containerRule -- Child of container rule

-- Rule that applies when condition is active (@WideContainer)

local queryStyle = Instance.new("StyleRule")

queryStyle.Selector = "@WideContainer Frame > TextButton" -- Child selector

queryStyle:SetProperty("BackgroundColor3", Color3.fromHex("CC0033"))

queryStyle.Parent = containerRule -- Child of container rule

-- Create instances

local container = Instance.new("Frame")

container.Size = UDim2.new(0.8, 0, 0, 200)

container.Parent = screenGui

local button = Instance.new("TextButton")

button.Text = "Main Menu"

button.Parent = container

```

Roblox also provides built-in queries  that map directly to global environment states such as [ViewportDisplaySize](/docs/en-us/reference/engine/classes/GuiService#ViewportDisplaySize)  or [ReducedMotionEnabled](/docs/en-us/reference/engine/classes/GuiService#ReducedMotionEnabled) . These do not require a ::StyleQuery  definition and can be used directly with a @  prefix.

| CSS Media Feature | | Roblox Style Query Selector |
| --- | --- |
| (max-width: 600px) | | @ViewportDisplaySizeSmall |
| (min-width: 601px) and (max-width: 1200px) | | @ViewportDisplaySizeMedium |
| (min-width: 1201px) | | @ViewportDisplaySizeLarge |
| (pointer: fine) | | @PreferredInputKeyboardAndMouse |
| (pointer: coarse) | | @PreferredInputTouch |
| (any-pointer: coarse) | | @PreferredInputGamepad |
| (prefers-reduced-motion: reduce) | | @ReducedMotionEnabledTrue |
| (prefers-reduced-motion: no-preference) | | @ReducedMotionEnabledFalse |

CSS

```

.container {

	container-type: inline-size;

	background-color: rgba(0, 0, 34, 0.5);

}

@media (prefers-reduced-motion: reduce) {

	.container {

		background-color: rgba(0, 0, 34, 1);

	}

}

```

HTML

```

<div class="container" style="width: 80%; height: 200px;">

</div>

```

Luau

```

-- Container rule

local containerRule = Instance.new("StyleRule")

containerRule.Selector = "Frame" -- Roblox class selector

containerRule:SetProperties({

	BackgroundColor3 = Color3.fromRGB(0, 0, 34),

	BackgroundTransparency = 0.5,

	BorderSizePixel = 0

})

containerRule.Parent = coreSheet

-- Built-in query

local motionRule = Instance.new("StyleRule")

motionRule.Selector = "@ReducedMotionEnabledTrue Frame"

motionRule:SetProperty("BackgroundTransparency", 0)

motionRule.Parent = containerRule -- Child of container rule

-- Create instances

local container = Instance.new("Frame")

container.Size = UDim2.new(0.8, 0, 0, 200)

container.Parent = screenGui

```

## [Variables](#variables)[](#variables)

CSS lets you declare and reference [variables](https://developer.mozilla.org/docs/Web/CSS/--*)  throughout a style system. Roblox achieves this through tokens and the [instance attributes](/docs/en-us/studio/properties#instance-attributes)  system. Using $  as a prefix, you can reference attributes declared in a [StyleRule](/docs/en-us/reference/engine/classes/StyleRule)  or [StyleSheet](/docs/en-us/reference/engine/classes/StyleSheet)  inheritance chain when setting style properties.

CSS

```

:root {

	--button-bg-color: #335FFF;

	--button-text-color: #E1E1E1;

}

button {

	background-color: var(--button-bg-color);

	color: var(--button-text-color);

}

```

HTML

```

<button>Main Menu</button>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

-- Set style sheet tokens using attributes

coreSheet:SetAttribute("ButtonBgColor", Color3.fromHex("335FFF"))

coreSheet:SetAttribute("ButtonTextColor", Color3.fromHex("E1E1E1"))

rule.Selector = "TextButton" -- Class selector

rule:SetProperties({

	BackgroundColor3 = "$ButtonBgColor",

	TextColor3 = "$ButtonTextColor"

})

-- Create button

local button = Instance.new("TextButton")

button.AutomaticSize = Enum.AutomaticSize.XY

button.Text = "Main Menu"

button.Parent = screenGui

```

## [Transitions](#transitions)[](#transitions)

CSS [transitions](https://developer.mozilla.org/docs/Web/CSS/Guides/Transitions)  let you tween property values over a set duration. You can achieve this in Roblox by setting property transitions on a [StyleRule](/docs/en-us/reference/engine/classes/StyleRule)  through [SetPropertyTransition()](/docs/en-us/reference/engine/classes/StyleRule#SetPropertyTransition)  (single) or [SetPropertyTransitions()](/docs/en-us/reference/engine/classes/StyleRule#SetPropertyTransitions)  (multiple).

CSS

```

button {

	background-color: #335FFF;

	color: #E1E1E1;

	width: 15%;

	height: 40px;

	border: none;

	transition:

		background-color 1s ease-out,

		transform 1.25s ease-out

}

button:hover {

	background-color: #33AAFF;

	transform: rotate(-5deg);

}

```

HTML

```

<button>Main Menu</button>

```

Luau

```

-- Button rule

local buttonRule = Instance.new("StyleRule")

buttonRule.Selector = "TextButton" -- Roblox class selector

buttonRule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	Size = UDim2.new(0.15, 0, 0, 40),

	BorderSizePixel = 0

})

-- Set property transition behaviors

buttonRule:SetPropertyTransitions({

	BackgroundColor3 = TweenInfo.new(1, Enum.EasingStyle.Cubic, Enum.EasingDirection.Out),

	Rotation = TweenInfo.new(1.25, Enum.EasingStyle.Cubic, Enum.EasingDirection.Out)

})

buttonRule.Parent = coreSheet

-- Button hover rule

local hoverRule = Instance.new("StyleRule")

hoverRule.Selector = "TextButton:Hover" -- State selector

hoverRule:SetProperties({

	AutoButtonColor = false,

	BackgroundColor3 = Color3.fromHex("33AAFF"),

	Rotation = -5

})

hoverRule.Parent = coreSheet

-- Create text button

local button = Instance.new("TextButton")

button.Text = "Main Menu"

button.Parent = screenGui

```

## [Nesting and merging](#nesting-and-merging)[](#nesting-and-merging)

Borrowing a concept from [SCSS](https://sass-lang.com/guide/#nesting) , [StyleRules](/docs/en-us/reference/engine/classes/StyleRule)  can be nested together and their selectors will merge .

SCSS

```

#menu-frame {

	background-color: #000022;

	width: 25%;

	min-height: 200px;

	display: flex;

	flex-direction: column;

	justify-content: space-evenly;

	align-items: center;

	> button {

		background-color: #335FFF;

		color: #E1E1E1;

		width: 80%;

		height: 40px;

		border: none;

		&:hover {

			opacity: 0.5;

		}

	}

}

```

HTML

```

<div id="menu-frame">

	<button>Charms</button>

	<button>Mana</button>

	<button>Scrolls</button>

</div>

```

Luau

```

-- Menu frame rule

local menuFrameRule = Instance.new("StyleRule")

menuFrameRule.Selector = "#MenuFrame"

menuFrameRule:SetProperties({

	BackgroundColor3 = Color3.fromHex("000022"),

	Size = UDim2.new(0.25, 0, 0, 200),

	AutomaticSize = Enum.AutomaticSize.Y

})

menuFrameRule.Parent = coreSheet

-- Menu layout rule

local menuLayoutRule = Instance.new("StyleRule")

menuLayoutRule.Selector = "::UIListLayout"

menuLayoutRule:SetProperties({

	FillDirection = Enum.FillDirection.Vertical,

	VerticalFlex = Enum.UIFlexAlignment.SpaceEvenly,

	HorizontalAlignment = Enum.HorizontalAlignment.Center

})

menuLayoutRule.Parent = menuFrameRule -- Set menu frame rule as parent

-- Button rule

local buttonRule = Instance.new("StyleRule")

buttonRule.Selector = "> TextButton"

buttonRule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	Size = UDim2.new(0.8, 0, 0, 40),

	BorderSizePixel = 0

})

buttonRule.Parent = menuFrameRule -- Set menu frame rule as parent

-- Button hover rule

local buttonHoverRule = Instance.new("StyleRule")

buttonHoverRule.Selector = ":Hover"

buttonHoverRule:SetProperties({

	AutoButtonColor = false,

	BackgroundTransparency = 0.5,

	TextTransparency = 0.5

})

buttonHoverRule.Parent = buttonRule -- Set button rule as parent

-- Create parent frame

local menuFrame = Instance.new("Frame")

menuFrame.Name = "MenuFrame"

menuFrame.Parent = screenGui

-- Create buttons inside frame

local button1 = Instance.new("TextButton")

button1.Text = "Charms"

button1.Parent = menuFrame

local button2 = Instance.new("TextButton")

button2.Text = "Mana"

button2.Parent = menuFrame

local button3 = Instance.new("TextButton")

button3.Text = "Scrolls"

button3.Parent = menuFrame

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
