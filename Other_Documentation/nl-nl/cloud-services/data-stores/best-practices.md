<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/data-stores/best-practices -->

Beste praktijken voor datastores | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Gegevensopslag](/docs/nl-nl/cloud-services/data-stores)

# Beste praktijken voor datastores

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Gebruik deze praktijken om betrouwbare, schaalbare en observeerbare gegevens gedurende de hele levenscyclus te organiseren en te beheren.

## [Organiseer je gegevens](#organiseer-je-gegevens)[](#organiseer-je-gegevens)

### [Maak minder datastores](#maak-minder-datastores)[](#maak-minder-datastores)

Datastores gedragen zich vergelijkbaar als tabellen in databases. Gebruik een kleine, vaste set datastores en organiseer records binnen deze datastores op sleutel. Bewaar bijvoorbeeld het profiel van elke speler in één PlayerData  datastore in plaats van een datastore voor elke speler te creëren.

### [Gebruik één of enkele sleutels per speler](#gebruik-één-of-enkele-sleutels-per-speler)[](#gebruik-één-of-enkele-sleutels-per-speler)

Bewaar de persistente gegevens voor elke speler onder één sleutel, wanneer de gegevens binnen de [4 MB objectgrootte limiet](/docs/nl-nl/cloud-services/data-stores/error-codes-and-limits#gegevenslimieten)  passen. Gebruik bijvoorbeeld een sleutel zoals User_123456  in de PlayerData  datastore. Dit patroon vermindert verzoeken, stelt je in staat om gerelateerde waarden atomisch bij te werken en maakt rollbacks gemakkelijker te begrijpen.

Als verschillende delen van de gegevens van een speler verschillende toegangspatronen hebben of de per-sleutel grootte- of doorvoerlijsten benaderen, splits dan het record in een klein aantal deterministische sleutels. Houd gegevens die atomisch moeten veranderen in dezelfde sleutel.

### [Gebruik statische sleutelpatronen en -voorvoegsels](#gebruik-statische-sleutelpatronen-en--voorvoegsels)[](#gebruik-statische-sleutelpatronen-en--voorvoegsels)

Bouw sleutelnamen op uit stabiele identificatoren en statische patronen, zoals User_{UserId} . Gebruik geen weergavenamen of andere waarden die kunnen veranderen. Statische patronen maken sleutels voorspelbaar over servers en tooling. Voor datastores laten ze ook [geautomatiseerde verwerking van het recht om vergeten te worden](/docs/nl-nl/cloud-services/data-stores/right-to-be-forgotten)  spelergegevens identificeren.

Gebruik [voorvoegsels](/docs/nl-nl/cloud-services/data-stores/versioning-listing-and-caching#opsommen-en-voorvoegsels)  om gerelateerde sleutels te groeperen. Een ervaring die meerdere karakterprofielen ondersteunt, kan bijvoorbeeld User_123456/Profile/Warrior  en User_123456/Profile/Mage  gebruiken. Je kunt dan User_123456/Profile  doorgeven aan [ListKeysAsync()](/docs/nl-nl/reference/engine/classes/DataStore#ListKeysAsync)  om de profielen van die speler te lijsten.

[Scopes](/docs/nl-nl/cloud-services/data-stores/versioning-listing-and-caching#scopes)  zijn een andere manier om een datastore te subdivideren. Een scope voegt een string toe aan elke sleutel in die datastore-instantie, en de standaard is global .

### [Evalueer datastores-modules](#evalueer-datastores-modules)[](#evalueer-datastores-modules)

Derde partij datastores-modules zijn altijd een optie, en in veel gevallen kunnen ze de voorkeur hebben boven het bouwen van systemen vanaf nul. Voordat je er een aanneemt, bekijk de eigendom, onderhoudstatus en functies. Begrijp hoe je toegang krijgt tot en je gegevens migreert zonder de module.

DataStore2 is een verouderde derde partij bibliotheek en je zou deze niet moeten gebruiken voor nieuwe ervaringen. Als je ervaring momenteel DataStore2 gebruikt, gebruik dan Roblox's officiële [beta DataStore2 migratietool](https://create.roblox.com/store/asset/82521207271039/BETA-DataStore2-Migration-Tool)  om te migreren van het één-datastore-per-speler patroon.

## [Verminder en verdeel verzoeken](#verminder-en-verdeel-verzoeken)[](#verminder-en-verdeel-verzoeken)

### [Buffers spelergegevens in het geheugen](#buffers-spelergegevens-in-het-geheugen)[](#buffers-spelergegevens-in-het-geheugen)

Laad de gegevens van een speler aan het begin van een sessie en houd een server-lokale kopie voor gameplay. Werk de lokale kopie bij in plaats van voor elke wijziging een verzoek naar de datastore te sturen. Sla het periodiek op, wanneer de speler vertrekt, wanneer de server afsluit, en op kritieke controlepunten zoals aankoopverwerking. Kies een periodieke opsla-intervallen die binnen je verzoeklimieten blijft en korter is dan elke sessie-lock vervalt; de [voorbeeld van spelergegevens en aankopen](/docs/nl-nl/cloud-services/data-stores/player-data-purchasing)  gebruikt 180 seconden.

### [Verspreid terugkerende verzoeken](#verspreid-terugkerende-verzoeken)[](#verspreid-terugkerende-verzoeken)

Begin geen terugkerende verzoeken vanaf elke server op hetzelfde schema. Voordat je een vaste frequentielus start, wijs je elke server of speler een willekeurige initiële offset toe. Voor polling of coördinatielussen die geen exacte cadans vereisen, voeg begrensde willekeurige jitter toe aan elk interval. Deze patronen verdelen verzoeken over de tijd en verminderen gesynchroniseerde verkeerspieken.

### [Herhaal tijdelijke fouten](#herhaal-tijdelijke-fouten)[](#herhaal-tijdelijke-fouten)

Wikkel verzoeken in [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  en herhaal tijdelijke fouten met exponentiële backoff. Voeg willekeurige jitter toe aan elke vertraging zodat servers niet gelijktijdig opnieuw proberen. Beperk de vertraging en het aantal pogingen, en herhaal geen fouten die zijn veroorzaakt door ongeldige verzoeken of bewerkingen die geen nuttige resultaten meer kunnen opleveren.

Verwerk herhalingen van datastores in volgorde voor elke sleutel. Een ouder verzoek dat opnieuw probeert nadat een nieuwer verzoek is geslaagd, kan nieuwere gegevens overschrijven. Houd ook rekening met schrijfacties met onbekende uitkomsten: een mislukte oproep betekent dat de server geen succesvolle reactie heeft ontvangen, maar de backend kan de schrijfactie hebben voltooid. Voor meer informatie, zie [Foutcodes en limieten van datastores](/docs/nl-nl/cloud-services/data-stores/error-codes-and-limits)  en [Herhalingen](/docs/nl-nl/cloud-services/data-stores/player-data-purchasing#retries) .

### [Geef de voorkeur aan UpdateAsync boven SetAsync](#geef-de-voorkeur-aan-updateasync-boven-setasync)[](#geef-de-voorkeur-aan-updateasync-boven-setasync)

Geef de voorkeur aan [UpdateAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#UpdateAsync)  wanneer een schrijfactie afhankelijk is van de huidige waarde of wanneer meerdere servers mogelijk dezelfde sleutel schrijven. UpdateAsync()  leest de laatste waarde in je callback voordat het schrijft, wat verloren updates vermindert. [SetAsync()](/docs/nl-nl/reference/engine/classes/GlobalDataStore#SetAsync)  overschrijft de sleutel zonder eerst te lezen en kan inconsistentie veroorzaken als twee servers tegelijkertijd schrijven.

Gebruik SetAsync()  wanneer je een nieuwe sleutel maakt of een waarde vervangt die niet afhankelijk is van de vorige waarde. Voor een vergelijking van de twee methoden, zie [Set vs update](/docs/nl-nl/cloud-services/data-stores#instellen-versus-bijwerken) .

### [Shard hete sleutels](#shard-hete-sleutels)[](#shard-hete-sleutels)

Elke sleutel heeft [lees- en schrijfdoorvoerlijsten](/docs/nl-nl/cloud-services/data-stores/error-codes-and-limits#doorvoerlimieten) . Voor gedeelde gegevens die veel servers lezen maar zelden bijwerken, verdeel je de leesacties over meerdere sleutels die kopieën van hetzelfde record bevatten. Gebruik deze aanpak alleen om per-sleutel lees-throttling  aan te pakken, nadat je onnodige verzoeken hebt verminderd. Het lost geen schrijf-throttling op of verhoogt de verzoekbudgetten op ervarings- of serverniveau.

Overweeg bijvoorbeeld een Admin Misbruik  evenement dat het Weer  in een ervaring verandert. Als elke server het huidige weer van een enkele Weather  sleutel leest, kan die sleutel zijn leesdoorvoerlijst bereiken, ook al verandert het weer zelden. Bewaar in plaats daarvan kopieën onder een vaste set sleutels zoals Weather_1 , Weather_2 , en Weather_3 . Wijs elke server een shard toe bij opstarten, bijvoorbeeld door zijn [DataModel.JobId](/docs/nl-nl/reference/engine/classes/DataModel#JobId)  in de vaste set te hashen, zodat de leesacties over de sleutels verspreid worden. Elke server leest alleen zijn toegewezen kopie.

Bij het polleren van gedeelde sleutels, inclusief weerkopieën, voeg een willekeurige initiële vertraging toe voordat de eerste lezing en begrensde willekeurige jitter tussen de daaropvolgende lezingen. Kies een pollinginterval dat in balans is met hoe snel servers wijzigingen moeten waarnemen met de leesdoorvoerlijst. Vermijd dat elke server tegelijkertijd leest, zoals onmiddellijk na een gedeelde evenementmelding. Voor meer informatie, zie [Verspreid terugkerende verzoeken](#verspreid-terugkerende-verzoeken) .

Wanneer het weer verandert, werk dan elke kopie bij. Deze schrijfacties zijn niet atomisch over sleutels, dus servers kunnen tijdelijk verschillende weersomstandigheden lezen. Het repliceren van het record voegt schrijfacties toe en maakt consistentie en toekomstige migraties complexer. Gebruik deze aanpak niet voor gegevens die atomische updates over alle lezers vereisen of al onder de per-sleutel leesdoorvoerlijst blijven.

## [Bouw een operationele workflow](#bouw-een-operationele-workflow)[](#bouw-een-operationele-workflow)

Gebruik de beschikbare tools samen:

1.

Observeer.  Gebruik het [Data Stores Observability Dashboard](/docs/nl-nl/cloud-services/data-stores/observability)  om verzoeken, responsstatus, doorvoer en opslag bij te houden. Configureer [aangepaste waarschuwingen](/docs/nl-nl/production/analytics/alerts)  voor belangrijke datastore-metrics, zodat je team kan reageren op aanhoudende fouten of onverwachte groei. Meldingen van de Creator Hub laten je ook weten wanneer opslag de limieten nadert of overschrijdt en bevatten richtlijnen en links naar dashboards.

2.

Inspecteer.  Gebruik [Data Stores Manager](/docs/nl-nl/cloud-services/data-stores/data-stores-manager)  om datastores, sleutels, opslaggebruik en geschatte kosten te onderzoeken. Als de ervaring meer dan 100 datastores heeft, toont de lijst met datastores geen grootte- en sleutelcounts. Gebruik Open Cloud of de [Data Stores Batch Processor](https://github.com/Roblox/data-stores-batch-processor-cli)  voor die metrics.

3.

Herstel.  Gebruik Data Stores Manager voor individuele records. Gebruik de [Open Cloud datastore API's](/docs/nl-nl/cloud/guides/data-stores)  of [Data Stores Batch Processor](https://github.com/Roblox/data-stores-batch-processor-cli)  voor herhaalbare of grootschalige workflows.

4.

Schaal opzettelijk.  Verminder eerst onnodige opslag en verzoeken. Als legitiem gebruik de standaardquota overschrijdt, evalueer dan [Extended Services](/docs/nl-nl/cloud-services/extended-services) .

Open Cloud en game-servers delen het verzoekbudget op ervaringsniveau. Beperk operationele Open Cloud-scripts zodat ze de live verkeersstroom niet verstoren.

## [Beheer de gegevenslevenscyclus](#beheer-de-gegevenslevenscyclus)[](#beheer-de-gegevenslevenscyclus)

Gebruik versies van datastores in plaats van voor elke revisie een nieuwe sleutel te creëren. Alleen de laatste versie van een sleutel telt mee voor het opslaggebruik, en versies stellen je in staat om eerdere waarden te inspecteren of te herstellen.

Gebruik [geheugenstoren](/docs/nl-nl/cloud-services/memory-stores)  voor tijdelijke en snel veranderende gegevens. Gegevens in geheugenstoren vervallen automatisch en voegen geen opslag toe aan persistente datastores.

Verwijder testgegevens wanneer de tests eindigen en verwijder gegevens voor verlopen evenementen of gepensioneerde functies. Nadat je een datastore voor verwijdering hebt gemarkeerd, is er een buffer van 30 dagen waarin je deze kunt herstellen. Na die 30 dagen verwijdert Roblox de datastore permanent. Voor meer informatie, zie [Data Stores Manager](/docs/nl-nl/cloud-services/data-stores/data-stores-manager#verwijder-datastores-en-sleutels) .

## [Stel verwerking van het recht om vergeten te worden in](#stel-verwerking-van-het-recht-om-vergeten-te-worden-in)[](#stel-verwerking-van-het-recht-om-vergeten-te-worden-in)

Configureer [geautomatiseerde verwerking van het recht om vergeten te worden (RTBF)](/docs/nl-nl/cloud-services/data-stores/right-to-be-forgotten)  voor spelergegevens die volgen op statische datastore- en sleutelpatronen. Geautomatiseerde RTBF is de voorkeursworkflow omdat Roblox je verwijderingssjablonen toepast wanneer het een in aanmerking komend verzoek verwerkt.

Als geautomatiseerde RTBF je dataschema niet ondersteunt, gebruik dan de [recht-op-verwijdering webhook](/docs/nl-nl/cloud/webhooks/automate-right-to-erasure)  om een aangepaste verwijderworkflow uit te voeren. Zorg ervoor dat beide workflows alle overeenkomende spelergegevens verwijderen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
