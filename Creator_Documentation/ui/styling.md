<!-- Source: https://create.roblox.com/docs/en-us/ui/styling -->

UI styling | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/styling.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)
6. /
7. UI styling

# UI styling

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/styling/index.md)

UI styling is a Roblox solution to stylesheets, [similar to CSS](/docs/en-us/ui/styling/css-comparisons) , that lets you declare and globally apply overrides to UI instance properties. This engine‑level support is the foundation for the [Style Editor](/docs/en-us/ui/styling/editor)  and the end‑to‑end token pipeline.

## [Concepts](#concepts)[](#concepts)

Style rules  (part of a [StyleSheet](/docs/en-us/reference/engine/classes/StyleSheet) ) apply to every instance that matches the rule's [Selector](/docs/en-us/reference/engine/classes/StyleRule#Selector)  definition to match characteristics such as class name, instance name, and hierarchy relationships. See the [Selector](/docs/en-us/reference/engine/classes/StyleRule#Selector)  documentation for details.

Style tokens , defined through [attributes](/docs/en-us/studio/properties#instance-attributes)  of a token [StyleSheet](/docs/en-us/reference/engine/classes/StyleSheet) , represent UI property variables that can be used across styles and components, for example a common color for a [Frame.BackgroundColor3](/docs/en-us/reference/engine/classes/Frame#BackgroundColor3) , [TextLabel.TextColor3](/docs/en-us/reference/engine/classes/TextLabel#TextColor3) , and [UIStroke.Color](/docs/en-us/reference/engine/classes/UIStroke#Color) . Tokens are comparable to CSS [variables](/docs/en-us/ui/styling/css-comparisons#variables) .

Style themes , configured through [attributes](/docs/en-us/studio/properties#instance-attributes)  of a theme [StyleSheet](/docs/en-us/reference/engine/classes/StyleSheet) , consist of sets of specific tokens that can be swapped, for example color tokens that define a "light" and "dark" theme. Related themes must have the same set of tokens to work correctly.

Style queries  allow you to apply styles conditionally based on the UI's context or environment. These are comparable to CSS [container queries and media queries](/docs/en-us/ui/styling/css-comparisons#queries) , enabling UI to adapt to screen size, input types, or user accessibility settings.

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Styling-Hierarchy.png)

## [Rule propagation](#rule-propagation)[](#rule-propagation)

A [StyleLink](/docs/en-us/reference/engine/classes/StyleLink)  instance links a [StyleSheet](/docs/en-us/reference/engine/classes/StyleSheet)  and its associated rules to a parent [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  and all of the [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  within it. Only one [StyleSheet](/docs/en-us/reference/engine/classes/StyleSheet)  can apply to a given tree.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StyleLink-Propagation.png)

## [Selector definitions](#selector-definitions)[](#selector-definitions)

At a high level, instance matching and modification via a rule's [Selector](/docs/en-us/reference/engine/classes/StyleRule#Selector)  definition operates through:

-

Roblox class  selectors which target all instances of a given [GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  class, for example [Frame](/docs/en-us/reference/engine/classes/Frame) , [ImageLabel](/docs/en-us/reference/engine/classes/ImageLabel) , [TextButton](/docs/en-us/reference/engine/classes/TextButton) , etc.

-

Instance [tags](/docs/en-us/studio/properties#instance-tags)  applied to specific UI objects through [CollectionService](/docs/en-us/reference/engine/classes/CollectionService) .

-

Instance name  selection according to the value of the UI object's [Instance.Name](/docs/en-us/reference/engine/classes/Instance#Name) .

-

Instance modifiers , similar to [CSS pseudo-elements](/docs/en-us/ui/styling/css-comparisons#pseudo-instances) , applied through phantom [UIComponents](/docs/en-us/reference/engine/classes/UIComponent)  such as [UICorner](/docs/en-us/reference/engine/classes/UICorner)  or [UIStroke](/docs/en-us/reference/engine/classes/UIStroke) .

-

[GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  state  selectors, similar to [CSS pseudo-class](/docs/en-us/ui/styling/css-comparisons#pseudo-classes)  selectors, which correspond to one of the four [GuiState](/docs/en-us/reference/engine/enums/GuiState)  enum values such as [Hover](/docs/en-us/reference/engine/enums/GuiState) .

-

Roblox query  selectors, similar to [CSS container and media queries](/docs/en-us/ui/styling/css-comparisons#queries) , which use the @  prefix to apply styles only while a [StyleQuery](/docs/en-us/reference/engine/classes/StyleQuery)  instance or pseudo‑instance with the same name is active.

Class Selector Tag Selector UI Modifier Selector

The following setup shows how size and color tokens, a theme, and a class selector of "Frame"  produce a magenta [Frame](/docs/en-us/reference/engine/classes/Frame)  of size 200×200 pixels.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/Styling-Flowchart-Class.png)

Code Equivalent

UI Class Selector

```

local CollectionService = game:GetService("CollectionService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local screenGui = script.Parent

-- Tokens

local tokens = Instance.new("StyleSheet")

tokens.Name = "Tokens"

tokens.Parent = ReplicatedStorage

tokens:SetAttribute("SquareS", UDim2.fromOffset(50, 50))

tokens:SetAttribute("SquareM", UDim2.fromOffset(100, 100))

tokens:SetAttribute("SquareL", UDim2.fromOffset(200, 200))

tokens:SetAttribute("Fit", UDim2.fromScale(1, 1))

tokens:SetAttribute("Magenta", Color3.fromHex("FF0099"))

tokens:SetAttribute("Gold", Color3.fromHex("FFCC00"))

tokens:SetAttribute("Aqua", Color3.fromHex("0093F0"))

-- ThemeA

local themeA = Instance.new("StyleSheet")

themeA.Name = "ThemeA"

themeA.Parent = ReplicatedStorage

local tokensDerive = Instance.new("StyleDerive")

tokensDerive.StyleSheet = tokens  -- Derive global tokens

tokensDerive.Parent = themeA

themeA:SetAttribute("FrameSize", "$SquareM")

themeA:SetAttribute("FrameColor", "$Aqua")

-- ThemeB

local themeB = Instance.new("StyleSheet")

themeB.Name = "ThemeB"

themeB.Parent = ReplicatedStorage

local tokensDerive = Instance.new("StyleDerive")

tokensDerive.StyleSheet = tokens  -- Derive global tokens

tokensDerive.Parent = themeB

themeB:SetAttribute("FrameSize", "$SquareL")

themeB:SetAttribute("FrameColor", "$Magenta")

-- DesignSheet

local designSheet = Instance.new("StyleSheet")

designSheet.Name = "DesignSheet"

designSheet.Parent = ReplicatedStorage

local themeDerive = Instance.new("StyleDerive")

themeDerive.StyleSheet = themeB  -- Derive from ThemeB

themeDerive.Parent = designSheet

-- Link DesignSheet to ScreenGui

local styleLink = Instance.new("StyleLink")

styleLink.StyleSheet = designSheet

styleLink.Parent = screenGui

-- Configure rule

local rule = Instance.new("StyleRule")

rule.Selector = "Frame"  -- Class selector

rule.Parent = designSheet

-- Set rule properties

rule:SetProperties({

	["BackgroundColor3"] = "$FrameColor",

	["Size"] = "$FrameSize",

	["BorderSizePixel"] = 0

})

local frame = Instance.new("Frame")

frame.Parent = screenGui

```

## [Modified properties](#modified-properties)[](#modified-properties)

Instance properties affected by styling are flagged with a ⚠  in the Properties  window, and hovering over an affected property shows which style is influencing it. For example, if a style rule tells a tagged [Frame](/docs/en-us/reference/engine/classes/Frame)  to use an [AnchorPoint](/docs/en-us/reference/engine/classes/Frame#AnchorPoint)  of 0.5, 0.5 , that object property will show the default  value of 0, 0  but its actual [AnchorPoint](/docs/en-us/reference/engine/classes/Frame#AnchorPoint)  will use the rule's styled  value.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Styling-Modified-Property.png)

When a default or styled property value is further modified for a specific UI object, it becomes bold  to indicate an overridden value. For example — assuming a default [AnchorPoint](/docs/en-us/reference/engine/classes/Frame#AnchorPoint)  of 0, 0  — setting that property to 1, 1  for a specific instance reveals an override in bold:

Default Property Value Overridden Property Value

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui-HUDContainer.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/AnchorPoint-Default.png)

For any overridden property value, you can right-click it in the Properties  window and select Reset to Default  to revert it to the styled value, or to the default property value if it hasn't been styled.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
