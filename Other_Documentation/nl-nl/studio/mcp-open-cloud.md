<!-- Source: https://create.roblox.com/docs/nl-nl/studio/mcp-open-cloud -->

Gebruik Open Cloud met de Studio MCP-server | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)
4. /
5. [MCP-server](/docs/nl-nl/studio/mcp)

# Gebruik Open Cloud met de Studio MCP-server

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [Studio MCP-server](/docs/nl-nl/studio/mcp)  kan [Open Cloud](/docs/nl-nl/cloud)  API's namens jou aanroepen. Jouw MCP-client kan assets uploaden, ontwikkelaarsproducten en gamepassen beheren, spelinstellingen wijzigen en meer zonder een [API-sleutel](/docs/nl-nl/cloud/auth/api-keys)  te maken of in te voeren.

Jij beslist wat jouw client mag doen. Machtigingen worden opgeslagen op jouw Roblox-account voor elk spel, en Studio handhaaft deze bij elke aanvraag.

## [Vereisten](#vereisten)[](#vereisten)

Voordat je Open Cloud met de Studio MCP-server gebruikt:

-

Schakel de Studio MCP-server in en verbind jouw client. Voor meer informatie, zie [Verbind met de Roblox Studio MCP-server](/docs/nl-nl/studio/mcp) .

-

Open een plaats die behoort tot een gepubliceerd spel. Machtigingen worden per spel opgeslagen, dus niet-gepubliceerde lokale plaatsen kunnen ze niet gebruiken.

-

Heb toestemming om het spel te beheren. Als een groep het spel bezit, moet jouw groepsrol de acties toestaan die je aan de client verleent.

## [Hoe het werkt](#hoe-het-werkt)[](#hoe-het-werkt)

De Studio MCP-server voegt de open_cloud_invoke  tool toe. Studio beheert de toegang voor jou. Jouw client kan alleen de scopes gebruiken die je hebt ingeschakeld voor het huidige spel, en het ziet of beheert nooit inloggegevens. Alleen jij kunt jouw machtigingen wijzigen. Jouw client kan ze niet zelf inschakelen.

Voor elk spel bepaal je welke Open Cloud scopes jouw client kan aanroepen, uit welke mappen het kan uploaden, of data store en memory store aanroepen werken vanuit execute_luau , en of scripts HTTP-aanvragen kunnen doen en naar welke domeinen.

