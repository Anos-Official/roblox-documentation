<!-- Source: https://create.roblox.com/docs/cloud/auth/oauth2-overview -->

OAuth 2.0 overview | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/auth/oauth2-overview.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)
4. /
5. [OAuth 2.0](/docs/cloud/auth/oauth2-overview)

# OAuth 2.0 overview

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/auth/oauth2-overview.md)

You can build or authorize apps that use Open Cloud APIs to access Roblox resources. Open Cloud provides authentication for these apps using OAuth 2.0.

As a game creator or group owner

You can securely use tools created by others to improve your creation productivity. The OAuth 2.0 authorization layer allows you to grant permissions to third-party apps to access your or your group's games without giving them your credentials and personal information. You select the access permissions of your specific Roblox resources, and Roblox handles the authorization process for you with the OAuth 2.0 framework.

You must have a 13+ account to authorize OAuth 2.0 apps.

As an app developer

You can create apps for yourself and others in the Roblox community. OAuth 2.0 defines the roles involved in the authorization process, the protocol of how roles interact with each other, and the authorization flows that you need to follow to develop secure and compatible apps.

You must be [ID verified](/docs/production/publishing/account-verification#verify-through-government-id)  to register and publish OAuth 2.0 apps.

## [Roles](#roles)[](#roles)

The Open Cloud OAuth 2.0 protocol has the following roles. It's useful to understand the specific roles before learning about how they interact with one another in authorization flows.

-

Resource owner : An entity capable of granting access to a protected resource. For example, a creator who allows a third-party app to access their Roblox resources through Open Cloud Web APIs.

-

Resource server : A Roblox service that hosts protected resources and responds to requests from a resource owner.

-

Client : An app that accesses protected resources on behalf of the resource owner (with the owner's authorization).

-

Authorization server : The Roblox server that authenticates the identity of the resource owner and issues access tokens to the client.

## [Grant types](#grant-types)[](#grant-types)

Authorization flows, or grant types, are the steps of actions that roles perform during the authorization process. Roblox supports the OAuth 2.0 authorization code flow and its Proof Key for Code Exchange (PKCE) extension, with different implementation requirements for apps that are capable or incapable of storing client secrets.

### [Authorization code flow](#authorization-code-flow)[](#authorization-code-flow)

Through the authorization code flow, a client exchanges an authorization code for an access token and a refresh token to complete the authorization process in the following steps:

1.

The client sends an authorization request to the Roblox authorization server.

2.

The authorization server verifies the identity of the resource owner.

3.

The authorization server receives permissions for accessing specific Roblox resources from the resource owner.

4.

The authorization server redirects the resource owner back to the client with an authorization code.

5.

The client requests an access token using the authorization code at the token endpoint.

6.

The client receives a response from the token endpoint containing an access token, an ID token, and a refresh token.

7.

The client retrieves the permitted resources after getting the access token.

The following figure describes the interactions between roles in the authorization code flow that you'll read in the following sections:

 ![](https://prod.docsiteassets.roblox.com/assets/open-cloud/protocol-flow.png)

### [Authorization code flow with PKCE](#authorization-code-flow-with-pkce)[](#authorization-code-flow-with-pkce)

The [PKCE extension](https://www.rfc-editor.org/rfc/rfc7636)  of the authorization code flow helps reduce risk of leaking the authorization code and prevent cross-site request forgery (CSRF), an attack that tricks users into submitting unintended web requests. This flow completes the authorization process with the following steps:

1.

The client generates a unique and cryptographically random key called a * code verifier*  for every authorization request.

2.

The client runs a SHA-256 hash algorithm on the code verifier to generate a * code challenge* .

3.

If the client:

-

Is a [public client](/docs/cloud/auth/oauth2-develop#public-clients) , instead of using the client secret, it passes the client ID and the code challenge in the authorization request.

-

Is a [confidential client](/docs/cloud/auth/oauth2-develop#confidential-clients) , it adds the code challenge along with the client ID and secret in the request.

4.

The client sends an authorization request to the Roblox authorization server.

5.

The authorization server verifies the identity of the resource owner.

6.

The authorization server receives permissions for accessing specific Roblox resources from the resource owner.

7.

The authorization server redirects the resource owner back to the client with an authorization code.

8.

The client includes the authorization code and the original code verifier in the token request to the [token endpoint](/docs/cloud/auth/oauth2-reference#token-exchange) .

9.

The authorization server verifies the authorization code and the associated code verifier.

10.

The client receives a response from the token endpoint containing an access token, an ID token, and a refresh token.

11.

The client retrieves the permitted resources after getting the access token.

## [OpenID Connect support](#openid-connect-support)[](#openid-connect-support)

Roblox uses [OpenID Connect (OIDC)](https://openid.net/connect/)  as an identity layer on top of the OAuth 2.0 protocol for authentication to protect sensitive account information. OIDC allows applications to verify the identity of users and obtain their basic public profile information, such as user ID, usernames, display names, and profile links.

When [adding permission scopes](/docs/cloud/auth/oauth2-registration#register-an-app)  to your app on Creator Dashboard , make sure to select the openid  identity scope for receiving an ID token in the token response as part of the authentication process.

## [Registration and implementation](#registration-and-implementation)[](#registration-and-implementation)

To implement a web or mobile app that uses authorization code flow, you need to:

1.

[Register](/docs/cloud/auth/oauth2-registration)  your app with Roblox. This lets you obtain a client ID and secret to register your app with Roblox and make calls to your endpoints.

2.

[Implement](/docs/cloud/auth/oauth2-develop)  the authorization code flow. For a complete reference of the OAuth 2.0 endpoints that you need to call, see the [Authentication](/docs/cloud/auth/oauth2-reference)  reference.

3.

Go through the [review process](/docs/cloud/auth/oauth2-registration#submit-for-review)  to get more user quota.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
