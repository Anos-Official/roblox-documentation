<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/gameplay-scripting/create-teams -->

Teams maken | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Teams maken

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Teams maken  stelt je in staat om spelers in groepen te sorteren die concurreren om een gemeenschappelijk doel te bereiken, zoals het scoren van de meeste punten of het oversteken van de finishlijn voordat andere leden van het vijandige team dat doen. Voor een first-person shooter is het creëren van teams bijzonder belangrijk omdat het complexe, gecoördineerde gameplaystrategieën mogelijk maakt die verder gaan dan de vaardigheden van een individuele speler.

Met behulp van het [voorbeeld laser tag spel](https://www.roblox.com/games/14817965191/Laser-Tag-1A)  als referentie, leert dit gedeelte van de tutorial je hoe je spelers in teams sorteert, inclusief scriptinstructies over:

-

Het gebruik van de standaardfunctionaliteit van de [Teams](/docs/nl-nl/reference/engine/classes/Teams)  service om spelers aan ofwel het groene of het roze team toe te wijzen.

-

Het helpen van spelers om onderscheid te maken tussen hun bondgenoten en vijandige teamleden door middel van on-screen en in-game teamindicatoren.

-

Het mogelijk maken van vergevingsgezinde gameplay die spelers niet bestraft voor het raken van hun teamgenoten.

Nadat je dit gedeelte hebt voltooid, leer je over de scripts die spelers in staat stellen om te spawnen of te respawnen naar een neutrale lobby of team spawnzone, de visuals van het first-person krachtveld aan te passen en de clientstatus zowel vanaf de server als de client te beheren.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Intro.png)

## [Teamkleuren toewijzen](#teamkleuren-toewijzen)[](#teamkleuren-toewijzen)

Het voorbeeld laser tag spel gebruikt de [Teams](/docs/nl-nl/reference/engine/classes/Teams)  service als basis voor het creëren van twee teams omdat de service ingebouwde team sorteerfunctionaliteit biedt die in grote lijnen direct werkt. Bijvoorbeeld, zonder enige extra scriptinginspanningen, handelt de service acties zoals:

-

Spelers gelijkmatig sorteren en balanceren in elk team.

-

Spelers onder hun team op het leaderboard groeperen.

-

Spelersnamen in de 3D-ruimte tinten naar hun bijbehorende teamkleur.

-

Spelers naar verschillende spawnlocaties spawnen die alleen toegankelijk zijn voor hun team.

Vanwege deze standaardfunctionaliteit, stelt het voorbeeld de [Teams](/docs/nl-nl/reference/engine/classes/Teams)  service in, en gebruikt vervolgens twee verschillende [Team](/docs/nl-nl/reference/engine/classes/Team)  objecten met verschillende waarden voor de [Team.Color](/docs/nl-nl/reference/engine/classes/Team#Color)  eigenschappen om elk team te vertegenwoordigen: mint  voor het team dat aan de ene kant van de kaart samenkomt, en carnation pink  voor het team dat aan de andere kant van de kaart samenkomt. Deze specifieke kleuren zijn nuttig omdat ze complementair zijn, wat betekent dat ze goed contrasteren, en ze stellen spelers in staat om gemakkelijk hun omgeving te scannen en zich te oriënteren binnen het gebouw en naar andere spelers.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Green-Team-Players.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Pink-Team-Players.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Green-Team-Properties.png)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Pink-Team-Properties.png)

Om meer te leren over dit kleurthema, zie [Selecteer een kleurthema](/docs/nl-nl/tutorials/curriculums/user-interface-design/choose-an-art-style#selecteer-een-kleurthema)  uit het UI-curriculum.

Het is belangrijk om de exacte [BrickColor](/docs/nl-nl/reference/engine/datatypes/BrickColor)  naam voor de [Team.Color](/docs/nl-nl/reference/engine/classes/Team#Color)  eigenschap op te merken omdat het spel deze naam in veel scripts in het spel gebruikt om spelers bij te houden terwijl ze in teams worden gesorteerd, punten te verhogen wanneer spelers vijandige spelers taggen tijdens een ronde, en aangepaste UI-elementen bij te werken. Bijvoorbeeld, wanneer een ronde begint, vereist ReplicatedStorage  ⟩ HUDGuiSetup  startSyncingTeamColor  en startSyncingTeamPoints , die beide verwijzen naar [Team.Color](/docs/nl-nl/reference/engine/classes/Team#Color)  om unieke acties voor elk team uit te voeren.

startSyncingTeamColor startSyncingTeamPoints

startSyncingTeamColor  verwijst naar [Team.Color](/docs/nl-nl/reference/engine/classes/Team#Color)  zodat het de juiste kleur en het juiste pictogram voor de teamindicator van de speler in de linkerbenedenhoek van hun scherm kan toewijzen.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Green-Team.jpg) Groen Team

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Pink-Team.jpg) Roze Team

```

local function setPlayerTeamIcon(gui: ScreenGui)

	for _, teamColorIcon in gui.PlayerDisplay.TeamIcons:GetChildren() do

		local iconTeamColor = teamColorIcon:GetAttribute(GuiAttribute.teamColor)

		teamColorIcon.Visible = localPlayer.TeamColor == iconTeamColor

	end

end

local function startSyncingTeamColor(gui: ScreenGui)

	setPlayerTeamIcon(gui)

	localPlayer:GetPropertyChangedSignal("Team"):Connect(function()

		setPlayerTeamIcon(gui)

	end)

end

```

## [Teamindicatoren weergeven](#teamindicatoren-weergeven)[](#teamindicatoren-weergeven)

Zodra een speler in een team is gesorteerd, moet hij snel kunnen begrijpen tot welk team hij behoort en onderscheid maken tussen zijn bondgenoten en vijandige teamleden. Dit vermogen is belangrijk omdat de gameplay van een first-person shooter vereist dat spelers snelle strategische beslissingen nemen terwijl ze zich in gevechtszones bevinden, zodat ze niet worden getagd en de ronde verliezen.

Om spelers voor succes op te zetten, biedt het voorbeeld laser tag spel meerdere teamindicatoren zowel op het scherm als in de 3D-ruimte:

-

Spelerindicator  – Aangepaste on-screen UI die de teamkleur en het pictogram van de speler weergeeft.

-

Teamindicator  – Aangepaste in-game UI die de teamkleur van de speler weergeeft.

-

Leaderboardindicator  – Standaard Teams service on-screen UI die spelers onder hun teamkleur groepeert.

-

Naamtint  – Standaard Teams service in-game UI die de naam van de speler boven hun hoofd tint naar hun teamkleur.

** On-screen Indicatoren**

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Player-Indicator.jpg) Spelerindicator

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Leaderboard-Indicator.jpg) Leaderboardindicator

** In-game Indicatoren**

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Team-Indicator.jpg) Teamindicator

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Creating-Teams/Name-Tint.jpg) Naamtint

