<!-- Source: https://create.roblox.com/docs/nl-nl/production/promotion/invite-prompts -->

Speler uitnodigingsprompten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Ontdekking](/docs/nl-nl/discovery)

# Speler uitnodigingsprompten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Naast de gebruikelijke [promotie](/docs/nl-nl/production/promotion)  methoden om je spelersbasis te vergroten, kun je uitnodigingsprompten  direct in je spel implementeren, waardoor spelers worden aangemoedigd om hun vrienden uit te nodigen en de co-ervaring gameplay te vergroten.

Het uitnodigingsprompt-systeem heeft de volgende kenmerken:

-

Dynamische Uitnodigden  — Vraag spelers om meerdere vrienden uit een selectielijst uit te nodigen, of nodig één specifieke vriend uit.

-

Startgegevens  — Voeg optionele [startgegevens](#inclusief-startgegevens)  toe die kunnen worden gelezen via [Player:GetJoinData()](/docs/nl-nl/reference/engine/classes/Player#GetJoinData)  wanneer de uitgenodigde vriend zich aansluit. Voorbeeldtoepassingen zijn het routeren van uitgenodigde vrienden naar een coördinatenlocatie of het personaliseren van het spel voor de uitgenodigde.

-

Aanpasbare Tekst  — Pas de [uitnodigingsprompt](#vraag-om-een-uitnodiging)  boodschap en de [melding](#stel-meldingsopties-in)  boodschap aan. Bijvoorbeeld, een uitnodigingsprompt voor de speler kan lezen "Vraag je vrienden om mee te doen aan het avontuur!" en de meldingsboodschap voor de uitgenodigde vriend(en) kan lezen "{displayName} wil dat je je bij hun avontuur in {experienceName} voegt!".

Je kunt ook uitnodigers en uitgenodigden volgen en belonen met behulp van het [Vriend Uitnodigingsbeloningssysteem](/docs/nl-nl/production/promotion/referral-system) .

In-ervaring prompt Uitnodigingsmelding

![](https://prod.docsiteassets.roblox.com/assets/promotion/invite-prompts/Invite-From-Experience.png)

## [Stel uitnodigingsopties in](#stel-uitnodigingsopties-in)[](#stel-uitnodigingsopties-in)

Standaard toont een uitnodigingsprompt voor de speler een menu van hun vrienden met Uitnodigen  knoppen. Om de promptboodschap aan te passen, een specifieke vriend te targeten, of startgegevens in de uitnodiging op te nemen, moet je een [ExperienceInviteOptions](/docs/nl-nl/reference/engine/classes/ExperienceInviteOptions)  object instellen met de gewenste eigenschappen.

| Eigenschap | | Type | | Beschrijving |
| --- | --- |
| [PromptMessage](/docs/nl-nl/reference/engine/classes/ExperienceInviteOptions#PromptMessage) | | string | | Aangepaste tekst die wordt weergegeven op de uitnodigingsprompt voor de verzendende speler, bijvoorbeeld "Vraag je vrienden om mee te doen aan het avontuur!" voor een multi-vriend uitnodigingsprompt, of "Nodig deze vriend uit om mee te doen aan het avontuur!" voor een specifieke vriend uitnodigingsprompt. Let op dat als je aangepaste uitnodigingspromptboodschap lang genoeg is om de grenzen van de UI te overschrijden, deze niet zal worden weergegeven. |
| [InviteUser](/docs/nl-nl/reference/engine/classes/ExperienceInviteOptions#InviteUser) | | number | | Roblox [UserId](/docs/nl-nl/reference/engine/classes/Player#UserId)  van de specifieke vriend om uit te nodigen; als dit niet wordt opgegeven, wordt de speler gevraagd om een lijst van vrienden te kiezen. |
| [InviteMessageId](/docs/nl-nl/reference/engine/classes/ExperienceInviteOptions#InviteMessageId) | | string | | Asset-ID die overeenkomt met een Melding  assettype. Deze asset wordt gebruikt om een aangepaste string voor de uitnodigingsmelding die vrienden ontvangen op te slaan/lokaliseren. Zie [Instellen van meldingsopties](#stel-meldingsopties-in)  voor details. |
| [LaunchData](/docs/nl-nl/reference/engine/classes/ExperienceInviteOptions#LaunchData) | | string | | Wordt gebruikt om een parameter in [Player:GetJoinData()](/docs/nl-nl/reference/engine/classes/Player#GetJoinData)  in te stellen wanneer een vriend zich aansluit via de uitnodigingsmelding. Maximaal 200 tekens. Zie [Inclusief startgegevens](#inclusief-startgegevens)  voor een gebruiksvoorbeeld. |

Meerdere vrienden Specifieke vriend

LocalScript - Nodig Meerdere Vrienden Uit

```

local SocialService = game:GetService("SocialService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Construct invite options with a custom prompt message

local inviteOptions = Instance.new("ExperienceInviteOptions")

inviteOptions.PromptMessage = "Vraag je vrienden om mee te doen aan het avontuur!"

```

## [Stel meldingsopties in](#stel-meldingsopties-in)[](#stel-meldingsopties-in)

Standaard bevat de uitnodigingsmelding die vrienden ontvangen de [DisplayName](/docs/nl-nl/reference/engine/classes/Player#DisplayName) , gebruikersnaam en de spelnaam van de verzender. Om de boodschap aan te passen, kun je een Melding  asset maken op het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  en de asset-ID als parameter van [ExperienceInviteOptions](/docs/nl-nl/reference/engine/classes/ExperienceInviteOptions)  opnemen.

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Net als bij [badges](/docs/nl-nl/production/publishing/badges) , zijn meldingsstrings gekoppeld aan een specifiek spel . Zoek de thumbnail van dat spel en klik erop.

3.

In de linker kolom, onder Betrokkenheid , klik op Meldingen .

4.

In het middengebied, klik op de knop Maak een meldingsstring .

5.

Vul een identificatienaam in (alleen zichtbaar voor jou) en de aangepaste meldingsboodschap. Let op dat je {experienceName}  als een placeholder moet opnemen om de naam van het spel voor uitgenodigde vrienden te identificeren, en je kunt optioneel de [DisplayName](/docs/nl-nl/reference/engine/classes/Player#DisplayName)  van de verzender opnemen via de {displayName}  placeholder.

Voorbeeldmeldingsstrings:

-

 {displayName} wil dat je je bij hun avontuur in {experienceName} voegt!

-

 {displayName} heeft net de zesde fase van {experienceName} gehaald. Kun jij dat ook?

6.

Wanneer je klaar bent, klik op de knop Maak meldingsstring .

7.

Op de meldingenpagina, in de tabel van meldingen, klik op de ⋯  knop in de Acties  kolom en selecteer Kopieer Asset-ID .

8.

In het [ExperienceInviteOptions](/docs/nl-nl/reference/engine/classes/ExperienceInviteOptions)  object voor de uitnodigingsprompt, plak de asset-ID als de waarde van de [InviteMessageId](/docs/nl-nl/reference/engine/classes/ExperienceInviteOptions#InviteMessageId)  eigenschap.

LocalScript - Nodig Meerdere Vrienden Uit

```

local SocialService = game:GetService("SocialService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Construct invite options with friend's user ID

local inviteOptions = Instance.new("ExperienceInviteOptions")

inviteOptions.InviteMessageId = "ef0e0790-e2e8-4441-9a32-93f3a5783bf1"

```

## [Vraag om een uitnodiging](#vraag-om-een-uitnodiging)[](#vraag-om-een-uitnodiging)

Om om een uitnodiging te vragen, moet je eerst bepalen of de speler kan  uitnodigen, aangezien de mogelijkheid kan variëren afhankelijk van het platform of de speler. Zodra dit is bevestigd, kun je de uitnodigingsprompt aan de speler tonen.

1.

Roep [SocialService:CanSendGameInviteAsync()](/docs/nl-nl/reference/engine/classes/SocialService#CanSendGameInviteAsync)  aan, gewikkeld in een [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  aangezien het een asynchrone netwerkoproep is die af en toe kan mislukken.

2.

Als de uitnodigingsmogelijkheid is bevestigd, roep dan [SocialService:PromptGameInvite()](/docs/nl-nl/reference/engine/classes/SocialService#PromptGameInvite)  aan met het optionele [uitnodigingsopties object](#stel-uitnodigingsopties-in)  als het tweede argument.

Zodra de uitnodiging is geprompt, ziet de speler een prompt op het scherm om meerdere vrienden uit te nodigen, of de specifieke vriend die is gedefinieerd in het [uitnodigingsopties object](#stel-uitnodigingsopties-in) . Wanneer de speler vervolgens op de Uitnodigen  knop voor een of meer vrienden klikt, ontvangen die vrienden een melding met de [DisplayName](/docs/nl-nl/reference/engine/classes/Player#DisplayName) , gebruikersnaam en de naam van de ervaring van de verzender. Meldingen kunnen verder worden gepersonaliseerd zoals beschreven in [Stel meldingsopties in](#stel-meldingsopties-in) .

Meerdere Vrienden Specifieke Vriend

LocalScript - Nodig Meerdere Vrienden Uit

```

local SocialService = game:GetService("SocialService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Functie om te controleren of de speler een uitnodiging kan versturen

local function canSendGameInvite(sendingPlayer)

	local success, canSend = pcall(function()

		return SocialService:CanSendGameInviteAsync(sendingPlayer)

	end)

	return success and canSend

end

local canInvite = canSendGameInvite(player)

if canInvite then

	SocialService:PromptGameInvite(player)

end

```

## [Inclusief startgegevens](#inclusief-startgegevens)[](#inclusief-startgegevens)

Om de samenwerking in de ervaring verder te verbeteren of om spelersuitnodigingen te stimuleren, kun je startgegevens  opnemen in een uitnodigingsprompt, nuttig voor scenario's zoals het routeren van uitgenodigde vrienden naar een coördinatenlocatie of het personaliseren van het spel voor de uitgenodigde.

1.

Wanneer je [om een uitnodiging vraagt](#vraag-om-een-uitnodiging) , voeg een [ExperienceInviteOptions](/docs/nl-nl/reference/engine/classes/ExperienceInviteOptions)  object toe met relevante gegevens die zullen worden gebruikt wanneer de vriend zich bij het spel voegt, bijvoorbeeld de [Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId)  van de verzender, de ID van een [badge](/docs/nl-nl/production/publishing/badges)  die aan de vriend moet worden toegekend bij het joinen, of een coördinatenlocatie om de vriend te laten spawnen. Als je meerdere gegevensstukken moet samenstellen, codeer de gegevens met [JSONEncode()](/docs/nl-nl/reference/engine/classes/HttpService#JSONEncode) .

Meerdere Vrienden Specifieke Vriend

LocalScript - Nodig Meerdere Vrienden Uit

```

local HttpService = game:GetService("HttpService")

local SocialService = game:GetService("SocialService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local data = {

	senderUserID = player.UserId,

	spawnLocation = {12, 48, 205.5}

}

local launchData = HttpService:JSONEncode(data)

-- Construct invite options with launch data

local inviteOptions = Instance.new("ExperienceInviteOptions")

inviteOptions.LaunchData = launchData

-- Functie om te controleren of de speler een uitnodiging kan versturen

local function canSendGameInvite(sendingPlayer)

	local success, canSend = pcall(function()

		return SocialService:CanSendGameInviteAsync(sendingPlayer)

	end)

	return success and canSend

end

local canInvite = canSendGameInvite(player)

if canInvite then

	SocialService:PromptGameInvite(player, inviteOptions)

end

```

Vergeet niet om inviteOptions  met de startgegevens (maximaal 200 tekens) als de tweede parameter van [PromptGameInvite()](/docs/nl-nl/reference/engine/classes/SocialService#PromptGameInvite)  op te nemen.

2.

Voor binnenkomende vrienden die zich via de melding aansluiten, controleer je de startgegevens aan de serverzijde via [Player:GetJoinData()](/docs/nl-nl/reference/engine/classes/Player#GetJoinData) . Als je meerdere gegevensstukken in JSON voor de uitnodigingsprompt hebt gecodeerd, vergeet dan niet om het te decoderen met [JSONDecode()](/docs/nl-nl/reference/engine/classes/HttpService#JSONDecode) .

Script - Gebruik Uitnodigingsstartgegevens

```

local HttpService = game:GetService("HttpService")

local Players = game:GetService("Players")

local ATTEMPT_LIMIT = 10

local RETRY_DELAY = 1

local function onPlayerAdded(player)

	local launchData

	for _ = 1, ATTEMPT_LIMIT do

		task.wait(RETRY_DELAY)

		local joinData = player:GetJoinData()

		if joinData.LaunchData ~= "" then

			launchData = joinData.LaunchData

			break

		end

	end

	if launchData then

		local data = HttpService:JSONDecode(launchData)

		print(data.senderUserID)

		print(data.spawnLocation)

	else

		warn("Geen startgegevens ontvangen!")

	end

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Startgegevens kunnen enkele seconden duren om te verschijnen nadat de vriend zich via de uitnodiging heeft aangesloten. Zoals weergegeven in het bovenstaande codevoorbeeld, is het aan te raden om te wachten tot de startgegevens zijn aangekomen voordat je probeert ze te gebruiken.

3.

Als de startgegevens bestaan, kun je deze gebruiken voor een breed scala aan ontwerpscenario's, waaronder:

-

Spawn de binnenkomende vriend aan het begin van een uitdagend obstakelparcours dat de verzender net heeft voltooid, op basis van een coördinatenlocatie die via de startgegevens is doorgegeven.

-

Controleer of de verzender  zich op de plek bevindt, op basis van hun [Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId)  in de startgegevens, en teleporteer het personage van de vriend in de buurt van hun personage.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
