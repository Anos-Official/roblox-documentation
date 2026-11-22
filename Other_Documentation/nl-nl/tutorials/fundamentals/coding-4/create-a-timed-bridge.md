<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-4/create-a-timed-bridge -->

Lussen oefenen - maak een getimede brug | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Loops](/docs/nl-nl/tutorials/fundamentals/coding-4/landing)

# Lussen oefenen - maak een getimede brug

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Dit project is een ander voorbeeld van het gebruik van for-lussen op een praktische manier. Voor deze brug zullen spelers een knop aanraken om een brug begaanbaar te maken voor een beperkte tijd voordat deze verdwijnt. Om een timer te maken en de resterende tijd aan een speler te tonen, gebruik je for-lussen.

## [Stel het project in](#stel-het-project-in)[](#stel-het-project-in)

Deze brug kan worden opgenomen in elk Roblox-project met op beweging gebaseerde uitdagingen, zoals een obby.

### [Maak onderdelen](#maak-onderdelen)[](#maak-onderdelen)

1.

Zoek een plek om een brug te bouwen, zoals een rivier of een grote kloof in een obby. Maak drie geankerde  onderdelen zoals hieronder.

-

TimerDisplay

-

Brug

-

ButtonBridge

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-4/forLoopBridge_bridgeSetup.png)

2.

Wanneer inactief, zal de brug semi-transparant zijn. Om dit te doen, selecteer de Brug  en wijzig de eigenschappen.

-

Transparantie  = 0.8

-

KanCollide  = Onwaar

### [Maak de timerweergave](#maak-de-timerweergave)[](#maak-de-timerweergave)

Wanneer spelers de brug oversteken, moeten ze zien hoeveel seconden er nog over zijn voordat de brug verdwijnt. Een manier om afbeeldingen of tekst weer te geven, is door een object genaamd een Surface GUI aan een onderdeel toe te voegen. Surface GUIs  kunnen ook worden gebruikt om in-game borden, aangepaste gezondheidsbalken en inventarisystemen te maken. Deze tutorial zal dit snel doorlopen, maar meer informatie is te vinden in de [Tutorials](/docs/nl-nl/tutorials)  sectie.

1.

Selecteer TimerDisplay en voeg een SurfaceGui  toe. Voeg vervolgens, als kind van de Surface Gui, een TextLabel  toe.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-4/forLoopBridge_addTextLabel.png)

2.

Selecteer de Surface GUI. Maak in de eigenschappen de volgende wijzigingen:

-

Wijzig de Face  zodat je het tekstlabel op de voorkant van de timer kunt zien waar de speler naar kijkt.

3.

Selecteer de TextLabel. Maak in de eigenschappen de volgende wijzigingen:

-

Stel Grootte  in op {1, 0},{1, 0} .

-

Stel TextScaled  in op waar.

-

Stel Text  in op leeg. De tekst zal worden bijgewerkt met behulp van het script.

### [Stel het script in](#stel-het-script-in)[](#stel-het-script-in)

Nu de timer is ingesteld, maak een script om de brug te bedienen en het aftelt getal aan de spelers weer te geven.

1.

Voeg in het Brug-onderdeel een nieuw script toe met de naam TimedBridge. Maak in dat script de volgende variabelen aan.

```

local bridge = script.Parent

local button = workspace.ButtonBridge

local timerText = workspace.TimerDisplay.SurfaceGui.TextLabel

-- Hoe lang de brug solide blijft

local timerDuration = 5

```

## [Code de aanraking interactie](#code-de-aanraking-interactie)[](#code-de-aanraking-interactie)

Om de brug te gebruiken, moet je twee functies maken. Eén functie maakt de brug begaanbaar en toont de timer. De andere functie luistert of een speler de knop aanraakt die de brug activeert.

1.

Maak een nieuwe functie genaamd startTimer()  met een printstatement erin. Je zult de printstatement gebruiken om je code te testen.

```

local timerDuration = 5

local function startTimer()

    print("Aftelling gestart")

end

```

2.

Code een functie genaamd buttonPressed()  om te controleren of een humanoïde de knop aanraakt. De functie moet een parameter partTouched  accepteren, en dan een lege if-statement hebben als een humanoïde in dat onderdeel wordt gedetecteerd.

