<!-- Source: https://create.roblox.com/docs/reference/engine/libraries/math.md -->

---
name: math
last_updated: 2026-11-20T18:47:27Z
type: library
summary: "A library of math functions."
---

# math

A library of math functions.

**Type:** library

## Description

This library is an interface to the standard C math library, providing all of
its functions inside the [math](/docs/reference/engine/globals/math.md) table.

## Properties

### math.e

**Type:** `number`

The value of Euler's number, e.

**Math E**

Demonstrates the `math.e` constant.

```lua
print(math.e) --> 2.718281828459045
print(math.exp(1) == math.e) --> true

-- Continuous compounding: principal * e^(rate * years)
local principal = 100
local rate = 0.05
local years = 10
print(math.floor(principal * math.e ^ (rate * years) * 100) / 100) --> 164.87
```

### math.huge

**Type:** `number`

Returns a value larger than or equal to any other numerical value (about
2<sup>1024</sup>). Dividing a positive number by zero yields this same
value.

**Math Huge**

Demonstrates the `math.huge` constant.

```lua
print(math.huge) --> inf
print(-math.huge) --> -inf
print(1 / 0 == math.huge) --> true

-- Useful as a starting value when searching for a minimum
local distances = {12.5, 3.75, 8}
local closest = math.huge
for _, distance in distances do
	closest = math.min(closest, distance)
end
print(closest) --> 3.75
```

### math.nan

**Type:** `number`

A NaN value, as defined by the IEEE 754 standard. Comparing directly to
`math.nan` will always return false; use [math.isnan()](/docs/reference/engine/globals/math.md) instead.

**Math NaN**

Demonstrates the `math.nan` constant and why it must be tested with
`math.isnan`.

```lua
local value = math.nan
print(value == math.nan) --> false
print(value == value) --> false
print(math.isnan(value)) --> true

-- NaN also results from undefined operations
print(math.isnan(0 / 0)) --> true
```

### math.phi

**Type:** `number`

The value of the golden ratio.

**Math Phi**

Demonstrates the `math.phi` golden ratio constant.

```lua
print(math.phi) --> 1.618033988749895

-- The golden ratio satisfies phi^2 == phi + 1
print(math.abs(math.phi ^ 2 - (math.phi + 1)) < 1e-12) --> true

-- Split a length of 100 into golden sections
local long = 100 / math.phi
print(math.floor(long * 100) / 100) --> 61.8
```

### math.pi

**Type:** `number`

The value of pi.

**Math Pi**

Demonstrates the `math.pi` constant.

```lua
print(math.pi) --> 3.141592653589793

local radius = 2
print(math.floor(math.pi * radius ^ 2 * 100) / 100) --> 12.56

-- Half a turn in radians is 180 degrees
print(math.deg(math.pi)) --> 180
```

### math.sqrt2

**Type:** `number`

The value of the square root of 2.

**Math Sqrt2**

Demonstrates the `math.sqrt2` constant.

```lua
print(math.sqrt2) --> 1.4142135623730951
print(math.sqrt2 == math.sqrt(2)) --> true

-- The diagonal of a unit square is sqrt(2)
local side = 1
print(math.sqrt(side ^ 2 + side ^ 2) == side * math.sqrt2) --> true
```

### math.tau

**Type:** `number`

The value of tau, which is defined as `2 * math.pi`.

**Math Tau**

Demonstrates the `math.tau` constant.

```lua
print(math.tau) --> 6.283185307179586
print(math.tau == 2 * math.pi) --> true

-- tau is one full turn in radians
print(math.deg(math.tau)) --> 360
print(math.floor(math.tau * 5) / 5) --> 6.2
```

## Functions

### math.abs

**Signature:** `math.abs(x: number): number`

Returns the absolute value of `x`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to return the absolute value of. |

**Returns:** `number` — The absolute value of `x`.

**Math Abs**

Demonstrates the `math.abs` function.

