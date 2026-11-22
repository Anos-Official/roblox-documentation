<!-- Source: https://create.roblox.com/docs/nl-nl/production/analytics/funnel-events -->

Trechtergebeurtenissen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Analytics](/docs/nl-nl/production/analytics)
4. /
5. Evenementtypes

# Trechtergebeurtenissen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Trechtergebeurtenissen  stellen je in staat om de voortgang van je gebruikers door belangrijke fasen van je game te volgen. Dit omvat:

-

Onboarding  — Waar haken gebruikers af bij het starten van je game?

-

Voortgang  — Waar stoppen gebruikers met het vorderen in je game?

-

Winkel  — Waar laten gebruikers aankopen achterwege?

Zodra je game begint met het volgen van trechtergebeurtenissen, ontgrendel je de Trechterpagina van het Analytics-dashboard op de Creator Hub. Je kunt tabbladen aan het dashboard toevoegen voor maximaal tien trechters.

Als een gebruiker meer dan 180 dagen geen gebeurtenissen voor een trechter heeft, verloopt hun opgeslagen stap en worden ze als een nieuwe gebruiker voor die trechter geteld als ze terugkomen.

## [Trechtergebeurtenissen volgen](#trechtergebeurtenissen-volgen)[](#trechtergebeurtenissen-volgen)

Om trechtergebeurtenissen te volgen, identificeer je eerst de belangrijkste trechters in je game en segmenteer je ze in stappen. Omdat het doel is om het gedrag van spelers te begrijpen, komen deze stappen meestal overeen met een actie of prestatie.

