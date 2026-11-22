<!-- Source: https://create.roblox.com/docs/nl-nl/reference/engine/classes/EncodingService -->

EncodingService | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Meer informatie

1. [Klassen](/docs/nl-nl/reference/engine/classes)
2. /
3. [Object](/docs/nl-nl/reference/engine/classes/Object)
4. /
5. [Instance](/docs/nl-nl/reference/engine/classes/Instance)
6. /
7. [EncodingService](/docs/nl-nl/reference/engine/classes/EncodingService)

Nederlands

Feedback

Engine-klasse

EncodingService

Niet maakbaar

Service

Niet gerepliceerd

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier](/docs/en-us/reference/engine/classes/EncodingService)  om deze pagina in het Engels te bekijken.

---

## Samenvatting

Methoden

|

[Base64Decode](#Base64Decode) (input :  [buffer](/docs/nl-nl/reference/engine/libraries/buffer) ) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |
| --- | --- |
|

[Base64Encode](#Base64Encode) (input :  [buffer](/docs/nl-nl/reference/engine/libraries/buffer) ) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |
|

[CompressBuffer](#CompressBuffer) (input :  [buffer](/docs/nl-nl/reference/engine/libraries/buffer) , algorithm :  [Enum.CompressionAlgorithm](/docs/nl-nl/reference/engine/enums/CompressionAlgorithm) , compressionLevel :  [number](/docs/nl-nl/luau/numbers) ) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |
|

[ComputeBufferHash](#ComputeBufferHash) (input :  [buffer](/docs/nl-nl/reference/engine/libraries/buffer) , algorithm :  [Enum.HashAlgorithm](/docs/nl-nl/reference/engine/enums/HashAlgorithm) ) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |
|

[ComputeStringHash](#ComputeStringHash) (input :  [string](/docs/nl-nl/luau/strings) , algorithm :  [Enum.HashAlgorithm](/docs/nl-nl/reference/engine/enums/HashAlgorithm) ) :[string](/docs/nl-nl/luau/strings)

 |
|

[DecompressBuffer](#DecompressBuffer) (input :  [buffer](/docs/nl-nl/reference/engine/libraries/buffer) , algorithm :  [Enum.CompressionAlgorithm](/docs/nl-nl/reference/engine/enums/CompressionAlgorithm) ) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |
|

[GetDecompressedBufferSize](#GetDecompressedBufferSize) (input :  [buffer](/docs/nl-nl/reference/engine/libraries/buffer) , algorithm :  [Enum.CompressionAlgorithm](/docs/nl-nl/reference/engine/enums/CompressionAlgorithm) ) :[number](/docs/nl-nl/luau/numbers) ?

 |

Overgenomen leden

58  overgenomen van [Instance](/docs/nl-nl/reference/engine/classes/Instance)

6  overgenomen van [Object](/docs/nl-nl/reference/engine/classes/Object)

---

API-referentie

Methoden

Base64Decode

Parallel schrijven

EncodingService:Base64Decode (input :[buffer](/docs/nl-nl/reference/engine/libraries/buffer) ) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Parameters

|

input :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |

Teruggaves

[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Feedback geven

---

Base64Encode

Parallel schrijven

EncodingService:Base64Encode (input :[buffer](/docs/nl-nl/reference/engine/libraries/buffer) ) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Parameters

|

input :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |

Teruggaves

[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Feedback geven

---

CompressBuffer

Parallel schrijven

EncodingService:CompressBuffer (

input :[buffer](/docs/nl-nl/reference/engine/libraries/buffer) , algorithm :[Enum.CompressionAlgorithm](/docs/nl-nl/reference/engine/enums/CompressionAlgorithm) , compressionLevel :[number](/docs/nl-nl/luau/numbers)

) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Parameters

|

input :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |
|

algorithm :[Enum.CompressionAlgorithm](/docs/nl-nl/reference/engine/enums/CompressionAlgorithm)

 |
|

compressionLevel :[number](/docs/nl-nl/luau/numbers)

Standaardwaarde: 1 |

Teruggaves

[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Feedback geven

---

ComputeBufferHash

Parallel schrijven

EncodingService:ComputeBufferHash (

input :[buffer](/docs/nl-nl/reference/engine/libraries/buffer) , algorithm :[Enum.HashAlgorithm](/docs/nl-nl/reference/engine/enums/HashAlgorithm)

) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Parameters

|

input :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |
|

algorithm :[Enum.HashAlgorithm](/docs/nl-nl/reference/engine/enums/HashAlgorithm)

 |

Teruggaves

[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Feedback geven

---

ComputeStringHash

Parallel schrijven

EncodingService:ComputeStringHash (

input :[string](/docs/nl-nl/luau/strings) , algorithm :[Enum.HashAlgorithm](/docs/nl-nl/reference/engine/enums/HashAlgorithm)

) :[string](/docs/nl-nl/luau/strings)

Parameters

|

input :[string](/docs/nl-nl/luau/strings)

 |
|

algorithm :[Enum.HashAlgorithm](/docs/nl-nl/reference/engine/enums/HashAlgorithm)

 |

Teruggaves

[string](/docs/nl-nl/luau/strings)

Feedback geven

---

DecompressBuffer

Parallel schrijven

EncodingService:DecompressBuffer (

input :[buffer](/docs/nl-nl/reference/engine/libraries/buffer) , algorithm :[Enum.CompressionAlgorithm](/docs/nl-nl/reference/engine/enums/CompressionAlgorithm)

) :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Parameters

|

input :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |
|

algorithm :[Enum.CompressionAlgorithm](/docs/nl-nl/reference/engine/enums/CompressionAlgorithm)

 |

Teruggaves

[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

Feedback geven

---

GetDecompressedBufferSize

Parallel schrijven

EncodingService:GetDecompressedBufferSize (

input :[buffer](/docs/nl-nl/reference/engine/libraries/buffer) , algorithm :[Enum.CompressionAlgorithm](/docs/nl-nl/reference/engine/enums/CompressionAlgorithm)

) :[number](/docs/nl-nl/luau/numbers) ?

Parameters

|

input :[buffer](/docs/nl-nl/reference/engine/libraries/buffer)

 |
|

algorithm :[Enum.CompressionAlgorithm](/docs/nl-nl/reference/engine/enums/CompressionAlgorithm)

 |

Teruggaves

[number](/docs/nl-nl/luau/numbers) ?

Feedback geven

---

Ga naar

▼

EncodingService

[Samenvatting](#summary)

[Methoden](#summary-methods)

[Methoden](#methods)

[Base64Decode()](#Base64Decode)

[Base64Encode()](#Base64Encode)

[CompressBuffer()](#CompressBuffer)

[ComputeBufferHash()](#ComputeBufferHash)

[ComputeStringHash()](#ComputeStringHash)

[DecompressBuffer()](#DecompressBuffer)

[GetDecompressedBufferSize()](#GetDecompressedBufferSize)

Nederlands

Feedback

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
