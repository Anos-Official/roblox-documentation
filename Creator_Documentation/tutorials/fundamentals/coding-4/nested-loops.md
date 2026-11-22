<!-- Source: https://create.roblox.com/docs/en-us/tutorials/fundamentals/coding-4/nested-loops -->

Nested loops | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/tutorials/fundamentals/coding-4/nested-loops.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Tutorials](/docs/en-us/tutorials)
4. /
5. [Loops](/docs/en-us/tutorials/fundamentals/coding-4/landing)

# Nested loops

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/tutorials/fundamentals/coding-4/nested-loops.md)

Nesting loops allows you to repeat tasks in batches. For example, baking three batches of six cupcakes, or assigning weapons to players on two teams.

## [How nested loops run](#how-nested-loops-run)[](#how-nested-loops-run)

When loops are nested, scripts go line by line until it reaches the next loop. The inner loop will run until it's condition is met before returning to the outer loop.

### [Nested loop logic](#nested-loop-logic)[](#nested-loop-logic)

The following diagram shows the steps a loop takes.

|
-

Outer loop: code runs line-by-line until it reaches the inner loop.

-

Outer loop: code runs line-by-line until it reaches the inner loop.

-

Outer loop: code runs line-by-line until it reaches the inner loop.

 | | ![](https://prod.docsiteassets.roblox.com/assets/education/coding-4/NestedLoopsDiagram300x500.png) |
| --- | --- |

### [Nested loop example](#nested-loop-example)[](#nested-loop-example)

Nested loops can seem somewhat abstract, so a visual example can help. For this exercise, copy and paste a sample script and run it in Studio. This script will create towers of parts. The outer loop will control how many parts to make, while the inner loop will create the actual batch.

1.

Create a new script in ServerScriptService  named PartMaker. Copy the code below.

```

local numberOfBatches = 7

local partsPerBatch = 5

local partsMade = 0

-- Makes a single cube

local function createPart()

  local part = Instance.new("Part")

  part.Size = Vector3.new(2, 2, 2)

  part.CFrame = CFrame.new(20, 0, 20)

  part.Color = currentColor

  part.Parent = workspace

end

-- Outer loop

for partBatch = 1, numberOfBatches do

  print("Top outer loop: part batch " .. partBatch)

  currentColor = Color3.fromRGB(math.random(0, 255), math.random(0, 255), math.random(0, 255))

  -- Inner loop

  for partNumber = 1, partsPerBatch do

    createPart()

    print("Inner loop: part " .. partNumber)

    partsMade += 1

    task.wait(0.5)

  end

  print("Bottom outer loop: " .. partsMade .. " parts made so far.")

  task.wait(2)

end

```

2.

Watch as the script spawns a different batch of colored parts. After going through one batch, it'll pause for 2 seconds. The print statement in the outer loop will run only one time per completed inner loop.

## [Nested for loop tower](#nested-for-loop-tower)[](#nested-for-loop-tower)

Each loop has its own set of code, so can be responsible for different tasks. One thing nested loops can do is change the placement of where an object spawns to create a tower like the one in this video. There's three different loops, one each for controlling where along the width, length, and height of the tower the cube spawns.

## [Code a cube maker script](#code-a-cube-maker-script)[](#code-a-cube-maker-script)

To practice nested loops, you'll make a script that creates a tower of cubes. For the cube tower script, first code a function that spawns a single cube. The tower will be built by repeatedly calling this function.

### [Set up the script](#set-up-the-script)[](#set-up-the-script)

For the cube tower script, first code a function that spawns a single cube. The tower will be built by repeatedly calling this function.

1.

Delete  the PartMaker script or disable it (in the script properties, check Disabled). If you don't, there will be two scripts making parts at the same time in the same place.

2.

Create a new script named TowerBuilder. Add variables for tower size and cube size at the top.

```

local TOWER_SIZE = 4

local CUBE_SIZE = 2

```

Notice how the variables above are all capitalized. These are called constants , or variables that don't change. To set them apart from variables that will be changed within the script, type them using capitals and underscores.

3.

Add a local function named makeCube()  that creates a single square cube using CUBE_SIZE .

```

local TOWER_SIZE = 4

local CUBE_SIZE = 2

-- Creates individual cubes

local function makeCube()

  local cube = Instance.new("Part")

  cube.Size = Vector3.new(CUBE_SIZE, CUBE_SIZE, CUBE_SIZE)

end

```

4.

Set the cube's color to a variable which will be updated in the nested loops.

```

local function makeCube()

  local cube = Instance.new("Part")

  cube.Size = Vector3.new(CUBE_SIZE, CUBE_SIZE, CUBE_SIZE)

  cube.Color = currentColor

end

```

5.

Lastly, parent  the new cube to the workspace so it appears.

```

local function makeCube()

    local cube = Instance.new("Part")

    cube.Size = Vector3.new(CUBE_SIZE, CUBE_SIZE, CUBE_SIZE)

    cube.Color = currentColor

    cube.Parent = workspace

end

```

In Roblox code, once an object is created by script, it's recommended to parent it at the end. It's faster to make changes to an instance before there is a physical object in the 3D world.

### [Spawn in different directions](#spawn-in-different-directions)[](#spawn-in-different-directions)

To create a tower, spawn cubes at specific points by setting the X, Y, Z properties of each new cube. X and Z are side to side. Y is up and down.

1.

In makeCube() , add parameters for spawnX , spawnY , and spawnZ . These numbers will set each new cube's spawn location.

```

-- Creates individual cubes

local function makeCube(spawnX, spawnY, spawnZ)

    local cube = Instance.new("Part")

    cube.Size = Vector3.new(CUBE_SIZE, CUBE_SIZE, CUBE_SIZE)

    cube.Color = currentColor

    cube.Parent = workspace

end

```

2.

Inside the function, set the cube's CFrame property to a new CFrame using the spawnX , spawnY , spawnZ  parameters.

```

local function makeCube(spawnX, spawnY, spawnZ)

    local cube = Instance.new("Part")

    cube.Size = Vector3.new(CUBE_SIZE, CUBE_SIZE, CUBE_SIZE)

    cube.Color = currentColor

    cube.CFrame = CFrame.new(spawnX, spawnY, spawnZ)

    cube.Parent = workspace

end

```

In Roblox, CFrame is a data type used to store 3D position and orientation. It's used to place objects in a world.

### [Spawn with nested loops](#spawn-with-nested-loops)[](#spawn-with-nested-loops)

The script will have three loops total, one each for the length, width, and height of the tower. To complete an entire floor before moving upwards, start with setting the Y coordinate in the first, outermost loop.

1.

Under the makeCube()  function, Create a for loop to set how high  each cube spawns.

-

Control variable : heightIndex = 1

-

End point : TOWER_SIZE

-

Inside the loop, add: local spawnY = (heightIndex - 1) * CUBE_SIZE

```

-- Builds tower

for heightIndex = 1, TOWER_SIZE do

    local spawnY = (heightIndex - 1) * CUBE_SIZE

end

```

The calculation for spawnY  makes sure the first cube spawns at ground height and then moves over the space of a single cube every time. Ground level is at 0, which is why 1 needs to be subtracted from the heightIndex .

2.

With the first loop for height finished, start on the second. Inside the first for loop, add a new for loop for where to place the cube along the length of the tower.

-

Control variable : lengthIndex = 1

-

End point : TOWER_SIZE

-

Inside that loop add: local spawnX = lengthIndex * CUBE_SIZE

```

for heightIndex = 1, TOWER_SIZE do

    local spawnY = (heightIndex - 1) * CUBE_SIZE

    for lengthIndex = 1, TOWER_SIZE do

        local spawnX = lengthIndex * CUBE_SIZE

    end

end

```

When working with nested loops, it's important to make sure code is well indented. This helps make your code readable and organized.

3.

Inside the second  loop, add a third  for loop for the tower width . In this final loop, call makeCube()  and pass in the X,Y, Z parameters.

-

Control variable : widthIndex = 1

-

End point : TOWER_SIZE

-

Inside the loop add:

-

local spawnZ = widthIndex * CUBE_SIZE

-

makeCube(spawnX, spawnY, spawnZ)

-

A wait time of 0.25 so you can watch the tower be built.

```

-- Builds tower

for heightIndex = 1, TOWER_SIZE do

    local spawnY = (heightIndex - 1) * CUBE_SIZE

    for lengthIndex = 1, TOWER_SIZE do

        local spawnX = lengthIndex * CUBE_SIZE

        for widthIndex = 1, TOWER_SIZE do

            local spawnZ = widthIndex * CUBE_SIZE

            makeCube(spawnX, spawnY, spawnZ)

            task.wait(0.25)

        end

    end

end

```

4.

To have each floor be a random color, change currentColor  to random RGB  numbers in the same loop in which you create a new floor.

```

for heightIndex = 1, TOWER_SIZE do

    local spawnY = (heightIndex - 1) * CUBE_SIZE

    currentColor = Color3.fromRGB(math.random(0, 255), math.random(0, 255), math.random(0, 255))

    for lengthIndex = 1, TOWER_SIZE do

        local spawnX = lengthIndex * CUBE_SIZE

        for widthIndex = 1, TOWER_SIZE do

            local spawnZ = widthIndex * CUBE_SIZE

            makeCube(spawnX, spawnY, spawnZ)

            task.wait(0.25)

        end

    end

end

```

5.

Run the project and wait to see that a full tower has been created without any errors in the Output window.

## [Optional challenges](#optional-challenges)[](#optional-challenges)

Below are different self-directed challenges that use nested loops in different ways. Try and code on your own before looking at the solution.

### [Fade away parts](#fade-away-parts)[](#fade-away-parts)

As the tower is built, have the parts fade in transparency from left to right.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-4/Fade_480x320.png)

