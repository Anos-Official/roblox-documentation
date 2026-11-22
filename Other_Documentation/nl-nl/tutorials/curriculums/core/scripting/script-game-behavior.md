<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/core/scripting/script-game-behavior -->

Maak een muntverzameling mechaniek | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Maak een muntverzameling mechaniek

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Nu je een 3D-wereld hebt, is het tijd om je eerste script toe te voegen. In deze sectie maak je een muntverzameling mechaniek waarmee spelers munten kunnen verzamelen en die tijdelijk de munten uitschakelt nadat ze zijn verzameld.

## [Maak de munten](#maak-de-munten)[](#maak-de-munten)

Voordat je iets kunt scripten, moet je placeholder-objecten in de wereld hebben om als je munten te gebruiken. Net als de zee-stapelplatforms die je in de vorige sectie hebt gemaakt, kunnen de munten eenvoudige [Part](/docs/nl-nl/reference/engine/classes/Part)  objecten zijn.

Bouw met Assistent Bouw het Zelf

Maak de munten

```

In Workspace > World, maak een nieuwe map genaamd Coins.

Binnen de Coins-map, maak een cilinder Part genaamd Coin met BrickColor ingesteld op Gold, Material ingesteld op Metal, Size 0.6, 8, 4, en Orientation 90, 0, 0.

Schakel CanCollide uit en schakel Anchored in.

Dupliceer vervolgens het Coin-deel meerdere keren en verspreid de duplicaten rond het eiland en op de platforms zodat ze bereikbaar zijn vanaf de zee-stapel niveaus.

Houd elke duplicaat genaamd Coin.

```

## [Maak het script](#maak-het-script)[](#maak-het-script)

Vervolgens laat je de munten reageren op spelers. De Roblox-engine kan detecteren wanneer iets een munt aanraakt, maar je moet een script gebruiken om te definiëren hoe de munt moet reageren.

Bouw met Assistent Bouw het Zelf

Maak CoinService

```

In ServerScriptService, maak een Script genaamd CoinService met de volgende code:

```lua

-- Initializing services and variables

local Workspace = game:GetService("Workspace")

local Players = game:GetService("Players")

local coinsFolder = Workspace.World.Coins

local coins = coinsFolder:GetChildren()

local COOLDOWN = 10

-- Defining the event handler

local function onCoinTouched(otherPart, coin)

	if coin:GetAttribute("Enabled") then

		local character = otherPart.Parent

		local player = Players:GetPlayerFromCharacter(character)

		if player then

			-- Speler heeft een munt aangeraakt

			coin.Transparency = 1

			coin:SetAttribute("Enabled", false)

			print("Speler verzamelde munt")

			task.wait(COOLDOWN)

			coin.Transparency = 0

			coin:SetAttribute("Enabled", true)

		end

	end

end

-- Setting up event listeners

for _, coin in coins do

	coin:SetAttribute("Enabled", true)

	coin.Touched:Connect(function(otherPart)

		onCoinTouched(otherPart, coin)

	end)

end

```

```

Nu, telkens wanneer een speler een munt aanraakt, verdwijnt de munt gedurende 10 seconden, en het uitvoerlogboek print Speler verzamelde munt .

Code uitleg

De volgende secties beschrijven hoe het script in meer detail werkt.

#### Initialiseer services en variabelen

Net als bij veel van de code die je waarschijnlijk in andere talen hebt geschreven, definieer je variabelen die je later nodig hebt aan de bovenkant van het script. Onze code doet het volgende:

-

Verkrijg service-instanties  - Roblox-services bieden ingebouwde functionaliteit voor veelvoorkomende functies. Het script verkrijgt eerst instanties van de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  service, die elk object in de 3D-wereld bevat, en de [Player](/docs/nl-nl/reference/engine/classes/Player)  service, die alle spelers beheert en bevat die verbonden zijn met je spel.

-

