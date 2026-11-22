<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/gameplay-scripting/add-rounds -->

Ronden toevoegen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Ronden toevoegen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Ronden toevoegen  stelt je in staat om gameplay te structureren in fasen met een duidelijk begin- en eindpunt, zodat spelers hun voortgang kunnen meten en periodiek de kans hebben op een gelijk speelveld. Dit is vooral belangrijk voor teamgebaseerde gameplay omdat het spelers de kans biedt om hun speelstijl aan te passen, afhankelijk van wie er in hun team zit tijdens die ronde.

Met behulp van het [voorbeeld laser tag spel](https://www.roblox.com/games/14817965191/Laser-Tag-1A)  als referentie, leert deze sectie van de tutorial je hoe je de ingebouwde functies van Roblox kunt gebruiken en aanpassen om elke ronde te structureren, inclusief scriptingrichtlijnen over:

-

Het beginnen van een ronde door individuele en teampunten te resetten, en vervolgens spelers naar hun team spawnzones te spawnen.

-

Het aanpassen van variabelen die het doel voor de ronde instellen bovenaan het scherm van elke speler.

-

Het bijhouden van de puntbijdragen van spelers voor hun teamscore.

-

Het activeren van unieke UI-schermen afhankelijk van of het team van de speler de ronde heeft gewonnen of verloren.

-

Het beëindigen van een ronde door spelers te ontkoppelen en hen in de neutrale lobby te spawnen.

Nadat je deze sectie hebt voltooid, leer je hoe je blastergedrag implementeert dat zowel nauwkeurig als bevredigend is voor spelers.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Adding-Rounds/Rounds-Diagram.png)

## [Start loop](#start-loop)[](#start-loop)

ServerScriptService  ⟩ Gameplay  ⟩ Rounds  behandelt de meeste logica voor het implementeren van ronden, en het begint met het aanroepen van de startRoundLoopAsync()  functie om het begin van een ronde loop te markeren. Terwijl spelers de lobby binnenkomen en wachten om in een team te worden ingedeeld, roept startRoundLoopAsync()  de resetScores()  functie aan in ServerScriptService  ⟩ Gameplay  ⟩ Scoring  om zowel het leaderboard als de teampunten te resetten.

Scoring

```

function Scoring.resetScores()

	for _, player in Players:GetPlayers() do

		player.leaderstats.Points.Value = 0

	end

	for _, team in Teams:GetTeams() do

		team:SetAttribute(GuiAttribute.teamPoints, 0)

	end

end

```

