<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/http-service -->

HTTP-verzoeken in het spel | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)

# HTTP-verzoeken in het spel

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt [HttpService](/docs/nl-nl/reference/engine/classes/HttpService)  gebruiken om generieke HTTP-verzoeken te verzenden naar externe webservices voor gebruiksgevallen zoals analytics, gegevensopslag of foutlogging. [HttpService](/docs/nl-nl/reference/engine/classes/HttpService)  ondersteunt ook bepaalde Open Cloud-eindpunten.

## [HTTP-verzoeken inschakelen](#http-verzoeken-inschakelen)[](#http-verzoeken-inschakelen)

De methoden [HttpService:GetAsync()](/docs/nl-nl/reference/engine/classes/HttpService#GetAsync) , [HttpService:PostAsync()](/docs/nl-nl/reference/engine/classes/HttpService#PostAsync)  en [HttpService:RequestAsync()](/docs/nl-nl/reference/engine/classes/HttpService#RequestAsync)  zijn standaard niet ingeschakeld. Om verzoeken te verzenden, moet je HTTP-verzoeken toestaan  onder Bestand  ⟩ Ervaringsinstellingen  ⟩ Beveiliging  in Studio.

## [Gebruik in plugins](#gebruik-in-plugins)[](#gebruik-in-plugins)

Je kunt [HttpService](/docs/nl-nl/reference/engine/classes/HttpService)  gebruiken in Studio-plugins om te controleren op updates, inhoud te downloaden of andere bedrijfslogica. De eerste keer dat een plugin probeert de service te gebruiken, kan de gebruiker worden gevraagd om de plugin toestemming te geven om te communiceren met het specifieke webadres. Gebruikers kunnen deze toestemmingen op elk moment accepteren, weigeren en intrekken via het venster Pluginbeheer .

Plugins kunnen ook communiceren met andere software die op dezelfde computer draait via de hosts localhost  en 127.0.0.1 . Door programma's te draaien die compatibel zijn met dergelijke plugins, kun je de functionaliteit van je plugin uitbreiden buiten de normale mogelijkheden van Studio, zoals interactie met het bestandssysteem van je computer. Wees voorzichtig, want dergelijke software moet apart van de plugin zelf worden verspreid en kan beveiligingsrisico's met zich meebrengen.

## [Gebruik met Open Cloud](#gebruik-met-open-cloud)[](#gebruik-met-open-cloud)

[HttpService](/docs/nl-nl/reference/engine/classes/HttpService)  kan momenteel een subset van de Open Cloud-eindpunten aanroepen. Je kunt deze eindpunten op dezelfde manier aanroepen als je andere eindpunten via HttpService  zou aanroepen. Het enige verschil is dat je een Open Cloud API-sleutel in het verzoek moet opnemen:

1.

[Maak een Open Cloud API-sleutel](/docs/nl-nl/cloud/auth/api-keys#create-api-keys) .

2.

[Sla de API-sleutel op in je geheimenopslag](/docs/nl-nl/cloud-services/secrets#add-secrets) .

3.

Doe het verzoek.

De volgende codevoorbeeld laat zien hoe je het groepslidmaatschap van een gebruiker vanuit een spel kunt bijwerken:

```

local HttpService = game:GetService("HttpService")

local groupId = "your_group_id"

local membershipId = "your_membership_id"

local roleId = "your_role_id"

local function request()

	local response = HttpService:RequestAsync({

		Url = `https://apis.roblox.com/cloud/v2/groups/{groupId}/memberships/{membershipId}`,

		Method = "PATCH",

		Headers = {

			["Content-Type"] = "application/json", -- Wanneer je JSON verzendt, stel dit in!

			["x-api-key"] = HttpService:GetSecret("APIKey"), -- Ingesteld in Creator Hub

		},

		Body = HttpService:JSONEncode({ role = `groups/{groupId}/roles/{roleId}` }),

	})

	if response.Success then

		print("Het antwoord was succesvol:", response.StatusCode, response.StatusMessage)

	else

		print("Het antwoord gaf een fout terug:", response.StatusCode, response.StatusMessage)

	end

	print("Antwoord lichaam:\n", response.Body)

	print("Antwoord headers:\n", HttpService:JSONEncode(response.Headers))

end

-- Wikkel de functie in pcall() voor veiligheid

local success, errorMessage = pcall(request)

if not success then

	print("Het HTTP-verzoek kon niet worden verzonden:", errorMessage)

end

```

### [Ondersteunde Open Cloud-eindpunten](#ondersteunde-open-cloud-eindpunten)[](#ondersteunde-open-cloud-eindpunten)

De volgende eindpunten worden ondersteund. Vanwege huidige beperkingen op [HttpService](/docs/nl-nl/reference/engine/classes/HttpService)  is de ..  string niet toegestaan in URL-padparameters naar Roblox-domeinen. Dit betekent bijvoorbeeld dat gegevensopslag en -invoeren die deze string bevatten momenteel niet toegankelijk zijn vanuit [HttpService](/docs/nl-nl/reference/engine/classes/HttpService) .

#### [Activa](#activa)[](#activa)

-

[GetAsset](/docs/nl-nl/cloud/features/assets#/default/Assets_GetAsset)

-

[ListAssetVersions](/docs/nl-nl/cloud/features/assets#/default/listAssetVersions)

-

[GetAssetVersion](/docs/nl-nl/cloud/features/assets#/default/Assets_GetAssetVersion)

#### [Verboden en blokkades](#verboden-en-blokkades)[](#verboden-en-blokkades)

-

[ListUserRestrictions (Plaats)](/docs/nl-nl/cloud/features/bans-and-blocks#/UserRestriction/Cloud_ListUserRestrictions__Using_Universes)

-

[GetUserRestriction (Plaats)](/docs/nl-nl/cloud/features/bans-and-blocks#/UserRestriction/Cloud_GetUserRestriction__Using_Universes_Places)

-

[UpdateUserRestriction (Plaats)](/docs/nl-nl/cloud/features/bans-and-blocks#/UserRestriction/Cloud_UpdateUserRestriction__Using_Universes_Places)

-

[ListUserRestrictions (Universum)](/docs/nl-nl/cloud/features/bans-and-blocks#/UserRestriction/Cloud_ListUserRestrictions)

-

[GetUserRestriction (Universum)](/docs/nl-nl/docs/cloud/features/bans-and-blocks#/UserRestriction/Cloud_GetUserRestriction__Using_Universes)

-

[UpdateUserRestriction (Universum)](/docs/nl-nl/cloud/features/bans-and-blocks#/UserRestriction/Cloud_UpdateUserRestriction__Using_Universes)

-

[ListUserRestrictionLogs (Universum)](/docs/nl-nl/cloud/features/bans-and-blocks#/UserRestriction/Cloud_ListUserRestrictionLogs)

#### [Configuraties](#configuraties)[](#configuraties)

-

[GetConfigRepositoryValues](/docs/nl-nl/cloud/reference/features/configs#CreatorConfigsPublicApi_GetConfigRepositoryValues)

-

[GetConfigRepositoryDraft](/docs/nl-nl/cloud/reference/features/configs#CreatorConfigsPublicApi_GetConfigRepositoryDraft)

-

[UpdateDraft](/docs/nl-nl/cloud/reference/features/configs#CreatorConfigsPublicApi_UpdateDraft)

-

[DeleteDraft](/docs/nl-nl/cloud/reference/features/configs#CreatorConfigsPublicApi_DeleteDraft)

-

[OverwriteDraft](/docs/nl-nl/cloud/reference/features/configs#CreatorConfigsPublicApi_OverwriteDraft)

-

[GetConfigRepositoryFull](/docs/nl-nl/cloud/reference/features/configs#CreatorConfigsPublicApi_GetConfigRepositoryFull)

-

[PublishDraft](/docs/nl-nl/cloud/reference/features/configs#CreatorConfigsPublicApi_PublishDraft)

-

[ListRevisions](/docs/nl-nl/cloud/reference/features/configs#CreatorConfigsPublicApi_ListRevisions)

-

[RestoreRevision](/docs/nl-nl/cloud/reference/features/configs#CreatorConfigsPublicApi_RestoreRevision)

#### [Creator Store](#creator-store)[](#creator-store)

-

[CreateCreatorStoreProduct](/docs/nl-nl/cloud/features/creator-store#/CreatorStoreProduct/Cloud_CreateCreatorStoreProduct)

-

[GetCreatorStoreProduct](/docs/nl-nl/cloud/features/creator-store#/CreatorStoreProduct/Cloud_GetCreatorStoreProduct)

-

[UpdateCreatorStoreProduct](/docs/nl-nl/cloud/features/creator-store#/CreatorStoreProduct/Cloud_UpdateCreatorStoreProduct)

-

[CreatorStoreAssetsSearch](/docs/nl-nl/cloud/features/creator-store#toolbox-service)

#### [Ontwikkelaarsproducten](#ontwikkelaarsproducten)[](#ontwikkelaarsproducten)

-

[CreateDeveloperProduct](/docs/nl-nl/cloud/reference/features/developer-products#DeveloperProducts_CreateDeveloperProductV2)

-

[UpdateDeveloperProduct](/docs/nl-nl/cloud/reference/features/developer-products#DeveloperProducts_UpdateDeveloperProductV2)

-

[GetDeveloperProductConfig](/docs/nl-nl/cloud/reference/features/developer-products#DeveloperProducts_GetDeveloperProductConfigV2)

-

[ListDeveloperProductConfigsByUniverse](/docs/nl-nl/cloud/reference/features/developer-products#DeveloperProducts_ListDeveloperProductConfigsByUniverseV2)

#### [Gamepassen](#gamepassen)[](#gamepassen)

-

[CreateGamePass](/docs/nl-nl/cloud/reference/features/game-passes#GamePasses_CreateGamePass)

-

[UpdateGamePass](/docs/nl-nl/cloud/reference/features/game-passes#GamePasses_UpdateGamePass)

-

[GetGamePassConfig](/docs/nl-nl/cloud/reference/features/game-passes#GamePasses_GetGamePassConfig)

-

[ListGamePassConfigsByUniverse](/docs/nl-nl/cloud/reference/features/game-passes#GamePasses_ListGamePassConfigsByUniverse)

#### [Gegevens- en geheugenopslag](#gegevens--en-geheugenopslag)[](#gegevens--en-geheugenopslag)

Gegevensopslag:

-

[ListDataStores](/docs/nl-nl/cloud/reference/DataStore#Cloud_ListDataStores)

-

[SnapshotDataStores](/docs/nl-nl/cloud/features/storage#/DataStore/Cloud_SnapshotDataStores)

-

[ListDataStoreEntries](/docs/nl-nl/cloud/reference/DataStoreEntry#Cloud_ListDataStoreEntries__Using_Universes)

-

[CreateDataStoreEntry](/docs/nl-nl/cloud/reference/DataStoreEntry#Cloud_CreateDataStoreEntry__Using_Universes)

-

[GetDataStoreEntry](/docs/nl-nl/cloud/reference/DataStoreEntry#Cloud_GetDataStoreEntry__Using_Universes_DataStores)

-

[DeleteDataStoreEntry](/docs/nl-nl/cloud/reference/DataStoreEntry#Cloud_DeleteDataStoreEntry__Using_Universes_DataStores)

-

[UpdateDataStoreEntry](/docs/nl-nl/cloud/reference/DataStoreEntry#Cloud_UpdateDataStoreEntry__Using_Universes_DataStores)

-

[IncrementDataStoreEntry](/docs/nl-nl/cloud/reference/DataStoreEntry#Cloud_IncrementDataStoreEntry__Using_Universes_DataStores)

-

[ListDataStoreEntryRevisions](/docs/nl-nl/cloud/features/storage#/DataStoreEntry/Cloud_ListDataStoreEntryRevisions__Using_Universes_DataStores)

-

[ListDataStoreEntries (Met Scope)](/docs/nl-nl/cloud/features/storage#/DataStoreEntry/Cloud_ListDataStoreEntries__Using_Universes_DataStores)

-

[CreateDataStoreEntry (Met Scope)](/docs/nl-nl/cloud/reference/DataStoreEntry#Cloud_CreateDataStoreEntry__Using_Universes_DataStores)

-

[GetDataStoreEntry (Met Scope)](/docs/nl-nl/cloud/features/storage#/DataStoreEntry/Cloud_GetDataStoreEntry__Using_Universes_DataStores_Scopes)

-

[DeleteDataStoreEntry (Met Scope)](/docs/nl-nl/cloud/features/storage#/DataStoreEntry/Cloud_DeleteDataStoreEntry__Using_Universes_DataStores_Scopes)

-

[UpdateDataStoreEntry (Met Scope)](/docs/nl-nl/cloud/features/storage#/DataStoreEntry/Cloud_UpdateDataStoreEntry__Using_Universes_DataStores_Scopes)

-

[IncrementDataStoreEntry (Met Scope)](/docs/nl-nl/cloud/features/storage#/DataStoreEntry/Cloud_IncrementDataStoreEntry__Using_Universes_DataStores_Scopes)

-

[ListDataStoreEntryRevisions (Met Scope)](/docs/nl-nl/cloud/features/storage#/DataStoreEntry/Cloud_ListDataStoreEntryRevisions__Using_Universes_DataStores_Scopes)

Geheugenopslag:

-

[CreateMemoryStoreQueueItem](/docs/nl-nl/cloud/features/storage#/MemoryStoreQueueItem/Cloud_CreateMemoryStoreQueueItem)

-

[DiscardMemoryStoreQueueItems](/docs/nl-nl/cloud/features/storage#/MemoryStoreQueueItem/Cloud_DiscardMemoryStoreQueueItems)

-

[ReadMemoryStoreQueueItems](/docs/nl-nl/cloud/features/storage#/MemoryStoreQueueItem/Cloud_ReadMemoryStoreQueueItems)

-

[ListMemoryStoreSortedMapItems](/docs/nl-nl/cloud/features/storage#/MemoryStoreSortedMapItem/Cloud_ListMemoryStoreSortedMapItems)

-

[CreateMemoryStoreSortedMapItem](/docs/nl-nl/cloud/features/storage#/MemoryStoreSortedMapItem/Cloud_CreateMemoryStoreSortedMapItem)

-

[GetMemoryStoreSortedMapItem](/docs/nl-nl/cloud/features/storage#/MemoryStoreSortedMapItem/Cloud_GetMemoryStoreSortedMapItem)

-

[DeleteMemoryStoreSortedMapItem](/docs/nl-nl/cloud/features/storage#/MemoryStoreSortedMapItem/Cloud_DeleteMemoryStoreSortedMapItem)

-

[UpdateMemoryStoreSortedMapItem](/docs/nl-nl/cloud/features/storage#/MemoryStoreSortedMapItem/Cloud_UpdateMemoryStoreSortedMapItem)

-

[FlushMemoryStore](/docs/nl-nl/cloud/features/storage#/MemoryStore/Cloud_FlushMemoryStore)

Geordende gegevensopslag:

-

[ListOrderedDataStoreEntries](/docs/nl-nl/cloud/features/storage#/OrderedDataStoreEntry/Cloud_ListOrderedDataStoreEntries)

-

[CreateOrderedDataStoreEntry](/docs/nl-nl/cloud/features/storage#/OrderedDataStoreEntry/Cloud_CreateOrderedDataStoreEntry)

-

[GetOrderedDataStoreEntry](/docs/nl-nl/cloud/features/storage#/OrderedDataStoreEntry/Cloud_GetOrderedDataStoreEntry)

-

[DeleteOrderedDataStoreEntry](/docs/nl-nl/cloud/features/storage#/OrderedDataStoreEntry/Cloud_DeleteOrderedDataStoreEntry)

-

[UpdateOrderedDataStoreEntry](/docs/nl-nl/cloud/features/storage#/OrderedDataStoreEntry/Cloud_UpdateOrderedDataStoreEntry)

-

[IncrementOrderedDataStoreEntry](/docs/nl-nl/cloud/features/storage#/OrderedDataStoreEntry/Cloud_IncrementOrderedDataStoreEntry)

#### [Groepen](#groepen)[](#groepen)

-

[GetGroup](/docs/nl-nl/cloud/reference/Group#Cloud_GetGroup)

-

[ListGroupJoinRequests](/docs/nl-nl/cloud/reference/GroupJoinRequest#Cloud_ListGroupJoinRequests)

-

[AcceptGroupJoinRequest](/docs/nl-nl/cloud/reference/GroupJoinRequest#Cloud_AcceptGroupJoinRequest)

-

[DeclineGroupJoinRequest](/docs/nl-nl/cloud/reference/GroupJoinRequest#Cloud_DeclineGroupJoinRequest)

-

[ListGroupMemberships](/docs/nl-nl/cloud/reference/GroupMembership#Cloud_ListGroupMemberships)

-

[UpdateGroupMembership](/docs/nl-nl/cloud/reference/GroupMembership#Cloud_UpdateGroupMembership)

-

[ListGroupRoles](/docs/nl-nl/cloud/reference/GroupRole#Cloud_ListGroupRoles)

-

[GetGroupRole](/docs/nl-nl/cloud/reference/GroupRole#Cloud_GetGroupRole)

-

[GetGroupShout](/docs/nl-nl/cloud/reference/GroupShout#Cloud_GetGroupShout)

#### [Inventarissen](#inventarissen)[](#inventarissen)

-

[ListInventoryItems](/docs/nl-nl/cloud/reference/InventoryItem#Cloud_ListInventoryItems)

#### [Luau-uitvoering](#luau-uitvoering)[](#luau-uitvoering)

-

[CreateLuauExecutionSessionTaskBinaryInput](/docs/nl-nl/cloud/features/luau-execution#/LuauExecutionSessionTaskBinaryInput/Cloud_CreateLuauExecutionSessionTaskBinaryInput)

-

[CreateLuauExecutionSessionTask](/docs/nl-nl/cloud/features/luau-execution#/LuauExecutionSessionTask/Cloud_CreateLuauExecutionSessionTask__Using_Universes)

-

[CreateLuauExecutionSessionTask (met versie)](/docs/nl-nl/cloud/features/luau-execution#/LuauExecutionSessionTask/Cloud_CreateLuauExecutionSessionTask__Using_Universes_Places)

-

[GetLuauExecutionSessionTask](/docs/nl-nl/cloud/features/luau-execution#/LuauExecutionSessionTask/Cloud_GetLuauExecutionSessionTask)

-

[ListLuauExecutionSessionTaskLogs](/docs/nl-nl/cloud/features/luau-execution#/LuauExecutionSessionTaskLog/Cloud_ListLuauExecutionSessionTaskLogs)

#### [Meldingen](#meldingen)[](#meldingen)

-

[CreateUserNotification](/docs/nl-nl/cloud/features/notifications#/UserNotification/Cloud_CreateUserNotification)

#### [Plaatsen](#plaatsen)[](#plaatsen)

-

[GetPlace](/docs/nl-nl/cloud/features/places#/Place/Cloud_GetPlace)

-

[UpdatePlace](/docs/nl-nl/cloud/features/places#/Place/Cloud_UpdatePlace)

-

[GetInstance](/docs/nl-nl/cloud/features/places#/Instance/Cloud_GetInstance)

-

[UpdateInstance](/docs/nl-nl/cloud/features/places#/Instance/Cloud_UpdateInstance)

#### [Universums](#universums)[](#universums)

-

[UpdateUniverse](/docs/nl-nl/cloud/features/universes#/Universe/Cloud_UpdateUniverse)

-

[GetUniverse](/docs/nl-nl/cloud/features/universes#/Universe/Cloud_GetUniverse)

-

[PublishUniverseMessage](/docs/nl-nl/cloud/features/universes#/Universe/Cloud_PublishUniverseMessage)

-

[RestartUniverseServers](/docs/nl-nl/cloud/features/universes#/Universe/Cloud_RestartUniverseServers)

#### [Gebruikers](#gebruikers)[](#gebruikers)

-

[GetUser](/docs/nl-nl/cloud/features/users#/User/Cloud_GetUser)

-

[GenerateUserThumbnail](/docs/nl-nl/cloud/features/users#/User/Cloud_GenerateUserThumbnail)

## [Beperkingen](#beperkingen)[](#beperkingen)

-

Alleen de headers x-api-key  en content-type  zijn toegestaan.

-

De header x-api-key  moet een [Secret](/docs/nl-nl/reference/engine/datatypes/Secret)  zijn. Zie [Geheimenopslag](/docs/nl-nl/cloud-services/secrets) .

-

De string ".."  is niet toegestaan in URL-padparameters.

-

Alleen het HTTPS-protocol wordt ondersteund.

-

Je kunt poort 1194  of een poort onder 1024  niet gebruiken, behalve 80  en 443 . Als je probeert een geblokkeerde poort te gebruiken, ontvang je een 403 Forbidden  of ERR_ACCESS_DENIED  fout.

## [Snelheidslimieten](#snelheidslimieten)[](#snelheidslimieten)

Voor elke Roblox-game-server is er een limiet van 2500 Open Cloud-verzoeken per minuut. Het overschrijden hiervan kan ervoor zorgen dat de methoden voor het verzenden van verzoeken ongeveer 30 seconden stagneren. Je [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  kan ook mislukken met een bericht van Aantal Open Cloud-verzoeken overschreed limiet .

-

Open Cloud-verzoeken verbruiken niet  dezelfde totale limiet van 500 HTTP-verzoeken per minuut die op alle andere verzoeken wordt afgedwongen.

-

Elk eindpunt heeft zijn eigen limiet per eigenaar van de API-sleutel (kan een gebruiker of een groep zijn) die wordt afgedwongen, ongeacht waar de oproepen vandaan komen ([HttpService](/docs/nl-nl/reference/engine/classes/HttpService) , het web, enz.).

Voor gedetailleerde informatie over Open Cloud-snelheidslimieten, authenticatie-gebaseerde snelheidslimitering en best practices, zie [Snelheidslimieten](/docs/nl-nl/cloud/reference/rate-limits) .

## [Best practices](#best-practices)[](#best-practices)

Om je gebruik van [HttpService](/docs/nl-nl/reference/engine/classes/HttpService)  te optimaliseren en te voorkomen dat je de limieten overschrijdt, pas je de volgende best practices toe:

-

Behandel fouten op een nette manier . Webverzoeken kunnen om veel redenen mislukken. Gebruik [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  en heb een plan voor wanneer verzoeken mislukken. Valideer en saniteer bovendien strikt alle ontvangen gegevens van externe API's, zodat je waar mogelijk correcte gegevens hebt.

-

Gebruik [exponentiële backoff](https://en.wikipedia.org/wiki/Exponential_backoff)  om onder de limieten te blijven.

Als een verzoek een herstelbare fout retourneert, wacht dan in plaats van onmiddellijk opnieuw te proberen twee seconden, dan vier, acht, enzovoort tussen pogingen. Dit helpt congestie te beperken en verbetert de kans op een succesvol verzoek door de eindpunt tijd te geven om "af te koelen."

-

Verzamel en verzend gegevens in bulk.

Wanneer mogelijk, is het aan te raden om je server alle benodigde gegevens te laten verzamelen om één HTTP-verzoek te verzenden, in plaats van meerdere kleine verzoeken. Als je bijvoorbeeld een HTTP-verzoek verzendt voor elke speler op je server, controleer dan of de API een bulk/batch-eindpunt heeft en, zo ja, verzamel de informatie van alle spelers en verzend deze allemaal in één verzoek.

In sommige gevallen moet je mogelijk [HttpService:RequestAsync()](/docs/nl-nl/reference/engine/classes/HttpService#RequestAsync)  gebruiken om gegevens in de body van het verzoek op te nemen.

-

Gebruik HTTP/2-eindpunten . HTTP/2 biedt aanzienlijke prestatievoordelen door functies zoals headercompressie en multiplexing van verzoeken/antwoorden over één enkele verbinding. [HttpService](/docs/nl-nl/reference/engine/classes/HttpService)  gebruikt automatisch HTTP/2 wanneer beschikbaar. Houd er rekening mee dat de HTTP/2-specificatie vereist dat alle header-namen in kleine letters worden verzonden.

## [Observeerbaarheid](#observeerbaarheid)[](#observeerbaarheid)

Het Observeerbaarheid Dashboard  biedt inzichten en analyses voor het monitoren en oplossen van problemen met je gebruik van [HttpService](/docs/nl-nl/reference/engine/classes/HttpService) . Het dashboard bevat twee primaire grafieken: Verzoektelling  die het volume van [HttpService](/docs/nl-nl/reference/engine/classes/HttpService) -verzoeken vanuit je spel bijhoudt, en Antwoordtijd  die de latentie meet voor eindpunten om te reageren.

De beschikbare dimensies voor filtering en uitsplitsing zijn als volgt gedefinieerd:

### Verzoektype

-

GET

-

POST

-

PUT

-

PATCH

-

DELETE

-

Overig  (voor niet-gespecificeerde verzoektypes)

### Status

-

Succes (HTTP 1xx en 2xx statuscodes)

-

Omleiden (HTTP 3xx statuscodes)

-

400 (Slechte aanvraag)

-

401 (Niet gemachtigd)

-

403 (Verboden)

-

404 (Niet gevonden)

-

429 (Te veel verzoeken)

-

500 (Interne serverfout)

-

503 (Dienst niet beschikbaar)

-

ExternalError (elke andere niet-gespecificeerde foutcodes die door de externe service worden geretourneerd)

-

InternalError (een probleem dat door [HttpService](/docs/nl-nl/reference/engine/classes/HttpService)  binnen Roblox is geretourneerd)

De Antwoordtijd -grafiek is niet gecorreleerd met statusgegevens. Als je "Status" selecteert als uitsplitsing of filter, wordt deze grafiek geen gegevens weergeven.

## [Aanvullende overwegingen](#aanvullende-overwegingen)[](#aanvullende-overwegingen)

-

Verzoeken moeten een veilige vorm van authenticatie bieden, zoals een vooraf gedeeld geheim sleutel, zodat kwaadwillenden zich niet als een van je Roblox-servers kunnen voordoen.

-

Wees je bewust van de algemene capaciteit en snelheidslimiteringsbeleid van de webservers waarnaar verzoeken worden verzonden.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
