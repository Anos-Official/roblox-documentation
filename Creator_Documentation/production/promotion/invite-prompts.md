<!-- Source: https://create.roblox.com/docs/en-us/production/promotion/invite-prompts -->

Player invite prompts | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/production/promotion/invite-prompts.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Discovery](/docs/en-us/discovery)

# Player invite prompts

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/production/promotion/invite-prompts.md)

In addition to common [promotion](/docs/en-us/production/promotion)  methods for increasing your player base, you can implement invite prompts  directly inside your game, encouraging players to invite their friends and increase co-experience gameplay.

The invite prompt system features the following:

-

Dynamic Invitees  — Prompt players to invite multiple friends from a selection list, or invite one specific friend.

-

Launch Data  — Include optional [launch data](#include-launch-data)  that can be read through [Player:GetJoinData()](/docs/en-us/reference/engine/classes/Player#GetJoinData)  when the invited friend joins. Example use cases include routing invited friends to a coordinate location or personalizing the joining game for the invitee.

-

Customizable Text  — Customize the [invite prompt](#prompt-an-invite)  message and the [notification](#set-notification-options)  message. For example, an invite prompt for the player may read "Ask your friends to join the adventure!" and the notification message for the invited friend(s) may read "{displayName} wants you to join their adventure in {experienceName}!".

You can also track and reward inviters and invitees using the [Friend Invite Reward System](/docs/en-us/production/promotion/referral-system) .

In-experience prompt Invite notification

![](https://prod.docsiteassets.roblox.com/assets/promotion/invite-prompts/Invite-From-Experience.png)

## [Set invite options](#set-invite-options)[](#set-invite-options)

By default, an invite prompt for the player shows a menu of their friends with Invite  buttons. To customize the prompt message, target a specific friend, or include launch data in the invite, you'll need to set up an [ExperienceInviteOptions](/docs/en-us/reference/engine/classes/ExperienceInviteOptions)  object with the desired properties.

| Property | | Type | | Description |
| --- | --- |
| [PromptMessage](/docs/en-us/reference/engine/classes/ExperienceInviteOptions#PromptMessage) | | string | | Custom text shown on the invite prompt for the sending player, for example "Ask your friends to join the adventure!" for a multi-friend invite prompt, or "Invite this friend to join the adventure!" for a specific friend invite prompt. Note that if your custom invite prompt message is long enough to overflow the bounds of the UI, it will not be shown. |
| [InviteUser](/docs/en-us/reference/engine/classes/ExperienceInviteOptions#InviteUser) | | number | | Roblox [UserId](/docs/en-us/reference/engine/classes/Player#UserId)  of the specific friend to invite; if not provided, the player will be prompted to pick from a list of friends. |
| [InviteMessageId](/docs/en-us/reference/engine/classes/ExperienceInviteOptions#InviteMessageId) | | string | | Asset ID that maps to a Notification  asset type. This asset is used to store/localize a custom string for the invite notification that friends receive. See [Setting Notification Options](#set-notification-options)  for details. |
| [LaunchData](/docs/en-us/reference/engine/classes/ExperienceInviteOptions#LaunchData) | | string | | Used to set a parameter in [Player:GetJoinData()](/docs/en-us/reference/engine/classes/Player#GetJoinData)  when a friend joins from the invite notification. Maximum of 200 characters. See [Include launch data](#include-launch-data)  for a usage example. |

Multiple friends Specific friend

LocalScript - Invite Multiple Friends

```

local SocialService = game:GetService("SocialService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Construct invite options with a custom prompt message

local inviteOptions = Instance.new("ExperienceInviteOptions")

inviteOptions.PromptMessage = "Ask your friends to join the adventure!"

```

## [Set notification options](#set-notification-options)[](#set-notification-options)

By default, the invite notification that friends receive contains the sender's [DisplayName](/docs/en-us/reference/engine/classes/Player#DisplayName) , username, and the game name. To customize the message, you can create a Notification  asset on the [Creator Dashboard](https://create.roblox.com/dashboard/creations)  and include its asset ID as a parameter of [ExperienceInviteOptions](/docs/en-us/reference/engine/classes/ExperienceInviteOptions) .

1.

Navigate to the [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Similar to [badges](/docs/en-us/production/publishing/badges) , notification strings are tied to a specific game . Locate that game's thumbnail and click on it.

3.

In the left column, under Engagement , click Notifications .

4.

In the center region, click the Create a Notification String  button.

5.

Fill in an identifier name (only visible to you) and the custom notification text. Note that you must include {experienceName}  as a placeholder to identify the game's name for invited friends, and you can optionally include the sender's [DisplayName](/docs/en-us/reference/engine/classes/Player#DisplayName)  through the {displayName}  placeholder.

Example notification strings:

-

 {displayName} wants you to join their adventure in {experienceName}!

-

 {displayName} just cleared the sixth stage of {experienceName}. Can you?

6.

When ready, click the Create Notification String  button.

7.

On the notifications page, in the table of notifications, click the ⋯  button in the Actions  column and select Copy Asset ID .

8.

In the [ExperienceInviteOptions](/docs/en-us/reference/engine/classes/ExperienceInviteOptions)  object for the invite prompt, paste the asset ID as the value of the [InviteMessageId](/docs/en-us/reference/engine/classes/ExperienceInviteOptions#InviteMessageId)  property.

LocalScript - Invite Multiple Friends

```

local SocialService = game:GetService("SocialService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Construct invite options with friend's user ID

local inviteOptions = Instance.new("ExperienceInviteOptions")

inviteOptions.InviteMessageId = "ef0e0790-e2e8-4441-9a32-93f3a5783bf1"

```

## [Prompt an invite](#prompt-an-invite)[](#prompt-an-invite)

To prompt an invite, you should first determine whether the player can  send an invite, as the ability may vary depending on the platform or player. Once confirmed, you can display the invitation prompt to the player.

1.

Call [SocialService:CanSendGameInviteAsync()](/docs/en-us/reference/engine/classes/SocialService#CanSendGameInviteAsync) , wrapped in a [pcall()](/docs/en-us/reference/engine/globals/LuaGlobals#pcall)  since it's an asynchronous network call that may occasionally fail.

2.

If the invite ability is confirmed, call [SocialService:PromptGameInvite()](/docs/en-us/reference/engine/classes/SocialService#PromptGameInvite)  with the optional [invite options object](#set-invite-options)  as the second argument.

Once prompted, the player will see an on-screen prompt to invite multiple friends, or the specific friend defined in the [invite options object](#set-invite-options) . When the player then clicks the Invite  button for one or more friends, those friends will receive a notification containing the sender's [DisplayName](/docs/en-us/reference/engine/classes/Player#DisplayName) , username, and the experience name. Notifications may be further customized as outlined in [Set notification options](#set-notification-options) .

Multiple Friends Specific Friend

LocalScript - Invite Multiple Friends

```

local SocialService = game:GetService("SocialService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Function to check whether the player can send an invite

local function canSendGameInvite(sendingPlayer)

	local success, canSend = pcall(function()

		return SocialService:CanSendGameInviteAsync(sendingPlayer)

	end)

	return success and canSend

end

local canInvite = canSendGameInvite(player)

if canInvite then

	SocialService:PromptGameInvite(player)

end

```

## [Include launch data](#include-launch-data)[](#include-launch-data)

To further improve in-experience cooperation or to incentivize player invites, you can include launch data  in an invite prompt, useful for scenarios such as routing invited friends to a coordinate location or personalizing the joining game for the invitee.

1.

When [prompting an invite](#prompt-an-invite) , include an [ExperienceInviteOptions](/docs/en-us/reference/engine/classes/ExperienceInviteOptions)  object with relevant data that will be used when the friend joins the game, for example the sender's [Player.UserId](/docs/en-us/reference/engine/classes/Player#UserId) , the ID of a [badge](/docs/en-us/production/publishing/badges)  to award to the friend upon joining, or a coordinate location to spawn the friend at. If you need to compile multiple pieces of data, encode the data using [JSONEncode()](/docs/en-us/reference/engine/classes/HttpService#JSONEncode) .

Multiple Friends Specific Friend

LocalScript - Invite Multiple Friends

```

local HttpService = game:GetService("HttpService")

local SocialService = game:GetService("SocialService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local data = {

	senderUserID = player.UserId,

	spawnLocation = {12, 48, 205.5}

}

local launchData = HttpService:JSONEncode(data)

-- Construct invite options with launch data

local inviteOptions = Instance.new("ExperienceInviteOptions")

inviteOptions.LaunchData = launchData

-- Function to check whether the player can send an invite

local function canSendGameInvite(sendingPlayer)

	local success, canSend = pcall(function()

		return SocialService:CanSendGameInviteAsync(sendingPlayer)

	end)

	return success and canSend

end

local canInvite = canSendGameInvite(player)

if canInvite then

	SocialService:PromptGameInvite(player, inviteOptions)

end

```

Always remember to include inviteOptions  containing the launch data (maximum of 200 characters) as the second parameter of [PromptGameInvite()](/docs/en-us/reference/engine/classes/SocialService#PromptGameInvite) .

2.

For incoming friends who join via the notification, check for launch data on the server side through [Player:GetJoinData()](/docs/en-us/reference/engine/classes/Player#GetJoinData) . If you encode multiple pieces of data into JSON for the invite prompt, remember to decode it with [JSONDecode()](/docs/en-us/reference/engine/classes/HttpService#JSONDecode) .

Script - Using Invite Launch Data

```

local HttpService = game:GetService("HttpService")

local Players = game:GetService("Players")

local ATTEMPT_LIMIT = 10

local RETRY_DELAY = 1

local function onPlayerAdded(player)

	local launchData

	for _ = 1, ATTEMPT_LIMIT do

		task.wait(RETRY_DELAY)

		local joinData = player:GetJoinData()

		if joinData.LaunchData ~= "" then

			launchData = joinData.LaunchData

			break

		end

	end

	if launchData then

		local data = HttpService:JSONDecode(launchData)

		print(data.senderUserID)

		print(data.spawnLocation)

	else

		warn("No launch data received!")

	end

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Launch data can take a few seconds to appear after the friend joins from the invite. As shown in the code sample above, it's recommended that you wait until the launch data arrives before attempting to use it.

3.

If the launch data exists, you can use it for a wide variety of design scenarios, including:

-

Spawn the incoming friend at the beginning of a challenging obstacle course that the sender just completed, based on a coordinate location passed through the launch data.

-

Check if the sender  is in the place, based on their [Player.UserId](/docs/en-us/reference/engine/classes/Player#UserId)  in the launch data, and teleport the friend's character near their character.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