Nu iedereen begint met nul punten, stelt startRoundLoopAsync()  de Neutrale  spawnlocatie's [Neutral](/docs/nl-nl/reference/engine/classes/SpawnLocation#Neutral)  eigenschap in op false , zodat alleen spelers met dezelfde [Team.Color](/docs/nl-nl/reference/engine/classes/Team#Color)  eigenschap als de spawnlocatie's [TeamColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#TeamColor)  eigenschap daar kunnen spawnen. Omdat de spawnlocatie's [TeamColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#TeamColor)  eigenschap is ingesteld op wit  in plaats van de mint of carnation pink teams van het voorbeeld, voorkomt deze configuratie dat alle spelers daar kunnen spawnen of respawnen terwijl een ronde actief is.

Voor spelers die momenteel in de lobby zijn, geeft startRoundLoopAsync()  alle spelers die momenteel in het spel zijn door aan de spawnPlayersInMap  functie in ServerScriptService  ⟩ Gameplay  ⟩ Rounds  ⟩ spawnPlayersInMap  om iedereen in een team met ongeveer hetzelfde aantal spelers in te delen en in balans te brengen.

Voor nieuwe spelers die zich bij het spel voegen nadat de lobbygroep in een team is ingedeeld, luistert startRoundLoopAsync()  naar het Players.PlayerAdded:Connect  evenement, en roept vervolgens de spawnPlayersInMap  functie opnieuw aan om hen toe te voegen aan het team met het minste aantal spelers. Voor meer informatie over dit proces, zie [Configure Spawn Locations](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/spawn-respawn#configureer-spawnlocaties)  uit de vorige sectie Spawnen en Respawnen  van de tutorial.

Rounds

```

-- Spawn alle spelers in de map

		neutralSpawn.Neutral = false

		spawnPlayersInMap(Players:GetPlayers())

		-- Spawn nieuwe spelers in de map wanneer ze zich aanmelden

		local playerAddedConnection = Players.PlayerAdded:Connect(function(player: Player)

			spawnPlayersInMap({ player })

		end)

```

## [Stel doel in](#stel-doel-in)[](#stel-doel-in)

Nu elke speler in de arena met hun teamgenoten is, moet het spel instructies geven over wat te doen om succesvol te zijn binnen de ronde. Het voorbeeld laser tag spel pakt deze vereiste aan door een doelprompt bovenaan het scherm van elke speler te geven met duidelijke richtlijnen over wat het team moet doen om te winnen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Objective-UI.jpg)

Hoewel je meer kunt leren over hoe je de [Objective UI](/docs/nl-nl/tutorials/curriculums/user-interface-design/implement-designs-in-studio#doel-ui)  component kunt configureren en weergeven in het UI Curriculum, richt deze sectie zich op hoe je het doel als de ronde begint implementeert, te beginnen met hoe je het aantal punten instelt dat elk team nodig heeft om de ronde te voltooien.

Hoewel de doelprompt tijdens runtime spelers informeert dat ze drie punten moeten scoren om te winnen, als je de prompt in StarterGui  ⟩ HUDGui  bekijkt, zie je dat deze in plaats daarvan een configureerbare " %d " voor de puntwaarde bevat.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Adding-Rounds/Placeholder-Prompt.jpg)

" %d " is een placeholder-string die je op elk moment kunt verhogen of verlagen om aan je eigen gameplayvereisten te voldoen door de TEAM_SCORE_LIMIT  variabele in ReplicatedStorage  ⟩ TEAM_SCORE_LIMIT  bij te werken. Bijvoorbeeld, als je dit nummer zou instellen op een buitensporig hoog 200 , zou de prompt en de teampuntenteller dienovereenkomstig worden bijgewerkt.

TEAM_SCORE_LIMIT

```

local TEAM_SCORE_LIMIT = 200 -- bijgewerkte regel, zorg ervoor dat je het terugverandert

return TEAM_SCORE_LIMIT

```

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Adding-Rounds/Large-Prompt.jpg)

Deze eenvoudige variabele-update werkt tijdens runtime omdat wanneer de ronde begint, ReplicatedStorage  ⟩ HUDGuiSetup  ⟩ SetObjective  de TEAM_SCORE_LIMIT  module script vereist, zodat het de placeholder-string in het UI Objective's [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  object kan verwisselen.

TEAM_SCORE_LIMIT

```

local TEAM_SCORE_LIMIT = require(ReplicatedStorage.TEAM_SCORE_LIMIT)

local function setObjective(gui: ScreenGui)

	local bodyTextLabel = gui.Objective.ObjectiveDisplay.Body.BodyTextLabel

	bodyTextLabel.Text = bodyTextLabel.Text:format(TEAM_SCORE_LIMIT)

end

```

## [Volg punten](#volg-punten)[](#volg-punten)

Nu spelers een doel hebben voor de ronde, moet het spel de punten van elk team bijhouden totdat ze hun doel bereiken. Terwijl het standaardgedrag van de [Teams](/docs/nl-nl/reference/engine/classes/Teams)  service automatisch elke speler onder hun team groepeert en de bijdragen van elke speler aan hun teamscore optelt, is het belangrijk om punten op een aparte locatie op te slaan en te monitoren voor ronde-gebaseerde gameplay, omdat als een speler scoort en vervolgens vertrekt voordat de ronde voorbij is, hun bijdrage van het leaderboard wordt afgetrokken zodra ze zich ontkoppelen van het spel.

Om ervoor te zorgen dat dit niet gebeurt en elke bijdrage aan het teamdoel behouden blijft, slaat ReplicatedStorage  ⟩ HUDGuiSetup  ⟩ StartSyncingTeamPoints  alle punten apart op onder de teamPoints  attribuut in de [Teams](/docs/nl-nl/reference/engine/classes/Teams)  service. Terwijl teamPoints  toeneemt, roept dit module script de functie startSyncingTeamPoints  aan om de teamcounter Class.GuiObjects  binnen de Objective UI component te vinden.