```lua
print(math.abs(-5)) --> 5
print(math.abs(5)) --> 5
print(math.abs(-0.25)) --> 0.25

-- Distance between two values regardless of order
local function distance(a, b)
	return math.abs(a - b)
end
print(distance(3, 10), distance(10, 3)) --> 7 7
```

### math.acos

**Signature:** `math.acos(x: number): number`

Returns the arc cosine of `x`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The cosine value, between `-1` and `1`. |

**Returns:** `number` — The angle in radians whose cosine is `x`, in the range `[0, pi]`.

**Math Acos**

Demonstrates the `math.acos` function.

```lua
print(math.acos(1)) --> 0
print(math.acos(0) == math.pi / 2) --> true
print(math.acos(-1) == math.pi) --> true

-- Angle between two unit vectors from their dot product
local dot = 0.5
print(math.floor(math.deg(math.acos(dot)) + 0.5)) --> 60
```

### math.asin

**Signature:** `math.asin(x: number): number`

Returns the arc sine of `x`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The sine value, between `-1` and `1`. |

**Returns:** `number` — The angle in radians whose sine is `x`, in the range `[-pi/2, pi/2]`.

**Math Asin**

Demonstrates the `math.asin` function.

```lua
print(math.asin(0)) --> 0
print(math.asin(1) == math.pi / 2) --> true
print(math.asin(-1) == -math.pi / 2) --> true

-- Angle of a slope that rises 1 unit over a 2 unit hypotenuse
print(math.floor(math.deg(math.asin(1 / 2)) + 0.5)) --> 30
```

### math.atan

**Signature:** `math.atan(x: number): number`

Returns the arc tangent of `x` in radians.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The value to compute the arc tangent of. |

**Returns:** `number` — The arc tangent of `x` in radians, in the range `[-pi/2, pi/2]`.

**Math Atan**

Demonstrates the `math.atan` function.

```lua
print(math.atan(0)) --> 0
print(math.atan(1) == math.pi / 4) --> true
print(math.deg(math.atan(1))) --> 45

-- The result approaches pi / 2 for large inputs
print(math.atan(math.huge) == math.pi / 2) --> true
```

### math.atan2

**Signature:** `math.atan2(y: number, x: number): number`

Returns the arc tangent of `y`/`x` (in radians) while using the signs of
both parameters to find the quadrant of the result. It also handles
correctly the case of `x` being zero.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `y` | `number` |  | The **Y** coordinate. |
| `x` | `number` |  | The **X** coordinate. |

**Returns:** `number` — The arc tangent of `y`/`x` in radians, in the range `[-pi, pi]`.

**Math Atan2**

Demonstrates the `math.atan2` function.

```lua
-- atan2 uses the signs of both arguments to pick the quadrant
print(math.deg(math.atan2(1, 1))) --> 45
print(math.deg(math.atan2(1, -1))) --> 135
print(math.deg(math.atan2(-1, -1))) --> -135

-- A zero x is handled correctly, unlike math.atan(y / x)
print(math.deg(math.atan2(1, 0))) --> 90
print(math.atan2(0, -1) == math.pi) --> true
```

### math.ceil

**Signature:** `math.ceil(x: number): int`

Returns the smallest integer larger than or equal to `x`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to round up. |

**Returns:** `int` — The smallest integer greater than or equal to `x`.

**Math Ceil**

Demonstrates the `math.ceil` function.

```lua
print(math.ceil(4.1)) --> 5
print(math.ceil(4)) --> 4
print(math.ceil(-4.9)) --> -4

-- Number of pages needed for 23 items at 10 per page
print(math.ceil(23 / 10)) --> 3
```

### math.clamp

**Signature:** `math.clamp(x: number, min: number, max: number): number`

Returns a number between `min` and `max`, inclusive.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to clamp. |
| `min` | `number` |  | The minimum value of the range. |
| `max` | `number` |  | The maximum value of the range; must be greater than or equal to `min`. |

