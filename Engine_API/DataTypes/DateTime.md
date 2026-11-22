<!-- Source: https://create.roblox.com/docs/reference/engine/datatypes/DateTime -->

DateTime | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/datatypes/DateTime.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Data types](/docs/reference/engine/datatypes)
2. /
3. [DateTime](/docs/reference/engine/datatypes/DateTime)

English

Feedback

Engine Data Type

DateTime

---

## Summary

Constructors

|

[now](#now) ()

 |
| --- | --- |
|

[fromUnixTimestamp](#fromUnixTimestamp) (unixTimestamp :  [number](/docs/luau/numbers) )

 |
|

[fromUnixTimestampMillis](#fromUnixTimestampMillis) (unixTimestampMillis :  [number](/docs/luau/numbers) )

 |
|

[fromUniversalTime](#fromUniversalTime) (year :  [number](/docs/luau/numbers) , month :  [number](/docs/luau/numbers) , day :  [number](/docs/luau/numbers) , hour :  [number](/docs/luau/numbers) , minute :  [number](/docs/luau/numbers) , second :  [number](/docs/luau/numbers) , millisecond :  [number](/docs/luau/numbers) )

 |
|

[fromLocalTime](#fromLocalTime) (year :  [number](/docs/luau/numbers) , month :  [number](/docs/luau/numbers) , day :  [number](/docs/luau/numbers) , hour :  [number](/docs/luau/numbers) , minute :  [number](/docs/luau/numbers) , second :  [number](/docs/luau/numbers) , millisecond :  [number](/docs/luau/numbers) )

 |
|

[fromIsoDate](#fromIsoDate) (isoDate :  [string](/docs/luau/strings) )

 |

Properties

|

[UnixTimestamp](#UnixTimestamp) :[number](/docs/luau/numbers)

 |
|

[UnixTimestampMillis](#UnixTimestampMillis) :[number](/docs/luau/numbers)

 |

Methods

|

[ToUniversalTime](#ToUniversalTime) () :[Dictionary](/docs/luau/tables#dictionaries)

 |
|

[ToLocalTime](#ToLocalTime) () :[Dictionary](/docs/luau/tables#dictionaries)

 |
|

[ToIsoDate](#ToIsoDate) () :[string](/docs/luau/strings)

 |
|

[FormatUniversalTime](#FormatUniversalTime) (format :  [string](/docs/luau/strings) , locale :  [string](/docs/luau/strings) ) :[string](/docs/luau/strings)

 |
|

[FormatLocalTime](#FormatLocalTime) (format :  [string](/docs/luau/strings) , locale :  [string](/docs/luau/strings) ) :[string](/docs/luau/strings)

 |

---

API Reference

Constructors

now

DateTime.now ()

Provide feedback

---

fromUnixTimestamp

DateTime.fromUnixTimestamp (unixTimestamp :[number](/docs/luau/numbers) )

Parameters

|

unixTimestamp :[number](/docs/luau/numbers)

 |

Provide feedback

---

fromUnixTimestampMillis

DateTime.fromUnixTimestampMillis (unixTimestampMillis :[number](/docs/luau/numbers) )

Parameters

|

unixTimestampMillis :[number](/docs/luau/numbers)

 |

Provide feedback

---

fromUniversalTime

DateTime.fromUniversalTime (

year :[number](/docs/luau/numbers) , month :[number](/docs/luau/numbers) , day :[number](/docs/luau/numbers) , hour :[number](/docs/luau/numbers) , minute :[number](/docs/luau/numbers) , second :[number](/docs/luau/numbers) , millisecond :[number](/docs/luau/numbers) )

Parameters

|

year :[number](/docs/luau/numbers)

Default Value: 1970 |
|

month :[number](/docs/luau/numbers)

Default Value: 1 |
|

day :[number](/docs/luau/numbers)

Default Value: 1 |
|

hour :[number](/docs/luau/numbers)

Default Value: 0 |
|

minute :[number](/docs/luau/numbers)

Default Value: 0 |
|

second :[number](/docs/luau/numbers)

Default Value: 0 |
|

millisecond :[number](/docs/luau/numbers)

Default Value: 0 |

Provide feedback

---

fromLocalTime

DateTime.fromLocalTime (

year :[number](/docs/luau/numbers) , month :[number](/docs/luau/numbers) , day :[number](/docs/luau/numbers) , hour :[number](/docs/luau/numbers) , minute :[number](/docs/luau/numbers) , second :[number](/docs/luau/numbers) , millisecond :[number](/docs/luau/numbers) )

Parameters

|

year :[number](/docs/luau/numbers)

Default Value: 1970 |
|

month :[number](/docs/luau/numbers)

Default Value: 1 |
|

day :[number](/docs/luau/numbers)

Default Value: 1 |
|

hour :[number](/docs/luau/numbers)

Default Value: 0 |
|

minute :[number](/docs/luau/numbers)

Default Value: 0 |
|

second :[number](/docs/luau/numbers)

Default Value: 0 |
|

millisecond :[number](/docs/luau/numbers)

Default Value: 0 |

Provide feedback

---

fromIsoDate

DateTime.fromIsoDate (isoDate :[string](/docs/luau/strings) )

Parameters

|

isoDate :[string](/docs/luau/strings)

 |

Provide feedback

---

Properties

UnixTimestamp

DateTime.UnixTimestamp :[number](/docs/luau/numbers)

Provide feedback

---

UnixTimestampMillis

DateTime.UnixTimestampMillis :[number](/docs/luau/numbers)

Provide feedback

---

Methods

ToUniversalTime

DateTime:ToUniversalTime () :[Dictionary](/docs/luau/tables#dictionaries)

Returns

[Dictionary](/docs/luau/tables#dictionaries)

Provide feedback

---

ToLocalTime

DateTime:ToLocalTime () :[Dictionary](/docs/luau/tables#dictionaries)

Returns

[Dictionary](/docs/luau/tables#dictionaries)

Provide feedback

---

ToIsoDate

DateTime:ToIsoDate () :[string](/docs/luau/strings)

Returns

[string](/docs/luau/strings)

Provide feedback

---

FormatUniversalTime

DateTime:FormatUniversalTime (

format :[string](/docs/luau/strings) , locale :[string](/docs/luau/strings)

) :[string](/docs/luau/strings)

Parameters

|

format :[string](/docs/luau/strings)

 |
|

locale :[string](/docs/luau/strings)

 |

Returns

[string](/docs/luau/strings)

Provide feedback

---

FormatLocalTime

DateTime:FormatLocalTime (

format :[string](/docs/luau/strings) , locale :[string](/docs/luau/strings)

) :[string](/docs/luau/strings)

Parameters

|

format :[string](/docs/luau/strings)

 |
|

locale :[string](/docs/luau/strings)

 |

Returns

[string](/docs/luau/strings)

Provide feedback

---

Jump to

▼

DateTime

[Summary](#summary)

[Constructors](#summary-constructors)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Constructors](#constructors)

[now()](#now)

[fromUnixTimestamp()](#fromUnixTimestamp)

[fromUnixTimestampMillis()](#fromUnixTimestampMillis)

[fromUniversalTime()](#fromUniversalTime)

[fromLocalTime()](#fromLocalTime)

[fromIsoDate()](#fromIsoDate)

[Properties](#properties)

[UnixTimestamp](#UnixTimestamp)

[UnixTimestampMillis](#UnixTimestampMillis)

[Methods](#methods)

[ToUniversalTime()](#ToUniversalTime)

[ToLocalTime()](#ToLocalTime)

[ToIsoDate()](#ToIsoDate)

[FormatUniversalTime()](#FormatUniversalTime)

[FormatLocalTime()](#FormatLocalTime)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
