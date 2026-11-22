<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/datatypes/DateTime -->

DateTime | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Gegevenstypen](/docs/nl-nl/reference/engine/datatypes)
2. /
3. [DateTime](/docs/nl-nl/reference/engine/datatypes/DateTime)

Nederlands

Feedback

Engine-gegevenstype

DateTime

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/datatypes/DateTime)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Constructors

|

[now](#now) ()

 |
| --- | --- |
|

[fromUnixTimestamp](#fromUnixTimestamp) (unixTimestamp :  [number](/docs/nl-nl/luau/numbers) )

 |
|

[fromUnixTimestampMillis](#fromUnixTimestampMillis) (unixTimestampMillis :  [number](/docs/nl-nl/luau/numbers) )

 |
|

[fromUniversalTime](#fromUniversalTime) (year :  [number](/docs/nl-nl/luau/numbers) , month :  [number](/docs/nl-nl/luau/numbers) , day :  [number](/docs/nl-nl/luau/numbers) , hour :  [number](/docs/nl-nl/luau/numbers) , minute :  [number](/docs/nl-nl/luau/numbers) , second :  [number](/docs/nl-nl/luau/numbers) , millisecond :  [number](/docs/nl-nl/luau/numbers) )

 |
|

[fromLocalTime](#fromLocalTime) (year :  [number](/docs/nl-nl/luau/numbers) , month :  [number](/docs/nl-nl/luau/numbers) , day :  [number](/docs/nl-nl/luau/numbers) , hour :  [number](/docs/nl-nl/luau/numbers) , minute :  [number](/docs/nl-nl/luau/numbers) , second :  [number](/docs/nl-nl/luau/numbers) , millisecond :  [number](/docs/nl-nl/luau/numbers) )

 |
|

[fromIsoDate](#fromIsoDate) (isoDate :  [string](/docs/nl-nl/luau/strings) )

 |

Eigenschappen

|

[UnixTimestamp](#UnixTimestamp) :[number](/docs/nl-nl/luau/numbers)

 |
|

[UnixTimestampMillis](#UnixTimestampMillis) :[number](/docs/nl-nl/luau/numbers)

 |

Methoden

|

[ToUniversalTime](#ToUniversalTime) () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

[ToLocalTime](#ToLocalTime) () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

 |
|

[ToIsoDate](#ToIsoDate) () :[string](/docs/nl-nl/luau/strings)

 |
|

[FormatUniversalTime](#FormatUniversalTime) (format :  [string](/docs/nl-nl/luau/strings) , locale :  [string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[FormatLocalTime](#FormatLocalTime) (format :  [string](/docs/nl-nl/luau/strings) , locale :  [string](/docs/nl-nl/luau/strings) ) :[string](/docs/nl-nl/luau/strings)

 |

---

API-referentie

Constructors

now

DateTime.now ()

Feedback geven

---

fromUnixTimestamp

DateTime.fromUnixTimestamp (unixTimestamp :[number](/docs/nl-nl/luau/numbers) )

Parameters

|

unixTimestamp :[number](/docs/nl-nl/luau/numbers)

 |

Feedback geven

---

fromUnixTimestampMillis

DateTime.fromUnixTimestampMillis (unixTimestampMillis :[number](/docs/nl-nl/luau/numbers) )

Parameters

|

unixTimestampMillis :[number](/docs/nl-nl/luau/numbers)

 |

Feedback geven

---

fromUniversalTime

DateTime.fromUniversalTime (

year :[number](/docs/nl-nl/luau/numbers) , month :[number](/docs/nl-nl/luau/numbers) , day :[number](/docs/nl-nl/luau/numbers) , hour :[number](/docs/nl-nl/luau/numbers) , minute :[number](/docs/nl-nl/luau/numbers) , second :[number](/docs/nl-nl/luau/numbers) , millisecond :[number](/docs/nl-nl/luau/numbers) )

Parameters

|

year :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1970 |
|

month :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |
|

day :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |
|

hour :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

minute :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

second :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

millisecond :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |

Feedback geven

---

fromLocalTime

DateTime.fromLocalTime (

year :[number](/docs/nl-nl/luau/numbers) , month :[number](/docs/nl-nl/luau/numbers) , day :[number](/docs/nl-nl/luau/numbers) , hour :[number](/docs/nl-nl/luau/numbers) , minute :[number](/docs/nl-nl/luau/numbers) , second :[number](/docs/nl-nl/luau/numbers) , millisecond :[number](/docs/nl-nl/luau/numbers) )

Parameters

|

year :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1970 |
|

month :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |
|

day :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |
|

hour :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

minute :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

second :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |
|

millisecond :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 0 |

Feedback geven

---

fromIsoDate

DateTime.fromIsoDate (isoDate :[string](/docs/nl-nl/luau/strings) )

Parameters

|

isoDate :[string](/docs/nl-nl/luau/strings)

 |

Feedback geven

---

Eigenschappen

UnixTimestamp

DateTime.UnixTimestamp :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

UnixTimestampMillis

DateTime.UnixTimestampMillis :[number](/docs/nl-nl/luau/numbers)

Feedback geven

---

Methoden

ToUniversalTime

DateTime:ToUniversalTime () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Feedback geven

---

ToLocalTime

DateTime:ToLocalTime () :[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Teruggaves

[Dictionary](/docs/nl-nl/luau/tables#dictionaries)

Feedback geven

---

ToIsoDate

DateTime:ToIsoDate () :[string](/docs/nl-nl/luau/strings)

Teruggaves

[string](/docs/nl-nl/luau/strings)

Feedback geven

---

FormatUniversalTime

DateTime:FormatUniversalTime (

format :[string](/docs/nl-nl/luau/strings) , locale :[string](/docs/nl-nl/luau/strings)

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

format :[string](/docs/nl-nl/luau/strings)

 |
|

locale :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Feedback geven

---

FormatLocalTime

DateTime:FormatLocalTime (

format :[string](/docs/nl-nl/luau/strings) , locale :[string](/docs/nl-nl/luau/strings)

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

format :[string](/docs/nl-nl/luau/strings)

 |
|

locale :[string](/docs/nl-nl/luau/strings)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Feedback geven

---

Ga naar

▼

DateTime

[Samenvatting](#summary)

[Constructors](#summary-constructors)

[Eigenschappen](#summary-properties)

[Methoden](#summary-methods)

[Constructors](#constructors)

[now()](#now)

[fromUnixTimestamp()](#fromUnixTimestamp)

[fromUnixTimestampMillis()](#fromUnixTimestampMillis)

[fromUniversalTime()](#fromUniversalTime)

[fromLocalTime()](#fromLocalTime)

[fromIsoDate()](#fromIsoDate)

[Eigenschappen](#properties)

[UnixTimestamp](#UnixTimestamp)

[UnixTimestampMillis](#UnixTimestampMillis)

[Methoden](#methods)

[ToUniversalTime()](#ToUniversalTime)

[ToLocalTime()](#ToLocalTime)

[ToIsoDate()](#ToIsoDate)

[FormatUniversalTime()](#FormatUniversalTime)

[FormatLocalTime()](#FormatLocalTime)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