**Returns:** `number` — `x` constrained to the range `[`min`, `max`]`.

**Math Clamp**

Demonstrates the `math.clamp` function.

```lua
print(math.clamp(5, 0, 10)) --> 5
print(math.clamp(-3, 0, 10)) --> 0
print(math.clamp(42, 0, 10)) --> 10

-- Keep a health value inside its valid range
local health = 100
health = math.clamp(health - 130, 0, 100)
print(health) --> 0
```

### math.cos

**Signature:** `math.cos(x: number): number`

Returns the cosine of `x`, assumed to be in radians.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The angle in radians. |

**Returns:** `number` — The cosine of `x`.

**Math Cos**

Demonstrates the `math.cos` function.

```lua
print(math.cos(0)) --> 1
print(math.cos(math.pi)) --> -1

-- The argument is in radians, so convert degrees first
local angle = math.rad(60)
print(math.floor(math.cos(angle) * 1000 + 0.5) / 1000) --> 0.5
```

### math.cosh

**Signature:** `math.cosh(x: number): number`

Returns the hyperbolic cosine of `x`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to compute the hyperbolic cosine of. |

**Returns:** `number` — The hyperbolic cosine of `x`.

**Math Cosh**

Demonstrates the `math.cosh` function.

```lua
print(math.cosh(0)) --> 1
print(math.cosh(1) == math.cosh(-1)) --> true

-- cosh(x) == (e^x + e^-x) / 2
local x = 2
print(math.abs(math.cosh(x) - (math.exp(x) + math.exp(-x)) / 2) < 1e-12) --> true
```

### math.deg

**Signature:** `math.deg(x: number): number`

Returns the angle `x` (given in radians) in degrees.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The angle in radians to convert. |

**Returns:** `number` — The angle `x` converted to degrees.

**Math Deg**

Demonstrates the `math.deg` function.

```lua
print(math.deg(math.pi)) --> 180
print(math.deg(math.pi / 2)) --> 90
print(math.deg(0)) --> 0

-- Trigonometric functions return radians; convert for display
print(math.deg(math.atan2(1, 1))) --> 45
```

### math.exp

**Signature:** `math.exp(x: number): number`

Returns the value `e`^`x`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The exponent. |

**Returns:** `number` — The value of `e` raised to the power `x`.

**Math Exp**

Demonstrates the `math.exp` function.

```lua
print(math.exp(0)) --> 1
print(math.exp(1) == math.e) --> true

-- exp is the inverse of the natural logarithm
print(math.floor(math.log(math.exp(3)) + 0.5)) --> 3
```

### math.floor

**Signature:** `math.floor(x: number): int`

Returns the largest integer smaller than or equal to `x`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to round down. |

**Returns:** `int` — The largest integer less than or equal to `x`.

**Math Floor**

Demonstrates the `math.floor` function.

```lua
print(math.floor(4.9)) --> 4
print(math.floor(4)) --> 4

-- Negative numbers round toward negative infinity, not toward zero
print(math.floor(-4.1)) --> -5

-- Snap a coordinate to a grid of size 4
local grid = 4
print(math.floor(13.7 / grid) * grid) --> 12
```

### math.fmod

**Signature:** `math.fmod(x: number, y: number): number`

Returns the remainder of the division of `x` by `y` that rounds the
quotient towards zero.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The dividend. |
| `y` | `number` |  | The divisor. |

**Returns:** `number` — The remainder of the division of `x` by `y`.

**Math Fmod**

Demonstrates the `math.fmod` function.

```lua
print(math.fmod(7, 3)) --> 1

-- The quotient rounds toward zero, so the result keeps the sign of the dividend
print(math.fmod(-7, 3)) --> -1

-- The % operator rounds toward negative infinity instead
print(-7 % 3) --> 2
```

### math.frexp

**Signature:** `math.frexp(x: number): number, int`

