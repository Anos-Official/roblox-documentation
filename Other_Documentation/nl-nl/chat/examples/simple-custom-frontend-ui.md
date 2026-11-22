<!-- Source: https://create.roblox.com/docs/nl-nl/chat/examples/simple-custom-frontend-ui -->

Aangepaste tekstchat UI | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Chat
6. /
7. [Tekstchat](/docs/nl-nl/chat/in-experience-text-chat)
8. /
9. [Voorbeelden](/docs/nl-nl/chat/examples/simple-custom-frontend-ui)

# Aangepaste tekstchat UI

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Wanneer [platform-geïntegreerde chat](/docs/nl-nl/chat/platform-integrated-chat)  is ingeschakeld, kunnen aangepaste UI's de tekst van spelersberichten niet meer zelf weergeven. Gebruik [TextChannelWindow](/docs/nl-nl/reference/engine/classes/TextChannelWindow)  in plaats van [Text](/docs/nl-nl/reference/engine/classes/TextChatMessage#Text)  te lezen of te luisteren naar [MessageReceived](/docs/nl-nl/reference/engine/classes/TextChatService#MessageReceived)  voor weergave.

Dit voorbeeld laat zien hoe je de [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  klasse kunt gebruiken om je eigen frontend te ontwerpen. Het hergebruikt de standaard tekstkanalen van [CreateDefaultTextChannels](/docs/nl-nl/reference/engine/classes/TextChatService#CreateDefaultTextChannels)  en is zeer eenvoudig in vergelijking met de standaard UI.

1.

Schakel de standaard UI die bij de [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  wordt geleverd uit door de eigenschappen [ChatWindowConfiguration.Enabled](/docs/nl-nl/reference/engine/classes/ChatWindowConfiguration#Enabled)  en [ChatInputBarConfiguration.Enabled](/docs/nl-nl/reference/engine/classes/ChatInputBarConfiguration#Enabled)  in het Eigenschappen  venster van Studio op false  te zetten.

2.

Maak een vervanging voor de chatinvoerbalk. Dit is het tekstvak dat berichten verzendt wanneer de gebruiker op Enter  drukt.

1.

Maak een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  en maak deze een kind van [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) .

2.

Maak een [TextBox](/docs/nl-nl/reference/engine/classes/TextBox)  en maak deze een kind van de nieuwe [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui) , en [herpositioneer](/docs/nl-nl/ui/position-and-size#position)  en [verander de grootte](/docs/nl-nl/ui/position-and-size#size)  zoals gewenst.

3.

Maak een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  en maak deze een kind van de nieuwe [TextBox](/docs/nl-nl/reference/engine/classes/TextBox) .

4.

Voeg de volgende code toe aan de [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) :

Client

```

local TextChatService = game:GetService("TextChatService")

-- RBXGeneral is het standaard openbare kanaal

local RBXGeneral = TextChatService:FindFirstChild("TextChannels"):WaitForChild("RBXGeneral")

local textBox = script.Parent

textBox.FocusLost:Connect(function(enterPressed)

	local text = textBox.Text

	if enterPressed and #text > 0 then

		local success, response = pcall(function()

			return RBXGeneral:SendAsync(textBox.Text)

		end)

		if not success then

			RBXGeneral:DisplaySystemMessage("Verzenden van bericht mislukt")

		end

		-- Gebruikers verwachten dat het invoervak wordt leeggemaakt na het verzenden van een bericht

		textBox.Text = ""

	end

end)

```

3.

Maak een vervanging voor het chatvenster. Dit is de [ScrollingFrame](/docs/nl-nl/reference/engine/classes/ScrollingFrame)  die berichten weergeeft zodra ze worden ontvangen van [TextChatService.MessageReceived](/docs/nl-nl/reference/engine/classes/TextChatService#MessageReceived) . Deze stap maakt ook een [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  aan om de berichten automatisch te rangschikken.

1.

Maak een andere nieuwe [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  en maak deze een kind van [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) .

2.

Maak een [ScrollingFrame](/docs/nl-nl/reference/engine/classes/ScrollingFrame)  en maak deze een kind van de ScreenGui , en [herpositioneer](/docs/nl-nl/ui/position-and-size#position)  en [verander de grootte](/docs/nl-nl/ui/position-and-size#size)  zoals gewenst.

3.

Maak een [UIListLayout](/docs/nl-nl/reference/engine/classes/UIListLayout)  en maak deze een kind van de [ScrollingFrame](/docs/nl-nl/reference/engine/classes/ScrollingFrame) .

4.

Maak een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  en maak deze een kind van de [ScrollingFrame](/docs/nl-nl/reference/engine/classes/ScrollingFrame) .

5.

Voeg de volgende code toe aan de [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) :

Client

```

local TextChatService = game:GetService("TextChatService")

-- Functie om een nieuw tekstlabel te maken voor elk ontvangen bericht

local function addMessageGui(textChatMessage: TextChatMessage)

	local isOutgoingMessage = textChatMessage.Status == Enum.TextChatMessageStatus.Sending

	local parent = script.Parent

	local originalLabel = parent:FindFirstChild(textChatMessage.MessageId)

	if originalLabel then

		originalLabel.Text = textChatMessage.Text

		originalLabel.BackgroundTransparency = if isOutgoingMessage then 0.5 else 0

	else

		local textLabel = Instance.new("TextLabel")

		textLabel.BorderSizePixel = 0

		textLabel.Font = Enum.Font.BuilderSans

		textLabel.TextSize = 18

		textLabel.TextXAlignment = Enum.TextXAlignment.Left

		textLabel.BackgroundTransparency = if isOutgoingMessage then 0.5 else 0

		textLabel.BackgroundColor3 = Color3.fromRGB(0, 0, 0)

		textLabel.TextColor3 = Color3.fromRGB(255, 255, 255)

		textLabel.Name = textChatMessage.MessageId

		textLabel.AutomaticSize = Enum.AutomaticSize.XY

		textLabel.Text = textChatMessage.Text

		textLabel.Parent = parent

	end

end

-- Begin met luisteren naar binnenkomende berichten

TextChatService.MessageReceived:Connect(addMessageGui)

```

Bij het gebruik van het [TextChatService.MessageReceived](/docs/nl-nl/reference/engine/classes/TextChatService#MessageReceived)  evenement is het belangrijk om te controleren of het bericht al bestaat in het chatvenster. Dit evenement wordt eenmaal aangeroepen bij het verzenden en eenmaal wanneer het bericht van de server wordt ontvangen.

4.

Test je spel door berichten te verzenden in de chatinvoerbalk. Je zou de berichten in het chatvenster moeten zien verschijnen. Je kunt dit voorbeeld vervolgens uitbreiden door functies toe te voegen, zoals het focussen op de [TextBox](/docs/nl-nl/reference/engine/classes/TextBox)  wanneer een toets wordt ingedrukt of het toevoegen van [chat-tags](/docs/nl-nl/chat/examples/group-chat-tags) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
