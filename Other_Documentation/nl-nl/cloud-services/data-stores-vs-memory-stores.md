<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/data-stores-vs-memory-stores -->

Kies tussen cloudservices | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)

# Kies tussen cloudservices

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox biedt verschillende opties voor gegevensopslag. Elke opslagoptie heeft voor- en nadelen en is geschikt voor verschillende gebruikssituaties. Deze tabel geeft een samenvatting van de beschikbare opties en biedt de dichtstbijzijnde vergelijkingspunten van standaard webservices.

| Dienst | | Persistentie | | Bereik | | Toegang in-game | | Vergelijking met cloud |
| --- | --- |
| Datastores | | Permanent | | Cross-server | | Lezen-schrijven | | NoSQL-database |
| Geheugenopslag | | Maximaal 45 dagen | | Cross-server | | Lezen-schrijven | | In-memory cache |
| Configuraties | | Permanent | | Cross-server | | Alleen-lezen | | App-configuratie en functie-vlaggen |
| Geheimenopslag | | Permanent | | Cross-server | | Alleen-lezen | | Geheimenbeheer |
| Luau in-memory | | Sessieduur | | Enkele server | | Lezen-schrijven | | Server RAM |

Binnen Roblox-spellen zijn cloudservices alleen toegankelijk vanuit server-scripts.

## [Wanneer datastores te gebruiken](#wanneer-datastores-te-gebruiken)[](#wanneer-datastores-te-gebruiken)

[DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  slaat langdurige gegevens op die tussen sessies moeten blijven bestaan, zoals gebruikersvoortgang of inventariselementen. Datastores zijn consistent per spel, zodat elke server voor elke plaats binnen een spel dezelfde gegevens kan openen en wijzigen. Er zijn twee soorten datastores: standaard en geordend.

-

Standaard datastores  kunnen gegevens opslaan zoals getallen, strings en tabellen die niet gerangschikt of gesorteerd hoeven te worden. Ze slaan gegevens op als sleutel-waarde paren; elke invoer wordt opgeslagen onder een sleutel die uniek is binnen zijn datastore en die je kunt ophalen, bijwerken of verwijderen. Voor meer informatie, zie [Datastores](/docs/nl-nl/cloud-services/data-stores) .

-

Geordende datastores  kunnen alleen getallen opslaan. Elke invoer wordt opgeslagen onder een sleutel die uniek is binnen zijn datastore en die je kunt ophalen, bijwerken of verwijderen. Je kunt deze gegevens numeriek rangschikken en sorteren en ze in oplopende of aflopende volgorde ophalen op basis van opgeslagen numerieke waarden. Voor meer informatie, zie [Geordende datastores](/docs/nl-nl/cloud-services/data-stores#geordende-gegevensopslag) .

|  | | Standaard datastores | | Geordende datastores |
| Gegevenstype | | Getallen, strings, booleans en tabellen. | | Alleen getallen. |
| Veelvoorkomende gebruikssituaties | | Gebruikersvoortgang, inventariselementen en spelinstellingen. | | Altijd, persistente rangsystemen en leaderboards. In tegenstelling tot leaderboards in geheugenopslag, zijn deze leaderboardgegevens permanent. |
| Back-up van vorige versies | | Beheert automatisch eerdere versies van je gegevens gedurende 30 dagen. | | Beheert geen eerdere versies van je gegevens. |

Als je gedetailleerde toegangscontrole aan je datastores wilt toevoegen en ze buiten Studio of Roblox-servers wilt openen, gebruik dan de [Open Cloud API's voor datastores](/docs/nl-nl/cloud/reference/features/storage) .

## [Wanneer geheugenopslag te gebruiken](#wanneer-geheugenopslag-te-gebruiken)[](#wanneer-geheugenopslag-te-gebruiken)

[MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService)  is een service met hoge doorvoer en lage latentie die tijdelijke gegevens opslaat die vaak moeten worden bijgewerkt of geopend, zoals wereldwijde leaderboards of matchmaking-wachtrijen. Met geheugenopslag kan elke server voor elke plaats binnen een spel dezelfde gegevens snel en vaak openen en wijzigen. Gegevens in een geheugenopslag vervallen na een bepaalde periode, tot 45 dagen.

Als je snel een klein aantal waarden over alle servers wilt lezen (niet schrijven), zijn [configuraties](#wanneer-configuraties-te-gebruiken)  de betere keuze. Geheugenopslag is niet zo performant als configuraties bij het frequent openen van een enkele sleutel of partitie.

Hoewel geheugenopslag tijdelijke gegevens opslaat, ondersteunt het ook permanente functies zoals een wereldwijde marktplaats. De marktplaats is permanent, maar de te koop aangeboden items hebben een vervaldatum.

|  | | Geheugenopslag |
| Gegevenstype | | Getallen, strings, booleans en tabellen die niet langer dan 45 dagen hoeven te blijven bestaan. |
| Veelvoorkomende gebruikssituaties | | Skill-based matchmaking, matchstatus voor multiplayer-spellen. |
| Dagelijkse en maandelijkse leaderboards. |

## [Wanneer configuraties te gebruiken](#wanneer-configuraties-te-gebruiken)[](#wanneer-configuraties-te-gebruiken)

[Configuraties](/docs/nl-nl/production/configs)  stellen je in staat om in-game variabelen in realtime bij te werken zonder servers opnieuw op te starten. Ze zijn ideaal voor functie-vlaggen en alle in-game waarden die je in de loop van de tijd wilt afstemmen of mee wilt [experimenteren](/docs/nl-nl/production/experiments) .

-

Configuraties zijn alleen-lezen vanuit een spel—je wijzigt ze op Creator Hub of in Roblox Studio—dus ze dienen niet dezelfde gebruikssituaties als datastores en geheugenopslag.

-

Wijzigingen in configuraties worden over een periode van vijf minuten uitgerold; wijzigingen in gegevens en geheugenopslag zijn meer onmiddellijk.

|  | | Configuraties |
| Gegevenstype | | Getallen, strings, booleans en JSON-objecten. |
| Veelvoorkomende gebruikssituaties | | Een nieuwe kerker inschakelen, een tijdelijke spelmodus uitschakelen, een feestevenement starten. |
| Gezondheidswaarden van vijanden, wapenbeschadiging, prijzen van items, spelvermenigvuldigers, welkomstberichten. |

## [Wanneer geheimenopslag te gebruiken](#wanneer-geheimenopslag-te-gebruiken)[](#wanneer-geheimenopslag-te-gebruiken)

Gebruik de [geheimenopslag](/docs/nl-nl/cloud-services/secrets)  voor je spel om API-sleutels, wachtwoorden en toegangstokens op te slaan die je gebruikt om te authenticeren met externe services. Het opslaan van deze waarden in een datastore brengt onnodige beveiligingsrisico's met zich mee.

|  | | Geheimenopslag |
| Gegevenstype | | Strings. |
| Veelvoorkomende gebruikssituaties | | API-sleutels, wachtwoorden en toegangstokens voor analytics of muziekdiensten. |

## [Wanneer in-memory opslag in Luau te gebruiken](#wanneer-in-memory-opslag-in-luau-te-gebruiken)[](#wanneer-in-memory-opslag-in-luau-te-gebruiken)

Gebruik in-memory opslag in Luau om tijdelijke gegevens op te slaan die met minimale latentie moeten worden geopend en zonder de kosten van externe service-aanroepen. Deze opslag is ingebouwd in Luau en vereist geen configuratie.

|  | | In-memory opslag in Luau |
| Gegevenstype | | Getallen, strings, booleans en tabellen. |
| Veelvoorkomende gebruikssituaties | | Gegevens die alleen relevant zijn voor een enkele server-sessie en niet hoeven te worden opgeslagen, zoals status-effecten of tijdelijke punten die resetten wanneer de gebruiker het spel verlaat. |
| Waarden die vaak veranderen, zoals tellers, timers, statusvlaggen of een gezondheidsbalk. |
| Gegevens die de spel-logica aansturen, die onmiddellijk toegankelijk moeten zijn, zoals tijdelijke variabelen of de huidige gezondheid van een vijand. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
