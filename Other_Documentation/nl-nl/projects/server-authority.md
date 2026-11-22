<!-- Source: https://create.roblox.com/docs/nl-nl/projects/server-authority -->

Server autoriteitsmodel | Documentatie - Roblox Creator Hub

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

# Server autoriteitsmodel

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In een server autoriteitsmodel  is de server de enige bron van waarheid  voor de gehele spelstatus, en clients worden alleen vertrouwd om hun eigen invoer te rapporteren. Deze architectuur is de kern van de netcode voor een eerlijke, competitieve game omdat het hele klassen van valsspelen zoals flyhacks of speedhacks voorkomt door nooit een client te vertrouwen om zijn eigen positie of status te rapporteren.

## [Voordelen](#voordelen)[](#voordelen)

In een naïef server-bezit systeem zouden clients eenvoudig hun invoer naar de server sturen en de resultaten van het spel weergeven die door de server zijn teruggestuurd. Hoewel technisch correct, zou een dergelijk systeem aanzienlijke invoerlatenz  ondervinden omdat elke spelersactie naar de server moet reizen, verwerkt moet worden en het resultaat naar de client moet worden teruggestuurd voordat het kan worden weergegeven. Voor de meeste games, vooral die met een hoge snelheid, zou die rondreisvertraging ervoor zorgen dat de gameplay traag, onresponsief en onspeelbaar aanvoelt.

In Roblox's server autoriteits  model wordt de latentie gecompenseerd door clients onmiddellijk de effecten van hun invoer te [voorspellen](#client-voorspelling)  naast het verzenden ervan naar de server. Bijvoorbeeld, wanneer een speler een toets indrukt, wacht de client niet op een reactie van de server; in plaats daarvan voorspelt  het een paar frames vooruit van de laatst bekende serverstatus. Dit stelt de client in staat om het resultaat van de invoeractie onmiddellijk weer te geven, waardoor netwerklatentie effectief wordt verborgen en het spel responsief aanvoelt.

