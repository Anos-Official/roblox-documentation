<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/events/bindable -->

Bindbare evenementen en callbacks | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Evenementen](/docs/nl-nl/scripting/events)

# Bindbare evenementen en callbacks

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent)  en [BindableFunction](/docs/nl-nl/reference/engine/classes/BindableFunction)  objecten stellen je in staat om gedragingen tussen scripts aan dezelfde kant  van de [client-server](/docs/nl-nl/projects/client-server)  grens te binden en een specifieke gewenste uitkomst voor in-game acties te communiceren.

De meest voorkomende gebruiksgevallen voor bindbare evenementen zijn voor games die een ronde-gebaseerde structuur hebben. Bijvoorbeeld, je zou een "wedstrijd gestart" evenement kunnen hebben dat andere scripts in staat stelt een timer te starten en een leaderboard weer te geven, met een bijbehorend "wedstrijd beëindigd" evenement dat andere scripts laat weten wanneer ze spelers terug naar een lobby moeten verplaatsen en de winnaars moeten weergeven.

Omdat ze activiteiten tussen scripts coördineren, worden bindbare evenementen meestal op de server gebruikt, maar je kunt ze ook aan de clientzijde gebruiken.

Afhankelijk van hoe je game werkt, kunnen bindbare evenementen helpen om je code modulairder te maken, maar [module scripts](/docs/nl-nl/scripting/module)  zijn vaak een betere alternatieve voor situaties waarin je gegevens tussen scripts moet delen. Je kunt ook bindbare evenementen gebruiken in combinatie met module scripts voor een schonere syntaxis, zoals opgemerkt in [Aangepaste evenementen](/docs/nl-nl/scripting/module#aangepaste-evenementen) .

Om te communiceren tussen scripts over  de client-servergrens, zie [Remote events](/docs/nl-nl/scripting/events/remote) .

## [Bindbare evenementen](#bindbare-evenementen)[](#bindbare-evenementen)

Het [BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent)  object maakt aangepaste evenementen mogelijk via asynchrone, eenrichtingscommunicatie tussen scripts.

Wanneer je een [BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent)  activeert via de [Fire()](/docs/nl-nl/reference/engine/classes/BindableEvent#Fire)  methode, yield de activerende script niet , en de doel functie ontvangt de doorgegeven argumenten met bepaalde [beperkingen](#argumentbeperkingen) . Zoals alle evenementen, creëren [BindableEvents](/docs/nl-nl/reference/engine/classes/BindableEvent)  threads van elke verbonden functie, dus zelfs als er een fout optreedt, gaan anderen door.

Om een nieuwe [BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent)  te maken met behulp van het [Explorer](/docs/nl-nl/studio/explorer)  venster in Studio:

1.

Beweeg de muis over de container waarin je de [BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent)  wilt invoegen. We raden aan om [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  te gebruiken voor communicatie tussen server scripts en [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  voor communicatie tussen client scripts.

2.

Klik op de ⊕  knop die verschijnt rechts van de naam van de container en voeg een BindableEvent  instantie toe.

3.

Hernoem de instantie naar TestBindableEvent .

Nadat je een [BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent)  hebt gemaakt, verbind je een functie aan zijn [Event](/docs/nl-nl/reference/engine/classes/BindableEvent#Event)  evenement in één script, en activeer je vervolgens [Fire()](/docs/nl-nl/reference/engine/classes/BindableEvent#Fire)  het evenement vanuit een ander script.

Evenement Verbinding

```

local ServerScriptService = game:GetService("ServerScriptService")

-- Verkrijg referentie naar bindbare evenement instantie

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

-- Verbind anonieme functie met evenement

bindableEvent.Event:Connect(function(data)

	print(data)  --> Ronde gestart!

end)

```

Evenement Activering

```

local ServerScriptService = game:GetService("ServerScriptService")

-- Verkrijg referentie naar bindbare evenement instantie

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

-- Activeer bindbare evenement

bindableEvent:Fire("Ronde gestart!")

```

Je kunt meerdere functies verbinden met dezelfde [BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent) , maar Luau voert ze in een onvoorspelbare volgorde uit. Om ervoor te zorgen dat functies in een bepaalde volgorde worden uitgevoerd, combineer ze in één functie en verbind deze met het evenement.

## [Aangepaste callbacks](#aangepaste-callbacks)[](#aangepaste-callbacks)

Het [BindableFunction](/docs/nl-nl/reference/engine/classes/BindableFunction)  object staat synchrone, tweerichtingscommunicatie tussen scripts toe. Je kunt het gebruiken om een aangepaste callbackfunctie te definiëren en deze handmatig aan te roepen door [BindableFunction:Invoke()](/docs/nl-nl/reference/engine/classes/BindableFunction#Invoke)  aan te roepen. De code die de functie aanroept yield  totdat de bijbehorende callback is gevonden, en de callback ontvangt de argumenten die je doorgegeven hebt aan [Invoke()](/docs/nl-nl/reference/engine/classes/BindableFunction#Invoke) . Als de callback nooit is ingesteld, hervat het script dat het aanroept geen uitvoering.

Om een nieuwe [BindableFunction](/docs/nl-nl/reference/engine/classes/BindableFunction)  te maken met behulp van het [Explorer](/docs/nl-nl/studio/explorer)  venster in Studio:

1.

Beweeg de muis over de container waarin je de [BindableFunction](/docs/nl-nl/reference/engine/classes/BindableFunction)  wilt invoegen. We raden aan om [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  te gebruiken voor communicatie tussen server scripts en [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  voor communicatie tussen client scripts.

2.

Klik op de ⊕  knop die verschijnt rechts van de naam van de container en voeg een BindableFunction  instantie toe.

3.

Hernoem de instantie naar TestBindableFunction .

Zodra je een [BindableFunction](/docs/nl-nl/reference/engine/classes/BindableFunction)  hebt gemaakt, kun je verbinding maken met zijn [OnInvoke](/docs/nl-nl/reference/engine/classes/BindableFunction#OnInvoke)  callback in één script, en vervolgens [Invoke()](/docs/nl-nl/reference/engine/classes/BindableFunction#Invoke)  de callbackfunctie vanuit een ander script aanroepen.

Callback Verbinding

```

local ServerScriptService = game:GetService("ServerScriptService")

-- Verkrijg referentie naar bindbare functie

local bindableFunction = ServerScriptService:WaitForChild("TestBindableFunction")

-- Callback functie

local function addTwoNumbers(a, b)

	return a + b

end

-- Stel functie in als callback van bindbare functie

bindableFunction.OnInvoke = addTwoNumbers

```

Evenement Aanroep

```

local ServerScriptService = game:GetService("ServerScriptService")

-- Verkrijg referentie naar bindbare functie

local bindableFunction = ServerScriptService:WaitForChild("TestBindableFunction")

-- Roep callback functie aan en geef geretourneerde waarde weer

local sum = bindableFunction:Invoke(2, 4)

print(sum)  --> 6

```

Elke [BindableFunction](/docs/nl-nl/reference/engine/classes/BindableFunction)  kan slechts één [OnInvoke](/docs/nl-nl/reference/engine/classes/BindableFunction#OnInvoke)  callback gebruiken. Als je meerdere definities maakt, wordt alleen de laatste toegewezen functie uitgevoerd. Houd er ook rekening mee dat als de [OnInvoke](/docs/nl-nl/reference/engine/classes/BindableFunction#OnInvoke)  callback geen return  statement heeft, de aanroep nil  retourneert.

## [Argumentbeperkingen](#argumentbeperkingen)[](#argumentbeperkingen)

Wanneer je een [BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent)  activeert of een [BindableFunction](/docs/nl-nl/reference/engine/classes/BindableFunction)  aanroept, worden alle argumenten die je doorgeeft met het evenement of aan de callbackfunctie doorgestuurd. Je kunt elk type Roblox-object doorgeven ([Enum](/docs/nl-nl/reference/engine/datatypes/Enum) , [Instance](/docs/nl-nl/reference/engine/classes/Instance) , enz.), evenals Luau-typen zoals getallen, strings en booleans, hoewel je zorgvuldig de volgende beperkingen moet overwegen.

### [Niet-string indices](#niet-string-indices)[](#niet-string-indices)

Als enige indices  van een doorgegeven tabel niet-stringtypes zijn, zoals een [Instance](/docs/nl-nl/reference/engine/classes/Instance) , [userdata](/docs/nl-nl/luau/userdata) , of [functie](/docs/nl-nl/luau/functions) , converteert Roblox deze indices automatisch naar strings.

Evenement Verbinding

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

local function onEventFire(passedTable)

	for k, v in passedTable do

		print(typeof(k))  --> string

	end

end

-- Verbind functie met evenement

bindableEvent.Event:Connect(onEventFire)

```

Evenement Activering

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

-- Activeer evenement met tabel die een workspace instantie als sleutel bevat

bindableEvent:Fire({

	[workspace.Baseplate] = true

})

```

### [Tabelindexering](#tabelindexering)[](#tabelindexering)

Als je een tabel met gegevens doorgeeft, geef dan geen gemengde tabel van numerieke en string sleutels door. Dit kan resulteren in verwijderde elementen tijdens de overdracht. Geef in plaats daarvan een tabel door die volledig  uit sleutel-waarde paren (een woordenboek) of volledig  uit numerieke indices (een array) bestaat.

In beide gevallen, of je nu een woordenboek tabel of een numeriek geïndexeerde tabel doorgeeft, vermijd nil  waarden voor enige index.

Evenement Verbinding

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

local function onEventFire(passedTable)

	for k, v in passedTable do

		print(k .. " = " .. v)

		--> 1 = Zwaard

		--> 2 = Boog

		--> CharName = Diva Dragonslayer

		--> CharClass = Rogue

	end

end

-- Verbind functie met evenement

bindableEvent.Event:Connect(onEventFire)

```

Evenement Activering

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

-- Numeriek geïndexeerde tabel

local inventoryData = {

	"Zwaard", "Boog"

}

-- Woordenboek tabel

local characterData = {

	CharName = "Diva Dragonslayer",

	CharClass = "Rogue"

}

-- Activeer evenement met consistent geïndexeerde tabellen

bindableEvent:Fire(inventoryData)

bindableEvent:Fire(characterData)

```

### [Tabelidentiteiten](#tabelidentiteiten)[](#tabelidentiteiten)

Tabellen die als argumenten naar bindbare evenementen en callbacks worden doorgegeven, worden gekopieerd, wat betekent dat ze niet exact gelijk zullen zijn aan die welke zijn verstrekt bij het activeren van het evenement of het aanroepen van de callback. Evenmin zullen tabellen die aan de aanroeper worden geretourneerd exact gelijk zijn aan die welke zijn verstrekt. Je kunt dit demonstreren door het volgende script op een [BindableFunction](/docs/nl-nl/reference/engine/classes/BindableFunction)  uit te voeren en te observeren hoe de tabelidentiteiten verschillen.

Callback Verbinding

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableFunction = ServerScriptService:WaitForChild("TestBindableFunction")

-- Callback functie

local function returnTable(passedTable)

	-- Geef tabelidentiteit weer bij aanroep

	print(tostring(passedTable))  --> table: 0x48eb7aead27563d9

	return passedTable

end

-- Stel functie in als callback van bindbare functie

bindableFunction.OnInvoke = returnTable

```

Evenement Aanroep

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableFunction = ServerScriptService:WaitForChild("TestBindableFunction")

local inventoryData = {

	"Zwaard", "Boog"

}

-- Geef originele tabelidentiteit weer

print(tostring(inventoryData))  --> table: 0x059bcdbb2b576549

local invokeReturn = bindableFunction:Invoke(inventoryData)

-- Geef tabelidentiteit bij terugkeer weer

print(tostring(invokeReturn))  --> table: 0x9fcae7919563a0e9

```

### [Metatables](#metatables)[](#metatables)

Als een tabel een metatable heeft, gaat alle metatable-informatie verloren tijdens de overdracht. In de volgende codevoorbeeld is de NumWheels  eigenschap onderdeel van de Car  metatable. Wanneer de server de volgende tabel ontvangt, heeft de truck  tabel de Name  eigenschap maar niet  de NumWheels  eigenschap.

Evenement Verbinding

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

local function onEvent(param)

	print(param)  --> {["Name"] = "MyTruck"}

end

-- Verbind functie met evenement

bindableEvent.Event:Connect(onEvent)

```

Evenement Activering

```

local ServerScriptService = game:GetService("ServerScriptService")

local bindableEvent = ServerScriptService:WaitForChild("TestBindableEvent")

local Car = {}

Car.NumWheels = 4

Car.__index = Car

local truck = {}

truck.Name = "MyTruck"

setmetatable(truck, Car)

-- Activeer evenement met tabel inclusief een metatable

bindableEvent:Fire(truck)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
