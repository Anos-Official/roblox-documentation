<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/security/network-ownership -->

Netwerkbezit, bewegingsvalidatie en fysica | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. Beveiliging

# Netwerkbezit, bewegingsvalidatie en fysica

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De volgende inhoud behandelt verschillende concepten en tactieken om de beveiliging te verbeteren en valsspelen in je Roblox-spellen te verminderen. Het wordt ten zeerste aanbevolen dat alle ontwikkelaars deze doorlezen om ervoor te zorgen dat je spellen veilig en eerlijk zijn voor alle gebruikers. Bekijk de zijbalk voor aanvullende beveiligingsthema's.

[Netwerkbezit](/docs/nl-nl/physics/network-ownership)  is een van de meer genuanceerde en vaak verkeerd begrepen aspecten van de Roblox-engine. Wanneer een speler netwerkbezit heeft over een onderdeel of assemblage, heeft hij volledige autoriteit over de fysicasimulatie voor die objecten. Standaard verleent de server netwerkbezit van niet-geankerde onderdelen aan clients met nabijgelegen spelerspersonages om de belasting van de fysicasimulatie te verdelen. Dit systeem verbetert de responsiviteit, maar creëert aanzienlijke beveiligingsimplicaties die elke ontwikkelaar moet begrijpen.

## [Begrijpen van netwerkbezit](#begrijpen-van-netwerkbezit)[](#begrijpen-van-netwerkbezit)

Wanneer een client netwerkbezit heeft over onderdelen (inclusief hun personage), heeft hij toegang tot:

Assemblage-manipulatie:

-

Teleporteren naar elke positie.

-

Dit kan worden gebruikt om snel bezit en controle te krijgen over zoveel niet-geankerde onderdelen en assemblages als de server toestaat.

-

Hun beweging en staat manipuleren, zoals vliegen of hun snelheid veranderen.

-

Valsspelers kunnen hun Humanoid WalkSpeed op elke waarde instellen. Eigenschappen kunnen lokaal worden gewijzigd zonder dat er evenementen op de lokale client worden geactiveerd, en zonder dat dergelijke eigenschapswijzigingen kunnen worden gelezen vanuit lokale scripts.

-

Willekeurige animaties afspelen en de animatiestatus manipuleren.

-

Fysieke obstakels omzeilen en hun botsing veranderen.

Fysica-manipulatie

-

De positie en rotatie van alle niet-geankerde onderdelen of mechanismen controleren, inclusief het repliceren van Inf  of NaN  componenten in [CFrames](/docs/nl-nl/reference/engine/datatypes/CFrame) . Stel de snelheden van onderdelen in op extreme waarden (inclusief Inf  of NaN ), wat de fysica van andere niet-geankerde onderdelen/assemblages kan verstoren, zelfs die niet eigendom zijn van de valsspeler. Dit wordt vaak gebruikt om andere spelerspersonages en nabijgelegen onderdelen weg te slingeren. Manipuleer het afvuren van Touched-evenementen, inclusief het helemaal niet afvuren van Touched.

Als je spel gameplay-kritieke volledig niet-geankerde onderdelen of assemblages vereist, overweeg dan om de netwerkbezit-API te gebruiken om handmatig bezit in te stellen of automatische toewijzing uit te schakelen.

## [Bewegingsvalidatie](#bewegingsvalidatie)[](#bewegingsvalidatie)

In competitieve spellen is server-side validatie van spelersbeweging cruciaal voor de integriteit van de simulatie, aangezien clients de beweging en fysica van personages controleren. Er bestaat echter geen universele oplossing vanwege de variërende gameplay-mechanica.

Traditionele methoden schieten vaak tekort in complexe scenario's. Eenvoudige afstand-over-tijd berekeningen kunnen voldoende zijn voor competitieve shooters, maar falen in fysica-intensieve spellen met voertuigen, vliegen of ingewikkelde interacties. Validatie moet ook rekening houden met netwerklatentie.

[Serverautoriteit](/docs/nl-nl/../../projects/server-authority)  is momenteel in bèta en zal binnenkort worden uitgebracht. De meest betrouwbare oplossing om fysica- en bewegingsuitbuitingen te voorkomen, is serverautoriteit, die de fysicasimulatie en bewegingsvalidatie volledig naar de server verplaatst. Dit elimineert de fundamentele beveiligingszwakte van client-gecontroleerde beweging door ervoor te zorgen dat alle bewegingsbeslissingen op de server worden genomen met autoritatieve validatie.

Totdat serverautoriteit beschikbaar komt, moeten ontwikkelaars die client-side validatie implementeren begrijpen dat effectieve benaderingen dramatisch kunnen variëren. Basisheuristieken kunnen onschuldige spelers met onbetrouwbare verbindingen markeren, en eenvoudige snelheidsberekeningen falen in spellen met complexe bewegingssystemen. Positiewijzigingen zijn onderhevig aan internetlatentie, wat averaging over tijd vereist. Veel ontwikkelaars ontdekken dat leaky bucket-stijl accumulators goed werken voor het omgaan met burstbewegingen terwijl ze aanhoudende overtredingen voorkomen.

Praktische implementatie vereist vaak het projecteren van beweging op specifieke vlakken (bijv. XZ voor grondgebonden beweging) om te voorkomen dat legitieme verticale beweging wordt bestraft terwijl horizontale teleportatie wordt gedetecteerd. Spellen met legitieme teleportatiemechanica hebben expliciete vrijstellingssystemen nodig. Validatiefrequentie, tolerantieniveaus en handhavingsstrategieën moeten worden afgestemd op de specifieke vereisten van elk spel.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
