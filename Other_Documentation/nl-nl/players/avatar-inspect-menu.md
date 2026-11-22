<!-- Source: https://create.roblox.com/docs/nl-nl/players/avatar-inspect-menu -->

Avatar Inspect Menu | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelers](/docs/nl-nl/players)
6. /
7. UI voor spelers

# Avatar Inspect Menu

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het Avatar Inspect Menu  stelt gebruikers in staat om de Roblox-avatar van een andere gebruiker te bekijken, items uit te proberen en zelfs aankopen te doen binnen een spel. Roblox maakt dit menu standaard beschikbaar en gebruikers in jouw spel kunnen dit menu op drie manieren openen:

-

Het hoofdmenu van het spel openen en op de Bekijk  knop naast een gebruiker in het Spelers  tabblad klikken.

-

Op de naam van een gebruiker in de spelerslijst klikken.

-

De Inspecteer optie selecteren in het [Avatar Context Menu](/docs/nl-nl/players/avatar-context-menu) , een opt-in functie die extra sociale interactie tussen gebruikers mogelijk maakt.

Je kunt het Avatar Inspect Menu  van een gebruiker op de volgende manieren aanpassen:

-

Verander het inspectdoel van de Roblox-avatar van de gebruiker naar hun [huidige in-game uiterlijk](#inspecteer-momenteel-uitgeruste-items) .

-

Verander het inspectdoel naar een [specifieke gebruikers-ID](#inspecteer-specifieke-gebruikers) , zelfs als ze niet in het spel zijn.

Voor meer specifieke catalogustoegang kun je ook de [Avatar Editor Service](/docs/nl-nl/players/avatar-editor)  gebruiken om toegang te krijgen tot en wijzigingen aan te brengen in de platformbrede avatar van een gebruiker binnen een spel.

## [Inspecteer momenteel uitgeruste items](#inspecteer-momenteel-uitgeruste-items)[](#inspecteer-momenteel-uitgeruste-items)

Standaard toont het Inspect Menu dezelfde informatie als de profielpagina van de Roblox-avatar van de gebruiker. De avataroutfit komt mogelijk niet overeen met het huidige uiterlijk van de gebruiker, aangezien je op dat specifieke moment mogelijk andere accessoires of avataritems hebt uitgerust.

In de gevallen waarin het standaard Inspect Menu mogelijk niet nauwkeurig is voor de outfit van het huidige personage, kun je de huidige outfit van een personage inspecteren met de volgende stappen:

1.

Schakel het standaard profielgebaseerde Inspect Menu uit door [GuiService:SetInspectMenuEnabled()](/docs/nl-nl/reference/engine/classes/GuiService#SetInspectMenuEnabled)  in te stellen met een waarde van false .

2.

Verkrijg een huidige [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  van het doelspelerpersonage.

3.

Roep [GuiService:InspectPlayerFromHumanoidDescription()](/docs/nl-nl/reference/engine/classes/GuiService#InspectPlayerFromHumanoidDescription)  aan om het Inspect menu te laden op basis van de [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription) .

Gebruik het volgende codevoorbeeld om de momenteel uitgeruste items van een specifieke speler te inspecteren:

```

local GuiService = game:GetService("GuiService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Maak het profielgebaseerde Inspect Menu ontoegankelijk

GuiService:SetInspectMenuEnabled(false)

local humanoid = player.Character and player.Character:FindFirstChildWhichIsA("Humanoid")

if humanoid then

	-- Verkrijg de huidige HumanoidDescription van een spelerpersonage

	local humanoidDescription = humanoid:GetAppliedDescription()

	-- Laad het inspect menu vanuit een humanoid beschrijving

	GuiService:InspectPlayerFromHumanoidDescription(humanoidDescription, player.Name)

end

```

## [Inspecteer specifieke gebruikers](#inspecteer-specifieke-gebruikers)[](#inspecteer-specifieke-gebruikers)

Het Avatar Inspect Menu kan spelers inspecteren die niet in het huidige spel zijn. Je kunt [GuiService:InspectPlayerFromUserId()](/docs/nl-nl/reference/engine/classes/GuiService#InspectPlayerFromUserId)  gebruiken om een speler te inspecteren op basis van een [Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId) .

Gebruik het volgende codevoorbeeld om het Avatar Inspect Menu te openen op basis van een [UserId](/docs/nl-nl/reference/engine/classes/Player#UserId) :

```

local GuiService = game:GetService("GuiService")

local Players = game:GetService("Players")

-- Verkrijg gebruikers-ID op basis van gebruikersnaam

local success, userId = pcall(function()

	return Players:GetUserIdFromNameAsync("RobloxUser")

end)

if success then

	GuiService:InspectPlayerFromUserId(userId)

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
