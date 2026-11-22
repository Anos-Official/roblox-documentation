<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/UserService -->

UserService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/UserService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [UserService](/docs/en-us/reference/engine/classes/UserService)

English

Feedback

Engine Class

UserService

Not Creatable

Service

---

## Summary

Methods

|

[GetUserInfosByUserIdsAsync](#GetUserInfosByUserIdsAsync) (userIds :  [{any}](/docs/en-us/luau/tables#arrays) ) :[{any}](/docs/en-us/luau/tables#arrays)

 |
| --- | --- |
|

[GetUserFromGlobalUserIdAsync](#GetUserFromGlobalUserIdAsync) (userId :  [number](/docs/en-us/luau/numbers) ) :[User](/docs/en-us/reference/engine/datatypes/User)

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

GetUserInfosByUserIdsAsync

Yields

Capabilities: Basic

UserService:GetUserInfosByUserIdsAsync (userIds :[{any}](/docs/en-us/luau/tables#arrays) ) :[{any}](/docs/en-us/luau/tables#arrays)

Parameters

|

userIds :[{any}](/docs/en-us/luau/tables#arrays)

 |

Returns

[{any}](/docs/en-us/luau/tables#arrays)

Code Samples

UserService:GetUserInfosByUserIdsAsync Example

```

local UserService = game:GetService("UserService")

local success, result = pcall(function()

	return UserService:GetUserInfosByUserIdsAsync({ 156, 1, 735878936 })

end)

if success then

	for _, userInfo in ipairs(result) do

		print("Id:", userInfo.Id)

		print("Username:", userInfo.Username)

		print("DisplayName:", userInfo.DisplayName)

	end

else

	-- An error occurred

end

```

Provide feedback

---

GetUserFromGlobalUserIdAsync

Yields

Capabilities: Basic

UserService:GetUserFromGlobalUserIdAsync (userId :[number](/docs/en-us/luau/numbers) ) :[User](/docs/en-us/reference/engine/datatypes/User)

Parameters

|

userId :[number](/docs/en-us/luau/numbers)

 |

Returns

[User](/docs/en-us/reference/engine/datatypes/User)

Code Samples

Get User From Global User Id Async

```

local UserService = game:GetService("UserService")

local user = UserService:GetUserFromGlobalUserIdAsync(globalUserId)

print(user.Id)         -- Domain user ID for this experience

print(user.DomainType) -- Enum.DomainType.Experience

print(user.DomainId)   -- Current universe ID

```

Provide feedback

---

Jump to

▼

UserService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetUserInfosByUserIdsAsync()](#GetUserInfosByUserIdsAsync)

[GetUserFromGlobalUserIdAsync()](#GetUserFromGlobalUserIdAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
