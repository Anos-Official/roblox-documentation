<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/reference/openapi -->

OpenAPI-document | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)
4. /
5. [Gemeenschappelijke componenten](/docs/nl-nl/cloud/reference/patterns)

# OpenAPI-document

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox publiceert een [OpenAPI 3.0.4-document](https://spec.openapis.org/oas/v3.0.4)  (voorheen bekend als een Swagger-bestand) dat alle  Roblox Cloud API's bevat. Je kunt dit bestand, openapi.json , vinden in de open source [creator-docs](https://github.com/Roblox/creator-docs/tree/main/content/en-us/reference/cloud)  repository.

Je kunt OpenAPI-documenten gebruiken met tools zoals de [Swagger Editor](https://editor.swagger.io/)  en [Postman](https://www.postman.com/)  om oproepen te testen en de ontwikkeling te stroomlijnen. Tools zoals [OpenAPI Generator](https://github.com/OpenAPITools/openapi-generator)  kunnen ook clientbibliotheken genereren voor jouw voorkeursprogrammeertalen.

Dit document is nog in actieve ontwikkeling en kan problemen bevatten. Meld een bug als je onnauwkeurige informatie opmerkt.

 [Download openapi.json hier](https://create.roblox.com/docs/cloud/openapi.json)

### [Leverancier extensies](#leverancier-extensies)[](#leverancier-extensies)

Roblox gebruikt [specificatie-extensies](https://spec.openapis.org/oas/v3.0.4#specification-extensions)  om de OpenAPI-specificatie uit te breiden. Deze extensies vertegenwoordigen informatie die de specificatie standaard niet vastlegt. Extensies kunnen door het bestand heen verschijnen waar dit door de OpenAPI-specificatie is toegestaan.

De meeste van deze specificatie-extensies zijn experimenteel. De gebruikte extensies kunnen zonder voorafgaande kennisgeving veranderen ten gunste van velden die in de officiële OpenAPI-specificatie zijn te vinden.

| Extensie | | Locatie | | Beschrijving |
| --- | --- |
| x-roblox-extensions-version | | OpenAPI-object | | Een versie-string, gebruikmakend van semantische versiebeheer, die de versies van de hier gespecificeerde extensies en andere veelvoorkomende structuren vertegenwoordigt |
| x-roblox-stability | | Operatie-object | | Een string die het stabiliteitsniveau van een operatie vertegenwoordigt. |
| x-roblox-deprecated | | Operatie-object | | Een object dat aanvullende informatie biedt met betrekking tot de deprecatiestatus van een eindpunt. |
| x-roblox-alternatives | | Operatie-object | | Een object dat aanvullende informatie biedt met betrekking tot de alternatieven van een eindpunt. |
| x-roblox-rate-limits | | Operatie-object | | Een object dat informatie over snelheidslimieten voor een eindpunt biedt. |
| x-roblox-scopes | | Operatie-object | | Een object dat de lijst van vereiste, voorwaardelijke en optionele scopes biedt die aan een eindpunt zijn gekoppeld. |
| x-roblox-engine-usability | | Operatie-object | | Een object dat de bruikbaarheid van het eindpunt met de Roblox-engine aangeeft. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
