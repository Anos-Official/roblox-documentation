<!-- Source: https://create.roblox.com/docs/nl-nl/production/localization/image-translations -->

Afbeelding vertalingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Lokalisatie
6. /
7. Automatische vertaling

# Afbeelding vertalingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Afbeeldingvertaling is momenteel in beta. Functionaliteit en beschikbaarheid kunnen veranderen.

Afbeeldingvertaling  vertaalt automatisch afbeeldingen met tekst in je game, waarbij de stijl van de originele tekst zo nauwkeurig mogelijk wordt nagebootst. Dit stelt je in staat om borden, UI-grafieken en andere tekst-in-afbeelding inhoud te lokaliseren zonder handmatig een versie voor elke ondersteunde taal te maken.

## [Hoe afbeeldingvertaling werkt](#hoe-afbeeldingvertaling-werkt)[](#hoe-afbeeldingvertaling-werkt)

Het afbeeldingvertalingssysteem van Roblox is getraind om de lettergrootte, stijl en kleur van de originele tekst zo nauwkeurig mogelijk te matchen in de vertaalde afbeelding. Alle niet-tekst elementen in de afbeelding blijven precies hetzelfde.

Bijvoorbeeld, de volgende borden behouden hun originele kleur, letterstijl en lay-out in zowel de bron- als de vertaalde afbeelding:

![](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Example-Cash-English.png) Engels (Bron)

![](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Example-Cash-Korean.png) Koreaans

![](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Example-Ice-Cream-English.png) Engels (Bron)

![](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Example-Ice-Cream-Spanish.png) Spaans

We ondersteunen nog niet alle talen voor afbeeldingvertaling. Alleen de volgende talen worden momenteel ondersteund:

-

Frans

-

Duits

-

Indonesisch

-

Italiaans

-

Koreaans

-

Portugees

-

Spaans

Automatische afbeeldingvertaling is standaard niet ingeschakeld. Je kunt het inschakelen in de lokalisatie-instellingen van je ervaring in Creator Hub, zoals beschreven in de volgende sectie.

## [Automatische afbeeldingvertaling inschakelen](#automatische-afbeeldingvertaling-inschakelen)[](#automatische-afbeeldingvertaling-inschakelen)

Om afbeeldingen in je game te vertalen, schakel je de volgende drie instellingen in de lokalisatie-instellingen van je ervaring in.

1.

Navigeer naar het tabblad Talen  en schakel afbeeldingvertaling in voor elke taal die je wilt ondersteunen.

 ![De sectie Lokalisatie Talen toont de optie om automatische vertaling voor ervaring afbeeldingen voor een taal in te schakelen.](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Enable-Per-Language.png)

2.

Navigeer naar het tabblad Instellingen  en schakel Automatische Afbeelding Captatie  in. Dit stelt Roblox in staat om automatisch te detecteren welke afbeeldingen in je game tekst bevatten en vertaald moeten worden.

Zodra het is ingeschakeld, voegt Roblox in aanmerking komende afbeeldingen toe aan je lokalisatietabel wanneer spelers ze in je game tegenkomen. Afbeeldingvertaling is niet onmiddellijk — het kan tot enkele dagen duren voordat afbeeldingen zijn vastgelegd en vertalingen zijn gegenereerd.

 ![De sectie Lokalisatie Instellingen benadrukt de schakelaar voor Automatische Afbeelding Captatie.](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Automatic-Image-Capture.png)

3.

Schakel in het tabblad Instellingen  Gebruik Vertaald Inhoud  in voor afbeeldingen om vertaalde afbeeldingen live aan spelers te tonen. Als je vertaalde afbeeldingen in Creator Hub wilt bekijken voordat spelers ze zien, laat je deze instelling uitgeschakeld totdat je de vertalingen hebt beoordeeld en klaar bent om ze weer te geven.

 ![De sectie Lokalisatie Instellingen benadrukt de schakelaar voor het inschakelen van vertaalde afbeeldingen in de ervaring.](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Use-Translated-Content.png)

## [Beheer vertaalde afbeeldingen](#beheer-vertaalde-afbeeldingen)[](#beheer-vertaalde-afbeeldingen)

Afbeeldingen die aan je lokalisatietabel zijn toegevoegd, verschijnen in het tabblad Afbeeldingen  van de Vertaalpagina. Om daar te komen, navigeer je naar de lokalisatiepagina van je game en selecteer je Vertalen .

 ![De sectie Lokalisatie Talen benadrukt de Vertaal knop.](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Translate-Button.png)

Selecteer het tabblad Afbeeldingen  om een zij-aan-zij vergelijking van de bron- en vertaalde afbeelding voor elke vermelding in je lokalisatietabel te zien.

 ![De Vertaalpagina Afbeeldingen tab toont een zij-aan-zij vergelijking van een bronafbeelding en zijn vertaalde afbeelding.](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Images-Tab.png)

Als er een vertaling is die je niet bevalt, kun je deze uitschakelen door de [AutoLocalize](/docs/nl-nl/reference/engine/classes/GuiBase2d#AutoLocalize)  eigenschap voor die afbeelding in Studio uit te schakelen. Je kunt ook feedback geven over een vertaling die je niet bevalt door op het pictogram rechtsonder in de vertaalde afbeelding te klikken.

 ![De Vertaalpagina Afbeeldingen tab benadrukt het feedbackpictogram rechtsonder in een vertaalde afbeelding.](https://prod.docsiteassets.roblox.com/assets/localization/Image-Translation-Feedback-Icon.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