Wanneer het TeamACounter  en TeamBCounter  vindt, krijgt het hun teamColor  attribuut, dat overeenkomt met de team spawnzones: TeamACounter toont de punten van het groene team, en TeamBCounter houdt de punten van het roze team bij.

StartSyncingTeamPoints

```

local function startSyncingTeamPoints(gui: ScreenGui)

	for _, teamPointCounter in gui.Objective.TeamPointCounter:GetChildren() do

		if not teamPointCounter:IsA("GuiObject") then

			continue

		end

		local iconTeamColor = teamPointCounter:GetAttribute(GuiAttribute.teamColor)

```

Het module script roept vervolgens zijn getTeamFromTeamColor  functie aan om te valideren dat de mint  teamColor  attribuut van TeamACounter en de carnation pink  teamColor  attribuut van TeamBCounter beide overeenkomen met de overeenkomstige [Team.Color](/docs/nl-nl/reference/engine/classes/Team#Color)  eigenschappen onder de [Teams](/docs/nl-nl/reference/engine/classes/Teams)  service. Als dat zo is, retourneert het beide teams.

StartSyncingTeamPoints

```

local function getTeamFromTeamColor(teamColor: Color3): Team?

	for _, team in Teams:GetTeams() do

		if team.TeamColor == teamColor then

			return team

		end

	end

	return nil

end

```

Wanneer dit gebeurt, stelt startSyncingTeamPoints  de [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  objecten van beide team counters in op hun overeenkomstige teamPoints  waarden, en blijft ze bijwerken telkens wanneer een speler een punt scoort door een andere speler uit het tegenovergestelde team te taggen.

StartSyncingTeamPoints

```

teamPointCounter.TextLabel.Text = team:GetAttribute(GuiAttribute.teamPoints)

		team:GetAttributeChangedSignal(GuiAttribute.teamPoints):Connect(function()

			teamPointCounter.TextLabel.Text = team:GetAttribute(GuiAttribute.teamPoints)

```

Alles in deze sectie tot nu toe heeft zich gericht op hoe punten op het scherm van de speler te volgen, maar het is belangrijk om de logica te herzien die het bijhouden van punten op de server afhandelt, zodat het weet wanneer een team het doel bereikt en de ronde wint. Als je ServerScriptService  ⟩ Gameplay  ⟩ Scoring  opnieuw bekijkt, zie je dat het module script begint met het creëren van een bindbare gebeurtenis, die elke keer wordt geactiveerd wanneer een speler een punt scoort.

Scoring

```

local teamScoreChangedBindable = Instance.new("BindableEvent")

local Scoring = {

	teamScoreChanged = teamScoreChangedBindable.Event,

}

```

Vervolgens roept het de incrementScore  functie aan, die de volgende acties uitvoert:

-

Pakt het team van de speler en hun huidige teamPoints waarde op het [Team](/docs/nl-nl/reference/engine/classes/Team)  object in de [Teams](/docs/nl-nl/reference/engine/classes/Teams)  service, en voegt er één aan toe.

-

Pakt de individuele score van de speler op het leaderboard, en voegt er één aan toe.

-

Activeert de eerder genoemde bindbare gebeurtenis met zowel het team van de speler als hun score.

Dit proces houdt effectief zowel de client als de server in lijn met betrekking tot zowel de individuele scores van spelers als hun team scores.

Scoring

```

function Scoring.incrementScore(player: Player, amount: number)

	local team = player.Team

	assert(team, `Speler {player.Name} moet in een team zitten om een punt te scoren, maar heeft geen team`)

	local teamPoints = team:GetAttribute(GuiAttribute.teamPoints)

	teamPoints += amount

	team:SetAttribute(GuiAttribute.teamPoints, teamPoints)

	local leaderstat = player.leaderstats.Points

	leaderstat.Value += amount

	teamScoreChangedBindable:Fire(team, teamPoints)

end

```

## [Resultaten weergeven](#resultaten-weergeven)[](#resultaten-weergeven)

Terwijl spelers elkaar taggen en punten scoren voor hun team, controleert ServerScriptService  ⟩ Gameplay  ⟩ Rounds  of het team dat scoorde het ronde doel heeft bereikt. Als hun teamscore lager is dan de TEAM_SCORE_LIMIT  variabele in ReplicatedStorage  ⟩ TEAM_SCORE_LIMIT , blijft de server wachten totdat een van de teams opnieuw scoort.

Echter, zodra de score van een team de TEAM_SCORE_LIMIT  variabele bereikt, activeert het script een roundWinnerRemote  gebeurtenis instantie met de naam van de speler en hun team.

Rounds

```

-- Controleer of de ronde is afgelopen na elke score

		local team: Team

		local score: number = 0

		while score < TEAM_SCORE_LIMIT do

			team, score = Scoring.teamScoreChanged:Wait()

		end

		-- Toon winnend team

		for _, player in Players:GetPlayers() do

			-- Stuur door welk team de speler aan het einde van de ronde is

			-- omdat het team van de speler op het punt staat te worden verwijderd, zodat de client

			-- zijn eigen team niet kan controleren

			roundWinnerRemote:FireClient(player, team, player.Team)

		end

```

Het ReplicatedStorage  ⟩ RoundResultsGuiSetup  script op elke client luistert naar deze roundWinnerRemote  gebeurtenis instantie zodat het kan:

-

Een unieke StarterGui  ⟩ RoundResultsGui  UI-scherm weergeven dat de resultaten van de ronde aankondigt en of de speler in het winnende team zat.

-

Een overwinning of nederlaag audiofragment afspelen.

Bijvoorbeeld, als een speler in het team zit dat het winnende punt scoorde, ontvangt hij meerdere vormen van feedback over de ronde resultaten in de vorm van een UI-scherm dat overwinningstekst weergeeft, en een audiofragment dat een vrolijk geluid afspeelt. Omgekeerd, als een speler niet in het team zit dat het winnende punt scoorde, ontvangt hij een UI-scherm dat nederlaagstekst weergeeft, en een audiofragment dat een onheilspellend geluid afspeelt.

Overwinningsfeedback

Nederlaagfeedback

RoundResultsGuiSetup

```

local function onRoundWinner(winner: Team, localTeam: Team?)

	local victoryDefeatText = "Ronde beëindigd!"

	if localTeam then

		-- Als ons team heeft gewonnen, tonen we Victory! Anders tonen we Defeat...

		local isVictory = winner == localTeam

		if isVictory then

			victorySound:Play()

			victoryDefeatText = VICTORY_TEXT

		else

			defeatSound:Play()

			victoryDefeatText = DEFEAT_TEXT

		end

	end

```

## [Reset teams](#reset-teams)[](#reset-teams)

Tegelijkertijd dat ServerScriptService  ⟩ Gameplay  ⟩ Rounds  verifieert dat een team het ronde doel heeft bereikt en de juiste UI-weergave voor elke speler activeert, transporteert het ook alle spelers van de arena naar de lobby door hen van de ronde te ontkoppelen. Dit start het proces van het formeel beëindigen van de ronde en het resetten van beide teams.

Met behulp van dezelfde logica in [Configure Spawn Locations](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/spawn-respawn#configureer-spawnlocaties) , stelt Rounds  vervolgens de Neutrale  spawnlocatie's [Neutral](/docs/nl-nl/reference/engine/classes/SpawnLocation#Neutral)  eigenschap in op true  zodat spelers daar kunnen spawnen, ongeacht hun teamstatus. Dit betekent dat de lobby de enige locatie wordt waar spelers kunnen spawnen nadat ze zijn ontkoppeld van de ronde.

Rounds

```

-- Stuur iedereen naar de lobby

		playerAddedConnection:Disconnect()

		neutralSpawn.Neutral = true

		spawnPlayersInLobby(Players:GetPlayers())

```

Na tien seconden te hebben gewacht voor een onderbreking, start het Rounds  server script vervolgens de loop opnieuw door ieders scores te resetten en hen in nieuwe teams in te delen. Het voorbeeld herhaalt dit cyclische rondeproces opnieuw totdat er geen spelers meer binnen de server zijn.

Nu spelers in de map kunnen spawnen met hun eigen team en een volledige ronde kunnen spelen, leert de volgende sectie je over de scripts achter het gedrag van elke blaster.

[Volgende](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/implement-blasters)[Vorige](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/spawn-respawn)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
