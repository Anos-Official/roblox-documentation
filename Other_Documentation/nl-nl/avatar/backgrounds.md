<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/backgrounds -->

Achtergronden | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Backgrounds

# Achtergronden

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Achtergronden  voor avatars zijn 2D-assets die achter een avatar op verschillende oppervlakken in Roblox worden weergegeven. Wanneer gebruikers achtergronden kopen op de [Marketplace](https://www.roblox.com/catalog) , kunnen ze deze onmiddellijk uitrusten zodat de achtergronden zichtbaar zijn op hun webprofiel en in de 3D-avatarviewer.

Je kunt een achtergrond maken met behulp van elke 2D-bewerkingssoftware, zoals [Procreate](https://procreate.com/)  of [GNU Image Manipulation Program](https://www.gimp.org/)  (GIMP). Nadat je hebt gecontroleerd of de afbeelding voldoet aan de [technische achtergrondspecificaties](/docs/nl-nl/avatar/backgrounds/specifications)  van Roblox die garanderen dat je achtergronden consistent functioneren in de 3D-viewer en webprofielen, kun je de afbeelding uploaden in de [Creator Hub](https://create.roblox.com/dashboard/creations)  om deze te verwerken tot een avatarasset die klaar is om te worden verkocht op de Marketplace.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/backgrounds/Backgrounds-Examples.png)

## [Hoe een achtergrond wordt weergegeven](#hoe-een-achtergrond-wordt-weergegeven)[](#hoe-een-achtergrond-wordt-weergegeven)

Achtergronden worden anders weergegeven, afhankelijk van of een gebruiker de achtergrond bekijkt vanuit de 3D-viewer of een profielpagina. Terwijl de volgende subsections de verschillen tussen deze twee weergaven beschrijven, is het belangrijk om je afbeelding te optimaliseren voor de 3D-viewer, omdat achtergronden die goed werken voor de 3D-ruimte nog steeds correct worden weergegeven als een platte afbeelding op profielpagina's.

### [3D-viewer](#3d-viewer)[](#3d-viewer)

Roblox projecteert de afbeelding op een cyclorama , wat een gebogen vlak achter een avatar is. De curve verbergt de naad tussen de muur en de vloer, op dezelfde manier als een achtergrond in een fotostudio. De avatar wordt in 3D weergegeven, staande voor de cyclorama. Terwijl de camera beweegt, komen verschillende delen van de afbeelding in beeld.

Om dit concept te demonstreren, bekijk de volgende afbeeldingen van hoe een kattenavatar wordt weergegeven terwijl de camera dichter bij de cyclorama komt. Wanneer de camera ver weg is, is de hele achtergrond zichtbaar, maar wanneer de camera inzoomt, is er slechts een klein deel van de achtergrond zichtbaar.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/backgrounds/Cyclorama.png)  ![](https://prod.docsiteassets.roblox.com/assets/avatar/backgrounds/Cyclorama-2.png)

### [Profielpagina's](#profielpaginas)[](#profielpaginas)

De webprofielpagina toont de afbeelding als een platte afbeelding achter de avatar-miniatuur. Er is geen 3D-scène en geen camera, dus de afbeelding lijkt dichter bij het bestand dat je hebt geëxporteerd. De avatar-miniatuur bedekt nog steeds het midden van het frame, dus houd belangrijke inhoud in het veilige gebied.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/backgrounds/Web-profile.png)

## [Sjabloonzones](#sjabloonzones)[](#sjabloonzones)

Het 2D-sjabloon voor achtergronden heeft vier zones en een horizonlijn. Terwijl je achtergronden maakt, is het belangrijk om elke zone en hoe deze details behandelt te bekijken, zodat je afbeelding scherp is en wordt weergegeven volgens je creatieve visie.

| ** Zone** | | ** Waar het zich bevindt** | | ** Instructies** |
| --- | --- |
| Transparant gebied | | Buitenrand van de afbeelding | | Roblox past een alpha-vervaging toe in dit gebied zodat de achtergrond opgaat in de omliggende UI. Laat het vrij van belangrijke details en exporteer de afbeelding zonder een eigen vervaging. |
| Veilig gebied | | Midden van de afbeelding, inclusief de horizon | | Plaats hier belangrijke inhoud. Dit gebied blijft zichtbaar vanuit elke camerahoek, en de curve van de cyclorama behoudt zijn vorm. |
| Vervormingsgebied | | Voorkeursvloer en de buitenste gebieden waar de curve buigt | | Gebruik grondtextuur en verlopen. De cyclorama verkort dit gebied, waardoor gedetailleerde onderwerpen hun vorm verliezen. |
| Avatarlocatie | | Onderste midden | | De avatar staat hier. Houd de vloer onder de avatar vrij. |
| Horizontlijn | | Grens tussen de vloer en de verre achtergrond | | Houd hoge objecten boven deze lijn, in de verre achtergrond. |

![Achtergrondsjabloon met een vervaagde transparante rand, een groene veilige zone, rode vervormingsgebieden, een horizonlijn en de avatar in het onderste midden.](https://prod.docsiteassets.roblox.com/assets/avatar/backgrounds/Template-Zones.png)

Overweeg bovendien de volgende richtlijnen voor best practices:

-

Plaats hoge elementen, zoals bomen en gebouwen, in de verre achtergrond.

-

Geef de avatar een duidelijke vloer om op te staan.

-

Houd belangrijke inhoud in het midden van de afbeelding en houd foreground-elementen laag in de compositie.

-

Zorg ervoor dat hoge objecten de horizonlijn niet overschrijden.

## [Creatieproces](#creatieproces)[](#creatieproces)

Om een achtergrond voor avatars te maken:

1.

Bekijk de vorige [sjabloonzones](#sjabloonzones)  terwijl je over je ontwerp nadenkt, en raadpleeg alle [bestandspecificaties](/docs/nl-nl/avatar/backgrounds/specifications) .

2.

Maak de afbeelding met je favoriete 2D-bewerkingssoftware, zoals Procreate of GIMP.

3.

Exporteer een afgevlakte bestand in de sRGB-kleurruimte dat aan de specificaties voldoet.

4.

[Upload](#achtergronden-uploaden)  de achtergrond in de Creator Hub.

5.

[Publiceer](#achtergronden-publiceren)  de achtergrond zodat anderen deze kunnen kopen op de Marketplace.

## [Achtergronden uploaden](#achtergronden-uploaden)[](#achtergronden-uploaden)

Om achtergronden te uploaden, moet je je account verifiëren via je eigen [overheidsidentificatie](/docs/nl-nl/production/publishing/account-verification#verifi%C3%ABren-via-overheidsidentificatie)  of een gekoppeld [ouderaccount](https://about.roblox.com/parental-controls)  met verificatie van de overheidsidentificatie, en 200 Robux hebben voor de uploadkosten. Er is een uploadlimiet van 1 achtergrond per dag.

Om een achtergrond voor avatars te uploaden:

1.

Navigeer in de linkernavigatie van de Creator Hub naar Avatar-items. De pagina Avatar-items  wordt weergegeven.

2.

Navigeer in de horizontale navigatie naar Achtergronden , en klik vervolgens op de knop Achtergrond maken . De pagina wordt bijgewerkt met nieuwe UI-opties.

3.

Klik op de knop Uploaden , selecteer vervolgens je afbeelding van 2560 x 1440.

4.

Vul de velden Naam  en Beschrijving  in.

5.

Klik op de knop Maken , en accepteer de kosten van 200 Robux.

 ![Pagina voor het maken van een achtergrond met een afbeeldingsvoorbeeld, naam- en beschrijvingsvelden, een uploadkosten van 200 Robux, en de knoppen Maken en Annuleren.](https://prod.docsiteassets.roblox.com/assets/avatar/backgrounds/Create-UI.png)

## [Achtergronden publiceren](#achtergronden-publiceren)[](#achtergronden-publiceren)

Om achtergronden te publiceren, moet je een [Roblox Plus](https://www.roblox.com/plus)  account hebben, je account verifiëren via je eigen [overheidsidentificatie](/docs/nl-nl/production/publishing/account-verification#verifi%C3%ABren-via-overheidsidentificatie)  of een gekoppeld [ouderaccount](https://about.roblox.com/parental-controls)  met verificatie van de overheidsidentificatie, en Robux hebben voor de publicatiekosten:

-

100 per eenheid voor gratis beperkte achtergronden

-

2000 voor betaalde niet-beperkte achtergronden

-

15000 voor betaalde beperkte achtergronden

Voor commissies en de standaard publicatiestroom, zie [Marketplace-kosten en commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions)  en [Publiceer op Marketplace - Publiceer een asset](/docs/nl-nl/marketplace/publish-to-marketplace#publiceer-een-activum) .

Achtergronden ondersteunen standaard publicatieopties, inclusief [Beperkte items](/docs/nl-nl/marketplace/publish-to-marketplace#itemattributen) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
