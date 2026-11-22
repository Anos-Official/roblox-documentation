<!-- Source: https://create.roblox.com/docs/nl-nl/production/promotion/experience-notifications -->

Ervaringsmeldingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Ontdekking](/docs/nl-nl/discovery)

# Ervaringsmeldingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Ervaringsmeldingen  zijn een manier voor [ingeschreven](https://en.help.roblox.com/hc/en-us/articles/24769602332692-Out-of-Experience-Notifications)  gebruikers van 13 jaar en ouder om op de hoogte te blijven van hun favoriete games via tijdige, gepersonaliseerde meldingen. Als ontwikkelaar kun je bepalen welke soorten in-game activiteiten het belangrijkst zijn om je gebruikers over te informeren, evenals de inhoud van de meldingen.

Asynchrone Activiteit Vooruitgang / Prestatie Gebruikersvermeldingen

![Voorbeeldmelding](https://prod.docsiteassets.roblox.com/assets/open-cloud/experience-notifications/Example-Notification-A.png)

![Voorbeeldmelding](https://prod.docsiteassets.roblox.com/assets/open-cloud/experience-notifications/Example-Notification-D.png)

Het ervaringsmeldingssysteem heeft de volgende kenmerken:

-

Aanpasbare meldingen met parameters  — Volledige flexibiliteit om de [meldingsboodschap](#maak-een-meldingsstring)  aan te passen met parameters, bijvoorbeeld:

Je gouden gans ei is uitgekomen!

Allie @LaterSk8er1 heeft net jouw record op het Tokyo Tour-circuit verbroken!

-

Startgegevens  — Voeg optionele [startgegevens](#neem-start--en-analyticsgegevens-op)  toe die kunnen worden gelezen via [Player:GetJoinData()](/docs/nl-nl/reference/engine/classes/Player#GetJoinData)  wanneer de ontvanger van de melding zich aanmeldt. Dit kan inhouden dat een gebruiker naar een coördinaatlocatie wordt geleid of dat hun aanmeldervaring wordt gepersonaliseerd.

-

Analytics-ondersteuning  — Volg je bereikbare publiek en de prestaties van je meldingen in het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

## [Geschiktheidseisen](#geschiktheidseisen)[](#geschiktheidseisen)

In order to use the APIs to send notifications, the game must meet the following base criteria:

-

Minimum 100 visits since launch.

-

The game must not be under moderation.

-

You as the developer must have permission to manage the game.

## [Gebruik richtlijnen](#gebruik-richtlijnen)[](#gebruik-richtlijnen)

Beste praktijken

Meldingen moeten gepersonaliseerd  zijn voor de ontvanger en moeten gebaseerd zijn op in-game activiteiten die specifiek relevant zijn voor de gebruiker. Omgekeerd mogen meldingen niet van een generieke, advertentieachtige aard zijn.

Je bent nog 2 races verwijderd van het voltooien van de wekelijkse uitdaging!

Er is een nieuwe lijn raceauto's verschenen in Race Car Craze. Bekijk ze!

Idealiter moeten meldingen gebruikers ook waarschuwen voor iets waar ze onmiddellijk actie  op kunnen ondernemen. Vermijd puur informatieve meldingen die geen directe reactie of actie uitlokken.

Allie @LaterSk8er1 heeft zojuist jouw record op het Tokyo Tour-circuit verbroken! Tijd voor wraak?

Het is al een paar dagen geleden dat je aan een race met Allie @LaterSk8er1 hebt deelgenomen.

Respecteer de gemeenschapsnormen

Alle inhoud en gedragingen van meldingen zijn onderhevig aan Roblox's [Gemeenschapsnormen](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  en platformbrede [tekstfiltering](/docs/nl-nl/ui/text-filtering) , ongeacht de [inhoudsbeoordelingen](/docs/nl-nl/production/promotion/content-ratings)  van jouw game. Dit betekent dat als jouw game een 18+ game is, jouw meldingen nog steeds onderhevig zijn aan de platformbrede normen, niet  de [Beleid voor Leeftijdsbeperkte Inhoud](https://en.help.roblox.com/hc/en-us/articles/15869919570708-Restricted-Content-Policy) .

Vermijd misleidende duwtactieken

Inhoud van meldingen is niet  toegestaan om donkere patronen of andere tactieken te incorporeren die gebruikers manipuleren of misleiden om keuzes te maken die ze niet van plan zijn, of die mogelijk tegen hun beste belangen ingaan. Dit kan het volgende omvatten:

-

Verklede advertenties  — Meldingen die opzettelijk zijn verkleed als organische inhoud, maar in werkelijkheid advertenties zijn. Bijvoorbeeld, stel je voor dat het klikken op de volgende melding leidt naar Petz World, maar er wordt geen "belangrijke informatie" weergegeven.

Klik hier voor belangrijke informatie over jouw Petz World-account.

-

Tijddrukacties  — Meldingen die gebruikers onder druk zetten om te klikken, zich te abonneren, in te stemmen of aankopen te doen door valse tijdsdruk toe te passen.

Doe een aankoop in Petz World in de komende 10 minuten om belangrijke gameplay-updates niet te missen!

-

Bait-and-switch met gratis items of andere beloningen  — Meldingen die gebruikers ten onrechte vertellen dat ze iets gratis zullen ontvangen wanneer dat niet het geval is. Bijvoorbeeld, bij het klikken op de volgende melding wordt duidelijk dat er iets anders nodig is om het cadeau te krijgen.

Speel nu Petz World en krijg een gratis hondenbed!

-

Gebruikers misleiden om aankopen te doen  — Meldingen die gebruikers misleiden om onbedoelde aankopen te doen. Bijvoorbeeld, stel je voor dat het klikken op de volgende melding direct leidt naar een aankoopsysteem dat is voorgeconfigureerd met items die de gebruiker niet heeft gekozen om te kopen.

Bekijk onze nieuwe Petz in Petz World!

Vergrendel gameplay niet

Games mogen niet  vereisen dat gebruikers meldingen inschakelen om deel te nemen of vooruitgang te boeken in de gameplay.

## [Implementatie](#implementatie)[](#implementatie)

Het implementeren van ervaringsmeldingen begint met [het maken van een meldingsstring](#maak-een-meldingsstring)  en het opnemen van het [pakket](#neem-het-pakket-op)  in je project. Zodra deze zijn ingesteld, kun je [meldingen verzenden](#stuur-een-ervaringsmelding)  met optionele [aangepaste parameters](#pas-meldingen-aan-met-parameters) .

Alternatief kun je de [Open Cloud API](/docs/nl-nl/cloud/guides/experience-notifications)  gebruiken om meldingen te activeren via vrije API-aanroepen.

### [Maak een meldingsstring](#maak-een-meldingsstring)[](#maak-een-meldingsstring)

As with [Player Invite Prompts](/docs/nl-nl/production/promotion/invite-prompts) , you must create and edit your notification strings in the [Creator Dashboard](https://create.roblox.com/dashboard/creations) . Er is geen standaard game-meldingsstring, dus deze stap is vereist.

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Net als bij [badges](/docs/nl-nl/production/publishing/badges)  zijn meldingsstrings gekoppeld aan een specifieke game . Zoek de thumbnail van die game en klik erop.

3.

In de linker kolom, onder Betrokkenheid , klik op Meldingen .

4.

In het middengebied, klik op de knop Maak een meldingsstring .

5.

Vul een identificatienaam in (alleen zichtbaar voor jou) en de aangepaste meldingsstring; deze is beperkt tot 99 tekens en kan onbeperkte aangepaste parameters bevatten. Meldingen gebruiken automatisch de titel van je game als de meldingtitel, maar je kunt ook {experienceName}  gebruiken om naar je game te verwijzen in de tekst van de melding.

Voorbeeld meldingsstrings:

Je bent {numQuests} quests verwijderd van het voltooien van de wekelijkse uitdaging!

Je {eggName} is uitgekomen! Kom je nieuwe huisdier ontmoeten.

Je hebt deze week {numRaces} races gewonnen en het {racetrackName} circuit ontgrendeld!

{userId-friend} heeft net jouw record op het Tokyo Tour circuit verbroken! Tijd voor wraak?

Voordat je meldingsstrings schrijft, bekijk de [richtlijnen](#usage-guidelines)  voor het gebruik van het systeem.

6.

Wanneer je klaar bent, klik op de knop Maak meldingsstring .

7.

Op de meldingenpagina, in de tabel met meldingen, klik op de ⋯  knop in de Acties  kolom en selecteer Kopieer asset-ID .

8.

Gebruik de gekopieerde ID voor de messageId  sleutelwaarde in de payload  tabel zoals gedemonstreerd in het voorbeeldscript.

### [Neem het pakket op](#neem-het-pakket-op)[](#neem-het-pakket-op)

Om ervaringsmeldingen te implementeren, moet je het Luau-pakket verkrijgen uit de [Creator Store](/docs/nl-nl/production/creator-store) .

1.

Open vanuit het Venster -menu of de Start -tabbladwerkbalk de [Toolbox](/docs/nl-nl/projects/assets/toolbox)  en selecteer het tabblad Creator Store .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Creator-Store-Tab.png)

2.

Zorg ervoor dat de sortering op Modellen  is geselecteerd, klik vervolgens op de knop Zie Alles  voor Categorieën .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Creator-Store-Categories-See-All.png)

3.

Zoek en klik op de tegel Pakketten .

4.

Zoek de Open Cloud -module en klik erop, of sleep het naar de 3D-weergave.

 ![](https://prod.docsiteassets.roblox.com/assets/open-cloud/experience-notifications/Toolbox-Package.png)

5.

Verplaats in het [Explorer](/docs/nl-nl/studio/explorer) -venster het hele OpenCloud -model naar ServerScriptService .

### [Stuur een ervaringsmelding](#stuur-een-ervaringsmelding)[](#stuur-een-ervaringsmelding)

Zodra je een [meldingsstring](#maak-een-meldingsstring)  hebt gemaakt en het [pakket](#neem-het-pakket-op)  in je project hebt opgenomen, kun je meldingen verzenden vanuit server-side scripts. Meldingen worden afgeleverd aan [ingeschreven](https://en.help.roblox.com/hc/en-us/articles/24769602332692-Out-of-Experience-Notifications)  gebruikers van 13 jaar en ouder via hun Roblox-meldingsstroom, waarna ze zich rechtstreeks via de knop Deelnemen  op de melding kunnen aanmelden en spawnen volgens jouw [startgegevens](#neem-start--en-analyticsgegevens-op) .

 ![Meldingenstroom op de Roblox-app](https://prod.docsiteassets.roblox.com/assets/open-cloud/experience-notifications/Notification-Stream.png)

Om een basismelding naar een specifieke gebruiker te sturen, neem je de [meldingsstring](#maak-een-meldingsstring)  asset ID op in het messageId -veld van de payload en roep je de [createUserNotification](#createusernotification)  functie aan met de [Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId)  van de ontvanger en de aanvraaggegevens.

Stuur een ervaringsmelding

```

local ServerScriptService = game:GetService("ServerScriptService")

local OCUserNotification = require(ServerScriptService.OpenCloud.V2.UserNotification)

local recipientPlayerID = 505306092

-- In de payload is "messageId" de waarde van de meldingsasset ID

local userNotification = {

	payload = {

		messageId = "5dd7024b-68e3-ac4d-8232-4217f86ca244",

		type = "MOMENT"

	}

}

local result = OCUserNotification.createUserNotification(recipientPlayerID, userNotification)

if result.statusCode ~= 200 then

	print(result.statusCode)

	print(result.error.code)

	print(result.error.message)

end

```

### [Pas meldingen aan met parameters](#pas-meldingen-aan-met-parameters)[](#pas-meldingen-aan-met-parameters)

Om de melding voor elke ontvanger aan te passen, kun je parameters  opnemen in de [meldingsstring](#maak-een-meldingsstring)  en vervolgens de parameters aanpassen bij het aanroepen van de API. Je kunt bijvoorbeeld de meldingsstring definiëren als:

{userId-vriend} heeft jouw hoogste score met {punten} punten verbroken! Tijd om te levelen?

Stel vervolgens de userId-vriend  en punten  parameters in het script in:

Pas melding aan met parameters

```

local ServerScriptService = game:GetService("ServerScriptService")

local OCUserNotification = require(ServerScriptService.OpenCloud.V2.UserNotification)

local recipientPlayerID = 505306092

local userIdVriendParam = {int64Value = 3702832553}

local puntenParam = {stringValue = "5"}

-- In de payload is "messageId" de waarde van de meldingsasset ID

-- In dit voorbeeld is de meldingsstring "{userId-vriend} heeft jouw hoogste score met {punten} punten verbroken! Tijd om te levelen?"

local userNotification = {

	payload = {

		messageId = "ef0e0790-e2e8-4441-9a32-93f3a5783bf1",

		type = "MOMENT",

		parameters = {

			["userId-vriend"] = userIdVriendParam,

			["punten"] = puntenParam

		}

	}

}

local result = OCUserNotification.createUserNotification(recipientPlayerID, userNotification)

if result.statusCode ~= 200 then

	print(result.statusCode)

	print(result.error.code)

	print(result.error.message)

end

```

### [Vraag gebruikers om meldingen in te schakelen](#vraag-gebruikers-om-meldingen-in-te-schakelen)[](#vraag-gebruikers-om-meldingen-in-te-schakelen)

Om gebruikers aan te moedigen meldingen voor jouw ervaring in te schakelen, kun je een toestemmingprompt binnen de ervaring weergeven aan gebruikers van 13 jaar en ouder met behulp van de [ExperienceNotificationService:PromptOptIn()](/docs/nl-nl/reference/engine/classes/ExperienceNotificationService#PromptOptIn) -methode.

 ![De toestemmingprompt binnen de ervaring moedigt gebruikers aan om meldingen in te schakelen](https://prod.docsiteassets.roblox.com/assets/promotion/misc/In-Experience-Enable-Notifications.png)

Je kunt de prompt in elke geschikte context binnen jouw ervaring activeren die een toekomstige melding rechtvaardigt. De tekst van de prompt is niet aanpasbaar en is gestandaardiseerd voor alle ervaringen.

De modal verschijnt niet  als de gebruiker:

-

Jonger is dan 13 jaar.

-

Al meldingen voor jouw ervaring heeft ingeschakeld.

-

De toestemmingprompt voor jouw ervaring in de afgelopen 30 dagen al heeft gezien.

Om gebruikers om meldingen in te schakelen te vragen, moet je eerst bepalen of de gebruiker in aanmerking komt. Zodra dit is bevestigd, kun je de toestemmingprompt aan de gebruiker weergeven.

1.

Roep [ExperienceNotificationService:CanPromptOptInAsync()](/docs/nl-nl/reference/engine/classes/ExperienceNotificationService#CanPromptOptInAsync)  aan, ingepakt in een [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  omdat het een asynchrone netwerkoproep is die af en toe kan mislukken.

2.

Als de gebruiker kan worden gevraagd, roep dan [ExperienceNotificationService:PromptOptIn()](/docs/nl-nl/reference/engine/classes/ExperienceNotificationService#PromptOptIn)  aan.

LocalScript - Implementatie van de meldingstoestemmingprompt

```

local ExperienceNotificationService = game:GetService("ExperienceNotificationService")

-- Functie om te controleren of de speler kan worden gevraagd om meldingen in te schakelen

local function canPromptOptIn()

	local success, canPrompt = pcall(function()

		return ExperienceNotificationService:CanPromptOptInAsync()

	end)

	return success and canPrompt

end

local canPrompt = canPromptOptIn()

if canPrompt then

	local success, errorMessage = pcall(function()

		ExperienceNotificationService:PromptOptIn()

	end)

end

-- Luister naar het evenement dat de opt-in prompt is gesloten

ExperienceNotificationService.OptInPromptClosed:Connect(function()

	print("Opt-in prompt gesloten")

end)

```

### [Neem start- en analyticsgegevens op](#neem-start--en-analyticsgegevens-op)[](#neem-start--en-analyticsgegevens-op)

Om de gebruikerservaring verder te verbeteren, kun je startgegevens  opnemen in de melding, nuttig voor scenario's zoals het leiden van gebruikers naar een coördinaatlocatie of het personaliseren van de aanmeldervaring. Daarnaast kun je [analytics](#analytics)  gegevens opnemen om de prestaties van verschillende categorieën meldingen te segmenteren. Raadpleeg ook het voorbeeld van [Speler uitnodigingsprompts](/docs/nl-nl/production/promotion/invite-prompts#inclusief-startgegevens)  over hoe startgegevens kunnen worden ingesteld en gebruikt.

Neem startgegevens en analyticsgegevens op

```

local ServerScriptService = game:GetService("ServerScriptService")

local OCUserNotification = require(ServerScriptService.OpenCloud.V2.UserNotification)

local recipientPlayerID = 505306092

-- In de payload is "messageId" de waarde van de meldingsasset ID

local userNotification = {

	payload = {

		messageId = "5dd7024b-68e3-ac4d-8232-4217f86ca244",

		type = "MOMENT",

		joinExperience = {

			launchData = "Test_Launch_Data"

		},

		analyticsData = {

			category = "Test_Analytics_Category"

		}

	}

}

local result = OCUserNotification.createUserNotification(recipientPlayerID, userNotification)

if result.statusCode ~= 200 then

	print(result.statusCode)

	print(result.error.code)

	print(result.error.message)

end

```

## [Leveringssysteem](#leveringssysteem)[](#leveringssysteem)

A spampreventiesysteem bestaat om de kwaliteit van meldingen voor gebruikers te waarborgen en het gedeelde meldingskanaal voor alle ontwikkelaars te beschermen. Vanwege dit systeem is de levering van meldingen niet gegarandeerd. Dit spampreventiesysteem wordt rechtstreeks beïnvloed door de betrokkenheid van gebruikers: hoe meer gebruikers betrokken zijn bij uw meldingen, hoe meer bereik ze zullen ontvangen. U kunt de betrokkenheidsstatistieken transparant volgen in het analysemenu, zoals hieronder uitgelegd.

Ervaringsmeldingen hebben een statische throttlinglimiet; elke gebruiker kan één melding per dag ontvangen van een bepaalde ervaring, en u ontvangt transparante feedback wanneer de throttlinglimiet van een gebruiker is bereikt.

Bovendien schetst de volgende lijst enkele van de speciale gevallen die kunnen leiden tot niet-levering  van een melding:

-

Er zijn niet voldaan aan de geschiktheidseisen  voor de ervaring.

-

De ontvanger heeft zich niet aangemeld voor meldingen van uw ervaring.

-

De throttlinglimiet van de ontvanger voor uw ervaring is bereikt.

-

De totale dagelijkse throttlinglimiet van de ontvanger is bereikt.

-

Ontbrekende of ongeldige aanvraagparameters.

-

De meldingsstring is gemodereerd.

-

Voor meldingen met gebruikersvermeldingen vindt niet-levering plaats als aan een van deze voorwaarden is voldaan:

-

De ontvanger en de genoemde gebruiker zijn geen vrienden.

-

De genoemde gebruiker heeft Nee  geselecteerd voor "Vrienden op de hoogte houden van mijn activiteit?" onder Privacy  → Andere Instellingen  in hun Roblox-accountinstellingen.

## [Analytics](#analytics)[](#analytics)

Performance van uw meldingen en meldbare publiek worden weergegeven in het Analytics  tabblad van de Notifications  pagina waar u meldingsstrings configureert (simply tab van Creations  naar Analytics ).

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Net als bij [badges](/docs/nl-nl/production/publishing/badges) , zijn meldingsstrings gekoppeld aan een specifiek spel . Zoek de thumbnail van dat spel en klik erop.

3.

In de linkerkolom, onder Engagement , klik op Notifications .

4.

Op de doelpagina, klik op het Analytics  tabblad om over te schakelen naar het analytics dashboard.

### [Meldingenoverzicht](#meldingenoverzicht)[](#meldingenoverzicht)

De samenvattingssectie dient als een momentopname van de totale prestaties van uw meldingen. Een minimum van 100 totale impressies is vereist om de prestatiestatistieken weer te geven.

 ![](https://prod.docsiteassets.roblox.com/assets/open-cloud/experience-notifications/Analytics-Summary.png)

| Statistiek | | Beschrijving |
| --- | --- |
| Ingeschreven Gebruikers | | Het totale aantal gebruikers dat meldingen voor uw game heeft ingeschakeld. Houd er rekening mee dat dit ook gebruikers onder de 13 jaar omvat die alleen meldingen van [ervaring updates](/docs/nl-nl/production/promotion/experience-events#announce-experience-updates)  kunnen ontvangen, niet gepersonaliseerde [ervaring meldingen](/docs/nl-nl/production/promotion/experience-notifications) . |
| Impressies | | Het totale aantal gebruikersimpressies dat al uw meldingen in totaal hebben ontvangen. |
| Klikken | | Het totale aantal klikken dat al uw meldingen in totaal hebben ontvangen. |
| CTR | | De snelheid waarmee gebruikers op uw meldingen klikken, berekend als de verhouding van klikken tot impressies. |
| Uitschakelen | | De snelheid waarmee gebruikers meldingen voor uw game direct vanuit uw meldingen uitschakelen, berekend als de verhouding van uitschakelacties tot impressies. |
| Afwijzen | | De snelheid waarmee gebruikers uw meldingen afwijzen, berekend als de verhouding van afwijsacties tot impressies. |

### [Gedetailleerde statistieken](#gedetailleerde-statistieken)[](#gedetailleerde-statistieken)

De Ervaringsmeldingen  tabel toont gedetailleerde prestatiestatistieken voor elke melding met ten minste 100 vertoningen, gesorteerd op de datum van de eerste vertoning voor die melding.

 ![](https://prod.docsiteassets.roblox.com/assets/open-cloud/experience-notifications/Analytics-Itemized.png)

De Naam  kolom is de belangrijkste identifier voor de melding. Standaard komt de naam overeen met de identifier naam die je hebt opgegeven bij het [maken van de meldingsstring](#create-a-notification-string) , maar je kunt deze overschrijven via het category  veld in je API-aanroepen, in welk geval category  de naam overschrijft. Het wijzigen van de stringnaam in het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  of het wijzigen van de string waar je bericht-ID naar verwijst in de API-aanroep zal een nieuwe rij in de tabel genereren.

Als je de prestaties van verschillende strings wilt A/B-testen, is het aan te raden om een geheel nieuwe meldingsstring te maken met een vergelijkbare naam, bijvoorbeeld:

-

EggHatchA  — "Je gouden ei is uitgekomen! Kom je nieuwe huisdier ontmoeten."

-

EggHatchB  — "Het is tijd om uit te komen! Kom je nieuwe huisdier ontmoeten."

## [API-referentie](#api-referentie)[](#api-referentie)

### [Functies](#functies)[](#functies)

#### [createUserNotification](#createusernotification)[](#createusernotification)

 ** createUserNotification (** userId : [number](/docs/nl-nl/luau/numbers) , userNotification : [UserNotification](#usernotification)** )**  : [UserNotificationResult](#usernotificationresult)

Verzendt een melding vanuit een server-side script. Vereist de [Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId)  van de ontvanger en een [UserNotification](#usernotification) . Retourneert een [UserNotificationResult](#usernotificationresult) .

Stuur een ervaringsmelding

```

local ServerScriptService = game:GetService("ServerScriptService")

local OCUserNotification = require(ServerScriptService.OpenCloud.V2.UserNotification)

local recipientPlayerID = 505306092

-- In de payload is "messageId" de waarde van de meldingsasset ID

local userNotification = {

	payload = {

		messageId = "5dd7024b-68e3-ac4d-8232-4217f86ca244",

		type = "MOMENT"

	}

}

local result = OCUserNotification.createUserNotification(recipientPlayerID, userNotification)

if result.statusCode ~= 200 then

	print(result.statusCode)

	print(result.error.code)

	print(result.error.message)

end

```

### [Types](#types)[](#types)

#### [UserNotification](#usernotification)[](#usernotification)

Tabel met details over de melding die naar de gebruiker moet worden verzonden. Moet een payload -tabel bevatten met vereiste messageId  en type -strings, en optionele parameters , joinExperience  en analyticsData -tabellen.

| Sleutel | | Type | | Beschrijving |
| messageId | | string | | Een ID die een aanpasbare meldingsboodsjablon vertegenwoordigt die je maakt in het [Creator Dashboard](https://create.roblox.com/dashboard/creations) . |
| type | | string | | Het type melding. Momenteel wordt alleen "MOMENT"  ondersteund. |
| parameters | | table | | Een tabel met parameters die worden gebruikt om een meldingsboodsjablon weer te geven. Zie [Pas meldingen aan met parameters](#pas-meldingen-aan-met-parameters)  voor voorbeeldgebruik. |
| joinExperience | | table | | Een call-to-action die het deelnemen aan een ervaring vertegenwoordigt. Ondersteunt momenteel een launchData  sleutel-waarde paar dat willekeurige gegevens vertegenwoordigt die beschikbaar zijn voor een ervaring wanneer een gebruiker zich vanuit de melding aanmeldt; deze waarde is beperkt tot maximaal 200 bytes. Zie [Neem start- en analyticsgegevens op](#neem-start--en-analyticsgegevens-op)  voor voorbeeldgebruik. |
| analyticsData | | table | | Gegevens over hoe analytics worden gerapporteerd. Ondersteunt momenteel een category  sleutel-waarde paar dat de meldingscategorie vertegenwoordigt, gebruikt om analyticsgegevens te groeperen. Zie [Neem start- en analyticsgegevens op](#neem-start--en-analyticsgegevens-op)  voor voorbeeldgebruik. |

#### [UserNotificationResult](#usernotificationresult)[](#usernotificationresult)

Een wrapper-object dat de reactie van een verzonden melding bevat. Bevat de volgende sleutel-waarde paren:

| Sleutel | | Type | | Beschrijving |
| statusCode | | number | | De HTTP-statuscode voor de aanvraag. |
| error | | table | | Tabel met code  en message  sleutels die de GRPC-foutcode en het foutbericht beschrijven, respectievelijk. |
| response | | table | | Tabel met id  en path  sleutels die een unieke UUID en het resourcepad van de gebruikersmelding beschrijven, respectievelijk. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
