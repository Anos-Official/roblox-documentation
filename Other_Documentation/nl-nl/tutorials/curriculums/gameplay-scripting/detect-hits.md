<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/gameplay-scripting/detect-hits -->

Detecteer hits | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Detecteer hits

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Hits detecteren  is het proces van het identificeren wanneer schoten botsen met spelers, en vervolgens hun gezondheid dienovereenkomstig verminderen. Op een hoog niveau kun je dit werk beschouwen als:

1.

Een fysiek gesimuleerde controle of een projectiel het doel heeft geraakt.

2.

Een onmiddellijke controle of de blaster op het doel was gericht.

Het type hitdetectie dat je gebruikt, hangt af van de gameplay-eisen van je spel. Bijvoorbeeld, een fysiek gesimuleerde controle is geschikt voor een trefbalspel waar ballen met een bepaalde snelheid uit de hand moeten komen, dalen terwijl ze door de lucht bewegen, of van richting veranderen door weersomstandigheden. Een onmiddellijke controle is echter beter geschikt voor een laser tag-spel waar stralen een bijna oneindige snelheid moeten hebben en omgevingsfactoren zoals zwaartekracht en windsnelheid negeren.

Met behulp van het [voorbeeld laser tag-spel](https://www.roblox.com/games/14817965191/Laser-Tag-1A)  als referentie, leert deze sectie van de tutorial je over de scripts achter hitdetectie in de 3D-ruimte, inclusief richtlijnen over:

-

Het verkrijgen van de blastrichting op basis van de huidige camerawaarden en het type blaster van de speler.

-

Het casten van stralen in een rechte lijn vanaf de blaster terwijl deze schiet.

-

Het valideren van de blast om misbruik van blastergegevens te voorkomen.

-

Het verminderen van de gezondheid van de speler volgens de blastbeschadiging van elk type blaster en hoeveel stralen de speler hebben geraakt.

Nadat je deze sectie hebt voltooid, kun je aanvullende ontwikkelingsthema's verkennen om je gameplay te verbeteren, zoals audio, verlichting en speciale effecten.

## [Verkrijg blastrichting](#verkrijg-blastrichting)[](#verkrijg-blastrichting)

Nadat een speler hun blaster heeft afgevuurd, roept ReplicatedStorage  ⟩ Blaster  ⟩ attemptBlastClient  ⟩ blastClient  ⟩ generateBlastData  twee functies aan om het hitdetectieproces te starten: rayDirections()  en rayResults() .

generateBlastData

```

local rayDirections = getDirectionsForBlast(currentCamera.CFrame, blasterConfig)

local rayResults = castLaserRay(localPlayer, currentCamera.CFrame.Position, rayDirections)

```

De invoer voor rayDirections  is eenvoudig: de huidige camerastand en rotatiewaarden, en het type blaster van de speler. Als het voorbeeld laser tag-spel alleen blasters gaf die een enkele laserstraal produceren, zou ReplicatedStorage  ⟩ LaserRay  ⟩ getDirectionsForBlast  overbodig zijn omdat je currentCamera.CFrame.LookVector  zou kunnen gebruiken om de richting voor de blast te berekenen.

Echter, omdat het voorbeeld een extra blastertype biedt dat verschillende laserstralen met een brede, horizontale spreiding produceert, moet getDirectionsForBlast  de richting voor elke laserstraal van de spreiding berekenen volgens hun hoeken binnen de blasterconfiguratie:

getDirectionsForBlast

```

if numLasers == 1 then

	-- Voor enkele lasers, richten ze recht

	table.insert(directions, originCFrame.LookVector)

elseif numLasers > 1 then

	-- Voor meerdere lasers, spreid ze gelijkmatig horizontaal

	-- over een interval laserSpreadDegrees rond het midden

	local leftAngleBound = laserSpreadDegrees / 2

	local rightAngleBound = -leftAngleBound

	local degreeInterval = laserSpreadDegrees / (numLasers - 1)

	for angle = rightAngleBound, leftAngleBound, degreeInterval do

		local direction = (originCFrame * CFrame.Angles(0, math.rad(angle), 0)).LookVector

		table.insert(directions, direction)

	end

end

```

Om dit concept verder te demonstreren, als je een derde blastertype met een brede, verticale  spreiding zou opnemen, zou je een nieuwe blasterattribuut kunnen creëren, zoals spreadDirection , en vervolgens de [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) -berekening aanpassen om een andere as te gebruiken. Let bijvoorbeeld op het verschil in de direction -berekeningen in het volgende script hieronder voor dit hypothetische derde blastertype.

```

if numLasers == 1 then

	table.insert(directions, originCFrame.LookVector)

elseif numLasers > 1 then

	local leftAngleBound = laserSpreadDegrees / 2

	local rightAngleBound = -leftAngleBound

	local degreeInterval = laserSpreadDegrees / (numLasers - 1)

	for angle = rightAngleBound, leftAngleBound, degreeInterval do

		local direction

		if spreadDirection == "vertical" then

			direction = (originCFrame * CFrame.Angles(math.rad(angle), 0, 0)).LookVector

		else

			direction = (originCFrame * CFrame.Angles(0, math.rad(angle), 0)).LookVector

		end

		table.insert(directions, direction)

	end

end

return directions

```

Uiteindelijk retourneert de functie rayDirections()  een tabel van [Vectors](/docs/nl-nl/reference/engine/datatypes/Vector3)  die de richting van elke laserstraal vertegenwoordigen. Als het nuttig is, kun je wat logging toevoegen om een idee te krijgen van hoe deze gegevens eruitzien.

generateBlastData

```

local rayDirections = getDirectionsForBlast(currentCamera.CFrame, blasterConfig)

for _, direction in rayDirections do  -- nieuwe regel

    print(direction)                  -- nieuwe regel

end                                   -- nieuwe regel

local rayResults = castLaserRay(localPlayer, currentCamera.CFrame.Position, rayDirections)

```

## [Stralen casten](#stralen-casten)[](#stralen-casten)

castLaserRay() , de tweede functie in ReplicatedStorage  ⟩ Blaster  ⟩ attemptBlastClient  ⟩ blastClient  ⟩ generateBlastData , voert de complexere bewerkingen binnen het script uit. Het begint met het specificeren van parameters zodat het [Workspace:Raycast()](/docs/nl-nl/reference/engine/classes/Workspace#Raycast) -aanroepen kan doen voor raycastingdoeleinden. Raycasting is het proces van het uitzenden van een onzichtbare straal vanuit een [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) -punt in een specifieke richting met een gedefinieerde lengte, en vervolgens het pad te controleren om te zien waar het intersecteert met andere objecten.

Deze informatie is bijzonder nuttig voor first-person shooter-spellen omdat het je in staat stelt te zien wanneer en waar schoten intersecteren met spelers of de omgeving. Bijvoorbeeld, de volgende afbeelding toont twee stralen die parallel aan elkaar worden gecast. Volgens hun oorsprong en richting mist Ray A de muur en gaat verder totdat het zijn maximale afstand bereikt, terwijl Ray B met de muur botst. Voor meer informatie over dit proces, zie [Raycasting](/docs/nl-nl/workspace/raycasting) .

![Een diagram waar Ray A door de muur gaat, en Ray B met de muur botst.](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Detecting-Hits/Two-Rays.png)

De parameters van castLaserRay()  specificeren dat Raycast() -aanroepen elke deel in de werkruimte behalve  het karakter dat heeft geschoten, moeten overwegen. Het script cast vervolgens een straal voor elke richting in de directions -tabel. Als een straal iets raakt, genereert het een [RaycastResult](/docs/nl-nl/reference/engine/datatypes/RaycastResult) , dat vijf eigenschappen heeft:

-

[Distance](/docs/nl-nl/reference/engine/datatypes/RaycastResult#Distance)  – De afstand tussen de straal oorsprong en het snijpunt.

-

[Instance](/docs/nl-nl/reference/engine/datatypes/RaycastResult#Instance)  – Het [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  of [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  cel dat de straal snijdt.

-

[Material](/docs/nl-nl/reference/engine/datatypes/RaycastResult#Material)  – Het [Enum.Material](/docs/nl-nl/reference/engine/enums/Material)  op het snijpunt.

-

[Position](/docs/nl-nl/reference/engine/datatypes/RaycastResult#Position)  – De [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  positie van de intersectie tussen de straal en de instantie.

-

[Normal](/docs/nl-nl/reference/engine/datatypes/RaycastResult#Normal)  – De [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  van de normale vector van het vlak waarmee de straal intersecteert.

Standaard respecteert Raycast()  de [BasePart.CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide) -eigenschap niet . Als sommige delen in je spel strikt decoratief zijn, overweeg dan hoe je wilt dat ze zich gedragen en zie [RaycastParams.RespectCanCollide](/docs/nl-nl/reference/engine/datatypes/RaycastParams#RespectCanCollide) .

De waarde van [Instance](/docs/nl-nl/reference/engine/datatypes/RaycastResult#Instance)  is de meest kritische van deze eigenschappen voor de gameplay van het voorbeeld laser tag-spel omdat het communiceert wanneer stralen botsen met andere spelers. Om deze informatie te verkrijgen, gebruikt het spel de ReplicatedStorage  ⟩ LaserRay  ⟩ castLaserRay  ⟩ getPlayerFromDescendant  hulpfunctie. Als het nil  retourneert, is de instantie geen onderdeel van een speler, wat betekent dat de straal een levenloos object binnen de omgeving heeft geraakt.

castLaserRay()  gebruikt vervolgens [Position](/docs/nl-nl/reference/engine/datatypes/RaycastResult#Position)  en [Normal](/docs/nl-nl/reference/engine/datatypes/RaycastResult#Normal)  om een nieuwe [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  te creëren die het eindpunt van de straal wordt genoemd. Elke straal heeft een bestemming, en het is ofwel waar de straal in de 3D-ruimte heeft geraakt, of het punt aan het einde van zijn maximale afstand. Afhankelijk van hoe goed je spelers richten, zijn veel of de meeste taggedPlayer -waarden nil .

castLaserRay

```

if result then

	-- De blast raakte iets, controleer of het een speler was.

    destination = CFrame.lookAt(result.Position, result.Position + result.Normal)

    taggedPlayer = getPlayerFromDescendant(result.Instance)

else

	-- De blast raakte niets, dus de bestemming is

	-- het punt op zijn maximale afstand.

	local distantPosition = origin + rayDirection * MAX_DISTANCE

	destination = CFrame.lookAt(distantPosition, distantPosition - rayDirection)

	taggedPlayer = nil

end

```

[Distance](/docs/nl-nl/reference/engine/datatypes/RaycastResult#Distance)  is niet bijzonder interessant in de scripts van deze sectie, maar je zou het op unieke manieren kunnen gebruiken als je wilt dat blasters meer schade toebrengen op korte afstand. Evenzo houden de scripts van deze sectie geen rekening met [Material](/docs/nl-nl/reference/engine/datatypes/RaycastResult#Material) , maar je zou materiaaltypes kunnen gebruiken om onderscheid te maken tussen een gepantserde lichaamsdeel en een set zwakke punten tijdens schadeberekeningen.

## [Valideer de blast](#valideer-de-blast)[](#valideer-de-blast)

Om te voorkomen dat er wordt vals gespeeld, legt het vorige hoofdstuk [Implementing Blasters](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/implement-blasters)  uit hoe blastClient  de server op de hoogte stelt van de blast met behulp van een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent) , zodat deze alle gegevens kan verifiëren die elke client verzendt, zoals of ze daadwerkelijk een andere speler met hun blaster hebben getagd. Dit validatieproces van de straal vindt plaats in ServerScriptService  ⟩ LaserBlastHandler  ⟩ getValidatedBlastData  ⟩ getValidatedRayResults , en elke controle komt overeen met een geneste module-script:

1.

Eerst roept getValidatedRayResults  validateRayResult  aan om te controleren of elke invoer in de rayResults -tabel van de client een [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  en een Player  (of nil) is.

2.

Vervolgens roept het isRayAngleFromOriginValid  aan om de verwachte hoeken van de laser spreiding te vergelijken met die van de client. Deze code laat in het bijzonder het voordeel zien van het gebruik van ReplicatedStorage  omdat de server getDirectionsForBlast  zelf kan aanroepen, de return kan opslaan als de "verwachte" gegevens, en deze kan vergelijken met de gegevens van de client.

Net als bij de validatie van blasters uit het vorige hoofdstuk, vertrouwt isRayAngleFromOriginValid  op een tolerantiewaarde om te bepalen wat een "excessief" verschil in hoeken vormt:

isRayAngleFromOriginValid

```

local claimedDirection = (rayResult.destination.Position - originCFrame.Position).Unit

local directionErrorDegrees = getAngleBetweenDirections(claimedDirection, expectedDirection)

return directionErrorDegrees <= ToleranceValues.BLAST_ANGLE_SANITY_CHECK_TOLERANCE_DEGREES

```

Roblox abstraheert de meest betrokken wiskunde, zodat het resultaat een korte, zeer herbruikbare hulpfunctie is die toepasbaar is in een reeks spellen:

getAngleBetweenDirections

```

local function getAngleBetweenDirections(directionA: Vector3, directionB: Vector3)

    local dotProduct = directionA:Dot(directionB)

    local cosAngle = math.clamp(dotProduct, -1, 1)

    local angle = math.acos(cosAngle)

    return math.deg(angle)

end

```

3.

De volgende controle is de meest intuïtieve. Terwijl getValidatedBlastData  DISTANCE_SANITY_CHECK_TOLERANCE_STUDS  gebruikt om te verifiëren dat de speler die heeft geschoten dicht bij het punt van oorsprong van de straal was, gebruikt isPlayerNearPosition  identieke logica om te controleren of de getagde speler dicht bij de bestemming van de straal was:

isPlayerNearPosition

```

local distanceFromCharacterToPosition = position - character:GetPivot().Position

if distanceFromCharacterToPosition.Magnitude > ToleranceValues.DISTANCE_SANITY_CHECK_TOLERANCE_STUDS then

    return false

end

```

4.

De laatste controle isRayPathObstructed  gebruikt een variatie van de ray cast-operatie om te controleren of de bestemming van de straal achter een muur of andere obstructie van de positie van de client ligt. Bijvoorbeeld, als een kwaadwillende speler systematisch alle muren uit het spel zou verwijderen om andere spelers te taggen, zou de server controleren en bevestigen dat de stralen ongeldig zijn omdat deze de positie van elk object binnen de omgeving kent.

isRayPathObstructed

```

local scaledDirection = (rayResult.destination.Position - blastData.originCFrame.Position)

scaledDirection *= (scaledDirection.Magnitude - 1) / scaledDirection.Magnitude

```

Geen enkele anti-exploitstrategie is alomvattend, maar het is belangrijk om te overwegen hoe kwaadwillende spelers je spel kunnen benaderen, zodat je controles kunt implementeren die de server kan uitvoeren om verdacht gedrag te markeren.

## [Verminder de gezondheid van de speler](#verminder-de-gezondheid-van-de-speler)[](#verminder-de-gezondheid-van-de-speler)

Nadat is geverifieerd dat een speler een andere speler heeft getagd, zijn de laatste stappen in het voltooien van de hoofdgameplayloop in het voorbeeld laser tag-spel het verminderen van de gezondheid van de getagde speler, het verhogen van de leaderboard en het respawnen van de speler terug in de ronde.

Te beginnen met het verminderen van de gezondheid van de getagde speler, behandelt [Spawning and respawning](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/spawn-respawn)  het onderscheid tussen [Player](/docs/nl-nl/reference/engine/classes/Player)  en [Player.Character](/docs/nl-nl/reference/engine/classes/Player#Character) , specifiek dat een karakter een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid) -model is. [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid) -modellen hebben een [Health](/docs/nl-nl/reference/engine/classes/Humanoid#Health) -eigenschap met een standaardwaarde van 100. In plaats van een eigen systeem te implementeren, gebruikt het voorbeeld laser tag-spel deze ingebouwde eigenschap om bij te houden hoeveel schade een speler nodig heeft voordat ze uit de ronde worden getagd.

Het spel slaat schadewaarden op in de damagePerHit -attribuut van elke blaster. Bijvoorbeeld, de blaster die een enkele laserstraal afvuurt, brengt 10 punten schade toe, dus het kost tien schoten met deze blaster om een andere speler uit te taggen. Om het proces van het taggen van een speler te starten, roept LaserBlastHandler  ServerScriptService  ⟩ LaserBlastHandler  ⟩ processTaggedPlayers  aan, die de nu gevalideerde rayResults -tabel controleert op spelers en damagePerHit  doorgeeft aan onPlayerTagged .

Let op dat dit proces voor elke straal  plaatsvindt, niet voor elke speler. Een blast kan meerdere laserstralen hebben, zodat een speler meerdere keren schade kan oplopen van een enkele blast.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/gameplay-scripting/Detecting-Hits/Reduce-Player-Health.png)

[Health](/docs/nl-nl/reference/engine/classes/Humanoid#Health)  accepteert geen negatieve waarden, dus onPlayerTagged  heeft enige logica om de gezondheid van de speler op of boven nul te houden. Nadat is geverifieerd dat de gezondheid van de speler boven nul is, vergelijkt het de gezondheid met damagePerHit  en gebruikt het de kleinere van de twee waarden. Bijvoorbeeld, als een speler 10 gezondheid heeft en wordt geraakt door een laserstraal van 15 schade, brengt de laser slechts 10 punten schade toe.

Deze manier van het probleem benaderen lijkt misschien een beetje ingewikkeld. Waarom zou je de gezondheid van de speler niet gewoon op nul zetten als deze negatief zou zijn? De reden is dat het instellen van gezondheidswaarden de krachtveld omzeilt. Het gebruik van de [Humanoid:TakeDamage()](/docs/nl-nl/reference/engine/classes/Humanoid#TakeDamage) -methode zorgt ervoor dat spelers geen schade oplopen terwijl hun krachtvelden actief zijn.

onPlayerTagged

```

local function onPlayerTagged(playerBlasted: Player, playerTagged: Player, damageAmount: number)

	local character = playerTagged.Character

	local isFriendly = playerBlasted.Team == playerTagged.Team

	-- Vriendelijk vuur niet toestaan

	if isFriendly then

		return

	end

	local humanoid = character and character:FindFirstChild("Humanoid")

	if humanoid and humanoid.Health > 0 then

		-- Voorkom negatieve gezondheid

		local damage = math.min(damageAmount, humanoid.Health)

		-- TakeDamage zorgt ervoor dat de gezondheid niet verlaagd wordt als ForceField actief is

		humanoid:TakeDamage(damage)

		if humanoid.Health <= 0 then

			-- Ken playerBlasted een punt toe voor het taggen van playerTagged

			Scoring.incrementScore(playerBlasted, 1)

		end

	end

end

```

De volgende stap is het verhogen van de leaderboard. Het lijkt misschien overbodig dat LaserBlastHandler  de speler die heeft geschoten samen met de blastgegevens heeft opgenomen, maar zonder die informatie kan het spel de speler niet crediteren voor het taggen van iemand. Ten slotte respawnt de getagde speler terug in de ronde, wat je kunt bekijken in [Spawning and Respawning](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/spawn-respawn) .

De vijf hoofdstukken in dit curriculum behandelen de kern gameplayloop van het spel, maar er zijn nog veel gebieden te verkennen, zoals:

-

Blaster visuals : Zie ReplicatedStorage  ⟩ FirstPersonBlasterVisuals  en ServerScriptService  ⟩ ThirdPersonBlasterVisuals .

-

Audio : Zie ReplicatedStorage  ⟩ SoundHandler .

-

Aangepaste modi : Hoe zou je dit spel kunnen aanpassen om nieuwe soorten doelstellingen in te voeren, zoals het scoren van de meeste punten voordat de tijd om is?

Voor uitgebreide gameplaylogica voor het laser tag-spel, evenals herbruikbare, hoogwaardige omgevingsassets, bekijk de [Laser Tag](/docs/nl-nl/resources/templates#laser-tag)  sjabloon.

We zijn geïnteresseerd in je ervaringen met het volgen van het Gameplay Scripting Curriculum. Als je vragen, opmerkingen of aanvullende feedback over het proces hebt, laat dan een reactie achter op onze [Gameplay Scripting Curriculum Q&A](https://devforum.roblox.com/t/gameplay-scripting-curriculum-qa/2731896) .

[Vorige](/docs/nl-nl/tutorials/curriculums/gameplay-scripting/implement-blasters)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
