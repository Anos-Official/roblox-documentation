<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/security/server-side-detection -->

Server-side detectie en consequenties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. Beveiliging

# Server-side detectie en consequenties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De volgende inhoud behandelt verschillende concepten en tactieken om de beveiliging te verbeteren en valsspelen in je Roblox-spellen te verminderen. Het wordt ten zeerste aanbevolen dat alle ontwikkelaars deze doornemen om ervoor te zorgen dat je spellen veilig en eerlijk zijn voor alle gebruikers. Bekijk de zijbalk voor aanvullende beveiligingsthema's.

Deze sectie gaat ervan uit dat je al invoer en context valideert (zie eerdere secties). Dit artikel behandelt wat te doen nadat een verzoek technisch geldig is, maar het gedrag misbruik lijkt, plus hoe te reageren zonder legitieme spelers te schaden.

## [Filosofie](#filosofie)[](#filosofie)

-

De server beslist . Detectie en consequenties vinden plaats op de server. Probeer nooit te verbannen op basis van client-side detecties, aangezien exploiters deze gemakkelijk kunnen omzeilen.

-

Voorkom eerst schade . Neutraliseer stilletjes de impact van een exploit. Als een speler bijvoorbeeld speed-hacks gebruikt, breng ze dan gewoon terug naar hun laatste geldige positie in plaats van ze onmiddellijk te schoppen. Straf alleen wanneer nodig om het spel of andere spelers te beschermen.

-

Wees proportioneel en omkeerbaar . Ga ervan uit dat valse positieven kunnen voorkomen. Geef de voorkeur aan acties die je kunt terugdraaien, zoals tijdelijke schorsingen of het verwijderen van middelen, boven permanente verbannen.

-

Ontwerp > detectie . Je primaire beveiliging komt van robuuste validatie en snelheidsbeperkingen (behandeld in [Beveiligen van de client-server grens](/docs/nl-nl/scripting/security/client-server-boundary)  en andere secties). De detectiemethoden hieronder zijn bedoeld om die verdedigingen aan te vullen, niet om ze te vervangen.

## [Heuristieken](#heuristieken)[](#heuristieken)

Heuristieken zijn gedragscontroles die acties markeren die technisch mogelijk zijn, maar zeer onwaarschijnlijk voor een legitieme speler. Het zijn "vuistregels" voor het opvangen van verdachte activiteiten die door basisvalidatie glippen. Een effectieve heuristiek vergelijkt de actie van een speler met een theoretisch maximum of een redelijke basislijn.

Bijvoorbeeld, als een speler plotseling beweert 1 miljard munten te hebben verdiend in je simulator-spel, kan je externe validatie bevestigen dat het verzoek correct is gestructureerd. Maar een heuristische controle op de server zou weten dat het verdienen van zoveel weken zou moeten duren, niet seconden, en de transactie als verdacht markeren.

Hier zijn drie klassieke voorbeelden van server-side heuristieken. Elk valideert het gedrag van de speler tegen de regels en fysieke beperkingen van het spel, waardoor een sterke verdediging tegen veelvoorkomende exploits ontstaat.

| Server-side heuristiek | | Beschrijving | | Voorbeeld |
| --- | --- |
| Snelste Voltooiingstijd | | Bereken de theoretisch snelst mogelijke tijd om een taak te voltooien, zoals een obstakelbaan. Dit houdt in dat je het optimale pad vindt en de maximale snelheid van de speler aanneemt. | | In een obby, als het wereldrecord 30 seconden is, is een voltooiingstijd van 5 seconden een sterk signaal van teleportatie of snelheidsexploits. |
| Snelheid van Verzameling | | Volg de maximale legitieme snelheid waarmee een speler een hulpbron (valuta, ervaring, items) kan verdienen. | | Als een speler legitiem 100 munten per minuut kan verdienen, zou een plotselinge winst van 10.000 munten in één seconde gemarkeerd moeten worden. |
| Actie Cadans | | De server analyseert de tijdsintervallen tussen de herhaalde acties van een speler. Menselijke invoer heeft natuurlijke, lichte variaties in timing, terwijl eenvoudige automatiseringsscripts (zoals auto-clickers) vaak acties met robotachtige consistentie uitvoeren. | | In een visminigame klikt een speler om hun lijn uit te werpen. De server registreert de tijdstempel van elke worp. Als de speler hun lijn 100 keer achter elkaar werpt met exact hetzelfde interval (bijv. precies 2,500 seconden) tussen elke actie, is dat een sterk teken van een macro of bot. De timing van een mens zou natuurlijk fluctueren. |

