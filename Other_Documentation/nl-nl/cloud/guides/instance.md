<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/guides/instance -->

Engine-instanties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Engine-instanties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Engine Open Cloud API's stellen je in staat om [Instance](/docs/nl-nl/reference/engine/classes/Instance)  objecten in je Roblox-spellen vanaf het web te beheren.

## [Bèta-beperkingen](#bèta-beperkingen)[](#bèta-beperkingen)

Deze API's zijn momenteel in bèta en hebben de volgende beperkingen:

-

Je kunt alleen [Script](/docs/nl-nl/reference/engine/classes/Script) , [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) , en [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  objecten lezen en bijwerken.

-

Je kunt scripts die momenteel open zijn in Roblox Studio niet bijwerken.

-

Je kunt scripts die deel uitmaken van een [pakket](/docs/nl-nl/projects/assets/packages)  niet bijwerken.

-

Je kunt alleen API-sleutelauthenticatie gebruiken. Maak een [API-sleutel](/docs/nl-nl/cloud/auth/api-keys)  met universe-place-instances  toegevoegd als een API-systeem.

Je moet de spellen specificeren waartoe je wilt dat de sleutel toegang heeft, evenals de gewenste lees- en schrijfrechten.

![Het Creator Hub API-sleutelscherm](https://prod.docsiteassets.roblox.com/assets/open-cloud/instance-api.png)

-

Je moet een [samenwerkings](/docs/nl-nl/projects/collaboration)  sessie ingeschakeld hebben voor het spel dat je wilt openen.

-

Verzoeklichamen, zoals voor [Update Instance](/docs/nl-nl/cloud/reference/Instance#Cloud_UpdateInstance) , zijn beperkt tot 200 KB.

## [Lijst kinderen](#lijst-kinderen)[](#lijst-kinderen)

Lijst alle kinderen van een specifieke instantie door een instantie-ID op te geven en de [List Instance Children](/docs/nl-nl/cloud/reference/Instance#Cloud_ListInstanceChildren)  methode aan te roepen.

De eerste keer dat je deze methoden gebruikt, geef je root  op voor de instantie-ID. Nadat je de lijst met top-level kinderen en hun ID's hebt ontvangen, kun je aanvullende aanroepen doen om instanties dieper binnen de hiërarchie van instanties van je plaats te vinden.

Python cURL

```

import requests

# Genereer op https://create.roblox.com/dashboard/credentials

apiKey = "<API_KEY>"

# Vind op https://create.roblox.com/dashboard/creations in het overflow-menu van een speltegel

universeId = "<UNIVERSE_ID>"

# Vind Start Plaats ID op https://create.roblox.com/dashboard/creations in het overflow-menu van een speltegel

placeId = "<PLACE_ID>"

# De standaard-ID voor de root van elk datamodel van een plaats

instanceId = "root"

# Verzoekheader

apiKeyHeaderKey = "x-api-key"

# Eindpunt-URL voor de List Children-methode

listChildrenUrl = "https://apis.roblox.com/cloud/v2/universes/%s/places/%s/instances/%s:listChildren"

def ListChildren():

  url = listChildrenUrl % (universeId, placeId, instanceId)

  headerData = {apiKeyHeaderKey: apiKey}

  results = requests.get(url, headers = headerData)

  return results

response = ListChildren()

print("Operation Results:", response.status_code, response.text)

# Parse het pad van het Operation-object om later de Instance-resource te verkrijgen. Zie de sectie Polling for Results voor meer informatie.

operationPath = response.json()['path']

```

In plaats van alleen de kinderen op te sommen, bevat de reactie een Operation  object met een ander eindpunt. [Poll dit eindpunt](#poll-for-results)  om asynchroon de werkelijke lijst van kinderen op te halen. Een completer codevoorbeeld ziet er als volgt uit:

```

import requests

import time

apiKey = "<API_KEY>"

universeId = "<UNIVERSE_ID>"

placeId = "<PLACE_ID>"

instanceId = "root"

apiKeyHeaderKey = "x-api-key"

listChildrenUrl = "https://apis.roblox.com/cloud/v2/universes/%s/places/%s/instances/%s:listChildren"

getOperationUrl = "https://apis.roblox.com/cloud/v2/%s"

numberOfRetries = 10

retryPollingCadence = 5

doneJSONKey = "done"

def ListChildren():

  url = listChildrenUrl % (universeId, placeId, instanceId)

  headerData = {apiKeyHeaderKey: apiKey}

  results = requests.get(url, headers = headerData)

  return results

def GetOperation(operationPath):

  url = getOperationUrl % (operationPath)

  headerData = {apiKeyHeaderKey: apiKey}

  results = requests.get(url, headers = headerData)

  return results

def PollForResults(operationPath):

  currentRetries = 0

  while (currentRetries < numberOfRetries):

    time.sleep(retryPollingCadence)

    results = GetOperation(operationPath)

    currentRetries += 1

    if (results.status_code != 200 or results.json()[doneJSONKey]):

      return results

response = ListChildren()

print("Operation Results:", response.status_code, response.text)

# Parse het pad van het Operation-object om te gebruiken bij het polleren voor de instantie-resource.

operationPath = response.json()['path']

response = PollForResults(operationPath)

print("Response:", response.status_code, response.text)

```

De uiteindelijke reactie kan er als volgt uitzien:

```

{

  "path": "universes/1234567890/places/98765432109/instances/root/operations/a1a2a3a4-a1a2-a1a2-a1a2-a1a2a3a4a5a6",

  "done": true,

  "response": {

    "@type": "type.googleapis.com/roblox.open_cloud.cloud.v2.ListInstanceChildrenResponse",

    "instances": [

      {

        "path": "universes/1234567890/places/98765432109/instances/b1b2b3b4-b1b2-b1b2-b1b2-b1b2b3b4b5b6",

        "hasChildren": true,

        "engineInstance": {

          "Id": "b1b2b3b4-b1b2-b1b2-b1b2-b1b2b3b4b5b6",

          "Parent": "a1a2a3a4-a1a2-a1a2-a1a2-a1a2a3a4a5a6",

          "Name": "Workspace",

          "Details": {}

        }

      },

      ...

    ]

  }

}

```

Je kunt vervolgens door de JSON itereren om een specifieke instantie-ID te vinden:

```

instances = response.json()['response']['instances']

replicatedStorageId = ""

for i in instances:

  if i['engineInstance']['Name'] == "ReplicatedStorage":

    replicatedStorageId = i['engineInstance']['Id']

if replicatedStorageId:

  # Je hebt nu een instantie-ID en kunt deze ophalen of bijwerken.

else:

  # De naam is niet gevonden.

```

Scripts bevatten enkele aanvullende informatie in het Details  object, zoals het type script, de bron en of ze zijn ingeschakeld.

## [Verkrijg een instantie](#verkrijg-een-instantie)[](#verkrijg-een-instantie)

Deze methode retourneert een enkele [Instance](/docs/nl-nl/cloud/reference/Instance) .

Python cURL

```

import requests

# Genereer op https://create.roblox.com/dashboard/credentials

apiKey = "<API_KEY>"

# Vind op https://create.roblox.com/dashboard/creations in het overflow-menu van een speltegel

universeId = "<UNIVERSE_ID>"

# Vind Start Plaats ID op https://create.roblox.com/dashboard/creations in het overflow-menu van een speltegel

placeId = "<PLACE_ID>"

# De standaard-ID voor de root van elk datamodel van een plaats

instanceId = "<INSTANCE_ID>"

# Verzoekheader

apiKeyHeaderKey = "x-api-key"

# Eindpunt-URL voor de Get Instance-methode

getInstanceUrl = "https://apis.roblox.com/cloud/v2/universes/%s/places/%s/instances/%s"

def GetInstance():

  url = getInstanceUrl % (universeId, placeId, instanceId)

  headerData = {apiKeyHeaderKey: apiKey}

  return requests.get(url, headers = headerData)

response = GetInstance()

print("Response:", response.status_code, response.text)

# Parse het pad van het Operation-object uit de reactie. Zie de sectie Polling for Results voor meer informatie.

operationPath = response.json()['path']

```

Net als de List Instance Children-methode bevat de reactie een Operation  object dat je moet polleren om de werkelijke instantie te verkrijgen. Zie [Poll for results](#poll-for-results)  voor meer informatie.

## [Update instanties](#update-instanties)[](#update-instanties)

Nadat je de juiste instantie-ID hebt verkregen, kun je deze bijwerken. [Poll for results](#poll-for-results)  na het doen van het initiële updateverzoek.

Python cURL

```

import json

import requests

# Genereer op https://create.roblox.com/dashboard/credentials

apiKey = "<API_KEY>"

# Vind op https://create.roblox.com/dashboard/creations in het overflow-menu van een speltegel

universeId = "<UNIVERSE_ID>"

# Vind Start Plaats ID op https://create.roblox.com/dashboard/creations in het overflow-menu van een speltegel

placeId = "<PLACE_ID>"

instanceId = "<INSTANCE_ID>"

instanceType = ""

propertyName = ""

propertyValue = ""

# Verzoekheader

apiKeyHeaderKey = "x-api-key"

contentTypeHeaderKey = "Content-type"

contentTypeHeaderValue = "application/json"

# Eindpunt-URL voor de Update Instance-methode

updateInstanceUrl = "https://apis.roblox.com/cloud/v2/universes/%s/places/%s/instances/%s"

# JSON-sleutels

detailsJSONKey = "Details"

engineInstanceJSONKey = "engineInstance"

def GeneratePostData():

  propertiesDict = {propertyName: propertyValue}

  detailsDict = {instanceType: propertiesDict}

  instanceDict = {detailsJSONKey: detailsDict}

  outerDict = {engineInstanceJSONKey: instanceDict}

  return json.dumps(outerDict)

def UpdateInstance(postData):

    url = updateInstanceUrl % (universeId, placeId, instanceId)

    headerData = {apiKeyHeaderKey: apiKey,

    contentTypeHeaderKey: contentTypeHeaderValue}

    return requests.patch(url, headers = headerData, data = postData)

postData = GeneratePostData()

response = UpdateInstance(postData)

print("Response:", response.status_code, response.text)

# Parse het pad van het Operation-object uit de reactie. Poll voor resultaten om de update uit te voeren.

operationPath = response.json()['path']

```

Als je een TypeError  ontvangt bij het proberen een script bij te werken, controleer dan of het script niet open is in Roblox Studio. Als dat zo is, sluit dan het tabblad Script Editor. Je kunt ook de Studio-uitvoer controleren op aanvullende fouten, zoals Engine_OC_API: Processing Error - Live scripting session is active .

## [Poll voor resultaten](#poll-voor-resultaten)[](#poll-voor-resultaten)

Alle huidige [Instance](/docs/nl-nl/cloud/reference/Instance)  methoden retourneren een Operation  object in plaats van de resource die je hebt aangevraagd. Dit object stelt je in staat om asynchroon de oorspronkelijke bewerking uit te voeren. Gebruik het pad van het Operation  object (inbegrepen in de initiële reactie) om te polleren wanneer de resource gereed is.

Je kunt verschillende pollstrategieën gebruiken, zoals het gebruik van exponentiële backoff of een vaste vertraging tussen verzoeken. Het volgende voorbeeld pollt elke vijf seconden, tot 10 keer.

Python cURL

```

import requests

import time

# Genereer op https://create.roblox.com/dashboard/credentials

apiKey = "<API_KEY>"

# Gebruik het Operation-pad van je initiële verzoek

# Heeft de vorm van "universes/<UNIVERSE_ID>/places/<PLACE_ID>/instances/<INSTANCE_ID>/operations/<OPERATION_ID>"

operationPath = "<OPERATION_PATH>"

# Polling constanten

numberOfRetries = 10

retryPollingCadence = 5

# Verzoekheader

apiKeyHeaderKey = "x-api-key"

# Eindpunt-URL voor polling van langdurige operaties

getOperationUrl = "https://apis.roblox.com/cloud/v2/%s"

# JSON-sleutels

doneJSONKey = "done"

def GetOperation(operationPath):

  url = getOperationUrl % (operationPath)

  headerData = {apiKeyHeaderKey: apiKey}

  results = requests.get(url, headers = headerData)

  return results

def PollForResults(operationPath):

  currentRetries = 0

  while (currentRetries < numberOfRetries):

    time.sleep(retryPollingCadence)

    results = GetOperation(operationPath)

    currentRetries += 1

    if (results.status_code != 200 or results.json()[doneJSONKey]):

      return results

response = PollForResults(operationPath)

print("Response:", response.status_code, response.text)

```

## [Potion Shop-demo](#potion-shop-demo)[](#potion-shop-demo)

De Potion Shop Google Sheets-demo laat je zien hoe je een script van een spel vanaf het web kunt bijwerken. De demo bestaat uit het volgende:

-

Een niet-gekopieerde plaats met een nep-UI die verschillende toverdranken en hun prijzen weergeeft.

-

Een .ods  bestand dat je importeert in Google Sheets. Deze spreadsheet stelt je in staat om waarden voor eigenschappen binnen het spel op te geven en bij te werken.

-

Code voor een Google Apps Script dat gegevens uit de Google Sheet leest en het ReplicatedStorage > ItemList  script in het Potion Shop-spel bijwerkt.

### [Stel de demo in](#stel-de-demo-in)[](#stel-de-demo-in)

1.

Ga naar de [Potion Shop Demo](https://www.roblox.com/games/14215142052/Potion-Shop-Demo)  Discover-pagina. Klik op het overflow-menu en klik vervolgens op Bewerken in Studio . Studio opent met een kopie van de plaats.

2.

Klik op Bestand  → Opslaan naar Roblox  en vul de benodigde informatie in om de Potion Shop Demo als de standaardplaats voor je spel op te slaan. Test het spel. Je zou de UI voor de Potion Shop Demo moeten zien. Maak een notitie van de naam, kosten en kleuren van de toverdranken. Je zult ze later wijzigen met Open Cloud!

### [Stel de sheet in](#stel-de-sheet-in)[](#stel-de-sheet-in)

1.

[Download](https://prod.docsiteassets.roblox.com/assets/open-cloud/open-cloud-potion-shop-demo.ods)  het Potion Shop spreadsheetbestand.

2.

Ga naar [Google Sheets](https://sheets.google.com/)  en klik op Lege Spreadsheet .

3.

In de sheet die verschijnt, klik op Bestand > Importeren , en klik op het Uploaden  tabblad.

4.

Sleep het Potion Shop spreadsheetbestand in het uploadvenster.

5.

Kies Spreadsheet vervangen  en klik vervolgens op Gegevens importeren .

6.

In het AppScript-tabblad van de sheet, kopieer de code in cel A1.

7.

Klik op het menu Extensies > Apps Script  en plak de code in het Code.gs  bestand. Sla vervolgens het project op.

8.

Terug in de spreadsheet, selecteer het Update Potion Shop  tabblad. Klik op de Update Script  knop, klik op het overflow-menu en selecteer Script toewijzen .

9.

Voer in het venster Script toewijzen  UpdateScript  in en klik op OK .

### [Maak een API-sleutel](#maak-een-api-sleutel)[](#maak-een-api-sleutel)

1.

Ga naar de [Creator Hub Open Cloud API-sleutels](https://create.roblox.com/dashboard/credentials?activeTab=ApiKeysTab)  pagina en klik op API-sleutel maken .

2.

Vul het formulier in met de volgende informatie.

-

Naam : PotionShop

-

API-systeem : Voeg het universe-place-instances  API-systeem toe. Voeg je Potion Shop-spel toe aan het systeem. Voor Experience Operations , voeg lees- en schrijfrechten toe.

-

Geaccepteerde IP-adressen : Voeg 0.0.0.0/0 toe als IP-adres

-

Vervaldatum : Geen vervaldatum

-

Klik op Opslaan & Sleutel genereren  en klik vervolgens op Sleutel naar klembord kopiëren .

3.

Plak de API-sleutel in de API-sleutelcel (D2) op het Intro-tabblad van je Google Sheet.

### [Verkrijg de universum- en plaats-ID](#verkrijg-de-universum--en-plaats-id)[](#verkrijg-de-universum--en-plaats-id)

1.

Ga naar de [Creator Hub Creations](https://create.roblox.com/dashboard/creations)  pagina, beweeg over de speltegel van de Potion Shop en klik op het overflow-menu.

2.

Selecteer Kopieer Universum-ID  en plak deze in de Universum-ID  cel (E2) op het Intro-tabblad van je Google Sheet.

3.

Selecteer Kopieer Start Plaats-ID  en plak deze in de Plaats-ID  cel (F2) op het Intro-tabblad van je Google Sheet.

### [Werk de scriptwaarden bij](#werk-de-scriptwaarden-bij)[](#werk-de-scriptwaarden-bij)

1.

In het Update Potion Shop  tabblad van de sheet, wijzig eventuele waarden die je wilt en klik op de Update Script  knop.

2.

Als Google Sheets je om autorisatie vraagt, klik dan op OK  en sta je account toe om het script uit te voeren.

3.

Test in Studio de Potion Shop om eventuele weerspiegelde wijzigingen te zien. Vanuit het Explorer  venster kun je ook het ReplicatedStorage > ItemList  script openen om de wijzigingen te inspecteren.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
