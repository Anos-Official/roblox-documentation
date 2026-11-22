<!-- Source: https://create.roblox.com/docs/characters/name-health-display -->

Character name/health display | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/characters/name-health-display.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Characters](/docs/characters)

# Character name/health display

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/characters/name-health-display.md)

The [Humanoid](/docs/reference/engine/classes/Humanoid)  instance is used to create character models, both for user avatars and NPCs. When a [Humanoid](/docs/reference/engine/classes/Humanoid)  is present inside a [Model](/docs/reference/engine/classes/Model)  that contains a part named Head , Roblox displays a name and/or health bar above that part.

 ![Character display information above an in-game avatar](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/Display-Indicated.jpg)

Through various [Humanoid](/docs/reference/engine/classes/Humanoid)  properties, you can modify the following:

-

The [distance](#display-distance-type)  from which users can see the name/health of other humanoids in relation to their own character's humanoid.

-

The [display name](#override-display-names)  which shows over a humanoid.

-

Whether a humanoid's [health bar](#health-display-type)  always appears, never appears, or only appears when the humanoid is damaged.

-

Whether names and health bars are [occluded](#occlusion)  (hidden) when line-of-sight between the camera and another humanoid is blocked.

As noted in the introduction, character name/health display requires that the [Humanoid](/docs/reference/engine/classes/Humanoid)  instance is inside a [Model](/docs/reference/engine/classes/Model)  and that the model contains a [BasePart](/docs/reference/engine/classes/BasePart)  named Head . Both objects must also be at the same level in the model's hierarchy.

## [Display properties](#display-properties)[](#display-properties)

### [Display distance type](#display-distance-type)[](#display-distance-type)

The [Humanoid.DisplayDistanceType](/docs/reference/engine/classes/Humanoid#DisplayDistanceType)  property sets how users see the name/health of other characters in relation to their own character.

#### [Viewer](#viewer)[](#viewer)

When a humanoid's [DisplayDistanceType](/docs/reference/engine/classes/Humanoid#DisplayDistanceType)  is set to [HumanoidDisplayDistanceType.Viewer](/docs/reference/engine/enums/HumanoidDisplayDistanceType) , it sees the name/health of other humanoids within range of its own [NameDisplayDistance](/docs/reference/engine/classes/Humanoid#NameDisplayDistance)  and [HealthDisplayDistance](/docs/reference/engine/classes/Humanoid#HealthDisplayDistance) . You can consider this the lowest priority since it is not taken into account for other humanoids configured as [subject](#subject)  or [none](#none) .

In the following scenario, the user's character (Viewer ) has a larger [NameDisplayDistance](/docs/reference/engine/classes/Humanoid#NameDisplayDistance)  than [HealthDisplayDistance](/docs/reference/engine/classes/Humanoid#HealthDisplayDistance) , as indicated by the circles. As a result, the user sees character names for both Watchman  and Octavia , but only sees a health bar for Watchman .

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/DisplayDistanceType-Viewer.jpg)

#### [Subject](#subject)[](#subject)

When a humanoid's [DisplayDistanceType](/docs/reference/engine/classes/Humanoid#DisplayDistanceType)  is set to [HumanoidDisplayDistanceType.Subject](/docs/reference/engine/enums/HumanoidDisplayDistanceType) , it takes full control  over its own name and health display through its [NameDisplayDistance](/docs/reference/engine/classes/Humanoid#NameDisplayDistance)  and [HealthDisplayDistance](/docs/reference/engine/classes/Humanoid#HealthDisplayDistance)  values. Effectively, other humanoids will only see the subject's name/health within those distances from the subject  humanoid.

In the following scenario, both Watchman  and Octavia  are set to Subject  and their [NameDisplayDistance](/docs/reference/engine/classes/Humanoid#NameDisplayDistance)  ranges are indicated by the circles. Only the name Octavia  is seen by the user whose character is standing inside her range but outside the Watchman  humanoid's range.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/DisplayDistanceType-Subject.jpg)

#### [None](#none)[](#none)

When a humanoid's [DisplayDistanceType](/docs/reference/engine/classes/Humanoid#DisplayDistanceType)  is set to [HumanoidDisplayDistanceType.None](/docs/reference/engine/enums/HumanoidDisplayDistanceType) , its name and health bar do not appear under any circumstances. In the following scenario, both Watchman  and Octavia  are set to None , so the other character does not see their name or health even when in range.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/DisplayDistanceType-None.jpg)

### [Health display type](#health-display-type)[](#health-display-type)

The [Humanoid.HealthDisplayType](/docs/reference/engine/classes/Humanoid#HealthDisplayType)  property provides further control over the character's health bar visibility. The bar reflects the humanoid's [Health](/docs/reference/engine/classes/Humanoid#Health)  as a factor of its [MaxHealth](/docs/reference/engine/classes/Humanoid#MaxHealth)  and it changes color from green to yellow to red as the humanoid's health decreases.

#### [AlwaysOn](#alwayson)[](#alwayson)

When a humanoid's [HealthDisplayType](/docs/reference/engine/classes/Humanoid#HealthDisplayType)  is set to [HumanoidHealthDisplayType.AlwaysOn](/docs/reference/engine/enums/HumanoidHealthDisplayType) , its health bar always appears.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/HealthDisplayType-AlwaysOn.jpg)

#### [DisplayWhenDamaged](#displaywhendamaged)[](#displaywhendamaged)

A humanoid with [HealthDisplayType](/docs/reference/engine/classes/Humanoid#HealthDisplayType)  set to [HumanoidHealthDisplayType.DisplayWhenDamaged](/docs/reference/engine/enums/HumanoidHealthDisplayType)  only shows a health bar when its [Health](/docs/reference/engine/classes/Humanoid#Health)  is less than its [MaxHealth](/docs/reference/engine/classes/Humanoid#MaxHealth) . In the following scenario, Watchman  has full health and does not display a health bar, but Octavia  is damaged by 50% and displays a yellow health bar.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/HealthDisplayType-DisplayWhenDamaged.jpg)

#### [AlwaysOff](#alwaysoff)[](#alwaysoff)

When a humanoid's [HealthDisplayType](/docs/reference/engine/classes/Humanoid#HealthDisplayType)  is set to [HumanoidHealthDisplayType.AlwaysOff](/docs/reference/engine/enums/HumanoidHealthDisplayType) , its health bar never appears under any circumstances.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/HealthDisplayType-AlwaysOff.jpg)

### [Occlusion](#occlusion)[](#occlusion)

Occlusion (hiding) of humanoid names behind walls or other objects is controlled by the character's [Humanoid.NameOcclusion](/docs/reference/engine/classes/Humanoid#NameOcclusion)  property.

Occlusion does not occur if the occluding object's [Transparency](/docs/reference/engine/classes/BasePart#Transparency)  is higher than 0.99. Occlusion also does not occur when a humanoid is hidden behind a [Model](/docs/reference/engine/classes/Model)  containing a [Humanoid](/docs/reference/engine/classes/Humanoid) , such as another user's avatar character.

#### [NoOcclusion](#noocclusion)[](#noocclusion)

When a humanoid is hidden behind a visible object and its [NameOcclusion](/docs/reference/engine/classes/Humanoid#NameOcclusion)  is set to [NameOcclusion.NoOcclusion](/docs/reference/engine/enums/NameOcclusion) , its name and health are never occluded from viewing humanoids.

In the following scenario, both Watchman  and Octavia  are set to NoOcclusion . Although both are sufficiently hidden behind stone columns, the viewing humanoid still sees their name/health displays.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/NameOcclusion-NoOcclusion.jpg)

#### [OccludeAll](#occludeall)[](#occludeall)

When a humanoid is hidden behind a visible object and its [NameOcclusion](/docs/reference/engine/classes/Humanoid#NameOcclusion)  is set to [NameOcclusion.OccludeAll](/docs/reference/engine/enums/NameOcclusion) , its name and health are always occluded from viewing humanoids.

In the following scenario, both Watchman  and Octavia  are sufficiently hidden behind stone columns. Watchman  is set to OccludeAll , so its name and health are hidden from the viewing humanoid. Octavia , however, is set to [NoOcclusion](#noocclusion)  and her name/health remains visible to the viewing humanoid.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/NameOcclusion-OccludeAll.jpg)

#### [EnemyOcclusion](#enemyocclusion)[](#enemyocclusion)

When a humanoid is hidden behind a visible object and its [NameOcclusion](/docs/reference/engine/classes/Humanoid#NameOcclusion)  is set to [NameOcclusion.EnemyOcclusion](/docs/reference/engine/enums/NameOcclusion) , its name and health are only occluded from enemy humanoids (players on a different [Team](/docs/reference/engine/classes/Team) ).

In the following scenario, both Watchman  and Octavia  are sufficiently hidden behind stone columns, and both are set to EnemyOcclusion . The viewing humanoid and Watchman  are on the same [Team](/docs/reference/engine/classes/Team) , so name/health occlusion does not occur. However, the name and health of Octavia , on the opposing team, are occluded.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/NameOcclusion-EnemyOcclusion.jpg)

## [Modify character displays](#modify-character-displays)[](#modify-character-displays)

### [User avatars](#user-avatars)[](#user-avatars)

To modify the name or health display for every incoming avatar in a game, connect the [Players.PlayerAdded](/docs/reference/engine/classes/Players#PlayerAdded)  and [Player.CharacterAdded](/docs/reference/engine/classes/Player#CharacterAdded)  events in a [Script](/docs/reference/engine/classes/Script)  and set [display properties](#display-properties)  on the character's [Humanoid](/docs/reference/engine/classes/Humanoid) .

Script - Global Customization

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(function(character)

		local humanoid = character:FindFirstChildWhichIsA("Humanoid")

		if humanoid then

			-- Give each humanoid full control over its name/health display distance

			humanoid.DisplayDistanceType = Enum.HumanoidDisplayDistanceType.Subject

			-- Set name display distance to 20 studs

			humanoid.NameDisplayDistance = 20

			-- Set health bar display distance to 15 studs

			humanoid.HealthDisplayDistance = 15

			-- Only show health bar when humanoid is damaged

			humanoid.HealthDisplayType = Enum.HumanoidHealthDisplayType.DisplayWhenDamaged

		end

	end)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

You can also customize properties based on a player's [Team](/docs/reference/engine/classes/Team) , such as setting all "guard" players to a generic name, and hiding the names of all "ninja" players.

Script - Team Customization

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(function(character)

		local humanoid = character:FindFirstChildWhichIsA("Humanoid")

		if humanoid then

			-- Set the name of all guards to generic "Guard"

			if player.Team.Name == "Guards" then

				humanoid.DisplayName = "Guard"

			-- Hide the name for all ninjas

			elseif player.Team.Name == "Ninjas" then

				humanoid.DisplayDistanceType = Enum.HumanoidDisplayDistanceType.None

			end

		end

	end)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

When a player is assigned to a [Team](/docs/reference/engine/classes/Team) , their character's name appears in the same color as the team's [TeamColor](/docs/reference/engine/classes/Team#TeamColor) . This helps identify teammates and opposing players in team-based experiences.

### [NPC characters](#npc-characters)[](#npc-characters)

For NPC characters already placed in the 3D world, you can edit name/health directly on the [Humanoid](/docs/reference/engine/classes/Humanoid)  object in the [Properties](/docs/studio/properties)  window.

![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/Customize-NPC.jpg)

![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/Humanoid-Properties.png)

## [Override display names](#override-display-names)[](#override-display-names)

By default, a humanoid's display name matches the user's Roblox account Display Name  which is unique and separate from their account Username . To show a fully custom name that's unrelated to the user's account, you can override the [Humanoid.DisplayName](/docs/reference/engine/classes/Humanoid#DisplayName)  property.

### [Set directly](#set-directly)[](#set-directly)

You can set the [DisplayName](/docs/reference/engine/classes/Humanoid#DisplayName)  property of any [Humanoid](/docs/reference/engine/classes/Humanoid)  instance which you gain reference to through a [Script](/docs/reference/engine/classes/Script) , such as the [team customization](#user-avatars)  example, or directly on an [NPC](#npc-characters)  character's Humanoid  object.

### [Set through user input](#set-through-user-input)[](#set-through-user-input)

In some genres like roleplaying or fighting, you may want to provide a method for users to input their own character name, pet character name, etc. that's specific to the experience and isn't tied to their account display name. You can gather this input on the client side through a [TextBox](/docs/reference/engine/classes/TextBox)  name entry.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/TextBox-Example.jpg)

Once the input is submitted, you can pass it to the server through a [remote event](/docs/scripting/events/remote)  and then, on the server side, listen for the remote event and assign the [filtered](/docs/ui/text-filtering)  name to the user character's [Humanoid](/docs/reference/engine/classes/Humanoid) .

LocalScript - Fire Remote Event

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local changeNameEvent = ReplicatedStorage:WaitForChild("ChangeNameEvent")

changeNameEvent:FireServer("Amory")

```

Script - Assign Filtered Name

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local TextService = game:GetService("TextService")

-- Create remote event to receive text from client for filtering

local changeNameEvent = Instance.new("RemoteEvent")

changeNameEvent.Name = "ChangeNameEvent"

changeNameEvent.Parent = ReplicatedStorage

local function onRequestNameChange(player, newName)

	local character = player.Character

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	local filterResult

	local success, errorMessage = pcall(function()

		filterResult = TextService:FilterStringAsync(newName, player.UserId)

	end)

	if success then

		local filteredName

		local success, errorMessage = pcall(function()

			filteredName = filterResult:GetNonChatStringForBroadcastAsync()

		end)

		if success and humanoid then

			humanoid.DisplayName = filteredName

		end

	end

end

changeNameEvent.OnServerEvent:Connect(onRequestNameChange)

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
