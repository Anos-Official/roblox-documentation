<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/classes/RecommendationService -->

RecommendationService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/RecommendationService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/en-us/reference/engine/classes)
2. /
3. [Object](/docs/en-us/reference/engine/classes/Object)
4. /
5. [Instance](/docs/en-us/reference/engine/classes/Instance)
6. /
7. [RecommendationService](/docs/en-us/reference/engine/classes/RecommendationService)

English

Feedback

Engine Class

RecommendationService

Not Creatable

Service

---

## Summary

Methods

|

[GenerateItemListAsync](#GenerateItemListAsync) (generateRecommendationItemListRequest :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[RecommendationPages](/docs/en-us/reference/engine/classes/RecommendationPages)

 |
| --- | --- |
|

[GetRecommendationItemAsync](#GetRecommendationItemAsync) (itemId :  [string](/docs/en-us/luau/strings) ) :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

[LogActionEvent](#LogActionEvent) (actionType :  [Enum.RecommendationActionType](/docs/en-us/reference/engine/enums/RecommendationActionType) , itemId :  [string](/docs/en-us/luau/strings) , tracingId :  [string](/docs/en-us/luau/strings) , actionEventDetails :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |
|

[LogImpressionEvent](#LogImpressionEvent) (impressionType :  [Enum.RecommendationImpressionType](/docs/en-us/reference/engine/enums/RecommendationImpressionType) , itemId :  [string](/docs/en-us/luau/strings) , tracingId :  [string](/docs/en-us/luau/strings) , impressionEventDetails :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |
|

[LogPreferenceEvent](#LogPreferenceEvent) (preferenceType :  [Enum.RecommendationPreferenceType](/docs/en-us/reference/engine/enums/RecommendationPreferenceType) , targetType :  [Enum.RecommendationPreferenceTargetType](/docs/en-us/reference/engine/enums/RecommendationPreferenceTargetType) , targetId :  [string](/docs/en-us/luau/strings) , tracingId :  [string](/docs/en-us/luau/strings) , itemId :  [string](/docs/en-us/luau/strings) ) : ()

 |
|

[RegisterItemAsync](#RegisterItemAsync) (player :  [Player](/docs/en-us/reference/engine/classes/Player) , registerRecommendationItemsRequest :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |
|

[RemoveItemAsync](#RemoveItemAsync) (itemId :  [string](/docs/en-us/luau/strings) ) : ()

 |
|

[UpdateItemAsync](#UpdateItemAsync) (updateRecommendationItemRequest :  [Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

 |

Inherited Members

58  inherited from [Instance](/docs/en-us/reference/engine/classes/Instance)

6  inherited from [Object](/docs/en-us/reference/engine/classes/Object)

---

API Reference

Methods

GenerateItemListAsync

Yields

Capabilities: Basic

RecommendationService:GenerateItemListAsync (generateRecommendationItemListRequest :[Dictionary](/docs/en-us/luau/tables#dictionaries) ) :[RecommendationPages](/docs/en-us/reference/engine/classes/RecommendationPages)

Parameters

|

generateRecommendationItemListRequest :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Returns

[RecommendationPages](/docs/en-us/reference/engine/classes/RecommendationPages)

Code Samples

Generate a list of recommended items

```

local RecommendationService = game:GetService("RecommendationService")

-- Define the request for generating a recommendation list

local request: GenerateRecommendationItemListRequest = {

	ConfigName = "MaximizeEngagement",

	LocationId = "Lobby",

	PageSize = 10

    -- NOTE: Uncomment and set CustomContexts.UserId for Server script.

    -- No need to set for Local script.

    -- CustomContexts = {

    --     ["UserId"] = tostring(player.UserId),

    -- }

}

-- Call GenerateItemListAsync to get the recommendation pages

local success, recommendationPages = pcall(function()

    return RecommendationService:GenerateItemListAsync(request)

end)

```

Provide feedback

---

GetRecommendationItemAsync

Yields

Capabilities: Basic

RecommendationService:GetRecommendationItemAsync (itemId :[string](/docs/en-us/luau/strings) ) :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Parameters

|

itemId :[string](/docs/en-us/luau/strings)

 |

Returns

[Dictionary](/docs/en-us/luau/tables#dictionaries)

Code Samples

Get a single recommendation item

```

local RecommendationService = game:GetService("RecommendationService")

local function getItem(itemId)

    local success, item = pcall(function()

        return RecommendationService:GetRecommendationItemAsync(itemId)

    end)

    if success and item then

        print("Successfully retrieved item: " .. item.ItemId)

        print("  ReferenceId: " .. item.ReferenceId)

        -- The TracingId will be empty when fetching a single item directly

        if item.Creator then

            print("  CreatorId: " .. tostring(item.Creator.CreatorId))

        end

        if item.CustomTags then

            print("  CustomTags: ")

            for _, customTag in ipairs(item.CustomTags) do

                print("    " .. customTag)

            end

        end

    else

        warn("Failed to retrieve item: " .. itemId .. ". Error: " .. tostring(item))

    end

end

-- Example usage (requires a valid itemId)

-- getItem("some-item-id")

```

Provide feedback

---

LogActionEvent

Capabilities: Basic

RecommendationService:LogActionEvent (

actionType :[Enum.RecommendationActionType](/docs/en-us/reference/engine/enums/RecommendationActionType) , itemId :[string](/docs/en-us/luau/strings) , tracingId :[string](/docs/en-us/luau/strings) , actionEventDetails :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) : ()

Parameters

|

actionType :[Enum.RecommendationActionType](/docs/en-us/reference/engine/enums/RecommendationActionType)

 |
|

itemId :[string](/docs/en-us/luau/strings)

 |
|

tracingId :[string](/docs/en-us/luau/strings)

 |
|

actionEventDetails :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

()

Code Samples

Logging a user action

```

local RecommendationService = game:GetService("RecommendationService")

local function logLike(itemId, tracingId)

    local detail: RecommendationActionEventDetails = {

        ReactionType = "Like",

        Weight = 1.0

    }

    RecommendationService:LogActionEvent(Enum.RecommendationActionType.AddReaction, itemId, tracingId, detail)

    print("Logged 'Like' action for item: " .. itemId)

end

-- Example usage (requires a valid itemId and tracingId from GenerateItemListAsync)

-- logLike("item-id", "tracing-id")

```

Provide feedback

---

LogImpressionEvent

Capabilities: Basic

RecommendationService:LogImpressionEvent (

impressionType :[Enum.RecommendationImpressionType](/docs/en-us/reference/engine/enums/RecommendationImpressionType) , itemId :[string](/docs/en-us/luau/strings) , tracingId :[string](/docs/en-us/luau/strings) , impressionEventDetails :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) : ()

Parameters

|

impressionType :[Enum.RecommendationImpressionType](/docs/en-us/reference/engine/enums/RecommendationImpressionType)

 |
|

itemId :[string](/docs/en-us/luau/strings)

 |
|

tracingId :[string](/docs/en-us/luau/strings)

 |
|

impressionEventDetails :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Default Value: nil |

Returns

()

Code Samples

Log a user impression

```

local RecommendationService = game:GetService("RecommendationService")

local function logView(itemId, tracingId)

    local detail: RecommendationImpressionEventDetails = {

        Duration = 5, -- User viewed for 5 seconds

        ItemPosition = 1,

        DepartureIntent = Enum.RecommendationDepartureIntent.Neutral

    }

    RecommendationService:LogImpressionEvent(Enum.RecommendationImpressionType.View, itemId, tracingId, detail)

    print("Logged 'View' impression for item: " .. itemId)

end

-- Example usage (requires a valid itemId and tracingId from GenerateItemListAsync)

-- logView("some-item-id", "some-tracing-id")

```

Provide feedback

---

LogPreferenceEvent

Capabilities: Basic

RecommendationService:LogPreferenceEvent (

preferenceType :[Enum.RecommendationPreferenceType](/docs/en-us/reference/engine/enums/RecommendationPreferenceType) , targetType :[Enum.RecommendationPreferenceTargetType](/docs/en-us/reference/engine/enums/RecommendationPreferenceTargetType) , targetId :[string](/docs/en-us/luau/strings) , tracingId :[string](/docs/en-us/luau/strings) , itemId :[string](/docs/en-us/luau/strings)

) : ()

Parameters

|

preferenceType :[Enum.RecommendationPreferenceType](/docs/en-us/reference/engine/enums/RecommendationPreferenceType)

 |
|

targetType :[Enum.RecommendationPreferenceTargetType](/docs/en-us/reference/engine/enums/RecommendationPreferenceTargetType)

 |
|

targetId :[string](/docs/en-us/luau/strings)

 |
|

tracingId :[string](/docs/en-us/luau/strings)

 |
|

itemId :[string](/docs/en-us/luau/strings)

 |

Returns

()

Provide feedback

---

RegisterItemAsync

Yields

Capabilities: Basic

RecommendationService:RegisterItemAsync (

player :[Player](/docs/en-us/reference/engine/classes/Player) , registerRecommendationItemsRequest :[Dictionary](/docs/en-us/luau/tables#dictionaries)

) :[Dictionary](/docs/en-us/luau/tables#dictionaries)

Parameters

|

player :[Player](/docs/en-us/reference/engine/classes/Player)

 |
|

registerRecommendationItemsRequest :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Returns

[Dictionary](/docs/en-us/luau/tables#dictionaries)

Code Samples

Register a new item

```

local RecommendationService = game:GetService("RecommendationService")

local storage = game:GetService("ReplicatedStorage")

-- Assume a RemoteFunction named 'RegisterItemRemote' exists in ReplicatedStorage

local registerItemRemote = storage.RegisterItemRemote

registerItemRemote.OnServerInvoke = function(player, refId)

    local request: RegisterRecommendationItemRequest = {

        ContentType = Enum.RecommendationItemContentType.Dynamic,

        ReferenceId = refId,

        Duration = 60,

        Visibility = Enum.RecommendationItemVisibility.Public,

        CustomTags = {"locale:en-us", "seasonal:summer"},

        Attributes = {

			{

				AssetId = 123,

				Description = "test video",

				TrimStartTime = 0,

				TrimEndTime = 10.5

			}

		}

    }

    local success, response = pcall(function()

        return RecommendationService:RegisterItemAsync(player, request)

    end)

    if success and response then

        print("Successfully registered item. ItemId: " .. response.ItemId)

        return response.ItemId

    else

        warn("Failed to register item. Error: " .. tostring(response))

        return nil

    end

end

```

Provide feedback

---

RemoveItemAsync

Yields

Capabilities: Basic

RecommendationService:RemoveItemAsync (itemId :[string](/docs/en-us/luau/strings) ) : ()

Parameters

|

itemId :[string](/docs/en-us/luau/strings)

 |

Returns

()

Code Samples

Remove an item

```

local RecommendationService = game:GetService("RecommendationService")

local function removeItem(itemId)

    local success, err = pcall(function()

        return RecommendationService:RemoveItemAsync(itemId)

    end)

    if success then

        print("Successfully removed item: " .. itemId)

    else

        warn("Failed to remove item: " .. itemId .. ". Error: " .. tostring(err))

    end

end

```

Provide feedback

---

UpdateItemAsync

Yields

Capabilities: Basic

RecommendationService:UpdateItemAsync (updateRecommendationItemRequest :[Dictionary](/docs/en-us/luau/tables#dictionaries) ) : ()

Parameters

|

updateRecommendationItemRequest :[Dictionary](/docs/en-us/luau/tables#dictionaries)

 |

Returns

()

Code Samples

Update an item

```

local RecommendationService = game:GetService("RecommendationService")

local function updateItem(itemId)

    -- Only include the fields you want to update

    local request: UpdateRecommendationItemRequest = {

        ItemId = itemId,

        Visibility = Enum.RecommendationItemVisibility.Private,

        -- NOTE: the whole CustomTags list will be replaced with this new list

        CustomTags = {"updated-tag"}

    }

    local success, err = pcall(function()

        return RecommendationService:UpdateItemAsync(request)

    end)

    if success then

        print("Successfully updated item: " .. itemId)

    else

        warn("Failed to update item: " .. itemId .. ". Error: " .. tostring(err))

    end

end

-- Example usage

-- updateItem("some-item-id-to-update")

```

Provide feedback

---

Jump to

▼

RecommendationService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GenerateItemListAsync()](#GenerateItemListAsync)

[GetRecommendationItemAsync()](#GetRecommendationItemAsync)

[LogActionEvent()](#LogActionEvent)

[LogImpressionEvent()](#LogImpressionEvent)

[LogPreferenceEvent()](#LogPreferenceEvent)

[RegisterItemAsync()](#RegisterItemAsync)

[RemoveItemAsync()](#RemoveItemAsync)

[UpdateItemAsync()](#UpdateItemAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
