<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/audio/add-voice-chat -->

Voeg spraakchat toe | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Audio

# Voeg spraakchat toe

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Spraakchat  is een op nabijheid gebaseerde chatfunctie die realistische communicatie simuleert door het volume van sprekende spelers aan te passen naarmate ze dichterbij of verder van elkaar in de 3D-ruimte bewegen. Door spelers met elkaar te laten praten via hun microfoons, kunnen ze in real-time socializen en strategiseren over de hele wereld om de doelstellingen van je game te voltooien.

Met behulp van het [Gingerbread Island - Spraakchat](https://www.roblox.com/games/91891961746476/Gingerbread-Island-Voice-Chat)  .rbxl  bestand als referentie, laat deze tutorial je zien hoe je verschillende vormen van spraakchat in je gameplay kunt integreren, inclusief richtlijnen over:

-

Spelers indelen in teams die alleen spraakchat met hun teamgenoten kunnen gebruiken.

-

Spelers tijdelijk hun microfoon laten activeren terwijl ze een specifieke knop op hun apparaat indrukken.

-

Tijdperiodes configureren waarin spraakchat ofwel is ingeschakeld of uitgeschakeld.

Terwijl je de volgende secties doorneemt naast het voorbeeld, kun je elk codevoorbeeld aanpassen om beter aan de behoeften van jouw spraakchatvereisten te voldoen.

Spraakchat is alleen beschikbaar voor spelers die minstens 13 jaar oud zijn en hun account hebben geverifieerd via een telefoonnummer of een door de overheid uitgegeven ID, afhankelijk van hun land. Voor een volledige lijst van de verificatievereisten per land, zie [Spraakchat](/docs/nl-nl/chat/voice-chat) .

## [Configureer instellingen](#configureer-instellingen)[](#configureer-instellingen)

Om teamchat, push-to-chat of tijdgebonden chat correct te laten werken, moet je [je spraakchatconfiguratie instellen](/docs/nl-nl/chat/voice-chat#stemchat-inschakelen)  om spraakchat in te schakelen en de juiste audio-objecten te creëren die nodig zijn om audio op te vangen en uit te zenden binnen de 3D-omgeving.

Wanneer spelers je game betreden, zorgt je spraakchatconfiguratie nu voor:

-

Staat spraakgeschikte spelers toe om hun microfoons te gebruiken.

-

Creëert en plaatst een [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  object onder elk spraakgeschikt [Player](/docs/nl-nl/reference/engine/classes/Player)  object.

-

Creëert en plaatst een [AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter)  object onder elk spraakgeschikt [Player.Character](/docs/nl-nl/reference/engine/classes/Player#Character) .

-

Creëert en plaatst een [AudioListener](/docs/nl-nl/reference/engine/classes/AudioListener)  onder de [Workspace.CurrentCamera](/docs/nl-nl/reference/engine/classes/Workspace#CurrentCamera) .

De volgende secties beschrijven drie unieke spraakchatconfiguraties met behulp van deze instellingen. Terwijl je het voorbeeld [Gingerbread Island - Spraakchat](https://www.roblox.com/games/91891961746476/Gingerbread-Island-Voice-Chat)  plaatsbestand volgt, kun je het overeenkomstige uitgeschakelde script in het Explorer  venster inschakelen om hun gedrag te testen. Om ervoor te zorgen dat elk script correct werkt, zorg ervoor dat je het script weer uitschakelt voordat je verdergaat naar de volgende configuratie .

 ![Uitgeschakelde scripts in het Explorer venster](https://prod.docsiteassets.roblox.com/assets/tutorials/add-voice-chat/DisabledScripts.jpg)

## [Voeg teamchat toe](#voeg-teamchat-toe)[](#voeg-teamchat-toe)

Teamchat  is een spraakchatconfiguratie waarin alleen spelers van hetzelfde team met elkaar kunnen spreken of elkaar kunnen horen in een game. Het integreren van teamchat in je gameplay is nuttig wanneer je wilt dat spelers samenwerken en strategiseren om problemen in het spel op te lossen, zoals het coördineren van informatie over de posities van het vijandige team, middelen en opdrachten.

Om de team spraakchat in het voorbeeld [Gingerbread Island - Spraakchat](https://www.roblox.com/games/91891961746476/Gingerbread-Island-Voice-Chat)  plaatsbestand te recreëren:

1.

In het Explorer  venster, voeg een Script  toe aan ServerScriptService .

2.

Hernoem het script naar TeamChat , en plak de volgende code in het script:

```

local Teams = game:GetService("Teams")

local Players = game:GetService("Players")

local redTeam = Instance.new("Team", Teams)

redTeam.TeamColor = BrickColor.new("Bright red")

redTeam.AutoAssignable = true

redTeam.Name = "Rood Team"

local blueTeam = Instance.new("Team", Teams)

blueTeam.TeamColor = BrickColor.new("Bright blue")

blueTeam.AutoAssignable = true

blueTeam.Name = "Blauw Team"

local function getUserIds(team : Team) : {number}

    local userIds = {}

    for _, player : Player in team:GetPlayers() do

 	   table.insert(userIds, player.UserId)

    end

    return userIds

end

local function getDevices(team : Team) : {AudioDeviceInput}

    local devices = {}

    for _, player : Player in team:GetPlayers() do

 	   local device : AudioDeviceInput = player:FindFirstChild("AudioDeviceInput")

 	   if not device then

 		   continue

 	   end

 	   table.insert(devices, device)

    end

    return devices

end

local function updateTeam(team : Team)

    local users = getUserIds(team)

    for _, device in getDevices(team) do

 	   device.AccessType = Enum.AccessModifierType.Allow

 	   device:SetUserIdAccessList(users)

    end

end

local function onDeviceAdded(device : AudioDeviceInput)

    local player : Player = device.Parent

    if player.Team then

 	   updateTeam(player.Team)

    end

end

local function onPlayerAdded(player : Player)

    local device = player:FindFirstChild("AudioDeviceInput")

    if device then

 	   onDeviceAdded(device)

    end

    player.ChildAdded:Connect(function(child)

 	   if child.Name == "AudioDeviceInput" then

 		   onDeviceAdded(child)

 	   end

    end)

end

updateTeam(blueTeam)

updateTeam(redTeam)

for _, player in Players:GetPlayers() do

    onPlayerAdded(player)

end

Players.PlayerAdded:Connect(onPlayerAdded)

blueTeam.PlayerAdded:Connect(function() updateTeam(blueTeam) end)

blueTeam.PlayerRemoved:Connect(function() updateTeam(blueTeam) end)

redTeam.PlayerAdded:Connect(function() updateTeam(redTeam) end)

redTeam.PlayerRemoved:Connect(function() updateTeam(redTeam) end)

```

Code uitleg

Het script begint met het verkrijgen van de [Teams](/docs/nl-nl/reference/engine/classes/Teams)  en [Players](/docs/nl-nl/reference/engine/classes/Players)  services, zodat het hun standaardfunctionaliteit kan gebruiken om spelers in teams in te delen zodra ze de game betreden. Bijvoorbeeld, zonder extra scriptinginspanningen, beheert de [Teams](/docs/nl-nl/reference/engine/classes/Teams)  service acties zoals:

-

Spelers gelijkmatig indelen en balanceren in elk team.

-

Spelers onder hun team op het leaderboard groeperen.

-

Speler namen in de 3D-ruimte tinten naar hun bijbehorende teamkleur.

Met deze service creëert het script twee verschillende [Team](/docs/nl-nl/reference/engine/classes/Team)  objecten met verschillende [Color](/docs/nl-nl/reference/engine/classes/Team#Color)  eigenschapswaarden om elk team te vertegenwoordigen: helder rood  voor het ene team en helder blauw  voor het andere.

Het script definieert vervolgens drie functies waar het grootste deel van het werk plaatsvindt voor het instellen van de team spraakchatconfiguratie:

-

getUserIds  - Retourneert een array van userIDs voor alle spelers in een team.

-

getDevices  - Retourneert een array van [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  objecten voor alle spelers in een team. Elk Class. AudioDeviceInput  object vertegenwoordigt de fysieke microfoon  van een speler in de echte wereld.

-

updateTeam  - Haalt alle userIDs op van getUserIds , doorloopt de [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  objecten van getDevices , stelt hun [Enum.AccessModifierType](/docs/nl-nl/reference/engine/enums/AccessModifierType)  eigenschap in op Allow  zodat alleen de userIDs in elk team zijn toegestaan om de microfoons van hun teamgenoten te horen, en werkt vervolgens de SetUserIdAccessList  bij met de userIDs van het team.

De rest van het script regelt hoe deze functies en gebeurtenislijsten samenwerken:

-

Wanneer een nieuwe speler de game betreedt, controleert het script of de speler een microfoon heeft en werkt hun team bij.

-

Wanneer het script een nieuw [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  object detecteert, roept het updateTeam  aan voor hun respectieve rode of blauwe team.

-

Terwijl spelers de game betreden of verlaten, verbindt het script zich met de PlayerAdded  en PlayerRemoved  gebeurtenissen om de instellingen van elk team bij te werken.

3.

Speel de game met een paar vrienden om te verifiëren dat teamgenoten van elk team alleen elkaar kunnen horen via spraakchat.

## [Voeg push-to-chat toe](#voeg-push-to-chat-toe)[](#voeg-push-to-chat-toe)

Push-to-chat  is een spraakchatconfiguratie waarin spelers alleen hun microfoon kunnen activeren binnen een game terwijl ze een specifieke knop op hun apparaat indrukken en vasthouden. Het integreren van push-to-chat in je gameplay is nuttig wanneer je wilt dat spelers meer privacy en controle hebben over wanneer ze gehoord willen worden boven andere spelers en omgevingsgeluiden.

Om de push-to-voice chat in het voorbeeld [Gingerbread Island - Spraakchat](https://www.roblox.com/games/91891961746476/Gingerbread-Island-Voice-Chat)  plaatsbestand te recreëren:

1.

In het Explorer  venster, voeg een Script  toe aan ReplicatedStorage .

2.

In het Properties  venster, stel RunContext  in op Client  zodat het script alleen de microfoon van de lokale speler controleert.

3.

Hernoem het script naar PushToChat , en plak de volgende code in het script:

```

local Players = game:GetService("Players")

local UserInputService = game:GetService("UserInputService")

local audioIn: AudioDeviceInput = Players.LocalPlayer:WaitForChild("AudioDeviceInput")

local pushToTalkKey = Enum.KeyCode.V

audioIn.Muted = true

UserInputService.InputBegan:Connect(function(input: InputObject)

    if input.KeyCode == pushToTalkKey then

        audioIn.Muted = false

    end

end)

UserInputService.InputEnded:Connect(function(input: InputObject)

    if input.KeyCode == pushToTalkKey then

        audioIn.Muted = true

    end

end)

```

Code uitleg

Het script begint met het verkrijgen van:

-

De [Players](/docs/nl-nl/reference/engine/classes/Players)  service zodat het alle spelers binnen de game kan refereren.

-

De [UserInputService](/docs/nl-nl/reference/engine/classes/UserInputService)  service zodat het kan controleren wanneer een speler knoppen op hun apparaat indrukt.

-

Het [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  object van de lokale speler, of de fysieke microfoon op hun apparaat.

Het script stelt vervolgens:

-

De V  toets in als de knop die de speler moet indrukken en vasthouden om in hun microfoon te spreken.

-

Het dempen van de microfoon van de speler.

De rest van het script stelt twee gebeurtenislijsten in voor InputBegan  en InputEnded  van [UserInputService](/docs/nl-nl/reference/engine/classes/UserInputService) . Wanneer ze de V  toets indrukken, dempt het InputBegan  evenement de microfoon van de speler niet meer, en wanneer ze de V  toets loslaten, dempt het InputEnded  evenement hun microfoon weer.

4.

Speel de game om te verifiëren dat spelers elkaar alleen kunnen horen via spraakchat wanneer ze de V  toets indrukken.

## [Voeg tijdgebonden chat toe](#voeg-tijdgebonden-chat-toe)[](#voeg-tijdgebonden-chat-toe)

Tijdgebonden chat  is een spraakchatconfiguratie waarin spelers alleen gedurende een bepaalde tijd met elkaar kunnen spreken en elkaar kunnen horen. Het integreren van tijdgebonden chat in je gameplay is nuttig wanneer je wilt dat spelers zorgvuldig plannen hoe ze met elkaar communiceren tijdens specifieke fasen, zoals tijdens ronde-gebaseerde discussies of na cutscenes.

Om de tijdgebonden spraakchat in het voorbeeld [Gingerbread Island - Spraakchat](https://www.roblox.com/games/91891961746476/Gingerbread-Island-Voice-Chat)  plaatsbestand te recreëren:

1.

In het Explorer  venster, voeg een Script  toe aan ServerScriptService .

2.

Hernoem het script naar TimeBasedChat , en plak de volgende code in het script:

```

local Players = game:GetService("Players")

local muteAll = false

local function toggleMuteAll()

    muteAll = not muteAll

    for _, player in Players:GetPlayers() do

 	   local device : AudioDeviceInput = player:FindFirstChild("AudioDeviceInput")

 	   if not device then

 		   continue

 	   end

 	   device.Muted = muteAll

    end

end

while true do

    task.wait(15) -- elke 15 seconden

    toggleMuteAll() -- ofwel mensen toestaan om te spreken, of ze verhinderen om te spreken

end

```

Code uitleg

Dit script begint met het verkrijgen van de [Players](/docs/nl-nl/reference/engine/classes/Players)  service zodat het zijn functionaliteit kan gebruiken om alle spelers in de game te beheren. Het stelt vervolgens een vlag muteAll  in op false , die de volgende toggleMuteAll  functie gebruikt om spraakchat in en uit te schakelen.

Laten we de toggleMuteAll  functie bekijken:

-

Het begint met het doorlopen van alle spelers in de game met behulp van [Players.GetPlayers](/docs/nl-nl/reference/engine/classes/Players#GetPlayers) .

-

Voor elke speler controleert het of deze een kind [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  object heeft, of de fysieke microfoon op hun apparaat.

-

Als ze dat hebben, stelt de functie de [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  object's [Muted](/docs/nl-nl/reference/engine/classes/AudioDeviceInput#Muted)  eigenschap in op de waarde van muteAll . Bijvoorbeeld, als muteAll  true  is, is de microfoon van de speler uitgeschakeld, en als muteAll  false  is, is de microfoon van de speler ingeschakeld.

Het script gaat vervolgens in een oneindige lus, wacht 15 seconden om alle [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  objecten te dempen en weer in te schakelen.

3.

Speel de game om te verifiëren dat spelers elkaar alleen kunnen horen via spraakchat in intervallen van 15 seconden.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
