<!-- Source: https://create.roblox.com/docs/en-us/ui/proximity-prompts -->

Proximity prompts | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/ui/proximity-prompts.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [User interface](/docs/en-us/ui)
6. /
7. UI objects

# Proximity prompts

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/ui/proximity-prompts.md)

[ProximityPrompt](/docs/en-us/reference/engine/classes/ProximityPrompt)  objects encourage user interaction to trigger an action when they approach in-game objects such as doors, light switches, and buttons. Using this object, you can:

-

Indicate what objects a user can interact with in the game.

-

Display the action a user can take on the object, then trigger the action through user input such as pressing or holding a key.

-

Display the correct input for all input types, such a keyboard, gamepad, and touchscreen keys.

See the [Dungeon Delve](https://www.roblox.com/games/6074153281/Dungeon-Delve)  sample place for the fully working proximity prompt examples shown in the video above.

## [Create proximity prompts](#create-proximity-prompts)[](#create-proximity-prompts)

You must parent proximity prompts to the part, model, or attachment that you want a user to interact with. To add a proximity prompt to a [BasePart](/docs/en-us/reference/engine/classes/BasePart) , [Model](/docs/en-us/reference/engine/classes/Model) , or [Attachment](/docs/en-us/reference/engine/classes/Attachment)  object:

1.

In the [Explorer](/docs/en-us/studio/explorer)  window, hover over the [BasePart](/docs/en-us/reference/engine/classes/BasePart) , [Model](/docs/en-us/reference/engine/classes/Model) , or [Attachment](/docs/en-us/reference/engine/classes/Attachment)  and click the ⊕ button. A contextual menu displays.

2.

From the menu, insert a ProximityPrompt .

 ![Explorer hierarchy showing a ProximityPrompt parented to an Attachment](https://prod.docsiteassets.roblox.com/assets/ui/proximity-prompt/ProximityPrompt-New.png)

## [Customize proximity prompts](#customize-proximity-prompts)[](#customize-proximity-prompts)

You can customize a proximity prompt based on how you want it to [appear](#appearance) , when you want it to be [visible](#visibility) , and what you want a user to do to [trigger the action](#interactivity) .

### [Appearance](#appearance)[](#appearance)

Proximity prompts need to communicate three things:

-

The object  that a user can interact with.

-

The action  that triggers when they interact with the proximity prompt.

-

The key  that a user must press or hold.

You can specify these through the following properties:

-

[ObjectText](/docs/en-us/reference/engine/classes/ProximityPrompt#ObjectText)  An optional name for the object a user can interact with.

-

[ActionText](/docs/en-us/reference/engine/classes/ProximityPrompt#ActionText)  An optional name for the action a user will trigger.

-

[KeyboardKeyCode](/docs/en-us/reference/engine/classes/ProximityPrompt#KeyboardKeyCode)  The keyboard key a user must press or hold to trigger the action.

-

[GamepadKeyCode](/docs/en-us/reference/engine/classes/ProximityPrompt#GamepadKeyCode)  The gamepad key a user must press or hold to trigger the action.

 ![Diagram indicating basic elements of a ProximityPrompt](https://prod.docsiteassets.roblox.com/assets/ui/proximity-prompt/Prompt-Diagram.png)

### [Visibility](#visibility)[](#visibility)

You can control when the proximity prompt is visible through its [MaxActivationDistance](/docs/en-us/reference/engine/classes/ProximityPrompt#MaxActivationDistance) , [RequiresLineOfSight](/docs/en-us/reference/engine/classes/ProximityPrompt#RequiresLineOfSight) , and [Exclusivity](/docs/en-us/reference/engine/classes/ProximityPrompt#Exclusivity)  properties.

#### [MaxActivationDistance](#maxactivationdistance)[](#maxactivationdistance)

The [MaxActivationDistance](/docs/en-us/reference/engine/classes/ProximityPrompt#MaxActivationDistance)  property allows you to define the range from around the [ProximityPrompt](/docs/en-us/reference/engine/classes/ProximityPrompt)  object that activates the visibility of the proximity prompt. Once a user's character enters that range, the proximity prompt becomes visible.

 ![Diagram indicating how a character's distance from a ProximityPrompt object affects whether the prompt appears on screen](https://prod.docsiteassets.roblox.com/assets/ui/proximity-prompt/MaxActivationDistance.jpg)

#### [RequiresLineOfSight](#requireslineofsight)[](#requireslineofsight)

The [RequiresLineOfSight](/docs/en-us/reference/engine/classes/ProximityPrompt#RequiresLineOfSight)  property activates the visibility of the proximity prompt when there's a clear path from the camera  to the [ProximityPrompt](/docs/en-us/reference/engine/classes/ProximityPrompt)  object. By default, this property is set to true.

#### [Exclusivity](#exclusivity)[](#exclusivity)

If a user's character is within range of multiple proximity prompts, each proximity prompt's visibility depends on which proximity prompt the camera is pointing at, as well as each proximity prompt's [Exclusivity](/docs/en-us/reference/engine/classes/ProximityPrompt)  property value.

OnePerButton OneGlobally AlwaysShow

![ProximityPrompt objects set to exclusivity of OnePerButton](https://prod.docsiteassets.roblox.com/assets/ui/proximity-prompt/Exclusivity-OnePerButton.jpg) Only one proximity prompt is visible per input keycode. If multiple in-range proximity prompts use different keycodes, they are all visible. However, if multiple in-range proximity prompts use the same keycode, only one proximity prompt is visible at any given time, depending on the camera's view direction.

### [Interactivity](#interactivity)[](#interactivity)

You can customize how a user interacts with a proximity prompt through its [HoldDuration](/docs/en-us/reference/engine/classes/ProximityPrompt#HoldDuration)  and [ClickablePrompt](/docs/en-us/reference/engine/classes/ProximityPrompt#ClickablePrompt)  properties.

#### [HoldDuration](#holdduration)[](#holdduration)

The [HoldDuration](/docs/en-us/reference/engine/classes/ProximityPrompt#HoldDuration)  property determines how many seconds a user has to press a key before the proximity prompt's action triggers. If this property has a value of 0 , the proximity prompt's action triggers immediately.

#### [ClickablePrompt](#clickableprompt)[](#clickableprompt)

The [ClickablePrompt](/docs/en-us/reference/engine/classes/ProximityPrompt#ClickablePrompt)  property specifies if a user can click on a proximity prompt to trigger its action. When set to true , a user can interact with the proximity prompt by directly clicking the proximity prompt or  by pressing the specified key. When set to false , a user can only interact with the proximity prompt by pressing the specified key.

Note that if a user is using a phone or a tablet, they can always interact with the proximity prompt by directly clicking the proximity prompt regardless of the [ClickablePrompt](/docs/en-us/reference/engine/classes/ProximityPrompt#ClickablePrompt)  property's value.

## [Script proximity prompts](#script-proximity-prompts)[](#script-proximity-prompts)

You can connect to proximity prompt events either on the [ProximityPrompt](/docs/en-us/reference/engine/classes/ProximityPrompt)  object itself or globally through [ProximityPromptService](/docs/en-us/reference/engine/classes/ProximityPromptService) . The [ProximityPromptService](/docs/en-us/reference/engine/classes/ProximityPromptService)  allows you to manage all proximity prompt behavior from one location, preventing any need for duplicate code in your game.

| Event | | Description |
| --- | --- |
| [PromptTriggered](/docs/en-us/reference/engine/classes/ProximityPromptService#PromptTriggered) | | Fires when a player interacts with a proximity prompt (after the duration for a prompt with non-zero [HoldDuration](/docs/en-us/reference/engine/classes/ProximityPrompt#HoldDuration) ). |
| [PromptTriggerEnded](/docs/en-us/reference/engine/classes/ProximityPromptService#PromptTriggerEnded) | | Triggers when the player stops interacting with a proximity prompt. |
| [PromptButtonHoldBegan](/docs/en-us/reference/engine/classes/ProximityPromptService#PromptButtonHoldBegan) | | Fires when a player begins interacting with a proximity prompt with a non-zero [HoldDuration](/docs/en-us/reference/engine/classes/ProximityPrompt#HoldDuration)  value. |
| [PromptButtonHoldEnded](/docs/en-us/reference/engine/classes/ProximityPromptService#PromptButtonHoldEnded) | | Fires when a player stops interacting with a proximity prompt with a non-zero [HoldDuration](/docs/en-us/reference/engine/classes/ProximityPrompt#HoldDuration)  value. |
| [PromptShown](/docs/en-us/reference/engine/classes/ProximityPromptService#PromptShown) | | Triggers in [LocalScripts](/docs/en-us/reference/engine/classes/LocalScript)  when a proximity prompt is made visible. |
| [PromptHidden](/docs/en-us/reference/engine/classes/ProximityPromptService#PromptHidden) | | Triggers in [LocalScripts](/docs/en-us/reference/engine/classes/LocalScript)  when a prompt is hidden. |

The following code sample includes a basic framework for using [ProximityPromptService](/docs/en-us/reference/engine/classes/ProximityPromptService) :

```

local ProximityPromptService = game:GetService("ProximityPromptService")

-- Detect when prompt is triggered

local function onPromptTriggered(promptObject, player)

end

-- Detect when prompt hold begins

local function onPromptHoldBegan(promptObject, player)

end

-- Detect when prompt hold ends

local function onPromptHoldEnded(promptObject, player)

end

-- Connect prompt events to handling functions

ProximityPromptService.PromptTriggered:Connect(onPromptTriggered)

ProximityPromptService.PromptButtonHoldBegan:Connect(onPromptHoldBegan)

ProximityPromptService.PromptButtonHoldEnded:Connect(onPromptHoldEnded)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
