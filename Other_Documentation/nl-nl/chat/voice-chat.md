<!-- Source: https://create.roblox.com/docs/nl-nl/chat/voice-chat -->

Stemchat | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Chat

# Stemchat

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Stemchat is momenteel beschikbaar voor alle 13+ leeftijdsgeverifieerde gebruikers in een specifieke set van landen. Bekijk de [Stemchat FAQ](https://en.help.roblox.com/hc/en-us/articles/4405807645972-Voice-Chat-FAQs)  voor meer informatie. Gebruikers niet  in deze landen moeten [ID-verificatie](https://en.help.roblox.com/hc/en-us/articles/4407282410644)  gebruiken om chat met stem in te schakelen. Eenmaal geverifieerd, kunnen in aanmerking komende 13+ gebruikers zich aanmelden om deze functie te gebruiken door hun account Instellingen -pagina te bezoeken of vanuit een stem-geactiveerd spel, waardoor ze met stem kunnen chatten in elk Roblox-spel dat dit ondersteunt. Spellen met stem zien vaak een toename in betrokkenheid, DAU en uitgaven.

Stemchat  is een functie die realtime, gesproken communicatie tussen jou en andere spelers mogelijk maakt. Het is alleen beschikbaar voor plaatsen die een maximum van 100 spelers ondersteunen.

 ![Twee gebruikers chatten met stem binnen een spel.](https://prod.docsiteassets.roblox.com/assets/players/voice-chat/In-Experience-Example.jpg)

## [Stemchat inschakelen](#stemchat-inschakelen)[](#stemchat-inschakelen)

Stemchat is standaard ingeschakeld voor geverifieerde 13+ gebruikers in alle nieuwe spellen met een maximum van 100 spelers. Stemchat inschakelen is vereist om de spraak-naar-tekst API te gebruiken.

Om stem voor bestaande spellen te activeren of uit te schakelen voor nieuwe:

1.

Open je spel in Studio.

2.

Open Bestand  > Ervaringsinstellingen .

3.

Navigeer naar het tabblad Communicatie  aan de linkerkant van het venster.

4.

Zet Stemchat inschakelen  op de gewenste instelling.

5.

OPTIEEL

 Voor betere communicatie tussen spelers binnen je spel, zet Camera inschakelen  aan om in aanmerking komende spelers hun avatar te laten animeren met hun beweging.

6.

[Publiceer](/docs/nl-nl/production/publishing/publish-games-and-places)  de plaats om de wijzigingen op te slaan.

### [Stel maximaal aantal spelers in](#stel-maximaal-aantal-spelers-in)[](#stel-maximaal-aantal-spelers-in)

Als je eerder het maximale aantal spelers in een plaats op meer dan 100 hebt ingesteld, moet je dit verlagen om Stemchat te ondersteunen.

1.

Selecteer het spel op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Navigeer in de navigatie aan de linkerkant naar Configuraties  > Plaatsen .

3.

Selecteer de gewenste plaats en navigeer vervolgens naar Toegang in de linkerkolom.

4.

Voor Maximaal aantal bezoekers , voer een getal in dat kleiner is dan of gelijk aan 100.

5.

Klik op de knop Wijzigingen opslaan .

Wanneer je het maximale aantal spelers in een plaats bijwerkt naar minder dan 100, kunnen er al servers zijn geconfigureerd naar een ander, hoger aantal. Aangezien die servers Stemchat niet ondersteunen, wordt aanbevolen om [servers opnieuw op te starten](/docs/nl-nl/projects/update-games#servers-opnieuw-opstarten) .

### [Pas stemgedrag aan](#pas-stemgedrag-aan)[](#pas-stemgedrag-aan)

Stemchat is standaard proximity-based , waarbij het volume van deelnemers wordt aangepast op basis van hoe dicht ze bij elkaar zijn. Je kunt echter [UseAudioApi](/docs/nl-nl/reference/engine/classes/VoiceChatService#UseAudioApi)  instellen op [Enabled](/docs/nl-nl/reference/engine/enums/AudioApiRollout)  om controle te krijgen over hoe stemmen zijn ingesteld en gebruikt in je spel.

Als [VoiceChatService](/docs/nl-nl/reference/engine/classes/VoiceChatService)  nog niet verschijnt:

1.

Klik met de rechtermuisknop in het Explorer -venster en selecteer Toon Services…  in het contextmenu.

2.

Selecteer [VoiceChatService](/docs/nl-nl/reference/engine/classes/VoiceChatService)  in het pop-upvenster en klik op Invoegen . De service verschijnt in de Explorer -hiërarchie.

 ![VoiceChatService in Explorer-hiërarchie](https://prod.docsiteassets.roblox.com/assets/studio/explorer/VoiceChatService.png)

3.

Zorg ervoor dat [UseAudioApi](/docs/nl-nl/reference/engine/classes/VoiceChatService#UseAudioApi)  is ingesteld op [Enabled](/docs/nl-nl/reference/engine/enums/AudioApiRollout)  in het Eigenschappen -venster. Dit kan al voor je zijn gedaan.

#### [Team-gebaseerd](#team-gebaseerd)[](#team-gebaseerd)

Om [Team](/docs/nl-nl/reference/engine/classes/Team) -gebaseerde chat te implementeren waarbij alleen teamgenoten elkaar kunnen horen, kun je de volgende [Script](/docs/nl-nl/reference/engine/classes/Script)  binnen [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  gebruiken:

Team Chat

```

local Teams = game:GetService("Teams")

local function findAudioInput(forPlayer : Player) : AudioDeviceInput?

	-- Gaat ervan uit dat er slechts één AudioDeviceInput per speler is, gekoppeld aan het Speler-object

	-- Dit wordt voor je verzorgd als VoiceChatService.EnableDefaultVoice waar is

	-- Moet mogelijk opnieuw worden ontworpen voor generaliteit als je plaats AudioDeviceInput-objecten elders plaatst

	return forPlayer:FindFirstChildWhichIsA("AudioDeviceInput")

end

local function onTeamChanged(player : Player)

	local team = player.Team

	if not team then return end

	local device = findAudioInput(player)

	if not device then return end

	-- Sta alleen teamgenoten toe om elkaar te horen

	device.AccessType = Enum.AccessModifierType.Allow

	local allowed = {}

	for _, player : Player in team:GetPlayers() do

		table.insert(allowed, player.UserId)

	end

	device:SetUserIdAccessList(allowed)

end

local function onTeamAdded(team : Team)

	team.PlayerAdded:Connect(onTeamChanged)

	team.PlayerRemoved:Connect(onTeamChanged)

end

for _, team : Team in Teams:GetTeams() do

	onTeamAdded(team)

end

Teams.ChildAdded:Connect(function(child : Instance)

	if child:IsA("Team") then

		onTeamAdded(child)

	end

end)

```

#### [Niet-ruimtelijk](#niet-ruimtelijk)[](#niet-ruimtelijk)

Afhankelijk van de behoeften van je spel, kan het logischer zijn om anderen met gelijke volume te horen, ongeacht hun geografische locatie. Als je [standaard Stemchat uitschakelt](#uitschakelen-per-plaats) , kun je vervolgens niet-ruimtelijke Stemchat implementeren via de volgende [Script](/docs/nl-nl/reference/engine/classes/Script)  binnen [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) :

Non-Proximity Chat

```

local Players = game:GetService("Players")

local Workspace = game:GetService("Workspace")

local function wireUp(source : Instance, target : Instance)

	local wire = Instance.new("Wire")

	wire.SourceInstance = source

	wire.TargetInstance = target

	wire.Parent = source

end

-- Stel een globale volumeregelaar in voor ieders stem

local volumeSlider = Instance.new("AudioFader", Workspace)

local output = Instance.new("AudioDeviceOutput", Workspace)

wireUp(volumeSlider, output)

local function onPlayerAdded(player : Player)

	local device = Instance.new("AudioDeviceInput", player)

	device.Player = player

	-- Route de microfooninvoer van elke nieuwe speler naar de globale volumeregelaar

	wireUp(device, volumeSlider)

end

for _, player in Players:GetPlayers() do

	onPlayerAdded(player)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Het bovenstaande script draait op de server, waardoor er een [AudioDeviceInput](/docs/nl-nl/reference/engine/classes/AudioDeviceInput)  per speler wordt gemaakt en ze allemaal worden verbonden met een gedeelde [AudioFader](/docs/nl-nl/reference/engine/classes/AudioFader) . Dit gedrag zoals het is, stelt spelers in staat om alle andere spelers en  zichzelf te horen. Aangezien het horen van jezelf behoorlijk afleidend kan zijn, kun je de volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  in [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts)  plaatsen om de [Wires](/docs/nl-nl/reference/engine/classes/Wire)  te verwijderen die anders je eigen stem terug naar je eigen luidsprekers zouden vervoeren.

LocalScript

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local function onDescendantAdded(descendant : Instance)

	if descendant:IsA("Wire") then

		descendant:Destroy()

	end

end

for _, descendant in player:GetDescendants() do

	onDescendantAdded(descendant)

end

player.DescendantAdded:Connect(onDescendantAdded)

```

### [Uitschakelen per plaats](#uitschakelen-per-plaats)[](#uitschakelen-per-plaats)

Als je Stemchat niet voor elke plaats binnen je spel wilt inschakelen, kun je het uitschakelen binnen specifieke plaatsen die anders stem-geschikt zouden zijn.

Als je momenteel het Maximaal aantal spelers  van een plaats op een waarde boven 100 instelt om Stemchat uit te schakelen, wordt aanbevolen om deze workflow in plaats daarvan te gebruiken.

Om Stemchat voor een specifieke plaats binnen een spel uit te schakelen:

1.

Klik met de rechtermuisknop in het Explorer -venster en selecteer Toon Services…  in het contextmenu.

2.

Selecteer [VoiceChatService](/docs/nl-nl/reference/engine/classes/VoiceChatService)  in het pop-upvenster en klik op Invoegen . De service verschijnt in de Explorer -hiërarchie.

 ![VoiceChatService in Explorer-hiërarchie](https://prod.docsiteassets.roblox.com/assets/studio/explorer/VoiceChatService.png)

3.

Zorg ervoor dat [EnableDefaultVoice](/docs/nl-nl/reference/engine/classes/VoiceChatService#EnableDefaultVoice)  is uitgeschakeld in het Eigenschappen -venster.

4.

Publiceer de plaats om de wijzigingen op te slaan en [herstart servers](/docs/nl-nl/projects/update-games#servers-opnieuw-opstarten)  om ervoor te zorgen dat de wijziging van kracht wordt voor alle servers die momenteel je spel draaien.

## [Controleer status](#controleer-status)[](#controleer-status)

Je kunt controleren of een speler Stemchat heeft ingeschakeld door [IsVoiceEnabledForUserIdAsync()](/docs/nl-nl/reference/engine/classes/VoiceChatService#IsVoiceEnabledForUserIdAsync)  aan te roepen in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) , of in een [Script](/docs/nl-nl/reference/engine/classes/Script)  met [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  ingesteld op [Enum.RunContext.Client](/docs/nl-nl/reference/engine/enums/RunContext#Client) .

Client Script - Controleer Stemchat Status

```

local Players = game:GetService("Players")

local VoiceChatService = game:GetService("VoiceChatService")

local localPlayer = Players.LocalPlayer

local success, enabled = pcall(function()

	return VoiceChatService:IsVoiceEnabledForUserIdAsync(localPlayer.UserId)

end)

if success and enabled then

	print("Stemchat ingeschakeld!")

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
