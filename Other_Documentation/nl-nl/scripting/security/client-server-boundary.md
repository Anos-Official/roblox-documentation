<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/security/client-server-boundary -->

Beveiligen van de client-servergrens | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. Beveiliging

# Beveiligen van de client-servergrens

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De volgende inhoud behandelt verschillende concepten en tactieken om de beveiliging te verbeteren en valsspelen in je Roblox-spellen te verminderen. Het wordt ten zeerste aanbevolen dat alle ontwikkelaars deze doorlezen om ervoor te zorgen dat je spellen veilig en eerlijk zijn voor alle gebruikers. Controleer de zijbalk voor aanvullende beveiligingsthema's.

Elke keer dat een client een actie op de server kan activeren, is er potentieel voor misbruik. Terwijl [RemoteEvents](/docs/nl-nl/reference/engine/classes/RemoteEvent)  en [RemoteFunctions](/docs/nl-nl/reference/engine/classes/RemoteFunction)  de meest voorkomende aanvalsvector hier zijn, zijn andere instanties zoals [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)  ook kwetsbaar. Dit gedeelte behandelt hoe je deze grens kunt beveiligen.

## [Valideren van externe invoer](#valideren-van-externe-invoer)[](#valideren-van-externe-invoer)

Elk stuk gegevens dat van een client wordt verzonden, moet door de server worden gevalideerd voordat het wordt gebruikt. Pas deze lagen van validatie toe op basis van wat de remote doet.

### [Context/vergunningvalidatie](#contextvergunningvalidatie)[](#contextvergunningvalidatie)

Dit is noodzakelijk voor remotes die de staat van het spel, de voortgang of andere spelers beïnvloeden. De server moet verifiëren of de speler de nodige vergunningen heeft om het verzoek te doen. Bijvoorbeeld, is de speler dichtbij genoeg bij een winkel om iets te kopen? Heeft hij een sleutel nodig om een deur te openen? Is hun karakter levend?

Validatie is noodzakelijk voor remotes die:

-

Beloningen toekennen of de voortgang van de speler wijzigen

-

Andere spelers of gedeelde spelstatus beïnvloeden

-

Acties uitvoeren met afstand-, tijd- of vergunningseisen (bijvoorbeeld, winkelafstand)

### [Type- en structuurvalidatie](#type--en-structuurvalidatie)[](#type--en-structuurvalidatie)

Een andere aanval die exploiters kunnen lanceren, is het verzenden van technisch geldige types, maar deze extreem groot, lang of anderszins verkeerd gevormd maken. Bijvoorbeeld, als de server een dure bewerking op een string moet uitvoeren die met de lengte schaalt, kan een exploiter een ongelooflijk grote of verkeerd gevormde string verzenden om de server te vertragen.

Een andere veelvoorkomende aanval die exploiters kunnen gebruiken, houdt in dat ze [tables](/docs/nl-nl/reference/engine/libraries/table)  in plaats van een [Instance](/docs/nl-nl/reference/engine/classes/Instance)  verzenden. Complexe payloads kunnen nabootsen wat anders een gewone objectreferentie zou zijn.

