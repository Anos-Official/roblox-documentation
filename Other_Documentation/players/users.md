<!-- Source: https://create.roblox.com/docs/players/users -->

Users and scoped user IDs | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/players/users.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Players](/docs/players)

# Users and scoped user IDs

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/players/users.md)

Scoped user IDs have not rolled out broadly yet. [Player.User](/docs/reference/engine/classes/Player#User)  and the [User](/docs/reference/engine/datatypes/User)  data type are available now, and a user's effective user ID currently remains their global user ID.

Roblox exposes one effective user ID  for each user in each game, group, or app. Depending on the user's history with that domain, their effective user ID is either their global user ID or a scoped user ID . This page explains how effective user IDs work and how to use the [User](/docs/reference/engine/datatypes/User)  type in your game code.

The following concepts are central to user identification:

| Concept | | Description |
| --- | --- |
| User | | A persistent account on Roblox. |
| Player | | The representation of a user within a running game's data model (see [Players](/docs/players) ). |
| [User](/docs/reference/engine/datatypes/User)  data type | | A data type that carries a user's effective user ID and its domain context. This is the standard identifier for referencing users in game code. |
| Global user ID | | The platform-level user ID that Roblox assigns to each account. It's globally unique across Roblox. |
| Scoped user ID | | A user ID assigned within a specific domain. A user's scoped user IDs are different in each game, group, or app. |
| Effective user ID | | The single user ID that Roblox exposes for a user within a [domain](#effective-user-ids-and-domains) . |
| Pre-rollout user | | A user who first engaged with a domain before the scoped user ID rollout. In that domain, their effective user ID remains their global user ID. |
| Post-rollout user | | A user who first engaged with a domain after the scoped user ID rollout. In that domain, their effective user ID is a scoped user ID. |

## [Effective user IDs and domains](#effective-user-ids-and-domains)[](#effective-user-ids-and-domains)

Each user has one effective user ID within a specific game , group , or app . Roblox doesn't expose separate global and scoped user IDs for the same user in that domain:

-

A pre-rollout user  has their global user ID as their effective user ID.

-

A post-rollout user  has a scoped user ID as their effective user ID. That ID is only meaningful within that domain.

In game code, [Player.UserId](/docs/reference/engine/classes/Player#UserId)  and [Player.User.Id](/docs/reference/engine/datatypes/User#Id)  both return this effective user ID and always have the same numeric value ([Player.User.Id](/docs/reference/engine/classes/Player#User)  equals [Player.UserId](/docs/reference/engine/classes/Player#UserId) ), so your code doesn't need branching logic to choose between them.

Roblox scopes user identity across three types of domains:

| Domain | | Scoped to | | Example |
| Experience  ([Enum.DomainType.EXPERIENCE](/docs/reference/engine/enums/DomainType#EXPERIENCE) ) | | A specific experience | | A player's ID in your experience |
| Group | | A specific Roblox group (community) | | A member's ID in your group |
| OAuth app  ([Enum.DomainType.OAUTH](/docs/reference/engine/enums/DomainType#OAUTH) ) | | A specific OAuth application | | A user's ID in your external tool |

### [How effective user IDs work](#how-effective-user-ids-work)[](#how-effective-user-ids-work)

When a player joins your game, they have one effective user ID for that game. A post-rollout user's effective user ID is a scoped user ID unique to that game. They receive a different scoped user ID in any other game, group, or app where they are also a post-rollout user. This means:

-

Effective user IDs are integers, whether they are global or scoped.

-

Effective user IDs are stable across sessions within the same domain.

-

A scoped user ID does not collide with any existing global user ID.

-

The same numeric value can appear in different domains for different users. The unique key is the combination of the domain (domain type and domain ID) and the effective user ID.

### [Example scenario](#example-scenario)[](#example-scenario)

The following example demonstrates how different games reference the same user:

| Scenario | | User context | | Effective user ID seen by game |
| User connects to Game A | | Pre-rollout user | | 123  (global user ID, unchanged) |
| User connects to Game B | | Post-rollout user | | 500789  (scoped user ID for Game B) |
| User connects to Game C | | Post-rollout user | | 302441  (scoped user ID for Game C) |

### [Pre-rollout users](#pre-rollout-users)[](#pre-rollout-users)

If a player is a pre-rollout user in your game, their effective user ID remains their global user ID in that game. Both [Player.UserId](/docs/reference/engine/classes/Player#UserId)  and [Player.User.Id](/docs/reference/engine/datatypes/User#Id)  return that global user ID. Roblox doesn't expose a second user ID for the player in that game. This ensures existing data store keys, leaderboards, and inventories continue to work without any changes.

### [Group domain](#group-domain)[](#group-domain)

Each Roblox group is its own domain. A user has one effective user ID within a group, separate from their effective user ID in any game or OAuth application:

-

In-game group checks don't change  — Engine methods on [Player](/docs/reference/engine/classes/Player)  such as [Player:IsInGroupAsync()](/docs/reference/engine/classes/Player#IsInGroupAsync) , [Player:GetRankInGroupAsync()](/docs/reference/engine/classes/Player#GetRankInGroupAsync) , and [Player:GetRoleInGroupAsync()](/docs/reference/engine/classes/Player#GetRoleInGroupAsync) , as well as [GroupService:PromptJoinAsync()](/docs/reference/engine/classes/GroupService#PromptJoinAsync) , resolve identity internally without exposing a user ID.

-

Open Cloud group APIs use the group's domain  — This applies to endpoints that list or manage group memberships and join requests.

## [Working with the User Type](#working-with-the-user-type)[](#working-with-the-user-type)

[User](/docs/reference/engine/datatypes/User)  is the standard way to identify users in game code. A [User](/docs/reference/engine/datatypes/User)  value carries the effective user ID alongside the domain type and domain ID, so the identity context always travels with the identifier. For full API details, see the [User](/docs/reference/engine/datatypes/User)  reference.

### [Get a User from a Player](#get-a-user-from-a-player)[](#get-a-user-from-a-player)

The primary way to obtain a [User](/docs/reference/engine/datatypes/User)  is from a connected [Player](/docs/reference/engine/classes/Player)  via [Player.User](/docs/reference/engine/classes/Player#User) :

```

local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)

    local user = player.User

    print("Effective user ID:", user.Id) -- Always matches player.UserId

    print("Domain type:", user.DomainType)

    print("Domain ID:", user.DomainId)

end)

```

### [Construct a User from an ID](#construct-a-user-from-an-id)[](#construct-a-user-from-an-id)

To create a [User](/docs/reference/engine/datatypes/User)  from a known effective user ID within the current game, use [User.fromId()](/docs/reference/engine/datatypes/User#fromId) :

```

local user = User.fromId(knownUserId)

```

## [Using User with engine APIs](#using-user-with-engine-apis)[](#using-user-with-engine-apis)

Engine APIs that accept a user ID parameter also accept [User](/docs/reference/engine/datatypes/User)  values directly. Using [User](/docs/reference/engine/datatypes/User)  is recommended:

```

-- Both forms work:

BadgeService:AwardBadge(player.User, badgeId)    -- Recommended

BadgeService:AwardBadge(player.UserId, badgeId)

```

```

-- Both forms work:

local target = Players:GetPlayerByUserId(player.User) -- Recommended

local target = Players:GetPlayerByUserId(someUserId)

```

When a numeric user ID is passed to an engine API that accepts user IDs, it is automatically wrapped into a [User](/docs/reference/engine/datatypes/User)  internally.

### [Engine APIs that return user IDs](#engine-apis-that-return-user-ids)[](#engine-apis-that-return-user-ids)

Engine APIs that return numeric user IDs return the user's effective user ID:

-

Pre-rollout users  — the API returns the user's global user ID.

-

Post-rollout users  — the API returns the user's scoped user ID.

[Player.UserId](/docs/reference/engine/classes/Player#UserId) , [Player.User.Id](/docs/reference/engine/datatypes/User#Id) , and other engine APIs all return this same effective user ID for a user in your game, so existing code that reads numeric user ID fields continues to work without branching logic.

Open Cloud requests and responses use the same effective user ID for the target domain. They don't expose a second user ID for the same user in that domain.

## [Storing user identity](#storing-user-identity)[](#storing-user-identity)

Use a numeric effective user ID only to identify a user within a single domain. A data store key in one game can use user.Id  directly:

```

local key = ("player_%d"):format(player.User.Id)

PlayerDataStore:SetAsync(key, data)

```

When another domain reads the stored identity, such as an OAuth app that moderates users, store the string from [ToString()](/docs/reference/engine/datatypes/User#ToString) . The string encodes the domain context together with the effective user ID. Using the integer alone can apply an action to the wrong user when the same number identifies a different user in another domain.

```

local encoded = player.User:ToString()

SomeDataStore:SetAsync("support_ticket_user", encoded)

-- Later, restore from the string

local user = User.fromString(encoded)

```

For more details on serialization guarantees, see the [User](/docs/reference/engine/datatypes/User)  reference.

## [Best practices](#best-practices)[](#best-practices)

-

Use [Player.User](/docs/reference/engine/classes/Player#User)  as the standard identifier in new code.

-

Use the numeric effective user ID only within a single domain, such as data store keys for one game.

-

Use [ToString()](/docs/reference/engine/datatypes/User#ToString)  and [fromString()](/docs/reference/engine/datatypes/User#fromString)  when another domain reads the stored identity.

### [When to use User or Player](#when-to-use-user-or-player)[](#when-to-use-user-or-player)

-

Use [Player](/docs/reference/engine/classes/Player)  for in-server actions: character movement, GUI, teleport, chat, inventory.

-

Use [User](/docs/reference/engine/datatypes/User)  for identity that outlives a session: data stores, Open Cloud tools, cross-game references.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
