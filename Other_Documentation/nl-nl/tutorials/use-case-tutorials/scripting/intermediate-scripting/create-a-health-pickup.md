<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/scripting/intermediate-scripting/create-a-health-pickup -->

Maak een gezondheidsopname | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Scripting
6. /
7. Spel voor gemiddeld niveau

# Maak een gezondheidsopname

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Gedurende de Basis Scripting tutorials heb je individuele onderdelen geprogrammeerd om speelbare scènes te creëren. Met de vorige methode, als je de onderdelen zou dupliceren, zou je ook duplicaten van de scripts hebben. Dit zou het bijwerken van de scripts moeizaam maken, omdat wijzigingen script voor script gedaan moesten worden.

In deze tutorial zal een ander patroon worden gebruikt om een aantal gezondheidsopnames te maken, met slechts één kopie van het script dat het gedrag van de gezondheidsopname bepaalt. Wanneer de opname wordt aangeraakt, herstelt deze de gezondheid van de speler, vervaagt deze iets en wordt deze voor een korte periode uitgeschakeld.

## [Opzetten](#opzetten)[](#opzetten)

Allereerst heb je een onderdeel of een model nodig om als opname te gebruiken. De [Showdown Town voorbeeldwereld](https://www.roblox.com/games/6407123421/Showdown-Town-Health-Pickups)  bevat veel gezondheidsopnames verspreid over de kaart.

 ![Bewerken in Studio optie van de hoofdpagina van het spel](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-a-health-pickup/Showdown-Town-Edit-Place.png)

Elke gezondheidsopname is een Unie van twee rechthoekige onderdelen met een groene PointLight erin. Ze zijn allemaal opgeslagen in één map in de Workspace genaamd HealthPickups , waar het script naar zal zoeken. Als je er meer aan de kaart toevoegt, is het essentieel dat je ervoor zorgt dat ze ook in deze map zijn opgeslagen.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-a-health-pickup/healthPickupGame.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-a-health-pickup/healthPickupExplorer.png)

## [Herstel gezondheid](#herstel-gezondheid)[](#herstel-gezondheid)

Om te beginnen moet het script de gezondheid van een speler herstellen. Dit patroon zou je bekend moeten zijn van de [Dodelijke Lava](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/deadly-lava)  tutorial.

1.

Voeg in ServerScriptService  een script toe genaamd PickupManager .

2.

Declareer in dit script een constante genaamd MAX_HEALTH  met de waarde 100 .

3.

Maak een functie genaamd onTouchHealthPickup  met parameters voor het andere onderdeel dat de opname aanraakt en de opname zelf.

```

local MAX_HEALTH = 100

local function onTouchHealthPickup(otherPart, healthPickup)

end

```

4.

