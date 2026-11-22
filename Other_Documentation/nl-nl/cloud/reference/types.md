<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/reference/types -->

Typen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)
4. /
5. [Gemeenschappelijke componenten](/docs/nl-nl/cloud/reference/patterns)

# Typen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Open Cloud vertegenwoordigt aanvraag- en antwoordpayloads als [standaard JSON](https://www.ecma-international.org/publications-and-standards/standards/ecma-404/) . De standaard JSON-typen zijn tekst, waarden, objecten, arrays, getallen en strings. Sommige typen hebben speciale overwegingen voor het vertegenwoordigen van specifieke soorten gegevens, die in de volgende secties worden beschreven.

## [Tijdstempel](#tijdstempel)[](#tijdstempel)

Gebruikt RFC 3339, waarbij de gegenereerde uitvoer altijd Z-genormaliseerd zal zijn en 0, 3, 6 of 9 fractiedigits gebruikt. Afwijkingen anders dan "Z" worden ook geaccepteerd.

Voorbeeld Tijdstempel

```

{ "timestamp": "1972-01-01T10:00:20.021Z" }

```

## [Duur](#duur)[](#duur)

Gegenereerde uitvoer bevat altijd 0, 3, 6 of 9 fractiedigits, afhankelijk van vereiste precisie, gevolgd door de suffix "s". Geaccepteerd zijn alle fractiedigits (ook geen) zolang ze passen in nanoseconden precisie en de suffix "s" is vereist. Het bereik moet van -315.576.000.000 tot 315.576.000.000 seconden zijn, inclusief.

Voorbeeld Duur

```

{

  "duration-9": "1.000340012s",

  "duration-0": "1s"

}

```

## [Bytes](#bytes)[](#bytes)

Bytegegevens worden gecodeerd als een string met behulp van standaard base64-codering met opvullingen. Zowel standaard als URL-veilige base64-codering met of zonder opvullingen worden ondersteund.

Voorbeeld Bytes

```

{

  "bytes": "YWJjMTIzIT8kKiYoKSctRbLx+"

}

```

## [FieldMask](#fieldmask)[](#fieldmask)

Een FieldMask is een string die de velden beschrijft waarop moet worden ingegrepen bij het doen van een aanvraag. Om een field mask te construeren, specificeer je komma-gescheiden JSON-veldnamen in een string. Bijvoorbeeld, gegeven het volgende:

Voorbeeld JSON

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

Als je een field mask wilde specificeren om de waarden van alleen foo.b  en bar  bij te werken, zou het field mask eruitzien als: foo.b, bar

In Open Cloud hebben update-methoden die een field mask ondersteunen een parameter genaamd updateMask , waar je een field mask als waarde kunt specificeren.

## [Geld](#geld)[](#geld)

Over het algemeen gebruikt om een prijs te definiëren, heeft het Money -type een drieletterige valutacode (zoals gedefinieerd in ISO 4217) en een hoeveelheid, die het Decimal -type gebruikt. Bijvoorbeeld, je zou een prijs van $17,99 als volgt kunnen weergeven:

```

"myPrice": {

  "currencyCode": "USD",

  "quantity": {

    "significand": 1799,

    "exponent": -2

  }

}

```

Creator Store-producten vereisen een exponent  van -9, dus dezelfde prijs ziet er als volgt uit:

```

"myPrice": {

  "currencyCode": "USD",

  "quantity": {

    "significand": 17990000000,

    "exponent": -9

  }

}

```

## [Decimaal](#decimaal)[](#decimaal)

Stelt een decimaal getal voor in een vorm die lijkt op wetenschappelijke notatie, met significante cijfers en een exponent.

Voorbeelden:

-

17

{"significand": 17, "exponent": 0}  of gewoon {"significand": 17}

-

-0.005

{"significand": -5, "exponent": -3}

-

33,5 miljoen (33.500.000)

{"significand": 335, "exponent": 5}

-

11/8 (1.375)

{"significand": 1375, "exponent": -3}

Wanneer exponent  groter is dan 0, vertegenwoordigt het het aantal achtereenvolgende nullen na de significante cijfers. Wanneer exponent  kleiner is dan 0, vertegenwoordigt het hoeveel van de significante cijfers na de decimale punt komen. Wanneer exponent  0 is, is de waarde van de Decimal  de waarde van de significand .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
