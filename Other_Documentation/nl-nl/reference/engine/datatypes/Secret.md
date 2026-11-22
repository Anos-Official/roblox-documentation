<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/datatypes/Secret -->

Secret | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Gegevenstypen](/docs/nl-nl/reference/engine/datatypes)
2. /
3. [Secret](/docs/nl-nl/reference/engine/datatypes/Secret)

Nederlands

Feedback

Engine-gegevenstype

Secret

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/datatypes/Secret)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[AddPrefix](#AddPrefix) (prefix :  [string](/docs/nl-nl/luau/strings) ) :[Secret](/docs/nl-nl/reference/engine/datatypes/Secret)

 |
| --- | --- |
|

[AddSuffix](#AddSuffix) (suffix :  [string](/docs/nl-nl/luau/strings) ) :[Secret](/docs/nl-nl/reference/engine/datatypes/Secret)

 |

Codevoorbeelden

Geheim

```

local HttpService = game:GetService("HttpService")

local mySiteApiKey = HttpService:GetSecret("my_site")

local url = "https://apis.mysite.com?apiKey="

local urlWithKey = mySiteApiKey:AddPrefix(url)

local params = "&request=join&user=myname"

local resultingUrl = urlWithKey:AddSuffix(params)

```

---

API-referentie

Methoden

AddPrefix

Secret:AddPrefix (prefix :[string](/docs/nl-nl/luau/strings) ) :[Secret](/docs/nl-nl/reference/engine/datatypes/Secret)

Parameters

|

prefix :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Secret](/docs/nl-nl/reference/engine/datatypes/Secret)

Feedback geven

---

AddSuffix

Secret:AddSuffix (suffix :[string](/docs/nl-nl/luau/strings) ) :[Secret](/docs/nl-nl/reference/engine/datatypes/Secret)

Parameters

|

suffix :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[Secret](/docs/nl-nl/reference/engine/datatypes/Secret)

Feedback geven

---

Ga naar

▼

Secret

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[AddPrefix()](#AddPrefix)

[AddSuffix()](#AddSuffix)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
