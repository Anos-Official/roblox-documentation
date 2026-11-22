<!-- Source: https://create.roblox.com/docs/nl-nl/ui/text-filtering -->

Tekstfiltering | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)

# Tekstfiltering

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Toegepast op verschillende bronnen en invoer, voorkomt tekstfiltering  dat gebruikers ongepaste taal en persoonlijk identificeerbare informatie zoals telefoonnummers zien. Roblox filtert automatisch veelvoorkomende tekstuitvoer zoals berichten die zijn doorgegeven via [in-game tekstchat](/docs/nl-nl/chat/in-experience-text-chat) , maar jij bent verantwoordelijk voor het filteren van alle weergegeven tekst waar je geen expliciete controle over hebt .

Omdat filtering cruciaal is voor een veilige omgeving, modereert Roblox actief de inhoud van games om ervoor te zorgen dat ze voldoen aan de [gemeenschapsnormen](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) . Als Roblox meldingen ontvangt of automatisch detecteert dat jouw game geen tekstfiltering toepast, dan verwijdert het systeem de game totdat je filtering toevoegt.

## [Filterscenario's](#filterscenarios)[](#filterscenarios)

Tekst kan in verschillende scenario's worden verzameld en/of weergegeven aan gebruikers, waaronder:

-

Een game die de [tekstinvoer](/docs/nl-nl/ui/text-input)  van gebruikers verzamelt via [TextBox](/docs/nl-nl/reference/engine/classes/TextBox) -invoeren, een aangepaste GUI met knoppen zoals een toetsenbord/toetsenpaneelinterface, of een interactief toetsenbordmodel in de 3D-ruimte.

-

Een game die woorden genereert uit willekeurige karakters en deze aan gebruikers toont, omdat er een kans is dat het ongepaste woorden creëert.

-

Een game die verbinding maakt met een externe webserver om inhoud op te halen die in de game wordt weergegeven. Vaak heb je geen controle over de inhoud van de externe site en kan een derde partij de informatie bewerken.

-

Een game die tekst opslaat, zoals de huisdiernamen van gebruikers, met behulp van [gegevensopslag](/docs/nl-nl/../cloud-services/data-stores) , waarbij de opgeslagen tekst ongepaste woorden kan bevatten die gefilterd moeten worden bij het ophalen ervan.

## [Filteringproces](#filteringproces)[](#filteringproces)

[TextService:FilterStringAsync()](/docs/nl-nl/reference/engine/classes/TextService#FilterStringAsync)  filtert in-game tekst door een tekststring en de [UserId](/docs/nl-nl/reference/engine/classes/Player#UserId)  van de gebruiker die de tekst heeft gemaakt als invoer te nemen. Het retourneert een [TextFilterResult](/docs/nl-nl/reference/engine/classes/TextFilterResult) -object dat twee extra methoden heeft die je in verschillende scenario's kunt aanroepen:

-

[TextFilterResult:GetNonChatStringForBroadcastAsync()](/docs/nl-nl/reference/engine/classes/TextFilterResult#GetNonChatStringForBroadcastAsync)  voor het filteren van tekst die zichtbaar is voor alle gebruikers in een game, zoals voor een dialoog waarmee een gebruiker een bericht op een bord kan schrijven dat zichtbaar is voor alle gebruikers op de server.

-

[TextFilterResult:GetNonChatStringForUserAsync()](/docs/nl-nl/reference/engine/classes/TextFilterResult#GetNonChatStringForUserAsync)  om gefilterde tekst weer te geven voor één specifieke gebruiker, op basis van leeftijd en andere details.

In de context van [TextBox](/docs/nl-nl/reference/engine/classes/TextBox) -invoer verzamelt het volgende voorbeeld invoer op het [FocusLost](/docs/nl-nl/reference/engine/classes/TextBox#FocusLost) -evenement en verzendt het naar de server via een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent) . Op de server wordt het eerst gefilterd via [FilterStringAsync()](/docs/nl-nl/reference/engine/classes/TextService#FilterStringAsync)  en vervolgens [GetNonChatStringForBroadcastAsync()](/docs/nl-nl/reference/engine/classes/TextFilterResult#GetNonChatStringForBroadcastAsync)  met de bedoeling dat de tekst wordt weergegeven aan alle gebruikers op een server-side object zoals een [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  in de 3D-wereld.

Filter geen tekst in realtime "per ingevoerd teken" in een [TextBox](/docs/nl-nl/reference/engine/classes/TextBox) , omdat dit resulteert in tekst die alleen zichtbaar is voor de gebruiker die het typt. Filter in plaats daarvan de ingevoerde tekst nadat  de gebruiker deze heeft ingediend.

Filtering Tekst Invoer - Client Script

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local textBox = script.Parent

textBox.ClearTextOnFocus = false

textBox.PlaceholderText = "..."

textBox.TextXAlignment = Enum.TextXAlignment.Left

textBox.TextScaled = true

-- RemoteEvent om tekstinvoer naar de server te verzenden voor filtering

local inputRemoteEvent = ReplicatedStorage:FindFirstChild("InputRemoteEvent")

-- Evenement handler voor focus verloren en enter ingedrukt

local function onFocusLost(enterPressed, inputObject)

	if enterPressed then

		print("INGEDIEND:", textBox.Text)

		if inputRemoteEvent then

			inputRemoteEvent:FireServer(textBox.Text)

		end

	end

end

textBox.FocusLost:Connect(onFocusLost)

```

Filtering Tekst Invoer - Server Script

```

local TextService = game:GetService("TextService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- RemoteEvent om tekstinvoer van de client te ontvangen voor filtering

local inputRemoteEvent = ReplicatedStorage:FindFirstChild("InputRemoteEvent")

local function getFilterResult(text, fromUserId)

	local filterResult

	local success, errorMessage = pcall(function()

		filterResult = TextService:FilterStringAsync(text, fromUserId)

	end)

	if success then

		return filterResult

	else

		warn("Fout bij het genereren van TextFilterResult:", errorMessage)

	end

end

-- Geactiveerd wanneer de client invoer indient vanuit de TextBox

local function onInputReceived(player, text)

	if text ~= "" then

		local filterResult = getFilterResult(text, player.UserId)

		if filterResult then

			local success, filteredText = pcall(function()

				return filterResult:GetNonChatStringForBroadcastAsync()

			end)

			if success then

				print("GEFILTERD:", filteredText)

			else

				warn("Fout bij het filteren van tekst!")

			end

		end

	end

end

inputRemoteEvent.OnServerEvent:Connect(onInputReceived)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