In een RPG zou je een stap kunnen hebben voor het deelnemen aan de game, een voor het kiezen van een klasse, een andere voor het verlaten van de startkamer, enzovoort. Je roept doorgaans [LogFunnelStepEvent()](/docs/nl-nl/reference/engine/classes/AnalyticsService#LogFunnelStepEvent)  of [LogOnboardingFunnelStepEvent()](/docs/nl-nl/reference/engine/classes/AnalyticsService#LogOnboardingFunnelStepEvent)  na  het voltooien van een stap door een speler, maar het belangrijkste is om consistent te zijn over wanneer je deze methoden aanroept en gebruik te maken van gemakkelijk te interpreteren namen.

Je onboardingflow is een geweldige plek om te beginnen met het volgen van trechtergebeurtenissen, omdat dit waarschijnlijk de plek is waar je het merendeel van je gebruikers verliest.

Gegevens kunnen alleen vanaf de server en in gepubliceerde games worden verzonden. Gegevens kunnen niet vanaf de client of Studio worden verzonden.

### [Eenmalige trechters volgen](#eenmalige-trechters-volgen)[](#eenmalige-trechters-volgen)

Een eenmalige trechter houdt conversiegebeurtenissen bij die slechts één keer per gebruiker plaatsvinden.

Een veelvoorkomend voorbeeld is een onboardingtrechter , die cruciaal is om te begrijpen hoe je de retentie en sessietijd van nieuwe gebruikers in je game kunt verbeteren. Het volgende voorbeeld is een onboardingtrechter voor [Plant](https://create.roblox.com/docs/resources/plant-reference-project) , een tycoon-game waarin nieuwe gebruikers een boerderij binnenkomen, zaden planten, planten water geven, en meer in volgorde:

Onboardingstappen volgen in Plant

```

local AnalyticsService = game:GetService("AnalyticsService")

-- Log de eerste stap van de FTUE

AnalyticsService:LogOnboardingFunnelStepEvent(

    player,

    1, -- Stapnummer

    "In Boerderij" -- Stapnaam

)

-- Log de tweede stap

AnalyticsService:LogOnboardingFunnelStepEvent(

    player,

    2, -- Stapnummer

    "Zaad Planten" -- Stapnaam

)

```

### [Terugkerende trechters volgen](#terugkerende-trechters-volgen)[](#terugkerende-trechters-volgen)

Een terugkerende trechter houdt conversiegebeurtenissen bij die meerdere keren per gebruiker plaatsvinden.

Een veelvoorkomend voorbeeld is een winkeltrechter , die je kan helpen begrijpen hoe je de conversie van betalende gebruikers, ARPPU en inkomsten van je game kunt verbeteren. Het volgende voorbeeld is een winkeltrechter waarin gebruikers de winkel openen, een item bekijken, een item aan hun winkelwagentje toevoegen, en meer.

Gebruik funnelSessionId  om onderscheid te maken tussen verschillende sessies van dezelfde gebruiker in een terugkerende trechter, zoals het meerdere keren openen van de winkel in een enkele sessie.

Winkelstappen volgen

```

local AnalyticsService = game:GetService("AnalyticsService")

local HttpService = game:GetService("HttpService")

local funnelSessionId = HttpService:GenerateGUID()

-- Log wanneer de gebruiker de winkel opent

AnalyticsService:LogFunnelStepEvent(

    player,

    "ArmoryCheckout", -- Trechternaam die wordt gebruikt om stappen samen te groeperen

    funnelSessionId, -- Trechter-sessie-ID voor deze unieke checkout-sessie

    1, -- Stapnummer

    "Winkel Geopend" -- Stapnaam

)

-- Log wanneer de gebruiker een item bekijkt

AnalyticsService:LogFunnelStepEvent(

    player,

    "ArmoryCheckout", -- Trechternaam die wordt gebruikt om stappen samen te groeperen

    funnelSessionId, -- Trechter-sessie-ID voor deze unieke checkout-sessie

    2, -- Stapnummer

    "Item Bekeken" -- Stapnaam

)

-- Log wanneer de gebruiker iets aan het winkelwagentje toevoegt

AnalyticsService:LogFunnelStepEvent(

    player,

    "ArmoryCheckout", -- Trechternaam die wordt gebruikt om stappen samen te groeperen

    funnelSessionId, -- Trechter-sessie-ID voor deze unieke checkout-sessie

    3, -- Stapnummer

    "Aan Winkelwagentje Toegevoegd" -- Stapnaam

)

```

### [Implementatie van funnelSessionId](#implementatie-van-funnelsessionid)[](#implementatie-van-funnelsessionid)

Bij het implementeren van trechters kan een funnelSessionId  je helpen om je gebeurtenissen bij te houden, maar is mogelijk niet in elke situatie vereist. Gebruik de volgende richtlijnen:

-

Eenmalige trechters  - Je hoeft funnelSessionId  niet te gebruiken voor eenmalige trechters omdat ze slechts één keer per gebruiker plaatsvinden.

-

Winkeltrechters  - Gebruik funnelSessionId  om onderscheid te maken tussen verschillende sessies van dezelfde gebruiker in een terugkerende trechter, zoals het meerdere keren openen van de winkel in een enkele sessie in het [eerder voorbeeld](#terugkerende-trechters-volgen) . In gevallen zoals deze, waar de speler de winkel meerdere keren in een enkele sessie kan openen, is het aan te raden om een GUID als funnelSessionId  te gebruiken.

-

Item-upgrades  - Gebruik funnelSessionId  om onderscheid te maken tussen verschillende upgradepaden voor items, meestal over een langere periode dan een enkele speelsessie. In plaats van een GUID te gebruiken zoals in het geval van de winkeltrechter, kun je vaak een unieke sleutel opbouwen op basis van het item dat wordt geüpgraded, bijvoorbeeld: <playerId>-<itemId> .

Analytics houdt alleen de 10 meest recente unieke funnelSessionId -waarden per gebruiker voor elke trechter bij. Als een gebruiker een funnelSessionId  hergebruikt die niet tot hun 10 meest recente voor die trechter behoort, telt de trechter het als een nieuwe sessie.

## [Eerste stap](#eerste-stap)[](#eerste-stap)

Trechters beginnen wanneer de eerste stap wordt gelogd. Als je een trechter onmiddellijk wilt starten bij het joinen van de speler, log dan de eerste stap bij de PlayerAdded -gebeurtenis.

De eerste stap loggen in de PlayerAdded-gebeurtenis

```

local AnalyticsService = game:GetService("AnalyticsService")

local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)

    AnalyticsService:LogOnboardingFunnelStepEvent(

        player,

        1, -- Stapnummer

        "Speler Toegevoegd" -- Stapnaam

    )

end)

```

## [Herhaalde stappen](#herhaalde-stappen)[](#herhaalde-stappen)

Als een gebruiker een stap in een trechter herhaalt, beschouwt de trechter alleen de eerste instantie van de stap. Bijvoorbeeld, als een gebruiker stap 2 van een trechter twee keer logt, telt de trechter alleen de eerste instantie van stap 2. Je hoeft geen speciale actie te ondernemen om eenmalige trechters te behandelen voor spelers die disconnecten en opnieuw verbinden, en funnelSessionId  behandelt terugkerende trechters.

Herhaalde stappen worden genegeerd door de trechter, maar ze worden nog steeds gelogd en dragen bij aan de [globale rate limit](/docs/nl-nl/production/analytics/event-types#beperkingen-van-evenementtracking) .

## [Overgeslagen stappen](#overgeslagen-stappen)[](#overgeslagen-stappen)

Als je om de een of andere reden een stap in een trechter overslaat, worden de eerdere stappen automatisch als voltooid beschouwd. Bijvoorbeeld, als je een trechter hebt met stappen 1, 2 en 3 en je logt stap 3 zonder stap 1 of 2 te loggen, beschouwt de trechter stappen 1 en 2 als voltooid.

## [Gebruik trechterfilters](#gebruik-trechterfilters)[](#gebruik-trechterfilters)

Roblox biedt filters om je te helpen je trechtergegevens te analyseren. Deze omvatten spelersgegevens en apparaatgegevens, en je kunt ook aangepaste gegevens verzenden. In sommige gevallen kan de status van een speler tijdens de trechter veranderen, zoals wanneer de speler van apparaat wisselt van mobiel naar desktop.

Om dubbele telling van trechters te voorkomen, zijn filters alleen van toepassing op de eerste stap  van de trechter. Dit betekent dat als een speler van apparaat wisselt tijdens de trechter, de trechter alleen aan hun apparaat wordt toegeschreven op het moment dat ze de trechter binnenkomen.

Evenzo worden trechters weergegeven per cohort, wat betekent dat als een speler de trechter op 19/6 binnenkomt, de trechter aan de cohort van 19/6 wordt toegeschreven, zelfs als ze de trechter op 20/6 voltooien.

## [Wijzig trechters](#wijzig-trechters)[](#wijzig-trechters)

Nadat je een update hebt gemaakt aan je trechterstappen, is het belangrijk om het juiste datumbereik in te stellen om de nieuwste trechter te zien. Als de huidige datum 21/6 is en je stap 2 van je onboardingtrechter op 14/6 hebt bijgewerkt, moet je het datumbereik instellen op 14/6 – 21/6 om de nieuwste trechter te bekijken.

Als je een datumbereik selecteert dat een update van een trechterstap omvat, wordt er een waarschuwing weergegeven op de relevante stap:

 ![Een waarschuwing wordt weergegeven op het trechterdashboard die een naamswijziging binnen het geselecteerde datumbereik aangeeft.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Plant-Game-Warning.png)

## [Bescherm je trechters tegen exploiters](#bescherm-je-trechters-tegen-exploiters)[](#bescherm-je-trechters-tegen-exploiters)

Om je gegevens schoon te houden, is het belangrijk om een bepaald niveau van gegevensvalidatie in je servercode toe te voegen om te voorkomen dat exploiters ongeldige gegevens naar je analytics-service verzenden.

Bijvoorbeeld, als je een onboardingtrechter hebt met drie stappen, kun je een RemoteEvent  gebruiken voor de client om de server te informeren wanneer de speler elke stap heeft voltooid en een servercontrole toevoegen om ervoor te zorgen dat het stapnummer geldig is voordat je de gebeurtenis logt:

Client-side event code

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local onboardingEvent = ReplicatedStorage:WaitForChild("OnboardingEvent")

local function fireOnboardingEvent(step: number)

	onboardingEvent:FireServer({ step = step })

end

fireOnboardingEvent(1)

fireOnboardingEvent(2)

fireOnboardingEvent(10) -- ongeldige stap

```

Server-side event code

```

local AnalyticsService = game:GetService("AnalyticsService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local onboardingEvent = ReplicatedStorage:WaitForChild("OnboardingEvent")

local maxStep = 3

local function onPlayerEventFired(player: Player, args: { step: number })

	local step = args.step

	if(step > maxStep) then

		warn(`Ongeldig tutorial stap {step} ontvangen van client.`)

		return

	end

	print(`{player.Name} voltooide stap: {step}`)

	AnalyticsService:LogOnboardingFunnelStepEvent(player, step)

end

onboardingEvent.OnServerEvent:Connect(onPlayerEventFired)

```

## [Gebruik aangepaste velden](#gebruik-aangepaste-velden)[](#gebruik-aangepaste-velden)

Trechtergebeurtenissen stellen je ook in staat om op aangepaste velden te splitsen om een gemakkelijkere vergelijking tussen segmenten te ondersteunen. Bijvoorbeeld, je kunt bijhouden welke starterauto spelers de beste voortgang geeft, of verschillende kaarten koppelen om te zien of een bepaalde kaart een betere game-loop heeft dan andere.

 ![Een dropdown die de drie aangepaste velden aangeeft die je kunt vergelijken, samen met standaard uitsplitsingen zoals leeftijd, geslacht, besturingssysteem en meer.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Custom-Event-Breakdown.png)

Voor meer informatie, zie [aangepaste velden](/docs/nl-nl/production/analytics/custom-fields) .

## [Gebruik trechters om je game te laten groeien](#gebruik-trechters-om-je-game-te-laten-groeien)[](#gebruik-trechters-om-je-game-te-laten-groeien)

Een van de belangrijkste trechters om te volgen is onboarding, omdat veel games moeite hebben met het behouden en betrekken van nieuwe gebruikers.

In de onboardingtrechter voor [Plant](https://create.roblox.com/docs/resources/plant-reference-project)  hieronder is de grootste afname stap 2 ("Zaad Planten").

 ![Trechterdiagram voor de Plant-game dat een afname van 70% laat zien tussen In Boerderij, stap 1, en Zaad Planten, stap 2.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Plant-Game-Funnel.png)

Op basis van deze gegevens zou je kunnen:

-

Contextuele indicatoren toevoegen om gebruikers beter te begeleiden bij het planten van zaden wanneer ze beginnen.

-

Een nieuwe gebruikerservaring ontwerpen die vereist dat gebruikers zaden planten en een succesvolle plant laten groeien voordat ze de rest van de game verkennen. Je kunt deze gebeurtenis verbeteren door [positieve feedbackelementen](/docs/nl-nl/production/game-design/onboarding-techniques#faciliteer-feedback)  te creëren of andere game-ontwerptechnieken te gebruiken.

 ![In-game weergave van de Plant-game met prompts om zaden te planten boven de bloempotten.](https://prod.docsiteassets.roblox.com/assets/analytics/event-types/Plant-Game-Prompts.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
