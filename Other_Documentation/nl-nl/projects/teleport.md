<!-- Source: https://create.roblox.com/docs/nl-nl/projects/teleport -->

Teleporteren tussen plaatsen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelers](/docs/nl-nl/players)

# Teleporteren tussen plaatsen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Veel games zijn onderverdeeld in meerdere [plaatsen](/docs/nl-nl/production/publishing/publish-games-and-places#maak-extra-plaatsen) , zoals een fantasiewereld met steden, kastelen, kerkers en een uitgestrekt bos. Gebruik [TeleportService](/docs/nl-nl/reference/engine/classes/TeleportService)  om gebruikers tussen plaatsen, naar verschillende servers of zelfs naar andere games te teleporteren.

## [Teleporteer spelers](#teleporteer-spelers)[](#teleporteer-spelers)

Om spelers te teleporteren, gebruik je [TeleportService:TeleportAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportAsync) . Deze methode accepteert drie parameters:

-

De [PlaceId](/docs/nl-nl/reference/engine/classes/DataModel#PlaceId)  waarnaar gebruikers moeten worden geteleporteerd.

-

Een array met de [Player](/docs/nl-nl/reference/engine/classes/Player)  instanties die je wilt teleporteren.

-

Een optionele [TeleportOptions](/docs/nl-nl/reference/engine/classes/TeleportOptions)  instantie die aangepaste eigenschappen bevat voor de [TeleportAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportAsync)  aanroep.

```

local Players = game:GetService("Players")

local TeleportService = game:GetService("TeleportService")

local TARGET_PLACE_ID = 12345678901234 -- vervang dit door je eigen

local playerToTeleport = Players:GetPlayers()[1] -- krijg de eerste gebruiker in de game

TeleportService:TeleportAsync(TARGET_PLACE_ID, {playerToTeleport})

```

Om de juiste spelers te teleporteren, kun je een [BasePart.Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  of een [ProximityPrompt.Triggered](/docs/nl-nl/reference/engine/classes/ProximityPrompt#Triggered)  evenement gebruiken om een individuele [Player](/docs/nl-nl/reference/engine/classes/Player)  te krijgen. Vervolgens kun je controleren of de speler deel uitmaakt van een team ([Player.Team](/docs/nl-nl/reference/engine/classes/Player#Team) ) of partij ([Player.PartyId](/docs/nl-nl/reference/engine/classes/Player#PartyId) ). Ten slotte kun je [Team:GetPlayers()](/docs/nl-nl/reference/engine/classes/Team#GetPlayers)  of [SocialService:GetPlayersByPartyId()](/docs/nl-nl/reference/engine/classes/SocialService#GetPlayersByPartyId)  gebruiken als je de hele groep wilt teleporteren in plaats van alleen de individuele speler.

Om client-side exploits te verminderen, kun je [TeleportAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportAsync)  alleen aanroepen vanuit serverscripts. De client-side [Teleport()](/docs/nl-nl/reference/engine/classes/TeleportService#Teleport)  methode is verouderd en mag niet worden gebruikt voor nieuw werk, zelfs niet als je plaats is geconfigureerd als "Volledig Open." Voor meer informatie, zie [Configureer veilige teleportatie](#configureer-veilige-teleportatie) .

## [Configureer veilige teleportatie](#configureer-veilige-teleportatie)[](#configureer-veilige-teleportatie)

Drie instellingen regelen de teleportbeveiliging.

| Instelling | | Beschrijving |
| --- | --- |
| (Creator Dashboard) Doelgroep  > Toegangsinstellingen  > Toegangscontrole voor Plaatsen | | Beheert of spelers zich bij elke plaats in je game kunnen voegen of eerst de [startplaats](/docs/nl-nl/production/publishing/publish-games-and-places#maak-games)  moeten betreden. |
| (Creator Dashboard) Plaats  > Toegang  > Directe Toegangscontrole | | Overschrijft je game-niveau Toegangscontrole voor Plaatsen  instelling voor een niet-startplaats. |
| (Studio) Bestand  > Ervaringsinstellingen  > Beveiliging  > Sta Derde Partij Teleportaties toe | | Beheert teleportaties van je game naar games die je niet bezit . Je kunt deze instelling uitgeschakeld laten en toch spelers tussen gepubliceerde games die je bezit teleporteren. |

Toegangscontrole voor Plaatsen  beheert spelers die in  je game teleporteren en is de meest kritische instelling om teleport-gebaseerde exploits te voorkomen.

![Toegangscontrole voor plaatsen op het Creator Hub](https://prod.docsiteassets.roblox.com/assets/players/teleport-access-control.png)

-

Als je Volledig open  kiest, kunnen spelers zich bij elke plaats in je game voegen via teleportaties vanuit elke game, inclusief deeplinks, game-uitnodigingen, het joinen van een vriend, en meer.

Dit is een goede keuze als je game meerdere plaatsen heeft en je wilt dat vrienden elkaar gemakkelijk kunnen joinen, ongeacht welke plaats ze zich bevinden. Als je deze optie niet kiest, zullen spelers die proberen zich bij hun vrienden in niet-startplaatsen te voegen in plaats daarvan de startplaats van je game betreden.

-

Als je Beperkt tot dezelfde universum  kiest, kunnen spelers zich alleen bij niet-startplaatsen voegen via teleportaties binnen je games. Deze instelling staat zowel client- als server-geïnitieerde teleportaties toe.

Dit is een goede keuze als je een legacy game hebt die je niet wilt [migreren naar veilige teleportaties](#migreer-naar-veilige-teleportaties) .

-

Als je Veilig binnen universum alleen  kiest, kunnen spelers zich alleen bij niet-startplaatsen voegen via server-geïnitieerde teleportaties binnen deze game.

Dit is een goede keuze als je game een strikt voortgangssysteem heeft voordat spelers toegang krijgen tot bepaalde gebieden. Het is ook een goede keuze als je game een testplaats heeft waar spelers geen toegang toe zouden moeten hebben of voor plaatsen die uitsluitend gebruik maken van gereserveerde servers.

Uiteindelijk hangt je Toegangscontrole voor Plaatsen  instelling af van het type game dat je wilt bouwen. Veel games hebben geen veilige teleportaties nodig.

### [Migreer naar veilige teleportaties](#migreer-naar-veilige-teleportaties)[](#migreer-naar-veilige-teleportaties)

Als je een bestaande game hebt die client-side teleportaties gebruikt en je wilt server-geïnitieerde teleportaties vereisen, is het doel om alle teleportlogica uit client-scripts en in serverscripts te verplaatsen:

1.

Zoek alle client-scripts die [Teleport()](/docs/nl-nl/reference/engine/classes/TeleportService#Teleport)  aanroepen.

2.

Verander deze aanroepen in plaats daarvan om [remote events](/docs/nl-nl/scripting/events/remote)  te activeren. Alternatief kun je de aanroepen veranderen in plaats daarvan gebruik te maken van [ProximityPrompts](/docs/nl-nl/reference/engine/classes/ProximityPrompt) , [ClickDetectors](/docs/nl-nl/reference/engine/classes/ClickDetector) , of zelfs gewoon het [BasePart.Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  evenement.

3.

Herimplement de teleport in een serverscript met [TeleportAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportAsync) .

4.

Wanneer er geen [Teleport()](/docs/nl-nl/reference/engine/classes/TeleportService#Teleport)  aanroepen meer bestaan, verander Toegangscontrole voor Plaatsen  naar Veilig .

## [Maak aangepaste teleportschermen](#maak-aangepaste-teleportschermen)[](#maak-aangepaste-teleportschermen)

Wanneer een gebruiker een teleportatie activeert, ziet hij het standaard Roblox laadscherm terwijl hij wacht tot de nieuwe plaats is geladen. Indien gewenst, kun je een aangepast teleportscherm toevoegen door [TeleportService:SetTeleportGui()](/docs/nl-nl/reference/engine/classes/TeleportService#SetTeleportGui)  aan te roepen op de client.

Het volgende voorbeeld stelt een gepersonaliseerde [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  in vanuit [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) . Alle scripts binnen de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  worden niet  uitgevoerd.

```

local TeleportService = game:GetService("TeleportService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local teleportGui = ReplicatedStorage.TeleportGui

TeleportService:SetTeleportGui(teleportGui)

```

## [Pas teleportopties aan](#pas-teleportopties-aan)[](#pas-teleportopties-aan)

Je kunt teleportaties aanpassen, zoals [gebruikers naar een specifieke server teleporteren](#teleporteer-naar-specifieke-servers)  en [gebruikersgegevens samen met teleportaties verzenden](#stuur-gebruikersgegevens-mee-met-teleportaties) , door de [TeleportOptions](/docs/nl-nl/reference/engine/classes/TeleportOptions)  instantie in te stellen en deze door te geven aan de [TeleportService:TeleportAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportAsync)  methode.

### [Teleporteer naar specifieke servers](#teleporteer-naar-specifieke-servers)[](#teleporteer-naar-specifieke-servers)

Om gebruikers naar specifieke servers te teleporteren, stel je de doelsserver in met [TeleportOptions](/docs/nl-nl/reference/engine/classes/TeleportOptions)  en geef je deze door aan de [TeleportAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportAsync)  methode. Als je geen server opgeeft, worden gebruikers naar een openbare server geteleporteerd; de informatie van de eerste gebruiker in de lijst wordt gebruikt voor matchmaking.

Om gebruikers naar een specifieke openbare server te teleporteren, stel je de [TeleportOptions.ServerInstanceId](/docs/nl-nl/reference/engine/classes/TeleportOptions#ServerInstanceId)  eigenschap in als een geldige instantie-ID, wat een unieke identificatie is voor een openbare server.

```

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.ServerInstanceId = targetServerId

```

Om gebruikers naar een gereserveerde server  te teleporteren, genereer je een GUID met [HttpService:GenerateGUID(false)](/docs/nl-nl/reference/engine/classes/HttpService#GenerateGUID)  en stel je [TeleportOptions.ReservedServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#ReservedServerId)  in. De eerste teleportatie met een nieuwe ID creëert de server; het hergebruiken van dezelfde ID leidt volgende teleportaties naar die server.

```

local HttpService = game:GetService("HttpService")

local TeleportService = game:GetService("TeleportService")

local TARGET_PLACE_ID = 12345678901234

local reservedServerId = HttpService:GenerateGUID(false)

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.ReservedServerId = reservedServerId

TeleportService:TeleportAsync(TARGET_PLACE_ID, {player}, teleportOptions)

```

Om gebruikers naar een VIP (privé) server  te teleporteren, stel je [TeleportOptions.VipServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#VipServerId)  in op de [DataModel.PrivateServerId](/docs/nl-nl/reference/engine/classes/DataModel#PrivateServerId)  van de doel VIP server:

```

-- De PrivateServerId van de bestemming VIP server, bijvoorbeeld gedragen

-- in de teleportgegevens van de speler of gelezen uit een gegevensopslag

local vipServerId = player:GetJoinData().TeleportData.vipServerId

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.VipServerId = vipServerId

```

Wanneer je gebruikers naar een andere plaats binnen dezelfde ervaring teleport, stel je [TeleportOptions.VipServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#VipServerId)  in op game.PrivateServerId  als je wilt dat ze in dezelfde VIP server blijven:

```

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions.VipServerId = game.PrivateServerId

```

Voor meer informatie over gereserveerde en VIP server teleportpatronen, inclusief het hergebruiken van server-ID's en migreren van legacy toegangscodes, zie [Teleport naar privéservers](/docs/nl-nl/projects/teleport-private-servers) .

### [Stuur gebruikersgegevens mee met teleportaties](#stuur-gebruikersgegevens-mee-met-teleportaties)[](#stuur-gebruikersgegevens-mee-met-teleportaties)

Het teleporteren van een gebruiker tussen plaatsen verwerpt alle lokale gegevens die aan die gebruiker zijn gekoppeld. Je kunt de volgende benaderingen gebruiken om gegevenspersistentie tussen plaatsen te beheren:

-

Als je game veilige  gebruikersgegevens gebruikt, zoals in-game valuta of inventaris, implementeer dan [gegevensopslag](/docs/nl-nl/../cloud-services/data-stores)  of [geheugenopslag](/docs/nl-nl/cloud-services/memory-stores)  om gegevens van plaats naar plaats te behouden.

-

Om basis niet-veilige  gegevens van plaats naar plaats te verzenden, roep je [TeleportOptions:SetTeleportData()](/docs/nl-nl/reference/engine/classes/TeleportOptions#SetTeleportData)  aan voordat je deze doorgeeft aan [TeleportAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportAsync) . Verzend geen  veilige gegevens met deze methode; de gegevens zijn zichtbaar voor de client en niet versleuteld.

```

local teleportData = {

    randomNumber = RNG:NextInteger(1, 100),

}

local teleportOptions = Instance.new("TeleportOptions")

teleportOptions:SetTeleportData(teleportData)

```

Om alle gegevens op te halen wanneer een gebruiker aankomt op de nieuwe plaats na een teleport, gebruik je de [Player:GetJoinData()](/docs/nl-nl/reference/engine/classes/Player#GetJoinData)  functie, die een woordenboek retourneert met een TeleportData  sleutel.

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

    local joinData = player:GetJoinData()

    local teleportData = joinData.TeleportData

    local randomNumber = teleportData.randomNumber

    print(player.Name .. " is binnengekomen met het nummer " .. randomNumber)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Om alleen de teleportgegevens aan de client op te halen, kun je [TeleportService:GetLocalPlayerTeleportData()](/docs/nl-nl/reference/engine/classes/TeleportService#GetLocalPlayerTeleportData)  gebruiken.

## [Test teleportaties in Studio](#test-teleportaties-in-studio)[](#test-teleportaties-in-studio)

Je kunt [TeleportAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportAsync)  teleportaties testen in de Test  en Team Test  modi van Studio zonder je ervaring te publiceren. Wanneer een teleport tijdens een test wordt uitgevoerd, opent de bestemmingsplaats als een nieuwe testserver, zodat je zowel de oorsprong als de bestemmingsplaatsen in Studio kunt debuggen. Studio-tools zoals serverinspectie, de debugger (inclusief breakpoints) en de apparaat-simulator worden overgedragen naar de bestemmingsplaats. Je kunt ook teleportaties testen in [Build](/docs/nl-nl/ai/build)  en via playtestautomatisering in de [Studio MCP server](/docs/nl-nl/studio/mcp) .

Het testen van teleportaties ondersteunt alleen [TeleportAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportAsync) . Verouderde methoden zoals [Teleport()](/docs/nl-nl/reference/engine/classes/TeleportService#Teleport) , [TeleportPartyAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportPartyAsync) , en TeleportToPlaceAsync()  worden niet ondersteund in testen. Als je game deze methoden nog gebruikt, zie [Migreer naar veilige teleportaties](#migreer-naar-veilige-teleportaties) .

### [Bekende beperkingen](#bekende-beperkingen)[](#bekende-beperkingen)

Een paar gedragingen verschillen tussen testen en productie:

-

[PrivateServerId](/docs/nl-nl/reference/engine/classes/DataModel#PrivateServerId)  en [JobId](/docs/nl-nl/reference/engine/classes/DataModel#JobId) : In Test  modus zijn beide altijd leeg, zelfs voor privéservers. In Team Test  is elke server privé, dus PrivateServerId  is nooit leeg, zelfs niet voor teleportaties naar openbare servers. Code die controleert of PrivateServerId  leeg is, gedraagt zich anders in Team Test dan in productie.

-

[ReservedServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#ReservedServerId)  vs. PrivateServerId : Deze waarden kunnen verschillen in Team Test, hoewel ze overeenkomen in productie. Om meer spelers naar dezelfde gereserveerde server te sturen, hergebruik je de originele ReservedServerId , niet de PrivateServerId  van de bestemmingsserver.

-

VIP teleportaties : Teleportaties die [VipServerId](/docs/nl-nl/reference/engine/classes/TeleportOptions#VipServerId)  gebruiken, falen in testen omdat Team Test servers geen eigenaar hebben.

-

Alleen dezelfde ervaring : Je kunt alleen teleporteren tussen plaatsen die de [GameId](/docs/nl-nl/reference/engine/classes/DataModel#GameId)  van de startplaats delen.

-

Niet-ondersteunde methoden : [GetPlayerPlaceInstanceAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#GetPlayerPlaceInstanceAsync)  werkt niet in testen.

## [Behandel mislukte teleportaties](#behandel-mislukte-teleportaties)[](#behandel-mislukte-teleportaties)

Net als bij elke API-aanroep die netwerkverzoeken omvat, kunnen teleportaties mislukken en een fout genereren. Wikkel ze in beschermde aanroepen ([pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall) ). Sommige mislukkingen profiteren van herhalingen, vooral die met gereserveerde servers, dus we raden aan om een aantal keren opnieuw te proberen bij een mislukking.

Zelfs als een aanroep succesvol is en de teleportatie wordt geïnitieerd, kan deze nog steeds op het laatste moment mislukken zonder een fout te genereren en de gebruiker in de server achterlaten. Wanneer dit gebeurt, wordt het [TeleportService.TeleportInitFailed](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportInitFailed)  evenement geactiveerd.

Het volgende voorbeeld [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  retourneert een enkele SafeTeleport  functie die spelers in een beschermde aanroep met herhalingslogica teleporteert. Het heeft ook een handleFailedTeleport  functie om om te gaan met situaties waarin de aanroep succesvol was, maar de teleportatie niet plaatsvond.

```

local TeleportService = game:GetService("TeleportService")

local ATTEMPT_LIMIT = 5

local RETRY_DELAY = 1

local FLOOD_DELAY = 15

local function SafeTeleport(placeId, players, options)

    local attemptIndex = 0

    local success, result -- definieer pcall resultaten buiten de lus zodat resultaten later kunnen worden gerapporteerd

    repeat

        success, result = pcall(function()

            return TeleportService:TeleportAsync(placeId, players, options) -- teleport de gebruiker in een beschermde aanroep om fouten te voorkomen

        end)

        attemptIndex += 1

        if not success then

            task.wait(RETRY_DELAY)

        end

    until success or attemptIndex == ATTEMPT_LIMIT -- stop met proberen te teleporteren als de aanroep succesvol was, of als de herhalingslimiet is bereikt

    if not success then

        warn(result) -- print de reden van de mislukking naar de output

    end

    return success, result

end

local function handleFailedTeleport(player, teleportResult, errorMessage, targetPlaceId, teleportOptions)

    if teleportResult == Enum.TeleportResult.Flooded then

        task.wait(FLOOD_DELAY)

    elseif teleportResult == Enum.TeleportResult.Failure then

        task.wait(RETRY_DELAY)

    else

        -- als de teleportatie ongeldig is, rapporteer de fout in plaats van opnieuw te proberen

        error(("Ongeldige teleportatie [%s]: %s"):format(teleportResult.Name, errorMessage))

    end

    SafeTeleport(targetPlaceId, {player}, teleportOptions)

end

TeleportService.TeleportInitFailed:Connect(handleFailedTeleport)

return SafeTeleport

```

De SafeTeleport  functie ontvangt dezelfde argumenten als de [TeleportAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportAsync)  functie. Je kunt het volgende script gebruiken met de SafeTeleport  functie om teleportaties vanuit elke plek in je game uit te voeren:

```

local Players = game:GetService("Players")

local TeleportService = game:GetService("TeleportService")

local ServerScriptService = game:GetService("ServerScriptService")

local SafeTeleport = require(ServerScriptService.SafeTeleport)

local PLACE_TO_TELEPORT_TO = 12345678

local function teleport(touchPart)

    local playerToTeleport = game.Players:GetPlayerFromCharacter(touchPart.Parent)

    if playerToTeleport then

        SafeTeleport(PLACE_TO_TELEPORT_TO, {playerToTeleport})

    end

end

script.Parent.Touched:Connect(teleport)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
