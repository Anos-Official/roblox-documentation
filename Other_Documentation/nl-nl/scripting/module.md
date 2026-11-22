<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/module -->

Hergebruik code | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)

# Hergebruik code

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Na het maken van een paar scripts duurt het nooit lang voordat je wat code tussen hen wilt hergebruiken. Afhankelijk van [locatie](/docs/nl-nl/scripting/locations)  stellen [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  je in staat om code tussen scripts aan verschillende zijden van de client-servergrens of aan dezelfde kant van de grens te hergebruiken.

Je kunt modulescripts overal plaatsen waar je scripts plaatst, maar [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  is een populaire locatie; het opslaan van modulescripts hier stelt je in staat om code tussen de server en clients te hergebruiken.

## [Anatomie van een modulescript](#anatomie-van-een-modulescript)[](#anatomie-van-een-modulescript)

Voeg in Roblox Studio een modulescript toe aan ReplicatedStorage  en hernoem het naar PickupManager . Elk [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  begint met de volgende code:

```

local module = {}

return module

```

Deze code creëert een lege Luau [tabel](/docs/nl-nl/luau/tables)  en retourneert deze aan elk script dat het modulescript vereist.

De retourwaarde kan elk [gegevenstype](/docs/nl-nl/reference/engine/datatypes)  zijn, behalve nil , maar de meeste modulescripts retourneren een functie, een tabel of een tabel van functies. Om zijn retourwaarde te genereren, kunnen modulescripts natuurlijk willekeurige code uitvoeren, wat het vereisen van andere modulescripts omvat.

Wees voorzichtig om niet te hebben dat modulescripts elkaar op een circulaire manier vereisen, wat resulteert in een Requested module was required recursively  fout.

Het volgende voorbeeld retourneert een tabel met een enkele functie genaamd getPickupBonus . Plak het in het nieuwe modulescript:

```

-- ModuleScript in ReplicatedStorage

local PickupManager = {}

local defaultMultiplier = 1.25

local rarityMultipliers = {

	common = 10,

	uncommon = 20,

	rare = 50,

	legendary = 100

}

-- Voeg de getPickupBonus functie toe aan de PickupManager tabel

PickupManager.getPickupBonus = function(rarity)

	local bonus = rarityMultipliers[rarity] * defaultMultiplier

	return bonus

end

return PickupManager

```

Het toevoegen van de functie aan een tabel is niet strikt noodzakelijk; je zou gewoon de functie zelf kunnen retourneren, maar het is een goed patroon om te volgen; het geeft je een gemakkelijk te begrijpen syntaxis wanneer je de functie vanuit een ander script aanroept en stelt je in staat om in de loop van de tijd eenvoudig meer functies aan het modulescript toe te voegen.

## [Vereis modulescripts](#vereis-modulescripts)[](#vereis-modulescripts)

Om een modulescript te laden, roep je de [require()](/docs/nl-nl/reference/engine/globals/LuaGlobals#require)  functie aan. Voeg in ReplicatedStorage  een nieuw script toe en wijzig de RunContext  naar Client . Voeg vervolgens de volgende code toe om de PickupManager.getPickupBonus  functie aan te roepen:

Client script in ReplicatedStorage

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Verkrijg de waarde die door het ModuleScript is geretourneerd

local PickupManager = require(ReplicatedStorage:WaitForChild("PickupManager"))

-- Roep een ModuleScript functie aan

local bonus = PickupManager.getPickupBonus("legendary")

print(bonus)  --> 125

```

Het [Instance:WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  patroon is een belangrijke veiligheidsmaatregel in client scripts. Voor meer informatie, zie [Replicatie volgorde](/docs/nl-nl/scripting/attributes#replicatievolgorde) .

Het opslaan van modulescripts in ReplicatedStorage  stelt je in staat om code tussen de server en client te delen, zodat je dezelfde code kunt gebruiken om het script vanuit ServerScriptService  te vereisen:

Script in ServerScriptService

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local PickupManager = require(ReplicatedStorage:WaitForChild("PickupManager"))

```

Wanneer je [require()](/docs/nl-nl/reference/engine/globals/LuaGlobals#require)  aanroept op een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript) , wordt deze eenmaal uitgevoerd en retourneert deze een enkel item als referentie. Het opnieuw aanroepen van [require()](/docs/nl-nl/reference/engine/globals/LuaGlobals#require)  retourneert exact dezelfde referentie, wat betekent dat als je een geretourneerde [tabel](/docs/nl-nl/luau/tables)  of [Instance](/docs/nl-nl/reference/engine/classes/Instance)  wijzigt, de daaropvolgende [require()](/docs/nl-nl/reference/engine/globals/LuaGlobals#require)  aanroepen die gewijzigde referentie retourneren. Het module zelf wordt niet meerdere keren uitgevoerd.

Als je een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  van beide zijden van de client-servergrens vereist, zoals in het bovenstaande voorbeeld, retourneert het [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  een unieke referentie voor elke kant.

## [Patronen](#patronen)[](#patronen)

Modulescripts hebben enkele veelvoorkomende patronen die je kunt gebruiken om je code te vereenvoudigen en valkuilen te vermijden naarmate je spel groter en complexer wordt.

De meeste van deze patronen vereisen een begrip van evenementen. Als je daar niet mee bekend bent, zie [Evenementen](/docs/nl-nl/scripting/events) .

### [Gegevens delen](#gegevens-delen)[](#gegevens-delen)

Om gegevens aan individuele objecten te koppelen, kun je attributen aan hen toewijzen of [Configuration](/docs/nl-nl/reference/engine/classes/Configuration)  mappen maken met waarde-objecten zoals [StringValue](/docs/nl-nl/reference/engine/classes/StringValue)  of [IntValue](/docs/nl-nl/reference/engine/classes/IntValue) . Beide benaderingen zijn echter problematisch als je tientallen objecten of datavariabelen wilt toevoegen of wijzigen. Ze slaan ook geen tabellen of functies op.

Als je dezelfde gegevens voor meerdere kopieën van hetzelfde object wilt wijzigen of dezelfde gegevens voor verschillende objecten wilt hergebruiken, sla de gegevens dan op in [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript) . Het is een gemakkelijkere manier voor jou om de gegevens in andere scripts te hergebruiken, en je kunt tabellen en functies opslaan.

Het volgende voorbeeld [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  slaat de configuratiewaarden voor een generiek wapen op:

ModuleScript in ReplicatedStorage

```

local GunConfig = {}

GunConfig.MagazineSize = 20

GunConfig.AmmoCount = 100

GunConfig.Firerate = 600

GunConfig.Damage = {

  ["Head"] = 50;

  ["Torso"] = 40;

  ["Body"] = 25;

}

return GunConfig

```

### [Aangepaste evenementen](#aangepaste-evenementen)[](#aangepaste-evenementen)

Aangepaste evenementen stellen scripts in staat om met elkaar te communiceren, maar het bijhouden van referenties naar individuele [BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent)  objecten kan je code rommelig maken.

Je kunt [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  gebruiken om [BindableEvents](/docs/nl-nl/reference/engine/classes/BindableEvent)  op te slaan en aangepaste gebeurtenishandlers te bieden die direct zijn gekoppeld aan de methoden van [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript) .

Het volgende [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  heeft een aangepast evenement dat afgaat wanneer de schakelaar van staat verandert:

ModuleScript in ReplicatedStorage

```

local Switch = {}

-- Een bindbare maken zodat elk script kan luisteren naar wanneer de schakelaar is veranderd

local bindableEvent = Instance.new("BindableEvent")

Switch.Changed = bindableEvent.Event

local state = false

function Switch.flip()

  state = not state

  bindableEvent:Fire(state)

end

return Switch

```

Het volgende client script in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  verbindt een functie die moet worden aangeroepen wanneer het Switch.Changed  evenement afgaat.

Script in ReplicatedStorage

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Switch = require(ReplicatedStorage:WaitForChild("Switch"))

Switch.Changed:Connect(function(newState)

  print("Schakelaar staat is nu", newState)

end)

-- Test het flippen een paar keer

task.wait(1)

Switch.flip()

task.wait(1)

Switch.flip()

```

### [Encapsulatie](#encapsulatie)[](#encapsulatie)

Encapsulatie is de praktijk van het creëren van een abstractielaag rond objecten of scriptinglogica om complexiteit te verbergen. Je kunt [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  gebruiken om Roblox-objecten te encapsuleren met aangepaste Luau-functies om de code te vereenvoudigen.

Bijvoorbeeld, je kunt encapsulatie gebruiken om:

-

Communicatie tussen netwerken te vereenvoudigen met een enkel [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  object.

-

Foutafhandelingscode rond gevoelige services zoals [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  te wikkelen.

-

Aangepaste methoden te definiëren om de functies van Roblox-objecten te controleren of uit te breiden.

Het is moeilijk om tientallen individuele [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  objecten bij te houden om netwerken in een spel te implementeren. Je kunt een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  gebruiken om een enkele [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  te encapsuleren om dit probleem te vereenvoudigen. Door een unieke id  argument op te nemen, kun je nog steeds verschillende netwerkberichten verzenden terwijl je slechts één [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  gebruikt.

In het onderstaande voorbeeld encapsuleert het [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  genaamd NetworkManagerClient  de [RemoteEvent:FireServer()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireServer)  methode om dit extra id  argument op te nemen. Bovendien verwijst dit [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  naar het [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  object zelf, zodat je het niet in andere delen van je code hoeft te verwijzen. Je hoeft alleen dit [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  te vereisen om netwerkberichten te verzenden en hoeft niet met [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  objecten in de rest van je codebase om te gaan.

Het volgende [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  in [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  biedt een ingekapselde functie die je kunt aanroepen in je client scripts om een netwerkbericht te verzenden:

Netwerk Module

```

-- ModuleScript in ReplicatedFirst genaamd NetworkManagerClient

local NetworkManagerClient = {}

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:WaitForChild("RemoteEvent")

-- De FireServer functie van het remote object encapsuleren

function NetworkManagerClient.FireServer(id, ...)

  remoteEvent:FireServer(id, ...)

end

return NetworkManagerClient

```

Het volgende [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  gebruikt [BindableEvents](/docs/nl-nl/reference/engine/classes/BindableEvent)  voor elk script om verbinding te maken met een specifieke ID. Wanneer een client een netwerkbericht verzendt, gaat elke [BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent)  die aan de opgegeven ID is gekoppeld af.

```

-- ModuleScript in ServerScriptService genaamd NetworkManagerServer

local NetworkManagerServer = {}

local networkSignalList = {}

function NetworkManagerServer.GetServerEventSignal(id)

	local bindableEvent = Instance.new("BindableEvent")

	-- De nieuwe BindableEvent koppelen aan de id

	table.insert(networkSignalList, {

		id = id,

		bindableEvent = bindableEvent,

	})

	return bindableEvent.Event

end

-- Verbinden met

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:WaitForChild("RemoteEvent")

remoteEvent.OnServerEvent:Connect(function(player, id, ...)

	-- Elke bindbare gebeurtenis vinden die overeenkomt met de ID van het ontvangen remote event

	for _, signal in networkSignalList do

		if signal.id == id then

			signal.bindableEvent:Fire(player, ...)

		end

	end

end)

return NetworkManagerServer

```

Het volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  verzendt een bericht met de ID RequestA  met een optionele Hello  argument.

```

-- LocalScript in ReplicatedFirst

local ReplicatedFirst = game:GetService("ReplicatedFirst")

local NetworkManagerClient = require(ReplicatedFirst:WaitForChild("NetworkManagerClient"))

NetworkManagerClient.FireServer("RequestA", "Hello")

```

Het volgende [Script](/docs/nl-nl/reference/engine/classes/Script)  maakt verbinding met de netwerkbericht ID RequestA  en print een verklaring met eventuele extra parameters wanneer het de aanvraag ontvangt.

```

-- Script in ServerScriptService

local ServerScriptService = game:GetService("ServerScriptService")

local NetworkManagerServer = require(ServerScriptService:WaitForChild("NetworkManagerServer"))

NetworkManagerServer.GetServerEventSignal("RequestA"):Connect(function(player, ...)

	print("Ontvangen RequestA van", player, ...)

end)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
