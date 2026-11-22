<!-- Source: https://create.roblox.com/docs/nl-nl/chat/preset-system-guidelines -->

Richtlijnen voor het presetsysteem | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Chat
6. /
7. [Tekstchat](/docs/nl-nl/chat/in-experience-text-chat)

# Richtlijnen voor het presetsysteem

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Presetsystemen stellen gebruikers in staat om veilig vooraf gedefinieerde tekst naar elkaar te sturen om de gameplay te coördineren. Ze kunnen op verschillende manieren worden geïmplementeerd, zoals wielen waarmee gebruikers presets publiekelijk aan elkaar kunnen selecteren en verzenden in het spel.

Deze systemen * mogen niet*  worden gebruikt om onbeperkte, realtime, tweerichtingscommunicatie tussen spelers van verschillende leeftijden mogelijk te maken of om platformsystemen voor veiligheid te omzeilen. Ze zijn bedoeld om:

-

Snelle coördinatie in het spel te ondersteunen

-

Wrijving in veelvoorkomende gameplay-momenten te verminderen

-

De bestaande veiligheids- en leeftijdsgebonden communicatiebescherming van Roblox te behouden

Het ingebouwde [Snelle Woorden](/docs/nl-nl/chat/quick-words)  systeem van Roblox is een presetsysteem dat al voldoet aan deze richtlijnen. Gebruik het om aangepaste Snelle Woorden toe te voegen zonder je eigen presetsysteem te bouwen.

## [Richtlijnen](#richtlijnen)[](#richtlijnen)

