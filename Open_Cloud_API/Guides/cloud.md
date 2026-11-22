<!-- Source: https://create.roblox.com/docs/en-us/cloud -->

Cloud API reference | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Open Cloud API](/docs/en-us/cloud)

# Cloud API reference

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/index.md)

With Open Cloud, you can access Roblox resources through standard [REST](https://en.wikipedia.org/wiki/REST)  APIs, which lets you build everything from command line automation tools to complex web apps. You can update games, restart servers, work with your data stores and memory stores, manage user restrictions, list inventory items, and much, much more.

This reference is broken into two sections:

-

A [section that separates endpoints by feature](/docs/en-us/cloud/reference/features/accounts)  (Avatars, Game Passes, Users, etc.)

-

A [section that separates endpoints by domain](/docs/en-us/cloud/reference/domains/apis)  (base URL)

Both sections  contain the full list of available API endpoints. We recommend the [features section](/docs/en-us/cloud/reference/features/accounts)  since it helps consolidate endpoints by use case, but experienced Open Cloud developers might prefer to browse by domain.

-

Whenever possible, use endpoints that support [API keys](/docs/en-us/cloud/auth/api-keys)  or [OAuth 2.0](/docs/en-us/cloud/auth/oauth2-overview)  for authentication. They have strong stability guarantees and receive regular updates.

-

Legacy APIs use cookie-based authentication, can incorporate breaking changes without notice, and have minimal stability guarantees. We don't recommend them for production applications.

Roblox also offers [webhooks](/docs/en-us/cloud/webhooks/webhook-notifications) , which can notify your applications when certain events occur, such as refunds or changes to subscriptions.

## [Get started with Open Cloud](#get-started-with-open-cloud)[](#get-started-with-open-cloud)

1.

Set up authentication for your application.

See the documentation for how to use [API keys](/docs/en-us/cloud/auth/api-keys)  or [OAuth 2.0](/docs/en-us/cloud/auth/oauth2-overview) . API keys are the easiest way to get started.

2.

Test API calls using tools like [Postman](https://www.postman.com)  with [OpenAPI descriptions](/docs/en-us/cloud/reference/openapi)  or the [OAuth 2.0 sample app](/docs/en-us/cloud/auth/oauth2-sample) .

3.

Review the [resource guides](/docs/en-us/cloud/guides)  for end-to-end walkthroughs of using certain APIs.

4.

Explore the left navigation for the full list of features, [common API patterns](/docs/en-us/cloud/reference/patterns) , [types](/docs/en-us/cloud/reference/types) , and [error codes](/docs/en-us/cloud/reference/errors) .

## [Make requests within games](#make-requests-within-games)[](#make-requests-within-games)

[HttpService](/docs/en-us/reference/engine/classes/HttpService)  lets you make HTTP requests to a subset of the Open Cloud endpoints. For more information, see [In-game HTTP requests](/docs/en-us/cloud-services/http-service) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