Verkrijg referenties naar alle munten  - Het script vraagt vervolgens de 3D-werkruimte op naar alle referenties naar muntobjecten met de [GetChildren()](/docs/nl-nl/reference/engine/classes/Instance#GetChildren)  methode. Deze methode retourneert een array die alles bevat wat aan het object is gekoppeld, wat in dit geval de Workspace.World.Coins  map is die je eerder hebt gemaakt.

-

Definieert een globale variabele  - De COOLDOWN  variabele wordt later gebruikt om te definiëren hoe lang een munt moet worden uitgeschakeld nadat deze is verzameld.

Initialiseren van Services en Variabelen

```

local Workspace = game:GetService("Workspace")

   local Players = game:GetService("Players")

   local coinsFolder = Workspace.World.Coins

   local coins = coinsFolder:GetChildren()

   local COOLDOWN = 10

   ...

```

#### Definieer de event handler

De Roblox Engine simuleert fysiek de 3D-wereld en behandelt veel van de logica om gebeurtenissen met betrekking tot rendering, fysica en netwerken te verwerken. Wanneer je geïnteresseerd bent in het scripten van je eigen logica tijdens enkele van deze gebeurtenissen, kun je luisteren naar en ze verwerken, terwijl je de engine de rest laat doen. In dit geval luister je naar en verwerk je gebeurtenissen met betrekking tot het aanraken van munten. Het script definieert de logica voor het verwerken van deze gebeurtenis in de onCoinTouched()  methode, die het volgende doet:

-

Detecteert of de munt is ingeschakeld  - Elke [Instance](/docs/nl-nl/reference/engine/classes/Instance)  heeft een Enabled  boolean attribuut dat definieert of het object al dan niet bestaat in de 3D-wereld. Je kunt instantie-attributen ophalen met de [GetAttribute()](/docs/nl-nl/reference/engine/classes/Instance#GetAttribute)  methode.

-

Detecteert of een speler de munt heeft aangeraakt  - Als een munt is ingeschakeld, gebruikt de methode de spelerservice om te controleren of het object dat de munt aanraakte inderdaad een speler was. Wanneer een aanraking plaatsvindt, geeft de Roblox Engine het object dat de munt aanraakte door als een otherPart  parameter. Het script controleert of de ouder van otherPart  tot een speler behoort.

-

Schakelt de munt uit als een speler deze aanraakt, en schakelt deze weer in na 10 seconden  - Ten slotte, als een speler de munt aanraakt, schakelt de methode de munt uit, wacht 10 seconden en schakelt de munt weer in voor verzameling. [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  wordt gebruikt in plaats van wait()  omdat het betere prestaties biedt door de code-uitvoering niet volledig te pauzeren, waardoor taken in andere threads gelijktijdig kunnen worden uitgevoerd.

Definiëren van de Event Handler

```

local function onCoinTouched(otherPart, coin)

      if coin:GetAttribute("Enabled") then

         local character = otherPart.Parent

         local player = Players:GetPlayerFromCharacter(character)

         if player then

            -- Speler heeft een munt aangeraakt

            coin.Transparency = 1

            coin:SetAttribute("Enabled", false)

            print("Speler verzamelde munt")

            task.wait(COOLDOWN)

            coin.Transparency = 0

            coin:SetAttribute("Enabled", true)

         end

      end

   end

```

#### Verbind de event handler

Alle gesimuleerde 3D-objecten erven van [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  en hebben daarom een [Touched()](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  evenement. De volgende lus verbindt de onTouchedEvent()  handler aan het aanraken van elke munt door het volgende te doen:

-

Loop door alle munten  - Loop door elke munt met behulp van algemene iteratie.

-

Verbind de handler met het evenement  - In elke iteratie van de lus wordt de munt standaard ingeschakeld, zodat deze zichtbaar is in de 3D-wereld tijdens de initiële start van het spel. De onCoinTouched()  handler methode wordt ook verbonden met het Touched  evenement van de munt, zodat deze elke keer wordt uitgevoerd wanneer het evenement plaatsvindt. Wanneer de engine een aanraking detecteert, geeft deze ook het object door dat het object aanraakte, otherPart .

Verbinding maken met de Event Handler

```

for _, coin in coins do

      coin:SetAttribute("Enabled", true)

      coin.Touched:Connect(function(otherPart)

         onCoinTouched(otherPart, coin)

      end)

   end

```

## [Speeltest de mechaniek](#speeltest-de-mechaniek)[](#speeltest-de-mechaniek)

Selecteer Test  in de dropdown en klik op Play . Beweeg je karakter om een munt aan te raken. Als alles werkt, verdwijnt de munt, het [Output](/docs/nl-nl/studio/output)  venster print Speler verzamelde munt , en de munt verschijnt 10 seconden later weer.

 ![Het uitvoervenster van Studio dat bevestigt dat de speler een munt heeft verzameld.](https://prod.docsiteassets.roblox.com/assets/tutorials/script-game-behavior/Output-Collect-Coin.png)

[Volgende](/docs/nl-nl/tutorials/curriculums/core/scripting/record-and-display-player-data)[Vorige](/docs/nl-nl/tutorials/curriculums/core/building/greybox-a-playable-area)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