Je hoeft geen extra werk te doen voor de Leaderboardindicator of Naamtint buiten het toewijzen van teamkleuren uit het vorige gedeelte van de tutorial, maar de aangepaste UI teamindicatoren vereisen meer programmeerinspanningen om zowel de indicatoren weer te geven als vijandindicatoren te blokkeren wanneer ze achter muren staan. Voor een volledige uitleg van de scripts die het aangepaste UI-gedrag beheersen, evenals hoe je elk UI-element zelf kunt implementeren, zie [Spelerindicator](/docs/nl-nl/tutorials/curriculums/user-interface-design/implement-designs-in-studio#spelerindicator)  en [Teamindicator](/docs/nl-nl/tutorials/curriculums/user-interface-design/implement-designs-in-studio#team-indicator)  uit het UI-curriculum.

## [Vriendelijk vuur uitschakelen](#vriendelijk-vuur-uitschakelen)[](#vriendelijk-vuur-uitschakelen)

Hoewel sommige first-person shooter spellen spelers bestraffen die hun eigen teamgenoten raken, staat het voorbeeld laser tag spel meer vergevingsgezinde gameplay toe door vriendelijk vuur uit te schakelen. Deze ontwerpbeslissing stelt iedereen in staat om alleen hun teamscore te verhogen, niet te verlagen door gameplay-ongelukken.

Om te begrijpen hoe het voorbeeld deze functionaliteit implementeert, bekijk hoe ServerScriptService  ⟩ LaserBlastHandler  ⟩ processTaggedPlayers  ⟩ onPlayerTagged  omgaat met het toebrengen van schade aan getagde spelers. Wanneer de server een botsing detecteert tussen de blast van een speler en een andere speler, roept het de functie onPlayerTagged  aan om te begrijpen welke speler de blast heeft afgevuurd, welke speler door de blast is geraakt, en hoeveel schade het van de gezondheid van de speler moet verwijderen volgens het type blaster.

```

local function onPlayerTagged(playerBlasted: Player, playerTagged: Player, damageAmount: number)

```

Voordat het de gezondheid verlaagt, verifieert het script eerst of de getagde speler in hetzelfde team zit als de speler die de blast heeft geïnitieerd. Als ze in hetzelfde team zitten, negeert het script de blastgegevens volledig.

```

local character = playerTagged.Character

	local isFriendly = playerBlasted.Team == playerTagged.Team

	-- Vriendelijk vuur uitschakelen

	if isFriendly then

		return

	end

```

Als de getagde speler wel  in het vijandige team zit, krijgt de speler de juiste hoeveelheid schade volgens het type blaster. Bovendien, als de speler genoeg schade oploopt om getagd te worden, beloont het script een punt aan het team van de speler die de blast heeft geïnitieerd. Voor meer informatie over hoe het voorbeeld punten bijhoudt, zie [Rondes toevoegen](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/add-rounds#volg-punten)  later in de tutorial.

```

local humanoid = character and character:FindFirstChild("Humanoid")

	if humanoid and humanoid.Health > 0 then

		local damage = math.min(damageAmount, humanoid.Health)

		humanoid:TakeDamage(damage)

		if humanoid.Health <= 0 then

			Scoring.incrementScore(playerBlasted, 1)

		end

	end

end

return onPlayerTagged

```

Voor meer informatie over wat er gebeurt wanneer een speler zijn blaster afvuurt, zie [Implementeer blastergedrag](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/implement-blasters)  en [Detecteer hits](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/detect-hits)  later in de tutorial.

Als je het spel nu zou testen, zouden alle spelers willekeurig spawnen in een van de spawnzones aan de tegenovergestelde uiteinden van de arena, ongeacht tot welk team ze behoren, wat betekent dat elk team direct naast elkaar zou spawnen.

Om dit probleem aan te pakken, leert het volgende gedeelte van de tutorial je over de aangepaste logica achter het beperken van teamspawnen naar bepaalde spawnlocaties, het beheren van de clientstatus terwijl spelers het spawngebied verlaten nadat ze hun blaster hebben geselecteerd, en het respawnen van spelers terug naar hun spawnzone of lobbygebied wanneer hun gezondheid nul bereikt.

[Volgende](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/spawn-respawn)[Vorige](/docs/nl-nl/tutorials/curriculums/gameplay-scripting)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
