<!-- Source: https://create.roblox.com/docs/en-us/ui/styling/editor -->

Style Editor | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/styling/editor.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)
6. /
7. UI styling

# Style Editor

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/styling/editor.md)

The built-in Style Editor  is a comprehensive tool that allows you to create, manage, and apply UI styles for Roblox games through a combination of [tokens](#style-tokens) , [design sheets](#design-sheets) , [style rules](#style-rules) , and [themes](#style-themes) .

Access the Style Editor  via the UI  tab.

 ![Style Editor tool indicated in UI tab of Studio toolbar](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Style-Editor.png)

Once open, click the Create Design  button to generate a base style set.

 ![Create Design button in opening dialog of Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Create-Design-Entry.png)

Creating a design style set through the Style Editor generates a BaseStyleSheet  inside a Design  folder within [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage) . This base sheet syncs specific engine‑level defaults like the [Color3](/docs/en-us/reference/engine/datatypes/Color3)  default of [163, 162, 165]  with defaults that come from insertion workflows in Studio. It's highly recommended that you do not  delete or attempt to modify the base style sheet — instead, build tokens and style rules around a design sheet to match your UI goals.

Additionally, a StyleSheet  sheet is generated in the Design  folder which contains a [StyleDerive](/docs/en-us/reference/engine/classes/StyleDerive)  to the base style sheet. If you choose to remove that [StyleDerive](/docs/en-us/reference/engine/classes/StyleDerive) , unstyled values for [GuiObjects](/docs/en-us/reference/engine/classes/GuiObject)  may become unexpected values, for example a default [Size](/docs/en-us/reference/engine/classes/GuiObject#Size)  of 0, 0, 0, 0 .

## [Style tokens](#style-tokens)[](#style-tokens)

Style tokens , defined through [attributes](/docs/en-us/studio/properties#instance-attributes)  of a token [StyleSheet](/docs/en-us/reference/engine/classes/StyleSheet) , represent UI property variables that can be used across styles and components; for example, there could be a common color for a [Frame.BackgroundColor3](/docs/en-us/reference/engine/classes/Frame#BackgroundColor3) , [TextLabel.TextColor3](/docs/en-us/reference/engine/classes/TextLabel#TextColor3) , and [UIStroke.Color](/docs/en-us/reference/engine/classes/UIStroke#Color) . Tokens are comparable to [CSS variables](/docs/en-us/ui/styling/css-comparisons#variables) .

Although not required for UI styling, tokens are highly recommended for extensible UI design and style updates over time. You should begin by creating the following tokens to understand how they tie into other aspects of universal styling.

1.

Create a new token style sheet:

1.

In the left column of the Style Editor, hover over Tokens , click the ⊕ , and select New Token StyleSheet .

2.

Rename the new sheet to TokenSheet .

 ![New token sheet created in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-TokenSheet-New.png)

2.

With the new token sheet selected, create several tokens by clicking Add a Token…  in the main panel. These tokens will be used throughout this guide for both [rules](#style-rules)  and [themes](#style-themes) .

 ![Token addition field in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-TokenSheet-Add-Token.png)

| Token Name | | Type | | Value |
| --- | --- |
| Gold | | [Color3](/docs/en-us/reference/engine/datatypes/Color3) | | #ffcc00 |
| Magenta | | [Color3](/docs/en-us/reference/engine/datatypes/Color3) | | #ff0099 |
| Orange | | [Color3](/docs/en-us/reference/engine/datatypes/Color3) | | #dd6030 |
| Oswald | | [Font](/docs/en-us/reference/engine/datatypes/Font) | | Oswald |
| Rad20 | | [UDim](/docs/en-us/reference/engine/datatypes/UDim) | | 0, 20 |
| RectL | | [UDim2](/docs/en-us/reference/engine/datatypes/UDim2) | | 0, 300, 0, 160 |
| SquareL | | [UDim2](/docs/en-us/reference/engine/datatypes/UDim2) | | 0, 200, 0, 200 |
| Text24 | | number | | 24 |
| Text32 | | number | | 32 |

 ![Tokens added to TokenSheet in Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-TokenSheet-Tokens.png)

## [Design sheets](#design-sheets)[](#design-sheets)

A design style sheet aggregates [style rules](#style-rules)  and can be linked to [DataModel](/docs/en-us/reference/engine/classes/DataModel)  trees to apply style properties to UI instances. Only one [StyleSheet](/docs/en-us/reference/engine/classes/StyleSheet)  can apply to a given tree, although you can use [themes](#style-themes)  to swap related styles across your UI, a concept covered later in this guide.

A prepopulated design sheet named StyleSheet  is created via the Create Design  button. It contains class rules for common UI objects such as [Frame](/docs/en-us/reference/engine/classes/Frame)  and [TextLabel](/docs/en-us/reference/engine/classes/TextLabel) . It also contains two [StyleDerive](/docs/en-us/reference/engine/classes/StyleDerive)  instances which derive (inherit) [tokens](#style-tokens)  and styles from the base style sheet for use in your custom styling configurations.

 ![Initial configuration of design sheet in Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Initial-Config.png)

Once you have a design sheet, you can set up a test [on‑screen container](/docs/en-us/ui/on-screen-containers)  to use with the Style Editor, or an [in‑game container](/docs/en-us/ui/in-experience-containers)  if desired.

1.

Hover over [StarterGui](/docs/en-us/reference/engine/classes/StarterGui)  in the [Explorer](/docs/en-us/studio/explorer)  and insert a [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui) .

2.

Confirm that a new [StyleLink](/docs/en-us/reference/engine/classes/StyleLink)  instance appears under the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  with its [StyleSheet](/docs/en-us/reference/engine/classes/StyleLink#StyleSheet)  property set to the StyleSheet  design sheet.

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui-StyleLink.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/StyleLink-StyleSheet.png)

If the [StyleLink](/docs/en-us/reference/engine/classes/StyleLink)  is not created, you can quickly create one by selecting the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  in the [Explorer](/docs/en-us/studio/explorer)  as well as the StyleSheet  design sheet in the left column of the Style Editor. Then, click the Insert StyleLink  button in the upper‑right section of the editor's main panel.

## [Style rules](#style-rules)[](#style-rules)

Style rules  apply to every instance that matches the rule's [Selector](/docs/en-us/reference/engine/classes/StyleRule#Selector)  definition to match characteristics such as class name, instance tag, and hierarchy relationships. At a high level, instance matching and modification via a rule's [Selector](/docs/en-us/reference/engine/classes/StyleRule#Selector)  definition operates through:

-

Roblox [class](#class-rule)  selectors which target all instances of a given UI class, for example [Frame](/docs/en-us/reference/engine/classes/Frame) , [ImageLabel](/docs/en-us/reference/engine/classes/ImageLabel) , [TextButton](/docs/en-us/reference/engine/classes/TextButton) , etc.

-

Instance [tag](#tag-rule)  selectors that target specific UI objects [tagged](/docs/en-us/studio/properties#instance-tags)  through [CollectionService](/docs/en-us/reference/engine/classes/CollectionService) .

-

Instance [modifiers](#ui-modifier)  applied through phantom [UIComponents](/docs/en-us/reference/engine/classes/UIComponent)  such as [UICorner](/docs/en-us/reference/engine/classes/UICorner)  or [UIStroke](/docs/en-us/reference/engine/classes/UIStroke) .

-

[GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  [state](#state-rule)  selectors which correspond to one of the four [Enum.GuiState](/docs/en-us/reference/engine/enums/GuiState)  enum values such as [Hover](/docs/en-us/reference/engine/enums/GuiState#Hover) .

-

Instance name selection according to the value of the UI object's [Instance.Name](/docs/en-us/reference/engine/classes/Instance#Name) .

### [Class rule](#class-rule)[](#class-rule)

A style class  selector targets all instances of a given UI class. The following rule setup styles all [Frames](/docs/en-us/reference/engine/classes/Frame)  with a uniform background color and size.

1.

In the left column of the Style Editor, select Frame  in the UI Elements  branch.

 ![Default class style in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Class-Rule-New-Class.png)

2.

Link two previously created [style tokens](#style-tokens)  to two [Frame](/docs/en-us/reference/engine/classes/Frame)  properties:

| Property | | Style Token |
| [BackgroundColor3](/docs/en-us/reference/engine/classes/Frame#BackgroundColor3) | | $Magenta |
| [Size](/docs/en-us/reference/engine/classes/Frame#Size) | | $SquareL |

1.

Click Add a Property…  in the main panel and select the necessary property. Note that you can type keywords to more quickly find properties in the dropdown menu.

2.

Instead of entering a static value, click the ⋮  button and select Link Token .

3.

Click the $  which appears in the value field and select the proper associated token.

![Token linking workflow diagrammed in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Class-Rule-Configure.png)

 ![Class rule configured with tokens in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Class-Rule-Tokens.png)

3.

Insert a new [Frame](/docs/en-us/reference/engine/classes/Frame)  into the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  you previously [created and linked](#design-sheets) . The styles you defined should automatically apply to it.

 ![Final styled class rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Class-Rule-Result.png)

### [Tag rule](#tag-rule)[](#tag-rule)

Instance tag  selectors target specific UI objects [tagged](/docs/en-us/studio/properties#instance-tags)  through [CollectionService](/docs/en-us/reference/engine/classes/CollectionService) . The following rule setup styles a [TextButton](/docs/en-us/reference/engine/classes/TextButton)  tagged as ButtonPrimary  with a custom background color, font, and text size.

1.

In the left column of the Style Editor, hover over the StyleSheet  sheet, click the ⋮  button, and navigate through to New  ⟩ Tag .

 ![Creation of tag rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Tag-Rule-New.png)

2.

Rename the new tag rule .ButtonPrimary  (note the leading . ).

 ![Tag rule renamed in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Tag-Rule-Renamed.png)

3.

Link three previously created [style tokens](#style-tokens)  to three [TextButton](/docs/en-us/reference/engine/classes/TextButton)  properties:

| Property | | Style Token |
| [BackgroundColor3](/docs/en-us/reference/engine/classes/TextButton#BackgroundColor3) | | $Gold |
| [FontFace](/docs/en-us/reference/engine/classes/TextButton#FontFace) | | $Oswald |
| [TextSize](/docs/en-us/reference/engine/classes/TextButton#TextSize) | | $Text32 |

1.

Click Add a Property…  in the main panel and select the necessary property. Remember that you can type keywords to more quickly find properties in the dropdown menu.

2.

Instead of entering a static value, click the ⋮  button and select Link Token .

3.

Click the $  which appears in the value field and select the proper associated token.

![Token linking workflow diagrammed in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Tag-Rule-Configure.png)

 ![Tag rule configured with tokens in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Tag-Rule-Tokens.png)

4.

Insert a new [TextButton](/docs/en-us/reference/engine/classes/TextButton)  into the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  you previously [created and linked](#design-sheets)  and [tag](/docs/en-us/studio/properties#instance-tags)  it as ButtonPrimary . A convenient shortcut is as follows:

1.

Make sure the new [TextButton](/docs/en-us/reference/engine/classes/TextButton)  is selected in the [Explorer](/docs/en-us/studio/explorer) .

2.

With the .ButtonPrimary  tag rule selected in the left column of the Style Editor, click Apply Tag  in the main panel. The styles you defined should automatically apply to the button.

![Tag linking workflow diagrammed in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Tag-Rule-Apply-Tag.png)

 ![Final styled tag rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Tag-Rule-Result.png)

### [UI modifier](#ui-modifier)[](#ui-modifier)

Instance modifier selectors apply phantom [UIComponents](/docs/en-us/reference/engine/classes/UIComponent)  such as [UICorner](/docs/en-us/reference/engine/classes/UICorner)  or [UIStroke](/docs/en-us/reference/engine/classes/UIStroke)  to further style an object. The following rule setup styles a [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)  with a custom text size and rounded corners.

1.

In the left column of the Style Editor, select TextLabel  in the UI Elements  branch.

 ![Default class style in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-New-Class.png)

2.

Link a previously created [style token](#style-tokens)  to the [TextSize](/docs/en-us/reference/engine/classes/TextLabel#TextSize)  property:

1.

Click Add a Property…  in the main panel and select the [TextSize](/docs/en-us/reference/engine/classes/TextLabel#TextSize)  property. Remember that you can type keywords to more quickly find properties in the dropdown menu.

2.

Instead of entering a static value, click the ⋮  button and select Link Token .

3.

Click the $  which appears in the value field and select the $Text32  token.

![Token linking workflow diagrammed in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-Configure.png)

 ![Class rule configured with tokens in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-Tokens.png)

A pseudo instance  is required to configure and apply rounded corners to other elements. To create one:

1.

In the left column, hover over TextLabel , click the ⋮  button, and navigate through to New  ⟩ Pseudo Instance  ⟩ UICorner .

 ![Creation of a pseudo instance in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-Pseudo-Instance-New.png)

A new UICorner  pseudo instance appears under the TextLabel  element in the left column.

 ![Resulting pseudo instance in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-Pseudo-Instance-Created.png)

2.

With the new UICorner  instance selected in the left column, link a previously created [style token](#style-tokens)  to the [CornerRadius](/docs/en-us/reference/engine/classes/UICorner#CornerRadius)  property:

1.

Click Add a Property…  in the main panel and select the [CornerRadius](/docs/en-us/reference/engine/classes/UICorner#CornerRadius)  property.

2.

Instead of entering a static value, click the ⋮  button and select Link Token .

3.

Click the $  which appears in the value field and select the $Rad20  token.

 ![Pseudo instance configured with tokens in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-Pseudo-Instance-Tokens.png)

3.

Insert a new [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)  into the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  you previously [created and linked](#design-sheets) . The styles you defined should automatically apply to it.

 ![Final styled modifier rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Modifier-Rule-Result.png)

### [State rule](#state-rule)[](#state-rule)

[GuiObject](/docs/en-us/reference/engine/classes/GuiObject)  state  selectors correspond to one of the four [GuiState](/docs/en-us/reference/engine/enums/GuiState)  enum values such as [Hover](/docs/en-us/reference/engine/enums/GuiState) , letting you automatically configure style changes for interactive states. The following rule setup creates a hover state of -4  degrees rotation for all [ImageButtons](/docs/en-us/reference/engine/classes/ImageButton) .

1.

In the left column of the Style Editor, select ImageButton  in the UI Elements  branch.

 ![Default class style in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-State-Rule-New-Class.png)

2.

Click the ⋮  button and navigate through to New  ⟩ GuiState  ⟩ Hover .

 ![Creation of state rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-State-Rule-New.png)

A new Hover  state modifier instance appears under the ImageButton  element in the left column.

 ![Resulting state rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-State-Rule-Created.png)

3.

With the new Hover  modifier selected in the left column, click Add a Property…  in the main panel and select [Rotation](/docs/en-us/reference/engine/classes/ImageButton#Rotation) . Remember that you can type keywords to more quickly find properties in the dropdown menu.

4.

Enter -4  in the property's value field.

 ![State rule configured with tokens in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-State-Rule-Tokens.png)

5.

Insert a new [ImageButton](/docs/en-us/reference/engine/classes/ImageButton)  into the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  you previously [created and linked](#design-sheets) . When you hover over the button in the viewport, it should rotate 4 degrees counterclockwise.

 ![Final styled state rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-State-Rule-Result.png)

## [Style queries](#style-queries)[](#style-queries)

Style queries , similar to [CSS container and media queries](/docs/en-us/ui/styling/css-comparisons#queries) , allow you to apply conditional logic to your UI based on container size, input type, or other factors. The Style Editor provides a streamlined workflow to create both the query logic (conditions) and the resulting styles as a unified set.

### [Built-in queries](#built-in-queries)[](#built-in-queries)

Some [StyleQuery](/docs/en-us/reference/engine/classes/StyleQuery)  conditions are very common, such as changing properties based on the [ViewportDisplaySize](/docs/en-us/reference/engine/classes/GuiService#ViewportDisplaySize) . To simplify this, the Style Editor includes built‑in  queries which allow you to create conditional rules without needing a pseudo or real instance of a [StyleQuery](/docs/en-us/reference/engine/classes/StyleQuery) ; instead, you simply use a query rule with a predefined selector like ViewportDisplaySizeSmall .

The following steps demonstrate how to generate built‑in queries for a [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)  to handle [Small](/docs/en-us/reference/engine/enums/DisplaySize#Small) , [Medium](/docs/en-us/reference/engine/enums/DisplaySize#Medium) , and [Large](/docs/en-us/reference/engine/enums/DisplaySize#Large)  viewport sizes.

1.

In the left column of the Style Editor, hover over TextLabel , click the ⋮  button, and navigate through to New  ⟩ StyleQuery  ⟩ Builtin  ⟩ ViewportDisplaySize .

 ![Creation of a built-in StyleQuery in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Query-New-Builtin.png)

This creates a Queries  folder under the TextLabel  rule containing three query rules:

-

@ViewportDisplaySizeLarge  — Define properties that apply when the viewport is [Large](/docs/en-us/reference/engine/enums/DisplaySize#Large) .

-

@ViewportDisplaySizeMedium  — Define properties that apply when the viewport is [Medium](/docs/en-us/reference/engine/enums/DisplaySize#Medium) .

-

@ViewportDisplaySizeSmall  — Define properties that apply when the viewport is [Small](/docs/en-us/reference/engine/enums/DisplaySize#Small) .

 ![Hierarchy of a StyleQuery within a class rule.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Query-Builtin-Hierarchy.png)

2.

Click Add a Property…  under each query rule and set the specific [Text](/docs/en-us/reference/engine/classes/TextLabel#Text)  string that should display when that query is active:

| Query Rule | | Property | | Value |
| @ViewportDisplaySizeLarge | | [Text](/docs/en-us/reference/engine/classes/TextLabel#Text) | | Large Text |
| @ViewportDisplaySizeMedium | | [Text](/docs/en-us/reference/engine/classes/TextLabel#Text) | | Medium Text |
| @ViewportDisplaySizeSmall | | [Text](/docs/en-us/reference/engine/classes/TextLabel#Text) | | Small Text |

3.

To verify the queries, use the [Device Emulator](/docs/en-us/studio/testing-modes#device-emulation)  to test how the UI responds to different resolutions across three distinct devices:

1.

Insert a new [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)  into the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui) .

2.

Change the Device  in the [Device Emulator](/docs/en-us/studio/testing-modes#device-emulation)  to see the text change in real time.

| Size | | Example Emulations |
| [Large](/docs/en-us/reference/engine/enums/DisplaySize#Large) | | PS5 , PS4 , Xbox One |
| [Medium](/docs/en-us/reference/engine/enums/DisplaySize#Medium) | | Average Laptop , HD 720 |
| [Small](/docs/en-us/reference/engine/enums/DisplaySize#Small) | | iPhone XR , iPad 7th Generation |

### [Custom query](#custom-query)[](#custom-query)

You can add a style query to any existing rule to create responsive UI that adapts to its container. The following setup configures a [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)  to automatically change its appearance only when it expands to a width of 400 pixels or more.

1.

In the left column of the Style Editor, hover over TextLabel , click the ⋮  button, and navigate through to New  ⟩ StyleQuery  ⟩ Custom .

 ![Creation of a custom StyleQuery in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Query-New-Custom.png)

This action creates a Queries  folder under the TextLabel  rule containing two linked items:

-

::StyleQuery  pseudo-instance rule where you define the Conditions .

-

@StyleQuery  rule where you define the Properties  to apply when those conditions are met.

 ![Hierarchy of a StyleQuery within a class rule.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Query-Custom-Hierarchy.png)

2.

Select the parent TextLabel  rule in the main panel and define the following default properties:

| Property | | Value |
| [BackgroundColor3](/docs/en-us/reference/engine/classes/TextLabel#BackgroundColor3) | | $Magenta |
| [Text](/docs/en-us/reference/engine/classes/TextLabel#Text) | | Default Text |

3.

Select the ::StyleQuery  rule in the main panel, click Add a Condition… , and configure the following:

| Condition | | Value |
| MinSize | | 400, 0 |

See [StyleQuery.IsActive](/docs/en-us/reference/engine/classes/StyleQuery#IsActive)  as a reference for other conditions available through the ::StyleQuery  rule.

4.

Select the @StyleQuery  rule in the main panel and set the properties that should apply when the query is active:

| Property | | Value |
| [BackgroundColor3](/docs/en-us/reference/engine/classes/TextLabel#BackgroundColor3) | | $Gold |
| [Text](/docs/en-us/reference/engine/classes/TextLabel#Text) | | Large Text |

To verify the query, you can manually resize a [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)  in the viewport.

1.

Insert a new [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)  into the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui) .

2.

Adjust its width to see the style swap in real-time.

0–400 Pixel Width Over 400 Pixel Width

While the [TextLabel](/docs/en-us/reference/engine/classes/TextLabel)  width is smaller, the MinSize  condition is not met and the label uses its default background color and text.

![TextLabel appearing magenta with 'Default Text' on a phone viewport.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Query-Test-Small.png)

While manual resizing is a quick way to check responsive logic, you can also use Studio's built‑in emulation tools for more precise testing:

-

Use the [Device Emulator](/docs/en-us/studio/testing-modes#device-emulation)  to test how your UI responds to specific screen resolutions and [ViewportDisplaySize](/docs/en-us/reference/engine/classes/GuiService#ViewportDisplaySize)  conditions.

-

Use the [Controller Emulator](/docs/en-us/studio/testing-modes#controller-simulation)  to verify [PreferredInput](/docs/en-us/reference/engine/classes/UserInputService#PreferredInput)  logic, such as switching styles when a gamepad is detected.

## [Style transitions](#style-transitions)[](#style-transitions)

Style transitions , comparable to [CSS transitions](/docs/en-us/ui/styling/css-comparisons#transitions) , let you tween property values over a set duration.

### [Default](#default)[](#default)

To tween many UI properties with the same parameters, you can set a default transition that applies to all  properties unless another transition is explicitly set for a specific property.

1.

Select TextButton  in the UI Elements  branch and then, in the main panel, add three new properties with the following values:

| Property | | Value |
| [AutoButtonColor](/docs/en-us/reference/engine/classes/TextButton#AutoButtonColor) | | false |
| [BackgroundColor3](/docs/en-us/reference/engine/classes/TextButton#BackgroundColor3) | | #335FFF |
| [Rotation](/docs/en-us/reference/engine/classes/TextButton#Rotation) | | 0 |

 ![Class style in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-New-Class.png)

2.

Hover over the parent TextButton  row, click the ⋮ button, and navigate through to Insert  ⟩ Transition .

 ![Add default transition to a rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Add-Default-Transition.png)

A default transition of 1, Quad, Out, 0  inserts directly under the TextButton  rule, indicating a transition of 1 second, easing style [Quad](/docs/en-us/reference/engine/enums/EasingStyle#Quad) , easing direction [Out](/docs/en-us/reference/engine/enums/EasingDirection#Out) , and no delay.

 ![Default transition highlighted in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Default-Transition-Added.png)

3.

Hover over the parent TextButton  row, click the ⋮  button, and navigate through to New  ⟩ GuiState  ⟩ Hover .

 ![Creation of state rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Default-New-State.png)

4.

For the new Hover  modifier, add two new properties as the targets  for the hover state.

| Property | | Value |
| [BackgroundColor3](/docs/en-us/reference/engine/classes/TextButton#BackgroundColor3) | | #33AAFF |
| [Rotation](/docs/en-us/reference/engine/classes/TextButton#Rotation) | | -5 |

 ![Properties on hover state rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-State-Properties.png)

5.

Insert a new [TextButton](/docs/en-us/reference/engine/classes/TextButton)  into the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  you previously [created and linked](#design-sheets) . When you hover over the button in the viewport, it should gradually brighten and rotate 5 degrees counterclockwise.

 ![Final styled state rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Result.png)

### [Token-linked](#token-linked)[](#token-linked)

To reuse transition behaviors across multiple rules, you can define tokens  representing the [TweenInfo](/docs/en-us/reference/engine/datatypes/TweenInfo)  data type. The following rule setup creates a hover state to transition all [TextButtons](/docs/en-us/reference/engine/classes/TextButton)  to/from -5 degrees rotation and a lighter background color.

1.

If you haven't already, create a [token style sheet](#style-tokens)  named TokenSheet .

 ![New token sheet created in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-TokenSheet-New.png)

2.

With the new token sheet selected, create two new tokens by clicking Add a Token…  in the main panel.

| Token Name | | Type | | Tween Parameters |
| CubicOut | | [TweenInfo](/docs/en-us/reference/engine/datatypes/TweenInfo) | |
-

Duration  = 1.25

-

EasingStyle  = Cubic

-

EasingDirection  = Out

-

Delay  = 0

 |
| QuadInOut | | [TweenInfo](/docs/en-us/reference/engine/datatypes/TweenInfo) | |
-

Duration  = 0.5

-

EasingStyle  = Quad

-

EasingDirection  = InOut

-

Delay  = 0

 |

 ![Tokens added to TokenSheet in Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Tokens-Defined.png)

3.

Select TextButton  in the UI Elements  branch and then, in the main panel, add three new properties with the following values:

| Property | | Value |
| [AutoButtonColor](/docs/en-us/reference/engine/classes/TextButton#AutoButtonColor) | | false |
| [BackgroundColor3](/docs/en-us/reference/engine/classes/TextButton#BackgroundColor3) | | #335FFF |
| [Rotation](/docs/en-us/reference/engine/classes/TextButton#Rotation) | | 0 |

 ![Class style in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-New-Class.png)

4.

For each new property except for [AutoButtonColor](/docs/en-us/reference/engine/classes/TextButton#AutoButtonColor) , hover over its row, click the ⋮  button, and select Insert  ⟩ Transition .

 ![Add transition to a property in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Add-Transition.png)

5.

Hover over the new Transition  row under each property, click the ⋮  button, and select Link Token . Then, instead of entering a static value, click the $  which appears in the value field and select the proper transition token.

 ![Token linking workflow diagrammed in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Tokens-Link.png)

| Property Transition | | Transition Token |
| [BackgroundColor3](/docs/en-us/reference/engine/classes/TextButton#BackgroundColor3) | | $CubicOut |
| [Size](/docs/en-us/reference/engine/classes/TextButton#Size) | | $QuadInOut |

 ![Transition tokens linked in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Tokens-Linked.png)

6.

Hover over the parent TextButton  row, click the ⋮  button, and navigate through to New  ⟩ GuiState  ⟩ Hover .

 ![Creation of state rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-New-State.png)

7.

For the new Hover  modifier, add two new properties as the targets  for the hover state.

| Property | | Value |
| [BackgroundColor3](/docs/en-us/reference/engine/classes/TextButton#BackgroundColor3) | | #33AAFF |
| [Rotation](/docs/en-us/reference/engine/classes/TextButton#Rotation) | | -5 |

 ![Properties on hover state rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-State-Properties.png)

8.

Insert a new [TextButton](/docs/en-us/reference/engine/classes/TextButton)  into the [ScreenGui](/docs/en-us/reference/engine/classes/ScreenGui)  you previously [created and linked](#design-sheets) . When you hover over the button in the viewport, it should gradually brighten and rotate 5 degrees counterclockwise.

 ![Final styled state rule in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Result.png)

## [Style themes](#style-themes)[](#style-themes)

Style themes  consist of sets of specific tokens that can be swapped, for example color tokens that define a "light" and "dark" theme.

### [Theme creation](#theme-creation)[](#theme-creation)

For extensibility, themes are organized into folders. While a single folder may suffice for most purposes, you're free to organize themes in folders like "colors" or "fonts" if desired.

1.

Create a new theme folder:

1.

In the left column of the Style Editor, hover over Themes , click the ⊕ , and select New Theme .

2.

Rename the new Folder  item to General .

 ![New themes folder created in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-New-Folder.png)

2.

Create a new theme style sheet:

1.

Hover over the new General  folder, click the ⋮  button, and select New Theme StyleSheet .

2.

Rename it to ThemeA .

 ![New theme created in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-New-Theme.png)

### [Theme tokens](#theme-tokens)[](#theme-tokens)

Once a theme is constructed, you can link its tokens to various UI object properties such as the [BackgroundColor3](/docs/en-us/reference/engine/classes/TextButton#BackgroundColor3)  of a [TextButton](/docs/en-us/reference/engine/classes/TextButton) . Theme sheets must use a common set of tokens to work correctly.

With ThemeA  selected in the left column of the Style Editor:

1.

Link three previously created [style tokens](#style-tokens)  to three new theme tokens:

| Theme Token | | Style Token |
| BackColor | | $Gold |
| ButtonFont | | $Oswald |
| ButtonTextSize | | $Text32 |

1.

Click Add a Token…  in the main panel and enter the theme token's name.

2.

Click the $  which appears in the value field and select the associated style token.

 ![Theme configured with tokens in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-ThemeA-Tokens.png)

2.

In the left column of the Style Editor, select TextButton  in the UI Elements  branch.

 ![Default class style in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-New-Class.png)

3.

Link the theme's tokens to three new [TextButton](/docs/en-us/reference/engine/classes/TextButton)  properties:

| Property | | Theme Token |
| [BackgroundColor3](/docs/en-us/reference/engine/classes/TextButton#BackgroundColor3) | | $BackColor |
| [FontFace](/docs/en-us/reference/engine/classes/TextButton#FontFace) | | $ButtonFont |
| [TextSize](/docs/en-us/reference/engine/classes/TextButton#TextSize) | | $ButtonTextSize |

1.

Click Add a Property…  in the main panel and select the necessary property.

2.

Instead of entering a static value, click the ⋮  button and select Link Token .

3.

Click the $  which appears in the value field and select the proper theme token.

![Token linking workflow diagrammed in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-Theme-Configure.png)

When linking the theme's tokens, look for $[Token] in ThemeA  in the hover‑over to know the token is coming from the theme  and not from the global token sheet (remember that the theme already derives the global tokens).

 ![Class rule configured with theme tokens in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-Class-Tokens.png)

### [Theme duplication](#theme-duplication)[](#theme-duplication)

Once you have a theme generally established, you can duplicate  it and change various tokens to define a unique theme style.

1.

In the left column of the Style Editor, hover over the ThemeA  theme, click the ⋮  button, and select Duplicate .

2.

Rename the duplicated theme to ThemeB .

 ![Theme duplicated in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-Duplicated-Theme.png)

3.

Link two of the theme's tokens to two different style tokens:

| Theme Token | | Style Token |
| BackColor | | $Magenta |
| ButtonTextSize | | $Text24 |

1.

To the right of the property's value field, click the ⋮  button and select Unlink Token .

2.

Click ⋮  again and select Link Token .

3.

In its value field, click the $  and select the new associated style token.

 ![Theme configured with tokens in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-ThemeB-Tokens.png)

### [Theme swapping](#theme-swapping)[](#theme-swapping)

Once you have [multiple themes](#theme-duplication) , you can swap between them via the theme's folder, or via a script as outlined in [SetDerives()](/docs/en-us/reference/engine/classes/StyleSheet#SetDerives) .

1.

In the left column of the Style Editor, select the General  folder in the Themes  branch.

2.

In the main panel, swap between the themes using the radio buttons.

ThemeA ThemeB

![ThemeA swapped in the Style Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-Swapping-ThemeA.png)![](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Themes-ThemeA-Result.png)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
