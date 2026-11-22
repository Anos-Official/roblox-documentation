<!-- Source: https://create.roblox.com/docs/nl-nl/chat/bubble-chat -->

Pas bubble chat aan | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Chat
6. /
7. [Tekstchat](/docs/nl-nl/chat/in-experience-text-chat)

# Pas bubble chat aan

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Met [TextChatService](/docs/nl-nl/chat/in-experience-text-chat)  kun je bubble chat gebruiken om aanpasbare spraakchatbellen boven gebruikersavatars en NPC's weer te geven. Bubble chat kan je spel visueel meeslepender maken en gebruikers helpen om berichten en hun sprekers op een contextueel relevante manier gemakkelijk te identificeren. Deze functie is vooral nuttig voor spellen waarin gebruikers zich moeten concentreren op de inhoud terwijl ze tegelijkertijd met anderen communiceren op een minder opdringerige manier.

## [Bubble chat inschakelen](#bubble-chat-inschakelen)[](#bubble-chat-inschakelen)

Om bubble chat in je spel in te schakelen:

1.

Selecteer in het Explorer  venster [BubbleChatConfiguration](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration)  onder [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService) .

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/TextChatService-BubbleChatConfiguration.png)

2.

Vink in het Properties  venster het vakje [BubbleChatConfiguration.Enabled](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration#Enabled)  aan.

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/TextChatService-BubbleChatConfiguration-Enabled.png)

## [Bubble aanpassing](#bubble-aanpassing)[](#bubble-aanpassing)

Nadat je bubble chat hebt ingeschakeld, kun je het uiterlijk en gedrag van je chatbellen aanpassen om overeen te komen met het thema van je spel. Gebruik het Properties  venster van [BubbleChatConfiguration](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration)  voor [basis](#basis-aanpassing)  wijzigingen zoals tekstkleur en spatiëring, of implementeer [geavanceerde](#geavanceerde-aanpassing)  aanpassingen voor achtergrondafbeeldingen van bellen en andere visuele aanpassingen.

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/TextChatService-BubbleChatConfiguration.png)

Voeg alternatieve een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  toe in [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts)  met al je aanpassingsinstellingen. Dit stelt de engine in staat om je aanpassingen tijdens runtime toe te passen, waarbij de instellingen in Studio worden overschreven. Het is nuttig voor het toevoegen van speciale effecten aan chatbellen wanneer gebruikers bepaalde gebeurtenissen of voorwaarden activeren.

### [Basis aanpassing](#basis-aanpassing)[](#basis-aanpassing)

De volgende tabel toont veelvoorkomende aanpassingsproperties voor bubble chat. Voor een volledige lijst van aanpassingsproperties, zie [BubbleChatConfiguration](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration) .

Uiterlijk Gedrag

