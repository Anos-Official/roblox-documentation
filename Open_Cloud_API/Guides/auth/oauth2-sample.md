<!-- Source: https://create.roblox.com/docs/en-us/cloud/auth/oauth2-sample -->

OAuth 2.0 sample app | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/auth/oauth2-sample.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Open Cloud API](/docs/en-us/cloud)
4. /
5. [OAuth 2.0](/docs/en-us/cloud/auth/oauth2-overview)

# OAuth 2.0 sample app

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/auth/oauth2-sample.md)

Roblox provides a Node.js sample app that shows how to use OAuth 2.0 to let users log in to their Roblox accounts and broadcast messages across their games. This app uses the [authorization code flow * without*  PKCE](/docs/en-us/cloud/auth/oauth2-overview#grant-types)  and is thus only suitable for confidential clients, such as private servers.

 [Get the Code](https://prod.docsiteassets.roblox.com/assets/open-cloud/open-cloud-nodejs-sample-oauth2-main.zip)

After downloading the .zip  file, extract it to its own folder.

## [Register the app](#register-the-app)[](#register-the-app)

The first step to setting up the app is to [register it on the Roblox website](/docs/en-us/cloud/auth/oauth2-registration)  and copy the client ID and secret somewhere safe. Then follow the standard registration steps with these settings:

1.

Under Permissions , add the openid , profile , and universe-messaging-service:publish  scopes.

2.

Under Redirect URLs , add the http://localhost:3000/oauth/callback  redirect. If you want to use a non-default port for your app, specify it here.

## [Set environment variables](#set-environment-variables)[](#set-environment-variables)

Rather than storing them in code (not recommended), the app uses environment variables for your client ID and secret. The process for adding environment variables differs by operating system.

On Windows, run the following PowerShell commands:

```

$env:ROBLOX_CLIENT_ID='your_client_id_here'

$env:ROBLOX_CLIENT_SECRET='your_client_secret_here'

$env:ROBLOX_PORT=3000 # Optional. Default is 3000.

```

On Mac and most Linux distributions, run these commands at the terminal:

```

export ROBLOX_CLIENT_ID=your_client_id_here

export ROBLOX_CLIENT_SECRET=your_client_secret_here

export ROBLOX_PORT=3000 # Optional. Default is 3000.

```

If you specified a non-default port in the redirect URL when registering your app, be sure to add the ROBLOX_PORT  variable.

These commands only set environment variables for the duration of your terminal session. If you want to load these variables every time you open a new terminal window, add the commands to your shell configuration file, such as .zshrc  or .bashrc . Many hosting services have features to help you add environment variables to your servers.

## [Install dependencies](#install-dependencies)[](#install-dependencies)

The app has a handful of dependencies, visible in package.json . To install them, run:

```

npm ci

```

## [Run the app](#run-the-app)[](#run-the-app)

To start the app, run:

```

npm start

```

Then navigate to http://localhost:3000  (or your non-default port) in a web browser.

The app immediately redirects you to the Roblox login screen, at which point you can log in, verify the permissions that the app is requesting, and click Confirm and Give Access .

Roblox then redirects you back to localhost , where you can see that the app now displays some minimal user information, a link back to your profile on Roblox, and fields that you can use to broadcast messages across your games.

### [About the app](#about-the-app)[](#about-the-app)

In broad strokes, index.js  performs the following operations:

1.

Starts a new web server using express .

2.

Retrieves the Roblox OpenID Connect (OIDC) configuration, which includes endpoints for authorization, user information, etc. For more information about these endpoints, see [OAuth 2.0 authentication](/docs/en-us/cloud/auth/oauth2-reference) .

3.

Creates a new Open ID client using openid-client  and your stored credentials. This client dramatically simplifies the process of properly forming and sending HTTP requests to the OAuth 2.0 endpoints.

4.

Defines the routes for the app, including redirects for the login and logout flows and the OAuth 2.0 callback.

5.

After a successful login, stores the various tokens as cookies, along with some minimal user information that it displays as HTML with help from getHomeHtml.js .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
