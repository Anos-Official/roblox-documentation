<!-- Source: https://create.roblox.com/docs/en-us/cloud/guides/experience-notifications -->

User notifications | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/guides/experience-notifications.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Open Cloud API](/docs/en-us/cloud)

# User notifications

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/guides/experience-notifications.md)

Experience notifications  are a way for [opted-in](https://en.help.roblox.com/hc/en-us/articles/24769602332692-Out-of-Experience-Notifications)  users age 13+ to keep up with their favorite games through timely, personalized notifications. As the developer, you can determine what kinds of in-game activities are most important to notify your users about, as well as define the notification content.

Async Activity Progress / Achievement User Mentions

![Example notification](https://prod.docsiteassets.roblox.com/assets/open-cloud/experience-notifications/Example-Notification-A.png)

![Example notification](https://prod.docsiteassets.roblox.com/assets/open-cloud/experience-notifications/Example-Notification-D.png)

After they receive a notification, users can join the experience directly via the Join  button and spawn according to your [launch data](#include-launch-and-analytics-data) .

For more information on features, eligibility requirements, usage guidelines, and the corresponding Engine API, see the [Experiences guide](/docs/en-us/production/promotion/experience-notifications) .

## [Implementation](#implementation)[](#implementation)

The [UserNotification](/docs/en-us/cloud/reference/UserNotification)  resource lets you send experience notifications to users. Before using it, you must [generate an API key](/docs/en-us/cloud/auth/api-keys)  or [configure OAuth 2.0](/docs/en-us/cloud/auth/oauth2-overview)  for your app. The examples on this page use API keys.

To send an experience notification to a user:

1.

[Create a notification string](/docs/en-us/production/promotion/experience-notifications#create-a-notification-string)  in the [Creator Dashboard](https://create.roblox.com/dashboard/creations)  (this step must be done in the Creator Dashboard; there's no Open Cloud API for it).

2.

Form the request:

1.

Copy the API key to the x-api-key  request header.

2.

Copy the notification string asset ID as the value of the payload.message_id  property.

3.

Set payload.type  to "MOMENT" .

4.

Set source.universe  to be the universe resource URL "universes/${UniverseID}" .

Send an experience notification

```

curl --location 'https://apis.roblox.com/cloud/v2/users/${UserId}/notifications' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

	"source": {

		"universe": "universes/${UniverseID}"

	},

	"payload": {

		"message_id": "${AssetID}",

		"type": "MOMENT"

	}

}'

```

Example response which returns the notification ID in the id  field:

```

{

  "path": "users/505306092/notifications/6ca4d981-36fa-4255-82a1-14d95c116889",

  "id": "6ca4d981-36fa-4255-82a1-14d95c116889"

}

```

### [Customize notifications using parameters](#customize-notifications-using-parameters)[](#customize-notifications-using-parameters)

To customize the notification for each recipient, include parameters  in the [notification string](#implementation) . Then customize the parameters when calling the API. For example, you can define the notification string as:

{userId-friend} beat your high score by {points} points! Time to level up?

Add the userId-friend  and points  parameters in the script:

Customize Notification Using Parameters

```

curl --location 'https://apis.roblox.com/cloud/v2/users/${UserId}/notifications' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

	"source": {

		"universe": "universes/${UniverseID}"

	},

	"payload": {

		"message_id": "${AssetID}",

		"type": "MOMENT",

		"parameters": {

			"userId-friend": {"int64_value": 3702832553},

			"points": {"string_value": "5"}

		}

	}

}'

```

### [Include launch and analytics data](#include-launch-and-analytics-data)[](#include-launch-and-analytics-data)

To further improve user experience, you can include launch data  in the notification, useful for scenarios such as routing users to a coordinate location or personalizing the joining experience. Additionally, you can include [analytics](/docs/en-us/production/promotion/experience-notifications#analytics)  data to segment the performance of different categories of notifications.

Include Launch Data and Analytics Data

```

curl --location 'https://apis.roblox.com/cloud/v2/users/${UserId}/notifications' \

--header 'x-api-key: ${ApiKey}' \

--header 'Content-Type: application/json' \

--data '{

	"source": {

		"universe": "universes/${UniverseID}"

	},

	"payload": {

		"message_id": "${AssetID}",

		"type": "MOMENT",

		"join_experience": {

			"launch_data": "Test_Launch_Data"

		},

		"analytics_data": {

			"category": "Test_Analytics_Category"

		}

	}

}'

```

## [Rate limits and delivery](#rate-limits-and-delivery)[](#rate-limits-and-delivery)

Each user can receive one  notification per day from a given experience, and you receive transparent feedback when a user's throttle limit is reached.

There are many other reasons that a notification might not be delivered. For more information, see [Delivery system](/docs/en-us/production/promotion/experience-notifications#delivery-system)  in the Engine guide.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