| Property | | Beschrijving | | Standaard |
| --- | --- |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration#BackgroundColor3) | | Achtergrondkleur van bellen in [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) . | | [250, 250, 250] |
| [FontFace](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration#FontFace) | | [Font](/docs/nl-nl/reference/engine/datatypes/Font)  van de bubble tekst. | | [BuilderSansMedium](/docs/nl-nl/reference/engine/enums/Font#BuilderSansMedium) |
| [TextColor3](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration#TextColor3) | | Kleur van bubble tekst in [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) . | | [57, 59, 61] |
| [TextSize](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration#TextSize) | | Grootte van bubble tekst. | | 16 |

### [Geavanceerde aanpassing](#geavanceerde-aanpassing)[](#geavanceerde-aanpassing)

Voor geavanceerde aanpassing van je bubble, voeg UI-objecten toe die bepaalde aspecten van het uiterlijk van de bubble vertegenwoordigen als kinderen onder [BubbleChatConfiguration](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration) , waaronder:

-

[ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel)  voor achtergrondafbeeldingsinstellingen.

-

[UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient)  voor achtergrondverloopinstellingen.

-

[UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  voor de hoekvorm van bellen.

-

[UIPadding](/docs/nl-nl/reference/engine/classes/UIPadding)  voor de paddingruimte tussen de tekst en de randen van de bubble, relatief aan de normale grootte van de ouder.

Nadat je deze objecten hebt toegevoegd, kun je eigenschappen van deze objecten aanpassen die van toepassing zijn op chatbellen voor geavanceerde bubble aanpassing. Het volgende voorbeeld [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  voegt een achtergrondafbeelding en scherpe hoeken toe aan bellen:

Geavanceerde Bubble Aanpassing

```

local TextChatService = game:GetService("TextChatService")

local bubbleChatConfiguration = TextChatService.BubbleChatConfiguration

bubbleChatConfiguration.TailVisible = false

bubbleChatConfiguration.TextColor3 = Color3.fromRGB(220, 50, 50)

bubbleChatConfiguration.FontFace = Font.fromEnum(Enum.Font.LuckiestGuy)

local bubbleUICorner = bubbleChatConfiguration:FindFirstChildOfClass("UICorner")

if not bubbleUICorner then

	bubbleUICorner = Instance.new("UICorner")

	bubbleUICorner.Parent = bubbleChatConfiguration

end

bubbleUICorner.CornerRadius = UDim.new(0, 0)

local bubbleUIPadding = bubbleChatConfiguration:FindFirstChildOfClass("UIPadding")

if not bubbleUIPadding then

	bubbleUIPadding = Instance.new("UIPadding")

	bubbleUIPadding.Parent = bubbleChatConfiguration

end

bubbleUIPadding.PaddingTop = UDim.new(0, 20)

bubbleUIPadding.PaddingRight = UDim.new(0, 10)

bubbleUIPadding.PaddingBottom = UDim.new(0, 15)

bubbleUIPadding.PaddingLeft = UDim.new(0, 10)

local bubbleImageLabel = bubbleChatConfiguration:FindFirstChildOfClass("ImageLabel")

if not bubbleImageLabel then

	bubbleImageLabel = Instance.new("ImageLabel")

	bubbleImageLabel.Parent = bubbleChatConfiguration

end

bubbleImageLabel.Image = "rbxassetid://109157529833093"

bubbleImageLabel.ScaleType = Enum.ScaleType.Slice

bubbleImageLabel.SliceCenter = Rect.new(40, 40, 320, 120)

bubbleImageLabel.SliceScale = 0.5

```

 ![](https://prod.docsiteassets.roblox.com/assets/players/in-experience-text-chat/Advanced-Bubble.png)

De volgende tabellen schetsen de beschikbare [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  en [uiterlijk modificator](/docs/nl-nl/ui/appearance-modifiers)  kinderen samen met hun geldige aanpassingsproperties:

ImageLabel UIGradient UICorner UIPadding

| Property | | Beschrijving | | Standaard |
| [Image](/docs/nl-nl/reference/engine/classes/ImageLabel#Image) | | Asset ID van de achtergrondafbeelding van de bubble. | |  |
| [ImageColor3](/docs/nl-nl/reference/engine/classes/ImageLabel#ImageColor3) | | Kleurstint van de achtergrondafbeelding van de bubble in [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) . | | [255, 255, 255] |
| [ImageRectOffset](/docs/nl-nl/reference/engine/classes/ImageLabel#ImageRectOffset) | | Offset van het afbeeldingsgebied dat moet worden weergegeven vanaf de bovenkant links in pixels. | | (0, 0) |
| [ImageRectSize](/docs/nl-nl/reference/engine/classes/ImageLabel#ImageRectSize) | | Grootte van het afbeeldingsgebied dat moet worden weergegeven in pixels. Om de volledige afbeelding weer te geven, stel je een van de dimensies in op 0 . | | (0, 0) |
| [ScaleType](/docs/nl-nl/reference/engine/classes/ImageLabel#ScaleType) | | Het schaaltype voor het weergeven van de afbeelding wanneer de grootte anders is dan de absolute grootte van de bubble. | | [Stretch](/docs/nl-nl/reference/engine/enums/ScaleType) |
| [SliceCenter](/docs/nl-nl/reference/engine/classes/ImageLabel#SliceCenter) | | Slice-grenzen van de afbeelding als de afbeelding een 9-slice afbeelding is. Alleen van toepassing wanneer je [ScaleType](/docs/nl-nl/reference/engine/classes/ImageLabel#ScaleType)  instelt als [Slice](/docs/nl-nl/reference/engine/enums/ScaleType) . | | (0, 0, 0, 0) |
| [SliceScale](/docs/nl-nl/reference/engine/classes/ImageLabel#SliceScale) | | Schaalverhouding van slice-randen als de afbeelding een 9-slice afbeelding is. Alleen van toepassing wanneer je [ScaleType](/docs/nl-nl/reference/engine/classes/ImageLabel#ScaleType)  instelt als [Slice](/docs/nl-nl/reference/engine/enums/ScaleType) . | | 1 |
| [TileSize](/docs/nl-nl/reference/engine/classes/ImageLabel#TileSize) | | Tilinggrootte van de afbeelding. Alleen van toepassing wanneer je [ScaleType](/docs/nl-nl/reference/engine/classes/ImageLabel#ScaleType)  instelt als [Tile](/docs/nl-nl/reference/engine/enums/ScaleType) . | | (1, 0, 1, 0) |

## [Per-bubble aanpassing](#per-bubble-aanpassing)[](#per-bubble-aanpassing)

Je kunt chatbellen individueel stylen en het gedrag ervan aanpassen op basis van specifieke voorwaarden om je algemene instellingen te overschrijven. Bijvoorbeeld, je kunt chatbellen gebruiken om NPC's en gebruikers te onderscheiden, kritieke gezondheidsstatus te benadrukken, en speciale effecten toe te passen op berichten met vooraf gedefinieerde sleutelwoorden.

Om per-bubble aanpassing in te stellen, voeg een client-side [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  toe met behulp van [BubbleChatMessageProperties](/docs/nl-nl/reference/engine/classes/BubbleChatMessageProperties) , die overeenkomende eigenschappen van [BubbleChatConfiguration](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration)  overschrijft, en de [TextChatService.OnBubbleAdded](/docs/nl-nl/reference/engine/classes/TextChatService#OnBubbleAdded)  callback om te specificeren hoe je elke bubble wilt aanpassen. De callback levert je de [TextChatMessage](/docs/nl-nl/reference/engine/classes/TextChatMessage)  eigenschap evenals de adornee, zodat je de aanpassing kunt toepassen op basis van attributen die zijn geassocieerd met gebruikers, de chattekstinhoud, eigenschappen van gebruikerskarakters, en eventuele speciale voorwaarden die je wilt definiëren.

De volgende basis aanpassingsproperties zijn beschikbaar voor per-bubble aanpassing:

| Property | | Beschrijving | | Standaard |
| [BackgroundColor3](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration#BackgroundColor3) | | Achtergrondkleur van bellen in [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) . | | (250, 250, 250) |
| [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration#BackgroundTransparency) | | Achtergrondtransparantie van bellen. | | 0.1 |
| [FontFace](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration#FontFace) | | [Font](/docs/nl-nl/reference/engine/datatypes/Font)  van de bubble tekst. | | [BuilderSansMedium](/docs/nl-nl/reference/engine/enums/Font#BuilderSansMedium) |
| [TextColor3](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration#TextColor3) | | Kleur van bubble tekst in [Color3](/docs/nl-nl/reference/engine/datatypes/Color3) . | | [57, 59, 61] |
| [TextSize](/docs/nl-nl/reference/engine/classes/BubbleChatConfiguration#TextSize) | | Grootte van bubble tekst. | | 16 |

Het volgende voorbeeld voegt een speciale uitstraling toe aan de chatbellen van VIP-gebruikers door te controleren of een chatbericht verzender de IsVIP  attribuut heeft:

VIP Bellen

```

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

-- Evenement handler voor wanneer een nieuwe chat bubble aan het spel is toegevoegd

TextChatService.OnBubbleAdded = function(message: TextChatMessage, adornee: Instance)

	-- Controleer of het chatbericht een TextSource (afzender) heeft die eraan is gekoppeld

	if message.TextSource then

		-- Maak een nieuwe BubbleChatMessageProperties instantie aan om de chat bubble aan te passen

		local bubbleProperties = Instance.new("BubbleChatMessageProperties")

		-- Verkrijg de gebruiker die het chatbericht heeft verzonden op basis van hun UserId

		local player = Players:GetPlayerByUserId(message.TextSource.UserId)

		if player:GetAttribute("IsVIP") then

			-- Als de speler een VIP is, pas de eigenschappen van de chat bubble aan

			bubbleProperties.TextColor3 = Color3.fromHex("#F5CD30")

			bubbleProperties.BackgroundColor3 = Color3.fromRGB(25, 27, 29)

			bubbleProperties.FontFace = Font.fromEnum(Enum.Font.PermanentMarker)

		end

		return bubbleProperties

	end

end

```

Alle geavanceerde aanpassingsopties zijn beschikbaar voor per-bubble aanpassing. Vergelijkbaar met geavanceerde aanpassing voor algemene bellen, voeg instanties toe die je wilt aanpassen als kinderen van [BubbleChatMessageProperties](/docs/nl-nl/reference/engine/classes/BubbleChatMessageProperties) . Het volgende voorbeeld voegt een speciaal verloop effect toe samen met andere eigenschappen aan chatbellen van gebruikers met een lage gezondheidsstatus door de [Humanoid.Health](/docs/nl-nl/reference/engine/classes/Humanoid#Health)  eigenschap van de chatbericht verzenders' karakters te controleren:

Lage Gezondheids Bellen

```

local TextChatService = game:GetService("TextChatService")

local Players = game:GetService("Players")

-- Evenement handler voor wanneer een nieuwe chat bubble aan het spel is toegevoegd

TextChatService.OnBubbleAdded = function(message: TextChatMessage, adornee: Instance)

	-- Controleer of het chatbericht een TextSource (afzender) heeft die eraan is gekoppeld

	if message.TextSource then

		-- Verkrijg de gebruiker die het chatbericht heeft verzonden door hun UserId te gebruiken

		local player = Players:GetPlayerByUserId(message.TextSource.UserId)

		-- Zoek de humanoïde in het karakter van de gebruiker

		local humanoid = player.Character:FindFirstChildWhichIsA("Humanoid")

		if humanoid and humanoid.Health < 25 then

			-- Maak een nieuwe BubbleChatMessageProperties instantie aan om de chat bubble aan te passen

			local bubbleProperties :BubbleChatMessageProperties = Instance.new("BubbleChatMessageProperties")

			-- Pas de eigenschappen van de chat bubble aan voor lage gezondheidsconditie

			bubbleProperties.BackgroundColor3 = Color3.fromRGB(245, 245, 245)

			bubbleProperties.TextColor3 = Color3.fromRGB(234, 51, 96)

			bubbleProperties.TextSize = 20

			bubbleProperties.FontFace = Font.fromEnum(Enum.Font.DenkOne)

			-- Voeg een UIGradient toe als kind om het verloop aan te passen

			local uiGradient : UIGradient = Instance.new("UIGradient")

			uiGradient.Color = ColorSequence.new(Color3.fromRGB(110, 4, 0), Color3.fromRGB(0, 0, 0))

			uiGradient.Rotation = 90

			uiGradient.Parent = bubbleProperties

			return bubbleProperties

		end

	end

end

```

## [Handmatig bellen weergeven](#handmatig-bellen-weergeven)[](#handmatig-bellen-weergeven)

Je wilt misschien een chat bubble weergeven wanneer spelers geen bericht hebben verzonden, zoals bij NPC's. Gebruik de [TextChatService:DisplayBubble()](/docs/nl-nl/reference/engine/classes/TextChatService#DisplayBubble)  methode om handmatig een chat bubble weer te geven.

De aanpassing van deze bellen is hetzelfde als de aanpassing van de bellen die automatisch worden weergegeven wanneer spelers berichten verzenden via TextChannels met behulp van de [[TextChatService.OnBubbleAdded](/docs/nl-nl/reference/engine/classes/TextChatService#OnBubbleAdded)  callback](#per-bubble-aanpassing) .

Om spraak of andere tekst te genereren met een LLM, zie de [TextGenerator](/docs/nl-nl/reference/engine/classes/TextGenerator)  klasse.

### [NPC bellen](#npc-bellen)[](#npc-bellen)

Geef chatbellen weer voor niet-speler personages (NPC's) door [TextChatService:DisplayBubble(character, message)](/docs/nl-nl/reference/engine/classes/TextChatService#DisplayBubble)  aan te roepen, met de NPC-figuur en het bericht als parameters. Deze bellen zijn aanpasbaar met behulp van de [TextChatService.OnBubbleAdded](/docs/nl-nl/reference/engine/classes/TextChatService#OnBubbleAdded)  callback, net als elke andere chat bubble.

[TextChatService:DisplayBubble()](/docs/nl-nl/reference/engine/classes/TextChatService#DisplayBubble)  werkt alleen op client-side scripts, dus zorg ervoor dat je een [Script](/docs/nl-nl/reference/engine/classes/Script)  gebruikt met [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  ingesteld op [Enum.RunContext.Client](/docs/nl-nl/reference/engine/enums/RunContext#Client) , of een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  in een [geschikte container](/docs/nl-nl/projects/data-model#client) , zoals [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts) . Als je een [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)  aan een NPC koppelt, kan een script voor het weergeven van een chat bubble er als volgt uitzien:

```

local TextChatService = game:GetService("TextChatService")

local Workspace = game:GetService("Workspace")

local prompt = Workspace.SomeNPC.ProximityPrompt

local head = prompt.Parent:WaitForChild("Head")

prompt.Triggered:Connect(function()

	TextChatService:DisplayBubble(head, "Hallo wereld!")

end)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
