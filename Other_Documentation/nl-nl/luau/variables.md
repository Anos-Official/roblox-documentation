<!-- Source: https://create.roblox.com/docs/nl-nl/luau/variables -->

Variabelen | Documentatie - Roblox Creator Hub

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

# Variabelen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een variabele  is een naam die een waarde vasthoudt. Variabelewaarden kunnen [getallen](/docs/nl-nl/luau/numbers) , [strings](/docs/nl-nl/luau/strings) , [booleans](/docs/nl-nl/luau/booleans) , [datatypes](/docs/nl-nl/reference/engine/datatypes)  en meer zijn.

## [Naam variabelen](#naam-variabelen)[](#naam-variabelen)

Variabelenamen kunnen elke niet-gereserveerde reeks letters, cijfers en onderstrepingen zijn die niet met een cijfer beginnen.

```

LETTERS   -- geldig

a1        -- geldig

var_name  -- geldig

_test     -- geldig

if        -- NIET geldig

25th      -- NIET geldig

```

Variabelenamen zijn hoofdlettergevoelig , dus TestVar  en TESTVAR  zijn verschillende namen. Vermijd het benoemen van variabelen met een onderstreping en alleen hoofdletters, zoals _VERSION , omdat Luau ze mogelijk reserveert voor interne globale variabelen.

### [Beste praktijken](#beste-praktijken)[](#beste-praktijken)

Het is een beste praktijk om woorden volledig te spellen. Afkortingen maken de code over het algemeen gemakkelijker te schrijven, maar moeilijker te lezen. Het volgen van gangbare naamgevingspraktijken bij het benoemen van je variabelen kan jou en anderen helpen hun betekenis of doel te begrijpen:

-

Gebruik PascalCase  namen voor klasse- en enum-achtige objecten.

-

Gebruik PascalCase  namen voor alle Roblox API's. camelCase  API's zijn grotendeels verouderd.

-

Gebruik camelCase  namen voor lokale variabelen, lidwaarden en [functies](/docs/nl-nl/luau/functions) .

-

Gebruik LOUD_SNAKE_CASE  namen voor constanten, zoals [const](#const-variabelen)  waarden of andere waarden waarvan je niet verwacht dat ze [veranderen](#waarden-veranderen) .

-

Hoofdletters niet volledig acroniemen binnen namen. Schrijf bijvoorbeeld aJsonVariable  of MakeHttpCall .

### [Gereserveerde namen](#gereserveerde-namen)[](#gereserveerde-namen)

Luau reserveert de volgende trefwoorden, dus je kunt ze niet gebruiken om variabelen of [functies](/docs/nl-nl/luau/functions)  te benoemen:

-

and

-

for

-

or

-

break

-

function

-

repeat

-

do

-

if

-

return

-

else

-

in

-

then

-

elseif

-

local

-

true

-

end

-

nil

-

until

-

false

-

not

-

while

## [Waarden toewijzen](#waarden-toewijzen)[](#waarden-toewijzen)

Om een variabele te maken en er een waarde aan toe te wijzen, gebruik je de =  operator. Zet de variabele aan de linkerkant van de =  en de waarde aan de rechterkant. Als je geen waarde opgeeft, is de waarde nil .

Variabelen kunnen globale  of lokale  [scopes](/docs/nl-nl/luau/scope)  hebben. Ze hebben standaard een globale scope, maar het is bijna altijd beter om ze met een lokale scope te maken omdat Luau lokale variabelen sneller benadert dan globale. Om een variabele een lokale scope te geven, zet je het trefwoord local  voor de naam van de variabele wanneer je er een waarde aan toewijst. Om het een lokale scope te geven en ook te voorkomen dat het opnieuw wordt toegewezen, gebruik je [const](#const-variabelen)  in plaats van local . Voor meer informatie, zie [Scope](/docs/nl-nl/luau/scope) .

```

local nilVar

local x = 10

local word = "Hallo"

local boolean = true

print(nilVar) -- nil

print(x) -- 10

print(word) -- Hallo

print(boolean) -- true

```

### [Waarden toewijzen aan meerdere variabelen](#waarden-toewijzen-aan-meerdere-variabelen)[](#waarden-toewijzen-aan-meerdere-variabelen)

Je kunt waarden aan meerdere variabelen in één regel toewijzen door elk variabele-waarde paar met een komma te scheiden. Als je meer variabelen hebt dan waarden, wijst Luau nil  toe aan de extra variabelen. Als je meer waarden dan variabelen hebt, wijst Luau de extra waarden aan geen enkele variabele toe.

```

local a, b, c = 1, 2, 3

local d, e, f = 4, 5 -- extra variabele

local g, h = 7, 8, 9 -- extra waarde

print(a, b, c) -- 1, 2, 3

print(d, e, f) -- 4, 5, nil

print(g, h) -- 7, 8

```

## [Waarden veranderen](#waarden-veranderen)[](#waarden-veranderen)

Om een waarde van een variabele te veranderen, wijs je er een andere waarde aan toe.

```

local x, y = 10, 20

print(x) -- 10

print(y) -- 20

x = 1000

y = 2000

print(x) -- 1000

print(y) -- 2000

```

## [Const variabelen](#const-variabelen)[](#const-variabelen)

Om een variabele te maken die je niet opnieuw kunt toewijzen, gebruik je const  in plaats van local . Proberen een const  variabele opnieuw toe te wijzen veroorzaakt een fout, ook via een [compound assignment operator](/docs/nl-nl/luau/operators#samengestelde-toewijzing)  zoals += .

```

const MAX_HEALTH = 100

MAX_HEALTH = 50 -- fout: kan een const variabele niet opnieuw toewijzen

MAX_HEALTH += 1 -- fout: kan een const variabele niet opnieuw toewijzen

```

Net als local  accepteert const  een [type annotatie](/docs/nl-nl/luau/type-checking) , zoals const MAX_HEALTH: number = 100 .

Je kunt ook een functie declareren met const , wat voorkomt dat de naam van de functie opnieuw wordt toegewezen.

```

const function addOneAndTwo()

	local result = 1 + 2

	print(result)

end

addOneAndTwo = nil -- fout: kan een const variabele niet opnieuw toewijzen

```

const  maakt de variabele zelf onveranderlijk, niet de waarde die het vasthoudt. Als een const  variabele een [tabel](/docs/nl-nl/luau/tables)  vasthoudt, kun je nog steeds de inhoud van de tabel wijzigen. Om de inhoud ook onveranderlijk te maken, gebruik je [table.freeze()](/docs/nl-nl/reference/engine/libraries/table#freeze) .

```

const SETTINGS = { volume = 0 }

SETTINGS.volume = 1 -- ok, verandert een waarde binnen de tabel

SETTINGS = {} -- fout: kan een const variabele niet opnieuw toewijzen

```

In tegenstelling tot de trefwoorden in [Gereserveerde namen](#gereserveerde-namen) , is const  contextueel. Luau beschouwt het alleen als een trefwoord waar local  geldig is, dus bestaande code die const  als variabelenaam gebruikt, werkt nog steeds.

```

local const = 1

print(const) -- 1

const = 2 -- ok, `const` is hier een variabelenaam

```

Voor meer informatie en randgevallen, zie de [Luau documentatie](https://luau.org/syntax/#const-bindings) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
