<!-- Source: https://create.roblox.com/docs/nl-nl/projects/server-authority/techniques -->

Server autoriteitstechnieken | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Architectuur](/docs/nl-nl/projects/data-model)
8. /
9. [Serverautoriteit](/docs/nl-nl/projects/server-authority)

# Server autoriteitstechnieken

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze gids beschrijft verschillende technieken voor het creëren van hoogwaardige, soepele multiplayergames met behulp van het [server autoriteitsmodel](/docs/nl-nl/projects/server-authority) .

## [Voorspellende instantiecreatie (instance stitching)](#voorspellende-instantiecreatie-instance-stitching)[](#voorspellende-instantiecreatie-instance-stitching)

Instance stitching  stelt clientscripts in staat om voorspellend [Instances](/docs/nl-nl/reference/engine/classes/Instance)  te creëren binnen [RunService:BindToSimulation()](/docs/nl-nl/reference/engine/classes/RunService#BindToSimulation)  callbacks. De client creëert de [Instance](/docs/nl-nl/reference/engine/classes/Instance)  onmiddellijk zonder te wachten op een server round‑trip; wanneer de autoritatieve kopie van de server arriveert, worden de door de client gemaakte instantie en de autoritatieve kopie van de server samengevoegd tot één. Vanuit het perspectief van je script bestaat de [Instance](/docs/nl-nl/reference/engine/classes/Instance)  onmiddellijk en is deze consistent met de server.

Instance stitching is nuttig in gevallen waarin een instantie zo snel mogelijk zichtbaar en actief moet zijn op de client. Hoewel de server uiteindelijk elke instantie die de client nodig heeft (samen met eventuele effecten die ze op de wereld hebben gehad) zal repliceren, brengt dit proces ten minste één round‑trip latentie met zich mee vanwege servercommunicatie. Voorbeelden zijn het afvuren van een raketwerper en het creëren van fysica-beperkingen — zonder stitching zal de client de raket ver weg zien verschijnen, of enige jitter wanneer de nieuwe beperkingen naar hen repliceren.

### [Technisch gedrag](#technisch-gedrag)[](#technisch-gedrag)

Instance stitching werkt door dezelfde deterministische GUID op zowel de client als de server te genereren. De GUID is afgeleid van vier invoerwaarden: het type van de [Instance](/docs/nl-nl/reference/engine/classes/Instance)  die wordt gemaakt, de identiteit van de bron (zie hieronder), het huidige simulatieframe en een per-script aanroepenteller die bij elk frame wordt gereset.

-

Voor [Instance.new()](/docs/nl-nl/reference/engine/datatypes/Instance#new)  — De bron is het script zelf (twee scripts met dezelfde tekst worden als verschillend beschouwd).

-

Voor [Instance.fromExisting()](/docs/nl-nl/reference/engine/datatypes/Instance#fromExisting)  — De bron is de [Instance](/docs/nl-nl/reference/engine/classes/Instance)  waarop je [Instance.fromExisting()](/docs/nl-nl/reference/engine/datatypes/Instance#fromExisting)  aanroept.

-

Voor [Instance:Clone()](/docs/nl-nl/reference/engine/classes/Instance#Clone)  — Elke gekloonde instantie gebruikt de GUID van de broninstantie als de contextzaad.

Als client en server het eens zijn over de invoerwaarden, produceren ze overeenkomende GUIDs en slaagt de stitching.

### [Implementatie](#implementatie)[](#implementatie)

Om instance stitching te gebruiken, roep je [Instance.new()](/docs/nl-nl/reference/engine/datatypes/Instance#new) , [Instance:Clone()](/docs/nl-nl/reference/engine/classes/Instance#Clone)  of [Instance.fromExisting()](/docs/nl-nl/reference/engine/datatypes/Instance#fromExisting)  aan binnen een [BindToSimulation()](/docs/nl-nl/reference/engine/classes/RunService#BindToSimulation)  callback van een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  dat op zowel de client als  de server wordt vereist. Verder is er niets anders nodig aan jouw kant; het systeem beheert de toewijzing en verzoening van GUIDs automatisch.

Je kunt vrij niet-[simulatie toegang](/docs/nl-nl/projects/server-authority#simulatie-toegang)  eigenschappen zoals [Name](/docs/nl-nl/reference/engine/classes/Instance#Name) , [Size](/docs/nl-nl/reference/engine/classes/BasePart#Size) , of [Parent](/docs/nl-nl/reference/engine/classes/Instance#Parent)  op een instantie instellen voordat deze in de [DataModel](/docs/nl-nl/reference/engine/classes/DataModel)  wordt geplaatst.

Simulatie (ModuleScript) - Maak instantie in een BindToSimulation() Callback

```

local RunService = game:GetService("RunService")

local Simulation = {}

Simulation.Initialize = function()

	RunService:BindToSimulation(function(deltaTime)

		local part = Instance.new("Part")

		part.Name = "PredictedPart"

		part.Size = Vector3.new(2, 2, 2)

		part.Parent = workspace -- Deel is nu in het datamodel; eventuele wijzigingen zonder simulatie toegang zullen een fout veroorzaken na dit

		-- Deel bestaat onmiddellijk op de client en zal worden verzoend met de server

	end)

end

return Simulation

```

[Instance:Clone()](/docs/nl-nl/reference/engine/classes/Instance#Clone)  en [Instance.fromExisting()](/docs/nl-nl/reference/engine/datatypes/Instance#fromExisting)  stitchen correct wanneer de broninstantie naar zowel client als server is gerepliceerd; beide zijden klonen van overeenkomende bron GUIDs en produceren overeenkomende voorspelde GUIDs.

Simulatie (ModuleScript) - Clone instantie in een BindToSimulation() Callback

```

local RunService = game:GetService("RunService")

local Simulation = {}

local sourceTemplate -- een gerepliceerde instantie

Simulation.Initialize = function()

	RunService:BindToSimulation(function(deltaTime)

		local cloned = sourceTemplate:Clone()

		cloned.Parent = workspace

		-- Gekloonde hiërarchie is gestitcht met de autoritatieve kopie van de server

	end)

end

return Simulation

```

Instanties die binnen een simulatiecallback zijn gemaakt, moeten vóór het einde van dat frame in de [DataModel](/docs/nl-nl/reference/engine/classes/DataModel)  hiërarchie worden geplaatst. Bewaar geen referentie naar een speculatieve instantie en plaats deze in een volgend frame.

## [Positie-smoothing](#positie-smoothing)[](#positie-smoothing)

Je kunt visueel de positie van verkeerd voorspelde gesynchroniseerde objecten gladstrijken door een ander object te renderen dan wat wordt gesimuleerd.

1.

Maak het gesimuleerde  object onzichtbaar.

2.

Maak een renderer  object als een massaloze, niet-collideerbare, visuele clone om het gesimuleerde object te volgen.

3.

Bevestig een script aan het renderer-object dat soepel de positie van het onzichtbare, gesimuleerde object volgt. Deze scheiding tussen rendering en simulatie stelt je in staat om de positie van het renderer-object te wijzigen om een visueel soepele ervaring te creëren.

In het volgende voorbeeld [Script](/docs/nl-nl/reference/engine/classes/Script)  volgt het gerenderde object (ouder) soepel het gesimuleerde object. Het gerenderde object is altijd iets "achter" het gesimuleerde object, wat meestal prima is, maar in bepaalde situaties ongewenst kan zijn.

Volg soepel de positie van BasePart met Renderer Part

```

local RunService = game:GetService("RunService")

local TweenService = game:GetService("TweenService")

-- Object om soepel te volgen

local smoothTarget:BasePart = workspace.SimulatedPart

-- Visueel object dat zal worden gladgestreken

local renderer:BasePart = script.Parent

-- Tijd om over te smoothen; kleiner betekent sneller

local smoothTime = 0.07

-- Bewaar gegevens die nodig zijn om de gladde positie te berekenen

local smoothVelocity = Vector3.new()

-- De fysica van het renderer-object uitschakelen

renderer.Massless = true

renderer.Anchored = true

renderer.CanCollide = false

RunService.RenderStepped:Connect(function(deltaTime: number)

	-- Volg soepel het doelobject

	local smoothPosition, smoothVelocity = TweenService:SmoothDamp(

		renderer.Position,

		smoothTarget.Position,

		smoothVelocity,

		smoothTime,

		math.huge,

		deltaTime)

	renderer.Position = smoothPosition

end)

```

Het [Voetbal](https://www.roblox.com/games/110687099504272/Soccer-Server-Authority-Template)  voorbeeldspel gebruikt een variatie van deze techniek om intelligenter de positie-smoothing voor de voetbal in en uit te schakelen. Specifiek, de voetbal smootht alleen zijn positie wanneer de gesimuleerde bal "ver" genoeg van de gerenderde bal is "gejumped". Deze aanpak biedt het beste van twee werelden: de voetbal heeft geen visuele latentie onder normale omstandigheden, en het spel interpolate soepel zijn positie alleen nadat de gesimuleerde bal onverwacht naar een nieuwe locatie is "gejumped", waarschijnlijk als gevolg van een netwerkartifact of serverzijde wijziging.

## [Animatiecode schrijven](#animatiecode-schrijven)[](#animatiecode-schrijven)

Onder serverautoriteit kan de simulatie van de client worden [teruggedraaid en opnieuw gesimuleerd](/docs/nl-nl/projects/server-authority#terugrollen-en-opnieuw-simuleren)  wanneer de server een verkeerde voorspelling corrigeert. Tijdens de terugdraaiing wordt de animatiestatus teruggedraaid, wat betekent dat [AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack)  die je in eerdere frames hebt gecached mogelijk niet meer geldig is.

### [Spiegelen van animatielogica](#spiegelen-van-animatielogica)[](#spiegelen-van-animatielogica)

Net als bij elke kern gameplay-logica, moet de logica voor het besturen van animaties in sync zijn tussen server en client, anders kunnen er verkeerde voorspellingen en jitterig gedrag optreden. Zie [simulatie sync](/docs/nl-nl/projects/server-authority#simulatie-synchronisatie)  voor een patroon dat functies bindt via [RunService:BindToSimulation()](/docs/nl-nl/reference/engine/classes/RunService#BindToSimulation)  in een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  dat op zowel de client als de server wordt geïnitialiseerd.

### [Vermijd track caching](#vermijd-track-caching)[](#vermijd-track-caching)

Een veelvoorkomend patroon in scripts zonder serverautoriteit is om [AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack)  objecten op laadtijd te cachen en ze eindeloos opnieuw te gebruiken. Dit patroon faalt in een server autoritatieve game wanneer de server een verkeerde voorspelling corrigeert en de client zijn simulatie terugdraait/herhaalt met gecorrigeerde gegevens. Als je script nog steeds een referentie heeft naar een gestopte of vervangen track, zullen aanroepen zoals [AdjustWeight()](/docs/nl-nl/reference/engine/classes/AnimationTrack#AdjustWeight)  of [AdjustSpeed()](/docs/nl-nl/reference/engine/classes/AnimationTrack#AdjustSpeed)  werken op een track die niet langer visueel wordt weergegeven.

Cache Tracks op Client (Onbetrouwbaar)

```

local Players = game:GetService("Players")

local RunService = game:GetService("RunService")

local player = Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

local humanoid = character:WaitForChild("Humanoid")

local animator = humanoid:WaitForChild("Animator")

-- Cache animatietracks

local tracks = {}

tracks["WalkForward"] = animator:LoadAnimation(walkForwardAnim)

RunService:BindToSimulation(function(dt: number)

	tracks["WalkForward"]:AdjustSpeed(1 + math.cos(time()))

end)

```

In plaats van vast te houden aan track-objecten, sla je de animatie-ID's  (of [Animation](/docs/nl-nl/reference/engine/classes/Animation)  instanties) op en vraag je de [Animator](/docs/nl-nl/reference/engine/classes/Animator)  op voor de live track wanneer je ermee wilt interageren. Twee API's zijn beschikbaar voor dit:

-

[Animator:GetTrackByAnimationId()](/docs/nl-nl/reference/engine/classes/Animator#GetTrackByAnimationId)  — Retourneert de momenteel actieve track voor een specifieke animatie-ID, of nil  als er geen actieve animaties met die ID zijn. Gebruik dit wanneer je weet welke specifieke animatie je zoekt.

-

[Animator:GetPlayingAnimationTracks()](/docs/nl-nl/reference/engine/classes/Animator#GetPlayingAnimationTracks)  — Retourneert alle actieve tracks (afspelend, vervagend of gepauzeerd). Gebruik dit wanneer je alles wilt doorlopen dat actief is (bijvoorbeeld om alle animaties te stoppen of tracks op basis van bepaalde criteria te vinden).

CustomAnimate ServerSync ClientSync

[ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  genaamd CustomAnimate  in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) :

CustomAnimate

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local RunService = game:GetService("RunService")

local CustomAnimate = {}

-- Bewaar animatiereferenties (niet geladen tracks)

local animations = {

	WalkForward = ReplicatedStorage.Animations.WalkForward,

}

local function getOrLoadTrack(animator: Animator, animation: Animation): AnimationTrack

	local track = animator:GetTrackByAnimationId(animation.AnimationId)

	if not track then

		track = animator:LoadAnimation(animation)

	end

	return track

end

CustomAnimate.SyncAnimations = function(character)

	local humanoid = character:WaitForChild("Humanoid")

	local animator = humanoid:WaitForChild("Animator")

	RunService:BindToSimulation(function(dt: number)

		local walkTrack = getOrLoadTrack(animator, animations.WalkForward)

		if not walkTrack.isPlaying then

			walkTrack.Looped = true

			walkTrack.Priority = Enum.AnimationPriority.Core

			walkTrack:Play()

		end

		walkTrack:AdjustSpeed(1 + math.cos(time()))

	end)

end

return CustomAnimate

```

## [Geluiden en visuele effecten afspelen](#geluiden-en-visuele-effecten-afspelen)[](#geluiden-en-visuele-effecten-afspelen)

In een voorspelde simulatie is het mogelijk om effecten of geluiden te activeren voor gebeurtenissen waarvan de client voorspelde dat ze zouden plaatsvinden, maar die nooit op de server zijn opgetreden. Het renderingssysteem moet voorbereid zijn om eventuele verkeerd voorspelde effecten "ongedaan" te maken. Bijvoorbeeld, een client kan voorspellen dat een granaat explodeert en een deeltjes effect activeren, maar als een andere speler de granaat heeft ontmanteld, moet de client het deeltjes effect verbergen.

Een goede strategie voor het renderen van een voorspelde simulatie is om een statusmachinepatroon te synchroniseren binnen de simulatielus en wijzigingen in de status in een renderstapfunctie te renderen. Het volgende voorbeeld simuleert een granaat met een statusmachinepatroon:

Eenvoudige Statusmachine voor het Volgen van een Granaat (ModuleScript)

```

local module = {}

module.GrenadeStates = {

	Idle = 0,

	Lit = 1,

	Exploded = 2,

	Defused = 3,

}

module.GrenadeExplodeTime = 3.0

module.Initialize = function(grenade)

	RunService:BindToSimulation(function(deltaTime)

		-- Initialiseer lege granaatstatus

		local grenadeState = grenade:GetAttribute("State")

		if grenadeState == nil then

			grenadeState = module.GrenadeStates.Idle

			grenade:SetAttribute("State", grenadeState)

			grenade:SetAttribute("Timer", 0.0)

		end

		-- Verhoog de granaattimer

		local timer = grenade:GetAttribute("Timer")

		timer = timer + deltaTime

		grenade:SetAttribute("Timer", timer)

		-- Explodeer verlichte granaten

		if grenadeState == module.GrenadeStates.Lit then

			if timer >= module.GrenadeExplodeTime then

				grenadeState = module.GrenadeStates.Exploded

				grenade:SetAttribute("State", grenadeState)

				grenade:SetAttribute("Timer", 0.0)

			end

		end

	end)

end

return module

```

Met de vorige statusmachine op zijn plaats, kun je granaateffecten renderen in een [RunService.RenderStepped](/docs/nl-nl/reference/engine/classes/RunService#RenderStepped)  verbinding binnen een apart script op basis van de gesynchroniseerde granaatstatus:

Render Deeltjes en Geluiden op Basis van de Gesynchroniseerde Granaatstatus

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local RunService = game:GetService("RunService")

local Simulation = require(ReplicatedStorage.Simulation)

local grenade = script.Parent

local previousGrenadeState = nil

-- Hooglicht instantie om granaatstatus aan te geven

local highlight = Instance.new("Highlight")

highlight.Parent = grenade

highlight.FillTransparency = 1

highlight.OutlineTransparency = 1

highlight.DepthMode = Enum.HighlightDepthMode.Occluded

RunService.RenderStepped:Connect(function(deltaTime: number)

	local grenadeState = grenade:GetAttribute("State")

	local grenadeTimer = grenade:GetAttribute("Timer")

	-- Emit de verlichte deeltjes als de granaat verlicht is

	grenade.LitEmitter.Enabled = grenadeState == Simulation.GrenadeStates.Lit

	-- Speel de explosie-emitter af als de granaat net is geëxplodeerd

	if previousGrenadeState ~= grenadeState then

		if grenadeState == Simulation.GrenadeStates.Exploded and grenadeTimer < 0.2 then

			grenade.ExplosionEmitter:Emit(100)

			grenade.ExplosionSound:Play()

		end

		previousGrenadeState = grenadeState

	end

	-- Verander de kleur van de highlight van de granaat op basis van de status en tijd

	if grenadeState == Simulation.GrenadeStates.Lit then

		highlight.FillColor = Color3.fromRGB(255, 0, 0)

		highlight.FillTransparency = 1 - (grenadeTimer / Simulation.GrenadeExplodeTime)

	elseif grenadeState == Simulation.GrenadeStates.Idle then

		highlight.FillTransparency = 1

	elseif grenadeState == Simulation.GrenadeStates.Exploded then

		highlight.FillTransparency = 1

	elseif grenadeState == Simulation.GrenadeStates.Defused then

		highlight.FillColor = Color3.fromRGB(0, 255, 125)

		highlight.FillTransparency = 0.5

	end

end)

```

## [Ontwerpen rond netwerklatentie](#ontwerpen-rond-netwerklatentie)[](#ontwerpen-rond-netwerklatentie)

Bepaalde gameplaymechanica lenen zich beter voor netwerkmultiplayer dan andere mechanica. Spelers zullen altijd enige vertraging hebben tussen het moment dat een andere speler een actie uitvoert en wanneer ze de invoer van die speler ontvangen. De beste manier om een super soepele multiplayergame te creëren, is door je game te ontwerpen met deze beperkingen in gedachten.

Bijvoorbeeld, een game met langzamere versnelling op spelersbeweging zal soepeler lijken dan een met hogere versnelling, omdat het verschil in positie veroorzaakt door de netwerklatentie van spelersinvoer minder zal zijn dan in een game met hogere versnelling.

Als een ander voorbeeld, een gameplaymechanica waarbij spelers onmiddellijk  een grote explosie kunnen activeren door een invoer in te drukken, zal meer netwerkartifacten hebben dan als de explosie wordt vertraagd na de invoer, alsof er een lont wordt aangestoken. Dit plaatst de her-simulatie op het lont-effect in plaats van op het explosie-effect, wat een minder merkbare netwerkartifact is.

## [Voorspellen van andere spelersinvoer](#voorspellen-van-andere-spelersinvoer)[](#voorspellen-van-andere-spelersinvoer)

Standaard stuurt Roblox de invoer van elke client niet door naar elke andere client. Of dit geschikt is voor jouw game hangt af van het ontwerp ervan:

-

Voor basis humanoïde beweging betekent het standaardgedrag dat de bewegingen van andere spelerpersonages niet worden geëxtrapoleerd vanuit de autoritatieve serverstatus en, als gevolg daarvan, zullen andere spelerpersonages niet verkeerd voorspellen maar iets in het verleden worden weergegeven.

-

In een racegame betekent het standaardgedrag daarentegen dat clients niet weten of andere spelers het gaspedaal of andere invoer toepassen, zodat andere auto's achter de lokale speler kunnen verschijnen, zelfs als ze daadwerkelijk vooraan zijn. Om dit te verlichten, kun je spelersinvoer opslaan in [attributen](/docs/nl-nl/studio/properties#instantie-attributen)  op de server en op die gesynchroniseerde attributen clientzijde werken met behulp van [RunService:BindToSimulation()](/docs/nl-nl/reference/engine/classes/RunService#BindToSimulation)  zoals gedemonstreerd in het volgende codevoorbeeld en de [Racing](https://www.roblox.com/games/134686834388911/Racing-Server-Authority-Template)  template. Deze aanpak stelt je in staat om attributen als invoer voor je simulatie te gebruiken om volledig gerepliceerde spelersinvoer te hebben.

Opslaan van Spelersinvoer in Attributen (ModuleScript)

```

local Players = game:GetService("Players")

local RunService = game:GetService("RunService")

local module = {}

module.storePlayerInput = function(player:Player, humanoidRootPart:BasePart)

	local inputContext:InputContext = player.PlayerGui.InputContext

	local throttle = inputContext.DefuseAction:GetState()

	humanoidRootPart:SetAttribute("Throttle", throttle)

	-- Schrijf andere invoer in attributen...

end

module.Initialize = function()

	RunService:BindToSimulation(function(deltaTime)

		if RunService:IsServer() then

			-- Stuur invoer van server naar alle clients

			for _, player in Players:GetPlayers() do

				local humanoidRootPart:BasePart = player.Character.HumanoidRootPart

				local inputContext:InputContext = player.PlayerGui.InputContext

				module.storePlayerInput(player, humanoidRootPart)

			end

		else

			-- Schrijf lokale spelersinvoer als attributen

			local player = Players.LocalPlayer

			local humanoidRootPart:BasePart = player.Character.HumanoidRootPart

			local inputContext:InputContext = player.PlayerGui.InputContext

			module.storePlayerInput(player, humanoidRootPart)

		end

		-- Gebruik de attributen als invoer voor het spel

		for _, player in Players:GetPlayers() do

			local humanoidRootPart:BasePart = player.Character.HumanoidRootPart

			local throttle = humanoidRootPart:GetAttribute("Throttle")

			if throttle then

				-- Pas het gaspedaal toe op het voertuig van de speler

			end

		end

	end)

end)

return module

```

## [Debuggen](#debuggen)[](#debuggen)

Er zijn enkele nieuwe tools en technieken die je kunt gebruiken om een server‑authoritative game te debuggen.

### [Server autoriteit visualizer](#server-autoriteit-visualizer)[](#server-autoriteit-visualizer)

Door Ctrl Shift F6  (Windows) of ⌘ Shift F6  (Mac) in te drukken, opent je de server autoriteit visualizer  van Studio, die verschillende belangrijke informatie toont:

| Details | | Beschrijving |
| --- | --- |
| Instance voorspelling succespercentage | | Het percentage correct voorspelde instanties over de laatste 8 seconden. |
| Invoer acceptatiepercentage | | Het percentage van alle spelersinvoeren die op tijd op de server zijn aangekomen. Te late invoeren verlagen dit aantal. |
| Client-server stapdelta | | Het aantal frames tussen de client en de server, inclusief de join-tijd van de client. De stabiliteit van dit nummer vertegenwoordigt de stabiliteit van je verbinding met de server. |
| RCC hartslag FPS | | De framerate van de simulatie op de server. Als dit nummer onder de 59 daalt, kan de server niet bijhouden met de simulatie en zal de kwaliteit van het spel afnemen. |
| Voorspelde instantie-aantal | | Het aantal instanties dat je client aan het [voorspellen](/docs/nl-nl/projects/server-authority#clientvoorspelling)  is. |
| Invoer drop reden tellingen | |

Het aantal keren dat de server een invoer om elke reden heeft laten vallen:

-

[x] te oud  — De invoeren arriveerden te laat, wat betekent dat je netwerk verslechterde of de client niet kon bijhouden met de simulatie.

-

[x] uit volgorde  — Er deed zich een netwerkfout voor die ervoor zorgde dat je invoeren werden herschikt en weggegooid.

-

[x] buffer vol  — De server kon je invoer niet bufferen. Ofwel verbeterde je netwerk plotseling of de server kon niet bijhouden met de simulatie.

 |

### [Simulatie radius](#simulatie-radius)[](#simulatie-radius)

Wanneer je vertrouwt op automatische voorspelling ([Enum.PredictionMode.Automatic](/docs/nl-nl/reference/engine/enums/PredictionMode#Automatic) ), kun je de voorspellingradius rond je spelerpersonage visualiseren door Zijn Regio's Ingeschakeld  in de instellingen van Studio in te schakelen (Alt S  op Windows; ⌥ S  op Mac). De groene cilinder geeft het bereik rond je personage aan waarin instanties worden voorspeld, en de straal groeit en krimpt op basis van de prestatiekenmerken van het apparaat.

 ![Simulatie radius rond spelerpersonage met server autoriteit actief](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Server-Authority-Simulation-Radius.jpg)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