Returns `m` and `e` such that `x` = `m`\*`2`^`e`. `e` is an integer and
the absolute value of `m` is in the range of `0.5` to `1` (inclusive of
`0.5` but exclusive of `1`), or zero when `x` is zero.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to decompose into mantissa and exponent. |

**Returns:** `number`, `int` — The mantissa `m`, a value whose absolute value is in `[0.5, 1)` or
zero. The exponent `e` such that `x = m * 2^e`.

**Math Frexp**

Demonstrates the `math.frexp` function.

```lua
local mantissa, exponent = math.frexp(8)
print(mantissa, exponent) --> 0.5 4

-- x == m * 2^e, with abs(m) in [0.5, 1)
print(mantissa * 2 ^ exponent) --> 8
print(math.frexp(-12)) --> -0.75 4
print(math.frexp(0)) --> 0 0
```

### math.isfinite

**Signature:** `math.isfinite(x: number): boolean`

Returns true if `x` is a finite number, meaning it is neither NaN nor
positive or negative infinity (±[math.huge](/docs/reference/engine/globals/math.md)).

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to test. |

**Returns:** `boolean` — True if `x` is neither NaN nor infinity, false otherwise.

**Math Isfinite**

Demonstrates the `math.isfinite` function.

```lua
print(math.isfinite(1.5)) --> true
print(math.isfinite(math.huge)) --> false
print(math.isfinite(-math.huge)) --> false
print(math.isfinite(math.nan)) --> false

-- Reject bad results of a calculation
local ratio = 1 / 0
print(math.isfinite(ratio) and ratio or 0) --> 0
```

### math.isinf

**Signature:** `math.isinf(x: number): boolean`

Returns true if `x` is positive or negative infinity
(±[math.huge](/docs/reference/engine/globals/math.md)) and false otherwise.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to test. |

**Returns:** `boolean` — True if `x` is positive or negative infinity, false otherwise.

**Math Isinf**

Demonstrates the `math.isinf` function.

```lua
print(math.isinf(math.huge)) --> true
print(math.isinf(-math.huge)) --> true
print(math.isinf(100)) --> false

-- NaN is not infinite
print(math.isinf(math.nan)) --> false
```

### math.isnan

**Signature:** `math.isnan(x: number): boolean`

Returns true if `x` is not a number (NaN) and false otherwise.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to test. |

**Returns:** `boolean` — True if `x` is NaN, false otherwise.

**Math Isnan**

Demonstrates the `math.isnan` function.

```lua
print(math.isnan(math.nan)) --> true
print(math.isnan(0 / 0)) --> true
print(math.isnan(1)) --> false

-- A NaN never equals itself, so == cannot detect it
local value = math.nan
print(value == value) --> false
```

### math.ldexp

**Signature:** `math.ldexp(x: number, e: int): number`

Returns `x`\*`2`^`e` (`e` should be an integer).

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The mantissa value. |
| `e` | `int` |  | The integer exponent. |

**Returns:** `number` — The value `x * 2^e`.

**Math Ldexp**

Demonstrates the `math.ldexp` function.

```lua
print(math.ldexp(1, 3)) --> 8
print(math.ldexp(0.5, 4)) --> 8
print(math.ldexp(3, -1)) --> 1.5

-- ldexp reverses frexp
local mantissa, exponent = math.frexp(40)
print(math.ldexp(mantissa, exponent)) --> 40
```

### math.lerp

**Signature:** `math.lerp(a: number, b: number, t: number): number`

Returns the linear interpolation between `a` and `b` based on the factor
`t`.

This function uses the formula `a`+`(b-a)`\*`t`. `t` is typically between
`0` and `1` but values outside this range are acceptable.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `a` | `number` |  | The starting value. |
| `b` | `number` |  | The ending value. |
| `t` | `number` |  | The interpolation factor, typically between `0` and `1`. |

**Returns:** `number` — The interpolated value between `a` and `b`.

**Math Lerp**

Demonstrates the `math.lerp` function.

