<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/security/device-trust -->

Apparaatvertrouwen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. Beveiliging

# Apparaatvertrouwen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Device Trust API  vertelt je hoeveel je het apparaat van elke speler die je spel betreedt kunt vertrouwen. Wanneer een speler zich aanmeldt, controleert Roblox of hun apparaat te vertrouwen is en geeft je het resultaat als een apparaatvertrouwensniveau . Deze controle is een optionele beschermingslaag bovenop de ingebouwde Roblox anti-cheat, die exploits detecteert nadat een speler zich heeft aangemeld.

Roblox onderneemt geen actie op basis van het apparaatvertrouwensniveau. Jij beslist wat het betekent voor jouw spel. Je kunt bijvoorbeeld spelers met een vergelijkbaar vertrouwen bij elkaar brengen, gevoelige functies zoals handelen beperken tot vertrouwde apparaten, of spelers weigeren wiens apparaten de controle niet doorstaan.

De Device Trust API bestaat uit de [IntegrityService.EvaluatePlayerDeviceTrust](/docs/nl-nl/reference/engine/classes/IntegrityService#EvaluatePlayerDeviceTrust)  callback en de [Player.DeviceTrustLevel](/docs/nl-nl/reference/engine/classes/Player#DeviceTrustLevel)  eigenschap. Om het in je scripts te gebruiken, zie [lees het vertrouwensniveau](#lees-het-vertrouwensniveau) .

Apparaatvertrouwen aanvult de tactieken in [beveiligings- en cheatmitigatietactieken](/docs/nl-nl/scripting/security/security-tactics)  in plaats van ze te vervangen.

## [Apparaatvertrouwensniveaus](#apparaatvertrouwensniveaus)[](#apparaatvertrouwensniveaus)

Het apparaatvertrouwensniveau van een speler is een van de volgende [Enum.PlayerDeviceTrustLevel](/docs/nl-nl/reference/engine/enums/PlayerDeviceTrustLevel)  waarden:

| Niveau | | Betekenis |
| --- | --- |
| Pending | | Roblox controleert het apparaat nog. Elke speler begint op dit niveau. |
| Unknown | | De speler bevindt zich op een niet-ondersteund platform, of er is een fout opgetreden aan de Roblox-kant. Roblox kan niet zeggen of het apparaat te vertrouwen is, dus het kan wel of niet betrouwbaar zijn. |
| None | | Het apparaat heeft de controle niet doorstaan, of de speler bevindt zich op een platform dat niet kan worden geverifieerd en vaak wordt gebruikt voor cheating. Spelers op dit niveau moeten meestal naar een ander apparaat overschakelen om een hoger niveau te bereiken, hoewel sommigen hun huidige apparaat kunnen repareren. |
| Standard | | Het apparaat heeft enkele van de controles doorstaan, maar niet allemaal. Het apparaat is meestal veilig, en de speler kan meestal Full  bereiken door hun apparaat bij te werken of te repareren. Sommige apparaten kunnen niet boven Standard  komen. |
| Full | | Het apparaat heeft elke controle doorstaan en is volledig veilig. |

Unknown  betekent niet onbetrouwbaar.  Het betekent dat Roblox niet kan zeggen of het apparaat betrouwbaar is. Het is aan jou om te beslissen wat Unknown  betekent voor jouw spel, en je kunt het op verschillende manieren behandelen in verschillende delen van je spel. Voor aanbevelingen, zie [aanbevolen beleidslijnen per genre](#aanbevolen-beleidslijnen-per-genre) .

## [Ondersteunde platforms](#ondersteunde-platforms)[](#ondersteunde-platforms)

Roblox controleert apparaatvertrouwen op de volgende platforms:

| Platform | | Status | | Gerapporteerd vertrouwensniveau |
| Android | |

Ondersteund

 | | None , Standard , of Full |
| Chromebook | |

Ondersteund

 | | None , Standard , of Full |
| Meta Quest | |

Ondersteund

 | | None , Standard , of Full |
| Webbrowser | |

Kan niet worden geverifieerd

 | | None |
| iOS | | Binnenkort | | Unknown |
| macOS | | Binnenkort | | Unknown |
| Windows | | Binnenkort | | Unknown |
| Xbox | | Binnenkort | | Unknown |
| PlayStation | | Binnenkort | | Unknown |

Totdat Roblox een platform ondersteunt, rapporteren spelers daarop Unknown .

Op een ondersteund platform hangt het vertrouwensniveau dat een apparaat kan bereiken ook af van de hardware. Niet elk Android-apparaat ondersteunt bijvoorbeeld de controles die Roblox gebruikt, zodat sommige apparaten niet Standard  of Full  kunnen bereiken, zelfs niet als ze niet zijn gemanipuleerd. Voor een lijst van bekende ondersteunde apparaten, zie het [Helpcentrum](https://en.help.roblox.com/hc/en-us/articles/49648939984916-Android-Remote-Attestation) .

## [Hoe het werkt](#hoe-het-werkt)[](#hoe-het-werkt)

Wanneer een speler zich aanmeldt bij jouw spel, gebruikt Roblox hardware-signalen van hun apparaat om het volgende te bevestigen:

-

Het apparaat is een fysiek apparaat en geen emulator.

-

Het besturingssysteem is niet gemanipuleerd, bijvoorbeeld door het apparaat te rooten.

-

De Roblox-app is niet gewijzigd.

Op basis van deze controles berekent Roblox een apparaatvertrouwensniveau voor de speler. Om de effectiviteit van het systeem te behouden, publiceert Roblox de specifieke signalen die het evalueert niet.

De controle wordt op de achtergrond uitgevoerd terwijl de speler zich aanmeldt, zodat het laden niet wordt vertraagd. Spelers kunnen beginnen met spelen voordat hun vertrouwensniveau beschikbaar is, dus beschouw een speler als onbetrouwbaar totdat dat het geval is. Voor details, zie [lees het vertrouwensniveau](#lees-het-vertrouwensniveau) .

Het apparaatvertrouwensniveau beschrijft het apparaat, niet de speler of hun account. Het vertelt je niet of een speler aan het cheaten is. Het vertelt je hoe moeilijk het is om te cheaten op hun apparaat. Om in plaats daarvan het account te controleren, gebruik je [Player:IsVerified()](/docs/nl-nl/reference/engine/classes/Player#IsVerified) .

## [Impact op legitieme spelers](#impact-op-legitieme-spelers)[](#impact-op-legitieme-spelers)

Sommige legitieme spelers gebruiken apparaten die geen hoog vertrouwensniveau kunnen bereiken. Als je spelers weigert of functies beperkt op basis van apparaatvertrouwen, beïnvloed je ook deze spelers.

Geen enkele apparaatcontrole is perfect. Sommige spelers die niet van plan zijn te cheaten, bereiken nog steeds een laag vertrouwensniveau. Deze spelers vallen in twee groepen.

### [Spelers die hun apparaat kunnen repareren](#spelers-die-hun-apparaat-kunnen-repareren)[](#spelers-die-hun-apparaat-kunnen-repareren)

Sommige apparaten zijn in staat om de controles door te staan, maar zijn niet goed ingesteld, zoals een apparaat met een verouderd besturingssysteem, een geroot apparaat of een apparaat dat een gewijzigde versie van de Roblox-app draait. Deze spelers kunnen meestal hun vertrouwensniveau verhogen door hun apparaat bij te werken, Roblox opnieuw te installeren vanuit een officiële app store, of hun apparaat naar de oorspronkelijke staat terug te brengen. Je kunt de getroffen spelers verwijzen naar de [oplossingsstappen](https://en.help.roblox.com/hc/en-us/articles/49648939984916-Android-Remote-Attestation)  op het Helpcentrum.

### [Spelers die hun apparaat niet kunnen repareren](#spelers-die-hun-apparaat-niet-kunnen-repareren)[](#spelers-die-hun-apparaat-niet-kunnen-repareren)

Andere spelers gebruiken oudere apparaten die de hardware waarop deze controles zijn gebaseerd niet ondersteunen. Deze spelers kunnen hun vertrouwensniveau op dat apparaat niet verhogen en kunnen alleen een hoger niveau bereiken door over te schakelen naar een nieuwer, ondersteund apparaat. Voor meer informatie, zie [ondersteunde platforms](#ondersteunde-platforms) .

### [Wat een geweigerde speler ziet](#wat-een-geweigerde-speler-ziet)[](#wat-een-geweigerde-speler-ziet)

Als jouw spel een speler weigert op basis van hun vertrouwensniveau, wordt de speler gedisconnecteerd en ziet een bericht. Je kunt dit bericht zelf schrijven, bijvoorbeeld om spelers naar een modus te verwijzen die ze nog steeds kunnen spelen. Als je dat niet doet, toont Roblox een standaardbericht dat uitlegt waarom ze zich niet konden aanmelden en hoe ze hun apparaat mogelijk kunnen repareren.

## [Implementatie](#implementatie)[](#implementatie)

### [Schat de impact in](#schat-de-impact-in)[](#schat-de-impact-in)

Voordat je actie onderneemt op basis van apparaatvertrouwen, controleer je hoeveel van jouw spelers elk vertrouwensniveau dekt. De Anti-cheat  pagina op Creator Hub schat hoe jouw dagelijkse actieve gebruikers, speeltijd en inkomsten op ondersteunde platforms zijn verdeeld per apparaatvertrouwensniveau. Om het te bekijken, moet je de eigenaar van het spel zijn of de [analyses voor ervaringen bekijken](/docs/nl-nl/projects/groups#rollen-en-machtigingen)  toestemming hebben.

1.

Navigeer naar jouw [Creations](https://create.roblox.com/dashboard/creations)  pagina op Creator Hub  en selecteer jouw spel.

2.

Selecteer in het menu aan de linkerkant Veiligheid , en selecteer vervolgens Anti-cheat .

### [Kies een beleid](#kies-een-beleid)[](#kies-een-beleid)

Jouw beleid is hoe jouw spel reageert op elk apparaatvertrouwensniveau. Om er een te kiezen:

1.

Bepaal wat Unknown  betekent voor jouw spel.  Het is aan jou of je spelers op Unknown  behandelt als spelers op vertrouwde apparaten, als spelers op None , of anders in verschillende delen van jouw spel.

2.

Controleer de impact.  Bekijk de Anti-cheat  pagina op Creator Hub om te zien hoe jouw spelers zijn verdeeld per vertrouwensniveau. Voor meer informatie, zie [schat de impact in](#schat-de-impact-in) .

3.

Kies hoe te reageren op elk niveau.  De volgende reacties gaan van minst tot meest verstorend, en je kunt ze combineren:

-

Routeren van spelers op basis van vertrouwensniveau.  Stuur spelers naar plaatsen of servers die passen bij hun vertrouwensniveau, zoals een casual plaats voor iedereen en een gerangschikte plaats voor vertrouwde apparaten. Elke speler kan nog steeds jouw spel spelen. Voor een voorbeeld, zie [route spelers op basis van vertrouwensniveau](#route-spelers-op-basis-van-vertrouwensniveau) .

-

Beperk gevoelige functies.  Vereis een hoger vertrouwensniveau voor een specifieke functie, zoals handelen, en laat iedereen de rest van jouw spel spelen. Voor een voorbeeld, zie [beperk functies op basis van vertrouwensniveau](#beperk-functies-op-basis-van-vertrouwensniveau) .

-

Weiger spelers.  Weiger spelers voor jouw hele spel. Weiger alleen spelers op None  als laatste redmiddel. Voor een voorbeeld, zie [weiger spelers bij aanmelding](#weiger-spelers-bij-aanmelding) .

#### [Aanbevolen beleidslijnen per genre](#aanbevolen-beleidslijnen-per-genre)[](#aanbevolen-beleidslijnen-per-genre)

De volgende tabel suggereert een startbeleid voor veelvoorkomende genres op Roblox. Pas het aan op basis van hoe jouw spel werkt.

| Genre | | Pending | | Unknown | | None | | Standard | | Full |
| Competitieve FPS | | Wacht tot een resultaat is berekend | |

Alleen casual

 | |

Alleen casual

 | |

Casual en gerangschikt

 | |

Casual en gerangschikt

 |
| Battlegrounds of vechten | | Wacht tot een resultaat is berekend | |

Gescheiden servers

 | |

Gescheiden servers

 | |

Vertrouwde servers

 | |

Vertrouwde servers

 |
| Racen, met ranglijsten | | Wacht tot een resultaat is berekend | |

Van ranglijsten af

 | |

Van ranglijsten af

 | |

Op ranglijsten

 | |

Op ranglijsten

 |
| Handels hangout | | Wacht tot een resultaat is berekend | |

Kan handelen

 | |

Kan niet handelen

 | |

Kan handelen

 | |

Kan handelen

 |
| Idle, AFK, of tycoon | | Wacht tot een resultaat is berekend | |

Verdient AFK-beloningen

 | |

Geen AFK-beloningen

 | |

Verdient AFK-beloningen

 | |

Verdient AFK-beloningen

 |
| Rollenspel of sociale hangout | | Wacht tot een resultaat is berekend | |

Volledige toegang

 | |

Volledige toegang

 | |

Volledige toegang

 | |

Volledige toegang

 |

### [Lees het vertrouwensniveau](#lees-het-vertrouwensniveau)[](#lees-het-vertrouwensniveau)

Elke gebruik van de Device Trust API begint met [Player.DeviceTrustLevel](/docs/nl-nl/reference/engine/classes/Player#DeviceTrustLevel) , dat het vertrouwensniveau van een speler bevat. Lees het op de server wanneer jouw spel een beslissing moet nemen, zoals wanneer een speler vraagt om deel te nemen aan een gerangschikte wedstrijd of een handel te starten.

Houd het volgende in gedachten wanneer je de eigenschap leest:

-

Elke speler begint op Pending , en de eigenschap verandert eenmaal, wanneer het vertrouwensniveau beschikbaar wordt. Als Roblox de controle van een apparaat niet kan voltooien, kan de eigenschap op Pending  blijven voor de hele sessie. Behandel Pending  altijd als niet betrouwbaar genoeg voor gevoelige functies.

-

Lees het vertrouwensniveau op de server, en laat de server elke client vertellen welke functies in te schakelen of uit te schakelen, bijvoorbeeld door een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  naar die speler te sturen. Vermijd het lezen van de eigenschap op de client. Alleen de eigen client van de speler kan hun vertrouwensniveau lezen, elke andere client ziet Pending , en exploiters kunnen veranderen wat hun client ermee doet.

-

In Studio is het vertrouwensniveau altijd Pending . Voor details, zie [test je logica](#test-je-logica) .

### [Wacht op het vertrouwensniveau](#wacht-op-het-vertrouwensniveau)[](#wacht-op-het-vertrouwensniveau)

Sommige delen van jouw spel hebben mogelijk het vertrouwensniveau nodig voordat een speler begint, zoals matchmaking die spelers naar een lobby stuurt op basis van hun vertrouwensniveau. In dat geval kun je een speler in [Players.PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded)  vasthouden totdat de callback wordt uitgevoerd, en dan doorgaan met hun vertrouwensniveau.

Gebruik dit patroon alleen om spelers te accepteren en hun ervaring aan te passen, bijvoorbeeld door ze te routeren of functies te beperken. Om spelers te weigeren, retourneer Reject  vanuit de [IntegrityService.EvaluatePlayerDeviceTrust](/docs/nl-nl/reference/engine/classes/IntegrityService#EvaluatePlayerDeviceTrust)  callback en houd die logica in de callback, zoals beschreven in [weiger spelers bij aanmelding](#weiger-spelers-bij-aanmelding) .

Het volgende script slaat de thread op waarin PlayerAdded  draait, yieldt het met [coroutine.yield()](/docs/nl-nl/reference/engine/libraries/coroutine#yield) , en hervat het vanuit de callback met [task.defer()](/docs/nl-nl/reference/engine/libraries/task#defer) . Als de speler vertrekt, of het vertrouwensniveau niet beschikbaar is na MAX_WAIT_SECONDS , hervat het script de thread zodat geen enkele speler voor altijd wacht:

Script in ServerScriptService

```

local IntegrityService = game:GetService("IntegrityService")

local Players = game:GetService("Players")

local RunService = game:GetService("RunService")

-- Hoe lang je een speler moet vasthouden voordat je stopt met wachten op hun vertrouwensniveau

local MAX_WAIT_SECONDS = 10

-- De thread die wacht op het vertrouwensniveau van elke speler

local waitingThreads: { [Player]: thread } = {}

-- Hervat de thread die wacht op de speler, als die er is

local function release(player: Player, trustLevel: Enum.PlayerDeviceTrustLevel?)

	local thread = waitingThreads[player]

	if thread then

		waitingThreads[player] = nil

		task.defer(thread, trustLevel)

	end

end

-- Yieldt totdat het vertrouwensniveau van de speler beschikbaar is. Retourneert Pending als de

-- wachttijd verstrijkt, en nil als de speler eerst vertrekt.

local function waitForTrustLevel(player: Player): Enum.PlayerDeviceTrustLevel?

	-- Roblox controleert geen apparaten in Studio, dus houd spelers niet vast tijdens playtests

	if player.DeviceTrustLevel ~= Enum.PlayerDeviceTrustLevel.Pending or RunService:IsStudio() then

		return player.DeviceTrustLevel

	end

	waitingThreads[player] = coroutine.running()

	task.delay(MAX_WAIT_SECONDS, release, player, Enum.PlayerDeviceTrustLevel.Pending)

	return coroutine.yield()

end

IntegrityService.EvaluatePlayerDeviceTrust = function(player, measures)

	release(player, player.DeviceTrustLevel)

	return { Action = Enum.PlayerDeviceTrustDecision.Accept }

end

Players.PlayerRemoving:Connect(function(player)

	release(player, nil)

end)

Players.PlayerAdded:Connect(function(player)

	local trustLevel = waitForTrustLevel(player)

	if trustLevel == nil then

		return

	end

	-- Start de sessie van de speler hier, bijvoorbeeld door ze naar een lobby te sturen

	-- die past bij hun vertrouwensniveau. Behandel Pending als niet vertrouwd.

	print(player.Name, "heeft zich aangemeld met vertrouwensniveau", trustLevel.Name)

end)

```

### [Route spelers op basis van vertrouwensniveau](#route-spelers-op-basis-van-vertrouwensniveau)[](#route-spelers-op-basis-van-vertrouwensniveau)

In plaats van spelers te weigeren, kun je ze naar een plaats sturen die past bij hun vertrouwensniveau. Bijvoorbeeld, een competitief spel kan iedereen accepteren in een casual startplaats, en alleen spelers wiens vertrouwensniveau aan jouw vereisten voldoet naar een aparte gerangschikte plaats sturen.

Controleer in de casual plaats het vertrouwensniveau voordat je een speler naar de gerangschikte plaats teleporteert met [TeleportService:TeleportAsync()](/docs/nl-nl/reference/engine/classes/TeleportService#TeleportAsync) . Dit script gaat ervan uit dat jouw client UI een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  genaamd JoinRanked  in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  activeert wanneer een speler vraagt om gerangschikt te spelen:

Script in ServerScriptService van de casual plaats

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local TeleportService = game:GetService("TeleportService")

local RANKED_PLACE_ID = 12345678901234 -- Vervang door de ID van jouw gerangschikte plaats

local RANKED_TRUST_LEVELS = {

	[Enum.PlayerDeviceTrustLevel.Standard] = true,

	[Enum.PlayerDeviceTrustLevel.Full] = true,

}

local joinRankedEvent = ReplicatedStorage:WaitForChild("JoinRanked")

joinRankedEvent.OnServerEvent:Connect(function(player)

	if not RANKED_TRUST_LEVELS[player.DeviceTrustLevel] then

		-- Laat de speler weten dat gerangschikt spelen niet beschikbaar is op hun apparaat

		return

	end

	local success, result = pcall(function()

		return TeleportService:TeleportAsync(RANKED_PLACE_ID, { player })

	end)

	if not success then

		warn("Teleport naar gerangschikte plaats mislukt:", result)

	end

end)

```

Spelers kunnen de gerangschikte plaats op andere manieren bereiken, zoals door zich bij een vriend aan te sluiten. Om hetzelfde beleid daar af te dwingen, wijs je de [IntegrityService.EvaluatePlayerDeviceTrust](/docs/nl-nl/reference/engine/classes/IntegrityService#EvaluatePlayerDeviceTrust)  callback toe in de gerangschikte plaats, zoals beschreven in [weiger spelers bij aanmelding](#weiger-spelers-bij-aanmelding) , en weiger spelers die daar niet aan voldoen:

Script in ServerScriptService van de gerangschikte plaats

```

local IntegrityService = game:GetService("IntegrityService")

local RANKED_TRUST_LEVELS = {

	[Enum.PlayerDeviceTrustLevel.Standard] = true,

	[Enum.PlayerDeviceTrustLevel.Full] = true,

}

IntegrityService.EvaluatePlayerDeviceTrust = function(player, measures)

	if RANKED_TRUST_LEVELS[player.DeviceTrustLevel] then

		return { Action = Enum.PlayerDeviceTrustDecision.Accept }

	end

	return {

		Action = Enum.PlayerDeviceTrustDecision.Reject,

		Message = "Gerangschikt spelen is niet beschikbaar op dit apparaat. Je kunt nog steeds de casual modus spelen.",

	}

end

```

Spelers kunnen beginnen met spelen voordat de callback wordt uitgevoerd, dus start geen gerangschikte wedstrijd voor een speler terwijl hun vertrouwensniveau Pending  is. Om te controleren welke plaatsen spelers direct kunnen betreden, zie [configureer veilige teleportatie](/docs/nl-nl/projects/teleport#configureer-veilige-teleportatie) .

Deze voorbeelden houden spelers op Pending , Unknown , en None  buiten gerangschikt spelen. Als je besluit om spelers op Unknown  het voordeel van de twijfel te geven, voeg dan Unknown  toe aan beide tabellen.

### [Beperk functies op basis van vertrouwensniveau](#beperk-functies-op-basis-van-vertrouwensniveau)[](#beperk-functies-op-basis-van-vertrouwensniveau)

Om iedereen te laten spelen maar gevoelige functies, zoals handelen, te beperken, controleer je het vertrouwensniveau op de server wanneer een speler probeert de functie te gebruiken. Het volgende script staat alleen een handel toe wanneer beide spelers een toegestaan vertrouwensniveau hebben. Het opsommen van de toegestane niveaus in een tabel houdt jouw beleid op één plek:

Script in ServerScriptService

```

local TRADE_TRUST_LEVELS = {

	[Enum.PlayerDeviceTrustLevel.Unknown] = true,

	[Enum.PlayerDeviceTrustLevel.Standard] = true,

	[Enum.PlayerDeviceTrustLevel.Full] = true,

}

local function canTrade(player: Player): boolean

	return TRADE_TRUST_LEVELS[player.DeviceTrustLevel] == true

end

local function tradeItem(sender: Player, receiver: Player, itemId: string): boolean

	if not (canTrade(sender) and canTrade(receiver)) then

		return false

	end

	-- Valideer en verplaats het item hier op de server

	return true

end

```

Dit voorbeeld blokkeert handelen voor spelers op Pending  en None , en laat spelers op Unknown  handelen. Om ook handelen voor spelers op Unknown  te blokkeren, verwijder Unknown  uit de tabel.

Om ook het account te controleren voordat een gevoelige actie wordt uitgevoerd, combineer je het vertrouwensniveau met [Player:IsVerified()](/docs/nl-nl/reference/engine/classes/Player#IsVerified) .

### [Weiger spelers bij aanmelding](#weiger-spelers-bij-aanmelding)[](#weiger-spelers-bij-aanmelding)

Als het routeren van spelers of het beperken van functies niet genoeg is, kun je spelers uit jouw spel weigeren. Wijs een functie toe aan de [IntegrityService.EvaluatePlayerDeviceTrust](/docs/nl-nl/reference/engine/classes/IntegrityService#EvaluatePlayerDeviceTrust)  callback in een [Script](/docs/nl-nl/reference/engine/classes/Script)  in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) . Roblox roept deze functie eenmaal voor elke speler aan, zodra hun apparaatvertrouwensniveau beschikbaar is.

Bijvoorbeeld, het volgende script weigert spelers wiens apparaten de controle niet doorstaan en accepteert iedereen, inclusief spelers op Unknown :

Script in ServerScriptService

```

local IntegrityService = game:GetService("IntegrityService")

IntegrityService.EvaluatePlayerDeviceTrust = function(player, measures)

	if player.DeviceTrustLevel == Enum.PlayerDeviceTrustLevel.None then

		return {

			Action = Enum.PlayerDeviceTrustDecision.Reject,

			Message = "Dit spel kan jouw apparaat niet verifiëren.",

		}

	end

	return { Action = Enum.PlayerDeviceTrustDecision.Accept }

end

```

Houd het volgende in gedachten wanneer je de callback toewijst:

-

De callback draait alleen op de server. Je kunt het niet toewijzen vanuit een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) .

-

Elke plaats heeft één callback. Als je het meer dan eens toewijst, vervangt de laatste toewijzing de eerdere, dus wijs het toe in één script. Verschillende plaatsen in jouw spel kunnen verschillende callbacks toewijzen.

-

De callback draait nadat [Players.PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded)  is geactiveerd, omdat het controleren van het apparaat tijd kost. Wanneer de callback draait, bevat [Player.DeviceTrustLevel](/docs/nl-nl/reference/engine/classes/Player#DeviceTrustLevel)  al het vertrouwensniveau van de speler.

-

De callback kan yielden, bijvoorbeeld om gegevens te laden voordat het een beslissing neemt. De speler blijft spelen terwijl de callback draait.

-

De callback time-out na ongeveer 10 seconden. Als het langer duurt om een beslissing terug te geven, accepteert Roblox de speler.

-

Als de speler vertrekt, of jouw scripts verwijderen ze, voordat hun vertrouwensniveau beschikbaar is, roept Roblox de callback voor die speler niet aan.

#### [Geef een beslissing terug](#geef-een-beslissing-terug)[](#geef-een-beslissing-terug)

Retourneer een tabel met de volgende velden:

| Veld | | Type | | Beschrijving |
| Action | | [Enum.PlayerDeviceTrustDecision](/docs/nl-nl/reference/engine/enums/PlayerDeviceTrustDecision) | | Vereist. Accept  laat de speler in het spel blijven. Reject  verbreekt de verbinding met de speler. |
| Message | | string | | Optioneel. Het bericht dat een geweigerde speler ziet. Als je het weglaat, toont Roblox een standaardbericht dat uitlegt hoe de speler hun apparaat mogelijk kan repareren, op basis van de maatregelen die hun apparaat niet heeft doorstaan. Roblox filtert dit bericht, vervangt het door het standaardbericht als het filteren mislukt, en verkort berichten die te lang zijn. |

Zodat een fout in jouw code nooit spelers buitensluit, accepteert Roblox de speler in elk van de volgende gevallen:

-

Geen enkel script wijst de callback toe.

-

De callback retourneert nil , een waarde die geen tabel is, of een tabel zonder een geldig Action .

-

De callback gooit een fout. Roblox rapporteert de fout zoals elke andere scriptfout.

#### [Reageer op individuele maatregelen](#reageer-op-individuele-maatregelen)[](#reageer-op-individuele-maatregelen)

Het tweede argument van de callback, measures , is een tabel van booleans die het vertrouwensniveau van de speler uitlegt. Een waarde van false  betekent dat het apparaat die maatregel niet heeft doorstaan. Op een apparaat dat een maatregel niet ondersteunt, is de waarde standaard true , dus een waarde van true  bewijst niet dat het apparaat is geslaagd. Wanneer je spelers of functies op een maatregel beperkt, controleer dan alleen of het false  is.

| Maatregel | | Slaag wanneer |
| IsPlatformVersionSecure | | Het besturingssysteem is op of boven de minimumversie die Roblox als veilig beschouwt. |
| IsPlatformBootSecure | | Het besturingssysteem is opgestart in een veilige staat. |
| IsAppSecure | | De Roblox-app is niet gemanipuleerd. |

Gebruik de maatregelen om jouw beleid te verfijnen. Het volgende script weigert spelers op None , weigert ook spelers op Standard  wiens besturingssysteem niet in een veilige staat is opgestart, en accepteert iedereen:

Script in ServerScriptService

```

local IntegrityService = game:GetService("IntegrityService")

IntegrityService.EvaluatePlayerDeviceTrust = function(player, measures)

	local trustLevel = player.DeviceTrustLevel

	local isRejected = trustLevel == Enum.PlayerDeviceTrustLevel.None

		or (trustLevel == Enum.PlayerDeviceTrustLevel.Standard and not measures.IsPlatformBootSecure)

	if isRejected then

		return { Action = Enum.PlayerDeviceTrustDecision.Reject }

	end

	return { Action = Enum.PlayerDeviceTrustDecision.Accept }

end

```

### [Veelvoorkomende fouten](#veelvoorkomende-fouten)[](#veelvoorkomende-fouten)

Vermijd de volgende patronen wanneer je de Device Trust API gebruikt:

-

Vergelijken van vertrouwensniveaus als getallen.  Elk vertrouwensniveau heeft een Value , maar de volgorde van de waarden weerspiegelt niet hoeveel je een apparaat kunt vertrouwen. Unknown  komt voor None , dus een controle dat het vertrouwensniveau van een speler groter is dan None  sluit ook elke speler op Unknown  uit. In plaats daarvan, som de niveaus op die je toestaat, zoals de voorbeelden op deze pagina doen. Als je spelers op Unknown  wilt accepteren, voeg Unknown  dan expliciet toe.

-

Spelers weigeren vanuit [Players.PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded) .  Wanneer PlayerAdded  wordt geactiveerd, is het vertrouwensniveau van de speler meestal nog niet beschikbaar, dus een controle op dat moment kan spelers weigeren wiens apparaten vertrouwd zijn. In plaats daarvan, retourneer Reject  vanuit de [IntegrityService.EvaluatePlayerDeviceTrust](/docs/nl-nl/reference/engine/classes/IntegrityService#EvaluatePlayerDeviceTrust)  callback, die Roblox aanroept zodra het vertrouwensniveau beschikbaar is. Als je het vertrouwensniveau in PlayerAdded  om andere redenen nodig hebt, zoals matchmaking, zie [wacht op het vertrouwensniveau](#wacht-op-het-vertrouwensniveau) .

-

Langzame bewerkingen uitvoeren in de callback.  De callback kan yielden, maar het time-out na ongeveer 10 seconden, en Roblox accepteert dan de speler. Verschillende gegevensopslaglezingen of HTTP-verzoeken kunnen lang genoeg duren om deze limiet te bereiken, dus houd het aantal yield-bewerkingen in de callback tot een minimum.

-

Het vertrouwensniveau op de client lezen.  De eigen client van een speler kan hun vertrouwensniveau lezen, dus je kunt in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  beslissen of je een functie wilt tonen of een remote event wilt activeren. Exploiters controleren hun client en kunnen deze controles omzeilen. In plaats daarvan, lees het vertrouwensniveau op de server en vertel de client welke functies in te schakelen. Baseer client-side wijzigingen, zoals het verbergen van een handelsknop, op wat de server de client vertelt, en controleer altijd het vertrouwensniveau opnieuw op de server voordat de actie plaatsvindt.

-

De maatregelen gebruiken in plaats van het vertrouwensniveau.  Een maatregel is true  wanneer deze niet beschikbaar is op een apparaat, dus een apparaat kan elke maatregel doorstaan zonder volledig vertrouwd te zijn. Behandel een apparaat dat elke maatregel doorstaat niet als Full . Controleer eerst het vertrouwensniveau, en gebruik de maatregelen alleen om te kijken naar controles die zijn mislukt.

### [Test je logica](#test-je-logica)[](#test-je-logica)

Roblox controleert geen apparaten in Studio, dus tijdens playtests blijft het apparaatvertrouwensniveau op Pending  en wordt de callback niet uitgevoerd. Omdat jouw scripts Pending  als niet vertrouwd beschouwen, zijn functies die je op basis van vertrouwensniveau beperkt ook niet beschikbaar tijdens playtests.

Om deze functies te testen en toch jouw beleid te testen, houd je jouw beleid in een functie die het vertrouwensniveau accepteert. Wanneer [RunService:IsStudio()](/docs/nl-nl/reference/engine/classes/RunService#IsStudio)  true  retourneert, sla de vertrouwenscontrole over en roep jouw beleid in plaats daarvan met elk vertrouwensniveau aan. Het volgende script doet dit voor het handelsvoorbeeld in [beperk functies op basis van vertrouwensniveau](#beperk-functies-op-basis-van-vertrouwensniveau) :

Script in ServerScriptService

```

local RunService = game:GetService("RunService")

local IS_STUDIO = RunService:IsStudio()

local TRADE_TRUST_LEVELS = {

	[Enum.PlayerDeviceTrustLevel.Unknown] = true,

	[Enum.PlayerDeviceTrustLevel.Standard] = true,

	[Enum.PlayerDeviceTrustLevel.Full] = true,

}

local function isTradeAllowed(trustLevel: Enum.PlayerDeviceTrustLevel): boolean

	return TRADE_TRUST_LEVELS[trustLevel] == true

end

-- Controleer dit op de server voordat elke handel plaatsvindt

local function canTrade(player: Player): boolean

	-- Roblox controleert geen apparaten in Studio, dus sta handelen toe tijdens playtests

	if IS_STUDIO then

		return true

	end

	return isTradeAllowed(player.DeviceTrustLevel)

end

-- In Studio, print hoe jouw beleid omgaat met elk vertrouwensniveau

if IS_STUDIO then

	for _, trustLevel in Enum.PlayerDeviceTrustLevel:GetEnumItems() do

		print(trustLevel.Name, isTradeAllowed(trustLevel))

	end

end

```

## [Beperkingen](#beperkingen)[](#beperkingen)

Apparaatvertrouwen verhoogt de kosten van cheaten, maar het is geen complete oplossing:

-

Het vervangt geen veilig spelontwerp.  Exploits die afhankelijk zijn van zwakke server-side validatie, zoals het vertrouwen op posities, scores of valuta die door de client worden gerapporteerd, werken nog steeds op vertrouwde apparaten. Valideer belangrijke acties op de server, zoals beschreven in [beveiliging van de client-servergrens](/docs/nl-nl/scripting/security/client-server-boundary) .

-

Het vermindert cheaten, maar elimineert het niet.  Cheatontwikkelaars passen zich in de loop van de tijd aan, dus beschouw apparaatvertrouwen als een laag van jouw verdedigingen naast [server-side detectie](/docs/nl-nl/scripting/security/server-side-detection) .

-

Niet elk platform wordt ondersteund.  Voor details, zie [ondersteunde platforms](#ondersteunde-platforms) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