Soms zal de client zijn voorspelling verkeerd hebben ([misprediction](#client-misprediction) ) en, vanwege netwerklatentie, zal de client niet weten dat het een fout heeft gemaakt voor een paar frames. Bijvoorbeeld:

Je client voorspelt dat je vooruit bent gegaan, maar op de server heeft een andere speler een stun-vaardigheid gebruikt die je tegenhield. De client en server hebben nu verschillende staten.

Wanneer een misvoorspelling wordt gedetecteerd, moet de client zijn voorspelling corrigeren op basis van de autoritatieve status  van de server. Als de autoritatieve status verschilt van de voorspelde status van de client, moet de client [terugrollen en opnieuw simuleren](#terugrollen-en-opnieuw-simuleren)  zijn voorspelde frames. Dit systeem van client-side voorspelling, terugrollen en opnieuw simuleren staat bekend als "latentiecompensatie" en helpt om server-autoritatieve multiplayer games soepel en responsief te laten aanvoelen.

Mispredictions zijn een normaal en verwacht  onderdeel van de server autoriteitsarchitectuur omdat clients inherent niet de invoer van andere spelers kunnen voorspellen, dus acties van andere spelers zullen altijd enige mate van misvoorspelling triggeren. Wanneer correct afgesteld, zijn de resulterende correcties klein en zouden ze onopgemerkt moeten blijven door spelers. Lees verder over [geavanceerde technieken](/docs/nl-nl/projects/server-authority/techniques)  om netwerkartefacten te verzachten en te maskeren.

## [Setup](#setup)[](#setup)

Het server autoriteitsmodel vereist bepaalde andere engine-technologieën om correct te functioneren. Bevestig de volgende eigenschapsinstellingen op het [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  object in de [Explorer](/docs/nl-nl/studio/explorer) :

1.

[Workspace.AuthorityMode](/docs/nl-nl/reference/engine/classes/Workspace#AuthorityMode)  moet [Server](/docs/nl-nl/reference/engine/enums/AuthorityMode#Server)  zijn (het instellen hiervan stelt automatisch de volgende vijf in).

2.

[Workspace.NextGenerationReplication](/docs/nl-nl/reference/engine/classes/Workspace#NextGenerationReplication)  moet ingeschakeld zijn.

3.

[Workspace.PlayerScriptsUseInputActionSystem](/docs/nl-nl/reference/engine/classes/Workspace#PlayerScriptsUseInputActionSystem)  moet ingeschakeld zijn.

4.

[Workspace.SignalBehavior](/docs/nl-nl/reference/engine/classes/Workspace#SignalBehavior)  moet [Deferred](/docs/nl-nl/reference/engine/enums/SignalBehavior#Deferred)  zijn.

5.

[Workspace.UseFixedSimulation](/docs/nl-nl/reference/engine/classes/Workspace#UseFixedSimulation)  moet ingeschakeld zijn.

6.

[Workspace.StreamingEnabled](/docs/nl-nl/reference/engine/classes/Workspace#StreamingEnabled)  moet ingeschakeld zijn.

## [Concepten](#concepten)[](#concepten)

Het server autoriteitssysteem draait op een paar kernconcepten als volgt.

### [Client voorspelling](#client-voorspelling)[](#client-voorspelling)

Door middel van client voorspelling  simuleert de client een paar frames vooruit van de laatst bekende serverstatus om de effecten van spelersinvoer onmiddellijk te voorspellen. Dit verbergt invoerlatenz, maar de voorspelling kan later onjuist blijken te zijn ([client misprediction](#client-misprediction) ) en dus correctie vereisen. De client probeert net ver genoeg vooruit te simuleren van de laatst bekende autoritatieve serverstatus zodat zijn invoer op de server aankomt op het bedoelde frame. Het aantal frames dat de client vooruit zal voorspellen van de bekende serverstatus is gebaseerd op de latentie tussen de client en de server.

### [Client misprediction](#client-misprediction)[](#client-misprediction)

Wanneer de client de autoritatieve status van de server ontvangt, controleert hij die status tegen een historische record van wat hij lokaal voor dat frame heeft voorspeld. Wanneer er een verschil is tussen wat de client [voorspelde](#client-voorspelling)  en wat de server daadwerkelijk deed, is dit een misprediction . Mispredictions kunnen om verschillende redenen optreden, waaronder verschuivingen in netwerklatentie, andere spelers die zich op manieren gedragen die de client niet had voorzien, de game die bepaalde logica exclusief op de server uitvoert, enz.

Als de autoritatieve status verschilt van de voorspelde status van de client, moet de client [terugrollen en opnieuw simuleren](#terugrollen-en-opnieuw-simuleren) .

### [Terugrollen en opnieuw simuleren](#terugrollen-en-opnieuw-simuleren)[](#terugrollen-en-opnieuw-simuleren)

Wanneer een client een [misprediction](#client-misprediction)  detecteert, moet hij terugkeren naar de autoritatieve status van de server en vervolgens opnieuw simuleren om terug te springen naar zijn voorspelde frame. Gebaseerd op de netwerklatentie probeert de client net ver genoeg vooruit te simuleren van de laatst bekende autoritatieve serverstatus zodat zijn invoer op de server aankomt op het bedoelde frame.

In het bovenstaande diagram simuleert de client 2 frames vooruit van de server. Het stuurt zijn invoer voor frame 3 die op het bedoelde frame (3) op de server aankomt. De server stuurt de autoritatieve status voor frame 3 en de client ontvangt deze op frame 7. De client ontdekt dat hij frame 3 verkeerd heeft voorspeld, dus hij reset naar het frame 3 van de server en simuleert opnieuw frames 4, 5 en 6 voordat hij frame 7 simuleert. Spelers kunnen een merkbaar netwerkartefact zien, zoals een plotselinge beweging.

Samenvattend, de client :

1.

Ontvangt de autoritatieve status  van de server en vergelijkt deze met zijn eigen voorspelde status .

2.

Als de voorspelling van de client onjuist was:

1.

De client rolt terug naar de laatst bekende autoritatieve status die van de server is ontvangen.

2.

De client simuleert opnieuw van de autoritatieve status naar zijn voorspelde status, waarbij eventuele lokale invoer opnieuw wordt toegepast.

## [Implementatie](#implementatie)[](#implementatie)

### [Netwerkbezit en voorspelling](#netwerkbezit-en-voorspelling)[](#netwerkbezit-en-voorspelling)

In het server autoriteitsmodel kun je de kern gameplay-objecten server-bezit houden zonder de kosten van invoerlatenz die normaal geassocieerd zijn met serverbezit. Dingen zoals auto's, spelerspersonages of andere gameplay-kritische objecten kunnen server-bezit blijven, zelfs wanneer ze met andere spelers interageren.

Standaard zal Roblox automatisch eigenschappen met [simulatie toegang](#simulatie-toegang)  nabij de lokale speler [Character](/docs/nl-nl/reference/engine/classes/Player#Character)  voorspellen, maar als je meer gedetailleerde controle wilt, kun je expliciet de voorspelling van een instantie in- of uitschakelen met [RunService:SetPredictionMode()](/docs/nl-nl/reference/engine/classes/RunService#SetPredictionMode) .

Automatische voorspelling geldt voor hele fysica-assemblages, niet voor individuele instanties. Wanneer de client een onderdeel voorspelt, voorspelt het ook elk onderdeel dat fysiek met het verbonden is via lassen, gewrichten of beperkingen, samen met het bovenliggende [Model](/docs/nl-nl/reference/engine/classes/Model)  van die onderdelen en elke [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  binnen dat model. Bijvoorbeeld:

-

Een zwaardmodel dat aan een voorspeld personage is gelast, wordt onderdeel van de assemblage van het personage, dus het wordt automatisch voorspeld.

-

Een model dat aan het personage is gekoppeld maar niet  fysiek met het verbonden is, is een aparte assemblage. Het wordt alleen voorspeld als het binnen de [simulatie radius](/docs/nl-nl/projects/server-authority/techniques#simulatie-radius)  van de client valt of als je de voorspelling inschakelt met [RunService:SetPredictionMode()](/docs/nl-nl/reference/engine/classes/RunService#SetPredictionMode) .

Om te controleren of een specifieke instantie momenteel wordt voorspeld, roep je [RunService:GetPredictionStatus()](/docs/nl-nl/reference/engine/classes/RunService#GetPredictionStatus)  aan vanuit de client.

### [Simulatie synchronisatie](#simulatie-synchronisatie)[](#simulatie-synchronisatie)

In het server autoriteitsmodel moeten de client en de server beide de kernsimulatie uitvoeren, en de simulatie van de client moet in staat zijn om [terug te rollen en opnieuw te simuleren](#terugrollen-en-opnieuw-simuleren)  wanneer er een [misprediction](#client-misprediction)  optreedt. Om dit mogelijk te maken, schrijf je je kernlogica binnen functies die zijn gebonden via [RunService:BindToSimulation()](/docs/nl-nl/reference/engine/classes/RunService#BindToSimulation)  in een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  dat op zowel de client als de server wordt geïnitialiseerd.

 ![Server autoriteit setup](https://prod.docsiteassets.roblox.com/assets/studio/explorer/ReplicatedStorage-Server-Authority.png)

Tijdens een her-simulatie zal Roblox de functies die aan de simulatie zijn gebonden via [BindToSimulation()](/docs/nl-nl/reference/engine/classes/RunService#BindToSimulation)  opnieuw uitvoeren. Het verwerken van spelersinvoer, interactie met gesynchroniseerde fysica-objecten en het bijwerken van de kernspelstatus moet binnen die gebonden functies plaatsvinden.

Gebruik [time()](/docs/nl-nl/reference/engine/globals/RobloxGlobals#time)  voor elke tijdgebaseerde logica binnen een gebonden simulatiefunctie, zoals het aansteken van een animatiesnelheid of het oscilleren van een waarde in de tijd. Wanneer [Workspace.AuthorityMode](/docs/nl-nl/reference/engine/classes/Workspace#AuthorityMode)  [Enum.AuthorityMode.Server](/docs/nl-nl/reference/engine/enums/AuthorityMode#Server)  is, is time()  gesynchroniseerd tussen de client en de server en gebruikt het een vaste stap simulatie tijd. Tijdens [her-simulatie](#terugrollen-en-opnieuw-simuleren)  spoelt het terug naar het autoritatieve frame en gaat het vooruit terwijl de client frames herhaalt, zodat het elke keer een consistente waarde retourneert wanneer een frame wordt gesimuleerd.

Andere tijdfuncties delen dit gedrag niet. [tick()](/docs/nl-nl/reference/engine/globals/RobloxGlobals#tick)  en [os.time()](/docs/nl-nl/reference/engine/libraries/os#time)  lezen de lokale apparaatklok, terwijl [os.clock()](/docs/nl-nl/reference/engine/libraries/os#clock)  de verstreken tijd meet vanaf een willekeurige lokale basislijn. Ze zijn niet gesynchroniseerd tussen de client en de server en rollen niet terug tijdens her-simulatie, dus vermijd ze voor simulatie-beïnvloedende logica.

Simulatie ServerLoader ClientLoader

[ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  genaamd Simulation  in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) :

Simulatie

```

local RunService = game:GetService("RunService")

local Players = game:GetService("Players")

local Simulation = {}

Simulation.Initialize = function()

	RunService:BindToSimulation(function(deltaTime)

		-- Lees spelersinvoer

		-- Werk de spelstatus bij

	end)

end

return Simulation

```

### [Status synchronisatie met attributen](#status-synchronisatie-met-attributen)[](#status-synchronisatie-met-attributen)

Roblox synchroniseert automatisch alle eigenschappen met [simulatie toegang](#simulatie-toegang)  op voorspelde instanties. Voor aangepaste gegevens zijn [attributen](/docs/nl-nl/studio/properties#instantie-attributen)  de primaire manier om instanties die als voorspeld zijn gemarkeerd te synchroniseren; op dergelijke instanties zal elke mismatch in attribuutwaarden tussen de bron van waarheid van de server en de voorspelling van de client een volledige [terugrol en her-simulatie](#terugrollen-en-opnieuw-simuleren)  triggeren.

Gebruik attributen om spelgegevens op te slaan die je kernsimulatie beïnvloeden, inclusief spelersgezondheid, munitie, inventaris of aangepaste regels (zie [beperkingen](#attribuutlimieten) ).

Schrijf alleen naar attributen op voorspelde  instanties vanuit functies die zijn gebonden via [BindToSimulation()](/docs/nl-nl/reference/engine/classes/RunService#BindToSimulation)  om ervoor te zorgen dat Roblox de relevante spelstatus volledig kan volgen en correct kan her-simuleren.

#### [Attribuutlimieten](#attribuutlimieten)[](#attribuutlimieten)

Om te worden gerepliceerd, moet een attribuut aan alle volgende criteria voldoen:

-

Het is een van de eerste 64 attributen op zijn [Instance](/docs/nl-nl/reference/engine/classes/Instance) .

-

De naam bevat maximaal 50 tekens.

-

Als een attribuut van het type string, bevat de waarde maximaal 50 tekens.

#### [Simulatie toegang](#simulatie-toegang)[](#simulatie-toegang)

Veel eigenschappen en methoden in de engine API-referentie bevatten het label Simulatie Toegang , bijvoorbeeld [BasePart.CFrame](/docs/nl-nl/reference/engine/classes/BasePart#CFrame) . Eigenschappen met dit label zullen worden voorspeld door het server autoriteitssysteem. Bovendien kunnen alleen eigenschappen en methoden met dit label worden benaderd binnen functies die zijn gebonden met [RunService:BindToSimulation()](/docs/nl-nl/reference/engine/classes/RunService#BindToSimulation) .

### [Instanties maken en verwijderen](#instanties-maken-en-verwijderen)[](#instanties-maken-en-verwijderen)

Binnen functies die zijn gebonden via [BindToSimulation()](/docs/nl-nl/reference/engine/classes/RunService#BindToSimulation) , kun je instanties maken met [Instance.new()](/docs/nl-nl/reference/engine/datatypes/Instance#new) , [Instance:Clone()](/docs/nl-nl/reference/engine/classes/Instance#Clone) , of [Instance.fromExisting()](/docs/nl-nl/reference/engine/datatypes/Instance#fromExisting) . De client maakt de instantie onmiddellijk, en Roblox voegt deze samen met de autoritatieve kopie van de server wanneer die kopie arriveert. Voor details, zie [voorspellende instantie creatie](/docs/nl-nl/projects/server-authority/techniques#voorspellende-instantiecreatie-instance-stitching) .

Het verwijderen van instanties werkt anders. [Instance:Destroy()](/docs/nl-nl/reference/engine/classes/Instance#Destroy)  heeft geen [simulatie toegang](#simulatie-toegang) , en je kunt de [Parent](/docs/nl-nl/reference/engine/classes/Instance#Parent)  van een instantie die al in het [DataModel](/docs/nl-nl/reference/engine/classes/DataModel)  is niet wijzigen, dus het aanroepen van een van beide binnen een gebonden functie veroorzaakt een fout. In plaats daarvan, registreer de intentie om een instantie te verwijderen in een [attribuut](#status-synchronisatie-met-attributen)  binnen de simulatie, en verwijder de instantie vervolgens buiten de simulatie, zoals in een [PostSimulation](/docs/nl-nl/reference/engine/classes/RunService#PostSimulation)  verbinding op de server.

Server Script - Verwijder een instantie buiten de simulatie

```

local RunService = game:GetService("RunService")

local character = script.Parent

RunService.PostSimulation:Connect(function()

	-- "SwordEquipped" wordt geschreven door de simulatie wanneer de speler het zwaard niet meer gebruikt

	local sword = character:FindFirstChild("Sword")

	if sword and not character:GetAttribute("SwordEquipped") then

		sword:Destroy()

	end

end)

```

[Tools](/docs/nl-nl/reference/engine/classes/Tool)  worden nog niet volledig ondersteund in het server autoriteitsmodel. [Humanoid:EquipTool()](/docs/nl-nl/reference/engine/classes/Humanoid#EquipTool)  en [Humanoid:UnequipTools()](/docs/nl-nl/reference/engine/classes/Humanoid#UnequipTools)  hebben geen [simulatie toegang](#simulatie-toegang) , dus ze kunnen niet binnen gebonden functies worden aangeroepen. Om een uitrustbaar item zoals een zwaard te bouwen, kloon en las een [Model](/docs/nl-nl/reference/engine/classes/Model)  aan het personage binnen de simulatie en houd bij of het is uitgerust met een attribuut.

### [Invoergebeurtenissen](#invoergebeurtenissen)[](#invoergebeurtenissen)

In een server-autoritatieve game is de primaire manier voor een client om de status van het spel te beïnvloeden via het [Input Action System](/docs/nl-nl/input/input-action-system) . Deze invoer wordt naar de server gestuurd en wordt tijdens de her-simulatie op de client opnieuw afgespeeld. Als gevolg hiervan moeten [InputActions](/docs/nl-nl/reference/engine/classes/InputAction)  worden gebruikt voor alle invoer die de kernsimulatie beïnvloedt  en ze moeten op geldigheid worden gecontroleerd voordat ze worden verwerkt.

Om te herhalen, gebruik geen traditionele gebeurtenissen zoals [UserInputService.InputBegan](/docs/nl-nl/reference/engine/classes/UserInputService#InputBegan)  in de kernsimulatie van een server-autoritatieve game.

Merk op dat [InputContexts](/docs/nl-nl/reference/engine/classes/InputContext)  een afstammeling van een [Player](/docs/nl-nl/reference/engine/classes/Player)  moet zijn, zodat de engine weet wie het eigendom heeft over de [InputContext](/docs/nl-nl/reference/engine/classes/InputContext) . Een benadering is om je [InputContexts](/docs/nl-nl/reference/engine/classes/InputContext)  aan een map onder [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  toe te voegen en een [Script](/docs/nl-nl/reference/engine/classes/Script)  onder [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  te gebruiken om de [InputContexts](/docs/nl-nl/reference/engine/classes/InputContext)  per speler te klonen:

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/IAS-InputSetup.png)

InputSetup

```

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local InputsFolder = ReplicatedStorage:WaitForChild("Inputs")

local function onPlayerAdded(player)

	local clone = InputsFolder:Clone()

	clone.Parent = player

end

Players.PlayerAdded:Connect(onPlayerAdded)

for _, player in Players:GetPlayers() do

	onPlayerAdded(player)

end

```

Met dit patroon kun je [InputActions](/docs/nl-nl/reference/engine/classes/InputAction)  voor alle spelers lezen in [RunService:BindToSimulation()](/docs/nl-nl/reference/engine/classes/RunService#BindToSimulation)  op zowel de client als de server om dezelfde gegevens voor een gegeven frame te ontvangen en de invoer van het vorige frame in een [attribuut](/docs/nl-nl/studio/properties#instantie-attributen)  vast te leggen, bijvoorbeeld om een karakter te laten rennen wanneer een RunAction  invoergebeurtenis wordt geactiveerd.

### [Remote evenementen](#remote-evenementen)[](#remote-evenementen)

[Remote events](/docs/nl-nl/scripting/events/remote)  kunnen nog steeds binnen het server autoriteitsmodel worden gebruikt om discrete communicatie tussen client en server te vergemakkelijken. Bijvoorbeeld, servers kunnen remote events gebruiken om gegevens over spelers die punten scoren of objecten oppakken uit te zenden, en clients kunnen remote events gebruiken als een alternatieve API voor het verzenden van invoer naar de server, zoals voor knopindrukken of het aanraken van objecten in de 3D-wereld.

[RemoteEvents](/docs/nl-nl/reference/engine/classes/RemoteEvent)  zijn mogelijk niet consistent geordend met eigenschaps- en attribuutupdates over het netwerk. Bijvoorbeeld, als je een eigenschap wijzigt voordat je een remote event op een client afvuurt, kan de server de eigenschapswijziging ontvangen na het remote event. Om meer te leren, zie [replicatievolgorde](/docs/nl-nl/scripting/attributes#replicatievolgorde) .

### [Animaties](#animaties)[](#animaties)

Animaties die de gameplay beïnvloeden, zoals karakterbeweging of aanvalanimaties, moeten worden gecontroleerd binnen functies die zijn gebonden via [BindToSimulation()](/docs/nl-nl/reference/engine/classes/RunService#BindToSimulation)  in dezelfde [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  die op zowel de client als de server draait. Kern [Animator](/docs/nl-nl/reference/engine/classes/Animator)  en [AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack)  leden zoals [LoadAnimation()](/docs/nl-nl/reference/engine/classes/Animator#LoadAnimation) , [Play()](/docs/nl-nl/reference/engine/classes/AnimationTrack#Play) , [Stop()](/docs/nl-nl/reference/engine/classes/AnimationTrack#Stop) , [AdjustSpeed()](/docs/nl-nl/reference/engine/classes/AnimationTrack#AdjustSpeed) , en [TimePosition](/docs/nl-nl/reference/engine/classes/AnimationTrack#TimePosition)  hebben [simulatie toegang](#simulatie-toegang) .

De animatiestatus maakt deel uit van de voorspelde simulatie. Wanneer er een [terugrol](#terugrollen-en-opnieuw-simuleren)  optreedt tijdens een animatie, spoelt de client de animatie terug naar de autoritatieve status en speelt deze opnieuw af samen met de rest van de simulatie, zodat client- en serveranimaties gesynchroniseerd blijven. Omdat de client mogelijk animatietracks vervangt tijdens een terugrol, cache geen [AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack)  referenties over frames. Zoek in plaats daarvan elke frame de live track op met [Animator:GetTrackByAnimationId()](/docs/nl-nl/reference/engine/classes/Animator#GetTrackByAnimationId) . Voor een volledig voorbeeld, zie [animatiecode schrijven](/docs/nl-nl/projects/server-authority/techniques#animatiecode-schrijven) .

### [Geluiden en effecten](#geluiden-en-effecten)[](#geluiden-en-effecten)

Client-side effecten zoals geluiden en deeltjes moeten worden geschreven met de wetenschap dat de client simulatie slechts een voorspelling is van de autoritatieve serverstatus. [BindToSimulation()](/docs/nl-nl/reference/engine/classes/RunService#BindToSimulation)  beperkt welke eigenschappen en methoden vanuit gebonden functies kunnen worden aangeroepen om je te helpen alleen naar de gesynchroniseerde simulatiestatus te schrijven. Het weergeven van de resultaten van deze simulatie, het activeren van effecten en geluiden, enz. moet worden gedaan in een aparte functie die is verbonden met [RenderStepped](/docs/nl-nl/reference/engine/classes/RunService#RenderStepped)  die de resultaten van de simulatie leest en de gewenste effecten activeert.

Omdat de client mogelijk een gebeurtenis voorspelt die nooit op de server gebeurt, moet je rendercode in staat zijn om misvoorspelde effecten ongedaan te maken of te verbergen. Verdere richtlijnen over het renderen van een voorspelde simulatie worden behandeld in [geluiden en visuele effecten afspelen](/docs/nl-nl/projects/server-authority/techniques#geluiden-en-visuele-effecten-afspelen) .

## [Voorbeeldprojecten](#voorbeeldprojecten)[](#voorbeeldprojecten)

Naast deze documentatie kunnen de volgende sjablonen je helpen om aan de slag te gaan:

[![](https://prod.docsiteassets.roblox.com/assets/misc/SA-Icon-Racing.jpg)](https://www.roblox.com/games/134686834388911/Racing-Server-Authority-Template) Racen

[![](https://prod.docsiteassets.roblox.com/assets/misc/SA-Icon-Soccer.jpg)](https://www.roblox.com/games/110687099504272/Soccer-Server-Authority-Template) Voetbal

[![](https://prod.docsiteassets.roblox.com/assets/misc/SA-Icon-Laser-Tag.jpg)](https://www.roblox.com/games/90572444221193/Laser-Tag-Server-Authority-Template) Laser Tag

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
