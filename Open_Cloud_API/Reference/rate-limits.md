<!-- Source: https://create.roblox.com/docs/cloud/reference/rate-limits -->

Rate limits | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/reference/rate-limits.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)
4. /
5. [Common components](/docs/cloud/reference/patterns)

# Rate limits

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/reference/rate-limits.md)

Rate limits control the number of requests you can make to endpoints within a specific time window. These limits help ensure service stability and protect Roblox resources from abuse.

## [Discovery](#discovery)[](#discovery)

There are two ways to determine rate limits: the reference documentation and response headers.

### [Documentation pages](#documentation-pages)[](#documentation-pages)

Public rate limits can be found under the Limits  section for each endpoint on their documentation pages. View these sections to understand the rate limits that apply before making requests.

We strive to be as transparent as possible about rate limits, but additional, undocumented limits may apply, including for DDoS protection and service stability. Always ensure your application handles HTTP 429 rate limit responses. See [Handling rate limits](#handling-rate-limits)  for guidance.

If you hit an undocumented rate limit that blocks your use case (or you would like higher limits for an endpoint), please leave feedback explaining your needs in the [Developer Forum](https://devforum.roblox.com/) .

### [Response headers](#response-headers)[](#response-headers)

Many API responses include headers that provide information about your current rate limit status.

| Header | | Description |
| --- | --- |
| x-ratelimit-limit | | The total number of requests allowed within the rate limit window. This may include multiple limit values for different time windows. |
| x-ratelimit-remaining | | The number of requests you can still make with your current authentication. When this reaches 0, you receive HTTP 429 responses. |
| x-ratelimit-reset | | The number of seconds remaining until your rate limit quota resets to the full limit. |

Here's an example of rate limit headers in an API response:

```

x-ratelimit-limit: 1000, 1000;w=60, 1000;w=60

x-ratelimit-remaining: 998

x-ratelimit-reset: 20

```

In this example:

-

You have 998 requests remaining out of your total limit.

-

Your quota will reset in 20 seconds.

## [Behavior](#behavior)[](#behavior)

Rate limit behavior differs by authentication method and request origin, including whether you make requests from within a Roblox game.

### [API key](#api-key)[](#api-key)

Rate limits for API keys are applied across all API keys per owner, which can be either a user or a group. These limits are enforced consistently regardless of where the requests originate—whether from [HttpService](/docs/reference/engine/classes/HttpService) , web applications, or other sources.

#### [In-game with HttpService](#in-game-with-httpservice)[](#in-game-with-httpservice)

When calling endpoints in-game using [HttpService](/docs/reference/engine/classes/HttpService) , requests also contribute to the fixed limit of 500 HTTP requests per minute per Roblox game server. See [In-game HTTP requests](/docs/cloud-services/http-service)  for more details.

### [OAuth 2.0](#oauth-20)[](#oauth-20)

OAuth 2.0 rate limits are applied per access token. Since each access token represents a unique combination of user and application, every user using your app receives their own independent rate limit quota.

## [Handling rate limits](#handling-rate-limits)[](#handling-rate-limits)

Write your code to expect and handle HTTP 429 (Too Many Requests) responses due to documented limits, abuse prevention, or high-load scenarios. When rate limited, check the retry-after  response header as a guideline for when to retry. If there is no retry-after  response header present, implement an exponential backoff retry strategy.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