The code solution is below.

```

local TOWER_SIZE = 6

local CUBE_SIZE = 2

-- Creates individual cubes

local function makeCube(spawnX, spawnY, spawnZ)

    local cube = Instance.new("Part")

    cube.Size = Vector3.new(CUBE_SIZE, CUBE_SIZE, CUBE_SIZE)

    cube.Color = currentColor

    cube.Transparency = cubeTransparency -- Sets transparency

    cube.CFrame = CFrame.new(spawnX, spawnY, spawnZ)

    cube.Parent = workspace

end

-- Builds tower

for heightIndex = 1, TOWER_SIZE do

    local spawnY = (heightIndex - 1) * CUBE_SIZE

    currentColor = Color3.fromRGB(math.random(0, 255), math.random(0, 255), math.random(0, 255))

    for lengthIndex = 1, TOWER_SIZE do

        local spawnX = lengthIndex * CUBE_SIZE

	cubeTransparency = (lengthIndex - 1) * 0.10 --Updates every loop starting at 0

        for widthIndex = 1, TOWER_SIZE do

            local spawnZ = widthIndex * CUBE_SIZE

            makeCube(spawnX, spawnY, spawnZ)

            task.wait(0.05)

        end

    end

end

```

### [Rain down objects](#rain-down-objects)[](#rain-down-objects)

