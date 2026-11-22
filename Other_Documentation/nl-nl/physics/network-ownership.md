<!-- Source: https://create.roblox.com/docs/nl-nl/physics/network-ownership -->

Netwerkbezit | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Fysica](/docs/nl-nl/physics)

# Netwerkbezit

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Om complexe fysieke mechanismen te ondersteunen en tegelijkertijd te streven naar een soepele en responsieve ervaring voor spelers, maakt de Roblox [fysica](/docs/nl-nl/physics)  engine gebruik van een gedistribueerd fysicasysteem  waarin berekeningen worden verdeeld tussen de server en alle verbonden clients. Binnen dit systeem wijst de engine netwerkbezit  van fysiek gesimuleerde [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  toe aan een client of server om het werk van het berekenen van fysica te verdelen.

Clients ervaren meer responsieve  fysica-interacties met onderdelen die zij bezitten, aangezien er geen vertraging is door communicatie met de server. Netwerkbezit verbetert ook de serverprestaties omdat fysica-berekeningen kunnen worden verdeeld over individuele clients, waardoor de server andere taken kan prioriteren.

## [BasePart bezit](#basepart-bezit)[](#basepart-bezit)

Standaard behoudt de server het bezit van elke [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) . Bovendien bezit de server altijd  verankerde [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  en je kunt hun bezit niet handmatig wijzigen.

Op basis van de hardwarecapaciteit van een client en de nabijheid van de [Player.Character](/docs/nl-nl/reference/engine/classes/Player#Character)  van de speler tot een onverankerde [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , wijst de engine automatisch het bezit van dat onderdeel toe aan de client. Dergelijke onderdelen die dicht bij het personage van een speler zijn, hebben een grotere kans om speler-bezit te worden.

## [Assemblagebezit](#assemblagebezit)[](#assemblagebezit)

Als een fysica-gebaseerd mechanisme geen verankerde onderdelen heeft, [het instellen van bezit](#bezit-instellen)  op een [assemblage](/docs/nl-nl/physics/assemblies)  binnen dat mechanisme stelt hetzelfde bezit in voor elke assemblage  in het mechanisme.

Als je een enkele assemblage verankert die geen  deel uitmaakt van een breder mechanisme, gaat het bezit naar de server, aangezien de server altijd verankerde [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  bezit. Bij het onverankeren van dezelfde assemblage gaat de vorige bezitstoestand verloren en wordt het automatisch beheerd door de engine.

Als je een assemblage verankert binnen een breder mechanisme van assemblages, gaat het bezit naar de server, maar het bezit van de andere assemblages blijft ongewijzigd. Het onverankeren van dezelfde assemblage herstelt het eerder ingestelde bezit.

## [Bezit instellen](#bezit-instellen)[](#bezit-instellen)

In games met complexe fysica-interacties of in gevallen waarin je directe controle moet toewijzen, kun je het bezit instellen via een server-side aanroep naar [BasePart:SetNetworkOwner()](/docs/nl-nl/reference/engine/classes/BasePart#SetNetworkOwner) .

Hoewel je handmatig [SetNetworkOwner(nil)](/docs/nl-nl/reference/engine/classes/BasePart#SetNetworkOwner)  voor de server kunt aanroepen voor gameplay-kritieke objecten die de client niet zou moeten kunnen manipuleren, moet je dit voorzichtig doen, aangezien het kan leiden tot schokkerige fysica-interacties voor clients.

 Houd er ook rekening mee dat de server altijd  verankerde [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  bezit en je hun bezit niet handmatig kunt wijzigen.

Overweeg een voertuig dat een [VehicleSeat](/docs/nl-nl/reference/engine/classes/VehicleSeat)  object heeft voor de bestuurder en een [Seat](/docs/nl-nl/reference/engine/classes/Seat)  object voor een passagier, waarbij beide zijn opgenomen in de voertuigassemblage. Met de standaardbezitregels, als een spelerpersonage in de [Seat](/docs/nl-nl/reference/engine/classes/Seat)  (passagier) gaat zitten en vervolgens een andere speler in de [VehicleSeat](/docs/nl-nl/reference/engine/classes/VehicleSeat)  (bestuurder) springt, krijgt de passagier  fysiek bezit van het hele voertuig omdat zij als eerste zijn ingestapt. De bestuurder moet enkele netwerkcycli wachten voordat hun invoer wordt herkend en het voertuig zal minder responsief aanvoelen.

De volgende [Script](/docs/nl-nl/reference/engine/classes/Script)  lost dit op door handmatig netwerkbezit toe te wijzen aan de bestuurder. Hierin stelt de [VehicleSeat](/docs/nl-nl/reference/engine/classes/VehicleSeat)  zijn [Occupant](/docs/nl-nl/reference/engine/classes/VehicleSeat#Occupant)  in op de [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  die erop zit, zodat het script luistert naar het [Changed](/docs/nl-nl/reference/engine/classes/Instance#Changed)  evenement van de stoel om te detecteren wanneer een speler in de stoel gaat zitten. Wanneer de bestuurder de stoel verlaat, wordt het netwerkbezit van het voertuig teruggezet naar automatisch met [BasePart:SetNetworkOwnershipAuto()](/docs/nl-nl/reference/engine/classes/BasePart#SetNetworkOwnershipAuto) .

```

local Players = game:GetService("Players")

local vehicleSeat = script.Parent

vehicleSeat.Changed:Connect(function(prop)

	if prop == "Occupant" then

		local humanoid = vehicleSeat.Occupant

		if humanoid then

			-- Verkrijg de speler van het personage

			local player = Players:GetPlayerFromCharacter(humanoid.Parent)

			if player then

				vehicleSeat:SetNetworkOwner(player)

			end

		else

			-- Reset bezit wanneer de stoel niet bezet is

			vehicleSeat:SetNetworkOwnershipAuto()

		end

	end

end)

```

Voor soepele prestaties en responsief gedrag, zorg ervoor dat je ook het bezit van losse [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  bovenop een voertuig toewijst aan dezelfde client die het voertuig bestuurt.

## [Bezit visualiseren](#bezit-visualiseren)[](#bezit-visualiseren)

Om te helpen bij het debuggen van netwerkbezit, kan Studio gekleurde omtrekken rond objecten renderen tijdens het testen.

| Omtrek kleur | | Beschrijving |
| --- | --- |
|  | | (groen) | | Jouw client bezit het onderdeel en simuleert het. |
|  | | (rood) | | Het onderdeel bevindt zich in een "bufferzone" waar jouw client het simuleert, maar het nog steeds door iets anders wordt bezeten. Jouw client kan na dit bezit krijgen, of het kan worden afgewezen. |
|
 | | (wit/grijs) | | Server of een andere client bezit het onderdeel via automatisch netwerkbezit of door expliciete toewijzing via [part:SetNetworkOwner()](/docs/nl-nl/reference/engine/classes/BasePart#SetNetworkOwner) . |
|  | | (zwart) | | Het onderdeel is door noch de server, noch de client bezeten. Fysica zal niet van toepassing zijn op dit onderdeel. |

Houd er rekening mee dat in een [multi-client simulatie](/docs/nl-nl/studio/testing-modes#multi-client-simulatie) , elke client een unieke kleur toegewezen krijgt om hun bezit aan te geven; dit wordt weerspiegeld in de [Server](/docs/nl-nl/studio/testing-modes#schakel-clientserver)  weergave, wat je helpt te bepalen welke client welke onderdeel(en) op elk moment bezit.

Om de visualisatie van netwerkbezit in te schakelen:

1.

Klik op de visualisatie-opties  knop in de rechterbovenhoek van het 3D-venster.

 ![Een close-up van het 3D-venster met de Visualisatie-opties knop aangegeven in de rechterbovenhoek.](https://prod.docsiteassets.roblox.com/assets/studio/general/Visualization-Options.png)

2.

Schakel in het dropdownmenu Netwerkbezitters  in.

## [Beveiligingszorgen](#beveiligingszorgen)[](#beveiligingszorgen)

Roblox kan fysica-berekeningen niet verifiëren wanneer een client bezit heeft over een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) . Clients kunnen dit misbruiken en slechte gegevens naar de server sturen, zoals het teleporteren van de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , waardoor deze door muren gaat of rondvliegt.

Bovendien zijn [BasePart.Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  evenementen gekoppeld aan netwerkbezit, wat betekent dat een client [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  evenementen kan afvuren op een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  die het bezit en dit naar de server kan sturen, zelfs als de server het niet ziet aanraken. Bijvoorbeeld, een client kan een zwaard schade toebrengen aan een andere speler aan de andere kant van de kaart door het evenement via scriptinjecties af te vuren, dus het is belangrijk om de geldigheid van dergelijke evenementen die door clients zijn afgevuurd te controleren.

Zie [Beveiligingstactieken en Cheat Mitigatie](/docs/nl-nl/scripting/security/security-tactics)  voor gedetailleerde beveiligingstactieken en cheat mitigatie tactieken voor Roblox-games.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
