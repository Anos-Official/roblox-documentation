<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/secrets -->

Geheimenopslag | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)

# Geheimenopslag

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox biedt een geheimen  opslag voor elke game. Geheimen zijn gevoelige informatie zoals API-sleutels, wachtwoorden en toegangstokens die je gebruikt om te authenticeren met externe services. Als je bijvoorbeeld verbinding wilt maken met een externe analyse- of muziekdienst, moet je waarschijnlijk een API-sleutel gebruiken om je daarmee te authentiseren.

Je zou de API-sleutel in een script kunnen kopiëren en plakken of deze aan een gegevensopslag kunnen toevoegen, maar die benaderingen brengen onnodige beveiligingsrisico's met zich mee. De betere oplossing is om de geheimenopslag te gebruiken en de sleutel te benaderen met een kleine set veilige methoden.

## [Geheimen toevoegen](#geheimen-toevoegen)[](#geheimen-toevoegen)

Om geheimen te bekijken, te maken of te bewerken, moet je de eigenaar van de game of groeps eigenaar zijn. Je kunt tot 500 geheimen per game hebben.

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Selecteer je game en selecteer vervolgens Geheimen  ⟩ Geheim maken .

3.

Voer een naam, het geheim en het toepasselijke domein in.

-

De naam fungeert als een unieke identifier voor het geheim, dus we raden iets beschrijvends aan.

-

Geheimen kunnen tot 1.024 tekens lang zijn. API-sleutels en toegangstokens moeten van de serviceprovider komen, maar als het geheim een wachtwoord is, heb je het waarschijnlijk zelf aangemaakt.

-

Je kunt een beperkte wildcard-syntaxis voor het domein gebruiken, zoals *  voor elk domein (niet aanbevolen) of *.example.com  voor elke subdomein op example.com . Specifieke domeinen zijn nog beter, zoals my.example.com .

Je kunt ook Open Cloud gebruiken om je geheimen te beheren. Zie de [referentiedocumentatie](/docs/nl-nl/cloud/reference/features/universes#get_cloud_v2_universes__universeId__secrets)  en [gids](/docs/nl-nl/cloud/guides/secrets-store) .

## [Lokale geheimen](#lokale-geheimen)[](#lokale-geheimen)

Om beveiligingsredenen is de geheimenopslag voor elke game alleen beschikbaar voor live servers of [samenwerkende test](/docs/nl-nl/studio/testing-modes#samenwerkend-testen)  omgevingen. Als je probeert toegang te krijgen tot een geheim tijdens [lokale playtesting](/docs/nl-nl/studio/testing-modes#spelen-testen) , ontvang je een Kan geheim met gegeven sleutel niet vinden  foutmelding. Je ontvangt een identieke fout als je probeert geheimen vanuit een clientscript te benaderen.

Om geheimen voor lokale tests op te geven, ga je naar Studio en vervolgens naar Bestand  ⟩ Ervaringsinstellingen  ⟩ Beveiliging . Je kunt nieuwe geheimen maken en bestaande geheimen bewerken of verwijderen in de sectie Lokale Geheimen .

## [Geheimen gebruiken](#geheimen-gebruiken)[](#geheimen-gebruiken)

Voordat je geheimen binnen je game kunt gebruiken, moet je HTTP-verzoeken toestaan  inschakelen in de sectie Beveiliging  van het venster Bestand  ⟩ Ervaringsinstellingen  van Studio. Roep vervolgens [HttpService:GetSecret()](/docs/nl-nl/reference/engine/classes/HttpService#GetSecret)  aan binnen een serverscript:

```

local HttpService = game:GetService("HttpService")

local testSecret = HttpService:GetSecret("test_secret")

```

Een deel van de aantrekkingskracht van het gebruik van geheimenopslag is dat je per ongeluk een geheim niet kunt afdrukken. In plaats van het geheim zelf, geeft de volgende code de naam weer die je hebt opgegeven bij het maken van het geheim:

```

print(testSecret) --> Geheim(test_secret)

```

Je kunt de string niet direct manipuleren. In plaats daarvan laat het datatype [Secret](/docs/nl-nl/reference/engine/datatypes/Secret)  je een prefix en suffix aan het geheim toevoegen om te helpen bij het vormen van een URL of om inhoud zoals Bearer  in te voegen:

```

local HttpService = game:GetService("HttpService")

local testSecret = HttpService:GetSecret("test_secret")

local prefix = "https://my.example.com/endpoint?apiKey="

local suffix = "&user=username"

local url = testSecret:AddPrefix(prefix)

url = url:AddSuffix(suffix)

print(url) --> https://my.example.com/endpoint?apiKey=Geheim(test_secret)&user=username

```

Nadat je een URL met het geheim hebt ingevoegd, kun je standaard HTTP-verzoeken doen met methoden zoals [HttpService:RequestAsync()](/docs/nl-nl/reference/engine/classes/HttpService#RequestAsync) . Natuurlijk kun je deze methoden negeren en het geheim ook direct in een header invoegen.

Je kunt geen geheimen opnemen in de HTTP-verzoekbody, alleen in de URL en headers.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