Bijvoorbeeld, voorzien van een [in-game winkelfsysteem](#in-game-winkel)  waar itemgegevens zoals prijzen zijn opgeslagen in [NumberValue](/docs/nl-nl/reference/engine/classes/NumberValue) -objecten, kan een exploiter alle andere controles omzeilen door het volgende te doen:

LocalScript in StarterPlayerScripts

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local itemDataFolder = ReplicatedStorage:WaitForChild("ItemData")

local buyItemEvent = ReplicatedStorage:WaitForChild("BuyItemEvent")

local payload = {

	Name = "Ultra Blade",

	ClassName = "Folder",

	Parent = itemDataFolder,

	Price = {

		Name = "Price",

		ClassName = "NumberValue",

		Value = 0, -- Negatieve waarden kunnen ook worden gebruikt, wat resulteert in het geven van valuta in plaats van het nemen ervan!

	},

}

-- Stuur kwaadaardige payload naar de server (dit zal worden afgewezen)

print(buyItemEvent:InvokeServer(payload))  -- Geeft "false Invalid item provided" weer

-- Stuur een echt item naar de server (dit zal doorgaan!)

print(buyItemEvent:InvokeServer(itemDatafolder["Real Blade"]))  -- Geeft "true" en resterende valuta weer als de aankoop slaagt

```

Script in ServerScriptStorage

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local itemDataFolder = ReplicatedStorage:WaitForChild("ItemData")

local buyItemEvent = ReplicatedStorage:WaitForChild("BuyItemEvent")

local function buyItem(player, item)

	-- Controleer of het doorgegeven item niet vervalst is en in de ItemData-map staat

	if typeof(item) ~= "Instance" or not item:IsDescendantOf(itemDataFolder) then

		return false, "Invalid item provided"

	end

	-- De server kan dan doorgaan met het verwerken van de aankoop op basis van de onderstaande voorbeeldstroom

end

-- Koppel "buyItem()" aan de callback van de remote functie

buyItemEvent.OnServerInvoke = buyItem

```

### [Waardevalidatie](#waardevalidatie)[](#waardevalidatie)

Naast het valideren van types en gegevens, moet je de waarden die worden doorgegeven via [RemoteEvents](/docs/nl-nl/reference/engine/classes/RemoteEvent)  en [RemoteFunctions](/docs/nl-nl/reference/engine/classes/RemoteFunction)  valideren, om ervoor te zorgen dat ze geldig en logisch zijn in de context die wordt aangevraagd. Dit is essentieel voor remotes die omgaan met valuta, items, numerieke invoer of door gebruikers gegenereerde inhoud. Je moet ervoor zorgen dat waarden binnen de verwachte grenzen liggen, bijvoorbeeld dat een aankoophoeveelheid groter is dan nul of dat een item-ID overeenkomt met een echt item in je spel.

Let op dat zowel inf  als NaN geldige nummer types zijn, maar beide kunnen grote problemen veroorzaken als een exploiter ze verzendt en ze niet correct worden afgehandeld. Gebruik [math.isfinite()](/docs/nl-nl/reference/engine/libraries/math#isfinite)  om ze te detecteren en af te wijzen:

```

-- Weiger numerieke waarden die NaN of +/-inf zijn

if not math.isfinite(offeredGold) then

	return false, "Invalid number provided"

end

```

### [Het gevaar van NaN](#het-gevaar-van-nan)[](#het-gevaar-van-nan)

Een exploiter kan NaN (Not a Number) als argument verzenden. NaN is uniek gevaarlijk omdat het van het type "nummer" is, maar faalt bij alle standaardvergelijkingen, waardoor het subtiel logische controles kan omzeilen die veilig lijken. Laten we kijken naar een kwetsbaar handelssysteem waar een speler een aanbod doet.

```

-- KWETSBARE SERVER CODE

local function onCreateTradeOffer(player, offeredGold)

    -- 1. TYPE CHECK: Dit slaagt! typeof(NaN) is "number".

    if typeof(offeredGold) ~= "number" then

      return "Invalid offer"

    end

    -- 2. RANGE CHECK: Dit wordt omzeild!

    -- (NaN < 0) is onwaar. (NaN > 1000000) is ook onwaar. De controle doet niets.

    if offeredGold < 0 or offeredGold > 1000000 then

      return "Offer out of range"

    end

    -- 3. INVENTORY CHECK: Dit wordt omzeild!

    -- (NaN > player.Gold.Value) is onwaar.

    if offeredGold > player.Gold.Value then

      return "Not enough gold"

    end

    -- KWETSBAARHEID: Een frauduleus handelsaanbod met NaN-goud wordt gecreëerd!

    createTrade(player, {gold = offeredGold})

    return "Trade offer created."

end

```

De exploiter heeft met succes een handelsaanbod gecreëerd zonder goud te hebben, omdat elke controle stilletjes faalde. Bovendien zal deze enkele NaN-waarde nu elk ander systeem dat probeert het te gebruiken vergiftigen, en zelfs verspreiden naar andere spelers via het aanbod.

Hieronder staan enkele voorbeelden op hoog niveau die de veilige ontwerpeisen van veelvoorkomende in-game functies behandelen.

### [In-game winkel](#in-game-winkel)[](#in-game-winkel)

Overweeg een in-game winkelfsysteem met een gebruikersinterface, bijvoorbeeld een productselectiemenu met een "Kopen" knop. Wanneer de knop wordt ingedrukt, kun je een [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  tussen de client en de server aanroepen om de aankoop aan te vragen. Het is echter belangrijk dat de server, de meest betrouwbare beheerder van het spel, bevestigt dat de gebruiker genoeg geld heeft om het item te kopen.

![Voorbeeld aankoopstroom van client naar server via een RemoteEvent](https://prod.docsiteassets.roblox.com/assets/scripting/security/Remote-Purchase-Flow.png) Voorbeeld aankoopstroom van client naar server via een [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)

### [Wapen richten](#wapen-richten)[](#wapen-richten)

Gevechtsscenario's vereisen speciale aandacht voor het valideren van waarden, met name via richten en hitvalidatie.

Stel je een spel voor waarin een speler een laserstraal op een andere speler kan afvuren. In plaats van dat de client de server vertelt wie te beschadigen, moet deze in plaats daarvan de server vertellen wat de oorsprongpositie van de schot is en het deel/positie dat hij denkt dat hij heeft geraakt. De server kan dan het volgende valideren:

-

De positie waar de client meldt dat hij vanaf schiet, is dichtbij het karakter van de speler op de server. Let op dat de server en client iets van elkaar zullen verschillen vanwege latentie, dus er moet extra tolerantie worden toegepast.

-

De positie waar de client meldt dat hij heeft geraakt, is redelijk dichtbij de positie van het deel dat de client meldt te hebben geraakt, op de server.

-

Er zijn geen statische obstructies tussen de positie waar de client meldt dat hij vanaf schiet en de positie waar de client meldt dat hij naartoe schiet. Deze controle zorgt ervoor dat een client niet probeert door muren te schieten. Let op dat dit alleen statische geometrie moet controleren om te voorkomen dat geldige schoten worden afgewezen vanwege latentie.

Bovendien wil je misschien verdere server-side validaties implementeren, zoals:

-

Volg wanneer de speler voor het laatst zijn wapen heeft afgevuurd en valideer om ervoor te zorgen dat ze niet te snel schieten.

-

Volg de hoeveelheid munitie van elke speler op de server en bevestig dat een schietende speler genoeg munitie heeft om de wapenaanval uit te voeren.

-

Als je teams of een "spelers tegen bots" gevechtssysteem hebt geïmplementeerd, bevestig dan dat het getroffene karakter een vijand is, geen teamgenoot.

-

Bevestig dat de getroffene speler levend is.

-

Bewaar wapen- en spelerstatus op de server en bevestig dat een schietende speler niet wordt geblokkeerd door een huidige actie zoals herladen of een status zoals sprinten.

## [Snelheidsbeperking](#snelheidsbeperking)[](#snelheidsbeperking)

Wanneer server-side logica kan worden geactiveerd door de client (via remotes, Touched-events, nabijheidsprompten, ClickDetectors, enz.), is er een mogelijkheid dat deze logica kan worden gespamd door exploiters of zelfs legitieme gebruikers. Snelheidsbeperking controleert hoe vaak deze acties kunnen worden uitgevoerd, waardoor misbruik en systeemoverbelasting worden voorkomen. Hoewel het praktisch (en soms noodzakelijk) is om snelheidsbeperkingen aan de clientzijde te implementeren, moet je nooit uitsluitend op een client-side snelheidsbeperking vertrouwen.

Voor elke server-side logica die door een client kan worden geactiveerd, moet je altijd de maximale snelheid overwegen waarop dergelijke logica moet draaien. Veel server-side acties moeten hun frequentie beperken om misbruik of falen te voorkomen, zoals:

-

Roblox API-aanroepen : Backend-API's zoals [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  en [BadgeService](/docs/nl-nl/reference/engine/classes/BadgeService)  hebben ingebouwde snelheidsbeperkingen die ervoor zorgen dat je verzoeken falen als ze worden overschreden

-

Computationally dure bewerkingen : Acties die aanzienlijke serverbronnen verbruiken of andere clients beïnvloeden

-

Servervoorbeeld: grote modellen klonen vanuit ServerStorage, zelfs als ze nooit naar clients worden gerepliceerd

-

Clientvoorbeeld : alle verbonden clients instrueren om hun GUI tegelijkertijd bij te werken

-

Misbruikbare mechanics : Acties die misbruikt kunnen worden als ze snel worden uitgevoerd, zoals het toekennen van onkwetsbaarheid, het teleporteren van spelers of het toekennen van valuta

### [Token bucket voorbeeld](#token-bucket-voorbeeld)[](#token-bucket-voorbeeld)

Een robuuste en veelgebruikte benadering voor snelheidsbeperking is het token bucket -algoritme. Stel je voor dat elke gebruiker een emmer heeft die een bepaald aantal tokens kan bevatten. Om een actie uit te voeren, moet de gebruiker een token uitgeven. De emmer vult zich met nieuwe tokens tegen een constante snelheid. Deze methode staat korte uitbarstingen van acties toe wanneer dat nodig is, maar voorkomt aanhoudende spam door een gemiddelde snelheid in de tijd af te dwingen.

```

--!strict

-- Module bevindt zich in ServerScriptService

type UserId = number

type Bucket = {

    tokens: number,

    last: number,

}

type TokenBucketT = {

    capacity: number,

    refillPerSecond: number,

    buckets: { [UserId]: Bucket },

    allow: (self: TokenBucketT, userId: UserId) -> boolean,

}

local TokenBucket = {}

TokenBucket.__index = TokenBucket

-- Creëert een limiter die maximaal `capacity` evenementen toestaat, die weer vol wordt

-- op een snelheid van `capacity / windowSeconds` tokens per seconde.

function TokenBucket.new(capacity: number, windowSeconds: number): TokenBucketT

    assert(capacity >= 1, "capacity must be >= 1")

    assert(windowSeconds > 0, "windowSeconds must be > 0")

    local self: TokenBucketT = {

        capacity = capacity,

        refillPerSecond = capacity / windowSeconds,

        buckets = {},

    }

    return (setmetatable(self, TokenBucket) :: any) :: TokenBucketT

end

local function refill(b: Bucket, now: number, cap: number, rate: number)

    local elapsed = now - b.last

    if elapsed > 0 then

        b.tokens = math.min(cap, b.tokens + elapsed * rate)

        b.last = now

    end

end

-- Geeft false terug als de gebruiker hun limiet zou overschrijden

function TokenBucket:allow(userId: UserId): boolean

    local now = time()

    local b = self.buckets[userId]

    if not b then

        b = { tokens = self.capacity, last = now }

        self.buckets[userId] = b

    else

        refill(b, now, self.capacity, self.refillPerSecond)

    end

    if b.tokens >= 1 then

        b.tokens -= 1

        return true

    end

    return false

end

return TokenBucket

```

Om de module te gebruiken, maak je eerst een nieuwe limiter-instantie met TokenBucket.new(capacity, windowSeconds) . De capacity  is het maximale aantal verzoeken dat een gebruiker in een snelle uitbarsting kan doen, en de windowSeconds  bepaalt hoe lang het duurt om al die tokens weer te vullen. Bijvoorbeeld, TokenBucket.new(5, 10)  creëert een limiter die uitbarstingen van maximaal 5 verzoeken toestaat en elke twee seconden (10 seconden / 5 tokens) één token weer vult.

Voordat je beschermde logica uitvoert, maak je een oproep naar de :allow(userId) -methode, waarbij je de actie weigert als deze false retourneert. Het is ook een goede praktijk om de emmergegevens van de gebruiker te wissen wanneer ze vertrekken om geheugenlekken te voorkomen.

Het volgende voorbeeldscript demonstreert hoe je een RemoteEvent  dat wordt gebruikt voor een aangepast chatsysteem kunt beschermen tegen spammen door spelers.

```

-- Voorbeeldgebruik in een serverscript

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local ServerScriptService = game:GetService("ServerScriptService")

local TokenBucket = require(ServerScriptService.TokenBucket)

local ChatRemote = ReplicatedStorage:WaitForChild("ChatRemote") :: RemoteEvent

-- 5 berichten per 10 seconden (capaciteit 5, vult bij 0.5 tokens/sec)

local chatLimiter = TokenBucket.new(5, 10)

ChatRemote.OnServerEvent:Connect(function(player: Player, message: string)

    if not chatLimiter:allow(player.UserId) then

        -- Te snel: laat het verzoek vallen of stuur een spamwaarschuwing

        return

    end

    -- Verwerk bericht (na andere validatie)

    broadcastMessage(player, message)

end)

-- Opruimen om geheugenlekken te voorkomen

Players.PlayerRemoving:Connect(function(p: Player)

    chatLimiter.buckets[p.UserId] = nil

end)

```

## [Beveiligen van client-geactiveerde instanties](#beveiligen-van-client-geactiveerde-instanties)[](#beveiligen-van-client-geactiveerde-instanties)

[ProximityPrompts](/docs/nl-nl/reference/engine/classes/ProximityPrompt) , [ClickDetectors](/docs/nl-nl/reference/engine/classes/ClickDetector)  en [DragDetectors](/docs/nl-nl/reference/engine/classes/DragDetector)  zijn geen remotes, maar een exploiter kan hun evenementen op elke afstand, op elk moment activeren, vaak negerend eigenschappen zoals Enabled  of MaxActivationDistance . Deze objecten moeten met dezelfde strengheid worden beveiligd als remotes.

### [ProximityPrompt](#proximityprompt)[](#proximityprompt)

-

Een exploiter kan elk evenement afvuren, zelfs als Enabled  op de server false is.

-

Enabled , MaxActivationDistance  en RequiresLineOfSight  kunnen stilletjes op de client worden gewijzigd, zodat elke gerepliceerde [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)  kan worden gezien en mogelijk van elke locatie kan worden geactiveerd.

-

De server accepteert hold-evenementen (zoals PromptButtonHoldBegan) zelfs als de serverzijde HoldDuration  nul is. De client kan de HoldDuration  manipuleren om interacties onnatuurlijk snel uit te voeren.

-

Alleen het Triggered -evenement heeft een serverzijde afstandscontrole. Andere evenementen (zoals PromptButtonHoldBegan  en TriggerEnded ) hebben geen afstandscontrole en kunnen willekeurig door elke client worden verzonden.

### [ClickDetector](#clickdetector)[](#clickdetector)

-

Er zijn helemaal geen controles op de server voor enige evenementen.

-

Exploiters kunnen elk evenement op elke afstand repliceren, zelfs als de ClickDetector is uitgeschakeld (MaxActivationDistance  van 0 of DragDetector.Enabled  false).

-

Evenementen kunnen worden gerepliceerd, zelfs als de [ClickDetector](/docs/nl-nl/reference/engine/classes/ClickDetector)  niet aan iets klikbaars is gekoppeld.

### [DragDetector](#dragdetector)[](#dragdetector)

-

Voor evenementen die zijn geërfd van ClickDetector zijn er geen controles.

-

Voor slepevenementen worden de Enabled -eigenschap en PermissionPolicy -eigenschappen gecontroleerd en gerespecteerd door de server. Alle andere eigenschappen worden niet gecontroleerd.

Wanneer een van deze evenementen wordt geactiveerd, moet je serverscript zijn eigen validatie uitvoeren voordat je enige actie onderneemt:

-

Controleer of het is ingeschakeld: Zorg ervoor dat de instantie bedoeld is om ingeschakeld te zijn door zijn eigenschappen (zoals Enabled, HoldDuration, RunLocally, enz.) op de server te controleren. Deze stap is niet nodig als het object altijd is ingeschakeld.

-

Controleer de spelerstatus: Zorg ervoor dat de speler de actie kan uitvoeren, gezien de huidige status van de speler. Is het karakter van de speler in de wereld? Is hun karakter dichtbij genoeg bij het object? Moet de speler levend zijn om met dit object te kunnen interageren? Controleer andere spelerstatussen die door je spel op de server worden onderhouden indien nodig.

-

Pas snelheidsbeperking toe: Zoals behandeld in [Snelheidsbeperking](#snelheidsbeperking) , pas cooldowns toe aan de client en handhaaf snelheidsbeperkingen op de server om te voorkomen dat deze evenementen worden gespamd en misbruikt. Voor interacties die naar verwachting een minimale tijd in beslag nemen, zorg ervoor dat clients ze niet te snel voltooien.

Opmerking over netwerkbezit : Standaard, als een van deze objecten kinderen zijn van niet-geankerde delen of een niet-geankerde assemblage, kan een exploiter het netwerkbezit van de bovenliggende delen overnemen en ze rechtstreeks naar hun karakter verplaatsen, waardoor afstandscontroles worden omzeild. Voor kritieke acties, gebruik geankerde delen of de netwerkbezit-API samen met de nodige server-side validatie.

### [RemoteEvents en RemoteFunctions](#remoteevents-en-remotefunctions)[](#remoteevents-en-remotefunctions)

Beperk de reikwijdte en impact van [RemoteFunctions](/docs/nl-nl/reference/engine/classes/RemoteFunction)  en [RemoteEvents](/docs/nl-nl/reference/engine/classes/RemoteEvent) . Wees uiterst voorzichtig met het dynamisch laden van activa (zelfs texturen of geluiden) of het uitvoeren van spelcode (vooral via require) op basis van de argumenten van remote functies/evenementen. Vermijd het implementeren van remotes die een client toestaan om een willekeurig pad of instantie referentie op te geven voor de server om te verwijderen of te wijzigen, zelfs als dergelijke wijzigingen triviaal lijken. Remotes die willekeurige instantie status kunnen wijzigen of wijdverspreide wijzigingen in de DataModel-boom kunnen aanbrengen, kunnen vaak worden gekoppeld aan andere bugs om de algehele status of logica ernstig te beïnvloeden. Controleer niet alleen het type instantie-argumenten, maar ook de klasse en verwachte locatie of structuur binnen de DataModel.

## [Client-naar-client communicatie](#client-naar-client-communicatie)[](#client-naar-client-communicatie)

Sommige remotes zijn ontworpen om één client effecten op andere clients te laten activeren. Dit gebeurt wanneer een client een remote naar de server afvuurt, die vervolgens RemoteEvent:FireAllClients() , RemoteEvent:FireClient()  of vergelijkbare methoden gebruikt om informatie door te geven. Dit patroon is gevaarlijk als het niet goed is beveiligd - de server moet een poortwachter zijn, niet alleen een doorgeefluik.

Stel je een scenario voor waarin spelers een bliksemspreuk kunnen casten. Wanneer deze wordt gecast, zien nabijgelegen spelers de flits, horen ze het geluid en ervaren ze cameratrilling.

Een kwetsbaar serverscript kan er als volgt uitzien:

Kwetsbare servercode (script in ServerScriptStorage)

```

local castLightningEvent = game.ReplicatedStorage.CastLightning

-- Dit serverscript geeft het bericht door aan iedereen zonder validatie

castLightningEvent.OnServerEvent:Connect(function(player, strikePosition)

    castLightningEvent:FireAllClients(strikePosition)

end)

```

Client effect code

```

local castLightningEvent = game.ReplicatedStorage.CastLightning

-- Maak visuele en geluidseffecten op de client

local function createLightningEffect(strikePosition)

    -- Code om de camera te laten trillen

    -- Code om een hard bliksemschichtgeluid af te spelen

    -- Code om een visuele bliksemschicht te creëren

    print("Bliksem slaat in op: " .. tostring(strikePosition))

end

-- Wanneer de server het evenement uitzendt, voert deze client het effect uit

castLightningEvent.OnClientEvent:Connect(createLightningEffect)

```

Een exploiter kan dit kwetsbare systeem misbruiken door:

-

Spammen : De remote honderden keren per seconde aanroepen, waardoor continue effecten ontstaan die het spel on speelbaar maken

-

Ongeldige gegevens : Nil, NaN of verkeerde types verzenden die scriptfouten op alle clients veroorzaken

-

Ongeautoriseerd gebruik : Spreuken casten die ze niet hebben ontgrendeld of waarvoor ze geen middelen hebben

De server moet een poortwachter  zijn, niet een doorgeefluik. Voordat het uitzendt, moet het het verzoek valideren en snelheidsbeperkingen per speler toepassen. Hier is een voorbeeld van enkele methoden die kunnen worden gebruikt om het verzoek te valideren.

Veilige servercode

```

local castLightningEvent = game.ReplicatedStorage.CastLightning

local playerCooldowns = {}

local COOLDOWN_TIME = 3

castLightningEvent.OnServerEvent:Connect(function(player, strikePosition)

    -- 1. Typevalidatie

    if typeof(strikePosition) ~= "Vector3" then

        return -- Ongeldig type, stilletjes afwijzen

    end

    -- 2. Controleer op NaN (NaN ~= NaN is de enige manier om het te detecteren)

    if strikePosition.X ~= strikePosition.X then

        return -- Bevat NaN, afwijzen

    end

    -- 3. Voorbeeld van snelheidsbeperking

    local lastCast = playerCooldowns[player] or 0

    if tick() - lastCast < COOLDOWN_TIME then

        return -- Nog steeds op cooldown

    end

    -- 4. Voorbeeld van vergunningcontrole

    if not player:GetAttribute("HasLightningSpell") then

        return -- Speler heeft deze spreuk niet

    end

    -- 5. Voorbeeld van bereikvalidatie

    local character = player.Character

    local humanoidRootPart = character and character:FindFirstChild("HumanoidRootPart")

    if not humanoidRootPart then

        return

    end

    local distance = (humanoidRootPart.Position - strikePosition).Magnitude

    if distance > 100 then

        return -- Buiten bereik

    end

    -- Alle controles geslaagd - veilig om uit te zenden

    playerCooldowns[player] = tick()

    castLightningEvent:FireAllClients(player, strikePosition)

end)

```

Door deze controles te implementeren, wordt het moeilijker voor een exploiter om het spel voor andere spelers te verpesten. De server fungeert als een beschermende barrière, waardoor alleen geldige, geautoriseerde acties naar andere clients worden uitgezonden.

## [Speciale overwegingen](#speciale-overwegingen)[](#speciale-overwegingen)

De volgende zijn enkele aanvullende gevallen die je moet overwegen en die mogelijk speciale behandeling vereisen.

### [Manipulatie van gegevensopslag](#manipulatie-van-gegevensopslag)[](#manipulatie-van-gegevensopslag)

In spellen die DataStoreService gebruiken om spelersgegevens op te slaan, kunnen exploiters profiteren van ongeldige gegevens, race-omstandigheden om opslagen te corrumperen of items in een DataStore te dupliceren. Dit is vooral problematisch in spellen met itemhandel, marktplaatsen en valutastelsels.

Zorg ervoor dat alle acties die worden uitgevoerd via een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  of [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  die invloed hebben op spelersgegevens met clientinvoer, worden gesaneerd op basis van het volgende:

-

Instantiewaarden  kunnen niet worden geserialiseerd in een DataStore en zullen falen. Gebruik typevalidatie om dit te voorkomen.

-

DataStores hebben gegevenslimieten . Strings van willekeurige lengte moeten worden gecontroleerd en/of beperkt om dit te voorkomen, naast ervoor te zorgen dat er geen onbeperkte willekeurige sleutels aan tabellen kunnen worden toegevoegd door de client.

-

Tabelindices kunnen niet NaN of nil zijn . Itereer over alle tabellen die door de client zijn doorgegeven en verifieer dat alle indices geldig zijn.

-

DataStores kunnen alleen geldige UTF-8-tekens accepteren , dus je moet alle strings die door de client worden verstrekt saneren via utf8.len() om ervoor te zorgen dat ze geldig zijn. utf8.len() retourneert de lengte van een string, waarbij unicode-tekens als één teken worden behandeld; als een ongeldig UTF-8-teken wordt aangetroffen, retourneert het nil en de positie van het ongeldige teken. Let op dat ongeldige UTF-8-strings ook in tabellen als sleutels en waarden kunnen voorkomen.

-

Oneindige/NaN nummer exploits  - Exploiters kunnen waarden zoals -1/0, 0/0 of math.huge verzenden om oneindige valuta te veroorzaken of berekeningen te breken. Valideer altijd met de methoden die zijn beschreven in [het gevaar van NaN](#het-gevaar-van-nan) .

Race-omstandigheden kunnen optreden wanneer spelers de timing tussen bewerkingen manipuleren om items te dupliceren of gegevens te corrumperen.

Voorbeeld van handelsmisbruik:  Een speler initieert een handel, stuurt hun item naar een andere speler en verlaat vervolgens onmiddellijk het spel. Als de handel wordt voltooid maar hun DataStore-opslag mislukt vanwege ongeldige gegevens, komen ze terug met hun oorspronkelijke items terwijl de andere speler de verhandelde items behoudt - wat resulteert in duplicatie.

Preventiestrategieën:

-

Valideer alle gegevens voordat je handelsoperaties uitvoert

-

Gebruik transactieachtige patronen waarbij de gegevens van alle spelers worden gevalideerd voordat wijzigingen worden doorgevoerd

-

Implementeer goede foutafhandeling die alle wijzigingen terugdraait als een deel mislukt

### [MarketplaceService](#marketplaceservice)[](#marketplaceservice)

Voor interacties met [MarketplaceService](/docs/nl-nl/reference/engine/classes/MarketplaceService) , zoals passen of ontwikkelaarsproducten, moet alle aankoopvalidatie en itemtoekenning op de server plaatsvinden. Gebruik specifiek de ProcessReceipt -callback om aankoopbewijzen veilig te valideren. Vertrouw nooit op een client-side signaal, zoals PromptProductPurchaseFinished , om een aankoop te bevestigen zonder serververificatie, aangezien deze kunnen worden vervalst. Zorg ervoor dat je ProcessReceipt -functie de details van het bewijs grondig controleert en alleen items of valuta toekent na bevestiging van een legitieme transactie met de Roblox-servers, en wees voorbereid om om te gaan met gevallen waarin een product al is toegekend voor een gegeven bewijs.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
