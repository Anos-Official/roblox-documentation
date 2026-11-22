<!-- Source: https://create.roblox.com/docs/nl-nl/luau/type-checking -->

Typechecking | Documentatie - Roblox Creator Hub

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

# Typechecking

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor de nieuwste en meest complete documentatie over typechecking, zie [hier](https://luau.org/typecheck) .

Luau ondersteunt een geleidelijk typesysteem door middel van typeannotaties en type-inferentie. Deze types worden gebruikt om betere waarschuwingen, fouten en suggesties te geven in de [Script Editor](/docs/nl-nl/studio/script-editor) .

## [Definieer een type](#definieer-een-type)[](#definieer-een-type)

Gebruik het type  sleutelwoord om je eigen types te definiëren:

```

type Vector2 = {x: number, y: number}

```

## [Inferentiemodi](#inferentiemodi)[](#inferentiemodi)

Er zijn drie Luau type-inferentiemodi die kunnen worden ingesteld op de eerste regel van een [Script](/docs/nl-nl/reference/engine/classes/Script) :

-

--!nocheck  — Controleer geen types.

-

--!nonstrict  — Bevestigt alleen variabele types als ze expliciet zijn geannoteerd.

-

--!strict  — Bevestigt alle types op basis van het inferentie- of expliciet geannoteerde type.

De --!nonstrict  en --!strict  modi bepalen hoe strikt de typechecker is met het afleiden en controleren van types voor variabelen en functies. Eventuele type-inconsistenties in scripts worden gemarkeerd in de [Script Editor](/docs/nl-nl/studio/script-editor)  en weergegeven als waarschuwingen in het [Script Analysis](/docs/nl-nl/studio/script-editor#scriptanalyse)  venster.

Om een standaardmodus voor alle scripts in te stellen die je indien nodig kunt overschrijven, zie [Workspace.LuauTypeCheckMode](/docs/nl-nl/reference/engine/classes/Workspace#LuauTypeCheckMode) .

## [Types](#types)[](#types)

Een typeannotatie kan worden gedefinieerd met behulp van de :  operator na een lokale variabele, gevolgd door een type-definitie. Standaard, in nonstrict  modus, krijgen alle variabelen het type any .

```

local foo: string = "bar"

local x: number = 5

```

Er zijn vier primitieve types die kunnen worden gebruikt in een annotatie:

-

nil  - geen waarde

-

boolean  - true  of false

-

number  - een numerieke waarde

-

string  - tekst

Binnen Roblox hebben alle klassen, datatypes en enums hun eigen types die je kunt controleren:

```

local somePart: Part = Instance.new("Part")

local brickColor: BrickColor = somePart.BrickColor

local material: Enum.Material = somePart.Material

```

Om een type optioneel te maken, gebruik een ?  aan het einde van de annotatie:

```

local foo: string? = nil

```

Dit staat de variabele toe om ofwel het gespecificeerde type (in dit geval string ) of nil  te zijn.

### [Letterlijke types](#letterlijke-types)[](#letterlijke-types)

Je kunt ook strings en booleans naar letterlijke waarden casten in plaats van string  en boolean  te gebruiken:

```

local alwaysHelloWorld: "Hello world!" = "Hello world!"

alwaysHelloWorld = "Just hello!"  -- Typefout: Type '"Just hello!"' kon niet worden omgezet naar '"Hello world!"'

local alwaysTrue: true = false  -- Typefout: Type 'false' kon niet worden omgezet naar 'true'

```

### [Typecasts](#typecasts)[](#typecasts)

Soms moet je de typechecker helpen door een waarde expliciet naar een ander type te casten met de ::  operator:

```

local myNumber = 1

local myString: string

myString = myNumber  -- Niet OK; typeconversiefout

myString = myNumber :: any  -- OK; alle expressies kunnen naar 'any' worden gecast

local myFlag = myNumber :: boolean  -- Niet OK; types zijn niet gerelateerd

```

## [Functietyping](#functietyping)[](#functietyping)

Overweeg de volgende functie:

```

local function add(x, y)

	return x + y

end

```

Deze functie voegt x  toe aan y , maar geeft een fout als een of beide een string zijn. Luau weet niet dat deze functie alleen nummers kan gebruiken. Om deze categorie van problemen te voorkomen, voeg types toe aan de parameters:

```

local function add(x: number, y: number)

	return x + y

end

```

Luau weet nu dat de functie twee nummers neemt en geeft een waarschuwing als je probeert iets door te geven dat geen nummer is:

```

add(5, 10)

add(5, "foo")  -- Typefout: string kon niet worden omgezet naar number

```

Om een retourtype te definiëren, plaats je een :  operator aan het einde van de functiedefinitie:

```

local function add(x: number, y: number): number

```

Om meerdere types te retourneren, plaats je de types tussen haakjes:

```

local function FindSource(script: BaseScript, pattern: string): (string, number)

	return 42, true  -- Typefouten

end

```

### [Definieer een functioneel type](#definieer-een-functioneel-type)[](#definieer-een-functioneel-type)

Een functioneel type kan worden gedefinieerd met de syntaxis (in) -> out . Met de functies uit de vorige voorbeelden zijn de types van de functies:

```

type add = (x: number, y: number) -> number

type FindSource = (script: BaseScript, pattern: string) -> (string, number)

```

## [Tabeltypes](#tabeltypes)[](#tabeltypes)

Luau heeft geen table  type; in plaats daarvan worden tabeltypes gedefinieerd met behulp van de {}  syntaxis. Een manier om tabellen te definiëren is met de {type}  syntaxis, die een lijsttype definieert.

```

local numbers: {number} = {1, 2, 3, 4, 5}

local characterParts: {Instance} = LocalPlayer.Character:GetChildren()

```

Definieer indextypes met {[indexType]: valueType} :

```

local numberList: {[string]: number} = {

	Foo = 1,

	Baz = 10

}

numberList["bar"] = true  -- Typefout: boolean kan niet worden omgezet naar number

```

Tabellen kunnen ook expliciete stringindices hebben die in een type zijn gedefinieerd.

```

type Car = {

	Speed: number,

	Drive: (Car) -> ()

}

local function drive(car)

	-- Altijd de snelheidslimiet respecteren

end

local taxi: Car = {Speed = 30, Drive = drive}

```

## [Variadics](#variadics)[](#variadics)

Hier is een functie die de som van een willekeurig aantal nummers berekent:

```

local function addLotsOfNumbers(...)

	local sum = 0

	for _, v in {...} do

		sum += v

	end

	return sum

end

```

Zoals verwacht kan deze functie elke waarde aannemen, en de typechecker zal geen waarschuwing geven als je een ongeldig type opgeeft, zoals een string .

```

print(addLotsOfNumbers(1, 2, 3, 4, 5))  -- 15

print(addLotsOfNumbers(1, 2, "car", 4, 5))  -- Poging om string aan number toe te voegen

```

Wijs in plaats daarvan een type toe aan de ... , net zoals je elk ander type zou toewijzen:

```

local function addLotsOfNumbers(...: number)

```

En nu geeft de tweede regel een typefout.

```

print(addLotsOfNumbers(1, 2, 3, 4, 5))

print(addLotsOfNumbers(1, 2, "car", 4, 5))  -- Typefout: string kon niet worden omgezet naar number

```

Echter, dit werkt niet bij het schrijven van een functionele type-definitie:

```

type addLotsOfNumbers = (...: number) -> number  -- Verwacht type, kreeg ':'

```

Gebruik in plaats daarvan de syntaxis ...type  om een variadisch type te definiëren.

```

type addLotsOfNumbers = (...number) -> number

```

## [Unies en intersecties](#unies-en-intersecties)[](#unies-en-intersecties)

Je kunt zelfs een type definiëren als twee of meer types met behulp van een unie of intersectie:

```

type numberOrString = number | string

type type1 = {foo: string}

type type2 = {bar: number}

type type1and2 = type1 & type2  -- {foo: string} & {bar: number}

local numString1: numberOrString = true  -- Typefout

local numString2: type1and2 = {foo = "hello", bar = 1}

```

## [Definieer een inferent type](#definieer-een-inferent-type)[](#definieer-een-inferent-type)

Je kunt de typeof  functie gebruiken in een type-definitie voor inferent types:

```

type Car = typeof({

	Speed = 0,

	Wheels = 4

})  --> Car: {Speed: number, Wheels: number}

```

Een manier om typeof  te gebruiken is om een metatabeltype te definiëren met behulp van setmetatable  binnen de typeof  functie:

```

type Vector = typeof(setmetatable({}::{

	x: number,

	y: number

}, {}::{

	__add: (Vector, Vector|number) -> Vector

}))

-- Vector + Vector zou een Vector type retourneren

```

## [Generics](#generics)[](#generics)

Generics zijn op een basisniveau parameters voor types. Overweeg het volgende State  object:

```

local State = {

	Key = "TimesClicked",

	Value = 0

}

```

Zonder generics zou het type voor dit object als volgt zijn:

```

type State = {

	Key: string,

	Value: number

}

```

Echter, je wilt misschien dat het type voor Value  gebaseerd is op de binnenkomende waarde, wat is waar generics in het spel komen:

```

type GenericType<T> = T

```

De <T>  geeft een type aan dat op alles kan worden ingesteld. De beste manier om dit te visualiseren is als een substitutietype.

```

type List<T> = {T}

local Names: List<string> = {"Bob", "Dan", "Mary"}  -- Type wordt {string}

local Fibonacci: List<number> = {1, 1, 2, 3, 5, 8, 13}  -- Type wordt {number}

```

Generics kunnen ook meerdere substituties binnen de haakjes hebben.

```

type Map<K, V> = {[K]: V}

```

Om het State  object van eerder opnieuw te werken om een generiek type te gebruiken:

```

type State<T> = {

	Key: string,

	Value: T

}

```

### [Functie generics](#functie-generics)[](#functie-generics)

Functies kunnen ook generics gebruiken. Het State  voorbeeld inferreert de waarde van T  uit de binnenkomende argumenten van de functie.

Om een generieke functie te definiëren, voeg een <>  toe aan de functienaam:

```

local function State<T>(key: string, value: T): State<T>

	return {

		Key = key,

		Value = value

	}

end

local Activated = State("Activated", false)  -- State<boolean>

local TimesClicked = State("TimesClicked", 0)  -- State<number>

```

## [Type-exporten](#type-exporten)[](#type-exporten)

Om ervoor te zorgen dat een type buiten een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  kan worden gebruikt, gebruik je het export  sleutelwoord:

Types Module in ReplicatedStorage

```

export type Cat = {

	Name: string,

	Meow: (Cat) -> ()

}

```

Script dat de Types Module gebruikt

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Types = require(ReplicatedStorage.Types)

local newCat: Types.Cat = {

	Name = "metatablecat",

	Meow = function(self)

		print(`{self.Name} zei meow`)

	end

}

newCat:Meow()

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
