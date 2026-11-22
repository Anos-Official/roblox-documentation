<!-- Source: https://create.roblox.com/docs/en-us/chat/voice-chat -->

Voice Chat | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/chat/voice-chat.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. Chat

# Voice Chat

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/chat/voice-chat.md)

Voice Chat is currently available to all 13+ age-verified users in a specific set of countries. Review the [Voice Chat FAQ](https://en.help.roblox.com/hc/en-us/articles/4405807645972-Voice-Chat-FAQs)  to learn more. Users not  in these countries should use [ID verification](https://en.help.roblox.com/hc/en-us/articles/4407282410644)  to enable chat with voice. Once verified, eligible 13+ users can opt‑in to use this feature by visiting their account Settings  page or from within a voice enabled game, allowing them to chat with voice in any Roblox game that supports it. Games with voice often see an uplift in engagement, DAU, and spending.

Voice Chat  is a feature enabling real-time, spoken communication between yourself and other players. It is only available for places that support a maximum of 100 players.

 ![Two users chatting with voice inside a game.](https://prod.docsiteassets.roblox.com/assets/players/voice-chat/In-Experience-Example.jpg)

## [Enable Voice Chat](#enable-voice-chat)[](#enable-voice-chat)

Voice Chat is enabled by default for verified 13+ users on all new games with a maximum of 100 players. Enabling Voice Chat is required to use the speech-to-text API.

To activate voice for existing games or disable it for new ones:

1.

Open your game in Studio.

2.

Open File  > Experience Settings .

3.

Navigate to the Communication  tab on the left side of the window.

4.

Toggle Enable Voice Chat  to your desired setting.

5.

OPTIONAL

 For greater communication among players within your game, toggle on Enable Camera  to allow eligible players to animate their avatar with their movement.

6.

[Publish](/docs/en-us/production/publishing/publish-games-and-places)  the place to save the changes.

### [Set maximum players](#set-maximum-players)[](#set-maximum-players)

If you previously set the maximum number of players in a place to more than 100, you'll need to reduce it to support Voice Chat.

1.

Select the game on the [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

In the left-hand navigation, navigate to Configurations  > Places .

3.

Select the desired place and then navigate to Access in the left column.

4.

For Maximum Visitor Count , enter a number less than or equal to 100.

5.

Click the Save Changes  button.

When you update the maximum number of players in a place to fewer than 100, there may be servers already configured to a different, higher number. Since those servers won't support Voice Chat, it's recommended to [restart servers](/docs/en-us/projects/update-games#restart-servers) .

### [Customize voice behavior](#customize-voice-behavior)[](#customize-voice-behavior)

Voice Chat is proximity-based  by default, adjusting the volume of participants based on how close they are to each other. However, you can set [UseAudioApi](/docs/en-us/reference/engine/classes/VoiceChatService#UseAudioApi)  to [Enabled](/docs/en-us/reference/engine/enums/AudioApiRollout)  to take control over how voices are set up and used in your game.

If [VoiceChatService](/docs/en-us/reference/engine/classes/VoiceChatService)  does not appear already:

1.

Right‑click in the Explorer  window and select Show Services…  from the context menu.

2.

Select [VoiceChatService](/docs/en-us/reference/engine/classes/VoiceChatService)  in the popup window and click Insert . The service appears in the Explorer  hierarchy.

 ![VoiceChatService in Explorer hierarchy](https://prod.docsiteassets.roblox.com/assets/studio/explorer/VoiceChatService.png)

3.

With [VoiceChatService](/docs/en-us/reference/engine/classes/VoiceChatService)  selected, ensure that [UseAudioApi](/docs/en-us/reference/engine/classes/VoiceChatService#UseAudioApi)  to [Enabled](/docs/en-us/reference/engine/enums/AudioApiRollout)  in the Properties  window. This may already be done for you.

#### [Team-based](#team-based)[](#team-based)

To implement [Team](/docs/en-us/reference/engine/classes/Team) -based chat where only teammates can hear one another, you can use the following [Script](/docs/en-us/reference/engine/classes/Script)  within [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService) :

Team Chat

```

local Teams = game:GetService("Teams")

local function findAudioInput(forPlayer : Player) : AudioDeviceInput?

	-- Assumes there is only one AudioDeviceInput per player, parented to the Player object

	-- This is provided for you if VoiceChatService.EnableDefaultVoice is true

	-- May need to be reworked for generality if your place puts AudioDeviceInput objects elsewhere

	return forPlayer:FindFirstChildWhichIsA("AudioDeviceInput")

end

local function onTeamChanged(player : Player)

	local team = player.Team

	if not team then return end

	local device = findAudioInput(player)

	if not device then return end

	-- Only permit teammates to hear each other

	device.AccessType = Enum.AccessModifierType.Allow

	local allowed = {}

	for _, player : Player in team:GetPlayers() do

		table.insert(allowed, player.UserId)

	end

	device:SetUserIdAccessList(allowed)

end

local function onTeamAdded(team : Team)

	team.PlayerAdded:Connect(onTeamChanged)

	team.PlayerRemoved:Connect(onTeamChanged)

end

for _, team : Team in Teams:GetTeams() do

	onTeamAdded(team)

end

Teams.ChildAdded:Connect(function(child : Instance)

	if child:IsA("Team") then

		onTeamAdded(child)

	end

end)

```

#### [Non-spatial](#non-spatial)[](#non-spatial)

Depending on your game's needs, it might make more sense to hear others with equal volume, regardless of their geographic location. If you [disable default Voice Chat](#disable-per-place) , you can then implement non‑spatial Voice Chat through the following [Script](/docs/en-us/reference/engine/classes/Script)  within [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService) :

Non-Proximity Chat

```

local Players = game:GetService("Players")

local Workspace = game:GetService("Workspace")

local function wireUp(source : Instance, target : Instance)

	local wire = Instance.new("Wire")

	wire.SourceInstance = source

	wire.TargetInstance = target

	wire.Parent = source

end

-- Set up a global volume slider for everybody's voice

local volumeSlider = Instance.new("AudioFader", Workspace)

local output = Instance.new("AudioDeviceOutput", Workspace)

wireUp(volumeSlider, output)

local function onPlayerAdded(player : Player)

	local device = Instance.new("AudioDeviceInput", player)

	device.Player = player

	-- Route each new player's microphone input to the global volume slider

	wireUp(device, volumeSlider)

end

for _, player in Players:GetPlayers() do

	onPlayerAdded(player)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

The above script runs on the server, creating an [AudioDeviceInput](/docs/en-us/reference/engine/classes/AudioDeviceInput)  per‑player and connecting them all to a shared [AudioFader](/docs/en-us/reference/engine/classes/AudioFader) . Taking this behavior as‑is allows players to hear all other players and  themselves. Since hearing yourself can be quite distracting, you can place the following [LocalScript](/docs/en-us/reference/engine/classes/LocalScript)  in [StarterPlayerScripts](/docs/en-us/reference/engine/classes/StarterPlayerScripts)  to remove the [Wires](/docs/en-us/reference/engine/classes/Wire)  that would otherwise ferry your own voice back to your own speakers.

LocalScript

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local function onDescendantAdded(descendant : Instance)

	if descendant:IsA("Wire") then

		descendant:Destroy()

	end

end

for _, descendant in player:GetDescendants() do

	onDescendantAdded(descendant)

end

player.DescendantAdded:Connect(onDescendantAdded)

```

### [Disable per place](#disable-per-place)[](#disable-per-place)

If you don't want to enable Voice Chat for every place within your game, you can disable it within specific places that would otherwise be voice‑eligible.

If you're currently setting a place's Max Players  to a value over 100 in order to disable Voice Chat, it's recommended to use this workflow instead.

To disable Voice Chat for a specific place within a game:

1.

Right‑click in the Explorer  window and select Show Services…  from the context menu.

2.

Select [VoiceChatService](/docs/en-us/reference/engine/classes/VoiceChatService)  in the popup window and click Insert . The service appears in the Explorer  hierarchy.

 ![VoiceChatService in Explorer hierarchy](https://prod.docsiteassets.roblox.com/assets/studio/explorer/VoiceChatService.png)

3.

With [VoiceChatService](/docs/en-us/reference/engine/classes/VoiceChatService)  selected, disable [EnableDefaultVoice](/docs/en-us/reference/engine/classes/VoiceChatService#EnableDefaultVoice)  in the Properties  window.

4.

Publish the place to save the changes and [restart servers](/docs/en-us/projects/update-games#restart-servers)  to ensure the change takes effect for all servers currently running your game.

## [Check status](#check-status)[](#check-status)

You can check if a player has enabled Voice Chat by calling [IsVoiceEnabledForUserIdAsync()](/docs/en-us/reference/engine/classes/VoiceChatService#IsVoiceEnabledForUserIdAsync)  in a [LocalScript](/docs/en-us/reference/engine/classes/LocalScript) , or in a [Script](/docs/en-us/reference/engine/classes/Script)  with [RunContext](/docs/en-us/reference/engine/classes/BaseScript#RunContext)  set to [Enum.RunContext.Client](/docs/en-us/reference/engine/enums/RunContext#Client) .

Client Script - Check Voice Chat Status

```

local Players = game:GetService("Players")

local VoiceChatService = game:GetService("VoiceChatService")

local localPlayer = Players.LocalPlayer

local success, enabled = pcall(function()

	return VoiceChatService:IsVoiceEnabledForUserIdAsync(localPlayer.UserId)

end)

if success and enabled then

	print("Voice Chat enabled!")

end

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