```

local function startTimer()

   print("Aftelling gestart")

end

local function buttonPressed(partTouched)

   local character = partTouched.Parent

   local humanoid = character:FindFirstChildWhichIsA("Humanoid")

   if humanoid then

   end

end

```

3.

Om de timer te starten, roep je in de if -statement de functie startTimer()  aan.

```

local function buttonPressed(otherPart)

   local character = otherPart.Parent

   local humanoid = character:FindFirstChildWhichIsA("Humanoid")

   if humanoid then

      startTimer()

   end

end

```

4.

Onder het einde van buttonPressed() , verbind de functie buttonPressed()  met de Touched -gebeurtenis van de knop.

```

local function buttonPressed(otherPart)

   local character = otherPart.Parent

   local humanoid = character:FindFirstChildWhichIsA("Humanoid")

   if humanoid then

      startTimer()

   end

end

button.Touched:Connect(buttonPressed)

```

5.

Voer het project uit. Raak het onderdeel aan en controleer in het Output-venster of je de printstatement ziet.

### [Probleemoplossing tips](#probleemoplossing-tips)[](#probleemoplossing-tips)

Op dit punt, als de brug niet werkt zoals bedoeld, probeer dan een van de volgende oplossingen hieronder.

Probleem : Foutmelding zegt: "... is geen geldig lid van workspace" .

-

Controleer in het TimedBridge-script of alle onderdelen precies zo zijn gespeld als ze in de Explorer worden weergegeven.

Probleem : Kan de onderdelen niet zien.

-

Zorg ervoor dat alle drie de onderdelen geankerd zijn.

-

Controleer de transparantie-eigenschap voor de brug.

## [Maak de timer](#maak-de-timer)[](#maak-de-timer)

Wanneer spelers op de brug stappen, zal startTimer()  de brug begaanbaar maken en de timer starten. Zodra de timer 0 bereikt, wordt de brug onbegaanbaar, waardoor iedereen die niet snel genoeg is valt.

### [Maak de brug begaanbaar](#maak-de-brug-begaanbaar)[](#maak-de-brug-begaanbaar)

Om te beginnen, moet het script de brug solide maken, of collidable, en dan een timer starten totdat deze onbegaanbaar wordt.

1.

Om de brug begaanbaar te maken, wijzig in startTimer()  de transparantie-eigenschap van de brug naar 0 (opake) en de CanCollide-eigenschap naar waar.

```

local function startTimer()

   -- Maak de brug zichtbaar en begaanbaar

   bridge.Transparency = 0

   bridge.CanCollide = true

end

```

2.

Om een timer te maken die aftelt, maak een for-lus met de volgende waarden.

-

Controlevariabele : genaamd count , ingesteld op timerDuration .

-

Einde : 0

-

Incrementeer : -1

```

local function startTimer()

   -- Maak de brug zichtbaar en begaanbaar

   bridge.Transparency = 0

   bridge.CanCollide = true

   for count = timerDuration, 0, -1 do

   end

end

```

3.

Om de timer aan de spelers te tonen, wijzig de tekst in timerText  om count weer te geven door timerText.Text = count  te typen. Elke keer dat de for-lus een iteratie doorloopt, toont het de volgende nummer in de timer aan de spelers.

```

for count = timerDuration, 0, -1 do

   timerText.Text = count

end

```

4.

Gebruik een task.wait functie om ervoor te zorgen dat de for-lus slechts één keer per seconde draait.

```

for count = timerDuration, 0, -1 do

   timerText.Text = count

   task.wait(1)

end

```

5.

Voer het spel uit. Wanneer je de knop aanraakt, zou de brug moeten verschijnen en de timer zal starten, en dan voltooien.

## [Houd de brug tegen het opnieuw starten](#houd-de-brug-tegen-het-opnieuw-starten)[](#houd-de-brug-tegen-het-opnieuw-starten)

Merk op dat als je rondbeweegt op de knop, de timer steeds opnieuw zal starten.

