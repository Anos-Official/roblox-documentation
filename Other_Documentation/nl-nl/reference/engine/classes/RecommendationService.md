<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/RecommendationService -->

RecommendationService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [RecommendationService](/docs/nl-nl/reference/engine/classes/RecommendationService)

Nederlands

Feedback

Engine-klasse

RecommendationService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/RecommendationService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[GenerateItemListAsync](#GenerateItemListAsync) (generateRecommendationItemListRequest :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[RecommendationPages](/docs/nl-nl/reference/engine/classes/RecommendationPages)

 |
| --- | --- |
|

[GetRecommendationItemAsync](#GetRecommendationItemAsync) (itemId :  [string](/docs/nl-nl/luau/strings) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

[LogActionEvent](#LogActionEvent) (actionType :  [Enum.RecommendationActionType](/docs/nl-nl/reference/engine/enums/RecommendationActionType) , itemId :  [string](/docs/nl-nl/luau/strings) , tracingId :  [string](/docs/nl-nl/luau/strings) , actionEventDetails :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[LogImpressionEvent](#LogImpressionEvent) (impressionType :  [Enum.RecommendationImpressionType](/docs/nl-nl/reference/engine/enums/RecommendationImpressionType) , itemId :  [string](/docs/nl-nl/luau/strings) , tracingId :  [string](/docs/nl-nl/luau/strings) , impressionEventDetails :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |
|

[LogPreferenceEvent](#LogPreferenceEvent) (preferenceType :  [Enum.RecommendationPreferenceType](/docs/nl-nl/reference/engine/enums/RecommendationPreferenceType) , targetType :  [Enum.RecommendationPreferenceTargetType](/docs/nl-nl/reference/engine/enums/RecommendationPreferenceTargetType) , targetId :  [string](/docs/nl-nl/luau/strings) , tracingId :  [string](/docs/nl-nl/luau/strings) , itemId :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[RegisterItemAsync](#RegisterItemAsync) (player :  [Player](/docs/nl-nl/reference/engine/classes/Player) , registerRecommendationItemsRequest :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

[RemoveItemAsync](#RemoveItemAsync) (itemId :  [string](/docs/nl-nl/luau/strings) ) : ()

 |
|

[UpdateItemAsync](#UpdateItemAsync) (updateRecommendationItemRequest :  [Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

GenerateItemListAsync

Opbrengst

Mogelijkheden: Basic

RecommendationService:GenerateItemListAsync (generateRecommendationItemListRequest :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) :[RecommendationPages](/docs/nl-nl/reference/engine/classes/RecommendationPages)

Parameters

|

generateRecommendationItemListRequest :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

[RecommendationPages](/docs/nl-nl/reference/engine/classes/RecommendationPages)

Codevoorbeelden

Genereer een lijst met aanbevolen items

```

local RecommendationService = game:GetService("RecommendationService")

-- Definieer het verzoek voor het genereren van een aanbevelingslijst

local request: GenerateRecommendationItemListRequest = {

	ConfigName = "MaximizeEngagement",

	LocationId = "Lobby",

	PageSize = 10

    -- OPMERKING: Verwijder de opmerkingen en stel CustomContexts.UserId in voor Server-script.

    -- Niet nodig om in te stellen voor Local-script.

    -- CustomContexts = {

    --     ["UserId"] = tostring(player.UserId),

    -- }

}

-- Roep GenerateItemListAsync aan om de aanbevelingspagina's te krijgen

local success, recommendationPages = pcall(function()

    return RecommendationService:GenerateItemListAsync(request)

end)

```

Feedback geven

---

GetRecommendationItemAsync

Opbrengst

Mogelijkheden: Basic

RecommendationService:GetRecommendationItemAsync (itemId :[string](/docs/nl-nl/luau/strings) ) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Parameters

|

itemId :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Codevoorbeelden

Krijg een enkel aanbevelingsitem

```

local RecommendationService = game:GetService("RecommendationService")

local function getItem(itemId)

    local success, item = pcall(function()

        return RecommendationService:GetRecommendationItemAsync(itemId)

    end)

    if success and item then

        print("Item succesvol opgehaald: " .. item.ItemId)

        print("  ReferenceId: " .. item.ReferenceId)

        -- De TracingId is leeg bij het ophalen van een enkel item direct

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

        warn("Mislukt om item op te halen: " .. itemId .. ". Fout: " .. tostring(item))

    end

end

-- Voorbeeldgebruik (vereist een geldige itemId)

-- getItem("some-item-id")

```

Feedback geven

---

LogActionEvent

Mogelijkheden: Basic

RecommendationService:LogActionEvent (

actionType :[Enum.RecommendationActionType](/docs/nl-nl/reference/engine/enums/RecommendationActionType) , itemId :[string](/docs/nl-nl/luau/strings) , tracingId :[string](/docs/nl-nl/luau/strings) , actionEventDetails :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : ()

Parameters

|

actionType :[Enum.RecommendationActionType](/docs/nl-nl/reference/engine/enums/RecommendationActionType)

 |
|

itemId :[string](/docs/nl-nl/luau/strings)

 |
|

tracingId :[string](/docs/nl-nl/luau/strings)

 |
|

actionEventDetails :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

()

Codevoorbeelden

Een gebruikersactie loggen

```

local RecommendationService = game:GetService("RecommendationService")

local function logLike(itemId, tracingId)

    local detail: RecommendationActionEventDetails = {

        ReactionType = "Like",

        Weight = 1.0

    }

    RecommendationService:LogActionEvent(Enum.RecommendationActionType.AddReaction, itemId, tracingId, detail)

    print("'Like' actie gelogd voor item: " .. itemId)

end

-- Voorbeeldgebruik (vereist een geldige itemId en tracingId van GenerateItemListAsync)

-- logLike("item-id", "tracing-id")

```

Feedback geven

---

LogImpressionEvent

Mogelijkheden: Basic

RecommendationService:LogImpressionEvent (

impressionType :[Enum.RecommendationImpressionType](/docs/nl-nl/reference/engine/enums/RecommendationImpressionType) , itemId :[string](/docs/nl-nl/luau/strings) , tracingId :[string](/docs/nl-nl/luau/strings) , impressionEventDetails :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) : ()

Parameters

|

impressionType :[Enum.RecommendationImpressionType](/docs/nl-nl/reference/engine/enums/RecommendationImpressionType)

 |
|

itemId :[string](/docs/nl-nl/luau/strings)

 |
|

tracingId :[string](/docs/nl-nl/luau/strings)

 |
|

impressionEventDetails :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Standaardwaarde: nil |

Teruggaves

()

Codevoorbeelden

Log een gebruikersindruk

```

local RecommendationService = game:GetService("RecommendationService")

local function logView(itemId, tracingId)

    local detail: RecommendationImpressionEventDetails = {

        Duration = 5, -- Gebruiker heeft 5 seconden bekeken

        ItemPosition = 1,

        DepartureIntent = Enum.RecommendationDepartureIntent.Neutral

    }

    RecommendationService:LogImpressionEvent(Enum.RecommendationImpressionType.View, itemId, tracingId, detail)

    print("'View' indruk gelogd voor item: " .. itemId)

end

-- Voorbeeldgebruik (vereist een geldige itemId en tracingId van GenerateItemListAsync)

-- logView("some-item-id", "some-tracing-id")

```

Feedback geven

---

LogPreferenceEvent

Mogelijkheden: Basic

RecommendationService:LogPreferenceEvent (

preferenceType :[Enum.RecommendationPreferenceType](/docs/nl-nl/reference/engine/enums/RecommendationPreferenceType) , targetType :[Enum.RecommendationPreferenceTargetType](/docs/nl-nl/reference/engine/enums/RecommendationPreferenceTargetType) , targetId :[string](/docs/nl-nl/luau/strings) , tracingId :[string](/docs/nl-nl/luau/strings) , itemId :[string](/docs/nl-nl/luau/strings)

) : ()

Parameters

|

preferenceType :[Enum.RecommendationPreferenceType](/docs/nl-nl/reference/engine/enums/RecommendationPreferenceType)

 |
|

targetType :[Enum.RecommendationPreferenceTargetType](/docs/nl-nl/reference/engine/enums/RecommendationPreferenceTargetType)

 |
|

targetId :[string](/docs/nl-nl/luau/strings)

 |
|

tracingId :[string](/docs/nl-nl/luau/strings)

 |
|

itemId :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Feedback geven

---

RegisterItemAsync

Opbrengst

Mogelijkheden: Basic

RecommendationService:RegisterItemAsync (

player :[Player](/docs/nl-nl/reference/engine/classes/Player) , registerRecommendationItemsRequest :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

) :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Parameters

|

player :[Player](/docs/nl-nl/reference/engine/classes/Player)

 |
|

registerRecommendationItemsRequest :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Codevoorbeelden

Registreer een nieuw item

```

local RecommendationService = game:GetService("RecommendationService")

local storage = game:GetService("ReplicatedStorage")

-- Neem aan dat er een RemoteFunction genaamd 'RegisterItemRemote' bestaat in ReplicatedStorage

local registerItemRemote = storage.RegisterItemRemote

registerItemRemote.OnServerInvoke = function(player, refId)

    local request: RegisterRecommendationItemRequest = {

        ContentType = Enum.RecommendationItemContentType.Dynamic,

        ReferenceId = refId,

        Duration = 60,

        Visibility = Enum.RecommendationItemVisibility.Public,

        CustomTags = {"locale:en-nl", "seasonal:summer"},

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

        print("Item succesvol geregistreerd. ItemId: " .. response.ItemId)

        return response.ItemId

    else

        warn("Registratie van item mislukt. Fout: " .. tostring(response))

        return nil

    end

end

```

Feedback geven

---

RemoveItemAsync

Opbrengst

Mogelijkheden: Basic

RecommendationService:RemoveItemAsync (itemId :[string](/docs/nl-nl/luau/strings) ) : ()

Parameters

|

itemId :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

()

Codevoorbeelden

Verwijder een item

```

local RecommendationService = game:GetService("RecommendationService")

local function removeItem(itemId)

    local success, err = pcall(function()

        return RecommendationService:RemoveItemAsync(itemId)

    end)

    if success then

        print("Item succesvol verwijderd: " .. itemId)

    else

        warn("Verwijderen van item mislukt: " .. itemId .. ". Fout: " .. tostring(err))

    end

end

```

Feedback geven

---

UpdateItemAsync

Opbrengst

Mogelijkheden: Basic

RecommendationService:UpdateItemAsync (updateRecommendationItemRequest :[Dictionary](/docs/nl-nl/luau/tables#dictionaries) ) : ()

Parameters

|

updateRecommendationItemRequest :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |

Teruggaves

()

Codevoorbeelden

Een item bijwerken

```

local RecommendationService = game:GetService("RecommendationService")

local function updateItem(itemId)

    -- Alleen de velden opnemen die je wilt bijwerken

    local request: UpdateRecommendationItemRequest = {

        ItemId = itemId,

        Visibility = Enum.RecommendationItemVisibility.Private,

        -- OPMERKING: de hele CustomTags-lijst wordt vervangen door deze nieuwe lijst

        CustomTags = {"updated-tag"}

    }

    local success, err = pcall(function()

        return RecommendationService:UpdateItemAsync(request)

    end)

    if success then

        print("Item succesvol bijgewerkt: " .. itemId)

    else

        warn("Bijwerken van item mislukt: " .. itemId .. ". Fout: " .. tostring(err))

    end

end

-- Voorbeeldgebruik

-- updateItem("some-item-id-to-update")

```

Feedback geven

---

Ga naar

▼

RecommendationService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[GenerateItemListAsync()](#GenerateItemListAsync)

[GetRecommendationItemAsync()](#GetRecommendationItemAsync)

[LogActionEvent()](#LogActionEvent)

[LogImpressionEvent()](#LogImpressionEvent)

[LogPreferenceEvent()](#LogPreferenceEvent)

[RegisterItemAsync()](#RegisterItemAsync)

[RemoveItemAsync()](#RemoveItemAsync)

[UpdateItemAsync()](#UpdateItemAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
