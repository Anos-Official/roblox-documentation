<!-- Source: https://create.roblox.com/docs/reference/engine/classes/SerializationService -->

SerializationService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/SerializationService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [SerializationService](/docs/reference/engine/classes/SerializationService)

English

Feedback

Engine Class

SerializationService

Not Creatable

Service

---

## Summary

Methods

|

[DeserializeInstancesAsync](#DeserializeInstancesAsync) (buffer :  [buffer](/docs/reference/engine/libraries/buffer) ) : {[Instance](/docs/reference/engine/datatypes/Instance) }

 |
| --- | --- |
|

[SerializeInstancesAsync](#SerializeInstancesAsync) (inputInstances :  {[Instance](/docs/reference/engine/datatypes/Instance) } ) :[buffer](/docs/reference/engine/libraries/buffer)

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

DeserializeInstancesAsync

Yields

Capabilities: PluginOrOpenCloud

SerializationService:DeserializeInstancesAsync (buffer :[buffer](/docs/reference/engine/libraries/buffer) ) : {[Instance](/docs/reference/engine/datatypes/Instance) }

Parameters

|

buffer :[buffer](/docs/reference/engine/libraries/buffer)

 |

Returns

{[Instance](/docs/reference/engine/datatypes/Instance) }

Code Samples

SerializationService:SerializeInstancesAsync

```

local SerializationService = game:GetService("SerializationService")

local part = Instance.new("Part")

part.Name = "MyPart"

local contentBuffer: buffer = SerializationService:SerializeInstancesAsync({ part })

local instances: { Instance } = SerializationService:DeserializeInstancesAsync(contentBuffer)

print(instances) -- {MyPart}

```

Provide feedback

---

SerializeInstancesAsync

Yields

Capabilities: PluginOrOpenCloud

SerializationService:SerializeInstancesAsync (inputInstances : {[Instance](/docs/reference/engine/datatypes/Instance) } ) :[buffer](/docs/reference/engine/libraries/buffer)

Parameters

|

inputInstances : {[Instance](/docs/reference/engine/datatypes/Instance) }

 |

Returns

[buffer](/docs/reference/engine/libraries/buffer)

Code Samples

SerializationService:SerializeInstancesAsync

```

local SerializationService = game:GetService("SerializationService")

local part = Instance.new("Part")

part.Name = "MyPart"

local contentBuffer: buffer = SerializationService:SerializeInstancesAsync({ part })

local instances: { Instance } = SerializationService:DeserializeInstancesAsync(contentBuffer)

print(instances) -- {MyPart}

```

Provide feedback

---

Jump to

▼

SerializationService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[DeserializeInstancesAsync()](#DeserializeInstancesAsync)

[SerializeInstancesAsync()](#SerializeInstancesAsync)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
