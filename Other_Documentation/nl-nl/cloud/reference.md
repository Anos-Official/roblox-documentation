<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/reference -->

Cloud API-referentie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Cloud API-referentie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Met Open Cloud kun je Roblox-resources benaderen via standaard [REST](https://en.wikipedia.org/wiki/REST)  API's, waarmee je alles kunt bouwen, van automatiseringstools voor de opdrachtregel tot complexe webapps. Je kunt games bijwerken, servers opnieuw opstarten, werken met je datastores en geheugenopslag, gebruikersbeperkingen beheren, inventarisitems opsommen en nog veel meer.

Deze referentie is opgedeeld in twee secties:

-

Een [sectie die eindpunten scheidt op basis van functie](/docs/nl-nl/cloud/reference/features/accounts)  (Avatars, Game Passes, Gebruikers, enz.)

-

Een [sectie die eindpunten scheidt op basis van domein](/docs/nl-nl/cloud/reference/domains/apis)  (basis-URL)

Beide secties  bevatten de volledige lijst van beschikbare API-eindpunten. We raden de [sectie functies](/docs/nl-nl/cloud/reference/features/accounts)  aan, omdat deze helpt om eindpunten te consolideren op basis van gebruiksscenario's, maar ervaren Open Cloud-ontwikkelaars geven misschien de voorkeur aan bladeren op basis van domein.

-

Gebruik waar mogelijk eindpunten die [API-sleutels](/docs/nl-nl/cloud/auth/api-keys)  of [OAuth 2.0](/docs/nl-nl/cloud/auth/oauth2-overview)  voor authenticatie ondersteunen. Ze hebben sterke stabiliteitsgaranties en ontvangen regelmatige updates.

-

Legacy API's gebruiken cookie-gebaseerde authenticatie, kunnen zonder kennisgeving ingrijpende wijzigingen bevatten en hebben minimale stabiliteitsgaranties. We raden ze niet aan voor productie-applicaties.

Roblox biedt ook [webhooks](/docs/nl-nl/cloud/webhooks/webhook-notifications) , die je applicaties kunnen informeren wanneer bepaalde gebeurtenissen plaatsvinden, zoals terugbetalingen of wijzigingen in abonnementen.

## [Aan de slag met Open Cloud](#aan-de-slag-met-open-cloud)[](#aan-de-slag-met-open-cloud)

1.

Stel authenticatie in voor je applicatie.

Zie de documentatie voor hoe je [API-sleutels](/docs/nl-nl/cloud/auth/api-keys)  of [OAuth 2.0](/docs/nl-nl/cloud/auth/oauth2-overview)  kunt gebruiken. API-sleutels zijn de gemakkelijkste manier om te beginnen.

2.

Test API-aanroepen met tools zoals [Postman](https://www.postman.com)  met [OpenAPI-beschrijvingen](/docs/nl-nl/cloud/reference/openapi)  of de [OAuth 2.0 voorbeeldapp](/docs/nl-nl/cloud/auth/oauth2-sample) .

3.

Bekijk de [resourcehandleidingen](/docs/nl-nl/cloud/guides)  voor end-to-end walkthroughs van het gebruik van bepaalde API's.

4.

Verken de linker navigatie voor de volledige lijst van functies, [veelvoorkomende API-patronen](/docs/nl-nl/cloud/reference/patterns) , [typen](/docs/nl-nl/cloud/reference/types)  en [foutcodes](/docs/nl-nl/cloud/reference/errors) .

## [Verzoeken doen binnen games](#verzoeken-doen-binnen-games)[](#verzoeken-doen-binnen-games)

[HttpService](/docs/nl-nl/reference/engine/classes/HttpService)  stelt je in staat om HTTP-verzoeken te doen naar een subset van de Open Cloud-eindpunten. Voor meer informatie, zie [HTTP-verzoeken in het spel](/docs/nl-nl/cloud-services/http-service) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