```lua
print(math.lerp(10, 20, 0)) --> 10
print(math.lerp(10, 20, 0.5)) --> 15
print(math.lerp(10, 20, 1)) --> 20

-- Values of t outside 0 to 1 extrapolate
print(math.lerp(10, 20, 1.5)) --> 25
print(math.lerp(10, 20, -1)) --> 0
```

### math.log

**Signature:** `math.log(x: number, base?: number): number`

Returns the logarithm of `x` using the given base, or the mathematical
constant `e` if no base is provided (natural logarithm).

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to compute the logarithm of. |
| `base` | `number` | `2.7182818` | The base of the logarithm, the constant `e` by default. |

**Returns:** `number` — The logarithm of `x` in the given base.

**Math Log**

Demonstrates the `math.log` function.

```lua
-- With no base, this is the natural logarithm
print(math.log(math.e)) --> 1
print(math.log(1)) --> 0

-- With a base
print(math.log(8, 2)) --> 3
print(math.log(1000, 10)) --> 3

-- Number of bits needed to represent 255
print(math.floor(math.log(255, 2)) + 1) --> 8
```

### math.log10

**Signature:** `math.log10(x: number): number`

Returns the base-10 logarithm of `x`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to compute the base-10 logarithm of. |

**Returns:** `number` — The base-10 logarithm of `x`.

**Math Log10**

Demonstrates the `math.log10` function.

```lua
print(math.log10(1)) --> 0
print(math.log10(100)) --> 2
print(math.log10(0.001)) --> -3

-- Number of decimal digits in a positive integer
local n = 12345
print(math.floor(math.log10(n)) + 1) --> 5
```

### math.map

**Signature:** `math.map(x: number, inmin: number, inmax: number, outmin: number, outmax: number): number`

Returns a value that represents `x` mapped linearly from the input range
(`inmin` to `inmax`) to the output range (`outmin` to `outmax`). This is
achieved by determining the relative position of `x` within the input
range and applying that ratio to the output range.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to be mapped. |
| `inmin` | `number` |  | The lower bound of the input range. |
| `inmax` | `number` |  | The upper bound of the input range. |
| `outmin` | `number` |  | The lower bound of the output range. |
| `outmax` | `number` |  | The upper bound of the output range. |

**Returns:** `number` — The value of `x` mapped to the output range.

**Math Map**

Demonstrates the `math.map` function.

```lua
print(math.map(5, 0, 10, 0, 100)) --> 50

-- Convert a 0-255 color channel to the 0-1 range
print(math.map(255, 0, 255, 0, 1)) --> 1

-- The output range may be reversed
print(math.map(25, 0, 100, 1, 0)) --> 0.75

-- Values outside the input range are extrapolated, not clamped
print(math.map(20, 0, 10, 0, 100)) --> 200
```

### math.max

**Signature:** `math.max(x: number, ...: number): number`

Returns the maximum value among the numbers passed to the function.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The first number to compare. |
| `...` | `number` |  | Additional numbers to compare. |

**Returns:** `number` — The largest value among all arguments.

**Math Max**

Demonstrates the `math.max` function.

```lua
print(math.max(3, 9, 5)) --> 9
print(math.max(-1, -7)) --> -1

-- Unpack a table to find its largest value
local scores = {42, 17, 88, 63}
print(math.max(table.unpack(scores))) --> 88
```

### math.min

**Signature:** `math.min(x: number, ...: number): number`

Returns the minimum value among the numbers passed to the function.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The first number to compare. |
| `...` | `number` |  | Additional numbers to compare. |

**Returns:** `number` — The smallest value among all arguments.

**Math Min**

Demonstrates the `math.min` function.

```lua
print(math.min(3, 9, 5)) --> 3
print(math.min(-1, -7)) --> -7

-- Cap a value at an upper limit
local requested = 250
print(math.min(requested, 100)) --> 100
```

### math.modf

**Signature:** `math.modf(x: number): number, number`

