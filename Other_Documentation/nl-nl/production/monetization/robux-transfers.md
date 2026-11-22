<!-- Source: https://create.roblox.com/docs/nl-nl/production/monetization/robux-transfers -->

Robux-overdrachten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Verdienen](/docs/nl-nl/production/monetization)

# Robux-overdrachten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Robux-overdrachten  stellen [Roblox Plus](/docs/nl-nl/production/monetization/roblox-plus#verdien-aan-robux-overdrachten)  abonnees in staat om Robux rechtstreeks naar andere gebruikers te sturen.

Om overdrachten in je game te ondersteunen, roep je [PromptRobuxTransferAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptRobuxTransferAsync)  aan om de overdracht prompt te openen en gebruik je [BindReceiptHandler](/docs/nl-nl/reference/engine/classes/MarketplaceService#BindReceiptHandler)  om overdrachtsontvangsten te verwerken. Wanneer een abonnee een overdracht voltooit, verdient je game 10%  van de verzonden Robux en ontvangt de ontvanger de resterende 90% . Bijvoorbeeld, een overdracht van 100 Robux betaalt 90 Robux aan de ontvanger en 10 Robux aan je game.

Robux die je game verdient uit overdrachten is in aanmerking voor het DevEx-programma . Roblox neemt geen vergoeding voor deze overdrachten.

Bij het instellen van overdrachten in je game moet het bedrag tussen de 10 en 500 Robux per transactie liggen.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/roblox-plus/TransferRobuxPrompt.png)

Als maker heb je geen toegang tot overdrachtsdetails of controle over de uitvoering. Alle Robux-overdrachten worden verwerkt en beheerd door het Roblox-platform, en alle acties van de afzender en ontvanger ondergaan dezelfde veiligheids- en geschiktheidcontroles. Binnen je game worden overdrachten voltooid via een door Roblox gecontroleerde gebruikersinterface om ervoor te zorgen dat ze veilig en beleidsconform zijn.

## [Robux-overdrachten aanvragen](#robux-overdrachten-aanvragen)[](#robux-overdrachten-aanvragen)

Om een Robux-overdracht binnen je game te starten:

1.

Roep [PromptRobuxTransferAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptRobuxTransferAsync)  aan vanuit een server-side script.

2.

Geef de vereiste parameters door:

-

sender : De speler die de overdracht initieert.

-

receiverUserId : De gebruikers-ID van de ontvanger.

-

amount : Het bedrag aan Robux dat je wilt overdragen.

3.

Bewaar de geretourneerde transferRequestId  die de overdrachtsaanvraag identificeert en kan worden gebruikt om de overdracht later te loggen of te correleren met ontvangsten.

Het volgende voorbeeld initieert een Robux-overdracht tussen twee gebruikers:

```

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

-- Verzendt Robux wanneer een gebruiker een RemoteEvent activeert

local transferEvent = game.ReplicatedStorage:WaitForChild("RequestTransfer")

transferEvent.OnServerEvent:Connect(function(sender, receiverUserId, amount)

	-- Valideert invoer

	if not sender or not sender:IsA("Player") then

		return

	end

	if typeof(receiverUserId) ~= "number" or receiverUserId <= 0 then

		warn("Ongeldige receiverUserId")

		return

	end

	if typeof(amount) ~= "number" or amount <= 0 then

		warn("Ongeldig bedrag")

		return

	end

	local success, result = pcall(function()

		return MarketplaceService:PromptRobuxTransferAsync(sender, receiverUserId, amount)

	end)

	if success then

		print(`Overdracht geïnitieerd met TransferRequestId: {result}`)

	else

		warn(`Overdracht mislukt: {result}`)

	end

end)

```

## [Ontvangst van overdrachten verwerken](#ontvangst-van-overdrachten-verwerken)[](#ontvangst-van-overdrachten-verwerken)

