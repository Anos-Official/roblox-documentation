<!-- Source: https://create.roblox.com/docs/cloud/guides/usage-messaging -->

Messaging usage guide | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/guides/usage-messaging.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)

# Messaging usage guide

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/guides/usage-messaging.md)

The [Messaging Service API](/docs/cloud/reference/Universe#Cloud_PublishUniverseMessage)  is the Open Cloud equivalent of the Engine [MessagingService](/docs/reference/engine/classes/MessagingService) , which lets you communicate across your game's servers and clients. The Engine API only allows you to write and update scripts manually in Studio for publishing messages, but the Open Cloud API lets you send messages to live servers from external tools to automate and improve your operations workflows.

## [Usage](#usage)[](#usage)

There are several helpful tools that you can build by supporting cross-server communication with the Messaging Service API, including:

-

Announcement Portals : A web portal can be helpful to support sending announcements to all users across servers in your game, such as announcing an upcoming event, an update, and the winner for a competition. On the portal, you can edit a message and click a button that calls the API to send the message out for all users or selected users.

-

Moderation System : A moderation system can help keep your game safe and secure. When detecting a user with inappropriate behavior, you can publish a message to trigger the game server to warn or ban the specific user. You can also use [data stores](/docs/cloud/reference/DataStore)  in the moderation system to add user accounts to a blocklist that prevents them from rejoining.

-

LiveOps Dashboard : LiveOps dashboards are useful tools for managing live events, such as a Halloween party. On the dashboard, you can pre-code an event, update event messages, trigger the event when it's ready, and reward selected users with special items like a virtual crown without updating any of the game's code.

Currently, the API can only target live game servers through HTTP.

## [Limits](#limits)[](#limits)

The Messaging Service API follows the same limits as the Engine [MessagingService](/docs/reference/engine/classes/MessagingService) . Rate limits are shared across both APIs, and usage from both APIs is counted against the same limits.

| Limit | | Description |
| --- | --- |
| Messages sent per game server | | 600 + 240 * (number of players in this game server)  per minute |
| Messages received per topic | | (40 + 80 * number of servers)  per minute |
| Messages received for entire game | | (400 + 200 * number of servers)  per minute |
| Subscriptions allowed per game server | | 20 + 8 * (number of players in this game server) |
| Subscribe requests per game server | | 240 requests per minute |
| Topic size | | 80 characters |
| Message size | | 1,024 characters (1 KiB) |

## [Set up a topic for messaging](#set-up-a-topic-for-messaging)[](#set-up-a-topic-for-messaging)

Before you can publish a message to your game's live servers, you must set up a topic , which is a customized message channel that is accessible from multiple servers. After defining a topic, you subscribe users to the topic in order to receive your incoming messages.

Currently, you can only define a topic in Studio and use the Luau API [MessagingService:SubscribeAsync()](/docs/reference/engine/classes/MessagingService#SubscribeAsync)  to subscribe users to it. The following code sample subscribes any user to a topic when they join the game:

Set up and Subscribe Users to a Topic

```

local MessagingService = game:GetService("MessagingService")

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	-- Define and subscribe to the topic

	local topic = "YourTopic"

	local connection = MessagingService:SubscribeAsync(topic, function(message)

		print(message.Data)

	end)

	player.AncestryChanged:Connect(function()

		-- Unsubscribe from the topic upon player ancestry change

		connection:Disconnect()

	end)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

## [Publish messages to live servers](#publish-messages-to-live-servers)[](#publish-messages-to-live-servers)

After [setting up](#set-up-a-topic-for-messaging)  a topic, publish a message to your game's live servers:

1.

[Create an API key](/docs/cloud/auth/api-keys#create-api-keys)  on [Creator Dashboard](https://create.roblox.com/dashboard/credentials?activeTab=ApiKeysTab)  and copy it somewhere safe. Make sure you perform the following settings:

1.

Add messaging-service  to Access Permissions .

2.

Select a game, and add the universe-messaging-service:publish  operation.

2.

Get the Universe ID  for your game:

1.

Navigate to the [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Find the game that you want to publish your messages to.

3.

Hover over a game's thumbnail, click the ⋯  button, and select Copy Universe ID .

 ![](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Options-Button-Experience-Public.png)

3.

Add the API key and universe to a POST  request, as in this example:

Example Request for Publishing a Message

```

curl -L -X POST 'https://apis.roblox.com/cloud/v2/universes/{universe}:publishMessage' \

-H 'x-api-key: {api-key}' \

-H 'Content-Type: application/json' \

--data '{

 "topic": "your-topic",

 "message": "Hello, everyone!"

}'

```

4.

Send the HTTP request to publish the message.

If your request succeeds, it returns HTTP 200 with an empty response body.

## [Add the Messaging Service API to OAuth 2.0 apps](#add-the-messaging-service-api-to-oauth-20-apps)[](#add-the-messaging-service-api-to-oauth-20-apps)

You can create [OAuth 2.0 applications](/docs/cloud/auth/oauth2-overview)  that allow your users to publish messages to their own live servers.

Third-party app support through OAuth 2.0 is a beta feature that might be subject to changes for future releases.

To use Messaging Service API for your application and request permissions from your users, perform the following settings:

1.

When [registering your application](/docs/cloud/auth/oauth2-registration#register-your-app) , under Permissions , select the universe-messaging-service:publish  scope.

2.

When [implementing the authorization flow](/docs/cloud/auth/oauth2-overview) , include universe-messaging-service:publish  in the scope  parameter of the authorization URL that redirects users back to your application, like the following example:

```

https://apis.roblox.com/oauth/v1/authorize?client_id=816547628409595165403873012&redirect_uri=https://my-app.com/redirect&scope=openid+universe-messaging-service:publish&response_type=Code&prompts=login+consent&nonce=12345&state=6789

```

3.

Request access to the universeId  of the game that the user wants to publish their messages to. Your application can send a POST  request to the [token resources endpoint](/docs/cloud/auth/oauth2-reference#token-exchange)  with the access token, client ID and secret or the code challenge , depending on your [implementation of your authorization flow](/docs/cloud/auth/oauth2-overview#implementing-authorization-flows) , as request parameters to get a list of universeIds  of games that the user granted permission to:

Example Request

```

curl --location --request POST 'https://apis.roblox.com/oauth/v1/token/resources' \

--header 'Content-Type: application/x-www-form-urlencoded' \

--data-urlencode 'token=<access_token>' \

--data-urlencode 'client_id=<client_id>' \

--data-urlencode 'client_secret=<client_secret>'

```

This endpoint returns a list of universeIds  like the following example response:

Example Response

```

{

  "resource_infos": [

    {

      "owner": {

        "id": "1516563360",

        "type": "User"

      },

      "resources": {

        "universe": {

          "ids": ["3828411582"]

        }

      }

    }

  ]

}

```

4.

Your application can now send messages to any game that a user has granted permission. When sending the request, include the access token in the authorization header and the universeId  and topic in the request URI in the following format:

Example Request

```

curl --location --request POST 'https://apis.roblox.com/cloud/v2/universes/{universe}:publishMessage' \

--header 'Authorization: Bearer <access_token>' \

--header 'Content-Type: application/json' \

--data-raw '{"topic": "some-topic","message":"message to publish"}'

```

## [Use with HTTPService](#use-with-httpservice)[](#use-with-httpservice)

This API is one of the [Open Cloud endpoints supported](/docs/cloud-services/http-service#supported-open-cloud-endpoints)  by [HttpService](/docs/reference/engine/classes/HttpService) . You can use it to publish messages across different games from within a game.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
