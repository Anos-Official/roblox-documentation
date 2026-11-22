<!-- Source: https://create.roblox.com/docs/cloud/reference/types -->

Types | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/reference/types.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)
4. /
5. [Common components](/docs/cloud/reference/patterns)

# Types

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/reference/types.md)

Open Cloud represents request and response payloads as [standard JSON](https://www.ecma-international.org/publications-and-standards/standards/ecma-404/) . The standards JSON types are text, values, objects, arrays, numbers, and strings. Some types have special considerations for representing specific kinds of data, which are described in the following sections.

## [Timestamp](#timestamp)[](#timestamp)

Uses RFC 3339, where generated output will always be Z-normalized and uses 0, 3, 6 or 9 fractional digits. Offsets other than "Z" are also accepted.

Example Timestamp

```

{ "timestamp": "1972-01-01T10:00:20.021Z" }

```

## [Duration](#duration)[](#duration)

Generated output always contains 0, 3, 6, or 9 fractional digits, depending on required precision, followed by the suffix "s". Accepted are any fractional digits (also none) as long as they fit into nano-seconds precision and the suffix "s" is required. The range must be from -315,576,000,000 to 315,576,000,000 seconds, inclusive.

Example Durations

```

{

  "duration-9": "1.000340012s",

  "duration-0": "1s"

}

```

## [Bytes](#bytes)[](#bytes)

Byte data are encoded as a string using standard base64 encoding with paddings. Either standard or URL-safe base64 encoding with or without paddings are supported.

Example Bytes

```

{

  "bytes": "YWJjMTIzIT8kKiYoKSctRbLx+"

}

```

## [FieldMask](#fieldmask)[](#fieldmask)

A FieldMask is a string that describes the fields to act on when making a request. To construct a field mask, you specify comma delimited JSON field names in a string. For example, given the following:

Example JSON

```

{

  "foo": {

    "a": "c",

    "b": "d"

  },

  "bar": "x",

  "baz": "y"

}

```

If you wanted to specify a field mask to update the values of only foo.b  and bar , the field mask would look like: foo.b, bar

In Open Cloud, update methods that support a field mask have a parameter named updateMask , where you can specify a field mask as a value.

## [Money](#money)[](#money)

Generally used to define a price, the Money  type has a three-letter currency code (as defined in ISO 4217) and a quantity, which uses the Decimal  type. For example, you might represent a $17.99 price like this:

```

"myPrice": {

  "currencyCode": "USD",

  "quantity": {

    "significand": 1799,

    "exponent": -2

  }

}

```

Creator Store products require an exponent  of -9, so the same price looks like this:

```

"myPrice": {

  "currencyCode": "USD",

  "quantity": {

    "significand": 17990000000,

    "exponent": -9

  }

}

```

## [Decimal](#decimal)[](#decimal)

Represents a decimal number in a form similar to scientific notation, with significant digits and an exponent.

Examples:

-

17

{"significand": 17, "exponent": 0}  or just {"significand": 17}

-

-0.005

{"significand": -5, "exponent": -3}

-

33.5 million (33,500,000)

{"significand": 335, "exponent": 5}

-

11/8 (1.375)

{"significand": 1375, "exponent": -3}

When exponent  is greater than 0, it represents the number of trailing zeroes after the significant digits. When exponent  is less than 0, it represents how many of the significant digits come after the decimal point. When exponent  is 0, the value of the Decimal  is the value of the significand .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