Instead of parts, try spawning an actual object. The example here used cupcakes.

On your own, see if you can:

-

Create an object from base parts. Make sure to weld all parts together so the object doesn't fall apart.

-

Place the object in ServerStorage

-

Modify the PartMaker found in the [Nested Loop Example](#nested-loop-example) to use your object instead of parts.

A sample is shown here.

A code solution using cupcakes is included.

```

local numberOfBatches = 30

local cupcakesPerBatch = 6

local cupcakesBaked = 0

--Makes a single cupcake

local function makeCupcake()

    local ServerStorage = game:GetService("ServerStorage")

    local cupcake = ServerStorage.Cupcake:Clone()

    local cup = cupcake.Cup

    local frosting = cupcake.Frosting

    cupcake:SetPrimaryPartCFrame(CFrame.new(0, 20, 0) * CFrame.Angles(0, 0, -90))

    frosting.Color = frostingColor

    cup.Color = cupColor

    cupcake.Parent = workspace

end

-- Outer loop

for cupcakeBatch = 1, numberOfBatches do

    print("Top outer loop: cupcake batch " .. cupcakeBatch)

    frostingColor = Color3.fromRGB(math.random(0, 255), math.random(0, 255), math.random(0, 255))

    cupColor = Color3.fromRGB(math.random(0, 255), math.random(0, 255), math.random(0, 255))

    -- Inner loop

    for cupcakeNumber = 1, cupcakesPerBatch do

        makeCupcake()

        print("Inner loop: cupcake " .. cupcakeNumber)

        -- Track muffins baked

        cupcakesBaked += 1

        task.wait(0.5)

    end

    print("Bottom outer loop: " .. cupcakesBaked .. " cupcakes baked so far.")

end

```

## [Summary](#summary)[](#summary)

To accomplish more complex tasks, coders will find it helpful to combine multiple loops, and even different types of loops. All loops can be nested, meaning that one loop is inside another. Nested loops follow the same logic as any other loop. It starts in the first, outermost loop, runs tasks through inner loops, and then cycles back to the first loop if applicable.

[Next](/docs/en-us/tutorials/fundamentals/coding-5/landing)[Previous](/docs/en-us/tutorials/fundamentals/coding-4/create-a-timed-bridge)

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
