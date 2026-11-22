<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/datatypes/Secret -->

Secret | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/datatypes/Secret.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Data types](/docs/en-us/reference/engine/datatypes)
2. /
3. [Secret](/docs/en-us/reference/engine/datatypes/Secret)

English

Feedback

Engine Data Type

Secret

---

## Summary

Methods

|

[AddPrefix](#AddPrefix) (prefix :  [string](/docs/en-us/luau/strings) ) :[Secret](/docs/en-us/reference/engine/datatypes/Secret)

 |
| --- | --- |
|

[AddSuffix](#AddSuffix) (suffix :  [string](/docs/en-us/luau/strings) ) :[Secret](/docs/en-us/reference/engine/datatypes/Secret)

 |

Code Samples

Secret

```

local HttpService = game:GetService("HttpService")

local mySiteApiKey = HttpService:GetSecret("my_site")

local url = "https://apis.mysite.com?apiKey="

local urlWithKey = mySiteApiKey:AddPrefix(url)

local params = "&request=join&user=myname"

local resultingUrl = urlWithKey:AddSuffix(params)

```

---

API Reference

Methods

AddPrefix

Secret:AddPrefix (prefix :[string](/docs/en-us/luau/strings) ) :[Secret](/docs/en-us/reference/engine/datatypes/Secret)

Parameters

|

prefix :[string](/docs/en-us/luau/strings)

 |

Returns

[Secret](/docs/en-us/reference/engine/datatypes/Secret)

Provide feedback

---

AddSuffix

Secret:AddSuffix (suffix :[string](/docs/en-us/luau/strings) ) :[Secret](/docs/en-us/reference/engine/datatypes/Secret)

Parameters

|

suffix :[string](/docs/en-us/luau/strings)

 |

Returns

[Secret](/docs/en-us/reference/engine/datatypes/Secret)

Provide feedback

---

Jump to

▼

Secret

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[AddPrefix()](#AddPrefix)

[AddSuffix()](#AddSuffix)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
