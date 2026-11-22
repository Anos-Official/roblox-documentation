<!-- Source: https://create.roblox.com/docs/nl-nl/matchmaking/attributes-and-signals -->

Attributen en signalen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Matchmaking](/docs/nl-nl/matchmaking)

# Attributen en signalen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

## [Bestaande attributen](#bestaande-attributen)[](#bestaande-attributen)

De standaard Roblox matchmaking-configuratie gebruikt signalen op basis van bestaande attributen zoals spelerslocatie, leeftijdsgroep en latentie.

Om gegevens voor matchmaking te gebruiken die Roblox niet automatisch in zijn standaardconfiguratie opneemt, moet je [aangepaste attributen](#aangepaste-attributen)  en [aangepaste signalen](#aangepaste-signalen)  maken.

| Attribuut | | Type | | Beschrijving |
| --- | --- |
| Geschatte Speler Latentie | | Numeriek | | De geschatte latentie van een speler in een server. |
| Heeft Vrienden | | Categorisch | | Of een server een vriend of een andere speler met hetzelfde IP-adres als de toetredende speler heeft. |
| Is Spraakchat Ingeschakeld | | Categorisch | | Of een speler spraakchat heeft ingeschakeld. |
| Speler Leeftijd | | Numeriek | | De leeftijd van de speler. |
| Speler Apparaat Type | | Categorisch | | Het apparaattype van de speler. Kan een mobiel apparaat, een computer, een tablet, een console of een VR-apparaat zijn. |
| Speler Taal | | Categorisch | | De taal van de speler. |
| Speler Speelgeschiedenis | | Numeriek | | Het log-10 aantal minuten dat een speler in een universum heeft gespeeld in de afgelopen 28 dagen. |
| Server Bezetting | | Numeriek | | Het aantal spelers in een server. |
| Speler Tekstchat Groep | | Categorisch | | De tekstchatgroep van de speler waar ze samen kunnen chatten. |

## [Bestaande signalen](#bestaande-signalen)[](#bestaande-signalen)

De volgende zijn door Roblox gedefinieerde signalen die zijn afgeleid op basis van Roblox-attributen:

| Signaal | | Beschrijving |
| [Leeftijd](#leeftijd) | | Het verschil tussen de gemiddelde leeftijd van spelers in de server en de leeftijd van de toetredende speler, met een maximale relevante verschil van 25. |
| [Apparaat Type](#apparaat-type) | | De verhouding van spelers in de server met hetzelfde apparaattype als de toetredende speler. |
| [Vrienden](#vrienden) | | Het aantal mensen in de server die vrienden zijn met de toetredende speler of die een IP-adres delen met de toetredende speler. 1 als er een voorkeurs speler is, 0 anders. |
| [Latentie](#latentie) | | De delta ping van de toetredende speler voor een server, wat de geschatte ping is boven de laagste ping die de speler zou kunnen bereiken op hun beste bereikbare datacenter, met een maximale relevante waarde van 100. |
| [Taal](#taal) | | De verhouding van spelers in de server met dezelfde taal als de toetredende speler. |
| [Bezetting](#bezetting) | | De verhouding van spelers in de server vergeleken met de capaciteit van de server. |
| [Speelgeschiedenis](#speelgeschiedenis) | | Het verschil tussen de gemiddelde speelgeschiedenis in de server en de speelgeschiedenis van de toetredende speler, met een maximale relevante verschil van 4.6. |
| [Spraakchat](#spraakchat) | | De verhouding van spelers in de server met spraakchat ingeschakeld. |
| [Tekstchat](#tekstchat) | | De verhouding van spelers in de server die samen met de toetredende speler kunnen chatten. |

### [Leeftijd](#leeftijd)[](#leeftijd)

Een numeriek signaal dat de gemiddelde leeftijden van spelers op een server vergelijkt met de leeftijd van de toetredende speler. Dit signaal heeft een maximale relevante verschil van 25. De signaalscore is omgekeerd gerelateerd aan het leeftijdsverschil, wat betekent dat lagere leeftijdsverschillen hogere scores hebben.

ageDifferenceSignalScore = 1 − min ⁡ (25 , ageDifference ) / 25 \text{ageDifferenceSignalScore} = 1 - \min(25, \text{ageDifference}) / 25 ageDifferenceSignalScore = 1 − min (25 , ageDifference ) /25

waar

ageDifference = ∣ avgServerAge − joiningPlayerAge ∣ \text{ageDifference} = |\text{avgServerAge} - \text{joiningPlayerAge}|ageDifference = ∣ avgServerAge − joiningPlayerAge ∣

### [Apparaat Type](#apparaat-type)[](#apparaat-type)

Een categorisch signaal dat de verhouding van spelers op de server meet met hetzelfde apparaattype als de toetredende speler. Apparaat types omvatten: Computer, mobiel apparaat, tablet, console en VR-apparaat.

deviceTypeSignalScore = # spelers met hetzelfde apparaat als toetredende speler / # spelers op de server \text{deviceTypeSignalScore} = \text{\# spelers met hetzelfde apparaat als toetredende speler} / \text{\# spelers op de server} deviceTypeSignalScore = # spelers met hetzelfde apparaat als toetredende speler / # spelers op de server

### [Vrienden](#vrienden)[](#vrienden)

Een voorkeurs speler is een speler die ofwel vrienden is met de toetredende speler of die hetzelfde IP-adres deelt als de toetredende speler. Het Vrienden signaal is een categorisch signaal met een score van 1 wanneer er een voorkeurs speler in de server is en een score van 0 wanneer er geen voorkeurs spelers op de server zijn.

friendsSignalScore = hasFriends ?  1 : 0 \text{friendsSignalScore} = \text{hasFriends} \ {?} \ 1 : 0 friendsSignalScore = hasFriends  ?  1 : 0

Het Vrienden signaal kan ook worden beschouwd als een numeriek signaal met een maximale relevante waarde van 1.

friendsSignalScore = min ⁡ (# voorkeurs spelers in server , 1 ) / 1 \text{friendsSignalScore} = \min(\text{\# voorkeurs spelers in server}, 1) / 1 friendsSignalScore = min (# voorkeurs spelers in server , 1 ) /1

### [Taal](#taal)[](#taal)

Een categorisch signaal dat de verhouding van spelers op de server meet die dezelfde taalinstelling hebben als de toetredende speler.

languageSignalScore = # spelers met dezelfde taalinstelling als toetredende speler / # spelers op de server \text{languageSignalScore} = \text{\# spelers met dezelfde taalinstelling als toetredende speler} / \text{\# spelers op de server} languageSignalScore = # spelers met dezelfde taalinstelling als toetredende speler / # spelers op de server

### [Latentie](#latentie)[](#latentie)

Een numeriek signaal dat de delta ping van de toetredende speler in milliseconden meet als ze op een server zouden spelen, wat de geschatte ping is boven de laagste ping die de speler zou kunnen bereiken op hun beste bereikbare datacenter. Dit signaal heeft een maximale relevante waarde van 100 milliseconden. De signaalscore is omgekeerd gerelateerd aan de delta ping, wat betekent dat lagere delta ping waarden hogere scores hebben.

latencySignalScore = 1 − min ⁡ (100 , deltaPingMs ) / 100 \text{latencySignalScore} = 1 - \min(100, \text{deltaPingMs}) / 100 latencySignalScore = 1 − min (100 , deltaPingMs ) /100

### [Bezetting](#bezetting)[](#bezetting)

Een numeriek signaal dat de verhouding van spelers op de server tot de capaciteit van de server meet.

occupancySignalScore = # spelers in server / serverCapacity \text{occupancySignalScore} = \text{\# spelers in server} / \text{serverCapacity} occupancySignalScore = # spelers in server / serverCapacity

### [Speelgeschiedenis](#speelgeschiedenis)[](#speelgeschiedenis)

De waarde van het Speelgeschiedenis attribuut is het log-10 aantal minuten dat een speler in een universum heeft gespeeld in de afgelopen 28 dagen. Dit numerieke signaal vergelijkt de gemiddelde log-10 Speelgeschiedenis waarde van spelers in de server met de Speelgeschiedenis waarde van de toetredende speler. Dit signaal heeft een maximale relevante verschil van 4.6. De signaalscore is omgekeerd gerelateerd aan het speelgeschiedenis verschil, wat betekent dat lagere speelgeschiedenis verschillen hogere scores hebben.

playHistorySignalScore = 1 − min ⁡ (4.6 , playHistoryDifference / 4.6 ) \text{playHistorySignalScore} = 1 - \min(4.6, \text{playHistoryDifference} / 4.6) playHistorySignalScore = 1 − min (4.6 , playHistoryDifference /4.6 ) , waar

playHistoryDifference = ∣ avgServerPlayHistory − joiningPlayerPlayHistory ∣ \text{playHistoryDifference} = |\text{avgServerPlayHistory} - \text{joiningPlayerPlayHistory}|playHistoryDifference = ∣ avgServerPlayHistory − joiningPlayerPlayHistory ∣

### [Spraakchat](#spraakchat)[](#spraakchat)

Een speler kan spraakchat ingeschakeld of uitgeschakeld hebben. Het Spraakchat signaal is een categorisch signaal dat de verhouding van spelers meet met dezelfde spraakchatinstelling als de toetredende speler ten opzichte van het aantal spelers in de server.

Als een plaats spraakchat heeft uitgeschakeld, is het gewicht van het Spraakchat signaal 0.

voiceChatSignalScore = # spelers met dezelfde spraakchatinstelling als toetredende speler / # spelers op de server \text{voiceChatSignalScore} = \text{\# spelers met dezelfde spraakchatinstelling als toetredende speler} / \text{\# spelers op de server} voiceChatSignalScore = # spelers met dezelfde spraakchatinstelling als toetredende speler / # spelers op de server

### [Tekstchat](#tekstchat)[](#tekstchat)

Een categorisch signaal dat de verhouding van spelers op de server meet die samen met de toetredende speler kunnen chatten.

textChatSignalScore = # spelers kunnen chatten met de toetredende speler in gemeenschappelijk / # spelers op de server \text{textChatSignalScore} = \text{\# spelers kunnen chatten met de toetredende speler in gemeenschappelijk } / \text{\# spelers op de server} textChatSignalScore = # spelers kunnen chatten met de toetredende speler in gemeenschappelijk / # spelers op de server

## [Aangepaste attributen](#aangepaste-attributen)[](#aangepaste-attributen)

Aangepaste attributen geven aangepaste signalen toegang tot speler- en servergegevens. Voor meer informatie over het maken van je eigen aangepaste attributen, zie [Maak een aangepast attribuut](/docs/nl-nl/matchmaking/customize-matchmaking#maak-een-aangepast-attribuut) . Voor meer informatie over bestaande Roblox-attributen, zie [Bestaande attributen](#bestaande-attributen) .

| Attribuut | | Kenmerken |
| Speler | | Persistent
 Aangepaste spelergegevens die persistent zijn in gegevensopslag, zoals het niveau of de score van een speler in het spel
 Beheerd met behulp van de [DataStore](/docs/nl-nl/reference/engine/classes/DataStore)  API's |
| Server | | Niet persistent en blijft alleen bestaan zolang de server actief is
 Server-specifieke gegevens zoals het serverniveau of de gamemodus
 Beheerd met behulp van de [MatchmakingService](/docs/nl-nl/reference/engine/classes/MatchmakingService)  API |

Voorbeeld van spelerattribuut

```

local DataStoreService = game:GetService("DataStoreService")

local eloStore = DataStoreService:GetDataStore("PlayerElo")

function onMatchEnded(players: {Player}, winners: {Player}, losers: {Player})

	for _, player in players do

		local updatedElo = CalculateUpdatedElo(player, winners, losers)

		local success, errorMessage = pcall(function()

			eloStore:SetAsync(player.UserId, updatedElo)

		end)

	end

end

```

Voorbeeld van serverattribuut

```

local MatchmakingService = game:GetService("MatchmakingService")

local RunService = game:GetService("RunService")

if RunService:IsStudio() then

	-- Stelt initiële attributen en schema in voor testen

	MatchmakingService:InitializeServerAttributesForStudio({

		Level = "Geavanceerd",

		Elo = 123.456,

		TrainingMode = true

	})

end

-- Haalt het Level attribuut op

local currentLevel, errorMessage = MatchmakingService:GetServerAttribute("Level")

if errorMessage then

	warn(errorMessage)

else

	print("Huidig niveau: " .. currentLevel)

end

-- Werk de waarde van het Level attribuut bij naar Geavanceerd

local success, errorMessage = MatchmakingService:SetServerAttribute("Level", "Geavanceerd")

if not success then

	warn("Kon serverattribuut [Level] niet bijwerken naar [Geavanceerd] vanwege fout: " .. errorMessage)

else

	print("Met succes [Level] ingesteld op [Geavanceerd]")

end

```

## [Aangepaste signalen](#aangepaste-signalen)[](#aangepaste-signalen)

Aangepaste signalen worden door jou gemaakt en gedefinieerd en kunnen numeriek of categorisch zijn:

-

Numerieke signalen zijn getallen. Ze vergelijken het verschil tussen het attribuut van de toetredende speler en de geaggregeerde waarde van de server, waarbij grotere verschillen de score verlagen of verhogen. Bijvoorbeeld, hoe dichter het vaardigheidsniveau van een speler bij het gemiddelde vaardigheidsniveau van de server ligt, hoe hoger de score van het numerieke signaal is. Deze score wordt vervolgens vermenigvuldigd met het gewicht van het signaal.

-

Categorische signalen zijn strings of booleans. Ze zijn gebaseerd op hoe gebruikelijk het attribuut van de toetredende speler is in vergelijking met de andere spelers in de server. Bijvoorbeeld, als een hoog percentage van de spelers in een server dezelfde voorkeurstaal heeft als de toetredende speler, neemt de score toe. Deze score wordt ook vermenigvuldigd met het gewicht van het signaal.

Voor meer informatie over het maken van je eigen aangepaste signalen, zie [Maak een aangepast signaal](/docs/nl-nl/matchmaking/customize-matchmaking#maak-een-aangepast-signaal) . Voor meer informatie over bestaande Roblox-signalen, zie [Bestaande signalen](#bestaande-signalen) .

### [Speler numeriek](#speler-numeriek)[](#speler-numeriek)

##### Toetredende speler

Minimaliseert het verschil tussen het gemiddelde spelerattribuut van de server en het attribuut van de toetredende speler. Verschillen groter dan 1000 geven een signaalscore van 0 terug.

Formule voor toetredende speler voor speler numeriek signaal

```

local diff = math.abs(server_{aggregation_function}_{attribute_name} - joining_player_{attribute_name})

local score = 1 - math.min(diff / max_relevant_difference, 1)

return score

```

Voorbeeld van toetredende speler voor speler numeriek signaal

```

local server_average_Elo = 2000

local joining_player_Elo = 1000

local max_relevant_difference = 1500

local diff = math.abs(server_average_Elo - joining_player_Elo)

local score = 1 - math.min(diff / max_relevant_difference, 1)

return score

```

##### Constante waarde

Minimaliseert het verschil tussen het gemiddelde spelerattribuut van de server en een constante waarde van 500. Verschillen groter dan 1000 geven een signaalscore van 0 terug.

Formule voor constante waarde voor speler numeriek signaal

```

local diff = math.abs(server_sum_{attribute_name} + joining_player_{attribute_name} - constant_value)

local score = 1 - math.min(diff / max_relevant_difference, 1)

return score

```

Voorbeeld van constante waarde voor speler numeriek signaal

```

local server_sum_PowerLevel = 4500

local joining_player_PowerLevel = 9901

local max_relevant_difference = 1500

local constant_value = 5000

local diff = math.abs(server_sum_PowerLevel + joining_player_PowerLevel - constant_value)

local score = 1 - math.min(diff / max_relevant_difference, 1)

```

### [Speler categorisch](#speler-categorisch)[](#speler-categorisch)

##### Clustering

Maximaliseert de verhouding van spelers in de server die hetzelfde attribuut hebben als het attribuut van de toetredende speler.

Formule voor clustering voor speler categorisch signaal

```

local score = num_players_same_{attribute_name} / occupancy

return score

```

Voorbeeld van clustering voor speler categorisch signaal

```

local num_players_same_Guild = 15

local occupancy = 19

local score = num_players_same_Guild / occupancy

return score

```

##### Diversifiëren

Maximaliseert de verhouding van spelers in de server die een ander attribuut hebben dan het attribuut van de toetredende speler.

Formule voor diversifiëren voor speler categorisch signaal

```

local score = num_players_same_{attribute_name} / occupancy

return 1 - score

```

Voorbeeld van diversifiëren voor speler categorisch signaal

```

local num_players_same_RpgClass = 15

local occupancy = 19

local score = num_players_same_RpgClass / occupancy

return score

```

### [Server numeriek](#server-numeriek)[](#server-numeriek)

##### Toetredende speler

Minimaliseert het verschil tussen het attribuut van de server en het attribuut van de toetredende speler. Verschillen groter dan 1000 geven een signaalscore van 0 terug.

Formule voor toetredende speler voor server numeriek signaal

```

local diff = math.abs(server_{attribute_name} - joining_player_{attribute_name})

local score = 1 - math.min(diff / max_relevant_difference, 1)

return score

```

Voorbeeld van toetredende speler voor server numeriek signaal

```

local server_Level = 4500

local joining_player_Level = 9000

local max_relevant_difference = 1500

local diff = math.abs(server_Level - joining_player_Level)

local score = 1 - math.min(diff / max_relevant_difference, 1)

```

##### Constante waarde

Minimaliseert het verschil tussen de waarde van het serverattribuut en een constante waarde. Verschillen groter dan deze constante waarde geven een signaalscore van 0 terug.

Formule voor constante waarde voor server numeriek signaal

```

local diff = math.abs(server_{attribute_name} - constant_value)

local score = math.min(diff / max_relevant_difference, 1)

return score

```

Voorbeeld van constante waarde voor server numeriek signaal

```

local server_GameTime = 500

local max_relevant_difference = 1000

local constant_value = 1000

local diff = math.abs(server_GameTime - constant_value)

local score = math.min(diff / max_relevant_difference, 1)

```

### [Server categorisch](#server-categorisch)[](#server-categorisch)

##### Vergelijken met toetredende speler

De score is 1 wanneer de waarde van het serverattribuut (bijvoorbeeld, Gamemodus) gelijk is aan de waarde van het attribuut van de speler (bijvoorbeeld, Voorkeurs Gamemodus). Anders is de signaalscore 0.

Formule voor toetredende speler voor server categorisch signaal

```

if server_{attribute_name} == joining_player_{attribute_name} then

	return 1

else

	return 0

end

```

Voorbeeld van toetredende speler voor server categorisch signaal

```

local server_GameMode = "Survival"

local joining_player_GameMode = "Survival"

if server_GameMode == joining_player_GameMode then

	return 1

else

	return 0

end

```

##### Vergelijken met constante waarde

De score is 1 wanneer de waarde van het serverattribuut gelijk is aan een constante waarde van waar. Anders is de signaalscore 0.

Formule voor constante waarde voor server categorisch signaal

```

if server_{attribute_name} == constant_value then

	return 1

else

	return 0

end

```

Voorbeeld van constante waarde voor server categorisch signaal

```

local server_GameNotStarted = true

if server_GameNotStarted == true then

	return 1

else

	return 0

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
