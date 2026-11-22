<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/libraries/buffer.md -->

---
name: buffer
last_updated: 2026-11-20T18:47:27Z
type: library
summary: "A library of buffer functions."
---

# buffer

A library of buffer functions.

**Type:** library

## Description

A buffer is an object that represents a fixed-size mutable block of memory.
The buffer library provides functions for creation and manipulation of buffer
objects, providing all its functions inside the global [buffer](/docs/reference/engine/globals/buffer.md)
variable.

Buffer is intended to be used a low-level binary data storage structure,
replacing the uses of [string.pack()](/docs/reference/engine/globals/string.md) and [string.unpack()](/docs/reference/engine/globals/string.md).
Use cases include reading and writing existing binary formats, working with
data in a more compact form, serialization to custom binary formats, and
general work with native memory types like fixed-length integers and floats.

When passed through Roblox APIs, including sending a buffer through custom
events, the identity of the buffer object is not preserved and the target will
receive a copy. Similar to other limitations, the same buffer object cannot be
used from multiple [Actor](/docs/reference/engine/classes/Actor.md) scripts (Parallel Luau).

Many of the functions accept an offset in bytes from the start of the buffer.
Offset of `0` from the start of the buffer memory block accesses the first
byte. All offsets, counts and sizes should be non-negative integer numbers. If
the bytes that are accessed by any read or write operation are outside the
buffer memory, an error is thrown.