Returns two numbers: the integral part of `x` and the fractional part of
`x`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to split into integral and fractional parts. |

**Returns:** `number`, `number` — The integral part of `x`. The fractional part of `x`.

**Math Modf**

Demonstrates the `math.modf` function.

```lua
local integral, fractional = math.modf(3.25)
print(integral, fractional) --> 3 0.25

-- Both parts keep the sign of the input
print(math.modf(-3.25)) --> -3 -0.25
```

### math.noise

**Signature:** `math.noise(x: number, y?: number, z?: number): number`

Returns a Perlin noise value. The returned value is most often between the
range of `-1` to `1` (inclusive) but sometimes may be outside that range;
if the interval is critical to you, use [math.clamp(noise, -1, 1)](/docs/reference/engine/globals/math.md)
on the output.

If you leave arguments out, they will be interpreted as zero, so
[math.noise(1.158)](/docs/reference/engine/globals/math.md) is equivalent to
[math.noise(1.158, 0, 0)](/docs/reference/engine/globals/math.md) and [math.noise(1.158, 5.723)](/docs/reference/engine/globals/math.md)
is equivalent to [math.noise(1.158, 5.723, 0)](/docs/reference/engine/globals/math.md).

Note that this function uses a Perlin noise algorithm to assign fixed
values to coordinates. For example, [math.noise(1.158, 5.723)](/docs/reference/engine/globals/math.md)
will always return `0.48397532105446` (to 14 digits) and
[math.noise(1.158, 6)](/docs/reference/engine/globals/math.md) will always return `0.15315161645412`.

If `x`, `y`, and `z` are all integers, the return value will be `0`. For
fractional values of `x`, `y`, and `z`, the return value changes smoothly
and in practice stays between about `-0.9` and `0.9`. For coordinates that
are close to each other, the return values will also be close to each
other.

The noise repeats with a period of `256` on each axis, so
[math.noise(x, y, z)](/docs/reference/engine/globals/math.md) and [math.noise(x + 256, y, z)](/docs/reference/engine/globals/math.md)
return the same value, apart from a small rounding error.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The **X** coordinate of the sample point. |
| `y` | `number` | `0` | The **Y** coordinate of the sample point. |
| `z` | `number` | `0` | The **Z** coordinate of the sample point. |

**Returns:** `number` — A Perlin noise value, typically between `-1` and `1`.

**Math Noise**

Demonstrates the `math.noise` function.

```lua
-- The same coordinates always produce the same value
print(math.noise(1.158, 5.723)) --> 0.4839753210544586
print(math.noise(1.158, 6)) --> 0.15315161645412445

-- Missing arguments are treated as zero
print(math.noise(1.158) == math.noise(1.158, 0, 0)) --> true

-- Integer coordinates always return 0
print(math.noise(1, 2, 3)) --> 0

-- The noise repeats every 256 units on each axis
print(math.noise(0.5, 0.3, 0.1) == math.noise(256.5, 0.3, 0.1)) --> true

-- Clamp if you need a strict -1 to 1 range
print(math.clamp(math.noise(0.5, 0.3, 0.1), -1, 1) == math.noise(0.5, 0.3, 0.1)) --> true

-- Inputs are rounded to 32-bit floats, so shifting by 256 matches only to a small rounding error
print(math.abs(math.noise(1.158, 5.723) - math.noise(257.158, 5.723)) < 0.001) --> true
```

### math.pow

**Signature:** `math.pow(x: number, y: number): number`

Returns `x`^`y` (you can also use the expression `x`^`y` to compute this
value).

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The base value. |
| `y` | `number` |  | The exponent value. |

**Returns:** `number` — The value `x` raised to the power `y`.

**Math Pow**

Demonstrates the `math.pow` function.

```lua
print(math.pow(2, 10)) --> 1024
print(math.pow(9, 0.5)) --> 3
print(math.pow(2, -1)) --> 0.5

-- Equivalent to the ^ operator
print(math.pow(5, 3) == 5 ^ 3) --> true
```

