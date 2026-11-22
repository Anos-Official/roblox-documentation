<!-- Source: https://create.roblox.com/docs/nl-nl/luau/numbers -->

Getallen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Luau-referentie](/docs/nl-nl/luau)
8. /
9. Typen

# Getallen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het getal  gegevenstype, of double , vertegenwoordigt een [dubbelprecisie (64-bits) drijvend-komma](https://wikipedia.org/wiki/Double-precision_floating-point_format)  getal. Getallen kunnen variëren van -1.7 * 10 308  tot 1.7 * 10 308  (ongeveer 15 cijfers precisie, positief of negatief).

## [Ondertekend en niet-ondertekend](#ondertekend-en-niet-ondertekend)[](#ondertekend-en-niet-ondertekend)

Het teken van het getal geeft aan of het positief of negatief is. Bijvoorbeeld, 1  is positief en -1  is negatief. In Luau is het getal -0  gelijk aan 0 .

```

print(0 == -0)  --> true

print(-0 > 1)  --> false

print(-0 < 1)  --> true

print(-0 > -1)  --> true

print(-0 < -1)  --> false

```

## [Getal classificaties](#getal-classificaties)[](#getal-classificaties)

Luau maakt geen onderscheid tussen gehele getallen en getallen, maar de API-referentie maakt soms onderscheid tussen hen om specifieker te zijn over hoe elke API te gebruiken.

### [float](#float)[](#float)

Het float  gegevenstype verwijst naar een reëel getal met een decimaal. In computerwetenschappelijke termen zijn ze [enkele precisie (32-bits) drijvende komma getallen](https://wikipedia.org/wiki/Single-precision_floating-point_format) , die niet zo precies zijn als dubbelprecisie drijvende komma getallen, maar voldoende precisie bieden voor de meeste gebruiksgevallen en minder geheugen en opslag vereisen.

### [int](#int)[](#int)

Het integer  gegevenstype, of int , verwijst naar een 32-bits geheel getal, dat varieert van -2 31  tot 2 31  - 1. Eigenschappen en functies die gehele getallen verwachten, kunnen automatisch afronden of fouten genereren wanneer je niet-gehele getallen aan hen toewijst of doorgeeft.

### [int64](#int64)[](#int64)

Het int64  gegevenstype verwijst naar een ondertekend 64-bits geheel getal, dat varieert van -2 63  tot 2 63  - 1. Dit type geheel getal is gebruikelijk voor methoden die ID-nummers van de Roblox-website gebruiken. Bijvoorbeeld, [Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId)  is een int64 , en [MarketplaceService:PromptPurchase()](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptPurchase)  en [TeleportService:Teleport()](/docs/nl-nl/reference/engine/classes/TeleportService#Teleport)  verwachten elk int64  voor de ID-argumenten.

## [Notatie](#notatie)[](#notatie)

Getallen worden genoteerd met de meest significante cijfers eerst (big-endian). Er zijn meerdere manieren om getal literals in Luau te noteren:

-

[Decimaal (basis-10)](https://wikipedia.org/wiki/Decimal)  — Schrijf de cijfers van het getal normaal met de cijfers 0–9 met een enkele optionele decimale punt, bijvoorbeeld 7 , 1.25 , of -22.5 .

-

[Wetenschappelijke notatie](https://wikipedia.org/wiki/Scientific_notation)  — Schrijf een decimaal getal gevolgd door e  of e+ , gevolgd door een geheel getal om het decimale getal tot een macht van 10 te verheffen. Bijvoorbeeld, 12e3  is 12 × 10^3 (12.000).

-

[Hexadecimaal (basis-16)](https://wikipedia.org/wiki/Hexadecimal)  — Begin het getal met 0x  gevolgd door cijfers 0–9 of A–F (hoofdletters genegeerd). Bijvoorbeeld, 0xF  is 15 en 0x3FC  is 1020.

-

[Binair (basis-2)](https://wikipedia.org/wiki/Binary_number)  — Begin het getal met 0b  gevolgd door 0's of 1's, bijvoorbeeld 0b1100  (12 in decimale notatie).

Om de leesbaarheid van lange getallen te verbeteren, kun je underscores op elke plaats binnen een getal literal opnemen zonder de waarde te veranderen, ** behalve**  aan het begin waar dit het een identifier zou maken. Bijvoorbeeld, 1_234_567  is hetzelfde als 1234567 , die beide gelijk zijn aan 1.234.567.

## [Operaties](#operaties)[](#operaties)

Je kunt logische en relationele [operatoren](/docs/nl-nl/luau/operators)  gebruiken om getallen te manipuleren en te vergelijken. Je kunt ook wiskundige functies zoals [math.sqrt()](/docs/nl-nl/reference/engine/libraries/math#sqrt)  en [math.exp()](/docs/nl-nl/reference/engine/libraries/math#exp)  in de [math](/docs/nl-nl/reference/engine/libraries/math)  bibliotheek en bitwise operaties in de [bit32](/docs/nl-nl/reference/engine/libraries/bit32)  bibliotheek gebruiken.

## [Type introspectie](#type-introspectie)[](#type-introspectie)

Je kunt bepalen of een waarde x  een getal is door type(x)  of typeof(x)  te gebruiken. Beide retourneren de string number  als x  een getal is.

```

local testInt = 5

local testDecimal = 9.12761656

local testString = "Hallo"

print(type(testInt))  --> number

print(type(testDecimal))  --> number

print(type(testString))  --> string

print(typeof(testInt))  --> number

print(typeof(testDecimal))  --> number

print(typeof(testString))  --> string

```

## [Afrondfuncties](#afrondfuncties)[](#afrondfuncties)

Je kunt getallen afronden met [math.floor()](/docs/nl-nl/reference/engine/libraries/math#floor) , [math.ceil()](/docs/nl-nl/reference/engine/libraries/math#ceil) , of [math.modf()](/docs/nl-nl/reference/engine/libraries/math#modf) . Deze functies retourneren een geheel resultaat als Luau het kan weergeven als een geheel getal. Als het getal te groot is, retourneert Luau het als een float.

-

Om te bepalen of een getal x  een geheel getal is, gebruik math.floor(x) == x .

-

Om een getal naar beneden af te ronden, gebruik [math.floor()](/docs/nl-nl/reference/engine/libraries/math#floor) .

-

Om een getal naar boven af te ronden, gebruik [math.ceil()](/docs/nl-nl/reference/engine/libraries/math#ceil) .

-

Om een getal naar nul af te ronden, gebruik [math.modf()](/docs/nl-nl/reference/engine/libraries/math#modf) . Het retourneert ook het fractionele verschil van het afgeronde getal als een tweede resultaat.

```

print(math.floor(3.3))  --> 3

print(math.floor(-3.3))  --> -4

print(math.ceil(3.3))  --> 4

print(math.ceil(-3.3))  --> -3

print(math.modf(3.3))  --> 3 0.2999999999999998

print(math.modf(-3.3))  --> -3 -0.2999999999999998

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
