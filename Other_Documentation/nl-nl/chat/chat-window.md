<!-- Source: https://create.roblox.com/docs/nl-nl/chat/chat-window -->

Pas het chatvenster aan | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Chat
6. /
7. [Tekstchat](/docs/nl-nl/chat/in-experience-text-chat)

# Pas het chatvenster aan

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het [in-game tekstchat](/docs/nl-nl/chat/in-experience-text-chat)  systeem, aangedreven door [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService) , stelt spelers in staat om gemakkelijk met elkaar te communiceren en te socialiseren in live games. Naast het ondersteunen van de standaard tekstchat, kun je de [frontend gebruikersinterface](#configuratie-van-het-chatvenster)  aanpassen.

## [Configuratie van het chatvenster](#configuratie-van-het-chatvenster)[](#configuratie-van-het-chatvenster)

Het algemene chatvenster bestaat uit:

-

Chatvenster

-

Invoerbalk

-

Kanaaltabs (optioneel)

 ![Kerncomponenten van het tekstchatvenster.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-Window-Components.jpg)

De kanaaltabs zijn standaard uitgeschakeld en elk component kan in Studio of via scripting aan en uit worden gezet:

Studio Scripting

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, vouw de [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  tak uit en selecteer [ChatWindowConfiguration](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration) , [ChatInputBarConfiguration](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration)  of [ChannelTabsConfiguration](/docs/nl-nl/reference/engine/classes/ChannelTabsConfiguration) . Schakel vervolgens het component in of uit in het [Properties](/docs/nl-nl/studio/properties)  venster.

![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/TextChatService-Configuration-Objects.png)

Wanneer [ChannelTabsConfiguration](/docs/nl-nl/reference/engine/classes/ChannelTabsConfiguration)  is ingeschakeld, verschijnt elke standaard [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel)  in een tab zoals uiteengezet in de volgende tabel. Bovendien creëert elke aangepaste [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel)  een tab die overeenkomt met de [Name](/docs/nl-nl/reference/engine/classes/Instance#Name)  eigenschap van het kanaal.

| Standaard kanaal | | Tabnaam |
| --- | --- |
| RBXGeneral | | Algemeen |
| RBXSystem | | Algemeen  (samengevoegd in een enkele tab met RBXGeneral ) |
| RBXTeam | | Team |
| RBXWhisper | | Gebruikersnaam van de andere speler |

### [Uiterlijk van het venster](#uiterlijk-van-het-venster)[](#uiterlijk-van-het-venster)

Het uiterlijk van het algemene chatvenster is aanpasbaar via [ChatWindowConfiguration](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration) .

 ![ChatWindowConfiguration instantie in de Explorer hiërarchie.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/TextChatService-ChatWindowConfiguration.png)

| Eigenschap | | Beschrijving | | Standaard |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#BackgroundColor3) | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  achtergrondkleur van het chatvenster. | | [25, 27, 29] |
| [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#BackgroundTransparency) | | Transparantie van de achtergrond van het chatvenster. | | 0.3 |
| [Enabled](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#Enabled) | | Of het standaard chatvenster moet worden weergegeven. Zet op false  om te verbergen. | | true |
| [FontFace](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#FontFace) | | [Font](/docs/nl-nl/reference/engine/datatypes/Font)  van de tekst in het chatvenster. | | [BuilderSansMedium](/docs/nl-nl/reference/engine/enums/Font#BuilderSansMedium) |
| [TextColor3](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#TextColor3) | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  van de tekst in het chatvenster. | | [255, 255, 255] |
| [TextSize](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#TextSize) | | Grootte van de tekst in het chatvenster. | | 14 |
| [TextStrokeColor3](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#TextStrokeColor3) | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  van de omtrek voor de tekst in het chatvenster. | | [0, 0, 0] |
| [TextStrokeTransparency](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#TextStrokeTransparency) | | Transparantie van de omtrek voor de tekst in het chatvenster. | | 0.5 |
| [HorizontalAlignment](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#HorizontalAlignment) | | Horizontale uitlijning van het chatvenster. | | [Left](/docs/nl-nl/reference/engine/enums/HorizontalAlignment#Left) |
| [VerticalAlignment](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#VerticalAlignment) | | Verticale uitlijning van het chatvenster. | | [Top](/docs/nl-nl/reference/engine/enums/VerticalAlignment#Top) |
| [HeightScale](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#HeightScale) | | Hoogteschaal van het chatvenster ten opzichte van de schermgrootte. | | 1 |
| [WidthScale](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#WidthScale) | | Breedteschaal van het chatvenster ten opzichte van de schermgrootte. | | 1 |

### [Uiterlijk van de invoerbalk](#uiterlijk-van-de-invoerbalk)[](#uiterlijk-van-de-invoerbalk)

Het uiterlijk van de chatinvoerbalk is aanpasbaar via [ChatInputBarConfiguration](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration) .

 ![ChatInputBarConfiguration instantie in de Explorer hiërarchie.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/TextChatService-ChatInputBarConfiguration.png)

| Eigenschap | | Beschrijving | | Standaard |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration#BackgroundColor3) | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  achtergrondkleur van de chatinvoerbalk. | | [25, 27, 29] |
| [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration#BackgroundTransparency) | | Transparantie van de achtergrond van de chatinvoerbalk. | | 0.2 |
| [FontFace](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration#FontFace) | | [Font](/docs/nl-nl/reference/engine/datatypes/Font)  van de chatinvoertekst. | | [BuilderSansMedium](/docs/nl-nl/reference/engine/enums/Font#BuilderSansMedium) |
| [PlaceholderColor3](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration#PlaceholderColor3) | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  van de placeholder chatinvoertekst. | | [178, 178, 178] |
| [TextColor3](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration#TextColor3) | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  van de door de speler ingevoerde chatinvoertekst. | | [255, 255, 255] |
| [TextSize](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration#TextSize) | | Grootte van de chatinvoertekst. | | 14 |
| [TextStrokeColor3](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration#TextStrokeColor3) | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  omtrekkleur van de chatinvoertekst. | | [0, 0, 0] |
| [TextStrokeTransparency](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration#TextStrokeTransparency) | | Transparantie van de omtrek voor de chatinvoertekst. | | 0.5 |
| [AutocompleteEnabled](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration#AutocompleteEnabled) | | Of het tekstchatsysteem autocomplete-opties voor emoji's en [commando's](/docs/nl-nl/chat/in-experience-text-chat)  toont. Emoji's worden automatisch aangevuld door :  gevolgd door niet-witte karakters te typen, terwijl commando's worden automatisch aangevuld door /  te typen. | | true |
| [KeyboardKeyCode](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration#KeyboardKeyCode) | | Extra toets die spelers kunnen indrukken om de focus op de standaard chatinvoerbalk te krijgen. | | [Slash](/docs/nl-nl/reference/engine/enums/KeyCode#Slash) |

### [Uiterlijk van de kanaaltabs](#uiterlijk-van-de-kanaaltabs)[](#uiterlijk-van-de-kanaaltabs)

Het uiterlijk van de kanaaltabs  is aanpasbaar via [ChannelTabsConfiguration](/docs/nl-nl/reference/engine/classes/ChannelTabsConfiguration) .

 ![ChannelTabsConfiguration instantie in de Explorer hiërarchie.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/TextChatService-ChannelTabsConfiguration.png)

| Eigenschap | | Beschrijving | | Standaard |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/ChannelTabsConfiguration#BackgroundColor3) | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  achtergrondkleur van de kanaaltabs. | | [25, 27, 29] |
| [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/ChannelTabsConfiguration#BackgroundTransparency) | | Transparantie van de achtergrond van de kanaaltabs. | | 0 |
| [HoverBackgroundColor3](/docs/nl-nl/reference/engine/classes/ChannelTabsConfiguration#HoverBackgroundColor3) | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  achtergrondkleur van tabs wanneer je eroverheen zweeft. | | [125, 125, 125] |
| [FontFace](/docs/nl-nl/reference/engine/classes/ChannelTabsConfiguration#FontFace) | | [Font](/docs/nl-nl/reference/engine/datatypes/Font)  voor de tekst in kanaaltabs. | | [BuilderSansBold](/docs/nl-nl/reference/engine/enums/Font#BuilderSansBold) |
| [TextColor3](/docs/nl-nl/reference/engine/classes/ChannelTabsConfiguration#TextColor3) | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  van de tekst in een niet-geselecteerde tab. | | [175, 175, 175] |
| [SelectedTabTextColor3](/docs/nl-nl/reference/engine/classes/ChannelTabsConfiguration#SelectedTabTextColor3) | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  van de tekst in een geselecteerde tab. | | [255, 255, 255] |
| [TextSize](/docs/nl-nl/reference/engine/classes/ChannelTabsConfiguration#TextSize) | | Grootte van de tekst in kanaaltabs. | | 18 |
| [TextStrokeColor3](/docs/nl-nl/reference/engine/classes/ChannelTabsConfiguration#TextStrokeColor3) | | [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  omtrekkleur van de tekst in kanaaltabs. | | [0, 0, 0] |
| [TextStrokeTransparency](/docs/nl-nl/reference/engine/classes/ChannelTabsConfiguration#TextStrokeTransparency) | | Transparantie van de omtrek voor tekst in kanaaltabs. | | 1 |

## [Pas berichten aan](#pas-berichten-aan)[](#pas-berichten-aan)

Je kunt het uiterlijk van chatberichtlichamen en -prefixen aanpassen met behulp van [ChatWindowMessageProperties](/docs/nl-nl/reference/engine/classes/ChatWindowMessageProperties)  en [TextChatService.OnChatWindowAdded](/docs/nl-nl/reference/engine/classes/TextChatService#OnChatWindowAdded)  callbacks zonder de bestaande gebruikersinterface te overschrijven. De aanpassingsopties stellen je in staat om het uiterlijk van chatberichten aan te passen aan het thema van je game, en je kunt ook berichten van verschillende gebruikersgroepen sorteren of markeren door prefixen te kleuren of [chat-tags](/docs/nl-nl/chat/examples/group-chat-tags)  toe te voegen.

[ChatWindowMessageProperties](/docs/nl-nl/reference/engine/classes/ChatWindowMessageProperties)  en [OnChatWindowAdded](/docs/nl-nl/reference/engine/classes/TextChatService#OnChatWindowAdded)  beïnvloeden alleen het uiterlijk van berichten in het chatvenster. Om chatbellen aan te passen, zie [Bubble Chat](/docs/nl-nl/chat/bubble-chat) .

### [Kleur gebruikersnamen](#kleur-gebruikersnamen)[](#kleur-gebruikersnamen)

Wanneer een gebruiker een chatbericht verzendt, wordt hun [DisplayName](/docs/nl-nl/reference/engine/classes/Player#DisplayName)  weergegeven als het prefixgedeelte van het bericht. Standaard wordt de naam van elke gebruiker gekleurd op basis van hun [Player.TeamColor](/docs/nl-nl/reference/engine/classes/Player#TeamColor) , maar je kunt de kleuren van chatnamen wijzigen met behulp van [ChatWindowMessageProperties](/docs/nl-nl/reference/engine/classes/ChatWindowMessageProperties)  en [OnChatWindowAdded](/docs/nl-nl/reference/engine/classes/TextChatService#OnChatWindowAdded) . De volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  in [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts)  wijst een vooraf bepaalde kleur toe aan elke gebruiker, waarbij willekeurig wordt gekozen uit een tabel van RGB-kleuren.

 ![Gekleurde gebruikersnaam in het chatvenster.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-User-Name-Colored.png)

LocalScript - Willekeurige gebruikersnaam kleuren

```

local TextChatService = game:GetService("TextChatService")

local chatWindowConfiguration = TextChatService.ChatWindowConfiguration

local nameColors = {

	Color3.fromRGB(255, 0, 0),

	Color3.fromRGB(0, 255, 0),

	Color3.fromRGB(0, 0, 255),

	Color3.fromRGB(255, 255, 0),

}

TextChatService.OnChatWindowAdded = function(message: TextChatMessage)

	local properties = chatWindowConfiguration:DeriveNewMessageProperties()

	local textSource = message.TextSource

	if textSource then

		local index: number = (textSource.UserId % #nameColors) + 1

		local randomColor: Color3 = nameColors[index]

    	properties.PrefixTextProperties = chatWindowConfiguration:DeriveNewMessageProperties()

		properties.PrefixTextProperties.TextColor3 = randomColor

	end

	return properties

end

```

Je kunt ook kleur- en transparantiegradiënten toepassen op de kleur van berichtprefixen met behulp van [UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient) .

 ![Gradiënt gebruikersnaam in het chatvenster.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-User-Name-Gradient.png)

Gradiënt gebruikersnaam kleuren

```

local TextChatService = game:GetService("TextChatService")

local chatWindowConfiguration = TextChatService.ChatWindowConfiguration

local gradient = Instance.new("UIGradient")

gradient.Color = ColorSequence.new{

	ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 0, 0)),

	ColorSequenceKeypoint.new(0.5, Color3.fromRGB(255, 255, 0)),

	ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 0, 255))

}

TextChatService.OnChatWindowAdded = function(message: TextChatMessage)

	local properties = chatWindowConfiguration:DeriveNewMessageProperties()

	local textSource = message.TextSource

	if textSource then

    	properties.PrefixTextProperties = chatWindowConfiguration:DeriveNewMessageProperties()

		gradient:Clone().Parent = properties.PrefixTextProperties

	end

	return properties

end

```

### [Aanpassing van rijke tekst](#aanpassing-van-rijke-tekst)[](#aanpassing-van-rijke-tekst)

Rijke tekst [letterkleur tags](/docs/nl-nl/ui/rich-text#ondersteunde-tags)  kunnen worden gebruikt om chatberichten te formatteren, wat handig is als je specifieke delen van het bericht wilt opmaken. Houd er rekening mee dat rijke tekst geen gradiënten ondersteunt, maar het volgende codevoorbeeld laat zien hoe je de gebruikersnaam (opgeslagen in [TextChatMessage.PrefixText](/docs/nl-nl/reference/engine/classes/TextChatMessage#PrefixText) ) in het berichtlichaam kunt verplaatsen en vervolgens rijke tekst tagging kunt toepassen op alleen het naamgedeelte.

 ![Aanpassing van rijke tekst van de gebruikersnaam in het chatvenster.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-Rich-Text.png)

Aanpassing van rijke tekst

```

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

local chatWindowConfiguration = TextChatService.ChatWindowConfiguration

local gradient = Instance.new("UIGradient")

gradient.Color = ColorSequence.new{

	ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 0, 0)),

	ColorSequenceKeypoint.new(0.5, Color3.fromRGB(255, 255, 0)),

	ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 0, 255))

}

TextChatService.OnChatWindowAdded = function(message: TextChatMessage)

	local properties = chatWindowConfiguration:DeriveNewMessageProperties()

	if message.TextSource then

		properties.PrefixText = "[VIP]"

		properties.Text = string.format("<font color='#00ffff'>%s</font>", message.PrefixText) .. " " .. message.Text

		properties.PrefixTextProperties = chatWindowConfiguration:DeriveNewMessageProperties()

		gradient:Clone().Parent = properties.PrefixTextProperties

	end

	return properties

end

```

## [Berichten van niet-spelerbronnen](#berichten-van-niet-spelerbronnen)[](#berichten-van-niet-spelerbronnen)

Wanneer [TextChatService.CreateDefaultTextChannels](/docs/nl-nl/reference/engine/classes/TextChatService#CreateDefaultTextChannels)  true  is, is een van de standaard tekstkanalen het RBXSystem  kanaal. De standaard chatscripts tonen automatisch systeemberichten in deze kanaal. Je kunt het uiterlijk van deze berichten aanpassen met behulp van de [TextChannel.OnIncomingMessage](/docs/nl-nl/reference/engine/classes/TextChannel#OnIncomingMessage)  callback.

Je wilt misschien de systeemberichten die automatisch door het chatsysteem worden uitgezonden aanpassen of wijzigen. Aangezien de standaard systeemberichten zijn gelokaliseerd voor gebruikers, moet je ze refereren via [TextChatMessage.Metadata](/docs/nl-nl/reference/engine/classes/TextChatMessage#Metadata)  in je [tekstchat callbacks](/docs/nl-nl/chat/in-experience-text-chat#tekstchat-hooks-en-callbacks)  als je hun uiterlijk wilt aanpassen. Bijvoorbeeld, je zou [Metadata](/docs/nl-nl/reference/engine/classes/TextChatMessage#Metadata)  kunnen gebruiken om systeemberichten, foutberichten of berichten van specifieke systemen in je game te identificeren.

### [Systeem](#systeem)[](#systeem)

Om een systeembericht aan de lokale speler te leveren, zoals "spraak" van een openbare omroep, roep je [DisplaySystemMessage()](/docs/nl-nl/reference/engine/classes/TextChannel#DisplaySystemMessage)  aan vanuit het standaard RBXGeneral  kanaal met een prefix voor de gebruikersnaam van de speler.

Client Script

```

local Players = game:GetService("Players")

local TextChatService = game:GetService("TextChatService")

local player = Players.LocalPlayer

local generalChannel: TextChannel = TextChatService:WaitForChild("TextChannels").RBXGeneral

local PREFIX = "[Gids] Welkom "

-- Stuur "systeembericht" naar speler met hun gebruikersnaam toegevoegd

generalChannel:DisplaySystemMessage(PREFIX .. player.DisplayName)

```

 ![Afbeelding die een basis systeembericht in het chatvenster toont.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-System.jpg)

### [NPC/object](#npcobject)[](#npcobject)

Je kunt ook niet-speler dialoogstijl en [chatbellen](/docs/nl-nl/chat/bubble-chat)  toevoegen om het te laten lijken alsof berichten afkomstig zijn van een NPC of object binnen de 3D-wereld.

Client Script

```

local TextChatService = game:GetService("TextChatService")

local Workspace = game:GetService("Workspace")

local generalChannel: TextChannel = TextChatService:WaitForChild("TextChannels").RBXGeneral

TextChatService.OnIncomingMessage = function(textChatMessage: TextChatMessage)

	local properties = Instance.new("TextChatMessageProperties")

	-- Controleer op systeemberichten die metadata bevatten

	if not textChatMessage.TextSource and textChatMessage.Metadata ~= "" then

		-- Voeg prefix toe om het bericht eruit te laten zien alsof het door een speler is verzonden

		properties.PrefixText = string.format("<font color='#%s'>%s: </font>", "#50C999", textChatMessage.Metadata)

		-- Voeg bubble chat toe

		TextChatService:DisplayBubble(Workspace.Statue, textChatMessage.Text)

	end

	return properties

end

local message = "Welkom! Ik zal je gids zijn."

local speakerName = "Oude Ridder"

generalChannel:DisplaySystemMessage(message, speakerName)

```

 ![Afbeelding die een ridderstandbeeld NPC toont die een chatbericht naar het chatvenster uitzendt, samen met een chatbel boven zijn hoofd.](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Chat-NPC.jpg)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
