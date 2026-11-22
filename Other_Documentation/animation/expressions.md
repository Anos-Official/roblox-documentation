<!-- Source: https://create.roblox.com/docs/animation/expressions -->

Graph Editor expressions | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/animation/expressions.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Animation](/docs/animation)
6. /
7. Create animations
8. /
9. [Graph Editor](/docs/animation/graph-editor)

# Graph Editor expressions

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/animation/expressions.md)

An expression  is a short Luau-like formula that reads graph parameters and returns a value, such as math.clamp((MovementSpeed + 0.5) / MaxSpeed, 0, 1) . Use expressions to drive a node property or a [state machine transition](/docs/animation/graph-editor-state-machine) . Expressions keep parameter transformations and animation decisions in your graph, close to the nodes they drive.

## [Prerequisites](#prerequisites)[](#prerequisites)

Before you create an expression, familiarize yourself with the [Animation Graph Editor](/docs/animation/graph-editor) , including how to [open it and create an animation graph](/docs/animation/graph-editor#build-a-graph) .

## [Create an expression](#create-an-expression)[](#create-an-expression)

This example uses an expression to drive the Position  property of an [Blend1DNode](/docs/reference/engine/enums/AnimationNodeType) . Configure the node with an idle animation at position 0 and a run animation at position 1. The expression converts the character's movement speed into the 0-to-1 range that the node uses to blend between those animations.

1.

Add MovementSpeed  and MaxSpeed  Number graph parameters.

 ![Parameters pane showing MovementSpeed and MaxSpeed Number parameters.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-expressions/Add-Parameters.png)

2.

Drag a connection from the Position  property pin of the [Blend1DNode](/docs/reference/engine/enums/AnimationNodeType)  and select New Expression .

 ![Animated demonstration of creating an Expression node from the Blend1D Position property pin.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-expressions/Add-Expression-Node.gif)

3.

Enter the following expression:

```

math.clamp(MovementSpeed / MaxSpeed, 0, 1)

```

 ![Animated demonstration of entering an expression in an Expression node.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-expressions/Edit-Expression.gif)

4.

Click outside the expression box to refresh it. As MovementSpeed  rises toward MaxSpeed , the [Blend1DNode](/docs/reference/engine/enums/AnimationNodeType)  receives a value from 0 to 1 and blends from the idle animation to the run animation.

After you load the graph onto an [AnimationTrack](/docs/reference/engine/classes/AnimationTrack) , update MovementSpeed  and MaxSpeed  from your gameplay script with [AnimationTrack:SetParameter()](/docs/reference/engine/classes/AnimationTrack#SetParameter) . The following example uses the [MoveDirection](/docs/reference/engine/classes/Humanoid#MoveDirection)  and [WalkSpeed](/docs/reference/engine/classes/Humanoid#WalkSpeed)  properties of a [Humanoid](/docs/reference/engine/classes/Humanoid) :

Script - Drive expression parameters

```

game:GetService("RunService").Stepped:Connect(function()

    animationTrack:SetParameter("MovementSpeed", humanoid.MoveDirection.Magnitude * humanoid.WalkSpeed)

    animationTrack:SetParameter("MaxSpeed", humanoid.WalkSpeed)

end)

```

The expression evaluates as the parameter values change. For the parameter workflow, see [API integration](/docs/animation/graph-editor#api-integration) .

## [What is supported](#what-is-supported)[](#what-is-supported)

Expression support includes arithmetic and comparison operations, logical and conditional expressions, calls to functions in the [math](/docs/reference/engine/libraries/math)  library, construction and member access for [CFrame](/docs/reference/engine/datatypes/CFrame) , [Vector2](/docs/reference/engine/datatypes/Vector2) , [Vector3](/docs/reference/engine/datatypes/Vector3) , and [Color3](/docs/reference/engine/datatypes/Color3)  values, and string concatenation. The following sections list the supported syntax and functions.

### [Arithmetic and comparisons](#arithmetic-and-comparisons)[](#arithmetic-and-comparisons)

Use standard arithmetic and comparison operations, with the usual order of operations. For example, //  divides and rounds down.

```

Speed * 2.0 + Offset

(Health / MaxHealth) * 100

DamageMultiplier ^ 2

Count % 3

10 // 3

Speed < 1

Health >= MaxHealth

```

Comparison operators work with numbers. Use ==  and ~=  to compare numbers, booleans, or strings.

### [Logic and short-circuiting](#logic-and-short-circuiting)[](#logic-and-short-circuiting)

and , or , and not  follow Luau truthiness and short-circuit evaluation. Only false  and nil  are considered false.

```

IsGrounded and GroundSpeed or AirSpeed

not IsDisabled

```

### [If-then-else expressions](#if-then-else-expressions)[](#if-then-else-expressions)

Use Luau's conditional expression form to branch within a single expression:

```

if Speed > 10 then "sprint" elseif Speed > 2 then "run" else "idle"

```

### [Math library](#math-library)[](#math-library)

Use the [math](/docs/reference/engine/libraries/math)  library. Graph expressions don't yet support [math.frexp()](/docs/reference/engine/libraries/math#frexp) , [math.noise()](/docs/reference/engine/libraries/math#noise) , or [math.randomseed()](/docs/reference/engine/libraries/math#randomseed) . [math.modf()](/docs/reference/engine/libraries/math#modf)  currently returns only the integer portion.

```

math.clamp(Speed / MaxSpeed, 0, 1)

math.sin(Time * 2 * math.pi)

math.atan2(Direction.Y, Direction.X)

math.max(A, B, C)

```

### [Vector construction and member access](#vector-construction-and-member-access)[](#vector-construction-and-member-access)

Construct [Vector2](/docs/reference/engine/datatypes/Vector2)  and [Vector3](/docs/reference/engine/datatypes/Vector3)  values, perform vector arithmetic, and access vector members such as Magnitude  and Unit .

```

Vector3.new(math.cos(Time), math.sin(Time), 0)

Vector2.new(InputX, InputY)

MoveDirection.Magnitude * 2.0

Position.X + Offset

Vector3.zero

```

### [Color3 construction and member access](#color3-construction-and-member-access)[](#color3-construction-and-member-access)

Construct [Color3](/docs/reference/engine/datatypes/Color3)  values and access their color channels.

```

Color3.fromRGB(255, 128, 0)

Color.R

```

### [CFrame construction, member access, and operations](#cframe-construction-member-access-and-operations)[](#cframe-construction-member-access-and-operations)

Construct [CFrame](/docs/reference/engine/datatypes/CFrame)  values, access CFrame members, and combine them with CFrames or [Vector3](/docs/reference/engine/datatypes/Vector3)  values.

```

CFrame.new(Position, LookAtPosition)

CFrame.Angles(RotationX, RotationY, RotationZ)

CFrame.identity

Transform.LookVector

Transform.Position + Vector3.new(0, 1, 0)

```

### [String concatenation](#string-concatenation)[](#string-concatenation)

Use ..  to concatenate two strings:

```

"state_" .. CurrentState

```

### [Local variables and multi-line expressions](#local-variables-and-multi-line-expressions)[](#local-variables-and-multi-line-expressions)

Use a multi-line expression to break a formula into named steps. A multi-line expression supports local  declarations, return , if / elseif / else , and standalone expressions. Inside an if  or else  body, use only return  or a standalone expression; nested if  statements and local declarations aren't supported.

```

local normalizedSpeed = Speed / MaxSpeed

local eased = math.clamp(normalizedSpeed, 0, 1)

return eased

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