Als je dit type systeem wilt implementeren, moet je je houden aan deze richtlijnen, die bedoeld zijn om je te helpen voldoen aan onze [Community Standards](https://about.roblox.com/community-standards)  en [Gebruiksvoorwaarden](https://en.help.roblox.com/hc/en-us/articles/115004647846-Roblox-Terms-of-Use) .

### [Veiligheid eerst](#veiligheid-eerst)[](#veiligheid-eerst)

Presetsystemen moeten bestaande veiligheidskenmerken van Roblox versterken – niet eromheen werken. Als het presetsysteem dynamische conversatie mogelijk maakt, ondermijnt het de veiligheid van het platform en voldoet het niet aan onze beleidsregels.

Vraag jezelf af : Breekt, omzeilt of omzeilt deze functie enige bestaande veiligheidskenmerken van Roblox door vrije, tweerichtings-, gerichte en dynamische conversatie mogelijk te maken? Als dat zo is, moet het systeem de vereisten respecteren dat gebruikers leeftijdscontrole ondergaan (via [Gezichtsleeftijdsinschatting](https://about.roblox.com/age-estimation)  of [ID-verificatie](/docs/nl-nl/production/publishing/account-verification#verifi%C3%ABren-via-overheidsidentificatie) ) en van een [vergelijkbare leeftijd zijn om te chatten](https://en.help.roblox.com/hc/en-us/articles/43611824582292-How-to-Chat-on-Roblox) .

Als het systeem dat je wilt implementeren puur bedoeld is om spelers te helpen communiceren over acties in het spel, bevestigingen of basisreacties, kun je een presetsysteem gebruiken dat gebruikers in staat stelt om presets naar elkaar te sturen, ongeacht leeftijd of leeftijdscontrolestatus.

### [Intentie, geen conversatie](#intentie-geen-conversatie)[](#intentie-geen-conversatie)

Presetsystemen zijn bedoeld voor het uiten van onmiddellijke gameplay-intentie, niet voor dialoog. Elke preset moet op zichzelf staan en compleet zijn zonder een reactie te vereisen die niet gerelateerd is aan de gameplay. Algemene heen-en-weer oproepen tot actie en antwoorden zoals "Help" gevolgd door een "OK" zijn acceptabel.

Presets moeten:

-

Relevant zijn voor de huidige spelmodus of scenario

-

Open eindige of sociaal verkennende taal vermijden

-

Bij voorkeur snel vervallen of irrelevant worden buiten het moment

Presets mogen niet:

-

Slang bevatten die verborgen of evoluerende betekenissen kan hebben

-

Verwijzen naar contact, identiteit of relaties in de echte wereld

-

Emotionele manipulatie, sociale druk of inhoud bevatten die in strijd is met de Community Standards van Roblox

Voorbeelden

-

✅ "Hulp nodig"

-

✅ "Dit gebied verdedigen"

-

✅ "Klaar"

-

❌ "Waarom hielp je me niet?"

-

❌ "Vind je me leuk?"

### [Beperkte, eindige reikwijdte](#beperkte-eindige-reikwijdte)[](#beperkte-eindige-reikwijdte)

Presetsystemen mogen geen betekenis krijgen wanneer ze worden gecombineerd, herhaald of in volgorde worden gebruikt. Ze moeten verbonden zijn met de huidige spelcontext en irrelevant worden buiten het moment. Als spelers het wiel kunnen gebruiken om "alles te zeggen, gewoon langzamer," is het ontwerp niet toegestaan.

Voorbeelden

-

✅ "Geef de bal door"

-

✅ "Herladen"

-

✅ "Vijand in de buurt"

-

❌ "Waar kom je vandaan?"

-

❌ "Wat zijn je sociale media?"

## [Handhaving en beoordeling](#handhaving-en-beoordeling)[](#handhaving-en-beoordeling)

Alle inhoud en gerelateerde functies kunnen door Roblox worden beoordeeld om te zorgen voor naleving van onze richtlijnen en om gebruikers op het platform te beschermen. Dit kan onder meer inhouden:

-

Beoordelen van de inhoud van het presetsysteem tijdens de spelbeoordeling

-

Vereisen van wijzigingen of verwijdering als een systeem omzeiling mogelijk maakt of anderszins in strijd is met de Community Standards van Roblox

-

Uitschakelen van presetsysteemfuncties die de veiligheidsdoelen van het platform ondermijnen

-

Het nemen van aanvullende handhavingsmaatregelen tegen jouw spel, account of groep

Creators zijn verantwoordelijk voor het waarborgen dat alle inhoud en toekomstige updates blijven voldoen aan deze richtlijnen.

### [Vereisten](#vereisten)[](#vereisten)

Alle presetsystemen en hun functies moeten voldoen aan de volgende vereisten:

-

Alle UI van presets moet correct worden gelabeld als systeempreset  wanneer deze binnen de chat wordt weergegeven

-

Alle presetsystemen moeten visueel onderscheidend zijn van de native vrije chat van Roblox

-

Presets mogen geen eindtekens of terminale interpunctie bevatten, zoals uitroeptekens, vraagtekens of punten, om te voorkomen dat ze worden verward met algemene chatberichten

-

Alle presets moeten door [TextService:FilterStringAsync()](/docs/nl-nl/reference/engine/classes/TextService#FilterStringAsync)  gaan

-

Voeg een rate-limit toe (10 seconden per verzending)

-

Beperk het aantal weergegeven presets tot 12 of minder voor jouw Universum

### [Wat is toegestaan](#wat-is-toegestaan)[](#wat-is-toegestaan)

Presetsystemen mogen bevatten:

-

Tactische gameplay-opdrachten (bijv. "Aanvallen", "Verdedigen", "Positie vasthouden")

-

Coöperatieve opdrachten (bijv. "Volg mij", "Klaar", "Wacht")

-

Sport/FPS-stijl oproepen (bijv. "Herladen", "Dek me", "Mooie schot")

-

Neutrale aanmoedigingen of spelverklaringen (bijv. "Goed gespeeld", "Bedankt")

Deze moeten altijd eindig, gecureerd en door de creator gecontroleerd zijn.

### [Wat is niet toegestaan](#wat-is-niet-toegestaan)[](#wat-is-niet-toegestaan)

Presetsystemen mogen niet worden gebruikt om:

-

Vrije chat of conversatie te simuleren

-

Anderen te complimenteren of te vleien met uitspraken die niet gerelateerd zijn aan de gameplay

-

Dialoog heen en weer mogelijk te maken tussen leeftijdsgroepen

-

Aangepaste berichten te coderen

-

Chat-, DM- of spraakbeperkingen te omzeilen

-

Onbeperkte sociale functies te vervangen of te spiegelen

-

Vragen of sociale vragen

Voorbeelden van niet-toegestane patronen:

-

Alfabetwielen of nummer-gebaseerde codering

-

Vraag/antwoordstructuren ("Waarom?", "Omdat")

-

"Hoi!" "Hallo!" "Hoe gaat het?" "Wat is er aan de hand?"

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
