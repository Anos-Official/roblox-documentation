<!-- Source: https://create.roblox.com/docs/nl-nl/projects/teleport-private-servers -->

Teleporteren naar privéservers | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelers](/docs/nl-nl/players)

# Teleporteren naar privéservers

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Naast het teleporteren van spelers tussen openbare servers, ondersteunt [TeleportService](/docs/nl-nl/reference/engine/classes/TeleportService)  het teleporteren naar privéservers , die servers zijn die beperkt zijn tot specifieke spelers. Er zijn twee soorten privéservers waar je naartoe kunt teleporteren:

-

Gereserveerde servers : Door ontwikkelaars gemaakte servers die toegankelijk zijn via een door de ontwikkelaar opgegeven ID. Handig voor privéwedstrijden, coöperatieve sessies of elke situatie waarin je controle hebt over wie zich aansluit.

-

VIP-servers : Door spelers aangeschafte privéservers. Gebruik [TeleportOptions.VipServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#VipServerId)  om spelers naar een VIP-server te leiden die ze hebben aangeschaft.

Zowel [ReservedServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#ReservedServerId)  als [VipServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#VipServerId)  zijn eigenschappen van de [TeleportOptions](/docs/nl-nl/reference/engine/classes/TeleportOptions) -klasse. Je kunt slechts één privéserver-routeringsveld tegelijk instellen. Zie [Teleporteren tussen plaatsen](/docs/nl-nl/projects/teleport)  voor een overzicht van alle teleportopties.

## [Teleporteren naar een gereserveerde server](#teleporteren-naar-een-gereserveerde-server)[](#teleporteren-naar-een-gereserveerde-server)

Gereserveerde servers worden op aanvraag gemaakt: de eerste teleport met een nieuwe ReservedServerId  creëert de server, en het hergebruiken van dezelfde ID leidt volgende teleports naar diezelfde server. Genereer de ID met [HttpService:GenerateGUID(false)](/docs/nl-nl/reference/engine/classes/HttpService#GenerateGUID) :

```

local HttpService = game:GetService("HttpService")

local TeleportService = game:GetService("TeleportService")

local Players = game:GetService("Players")

local TARGET_PLACE_ID = 12345678901234

-- De gebruikers die moeten worden geteleporteerd (bijv. van Players:GetPlayers() of een matchmakinggroep)

local player1, player2 = Players:GetPlayers()[1], Players:GetPlayers()[2]

-- Genereer een unieke ID voor de gereserveerde server

local reservedServerId = HttpService:GenerateGUID(false)

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.ReservedServerId = reservedServerId

-- De eerste teleport creëert de server

TeleportService:TeleportAsync(TARGET_PLACE_ID, {player1, player2}, teleportOptions)

```

### [Hergebruik een gereserveerde server-ID](#hergebruik-een-gereserveerde-server-id)[](#hergebruik-een-gereserveerde-server-id)

Om andere spelers later toe te laten voegen aan dezelfde gereserveerde server, bewaar de gereserveerde server-ID met een [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService) -gegevensopslag, zodat deze over sessies en servers heen blijft bestaan.

Op de server die de gereserveerde server creëert, genereer de ID voor de eerste teleport en sla deze op met een sleutel die de sessie identificeert (bijvoorbeeld een lobby-ID of party-ID):

```

local DataStoreService = game:GetService("DataStoreService")

local HttpService = game:GetService("HttpService")

local TeleportService = game:GetService("TeleportService")

local reservedServersStore = DataStoreService:GetDataStore("ReservedServers")

-- Sleutel die de gedeelde sessie over servers identificeert

local sessionKey = "lobby-123"

-- Een nieuwe ID creëert de gereserveerde server bij aankomst op de bestemming

local reservedServerId = HttpService:GenerateGUID(false)

reservedServersStore:SetAsync(sessionKey, reservedServerId)

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.ReservedServerId = reservedServerId

TeleportService:TeleportAsync(TARGET_PLACE_ID, { player }, teleportOptions)

```

Op elke andere server die spelers naar diezelfde gereserveerde server moet sturen, zoek de ID op met dezelfde sessiesleutel en stel deze in als de [TeleportOptions.ReservedServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#ReservedServerId)  van de teleport:

```

local DataStoreService = game:GetService("DataStoreService")

local TeleportService = game:GetService("TeleportService")

local reservedServersStore = DataStoreService:GetDataStore("ReservedServers")

local sessionKey = "lobby-123"

local existingId = reservedServersStore:GetAsync(sessionKey)

if existingId then

	local teleportOptions = Instance.new("TeleportOptions")

	teleportOptions.ReservedServerId = existingId

	TeleportService:TeleportAsync(TARGET_PLACE_ID, { player }, teleportOptions)

end

```

Op een VIP-server, om de VIP-server-ID beschikbaar te maken op de bestemmingsserver zonder een gegevensopslag, koppel deze aan elke speler met [TeleportOptions:SetTeleportData()](/docs/nl-nl/reference/engine/classes/TeleportOptions#SetTeleportData) :

```

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.VipServerId = game.PrivateServerId

teleportOptions:SetTeleportData({ vipServerId = game.PrivateServerId })

TeleportService:TeleportAsync(TARGET_PLACE_ID, {player}, teleportOptions)

```

Bij aankomst, lees het terug uit de join-gegevens van de speler. Voor meer informatie, zie [Stuur gebruikersgegevens mee met teleports](/docs/nl-nl/projects/teleport#stuur-gebruikersgegevens-mee-met-teleportaties) .

### [Identificeer een gereserveerde server bij aankomst](#identificeer-een-gereserveerde-server-bij-aankomst)[](#identificeer-een-gereserveerde-server-bij-aankomst)

Op de bestemmingsserver, controleer of de huidige server een gereserveerde server is:

```

local isReserved = game.PrivateServerId ~= "" and game.PrivateServerOwnerId == 0

```

[DataModel.PrivateServerId](/docs/nl-nl/reference/engine/classes/DataModel#PrivateServerId)  komt overeen met de ReservedServerId  die je hebt opgegeven en blijft constant over alle serverinstanties voor die gereserveerde server. [DataModel.JobId](/docs/nl-nl/reference/engine/classes/DataModel#JobId)  is uniek per draaiende instantie en verandert wanneer de server opnieuw opstart.

## [Teleporteren naar een VIP-server](#teleporteren-naar-een-vip-server)[](#teleporteren-naar-een-vip-server)

VIP-servers zijn privéservers die spelers kunnen kopen vanaf de pagina van het spel. Om een speler naar een VIP-server te teleporteren, stel je [TeleportOptions.VipServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#VipServerId)  in op de [DataModel.PrivateServerId](/docs/nl-nl/reference/engine/classes/DataModel#PrivateServerId)  van de doel-VIP-server.

```

local TeleportService = game:GetService("TeleportService")

local TARGET_PLACE_ID = 12345678901234

-- De PrivateServerId van de bestemmings-VIP-server, bijvoorbeeld meegenomen

-- in de teleportgegevens van de speler of gelezen uit een gegevensopslag

local vipServerId = player:GetJoinData().TeleportData.vipServerId

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.VipServerId = vipServerId

TeleportService:TeleportAsync(TARGET_PLACE_ID, {player}, teleportOptions)

```

[TeleportOptions.VipServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#VipServerId)  is verschillend van [TeleportOptions.ReservedServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#ReservedServerId) . Gebruik ReservedServerId  voor door ontwikkelaars gemaakte gereserveerde servers en VipServerId  voor door spelers aangeschafte VIP-servers.

Een VIP-server-ID is beperkt tot de ervaring die de VIP-server bezit: je kunt deze gebruiken met de plaats-ID van elke plaats in die ervaring, maar niet met een plaats-ID van een andere ervaring.

Wanneer je een routeringsveld niet instelt, kiest de engine de bestemmingsserver. Een teleport zonder ingestelde privéserver-routeringsvelden kan op een openbare server landen of, als de speler onlangs een VIP-server van die ervaring heeft bezocht, op die VIP-server.

Een veelvoorkomend gebruik van dit patroon is het terugbrengen van een speler van een gereserveerde server naar de VIP-server van de rootplaats van de ervaring. Aangezien de game.PrivateServerId  van een gereserveerde server zijn eigen gereserveerde ID is in plaats van de oorspronkelijke VIP-server, neem de ID van de VIP-server mee naar de gereserveerde server, bijvoorbeeld door deze door te geven in teleportData  bij de uitgaande teleport of door deze op te slaan in een gegevensopslag zoals getoond in [Hergebruik een gereserveerde server-ID](#hergebruik-een-gereserveerde-server-id) , en stel deze vervolgens in als de [TeleportOptions.VipServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#VipServerId)  van de retour-teleport.

Stel dezelfde [TeleportOptions.VipServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#VipServerId)  in op elke teleport om spelers in dezelfde VIP-server te houden tijdens het spel.

### [VIP-servertoegangscontroles](#vip-servertoegangscontroles)[](#vip-servertoegangscontroles)

Een speler kan zich bij een VIP-server aansluiten als de Vrienden Toegestaan -instelling van de server, de whitelist of een linkcode hen toegang verleent op het moment van de teleport. Eigenaren van VIP-servers kunnen deze instellingen op elk moment wijzigen, zodat een speler die eerder toegang had, deze kan verliezen.

Als een speler niet is toegestaan om zich aan te sluiten, wordt [TeleportService.TeleportInitFailed](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportInitFailed)  geactiveerd en ziet de speler een foutmelding dat de server beperkt is. Om een groep naar een VIP-server te teleporteren, geef je meerdere spelers door met dezelfde [TeleportOptions.VipServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#VipServerId) . De engine controleert elke speler onafhankelijk op het moment van verbinding, zodat spelers zonder toegang individueel falen terwijl de rest normaal teleport.

Zorg ervoor dat je altijd [TeleportService.TeleportInitFailed](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportInitFailed)  afhandelt voor VIP-teleports, aangezien spelers ook de VIP-server kunnen hebben gesloten of naar een andere kunnen zijn overgestapt.

## [Opslaan en delen van server-ID's](#opslaan-en-delen-van-server-ids)[](#opslaan-en-delen-van-server-ids)

Het [TeleportAsyncResult](/docs/nl-nl/reference/engine/classes/TeleportAsyncResult) -object dat wordt geretourneerd door [TeleportService:TeleportAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportAsync)  bevat informatie over de bestemming:

-

[TeleportAsyncResult.PrivateServerId](/docs/nl-nl/reference/engine/classes/TeleportAsyncResult#PrivateServerId)  - De privéserver-ID van de bestemmingsserver. Komt overeen met [DataModel.PrivateServerId](/docs/nl-nl/reference/engine/classes/DataModel#PrivateServerId)  op de bestemming.

-

[TeleportAsyncResult.ReservedServerAccessCode](/docs/nl-nl/reference/engine/classes/TeleportAsyncResult#ReservedServerAccessCode)  - Alleen gevuld voor legacy-toegangscode-teleports. Niet gevuld bij gebruik van ReservedServerId  of VipServerId .

```

local result = TeleportService:TeleportAsync(TARGET_PLACE_ID, {player}, teleportOptions)

if result then

    print("Bestemming PrivateServerId:", result.PrivateServerId)

end

```

## [Migreren van legacy-toegangscodes](#migreren-van-legacy-toegangscodes)[](#migreren-van-legacy-toegangscodes)

Als je spel de verouderde [TeleportOptions.ReservedServerAccessCode](/docs/nl-nl/reference/engine/classes/TeleportOptions#ReservedServerAccessCode)  of [TeleportOptions.ShouldReserveServer](/docs/nl-nl/reference/engine/classes/TeleportOptions#ShouldReserveServer)  gebruikt, migreer dan naar ReservedServerId  door de toegangscode-stroom te vervangen door een op GUID gebaseerde stroom:

1.

Vervang  ReserveServerAsync()  en ReservedServerAccessCode  door [HttpService:GenerateGUID(false)](/docs/nl-nl/reference/engine/classes/HttpService#GenerateGUID)  en ReservedServerId .

2.

Bewaar  de gegenereerde GUID zodat je deze kunt hergebruiken voor volgende teleports naar dezelfde server.

3.

Update  alle TeleportOptions -gebruikers om ReservedServerId  in te stellen in plaats van ReservedServerAccessCode  of ShouldReserveServer .

### [Voor (verouderd)](#voor-verouderd)[](#voor-verouderd)

```

-- Verouderd: ReserveServerAsync + ReservedServerAccessCode

local accessCode, privateServerId = TeleportService:ReserveServerAsync(TARGET_PLACE_ID)

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.ReservedServerAccessCode = accessCode

TeleportService:TeleportAsync(TARGET_PLACE_ID, {player}, teleportOptions)

```

### [Na (huidig)](#na-huidig)[](#na-huidig)

```

local HttpService = game:GetService("HttpService")

local TeleportService = game:GetService("TeleportService")

-- Huidig: GenerateGUID + ReservedServerId

local reservedServerId = HttpService:GenerateGUID(false)

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.ReservedServerId = reservedServerId

TeleportService:TeleportAsync(TARGET_PLACE_ID, {player}, teleportOptions)

```

De verouderde ReserveServerAsync()  en ReservedServerAccessCode  blijven beschikbaar voor achterwaartse compatibiliteit, maar worden niet aanbevolen voor nieuw werk. ReserveServerAsync()  reserveert niet daadwerkelijk een server van tevoren, maar genereert eenvoudigweg een willekeurige GUID. Bestaande gereserveerde servers die met toegangscodes zijn gemaakt, blijven functioneren.

## [Afhandelen van mislukte teleports](#afhandelen-van-mislukte-teleports)[](#afhandelen-van-mislukte-teleports)

Teleports naar privéservers kunnen mislukken zoals elke netwerkoproep. Wikkel ze in pcall  en probeer het opnieuw indien nodig. Wanneer een teleport wordt geïnitieerd maar op het laatste moment mislukt, wordt [TeleportService.TeleportInitFailed](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportInitFailed)  geactiveerd met de oorspronkelijke [TeleportOptions](/docs/nl-nl/reference/engine/classes/TeleportOptions) , zodat je het opnieuw kunt proberen met dezelfde bestemming.

Voor een volledige implementatie van opnieuw proberen, zie [Afhandelen van mislukte teleports](/docs/nl-nl/projects/teleport#omgaan-met-mislukte-teleportaties)  in de hoofdteleportgids.

Wanneer de engine zelf een gewone teleport naar een VIP-server leidt, vallen VIP-specifieke join-fouten zoals een volle of overstroomde server terug op een openbare join in plaats van [TeleportService.TeleportInitFailed](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportInitFailed)  te activeren. Alleen teleports met een expliciete [TeleportOptions.VipServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#VipServerId)  brengen deze fouten naar je opnieuw proberen-handler.

## [Beste praktijken](#beste-praktijken)[](#beste-praktijken)

-

Genereer ID's op de server.  Roep altijd [HttpService:GenerateGUID(false)](/docs/nl-nl/reference/engine/classes/HttpService#GenerateGUID)  aan vanuit een server [Script](/docs/nl-nl/reference/engine/classes/Script)  om te voorkomen dat clients gereserveerde server-ID's kunnen voorspellen of controleren.

-

Bewaar gereserveerde server-ID's.  Sla de GUID op in een gegevensopslag als spelers zich opnieuw moeten aansluiten bij dezelfde gereserveerde server over sessies heen.

-

Gebruik het juiste veld.  Gebruik ReservedServerId  voor door ontwikkelaars gemaakte gereserveerde servers, VipServerId  voor door spelers aangeschafte VIP-servers. Stel nooit beide in op dezelfde [TeleportOptions](/docs/nl-nl/reference/engine/classes/TeleportOptions) -instantie.

-

Meng geen routeringsvelden.  Je kunt slechts één van ReservedServerId , VipServerId  of ServerInstanceId  tegelijk instellen. Het instellen van meer dan één veroorzaakt een fout.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