### math.rad

**Signature:** `math.rad(x: number): number`

Returns the angle `x` (given in degrees) in radians.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The angle in degrees to convert. |

**Returns:** `number` — The angle `x` converted to radians.

**Math Rad**

Demonstrates the `math.rad` function.

```lua
print(math.rad(180) == math.pi) --> true
print(math.rad(90) == math.pi / 2) --> true
print(math.rad(0)) --> 0

-- Trigonometric functions take radians, so convert degrees first
print(math.floor(math.sin(math.rad(30)) * 1000 + 0.5) / 1000) --> 0.5
```

### math.random

**Signature:** `math.random(m: number, n: number): number`

When called without arguments, returns a uniform pseudo-random real number
in the range of `0` to `1` (inclusive of `0` but exclusive of `1`).

When called with an integer number `m`, returns a uniform pseudo-random
integer in the range of `1` to `m`, inclusive.

When called with two integer numbers `m` and `n`, returns a uniform
pseudo-random integer in the range of `m` to `n`, inclusive.

If the range contains no integers, such as `math.random(0)` or
`math.random(5, 1)`, the function raises an "interval is empty" error.

Internally, this uses a 32-bit PCG (Permuted Congruential Generator) which
achieves excellent statistical performance and makes its output hard to
predict.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `m` | `number` |  | When used alone, the upper bound of the integer range, which must be at least `1` (the lower bound is `1`). When used with `n`, the lower bound. |
| `n` | `number` |  | The upper bound of the integer range. Must be at least `m`. |

**Returns:** `number` — A pseudo-random number within the specified range.

**Math Random**

Demonstrates the `math.random` function.

```lua
-- No arguments: a real number in [0, 1)
local unit = math.random()
print(unit >= 0 and unit < 1) --> true

-- One argument: an integer in [1, m]
local die = math.random(6)
print(die >= 1 and die <= 6 and die == math.floor(die)) --> true

-- Two arguments: an integer in [m, n]
local offset = math.random(-5, 5)
print(offset >= -5 and offset <= 5 and offset == math.floor(offset)) --> true

-- A single argument below 1, or a lower bound above the upper bound, leaves no integers to pick
print(pcall(math.random, 0)) --> false invalid argument #1 to 'random' (interval is empty)
print(pcall(math.random, 5, 1)) --> false invalid argument #2 to 'random' (interval is empty)
```

### math.randomseed

**Signature:** `math.randomseed(x: number): ()`

Sets `x` as the seed for the pseudo-random generator: equal seeds produce
equal sequences of numbers.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The seed value for the pseudo-random number generator. |

**Returns:** `()`

**Math Randomseed**

Demonstrates the `math.randomseed` function.

```lua
math.randomseed(1234)
local first = {math.random(100), math.random(100), math.random(100)}

-- Reseeding with the same value replays the same sequence
math.randomseed(1234)
local second = {math.random(100), math.random(100), math.random(100)}

print(first[1] == second[1] and first[2] == second[2] and first[3] == second[3]) --> true
```

### math.round

**Signature:** `math.round(x: number): number`

Returns the integer with the smallest difference between it and the given
number. For example, the value `5.8` returns `6`.

For values like `0.5` that are equidistant to two integers, the value with
the greater difference between it and zero is chosen. In other words, the
function "rounds away from zero" such that `0.5` rounds to `1` and `-0.5`
rounds to `-1`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The value to be rounded. |

**Returns:** `number` — The nearest integer to `x`, rounding away from zero for midpoints.

**Math Round**

Demonstrates the `math.round` function.

```lua
print(math.round(5.8)) --> 6
print(math.round(5.2)) --> 5

-- Midpoints round away from zero
print(math.round(0.5)) --> 1
print(math.round(-0.5)) --> -1
print(math.round(2.5)) --> 3

-- Round to two decimal places
print(math.round(3.14159 * 100) / 100) --> 3.14
```

