<!-- Source: https://create.roblox.com/docs/nl-nl/production/localization -->

Lokalisatie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Lokalisatie

# Lokalisatie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox-gebruikers komen uit verschillende culturen over de hele wereld en spreken verschillende talen. Het effectief gebruiken van lokalisatie -tools zorgt ervoor dat alle gebruikers je game kunnen begrijpen en ervan kunnen genieten zoals bedoeld. Elke game kan onmiddellijk profiteren van Roblox's automatische lokalisatietools om je potentiële publiek direct uit te breiden. Naarmate je game groeit, gebruik je de verschillende lokalisatie-API-tools van Roblox, handmatige vertalersportalen en analyses om ervoor te zorgen dat gebruikers van over de hele wereld volledig kunnen deelnemen en socialiseren in je game.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Concept-Banner.jpg)

## [Gebruikersinstelling](#gebruikersinstelling)[](#gebruikersinstelling)

Elke gebruiker heeft een Automatische Vertalingen -instelling op hun [Accountinstellingen](https://www.roblox.com/my/account#!/info)  pagina waarmee ze automatische vertaling voor game-inhoud kunnen inschakelen. Als een speler deze instelling inschakelt, worden alle gamenamen, gamebeschrijvingen en in-game tekst voor hen vertaald, zelfs als je vertaling voor je game niet expliciet hebt ingeschakeld.

Als je enige [handmatige vertalingen](#handmatige-vertalingen)  aan je game toevoegt, zullen ze altijd aan spelers worden getoond . Roblox genereert alleen automatisch vertalingen als ze ontbreken. Volg de onderstaande stappen om de lokalisatie-instellingen voor je game in te schakelen en vertalingen te beheren.

Er kan tekst in je game zijn die nooit vertaald mag worden (bijvoorbeeld NPC-namen of straatnaamborden). Om ervoor te zorgen dat er geen vertalingen voor hen worden gegenereerd, kun je de [AutoLocalize](/docs/nl-nl/reference/engine/classes/GuiBase2d#AutoLocalize) -eigenschap voor die objecten in Studio uitschakelen.

## [Lokalisatie-instellingen](#lokalisatie-instellingen)[](#lokalisatie-instellingen)

De lokalisatie-instellingen van je game zijn de startplaats voor het inschakelen van vertalingen en het openen van je lokalisatietools. Je moet je [bron](#stel-brontaal-in)  en [ondersteunde](#stel-ondersteunde-talen-in)  talen instellen voordat je begint met lokaliseren naar een nieuwe taal.

De lokalisatiepagina bevat ook tools om te beginnen met het vertalen van je games, vertaalcollaborateurs toe te voegen en vertaalanalyses te downloaden.

Je kunt de lokalisatie-instellingen van je game openen via de hoofdpagina van het Creator Dashboard:

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com) .

2.

Beweeg met de muis over je game en klik op Beheer Ervaring .

3.

Navigeer in de linker navigatie naar Publiek  → Lokalisatie .

Je kunt ook de lokalisatie-instellingen van je game openen op je [Creations](https://create.roblox.com/dashboard/creations)  pagina:

1.

Navigeer naar je [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Zoek in het tabblad Ervaringen  je game en selecteer de ⋯  knop.

3.

Selecteer Configureer Lokalisatie .

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Experience-Page-Configure-Localization.png)

### [Stel brontaal in](#stel-brontaal-in)[](#stel-brontaal-in)

Voordat je met lokaliseren kunt beginnen, moet Roblox weten welke taal je aan het vertalen bent en naar welke talen je aan het vertalen bent.

De brontaal  is de primaire taal waarin de game is geschreven. Roblox ondersteunt momenteel slechts één brontaal tegelijk. De standaard is ingesteld op de [Roblox-accounttaal](https://www.roblox.com/my/account#!/info) .

Om de brontaal  in te stellen:

1.

Navigeer in de lokalisatie-instellingen naar Talen  en selecteer de dropdown voor Brontaal .

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Change-Source-Language-Dropdown.png)

2.

Selecteer een taal uit de lijst.

3.

Klik op Bevestigen  om de taal toe te voegen.

### [Stel ondersteunde talen in](#stel-ondersteunde-talen-in)[](#stel-ondersteunde-talen-in)

De ondersteunde talen  zijn de talen waarvoor je van plan bent vertalingen aan te bieden. Je kunt meerdere ondersteunde talen voor je game hebben. Zie [talen codes](/docs/nl-nl/production/localization/language-codes)  voor een lijst van alle talen die Roblox ondersteunt. Om de ondersteunde  talen in te stellen:

1.

Navigeer in de lokalisatie-instellingen naar Talen  en selecteer de Brontaal .

2.

Klik in de sectie Ondersteunde Talen  op Taal Toevoegen  om de talen toe te voegen waarvoor je van plan bent te lokaliseren.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Add-Languages.png)

3.

Klik op het invoerveld en typ de taal die je wilt toevoegen, of selecteer uit de lijst met talen.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Add-Languages-Menu.png)

4.

Klik op Bevestigen  om de taal toe te voegen.

## [Automatische vertalingen](#automatische-vertalingen)[](#automatische-vertalingen)

De automatische vertaaltool van Roblox is beschikbaar voor elke game en stelt je in staat om onmiddellijk te beginnen met het lokaliseren van de strings in je game en je potentiële publiek te verbreden. In veel gevallen kun je aanzienlijke vooruitgang boeken in je lokalisatieproces met behulp van automatische vertalingen voordat je [handmatige vertalingen](#handmatige-vertalingen)  toevoegt of samenwerkt met [vertalers](#samenwerken-met-vertalers) .

Voor meer informatie over het inschakelen van automatische vertalingen in je game, zie [Automatische vertalingen](/docs/nl-nl/production/localization/automatic-translations) .

## [Handmatige vertalingen](#handmatige-vertalingen)[](#handmatige-vertalingen)

Pas verschillende aanpassingen toe op je vertalingen om de lokalisatie van je game te verbeteren en uit te breiden. Jij, of een toegewezen vertaler, kunnen handmatig vertalingen toevoegen en wijzigen in de vertaaltafel van je game. Je kunt deze tabel ook programmatisch openen, zodat je contextuele vertalingen kunt maken, afbeeldingen of assets kunt wisselen op basis van taal, of zelfs handmatig vertalingen van een andere taal kunt weergeven.

Voor meer informatie over aangepaste vertaalgebruiksscenario's, zie [Vertaal in-game inhoud](/docs/nl-nl/production/localization/manual-translations) .

## [Afbeelding vertalingen](#afbeelding-vertalingen)[](#afbeelding-vertalingen)

De afbeeldingsvertalings-tool van Roblox is momenteel in bèta en stelt je in staat om automatisch afbeeldingen met tekst te vertalen terwijl je de stijl van de originele tekst behoudt. We ondersteunen nog niet alle talen voor afbeeldingsvertalingen; momenteel worden alleen Frans, Duits, Indonesisch, Italiaans, Koreaans, Portugees en Spaans ondersteund.

Voor meer informatie over het inschakelen van afbeeldingsvertalingen in je game, zie [Afbeelding vertalingen](/docs/nl-nl/production/localization/image-translations) .

## [Samenwerken met vertalers](#samenwerken-met-vertalers)[](#samenwerken-met-vertalers)

Voeg Roblox-gebruikers toe als vertalers voor je game om je te helpen automatische vertalingen te beoordelen en te verfijnen of handmatige vertalingen te bieden en te bewerken.

Je kunt maandelijkse analyses downloaden om je vertaaldekking en de bijdrage van je vertalers bij te houden. Voor meer informatie over het werken met lokalisatiebijdragers, zie [Samenwerken met vertalers](/docs/nl-nl/production/localization/work-with-translators) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
