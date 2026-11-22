<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/reference/rate-limits -->

Snelheidslimieten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)
4. /
5. [Gemeenschappelijke componenten](/docs/nl-nl/cloud/reference/patterns)

# Snelheidslimieten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Snelheidslimieten beheersen het aantal verzoeken dat je kunt doen naar eindpunten binnen een specifieke tijdsperiode. Deze limieten helpen de stabiliteit van de service te waarborgen en beschermen de Roblox-resources tegen misbruik.

## [Ontdekking](#ontdekking)[](#ontdekking)

Er zijn twee manieren om snelheidslimieten te bepalen: de referentiedocumentatie en de response headers.

### [Documentatiepagina's](#documentatiepaginas)[](#documentatiepaginas)

Openbare snelheidslimieten zijn te vinden onder de sectie Limieten  voor elk eindpunt op hun documentatiepagina's. Bekijk deze secties om de snelheidslimieten te begrijpen die van toepassing zijn voordat je verzoeken indient.

We streven ernaar zo transparant mogelijk te zijn over snelheidslimieten, maar er kunnen aanvullende, niet gedocumenteerde limieten van toepassing zijn, inclusief voor DDoS-bescherming en service-stabiliteit. Zorg er altijd voor dat je applicatie HTTP 429-snelheidslimietreacties afhandelt. Zie [Omgaan met snelheidslimieten](#omgaan-met-snelheidslimieten)  voor richtlijnen.

Als je een niet gedocumenteerde snelheidslimiet tegenkomt die je gebruiksgeval blokkeert (of als je hogere limieten voor een eindpunt wilt), laat dan feedback achter waarin je jouw behoeften uitlegt in het [Developer Forum](https://devforum.roblox.com/) .

### [Response headers](#response-headers)[](#response-headers)

Veel API-responses bevatten headers die informatie geven over je huidige status van de snelheidslimiet.

| Header | | Beschrijving |
| --- | --- |
| x-ratelimit-limit | | Het totale aantal verzoeken dat is toegestaan binnen de snelheidslimietperiode. Dit kan meerdere limietwaarden voor verschillende tijdsperioden omvatten. |
| x-ratelimit-remaining | | Het aantal verzoeken dat je nog kunt doen met je huidige authenticatie. Wanneer dit 0 bereikt, ontvang je HTTP 429-reacties. |
| x-ratelimit-reset | | Het aantal seconden dat nog resteert totdat je snelheidslimietquotum opnieuw wordt ingesteld op de volledige limiet. |

Hier is een voorbeeld van snelheidslimietheaders in een API-respons:

```

x-ratelimit-limit: 1000, 1000;w=60, 1000;w=60

x-ratelimit-remaining: 998

x-ratelimit-reset: 20

```

In dit voorbeeld:

-

Je hebt 998 verzoeken over van je totale limiet.

-

Je quotum wordt over 20 seconden opnieuw ingesteld.

## [Gedrag](#gedrag)[](#gedrag)

Het gedrag van snelheidslimieten verschilt per authenticatiemethode en verzoekoorsprong, inclusief of je verzoeken doet vanuit een Roblox-spel.

### [API-sleutel](#api-sleutel)[](#api-sleutel)

Snelheidslimieten voor API-sleutels worden toegepast op alle API-sleutels per eigenaar, wat een gebruiker of een groep kan zijn. Deze limieten worden consistent gehandhaafd, ongeacht waar de verzoeken vandaan komen—of het nu vanuit [HttpService](/docs/nl-nl/reference/engine/classes/HttpService) , webapplicaties of andere bronnen is.

#### [In-game met HttpService](#in-game-met-httpservice)[](#in-game-met-httpservice)

Wanneer je eindpunten in-game aanroept met [HttpService](/docs/nl-nl/reference/engine/classes/HttpService) , dragen verzoeken ook bij aan de vaste limiet van 500 HTTP-verzoeken per minuut per Roblox-spelserver. Zie [In-game HTTP-verzoeken](/docs/nl-nl/cloud-services/http-service)  voor meer details.

### [OAuth 2.0](#oauth-20)[](#oauth-20)

Snelheidslimieten voor OAuth 2.0 worden per toegangstoken toegepast. Aangezien elke toegangstoken een unieke combinatie van gebruiker en applicatie vertegenwoordigt, ontvangt elke gebruiker die jouw app gebruikt zijn eigen onafhankelijke snelheidslimietquotum.

## [Omgaan met snelheidslimieten](#omgaan-met-snelheidslimieten)[](#omgaan-met-snelheidslimieten)

Schrijf je code zodat deze HTTP 429 (Te Veel Verzoeken) reacties verwacht en afhandelt als gevolg van gedocumenteerde limieten, misbruikpreventie of hoge belastingscenario's. Wanneer je beperkt bent in snelheid, controleer dan de retry-after  response header als richtlijn voor wanneer je opnieuw moet proberen. Als er geen retry-after  response header aanwezig is, implementeer dan een exponentiële backoff retry-strategie.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
