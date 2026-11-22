<!-- Source: https://create.roblox.com/docs/en-us/luau/operators -->

Operators | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/luau/operators.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/en-us/scripting)
6. /
7. [Luau reference](/docs/en-us/luau)
8. /
9. Features

# Operators

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/luau/operators.md)

An operator  is a symbol for performing an operation or conditional evaluation.

## [Logical](#logical)[](#logical)

Logical operators return values depending on the boolean values of the given arguments. If an argument isn't false  or nil , then the operator evaluates it as true . Unlike many other languages, Luau considers both zero and the empty string as true . The following table summarizes how logical operators behave in [conditionals](/docs/en-us/luau/control-structures#if-statements) .

| Operator | | Descriptions |
| --- | --- |
| and | | Evaluates as true  only if both conditions are true |
| or | | Evaluates as true  if either condition is true |
| not | | Evaluates as the opposite of the condition |

### [and](#and)[](#and)

The binary operator and  returns one of the two arguments. If the first argument evaluates to true , then it returns the second argument. Otherwise, it returns the first argument.

```

print(4 and 5) -- 5

print(nil and 12) -- nil

print(false and 12) -- false

print(false and true) -- false

print(false and false) -- false

print(true and false) -- false

print(true and true) -- true

```

You can use and  to test multiple conditions in [control structures](/docs/en-us/luau/control-structures)  such as [if  statements](/docs/en-us/luau/control-structures#if-statements)  and [while  loops](/docs/en-us/luau/control-structures#while-loops) . For example, the following if ‑ then  statement tests that two conditions are both true:

```

local pasta = true

local tomatoSauce = true

if pasta == true and tomatoSauce == true then

	print("We have spaghetti dinner")

else

	print("Something is missing...")

end

-- Output: We have spaghetti dinner

```

### [or](#or)[](#or)

The binary operator or  returns one of the two arguments. If the first argument evaluates to true , then it returns the first argument. Otherwise, it returns the second argument.

```

local y = x or 1

print(y) -- 1 because x doesn't exist and is therefore nil

local d = false

local e = d or 1

print(e) -- 1 because d is false

print(4 or 5) -- 4

print(nil or 12) -- 12

print(false or 12) -- 12

print(false or true) -- true

print(false or false) -- false

print(true or false) -- true

print(true or true) -- true

```

You can use or  to perform complex logical tests in [control structures](/docs/en-us/luau/control-structures) . For example, the following if ‑ then  statement tests whether two conditions are true or  a third condition is true:

```

local pasta = false

local tomatoSauce = true

local garlicBread = true

if (pasta == true and tomatoSauce == true) or garlicBread == true then

	print("We have either spaghetti dinner OR garlic bread")

else

	print("Something is missing...")

end

-- Output: We have either spaghetti dinner OR garlic bread

```

### [not](#not)[](#not)

The unary operator not  returns the opposite boolean value of the argument. If the argument is false  or nil , then it returns true . Otherwise, it returns false .

```

print(not true) -- false

print(not false) -- true

print(not nil) -- true

print(not "text") -- false

print(not 0) -- false

```

You can use the not  operator to trigger a conditional or loop if a variable is false  or nil .

```

local nilVariable  -- Variable is declared but has no value, so it's nil

local falseVariable = false  -- Variable is declared with value of false

if not nilVariable then

	print(nilVariable)  -- Outputs "nil" because nil isn't true

end

if not falseVariable then

	print(falseVariable)  -- Outputs "false" because false isn't true

end

```

You can also use the not  operator to test for the opposite of an entire multi-condition statement. In the following code sample, the if ‑ then  conditional tests that it's neither true that three is greater than four nor is it true that five is greater than four.

```

local three = 3

local four = 4

local five = 5

if not (three > four or five < four) then

	print("Three is less than 4 and five is greater than 4.")

end

-- Output: Three is less than 4 and five is greater than 4.

```

## [Relational](#relational)[](#relational)

Relational operators compare two parameters and return a [boolean](/docs/en-us/luau/booleans) : true  or false .

| Operator | | Description | | Example | | Associated metamethod |
| == | | Equal to | | 3 == 5  → false | | __eq |
| ~= | | Not equal to | | 3 ~= 5  → true | |  |
| > | | Greater than | | 3 > 5  → false | |  |
| < | | Less than | | 3 < 5  → true | | __lt |
| >= | | Greater than or equal to | | 3 >= 5  → false | |  |
| <= | | Less than or equal to | | 3 <= 5  → true | | __le |

## [Arithmetic](#arithmetic)[](#arithmetic)

Luau supports the usual binary operators along with exponentiation, modulus, and unary negation.

| Operator | | Description | | Example | | Associated metamethod |
| + | | Addition | | 1 + 1 = 2 | | __add |
| - | | Subtraction | | 1 - 1 = 0 | | __sub |
| * | | Multiplication | | 5 * 5 = 25 | | __mul |
| / | | Division | | 10 / 5 = 2 | | __div |
| // | | Floor Division | |

10 // 4 = 2
 -10 // 4 = -3

 | | __idiv |
| ^ | | Exponentiation | | 2 ^ 4 = 16 | | __pow |
| % | | Modulus | | 13 % 7 = 6 | | __mod |
| - | | Unary negation | | -2 = 0 - 2 | | __unm |

## [Compound assignment](#compound-assignment)[](#compound-assignment)

You can use compound assignment operators to set a variable equal to the result of an operation where the first parameter is the variable's current value.

The operation in a compound assignment occurs once. For example, if an expression generates a random index in a table, Luau uses the same index for both the operation and the assignment.

In the following examples, suppose local x = 3 .

| Operator | | Operation | | Example | | New Value of x |
| += | | Addition | | x += 2 | | 5 |
| -= | | Subtraction | | x -= 2 | | 1 |
| *= | | Multiplication | | x *= 2 | | 6 |
| /= | | Division | | x /= 2 | | 1.5 |
| //= | | Floor Division | | x //= 2 | | 1 |
| %= | | Modulus | | x %= 2 | | 1 |
| ^= | | Exponentiation | | x ^= 2 | | 9 |
| ..= | | Concatenation | | x ..= " World!"  | | "3 World!" |

## [Miscellaneous](#miscellaneous)[](#miscellaneous)

Miscellaneous operators include concatenation  and length .

| Operator | | Description | | Example | | Associated metamethod |
| .. | | Concatenates two strings | | print("Hello " .. "World!") | | __concat |
| # | | Length of table | | If tableVar = {1, 2, 3} , then #tableVar == 3 . | | __len |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
