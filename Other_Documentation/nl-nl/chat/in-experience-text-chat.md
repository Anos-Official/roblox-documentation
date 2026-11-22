<!-- Source: https://create.roblox.com/docs/nl-nl/chat/in-experience-text-chat -->

Overzicht van tekstchat | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Chat
6. /
7. [Tekstchat](/docs/nl-nl/chat/in-experience-text-chat)

# Overzicht van tekstchat

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox biedt tekstgebaseerde messaging tussen spelers in live sessies via [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService) , een singleton klasse die verantwoordelijk is voor het beheren van het algehele chatsysteem, inclusief chatberichtfiltering, moderatie en gebruikersrechten. Deze service heeft zijn standaardfunctionaliteit en biedt ook een set methoden en evenementen voor het uitbreiden en aanpassen van chat, zoals het afleveren van berichten op basis van [aangepaste vereisten](#voorwaardelijk-berichten-afleveren) , het toevoegen van speciale rechten of moderatie aan specifieke spelers, en het creëren van [aangepaste commando's](/docs/nl-nl/chat/examples/custom-text-chat-commands)  om specifieke acties uit te voeren.

Wanneer [platform-geïntegreerde chat](/docs/nl-nl/chat/platform-integrated-chat)  is ingeschakeld, moet aangepaste chat gebruik maken van de native systemen van Roblox, en is de inhoud van berichten niet toegankelijk in de code.

## [UI-configuratie](#ui-configuratie)[](#ui-configuratie)

[TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  biedt een standaard UI die kan worden aangepast aan de behoeften van jouw game. Schakel een van deze configuraties uit om het bijbehorende UI-element te verbergen. Indien gewenst, kun je deze UI-elementen ook vervangen door aangepaste interfaces:

-

[ChatWindowConfiguration](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration)

-

[ChatInputBarConfiguration](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration)

-

[ChannelTabsConfiguration](/docs/nl-nl/reference/engine/classes/ChannelTabsConfiguration)

-

[BubbleChatConfiguration](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration)

Voor meer informatie, zie [Chatvenster](/docs/nl-nl/chat/chat-window)  en [Bubble chat](/docs/nl-nl/chat/bubble-chat) .

## [Kanalen, berichten en commando's](#kanalen-berichten-en-commandos)[](#kanalen-berichten-en-commandos)

-

[TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel)  — Tekstkanalen verzenden door gebruikers verzonden berichten van de client naar de server, die ze vervolgens aan andere gebruikers toont op basis van rechten. Tekstkanalen moeten aan [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  worden gekoppeld om te functioneren.

Als [TextChatService.CreateDefaultTextChannels](/docs/nl-nl/reference/engine/classes/TextChatService#CreateDefaultTextChannels)  is ingesteld op true , maakt de service automatisch twee tekstkanalen aan, RBXGeneral  en RBXSystem . Je kunt ook handmatig extra [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel)  instanties aanmaken en deze aan [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  koppelen.

Het hebben van meerdere [TextChannels](/docs/nl-nl/reference/engine/classes/TextChannel)  met dezelfde naam kan onbedoeld gedrag veroorzaken met het standaard [chatvenster](/docs/nl-nl/chat/chat-window) .

-

[TextSource](/docs/nl-nl/reference/engine/classes/TextSource)  — Een gebruiker in een [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel) . Tekstbronnen worden direct aan de [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel)  gekoppeld wanneer [AddUserAsync()](/docs/nl-nl/reference/engine/classes/TextChannel#AddUserAsync)  wordt aangeroepen. Tekstbronnen bevatten gedetailleerde rechten van een gebruiker in het kanaal, zoals hun mogelijkheid om berichten te verzenden. Als een enkele gebruiker in meerdere tekstkanalen zit, zijn ze gekoppeld aan meerdere tekstbronnen.

-

[TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)  — Een bericht in een tekstkanaal. Chatberichten bevatten basisinformatie zoals de afzender van het bericht, het originele bericht, het gefilterde bericht en de tijdstempel van de creatie.

-

[TextChatCommand](/docs/nl-nl/reference/engine/classes/TextChatCommand)  — Laat gebruikers specifieke acties of gedragingen aanroepen door berichten te verzenden die overeenkomen met de [PrimaryAlias](/docs/nl-nl/reference/engine/classes/TextChatCommand#PrimaryAlias)  of [SecondaryAlias](/docs/nl-nl/reference/engine/classes/TextChatCommand#SecondaryAlias)  eigenschappen. Chatcommando's moeten aan [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  worden gekoppeld om te functioneren.

Als [TextChatService.CreateDefaultCommands](/docs/nl-nl/reference/engine/classes/TextChatService#CreateDefaultCommands)  is ingesteld op true , worden standaard chatcommando's automatisch aangemaakt. Je kunt ook handmatig extra [TextChatCommand](/docs/nl-nl/reference/engine/classes/TextChatCommand)  instanties aanmaken en deze aan [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  koppelen.

## [Chat stroomdiagram](#chat-stroomdiagram)[](#chat-stroomdiagram)

Tekstchat gebruikt het [client-server](/docs/nl-nl/projects/client-server)  model, met een verzendende client , de server , en ontvangende clients .

 ![Een stroomdiagram voor tekstchat in de game.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-Workflow.png)

1.

Een speler verzendt een bericht vanaf hun lokale apparaat, wat de [TextChannel:SendAsync()](/docs/nl-nl/reference/engine/classes/TextChannel#SendAsync)  methode activeert. Deze methode verwerkt het bericht en bepaalt of het een chatcommando of een regulier chatbericht is.

-

Als het bericht een chatcommando is, wordt het [TextChatCommand.Triggered](/docs/nl-nl/reference/engine/classes/TextChatCommand#Triggered)  evenement geactiveerd om de gedefinieerde actie uit te voeren. Geen verdere stappen zijn vereist.

-

Als het bericht een regulier chatbericht is, wordt het [TextChatService.SendingMessage](/docs/nl-nl/reference/engine/classes/TextChatService#SendingMessage)  evenement geactiveerd om het bericht aan de afzender op de verzendende client weer te geven. Tegelijkertijd geeft [TextChannel:SendAsync()](/docs/nl-nl/reference/engine/classes/TextChannel#SendAsync)  het bericht door aan de server.

2.

De server activeert [TextChannel.ShouldDeliverCallback](/docs/nl-nl/reference/engine/classes/TextChannel#ShouldDeliverCallback)  om te bepalen of het bericht aan andere spelers moet worden afgeleverd op basis van rechten en de filteringseisen van de Roblox-gemeenschap.

3.

Als [TextChannel.ShouldDeliverCallback](/docs/nl-nl/reference/engine/classes/TextChannel#ShouldDeliverCallback)  bepaalt dat het bericht in aanmerking komt voor aflevering aan andere spelers, past de server eventuele filters toe en activeert [TextChannel.OnIncomingMessage](/docs/nl-nl/reference/engine/classes/TextChannel#OnIncomingMessage)  twee keer:

1.

De eerste keer is op de verzendende client en geeft aan dat de server het bericht verwerkt via het [TextChatService.MessageReceived](/docs/nl-nl/reference/engine/classes/TextChatService#MessageReceived)  evenement. Dit evenement vervangt het lokale bericht op de verzendende client met het verwerkte bericht van de server. Het bericht is identiek als het origineel geen filtering vereiste.

2.

De tweede keer is op de ontvangende clients, wat het [TextChatService.MessageReceived](/docs/nl-nl/reference/engine/classes/TextChatService#MessageReceived)  evenement activeert om het bericht aan andere spelers weer te geven.

## [Tekstchat hooks en callbacks](#tekstchat-hooks-en-callbacks)[](#tekstchat-hooks-en-callbacks)

De [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  API moedigt een duidelijke scheiding aan van het uiterlijk en de aflevering van chatberichten. Meerdere instanties van het tekstchatsysteem bieden hooks en callbacks om te formatteren op gecentraliseerde, duidelijke locaties.

Alle callbacks worden verwacht niet-blokkerende functies te zijn. Blokkeren of wachten op een reactie in een callback blokkeert het chatsysteem en kan onvoorspelbaar gedrag veroorzaken.

 ![Een stroomdiagram van de volgorde van de TextChatService callbacks](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/TextChatService-Callbacks.png)

| Callback | | Return Value |
| --- | --- |
| [TextChannel.ShouldDeliverCallback](/docs/nl-nl/reference/engine/classes/TextChannel#ShouldDeliverCallback) | | boolean |
| [TextChatService.OnIncomingMessage](/docs/nl-nl/reference/engine/classes/TextChatService#OnIncomingMessage) | | [TextChatMessageProperties](/docs/nl-nl/reference/engine/classes/TextChatMessageProperties) |
| [TextChannel.OnIncomingMessage](/docs/nl-nl/reference/engine/classes/TextChannel#OnIncomingMessage) | | [TextChatMessageProperties](/docs/nl-nl/reference/engine/classes/TextChatMessageProperties) |
| [TextChatService.OnBubbleAdded](/docs/nl-nl/reference/engine/classes/TextChatService#OnBubbleAdded) | | [BubbleChatMessageProperties](/docs/nl-nl/reference/engine/classes/BubbleChatMessageProperties) |
| [TextChatService.OnChatWindowAdded](/docs/nl-nl/reference/engine/classes/TextChatService#OnChatWindowAdded) | | [ChatWindowMessageProperties](/docs/nl-nl/reference/engine/classes/ChatWindowMessageProperties) |

### [Voorwaardelijk berichten afleveren](#voorwaardelijk-berichten-afleveren)[](#voorwaardelijk-berichten-afleveren)

De [TextChannel.ShouldDeliverCallback](/docs/nl-nl/reference/engine/classes/TextChannel#ShouldDeliverCallback)  callback moet alleen op de server worden gedefinieerd. De callback wordt geactiveerd voor elke [TextSource](/docs/nl-nl/reference/engine/classes/TextSource)  kind van het tekstkanaal wanneer een bericht wordt verzonden om te bepalen of het bericht moet worden afgeleverd. Deze callback kan worden gebruikt om aangepaste berichtafleveringslogica te implementeren die kan afhangen van extra gameplaycontext, zoals:

-

[Proximity-gebaseerde chat](/docs/nl-nl/chat/examples/proximity-chat)  waarbij gebruikers alleen berichten kunnen verzenden naar degenen die dichtbij hen zijn.

-

Voorkomen dat gebruikers met bepaalde attributen berichten naar anderen kunnen verzenden.

### [Pas de weergave van berichten aan](#pas-de-weergave-van-berichten-aan)[](#pas-de-weergave-van-berichten-aan)

De standaard [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  UI is afhankelijk van [rijke tekst](/docs/nl-nl/ui/rich-text)  om te formatteren en aan te passen hoe berichten worden weergegeven. Je kunt de volgende callbacks gebruiken om berichten te formatteren voordat ze aan gebruikers worden weergegeven, bijvoorbeeld om kleuren of [chat-tags](/docs/nl-nl/chat/examples/group-chat-tags)  aan gebruikersnamen toe te voegen of de inhoud van berichten te formatteren.

De volgende callbacks worden aangeroepen voor elke [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)  die op het punt staat om weergegeven te worden, waardoor je het uiterlijk van het chatvenster kunt aanpassen op basis van de inhoud van [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel) , [TextSource](/docs/nl-nl/reference/engine/classes/TextSource)  of [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage) . Wanneer een client een bericht verzendt, worden deze callbacks eenmaal aangeroepen wanneer het bericht naar de server wordt verzonden en de [TextChatMessage.Status](/docs/nl-nl/reference/engine/classes/TextChatMessage#Status)  waarde zal [Enum.TextChatMessageStatus.Sending](/docs/nl-nl/reference/engine/enums/TextChatMessageStatus#Sending)  zijn. Zodra het bericht door de server is ontvangen en aan andere gebruikers wordt afgeleverd, ontvangt de verzendende client het bericht opnieuw met een bijgewerkte [Enum.TextChatMessageStatus](/docs/nl-nl/reference/engine/enums/TextChatMessageStatus)  waarde.

-

[TextChatService.OnIncomingMessage](/docs/nl-nl/reference/engine/classes/TextChatService#OnIncomingMessage)  — Deze callback moet alleen op de client worden gedefinieerd. De callback wordt geactiveerd wanneer een bericht wordt ontvangen, hetzij van de server of als de lokale client net een bericht heeft verzonden. De callback wordt aangeroepen voor elke [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)  die wordt ontvangen van alle [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel)  instanties en is de eerste die het bericht verwerkt voordat het aan de gebruiker wordt weergegeven.

-

[TextChannel.OnIncomingMessage](/docs/nl-nl/reference/engine/classes/TextChannel#OnIncomingMessage)  — Deze callback moet alleen op de client worden gedefinieerd. De callback wordt geactiveerd wanneer een bericht van de server wordt ontvangen. De callback wordt aangeroepen voor elke [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)  die wordt ontvangen van de [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel) . Standaard [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel)  instanties die zijn aangemaakt vanuit [TextChatService.CreateDefaultTextChannels](/docs/nl-nl/reference/engine/classes/TextChatService#CreateDefaultTextChannels)  hebben deze callback gedefinieerd en kunnen worden overschreven.

-

[TextChatService.OnBubbleAdded](/docs/nl-nl/reference/engine/classes/TextChatService#OnBubbleAdded)  — Deze callback moet alleen op de client worden gedefinieerd. Gebruik het om het uiterlijk van chatbellen aan te passen, onafhankelijk van het uiterlijk van het bericht in de chatvenster UI.

-

[TextChatService.OnChatWindowAdded](/docs/nl-nl/reference/engine/classes/TextChatService#OnChatWindowAdded)  — Deze callback moet alleen op de client worden gedefinieerd. Gebruik het om het uiterlijk van chatberichten in de chatvenster UI aan te passen, onafhankelijk van het uiterlijk van het bericht in chatbellen.

## [Migreren van legacy chat](#migreren-van-legacy-chat)[](#migreren-van-legacy-chat)

Deze sectie helpt je bij het migreren van het legacy chatsysteem door alternatieve methoden te bieden voor het implementeren van veelvoorkomende chatfunctionaliteiten en -gedragingen met behulp van [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService) .

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, selecteer [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService) .

2.

In het [Properties](/docs/nl-nl/studio/properties)  venster, zoek de [ChatVersion](/docs/nl-nl/reference/engine/classes/TextChatService#ChatVersion)  dropdown en selecteer [TextChatService](/docs/nl-nl/reference/engine/enums/ChatVersion) .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/TextChatService-ChatVersion-TextChatService.png)

### [Basisfunctionaliteiten](#basisfunctionaliteiten)[](#basisfunctionaliteiten)

Hoewel beide systemen dezelfde basis chatfunctionaliteiten delen, zijn [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  implementaties over het algemeen duurzamer en gemakkelijker te itereren.

| Functionaliteit | | Legacy chat | | TextChatService | | Verschillen |
| Verzend een chatbericht | | [Players:Chat()](/docs/nl-nl/reference/engine/classes/Players#Chat) | | [TextChannel:SendAsync()](/docs/nl-nl/reference/engine/classes/TextChannel#SendAsync) | | De [SendAsync()](/docs/nl-nl/reference/engine/classes/TextChannel#SendAsync)  methode ondersteunt meer geavanceerde chatfuncties, zoals rijke tekstopmaak en berichtprioriteit. Het bevat ook ingebouwde filtering om te helpen ongepaste berichten te voorkomen. |
| Implementeer messaging callbacks | | [Chat:InvokeChatCallback()](/docs/nl-nl/reference/engine/classes/Chat#InvokeChatCallback)
[Chat:RegisterChatCallback()](/docs/nl-nl/reference/engine/classes/Chat#RegisterChatCallback) | | [TextChatService.SendingMessage](/docs/nl-nl/reference/engine/classes/TextChatService#SendingMessage)
[TextChatService.OnIncomingMessage](/docs/nl-nl/reference/engine/classes/TextChatService#OnIncomingMessage) | | Het legacy chatsysteem bindt een functie aan chat systeem evenementen voor het afleveren van berichten. De twee methoden van TextChatService  bieden betere flexibiliteit en aanpassing. |
| Voeg aangepaste chatcommando's toe | | ChatService/ChatCommand  module | | [TextChatCommand](/docs/nl-nl/reference/engine/classes/TextChatCommand) | | TextChatService  heeft een speciale klasse voor tekstcommando's in plaats van een legacy chatmodule te gebruiken. |
| Toon een systeembericht | | [StarterGui:SetCore()](/docs/nl-nl/reference/engine/classes/StarterGui#SetCore)  met ChatMakeSystemMessage | | [TextChannel:DisplaySystemMessage()](/docs/nl-nl/reference/engine/classes/TextChannel#DisplaySystemMessage) | | De [TextChannel.OnIncomingMessage](/docs/nl-nl/reference/engine/classes/TextChannel#OnIncomingMessage)  callback kan een [TextChatMessageProperties](/docs/nl-nl/reference/engine/classes/TextChatMessageProperties)  instantie retourneren om het uiterlijk van het bericht aan te passen. |
| Schakel chat uit | | ChatWindow/ChatSettings  module voor het verbergen van het chatvenster | | [ChatWindowConfiguration.Enabled](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#Enabled) | |  |

### [Berichtfiltering](#berichtfiltering)[](#berichtfiltering)

[TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  filtert automatisch chatberichten op basis van de accountinformatie van elke speler, zodat je geen handmatige tekstfiltering hoeft te implementeren voor alle soorten chatberichten.

| Functionaliteit | | Legacy chat | | TextChatService |
| Filter chatbericht voor individuele speler | | [Chat:FilterStringAsync()](/docs/nl-nl/reference/engine/classes/Chat#FilterStringAsync) | | Automatisch |
| Filter uitzending berichten | | [Chat:FilterStringForBroadcast()](/docs/nl-nl/reference/engine/classes/Chat#FilterStringForBroadcast) | | Automatisch |

### [Venster en bubble chat](#venster-en-bubble-chat)[](#venster-en-bubble-chat)

Zowel het [chatvenster](/docs/nl-nl/chat/chat-window)  als de [bubble chat](/docs/nl-nl/chat/bubble-chat)  gedrag en aanpassingsopties van [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  zijn identiek aan die van het legacy chatsysteem. Aangezien het legacy chatsysteem alleen aanpassing toestaat met behulp van chatmodules of de [Players](/docs/nl-nl/reference/engine/classes/Players)  container, biedt de service speciale klassen ([ChatWindowConfiguration](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration)  en [BubbleChatConfiguration](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration) ) om alle eigenschappen van het chatvenster en bubble chat te beheren. Bovendien kun je eenvoudig de eigenschappen van het uiterlijk en gedrag van je bubble chat aanpassen en bekijken met behulp van Studio-instellingen in plaats van dat je ze allemaal moet scripten.

| Functionaliteit | | Legacy chat | | TextChatService |
| Chatvenster inschakelen | | [Chat.LoadDefaultChat](/docs/nl-nl/reference/engine/classes/Chat#LoadDefaultChat)
[Players.ClassicChat](/docs/nl-nl/reference/engine/classes/Players#ClassicChat) | | [ChatWindowConfiguration.Enabled](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#Enabled) |
| Bubble Chat inschakelen | | [Chat.BubbleChatEnabled](/docs/nl-nl/reference/engine/classes/Chat#BubbleChatEnabled)
[Players.BubbleChat](/docs/nl-nl/reference/engine/classes/Players#BubbleChat) | | [BubbleChatConfiguration.Enabled](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration#Enabled) |
| Instellingen voor chatvenster instellen | | [Players:SetChatStyle()](/docs/nl-nl/reference/engine/classes/Players#SetChatStyle) | | [ChatWindowConfiguration](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration) |
| Instellingen voor bubble chat instellen | | [Chat:SetBubbleChatSettings()](/docs/nl-nl/reference/engine/classes/Chat#SetBubbleChatSettings)
[Chat.BubbleChatSettingsChanged()](/docs/nl-nl/reference/engine/classes/Chat#BubbleChatSettingsChanged)
[Players.BubbleChat](/docs/nl-nl/reference/engine/classes/Players#BubbleChat)
[Players:SetChatStyle()](/docs/nl-nl/reference/engine/classes/Players#SetChatStyle) | | [BubbleChatConfiguration](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration) |
| NPC-bellen inschakelen | | [Chat:Chat()](/docs/nl-nl/reference/engine/classes/Chat#Chat) | | [TextChatService:DisplayBubble()](/docs/nl-nl/reference/engine/classes/TextChatService#DisplayBubble) |

### [Migreren van "extra gegevens" van sprekers](#migreren-van-extra-gegevens-van-sprekers)[](#migreren-van-extra-gegevens-van-sprekers)

Het legacy Lua chatsysteem stond ontwikkelaars toe om SetExtraData  op de Speaker  klasse te gebruiken. Deze gegevens werden gebruikt om de naamkleur, chatkleur te formatteren, of om naamlabels toe te passen voor een gegeven spreker.

Legacy Chat System SetExtraData

```

-- Een voorbeeld van het instellen van extra gegevens op een spreker in het legacy chatsysteem

ChatService.SpeakerAdded:Connect(function(playerName)

	local speaker = ChatService:GetSpeaker(playerName)

	speaker:SetExtraData("NameColor", Color3.fromRGB(255, 255, 55))

	speaker:SetExtraData("ChatColor", Color3.fromRGB(212, 175, 55))

	speaker:SetExtraData("Tags", {{TagText = "YourTagName", TagColor = Color3.fromRGB(0, 255, 0)}, {TagText = "OtherTagName", TagColor = Color3.fromRGB(255, 0, 0)}})

end)

```

[TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  heeft geen directe tegenhanger van SetExtraData . Gebruik in plaats daarvan [callbacks](#tekstchat-hooks-en-callbacks)  zoals [OnWindowAdded](/docs/nl-nl/reference/engine/classes/TextChatService#OnWindowAdded)  om het uiterlijk van berichten aan te passen met behulp van rijke tekst op basis van de [TextSource](/docs/nl-nl/reference/engine/classes/TextSource)  van het bericht.

Het volgende is een voorbeeld van het emuleren van de "extra gegevens" van het legacy Lua chat door toegang te krijgen tot attributen op [Player](/docs/nl-nl/reference/engine/classes/Player)  objecten:

TextChatService SetAttributes

```

local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)

	player:SetAttribute("NameColor", Color3.fromRGB(255, 255, 55))

	player:SetAttribute("ChatColor", Color3.fromRGB(212, 175, 55))

	player:SetAttribute("isYourTag", true)

	player:SetAttribute("isOtherTag", true)

end)

```

Vervolgens kun je de [OnChatWindowAdded](/docs/nl-nl/reference/engine/classes/TextChatService#OnChatWindowAdded)  callback gebruiken om het uiterlijk van het chatvenster aan te passen op basis van de attributen die op de speler zijn ingesteld:

TextChatService OnChatWindowAdded

```

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

TextChatService.OnChatWindowAdded = function(textChatMessage)

	local textSource = textChatMessage.TextSource

	if textSource then

		local player = Players:GetPlayerByUserId(textSource.UserId)

		if player then

			local overrideProperties = TextChatService.ChatWindowConfiguration:DeriveNewMessageProperties()

			overrideProperties.PrefixText = textChatMessage.PrefixText

			overrideProperties.Text = textChatMessage.Text

			local nameColor = player:GetAttribute("NameColor")

			if nameColor and typeof(nameColor) == "Color3" then

				overrideProperties.PrefixTextProperties.TextColor3 = nameColor

			end

			local chatColor = player:GetAttribute("ChatColor")

			if chatColor and typeof(chatColor) == "Color3" then

				overrideProperties.TextColor3 = chatColor

			end

			local isYourTag = player:GetAttribute("isYourTag")

			if isYourTag == true then

				overrideProperties.PrefixText = `<font color='rgb(0, 255, 0)'>[YourTag]</font> {overrideProperties.PrefixText}`

			end

			local isOtherTag = player:GetAttribute("isOtherTag")

			if isOtherTag == true then

				overrideProperties.PrefixText = `<font color='rgb(255, 0, 0)'>[OtherTag]</font> {overrideProperties.PrefixText}`

			end

			return overrideProperties

		end

	end

	return nil

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