In de functie, haal het karaktermodel op van de ouder van otherPart . Controleer vervolgens of het een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  heeft met behulp van [FindFirstChildWhichIsA()](/docs/nl-nl/reference/engine/classes/Instance#FindFirstChildWhichIsA) .

5.

Als het een humanoïde heeft, stel dan hun Health  eigenschap in op MAX_HEALTH .

```

local MAX_HEALTH = 100

local function onTouchHealthPickup(otherPart, healthPickup)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.Health = MAX_HEALTH

	end

end

```

De code hier roept [FindFirstChildWhichIsA()](/docs/nl-nl/reference/engine/classes/Instance#FindFirstChildWhichIsA)  aan – die het type  van het gewenste object neemt – in plaats van [FindFirstChild()](/docs/nl-nl/reference/engine/classes/Instance#FindFirstChild)  dat alleen de naam neemt. Dit is een veiligere optie omdat het alleen een Humanoid kan retourneren in plaats van iets dat toevallig "Humanoid" heet.

## [Verkrijg de opnamemappen](#verkrijg-de-opnamemappen)[](#verkrijg-de-opnamemappen)

De map die de gezondheidsopnames bevat, is mogelijk nog niet geladen in het spel tegen de tijd dat het script draait. WaitForChild  kan worden gebruikt om het script te pauzeren en de HealthPickups-map op te halen wanneer deze laadt.

Wanneer op een map aangeroepen, retourneert de functie GetChildren  een array van de inhoud van de map.

1.

Onder MAX_HEALTH, declareer een variabele genaamd healthPickupsFolder  en gebruik de functie WaitForChild  om de HealthPickups  map uit de Workspace te krijgen.

2.

Maak een variabele genaamd healthPickups  om het resultaat op te slaan van het aanroepen van de functie GetChildren  op healthPickupsFolder .

```

local MAX_HEALTH = 100

local healthPickupsFolder = workspace:WaitForChild("HealthPickups")

local healthPickups = healthPickupsFolder:GetChildren()

local function onTouchHealthPickup(otherPart, healthPickup)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.Health = MAX_HEALTH

	end

end

```

## [Loop met ipairs](#loop-met-ipairs)[](#loop-met-ipairs)

onTouchHealthPickup  moet worden aangeroepen voor elke gezondheidsopname in de array. Om dit efficiënt te doen, zal een nieuw soort loop-syntaxis worden gebruikt.

ipairs  is een functie die kan worden gebruikt met een for-lus om door elk element van een array te gaan. Je hoeft niet op te geven waar de lus begint en eindigt. Een for-lus met ipairs  wordt als volgt gedefinieerd:

![for index, value in ipairs(array) do](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-a-health-pickup/forLoop.jpg)

-

Index : dit is gelijk aan de controlevariabele in een reguliere for-lus.

-

Value : dit zal worden gevuld met elk element in de array terwijl de lus iteraties uitvoert. Het is een goed idee om de waardevariabele te benoemen naar wat het daadwerkelijk zal bevatten.

-

Array : de array die je wilt doorlopen wordt doorgegeven aan de ipairs  functie.

In de volgende code heb je de index voor niets nodig, dus deze kan leeg worden gelaten met _ . Maak een for -lus met de ipairs  functie, waarbij je healthPickups  doorgeeft.

```

local function onTouchHealthPickup(otherPart, healthPickup)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.Health = MAX_HEALTH

	end

end

for _, healthPickup in ipairs(healthPickups) do

end

```

Een wrapperfunctie is nodig om de gezondheidsopname door te geven aan de onTouchHealthPickup  functie wanneer deze wordt verbonden met de Touched  gebeurtenis.

1.

In de for-lus, verbind de Touched gebeurtenis met een anonieme functie met een parameter genaamd otherPart .

2.

Roep de functie onTouchHealthPickups  aan, waarbij je zowel de otherPart  parameter als de healthPickup  doorgeeft.

```

for _, healthPickup in ipairs(healthPickups) do

	healthPickup.Touched:Connect(function(otherPart)

		onTouchHealthPickup(otherPart, healthPickup)

	end)

end

```

Test nu je code en je zou moeten ontdekken dat de gezondheidsopname je gezondheid herstelt. Je moet je speler eerst schade toebrengen - probeer op de ventilatieopening naast het spawnpunt te staan.

![Stoomventilatie in voorbeeldwereld rechts van het spawnpunt](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-a-health-pickup/dangerousVent.jpg)

Een gezondheidsbalk zou in de rechterbovenhoek moeten verschijnen die verdwijnt wanneer de speler is genezen.

## [Opname cooldown](#opname-cooldown)[](#opname-cooldown)

Momenteel zal de opname oneindig elke speler genezen die deze aanraakt. Het zou effectiever zijn als het slechts één keer kan worden opgepakt, met een korte cooldown voordat het opnieuw kan worden gebruikt.

Eerst moet je bijhouden of de opname zich in de cooldown-periode bevindt of niet. Het patroon hieronder zou je bekend moeten zijn van [Fade Trap](/docs/nl-nl/tutorials/use-case-tutorials/scripting/basic-scripting/fading-trap)  - deze keer zal de debounce worden bereikt door een attribuut op de gezondheidsopname in te stellen.

1.

In de for-lus, stel een nieuw attribuut  genaamd "Enabled"  in op true .

2.

Wikkel de code binnen onTouchHealthPickup  in een if-statement met de voorwaarde healthPickup:GetAttribute("Enabled") .

```

local function onTouchHealthPickup(otherPart, healthPickup)

	if healthPickup:GetAttribute("Enabled") then

		local character = otherPart.Parent

		local humanoid = character:FindFirstChildWhichIsA("Humanoid")

		if humanoid then

			humanoid.Health = MAX_HEALTH

		end

	end

end

for _, healthPickup in ipairs(healthPickups) do

	healthPickup:SetAttribute("Enabled", true)

	healthPickup.Touched:Connect(function(otherPart)

		onTouchHealthPickup(otherPart, healthPickup)

	end)

end

```

## [Schakel de opname uit](#schakel-de-opname-uit)[](#schakel-de-opname-uit)

De opname moet visuele feedback geven dat deze is uitgeschakeld - een veelgebruikte manier om dit aan te geven is door deze iets transparant te maken.

1.

Declareer drie constanten bovenaan het script (voel je vrij om elke waarde naar wens aan te passen):

-

ENABLED_TRANSPARENCY = 0.4

-

DISABLED_TRANSPARENCY = 0.9

-

COOLDOWN = 10

```

local MAX_HEALTH = 100

local ENABLED_TRANSPARENCY = 0.4

local DISABLED_TRANSPARENCY = 0.9

local COOLDOWN = 10

local healthPickupsFolder = workspace:WaitForChild("HealthPickups")

```

2.

In de if-statement in onTouchHealthPickup , stel de [Transparency](/docs/nl-nl/reference/engine/classes/BasePart#Transparency)  van de opname in op DISABLED_TRANSPARENCY , en de waarde van het Enabled  attribuut op false.

```

local function onTouchHealthPickup(otherPart, healthPickup)

	if healthPickup:GetAttribute("Enabled") then

		local character = otherPart.Parent

		local humanoid = character:FindFirstChildWhichIsA("Humanoid")

		if humanoid then

			humanoid.Health = MAX_HEALTH

			healthPickup.Transparency = DISABLED_TRANSPARENCY

			healthPickup:SetAttribute("Enabled", false)

		end

	end

end

```

3.

Roep de functie [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  aan, waarbij je COOLDOWN  doorgeeft als de hoeveelheid om te wachten.

4.

Stel Transparency  weer in op ENABLED_TRANSPARENCY  en Enabled  weer in op true .

```

local function onTouchHealthPickup(otherPart, healthPickup)

	if healthPickup:GetAttribute("Enabled") then

		local character = otherPart.Parent

		local humanoid = character:FindFirstChildWhichIsA("Humanoid")

		if humanoid then

			humanoid.Health = MAX_HEALTH

			healthPickup.Transparency = DISABLED_TRANSPARENCY

			healthPickup:SetAttribute("Enabled", false)

			task.wait(COOLDOWN)

			healthPickup.Transparency = ENABLED_TRANSPARENCY

			healthPickup:SetAttribute("Enabled", true)

		end

	end

end

```

Test je opname opnieuw: je zou moeten ontdekken dat wanneer je de opname aanraakt, deze je gezondheid herstelt, transparant wordt en dan weer klaar is om opnieuw te worden gebruikt.

Als je de feedback voor de speler impactvoller wilt maken wanneer de opname wordt verzameld, probeer dan de helderheid van de PointLight in de opname te verlagen wanneer je de transparantie verandert.

Probeer deze gezondheidsopnames in je eigen projecten te gebruiken, of verander het uiterlijk en effect om je spelers een ander soort power-up te geven.

## [Eindcode](#eindcode)[](#eindcode)

```

local MAX_HEALTH = 100

local ENABLED_TRANSPARENCY = 0.4

local DISABLED_TRANSPARENCY = 0.9

local COOLDOWN = 10

local healthPickupsFolder = workspace:WaitForChild("HealthPickups")

local healthPickups = healthPickupsFolder:GetChildren()

local function onTouchHealthPickup(otherPart, healthPickup)

	if healthPickup:GetAttribute("Enabled") then

		local character = otherPart.Parent

		local humanoid = character:FindFirstChildWhichIsA("Humanoid")

		if humanoid then

			humanoid.Health = MAX_HEALTH

			healthPickup.Transparency = DISABLED_TRANSPARENCY

			healthPickup:SetAttribute("Enabled", false)

			task.wait(COOLDOWN)

			healthPickup.Transparency = ENABLED_TRANSPARENCY

			healthPickup:SetAttribute("Enabled", true)

		end

	end

end

for _, healthPickup in ipairs(healthPickups) do

	healthPickup:SetAttribute("Enabled", true)

	healthPickup.Touched:Connect(function(otherPart)

		onTouchHealthPickup(otherPart, healthPickup)

	end)

end

```

[Volgende](/docs/nl-nl/tutorials/use-case-tutorials/scripting/intermediate-scripting/save-data)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
