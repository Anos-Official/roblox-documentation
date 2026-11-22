<!-- Source: https://create.roblox.com/docs/nl-nl/production/monetization/commerce-products -->

Commerce producten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Verdienen](/docs/nl-nl/production/monetization)

# Commerce producten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt echte producten, of commerce producten , in je Roblox-game catalogiseren en verkopen. Gebruikers kunnen deze producten in je game kopen en, indien in aanmerking komend, kun je digitale voordelen bieden als een gebundeld voordeel.

Om catalogusitems en commerce producten te maken en te beheren, moet je voldoen aan [commerce geschiktheid](#geschiktheid) . Om commerce producten aan je game toe te voegen:

1.

[Importeer een catalogusitem uit de echte wereld](#catalogusitems-importeren)  van Shopify.

2.

[Maak een commerce product aan](#commerce-producten-beheren)  in Creator Hub.

3.

[Implementeer een aankoopprompt](#aankopen-implementeren)  binnen je game.

## [Geschiktheid](#geschiktheid)[](#geschiktheid)

De volgende geschiktheidseisen zijn van toepassing voor makers  die geïnteresseerd zijn in het implementeren van commerce producten, games  die commerce functies hosten, en gebruikers  die commerce producten kunnen kopen. Gebundelde digitale items  vereisen ook aanvullende geschiktheidseisen.

Deze vereisten kunnen veranderen.

### [Maker](#maker)[](#maker)

Geschikte makers kunnen commerce producten aan hun game toevoegen. Om in aanmerking te komen, moeten makers voldoen aan en de volgende voorwaarden handhaven:

-

18 jaar of ouder zijn.

-

Een ID-geverifieerd en e-mail-geverifieerd account hebben.

-

2-staps verificatie ingeschakeld hebben.

-

De geregistreerde accounthouder op Shopify zijn voor de gekoppelde winkel.

-

Alternatief moet je schriftelijke toestemming hebben om de Shopify-winkel te koppelen van de geregistreerde accounthouder.

-

Bedrijfsinformatie  hebben ingediend. Je kunt dit indieningsformulier op de volgende manieren openen:

-

Commerce Geschiktheid pagina  — Wanneer je de commerce pagina voor de eerste keer bezoekt, verschijnt er een geschiktheidsformulier.

-

Creator Dashboard  — In [Accountinformatie](https://create.roblox.com/dashboard/account-information)  moet je de tabs Core Account  en Legal  invullen. Je kunt de sectie Uitgebreide Diensten onder Core Account overslaan als deze verschijnt.

-

Om bedrijfsinformatie namens een groep in te dienen, moet de maker Configureer en besteed groepsinkomsten  ingeschakeld hebben.

-

Als je toegang hebt tot de commerce-instellingen namens een groep, moet je rol Maak en bewerk community-ervaringen  ingeschakeld hebben.

-

In goede staat zijn met betrekking tot Roblox's [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  op een doorlopende basis.

### [Game](#game)[](#game)

Makers moeten ervoor zorgen dat games die commerce functies hosten aan de volgende vereisten voldoen:

-

De game moet openbaar zijn.

-

De game heeft [inhoudsbeoordelingen](/docs/nl-nl/production/promotion/content-ratings)  ontvangen na het invullen van de Inhoudsbeoordelingsvragenlijst.

-

De game voldoet op een doorlopende basis aan Roblox's [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) , [Advertentienormen](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards#advertising)  en [Commerce Normen](https://en.help.roblox.com/hc/articles/36495190721172) .

### [Gebruiker](#gebruiker)[](#gebruiker)

Op dit moment kunnen alleen gebruikers in de VS commerce producten kopen. Deelnemende gebruikers moeten ook aan de volgende vereisten voldoen:

-

Moet 13 jaar of ouder zijn, behalve in Texas.

-

Moet 18 jaar of ouder zijn in Texas.

Je kunt de geschiktheid van gebruikers verifiëren door [PolicyService](/docs/nl-nl/reference/engine/classes/PolicyService)  te gebruiken om beleidsinformatie over elke gebruiker terug te geven.

### [Digitale voordelen](#digitale-voordelen)[](#digitale-voordelen)

Bepaalde makers kunnen in aanmerking komen om een digitaal voordeel, zoals een avataritem of ontwikkelaarsitem, te bundelen met hun commerce product als ze ten minste één  van de volgende twee vereisten voldoen:

-

De game die de winkel host, voldoet aan het volgende:

-

Behoudt meer dan 100.000 dagelijkse actieve gebruikers gemiddeld over de laatste 90 dagen.

-

Behoudt meer dan 1.000.000 Robux gemiddelde maandelijkse inkomsten in de laatste 90 dagen.

-

Verkoop ten minste één bundel binnen drie maanden na goedkeuring om te bundelen.

-

Of sluit een schriftelijke overeenkomst met Roblox voor een advertentiebestedingsbedrag van ten minste $50.000 USD in één jaar.

#### [Gebundelde digitale voordelen](#gebundelde-digitale-voordelen)[](#gebundelde-digitale-voordelen)

Als je in aanmerking komt om een digitaal voordeel te bundelen met je commerce product, moet elk digitaal voordeel:

-

Voldoen aan Roblox's [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  en [Advertentienormen](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards#advertising) , zowel als individueel item als in de combinatie van het product en het gebundelde digitale voordeel in de context van de bundel.

-

Geen item zijn dat eerder beschikbaar was voor aankoop voordat de bundel werd vermeld of afzonderlijk beschikbaar werd gesteld voor aankoop met Robux.

-

Geen Robux of in-game valuta zijn.

-

Met voldoende detail worden bekendgemaakt in de productvermelding op Roblox en mag niet onduidelijk zijn voor de koper.

-

Geen willekeurig item zijn en mag geen kansmechanisme vereisen om het onderliggende item te ontvangen.

-

Geen extra stappen vereisen om te verwerven nadat de betaling voor de bundel is voltooid.

## [Catalogusitems importeren](#catalogusitems-importeren)[](#catalogusitems-importeren)

In het [Creator Dashboard](https://create.roblox.com/)  kun je je Roblox-account verbinden met je Shopify-winkel en catalogusitems aan je game koppelen. Je moet individuele producten toevoegen die je van plan bent te importeren in Roblox.

### [Catalogusitems importeren van Shopify](#catalogusitems-importeren-van-shopify)[](#catalogusitems-importeren-van-shopify)

Op dit moment, vanwege de link tussen de Shopify-winkel en een Roblox-account, is het overdragen van Roblox-groepseigendom niet toegestaan voor een groep die enige commerce-items bezit.

1.

Navigeer naar je game in het [Creator Dashboard](https://create.roblox.com/)  en selecteer Monetization Products  ⟩ Commerce .

2.

Klik op Ga naar Geïmporteerde Catalogus  ⟩ Begin met Importeren .

3.

Klik op Verbinden .

4.

Installeer het Roblox-verkoopkanaal op je winkel.

5.

Verbind je Roblox-account. Klik op Volgende .

1.

Nadat je je Roblox-account hebt verbonden, kun je optioneel een Roblox-groep verbinden om alle groepsleden toegang te geven tot je geïmporteerde catalogusitems. Dit kan op elk moment worden bijgewerkt onder Account  in het Roblox-verkoopkanaal.

6.

Klik op Producten Toevoegen  en selecteer de items die je naar Roblox wilt importeren.

7.

Klik op Voltooien  en wacht tot de items zijn gesynchroniseerd met Roblox. Je kunt je geïmporteerde catalogusitems bekijken in het tabblad Geïmporteerde Catalogus van de Commerce-pagina.

### [Catalogusitems verwijderen](#catalogusitems-verwijderen)[](#catalogusitems-verwijderen)

Op de Commerce-pagina kun je elk catalogusitem dat je in het tabblad Catalogus hebt geïmporteerd verwijderen door op de knop Verwijderen  of Verwijderen  naast het item te klikken.

Wanneer je een item verwijdert, worden automatisch alle commerce producten die het item bevatten verwijderd. Om het commerce product opnieuw te verkopen, moet je het item opnieuw importeren en het product opnieuw maken.

### [Catalogusitems wijzigen](#catalogusitems-wijzigen)[](#catalogusitems-wijzigen)

Wanneer je de prijs van een catalogusitem op Shopify wijzigt, worden alle bijbehorende commerce productbundels van de verkoop gehaald en opnieuw ingediend voor verwerking van de bundelkosten.

Wanneer je de inhoud van je Shopify-item bijwerkt, zoals de naam, beschrijving of weergave-afbeelding, worden alle bijbehorende producten niet van de verkoop gehaald, maar ze worden opnieuw ingediend voor moderatie. De productvermelding op Roblox voor elk product blijft de eerder goedgekeurde inhoud tonen totdat de nieuwe inhoud is goedgekeurd door moderatie. Zie [Productdetailpagina](#productdetailpagina)  voor meer informatie over hoe deze Shopify-attributen worden weergegeven en beheerd.

## [Commerce producten beheren](#commerce-producten-beheren)[](#commerce-producten-beheren)

Nadat je een catalogusitem naar de Commerce-pagina van je game hebt geïmporteerd, kun je beginnen met het maken van commerce producten.

### [Aanmaken](#aanmaken)[](#aanmaken)

Zodra je catalogusitems hebt geïmporteerd, kun je commerce producten aanmaken. Een commerce product kan een catalogusitem op zichzelf zijn, of een catalogusitem gebundeld met een digitaal voordeel.

Je kunt maximaal 500 producten per game aanmaken.

Je kunt geen avataritemtype digitaal voordeel aanmaken terwijl je het commerce product aanmaakt. Maak het avataritem eerst aan voordat je het aan een commerce productbundel toevoegt.

Om een commerce product aan te maken:

1.

Navigeer naar je game in het Creator Dashboard en selecteer Monetization Products  ⟩ Commerce .

2.

Klik op Begin met Aanmaken  of Producten Aanmaken .

3.

Selecteer welke geïmporteerde catalogusitems je wilt opnemen in je commerce producten en klik op Volgende .

1.

Als je geen Volgende  knop ziet, is je game niet in aanmerking om bundels met digitale voordelen te maken. Ga door naar stap 4.

2.

Op dit punt worden je commerce producten opgeslagen als concepten. Als je deze pagina verlaat en er later naar wilt terugkeren, kun je concept commerce producten vinden onder Concepten  in het tabblad Creations .

(Optioneel) Digitale voordelen bundelen

Als je [in aanmerking komt om een commerce product met digitale voordelen te bundelen](#digitale-voordelen) , kun je een digitaal voordeel aan je commerce product bundelen. Gebundelde producten vereisen een bundelkosten na moderatie. Om een digitaal voordeel te bundelen:

1.

Klik op Voordeel Toevoegen .

2.

Kies een Virtueel Voordeeltype :

3.

Avataritem : Om deel uit te maken van een bundel, mag het avataritem niet eerder te koop zijn geweest. Je moet het item bezitten of tot de groep behoren die het item bezit.

4.

Selecteer een avataritem door een Avataritemtype  te kiezen en de dropdowns te gebruiken. Klik op Opslaan .

5.

Ontwikkelaarsproduct : Om deel uit te maken van een bundel, moet het ontwikkelaarsproduct eigendom zijn van de game, mag het niet eerder te koop zijn geweest en mag het geen prijs hebben.

6.

Selecteer een bestaand Ontwikkelaarsproduct  of maak een nieuwe aan om in een bundel te gebruiken door op Nieuwe Aanmaken  te klikken, de informatie van het ontwikkelaarsproduct in te vullen en op Aanmaken  te klikken. Klik op Opslaan .

1.

Namen van ontwikkelaarsproducten binnen dezelfde game moeten uniek zijn.

2.

Ontwikkelaarsproducten worden aangemaakt wanneer je het product ter beoordeling indient. Om een ontwikkelaarsproduct in meerdere bundels te hergebruiken, dien je één product in (wat het ontwikkelaarsproduct creëert), selecteer dan dat voordeel in daaropvolgende bundels.

![](https://prod.docsiteassets.roblox.com/assets/monetization/commerce-products/Commerce-Product-Virtual-Benefits.png)

1.

Voer het Voorraadtype  van het catalogusitem in.

1.

Vaste Hoeveelheid : Er is een vaste hoeveelheid van het commerce-item. Voer de hoeveelheid in onder Qty

2.

Merch on Demand : Het commerce-item wordt op aanvraag gemaakt.

3.

Pre Order : Het commerce-item is voor pre-order.

1.

Controleer de details van je producten en klik op Voorbeeld  om de productvermelding voor elk product te bekijken. Voor details over wat deze pagina bevat en hoe deze wordt gevuld, zie [Het aanpassen van de Productdetailpagina](#productdetailpagina) . Klik op Indienen voor beoordeling .

2.

De status van je nieuw aangemaakte commerce producten is In afwachting  terwijl het product wacht op moderatie en mogelijke verwerking van de bundelkosten. Je kunt met de muis over het informatiepictogram zweven om te zien welke taken in afwachting zijn.

1.

Moderatie

1.

Als je commerce product wordt geacht de community-normen van Roblox te schenden, zie je de Status  van het commerce product veranderen in Gemodereerd .

2.

Hover over het informatiepictogram en klik op Bekijk Schending  om de schending te bekijken en een beroep in te dienen, of maak een nieuw commerce product dat voldoet aan de community-normen van Roblox. Je moet de gebruiker zijn wiens account is verbonden met de Shopify-winkel, of de groepshouder voor groepswinkels om de schending te bekijken.

2.

Bundelkosten  (indien van toepassing)

1.

Zodra er een bundelkosten beschikbaar is voor een gebundeld commerce product, navigeer naar het commerce product om het onder Bundelkosten  te bekijken.

2.

Om te accepteren, selecteer het product en klik op Accepteer Bundelkosten , of klik op de drie stippen bij de bundelkosten en klik op Accepteer .

3.

Zodra deze taken zijn goedgekeurd voor je commerce product, wordt de Status  van het commerce product Goedgekeurd  en is het klaar om in je game te worden geïntegreerd met [CommerceService](/docs/nl-nl/reference/engine/classes/CommerceService) .

### [Verkrijg ID's](#verkrijg-ids)[](#verkrijg-ids)

Je hebt de product-ID van een commerce product nodig om het in je game te verkopen.

Om de Product-ID te verkrijgen:

1.

Hover over de Product-ID .

2.

Klik op Kopieer ID  om het naar je klembord te kopiëren.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/commerce-products/Commerce-Product-ID.png)

### [Te koop aanbieden](#te-koop-aanbieden)[](#te-koop-aanbieden)

Commerce producten moeten beschikbaar zijn voor verkoop om in-game te worden gekocht.

Twee identieke catalogusitems kunnen niet tegelijkertijd te koop zijn. Je moet een bundel die een catalogusitem bevat van de verkoop halen om een andere met datzelfde item te koop aan te bieden. Een maximum van 100 producten kan tegelijkertijd te koop zijn per game.

Om de verkoopstatus van een product te wijzigen:

1.

Navigeer op de commerce-pagina naar het product dat je wilt verkopen.

2.

Klik op Te koop aanbieden  of Van de verkoop halen  voor het product.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/commerce-products/Commerce-Product-Put-On-Sale.png)

### [Verwijderen](#verwijderen)[](#verwijderen)

Om een commerce product te verwijderen:

1.

Hover over het product.

2.

Klik op Verwijderen  om het product te verwijderen.

## [Aankopen implementeren](#aankopen-implementeren)[](#aankopen-implementeren)

Implementeer aankopen van commerce producten in je game met behulp van de volgende [CommerceService](/docs/nl-nl/reference/engine/classes/CommerceService)  functies:

-

[CommerceService:PromptCommerceProductPurchase()](/docs/nl-nl/reference/engine/classes/CommerceService#PromptCommerceProductPurchase) : Vraagt een specifieke gebruiker om een commerce product aan te kopen met de opgegeven commerceProductId. Het opent een webview die de gebruiker door de aankoopstroom leidt.

-

[CommerceService:PromptCommerceProductPurchaseFinished()](/docs/nl-nl/reference/engine/classes/CommerceService#PromptCommerceProductPurchaseFinished) : Gebruik dit signaal om te detecteren wanneer een gebruiker de aankoopstroom heeft voltooid en de webview is gesloten om het spel binnen de game te hervatten.

-

Dit signaal geeft geen succesvolle aankoop aan en geeft alleen aan wanneer de prompt is gesloten.

-

Hoewel optioneel, wordt het aanbevolen om dit signaal te gebruiken om je gebruikers op Android opnieuw te oriënteren, aangezien de aankoopstroom hen in de portretmodus heeft gedwongen.

### [Digitale voordelen toekennen](#digitale-voordelen-toekennen)[](#digitale-voordelen-toekennen)

[Geschikte makers](#geschiktheid)  kunnen een digitaal voordeel aan hun commerce producten toevoegen.

Wanneer je [een commerce product aanmaakt](#aanmaken) , heb je de optie om het catalogusitem te bundelen met een digitaal voordeel.

#### [Avataritems](#avataritems)[](#avataritems)

Als een avataritem is gebundeld met een commerce item, kent Roblox automatisch het gekoppelde avataritem toe nadat een gebruiker met succes een commerce product heeft gekocht.

Als Roblox een annulering of terugbetaling van het fysieke item detecteert, trekt Roblox automatisch het avataritem in van het account.

Als het avataritem wordt gemodereerd, wordt de status van elk commerce product dat aan het item is gekoppeld gemodereerd en wordt het van de verkoop gehaald. Na 7 dagen zal Roblox automatisch het avataritem intrekken van alle accounts die deze producten hebben gekocht. Na een succesvolle beroepsprocedure zal het avataritem opnieuw worden toegekend.

#### [Ontwikkelaarsproducten](#ontwikkelaarsproducten)[](#ontwikkelaarsproducten)

Nadat een gebruiker met succes een commerce product heeft gekocht, genereert Roblox een ontwikkelaarsproductontvangst en stuurt deze naar de server waar de gebruiker zich bevindt. Volg de bestaande [MarketplaceService.ProcessReceipt](/docs/nl-nl/reference/engine/classes/MarketplaceService#ProcessReceipt)  stroom voor het afhandelen van het toekennen van ontwikkelaarsproducten.

In het geval van een terugbetaling of annulering van het fysieke item, wil je mogelijk de bijbehorende in-game items of voordelen intrekken. Roblox trekt geen ontwikkelaarsproducten automatisch in die aan gebruikers zijn toegekend als een digitaal voordeel.

Roblox biedt webhook-integratie voor commerce-evenementen. Wanneer een bestelling is betaald, geannuleerd of terugbetaald, zal Roblox een webhookbericht sturen met de laatste bestelstatus en bestelgegevens. Ontwikkelaars kunnen deze informatie gebruiken om in-game items of voordelen indien nodig in te trekken.

Voor meer informatie over webhookmeldingen, zie de [documentatie](/docs/nl-nl/cloud/webhooks/webhook-notifications#handel) .

Gebruik de evenementen CommerceProductOrderPaid  en CommerceProductOrderRefunded  om de status van de productbestelling te volgen. De EventPayload bevat de relevante CommerceProductOrder  die de volgende schema heeft:

EventPayload schema

```

{

  "type": "object",

  "properties": {

    "path": {

      "type": "string",

      "description": "Het resourcepad van de commerce productbestelling.\n\n Formaat:\n `universes/{universe_id}/commerce-products/{commerce_product_id}/orders/{commerce_product_order_id}`",

      "x-example-values": {

        "exampleValues": [

          "universes/123/commerce-products/123/orders/123e4567-e89b-12d3-a456-426655440000"

        ]

      }

    },

    "createTime": {

      "readOnly": true,

      "type": "string",

      "description": "De tijdstempel wanneer de commerce bestelling is aangemaakt.",

      "format": "date-time",

      "x-example-values": {

        "exampleValues": [

          "2023-07-05T12:34:56Z"

        ]

      }

    },

    "updateTime": {

      "readOnly": true,

      "type": "string",

      "description": "De tijdstempel wanneer de commerce bestelling voor het laatst is bijgewerkt.",

      "format": "date-time",

      "x-example-values": {

        "exampleValues": [

          "2023-07-05T12:34:56Z"

        ]

      }

    },

    "state": {

      "readOnly": true,

      "enum": [

        "STATE_UNSPECIFIED",

        "STATE_PAID",

        "STATE_REFUNDED"

      ],

      "type": "string",

      "description": "De huidige status van deze bestelling, d.w.z. BETAALD, TERUGGEGEVEN, GEANNULEERD\n\nMogelijke waarden:\n\n  | Waarde | Beschrijving |\n  | --- | --- |\n  | STATE_UNSPECIFIED | Ongekwalificeerde status. |\n  | STATE_PAID | De bestelling is betaald. |\n  | STATE_REFUNDED | De bestelling is teruggegeven. |",

      "format": "enum",

      "x-example-values": {

        "exampleValues": [

          "STATE_UNSPECIFIED"

        ]

      }

    },

    "merchantOrderId": {

      "immutable": true,

      "type": "string",

      "description": "De door de handelaar specifieke bestel-ID die kan worden gebruikt om de bestelling op de\n handelaarplatform op te zoeken."

    },

    "merchant": {

      "immutable": true,

      "enum": [

        "MERCHANT_PLATFORM_UNSPECIFIED",

        "SHOPIFY",

      ],

      "type": "string",

      "description": "De handelaar die wordt gebruikt om bestellingen te vervullen.\n\nMogelijke waarden:\n\n  | Waarde | Beschrijving |\n  | --- | --- |\n  | MERCHANT_PLATFORM_UNSPECIFIED | Ongekwalificeerd handelaarstype. |\n  | SHOPIFY | Het item wordt verkocht via Shopify. |",

      "format": "enum",

      "x-example-values": {

        "exampleValues": [

          "MERCHANT_PLATFORM_UNSPECIFIED"

        ]

      }

    },

    "user": {

      "immutable": true,

      "type": "string",

      "description": "De gebruiker die deze bestelling heeft geplaatst.",

      "x-example-values": {

        "exampleValues": [

          "users/123"

        ]

      }

    }

  },

  "description": "Een commerce productbestelling vertegenwoordigt een aankoop van een CommerceProduct door een\n Roblox-gebruiker. Het omvat de gebruiker die de aankoop heeft gedaan en de bestelgegevens van de handelaar.",

}

```

## [Productdetailpagina](#productdetailpagina)[](#productdetailpagina)

De Productdetailpagina (PDP)  toont je commerce product aan gebruikers binnen de Roblox-game, bijvoorbeeld wanneer gevraagd via [[CommerceService:PromptCommerceProductPurchase()](/docs/nl-nl/reference/engine/classes/CommerceService#PromptCommerceProductPurchase)](#aankopen-implementeren) . Je kunt verschillende elementen van deze pagina aanpassen om een unieke en informatieve winkelervaring te bieden.

Wanneer je de productdetailpagina bekijkt voor een product dat nog niet te koop is, wordt er een "Voorbeeldmodus" banner bovenaan weergegeven (zoals te zien in de voorbeeld PDP-afbeelding). Alleen makers met voldoende machtigingen in de game kunnen deze preview zien.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/commerce-products/Commerce-Product-PDP-Diagram.png)

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

[Productafbeeldingen](#productafbeeldingen)  toont productafbeeldingen die in je Shopify-winkel zijn verstrekt.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

[Producttitel, prijs en verkoperinformatie](#producttitel-prijs-en-verkoperinformatie)  bevat product- en verkoperdetails.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

[Varianten en hoeveelheid](#varianten-en-hoeveelheid)  toont verschillende beschikbare opties en hoeveelheden.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-D.png)

[Productdetails](#productdetails)  toont de productbeschrijving van Shopify.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-E.png)

[Aanvullende informatie](#aanvullende-informatie)  bevat aanvullende details, zoals "Materialen", "Verzorgingsinstructies" of "Maatgids".

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-F.png)

[Virtueel voordeel bij aankoop](#virtueel-voordeel-bij-aankoop)  beschrijft het virtuele item dat gebruikers ontvangen met hun aankoop.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-G.png)

[Meer van deze game](#meer-van-deze-game)  suggereert andere commerce producten die binnen dezelfde game worden aangeboden.

### [Productafbeeldingen](#productafbeeldingen)[](#productafbeeldingen)

De sectie productafbeeldingen toont alle productafbeeldingen uit je Shopify-winkel. De volgorde van de afbeeldingen weerspiegelt direct de volgorde die in Shopify is ingesteld.

De eerste afbeelding, bekend als de uitgelichte  afbeelding in Shopify, dient als de primaire thumbnail voor je product. Deze thumbnail wordt op verschillende plaatsen gebruikt, zoals in het winkelwagentje en in de [Meer van](#meer-van-deze-game)  sectie.

Wanneer je productafbeeldingen in Shopify bijwerkt, zijn deze wijzigingen onderhevig aan het [moderatieproces voor catalogusitems](#catalogusitems-wijzigen) . De productvermelding op Roblox blijft de eerder goedgekeurde afbeeldingen tonen totdat de nieuwe afbeeldingen zijn goedgekeurd.

### [Producttitel, prijs en verkoperinformatie](#producttitel-prijs-en-verkoperinformatie)[](#producttitel-prijs-en-verkoperinformatie)

De producttitel wordt rechtstreeks overgenomen van de producttitel die in de Shopify-winkel is ingesteld.

De weergegeven prijs wordt dynamisch bijgewerkt als de gebruiker verschillende geprijsde product [varianten en hoeveelheden](#varianten-en-hoeveelheid)  selecteert. De verkoperinformatie die wordt weergegeven is de naam van je Shopify-winkel.

Net als bij andere productattributen, als je de producttitel in Shopify bijwerkt, zijn deze wijzigingen onderhevig aan het [moderatieproces voor catalogusitems](#catalogusitems-wijzigen) . De productvermelding op Roblox blijft de eerder goedgekeurde titel tonen totdat de nieuwe titel is goedgekeurd.

### [Varianten en hoeveelheid](#varianten-en-hoeveelheid)[](#varianten-en-hoeveelheid)

Productvarianten en hun opties, zoals verschillende kleuren of maten, worden gesynchroniseerd vanuit je Shopify-winkel. De volgorde waarin deze varianten en opties verschijnen, komt overeen met de volgorde in Shopify, van boven naar beneden weergegeven.

Wanneer een gebruiker een specifieke variant selecteert, wordt de hoofdproductafbeelding bijgewerkt om de afbeelding weer te geven die aan die specifieke variant in Shopify is gekoppeld.

Op dit moment biedt de hoeveelheidselector op de PDP geen aanpassingsopties. Als de geselecteerde productvariant niet beschikbaar is, zijn de knoppen "Nu kopen" en "Toevoegen aan winkelwagentje" uitgeschakeld. Zorg ervoor dat je varianten correct zijn geconfigureerd in Shopify om aankopen mogelijk te maken.

Alle updates die aan productvarianten of hun afbeeldingen in Shopify worden aangebracht, zijn onderhevig aan het [moderatieproces voor catalogusitems](#catalogusitems-wijzigen) . De productdetailpagina blijft de eerder goedgekeurde variantinformatie en afbeeldingen tonen totdat de nieuwe versies zijn goedgekeurd.

### [Productdetails](#productdetails)[](#productdetails)

De sectie Productdetails  toont de inhoud rechtstreeks van je Shopify productbeschrijving.

Deze sectie ondersteunt het gebruik van HTML voor het stylen en formatteren van je productinformatie. Voor beveiliging en consistentie verwijdert Roblox automatisch bepaalde HTML-elementen, waaronder links, afbeeldingen, scripts en andere vergelijkbare tags en attributen. Je kunt anders HTML gebruiken om de tekstinhoud te stylen en structureren, zoals het gebruik van koppen, vetgedrukte tekst, lijsten en paragrafen.

Productbeschrijvingen moeten nauwkeurige beschrijvingen van de merchandise bevatten, met details zoals functionaliteit, specificaties, kenmerken, retour- of ruilbeleid en oorsprong. Zorg ervoor dat al je commerce producten volledige beschrijvingen in Shopify hebben om goedgekeurd te worden voor verkoop. Zie [Commerce Normen](https://en.help.roblox.com/hc/articles/36495190721172)  voor meer informatie.

Net als bij andere productinformatie die vanuit Shopify is gesynchroniseerd, zijn alle updates aan de productbeschrijving onderhevig aan het [moderatieproces voor catalogusitems](#catalogusitems-wijzigen) . De productdetails blijven de eerder goedgekeurde beschrijving tonen totdat de nieuwe inhoud is goedgekeurd door moderatie.

### [Aanvullende informatie](#aanvullende-informatie)[](#aanvullende-informatie)

De sectie Aanvullende informatie  toont aanvullende details over je product met behulp van inklapbare accordions. Je kunt tot vijf  accordionsecties voor verschillende onderwerpen toevoegen, zoals "Materialen", "Verzorgingsinstructies" of "Maatvoering".

Dit is een optionele functie en wordt gevuld met behulp van Shopify productmetavelden. Om een metafield-accordion in Shopify te maken:

-

Definieer een productmetafield in je Shopify-winkel met een specifieke namespace: Roblox.pdp_info_ .

-

Je kunt een unieke identifier aan deze namespace toevoegen, zoals Roblox.pdp_info_materials  of Roblox.pdp_info_care_instructions .

-

Stel de volgende velden in:

-

Naam  — De waarde in dit veld wordt weergegeven als de kop voor die accordion.

-

Type  — Alleen "Multi-line text" wordt ondersteund.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/commerce-products/Commerce-Product-Metafield-Example.png)

-

Stel vervolgens de Waarde  van het metafield in voor elk gewenst product. Deze waarde wordt weergegeven als de inhoud voor die accordion.

Net als andere productinhoud die vanuit Shopify is gesynchroniseerd, zijn alle nieuwe of bijgewerkte informatie in deze metafields onderhevig aan het [moderatieproces voor catalogusitems](#catalogusitems-wijzigen) . Deze pagina toont eerder goedgekeurde inhoud totdat de nieuwe informatie is goedgekeurd.

### [Virtueel voordeel bij aankoop](#virtueel-voordeel-bij-aankoop)[](#virtueel-voordeel-bij-aankoop)

Als je een [digitaal voordeel](#digitale-voordelen)  aan je product hebt gebundeld, toont deze sectie het virtuele item dat gebruikers ontvangen met hun aankoop. Deze sectie biedt een duidelijke visuele en informatieve aanwijzing aan gebruikers over de toegevoegde digitale waarde die ze ontvangen, waardoor de aantrekkingskracht van je commerce product wordt vergroot.

De inhoud in deze sectie hangt af van het type virtueel item dat wordt aangeboden:

-

Avataritem

-

Deze sectie toont de thumbnail en naam van het avataritem.

-

Gebruikers kunnen op deze sectie klikken om een 3D-preview van het avataritem te bekijken.

-

De beschrijving van het avataritem wordt weergegeven wanneer de gebruiker in deze sectie klikt.

-

Ontwikkelaarsproduct

-

Deze sectie toont de afbeelding en naam van het ontwikkelaarsproduct.

-

De beschrijving van het ontwikkelaarsproduct wordt weergegeven wanneer de gebruiker in deze sectie klikt.

Het specifieke avataritem of ontwikkelaarsproduct, inclusief de naam, beschrijving en afbeelding, wordt geconfigureerd wanneer je [de commerce productbundel aanmaakt](#aanmaken) . Aangezien deze voordelen deel uitmaken van de algehele productaanbieding, zijn ze onderhevig aan de inhoudsbeleid en moderatie van Roblox.

### [Meer van deze game](#meer-van-deze-game)[](#meer-van-deze-game)

Deze sectie toont andere commerce producten die je aanbiedt en momenteel te koop zijn binnen dezelfde Roblox-game. Deze feed moedigt verder verkennen van je productcatalogus aan en kan helpen de zichtbaarheid van het volledige assortiment van productaanbiedingen van je game te vergroten.

In deze sectie kunnen gebruikers de feature-afbeelding, naam en prijs van het product bekijken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
