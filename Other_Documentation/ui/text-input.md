<!-- Source: https://create.roblox.com/docs/ui/text-input -->

Text input fields | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/text-input.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/ui)
6. /
7. UI objects

# Text input fields

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/text-input.md)

A [TextBox](/docs/reference/engine/classes/TextBox)  is a rectangle that allows a user to provide text input while it's in focus. When you [script](#script-text-inputs)  a [TextBox](/docs/reference/engine/classes/TextBox) , you can use it as a search bar or an input field on a form. To help users know what type of text they should input, you can also provide a prompt through the [PlaceholderText](/docs/reference/engine/classes/TextBox#PlaceholderText)  property.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/TextBox-Example.jpg)

Because these objects are [GuiObjects](/docs/reference/engine/classes/GuiObject) , you can customize properties such as [BackgroundColor3](/docs/reference/engine/classes/GuiObject#BackgroundColor3) , [BorderMode](/docs/reference/engine/classes/GuiObject#BorderMode) , [Transparency](/docs/reference/engine/classes/GuiObject#Transparency) , and [Rotation](/docs/reference/engine/classes/GuiObject#Rotation)  to fit the aesthetics of your game.

## [Create text inputs on the screen](#create-text-inputs-on-the-screen)[](#create-text-inputs-on-the-screen)

A [TextBox](/docs/reference/engine/classes/TextBox)  on a screen is useful for things like an input field for a form.

To add a [TextBox](/docs/reference/engine/classes/TextBox)  to a screen:

1.

In the Explorer  window, select StarterGui  and add a ScreenGui .

1.

Hover over StarterGui and click the ⊕ button. A contextual menu displays.

2.

Insert a ScreenGui .

2.

Select the new ScreenGui  and add a TextBox .

1.

Hover over ScreenGui  and click the ⊕ button. A contextual menu displays.

2.

Insert a TextBox .

## [Create text inputs on part faces](#create-text-inputs-on-part-faces)[](#create-text-inputs-on-part-faces)

To add a [TextBox](/docs/reference/engine/classes/TextBox)  to the face of a part:

1.

In the Explorer  window, select StarterGui  and add a SurfaceGui .

1.

Hover over StarterGui and click the ⊕ button. A contextual menu displays.

2.

Insert a ScreenGui .

2.

Select the new SurfaceGui  and add a TextBox .

1.

Hover over SurfaceGui  and click the ⊕ button. A contextual menu displays.

2.

Insert a TextBox .

3.

Adorn the SurfaceGui  to the part  on which you want to display the TextBox .

1.

In the Properties  window, select the Adornee  property. Your cursor changes.

2.

In the Explorer  window, select the part.

If you don't see the [TextBox](/docs/reference/engine/classes/TextBox) , try [choosing a different face](/docs/parts/textures-decals#choose-a-face)  in the ** Face**  property of the ** SurfaceGui** .

## [Script text inputs](#script-text-inputs)[](#script-text-inputs)

Like [buttons](/docs/ui/buttons) , you can script any action for a [TextBox](/docs/reference/engine/classes/TextBox)  object when a user interacts with it. For example, the following script connects the [FocusLost](/docs/reference/engine/classes/TextBox#FocusLost)  event which fires when the user presses the Enter  button or clicks outside the box. If enterPressed  is true , meaning the user submitted the input instead of merely clicking outside the box, the script prints the contents of the entry to the [Output](/docs/studio/output)  window.

Basic Text Input Handling

```

local textBox = script.Parent

local function onFocusLost(enterPressed, inputObject)

	if enterPressed then

		print(textBox.Text)

	end

end

textBox.FocusLost:Connect(onFocusLost)

```

As another example, you might want to allow only numbers in a [TextBox](/docs/reference/engine/classes/TextBox) . The following code uses the [TextBox.GetPropertyChangedSignal](/docs/reference/engine/classes/TextBox#GetPropertyChangedSignal)  event to detect when the [TextBox.Text](/docs/reference/engine/classes/TextBox#Text)  changes, such as when a user starts typing, then it uses the [string.gsub()](/docs/reference/engine/libraries/string#gsub)  function to disallow non‑numbers.

Restricting Text Input to Numbers

```

local textBox = script.Parent

local function allowOnlyNumbers()

	textBox.Text = string.gsub(textBox.Text, "%D", "")

end

textBox:GetPropertyChangedSignal("Text"):Connect(allowOnlyNumbers)

```

## [Text filtering](#text-filtering)[](#text-filtering)

Applied to various sources and inputs, [text filtering](/docs/ui/text-filtering)  prevents users from seeing inappropriate language and personally identifiable information such as phone numbers. Roblox automatically filters common text outputs such as messages that have passed through [in-game text chat](/docs/chat/in-experience-text-chat) , but you are responsible for filtering any displayed text that you don't have explicit control over , including characters/strings that users input through text inputs .

Because filtering is crucial for a safe environment, Roblox actively moderates the content of games to make sure they meet [community standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) . If Roblox receives reports or automatically detects that your game doesn't apply text filtering, then the system removes the game until you add filtering.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
