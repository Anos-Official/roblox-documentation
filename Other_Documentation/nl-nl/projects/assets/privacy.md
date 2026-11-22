<!-- Source: https://create.roblox.com/docs/nl-nl/projects/assets/privacy -->

Asset privacy | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)

# Asset privacy

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het asset privacy-systeem  stelt je in staat om te controleren welke makers en games jouw assets op Roblox kunnen gebruiken. Assets kunnen een van de twee toegangstype privacy hebben:

-

Beperkt  — Makers of games kunnen de asset alleen gebruiken nadat de eigenaar van de asset toestemming heeft gegeven.

-

Open Gebruik  — Elke maker of game kan de asset gebruiken.

Als een maker of game geen toestemming heeft om een asset te gebruiken, kan deze niet worden geladen in Studio, en wordt er een klikbare foutmelding weergegeven in het [Output](/docs/nl-nl/studio/output)  venster. Als een maker toestemming heeft om een asset te gebruiken, maar de game waaraan ze werken niet, toont het klikken op de foutmelding een pop-upvenster waarmee de maker toestemming kan geven aan de game voor alle beperkte assets.

Wanneer een asset Open Gebruik is, hoeft Roblox zijn machtigingen niet te controleren wanneer het in een game wordt geladen, omdat elke maker en game het vrij kan gebruiken. Wanneer een asset echter Beperkt is, controleert Roblox altijd  de machtigingen wanneer het in een game wordt geladen of wanneer een maker een actie op de asset onderneemt, zoals het invoegen in Studio, het delen met een andere maker, of het vermelden in de [Creator Store](/docs/nl-nl/production/creator-store) .

Het asset privacy-systeem controleert welke makers en games de asset kunnen gebruiken, maar anderen kunnen nog steeds de metadata ervan zien, zoals de naam en beschrijving.

## [Wat Asset Privacy controleert](#wat-asset-privacy-controleert)[](#wat-asset-privacy-controleert)

Asset Privacy controleert alleen de standaard privacystatus die is toegewezen aan Afbeeldingen , Decals  en Meshes  wanneer ze worden gemaakt. Geen andere assettypes worden beïnvloed.

Asset Privacy beïnvloedt niet:

-

Audio, Video, Modellen, MeshParts, Animaties en Pakketten  — deze types hebben hun eigen creatie-instellingen en worden niet gewijzigd door de Asset Privacy-instelling. Als audio of andere assettypes niet worden geladen of verspreid zoals verwacht, is Asset Privacy niet de oorzaak.

-

Het verspreiden van assets op de Creator Store of Marketplace  — het inschakelen of uitschakelen van Asset Privacy verandert je distributiegeschiktheid of workflow niet.

-

Het gebruiken van je eigen assets in je eigen gepubliceerde games  — je assets zijn altijd toegankelijk voor jou in je eigen games, ongeacht hun privacy-instelling.

-

Assets die zijn gemaakt voordat Asset Privacy werd ingeschakeld  — de instelling is alleen van toepassing op nieuw gemaakte assets.

-

