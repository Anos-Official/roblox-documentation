<!-- Source: https://create.roblox.com/docs/nl-nl/chat/platform-integrated-chat -->

Platform-geïntegreerde chat | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Chat
6. /
7. [Tekstchat](/docs/nl-nl/chat/in-experience-text-chat)

# Platform-geïntegreerde chat

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Vanaf mei 2027 is platform-geïntegreerde chat verplicht voor alle games. De niet-ondersteunde API's worden verouderd, en aangepaste chat moet de nieuwe [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService) -functies gebruiken.

Wanneer je platform-geïntegreerde chat inschakelt, moeten aangepaste chatfuncties verhuizen naar de native systemen van Roblox ([TextChatCommands](/docs/nl-nl/reference/engine/classes/TextChatCommand) , [TextChannelWindow](/docs/nl-nl/reference/engine/classes/TextChannelWindow) , [Snelle Woorden](/docs/nl-nl/chat/quick-words) ). De inhoud van berichten is ook niet langer toegankelijk in de code.

Platform-geïntegreerde chat  geeft elke speler consistente toegang tot veiligheidstools zoals rapporteren en dempen, en laat chatfuncties zoals [Snelle Woorden](/docs/nl-nl/chat/quick-words)  betrouwbaar uitrollen over alle games. Het vervangt ook het huidige prefix-systeem, zodat rollen die aan gebruikers zijn gekoppeld consistent worden weergegeven en veilig zijn voor alle leeftijden.

