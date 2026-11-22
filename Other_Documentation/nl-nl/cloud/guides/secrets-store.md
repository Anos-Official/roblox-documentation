<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/guides/secrets-store -->

Geheimenopslag | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Geheimenopslag

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In aanvulling op [het beheren van je geheimen binnen games](/docs/nl-nl/cloud-services/secrets) , kun je geheimen beheren met behulp van de Open Cloud secrets store API.

Voordat je de API gebruikt, moet je [een API-sleutel genereren](/docs/nl-nl/cloud/auth/api-keys)  met het secret-store  API-systeem of [je OAuth 2.0-app configureren](/docs/nl-nl/cloud/auth/oauth2-overview)  met het universe.secret  scope-type. De voorbeelden op deze pagina gebruiken API-sleutels.

## [Geheimencryptie](#geheimencryptie)[](#geheimencryptie)

Bij het maken of bijwerken van geheimen op Roblox, moet je geheimen versleutelen met een [LibSodium sealed box](https://libsodium.gitbook.io/doc/public-key_cryptography/sealed_boxes)  en de openbare sleutel van je game, en vervolgens het resultaat base64-encoderen.

Eerst, haal de openbare sleutel van je game op:

```

curl --location 'https://apis.roblox.com/cloud/v2/universes/{universeId}/secrets/public-key' \

--request GET \

--header 'x-api-key: <your-secret-here>' \

```

Vervolgens, maak een sealed box en base64-codeer deze. Het onderstaande voorbeeld gebruikt Python en [PyNaCl](https://pynacl.readthedocs.io/en/latest/public/#nacl-public-sealedbox) . (Voer pip install pynacl  uit om het lokaal te installeren).

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

Je kunt vervolgens een geheim maken of bijwerken met de output. Dit voorbeeld maakt een nieuw geheim aan:

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

Nadat je er een hebt gemaakt, zie [Gebruik geheimen](/docs/nl-nl/cloud-services/secrets#geheimen-gebruiken)  om je geheim in de game te gebruiken.

## [Geheimen bijwerken](#geheimen-bijwerken)[](#geheimen-bijwerken)

Om het bovenstaande geheim bij te werken:

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

Als je een geheim wilt opruimen, ziet een verwijderingsverzoek er als volgt uit:

```

curl --location 'https://apis.roblox.com/cloud/v2/universes/6930499524/secrets/mySecret' \

--request DELETE \

--header 'Content-Type: application/json' \

--header 'x-api-key: <your-secret-here>'

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
