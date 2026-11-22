<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/datatypes/User -->

User | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Gegevenstypen](/docs/nl-nl/reference/engine/datatypes)
2. /
3. [User](/docs/nl-nl/reference/engine/datatypes/User)

Nederlands

Feedback

Engine-gegevenstype

User

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/datatypes/User)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Constructors

|

[fromId](#fromId) (domainUserId :  [number](/docs/nl-nl/luau/numbers) )

 |
| --- | --- |
|

[fromString](#fromString) (userString :  [string](/docs/nl-nl/luau/strings) )

 |

Eigenschappen

|

[Id](#Id) :[number](/docs/nl-nl/luau/numbers)

 |
|

[DomainType](#DomainType) :[Enum.DomainType](/docs/nl-nl/reference/engine/enums/DomainType)

 |
|

[DomainId](#DomainId) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[ToString](#ToString) () :[string](/docs/nl-nl/luau/strings)

 |

Codevoorbeelden

User Serialize Roundtrip

```

-- Serialiseren

local encoded = player.User:ToString()

-- Deserialiseren

local user = User.fromString(encoded)

```

---

API-referentie

Constructors

fromId

User.fromId (domainUserId :[number](/docs/nl-nl/luau/numbers) )

Parameters

|

domainUserId :[number](/docs/nl-nl/luau/numbers)

 |

Feedback geven

---

fromString

User.fromString (userString :[string](/docs/nl-nl/luau/strings) )

Parameters

|

userString :[string](/docs/nl-nl/luau/strings)

 |

Feedback geven

---

Eigenschappen

Id

User.Id :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

DomainType

User.DomainType :[Enum.DomainType](/docs/nl-nl/reference/engine/enums/DomainType)

Feedback geven

---

DomainId

User.DomainId :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

ToString

User:ToString () :[string](/docs/nl-nl/luau/strings)

Teruggaves

[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Ga naar

▼

User

[Samenvatting](#summary)

[Constructors](#summary-constructors)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Constructors](#constructors)

[fromId()](#fromId)

[fromString()](#fromString)

[Eigenschappen](#properties)

[Id](#Id)

[DomainType](#DomainType)

[DomainId](#DomainId)

[Methoden](#methods)

[ToString()](#ToString)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
