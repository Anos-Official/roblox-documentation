<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/attributes -->

Eigenschappen en attributen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)

# Eigenschappen en attributen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het interactief maken van games betekent vaak het manipuleren van objecteigenschappen en -attributen:

-

Eigenschappen maken deel uit van de objectklasse. Bijvoorbeeld, de [BasePart.Anchored](/docs/nl-nl/reference/engine/classes/BasePart#Anchored)  eigenschap controleert de fysica voor het onderdeel. In een atletiekspel wil je misschien een discus of speer verankeren op het moment dat deze landt, zodat spelers een visuele indicator hebben van hoe ver deze is gevlogen.

-

Attributen zijn in wezen aangepaste eigenschappen die je definieert. Bijvoorbeeld, het [Plant](/docs/nl-nl/resources/plant-reference-project)  referentieproject gebruikt attributen om de aankoopprijs voor zaden en de maximale plantgrootte die een pot kan bevatten in te stellen.

## [Replicatievolgorde](#replicatievolgorde)[](#replicatievolgorde)

Voordat je begint met het ophalen en manipuleren van objecten, moet je een begrip hebben van de replicatievolgorde.

De Roblox Engine garandeert niet de volgorde waarin objecten (en wijzigingen aan objecten) worden gerepliceerd van de server naar de client, wat de [Instance:WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  methode essentieel maakt voor het toegang krijgen tot objecten in clientscripts, met name objecten in de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) .

Bijvoorbeeld, als een serverscript een eigenschap van een instantie in de Workspace wijzigt en vervolgens [RemoteEvent:FireAllClients()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireAllClients)  aanroept, kan de wijziging van de eigenschap naar de client repliceren voordat of nadat [RemoteEvent.OnClientEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent#OnClientEvent)  wordt geactiveerd. Gebruik de beschikbare methoden en evenementen om [wijzigingen te detecteren](#wijzigingen-detecteren)  in plaats van aan te nemen dat een wijziging is gerepliceerd. Wijzigingen van hetzelfde type, zoals twee attribuutwijzigingen, komen over het algemeen wel  in volgorde aan.

Wanneer clients voor het eerst een game starten, zijn sommige aspecten van replicatie en scriptuitvoering voorspelbaar:

1.

De client laadt de inhoud van [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst) , zoals een laadscherm, assets en scripts.

2.

[LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  (en [Scripts](/docs/nl-nl/reference/engine/classes/Script)  met een [RunContext](/docs/nl-nl/reference/engine/classes/Script#RunContext)  van [Client](/docs/nl-nl/reference/engine/enums/RunContext#Client) ) in [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  worden uitgevoerd. Deze scripts kunnen veilig objecten ophalen uit [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  zonder [Instance:WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  te gebruiken:

```

-- Veilig

local ReplicatedFirst = game:GetService("ReplicatedFirst")

local LoadingScreen = require(ReplicatedFirst.LoadingScreen)

```

Deze scripts kunnen niet  veilig objecten ophalen uit andere [services](/docs/nl-nl/scripting/services) , omdat deze mogelijk nog niet zijn geladen:

```

-- Niet veilig

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local PickupManager = require(ReplicatedStorage.PickupManager)

```

Je kunt  [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  in deze scripts gebruiken om objecten uit andere services op te halen, maar dit tenietdoet de voordelen van het gebruik van [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst) .

3.

De client gaat verder met het laden van de rest van de game.

4.

Wanneer het klaar is, wordt het [Loaded](/docs/nl-nl/reference/engine/classes/DataModel#Loaded)  evenement geactiveerd en retourneert [IsLoaded()](/docs/nl-nl/reference/engine/classes/DataModel#IsLoaded)  waar.

5.

[LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  in Players.[Player].PlayerScripts  (gekopieerd van [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts) ) worden uitgevoerd, evenals client [Scripts](/docs/nl-nl/reference/engine/classes/Script)  in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) . Deze scripts kunnen veilig objecten ophalen uit [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  zonder [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  te gebruiken.

6.

Het [Character](/docs/nl-nl/reference/engine/classes/Player#Character)  model van de speler verschijnt in de game.

7.

[LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  in Workspace.[Character]  (gekopieerd van [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts) ) worden uitgevoerd.

Als je game [instantie-streaming](/docs/nl-nl/workspace/streaming)  ([Workspace.StreamingEnabled](/docs/nl-nl/reference/engine/classes/Workspace#StreamingEnabled) ) gebruikt, zijn sommige of de meeste objecten mogelijk nog niet in de workspace geladen, zodat het gebruik van [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  om toegang te krijgen tot workspace-objecten een nog belangrijkere veiligheidsmaatregel wordt. Zie in het bijzonder [stream in](/docs/nl-nl/workspace/streaming#stream-in)  en [per-model streamingcontroles](/docs/nl-nl/workspace/streaming#per-model-streaming-controls)  voor aanvullende informatie over het laden en afstemmen van streaminggedrag.

## [Objecten ophalen](#objecten-ophalen)[](#objecten-ophalen)

De eerste stap om objecteigenschappen en -attributen te wijzigen is het verkrijgen van een referentie naar het object. De eenvoudigste oplossing is om het script een kind van het object in de Explorer  te maken en script.Parent  te gebruiken om naar het object te verwijzen.

 ![Een script dat aan een model in de Explorer is gekoppeld.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Script-Parent-Model.png)

```

local sign = script.Parent

```

De meer universele oplossing is om het object uit een [service](/docs/nl-nl/scripting/services)  te halen met methoden zoals [Instance:FindFirstChild()](/docs/nl-nl/reference/engine/classes/Instance#FindFirstChild)  of [Instance:WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild) .

 ![Een Model binnen een Map in ReplicatedStorage.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Script-Parent-ReplicatedStorage.png)

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local signsFolder = ReplicatedStorage:WaitForChild("Signs")

local sign = signsFolder:WaitForChild("InteractiveSign")

```

## [Eigenschappen wijzigen](#eigenschappen-wijzigen)[](#eigenschappen-wijzigen)

Eigenschappen zijn eenvoudig toegankelijk — gebruik gewoon een .  na de objectreferentie — hoewel je, als je met een model werkt, misschien een individueel onderdeel moet kiezen in plaats van het model zelf.

 ![Een Model binnen ReplicatedStorage.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-Model.png)

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local chair = ReplicatedStorage:WaitForChild("Chair")

chair.LeftArmRest.Size = Vector3.new(10, 1, 10)

```

## [Attributen aanmaken](#attributen-aanmaken)[](#attributen-aanmaken)

Hoewel je attributen programmatisch kunt aanmaken, is de meer gebruikelijke oplossing om ze met standaardwaarden in de Studio-gebruikersinterface aan te maken. Vervolgens kun je scripts gebruiken om hun waarden te wijzigen als reactie op spelersacties.

 ![Een script binnen een map in ReplicatedStorage.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Attributes-Example.png)

Voor informatie over het aanmaken van attributen in Studio, zie [instantie-attributen](/docs/nl-nl/studio/properties#instantie-attributen) .

## [Attributen instellen](#attributen-instellen)[](#attributen-instellen)

Om de waarde van een attribuut te wijzigen, roep je [Instance:SetAttribute()](/docs/nl-nl/reference/engine/classes/Instance#SetAttribute)  aan met een naam en waarde.

Attribuut aanmaken of wijzigen

```

local cabbage = script.Parent

cabbage:SetAttribute("Harvestable", true)

```

Als het attribuut nog niet bestaat, maakt deze methode het aan.

## [Attribuutwaarden ophalen](#attribuutwaarden-ophalen)[](#attribuutwaarden-ophalen)

Om de waarde van één bestaand attribuut op te halen, roep je [Instance:GetAttribute()](/docs/nl-nl/reference/engine/classes/Instance#GetAttribute)  aan op de instantie.

Attribuutwaarde ophalen

```

local cabbage = script.Parent

cabbage:SetAttribute("Harvestable", true)

local isHarvestable = cabbage:GetAttribute("Harvestable")

print(isHarvestable) --> true

```

Evenzo kun je alle attributen ophalen door [Instance:GetAttributes()](/docs/nl-nl/reference/engine/classes/Instance#GetAttributes)  aan te roepen. Deze methode retourneert een woordenboek van sleutel-waarde paren.

Alle attributen ophalen

```

local cabbage = script.Parent

local cabbageAttributes = cabbage:GetAttributes()

print(cabbageAttributes.GrowthRate) --> 2

for k, v in cabbageAttributes do

	print(k, v)

end

```

## [Attributen verwijderen](#attributen-verwijderen)[](#attributen-verwijderen)

Om een attribuut te verwijderen, stel je de waarde in op nil .

Attribuut verwijderen

```

local cabbage = script.Parent

cabbage:SetAttribute("GrowthRate", nil)

```

## [Wijzigingen detecteren](#wijzigingen-detecteren)[](#wijzigingen-detecteren)

Er zijn verschillende manieren om te luisteren naar wijzigingen in eigenschappen en attributen:

-

Het [Instance.AttributeChanged](/docs/nl-nl/reference/engine/classes/Instance#AttributeChanged)  evenement luistert naar wijzigingen in elk attribuut en geeft de naam van het gewijzigde attribuut door als parameter.

-

De [Instance:GetPropertyChangedSignal()](/docs/nl-nl/reference/engine/classes/Instance#GetPropertyChangedSignal)  methode laat je luisteren naar wijzigingen in één eigenschap en geeft geen parameters door.

-

De [Instance:GetAttributeChangedSignal()](/docs/nl-nl/reference/engine/classes/Instance#GetAttributeChangedSignal)  methode laat je luisteren naar wijzigingen in één attribuut en geeft geen parameters door.

Vanwege de minimale informatie die deze evenementen en methoden als parameters doorgeven, zijn ze allemaal goed geschikt voor anonieme functies, met name [Instance:GetPropertyChangedSignal()](/docs/nl-nl/reference/engine/classes/Instance#GetPropertyChangedSignal)  en [Instance:GetAttributeChangedSignal()](/docs/nl-nl/reference/engine/classes/Instance#GetAttributeChangedSignal) . Om meer te leren over anonieme functies en het werken met evenementen, zie [Evenementen](/docs/nl-nl/scripting/events) .

Luister naar wijzigingen

```

local cabbage = script.Parent

-- Lokale functies

local function onAnyPropertyChange(property)

	-- Negeer wijzigingen in attributen

	if property ~= "Attributes" then

		print(property) --> Naam

		print(cabbage[property]) --> Cabbage1

	end

end

local function onAnyAttributeChange(attribute)

	print(attribute) --> Grow, GrowthRate

	print(cabbage:GetAttribute(attribute)) --> false, 3

end

-- Luister naar wijzigingen en verbind met lokale functies

cabbage.Changed:Connect(onAnyPropertyChange)

cabbage.AttributeChanged:Connect(onAnyAttributeChange)

-- Luister naar wijzigingen en verbind met anonieme functies

cabbage:GetPropertyChangedSignal("Name"):Connect(function()

	print(cabbage.Name) --> Cabbage1

end)

cabbage:GetAttributeChangedSignal("GrowthRate"):Connect(function()

	print(cabbage:GetAttribute("GrowthRate")) --> 3

end)

-- Activeert Changed en GetPropertyChangedSignal()

cabbage.Name = "Cabbage1"

-- Activeert Changed en AttributeChanged

cabbage:SetAttribute("Grow", false)

-- Activeert Changed, AttributeChanged, en GetAttributeChangedSignal()

cabbage:SetAttribute("GrowthRate", 3)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