Niets in je game verandert totdat je [platform-geïntegreerde chat inschakelt](#platform-ge%C3%AFntegreerde-chat-inschakelen)  in Studio. Nadat je het hebt ingeschakeld:

-

Roblox levert en geeft chat weer in het standaardvenster of een [TextChannelWindow](/docs/nl-nl/reference/engine/classes/TextChannelWindow)  die je in je UI plaatst. Aangepaste chat-UIs kunnen berichten niet langer zelf weergeven.

-

De tekst van spelersberichten is niet toegankelijk voor je code. Je kunt het niet lezen, loggen of exporteren. API's die eerder berichttekst teruggaven, geven nu een lege string ("" ) terug in plaats van nil , zodat je scripts blijven draaien maar geen inhoud ontvangen.

Opdrachten die vanuit de chat worden geactiveerd, moeten [TextChatCommand](/docs/nl-nl/reference/engine/classes/TextChatCommand)  gebruiken.

## [Niet-ondersteunde API's](#niet-ondersteunde-apis)[](#niet-ondersteunde-apis)

Wanneer platform-geïntegreerde chat is ingeschakeld, geven de volgende API's ""  (lege string, niet nil ) terug en loggen een waarschuwing:

| Functie | | Niet-ondersteunde API's | | Wat in plaats daarvan te gebruiken |
| --- | --- |
| Chatberichten en weergave | | [TextChatMessage.Text](/docs/nl-nl/reference/engine/classes/TextChatMessage#Text) , [TextChatMessage.Translation](/docs/nl-nl/reference/engine/classes/TextChatMessage#Translation) | | Migreer je aangepaste chat-GUI naar [TextChannelWindow](/docs/nl-nl/reference/engine/classes/TextChannelWindow) . Stel [Target](/docs/nl-nl/reference/engine/classes/TextChannelWindow#Target)  in op een [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel) . Gebruikers kunnen automatisch berichten verzenden en ontvangen. |
| Chat-prefixen | | [TextChatMessage.PrefixText](/docs/nl-nl/reference/engine/classes/TextChatMessage#PrefixText) | | Niet ondersteund. Als je game prefixen vereist, schakel platform-geïntegreerde chat dan nog niet in. |
| Voorinstellingen / chatwielen | | [TextChannel:SendAsync()](/docs/nl-nl/reference/engine/classes/TextChannel#SendAsync) | | Gebruik [Snelle Woorden](/docs/nl-nl/chat/quick-words)  maker aanpassing om relevante zinnen aan de chat toe te voegen. |
| Moderatie / admin-opdrachten | | [OnIncomingMessage](/docs/nl-nl/reference/engine/classes/TextChatService#OnIncomingMessage) , [Player.Chatted](/docs/nl-nl/reference/engine/classes/Player#Chatted) | | Gebruik [TextChatCommand](/docs/nl-nl/reference/engine/classes/TextChatCommand)  voor chat-geactiveerde opdrachten. Gebruik alleen-lezen chat om alle chats voor moderatie tijdens live evenementen te bekijken. |

## [Platform-geïntegreerde chat inschakelen](#platform-geïntegreerde-chat-inschakelen)[](#platform-geïntegreerde-chat-inschakelen)

Om platform-geïntegreerde chat in Studio in te schakelen:

1.

Open het [Explorer](/docs/nl-nl/studio/explorer)  venster.

2.

Selecteer [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService) .

3.

Zoek in het [Eigenschappen](/docs/nl-nl/studio/properties)  paneel naar [PlatformIntegratedChat](/docs/nl-nl/reference/engine/classes/TextChatService#PlatformIntegratedChat) .

4.

Stel het in op Ingeschakeld .

Met de ingeschakelde update geven de eerder genoemde niet-ondersteunde API's lege strings terug en loggen waarschuwingen. Je kunt de eigenschap op elk moment weer instellen op Uitgeschakeld  om terug te keren.

Je kunt deze eigenschap alleen in Studio wijzigen, niet vanuit een script.

## [Maak een TextChannelWindow](#maak-een-textchannelwindow)[](#maak-een-textchannelwindow)

Om een [TextChannelWindow](/docs/nl-nl/reference/engine/classes/TextChannelWindow)  te maken:

1.

Maak een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  in [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) .

2.

Voeg een [TextChannelWindow](/docs/nl-nl/reference/engine/classes/TextChannelWindow)  instantie toe als kind van de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui) .

3.

Stel de [Size](/docs/nl-nl/reference/engine/classes/GuiObject#Size)  en [Position](/docs/nl-nl/reference/engine/classes/GuiObject#Position)  eigenschappen in om het venster te plaatsen waar je het wilt.

4.

Stel de [Target](/docs/nl-nl/reference/engine/classes/TextChannelWindow#Target)  eigenschap in op de [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel)  die je wilt dat het venster weergeeft.

Elke [TextChannelWindow](/docs/nl-nl/reference/engine/classes/TextChannelWindow)  bindt aan een enkele [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel) . Om meerdere kanalen samen weer te geven, maak je een [TextChannelWindow](/docs/nl-nl/reference/engine/classes/TextChannelWindow)  voor elk kanaal en pas je je eigen toon/verberg-logica toe. Het globale kanaal is niet beschikbaar als doel voor een aangepast venster.

Het volgende codevoorbeeld maakt een aangepast chatvenster dat het RBXGeneral  kanaal weergeeft:

LocalScript in StarterGui

```

local TextChatService = game:GetService("TextChatService")

local screenGui = Instance.new("ScreenGui")

screenGui.Name = "TextChannelWindowDemo"

screenGui.Parent = script.Parent

local myTextChannelWindow = Instance.new("TextChannelWindow")

myTextChannelWindow.Size = UDim2.new(0, 400, 0, 300)

myTextChannelWindow.Position = UDim2.new(0, 10, 0, 10)

myTextChannelWindow.BackgroundColor3 = Color3.fromRGB(20, 20, 20)

myTextChannelWindow.BackgroundTransparency = 0.5

local targetChannelName = "RBXGeneral"

local targetChannel = TextChatService:WaitForChild("TextChannels"):WaitForChild(targetChannelName)

if targetChannel and targetChannel:IsA("TextChannel") then

	myTextChannelWindow.Target = targetChannel

end

myTextChannelWindow.Parent = screenGui

```

## [Toon een aangepast kanaal alleen in zijn eigen venster](#toon-een-aangepast-kanaal-alleen-in-zijn-eigen-venster)[](#toon-een-aangepast-kanaal-alleen-in-zijn-eigen-venster)

Standaard geeft het standaard chatvenster berichten weer van elk [TextChannel](/docs/nl-nl/reference/engine/classes/TextChannel) , zodat een kanaal dat je in een aangepast [TextChannelWindow](/docs/nl-nl/reference/engine/classes/TextChannelWindow)  toont, ook in het standaardvenster verschijnt.

Om een aangepast kanaal alleen in zijn eigen venster weer te geven:

1.

Selecteer in de Explorer [ChatWindowConfiguration](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration)  onder [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService) .

2.

Stel in het Eigenschappen  paneel [TextChannelDisplayMode](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#TextChannelDisplayMode)  in op DefaultTextChannels .

3.

Maak voor elk aangepast kanaal een [TextChannelWindow](/docs/nl-nl/reference/engine/classes/TextChannelWindow)  en stel de [Target](/docs/nl-nl/reference/engine/classes/TextChannelWindow#Target)  in op dat kanaal.

Het volgende voorbeeld toont een aangepast Guild-kanaal dat alleen in zijn eigen venster verschijnt:

LocalScript in StarterPlayerScripts

```

-- Voorwaarde: TextChannelDisplayMode is ingesteld op DefaultTextChannels in Studio.

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

local playerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

-- Scripts kunnen de eigenschap tijdens runtime lezen, maar kunnen deze niet wijzigen.

local config = TextChatService.ChatWindowConfiguration

if config.TextChannelDisplayMode ~= Enum.TextChannelDisplayMode.DefaultTextChannels then

	warn("Guild-berichten verschijnen ook in het standaard chatvenster.")

end

local guildChannel = TextChatService:WaitForChild("TextChannels"):WaitForChild("Guild")

local screenGui = Instance.new("ScreenGui")

screenGui.Name = "GuildChat"

screenGui.Parent = playerGui

local guildWindow = Instance.new("TextChannelWindow")

guildWindow.Size = UDim2.new(0, 400, 0, 300)

guildWindow.Target = guildChannel

guildWindow.Parent = screenGui

```

Houd rekening met deze gedragingen:

-

Je kunt [TextChannelDisplayMode](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#TextChannelDisplayMode)  alleen in Studio of vanuit een plugin instellen. Scripts kunnen het tijdens runtime lezen, maar kunnen het niet wijzigen.

-

De eigenschap bestaat alleen op [ChatWindowConfiguration](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration) . [TextChannelWindow](/docs/nl-nl/reference/engine/classes/TextChannelWindow)  heeft het niet nodig omdat het al een enkel kanaal weergeeft via [Target](/docs/nl-nl/reference/engine/classes/TextChannelWindow#Target) .

-

Kanalen die tijdens runtime worden gemaakt, volgen de huidige modus wanneer ze verschijnen. Standaardkanalen die tijdens runtime worden gemaakt, zoals Team en Whisper, verschijnen nog steeds in het standaardvenster.

## [Migreer chat-geactiveerde admin-opdrachten](#migreer-chat-geactiveerde-admin-opdrachten)[](#migreer-chat-geactiveerde-admin-opdrachten)

Of je je admin-opdrachten moet bijwerken, hangt af van hoe ze worden geactiveerd:

-

Opdrachten die vanuit de chat worden geactiveerd, moeten [TextChatCommand](/docs/nl-nl/reference/engine/classes/TextChatCommand)  gebruiken.

-

Opdrachtverwerking die ruwe chattekst leest, werkt niet langer. Dit omvat [MessageReceived](/docs/nl-nl/reference/engine/classes/TextChatService#MessageReceived) , [Chatted](/docs/nl-nl/reference/engine/classes/Player#Chatted) , of iets anders dat de inhoud van [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)  inspecteert.

Om te migreren:

1.

Identificeer admin-opdrachten in je game die momenteel ruwe chatberichten parseren.

2.

Maak een [TextChatCommand](/docs/nl-nl/reference/engine/classes/TextChatCommand)  voor elke opdracht.

3.

Definieer het triggerwoord en de callback-logica van de opdracht.

4.

Verwijder alle code die [Text](/docs/nl-nl/reference/engine/classes/TextChatMessage#Text)  leest of luistert naar [Chatted](/docs/nl-nl/reference/engine/classes/Player#Chatted)  voor opdrachtverwerking.

Voor een voorbeeld, zie [Aangepaste tekstchatopdrachten](/docs/nl-nl/chat/examples/custom-text-chat-commands) .

## [FAQ](#faq)[](#faq)

Zal er iets veranderen als ik niets doe?

Niets verandert in je game tenzij je [PlatformIntegratedChat](/docs/nl-nl/reference/engine/classes/TextChatService#PlatformIntegratedChat)  instelt op Ingeschakeld .

Heeft dit invloed op borden, borden, notities of andere tekst in de wereld die spelers kunnen schrijven?

Nee. Het beleid voor die oppervlakken is onveranderd: ze kunnen niet worden gebruikt voor tweerichtingscommunicatie tussen spelers, ze hebben een snelheidslimiet van ten minste 1 minuut nodig, en ze zijn onderhevig aan moderatie.

Heeft dit invloed op commentaarsystemen, mededelingenborden of post in mijn game?

Nee. Deze update betreft alleen [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService) .

Kan ik nog steeds chatlogs opnemen en ophalen als game-admin?

Nee. Wanneer [PlatformIntegratedChat](/docs/nl-nl/reference/engine/classes/TextChatService#PlatformIntegratedChat)  is Ingeschakeld , geeft geen enkele API de inhoud van spelersberichten terug op de client of server. Moderators in je game kunnen nog steeds alleen-lezen chatrechten gebruiken om chat te bekijken. Spelers kunnen ook vertrouwen op de misbruikrapportage van Roblox en op veiligheidstools zoals dempen en blokkeren.

Moet ik iets veranderen als ik de standaard Roblox-chat gebruik?

Nee. Als je game de standaard Roblox-chat zonder aanpassingen gebruikt, hoef je geen actie te ondernemen en zou je geen verandering moeten zien.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
