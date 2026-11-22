<!-- Source: https://create.roblox.com/docs/en-us/reference/engine/libraries/bit32 -->

bit32 | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/reference/engine/libraries/bit32.md | Documentation index: https://create.roblox.com/docs/llms.txt | Engine API index: https://create.roblox.com/docs/reference/engine/llms.txt

Learn

1. [Libraries](/docs/en-us/reference/engine/libraries)
2. /
3. [bit32](/docs/en-us/reference/engine/libraries/bit32)

English

Feedback

Engine Library

bit32

---

## Summary

Functions

|

[arshift](#arshift) (x :  [number](/docs/en-us/luau/numbers) , disp :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |
| --- | --- |
|

[band](#band) (numbers :  [Tuple](/docs/en-us/luau/tuples) ) :[number](/docs/en-us/luau/numbers)

 |
|

[bnot](#bnot) (x :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |
|

[bor](#bor) (numbers :  [Tuple](/docs/en-us/luau/tuples) ) :[number](/docs/en-us/luau/numbers)

 |
|

[btest](#btest) (numbers :  [Tuple](/docs/en-us/luau/tuples) ) :[boolean](/docs/en-us/luau/booleans)

 |
|

[bxor](#bxor) (numbers :  [Tuple](/docs/en-us/luau/tuples) ) :[number](/docs/en-us/luau/numbers)

 |
|

[byteswap](#byteswap) (x :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |
|

[countlz](#countlz) (n :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |
|

[countrz](#countrz) (n :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |
|

[extract](#extract) (n :  [number](/docs/en-us/luau/numbers) , field :  [number](/docs/en-us/luau/numbers) , width :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |
|

[replace](#replace) (n :  [number](/docs/en-us/luau/numbers) , v :  [number](/docs/en-us/luau/numbers) , field :  [number](/docs/en-us/luau/numbers) , width :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |
|

[lrotate](#lrotate) (x :  [number](/docs/en-us/luau/numbers) , disp :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |
|

[lshift](#lshift) (x :  [number](/docs/en-us/luau/numbers) , disp :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |
|

[rrotate](#rrotate) (x :  [number](/docs/en-us/luau/numbers) , disp :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |
|

[rshift](#rshift) (x :  [number](/docs/en-us/luau/numbers) , disp :  [number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

 |

---

API Reference

Functions

arshift

bit32.arshift (

x :[number](/docs/en-us/luau/numbers) , disp :[number](/docs/en-us/luau/numbers)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

x :[number](/docs/en-us/luau/numbers)

 |
|

disp :[number](/docs/en-us/luau/numbers)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 Arithmetic Shift

Provide feedback

---

band

bit32.band (numbers :[Tuple](/docs/en-us/luau/tuples) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

numbers :[Tuple](/docs/en-us/luau/tuples)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 AND

Provide feedback

---

bnot

bit32.bnot (x :[number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

x :[number](/docs/en-us/luau/numbers)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 NOT

Provide feedback

---

bor

bit32.bor (numbers :[Tuple](/docs/en-us/luau/tuples) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

numbers :[Tuple](/docs/en-us/luau/tuples)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 OR

Provide feedback

---

btest

bit32.btest (numbers :[Tuple](/docs/en-us/luau/tuples) ) :[boolean](/docs/en-us/luau/booleans)

Parameters

|

numbers :[Tuple](/docs/en-us/luau/tuples)

 |

Returns

[boolean](/docs/en-us/luau/booleans)

Code Samples

##### Bit32 Test

Provide feedback

---

bxor

bit32.bxor (numbers :[Tuple](/docs/en-us/luau/tuples) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

numbers :[Tuple](/docs/en-us/luau/tuples)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 XOR

Provide feedback

---

byteswap

bit32.byteswap (x :[number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

x :[number](/docs/en-us/luau/numbers)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 Byte Swap

Provide feedback

---

countlz

bit32.countlz (n :[number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

n :[number](/docs/en-us/luau/numbers)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 Count Leading Zeros

Provide feedback

---

countrz

bit32.countrz (n :[number](/docs/en-us/luau/numbers) ) :[number](/docs/en-us/luau/numbers)

Parameters

|

n :[number](/docs/en-us/luau/numbers)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 Count Trailing Zeros

Provide feedback

---

extract

bit32.extract (

n :[number](/docs/en-us/luau/numbers) , field :[number](/docs/en-us/luau/numbers) , width :[number](/docs/en-us/luau/numbers)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

n :[number](/docs/en-us/luau/numbers)

 |
|

field :[number](/docs/en-us/luau/numbers)

 |
|

width :[number](/docs/en-us/luau/numbers)

Default Value: 1 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 Extract

Provide feedback

---

replace

bit32.replace (

n :[number](/docs/en-us/luau/numbers) , v :[number](/docs/en-us/luau/numbers) , field :[number](/docs/en-us/luau/numbers) , width :[number](/docs/en-us/luau/numbers)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

n :[number](/docs/en-us/luau/numbers)

 |
|

v :[number](/docs/en-us/luau/numbers)

 |
|

field :[number](/docs/en-us/luau/numbers)

 |
|

width :[number](/docs/en-us/luau/numbers)

Default Value: 1 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 Replace

Provide feedback

---

lrotate

bit32.lrotate (

x :[number](/docs/en-us/luau/numbers) , disp :[number](/docs/en-us/luau/numbers)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

x :[number](/docs/en-us/luau/numbers)

 |
|

disp :[number](/docs/en-us/luau/numbers)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 Left Rotate

Provide feedback

---

lshift

bit32.lshift (

x :[number](/docs/en-us/luau/numbers) , disp :[number](/docs/en-us/luau/numbers)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

x :[number](/docs/en-us/luau/numbers)

 |
|

disp :[number](/docs/en-us/luau/numbers)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 Left Shift

Provide feedback

---

rrotate

bit32.rrotate (

x :[number](/docs/en-us/luau/numbers) , disp :[number](/docs/en-us/luau/numbers)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

x :[number](/docs/en-us/luau/numbers)

 |
|

disp :[number](/docs/en-us/luau/numbers)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 Right Rotate

Provide feedback

---

rshift

bit32.rshift (

x :[number](/docs/en-us/luau/numbers) , disp :[number](/docs/en-us/luau/numbers)

) :[number](/docs/en-us/luau/numbers)

Parameters

|

x :[number](/docs/en-us/luau/numbers)

 |
|

disp :[number](/docs/en-us/luau/numbers)

 |

Returns

[number](/docs/en-us/luau/numbers)

Code Samples

##### Bit32 Right Shift

Provide feedback

---

Jump to

▼

bit32

[Summary](#summary)

[Functions](#summary-functions)

[Functions](#functions)

[arshift()](#arshift)

[band()](#band)

[bnot()](#bnot)

[bor()](#bor)

[btest()](#btest)

[bxor()](#bxor)

[byteswap()](#byteswap)

[countlz()](#countlz)

[countrz()](#countrz)

[extract()](#extract)

[replace()](#replace)

[lrotate()](#lrotate)

[lshift()](#lshift)

[rrotate()](#rrotate)

[rshift()](#rshift)

English

Feedback

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