Het delen van beperkte assets  — Beperkt betekent niet permanent ontoegankelijk. Je kunt op elk moment toegang verlenen aan specifieke vrienden, groepen en games via het [Creator Dashboard](#machtigingen-verlenen) , of gebruik de [Revamped Asset Manager](https://devforum.roblox.com/t/beta-updates-to-revamped-asset-manager/4548832/1)  om in bulk toegang te verlenen voor veel assets tegelijk.

Belangrijke beperkingen:

-

Open Gebruik is onomkeerbaar.  Zodra een asset is ingesteld op Open Gebruik, kan deze niet meer worden teruggezet naar Beperkt.

-

Game-toestemmingen zijn permanent.  Zodra je een game toestemming geeft om een beperkte asset te gebruiken, kan die toestemming niet worden ingetrokken.

-

Het intrekken van de toegang van een samenwerker heeft geen invloed op games.  Als een samenwerker al een beperkte asset in een game heeft gebruikt, behoudt die game toegang, zelfs nadat de samenwerker is verwijderd.

-

De instelling is niet retroactief.  Alleen assets die zijn gemaakt na het inschakelen van Asset Privacy zijn standaard Beperkt.

## [Beperk machtigingen](#beperk-machtigingen)[](#beperk-machtigingen)

Je kunt je of de beperkte assets van je groep afzonderlijk of als een afhankelijkheid van een beperkte asset op de Creator Store vermelden. Dit stelt makers in staat om jouw assets te gebruiken zoals je ze onder modellen, mesh onderdelen of pakketten vermeldt, en voorkomt dat ze toegang krijgen tot en je beperkte asset-afhankelijkheden opnieuw verpakken.

Standaard worden Afbeeldingen, Decals en Meshes gemaakt als Open Gebruik . Schakel Asset Privacy  in om deze assettypes in plaats daarvan Beperkt  te maken bij creatie. Alle andere assettypes worden niet beïnvloed door deze instelling.

### [Schakel Asset Privacy in](#schakel-asset-privacy-in)[](#schakel-asset-privacy-in)

Individuele makers en groepen kunnen Asset Privacy inschakelen via het Creator Dashboard. Wanneer ingeschakeld, worden nieuw gemaakte Afbeeldingen, Decals en Meshes standaard ingesteld op Beperkt . Alle andere assettypes worden niet beïnvloed door deze instelling.

Het inschakelen van Asset Privacy verandert je vermogen om assets op de Creator Store of Marketplace te verspreiden, je assets in gepubliceerde games te gebruiken, of je assets met samenwerkers te delen niet.

Als maker Als groep

Om je mesh-, afbeelding- en decal-assets bij creatie te beperken:

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Klik in de rechterbovenhoek van de pagina op je gebruikersnaam en selecteer Instellingen .

3.

Selecteer in de navigatie aan de linkerkant Geavanceerd .

4.

Schakel in de sectie Asset Privacy  de schakelaar Opt-in om assets bij creatie te beperken  in. Elke nieuw gemaakte Afbeelding, Decal en Mesh is nu standaard Beperkt.

Na het inschakelen van Asset Privacy, controleer de assetmachtiging van elke nieuw geüploade asset op de assetconfiguratiepagina:

 ![De startpagina voor assetmachtigingen met het tabblad Samenwerkers geselecteerd.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Asset-Toggle.png)

Het selecteren van Open Gebruik  waarschuwt dat zodra een asset is ingesteld op Open Gebruik , deze niet kan worden teruggezet naar Beperkt .

 ![De startpagina voor assetmachtigingen met het tabblad Samenwerkers geselecteerd.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Asset-Make-OpenUse.png)

Na het instellen op Open Gebruik , toont de asset zijn huidige assettoegangsmachtiging.

 ![De startpagina voor assetmachtigingen met het tabblad Samenwerkers geselecteerd.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Asset-OpenUse.png)

### [Decals](#decals)[](#decals)

Alle [Decals](/docs/nl-nl/reference/engine/classes/Decal)  zijn gekoppeld aan een Afbeelding , wat betekent dat een Decal  alleen op Open Gebruik kan worden ingesteld als zijn Afbeelding -afhankelijkheid Open Gebruik is. Anders wordt de volgende waarschuwing weergegeven:

 ![De startpagina voor assetmachtigingen met het tabblad Samenwerkers geselecteerd.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Asset-Decals-Warning.png)

### [Avatar-assets](#avatar-assets)[](#avatar-assets)

Avatar-assets, zoals accessoires, kleding en lichamen, vereisen dat alle afhankelijke texturen en meshes Open Gebruik  zijn bij het uploaden van de Avatar-asset naar de Marketplace.

Als je Asset Privacy hebt ingeschakeld en een nieuw geïmporteerd model in een avatar-asset gebruikt, krijg je de prompt om je beperkte textuur- en mesh-afhankelijkheden in te stellen op Open Gebruik  tijdens de Marketplace [upload](/docs/nl-nl/marketplace/publish-to-marketplace#upload-een-activum) :

![De startpagina voor assetmachtigingen met het tabblad Samenwerkers geselecteerd.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Asset-Avatar-Restricted.png)

Als je avatar-item of bundel beperkte primitieve assets bevat, moet je ze omzetten naar Open Gebruik.

![De startpagina voor assetmachtigingen met het tabblad Samenwerkers geselecteerd.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Asset-Avatar-Success.png)

Als je hele avatar-item de juiste machtigingen heeft, kun je doorgaan met het uploaden en publiceren van je avatar-item naar de Marketplace.

## [Machtigingen verlenen](#machtigingen-verlenen)[](#machtigingen-verlenen)

Beperkte assets moeten expliciet toestemming krijgen voordat ze zichtbaar of hoorbaar zijn tijdens runtime. Verleen machtigingen individueel via het Creator Dashboard, of gebruik de [Revamped Asset Manager](https://devforum.roblox.com/t/beta-updates-to-revamped-asset-manager/4548832/1)  om in bulk machtigingen voor veel assets tegelijk te verlenen.

### [Aan samenwerkers](#aan-samenwerkers)[](#aan-samenwerkers)

Om een samenwerker toestemming te geven om een van je beperkte assets te gebruiken, moet het volgende waar zijn:

-

Om aan een individuele maker te verlenen: de maker moet je [vriend](https://en.help.roblox.com/hc/en-us/articles/203313580-How-to-Make-Friends)  zijn op het platform.

-

Om aan een groep te verlenen: je moet de Ervaringen bewerken  [machtiging](/docs/nl-nl/projects/groups#rollen-en-machtigingen)  in die groep hebben.

Wanneer je een individuele maker toestemming geeft:

-

Ze kunnen de asset gebruiken in een van hun individuele of groepsbezit games.

-

Ze kunnen toestemming verlenen voor games die ze bezitten of waartoe ze bewerkingsrechten hebben.

Wanneer je een groep toestemming geeft:

-

Alle groepsleden met bewerkingsrechten kunnen de asset gebruiken in games die door die groep worden beheerd.

Zodra een samenwerker toestemming heeft om een van je beperkte assets te gebruiken, kunnen ze de asset invoegen vanuit het Inventaris  en/of Creatie  tabblad van de [Toolbox](/docs/nl-nl/projects/assets/toolbox) , of door de beperkte asset-ID te gebruiken in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster.

![Een close-up van de Toolbox met het Inventaris-tabblad gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Inventory-Tab.png)![Een close-up van de Toolbox met het Creaties-tabblad gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Creations-Tab.png) Een beperkte asset invoegen via de Toolbox

![Een close-up van het Eigenschappen-venster met de Asset-eigenschap gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Enter-Private-Asset-ID.png) Een beperkte asset invoegen in het Eigenschappen-venster

Als een samenwerker de beperkte asset in een script wil gebruiken, of een sjabloonplaats wil opslaan of publiceren die de beperkte asset bevat, moet de game zelf ook toestemming hebben om de asset te gebruiken. Als deze stap wordt overgeslagen, is de asset niet zichtbaar of hoorbaar tijdens runtime, en wordt er een klikbare foutmelding weergegeven in het Output  venster.

Om een samenwerker toestemming te geven om een beperkte asset te gebruiken:

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Selecteer in de bovenste tabbalk Ontwikkelingsitems , en klik vervolgens op een van de volgende tabbladen:

-

Modellen & Pakketten

-

Audio

-

Decals

-

Afbeeldingen

-

Video's

-

Meshes

-

MeshParts

-

Animaties

3.

Selecteer de asset waarvoor je je samenwerker toestemming wilt geven om deze in hun games te gebruiken. De Configure  pagina van de asset wordt weergegeven.

4.

Selecteer in de navigatie aan de linkerkant van de asset Machtigingen . De Machtigingen  pagina van de asset wordt weergegeven.

5.

Klik op het tabblad Samenwerkers  op de knop Samenwerkers toevoegen .

 ![De startpagina voor assetmachtigingen met het tabblad Samenwerkers geselecteerd.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Permissions-Collaborators.png)

6.

Gebruik de zoekbalk om een vriend of groep in te voeren en te selecteren aan wie je toestemming wilt geven om je beperkte asset te gebruiken. De maker of groep wordt onder de zoekbalk weergegeven met hun toegangstype.

 ![Het pop-upmenu Samenwerkers toevoegen.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Add-Collaborators.png)

7.

OPTIONAL

 Als het geselecteerde assettype een model of pakket is, kun je een van de volgende toegangstypen kiezen:

-

Gebruik  - De samenwerker krijgt toestemming om de asset in hun games te gebruiken.

-

Bewerken  - De samenwerker krijgt toestemming om de metadata van de asset te bewerken, zoals de naam en beschrijving.

8.

Klik op de knop Klaar  om je assettoegangsmachtigingen te finaliseren.

Om machtigingen voor meerdere assets tegelijk te verlenen, of om assets in bulk te delen met specifieke groepen en gebruikers, gebruik de nieuwste Asset Manager beta. Zie [Revamped Asset Manager](https://devforum.roblox.com/t/beta-updates-to-revamped-asset-manager/4548832/1)  voor details.

### [Aan games](#aan-games)[](#aan-games)

Zodra een game toestemming heeft om een beperkte asset te gebruiken, kun je de toegang tot de asset niet intrekken.

Om een game toestemming te geven om een van je beperkte assets te gebruiken, moet de game bewerkbaar zijn voor jou of een groep waartoe je behoort waarin je de Ervaringen bewerken  [machtiging](/docs/nl-nl/projects/groups#rollen-en-machtigingen)  hebt.

Zodra een game toestemming heeft om een beperkte asset te gebruiken, kan iedereen met Bewerken  toegang tot die game:

-

De asset kopiëren en plakken in een ander plaatsbestand binnen die game.

-

De asset-ID gebruiken in het Eigenschappen  venster of in scripts binnen elk plaatsbestand binnen de game.

Wanneer je toestemming geeft aan een game door een beperkte asset in het spel van een samenwerker in te voegen, wordt de asset ook automatisch verleend aan de eigenaar van de game.

De volgende tabbladen begeleiden je door het proces van het verlenen van toegang aan een of meer games tot een enkele beperkte asset, of het verlenen van toegang aan een game tot een of meer beperkte assets.

Op assetniveau Op game-niveau

Om een game toestemming te geven om een beperkte asset te gebruiken:

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Selecteer in de bovenste tabbalk Ontwikkelingsitems , en klik vervolgens op een van de volgende tabbladen:

-

Modellen & Pakketten

-

Audio

-

Decals

-

Afbeeldingen

-

Video's

-

Meshes

-

MeshParts

-

Animaties

3.

Selecteer de asset waarvoor je de game toestemming wilt geven om deze te gebruiken. De Configure  pagina van de asset wordt weergegeven.

4.

Selecteer in de navigatie aan de linkerkant van de asset Machtigingen . De Machtigingen  pagina van de asset wordt weergegeven.

5.

Klik op het tabblad Ervaringen  op de knop Ervaringen toevoegen .

 ![De startpagina voor assetmachtigingen met het tabblad Ervaringen geselecteerd.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Permissions-Experiences.png)

6.

Typ de universeID van de game in het invoerveld Voer Universe ID's in , en klik vervolgens op de knop Toevoegen . De game wordt onder de invoer weergegeven met zijn toegang zichtbaar.

Om meerdere games tegelijkertijd toestemming te geven, voer je meerdere universeID's in, gescheiden door komma's.

 ![Het pop-upmenu Ervaringen toevoegen.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Add-Experiences.png)

7.

Klik op de knop Klaar  om je assettoegangsmachtigingen te finaliseren.

## [Bekijk machtigingen](#bekijk-machtigingen)[](#bekijk-machtigingen)

Om elke beperkte asset te bekijken waarvoor jouw of de games van je groep toestemming hebben om deze te gebruiken, bekijk de Machtigingen  pagina van de game op het Creator Dashboard.

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Selecteer een van je of de games van je groep. De overzichtspagina van de game wordt weergegeven.

3.

Navigeer in de navigatie aan de linkerkant van de game naar Configuraties  > Machtigingen .

4.

OPTIONAL

 Klik op de downloadpijlknop om de gegevens voor offline verwerking te exporteren.

## [Intrekken van machtigingen](#intrekken-van-machtigingen)[](#intrekken-van-machtigingen)

Een maker als vriend verwijderen intrekt niet automatisch hun toestemming om een beperkte asset te gebruiken.

Het intrekken van de toestemming van een samenwerker voorkomt dat ze nieuwe games toegang tot de asset kunnen verlenen. Het heeft geen invloed op games die de asset al gebruiken — die games behouden permanent toegang.

Om de toestemming voor een maker in te trekken om een beperkte asset in een andere game te gebruiken:

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Selecteer in de bovenste tabbalk Ontwikkelingsitems , en klik vervolgens op een van de volgende tabbladen:

-

Modellen & Pakketten

-

Audio

-

Decals

-

Afbeeldingen

-

Video's

-

Meshes

-

MeshParts

-

Animaties

3.

Selecteer de asset waarvoor je de toestemming wilt intrekken voor een of meer makers om deze in hun eigen games te gebruiken. De Configure  pagina van de asset wordt weergegeven.

4.

Selecteer in de navigatie aan de linkerkant van de asset Machtigingen . De Machtigingen  pagina van de asset wordt weergegeven.

5.

Zoek op het tabblad Samenwerkers  de maker van wie je de toestemming wilt intrekken, en klik vervolgens op de toegangsdropdown naast hun gebruikersnaam. Extra opties worden weergegeven.

6.

Klik op de knop Verwijderen . Een pop-up wordt weergegeven om te bevestigen dat je de toestemming van de samenwerker wilt intrekken.

7.

Klik in de pop-up op de knop Verwijderen .

## [Open machtigingen](#open-machtigingen)[](#open-machtigingen)

Het openen van de machtigingen van een asset is onomkeerbaar. Zodra je een asset instelt op Open Gebruik, kan deze niet  worden teruggezet naar Beperkt.

Om meerdere assets in bulk op Open Gebruik  in te stellen, gebruik de Revamped Asset Manager. Zie [Revamped Asset Manager](https://devforum.roblox.com/t/beta-updates-to-revamped-asset-manager/4548832/1)  voor details.

Met Asset Privacy  ingeschakeld, kun je nog steeds de machtigingen van elke Afbeelding, Decal of Mesh openen, zodat elke maker of game deze vrij kan gebruiken.

Om de machtigingen voor jouw of de Afbeelding, Decal of Mesh van je groep te openen:

1.

Schakel Asset Privacy in zoals beschreven in [Beperk machtigingen](#beperk-machtigingen) .

2.

Ga terug naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) , navigeer naar de bovenste tabbalk, selecteer Ontwikkelingsitems , en klik vervolgens op Decals , Afbeeldingen  of Meshes . Al jouw Decal-, Afbeelding- of Mesh-assets worden weergegeven.

Om een Decal op Open Gebruik in te stellen, moet je eerst de afhankelijkheid van de Afbeelding op Open Gebruik instellen. Het Asset Privacy-systeem blokkeert de wijziging als de Afbeelding nog Beperkt is.

3.

Selecteer de asset die je wilt dat elke maker en game vrij kan gebruiken. De Configure  pagina van de asset wordt weergegeven.

4.

In de sectie Assettoegang  schakel je Open Gebruik  in. Een pop-up wordt weergegeven waarin je wordt gevraagd deze permanente wijziging te bevestigen.

5.

Klik in de pop-up op de knop Maak Open Gebruik . Iedereen op Roblox kan nu jouw asset gebruiken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
