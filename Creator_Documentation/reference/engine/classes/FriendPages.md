<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/FriendPages -->

FriendPages | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/FriendPages.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [Pages](/docs/en-us/reference/engine/classes/Pages)
8. /
9. [FriendPages](/docs/en-us/reference/engine/classes/FriendPages)

English

Feedback

Engine Class

FriendPages

Not Creatable

Not Replicated

---

## Summary

Inherited Members

3  inherited from [Pages](/docs/en-us/reference/engine/classes/Pages)

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

Code Samples

Print Roblox Friends

```

local Players = game:GetService("Players")

local USERNAME = "Cozecant"

-- First, get the user ID of the player

local userId = Players:GetUserIdFromNameAsync(USERNAME)

-- Then, get a FriendPages object for their friends

local friendPages = Players:GetFriendsAsync(userId)

-- Walk the pages, collecting the username of every friend. Each page entry is

-- a table of information about the friend, including Username.

local usernames = {}

while true do

	for _, friend in ipairs(friendPages:GetCurrentPage()) do

		table.insert(usernames, friend.Username)

	end

	if friendPages.IsFinished then

		break

	end

	friendPages:AdvanceToNextPageAsync()

end

print("Friends of " .. USERNAME .. ": " .. table.concat(usernames, ", "))

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
