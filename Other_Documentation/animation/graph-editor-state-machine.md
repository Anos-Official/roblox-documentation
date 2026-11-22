<!-- Source: https://create.roblox.com/docs/animation/graph-editor-state-machine -->

Graph Editor state machines | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/animation/graph-editor-state-machine.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Animation](/docs/animation)
6. /
7. Create animations
8. /
9. [Graph Editor](/docs/animation/graph-editor)

# Graph Editor state machines

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/animation/graph-editor-state-machine.md)

A state machine  combines animation nodes into named states, such as Idle , Walk , Run , and Jump . It plays the active state and blends to another state when a transition condition evaluates to true . Use a state machine to define which animations can follow each other without writing transition logic in Luau.

Each state connects to an input on the state machine. A state can be a clip, a blend node, or another state machine. The state machine outputs the active animation pose or a blend between two poses if transitioning, which you connect to the next node in the graph.

## [Prerequisites](#prerequisites)[](#prerequisites)

Before you create a state machine, familiarize yourself with the [Animation Graph Editor](/docs/animation/graph-editor) , including how to [open it and create an animation graph](/docs/animation/graph-editor#build-a-graph) .

## [Create a state machine](#create-a-state-machine)[](#create-a-state-machine)

The following example uses three states from JumpFallLandRunExample : Locomotion , Fall , and LandIdle . The character moves normally, switches to a falling animation when airborne, and plays a landing animation before returning to locomotion. These steps focus on the state machine; start with animation nodes for locomotion, falling, and landing.

1.

In the Graph Editor , right-click and select Insert Node  ⟩ State Machine .

 ![Graph Editor context menu with the Insert Node submenu open and State Machine selected.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-state-machine/Insert-State-Machine.png)

2.

On the state machine node, click Open . In the State Machine  view, use Create State  to add three states named Locomotion , Fall , and LandIdle .

 ![State Machine view with the Create State button and Entry and Any state nodes.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-state-machine/Add-A-State.png)

3.

Click Back to Graph  and connect your animation nodes to the corresponding state machine inputs:

-

Locomotion : Connect your locomotion animation. The reference graph uses an [Blend1DNode](/docs/reference/engine/enums/AnimationNodeType)  named IdleRunBlend  to blend idle and running animations based on Speed .

-

Fall : Connect a falling [ClipNode](/docs/reference/engine/enums/AnimationNodeType)  and set Play Mode  to Enum.AnimationNodePlayMode|OnceAndHold , so it holds its final pose until the character lands.

-

LandIdle : Connect a landing clip and set Play Mode  to Enum.AnimationNodePlayMode|OnceAndHold , so it can finish and transition back to locomotion.

Connect the state machine output to the Pose  input of Graph Output .

 ![IdleRunBlend, Fall, and LandIdle nodes connected to the Locomotion, Fall, and LandIdle inputs of a State Machine node, whose output connects to Graph Output.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-state-machine/Wire-Nodes-To-State-Machine.png)

4.

Open the State Machine  view again and drag a transition from (Entry)  to Locomotion . The state machine starts in this state when the graph starts.

 ![Entry node connected to the Locomotion state.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-state-machine/Entry-State-To-Locomotion.png)

5.

Add a Boolean graph parameter named Grounded  and set it to true . This parameter indicates whether the character is on the ground.

6.

Add the following transitions by dragging a connection from the source state to the destination state, then configure each transition:

-

Locomotion  to Fall : Set Wait For  to [Expression](/docs/animation/expressions) , Expression  to not Grounded , and Length  to 0.2  seconds. The falling animation begins when the character leaves the ground.

-

Fall  to LandIdle : Set Wait For  to Expression , Expression  to Grounded , and Length  to 0.1  seconds. The landing animation begins when the character touches the ground.

-

LandIdle  to Locomotion : Set Wait For  to Finished , When  to Enum.AnimationNodeTransitionWhen|BeforeFinished , and Length  to 0.2  seconds. The state machine begins blending back to locomotion during the final 0.2 seconds of the landing animation.

 ![Transition settings for LandIdle to Locomotion, with Length set to 0.2, Curve to Linear, Wait For to Finished, and When to Before Finished.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-state-machine/Transition-Settings.png)

7.

Leave Curve  as the default ([Linear](/docs/reference/engine/enums/PoseEasingStyle) ) for all three transitions. Preview the graph and change Grounded  to false  to enter Fall , then back to true  to play LandIdle  and return to Locomotion .

8.

Update Grounded  from your gameplay code as the character leaves and touches the ground. If your locomotion blend uses Speed , update that parameter as the character moves. For the parameter workflow, see [API integration](/docs/animation/graph-editor#api-integration) .

9.

Extend the state machine with jumping and additional landing states to create the full movement graph. JumpFallLandRunExample  includes separate jumps for standing and running, plus different landings based on movement and fall speed.

For the full state machine, open JumpFallLandRunExample  in the [reference place](https://www.roblox.com/games/116845448376632) .

## [State machine properties](#state-machine-properties)[](#state-machine-properties)

### [State machine node properties](#state-machine-node-properties)[](#state-machine-node-properties)

Inputs

-

State1...StateN : The animation nodes that define each state. The name of the state must match the name of the input to the state machine node.

Properties

| Property | | Type | | Description |
| --- | --- |
| EntryState | | [ObjectValue](/docs/reference/engine/classes/ObjectValue) | | An [ObjectValue](/docs/reference/engine/classes/ObjectValue)  whose [Value](/docs/reference/engine/classes/ObjectValue#Value)  points to the [AnimationNodeDefinition](/docs/reference/engine/classes/AnimationNodeDefinition)  for the state that is active when the graph starts. |

Event data

-

Event Handling:  Events from the active state pass through with their weight unchanged.

-

Event Emission:  Passes through events from the active state only. During a transition, event emission follows the [global event rules](/docs/animation/graph-editor#global-event-rules) .

### [Transition properties](#transition-properties)[](#transition-properties)

A transition has one or more source states, a destination state, and a condition. When the active state matches a source state, the state machine checks the condition. It blends to the destination state when the condition evaluates to true .

Wait For  determines the transition condition UI. Select [Expression](/docs/animation/expressions)  (Enum.AnimationNodeWaitFor|Trigger ) to display an Expression  box. An Expression  can reference a boolean graph parameter directly, such as ShouldJump , or evaluate a condition, such as Speed >= 12 . Select Finished  (Enum.AnimationNodeWaitFor|Finished ) to display the When  dropdown.

If more than one transition has a true Expression , the state machine evaluates the transition with the highest Priority  value first. When priorities are the same, it selects one transition at random. Assign different priorities to competing transitions to make the result predictable.

| Property | | Type | | Description |
| From | | [ObjectValue](/docs/reference/engine/classes/ObjectValue) | | An [ObjectValue](/docs/reference/engine/classes/ObjectValue)  whose [Value](/docs/reference/engine/classes/ObjectValue#Value)  points to the [AnimationNodeDefinition](/docs/reference/engine/classes/AnimationNodeDefinition)  for the state that can begin the transition. Leave this property unset for an (Any)  transition. |
| To | | [ObjectValue](/docs/reference/engine/classes/ObjectValue) | | An [ObjectValue](/docs/reference/engine/classes/ObjectValue)  whose [Value](/docs/reference/engine/classes/ObjectValue#Value)  points to the [AnimationNodeDefinition](/docs/reference/engine/classes/AnimationNodeDefinition)  for the destination state. |
| WaitFor | | Enum.AnimationNodeWaitFor | | Determines which transition condition UI appears. Enum.AnimationNodeWaitFor|Trigger  displays the Expression  box. Enum.AnimationNodeWaitFor|Finished  displays the When  dropdown. |
| When | | Enum.AnimationNodeTransitionWhen | | Available when Wait For  is Finished . Select Enum.AnimationNodeTransitionWhen|Finished  to begin after the source state finishes, or Enum.AnimationNodeTransitionWhen|BeforeFinished  to begin blending one Duration  before the source state finishes. |
| Expression | | String | | Available when Wait For  is [Expression](/docs/animation/expressions) . A boolean graph parameter or expression that, when it evaluates to true , begins the transition. See [Expression](/docs/animation/expressions)  for what's supported. |
| Priority | | Number | | The order used when more than one Expression  is true. Higher values take precedence. Valid values range from 0 to 65,535. |
| Duration | | Number | | The time, in seconds, to blend into the destination state. The default is 0.15 seconds. |
| Curve | | [Enum.PoseEasingStyle](/docs/reference/engine/enums/PoseEasingStyle) | | The easing used during the blend. Only [Linear](/docs/reference/engine/enums/PoseEasingStyle)  and [CubicV2](/docs/reference/engine/enums/PoseEasingStyle)  are supported. The default is [Linear](/docs/reference/engine/enums/PoseEasingStyle) . |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
