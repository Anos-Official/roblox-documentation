<!-- Source: https://create.roblox.com/docs/nl-nl/luau/strings -->

Strings | Documentatie - Roblox Creator Hub

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

# Strings

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het string  gegevenstype is een reeks karakters, zoals letters, cijfers en symbolen. Het is het gegevenstype voor het opslaan van de meeste tekstgebaseerde informatie.

## [Declareer strings](#declareer-strings)[](#declareer-strings)

Om een stringvariabele te declareren, zet je aanhalingstekens om de karakters. Het is gebruikelijker om dubbele aanhalingstekens (" ), maar enkele aanhalingstekens (' ) werken ook. Als je een enkel of dubbel aanhalingsteken in je string wilt opnemen, sluit je je string in het andere type aanhalingsteken in, of gebruik je een [ontsnapte aanhaling](#escape-strings) .

```

local string1 = "Hallo wereld!"

print(string1)  --> Hallo wereld!

local string2 = 'Hallo "wereld"!'

print(string2)  --> Hallo "wereld"!

```

Om zowel enkele als dubbele aanhalingstekens in een string op te nemen, of om meerregelige strings te maken, declareer je ze met behulp van dubbele haken:

```

local string1 = [[Hallo

wereld!

Hallo "wereld"!

Hallo 'wereld'!]]

print(string1)

--> Hallo

--> wereld!

--> Hallo "wereld"!

--> Hallo 'wereld'!

```

Indien nodig kun je meerdere haken binnen een string nesten door hetzelfde aantal gelijkteken in zowel de begin- als eindhaak te gebruiken:

```

local string1 = [=[Hallo

[[wereld!]]

]=]

print(string1)

--> Hallo

--> [[wereld!]]

```

## [Combineer strings](#combineer-strings)[](#combineer-strings)

Om strings te combineren, concateneer  je ze met twee punten (.. ). Het concatenateren van strings voegt geen spatie tussen hen in, dus je moet spatie(s) aan het einde/begin van een voorafgaande/volgende string opnemen, of een spatie tussen de twee strings concatenateren.

```

local hello = "Hallo"

local helloWithSpace = "Hallo "

local world = "wereld!"

local string1 = hello .. world

local string2 = helloWithSpace .. world

local string3 = hello .. " " .. world

print(string1)  --> Hallowereld!

print(string2)  --> Hallo wereld!

print(string3)  --> Hallo wereld!

```

Merk op dat de print()  opdracht meerdere argumenten accepteert en deze met  spaties combineert, zodat je ,  in plaats van ..  kunt gebruiken om spaties in print()  uitvoer te krijgen.

```

local hello = "Hallo"

local world = "wereld"

local exclamationMark = "!"

print(hello .. world .. exclamationMark)  --> Hallowereld!

print(hello, world .. exclamationMark)  --> Hallo wereld!

print(hello, world, exclamationMark)  --> Hallo wereld !

```

## [Converteer strings](#converteer-strings)[](#converteer-strings)

Om een string naar een nummer te converteren, gebruik je de [tonumber()](/docs/nl-nl/reference/engine/globals/LuaGlobals#tonumber)  functie. Als de string geen nummerrepresentatie heeft, retourneert [tonumber()](/docs/nl-nl/reference/engine/globals/LuaGlobals#tonumber)  nil .

```

local numericString = "123"

print(tonumber(numericString))  --> 123

local alphanumericString = "Hallo123"

print(tonumber(alphanumericString))  --> nil

```

## [Escape strings](#escape-strings)[](#escape-strings)

Om een dubbele of enkele aanhalingsteken stringdeclaratie te ontsnappen en bijna elk teken in te voegen, zet je een backslash (\ ) voor het teken. Bijvoorbeeld:

-

Om een enkel aanhalingsteken in een enkele aanhalingsteken string in te voegen, gebruik \' .

-

Om een dubbel aanhalingsteken in een dubbele aanhalingsteken string in te voegen, gebruik \" .

```

local string1 = 'Hallo \'wereld\'!'

print(string1)  --> Hallo 'wereld'!

local string2 = "Hallo \"wereld\"!"

print(string2)  --> Hallo "wereld"!

```

Bepaalde karakters die volgen op backslashes produceren speciale karakters in plaats van ontsnapte karakters:

-

Om een nieuwe regel in te voegen, gebruik \n .

-

Om een horizontale tab in te voegen, gebruik \t .

```

local string1 = "Hallo\nwereld!"

print(string1)

--> Hallo

--> wereld!

local string2 = "Hallo\twereld!"

print(string2)  --> Hallo	wereld!

```

## [String interpolatie](#string-interpolatie)[](#string-interpolatie)

Luau ondersteunt string interpolatie , een functie waarmee je expressies in strings kunt invoegen. Gebruik backticks (`) om een geïnterpoleerde string te declareren, en voeg vervolgens expressies binnen accolades toe:

```

local world = "wereld"

local string1 = `Hallo {world}!`

print(string1)  --> Hallo wereld!

```

Hoewel variabelen het meest gebruikelijk zijn, kun je elke expressie gebruiken, inclusief wiskunde:

```

local world = "wereld"

local number = 1

local letters = {"w", "o", "r", "l", "d"}

local string1 = `Hallo {world}, {number} keer!`

local string2 = `Hallo {world}, {number + 1} keren!`

local string3 = `Hallo {table.concat(letters)} een derde keer!`

print(string1)  --> Hallo wereld, 1 keer!

print(string2)  --> Hallo wereld, 2 keren!

print(string3)  --> Hallo wereld een derde keer!

```

Standaard ontsnappingsregels zijn van toepassing voor backticks, accolades en backslashes:

```

local string1 = `Hallo \`\{world\}\`!`

print(string1)  --> Hallo `{world}`!

```

## [Wiskunde conversie](#wiskunde-conversie)[](#wiskunde-conversie)

Als je wiskundige bewerkingen op een string uitvoert, converteert Luau de string automatisch naar een nummer. Als de string geen nummerrepresentatie heeft, wordt er een foutmelding weergegeven.

```

print("55" + 10)  --> 65

print("55" - 10)  --> 45

print("55" * 10)  --> 550

print("55" / 10)  --> 5.5

print("55" % 10)  --> 5

print("Hallo" + 10)	 --> print("Hallo" + 10):1: poging om wiskunde (optellen) uit te voeren op string en nummer

```

## [Vergelijkingen](#vergelijkingen)[](#vergelijkingen)

Strings kunnen worden vergeleken met behulp van de < , <= , >  en >=  operatoren die vergelijken op basis van lexicografische volgorde op basis van de ASCII-codes van elk teken in een string. Dit zal resulteren in nummers in strings die niet correct worden vergeleken, bijvoorbeeld, "100"  zal minder zijn dan "20" , aangezien de bytes "0"  en "1"  lagere ASCII-codes hebben dan byte "2" .

```

print("Appel" < "appel") --> true

print("Banaan" < "appel") --> true (B komt voor a in ASCII)

print("nummer100" < "nummer20") --> true

```

## [String patroonreferentie](#string-patroonreferentie)[](#string-patroonreferentie)

Een stringpatroon  is een combinatie van karakters die je kunt gebruiken met [string.match()](/docs/nl-nl/reference/engine/libraries/string#match) , [string.gmatch()](/docs/nl-nl/reference/engine/libraries/string#gmatch) , en andere functies om een stuk, of substring, van een langere string te vinden.

### [Directe overeenkomsten](#directe-overeenkomsten)[](#directe-overeenkomsten)

Je kunt directe overeenkomsten gebruiken in een Luau-functie zoals [string.match()](/docs/nl-nl/reference/engine/libraries/string#match) , behalve voor [magische karakters](#magische-karakters) . Bijvoorbeeld, deze opdrachten zoeken naar het woord Roblox  binnen een string:

```

local match1 = string.match("Welkom bij Roblox!", "Roblox")

local match2 = string.match("Welkom bij mijn geweldige spel!", "Roblox")

print(match1)  --> Roblox

print(match2)  --> nil

```

### [Tekenklassen](#tekenklassen)[](#tekenklassen)

Tekenklassen zijn essentieel voor meer geavanceerde stringzoekopdrachten. Je kunt ze gebruiken om iets te zoeken dat niet noodzakelijkerwijs teken-specifiek is, maar binnen een bekende categorie (klasse) past, inclusief letters , cijfers , spaties , interpunctie , en meer.

De volgende tabel toont de officiële tekenklassen voor Luau stringpatronen:

| Klasse | | Vertegenwoordigt | | Voorbeeldovereenkomst |
| . | | Elk teken | | 32kasGJ1%fTlk?@94 |
| --- | --- |
| %a | | Een hoofdletter of kleine letter | | aBcDeFgHiJkLmNoPqRsTuVwXyZ |
| %l | | Een kleine letter | | abcdefghijklmnopqrstuvwxyz |
| %u | | Een hoofdletter | | ABCDEFGHIJKLMNOPQRSTUVWXYZ |
| %d | | Elk cijfer (nummer) | | 0123456789 |
| %p | | Elk interpunctieteken | | !@#;,. |
| %w | | Een alfanumeriek teken (of een letter ** of**  een nummer) | | aBcDeFgHiJkLmNoPqRsTuVwXyZ0123456789 |
| %s | | Een spatie of witruimte teken | |  , \n , en \r |
| %c | | Een speciaal [besturingskarakter](https://wikipedia.org/wiki/Control_character) | |  |
| %x | | Een hexadecimaal teken | | 0123456789ABCDEF |
| %z | | Het NULL-teken (\0 ) | |  |

Voor enkelletter tekenklassen zoals %a  en %s , vertegenwoordigt de overeenkomstige hoofdletter de "tegenovergestelde" van de klasse. Bijvoorbeeld, %p  vertegenwoordigt een interpunctieteken terwijl %P  alle tekens vertegenwoordigt, behalve interpunctie.

### [Magische karakters](#magische-karakters)[](#magische-karakters)

Er zijn 12 "magische karakters" die gereserveerd zijn voor speciale doeleinden in patronen:

| $ | | % | | ^ | | * | | ( | | ) |
| . | | [ | | ] | | + | | - | | ? |

Je kunt magische karakters ontsnappen en zoeken met behulp van het %  symbool. Bijvoorbeeld, om te zoeken naar roblox.com , ontsnap je het .  (punt) symbool door het vooraf te laten gaan door een % , zoals in %. .

```

-- "roblox.com" komt overeen met "roblox#com" omdat de punt wordt geïnterpreteerd als "elk teken"

local match1 = string.match("Wat is roblox#com?", "roblox.com")

print(match1)  --> roblox#com

-- Ontsnap de punt met % zodat deze wordt geïnterpreteerd als een letterlijke punt

local match2 = string.match("Ik hou van roblox.com!", "roblox%.com")

print(match2)  --> roblox.com

```

### [Ankers](#ankers)[](#ankers)

Je kunt zoeken naar een patroon aan het begin of het einde van een string door de ^  en $  symbolen te gebruiken.

```

local start1 = string.match("eerste tweede derde", "^eerste")  -- Komt overeen omdat "eerste" aan het begin staat

print(start1)  --> eerste

local start2 = string.match("derde tweede eerste", "^eerste")  -- Komt niet overeen omdat "eerste" niet aan het begin staat

print(start2)  --> nil

local end1 = string.match("eerste tweede derde", "derde$")  -- Komt overeen omdat "derde" aan het einde staat

print(end1)  --> derde

local end2 = string.match("derde tweede eerste", "derde$")  -- Komt niet overeen omdat "derde" niet aan het einde staat

print(end2)  --> nil

```

Je kunt ook zowel ^  als $  samen gebruiken om ervoor te zorgen dat een patroon alleen de volledige string overeenkomt en niet slechts een deel ervan.

```

-- Gebruik zowel ^ als $ om over een volledige string overeen te komen

local match1 = string.match("Roblox", "^Roblox$")  -- Komt overeen omdat "Roblox" de gehele string is (gelijkheid)

print(match1)  --> Roblox

local match2 = string.match("Ik speel Roblox", "^Roblox$")  -- Komt niet overeen omdat "Roblox" niet aan het begin EN einde staat

print(match2)  --> nil

local match3 = string.match("Ik speel Roblox", "Roblox")  -- Komt overeen omdat "Roblox" is opgenomen in "Ik speel Roblox"

print(match3)  --> Roblox

```

### [Klasse-modifiers](#klasse-modifiers)[](#klasse-modifiers)

Op zichzelf matcht een tekenklasse alleen één  teken in een string. Bijvoorbeeld, het volgende patroon ("%d" ) begint de string van links naar rechts te lezen, vindt het eerste  cijfer (2 ), en stopt.

```

local match = string.match("Het Cloud Koninkrijk heeft 25 kracht edelstenen", "%d")

print(match)  --> 2

```

Je kunt modifiers  gebruiken met elke tekenklasse om het resultaat te controleren:

| Quantifier | | Betekenis |
| + | | Match 1 of meer van de voorafgaande tekenklasse |
| - | | Match zo min mogelijk van de voorafgaande tekenklasse |
| * | | Match 0 of meer van de voorafgaande tekenklasse |
| ? | | Match 1 of minder van de voorafgaande tekenklasse |
| %n | | Voor n  tussen ** 1**  en ** 9** , matcht een substring gelijk aan de n de vastgelegde string. |
| %bxy | | De gebalanceerde vastlegging die x , y , en alles ertussen matcht (bijvoorbeeld, %b()  matcht een paar haakjes en alles ertussen) |

Door een modifier aan hetzelfde patroon toe te voegen ("%d+"  in plaats van "%d" ), geeft het 25  in plaats van 2 :

```

local match1 = string.match("Het Cloud Koninkrijk heeft 25 kracht edelstenen", "%d")

print(match1)  --> 2

local match2 = string.match("Het Cloud Koninkrijk heeft 25 kracht edelstenen", "%d+")

print(match2)  --> 25

```

### [Klasse sets](#klasse-sets)[](#klasse-sets)

Sets  moeten worden gebruikt wanneer een enkele tekenklasse de hele klus niet kan klaren. Bijvoorbeeld, je wilt misschien zowel kleine letters (%l ) als  interpunctietekens (%p ) matchen met behulp van een enkel patroon.

Sets worden gedefinieerd door haken []  eromheen. In het volgende voorbeeld, let op het verschil tussen het gebruik van een set ("[%l%p]+" ) en geen  set ("%l%p+" ).

```

local match1 = string.match("Hallo!!! Ik ben een andere string.", "[%l%p]+")  -- Set

print(match1)  --> ello!!!

local match2 = string.match("Hallo!!! Ik ben een andere string.", "%l%p+")  -- Geen set

print(match2)  --> o!!!

```

De eerste opdracht (set) vertelt Luau om zowel kleine letters als interpunctietekens te vinden. Met de +  quantifier toegevoegd na de gehele set, vindt het alle  van die karakters (ello!!! ), stopte wanneer het de spatie bereikt.

In de tweede opdracht (geen set), geldt de +  quantifier alleen voor de %p  klasse ervoor, zodat Luau alleen het eerste kleine letterteken (o ) voor de reeks interpunctietekens (!!! ) pakt.

Net als tekenklassen kunnen sets "tegenovergestelde" van zichzelf zijn. Dit wordt gedaan door een ^  teken aan het begin van de set toe te voegen, direct na de opening [. Bijvoorbeeld, "[%p%s]+"  vertegenwoordigt zowel interpunctie als spaties, terwijl "[^%p%s]+"  alle tekens vertegenwoordigt behalve  interpunctie en spaties.

Sets ondersteunen ook bereiken  waarmee je een volledig bereik van overeenkomsten tussen een start- en eindteken kunt vinden. Dit is een geavanceerde functie die in meer detail wordt beschreven in de [Lua 5.1 Handleiding](https://www.lua.org/manual/5.1/manual.html#5.4.1) .

### [String vastleggingen](#string-vastleggingen)[](#string-vastleggingen)

String vastleggingen  zijn sub-patronen binnen een patroon. Deze zijn ingesloten in haakjes ()  en worden gebruikt om overeenkomende substrings te krijgen (vast te leggen) en ze op te slaan in variabelen. Bijvoorbeeld, het volgende patroon bevat twee vastleggingen, (%a+)  en (%d+) , die twee substrings retourneren bij een succesvolle overeenkomst.

```

local pattern = "(%a+)%s?=%s?(%d+)"

local key1, val1 = string.match("TwintigEen = 21", pattern)

print(key1, val1)  --> TwintigEen 21

local key2, val2 = string.match("TweeDuizend= 2000", pattern)

print(key2, val2)  --> TweeDuizend 2000

local key3, val3 = string.match("EenMiljoen=1000000", pattern)

print(key3, val3)  --> EenMiljoen 1000000

```

De ?  quantifier die volgt op beide %s  klassen is een veilige toevoeging omdat het de spatie aan beide zijden van het =  teken optioneel maakt. Dat betekent dat de overeenkomst slaagt als een (of beide) spaties ontbreken rond het gelijkteken.

In de [string.gsub()](/docs/nl-nl/reference/engine/libraries/string#gsub)  functie kun je vastleggroepen opnemen in de vervangingsstring met behulp van %1 , %2 , %3 , enzovoort, tot %9 . Hoewel Luau tot 32 vastleggroepen ondersteunt voordat er een fout optreedt, kun je alleen de eerste negen met deze syntaxis verwijzen:

```

local str = "liefde2spelen Roblox"

local pattern = "(%w+)(%d+)(%w+)%s+(%w+)"

local replacement = "Ik %1 %2 %3 %4!"

local result = string.gsub(str, pattern, replacement)

print(result) --> Ik liefde 2 spelen Roblox!

```

Je kunt ook string vastleggingen nesten:

```

local places = "Het Cloud Koninkrijk is hemels, Het Bos Koninkrijk is vredig"

local pattern = "(Het%s(%a+%sKoninkrijk)[%w%s]+)"

for description, kingdom in string.gmatch(places, pattern) do

	print(description)

	print(kingdom)

end

--> Het Cloud Koninkrijk is hemels

--> Cloud Koninkrijk

--> Het Bos Koninkrijk is vredig

--> Bos Koninkrijk

```

Deze patroonzoekopdracht werkt als volgt:

De [string.gmatch()](/docs/nl-nl/reference/engine/libraries/string#gmatch)  iterator zoekt naar een overeenkomst op het gehele "beschrijving" patroon gedefinieerd door het buitenste paar haakjes. Dit stopt bij de eerste komma en legt het volgende vast:

| # | | Patroon | | Vastlegging |
| ** 1** | | (Het%s(%a+%sKoninkrijk)[%w%s]+) | | Het Cloud Koninkrijk is hemels |

Met zijn succesvolle eerste vastlegging zoekt de iterator vervolgens naar een overeenkomst op het "koninkrijk" patroon gedefinieerd door het binnenste paar haakjes. Dit geneste patroon legt eenvoudig het volgende vast:

| # | | Patroon | | Vastlegging |
| ** 2** | | (%a+%sKoninkrijk) | | Cloud Koninkrijk |

De iterator trekt zich dan terug en gaat verder met het zoeken in de volledige string, waarbij het volgende vastlegt:

| # | | Patroon | | Vastlegging |
| ** 3** | | (Het%s(%a+%sKoninkrijk)[%w%s]+) | | Het Bos Koninkrijk is vredig |
| ** 4** | | (%a+%sKoninkrijk) | | Bos Koninkrijk |

Naast al het bovenstaande is er een speciale situatie met een lege vastlegging  (() ). Als een vastlegging leeg is, wordt de positie in de string vastgelegd:

```

local match1 = "Waar gebeurt de vastlegging? Wie weet!"

local match2 = "Deze string is langer dan de eerste. Waar gebeurt de vastlegging? Wie weet?!"

local pattern = "()Waar gebeurt de vastlegging%? Wie weet!()"

local start1, finish1 = string.match(match1, pattern)

print(start1, finish1)  --> 1 42

local start2, finish2 = string.match(match2, pattern)

print(start2, finish2)  --> 43 84

```

Deze speciale vastleggingen kunnen genest zijn zoals normale:

```

local places = "Het Cloud Koninkrijk is hemels, Het Bos Koninkrijk is vredig."

local pattern = "Het (%a+()) Koninkrijk is %a+"

for kingdom, position in string.gmatch(places, pattern) do

	print(kingdom, position)

end

--> Cloud 10

--> Bos 42

```

De geretourneerde waarden zijn ongebruikelijk omdat ze nummers  zijn in plaats van strings:

```

local match = "Dit is een voorbeeld"

local pattern = "Dit is een ()voorbeeld"

local position = string.match(match, pattern)

print(typeof(position))  --> number

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
