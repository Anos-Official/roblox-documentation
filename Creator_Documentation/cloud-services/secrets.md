<!-- Source: https://create.roblox.com/docs/en-us/cloud-services/secrets -->

Secrets stores | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud-services/secrets.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/en-us/cloud-services/data-stores-vs-memory-stores)

# Secrets stores

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud-services/secrets.md)

Roblox offers a secrets  store for each game. Secrets are sensitive information like API keys, passwords, and access tokens that you use to authenticate with external services. For example, if you want to connect to a third-party analytics or music service, you likely need to use an API key to authenticate with it.

You could copy and paste the API key into a script or add it to a data store, but those approaches carry unnecessary security risks. The better solution is to use the secrets store and access the key using a small set of secure methods.

## [Add secrets](#add-secrets)[](#add-secrets)

To view, create, or edit secrets, you must be the game owner or group owner. You can have up to 500 secrets per game.

1.

Navigate to the [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Select your game, and then select Secrets  ⟩ Create Secret .

3.

Enter a name, the secret, and the applicable domain.

-

The name acts as a unique identifier for the secret, so we recommend something descriptive.

-

Secrets can be up to 1,024 characters in length. API keys and access tokens should come from the service provider, but if the secret is a password, you probably created it yourself.

-

You can use a limited wildcard syntax for the domain, such as *  for any domain (not recommended) or *.example.com  for any subdomain at example.com . Specific domains are even better, such as my.example.com .

You can also use Open Cloud to manage your secrets. See the [reference documentation](/docs/en-us/cloud/reference/features/universes#get_cloud_v2_universes__universeId__secrets)  and [guide](/docs/en-us/cloud/guides/secrets-store) .

## [Local secrets](#local-secrets)[](#local-secrets)

For security reasons, the secrets store for each game is only available to live servers or [collaborative testing](/docs/en-us/studio/testing-modes#collaborative-testing)  environments. If you try to access a secret during [local playtesting](/docs/en-us/studio/testing-modes#playtesting) , you receive a Can't find secret with given key  error. You receive an identical error if you try to access secrets from a client script.

To specify secrets for local testing, go to Studio and then go to File  ⟩ Experience Settings  ⟩ Security . You can create new secrets and edit or delete existing secrets in the Local Secrets  section.

## [Use secrets](#use-secrets)[](#use-secrets)

Before using secrets within your game, you must enable Allow HTTP Requests  in the Security  section of Studio's File  ⟩ Experience Settings  window. Then call [HttpService:GetSecret()](/docs/en-us/reference/engine/classes/HttpService#GetSecret)  within a server script:

```

local HttpService = game:GetService("HttpService")

local testSecret = HttpService:GetSecret("test_secret")

```

Part of the appeal of using secret stores is that you can't accidentally print a secret. Instead of the secret itself, the following code outputs the name you provided when creating the secret:

```

print(testSecret) --> Secret(test_secret)

```

You can't manipulate the string directly. Instead, the [Secret](/docs/en-us/reference/engine/datatypes/Secret)  data type lets you add a prefix and suffix to the secret to help form a URL or insert content like Bearer :

```

local HttpService = game:GetService("HttpService")

local testSecret = HttpService:GetSecret("test_secret")

local prefix = "https://my.example.com/endpoint?apiKey="

local suffix = "&user=username"

local url = testSecret:AddPrefix(prefix)

url = url:AddSuffix(suffix)

print(url) --> https://my.example.com/endpoint?apiKey=Secret(test_secret)&user=username

```

After you have a URL with the secret inserted, you can make standard HTTP requests using methods like [HttpService:RequestAsync()](/docs/en-us/reference/engine/classes/HttpService#RequestAsync) . Of course, you can ignore these methods and insert the secret directly into a header, too.

You can't include secrets in the HTTP request body, only the URL and headers.

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
