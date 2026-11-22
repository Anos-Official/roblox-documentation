<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/events/remote -->

Remote evenementen en callbacks | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Evenementen](/docs/nl-nl/scripting/events)

# Remote evenementen en callbacks

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox-spellen zijn standaard multiplayer, dus alle spellen communiceren inherent tussen de server en de verbonden clients van de spelers. In het eenvoudigste geval, terwijl spelers hun personages bewegen, worden bepaalde [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  eigenschappen, zoals toestanden, naar de server gecommuniceerd, die deze informatie doorgeeft aan andere verbonden clients.

Remote evenementen en callbacks stellen je in staat om over  de client-server grens te communiceren:

-

[RemoteEvents](/docs/nl-nl/reference/engine/classes/RemoteEvent)  maken eenrichtingscommunicatie mogelijk (een verzoek verzenden en niet  wachten op een antwoord).

-

[UnreliableRemoteEvents](/docs/nl-nl/reference/engine/classes/UnreliableRemoteEvent)  maken eenrichtingscommunicatie mogelijk voor gegevens die continu veranderen of niet kritisch zijn voor de status van het spel. Deze evenementen ruilen volgorde en betrouwbaarheid in voor verbeterde netwerkprestaties.

-

[RemoteFunctions](/docs/nl-nl/reference/engine/classes/RemoteFunction)  maken tweerichtingscommunicatie mogelijk (een verzoek verzenden en wachten totdat een antwoord is ontvangen van de ontvanger).

In tegenstelling tot [bindbare evenementen](/docs/nl-nl/scripting/events/bindable) , die een meer beperkte nut hebben, zijn de gebruiksgevallen voor remote evenementen en functies te talrijk om op te sommen:

-

Gameplay  - Basis gameplay, zoals een speler die het einde van een level bereikt, kan een remote evenement vereisen. Een clientscript meldt dit aan de server, en serverscripts resetten de positie van de speler.

-

Server verificatie  - Als een speler probeert een potion te drinken, heeft hij die potion dan echt? Om eerlijkheid te waarborgen, moet de server de bron van waarheid voor een spel zijn. Een clientscript kan een remote evenement gebruiken om de server te informeren dat de speler een potion drinkt, en dan kunnen serverscripts beslissen of de speler die potion daadwerkelijk heeft en of er voordelen moeten worden toegekend.

-

Updates van de gebruikersinterface  - Terwijl de status van het spel verandert, kunnen serverscripts remote evenementen gebruiken om clients te informeren over veranderingen in scores, doelstellingen, enz.

-

In-game Marketplace aankopen  - Voor een voorbeeldimplementatie die remote functies gebruikt, zie [Prompt abonnement aankopen](/docs/nl-nl/production/monetization/subscriptions#vraag-abonnement-aankopen-aan) .

## [Snelle referentie](#snelle-referentie)[](#snelle-referentie)

De volgende tabellen dienen als een snelle referentie voor hoe je [RemoteEvents](/docs/nl-nl/reference/engine/classes/RemoteEvent)  en [RemoteFunctions](/docs/nl-nl/reference/engine/classes/RemoteFunction)  kunt gebruiken om te communiceren tussen de client en de server.

Remote evenementen Remote functies

| [Client → Server](#client-server) |
| --- | --- |
| Client | | RemoteEvent:FireServer(args) |
| Server | | RemoteEvent.OnServerEvent:Connect(function(player, args)) |
| [Server → Client](#server-client) |
| Server | | RemoteEvent:FireClient(player, args) |
| Client | | RemoteEvent.OnClientEvent:Connect(function(args)) |
| [Server → Alle Clients](#server-alle-clients) |
| Server | | RemoteEvent:FireAllClients(args) |
| Client | | RemoteEvent.OnClientEvent:Connect(function(args)) |

## [Remote evenementen](#remote-evenementen)[](#remote-evenementen)

Een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  object faciliteert asynchrone, eenrichtingscommunicatie over de client-server grens zonder te wachten op een antwoord.

Om een nieuwe [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  te maken via het [Explorer](/docs/nl-nl/studio/explorer)  venster in Studio:

1.

Beweeg de muis over de container waarin je de [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  wilt invoegen. Om ervoor te zorgen dat zowel server als client toegang hebben, moet het zich op een plaats bevinden waar beide zijden het kunnen zien, zoals [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) , hoewel het in sommige gevallen gepast is om het op te slaan in [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  of binnen een [Tool](/docs/nl-nl/reference/engine/classes/Tool) .

2.

Klik op de ⊕  knop die verschijnt rechts van de naam van de container en voeg een RemoteEvent  instantie toe.

3.

Hernoem de instantie om het doel ervan te beschrijven.

Zodra je een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  hebt gemaakt, kan het eenrichtingscommunicatie faciliteren van [client naar server](#client-server) , van [server naar client](#server-client) , of van de [server naar alle clients](#server-alle-clients) .

![](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Client-Server.png) Client → Server

![](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Server-Client.png) Server → Client

![](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Server-All-Clients.png) Server → Alle Clients

Clients kunnen niet rechtstreeks met andere clients communiceren, hoewel je effectief een evenement van de ene client naar de andere kunt verzenden door de [RemoteEvent:FireServer()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireServer)  methode te gebruiken, en vervolgens [FireClient()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireClient)  of [FireAllClients()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireAllClients)  aan te roepen in de gebeurtenishandler voor [OnServerEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent#OnServerEvent) .

### [Client → server](#client-server)[](#client-server)

Je kunt een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  gebruiken om een evenement op de [server](/docs/nl-nl/projects/client-server)  te activeren door de [FireServer()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireServer)  methode aan te roepen op een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent) . Als je argumenten doorgeeft aan [FireServer()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireServer) , worden ze doorgegeven aan de gebeurtenishandler op de server met bepaalde [beperkingen](#argument-beperkingen) . Merk op dat de eerste parameter van de gebeurtenishandler op de server altijd het [Player](/docs/nl-nl/reference/engine/classes/Player)  object is van de client die het aanroept, en extra parameters volgen.

| Client | | RemoteEvent:FireServer(args) |
| Server | | RemoteEvent.OnServerEvent:Connect(function(player, args)) |

De volgende [Script](/docs/nl-nl/reference/engine/classes/Script)  verbindt een gebeurtenishandler met [OnServerEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent#OnServerEvent)  die een nieuwe [Part](/docs/nl-nl/reference/engine/classes/Part)  op de server creëert. Het bijbehorende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  roept vervolgens [FireServer()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireServer)  aan op de [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  instantie met de gewenste [Color](/docs/nl-nl/reference/engine/classes/BasePart#Color)  en [Position](/docs/nl-nl/reference/engine/classes/BasePart#Position)  voor het onderdeel.

Event Verbinding - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Workspace = game:GetService("Workspace")

-- Verkrijg referentie naar remote event instantie

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function onCreatePart(player, partColor, partPosition)

	print(player.Name .. " heeft het RemoteEvent geactiveerd")

	local newPart = Instance.new("Part")

	newPart.Color = partColor

	newPart.Position = partPosition

	newPart.Parent = Workspace

end

-- Verbind functie met evenement

remoteEvent.OnServerEvent:Connect(onCreatePart)

```

Event Activering - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Verkrijg referentie naar remote event instantie

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

-- Activeer het remote event en geef extra argumenten door

remoteEvent:FireServer(Color3.fromRGB(255, 0, 0), Vector3.new(0, 25, -20))

```

### [Server → client](#server-client)[](#server-client)

Je kunt een [Script](/docs/nl-nl/reference/engine/classes/Script)  gebruiken om een evenement op een [client](/docs/nl-nl/projects/client-server)  te activeren door de [FireClient()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireClient)  methode aan te roepen op een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent) . Het eerste argument voor [FireClient()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireClient)  is het [Player](/docs/nl-nl/reference/engine/classes/Player)  object van de client die je wilt laten reageren op het evenement, en extra argumenten worden met bepaalde [beperkingen](#argument-beperkingen)  naar de client doorgegeven. Merk op dat de gebeurtenishandler de [Player](/docs/nl-nl/reference/engine/classes/Player)  object niet als eerste argument hoeft op te nemen omdat je de speler op de client kunt bepalen met [Players.LocalPlayer](/docs/nl-nl/reference/engine/classes/Players#LocalPlayer) .

| Server | | RemoteEvent:FireClient(player, args) |
| Client | | RemoteEvent.OnClientEvent:Connect(function(args)) |

De volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  verbindt een gebeurtenishandler met het [OnClientEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent#OnClientEvent)  evenement. Het bijbehorende [Script](/docs/nl-nl/reference/engine/classes/Script)  luistert vervolgens naar binnenkomende spelers op de server en roept [FireClient()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireClient)  aan voor elk met willekeurige gegevens.

Event Verbinding - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Players = game:GetService("Players")

-- Verkrijg referentie naar remote event instantie

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local player = Players.LocalPlayer

local function onNotifyPlayer(maxPlayers, respawnTime)

   print("[Client] Evenement ontvangen door speler", player.Name)

   print(maxPlayers, respawnTime)

end

-- Verbind functie met evenement

remoteEvent.OnClientEvent:Connect(onNotifyPlayer)

```

Event Activering - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Players = game:GetService("Players")

-- Verkrijg referentie naar remote event instantie

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

-- Luister naar binnenkomende spelers en verstuur remote event naar elk

local function onPlayerAdded(player)

   print("[Server] Evenement versturen naar speler", player.Name)

   remoteEvent:FireClient(player, Players.MaxPlayers, Players.RespawnTime)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

### [Server → alle clients](#server-alle-clients)[](#server-alle-clients)

Je kunt een [Script](/docs/nl-nl/reference/engine/classes/Script)  gebruiken om een evenement op alle clients te activeren door de [FireAllClients()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireAllClients)  methode aan te roepen op een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent) . In tegenstelling tot [FireClient()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireClient) , vereist de [FireAllClients()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireAllClients)  methode geen [Player](/docs/nl-nl/reference/engine/classes/Player)  object omdat het het [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  naar alle clients verstuurt.

| Server | | RemoteEvent:FireAllClients(args) |
| Client | | RemoteEvent.OnClientEvent:Connect(function(args)) |

De volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  verbindt een gebeurtenishandler met het [OnClientEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent#OnClientEvent)  evenement dat een resterende afteltijd uitvoert. Het bijbehorende [Script](/docs/nl-nl/reference/engine/classes/Script)  roept vervolgens [FireAllClients()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireAllClients)  in een lus elke seconde aan om het [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  voor alle clients te activeren.

Event Verbinding - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Verkrijg referentie naar remote event instantie

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function onTimerUpdate(seconds)

	print(seconds)

end

-- Verbind functie met evenement

remoteEvent.OnClientEvent:Connect(onTimerUpdate)

```

Event Activering - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Verkrijg referentie naar remote event instantie

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local countdown = 5

-- Activeer het RemoteEvent elke seconde totdat de tijd verstrijkt

for timeRemaining = -1, countdown do

	remoteEvent:FireAllClients(countdown - timeRemaining)

	task.wait(1)

end

```

## [Remote callbacks](#remote-callbacks)[](#remote-callbacks)

Een [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  object faciliteert synchrone, tweerichtingscommunicatie over de client-server grens. De verzender van een remote functie zal wachten totdat hij een antwoord van de ontvanger ontvangt.

Om een nieuwe [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  te maken via het [Explorer](/docs/nl-nl/studio/explorer)  venster in Studio:

1.

Beweeg de muis over de container waarin je de [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  wilt invoegen. Om ervoor te zorgen dat zowel server als client toegang hebben, moet het zich op een plaats bevinden waar beide zijden het kunnen zien, zoals [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) , hoewel het in sommige gevallen gepast is om het op te slaan in [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  of binnen een [Tool](/docs/nl-nl/reference/engine/classes/Tool) .

2.

Klik op de ⊕  knop die verschijnt rechts van de naam van de container en voeg een RemoteFunction  instantie toe.

3.

Hernoem de instantie om het doel ervan te beschrijven.

Zodra je een [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  hebt gemaakt, kan het tweerichtingscommunicatie faciliteren tussen [client en server](#client-server-client)  of tussen [server en client](#server-client-server) .

![](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Client-Server-Client.png) Client → Server → Client

![](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Remote-Flow-Server-Client-Server.png) Server → Client → Server

### [Client → server → client](#client-server-client)[](#client-server-client)

Je kunt een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  gebruiken om een functie op de [server](/docs/nl-nl/projects/client-server)  aan te roepen door de [InvokeServer()](/docs/nl-nl/reference/engine/classes/RemoteFunction#InvokeServer)  methode aan te roepen op een [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction) . In tegenstelling tot een [remote evenement](#remote-evenementen) , wacht de [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  die de [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  aanroept totdat de callback retourneert. Argumenten die je doorgeeft aan [InvokeServer()](/docs/nl-nl/reference/engine/classes/RemoteFunction#InvokeServer)  worden doorgegeven aan de [OnServerInvoke](/docs/nl-nl/reference/engine/classes/RemoteFunction#OnServerInvoke)  callback van de [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  met bepaalde [beperkingen](#argument-beperkingen) . Merk op dat als je meerdere callbacks voor dezelfde [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  definieert, alleen de laatste definitie wordt uitgevoerd.

| Client | | RemoteFunction:InvokeServer(args) |
| Server | | RemoteFunction.OnServerInvoke = function(player, args) |

De volgende [Script](/docs/nl-nl/reference/engine/classes/Script)  definieert de callbackfunctie via [OnServerInvoke](/docs/nl-nl/reference/engine/classes/RemoteFunction#OnServerInvoke)  en retourneert het gevraagde [Part](/docs/nl-nl/reference/engine/classes/Part)  via zijn return  waarde. Het bijbehorende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  roept vervolgens [InvokeServer()](/docs/nl-nl/reference/engine/classes/RemoteFunction#InvokeServer)  aan met extra argumenten die de gevraagde kleur en positie van het onderdeel definiëren.

Callback Verbinding - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Workspace = game:GetService("Workspace")

-- Verkrijg referentie naar remote function instantie

local remoteFunction = ReplicatedStorage:FindFirstChildOfClass("RemoteFunction")

-- Callback functie

local function createPart(player, partColor, partPosition)

	print(player.Name .. " heeft een nieuw onderdeel aangevraagd")

	local newPart = Instance.new("Part")

	newPart.Color = partColor

	newPart.Position = partPosition

	newPart.Parent = Workspace

	return newPart

end

-- Stel functie in als callback van de remote functie

remoteFunction.OnServerInvoke = createPart

```

Event Aanroep - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Verkrijg referentie naar remote function instantie

local remoteFunction = ReplicatedStorage:FindFirstChildOfClass("RemoteFunction")

-- Geef een kleur en positie door bij het aanroepen van de callback

local newPart = remoteFunction:InvokeServer(Color3.fromRGB(255, 0, 0), Vector3.new(0, 25, -20))

-- Geef de geretourneerde referentie van het onderdeel weer

print("De server heeft het gevraagde onderdeel gemaakt:", newPart)

```

### [Server → client → server](#server-client-server)[](#server-client-server)

Je kunt een [Script](/docs/nl-nl/reference/engine/classes/Script)  gebruiken om een functie op de client aan te roepen door de [InvokeClient()](/docs/nl-nl/reference/engine/classes/RemoteFunction#InvokeClient)  methode aan te roepen op een [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction) , maar dit heeft ernstige risico's, zoals:

-

Als de client een fout gooit, gooit de server ook de fout.

-

Als de client wordt losgekoppeld terwijl deze wordt aangeroepen, gooit [InvokeClient()](/docs/nl-nl/reference/engine/classes/RemoteFunction#InvokeClient)  een fout.

-

Als de client geen waarde retourneert, wacht de server voor altijd.

Voor acties die geen tweerichtingscommunicatie vereisen, zoals het bijwerken van een GUI, gebruik een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  en communiceer van [server naar client](#server-client) .

## [Leveringsgaranties](#leveringsgaranties)[](#leveringsgaranties)

Elke remote type doet verschillende beloften over of een bericht aankomt en in welke volgorde. Deze beloften zijn alleen van toepassing op een enkele verbinding in één richting, wat betekent van de server naar één specifieke client, of van één specifieke client naar de server.

### [RemoteEvents](#remoteevents)[](#remoteevents)

[RemoteEvents](/docs/nl-nl/reference/engine/classes/RemoteEvent)  zijn betrouwbaar en geordend:

-

Als een bericht verloren gaat tijdens de verzending, verzendt Roblox het opnieuw totdat het aankomt, zolang de ontvanger verbonden blijft.

-

Berichten komen aan in de volgorde waarin je ze activeert, inclusief over verschillende [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  instanties . Bijvoorbeeld, als de server evenement A  activeert, dan B , en dan A  opnieuw naar dezelfde client, ontvangt die client A , B , A . Dit geldt of je nu [FireClient()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireClient)  of [FireAllClients()](/docs/nl-nl/reference/engine/classes/RemoteEvent#FireAllClients)  gebruikt.

-

Als een client evenementen sneller activeert dan de [beperkingen](#throttling-en-grootte-limieten) , verwerkt de server de overtollige evenementen later in plaats van ze te laten vallen, en ze behouden hun volgorde.

Een betrouwbaar, geordend bericht kan nog steeds falen om je code te bereiken in de volgende gevallen:

-

Er is geen handler verbonden.  Als er niets is verbonden met [OnServerEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent#OnServerEvent)  of [OnClientEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent#OnClientEvent)  wanneer een bericht aankomt, plaatst Roblox het in de wachtrij en levert het, in volgorde, zodra een handler verbindt. De wachtrij is beperkt in zowel aantal als geheugen. Zodra deze vol is, gooit Roblox verdere berichten weg en logt een Remote event invocation  fout in het [Output](/docs/nl-nl/studio/output)  venster.

-

De ontvanger wordt losgekoppeld.  Berichten die niet zijn afgeleverd wanneer een client vertrekt, gaan verloren.

De volgorde geldt voor wanneer elke handler begint , niet wanneer deze eindigt. Als een handler wacht, zoals door [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  of [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  aan te roepen, kan Roblox beginnen met het verwerken van het volgende bericht voordat de eerdere handler hervat.

### [RemoteFunctions](#remotefunctions)[](#remotefunctions)

[RemoteFunctions](/docs/nl-nl/reference/engine/classes/RemoteFunction)  verzenden aanroepen en antwoorden betrouwbaar, zodat Roblox verloren berichten opnieuw verzendt zolang beide zijden verbonden blijven. Omdat [InvokeServer()](/docs/nl-nl/reference/engine/classes/RemoteFunction#InvokeServer)  en [InvokeClient()](/docs/nl-nl/reference/engine/classes/RemoteFunction#InvokeClient)  wachten totdat een antwoord aankomt, kan een enkele thread niet meer dan één aanroep in de lucht hebben. Gescheiden threads kunnen echter tegelijkertijd aanroepen, en als een callback wacht, kunnen antwoorden in een andere volgorde terugkomen dan de aanroepen zijn verzonden.

Als er geen callback is toegewezen aan [OnServerInvoke](/docs/nl-nl/reference/engine/classes/RemoteFunction#OnServerInvoke)  of [OnClientInvoke](/docs/nl-nl/reference/engine/classes/RemoteFunction#OnClientInvoke) , plaatst Roblox aanroepen in de wachtrij totdat er een is. Deze wachtrij heeft dezelfde soort beperkingen als de [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  wachtrij.

Roblox garandeert niet de relatieve volgorde van [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  aanroepen en [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  berichten. Ze komen vaak aan in de volgorde waarin je ze verzendt, maar ze worden afzonderlijk in de wachtrij geplaatst terwijl er geen handler is verbonden, en een wachtende callback kan een antwoord vertragen. Als je code afhankelijk is van strikte volgorde, stuur dan alle gerelateerde berichten via hetzelfde remote type of voeg je eigen volgnummer toe.

### [UnreliableRemoteEvents](#unreliableremoteevents)[](#unreliableremoteevents)

[UnreliableRemoteEvents](/docs/nl-nl/reference/engine/classes/UnreliableRemoteEvent)  garanderen noch levering, noch volgorde. Ze hebben ook geen volgorde relatie met [RemoteEvents](/docs/nl-nl/reference/engine/classes/RemoteEvent)  of [RemoteFunctions](/docs/nl-nl/reference/engine/classes/RemoteFunction) . Roblox kan een bericht in een van de volgende gevallen laten vallen, zonder het opnieuw te verzenden:

-

Het bericht gaat verloren tijdens de verzending.

-

Het netwerk is overbelast en het bericht wacht te lang om te verzenden.

-

De payload is groter dan 1.000 bytes.

-

De client activeert sneller dan de [beperkingen](#throttling-en-grootte-limieten) . In tegenstelling tot een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent) , laat de server de overtollige berichten vallen in plaats van ze te vertragen.

-

Er is niets verbonden met [OnServerEvent](/docs/nl-nl/reference/engine/classes/UnreliableRemoteEvent#OnServerEvent)  of [OnClientEvent](/docs/nl-nl/reference/engine/classes/UnreliableRemoteEvent#OnClientEvent)  wanneer het bericht aankomt. In tegenstelling tot een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent) , gooit Roblox het bericht onmiddellijk weg in plaats van het in de wachtrij te plaatsen.

Roblox wacht ook niet op een eerder bericht om aan te komen voordat het een later bericht verwerkt, zodat berichten in een andere volgorde kunnen aankomen. Als de volgorde belangrijk is, voeg dan een tijdstempel of volgnummer toe aan elk bericht en negeer berichten die ouder zijn dan de laatste die je hebt verwerkt.

### [Throttling en grootte limieten](#throttling-en-grootte-limieten)[](#throttling-en-grootte-limieten)

Client-naar-server berichten zijn onderworpen aan een snelheidslimiet die elk remote type deelt over al zijn instanties. Voor de huidige limieten, zie de Throttling  sectie van [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  en de payloadlimieten in [UnreliableRemoteEvent](/docs/nl-nl/reference/engine/classes/UnreliableRemoteEvent) .

## [Argument beperkingen](#argument-beperkingen)[](#argument-beperkingen)

Wanneer je een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  activeert of een [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  aanroept, worden alle argumenten die je doorgeeft met het evenement of aan de callbackfunctie doorgestuurd. Elk type Roblox-object zoals een [Enum](/docs/nl-nl/reference/engine/datatypes/Enum) , [Instance](/docs/nl-nl/reference/engine/classes/Instance) , of andere kan worden doorgegeven, evenals Luau-typen zoals getallen, strings en booleans, hoewel je zorgvuldig de volgende beperkingen moet verkennen.

### [Niet-string indices](#niet-string-indices)[](#niet-string-indices)

Als enige indices  van een doorgegeven tabel niet-stringtypen zijn, zoals een [Instance](/docs/nl-nl/reference/engine/classes/Instance) , [userdata](/docs/nl-nl/luau/userdata) , of [functie](/docs/nl-nl/luau/functions) , converteert Roblox deze indices automatisch naar strings.

Event Verbinding - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function onEventFire(passedTable)

	for k, v in passedTable do

		print(typeof(k))  --> string

	end

end

-- Verbind functie met evenement

remoteEvent.OnClientEvent:Connect(onEventFire)

```

Event Activering - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Players = game:GetService("Players")

local Workspace = game:GetService("Workspace")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

-- Luister naar binnenkomende spelers en verstuur remote event naar elk

local function onPlayerAdded(player)

	remoteEvent:FireClient(player,

		{

			[Workspace.Baseplate] = true

		}

	)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

### [Doorgegeven functies](#doorgegeven-functies)[](#doorgegeven-functies)

Functies die als argumenten zijn opgenomen voor een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  of [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  zullen niet  worden gerepliceerd over de [client-server](/docs/nl-nl/projects/client-server)  grens, waardoor het onmogelijk is om functies op afstand door te geven. In plaats daarvan zal het resulterende argument aan de ontvangende kant nil  zijn.

Event Verbinding - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function onClientEvent(func)

	print(func)  --> nil

end

remoteEvent.OnClientEvent:Connect(onClientEvent)

```

Event Activering - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function testFunction()

	print("Hallo wereld!")

end

-- Activeer remote event met functie als argument

remoteEvent:FireAllClients(testFunction)

```

### [Tabel indexering](#tabel-indexering)[](#tabel-indexering)

Als je een tabel met gegevens doorgeeft, geef dan geen gemengde tabel door met numerieke en string sleutels. Geef in plaats daarvan een tabel door die volledig  bestaat uit sleutel-waarde paren (woordenboek) of volledig  uit numerieke indices.

Of je nu een woordenboektabel of  een numeriek geïndexeerde tabel doorgeeft, vermijd nil  waarden voor elke index.

Event Verbinding - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function onEventFire(player, passedTable)

	for k, v in passedTable do

		print(k .. " = " .. v)

		--> 1 = Zwaard

		--> 2 = Boog

		--> CharName = Diva Dragonslayer

		--> CharClass = Rogue

	end

end

-- Verbind functie met evenement

remoteEvent.OnServerEvent:Connect(onEventFire)

```

Event Activering - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

-- Numeriek geïndexeerde tabel

local inventoryData = {

	"Zwaard", "Boog"

}

-- Woordenboek tabel

local characterData = {

	CharName = "Diva Dragonslayer",

	CharClass = "Rogue"

}

remoteEvent:FireServer(inventoryData)

remoteEvent:FireServer(characterData)

```

### [Tabel identiteiten](#tabel-identiteiten)[](#tabel-identiteiten)

Tabellen die als argumenten naar remote evenementen/callbacks worden doorgegeven, worden gekopieerd, wat betekent dat ze niet exact gelijk zullen zijn aan die welke zijn verstrekt bij het activeren van het evenement of het aanroepen van de callback. Evenmin zullen tabellen die aan de aanroeper worden geretourneerd exact gelijk zijn aan die welke zijn verstrekt. Je kunt dit demonstreren door het volgende script op een [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  uit te voeren en te observeren hoe de tabelidentiteiten verschillen.

Callback Verbinding - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteFunction = ReplicatedStorage:FindFirstChildOfClass("RemoteFunction")

-- Callback functie

local function returnTable(player, passedTable)

	-- Geef tabelidentiteit weer bij aanroep

	print(tostring(passedTable))  --> table: 0x48eb7aead27563d9

	return passedTable

end

-- Stel functie in als callback van de remote functie

remoteFunction.OnServerInvoke = returnTable

```

Event Aanroep - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteFunction = ReplicatedStorage:FindFirstChildOfClass("RemoteFunction")

local inventoryData = {

	"Zwaard", "Boog"

}

-- Geef originele tabelidentiteit weer

print(tostring(inventoryData))  --> table: 0x059bcdbb2b576549

local invokeReturn = remoteFunction:InvokeServer(inventoryData)

-- Geef tabelidentiteit bij terugkeer weer

print(tostring(invokeReturn))  --> table: 0x9fcae7919563a0e9

```

### [Metatables](#metatables)[](#metatables)

Als een tabel een metatable heeft, gaat alle metatable-informatie verloren tijdens de overdracht. In het volgende codevoorbeeld is de NumWheels  eigenschap onderdeel van de Car  metatable. Wanneer de server de volgende tabel ontvangt, heeft de truck  tabel de Name  eigenschap maar niet  de NumWheels  eigenschap.

Event Verbinding - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local function onEvent(player, param)

	print(param)  --> {["Name"] = "MyTruck"}

end

-- Verbind functie met evenement

remoteEvent.OnServerEvent:Connect(onEvent)

```

Event Activering - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

local Car = {}

Car.NumWheels = 4

Car.__index = Car

local truck = {}

truck.Name = "MyTruck"

setmetatable(truck, Car)

-- Activeer evenement met tabel inclusief een metatable

remoteEvent:FireServer(truck)

```

### [Niet-gerepliceerde instanties](#niet-gerepliceerde-instanties)[](#niet-gerepliceerde-instanties)

Als een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  of [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  een waarde doorgeeft die alleen zichtbaar is voor de verzender, repliceert Roblox deze niet over de client-server grens en geeft in plaats daarvan nil  door in plaats van de waarde. Bijvoorbeeld, als een [Script](/docs/nl-nl/reference/engine/classes/Script)  een afgeleide van [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage)  doorgeeft, ontvangt de client die naar het evenement luistert een nil  waarde omdat dat object niet repliceerbaar is voor de client.

Event Activering - Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local ServerStorage = game:GetService("ServerStorage")

local Players = game:GetService("Players")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

-- Zal worden ontvangen als "nil" omdat de client geen toegang heeft tot ServerStorage

local storedPart = Instance.new("Part")

storedPart.Parent = ServerStorage

local function onPlayerAdded(player)

	remoteEvent:FireClient(player, storedPart)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Evenzo, als je een onderdeel maakt in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  en probeert het naar een [Script](/docs/nl-nl/reference/engine/classes/Script)  door te geven, zal de server nil  zien omdat het onderdeel niet repliceerbaar is voor de server.

Event Activering - LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Workspace = game:GetService("Workspace")

local remoteEvent = ReplicatedStorage:FindFirstChildOfClass("RemoteEvent")

-- Zal worden ontvangen als "nil" omdat de server niets weet over dit onderdeel

local clientPart = Instance.new("Part")

clientPart.Parent = Workspace

remoteEvent:FireServer(clientPart)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
