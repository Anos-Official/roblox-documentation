<!-- Source: https://create.roblox.com/docs/nl-nl/luau/metatables -->

Metatabellen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Luau-referentie](/docs/nl-nl/luau)
8. /
9. Gegevensstructuren

# Metatabellen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Metatabellen stellen tabellen in staat om krachtiger te worden dan voorheen. Ze zijn gekoppeld aan gegevens en bevatten waarden die metamethoden worden genoemd. Metamethoden worden geactiveerd wanneer een bepaalde actie wordt uitgevoerd met de datum waaraan ze zijn gekoppeld.

## [Manipuleer metatabellen](#manipuleer-metatabellen)[](#manipuleer-metatabellen)

De twee primaire functies voor het toevoegen en vinden van de metatable van een tabel zijn [setmetatable()](/docs/nl-nl/reference/engine/globals/LuaGlobals#setmetatable)  en [getmetatable()](/docs/nl-nl/reference/engine/globals/LuaGlobals#getmetatable) .

```

local x = {}

local metaTable = {} -- Metatabellen zijn ook tabellen!

setmetatable(x, metaTable) -- Geef x een metatable genaamd metaTable!

print(getmetatable(x)) --> table: [hexadecimale geheugenadres]

```

De functie [setmetatable()](/docs/nl-nl/reference/engine/globals/LuaGlobals#setmetatable)  retourneert ook de tabel waarvan je de metatable instelt, dus deze twee scripts doen hetzelfde:

```

local x = {}

setmetatable(x, {})

```

```

local x = setmetatable({}, {})

```

### [Metamethoden](#metamethoden)[](#metamethoden)

Metamethoden zijn de functies die zijn opgeslagen in een metatable. Ze kunnen variëren van het aanroepen van een tabel, tot het optellen van een tabel, tot zelfs het delen van tabellen. Hier is de lijst van beschikbare metamethoden:

| Methode | | Beschrijving |
| --- | --- |
| __index(table, index) | | Wordt geactiveerd wanneer table[index]  wordt geïndexeerd, als table[index]  nil  is. Kan ook worden ingesteld op een tabel, in welk geval die tabel zal worden geïndexeerd. |
| __newindex(table, index, value) | | Wordt geactiveerd wanneer table[index]  probeert te worden ingesteld (table[index] = value) , als table[index]  nil  is. Kan ook worden ingesteld op een tabel, in welk geval die tabel zal worden geïndexeerd. |
| __call(table, ...) | | Wordt geactiveerd wanneer de tabel wordt aangeroepen als een functie, ...  zijn de argumenten die zijn doorgegeven. |
| __concat(table, value) | | Wordt geactiveerd wanneer de ..  concatenatieoperator op de tabel wordt gebruikt. |
| __unm(table) | | Wordt geactiveerd wanneer de unitaire –  operator op de tabel wordt gebruikt. |
| __add(table, value) | | De +  optelling operator. |
| __sub(table, value) | | De –  aftrekking operator. |
| __mul(table, value) | | De *  vermenigvuldiging operator. |
| __div(table, value) | | De /  deling operator. |
| __idiv(table, value) | | De //  vloer deling operator. |
| __mod(table, value) | | De %  modulus operator. |
| __pow(table, value) | | De ^  exponentiatie operator. |
| __tostring(table) | | Wordt geactiveerd wanneer tostring wordt aangeroepen op de tabel. |
| __metatable | | Als aanwezig, vergrendelt de metatable zodat [getmetatable()](/docs/nl-nl/reference/engine/globals/LuaGlobals#getmetatable)  deze retourneert in plaats van de metatable en [setmetatable()](/docs/nl-nl/reference/engine/globals/LuaGlobals#setmetatable)  een fout geeft. Niet-functiewaarde. |
| __eq(table, value) | | De ==  gelijk aan operator¹ |
| __lt(table, value) | | De <  kleiner dan operator¹ |
| __le(table, value) | | De <=  operator¹ |
| __mode | | Gebruikt in zwakke tabellen, verklaart of de sleutels en/of waarden van een tabel zwak zijn. Zie [Gebruik zwakke tabellen](#gebruik-zwakke-tabellen) . |
| __len(table) | | Wordt geactiveerd wanneer de #  lengte operator op het object wordt gebruikt. |
| __iter(table) | | Gebruikt om een aangepaste iterator aan te duiden bij het gebruik van gegeneraliseerde iteratie. |

¹ Vereist twee waarden met dezelfde metamethode functie en basis type (tabel/userdata/etc.); werkt niet met een tabel en een andere willekeurige tabel, of met een userdata en een tabel.

Als je de relationele vergelijking voor jouw type wilt overschrijven, moet je __lt  implementeren. Standaard zullen alle vier de operatoren (< , <= , > , >= ) het aanroepen en het resultaat interpreteren volgens relationele identiteiten (a<b  == b>a , a<=b  == not(b<a) )

In sommige gevallen, zoals wanneer je ongesorteerde semantiek exact wilt behouden, kun je verschillende gedragingen hebben voor <= .. Bijvoorbeeld, voor drijvende getallen is NaN < NaN  onwaar, en NaN <= NaN  is ook onwaar. Voor dit geval kun je ook __le  overschrijven, in welk geval <=  en >=  het zullen gebruiken in plaats van het resultaat van __lt  om te keren.

Het moet worden opgemerkt dat wanneer je functies schrijft voor ofwel rekenkundige of relationele metamethoden de twee functieparameters verwisselbaar zijn tussen de tabel die de metamethode heeft geactiveerd en de andere waarde. Bijvoorbeeld, bij het uitvoeren van vectorbewerkingen met scalars is deling niet commutatief. Daarom, als je metamethoden voor jouw eigen vector2  klasse schrijft, moet je voorzichtig zijn om rekening te houden met beide scenario's.

```

local vector2 = {__type = "vector2"}

local mt = {__index = vector2}

function mt.__div(a, b)

	if type(a) == "number" then

		-- a is een scalar, b is een vector

		local scalar, vector = a, b

		return vector2.new(scalar / vector.x, scalar / vector.y)

	elseif type(b) == "number" then

		-- a is een vector, b is een scalar

		local vector, scalar = a, b

		return vector2.new(vector.x / scalar, vector.y / scalar)

	elseif (a.__type and a.__type == "vector2" and b.__type and b.__type == "vector2") then

		-- zowel a als b zijn vectoren

		return vector2.new(a.x / b.x, a.y / b.y)

	end

end

function mt.__tostring(t)

	return t.x .. ", " .. t.y

end

function vector2.new(x, y)

	local self = setmetatable({}, mt)

	self.x = x or 0

	self.y = y or 0

	return self

end

local a = vector2.new(10, 5)

local b = vector2.new(-3, 4)

print(a / b) -- -3.3333333333333, 1.25

print(b / a) -- -0.3, 0.8

print(2 / a) -- 0.2, 0.4

print(a / 2) -- 5, 2.5

```

### [Gebruik](#gebruik)[](#gebruik)

Er zijn veel manieren om metatabellen te gebruiken.

#### [Pas de unitaire min operator toe op tabellen](#pas-de-unitaire-min-operator-toe-op-tabellen)[](#pas-de-unitaire-min-operator-toe-op-tabellen)

De __unm  metamethode behandelt de unitaire min operator. Gebruik het om elke waarde in een tabel te negateren:

```

local metatable = {

	__unm = function(t) -- __unm is voor de unitaire - operator

    local negated = {}

  	for key, value in t do

  		negated[key] = -value -- negatie van alle waarden in deze tabel

  	end

  	return negated -- retourneer de tabel

	end

}

local table1 = setmetatable({10, 11, 12}, metatable)

print(table.concat(-table1, "; ")) --> -10; -11; -12

```

#### [Indexeer ontbrekende waarden vanuit een andere tabel](#indexeer-ontbrekende-waarden-vanuit-een-andere-tabel)[](#indexeer-ontbrekende-waarden-vanuit-een-andere-tabel)

Hier is een interessante manier om dingen te verklaren met __index :

```

local metatable = {

	__index = {x = 1}

}

local t = setmetatable({}, metatable)

print(t.x) --> 1

```

__index  werd geactiveerd toen x  werd geïndexeerd in de tabel en niet werd gevonden. Luau zocht vervolgens door de __index  tabel naar een index genaamd x , en, bij het vinden van een, retourneerde dat.

#### [Roep een tabel aan als een functie](#roep-een-tabel-aan-als-een-functie)[](#roep-een-tabel-aan-als-een-functie)

Metatabellen kunnen veel meer doen dan een ontbrekende waarde leveren. Neem dit voorbeeld:

```

local t = {10, 20, 30}

print(t(5))

```

Typisch kun je een tabel niet aanroepen, maar met metatabellen kun je dat:

```

local metatable = {

	__call = function(t, param)

	local sum = {}

		for i, value in ipairs(t) do

			sum[i] = value + param -- Voeg het argument (5) toe aan de waarde, en plaats het dan in de nieuwe tabel (t).

		end

		return unpack(sum) -- Retourneer de individuele tabelwaarden

	end

}

local t = setmetatable({10, 20, 30}, metatable)

print(t(5)) --> 15 25 35

```

#### [Pas de optelling operator toe op tabellen](#pas-de-optelling-operator-toe-op-tabellen)[](#pas-de-optelling-operator-toe-op-tabellen)

Je kunt ook veel meer doen, zoals tabellen optellen:

```

local table1 = {10, 11, 12}

local table2 = {13, 14, 15}

for k, v in table1 + table2 do

	print(k, v)

end

```

Dit zal een fout geven die zegt dat je probeert rekenkunde op een tabel uit te voeren, maar het werkt wanneer je het met een metatable probeert:

```

local metatable = {

	__add = function(t1, t2)

		local sum = {}

		for key, value in t1 do

			sum[key] = value

		end

		for key, value in t2 do

			if sum[key] then

				sum[key] += value

			else

				sum[key] = value

			end

		end

		return sum

	end

}

local table1 = setmetatable({10, 11, 12}, metatable)

local table2 = setmetatable({13, 14, 15}, metatable)

for k, v in table1 + table2 do

	print(k, v)

end

```

#### [Stel waarden in zonder metamethoden aan te roepen](#stel-waarden-in-zonder-metamethoden-aan-te-roepen)[](#stel-waarden-in-zonder-metamethoden-aan-te-roepen)

Wanneer je met metatabellen speelt, kun je tegen enkele problemen aanlopen. Als je de __index  metamethode moet gebruiken om nieuwe waarden in een tabel te creëren, maar de metatable van die tabel ook een __newindex  metamethode heeft, wil je de ingebouwde functie [rawset()](/docs/nl-nl/reference/engine/globals/LuaGlobals#rawset)  gebruiken om de waarde in te stellen zonder metamethoden aan te roepen. Neem de volgende code als voorbeeld van wat er gebeurt als je deze functies niet gebruikt.

```

local t = setmetatable({}, {

    __index = function(self, i)

    	self[i] = i * 10

    	return self[i]

    end,

    __newindex = function(self, i, v)

    	-- Stel geen waarden in de tabel op de normale manier in

    end

})

print(t[1]) -- Veroorzaakt een stack overflow

```

Stack overflows gebeuren wanneer je probeert een functie te veel keren vanuit zichzelf aan te roepen. In de __index  functie hierboven, wordt self[i]  ingesteld op een waarde, dus wanneer het de volgende regel bereikt, zou self[i]  moeten bestaan en vermoedelijk de __index  metamethode niet aanroepen. Het probleem is dat __newindex  je niet toestaat om de waarde in te stellen. De aanwezigheid ervan voorkomt dat waarden op de standaard manier aan de tabel worden toegevoegd met de methode t[i] = v . Om hier voorbij te komen, gebruik je de functie [rawset()](/docs/nl-nl/reference/engine/globals/LuaGlobals#rawset) :

```

local t = setmetatable({}, {

	__index = function(self, i)

		rawset(self, i, i * 10)

		return self[i]

	end,

	__newindex = function(self, i, v)

		-- Stel geen waarden in de tabel op de normale manier in

	end

})

print(t[1]) --> 10

```

## [Gebruik zwakke tabellen](#gebruik-zwakke-tabellen)[](#gebruik-zwakke-tabellen)

Variabelen die tabellen, functies, threads en [userdata](/docs/nl-nl/luau/userdata)  bevatten, inclusief [Instances](/docs/nl-nl/reference/engine/classes/Instance) , slaan verwijzingen naar die objecten op in plaats van kopieën ervan. Het toewijzen van een object aan een andere variabele creëert een andere verwijzing naar hetzelfde object:

```

local map = {key = 1}

local mapReference = map

print(map == mapReference) --> true

print(map == {key = 1}) --> false

local function func() end

local funcReference = func

print(func == funcReference) --> true

local part = Instance.new("Part")

local partReference = part

print(part == partReference) --> true

```

Objecten die niet langer bereikbaar zijn via sterke verwijzingen worden in aanmerking gebracht voor garbage collection. Het instellen van een variabele op nil  maakt een object niet in aanmerking voor garbage collection als een andere sterke verwijzing nog steeds naar dat object wijst:

```

local child = {}

local parent = {Child = child}

child = nil

print(parent.Child) --> table: [hexadecimale geheugenadres]

```

Hoewel child  niet langer naar de child tabel verwijst, doet parent.Child  dat nog steeds. Zolang de parent tabel bereikbaar blijft, houdt zijn verwijzing de child tabel ook bereikbaar.

Een zwakke tabel  houdt sleutels, waarden of beide zonder te voorkomen dat de garbage collector anders onbereikbare objecten terugwint. Stel het __mode  veld van de metatable van de tabel in om te bepalen welke verwijzingen zwak zijn:

-

"k"  maakt de sleutels zwak.

-

"v"  maakt de waarden zwak.

-

"kv"  of "vk"  maakt zowel de sleutels als de waarden zwak.

De volgende codevoorbeeld creëert een tabel met zwakke waarden:

```

local children = setmetatable({}, {

	__mode = "v",

})

do

	local child = {}

	children.example = child

end

```

Nadat het do  blok eindigt, heeft de waarde die is opgeslagen in children.example  geen sterke verwijzingen meer en wordt deze in aanmerking gebracht voor garbage collection. Wanneer de garbage collector de child tabel terugwint, verwijdert Luau de invoer uit children . Garbage collection is niet-deterministisch, dus reken niet op wanneer de invoer verdwijnt.

Elke modus die je weglaat blijft sterk. Sleutels in een __mode = "v"  tabel blijven sterke verwijzingen, dus een object dat als sleutel is opgeslagen blijft bereikbaar en zijn invoer blijft in de tabel.

Voor [Instances](/docs/nl-nl/reference/engine/classes/Instance)  geldt dat garbage collection van toepassing is op de Luau verwijzing in plaats van op het object zelf. De engine slaat instantiegegevens buiten de Luau VM op, dus het verzamelen van een Luau verwijzing verwijdert de instantie niet, en een instantie die in het gegevensmodel blijft, houdt zijn Luau verwijzing niet levend. Om een instantie vrij te geven, roep je [Instance:Destroy()](/docs/nl-nl/reference/engine/classes/Instance#Destroy)  aan en wis je elke resterende verwijzing ernaar.

Gebruik geen zwakke tabel om bij te houden of een [Instance](/docs/nl-nl/reference/engine/classes/Instance)  nog bestaat in het gegevensmodel, omdat Luau de verwijzing kan verzamelen terwijl de instantie nog leeft. Om hiërarchiewijzigingen te observeren, verbind je met [Instance.AncestryChanged](/docs/nl-nl/reference/engine/classes/Instance#AncestryChanged) . Om te observeren wanneer een getagde instantie zijn tag verliest of het gegevensmodel verlaat, gebruik je [CollectionService:GetInstanceRemovedSignal()](/docs/nl-nl/reference/engine/classes/CollectionService#GetInstanceRemovedSignal) .

## [Gebruik het set datatype](#gebruik-het-set-datatype)[](#gebruik-het-set-datatype)

Een set  is een verzameling items zonder volgorde en zonder dubbele elementen. Een item is  of is niet  opgenomen in een set. Met behulp van metatabellen kun je sets construeren en manipuleren binnen Luau-scripts.

### [Basis methoden](#basis-methoden)[](#basis-methoden)

De volgende code bevat basisfunctionaliteit voor sets, waarmee je nieuwe sets kunt construeren, een item kunt toevoegen en verwijderen, kunt controleren of een set een item bevat, en de inhoud van een set kunt weergeven.

```

local Set = {}

Set.__index = Set

-- Functie om een set te construeren vanuit een optionele lijst van items

function Set.new(items)

	local newSet = {}

	for key, value in items or {} do

		newSet[value] = true

	end

	return setmetatable(newSet, Set)

end

-- Functie om een item aan een set toe te voegen

function Set:add(item)

	self[item] = true

end

-- Functie om een item uit een set te verwijderen

function Set:remove(item)

	self[item] = nil

end

-- Functie om te controleren of een set een item bevat

function Set:contains(item)

	return self[item] == true

end

-- Functie om set weer te geven als een door komma's gescheiden lijst voor debugging

function Set:output()

	local elems = {}

	for key, value in self do

		table.insert(elems, tostring(key))

	end

	print(table.concat(elems, ", "))

end

```

#### [Maak set](#maak-set)[](#maak-set)

Een nieuwe set kan worden geconstrueerd door Set.new()  aan te roepen met een optionele array van items om toe te voegen.

```

local fruits = Set.new({"Apple", "Lemon", "Orange", "Cherry", "Lime", "Peach"})

```

Merk op dat een set per definitie geen concept van ordening heeft.

#### [Voeg item toe](#voeg-item-toe)[](#voeg-item-toe)

Een item aan een bestaande set toevoegen kan via de Set:add()  methode.

```

local fruits = Set.new({"Apple", "Lemon", "Orange", "Cherry", "Lime", "Peach"})

fruits:add("Mango")

```

#### [Verwijder item](#verwijder-item)[](#verwijder-item)

Om een item uit een set te verwijderen, roep je Set:remove()  aan met de naam van het item.

```

local fruits = Set.new({"Apple", "Lemon", "Orange", "Cherry", "Lime", "Peach"})

fruits:remove("Orange")

```

#### [Controleer op item](#controleer-op-item)[](#controleer-op-item)

Om te controleren of een set een specifiek item bevat, gebruik je Set:contains() .

```

local fruits = Set.new({"Apple", "Lemon", "Orange", "Cherry", "Lime", "Peach"})

local result1 = fruits:contains("Cherry")

print(result1) -- true

local result2 = fruits:contains("Watermelon")

print(result2) -- false

```

### [Aanvullende methoden](#aanvullende-methoden)[](#aanvullende-methoden)

Andere nuttige bewerkingen kunnen worden geïmplementeerd voor sets, waarmee je items tussen sets kunt vergelijken, sets kunt combineren of een set van een andere set kunt aftrekken.

#### [Doorsnede](#doorsnede)[](#doorsnede)

Wanneer je sets als Venn-diagrammen beschouwt, kun je de doorsnede  van twee sets als volgt krijgen, wat betekent de items die in beide  sets voorkomen.

```

local function getIntersection(set1, set2)

	local result = Set.new()

	for key, value in set1 do

		if set2:contains(key) then

			result:add(key)

		end

	end

	return result

end

local freshFruits = Set.new({"Mango", "Lemon", "Orange", "Cherry", "Lime", "Peach"})

local frozenFruits = Set.new({"Mango", "Peach", "Pineapple"})

local commonFruits = getIntersection(freshFruits, frozenFruits)

commonFruits:output() -- Mango, Peach

```

#### [Unie](#unie)[](#unie)

Je kunt de unie  van twee sets krijgen met de volgende functie, wat betekent een verzameling van de items in beide sets zonder duplicaten. Merk op dat deze functie de metatable __add  methode gebruikt om een optelling snelkoppeling van set1 + set2  te bieden.

```

function Set:__add(otherSet)

	local result = Set.new()

	for entry in self do

		result[entry] = true

	end

	for entry in otherSet do

		result[entry] = true

	end

	return result

end

local sweetFruits = Set.new({"Apple", "Mango", "Cherry", "Peach"})

local sourFruits = Set.new({"Lemon", "Lime"})

local allFruits = sweetFruits + sourFruits

allFruits:output() -- Peach, Lime, Apple, Cherry, Lemon, Mango

```

#### [Aftrekking](#aftrekking)[](#aftrekking)

Je kunt alle items in de ene set verwijderen van de items in een andere set via de volgende functie. Vergelijkbaar met de functie hierboven, gebruikt deze de metatable __sub  methode om een aftrekking snelkoppeling van set1 - set2  te bieden.

```

function Set:__sub(otherSet)

	local result = Set.new()

	for entry in self do

		result[entry] = true

	end

	for entry in otherSet do

		result[entry] = nil

	end

	return result

end

local allFruits = Set.new({"Apple", "Lemon", "Mango", "Cherry", "Lime", "Peach"})

local sourFruits = Set.new({"Lemon", "Lime"})

local sweetFruits = allFruits - sourFruits

sweetFruits:output() -- Mango, Apple, Cherry, Peach

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
