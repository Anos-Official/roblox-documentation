<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/gameplay-scripting/spawn-respawn -->

Spawnen en respawnen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Spawnen en respawnen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Spawnen  is het proces van het creëren van een object of karakter in een spel, en respawnen  is het proces van het opnieuw toevoegen van een object of karakter aan een spel nadat ze aan een verwijderingsvoorwaarde voldoen, zoals het bereiken van nul gezondheid van een karakter of van de kaart vallen. Beide processen zijn belangrijk omdat ze ervoor zorgen dat spelers zich bij je spel kunnen voegen en kunnen blijven spelen om hun vaardigheden te verbeteren.

Met behulp van het [voorbeeld laser tag-spel](https://www.roblox.com/games/14817965191/Laser-Tag-1A)  als referentie, leert deze sectie van de tutorial je hoe je de ingebouwde functies van Roblox kunt gebruiken en aanpassen om spawnen en respawnen te beheren, inclusief scriptingrichtlijnen over:

-

Het configureren van spawnlocaties zodat spelers alleen in de spawnzone van hun team kunnen spawnen.

-

Nieuwe spelers en hun karakter aan de ronde toevoegen wanneer ze zich bij het spel voegen.

-

Het aanpassen van krachtvelden die schade voorkomen terwijl spelers spawnen en respawnen.

-

Het beheren van de clientstatus zodat de gameplay op het juiste moment correct werkt.

-

Het respawnen van karakters nadat ze uit de ronde zijn getagd.

-

Het uitvoeren van kleine, diverse acties die cruciaal zijn voor het instellen van gameplay- en karakterparameters.

Deze sectie bevat veel scriptinginhoud, maar in plaats van alles vanaf nul te schrijven bij het maken van een spel, moedigt het je aan om bestaande componenten te benutten, snel te itereren en uit te zoeken welke systemen een aangepaste implementatie nodig hebben om aan jouw visie te voldoen. Nadat je deze sectie hebt voltooid, leer je hoe je ronde-gebaseerde gameplay implementeert die punten bijhoudt, de status van spelers monitort en de resultaten van de ronde weergeeft.

## [Configureer spawnlocaties](#configureer-spawnlocaties)[](#configureer-spawnlocaties)

Als je het spel nu zou testen, zouden alle spelers willekeurig spawnen bij het [SpawnLocation](/docs/nl-nl/reference/engine/classes/SpawnLocation)  object in de spawnzone van het groene team, of het [SpawnLocation](/docs/nl-nl/reference/engine/classes/SpawnLocation)  object in de spawnzone van het roze team. Dit presenteert een gameplayprobleem waarbij spelers elkaar binnen elke spawnzone kunnen taggen zodra het krachtveld van hun tegenstander verdwijnt.

Om dit probleem te bestrijden, configureert het voorbeeld laser tag-spel beide spawnlocaties met een [Neutral](/docs/nl-nl/reference/engine/classes/SpawnLocation#Neutral)  eigenschap ingesteld op false  om te voorkomen dat de spelers van het tegenovergestelde team in de verkeerde spawnzone spawnen, en een [TeamColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#TeamColor)  eigenschap ingesteld op de overeenkomstige [Team.Color](/docs/nl-nl/reference/engine/classes/Team#Color)  waarde van [Teamkleuren toewijzen](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/create-teams#teamkleuren-toewijzen)  in de vorige sectie van de tutorial:

-

TeamASpawn  – De spawnlocatie in de spawnzone van het groene team met een [TeamColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#TeamColor)  eigenschap ingesteld op Mint .

-

TeamBSpawn  – De spawnlocatie in de spawnzone van het roze team met een [TeamColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#TeamColor)  eigenschap ingesteld op Carnation Pink .

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Spawn-Respawn/TeamASpawn.jpg) TeamASpawn

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Spawn-Respawn/TeamBSpawn.jpg) TeamBSpawn

De [SpawnLocation.TeamColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#TeamColor)  eigenschap is anders dan de [SpawnLocation.BrickColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#BrickColor)  en [SpawnLocation.Color](/docs/nl-nl/reference/engine/classes/SpawnLocation#Color)  eigenschappen die de visuele kleur van het spawnobject vertegenwoordigen en niet gerelateerd zijn aan teamfunctionaliteit.

Wanneer een speler zich bij het spel voegt, controleert ServerScriptService  ⟩ Gameplay  ⟩ Rounds  ⟩ spawnPlayersInMap  hoeveel spelers er al op elk team zijn, en retourneert dan het team met de minste spelers.

spawnPlayersInMap

```

local function getSmallestTeam(): Team

	local teams = Teams:GetTeams()

	-- Sorteer teams in oplopende volgorde van klein naar groot

	table.sort(teams, function(teamA: Team, teamB: Team)

		return #teamA:GetPlayers() < #teamB:GetPlayers()

	end)

	-- Retourneer het kleinste team

	return teams[1]

end

```

Zodra het weet welk team de minste spelers heeft, sorteert het de speler in dat team, stelt hun [Player.Neutral](/docs/nl-nl/reference/engine/classes/Player#Neutral)  eigenschap in op false  zodat de speler alleen kan spawnen en respawnen naar de spawnlocatie van hun team, en stelt dan hun PlayerState  in op SelectingBlaster , waar je later in de tutorial meer over zult leren.

spawnPlayersInMap

```

local function spawnPlayersInMap(players: { Player })

	for _, player in players do

		player.Team = getSmallestTeam()

		player.Neutral = false

		player:SetAttribute(PlayerAttribute.playerState, PlayerState.SelectingBlaster)

		task.spawn(function()

			player:LoadCharacter()

		end)

	end

end

```

Als je Workspace  ⟩ World  ⟩ Map  ⟩ Spawns  bekijkt, zie je dat er nog een spawnlocatie in de kaart is: NeutralSpawn . Deze spawnlocatie is uniek van de anderen omdat het geen [TeamColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#TeamColor)  eigenschap heeft die is ingesteld op een van de twee teams in het spel; in plaats daarvan heeft deze spawnlocatie een [Neutral](/docs/nl-nl/reference/engine/classes/SpawnLocation#Neutral)  eigenschap die verandert afhankelijk van of er een ronde actief is.

Bijvoorbeeld, als de ronde actief is, wordt de [Neutral](/docs/nl-nl/reference/engine/classes/SpawnLocation#Neutral)  eigenschap ingesteld op false  zodat spawnPlayersInMap  spelers in teams kan sorteren en ze in de arena kan spawnen. Als de ronde echter niet actief is, zoals de tijd tussen de ene ronde en de volgende, wordt de [Neutral](/docs/nl-nl/reference/engine/classes/SpawnLocation#Neutral)  eigenschap ingesteld op true  zodat spelers daar kunnen spawnen ongeacht hun teamstatus. Dit proces maakt de Neutral  spawnlocatie een functionele lobby.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Spawn-Respawn/Neutral.jpg) Neutral

Om dit te demonstreren, als je ServerScriptService  ⟩ Gameplay  ⟩ Rounds  ⟩ SpawnPlayersInLobby  bekijkt, dat aan het einde van een ronde draait, zie je dat voor elke speler die in de players: { Player }  tabel wordt doorgegeven, het script:

-

Stelt hun [Player.Neutral](/docs/nl-nl/reference/engine/classes/Player#Neutral)  eigenschap in op true om automatisch hun [Player.Team](/docs/nl-nl/reference/engine/classes/Player#Team)  op nil  in te stellen, zodat de speler kan respawnen in de lobby wanneer er geen actieve ronde is, aangezien de [Neutral](/docs/nl-nl/reference/engine/classes/SpawnLocation#Neutral)  eigenschap van de spawnlocatie ook is ingesteld op true .

-

Verandert hun PlayerState  naar InLobby  om het blaster van de speler en de visuals van de eerste persoon UI te verwijderen.

Voor meer informatie over de neutrale spawnzone en de functionaliteit ervan voor elke ronde, zie [Rondes toevoegen](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/add-rounds)  in de volgende sectie van de tutorial.

spawnPlayersInLobby

```

local function spawnPlayersInLobby(players: { Player })

	for _, player in players do

		player.Neutral = true

		player:SetAttribute(PlayerAttribute.playerState, PlayerState.InLobby)

		task.spawn(function()

			player:LoadCharacter()

		end)

	end

end

```

## [Nieuwe spelers verbinden](#nieuwe-spelers-verbinden)[](#nieuwe-spelers-verbinden)

Luau-code in Studio is vaak gebeurtenisgestuurd, wat betekent dat scripts luisteren naar gebeurtenissen van een Roblox-service en vervolgens een functie aanroepen als reactie. Bijvoorbeeld, wanneer nieuwe spelers aan een multiplayer-spel worden toegevoegd, moet er een gebeurtenis zijn die alles afhandelt wat nodig is voor spelers om succesvol verbinding te maken. In het voorbeeld laser tag-spel is deze overeenkomstige gebeurtenis Players.PlayerAdded:Connect .

Players.PlayerAdded:Connect  maakt deel uit van meerdere scripts in het spel. Als je de Ctrl/Cmd+Shift+F  sneltoets gebruikt en zoekt naar Players.PlayerAdded:Connect , bieden de resultaten een goed startpunt voor het begrijpen van de initiële setup van het spel.

 ![Studio's Find All-venster met de Players.PlayerAdded-resultaten gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Spawn-Respawn/Find-All.png)

Om dit te demonstreren, open ServerScriptService  ⟩ SetupHumanoid . Het onderscheid tussen [Player](/docs/nl-nl/reference/engine/classes/Player)  en [Character](/docs/nl-nl/reference/engine/classes/Player#Character)  is cruciaal voor het begrijpen van dit script:

-

Een speler  is een verbonden client, en een karakter  is een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  model.

-

Spelers moeten een blaster kiezen en aan het leaderboard worden toegevoegd. Karakters moeten spawnen en een blaster ontvangen.

SetupHumanoid  controleert onmiddellijk of de speler een karakter heeft (net aangesloten) of niet (is aan het respawnen). Nadat het er een heeft gevonden, roept het onCharacterAdded()  aan, krijgt het het [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  model van het karakter en geeft het door aan ServerScriptService  ⟩ SetupHumanoid  ⟩ setupHumanoidAsync  voor aanpassing. Nadat deze waarden zijn ingesteld, wacht het script vervolgens tot de gezondheid van het karakter op nul komt. Je leert later meer over respawnen in deze sectie van de tutorial.

setupHumanoidAsync

```

local function setupHumanoidAsync(player: Player, humanoid: Humanoid)

	humanoid.DisplayDistanceType = Enum.HumanoidDisplayDistanceType.Subject

	humanoid.NameDisplayDistance = 1000

	humanoid.HealthDisplayDistance = 1000

	humanoid.NameOcclusion = Enum.NameOcclusion.OccludeAll

	humanoid.HealthDisplayType = Enum.HumanoidHealthDisplayType.AlwaysOn

	humanoid.BreakJointsOnDeath = false

	humanoid.Died:Wait()

	onHumanoidDied(player, humanoid)

end

```

De belangrijke opmerking bij dit script is dat de eigenschappen volledig optioneel zijn, wat betekent dat als je de eerste zes regels van de functie verwijdert, het spel nog steeds goed werkt. In plaats van functionele vereisten, stelt elke eigenschap je in staat om ontwerpbeslissingen te nemen die voldoen aan je gameplaydoelen. Bijvoorbeeld:

-

Als je wilt dat de namen van karakters op kortere afstanden worden weergegeven, verlaag je de waarde van [Humanoid.NameDisplayDistance](/docs/nl-nl/reference/engine/classes/Humanoid#NameDisplayDistance) .

-

Als je wilt dat de gezondheid van een karakter alleen wordt weergegeven als deze onder de 100% ligt, stel je [Humanoid.HealthDisplayType](/docs/nl-nl/reference/engine/classes/Humanoid#HealthDisplayType)  in op DisplayWhenDamaged .

-

Als je wilt dat karakters uit elkaar vallen wanneer hun gezondheid op 0 komt, stel je [Humanoid.BreakJointsOnDeath](/docs/nl-nl/reference/engine/classes/Humanoid#BreakJointsOnDeath)  in op True .

Als je de waarden van deze eigenschappen wijzigt, is het belangrijk om te playtesten zodat je de impact van je nieuwe instellingen kunt zien. Je kunt recreëren wat spelers ervaren in een [multi‑client simulatie](/docs/nl-nl/studio/testing-modes#multi-client-simulatie)  door ten minste twee karakters te selecteren in een Server & Clients  playtest vanuit de mezzanine.

 ![Server & Clients optie in de dropdown voor testmodi van de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Server-Clients.png)

Probeer enkele van deze waarden te wijzigen en te playtesten met meerdere spelers om te zien hoe ze de gameplay beïnvloeden. Hoe zou de strategie van spelers kunnen veranderen als je ervoor kiest om de gezondheidsweergave te verbergen?

Een ander voorbeeld van de Players.PlayerAdded:Connect  gebeurtenis is in ServerScriptService  ⟩ PlayerStateHandler . Net als in het vorige voorbeeld controleert PlayerStateHandler  onmiddellijk op een karakter. Als de speler niet in de lobby is, stelt het script een spelerattribuut in op de SelectingBlaster  status, de initiële status voor een ronde waarin spelers kunnen kiezen uit een van de twee verschillende blastertypes nadat ze in de arena zijn gespawnd. Deze status omvat ook een krachtveld dat voorkomt dat spelers schade oplopen terwijl ze hun keuze maken.

PlayerStateHandler

```

local function onPlayerAdded(player: Player)

	player.CharacterAdded:Connect(function()

		if not player.Neutral then

			player:SetAttribute(PlayerAttribute.playerState, PlayerState.SelectingBlaster)

			onPlayerStateChanged(player, PlayerState.SelectingBlaster)

		end

	end)

```

Een bepaalde variabele in PlayerStateHandler  verdient bespreking: attributeChangedConnectionByPlayer . Deze tabel slaat alle spelers en hun [Connections](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)  op naar de GetAttributeChangedSignal . De reden voor het opslaan van deze verbinding in een tabel is zodat PlayerStateHandler  deze kan ontkoppelen  wanneer de speler het spel verlaat. Dit proces dient als een soort geheugenbeheer om te voorkomen dat het aantal verbindingen in de loop van de tijd steeds groter wordt.

PlayerStateHandler

```

local attributeChangedConnectionByPlayer = {}

local function onPlayerAdded(player: Player)

	-- Behandel alle toekomstige updates van de spelerstatus

	attributeChangedConnectionByPlayer[player] = player

		:GetAttributeChangedSignal(PlayerAttribute.playerState)

		:Connect(function()

			local newPlayerState = player:GetAttribute(PlayerAttribute.playerState)

			onPlayerStateChanged(player, newPlayerState)

		end)

end

-- Ontkoppel van de attribuutveranderingsverbinding wanneer de speler vertrekt

local function onPlayerRemoving(player: Player)

	if attributeChangedConnectionByPlayer[player] then

		attributeChangedConnectionByPlayer[player]:Disconnect()

		attributeChangedConnectionByPlayer[player] = nil

	end

end

```

Je kunt zien dat beide verbonden functies in onPlayerAdded()  onPlayerStateChanged()  aanroepen. Tijdens de initiële setup nadat een speler in een team is gesorteerd, stelt onPlayerAdded()  PlayerState  in op SelectingBlaster , zodat de eerste if -verklaring als onwaar wordt geëvalueerd en de BlasterState  uitschakelt. In de latere [Implementeer blasters](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/implement-blasters)  sectie van de tutorial, leer je meer details over dit proces.

PlayerStateHandler

```

local function onPlayerStateChanged(player: Player, newPlayerState: string)

	-- Blasterstatus is 'Klaar' alleen als de spelerstatus 'Spelen' is

	local newBlasterState = if newPlayerState == PlayerState.Playing then BlasterState.Ready else BlasterState.Disabled

	-- Plan de logica voor het vernietigen van het krachtveld wanneer de speler begint te spelen

	if newPlayerState == PlayerState.Playing then

		scheduleDestroyForceField(player)

	end

	player:SetAttribute(PlayerAttribute.blasterStateServer, newBlasterState)

end

```

Als je breakpoints toevoegt of zelfs gewoon een print() -instructie, kun je zien dat onPlayerStateChanged()  vaak door het spel wordt aangeroepen: zoals tijdens de initiële setup van een ronde, om zichzelf op het hoofdcodepad in te stellen, nadat de speler een blaster heeft gekozen, en wanneer de speler terugkeert naar de lobby, of de Neutral  spawnlocatie. Bovendien, nadat de speler een blaster heeft gekozen, stelt ServerScriptService  ⟩ BlasterSelectedHandler  de PlayerState  in op Playing , en kan PlayerStateHandler  eindelijk het krachtveld verwijderen door scheduleDestroyForceField()  aan te roepen.

## [Pas krachtvelden aan](#pas-krachtvelden-aan)[](#pas-krachtvelden-aan)

In plaats van een aangepaste implementatie te gebruiken, gebruikt het voorbeeld laser tag-spel de ingebouwde [ForceField](/docs/nl-nl/reference/engine/classes/ForceField)  klasse van Studio om te voorkomen dat spelers schade oplopen terwijl ze hun blaster selecteren. Dit zorgt ervoor dat de enige vereiste voor spelers om met een krachtveld te spawnen is dat ze spawnlocaties moeten hebben met een [SpawnLocation.Duration](/docs/nl-nl/reference/engine/classes/SpawnLocation#Duration)  eigenschap die groter is dan 0. Het voorbeeld gebruikt een willekeurige waarde van 9.999 om krachtvelden in te schakelen, en beheert de werkelijke duur programmatisch in ReplicatedStorage  ⟩ ForceFieldClientVisuals .

Net als setupHumanoidAsync  zijn de meeste regels in ForceFieldClientVisuals  optioneel. Bijvoorbeeld, als je de inhoud van de functie commentarieert zoals het volgende script doet, gebruikt het spel het standaard sprankelende krachtveld in plaats van het hexagonale script in StarterGui  ⟩ ForceFieldGui .

Commenting Out Properties in ForceFieldClientVisuals

```

local function onCharacterAddedAsync(character: Model)

    -- local forceField = character:WaitForChild("ForceField", 3)

    -- if not forceField then

    -- return

    -- end

    -- forceField.Visible = false

    -- localPlayer.PlayerGui:WaitForChild("ForceFieldGui").Enabled = true

    -- forceField.Destroying:Wait()

    -- localPlayer.PlayerGui.ForceFieldGui.Enabled = false

end

```

Omdat het aangepaste krachtveld een GUI is in plaats van een nieuwe [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter) , beïnvloedt het ForceFieldClientVisuals  script alleen de visuals van de eerste persoon voor elke speler, niet  de visuals van de derde persoon wanneer spelers naar andere spelers kijken. De visuals van de derde persoon behouden het standaard Roblox uiterlijk. Voor meer informatie over het aanpassen van krachtvelden, zie [ForceField.Visible](/docs/nl-nl/reference/engine/classes/ForceField#Visible) .

![De visuals van het krachtveld in de eerste persoon omvatten een futuristisch hexagonaal raster aan de rand van het scherm.](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Spawn-Respawn/First-Person-Visuals.png) Visuals van het krachtveld in de eerste persoon

![De visuals van het krachtveld in de derde persoon omvatten een blauwe sprankelende orb rond de speler die in het spel spawnt.](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Spawn-Respawn/Third-Person-Visuals.png) Visuals van het krachtveld in de derde persoon

Krachtvelden zijn nuttig omdat ze spelers voldoende tijd geven tussen spawnen en respawnen zonder zich zorgen te maken over vijandige spelers, maar uiteindelijk moeten ze verdwijnen voor de hoofd gameplay van laser tag. Het script dat de verwijdering van krachtvelden beheert, bevindt zich in ReplicatedStorage  ⟩ scheduleDestroyForceField , en controleert op drie unieke voorwaarden:

-

Nadat spelers een blaster hebben geselecteerd, moeten krachtvelden lang genoeg duren om spelers in staat te stellen zich aan hun omgeving aan te passen.

-

Tijdens deze acclimatisatietijd kunnen krachtvelden geen voordeel zijn, dus ze moeten verdwijnen op het moment dat een speler hun blaster afvuurt.

-

Krachtvelden moeten verdwijnen wanneer spelers hun karakters resetten, hetzij voordat ze afvuren of voordat het krachtveld verloopt.

Elke van deze controles in het scheduleDestroyForceField  script roept endForceField()  aan voor deze voorwaarden.

scheduleDestroyForceField

```

-- Eindig krachtveld als speler afvuurt

local blasterStateAttribute = getBlasterStateAttribute()

attributeChangedConnection = player:GetAttributeChangedSignal(blasterStateAttribute):Connect(function()

	local currentBlasterState = player:GetAttribute(blasterStateAttribute)

	if currentBlasterState == BlasterState.Blasting then

		endForceField()

	end

end)

-- Eindig krachtveld als speler reset

characterRespawnedConnection = player.CharacterRemoving:Connect(endForceField)

-- Eindig krachtveld na 8 seconden

task.delay(MAX_FORCE_FIELD_TIME, endForceField)

```

endForceField()  bevat een schijnbaar vreemde if -verklaring rond de forceFieldEnded  boolean. Omdat de controles sequentieel worden uitgevoerd, kan het script de endForceField()  functie twee of zelfs drie keer aanroepen. De forceFieldEnded  boolean zorgt ervoor dat de functie slechts één keer probeert een krachtveld te vernietigen.

scheduleDestroyForceField

```

local function endForceField()

	if forceFieldEnded then

		return

	end

	forceFieldEnded = true

	attributeChangedConnection:Disconnect()

	characterRespawnedConnection:Disconnect()

	destroyForceField(player)

end

```

Om meer te leren over het omgaan met dit soort situaties, zie [Debounce Patterns](/docs/nl-nl/scripting/debounce) .

## [Beheer clientstatus](#beheer-clientstatus)[](#beheer-clientstatus)

Hoewel het grootste deel van deze sectie zich richt op ServerScriptService  ⟩ PlayerStateHandler , is er een ander script met dezelfde naam in ReplicatedStorage . De reden voor de splitsing is de client-serverarchitectuur:

-

De client moet informatie over de spelerstatus begrijpen zodat deze in realtime op de juiste manier kan reageren, zoals het weergeven van de juiste gebruikersinterface-elementen, of het mogelijk maken voor spelers om te bewegen en af te vuren.

-

De server heeft al deze informatie nodig zodat deze exploits kan voorkomen. Bijvoorbeeld, de server heeft ook de spelerstatus nodig om acties uit te voeren zoals het spawnen en uitrusten van karakters, het uitschakelen van krachtvelden en het weergeven van een leaderboard. Dit is waarom dit script in ReplicatedStorage  staat en niet in een puur client-side locatie.

Om deze kernlogica te zien, bekijk je het volgende script in ReplicatedStorage  ⟩ PlayerStateHandler  dat de huidige status van de gebruiker verifieert en vervolgens de juiste functie aanroept die de bijbehorende acties voor die status afhandelt.

PlayerStateHandler

```

local function onPlayerStateChanged(newPlayerState: string)

	if newPlayerState == PlayerState.SelectingBlaster then

		onSelectingBlaster()

	elseif newPlayerState == PlayerState.Playing then

		onPlaying()

	elseif newPlayerState == PlayerState.TaggedOut then

		onTaggedOut()

	elseif newPlayerState == PlayerState.InLobby then

		onInLobby()

	else

		warn(`Ongeldige spelerstatus ({newPlayerState})`)

	end

end

```

Alle gebeurtenisreacties zijn logisch gegroepeerd in dit script omdat ze vergelijkbaar gedrag vereisen bij het in- of uitschakelen van spelersbesturing, camerabeweging en welke UI-laag zichtbaar is. Bijvoorbeeld, tijdens de blasterselectie moeten spelers zowel onkwetsbaar zijn als niet kunnen bewegen. De server beheert al het krachtveld, maar de client beheert de beweging. Om dit te demonstreren, als je de logica voor de onSelectingBlaster()  functie controleert, kun je zien dat de client de beweging van de speler uitschakelt terwijl ze een blaster selecteren.

PlayerStateHandler

```

local function onSelectingBlaster()

	togglePlayerCamera(true)

	togglePlayerMovement(false)

	setGuiExclusivelyEnabled(playerGui.PickABlasterGui)

	localPlayer:SetAttribute(PlayerAttribute.blasterStateClient, BlasterState.Disabled)

end

```

De onPlaying()  functie is ook vrij eenvoudig. Het schakelt de beweging in, schakelt over naar de hoofd heads-up display (HUD), schakelt de blaster in en roept dezelfde krachtveld functie aan als de server.

PlayerStateHandler

```

local function onPlaying()

	togglePlayerMovement(true)

	setGuiExclusivelyEnabled(playerGui.HUDGui)

	localPlayer:SetAttribute(PlayerAttribute.blasterStateClient, BlasterState.Ready)

	scheduleDestroyForceField()

end

```

## [Respawn karakters](#respawn-karakters)[](#respawn-karakters)

Het voorbeeld laser tag-spel beheert het respawnen van karakters terug in een ronde via de onTaggedOut()  status in ReplicatedStorage  ⟩ PlayerStateHandler . Net als de onSelectingBlaster()  en onPlaying()  status, triggert onTaggedOut()  unieke gedragingen volgens de wijzigingen in het playerState  attribuut. Specifiek schakelt het de beweging van de speler uit, presenteert het de respawn UI en schakelt het de blaster uit.

PlayerStateHandler

```

local function onTaggedOut()

	-- Schakel besturing uit terwijl getagd

	togglePlayerMovement(false)

	togglePlayerCamera(false)

	setGuiExclusivelyEnabled(playerGui.OutStateGui)

	-- Schakel blaster uit terwijl getagd

	localPlayer:SetAttribute(PlayerAttribute.blasterStateClient, BlasterState.Disabled)

end

```

Als je dit gedrag wilt testen, kun je op Esc  drukken, naar het tabblad Instellingen  navigeren en vervolgens op de knop Reset Character  klikken. Merk op dat wanneer je het respawn-scherm activeert, je niet kunt bewegen, de camera niet kunt draaien of je blaster kunt afvuren.

![Roblox's instellingenmenu met de Reset Character-knop gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Spawn-Respawn/Reset-Character-Button.png) Reset Character-knop

![Het respawn-scherm verschijnt terwijl een speler terug in de ronde respawnt.](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Spawn-Respawn/Respawn-Screen.png) Respawn-scherm

Het is belangrijk op te merken dat dit script de karakters niet daadwerkelijk respawnt, het stopt ze gewoon met handelen en biedt visuele feedback aan spelers dat de server  hun karakters respawnt. Om dit te demonstreren, als je ServerScriptService  ⟩ SetupHumanoid  ⟩ setupHumanoidAsync  ⟩ onHumanoidDied  bekijkt, stelt het script PlayerState  in op TaggedOut  (in wezen de ReplicatedStorage  ⟩ PlayerStateHandler  notificerend), en voegt het enkele visuele indicatoren toe. De werkelijke logica van het respawnen is een ingebouwd Roblox-gedrag.

Wanneer spelers terug in de ronde respawnen, respawnen ze op de spawnlocatie van hun team volgens de [SpawnLocation.TeamColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#TeamColor)  eigenschap. Om de respawntijd aan te passen, kun je de volgende regel aan de bovenkant van SetupHumanoid  toevoegen. Voor meer informatie over deze techniek, zie [Players.RespawnTime](/docs/nl-nl/reference/engine/classes/Players#RespawnTime) .

SetupHumanoid

```

local Players = game:GetService("Players")

Players.RespawnTime = 10 -- nieuwe regel, in seconden

```

In een spel met een voortgangssysteem, zoals checkpoints, kun je [Player.RespawnLocation](/docs/nl-nl/reference/engine/classes/Player#RespawnLocation)  gebruiken om een exacte locatie op te geven waar spelers naartoe moeten respawnen nadat hun gezondheid op nul komt.

## [Diverse setup](#diverse-setup)[](#diverse-setup)

Als onderdeel van de initiële setup voert het voorbeeld laser tag-spel ook enkele kleine, maar cruciale stappen uit:

-

Het spel bevat een leeg script genaamd StarterPlayer  ⟩ StarterCharacterScripts  ⟩ Health  dat de standaard Roblox gezondheid regeneratie uitschakelt. Voor een uitleg van het gedrag van deze eigenschap, zie [Humanoid.Health](/docs/nl-nl/reference/engine/classes/Humanoid#Health) .

-

Het spel gebruikt een camera in de eerste persoon door de StarterPlayer.CameraMode.LockFirstPerson  eigenschap in te stellen. Merk op dat als je gebruikers wilt laten wisselen tussen eerste- en derdepersoonscamera's, je de eigenschap programmatisch moet wijzigen in plaats van deze slechts één keer in Studio in te stellen, en de besturing en UI moet aanpassen om rekening te houden met de verandering in perspectief.

-

Het spel gebruikt het ingebouwde Roblox leaderboard met de eenheid "punten", die spelers verdienen elke keer dat ze een andere speler taggen. Je kunt de configuratie zien in ServerScriptService  ⟩ SetupLeaderboard , maar [In-game Leaderboards](/docs/nl-nl/players/leaderboards)  biedt een volledig overzicht. Merk op dat onPlayerTagged  punten aan het leaderboard toevoegt, waar je meer over leert in [Rondes toevoegen](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/add-rounds)  en [Hits detecteren](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/detect-hits) .

Nu spelers kunnen spawnen, een blaster kiezen en deze vanuit een eerste-persoonsperspectief richten, leert de volgende sectie je over de scripts achter het creëren van ronde-gebaseerde gameplay.

[Volgende](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/add-rounds)[Vorige](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/create-teams)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
