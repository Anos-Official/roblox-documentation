<!-- Source: https://create.roblox.com/docs/reference/engine/classes/ReflectionService -->

ReflectionService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/ReflectionService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [ReflectionService](/docs/reference/engine/classes/ReflectionService)

English

Feedback

Engine Class

ReflectionService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[GetClass](#GetClass) (className :  [string](/docs/luau/strings) , filter :  [Dictionary](/docs/luau/tables#dictionaries) ) : ReflectedClass ?

 |
| --- | --- |
|

[GetClasses](#GetClasses) (filter :  [Dictionary](/docs/luau/tables#dictionaries) ) : { ReflectedClass }

 |
|

[GetEventsOfClass](#GetEventsOfClass) (className :  [string](/docs/luau/strings) , filter :  [Dictionary](/docs/luau/tables#dictionaries) ) : { ReflectedEvent }

 |
|

[GetMethodsOfClass](#GetMethodsOfClass) (className :  [string](/docs/luau/strings) , filter :  [Dictionary](/docs/luau/tables#dictionaries) ) : { ReflectedMethod }

 |
|

[GetPropertiesOfClass](#GetPropertiesOfClass) (className :  [string](/docs/luau/strings) , filter :  [Dictionary](/docs/luau/tables#dictionaries) ) : { ReflectedProperty }

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

Code Samples

ReflectionService Overview

```

local ReflectionService = game:GetService("ReflectionService")

-- Create a SecurityCapabilities object with all capabilities

local allCapabilities = SecurityCapabilities.new(table.unpack(Enum.SecurityCapability:GetEnumItems()))

-- Get all classes accessible with all capabilities

local allClasses = ReflectionService:GetClasses({ Security = allCapabilities })

print("Total classes:", #allClasses)

-- Get a specific class

local partClass = ReflectionService:GetClass("Part")

if partClass then

	print("\nPart class:")

	print("  Name:", partClass.Name)

	print("  Superclass:", partClass.Superclass and tostring(partClass.Superclass) or "none")

end

-- Get the first 5 properties of a class

local properties = ReflectionService:GetPropertiesOfClass("Part", { Security = allCapabilities })

print("\nPart properties:", #properties)

for i = 1, math.min(5, #properties) do

	print("  -", properties[i].Name)

end

```

---

API Reference

Methods

GetClass

ReflectionService:GetClass (

className :[string](/docs/luau/strings) , filter :[Dictionary](/docs/luau/tables#dictionaries)

) : ReflectedClass ?

Parameters

|

className :[string](/docs/luau/strings)

 |
|

filter :[Dictionary](/docs/luau/tables#dictionaries)

Default Value: nil |

Returns

ReflectedClass ?

Provide feedback

---

GetClasses

ReflectionService:GetClasses (filter :[Dictionary](/docs/luau/tables#dictionaries) ) : { ReflectedClass }

Parameters

|

filter :[Dictionary](/docs/luau/tables#dictionaries)

Default Value: nil |

Returns

{ ReflectedClass }

Provide feedback

---

GetEventsOfClass

ReflectionService:GetEventsOfClass (

className :[string](/docs/luau/strings) , filter :[Dictionary](/docs/luau/tables#dictionaries)

) : { ReflectedEvent }

Parameters

|

className :[string](/docs/luau/strings)

 |
|

filter :[Dictionary](/docs/luau/tables#dictionaries)

Default Value: nil |

Returns

{ ReflectedEvent }

Provide feedback

---

GetMethodsOfClass

ReflectionService:GetMethodsOfClass (

className :[string](/docs/luau/strings) , filter :[Dictionary](/docs/luau/tables#dictionaries)

) : { ReflectedMethod }

Parameters

|

className :[string](/docs/luau/strings)

 |
|

filter :[Dictionary](/docs/luau/tables#dictionaries)

Default Value: nil |

Returns

{ ReflectedMethod }

Provide feedback

---

GetPropertiesOfClass

ReflectionService:GetPropertiesOfClass (

className :[string](/docs/luau/strings) , filter :[Dictionary](/docs/luau/tables#dictionaries)

) : { ReflectedProperty }

Parameters

|

className :[string](/docs/luau/strings)

 |
|

filter :[Dictionary](/docs/luau/tables#dictionaries)

Default Value: nil |

Returns

{ ReflectedProperty }

Provide feedback

---

Jump to

▼

ReflectionService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[GetClass()](#GetClass)

[GetClasses()](#GetClasses)

[GetEventsOfClass()](#GetEventsOfClass)

[GetMethodsOfClass()](#GetMethodsOfClass)

[GetPropertiesOfClass()](#GetPropertiesOfClass)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