Een van deze voorbeelden alleen is misschien niet genoeg om een cheater te veroordelen. Elk moet worden behandeld als een signaal, niet als definitief bewijs. Een goede praktijk is om een verdenkingsscore te implementeren. Wanneer een speler een heuristische controle niet doorstaat, verhoog je hun score. Ernstige acties zoals schoppen of verbannen zouden alleen moeten plaatsvinden nadat meerdere, gevarieerde detecties de score van een speler boven een hoge drempel hebben geduwd.

Bijvoorbeeld, stel dat een bekwame speler je obby voltooit met een recordtijd, wat je "Snelste Voltooiingstijd" heuristiek activeert. Moeten ze worden verbannen? Het is mogelijk dat ze valsspelen, maar ze hebben misschien ook een legitieme maar onbedoelde snelkoppeling ontdekt. Ze verbannen op basis van dit enkele signaal zou riskant zijn en een van je meest toegewijde spelers kunnen straffen.

Als diezelfde speler echter ook de "Actie Cadans" heuristiek activeert voor onmenselijk consistente invoer, en een uur later de "Snelheid van Verzameling" heuristiek in je lobby activeert, wordt de zaak veel sterker. De combinatie van deze verschillende signalen schetst een veel betrouwbaarder beeld van valsspelen. De kracht van dit systeem ligt in het correlateren van meerdere gegevenspunten om een zelfverzekerde zaak op te bouwen voordat je actie onderneemt.

## [Honeypots](#honeypots)[](#honeypots)

Een manier om cheaters te detecteren die proberen je game's RemoteEvents te onderzoeken, is door een lokaas te gebruiken dat een honeypot wordt genoemd. Een honeypot is een [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent)  of [RemoteFunction](/docs/nl-nl/reference/engine/classes/RemoteFunction)  die legitiem lijkt voor een exploiter, maar nooit door een van je legitieme client-scripts wordt gebruikt. Omdat geen normale speler ooit deze remote zou moeten kunnen activeren, moet al het verkeer dat het ontvangt van een exploiter komen. Wanneer de server detecteert dat deze remote wordt geactiveerd, is dat een zeer hoog-signaal dat de client zich ermee bemoeit. De beste onmiddellijke actie is om het voorval te loggen en de speler uit de sessie te schoppen.

Een andere variant is om RemoteEvents te ontwerpen met specifieke richtingen - sommige uitsluitend voor client → server communicatie en andere uitsluitend voor server → client communicatie. Hoewel de evenementnamen hun bedoelde richting niet onthullen, houdt de server bij in welke richting elke remote moet worden gebruikt. Als een exploiter probeert een server → client remote vanuit de client te activeren, dient dit als een betrouwbare detectiemethode, aangezien legitiem spel nooit communicatie in de verkeerde richting zou activeren.

## [Toepassen van consequenties](#toepassen-van-consequenties)[](#toepassen-van-consequenties)

Wanneer detectiesystemen verdacht gedrag markeren, overweeg dan je responsstrategie zorgvuldig. Verschillende spellen vereisen verschillende benaderingen op basis van hun gemeenschap, competitieve inzet en tolerantie voor verstoring.

De consequentieladder  - De meeste spellen profiteren van escalatie van reacties in plaats van direct naar permanente verbannen te springen:

-

Stille logging  - Bouw bewijs op zonder impact op de speler

-

Stille mitigatie  - Blokkeer het effect van de exploit (verzoek afwijzen, waarden beperken, correcte status synchroniseren)

-

Tijdelijke beperkingen  - Beperk specifieke mogelijkheden (ruilen, ranglijsten, matchmaking)

-

Zichtbare handhaving  - Schoppen, tijdelijke schorsingen of permanente verbannen

Overwegingen voor je strategie

-

Vertraag zichtbare consequenties  om te voorkomen dat exploiters precies leren wat de detectie heeft geactiveerd

-

Stem de ernst af op de reactie  - kleine economische exploits kunnen een andere behandeling vereisen dan spelbrekende fysica cheats

-

Overweeg je gemeenschap  - competitieve spellen hebben mogelijk strengere handhaving nodig dan casual spellen

-

Plan voor fouten  - geef de voorkeur aan omkeerbare acties wanneer de detectiebetrouwbaarheid lager is

Voor hardnekkige overtreders, overweeg het gebruik van de [Ban API](/docs/nl-nl/reference/engine/classes/Players#BanAsync)  in plaats van alleen op schoppen te vertrouwen. De Ban API voorkomt dat verbannen spelers opnieuw deelnemen en biedt betere tracking in je universum. Versie je detectieregels en volg de consequentiepercentages, zodat je problematische systemen kunt identificeren. Houd de feedback van spelers in de gaten om te beoordelen of je handhaving eerlijk aanvoelt voor de gemeenschap. De juiste balans hangt volledig af van de behoeften van je spel en de verwachtingen van je spelers.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
