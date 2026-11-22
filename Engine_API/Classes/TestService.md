<!-- Source: https://create.roblox.com/docs/reference/engine/classes/TestService -->

TestService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/TestService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [TestService](/docs/reference/engine/classes/TestService)

English

Feedback

Engine Class

TestService

Service

---

## Summary

Properties

|

[Enabled](#Enabled) :[boolean](/docs/luau/booleans)

 |
| --- | --- |

Methods

|

[ListTests](#ListTests) () :[{any}](/docs/luau/tables#arrays)

 |
|

[RegisterSuite](#RegisterSuite) (suiteName :  [string](/docs/luau/strings) , options :  [Dictionary](/docs/luau/tables#dictionaries) ) :[TestSuite](/docs/reference/engine/classes/TestSuite)

 |
|

[RegisterTest](#RegisterTest) (testName :  [string](/docs/luau/strings) , callback :  [function](/docs/luau/functions) , options :  [Dictionary](/docs/luau/tables#dictionaries) ) :[TestCase](/docs/reference/engine/classes/TestCase)

 |
|

[ResetTestRegistry](#ResetTestRegistry) () : ()

 |
|

[RunTestsAsync](#RunTestsAsync) (filter :  [Dictionary](/docs/luau/tables#dictionaries) ) :[TestRunResult](/docs/reference/engine/classes/TestRunResult)

 |

Events

|

[TestRegistryChanged](#TestRegistryChanged) () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Properties

Enabled

Read Only

Not Replicated

TestService.Enabled :[boolean](/docs/luau/booleans)

Provide feedback

---

Methods

ListTests

TestService:ListTests () :[{any}](/docs/luau/tables#arrays)

Returns

[{any}](/docs/luau/tables#arrays)

Provide feedback

---

RegisterSuite

TestService:RegisterSuite (

suiteName :[string](/docs/luau/strings) , options :[Dictionary](/docs/luau/tables#dictionaries)

) :[TestSuite](/docs/reference/engine/classes/TestSuite)

Parameters

|

suiteName :[string](/docs/luau/strings)

 |
|

options :[Dictionary](/docs/luau/tables#dictionaries)

Default Value: nil |

Returns

[TestSuite](/docs/reference/engine/classes/TestSuite)

Provide feedback

---

RegisterTest

TestService:RegisterTest (

testName :[string](/docs/luau/strings) , callback :[function](/docs/luau/functions) , options :[Dictionary](/docs/luau/tables#dictionaries)

) :[TestCase](/docs/reference/engine/classes/TestCase)

Parameters

|

testName :[string](/docs/luau/strings)

 |
|

callback :[function](/docs/luau/functions)

 |
|

options :[Dictionary](/docs/luau/tables#dictionaries)

Default Value: nil |

Returns

[TestCase](/docs/reference/engine/classes/TestCase)

Provide feedback

---

ResetTestRegistry

TestService:ResetTestRegistry () : ()

Returns

()

Provide feedback

---

RunTestsAsync

Yields

TestService:RunTestsAsync (filter :[Dictionary](/docs/luau/tables#dictionaries) ) :[TestRunResult](/docs/reference/engine/classes/TestRunResult)

Parameters

|

filter :[Dictionary](/docs/luau/tables#dictionaries)

Default Value: nil |

Returns

[TestRunResult](/docs/reference/engine/classes/TestRunResult)

Provide feedback

---

Events

TestRegistryChanged

TestService.TestRegistryChanged () :[RBXScriptSignal](/docs/reference/engine/datatypes/RBXScriptSignal)

Provide feedback

---

Jump to

▼

TestService

[Summary](#summary)

[Properties](#summary-properties)

[Methods](#summary-methods)

[Events](#summary-events)

[Properties](#properties)

[Enabled](#Enabled)

[Methods](#methods)

[ListTests()](#ListTests)

[RegisterSuite()](#RegisterSuite)

[RegisterTest()](#RegisterTest)

[ResetTestRegistry()](#ResetTestRegistry)

[RunTestsAsync()](#RunTestsAsync)

[Events](#events)

[TestRegistryChanged](#TestRegistryChanged)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
