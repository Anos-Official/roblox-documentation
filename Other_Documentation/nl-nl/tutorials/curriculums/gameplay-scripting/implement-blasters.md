<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/gameplay-scripting/implement-blasters -->

Blastergedrag implementeren | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Blastergedrag implementeren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Blastergedrag implementeren  is het proces van het programmeren van een blastmechanisme in first-person shooter games. Terwijl spelers kunnen schieten met een enkele klik of druk op een knop, is het creëren van een bevredigend en nauwkeurig blastgedrag belangrijk omdat het de speelervaring van de spelers verbetert.

Met behulp van het [voorbeeld laser tag-spel](https://www.roblox.com/games/14817965191/Laser-Tag-1A)  als referentie, leert deze sectie van de tutorial je over de scripts achter het implementeren van blastergedrag voor twee verschillende soorten blasters, inclusief richtlijnen over:

-

Detecteren wanneer spelers de blastknop indrukken.

-

Controleren of de speler hun blaster kan gebruiken als ze recentelijk de blastknop hebben ingedrukt.

-

Genereren van blastgegevens die de server vertellen wie de blast heeft geïnitieerd, waar deze vandaan kwam en wat de uiteindelijke bestemming van elke laserstraal was.

-

De server op de hoogte stellen van de blastgegevens zodat deze de juiste acties kan uitvoeren als de blast met een andere speler in botsing komt.

-

De blaster resetten tussen elke blast om de blaster voldoende tijd te geven om af te koelen voordat deze opnieuw kan schieten.

Nadat je deze sectie hebt voltooid, leer je over de scripts die de blaster in staat stellen te detecteren wanneer zijn blasts in botsing komen met andere spelers, en vervolgens het overeenkomstige aantal gezondheidspunten aftrekken op basis van elk type blaster.

## [Detecteer spelersinvoer](#detecteer-spelersinvoer)[](#detecteer-spelersinvoer)

De eerste stap bij het implementeren van blastergedrag is luisteren naar wanneer een speler de blastknop indrukt. Het type invoer dat spelers gebruiken om de blastknop in te drukken, hangt af van welk apparaat ze gebruiken om toegang te krijgen tot het spel. Het voorbeeld laser tag-spel ondersteunt bijvoorbeeld muis- en toetsenbordbediening, gamepads en aanraakbediening. Je kunt elk van deze invoertypes zien in ReplicatedStorage  ⟩ UserInputHandler .

Dit clientscript gebruikt [ContextActionService](/docs/nl-nl/reference/engine/classes/ContextActionService)  om MouseButton1  en ButtonR2  aan de blastactie te binden. Dit betekent dat elke keer dat een speler ofwel de linkermuisknop of de R2-knop van een gamepad indrukt, er een laserstraal uit de blaster wordt geschoten. Merk op dat de HUDGui  een knop voor het schieten op mobiele apparaten bevat, die later in het script wordt verbonden.

UserInputHandler

```

ContextActionService:BindAction("_", onBlasterActivated, false,

  Enum.UserInputType.MouseButton1,

  Enum.KeyCode.ButtonR2

)

```

Een andere belangrijke opmerking is het gebruik van [Enum.UserInputState.Begin](/docs/nl-nl/reference/engine/enums/UserInputState#Begin)  in de definitie van onBlasterActivated() . Veel gebruikersinterface-interacties, zoals het kiezen van een blaster in dit voorbeeld, vinden pas plaats nadat de muisknop omhoog komt ([Enum.UserInputState.End](/docs/nl-nl/reference/engine/enums/UserInputState#End) ), wat gebruikers een laatste kans geeft om de interactie te vermijden. Een blastmechanisme voelt echter niet responsief aan tenzij het plaatsvindt op het moment dat de knop wordt ingedrukt.

Om dit te demonstreren, kun je [Enum.UserInputState.Begin](/docs/nl-nl/reference/engine/enums/UserInputState#Begin)  veranderen in [Enum.UserInputState.End](/docs/nl-nl/reference/engine/enums/UserInputState#End) , en vervolgens playtesten om te zien hoe de responsiviteit van de blast de gameplay van het spel beïnvloedt. Als spelers bijvoorbeeld de knop ingedrukt kunnen houden zonder de blast te activeren, hoe zou dat dan hun ervaring veranderen terwijl ze andere spelers taggen?

UserInputHandler

```

local function onBlasterActivated(_actionName: string,

  inputState: Enum.UserInputState, _inputObject: InputObject)

    if inputState == Enum.UserInputState.End then  -- bijgewerkte regel, zorg ervoor dat je terugverandert

        attemptBlastClient()

    end

end

```

## [Controleer of de speler kan schieten](#controleer-of-de-speler-kan-schieten)[](#controleer-of-de-speler-kan-schieten)

Nadat UserInputHandler  een knopdruk of schermaanraaking detecteert, roept het ReplicatedStorage  ⟩ Blaster  ⟩ attemptBlastClient  aan om te controleren of de speler kan schieten of niet. Zoals de meeste controles in het voorbeeld laser tag-spel, gebeurt dit twee keer: eerst op de client en later op de server. attemptBlastClient  roept vervolgens ReplicatedStorage  ⟩ Blaster  ⟩ canLocalPlayerBlast  aan om een eenvoudige controle van de blasterStateClient  spelerattribuut uit te voeren:

canLocalPlayerBlast

```

local function canLocalPlayerBlast(): boolean

    return localPlayer:GetAttribute(PlayerAttribute.blasterStateClient) == BlasterState.Ready

end

```

Als je ReplicatedStorage  ⟩ Blaster  ⟩ BlasterState  bekijkt, zie je dat het spel drie blastertoestanden heeft: Ready , Blasting  en Disabled . Om het effect van elk van deze toestanden te zien, kun je het spel playtesten, je speler selecteren onder de Players  service, en vervolgens het blasterStateClient  attribuut in het Properties  venster observeren. Merk op hoe het Disabled  weergeeft terwijl je je blaster kiest, Ready  het grootste deel van de tijd, en Blasting  voor minder dan een seconde nadat je de knop indrukt.

Deze lichte pauze voorkomt dat je zo snel kunt schieten als je kunt klikken. Als je bijvoorbeeld de functie verandert zodat deze altijd true retourneert, kun je snel je blaster afvuren zonder enige vertraging, wat onrealistisch is voor laser tag gameplay.

canLocalPlayerBlast

```

local function canLocalPlayerBlast(): boolean

    return true -- bijgewerkte regel, zorg ervoor dat je terugverandert

end

```

## [Genereer blastgegevens](#genereer-blastgegevens)[](#genereer-blastgegevens)

Nadat is bevestigd dat de blaster van de speler in de Ready  staat is, roept attemptBlastClient  ReplicatedStorage  ⟩ attemptBlastClient  ⟩ blastClient  aan. De eerste stap die blastClient  onderneemt, is het instellen van het blasterStateClient  spelerattribuut op Blasting , wat de eerder genoemde snelle vuurgeval voorkomt.

Het veranderen van BlasterState  naar Blasting  speelt ook een geluid in ReplicatedStorage  ⟩ SoundHandler .

De volgende stap is het genereren van de blastgegevens. Als je ReplicatedStorage  ⟩ Blaster  ⟩ BlastData  bekijkt, zie je dat elke blast uit drie stukken informatie bestaat:

-

De speler die de blast initieert.

-

Een DataType.CFrame  die het punt van oorsprong van de blast vertegenwoordigt.

-

Een RayResult  tabel die de uiteindelijke bestemming van elke laserstraal en de getroffen speler bevat, als er een andere speler is geraakt.

Om deze gegevens te genereren, roept blastClient  ReplicatedStorage  ⟩ attemptBlastClient  ⟩ blastClient  ⟩ generateBlastData  aan, die je hieronder kunt bekijken.

generateBlastData

```

local function generateBlastData(): BlastData.Type

    local blasterConfig = getBlasterConfig()

    local rayDirections = getDirectionsForBlast(

        currentCamera.CFrame, blasterConfig)

    local rayResults = castLaserRay(

        localPlayer, currentCamera.CFrame.Position, rayDirections)

    local blastData: BlastData.Type = {

        player = localPlayer,

        originCFrame = currentCamera.CFrame,

        rayResults = rayResults,

    }

    return blastData

end

```

Deze functie begint met het gebruik van getBlasterConfig  om het type blaster van de speler op te halen. Het voorbeeld biedt twee soorten blasters: een die meerdere stralen produceert met een brede, horizontale spreiding, en een andere die een enkele straal produceert. Je kunt hun configuraties vinden in ReplicatedStorage  ⟩ Instances  ⟩ LaserBlastersFolder .

De functie gebruikt vervolgens currentCamera.CFrame  als het punt van oorsprong voor de blast, en geeft dit door aan getDirectionsForBlast . Op dit punt gaat de code niet meer over de blaster, maar over de laserstraal, waar je meer over zult leren in de [detect hits](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/detect-hits)  sectie van de tutorial. Ten slotte, nadat de rayResults  tabel is aangemaakt, heeft generateBlastData  alle informatie die het nodig heeft om de blastgegevens aan blastClient  terug te geven.

## [Notify de server](#notify-de-server)[](#notify-de-server)

Zodra blastClient  complete gegevens voor de blast heeft, vuurt het twee evenementen af:

blastClient

```

local laserBlastedBindableEvent = ReplicatedStorage.Instances.LaserBlastedBindableEvent

local laserBlastedEvent = ReplicatedStorage.Instances.LaserBlastedEvent

laserBlastedBindableEvent:Fire(blastData)

laserBlastedEvent:FireServer(blastData)

```

De [BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent)  stelt andere clientscripts op de hoogte van de blast. Bijvoorbeeld, ReplicatedStorage  ⟩ FirstPersonBlasterVisuals  gebruikt dit evenement om te weten wanneer visuele effecten moeten worden weergegeven, zoals de blastanimatie en de cooldownbalk. Evenzo stelt de [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  serverscripts op de hoogte van de blast, die begint met het verwerken van de blast in ServerScriptService  ⟩ LaserBlastHandler .

LaserBlastHandler

```

local function onLaserBlastedEvent(playerBlasted: Player, blastData: BlastData.Type)

    local validatedBlastData = getValidatedBlastData(playerBlasted, blastData)

    if not validatedBlastData then

        return

    end

    if not canPlayerBlast(playerBlasted) then

        return

    end

    blastServer(playerBlasted)

    processTaggedPlayers(playerBlasted, blastData)

    for _, replicateToPlayer in Players:GetPlayers() do

        if playerBlasted == replicateToPlayer then

            continue

        end

        replicateBlastEvent:FireClient(replicateToPlayer, playerBlasted, blastData)

    end

end

```

Om te helpen valsspelen te voorkomen, moet de server alle gegevens die elke client verzendt verifiëren. Deze controles omvatten:

1.

Is BlastData  een tabel? Bevat het een Class.CFrame  en een andere tabel genaamd rayResults ?

2.

Heeft de speler een blaster uitgerust?

3.

Heeft de speler een karakter en een locatie binnen de wereld?

4.

Heeft de speler, na het verzenden van de blastgegevens, een buitensporige afstand afgelegd van waar ze de laserstraal hebben geschoten?

Deze laatste controle omvat een beoordelingskwestie, en afhankelijk van de serverlatentie en de snelheid van de spelerbeweging, kun je besluiten dat verschillende waarden buitensporig zijn voor je eigen spel. Om te demonstreren hoe je deze beoordelingskwestie kunt maken, kun je een printstatement toevoegen in getValidatedBlastData  en het spel playtesten.

getValidatedBlastData

```

local distanceFromCharacterToOrigin = blastData.originCFrame.Position - rootPartCFrame.Position

print(distanceFromCharacterToOrigin.Magnitude) -- bijgewerkte regel, zorg ervoor dat je verwijdert

if distanceFromCharacterToOrigin.Magnitude > ToleranceValues.DISTANCE_SANITY_CHECK_TOLERANCE_STUDS then

    warn(`Speler {player.Name} is niet geslaagd voor een oorsprongscontrole tijdens het schieten`)

    return

end

```

Terwijl je beweegt en schiet, let op de output. Het kan er ongeveer zo uitzien:

```

1.9019629955291748

3.1549558639526367

2.5742883682250977

4.8044586181640625

2.6434271335601807

```

Als je de snelheid van de beweging voor spelers in ReplicatedStorage  ⟩ PlayerStateHandler  ⟩ togglePlayerMovement  verhoogt, en vervolgens opnieuw playtest, zul je waarschijnlijk veel mislukte controles tegenkomen vanwege buitensporige beweging tussen blasts.

togglePlayerMovement

```

local ENABLED_WALK_SPEED = 60 -- bijgewerkte regel, zorg ervoor dat je terugverandert

```

Om deze reden, als je besluit de snelheid van de beweging te verhogen, overweeg dan om DISTANCE_SANITY_CHECK_TOLERANCE_STUDS  in ServerStorage  ⟩ ToleranceValues  aan te passen. Voor meer informatie over hoe je dit probleem kunt aanpakken, zie [Bewegingsvalidatie](/docs/nl-nl/scripting/security/security-tactics#movement-validation) .

De server doet vervolgens het volgende:

-

Valideert rayResults .

-

Controleert of de speler kan schieten.

-

Reset de blasterstatus.

-

Vermindert de gezondheid voor alle getagde spelers.

-

Repliceert de blast naar alle andere spelers zodat zij de derde persoon visueel kunnen zien.

Voor meer informatie over deze serveroperaties, zie de [detect hits](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/detect-hits)  sectie van de tutorial.

## [Reset de blaster](#reset-de-blaster)[](#reset-de-blaster)

In het voorbeeld laser tag-spel gebruiken blasters een hitte-mechanisme. In plaats van opnieuw te laden na een vastgesteld aantal blasts, hebben ze tijd nodig om "af te koelen" tussen elke blast. Dezezelfde cooldownvertraging vindt plaats op zowel de client (blastClient ) als de server (blastServer ), waarbij de server als de bron van waarheid fungeert.

blastServer

```

local blasterConfig = getBlasterConfig(player)

local secondsBetweenBlasts = blasterConfig:GetAttribute("secondsBetweenBlasts")

task.delay(secondsBetweenBlasts, function()

    local currentState = player:GetAttribute(PlayerAttribute.blasterStateServer)

    if currentState == BlasterState.Blasting then

        player:SetAttribute(PlayerAttribute.blasterStateServer, BlasterState.Ready)

    end

end)

```

Het secondsBetweenBlasts  attribuut maakt deel uit van de blasterconfiguratie in ReplicatedStorage  ⟩ Instances  ⟩ LaserBlastersFolder . Nadat de vertraging van secondsBetweenBlasts  is verstreken, kan de speler opnieuw schieten, en herhaalt het hele proces zich. Om de speler te helpen begrijpen wanneer ze weer kunnen schieten, bevat het spel een cooldownbalk.

Op dit punt kunnen spelers spawnen en respawnen, richten en schieten, maar het spel moet nog steeds de resultaten van elke blast bepalen. In de volgende sectie van de tutorial leer je hoe je de mogelijkheid programmeert voor de blaster om te detecteren wanneer de blast een andere speler raakt, en vervolgens het juiste aantal gezondheidspunten van de speler af te trekken op basis van de blasterinstellingen.

[Volgende](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/detect-hits)[Vorige](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/add-rounds)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
