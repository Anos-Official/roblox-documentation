<!-- Source: https://create.roblox.com/docs/nl-nl/characters/name-health-display -->

Weergave van karakternaam/gezondheid | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Personages](/docs/nl-nl/characters)

# Weergave van karakternaam/gezondheid

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  instantie wordt gebruikt om karaktermodellen te maken, zowel voor gebruikersavatars als NPC's. Wanneer een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  aanwezig is in een [Model](/docs/nl-nl/reference/engine/classes/Model)  die een onderdeel met de naam Head  bevat, toont Roblox een naam en/of gezondheidsbalk boven dat onderdeel.

 ![Informatie over karakterweergave boven een avatar in het spel](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/Display-Indicated.jpg)

Via verschillende [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  eigenschappen kun je het volgende aanpassen:

-

De [afstand](#weergaveafstandstype)  van waaruit gebruikers de naam/gezondheid van andere humanoïden kunnen zien in relatie tot de humanoïde van hun eigen karakter.

-

De [weergavenaam](#overschrijf-weergavenamen)  die boven een humanoïde wordt weergegeven.

-

Of de [gezondheidsbalk](#gezondheidsweergave-type)  van een humanoïde altijd verschijnt, nooit verschijnt, of alleen verschijnt wanneer de humanoïde beschadigd is.

-

Of namen en gezondheidsbalken [geoccludeerd](#occlusie)  (verborgen) zijn wanneer de zichtlijn tussen de camera en een andere humanoïde geblokkeerd is.

Zoals vermeld in de inleiding, vereist de weergave van karakternaam/gezondheid dat de [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  instantie zich binnen een [Model](/docs/nl-nl/reference/engine/classes/Model)  bevindt en dat het model een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  met de naam Head  bevat. Beide objecten moeten ook op hetzelfde niveau in de hiërarchie van het model staan.

## [Weergave-eigenschappen](#weergave-eigenschappen)[](#weergave-eigenschappen)

### [Weergaveafstandstype](#weergaveafstandstype)[](#weergaveafstandstype)

De [Humanoid.DisplayDistanceType](/docs/nl-nl/reference/engine/classes/Humanoid#DisplayDistanceType)  eigenschap stelt in hoe gebruikers de naam/gezondheid van andere karakters zien in relatie tot hun eigen karakter.

#### [Kijker](#kijker)[](#kijker)

Wanneer de [DisplayDistanceType](/docs/nl-nl/reference/engine/classes/Humanoid#DisplayDistanceType)  van een humanoïde is ingesteld op [HumanoidDisplayDistanceType.Viewer](/docs/nl-nl/reference/engine/enums/HumanoidDisplayDistanceType) , ziet deze de naam/gezondheid van andere humanoïden binnen het bereik van zijn eigen [NameDisplayDistance](/docs/nl-nl/reference/engine/classes/Humanoid#NameDisplayDistance)  en [HealthDisplayDistance](/docs/nl-nl/reference/engine/classes/Humanoid#HealthDisplayDistance) . Je kunt dit beschouwen als de laagste prioriteit, aangezien het niet in aanmerking wordt genomen voor andere humanoïden die zijn geconfigureerd als [subject](#onderwerp)  of [none](#geen) .

In het volgende scenario heeft het karakter van de gebruiker (Kijker ) een grotere [NameDisplayDistance](/docs/nl-nl/reference/engine/classes/Humanoid#NameDisplayDistance)  dan [HealthDisplayDistance](/docs/nl-nl/reference/engine/classes/Humanoid#HealthDisplayDistance) , zoals aangegeven door de cirkels. Als gevolg hiervan ziet de gebruiker de karakternamen voor zowel Watchman  als Octavia , maar ziet alleen een gezondheidsbalk voor Watchman .

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/DisplayDistanceType-Viewer.jpg)

#### [Onderwerp](#onderwerp)[](#onderwerp)

Wanneer de [DisplayDistanceType](/docs/nl-nl/reference/engine/classes/Humanoid#DisplayDistanceType)  van een humanoïde is ingesteld op [HumanoidDisplayDistanceType.Subject](/docs/nl-nl/reference/engine/enums/HumanoidDisplayDistanceType) , heeft deze volledige controle  over zijn eigen naam- en gezondheidsweergave via zijn [NameDisplayDistance](/docs/nl-nl/reference/engine/classes/Humanoid#NameDisplayDistance)  en [HealthDisplayDistance](/docs/nl-nl/reference/engine/classes/Humanoid#HealthDisplayDistance)  waarden. Effectief zullen andere humanoïden alleen de naam/gezondheid van het onderwerp binnen die afstanden van de onderwerp  humanoïde zien.

In het volgende scenario zijn zowel Watchman  als Octavia  ingesteld op Subject  en hun [NameDisplayDistance](/docs/nl-nl/reference/engine/classes/Humanoid#NameDisplayDistance)  bereiken zijn aangegeven door de cirkels. Alleen de naam Octavia  is zichtbaar voor de gebruiker wiens karakter zich binnen haar bereik bevindt, maar buiten het bereik van de Watchman  humanoïde.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/DisplayDistanceType-Subject.jpg)

#### [Geen](#geen)[](#geen)

Wanneer de [DisplayDistanceType](/docs/nl-nl/reference/engine/classes/Humanoid#DisplayDistanceType)  van een humanoïde is ingesteld op [HumanoidDisplayDistanceType.None](/docs/nl-nl/reference/engine/enums/HumanoidDisplayDistanceType) , verschijnen zijn naam en gezondheidsbalk onder geen enkele omstandigheid. In het volgende scenario zijn zowel Watchman  als Octavia  ingesteld op None , zodat de andere karakter hun naam of gezondheid niet ziet, zelfs niet wanneer ze binnen bereik zijn.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/DisplayDistanceType-None.jpg)

### [Gezondheidsweergave type](#gezondheidsweergave-type)[](#gezondheidsweergave-type)

De [Humanoid.HealthDisplayType](/docs/nl-nl/reference/engine/classes/Humanoid#HealthDisplayType)  eigenschap biedt verdere controle over de zichtbaarheid van de gezondheidsbalk van het karakter. De balk weerspiegelt de [Health](/docs/nl-nl/reference/engine/classes/Humanoid#Health)  van de humanoïde als een factor van zijn [MaxHealth](/docs/nl-nl/reference/engine/classes/Humanoid#MaxHealth)  en verandert van kleur van groen naar geel naar rood naarmate de gezondheid van de humanoïde afneemt.

#### [AltijdAan](#altijdaan)[](#altijdaan)

Wanneer de [HealthDisplayType](/docs/nl-nl/reference/engine/classes/Humanoid#HealthDisplayType)  van een humanoïde is ingesteld op [HumanoidHealthDisplayType.AlwaysOn](/docs/nl-nl/reference/engine/enums/HumanoidHealthDisplayType) , verschijnt zijn gezondheidsbalk altijd.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/HealthDisplayType-AlwaysOn.jpg)

#### [WeergaveBijBeschadiging](#weergavebijbeschadiging)[](#weergavebijbeschadiging)

Een humanoïde met [HealthDisplayType](/docs/nl-nl/reference/engine/classes/Humanoid#HealthDisplayType)  ingesteld op [HumanoidHealthDisplayType.DisplayWhenDamaged](/docs/nl-nl/reference/engine/enums/HumanoidHealthDisplayType)  toont alleen een gezondheidsbalk wanneer zijn [Health](/docs/nl-nl/reference/engine/classes/Humanoid#Health)  minder is dan zijn [MaxHealth](/docs/nl-nl/reference/engine/classes/Humanoid#MaxHealth) . In het volgende scenario heeft Watchman  volledige gezondheid en toont geen gezondheidsbalk, maar Octavia  is voor 50% beschadigd en toont een gele gezondheidsbalk.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/HealthDisplayType-DisplayWhenDamaged.jpg)

#### [AltijdUit](#altijduit)[](#altijduit)

Wanneer de [HealthDisplayType](/docs/nl-nl/reference/engine/classes/Humanoid#HealthDisplayType)  van een humanoïde is ingesteld op [HumanoidHealthDisplayType.AlwaysOff](/docs/nl-nl/reference/engine/enums/HumanoidHealthDisplayType) , verschijnt zijn gezondheidsbalk onder geen enkele omstandigheid.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/HealthDisplayType-AlwaysOff.jpg)

### [Occlusie](#occlusie)[](#occlusie)

Occlusie (verbergen) van humanoïd namen achter muren of andere objecten wordt geregeld door de [Humanoid.NameOcclusion](/docs/nl-nl/reference/engine/classes/Humanoid#NameOcclusion)  eigenschap van het karakter.

Occlusie vindt niet plaats als de [Transparency](/docs/nl-nl/reference/engine/classes/BasePart#Transparency)  van het occluderende object hoger is dan 0.99. Occlusie vindt ook niet plaats wanneer een humanoïde verborgen is achter een [Model](/docs/nl-nl/reference/engine/classes/Model)  die een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  bevat, zoals het avatar karakter van een andere gebruiker.

#### [GeenOcclusie](#geenocclusie)[](#geenocclusie)

Wanneer een humanoïde verborgen is achter een zichtbaar object en zijn [NameOcclusion](/docs/nl-nl/reference/engine/classes/Humanoid#NameOcclusion)  is ingesteld op [NameOcclusion.NoOcclusion](/docs/nl-nl/reference/engine/enums/NameOcclusion) , zijn naam en gezondheid zijn nooit occluded voor kijkende humanoïden.

In het volgende scenario zijn zowel Watchman  als Octavia  ingesteld op NoOcclusion . Hoewel beide voldoende verborgen zijn achter stenen kolommen, ziet de kijkende humanoïde nog steeds hun naam/gezondheidsweergaven.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/NameOcclusion-NoOcclusion.jpg)

#### [OccludeAll](#occludeall)[](#occludeall)

Wanneer een humanoïde verborgen is achter een zichtbaar object en zijn [NameOcclusion](/docs/nl-nl/reference/engine/classes/Humanoid#NameOcclusion)  is ingesteld op [NameOcclusion.OccludeAll](/docs/nl-nl/reference/engine/enums/NameOcclusion) , zijn naam en gezondheid zijn altijd occluded voor kijkende humanoïden.

In het volgende scenario zijn zowel Watchman  als Octavia  voldoende verborgen achter stenen kolommen. Watchman  is ingesteld op OccludeAll , zodat zijn naam en gezondheid verborgen zijn voor de kijkende humanoïde. Octavia  daarentegen is ingesteld op [NoOcclusion](#geenocclusie)  en haar naam/gezondheid blijft zichtbaar voor de kijkende humanoïde.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/NameOcclusion-OccludeAll.jpg)

#### [VijandOcclusie](#vijandocclusie)[](#vijandocclusie)

Wanneer een humanoïde verborgen is achter een zichtbaar object en zijn [NameOcclusion](/docs/nl-nl/reference/engine/classes/Humanoid#NameOcclusion)  is ingesteld op [NameOcclusion.EnemyOcclusion](/docs/nl-nl/reference/engine/enums/NameOcclusion) , zijn naam en gezondheid zijn alleen occluded voor vijandige humanoïden (spelers in een andere [Team](/docs/nl-nl/reference/engine/classes/Team) ).

In het volgende scenario zijn zowel Watchman  als Octavia  voldoende verborgen achter stenen kolommen, en zijn beide ingesteld op EnemyOcclusion . De kijkende humanoïde en Watchman  bevinden zich in dezelfde [Team](/docs/nl-nl/reference/engine/classes/Team) , dus occlusie van naam/gezondheid vindt niet plaats. De naam en gezondheid van Octavia , aan de tegenovergestelde team, zijn echter geoccludeerd.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/NameOcclusion-EnemyOcclusion.jpg)

## [Wijzig karakterweergaven](#wijzig-karakterweergaven)[](#wijzig-karakterweergaven)

### [Gebruikersavatars](#gebruikersavatars)[](#gebruikersavatars)

Om de naam of gezondheidsweergave voor elke binnenkomende avatar in een spel aan te passen, verbind je de [Players.PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded)  en [Player.CharacterAdded](/docs/nl-nl/reference/engine/classes/Player#CharacterAdded)  evenementen in een [Script](/docs/nl-nl/reference/engine/classes/Script)  en stel je de [weergave-eigenschappen](#weergave-eigenschappen)  in op de [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  van het karakter.

Script - Globale Aanpassing

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(function(character)

		local humanoid = character:FindFirstChildWhichIsA("Humanoid")

		if humanoid then

			-- Geef elke humanoïde volledige controle over zijn naam/gezondheid weergave afstand

			humanoid.DisplayDistanceType = Enum.HumanoidDisplayDistanceType.Subject

			-- Stel de naam weergave afstand in op 20 studs

			humanoid.NameDisplayDistance = 20

			-- Stel de gezondheidsbalk weergave afstand in op 15 studs

			humanoid.HealthDisplayDistance = 15

			-- Toon de gezondheidsbalk alleen wanneer de humanoïde beschadigd is

			humanoid.HealthDisplayType = Enum.HumanoidHealthDisplayType.DisplayWhenDamaged

		end

	end)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Je kunt ook eigenschappen aanpassen op basis van de [Team](/docs/nl-nl/reference/engine/classes/Team)  van een speler, zoals het instellen van alle "bewakers" op een generieke naam, en het verbergen van de namen van alle "ninja" spelers.

Script - Team Aanpassing

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	player.CharacterAdded:Connect(function(character)

		local humanoid = character:FindFirstChildWhichIsA("Humanoid")

		if humanoid then

			-- Stel de naam van alle bewakers in op generieke "Bewaker"

			if player.Team.Name == "Guards" then

				humanoid.DisplayName = "Guard"

			-- Verberg de naam voor alle ninja's

			elseif player.Team.Name == "Ninjas" then

				humanoid.DisplayDistanceType = Enum.HumanoidDisplayDistanceType.None

			end

		end

	end)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Wanneer een speler aan een [Team](/docs/nl-nl/reference/engine/classes/Team)  wordt toegewezen, verschijnt de naam van zijn karakter in dezelfde kleur als de [TeamColor](/docs/nl-nl/reference/engine/classes/Team#TeamColor)  van het team. Dit helpt om teamgenoten en tegenstanders te identificeren in teamgebaseerde ervaringen.

### [NPC-karakters](#npc-karakters)[](#npc-karakters)

Voor NPC-karakters die al in de 3D-wereld zijn geplaatst, kun je de naam/gezondheid rechtstreeks bewerken op het [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  object in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster.

![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/Customize-NPC.jpg)

![](https://prod.docsiteassets.roblox.com/assets/avatar/name-health-display/Humanoid-Properties.png)

## [Overschrijf weergavenamen](#overschrijf-weergavenamen)[](#overschrijf-weergavenamen)

Standaard komt de weergavenaam van een humanoïde overeen met de Weergavenaam  van het Roblox-account van de gebruiker, die uniek en gescheiden is van hun account Gebruikersnaam . Om een volledig aangepaste naam weer te geven die niet gerelateerd is aan het account van de gebruiker, kun je de [Humanoid.DisplayName](/docs/nl-nl/reference/engine/classes/Humanoid#DisplayName)  eigenschap overschrijven.

### [Direct instellen](#direct-instellen)[](#direct-instellen)

Je kunt de [DisplayName](/docs/nl-nl/reference/engine/classes/Humanoid#DisplayName)  eigenschap van elke [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  instantie instellen waar je referentie naar hebt via een [Script](/docs/nl-nl/reference/engine/classes/Script) , zoals het voorbeeld van [team aanpassing](#gebruikersavatars) , of rechtstreeks op het Humanoid  object van een [NPC](#npc-karakters)  karakter.

### [Instellen via gebruikersinvoer](#instellen-via-gebruikersinvoer)[](#instellen-via-gebruikersinvoer)

In sommige genres zoals rollenspellen of vechten, wil je misschien een methode bieden voor gebruikers om hun eigen karakternaam, huisdier karakternaam, enz. in te voeren die specifiek is voor de ervaring en niet is gekoppeld aan hun accountweergavenaam. Je kunt deze invoer aan de clientzijde verzamelen via een [TextBox](/docs/nl-nl/reference/engine/classes/TextBox)  naam invoer.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/TextBox-Example.jpg)

Zodra de invoer is ingediend, kun je deze naar de server sturen via een [remote event](/docs/nl-nl/scripting/events/remote)  en vervolgens, aan de serverzijde, luisteren naar het remote event en de [gefilterde](/docs/nl-nl/ui/text-filtering)  naam toewijzen aan de [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  van het gebruikerskarakter.

LocalScript - Vuur Remote Event

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local changeNameEvent = ReplicatedStorage:WaitForChild("ChangeNameEvent")

changeNameEvent:FireServer("Amory")

```

Script - Wijs Gefilterde Naam Toe

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local TextService = game:GetService("TextService")

-- Maak remote event om tekst van client te ontvangen voor filtering

local changeNameEvent = Instance.new("RemoteEvent")

changeNameEvent.Name = "ChangeNameEvent"

changeNameEvent.Parent = ReplicatedStorage

local function onRequestNameChange(player, newName)

	local character = player.Character

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	local filterResult

	local success, errorMessage = pcall(function()

		filterResult = TextService:FilterStringAsync(newName, player.UserId)

	end)

	if success then

		local filteredName

		local success, errorMessage = pcall(function()

			filteredName = filterResult:GetNonChatStringForBroadcastAsync()

		end)

		if success and humanoid then

			humanoid.DisplayName = filteredName

		end

	end

end

changeNameEvent.OnServerEvent:Connect(onRequestNameChange)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
