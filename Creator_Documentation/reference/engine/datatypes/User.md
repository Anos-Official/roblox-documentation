<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/datatypes/User -->

User | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/datatypes/User.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Data types](/docs/en-us/reference/engine/datatypes)
2. /
3. [User](/docs/en-us/reference/engine/datatypes/User)

English

Feedback

Engine Data Type

User

---

## Summary

Constructors

|

[fromId](#fromId) (domainUserId :  [number](/docs/en-us/luau/numbers) )

 |
| --- | --- |
|

[fromString](#fromString) (userString :  [string](/docs/en-us/luau/strings) )

 |

Properties

|

[Id](#Id) :[number](/docs/en-us/luau/numbers)

 |
|

[DomainType](#DomainType) :[Enum.DomainType](/docs/en-us/reference/engine/enums/DomainType)

 |
|

[DomainId](#DomainId) :[number](/docs/en-us/luau/numbers)

 |

Methods

|

[ToString](#ToString) () :[string](/docs/en-us/luau/strings)

 |

Code Samples

User Serialize Roundtrip

```

-- Serialize

local encoded = player.User:ToString()

-- Deserialize

local user = User.fromString(encoded)

```

---

API Reference

Constructors

fromId

User.fromId (domainUserId :[number](/docs/en-us/luau/numbers) )

Parameters

|

domainUserId :[number](/docs/en-us/luau/numbers)

 |

Provide feedback

---

fromString

User.fromString (userString :[string](/docs/en-us/luau/strings) )

Parameters

|

userString :[string](/docs/en-us/luau/strings)

 |

Provide feedback

---

Properties

Id

User.Id :[number](/docs/en-us/luau/numbers)

Provide feedback

---

DomainType

User.DomainType :[Enum.DomainType](/docs/en-us/reference/engine/enums/DomainType)

Provide feedback

---

DomainId

User.DomainId :[number](/docs/en-us/luau/numbers)

Provide feedback

---

Methods

ToString

User:ToString () :[string](/docs/en-us/luau/strings)

Returns

[string](/docs/en-us/luau/strings)

Provide feedback

---

Jump to

▼

User

[Summary](#summary)

[Constructors](#summary-constructors)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Constructors](#constructors)

[fromId()](#fromId)

[fromString()](#fromString)

[Properties](#properties)

[Id](#Id)

[DomainType](#DomainType)

[DomainId](#DomainId)

[Methods](#methods)

[ToString()](#ToString)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