### math.sign

**Signature:** `math.sign(x: number): int`

Returns `-1` if `x` is less than `0`, `0` if `x` equals `0`, or `1` if `x`
is greater than `0`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to determine the sign of. |

**Returns:** `int` — `-1` if `x` is negative, `0` if `x` is zero, or `1` if `x` is
positive.

**Math Sign**

Demonstrates the `math.sign` function.

```lua
print(math.sign(-12)) --> -1
print(math.sign(0)) --> 0
print(math.sign(7.5)) --> 1

-- Move toward a target without overshooting direction
local position, target = 10, 4
position += math.sign(target - position)
print(position) --> 9
```

### math.sin

**Signature:** `math.sin(x: number): number`

Returns the sine of `x`, assumed to be in radians.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The angle in radians. |

**Returns:** `number` — The sine of `x`.

**Math Sin**

Demonstrates the `math.sin` function.

```lua
print(math.sin(0)) --> 0
print(math.sin(math.pi / 2)) --> 1

-- The argument is in radians, so convert degrees first
print(math.floor(math.sin(math.rad(30)) * 1000 + 0.5) / 1000) --> 0.5

-- sin^2 + cos^2 == 1
local angle = 1.2
print(math.abs(math.sin(angle) ^ 2 + math.cos(angle) ^ 2 - 1) < 1e-12) --> true
```

### math.sinh

**Signature:** `math.sinh(x: number): number`

Returns the hyperbolic sine of `x`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to compute the hyperbolic sine of. |

**Returns:** `number` — The hyperbolic sine of `x`.

**Math Sinh**

Demonstrates the `math.sinh` function.

```lua
print(math.sinh(0)) --> 0
print(math.sinh(-1) == -math.sinh(1)) --> true

-- sinh(x) == (e^x - e^-x) / 2
local x = 2
print(math.abs(math.sinh(x) - (math.exp(x) - math.exp(-x)) / 2) < 1e-12) --> true
```

### math.sqrt

**Signature:** `math.sqrt(x: number): number`

Returns the square root of `x`. You can also use the expression `x`^`0.5`
to compute this value.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to compute the square root of. |

**Returns:** `number` — The square root of `x`.

**Math Sqrt**

Demonstrates the `math.sqrt` function.

```lua
print(math.sqrt(16)) --> 4
print(math.sqrt(2) == math.sqrt2) --> true

-- Same as raising to the power 0.5
print(math.sqrt(49) == 49 ^ 0.5) --> true

-- Distance between two points
local dx, dy = 3, 4
print(math.sqrt(dx * dx + dy * dy)) --> 5
```

### math.tan

**Signature:** `math.tan(x: number): number`

Returns the tangent of `x`, assumed to be in radians.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The angle in radians. |

**Returns:** `number` — The tangent of `x`.

**Math Tan**

Demonstrates the `math.tan` function.

```lua
print(math.tan(0)) --> 0

-- The argument is in radians, so convert degrees first
print(math.floor(math.tan(math.rad(45)) * 1000 + 0.5) / 1000) --> 1

-- tan(x) == sin(x) / cos(x)
local angle = 0.7
print(math.abs(math.tan(angle) - math.sin(angle) / math.cos(angle)) < 1e-12) --> true
```

### math.tanh

**Signature:** `math.tanh(x: number): number`

Returns the hyperbolic tangent of `x`.

**Parameters:**

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `x` | `number` |  | The number to compute the hyperbolic tangent of. |

**Returns:** `number` — The hyperbolic tangent of `x`.

**Math Tanh**

Demonstrates the `math.tanh` function.

```lua
print(math.tanh(0)) --> 0
print(math.tanh(-1) == -math.tanh(1)) --> true

-- The output approaches 1 for large inputs, squashing any value into (-1, 1)
print(math.tanh(20) > 0.999999) --> true
```