Dit komt omdat de for-lus elke keer wordt aangeroepen wanneer je de knop aanraakt en de for-lus vanaf het begin start. Om te voorkomen dat de timer constant opnieuw start, moet je een boolean toevoegen, een soort variabele, die zal controleren of startTimer()  opnieuw mag worden aangeroepen.

Booleans  worden op dezelfde manier geschreven als andere variabelen, maar in plaats van nummers of strings te gebruiken, kunnen ze alleen op waar of onwaar worden ingesteld. In deze situatie zal het script een boolean gebruiken om te controleren of de timer momenteel actief is voordat deze wordt gestart.

1.

Aan de bovenkant van je script, onder je variabelen, maak een variabele genaamd timerActive  en stel deze in op false  omdat nog niemand de knop heeft ingedrukt.

```

local timerDuration = 5

local timerActive = false

local function startTimer()

```

2.

Om ervoor te zorgen dat de timer alleen start wanneer de boolean timerActive  onwaar is, voeg een tweede voorwaarde toe aan de if-statement in buttonPressed() .

```

local function buttonPressed(otherPart)

   local character = otherPart.Parent

   local humanoid = character:FindFirstChildWhichIsA("Humanoid")

   if humanoid and timerActive == false then

      startTimer()

   end

end

```

3.

Om te voorkomen dat startTimer()  opnieuw wordt uitgevoerd voordat de timer is afgelopen, stel de boolean timerActive  in op waar.

```

local function startTimer()

   timerActive = true

   bridge.Transparency = 0

   bridge.CanCollide = true

```

4.

In de functie startTimer() , na  de for-lus, stel de brug terug in op zijn oorspronkelijke eigenschappen door de transparantie van de brug in te stellen op 0.8 en CanCollide op onwaar.

```

local function startTimer()

   timerActive = true

   bridge.Transparency = 0

   bridge.CanCollide = true

   -- For-lus die aftelt van timerDuration

   for count = timerDuration, 0, -1 do

      timerText.Text = count

      task.wait(1)

   end

   -- Maak de brug niet begaanbaar

   bridge.Transparency = 0.8

   bridge.CanCollide = false

end

```

5.

Een laatste ding om de brug te resetten is om de timerText  in te stellen op een lege string zoals het oorspronkelijk was. Stel vervolgens de boolean timerActive  in op onwaar.

```

bridge.Transparency = 0.8

bridge.CanCollide = false

timerText.Text = ""

timerActive = false

```

6.

Speeltest en controleer of de brug meerdere keren kan worden gebruikt.

## [Voltooi getimede brug script](#voltooi-getimede-brug-script)[](#voltooi-getimede-brug-script)

```

local bridge = script.Parent

-- Krijgt de knop zoals deze is getypt in de Explorer

local button = workspace.ButtonBridge

-- Krijgt het onderdeel voor de weergave

local timerPart = workspace.TimerDisplay

-- Krijgt de tekst die de timer zal weergeven

local timerText = timerPart.SurfaceGui.TextLabel

-- Hoe lang spelers hebben om de brug over te steken

local timerDuration = 5

local timerActive = false

local function startTimer()

    print("Aftelling gestart")

	timerActive = true

	bridge.Transparency = 0

	bridge.CanCollide = true

	-- For-lus die aftelt van timerDuration

	for count = timerDuration, 0, -1 do

		timerText.Text = count

		task.wait(1)

	end

	-- Maak de brug niet begaanbaar

	bridge.Transparency = 0.8

	bridge.CanCollide = false

	timerText.Text = ""

	timerActive = false

end

local function buttonPressed(partTouched)

	local character = partTouched.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	print("onderdeel aangeraakt")

	if humanoid and timerActive == false then

		print("timer starten")

		startTimer()

	end

end

button.Touched:Connect(buttonPressed)

```

## [Samenvatting](#samenvatting)[](#samenvatting)

Lussen kunnen worden gecombineerd met verschillende vormen van interactie om leuke gameplay-momenten te creëren. In deze tutorial wordt een getimede brug gemaakt met behulp van een for-lus die fungeert als een aftelling. Tijdens de aftelling krijgen spelers een beperkte tijd om over te steken.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-4/nested-loops)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-4/glow-lights-with-for-loops)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