Na een succesvolle overdracht genereert Roblox ontvangsten voor zowel de afzender als de ontvanger. Je kunt deze ontvangsten verwerken met [BindReceiptHandler](/docs/nl-nl/reference/engine/classes/MarketplaceService#BindReceiptHandler)  om te bevestigen dat de overdracht succesvol is voltooid.

Om Plus-abonnees aan te moedigen Robux binnen je game over te dragen, kun je items of andere voordelen aanbieden voor elke succesvolle overdracht. Als je dat doet, verwerk dan de ontvangst voordat je de beloning toekent om ervoor te zorgen dat deze alleen wordt gegeven voor voltooide overdrachten.

Om Robux-overdrachtsontvangsten te verwerken:

1.

Gebruik [BindReceiptHandler](/docs/nl-nl/reference/engine/classes/MarketplaceService#BindReceiptHandler)  om een handler te registreren voor [RobuxTransferSender](/docs/nl-nl/reference/engine/enums/ReceiptType#RobuxTransferSender) , die ontvangsten behandelt voor de gebruiker die de overdracht heeft geïnitieerd.

2.

Registreer een tweede handler voor [RobuxTransferReceiver](/docs/nl-nl/reference/engine/enums/ReceiptType#RobuxTransferReceiver) , die ontvangsten behandelt voor de gebruiker die de Robux heeft ontvangen.

3.

Inspecteer in elke handler de ontvangstinformatie, inclusief PlayerId  en TransferRequestId . Beide ontvangsttypes bevatten een TransferRequestId  die overeenkomt met de transferRequestId  die is geretourneerd door PromptRobuxTransferAsync .

4.

Geef een [Enum.ReceiptDecision](/docs/nl-nl/reference/engine/enums/ReceiptDecision)  waarde terug vanuit je handler:

-

Geef [Processed](/docs/nl-nl/reference/engine/enums/ReceiptDecision#Processed)  terug nadat je de ontvangst hebt afgehandeld. Dit markeert de ontvangst als voltooid en bevestigt dat de Robux-overdracht succesvol was.

-

Geef [NotProcessedYet](/docs/nl-nl/reference/engine/enums/ReceiptDecision#NotProcessedYet)  terug als de ontvangst nog niet kan worden verwerkt (bijvoorbeeld als de gebruiker niet meer op de server is). Dit houdt de ontvangst onopgelost zodat deze later kan worden afgeleverd (bijvoorbeeld wanneer de gebruiker weer bij de server komt).

Het volgende voorbeeld registreert handlers voor zowel afzender- als ontvangerontvangsten:

```

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

-- Behandelt afzenderontvangsten (de gebruiker die de Robux heeft verzonden)

local senderConnection = MarketplaceService:BindReceiptHandler(

	Enum.ReceiptType.RobuxTransferSender,

	function(receiptInfo)

		local player = Players:GetPlayerByUserId(receiptInfo.PlayerId)

		if not player then

			-- Gebruiker heeft de server verlaten - ontvangstverwerking wordt uitgesteld totdat de gebruiker weer bij de server komt

			return Enum.ReceiptDecision.NotProcessedYet

		end

		print(`{player.Name} heeft Robux verzonden (TransferRequestId: {receiptInfo.TransferRequestId})`)

		-- Je kunt hier elke afzenderzijde erkenning geven of de UI bijwerken

		return Enum.ReceiptDecision.Processed

	end

)

-- Behandelt ontvangerontvangsten (de gebruiker die de Robux heeft ontvangen)

local receiverConnection = MarketplaceService:BindReceiptHandler(

	Enum.ReceiptType.RobuxTransferReceiver,

	function(receiptInfo)

		local player = Players:GetPlayerByUserId(receiptInfo.PlayerId)

		if not player then

			return Enum.ReceiptDecision.NotProcessedYet

		end

		print(`{player.Name} heeft Robux ontvangen (TransferRequestId: {receiptInfo.TransferRequestId})`)

		-- Je kunt hier elke ontvangerzijde voordelen geven of de UI bijwerken

		return Enum.ReceiptDecision.Processed

	end

)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
