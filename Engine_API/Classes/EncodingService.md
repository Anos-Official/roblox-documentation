<!-- Source: https://create.roblox.com/docs/reference/engine/classes/EncodingService -->

EncodingService | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/classes/EncodingService.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Classes](/docs/reference/engine/classes)
2. /
3. [Object](/docs/reference/engine/classes/Object)
4. /
5. [Instance](/docs/reference/engine/classes/Instance)
6. /
7. [EncodingService](/docs/reference/engine/classes/EncodingService)

English

Feedback

Engine Class

EncodingService

Not Creatable

Service

Not Replicated

---

## Summary

Methods

|

[Base64Decode](#Base64Decode) (input :  [buffer](/docs/reference/engine/libraries/buffer) ) :[buffer](/docs/reference/engine/libraries/buffer)

 |
| --- | --- |
|

[Base64Encode](#Base64Encode) (input :  [buffer](/docs/reference/engine/libraries/buffer) ) :[buffer](/docs/reference/engine/libraries/buffer)

 |
|

[CompressBuffer](#CompressBuffer) (input :  [buffer](/docs/reference/engine/libraries/buffer) , algorithm :  [Enum.CompressionAlgorithm](/docs/reference/engine/enums/CompressionAlgorithm) , compressionLevel :  [number](/docs/luau/numbers) ) :[buffer](/docs/reference/engine/libraries/buffer)

 |
|

[ComputeBufferHash](#ComputeBufferHash) (input :  [buffer](/docs/reference/engine/libraries/buffer) , algorithm :  [Enum.HashAlgorithm](/docs/reference/engine/enums/HashAlgorithm) ) :[buffer](/docs/reference/engine/libraries/buffer)

 |
|

[ComputeStringHash](#ComputeStringHash) (input :  [string](/docs/luau/strings) , algorithm :  [Enum.HashAlgorithm](/docs/reference/engine/enums/HashAlgorithm) ) :[string](/docs/luau/strings)

 |
|

[DecompressBuffer](#DecompressBuffer) (input :  [buffer](/docs/reference/engine/libraries/buffer) , algorithm :  [Enum.CompressionAlgorithm](/docs/reference/engine/enums/CompressionAlgorithm) ) :[buffer](/docs/reference/engine/libraries/buffer)

 |
|

[GetDecompressedBufferSize](#GetDecompressedBufferSize) (input :  [buffer](/docs/reference/engine/libraries/buffer) , algorithm :  [Enum.CompressionAlgorithm](/docs/reference/engine/enums/CompressionAlgorithm) ) :[number](/docs/luau/numbers) ?

 |

Inherited Members

58  inherited from [Instance](/docs/reference/engine/classes/Instance)

6  inherited from [Object](/docs/reference/engine/classes/Object)

---

API Reference

Methods

Base64Decode

Write Parallel

EncodingService:Base64Decode (input :[buffer](/docs/reference/engine/libraries/buffer) ) :[buffer](/docs/reference/engine/libraries/buffer)

Parameters

|

input :[buffer](/docs/reference/engine/libraries/buffer)

 |

Returns

[buffer](/docs/reference/engine/libraries/buffer)

Provide feedback

---

Base64Encode

Write Parallel

EncodingService:Base64Encode (input :[buffer](/docs/reference/engine/libraries/buffer) ) :[buffer](/docs/reference/engine/libraries/buffer)

Parameters

|

input :[buffer](/docs/reference/engine/libraries/buffer)

 |

Returns

[buffer](/docs/reference/engine/libraries/buffer)

Provide feedback

---

CompressBuffer

Write Parallel

EncodingService:CompressBuffer (

input :[buffer](/docs/reference/engine/libraries/buffer) , algorithm :[Enum.CompressionAlgorithm](/docs/reference/engine/enums/CompressionAlgorithm) , compressionLevel :[number](/docs/luau/numbers)

) :[buffer](/docs/reference/engine/libraries/buffer)

Parameters

|

input :[buffer](/docs/reference/engine/libraries/buffer)

 |
|

algorithm :[Enum.CompressionAlgorithm](/docs/reference/engine/enums/CompressionAlgorithm)

 |
|

compressionLevel :[number](/docs/luau/numbers)

Default Value: 1 |

Returns

[buffer](/docs/reference/engine/libraries/buffer)

Provide feedback

---

ComputeBufferHash

Write Parallel

EncodingService:ComputeBufferHash (

input :[buffer](/docs/reference/engine/libraries/buffer) , algorithm :[Enum.HashAlgorithm](/docs/reference/engine/enums/HashAlgorithm)

) :[buffer](/docs/reference/engine/libraries/buffer)

Parameters

|

input :[buffer](/docs/reference/engine/libraries/buffer)

 |
|

algorithm :[Enum.HashAlgorithm](/docs/reference/engine/enums/HashAlgorithm)

 |

Returns

[buffer](/docs/reference/engine/libraries/buffer)

Provide feedback

---

ComputeStringHash

Write Parallel

EncodingService:ComputeStringHash (

input :[string](/docs/luau/strings) , algorithm :[Enum.HashAlgorithm](/docs/reference/engine/enums/HashAlgorithm)

) :[string](/docs/luau/strings)

Parameters

|

input :[string](/docs/luau/strings)

 |
|

algorithm :[Enum.HashAlgorithm](/docs/reference/engine/enums/HashAlgorithm)

 |

Returns

[string](/docs/luau/strings)

Provide feedback

---

DecompressBuffer

Write Parallel

EncodingService:DecompressBuffer (

input :[buffer](/docs/reference/engine/libraries/buffer) , algorithm :[Enum.CompressionAlgorithm](/docs/reference/engine/enums/CompressionAlgorithm)

) :[buffer](/docs/reference/engine/libraries/buffer)

Parameters

|

input :[buffer](/docs/reference/engine/libraries/buffer)

 |
|

algorithm :[Enum.CompressionAlgorithm](/docs/reference/engine/enums/CompressionAlgorithm)

 |

Returns

[buffer](/docs/reference/engine/libraries/buffer)

Provide feedback

---

GetDecompressedBufferSize

Write Parallel

EncodingService:GetDecompressedBufferSize (

input :[buffer](/docs/reference/engine/libraries/buffer) , algorithm :[Enum.CompressionAlgorithm](/docs/reference/engine/enums/CompressionAlgorithm)

) :[number](/docs/luau/numbers) ?

Parameters

|

input :[buffer](/docs/reference/engine/libraries/buffer)

 |
|

algorithm :[Enum.CompressionAlgorithm](/docs/reference/engine/enums/CompressionAlgorithm)

 |

Returns

[number](/docs/luau/numbers) ?

Provide feedback

---

Jump to

▼

EncodingService

[Summary](#summary)

[Methods](#summary-methods)

[Methods](#methods)

[Base64Decode()](#Base64Decode)

[Base64Encode()](#Base64Encode)

[CompressBuffer()](#CompressBuffer)

[ComputeBufferHash()](#ComputeBufferHash)

[ComputeStringHash()](#ComputeStringHash)

[DecompressBuffer()](#DecompressBuffer)

[GetDecompressedBufferSize()](#GetDecompressedBufferSize)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
