<!-- Source: https://create.roblox.com/docs/en-us/animation/events -->

Animation events | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/animation/events.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Animation](/docs/en-us/animation)
6. /
7. Create animations
8. /
9. [Animation Editor](/docs/en-us/animation/editor)

# Animation events

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/animation/events.md)

You can define animation event markers  across the timeline span and use [GetMarkerReachedSignal()](/docs/en-us/reference/engine/classes/AnimationTrack#GetMarkerReachedSignal)  to detect those markers as the animation runs.

By default, the event track isn't visible. To show the event track:

1.

Navigate to the right of the timeline and click the settings icon. A pop-up menu displays.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Timeline-Options-Menu.png)

2.

Select Show Animation Events . This opens the Animation Events  bar directly below the media and playback controls.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Animation-Events-Bar.png)

## [Create events](#create-events)[](#create-events)

Event markers are visual indicators of where an animation event begins. After you create an event marker, you can move it to any frame position on the timeline.

To create a new event marker:

1.

Navigate to the timeline, then click-and-drag the scrubber to the frame position where the event should occur.

2.

Navigate to the event track , then click the Edit Animation Events  button.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Animation-Events-Edit-Button.png)

3.

In the dialog, click + Add Event , then enter an event name.

4.

OPTIONAL

 In the Parameter  field, enter a parameter string for the event.

5.

Click the Save  button. In the events bar within the timeline, a new marker symbol displays at the frame position.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Animation-Events-Marker-In-Timeline.png)

## [Detect events](#detect-events)[](#detect-events)

To detect animation events in a [LocalScript](/docs/en-us/reference/engine/classes/LocalScript) , connect a function to the [GetMarkerReachedSignal()](/docs/en-us/reference/engine/classes/AnimationTrack#GetMarkerReachedSignal)  function of [AnimationTrack](/docs/en-us/reference/engine/classes/AnimationTrack) . For example:

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

local humanoid = character:WaitForChild("Humanoid")

local animator = humanoid:WaitForChild("Animator")

-- Create new "Animation" instance

local walkAnim = Instance.new("Animation")

-- Set its "AnimationId" to the corresponding animation asset ID

walkAnim.AnimationId = "rbxassetid://5432167890"

-- Load animation onto the animator

local walkAnimTrack = animator:LoadAnimation(walkAnim)

-- Connect "GetMarkerReachedSignal" event to a specific named keyframe

walkAnimTrack:GetMarkerReachedSignal("FootStep"):Connect(function(paramString)

	print(paramString)

end)

```

You can specify a Parameter  value for any event marker within the animation editor. This lets you pass a custom string  (single value, comma-separated string, etc.) to the [GetMarkerReachedSignal()](/docs/en-us/reference/engine/classes/AnimationTrack#GetMarkerReachedSignal)  method, as illustrated by the paramString  argument in the code example above. This string can then be parsed or converted, if necessary, and used for whatever action you wish to perform in the event.

## [Duplicate events](#duplicate-events)[](#duplicate-events)

As you create events, they become available for usage throughout the whole animation, not only at the frame position where you originally created them. For instance, you can create a FootStep  event marker at the point where a character's left  foot touches down, then use the same event when the character's right  foot touches down.

To duplicate an event:

1.

Right-click an event marker  in the event bar, then select Copy Selected  from the contextual menu.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Animation-Events-Marker-In-Timeline.png)

2.

Right-click at another time along the timeline and select Paste Events . The copied event inserts at the time position closest to where you click.

3.

OPTIONAL

 If the original event uses a parameter  but the duplicated event should use a modified parameter, perform the following steps:

1.

Right-click the duplicated event marker and select Edit Animation Event  from the contextual menu. The Edit Animation Events  dialog displays.

2.

Make your changes and click the Save  button.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
