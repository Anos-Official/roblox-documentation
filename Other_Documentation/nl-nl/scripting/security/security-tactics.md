<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/security/security-tactics -->

Beveiliging en tactieken voor het verminderen van valsspelen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. Beveiliging

# Beveiliging en tactieken voor het verminderen van valsspelen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De volgende inhoud behandelt verschillende concepten en tactieken om de beveiliging te verbeteren en valsspelen in je Roblox-spellen te verminderen. Het wordt ten zeerste aanbevolen dat alle ontwikkelaars deze doornemen om ervoor te zorgen dat je spellen veilig en eerlijk zijn voor alle gebruikers. Bekijk de zijbalk voor aanvullende beveiligingsthema's.

Voordat we ingaan op specifieke tactieken voor veilige ontwikkeling en het voorkomen van valsspelen, is het essentieel om de fundamentele principes van Roblox-beveiliging te begrijpen. Een veilig spel is gebouwd op een mindset die vijandige acties anticipeert. Voordat je een enkele regel code schrijft, moet je deze fundamentele principes internaliseren. Ze moeten elke architectonische en ontwerpbeslissing die je maakt, informeren.

## [Vertrouw nooit de client](#vertrouw-nooit-de-client)[](#vertrouw-nooit-de-client)

Dit is het fundamentele principe. Een vastberaden exploiteur heeft volledige controle over zijn lokale staat en netwerkverkeer. Omdat exploiters dit niveau van controle hebben, zal elke beveiligingsmaatregel die afhankelijk is van handhaving aan de clientzijde uiteindelijk worden omzeild. Dit is geen beperking van Roblox: het is een fundamentele realiteit van client-serverarchitecturen. Neem aan dat elk stuk data dat van de client wordt verzonden, is gemanipuleerd, gefabriceerd of verzonden met kwade bedoelingen. Dit omvat de mogelijkheid om:

-

Elke gerepliceerde LocalScript of ModuleScript te decompileren, zelfs als ze nooit op de client worden uitgevoerd

-

Netwerkbezit van hun karakter en alle niet-geankerde onderdelen te nemen

-

Client-geïnitieerde evenementen zoals Touched-evenementen of ProximityPrompt-activeringen op elke afstand of frequentie te triggeren

-

De positie, fysica of interacties van hun speler met de wereld te wijzigen

-

RemoteEvents en RemoteFunctions met willekeurige argumenten (behalve het eerste Player-argument) op elke frequentie te activeren of aan te roepen

-

Alles in hun lokale DataModel te veranderen zonder enige verwachte evenementen te activeren

-

Willekeurig het gedrag van elke lokaal draaiende code te wijzigen

Vanwege dit alles moet alle kritieke logica server-side worden gevalideerd of uitsluitend op de server worden uitgevoerd. De gevolgen van deze controle worden in detail beschreven in [Netwerkbezit, Bewegingsvalidatie en Fysica-exploits](/docs/nl-nl/scripting/security/network-ownership)  en [Toegangscontrole en Vertrouwelijkheid](/docs/nl-nl/scripting/security/access-control) .

## [Server als bron van waarheid](#server-als-bron-van-waarheid)[](#server-als-bron-van-waarheid)

De server moet de ultieme bron van waarheid zijn voor alle simulatiestaten, regels, spelerprogressie en kritieke beslissingen. De rol van de client is om de wereld weer te geven en gebruikersinvoer naar de server te sturen.

De rol van de server is om:

-

Invoer van de client te ontvangen

-

Te valideren dat de gevraagde actie mogelijk en toegestaan is

-

De actie uit te voeren en zijn autoritatieve staat bij te werken

-

De resultaten naar alle relevante clients te repliceren

Bijvoorbeeld, als een speler zegt "Ik wil een Bloxy Cola kopen", moet de server de werkelijke prijs van het item, het geld van de speler en de fysieke afstand van het spelerskarakter tot de winkel kennen voordat de transactie wordt gevalideerd en goedgekeurd. Voor zover mogelijk moet de staat die gevalideerd moet worden, uitsluitend door de server worden onderhouden en niet door clients. In het voorbeeld, als de Bloxy Cola-transactie wordt goedgekeurd, moet de server de prijs van de Bloxy Cola van het geld van de speler aftrekken, maar de server kan niet noodzakelijkerwijs altijd de controle over het karakter van de speler hebben.

Dit principe verschilt van serverautoriteit , een enginefunctie die het toepast op fysica en beweging. In het [serverautoriteitsmodel](/docs/nl-nl/projects/server-authority)  simuleert de server de gehele spelstaat en sturen clients alleen hun invoer, zodat een client nooit zijn eigen positie of staat kan rapporteren. Dit voorkomt hele klassen van valsspelen, zoals vliegen of snelheidshacks. Om de gameplay responsief te houden, voorspellen clients de resultaten van hun invoer, en corrigeert de server deze wanneer een voorspelling verkeerd is. Overweeg het serverautoriteitsmodel voor competitieve spellen zoals shooters, racen, sport en gevechten.

## [Beveiliging door ontwerp](#beveiliging-door-ontwerp)[](#beveiliging-door-ontwerp)

Integreer beveiligingsoverwegingen in het ontwerp van je spel vanaf het allereerste begin, in plaats van te proberen ze later als een bijgedachte toe te voegen.

-

Bedreigingsmodel voor elke nieuwe functie. Voor elke nieuwe functie, vraag:

-

Hoe zou een aanvaller dit kunnen misbruiken als ze volledige controle over hun client hebben?

-

Als een client elke waarde voor elke parameter die in de functie wordt gebruikt, zou kunnen verzenden, wat is dan de slechtst mogelijke uitkomst?

-

Wat gebeurt er als deze functie 1.000+ keer per seconde wordt gebruikt? Wat is de maximale snelheid waarmee het zou moeten worden gebruikt?

-

Zou een exploiteur dit kunnen gebruiken om de ervaring van een andere speler te verpesten?

-

Hoeveel middelen zou deze functie in het slechtste geval haalbaar kunnen gebruiken?

-

Wat is de minimale interne informatie of staat die ik moet blootstellen voor deze functie?

-

Verdeel verantwoordelijkheden vroeg. Houd logica en data in ServerScriptService vanaf dag één. Plaats ze nooit in gerepliceerde containers zoals ReplicatedStorage of Workspace.

## [Apparaatvertrouwen](#apparaatvertrouwen)[](#apparaatvertrouwen)

De principes op deze pagina beschermen je spel tegen wat een speler doet nadat ze zijn toegetreden. Roblox biedt ook de optionele [Device Trust API](/docs/nl-nl/scripting/security/device-trust) , die controleert of het apparaat van de speler kan worden vertrouwd wanneer ze zich aanmelden en geeft je het resultaat als een apparaatvertrouwensniveau . Roblox onderneemt geen actie op basis van dit niveau. Jij beslist hoe je spel reageert, bijvoorbeeld door spelers naar aparte plaatsen te sturen op basis van hun vertrouwensniveau, door gevoelige functies zoals handelen te beperken tot vertrouwde apparaten, of door spelers te weigeren wiens apparaten de controle niet doorstaan. Om het in je scripts te gebruiken, zie [lees het vertrouwensniveau](/docs/nl-nl/scripting/security/device-trust#lees-het-vertrouwensniveau) .

Apparaatvertrouwen vervangt de principes op deze pagina niet. Exploits die afhankelijk zijn van zwakke server-side validatie werken nog steeds op vertrouwde apparaten, dus blijf de client als onbetrouwbaar beschouwen en valideer belangrijke acties op de server.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