| Parameter | | Beschrijving |
| --- | --- |
| method | | GET , POST , PUT , PATCH  of DELETE . |
| endpoint | | Het pad onder https://apis.roblox.com , inclusief eventuele querystring. Bijvoorbeeld, /cloud/v2/universes/123`. |
| body | | Een JSON-gecodeerd aanvraaglichaam. Laat weg voor GET  en DELETE . |
| scopes | | De scopes die de endpoint vereist, zoals ["universe:read"] . Optioneel, maar retourneert een duidelijke fout als een vereiste scope niet is ingeschakeld. |
| files | | Lokale bestanden voor multipart/form-data  endpoints, zoals asset uploads. Bestanden moeten zich in een goedgekeurde [uploadmap](#uploadmappen)  bevinden. |

Machtigingen zijn per persoon. Als je aan een spel werkt met samenwerkers, stelt elke samenwerker zijn eigen machtigingen in. Een machtiging voor jezelf inschakelen, schakelt deze niet in voor anderen.

Deze machtigingen zijn alleen van toepassing op externe MCP-clients. Ze veranderen niet wat Assistant binnen Studio kan doen.

## [Beheer machtigingen](#beheer-machtigingen)[](#beheer-machtigingen)

Om machtigingen voor het spel dat je hebt geopend te beheren, klik je op MCP  in de rechterbenedenhoek van Studio, en selecteer je het tabblad MCP-machtigingen . Of, vanuit Assistant:

1.

Open Assistant .

2.

Klik op …  ⟩ Instellingen .

3.

Selecteer het tabblad MCP-machtigingen .

4.

Schakel machtigingen in of uit. Wijzigingen zijn van toepassing op de volgende aanvraag van jouw client.

### [Toegangslevels](#toegangslevels)[](#toegangslevels)

Kies een toegangslevel als uitgangspunt en schakel vervolgens individuele machtigingen in of uit. Elk spel begint op Gebalanceerd .

| Toegangslevel | | Wat het inschakelt |
| Veilig | | Alleen laag-risico scopes. De meeste machtigingen zijn uitgeschakeld. |
| Gebalanceerd | | Laag- en gematigd-risico scopes. |
| Volledige toegang | | Alle scopes, inclusief hoog-risico scopes die Robux kunnen kosten, invloed hebben op jouw spelers of publiceren naar jouw live spel. |
| Aangepast | | Weergegeven wanneer je een machtiging wijzigt na het kiezen van een level. |

Roblox stelt het risiconiveau voor elke scope in.

### [Machtigingssecties](#machtigingssecties)[](#machtigingssecties)

Machtigingen zijn gegroepeerd op basis van wat ze jouw client laten doen. Elke sectie komt overeen met een of meer Open Cloud [scopes](/docs/nl-nl/cloud/reference/scopes)  of scriptmogelijkheden. Voor details over elke scope, zie de [Open Cloud scopes](/docs/nl-nl/cloud/reference/scopes)  referentie.

| Sectie | | Wat het toestaat | | Scopes |
| Bekijk jouw spel | | Lees spel- en plaatsinstellingen, versiegeschiedenis, analyses en instanties. | | universe:read , universe.place:read , universe.analytics:read , universe.place.instance:read |
| Bewerk jouw spel | | Wijzig spel- en plaatsinstellingen, publiceer, herstart servers en bewerk instanties op afstand. | | universe:write , universe.place:write , universe.place.instance:write |
| Spelers & sociaal | | Lees profielen en inventarissen, stuur meldingen, beheer groepen en forums, beheer evenementen en lees opgeslagen Creator Store-items. | | user.* , group:* , group-forum:read , universe.event:* , creator-store-save:* |
| Gegevens opslaan & laden | | Gebruik [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  en [MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService)  vanuit execute_luau . | | universe-datastores.* , universe.ordered-data-store.* , memory-store.* |
| Verbind met het internet | | Maak HTTP-aanvragen vanuit Luau naar domeinen die je toestaat, en publiceer cross-server berichten. | | Network  mogelijkheid, universe-messaging-service:publish |
| Publiceer & beheer assets | | Upload assets en controleer hun status, deel assets, beheer Creator Store-lijsten, publiceer plaatsversies en beheer miniaturen. | | asset:* , asset-permissions:write , creator-store-product:* , universe-places:write , universe.thumbnail:* |
| Geld & monetisatie | | Maak en bewerk ontwikkelaarsproducten, gamepassen en advertentiecampagnes, en lees abonnementen. | | developer-product:* , game-pass:* , ad.campaign:* , ad.billing:read , universe.subscription-product.subscription:read |
| Gevolgen voor spelers | | Lees, maak en verwijder bans. | | universe.user-restriction:* |
| Beveiliging & inloggegevens | | Lees geheime namen en maak geheimen, en voer Luau uit in de cloud. | | universe.secret:* , universe.place.luau-execution-session:* |

Sommige machtigingen kunnen Robux kosten, invloed hebben op jouw spelers of wijzigingen publiceren naar jouw live spel. Deze omvatten Geld & monetisatie , Gevolgen voor spelers , Beveiliging & inloggegevens , universe:write , en universe-places:write . Schakel ze alleen in voor taken die ze vereisen, en schakel ze uit wanneer je klaar bent.

### [Uploadmappen](#uploadmappen)[](#uploadmappen)

Jouw client kan alleen bestanden uploaden vanuit mappen die je goedkeurt. Voeg een map toe voordat je jouw client vraagt om assets te uploaden, en houd exports daar.

De client kan geen bestanden kopiëren of verplaatsen naar een goedgekeurde map om deze beperking te omzeilen. Als een bestand ergens anders is, verplaats het dan zelf of keur de map goed.

### [Data stores en memory stores](#data-stores-en-memory-stores)[](#data-stores-en-memory-stores)

Jouw client heeft toegang tot data stores en memory stores via [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  en [MemoryStoreService](/docs/nl-nl/reference/engine/classes/MemoryStoreService)  in execute_luau , niet via Open Cloud. Om ze te gebruiken:

1.

Schakel de scopes in die je nodig hebt onder Gegevens opslaan & laden . Lezen vereist universe-datastores.objects:read . Schrijven vereist universe-datastores.objects:update .

2.

In Spelinstellingen  ⟩ Beveiliging , schakel Studio-toegang tot API-services inschakelen  in. Deze spelinstelling is afzonderlijk van jouw MCP-machtigingen.

Studio gebruikt jouw live data stores. Schrijfacties van jouw client wijzigen echte spelerdata. Overweeg eerst tegen een apart spel te testen.

### [HTTP-aanvragen](#http-aanvragen)[](#http-aanvragen)

Om scripts die jouw client uitvoert HTTP-aanvragen te laten maken met [HttpService](/docs/nl-nl/reference/engine/classes/HttpService) :

1.

Schakel Verbind met het internet  in. Dit verleent de Network  [scriptmogelijkheid](/docs/nl-nl/scripting/capabilities) .

2.

Voeg elk domein dat jouw client nodig heeft toe aan de HTTP-domein toestemmingslijst .

Studio weigert aanvragen naar elk domein dat niet op de lijst staat.

### [Onbeschikbare machtigingen](#onbeschikbare-machtigingen)[](#onbeschikbare-machtigingen)

Sommige scopes kunnen niet aan een MCP-client worden verleend. Deze omvatten badge scopes, universe-datastores.control:* , universe-datastores.objects:create , analysemeldingen, en alle legacy-*  scopes. Gebruik het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  of een [API-sleutel](/docs/nl-nl/cloud/auth/api-keys)  voor deze taken.

Sommige endpoints weigeren ook de token die Studio gebruikt, zelfs wanneer de bijbehorende scope is ingeschakeld. Als dat gebeurt, rapporteert jouw client de fout en stelt een andere manier voor om de taak te voltooien.

## [Importeer een 3D-model](#importeer-een-3d-model)[](#importeer-een-3d-model)

Het importeren van assets vanuit Blender, Maya of een andere 3D-tool is een veelvoorkomende workflow. Jouw client exporteert het model, uploadt het, voegt het in, en vergelijkt het resultaat met de bron en herstelt wat de import heeft veranderd.

Om een model te importeren:

1.

Schakel Publiceer & beheer assets  ⟩ asset:read  en asset:write  in.

2.

Keur de map goed waar jouw exports naartoe gaan.

3.

Open het model in jouw 3D-tool, of exporteer het als .glb  of .fbx  naar de goedgekeurde map.

4.

Vraag jouw client om hulp. Bijvoorbeeld:

Importeer het kasteel uit mijn open Blender-bestand in Studio, naast het spawnpunt.

De importvaardigheid vertelt jouw client om te bevestigen voordat het uploadt. Het doet dan het volgende:

-

Controleert elke mesh tegen de driehoeklimiet en vraagt of het moet splitsen of vereenvoudigen van diegene die deze overschrijdt.

-

Uploadt het model en wacht op moderatie.

-

Voegt het model in en herstelt schaal, rotatie, ontbrekende texturen, kleuren en verankering.

-

Plaatst het model op de grond, vrij van andere objecten en spawnpunten.

Uploads creëren permanente assets die eigendom zijn van de eigenaar van het spel. Als een groep het spel bezit, gaan uploads naar de groep. Open Cloud kan ze niet archiveren of verwijderen. Om een asset te verwijderen, gebruik je het [Creator Dashboard](https://create.roblox.com/dashboard/creations) . Jij bent verantwoordelijk voor wat er naar jouw account is geüpload, inclusief uploads die jouw client voor jou maakt.

Voor ondersteunde assettypes, formaten en limieten, zie [Gebruiksgids voor assets](/docs/nl-nl/cloud/guides/usage-assets#ondersteunde-assettypes-en-limieten) .

## [Vaardigheden](#vaardigheden)[](#vaardigheden)

De volgende vaardigheden leren jouw client hoe deze machtigingen te gebruiken. Clients die via MCP zijn verbonden, krijgen ze automatisch en laden ze met de skill  tool. Om ze te bekijken, open je Assistant , klik je op …  ⟩ Assistant-instellingen , en selecteer je Vaardigheden . Om er een aan te passen aan jouw workflow, selecteer je deze en klik je op Dupliceren , en bewerk je jouw kopie. Jouw kopie vervangt het origineel, maar ontvangt geen toekomstige updates.

| Vaardigheid | | Beschrijving |
| rbx-open-cloud-usage | | Roep Open Cloud aan met open_cloud_invoke , selecteert de juiste endpoint en behandelt fouten. |
| rbx-permissions | | Bepaalt welke machtigingen een taak nodig heeft, controleert welke zijn ingeschakeld, en vraagt jou alleen om de ontbrekende. |
| rbx-import-asset | | Implementeert een model vanuit een externe 3D-tool, controleert en herstelt het vervolgens in Studio. |

## [Probleemoplossing](#probleemoplossing)[](#probleemoplossing)

Wanneer een aanvraag wordt geblokkeerd, rapporteert de client wat ontbreekt. Het omzeilt nooit een machtiging die je hebt uitgeschakeld.

| Fout | | Oorzaak | | Oplossing |
| Scope '<scope>' is niet verleend | | De scope is uitgeschakeld, of de naam is verkeerd gespeld. | | Schakel de scope in de bijbehorende sectie in. |
| HTTP 403  of 401 , met de scope ingeschakeld | | De endpoint accepteert de MCP-token niet. | | Gebruik het Creator Dashboard of een API-sleutel voor deze taak. |
| ontbrekende mogelijkheid <capability> | | Een script heeft een mogelijkheid nodig die niet is verleend. | | Schakel Verbind met het internet  in voor Network . Andere mogelijkheden kunnen niet worden verleend. |
| domein <domain> staat niet op de Assistant HTTP-toestemmingslijst | | Het domein staat niet op jouw toestemmingslijst. | | Voeg het toe onder Verbind met het internet  ⟩ HTTP-domein toestemmingslijst . |
| 502 … Toegang verboden  van een data store-aanroep | | De bijbehorende Gegevens opslaan & laden  scope is uitgeschakeld. | | Schakel de lees- of update-scope in. |
| Studio-toegang tot API's is niet toegestaan | | Studio API-toegang is uitgeschakeld voor dit spel. | | Schakel Spelinstellingen  ⟩ Beveiliging  ⟩ Studio-toegang tot API-services inschakelen  in. |
| InternalError  van een memory store-aanroep | | De memory-store.*  scopes zijn uitgeschakeld. | | Schakel de memory store-scopes in onder Gegevens opslaan & laden . |
| Bestand niet in een goedgekeurde uploaddirectory | | Het bestand bevindt zich buiten jouw goedgekeurde mappen. | | Keuring de map goed, of verplaats het bestand naar een goedgekeurde map. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