The `read` and `write` methods that work with integers and floats use
[little-endian](https://en.wikipedia.org/wiki/Endianness) encoding.

## Functions

### buffer.create

**Signature:** `buffer.create(size: number): buffer`

Creates a buffer of the requested size with all bytes initialized to `0`.
A size of `0` creates an empty buffer, where every read or write is out of
bounds. A negative size raises an error. Size limit is 1 GiB, or
1,073,741,824 bytes. Keep in mind that larger buffers might fail to
allocate if device is running low on memory.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `size` | `number` |  | Size of the buffer in bytes. Must be a non-negative integer. |

**Returns:** `buffer` — A new buffer of the requested size with all bytes initialized to zero.

**Buffer Create**

Demonstrates `buffer.create`, which allocates a zero-initialized buffer.

```lua
local packet = buffer.create(16)
print(buffer.len(packet)) --> 16
print(buffer.readu32(packet, 0)) --> 0

-- A size of 0 is allowed and gives an empty buffer, but every read or write is out of bounds
local empty = buffer.create(0)
print(buffer.len(empty)) --> 0
print(pcall(buffer.readu8, empty, 0)) --> false buffer access out of bounds

-- A negative size is an error
print(pcall(buffer.create, -1)) --> false invalid argument #1 to 'create' (size)
```

### buffer.fromstring

**Signature:** `buffer.fromstring(str: string): buffer`

Creates a buffer initialized to the contents of the string. The size of
the buffer equals the length of the string.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `str` | `string` |  | The string whose bytes initialize the new buffer. |

**Returns:** `buffer` — A new buffer containing a copy of the string's bytes.

**Buffer From String**

Demonstrates `buffer.fromstring`, which copies a string's bytes into a new
buffer.

```lua
local greeting = buffer.fromstring("Hello")
print(buffer.len(greeting)) --> 5
print(buffer.readu8(greeting, 0)) --> 72
```

### buffer.tostring

**Signature:** `buffer.tostring(b: buffer): string`

Returns the buffer data as a string.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to convert. |

**Returns:** `string` — A string containing all bytes from the buffer.

**Buffer To String**

Demonstrates `buffer.tostring`, which returns the contents of a buffer as a
string.

```lua
local data = buffer.create(3)
buffer.writeu8(data, 0, 82)
buffer.writeu8(data, 1, 66)
buffer.writeu8(data, 2, 88)
print(buffer.tostring(data)) --> RBX
```

### buffer.len

**Signature:** `buffer.len(b: buffer): number`

Returns the size of the buffer in bytes.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to get the size of. |

**Returns:** `number` — The size of the buffer in bytes.

**Buffer Length**

Demonstrates `buffer.len`, which returns the size of a buffer in bytes.

```lua
local header = buffer.create(12)
print(buffer.len(header)) --> 12
print(buffer.len(buffer.fromstring("abc"))) --> 3
```

### buffer.readbits

**Signature:** `buffer.readbits(b: buffer, bitOffset: number, bitCount: number): number`

Reads a range of bits into an unsigned integer from the buffer based on a
specific `bitCount` integer from `0` to `32`, inclusive. For example:

- `buffer.readbits(b, 0, 8)` is equivalent to
  [buffer.readu8(b, 0)](/docs/reference/engine/globals/buffer.md).
- `buffer.readbits(b, 0, 16)` is equivalent to
  [buffer.readu16(b, 0)](/docs/reference/engine/globals/buffer.md).
- `buffer.readbits(b, 0, 32)` is equivalent to
  [buffer.readu32(b, 0)](/docs/reference/engine/globals/buffer.md).
- `buffer.readbits(b, 0, 24)` reads 24 bits from the buffer.

Note that `0` bit width is supported only to not error in generalized
cases where bit count is dynamic, and reading 0 bits returns `0`. Also
note that, since the max size of the buffer is 1&nbsp;GB, `bitOffset`
cannot be handled as a 32‑bit integer number like byte offset in other
buffer functions.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to read from. |
| `bitOffset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `bitCount` | `number` |  | Integer bit count to read. Error is thrown if this value is not in range of `0` to `32`, inclusive. |

**Returns:** `number` — The unsigned integer value read from the specified bits.

**Buffer Read Bits**

Demonstrates `buffer.readbits`, which reads an arbitrary bit range as an
unsigned integer.

```lua
local flags = buffer.create(4)
buffer.writeu8(flags, 0, 0b10110100)

print(buffer.readbits(flags, 0, 8) == buffer.readu8(flags, 0)) --> true
print(buffer.readbits(flags, 2, 3)) --> 5
print(buffer.readbits(flags, 0, 0)) --> 0
```

### buffer.readi8

**Signature:** `buffer.readi8(b: buffer, offset: number): number`

Reads the data from the buffer by reinterpreting bytes at the offset as an
8-bit signed integer and converting it into a number.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to read from. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |

**Returns:** `number` — The value of the 8-bit signed integer at the given offset.

**Buffer Read Int8**

Demonstrates `buffer.readi8`, which reads an 8-bit signed integer.

```lua
local data = buffer.create(2)
buffer.writeu8(data, 0, 255)
buffer.writeu8(data, 1, 100)
print(buffer.readi8(data, 0)) --> -1
print(buffer.readi8(data, 1)) --> 100
```

### buffer.readu8

**Signature:** `buffer.readu8(b: buffer, offset: number): number`

Reads the data from the buffer by reinterpreting bytes at the offset as an
8-bit unsigned integer and converting it into a number.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to read from. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |

**Returns:** `number` — The value of the 8-bit unsigned integer at the given offset.

**Buffer Read UInt8**

Demonstrates `buffer.readu8`, which reads an 8-bit unsigned integer.

```lua
local data = buffer.create(1)
buffer.writei8(data, 0, -1)
print(buffer.readu8(data, 0)) --> 255
```

### buffer.readi16

**Signature:** `buffer.readi16(b: buffer, offset: number): number`

Reads the data from the buffer by reinterpreting bytes at the offset as a
16-bit signed integer and converting it into a number.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to read from. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |

**Returns:** `number` — The value of the 16-bit signed integer at the given offset.

**Buffer Read Int16**

Demonstrates `buffer.readi16`, which reads a little-endian 16-bit signed
integer.

```lua
local data = buffer.create(2)
buffer.writeu8(data, 0, 0xFE)
buffer.writeu8(data, 1, 0xFF)
print(buffer.readi16(data, 0)) --> -2
```

### buffer.readu16

**Signature:** `buffer.readu16(b: buffer, offset: number): number`

Reads the data from the buffer by reinterpreting bytes at the offset as a
16-bit unsigned integer and converting it into a number.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to read from. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |

**Returns:** `number` — The value of the 16-bit unsigned integer at the given offset.

**Buffer Read UInt16**

Demonstrates `buffer.readu16`, which reads a little-endian 16-bit unsigned
integer.

```lua
local data = buffer.create(2)
buffer.writeu8(data, 0, 0x01)
buffer.writeu8(data, 1, 0x02)
print(buffer.readu16(data, 0)) --> 513
```

### buffer.readi32

**Signature:** `buffer.readi32(b: buffer, offset: number): number`

Reads the data from the buffer by reinterpreting bytes at the offset as a
32-bit signed integer and converting it into a number.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to read from. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |

**Returns:** `number` — The value of the 32-bit signed integer at the given offset.

**Buffer Read Int32**

Demonstrates `buffer.readi32`, which reads a 32-bit signed integer.

```lua
local data = buffer.create(4)
buffer.writeu32(data, 0, 4294967293)
print(buffer.readi32(data, 0)) --> -3
```

### buffer.readu32

**Signature:** `buffer.readu32(b: buffer, offset: number): number`

Reads the data from the buffer by reinterpreting bytes at the offset as a
32-bit unsigned integer and converting it into a number.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to read from. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |

**Returns:** `number` — The value of the 32-bit unsigned integer at the given offset.

**Buffer Read UInt32**

Demonstrates `buffer.readu32`, which reads a 32-bit unsigned integer.

```lua
local data = buffer.create(4)
buffer.writei32(data, 0, -3)
print(buffer.readu32(data, 0)) --> 4294967293

print(pcall(buffer.readu32, data, 2)) --> false buffer access out of bounds
```

### buffer.readf32

**Signature:** `buffer.readf32(b: buffer, offset: number): number`

Reads the data from the buffer by reinterpreting bytes at the offset as a
32-bit floating-point value and converting it into a number. If the
floating-point value matches any bit patterns that represent `NaN` (not a
number), the returned value may be converted to a different quiet `NaN`
representation.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to read from. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |

**Returns:** `number` — The value of the 32-bit floating-point number at the given offset.

**Buffer Read Float32**

Demonstrates `buffer.readf32`, which reads a 32-bit float and shows its
limited precision.

```lua
local data = buffer.create(4)
buffer.writef32(data, 0, 1.5)
print(buffer.readf32(data, 0)) --> 1.5

buffer.writef32(data, 0, 0.1)
print(buffer.readf32(data, 0) == 0.1) --> false
```

### buffer.readvectorf32x2

**Signature:** `buffer.readvectorf32x2(b: buffer, offset: number): vector`

Reads two contiguous 32-bit floating-point values from the buffer and
returns them as the `X` and `Y` components of a vector. The `Z` component
is set to `0`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to read from. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |

**Returns:** `vector` — A vector containing the two values read from the buffer. The third
component is zero.

**Buffer Read Vector 2**

Demonstrates `buffer.readvectorf32x2`, which reads two float32 values into a
vector.

```lua
local data = buffer.create(8)
buffer.writef32(data, 0, 1.5)
buffer.writef32(data, 4, -2)

local result = buffer.readvectorf32x2(data, 0)
print(result.X, result.Y, result.Z) --> 1.5 -2 0
```

### buffer.readvectorf32x3

**Signature:** `buffer.readvectorf32x3(b: buffer, offset: number): vector`

Reads three contiguous 32-bit floating-point values from the buffer and
returns them as the `X`, `Y`, and `Z` components of a vector.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to read from. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |

**Returns:** `vector` — A vector containing the three values read from the buffer.

**Buffer Read Vector 3**

Demonstrates `buffer.readvectorf32x3`, which reads three float32 values into a
vector.

```lua
local data = buffer.create(12)
buffer.writef32(data, 0, 1)
buffer.writef32(data, 4, 2)
buffer.writef32(data, 8, 3)

local result = buffer.readvectorf32x3(data, 0)
print(result.X, result.Y, result.Z) --> 1 2 3
```

### buffer.readf64

**Signature:** `buffer.readf64(b: buffer, offset: number): number`

Reads the data from the buffer by reinterpreting bytes at the offset as a
64-bit floating-point value and converting it into a number. If the
floating-point value matches any bit patterns that represent `NaN` (not a
number), the returned value may be converted to a different quiet `NaN`
representation.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to read from. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |

**Returns:** `number` — The value of the 64-bit floating-point number at the given offset.

**Buffer Read Float64**

Demonstrates `buffer.readf64`, which reads a 64-bit float without losing
precision.

```lua
local data = buffer.create(8)
buffer.writef64(data, 0, 0.1)
print(buffer.readf64(data, 0) == 0.1) --> true
```

### buffer.writebits

**Signature:** `buffer.writebits(b: buffer, bitOffset: number, bitCount: number, value: number): ()`

Writes data to the buffer based on a specific `bitCount` integer from `0`
to `32`, inclusive. `value` is treated as an unsigned 32‑bit number and
only `bitCount` least significant bits are written.

Note that `0` bit width is supported only to not error in generalized
cases where bit count is dynamic, and writing 0 bits has no effect. Also
note that, since the max size of the buffer is 1&nbsp;GB, `bitOffset`
cannot be handled as a 32‑bit integer number like byte offset in other
buffer functions.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to write to. |
| `bitOffset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `bitCount` | `number` |  | Integer bit count to write. Error is thrown if this value is not in range of `0` to `32`, inclusive. |
| `value` | `number` |  | Unsigned 32‑bit number. Only `bitCount` least significant bits are written. |

**Returns:** `()`

**Buffer Write Bits**

Demonstrates `buffer.writebits`, which writes only the least significant
`bitCount` bits of a value.

```lua
local packed = buffer.create(2)
buffer.writebits(packed, 0, 3, 5) -- 0b101
buffer.writebits(packed, 3, 5, 17) -- 0b10001
print(buffer.readbits(packed, 0, 3)) --> 5
print(buffer.readbits(packed, 3, 5)) --> 17

buffer.writebits(packed, 8, 4, 0xFF)
print(buffer.readbits(packed, 8, 8)) --> 15
```

### buffer.writei8

**Signature:** `buffer.writei8(b: buffer, offset: number, value: number): ()`

Writes data to the buffer by converting the number into an 8-bit signed
integer and writing a single byte.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to write to. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `value` | `number` |  | An integer number in range [-128, 127]. |

**Returns:** `()`

**Buffer Write Int8**

Demonstrates `buffer.writei8`, which writes an 8-bit signed integer.

```lua
local data = buffer.create(1)
buffer.writei8(data, 0, -128)
print(buffer.readi8(data, 0)) --> -128
print(buffer.readu8(data, 0)) --> 128
```

### buffer.writeu8

**Signature:** `buffer.writeu8(b: buffer, offset: number, value: number): ()`

Writes data to the buffer by converting the number into an 8-bit unsigned
integer and writing a single byte.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to write to. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `value` | `number` |  | An integer number in range [0, 255]. |

**Returns:** `()`

**Buffer Write UInt8**

Demonstrates `buffer.writeu8`, which writes an 8-bit unsigned integer.

```lua
local data = buffer.create(3)
for index = 0, 2 do
	buffer.writeu8(data, index, 100 + index)
end
print(buffer.readu8(data, 2)) --> 102
```

### buffer.writei16

**Signature:** `buffer.writei16(b: buffer, offset: number, value: number): ()`

Writes data to the buffer by converting the number into a 16-bit signed
integer and reinterpreting it as individual bytes.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to write to. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `value` | `number` |  | An integer number in range [-32,768, 32,767]. |

**Returns:** `()`

**Buffer Write Int16**

Demonstrates `buffer.writei16`, which writes a little-endian 16-bit signed
integer.

```lua
local data = buffer.create(2)
buffer.writei16(data, 0, -2)
print(buffer.readi16(data, 0)) --> -2
print(buffer.readu8(data, 0), buffer.readu8(data, 1)) --> 254 255
```

### buffer.writeu16

**Signature:** `buffer.writeu16(b: buffer, offset: number, value: number): ()`

Writes data to the buffer by converting the number into a 16-bit unsigned
integer and reinterpreting it as individual bytes.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to write to. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `value` | `number` |  | An integer number in range [0, 65,535]. |

**Returns:** `()`

**Buffer Write UInt16**

Demonstrates `buffer.writeu16`, which writes a little-endian 16-bit unsigned
integer.

```lua
local data = buffer.create(2)
buffer.writeu16(data, 0, 0x0102)
print(buffer.readu8(data, 0), buffer.readu8(data, 1)) --> 2 1
```

### buffer.writei32

**Signature:** `buffer.writei32(b: buffer, offset: number, value: number): ()`

Writes data to the buffer by converting the number into a 32-bit signed
integer and reinterpreting it as individual bytes.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to write to. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `value` | `number` |  | An integer number in range [-2,147,483,648, 2,147,483,647]. |

**Returns:** `()`

**Buffer Write Int32**

Demonstrates `buffer.writei32`, which writes a 32-bit signed integer.

```lua
local data = buffer.create(4)
buffer.writei32(data, 0, -2147483648)
print(buffer.readi32(data, 0)) --> -2147483648
print(buffer.readu32(data, 0)) --> 2147483648
```

### buffer.writeu32

**Signature:** `buffer.writeu32(b: buffer, offset: number, value: number): ()`

Writes data to the buffer by converting the number into a 32-bit unsigned
integer and reinterpreting it as individual bytes.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to write to. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `value` | `number` |  | An integer number in range [0, 4,294,967,295]. |

**Returns:** `()`

**Buffer Write UInt32**

Demonstrates `buffer.writeu32`, which writes a 32-bit unsigned integer.

```lua
local data = buffer.create(8)
buffer.writeu32(data, 0, 4294967295)
buffer.writeu32(data, 4, 1)
print(buffer.readu32(data, 0)) --> 4294967295
print(buffer.readu32(data, 4)) --> 1
```

### buffer.writef32

**Signature:** `buffer.writef32(b: buffer, offset: number, value: number): ()`

Writes data to the buffer by converting the number into a 32-bit
floating-point value and reinterpreting it as individual bytes.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to write to. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `value` | `number` |  | A single-precision floating-point number. |

**Returns:** `()`

**Buffer Write Float32**

Demonstrates `buffer.writef32`, which stores a number as a 32-bit float.

```lua
local data = buffer.create(4)
buffer.writef32(data, 0, -2.25)
print(buffer.readf32(data, 0)) --> -2.25
```

### buffer.writevectorf32x2

**Signature:** `buffer.writevectorf32x2(b: buffer, offset: number, value: vector): ()`

Writes the `X` and `Y` components of a vector as two contiguous 32-bit
floating-point values to the buffer. The `Z` component is not written.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to write to. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `value` | `vector` |  | The vector whose `X` and `Y` components are written to the buffer. |

**Returns:** `()`

**Buffer Write Vector 2**

Demonstrates `buffer.writevectorf32x2`, which writes only the X and Y
components of a vector.

```lua
local data = buffer.create(12)
buffer.writevectorf32x2(data, 0, vector.create(1, 2, 3))
print(buffer.readf32(data, 0), buffer.readf32(data, 4)) --> 1 2
print(buffer.readf32(data, 8)) --> 0
```

### buffer.writevectorf32x3

**Signature:** `buffer.writevectorf32x3(b: buffer, offset: number, value: vector): ()`

Writes the `X`, `Y`, and `Z` components of a vector as three contiguous
32-bit floating-point values to the buffer.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to write to. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `value` | `vector` |  | The vector whose `X`, `Y`, and `Z` components are written to the buffer. |

**Returns:** `()`

**Buffer Write Vector 3**

Demonstrates `buffer.writevectorf32x3`, which writes all three vector
components as float32 values.

```lua
local data = buffer.create(12)
buffer.writevectorf32x3(data, 0, vector.create(1, 2, 3))
print(buffer.readf32(data, 0), buffer.readf32(data, 4), buffer.readf32(data, 8)) --> 1 2 3
```

### buffer.writef64

**Signature:** `buffer.writef64(b: buffer, offset: number, value: number): ()`

Writes data to the buffer by converting the number into a 64-bit
floating-point value and reinterpreting it as individual bytes.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to write to. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `value` | `number` |  | A double-precision floating-point number. |

**Returns:** `()`

**Buffer Write Float64**

Demonstrates `buffer.writef64`, which stores a number as a 64-bit float.

```lua
local data = buffer.create(16)
buffer.writef64(data, 0, math.pi)
buffer.writef64(data, 8, -0.5)
print(buffer.readf64(data, 0) == math.pi) --> true
print(buffer.readf64(data, 8)) --> -0.5
```

### buffer.readstring

**Signature:** `buffer.readstring(b: buffer, offset: number, count: number): string`

Reads a string of length `count` from the buffer at the specified
`offset`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to read from. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `count` | `number` |  | Length to read. |

**Returns:** `string` — A string of length `count` read from the buffer at the specified
offset.

**Buffer Read String**

Demonstrates `buffer.readstring`, which reads `count` bytes from an offset as
a string.

```lua
local data = buffer.fromstring("Hello, world")
print(buffer.readstring(data, 7, 5)) --> world
print(buffer.readstring(data, 0, 5)) --> Hello
```

### buffer.writestring

**Signature:** `buffer.writestring(b: buffer, offset: number, value: string, count: number?): ()`

Writes data from a string into the buffer at the specified `offset`. If an
optional `count` is specified, only `count` bytes are taken from the
string.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | The buffer to write to. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `value` | `string` |  | Data to write. |
| `count` | `number?` |  | Number of bytes to take from the string. This value cannot be larger than the string length. |

**Returns:** `()`

**Buffer Write String**

Demonstrates `buffer.writestring`, including the optional `count` that limits
how many bytes are taken.

```lua
local data = buffer.create(8)
buffer.writestring(data, 0, "abcdef", 3)
buffer.writestring(data, 3, "XY")
print(buffer.readstring(data, 0, 5)) --> abcXY

print(pcall(buffer.writestring, data, 0, "ab", 5)) --> false string length overflow
```

### buffer.copy

**Signature:** `buffer.copy(target: buffer, targetOffset: number, source: buffer, sourceOffset?: number?, count: number?): ()`

Copies `count` bytes from `source` starting at offset `sourceOffset` into
the `target` at `targetOffset`.

It's possible for `source` and `target` to be the same. Copying an
overlapping region inside the same buffer acts as if the source region is
copied into a temporary buffer and then that buffer is copied over to the
target.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `target` | `buffer` |  | Buffer to copy data into. |
| `targetOffset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `source` | `buffer` |  | Buffer to take the data from. |
| `sourceOffset` | `number?` | `0` | Offset from the beginning of the buffer memory, starting from `0`. |
| `count` | `number?` |  | Number of bytes to copy. If omitted, the whole `source` data starting from `sourceOffset` is taken. |

**Returns:** `()`

**Buffer Copy**

Demonstrates `buffer.copy`, including copying an overlapping region within one
buffer.

```lua
local source = buffer.fromstring("abcdef")
local target = buffer.create(6)
buffer.copy(target, 0, source, 2, 3)
print(buffer.readstring(target, 0, 3)) --> cde

local overlap = buffer.fromstring("abcdef")
buffer.copy(overlap, 2, overlap, 0, 4)
print(buffer.tostring(overlap)) --> ababcd
```

### buffer.fill

**Signature:** `buffer.fill(b: buffer, offset: number, value: number, count: number?): ()`

Sets `count` bytes in the buffer starting at the specified `offset` to
`value`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `b` | `buffer` |  | Buffer to write the data into. |
| `offset` | `number` |  | Offset from the beginning of the buffer memory, starting from `0`. |
| `value` | `number` |  | An integer number in range [0, 255]. |
| `count` | `number?` |  | Number of bytes to write. If omitted, all bytes after the specified offset are set. |

**Returns:** `()`

**Buffer Fill**

Demonstrates `buffer.fill`, which sets a region of a buffer to a byte value.

```lua
local data = buffer.create(6)
buffer.fill(data, 0, 0xFF, 2)
print(buffer.readu8(data, 1), buffer.readu8(data, 2)) --> 255 0

buffer.fill(data, 2, 7)
print(buffer.readu8(data, 5)) --> 7
```