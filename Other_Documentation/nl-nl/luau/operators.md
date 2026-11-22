<!-- Source: https://create.roblox.com/docs/nl-nl/luau/operators -->

Operatoren | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Luau-referentie](/docs/nl-nl/luau)
8. /
9. Functies

# Operatoren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een operator  is een symbool voor het uitvoeren van een bewerking of voorwaardelijke evaluatie.

## [Logisch](#logisch)[](#logisch)

Logische operatoren geven waarden terug afhankelijk van de booleaanse waarden van de gegeven argumenten. Als een argument niet false  of nil  is, dan evalueert de operator het als true . In tegenstelling tot veel andere talen beschouwt Luau zowel nul als de lege string als true . De volgende tabel geeft een samenvatting van hoe logische operatoren zich gedragen in [voorwaardelijke uitspraken](/docs/nl-nl/luau/control-structures#if-uitspraken) .

| Operator | | Beschrijvingen |
| --- | --- |
| and | | Beoordeelt als true  alleen als beide voorwaarden waar zijn |
| or | | Beoordeelt als true  als een van de voorwaarden waar is |
| not | | Beoordeelt als het tegenovergestelde van de voorwaarde |

### [and](#and)[](#and)

De binaire operator and  retourneert een van de twee argumenten. Als het eerste argument evalueert naar true , dan retourneert het het tweede argument. Anders retourneert het het eerste argument.

```

print(4 and 5) -- 5

print(nil and 12) -- nil

print(false and 12) -- false

print(false and true) -- false

print(false and false) -- false

print(true and false) -- false

print(true and true) -- true

```

Je kunt and  gebruiken om meerdere voorwaarden te testen in [besturingsstructuren](/docs/nl-nl/luau/control-structures)  zoals [if -uitspraken](/docs/nl-nl/luau/control-structures#if-uitspraken)  en [while -lussen](/docs/nl-nl/luau/control-structures#while-loops) . Bijvoorbeeld, de volgende if ‑ then -uitspraken testen of twee voorwaarden beide waar zijn:

```

local pasta = true

local tomatoSauce = true

if pasta == true and tomatoSauce == true then

	print("We hebben spaghetti avondeten")

else

	print("Er ontbreekt iets...")

end

-- Output: We hebben spaghetti avondeten

```

### [or](#or)[](#or)

De binaire operator or  retourneert een van de twee argumenten. Als het eerste argument evalueert naar true , dan retourneert het het eerste argument. Anders retourneert het het tweede argument.

```

local y = x or 1

print(y) -- 1 omdat x niet bestaat en daarom nil is

local d = false

local e = d or 1

print(e) -- 1 omdat d false is

print(4 or 5) -- 4

print(nil or 12) -- 12

print(false or 12) -- 12

print(false or true) -- true

print(false or false) -- false

print(true or false) -- true

print(true or true) -- true

```

Je kunt or  gebruiken om complexe logische tests uit te voeren in [besturingsstructuren](/docs/nl-nl/luau/control-structures) . Bijvoorbeeld, de volgende if ‑ then -uitspraken testen of twee voorwaarden waar zijn of  een derde voorwaarde waar is:

```

local pasta = false

local tomatoSauce = true

local garlicBread = true

if (pasta == true and tomatoSauce == true) or garlicBread == true then

	print("We hebben of spaghetti avondeten OF knoflookbrood")

else

	print("Er ontbreekt iets...")

end

-- Output: We hebben of spaghetti avondeten OF knoflookbrood

```

### [not](#not)[](#not)

De unitaire operator not  retourneert de tegenovergestelde booleaanse waarde van het argument. Als het argument false  of nil  is, dan retourneert het true . Anders retourneert het false .

```

print(not true) -- false

print(not false) -- true

print(not nil) -- true

print(not "tekst") -- false

print(not 0) -- false

```

Je kunt de not -operator gebruiken om een voorwaarde of lus te activeren als een variabele false  of nil  is.

```

local nilVariable  -- Variabele is gedeclareerd maar heeft geen waarde, dus het is nil

local falseVariable = false  -- Variabele is gedeclareerd met de waarde false

if not nilVariable then

	print(nilVariable)  -- Geeft "nil" omdat nil niet waar is

end

if not falseVariable then

	print(falseVariable)  -- Geeft "false" omdat false niet waar is

end

```

Je kunt ook de not -operator gebruiken om te testen op het tegenovergestelde van een hele multi-voorwaarde uitspraak. In het volgende codevoorbeeld testen de if ‑ then -voorwaarden dat het noch waar is dat drie groter is dan vier, noch dat vijf groter is dan vier.

```

local three = 3

local four = 4

local five = 5

if not (three > four or five < four) then

	print("Drie is minder dan 4 en vijf is groter dan 4.")

end

-- Output: Drie is minder dan 4 en vijf is groter dan 4.

```

## [Relationeel](#relationeel)[](#relationeel)

Relationele operatoren vergelijken twee parameters en retourneren een [boolean](/docs/nl-nl/luau/booleans) : true  of false .

| Operator | | Beschrijving | | Voorbeeld | | Bijbehorende metamethode |
| == | | Gelijk aan | | 3 == 5  → false | | __eq |
| ~= | | Niet gelijk aan | | 3 ~= 5  → true | |  |
| > | | Groter dan | | 3 > 5  → false | |  |
| < | | Kleiner dan | | 3 < 5  → true | | __lt |
| >= | | Groter dan of gelijk aan | | 3 >= 5  → false | |  |
| <= | | Kleiner dan of gelijk aan | | 3 <= 5  → true | | __le |

## [Aritmetisch](#aritmetisch)[](#aritmetisch)

Luau ondersteunt de gebruikelijke binaire operatoren samen met exponentiatie, modulus en unitaire negatie.

| Operator | | Beschrijving | | Voorbeeld | | Bijbehorende metamethode |
| + | | Optelling | | 1 + 1 = 2 | | __add |
| - | | Aftrekking | | 1 - 1 = 0 | | __sub |
| * | | Vermenigvuldiging | | 5 * 5 = 25 | | __mul |
| / | | Deling | | 10 / 5 = 2 | | __div |
| // | | Vloer Deling | |

10 // 4 = 2
 -10 // 4 = -3

 | | __idiv |
| ^ | | Exponentiatie | | 2 ^ 4 = 16 | | __pow |
| % | | Modulus | | 13 % 7 = 6 | | __mod |
| - | | Unitaire negatie | | -2 = 0 - 2 | | __unm |

## [Samengestelde toewijzing](#samengestelde-toewijzing)[](#samengestelde-toewijzing)

Je kunt samengestelde toewijzingsoperatoren gebruiken om een variabele gelijk te stellen aan het resultaat van een bewerking waarbij de eerste parameter de huidige waarde van de variabele is.

De bewerking in een samengestelde toewijzing vindt één keer plaats. Bijvoorbeeld, als een expressie een willekeurige index in een tabel genereert, gebruikt Luau dezelfde index voor zowel de bewerking als de toewijzing.

In de volgende voorbeelden, stel dat local x = 3 .

| Operator | | Bewerking | | Voorbeeld | | Nieuwe waarde van x |
| += | | Optelling | | x += 2 | | 5 |
| -= | | Aftrekking | | x -= 2 | | 1 |
| *= | | Vermenigvuldiging | | x *= 2 | | 6 |
| /= | | Deling | | x /= 2 | | 1.5 |
| //= | | Vloer Deling | | x //= 2 | | 1 |
| %= | | Modulus | | x %= 2 | | 1 |
| ^= | | Exponentiatie | | x ^= 2 | | 9 |
| ..= | | Concatenatie | | x ..= " Wereld!"  | | "3 Wereld!" |

## [Diversen](#diversen)[](#diversen)

Diverse operatoren omvatten concatenatie  en lengte .

| Operator | | Beschrijving | | Voorbeeld | | Bijbehorende metamethode |
| .. | | Voegt twee strings samen | | print("Hallo " .. "Wereld!") | | __concat |
| # | | Lengte van tabel | | Als tableVar = {1, 2, 3} , dan #tableVar == 3 . | | __len |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
