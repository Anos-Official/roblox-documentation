<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/data-stores/versioning-listing-and-caching -->

Versiebeheer, opsommen en cachen van gegevensopslag | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Gegevensopslag](/docs/nl-nl/cloud-services/data-stores)

# Versiebeheer, opsommen en cachen van gegevensopslag

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Beheer uw gegevens met versiebeheer, opsommen en cachen.

## [Versiebeheer](#versiebeheer)[](#versiebeheer)

Versiebeheer vindt plaats wanneer u [instelt](/docs/nl-nl/cloud-services/data-stores#gegevens-maken) , [bijwerkt](/docs/nl-nl/cloud-services/data-stores#gegevens-bijwerken)  en [verhoogt](/docs/nl-nl/cloud-services/data-stores#gegevens-verhogen)  gegevens. De functies [SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync) , [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync) , en [IncrementAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#IncrementAsync)  maken versiegebonden back-ups van uw gegevens met behulp van de eerste schrijfopdracht naar elke sleutel in elk UTC-uur. Opvolgende schrijfbewerkingen naar een sleutel in hetzelfde UTC-uur overschrijven permanent de vorige gegevens.

Versiegebonden back-ups vervallen 30 dagen nadat een nieuwe schrijfopdracht ze heeft overschreven. De laatste versie vervalt nooit.

De volgende functies voeren versiebeheeroperaties uit:

| Functie | | Beschrijving |
| --- | --- |
|

[ListVersionsAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListVersionsAsync)

 | |

Lijst alle versies voor een sleutel door een [DataStoreVersionPages](/docs/nl-nl/reference/engine/classes/DataStoreVersionPages)  instantie terug te geven die u kunt gebruiken om alle versienummers te enumereren. U kunt versies filteren met behulp van een tijdsbereik.

 |
|

[GetVersionAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAsync)

 | |

Haalt een specifieke versie van een sleutel op met behulp van het versienummer van de sleutel.

 |
|

[RemoveVersionAsync()](/docs/nl-nl/reference/engine/classes/DataStore#RemoveVersionAsync)

 | |

Verwijdert een specifieke versie van een sleutel.

Deze functie maakt ook een tombstone-versie aan terwijl de vorige versie behouden blijft. Bijvoorbeeld, als u RemoveAsync("User_1234")  aanroept en vervolgens probeert GetAsync("User_1234")  aan te roepen, krijgt u nil  terug. U kunt echter nog steeds [ListVersionsAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListVersionsAsync)  en [GetVersionAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAsync)  gebruiken om oudere versies van de gegevens op te halen.

 |

U kunt versiebeheer gebruiken om gebruikersverzoeken af te handelen. Als een gebruiker meldt dat er een probleem is opgetreden op 2020-10-09T01:42, kunt u de gegevens terugzetten naar een vorige versie met behulp van het volgende voorbeeld:

```

local DataStoreService = game:GetService("DataStoreService")

local gameStore = DataStoreService:GetDataStore("PlayerGame")

local DATA_STORE_KEY = "User_1234"

local maxDate = DateTime.fromUniversalTime(2020, 10, 09, 01, 42)

-- Haalt de versie op die het dichtst bij de gegeven tijd ligt

local listSuccess, pages = pcall(function()

    return gameStore:ListVersionsAsync(DATA_STORE_KEY, Enum.SortDirection.Descending, nil, maxDate.UnixTimestampMillis)

end)

if listSuccess then

    local items = pages:GetCurrentPage()

    if #items > 0 then

        -- Leest de dichtstbijzijnde versie

        local closestEntry = items[1]

        local success, value, info = pcall(function()

            return gameStore:GetVersionAsync(DATA_STORE_KEY, closestEntry.Version)

        end)

        -- Herstelt de huidige waarde door deze te overschrijven met de dichtstbijzijnde versie

        if success then

            local setOptions = Instance.new("DataStoreSetOptions")

            setOptions:SetMetadata(info:GetMetadata())

            gameStore:SetAsync(DATA_STORE_KEY, value, nil, setOptions)

        end

    else

        -- Geen invoeren gevonden

    end

end

```

### [Momentopnamen](#momentopnamen)[](#momentopnamen)

De [Snapshot Data Stores Open Cloud API](/docs/nl-nl/cloud/reference/DataStore#Cloud_SnapshotDataStores)  stelt u in staat om eenmaal per dag een momentopname van alle gegevensopslag in een spel te maken. Voordat u een game-update publiceert die uw gegevensopslaglogica wijzigt, moet u ervoor zorgen dat u een momentopname maakt. Het maken van een momentopname garandeert dat u de meest recente gegevens beschikbaar heeft van de vorige versie van het spel.

Bijvoorbeeld, zonder een momentopname, als u een update publiceert om 3:30 UTC die gegevenscorruptie veroorzaakt, overschrijft de corrupte gegevens alle gegevens die zijn geschreven tussen 3:00-3:30 UTC. Als u echter een momentopname maakt om 3:29 UTC, overschrijft de corrupte gegevens niets dat vóór 3:29 UTC is geschreven, en de laatste gegevens voor alle sleutels die zijn geschreven tussen 3:00-3:29 UTC worden behouden.

## [Opsommen en voorvoegsels](#opsommen-en-voorvoegsels)[](#opsommen-en-voorvoegsels)

Gegevensopslag stelt u in staat om op voorvoegsel te lijsten. Bijvoorbeeld, opsommen op de eerste n  karakters van een naam, zoals "d", "do" of "dog" voor elke sleutel of gegevensopslag met een voorvoegsel van "dog".

U kunt een voorvoegsel opgeven bij het opsommen van alle gegevensopslag of sleutels, en alleen objecten terugkrijgen die overeenkomen met dat voorvoegsel. Zowel de [ListDataStoresAsync()](/docs/nl-nl/reference/engine/classes/DataStoreService#ListDataStoresAsync)  als de [ListKeysAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListKeysAsync)  functies retourneren een [DataStoreListingPages](/docs/nl-nl/reference/engine/classes/DataStoreListingPages)  object dat u kunt gebruiken om de lijst te enumereren.

| Functie | | Beschrijving |
| [ListDataStoresAsync()](/docs/nl-nl/reference/engine/classes/DataStoreService#ListDataStoresAsync) | | Listeert alle gegevensopslag. |
| [ListKeysAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListKeysAsync) | | Listeert alle sleutels in een gegevensopslag. |

### [Scopes](#scopes)[](#scopes)

Voor nieuwe spellen, gebruik [opsommen en voorvoegsels](#opsommen-en-voorvoegsels)  om sleutels in uw gegevensopslag te organiseren in plaats van de legacy scopes-functie. Voor bestaande spellen die scopes gebruiken, blijf ze gebruiken.

U kunt sleutels in een gegevensopslag verder organiseren door een unieke string in te stellen als een scope voor de tweede parameter van [GetDataStore()](/docs/nl-nl/reference/engine/classes/DataStoreService#GetDataStore) . De standaard scope (als er geen scope is opgegeven) is global . De scope wordt automatisch vooraan toegevoegd aan alle sleutels in alle bewerkingen die op de gegevensopslag worden uitgevoerd.

| Sleutel | | Scope |
| houses/User_1234 | | houses |
| pets/User_1234 | | pets |
| inventory/User_1234 | | inventory |

De combinatie van de naam van de gegevensopslag, scope en sleutel identificeert een sleutel uniek. Alle drie de waarden zijn vereist om een sleutel met een scope te identificeren. Bijvoorbeeld, u kunt een global -gescopeerde sleutel genaamd User_1234  lezen als:

```

local DataStoreService = game:GetService("DataStoreService")

local inventoryStore = DataStoreService:GetDataStore("PlayerInventory")

local success, currentGold = pcall(function()

  return inventoryStore:GetAsync("User_1234")

end)

```

Als de sleutel User_1234  echter een scope van gold  heeft, kunt u deze alleen lezen als:

```

local DataStoreService = game:GetService("DataStoreService")

local inventoryStore = DataStoreService:GetDataStore("PlayerInventory", "gold")

local success, currentGold = pcall(function()

  return inventoryStore:GetAsync("User_1234")

end)

```

### [AllScopes-eigenschap](#allscopes-eigenschap)[](#allscopes-eigenschap)

[DataStoreOptions](/docs/nl-nl/reference/engine/classes/DataStoreOptions)  bevat een [AllScopes](/docs/nl-nl/reference/engine/classes/DataStoreOptions#AllScopes)  eigenschap die u in staat stelt om sleutels uit alle [scopes](#scopes)  in een lijst terug te geven. U kunt vervolgens de [KeyName](/docs/nl-nl/reference/engine/classes/DataStoreKey#KeyName)  eigenschap van een lijstitem gebruiken voor algemene gegevensopslagoperaties zoals [gegevens lezen](/docs/nl-nl/cloud-services/data-stores#reading-data)  met [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  en [gegevens verwijderen](/docs/nl-nl/cloud-services/data-stores#removing-data)  met [RemoveAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#RemoveAsync) .

Wanneer u de AllScopes -eigenschap gebruikt, moet de tweede parameter van [GetDataStore()](/docs/nl-nl/reference/engine/classes/DataStoreService#GetDataStore)  een lege string ("" ) zijn.

```

local DataStoreService = game:GetService("DataStoreService")

local options = Instance.new("DataStoreOptions")

options.AllScopes = true

local ds = DataStoreService:GetDataStore("DS1", "", options)

```

Wanneer u de [AllScopes](/docs/nl-nl/reference/engine/classes/DataStoreOptions#AllScopes)  eigenschap gebruikt, retourneert [ListKeysAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListKeysAsync)  elke sleutel met hun scope als het voorvoegselargument, zoals global/player_data_1234  of houses/house3 . Vergeet niet dat de standaard scope global  is.

Als u de [AllScopes](/docs/nl-nl/reference/engine/classes/DataStoreOptions#AllScopes)  eigenschap inschakelt en een nieuwe sleutel in de gegevensopslag maakt, moet u altijd een scope voor die sleutel opgeven in het formaat van scope/sleutelnaam. Als u dat niet doet, geven de API's een foutmelding. Bijvoorbeeld, gold/player_34545  is acceptabel met gold als de scope, maar player_34545  leidt tot een fout.

| global/K1 | | house/K1 |
| global/L2 | | house/L2 |
| global/M3 | | house/M3 |

## [Caching](#caching)[](#caching)

Gebruik caching om tijdelijk gegevens van gegevensopslag op te slaan om de prestaties te verbeteren en het aantal verzoeken aan de server te verminderen. Bijvoorbeeld, een spel kan een kopie van zijn gegevens cachen zodat het die gegevens snel kan openen zonder een andere oproep naar de gegevensopslag te hoeven doen.

Caching is van toepassing op wijzigingen die u aanbrengt in sleutels van gegevensopslag met behulp van:

-

[GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  om [gegevens te lezen](/docs/nl-nl/cloud-services/data-stores#reading-data) .

-

[SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync)  om [gegevens te creëren](/docs/nl-nl/cloud-services/data-stores#creating-data) .

-

[UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  om [gegevens bij te werken](/docs/nl-nl/cloud-services/data-stores#updating-data) .

-

[IncrementAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#IncrementAsync)  om [gegevens te verhogen](/docs/nl-nl/cloud-services/data-stores#incrementing-data) .

-

[RemoveAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#RemoveAsync)  om [gegevens te verwijderen](/docs/nl-nl/cloud-services/data-stores#removing-data) .

[GetVersionAsync()](/docs/nl-nl/reference/engine/classes/DataStore#GetVersionAsync) , [ListVersionsAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListVersionsAsync) , [ListKeysAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListKeysAsync) , en [ListDataStoresAsync()](/docs/nl-nl/reference/engine/classes/DataStoreService#ListDataStoresAsync)  implementeren geen caching en halen altijd de nieuwste gegevens van de service-backend op.

Standaard gebruikt de engine [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  om waarden die u van de backend ophaalt vier seconden in een lokale cache op te slaan. Ook standaard retourneren [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  verzoeken voor gecachte sleutels de gecachte waarde in plaats van door te gaan naar de backend. Uw [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  verzoeken die een gecachte waarde retourneren tellen niet mee voor uw [serverlimieten](/docs/nl-nl/cloud-services/data-stores/error-codes-and-limits#server-limits)  en [doorvoerlijsten](/docs/nl-nl/cloud-services/data-stores/error-codes-and-limits#doorvoerlimieten) .

Alle [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  aanroepen die een waarde ophalen die niet in de cache wordt opgeslagen, werken de cache onmiddellijk bij en starten de timer van vier seconden opnieuw.

Caching is lokaal voor een specifieke instantie van gegevensopslag, zodat verschillende gegevensopslag hun caches in verschillende staten kunnen hebben. Bijvoorbeeld, als u een sleutel twee keer benadert via twee verschillende instanties van gegevensopslag, zoals het verkrijgen van één gegevensopslag met een opgegeven scope en een andere door de [AllScopes](/docs/nl-nl/reference/engine/classes/DataStoreOptions#AllScopes)  eigenschap in te schakelen, heeft elke instantie van gegevensopslag zijn eigen cache. Als u de waarde van die sleutel in de ene instantie van gegevensopslag wijzigt en niet in de andere, eindigt u met inconsistente gegevens.

### [Caching uitschakelen](#caching-uitschakelen)[](#caching-uitschakelen)

Om caching uit te schakelen en ervoor te zorgen dat de meest actuele waarde van de servers wordt opgehaald, voegt u de [DataStoreGetOptions](/docs/nl-nl/reference/engine/classes/DataStoreGetOptions)  parameter toe aan uw [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  oproep en stelt u de [UseCache](/docs/nl-nl/reference/engine/classes/DataStoreGetOptions#UseCache)  eigenschap in op false  om uw verzoek te laten negeren voor alle sleutels in de cache.

Het uitschakelen van caching is nuttig als u meerdere servers heeft die met hoge frequentie naar een sleutel schrijven en de laatste waarde van de servers moet ophalen. Het kan echter ervoor zorgen dat u meer van uw [gegevensopslaglimieten en -quota](/docs/nl-nl/cloud-services/data-stores/error-codes-and-limits#limieten)  verbruikt, aangezien [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  verzoeken die caching omzeilen altijd meetellen voor uw doorvoer- en serverlimieten.

Voor onmiddellijke verificatie-lezingen na een schrijfopdracht, gebruikt u [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  met DataStoreGetOptions.UseCache = false . Standaard gebruikt [GetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#GetAsync)  een lokale cache van vier seconden, zodat een normale verificatie-leesopdracht verouderde gegevens kan retourneren.

Dit is vooral belangrijk na schrijfoperaties zoals [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync) , [SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync) , [IncrementAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#IncrementAsync) , of [RemoveAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#RemoveAsync)  die een fout retourneren. In deze gevallen moet uw code bepalen of het moet opnieuw proberen, terugbetalen of andere corrigerende maatregelen moet nemen.

Het volgende voorbeeld toont hoe u de cache kunt omzeilen bij het verifiëren van het resultaat van een schrijfopdracht:

```

local ok = pcall(function()

    store:UpdateAsync(key, transform)

end)

if not ok then

    local options = Instance.new("DataStoreGetOptions")

    options.UseCache = false

    local success, value = pcall(function()

        return store:GetAsync(key, options)

    end)

    if success then

        -- beslis op basis van de backendstatus, niet de gecachte status

    end

end

```

## [Serialisatie](#serialisatie)[](#serialisatie)

De [DataStoreService](/docs/nl-nl/reference/engine/classes/DataStoreService)  slaat gegevens op in JSON-indeling. Wanneer u Luau-gegevens in Studio opslaat, gebruikt Roblox een proces dat serialisatie wordt genoemd om die gegevens om te zetten in JSON om ze in gegevensopslag op te slaan. Roblox zet uw gegevens vervolgens terug naar Luau en retourneert ze aan u in een ander proces dat deserialisatie wordt genoemd.

Serialisatie en deserialisatie ondersteunen de volgende Luau-gegevens typen:

-

[Nil](/docs/nl-nl/luau/nil)

-

[Booleans](/docs/nl-nl/luau/booleans)

-

[Getallen](/docs/nl-nl/luau/numbers)

-

U moet de speciale numerieke waarden inf , -inf  en nan  niet opslaan, omdat deze waarden niet voldoen aan de JSON-normen. Wanneer u een invoer met deze waarden via Open Cloud ophaalt, worden ze in de respons weergegeven als getagde JSON-objecten. Voor details, zie [Niet-finite getallen](/docs/nl-nl/cloud/guides/data-stores#niet-eindige-getallen) .

-

[Strings](/docs/nl-nl/luau/strings)

-

[Tabellen](/docs/nl-nl/luau/tables)

-

Tabellen mogen alleen andere ondersteunde gegevenstypen bevatten

-

Numerieke sleutels worden omgezet in strings als de lengte van de tabel 0 is

-

[Buffers](/docs/nl-nl/reference/engine/libraries/buffer)

Als u probeert een gegevenstype op te slaan dat serialisatie niet ondersteunt, dan:

-

Faalt u in het opslaan van dat gegevenstype en krijgt u een foutmelding.

-

Slaagt u in het opslaan van dat gegevenstype als nil .

Om te debuggen waarom uw gegevenstype als nil  wordt opgeslagen, kunt u de [JSONEncode](/docs/nl-nl/reference/engine/classes/HttpService#JSONEncode)  functie gebruiken. Wanneer u uw Luau-gegevenstype in deze functie doorgeeft, ontvangt u het terug in het formaat waarin Roblox het zou hebben opgeslagen met gegevensopslag, wat u in staat stelt om de geretourneerde gegevens te bekijken en te onderzoeken.

Serialisatie vindt niet plaats wanneer u de [DataStore Open Cloud API](/docs/nl-nl/cloud/reference/DataStore)  gebruikt, omdat die gegevens al in JSON-indeling naar Roblox zijn verzonden en niet hoeven te worden geconverteerd.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
