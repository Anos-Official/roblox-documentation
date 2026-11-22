<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/SerializationService -->

SerializationService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [SerializationService](/docs/nl-nl/reference/engine/classes/SerializationService)

Nederlands

Feedback

Engine-klasse

SerializationService

Niet maakbaar

Service

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/SerializationService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[DeserializeInstancesAsync](#DeserializeInstancesAsync) (buffer :  [buffer](/docs/nl-nl/reference/engine/libraries/buffer) ) : {[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) }

 |
| --- | --- |
|

[SerializeInstancesAsync](#SerializeInstancesAsync) (inputInstances :  {[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) } ) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

DeserializeInstancesAsync

Opbrengst

Mogelijkheden: PluginOrOpenCloud

SerializationService:DeserializeInstancesAsync (buffer :[buffer](/docs/nl-nl/reference/engine/libraries/buffer) ) : {[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) }

Parameters

|

buffer :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |

Teruggaves

{[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) }

Codevoorbeelden

SerializationService:SerializeInstancesAsync

```

local SerializationService = game:GetService("SerializationService")

local part = Instance.new("Part")

part.Name = "MyPart"

local contentBuffer: buffer = SerializationService:SerializeInstancesAsync({ part })

local instances: { Instance } = SerializationService:DeserializeInstancesAsync(contentBuffer)

print(instances) -- {MijnDeel}

```

Feedback geven

---

SerializeInstancesAsync

Opbrengst

Mogelijkheden: PluginOrOpenCloud

SerializationService:SerializeInstancesAsync (inputInstances : {[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) } ) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Parameters

|

inputInstances : {[Instance](/docs/nl-nl/reference/engine/datatypes/Instance) }

 |

Teruggaves

[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Codevoorbeelden

SerializationService:SerializeInstancesAsync

```

local SerializationService = game:GetService("SerializationService")

local part = Instance.new("Part")

part.Name = "MyPart"

local contentBuffer: buffer = SerializationService:SerializeInstancesAsync({ part })

local instances: { Instance } = SerializationService:DeserializeInstancesAsync(contentBuffer)

print(instances) -- {MijnDeel}

```

Feedback geven

---

Ga naar

▼

SerializationService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[DeserializeInstancesAsync()](#DeserializeInstancesAsync)

[SerializeInstancesAsync()](#SerializeInstancesAsync)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
