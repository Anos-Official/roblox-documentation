<!-- Source: https://create.roblox.com/docs/cloud/guides/secrets-store -->

Secrets stores | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/guides/secrets-store.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)

# Secrets stores

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/guides/secrets-store.md)

In addition to [managing your secrets within games](/docs/cloud-services/secrets) , you can manage secrets using the Open Cloud secrets store API.

Before using the API, you must [generate an API key](/docs/cloud/auth/api-keys)  with the secret-store  API system or [configure your OAuth 2.0 app](/docs/cloud/auth/oauth2-overview)  with the universe.secret  scope type. The examples on this page use API keys.

## [Secret encryption](#secret-encryption)[](#secret-encryption)

When creating or updating secrets on Roblox, you must encrypt secrets with a [LibSodium sealed box](https://libsodium.gitbook.io/doc/public-key_cryptography/sealed_boxes)  and your game's public key, and then base64-encode the result.

First, get your game's public key:

```

curl --location 'https://apis.roblox.com/cloud/v2/universes/{universeId}/secrets/public-key' \

--request GET \

--header 'x-api-key: <your-secret-here>' \

```

Next, create a sealed box and base64-encode it. The example below uses Python and [PyNaCl](https://pynacl.readthedocs.io/en/latest/public/#nacl-public-sealedbox) . (Run pip install pynacl  to install it locally).

```

from base64 import b64encode

from nacl import encoding, public

public_key = "Zgj4+V7vSaEZ06rXazKJUIcUnVa95tUNiwXAif/vdHo="

secret_content = "my_api_key_content"

public_key = public.PublicKey(public_key.encode("utf-8"), encoding.Base64Encoder())

sealed_box = public.SealedBox(public_key)

encrypted = sealed_box.encrypt(secret_content.encode("utf-8"))

print(b64encode(encrypted).decode("utf-8"))

```

You can then create or update a secret using the output. This example creates a new secret:

```

curl --location 'https://apis.roblox.com/cloud/v2/universes/6930499524/secrets' \

--request POST \

--header 'Content-Type: application/json' \

--header 'x-api-key: <your-secret-here>' \

--data '{

    "id": "mySecret",

    "secret": "fP9scJkcDk492F4c1VHZ5QS8v2qsAg7uI+NVVEw6zC0GBnj7xpi7UrNr++lCfr4wyq3ia9Uuu+Ao8HtIXz2gRxBX",

    "key_id": "1200590785272263122"

}'

```

After you create one, see [Use secrets](/docs/cloud-services/secrets#use-secrets)  to use your secret in game.

## [Update secrets](#update-secrets)[](#update-secrets)

To update the above secret:

```

curl --location 'https://apis.roblox.com/cloud/v2/universes/6930499524/secrets/mySecret' \

--request PATCH \

--header 'Content-Type: application/json' \

--header 'x-api-key: <your-secret-here>' \

--data '{

    "secret": "2Fczw/PL7woOzHnGHQ65sT0MbzJjEOlfibyKxy374CqzFyEb2QTS8grtNBgG/0sfIvSHEo9JWN+pUr0NTPs0V6lj",

    "key_id": "1200590785272263122"

}'

```

If you need to clean up a secret, a deletion request looks like this:

```

curl --location 'https://apis.roblox.com/cloud/v2/universes/6930499524/secrets/mySecret' \

--request DELETE \

--header 'Content-Type: application/json' \

--header 'x-api-key: <your-secret-here>'

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
