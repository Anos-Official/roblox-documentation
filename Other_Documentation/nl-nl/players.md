<!-- Source: https://create.roblox.com/docs/nl-nl/players -->

Gebruikers en spelers | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelers](/docs/nl-nl/players)

# Gebruikers en spelers

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Wanneer een Roblox-gebruiker zich bij een spel voegt, wordt hij weergegeven als een [Player](/docs/nl-nl/reference/engine/classes/Player)  in het [DataModel](/docs/nl-nl/reference/engine/classes/DataModel) . Dit [Player](/docs/nl-nl/reference/engine/classes/Player) -object bevat informatie over de gebruiker die universeel is voor spellen, zoals hun gebruikersnaam, vriendenlijst en opgeslagen [avatar-personage](/docs/nl-nl/characters#speler-personages) , evenals eigenschappen, methoden en gebeurtenissen die de [levenscyclus](#levenscyclus)  van de gebruiker beïnvloeden tussen het toetreden tot en het verlaten van het spel. Elk [Player](/docs/nl-nl/reference/engine/classes/Player) -object heeft ook vier belangrijke [containers](#containers)  die je kunt gebruiken om de ervaring van een gebruiker aan te passen: [Backpack](/docs/nl-nl/reference/engine/classes/Backpack) , [StarterGear](/docs/nl-nl/reference/engine/classes/StarterGear) , [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui)  en [PlayerScripts](/docs/nl-nl/reference/engine/classes/PlayerScripts) .

Elke [Player](/docs/nl-nl/reference/engine/classes/Player)  exposeert ook een [Player.User](/docs/nl-nl/reference/engine/classes/Player#User) -eigenschap, die een [User](/docs/nl-nl/reference/engine/datatypes/User)  is die de identiteit van de speler binnen het domein van het huidige spel vertegenwoordigt. De [Id](/docs/nl-nl/reference/engine/datatypes/User#Id) -eigenschap is altijd de [effectieve gebruikers-ID](/docs/nl-nl/players/users#effectieve-gebruikers-ids-en-domeinen)  van die gebruiker voor het bijbehorende domein. Voor meer informatie over effectieve gebruikers-ID's, zie [Gebruikers en gescoope gebruikers-ID's](/docs/nl-nl/players/users) .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Players-Player-Hierarchy.png)

## [Levenscyclus](#levenscyclus)[](#levenscyclus)

De [Players](/docs/nl-nl/reference/engine/classes/Players) -service bevat alle [Player](/docs/nl-nl/reference/engine/classes/Player) -instanties in een spel. Scripts aan de client- en serverzijde kunnen beide verbinding maken met de [Players.PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded)  en [Players.PlayerRemoved](/docs/nl-nl/reference/engine/classes/Players#PlayerRemoved) -evenementen om acties uit te voeren als reactie op de levenscyclus van een [Player](/docs/nl-nl/reference/engine/classes/Player) -object. Scripts kunnen ook verbinding maken met de [Player.CharacterAdded](/docs/nl-nl/reference/engine/classes/Player#CharacterAdded)  en [Player.CharacterRemoving](/docs/nl-nl/reference/engine/classes/Player#CharacterRemoving) -evenementen om gameplay-gerelateerde acties uit te voeren wanneer het personage verschijnt of verdwijnt.

### [Gebruiker voegt toe](#gebruiker-voegt-toe)[](#gebruiker-voegt-toe)

Wanneer een gebruikersclient verbinding maakt met een spel, wordt het [Players.PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded) -evenement geactiveerd en wordt het [Player](/docs/nl-nl/reference/engine/classes/Player) -object van de gebruiker die zich voegt doorgegeven; je kunt dit object voor verschillende doeleinden gebruiken, zoals het laden van [gebruikersgegevens](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)  uit een gegevensopslag of het toewijzen van de speler aan een [team](/docs/nl-nl/players/teams) .

Bijvoorbeeld, om de gegevens van een gebruiker te laden wanneer ze zich bij een spel voegen, gebruik je het [PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded) -evenement in een [Script](/docs/nl-nl/reference/engine/classes/Script)  om de gegevens van de gebruiker op te halen die zijn opgeslagen in een gegevensopslag onder hun gebruikers-ID:

Script in ServerScriptService

```

local DataStoreService = game:GetService("DataStoreService")

local Players = game:GetService("Players")

local playerDataStore = DataStoreService:GetDataStore("PlayerData")

Players.PlayerAdded:Connect(function(player)

	local userId = player.UserId

	-- Lees gegevensopslag sleutel

	local getSuccess, currentData = pcall(function()

		return playerDataStore:GetAsync(userId)

	end)

	if getSuccess then

		print(currentData)

	end

	-- Voer verdere acties uit met currentData

end)

```

### [Personage spawnen](#personage-spawnen)[](#personage-spawnen)

Standaard vertegenwoordigt het [Player.Character](/docs/nl-nl/reference/engine/classes/Player#Character) -model van een gebruiker hun platformavatar en is [Players.CharacterAutoLoads](/docs/nl-nl/reference/engine/classes/Players#CharacterAutoLoads)  true , wat betekent dat het personagemodel automatisch spawnt wanneer de gebruiker zich bij een spel voegt.

Wanneer het [Player.Character](/docs/nl-nl/reference/engine/classes/Player#Character)  van een gebruiker spawnt, worden [Scripts](/docs/nl-nl/reference/engine/classes/Script)  en [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  in [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts)  gekloond naar het personagemodel en wordt het [Player.CharacterAdded](/docs/nl-nl/reference/engine/classes/Player#CharacterAdded) -evenement geactiveerd. Dit evenement geeft het nieuwe personagemodel door aan zijn luisteraars, die je kunt gebruiken om het [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid) -object van het personage te vinden en het gedrag ervan te wijzigen. Je kunt bijvoorbeeld [Humanoid:ApplyDescription()](/docs/nl-nl/reference/engine/classes/Humanoid#ApplyDescription)  gebruiken om de outfit van de avatar te veranderen.

### [Personage despawnen](#personage-despawnen)[](#personage-despawnen)

Wanneer de [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  van de speler sterft, verwijdert de server automatisch het personagemodel na de tijd die is opgegeven door [Players.RespawnTime](/docs/nl-nl/reference/engine/classes/Players#RespawnTime) . Je kunt vervolgens het [Player.CharacterRemoving](/docs/nl-nl/reference/engine/classes/Player#CharacterRemoving) -evenement gebruiken om andere objecten opnieuw in te stellen of gegevens die aan het personage zijn gekoppeld bij te werken.

### [Gebruiker verlaat](#gebruiker-verlaat)[](#gebruiker-verlaat)

Wanneer een gebruikersclient zich loskoppelt van een spel, vernietigt de server het bijbehorende [Player](/docs/nl-nl/reference/engine/classes/Player) -object binnen de [Players](/docs/nl-nl/reference/engine/classes/Players) -service. Op dit punt wordt het [Players.PlayerRemoving](/docs/nl-nl/reference/engine/classes/Players#PlayerRemoving) -evenement geactiveerd en wordt het [Player](/docs/nl-nl/reference/engine/classes/Player) -object van de gebruiker die zich heeft losgekoppeld doorgegeven. Je kunt dit voor verschillende doeleinden gebruiken, zoals het opslaan van gebruikersgegevens, het verwijderen van spelersstatistieken van een scorebord of het vernietigen van door spelers gemaakte modellen in het spel.

Het volgende voorbeeld [Script](/docs/nl-nl/reference/engine/classes/Script)  luistert naar het [PlayerRemoving](/docs/nl-nl/reference/engine/classes/Players#PlayerRemoving) -evenement en probeert de gegevens van de gebruiker op te slaan in een gegevensopslag onder hun gebruikers-ID:

Script in ServerScriptService

```

local DataStoreService = game:GetService("DataStoreService")

local Players = game:GetService("Players")

local playerDataStore = DataStoreService:GetDataStore("PlayerData")

Players.PlayerRemoving:Connect(function(player)

	local userId = player.UserId

	-- Verkrijg de gegevensstatus van de speler in het spel

	local currentData = getCurrentData(player)

	-- Opslaan in gegevensopslag

	local setSuccess, errorMessage = pcall(function()

	    playerDataStore:SetAsync(userId, currentData)

	end)

	if not setSuccess then

	    warn(errorMessage)

	end

end)

```

## [Containers](#containers)[](#containers)

Elk [Player](/docs/nl-nl/reference/engine/classes/Player) -object dat een gebruikersclient vertegenwoordigt, slaat verschillende belangrijke containers op: [Backpack](/docs/nl-nl/reference/engine/classes/Backpack) , [StarterGear](/docs/nl-nl/reference/engine/classes/StarterGear) , [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui)  en [PlayerScripts](/docs/nl-nl/reference/engine/classes/PlayerScripts) . Tijdens de runtime van het spel kopiëren verschillende containers in het "bewerk" gegevensmodel hun inhoud naar deze [Player](/docs/nl-nl/reference/engine/classes/Player) -containers, waaronder [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  naar [PlayerGui](/docs/nl-nl/reference/engine/classes/PlayerGui) , [StarterPack](/docs/nl-nl/reference/engine/classes/StarterPack)  naar [Backpack](/docs/nl-nl/reference/engine/classes/Backpack)  en [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts)  naar [PlayerScripts](/docs/nl-nl/reference/engine/classes/PlayerScripts) .

![Een diagram dat objecten tussen 'bewerken' en 'runtime' gegevensmodellen in kaart brengt.](https://prod.docsiteassets.roblox.com/assets/scripting/client-server/Data-Model-Mapping.png)

Backpack StarterGear PlayerGui PlayerScripts

[Tool](/docs/nl-nl/reference/engine/classes/Tool) -objecten in de [Backpack](/docs/nl-nl/reference/engine/classes/Backpack)  vormen de inventaris van de speler en worden weergegeven als pictogramknoppen onderaan het scherm. Zie [in‑game tools](/docs/nl-nl/players/tools)  voor meer informatie.

Zoals hierboven geïllustreerd, worden de inhoud van [StarterPack](/docs/nl-nl/reference/engine/classes/StarterPack)  en de [StarterGear](/docs/nl-nl/reference/engine/classes/StarterGear)  van de speler gekloond naar [Backpack](/docs/nl-nl/reference/engine/classes/Backpack)  wanneer het [Character](/docs/nl-nl/reference/engine/classes/Player#Character)  van een speler spawnt. Wanneer het personage sterft, vernietigt de client de [Backpack](/docs/nl-nl/reference/engine/classes/Backpack)  en vervangt deze door een nieuwe.

Om de standaard Roblox-inventaris GUI uit te schakelen en deze te vervangen door je eigen, roep je [StarterGui:SetCoreGuiEnabled()](/docs/nl-nl/reference/engine/classes/StarterGui#SetCoreGuiEnabled)  aan in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) , zoals beschreven in [schakel standaard UI uit](/docs/nl-nl/players/disable-ui) .

## [Ban gebruikers](#ban-gebruikers)[](#ban-gebruikers)

Om de beleefdheid en eerlijk spel in je spellen te waarborgen, kun je gebruikers verbannen die de regels of richtlijnen van de gemeenschap schenden. Je kunt de banduur, banberichten en zelfs verbannen naar mogelijke alternatieve accounts aanpassen. Bij het gebruik van deze functie moet je de [richtlijnen](#ban-richtlijnen)  voor verbannen en [berichten](#bericht-richtlijnen)  volgen.

Je hebt verschillende opties voor het werken met bans:

-

Elke spelpagina op de [Creator Hub](https://create.roblox.com/)  heeft een [Bans](/docs/nl-nl/production/bans)  dashboard.

-

Voor programmatisch gebruik met de engine API, zie [Players:BanAsync()](/docs/nl-nl/reference/engine/classes/Players#BanAsync) .

-

Voor Open Cloud, zie [bans en blokkades](/docs/nl-nl/cloud/features/bans-and-blocks) .

### [Apparaat blokkeren](#apparaat-blokkeren)[](#apparaat-blokkeren)

Naast het verbannen van een account ondersteunt [Players:BanAsync()](/docs/nl-nl/reference/engine/classes/Players#BanAsync)  apparaat blokkeren  via het ApplyDeviceBlock -veld in de configuratietabel. Wanneer je een gebruiker verbant die momenteel met ApplyDeviceBlock  ingesteld op true  met je spel is verbonden, wordt het apparaat dat aan die gebruiker is gekoppeld ook geblokkeerd om opnieuw te verbinden voor 24 uur. Deze optie voegt wrijving toe tegen het omzeilen van bans; verbannen spelers kunnen zich niet onmiddellijk opnieuw bij het spel voegen vanaf een nieuw account op hetzelfde apparaat.

-

Apparaat blokkeren geldt momenteel alleen voor spelers op desktop (Windows en macOS). Het geldt niet voor mobiele apparaten of consoles.

-

De apparaatblokkade wordt niet als een ban doorgegeven aan andere accounts die het apparaat hebben gebruikt.

-

Het aanroepen van de unban API op de getroffen gebruiker verwijdert onmiddellijk elke actieve apparaatblokkade die aan het apparaat van die gebruiker is gekoppeld, waardoor ze zich opnieuw bij het spel kunnen voegen.

### [Ban richtlijnen](#ban-richtlijnen)[](#ban-richtlijnen)

Bij het implementeren van bans in je spel, houd je aan de volgende richtlijnen:

-

Spelregels mogen niet in tegenspraak zijn met Roblox's [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  en [Terms of Use](https://en.help.roblox.com/hc/en-us/articles/115004647846-Roblox-Terms-of-Use) . Bijvoorbeeld, je kunt geen spelregel maken die iemand uitsluit vanwege hun geslacht, omdat dit in strijd is met [Roblox's Discriminatie, Beledigingen en Haatacties beleid](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards#discrimination-slurs-and-hate-speech) .

-

Makers moeten hun spelregels duidelijk ergens toegankelijk voor alle gebruikers vermelden.

-

Makers moeten hun spelregels eerlijk toepassen en niet willekeurig bepaalde gebruikers targeten.

-

Gebruikers kunnen rechtstreeks bij makers in beroep gaan als ze geloven dat hun ban onterecht was. Roblox zal deze beroepen niet bemiddelen, tenzij de gebruiker gelooft dat de spelregels van de maker of de handhaving van hun regels in strijd zijn met de [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) .

-

Roblox kan een spel modereren als er reden is om te geloven dat de spelregels van een maker of de handhaving van hun regels in strijd zijn met de [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) .

### [Bericht richtlijnen](#bericht-richtlijnen)[](#bericht-richtlijnen)

Wanneer een gebruiker wordt verbannen, ontvangt hij een foutmodaal met informatie zoals de banlengte en reden. In het tekstgefilterde bericht kun je aanvullende informatie opnemen, zoals beroep of contactinformatie, zolang je voldoet aan Roblox's [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) .

Bijvoorbeeld, in je banberichten mag je merknamen en platforms vermelden:

-

"Bezoek de Discord in mijn groep/spelpagina"

-

"Stuur me een bericht op Twitter of X"

Vermeldingen van persoonlijke informatie of directe links zijn niet toegestaan in dit berichtveld. Dit omvat het plaatsen van een specifieke gebruikersnaam of handle, of het geven van een directe link naar een Discord-server of X-account.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
