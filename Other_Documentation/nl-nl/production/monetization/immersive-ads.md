<!-- Source: https://create.roblox.com/docs/nl-nl/production/monetization/immersive-ads -->

Indringende advertenties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Adverteren](/docs/nl-nl/production/promotion/advertise)

# Indringende advertenties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Met het indringende advertenties  systeem kun je advertentie-eenheden in je game invoegen waarmee Roblox programmatisch advertentie-inhoud van adverteerders aan je actieve gebruikers kan leveren.

De volgende advertentieformaten kunnen in je game worden weergegeven:

-

Billboards , die omvatten:

-

Video-advertenties : Een video van maximaal 30 seconden die gebruikers in de game kunnen bekijken, die ofwel klik-om-te-spelen of automatisch afspeelt.

-

Afbeeldingsadvertenties : Een statische, niet-klikbare afbeelding binnen de 3D-ruimte.

-

Portal-advertenties : Een statische, niet-klikbare afbeelding met een deur die gebruikers naar de game van een adverteerder teleporteert.

Bij portal-advertenties moet de game van de adverteerder een knop bevatten waarmee gebruikers naar je game kunnen terugkeren.

Video-advertentieformaat (automatisch afspelend)

Video-advertentieformaat (klik-om-te-spelen)

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-ImageAd.jpg) Afbeeldingsadvertentieformaat

Portal-advertentieformaat

Advertentie-inhoud is specifiek voor de gebruiker, wat betekent dat twee gebruikers tegelijkertijd verschillende weergaveadvertenties kunnen zien of naar verschillende adverteerdersgames kunnen teleporteren vanuit dezelfde advertentie-eenheid. Als een gebruiker niet in aanmerking komt om advertenties te zien, tonen advertentie-eenheden ofwel een aanpasbaar fallback-afbeelding of het Roblox-logo.

Om dit concept te illustreren, zie de volgende drie afbeeldingen van dezelfde advertentie-eenheid die verschillende inhoud toont, afhankelijk van de gebruiker. Gebruiker A ziet een advertentie die de game [The Mystery of Duvall Drive](/docs/nl-nl/resources/the-mystery-of-duvall-drive)  promoot, terwijl gebruiker B een advertentie ziet die de game [Beyond the Dark](/docs/nl-nl/resources/beyond-the-dark)  promoot. Gebruiker C ziet helemaal geen advertentie van deze advertentie-eenheid omdat ze niet in aanmerking komen om advertenties te zien.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-UserA.jpg) Gebruiker A

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-UserB.jpg) Gebruiker B

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Overview-UserC.jpg) Gebruiker C

## [Verdiensten van uitgevers uit indringende advertenties](#verdiensten-van-uitgevers-uit-indringende-advertenties)[](#verdiensten-van-uitgevers-uit-indringende-advertenties)

Als je actieve gebruikers in aanmerking komen om advertenties te zien en voldoen aan de specifieke criteria van de adverteerder, zoals hun land of apparaat, kom je mogelijk in aanmerking om Robux te verdienen op basis van hoe ze interactie hebben met de advertentie-inhoud.

Hoe uitgevers verdienen:

-

Voor video-advertenties die klik-om-te-spelen zijn , moeten gebruikers op de advertentie klikken om de video te starten. Adverteerders bieden op een "15 seconden weergave", dus uitgevers verdienen telkens wanneer een gebruiker een video minstens 15 seconden bekijkt. Je kunt een beloningsmechanisme implementeren met [beloningsvideo-advertenties](/docs/nl-nl/production/promotion/rewarded-video-ads)  om een gebruiker te stimuleren de video minstens 15 seconden te bekijken om verdiensten te genereren.

-

Voor video-advertenties die automatisch afspelen , begint de video te spelen wanneer een gebruiker naar de advertentie kijkt en pauzeert wanneer de gebruiker wegkijkt. Adverteerders bieden op een video-impressie, dus uitgevers verdienen voor elke video-impressie. Een video-impressie is wanneer een gebruiker minstens 0,5 seconden naar de advertentie kijkt, de advertentie 1,5% van het viewport beslaat, de advertentie vanuit een hoek van maximaal 55 graden wordt bekeken, en minstens 50% van de pixels van de video-advertentie zichtbaar zijn.

-

Afbeeldingsadvertenties  zijn statische, niet-klikbare afbeeldingen binnen de 3D-ruimte. Adverteerders bieden op een afbeelding-impressie, dus uitgevers verdienen voor elke afbeelding-impressie. Een afbeelding-impressie is wanneer een gebruiker minstens 1 seconde naar de advertentie kijkt, de advertentie 1,5% van het viewport beslaat, de advertentie vanuit een hoek van maximaal 55 graden wordt bekeken, en minstens 50% van de pixels van de afbeelding-advertentie zichtbaar zijn.

-

Portal-advertenties  zijn statische, niet-klikbare afbeeldingen met een deur die gebruikers naar de game van een adverteerder teleporteert. Adverteerders bieden op een teleport, dus uitgevers verdienen voor elke succesvolle teleport. Een teleport is wanneer een gebruiker de portal binnenkomt en aankomt in de game van de adverteerder.

Om meer te leren over hoe adverteerders worden gefactureerd, zie [Facturering](/docs/nl-nl/production/promotion/ads-manager#facturering) .

Roblox betaalt verdiensten uit op de 25e van de volgende maand vanaf het moment dat je advertentie-eenheden in je game hebt ingevoegd. Bijvoorbeeld, als je advertentie-eenheden invoegt tijdens de maand maart, is je uitbetalingsdatum voor de weergave-impressies en succesvolle teleports van die advertentie-eenheden 25 april. Je kunt je totale verdiensten uit advertenties volgen via de pagina Mijn Transacties  of de pagina Groepstransacties . Je kunt ook hun algehele prestaties analyseren via metrische grafieken op het Creator Dashboard.

Roblox heeft systemen voor advertentiefraude om een positieve ervaring voor adverteerders, uitgevers en gebruikers te creëren. Volgens de [Advertentienormen](https://en.help.roblox.com/hc/en-us/articles/13722260778260-Advertising-Standards)  van Roblox, als je betrokken bent bij kwaadaardige praktijken om impressies of teleports te verhogen, kan Roblox Robux van je verwachte uitbetaling aftrekken of de Robux die je op frauduleuze wijze hebt verdiend terugvorderen. Roblox kan ook je game of je account opschorten.

## [Geschiktheid van uitgevers](#geschiktheid-van-uitgevers)[](#geschiktheid-van-uitgevers)

Hoewel iedereen advertentie-eenheden in hun games kan invoegen, serveert Roblox alleen advertenties in advertentie-eenheden als de game in aanmerking komt om advertenties te tonen. Geschiktheid garandeert niet dat Roblox advertenties in je game zal tonen, en niets verplicht Roblox om advertenties in je game te tonen.

Om ervoor te zorgen dat je game in aanmerking komt om advertenties te tonen, moet je account en game voldoen aan de volgende criteria:

-

Je game moet openbaar  zijn.

-

Je moet 13 jaar of ouder  zijn.

-

Voor groepsbezit games geldt deze vereiste voor de eigenaar van de groep.

-

Je account moet [ID-geverifieerd](/docs/nl-nl/production/publishing/account-verification)  zijn en 2-factor authenticatie (2FA)  ingeschakeld hebben.

-

Voor groepsbezit games geldt deze vereiste voor de eigenaar van de groep.

-

Deze vereiste is persistent. Als je identiteitsverificatie of 2FA uitschakelt, verliest je game zijn geschiktheid.

-

Je moet de Maturity and Compliance Questionnaire  of de Content Rating Questionnaire  voor je game invullen.

-

De vragenlijst moet door Roblox worden beoordeeld en goedgekeurd voordat de game in aanmerking komt om advertenties te tonen. Als de beoordelingsstatus In afwachting  is, kun je een herbeoordeling aanvragen vanaf de advertentiegeschiktheidspagina van de game onder Monetization  ⟩ Ads  ⟩ Eligibility . Je ontvangt binnen 24 uur een reactie.

-

Je game moet 2.000 unieke bezoekers per maand  behouden.

-

Dit wordt maandelijks berekend en bijgewerkt op basis van bezoekersgegevens. Bots worden niet meegerekend in het aantal bezoekers.

-

Je moet voldoen aan de [gebruikersvoorwaarden van Roblox](https://en.help.roblox.com/hc/en-us/articles/115004647846-Roblox-Terms-of-Use) , [gemeenschapsnormen](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) , en [eisen voor uitgeverintegriteit](https://en.help.roblox.com/hc/en-us/articles/13722260778260-Advertising-Standards#publisher-integrity) .

Het opnieuw indienen van je Content Rating Questionnaire  zal tijdelijk je geschiktheid voor advertenties verwijderen terwijl de vragenlijst in beoordeling is. Om herhaalde onderbrekingen te voorkomen, dien je de vragenlijst alleen opnieuw in wanneer je een game-update publiceert die je eerdere antwoorden wijzigt.

Als je niet voldoet aan deze vereisten, kun je tijdelijk of permanent je uitgeversgeschiktheid verliezen. In sommige gevallen kun je een deel of al je advertentie-uitbetalingen verliezen en kan je inhoud of account worden opgeschort.

## [Geschiktheid van gebruikers](#geschiktheid-van-gebruikers)[](#geschiktheid-van-gebruikers)

Zelfs als je game in aanmerking komt om advertenties te tonen, zijn niet alle gebruikers in aanmerking om advertenties te zien, zoals degenen buiten de doelgroepselectie van een campagne. Als een gebruiker niet in aanmerking komt om advertenties te zien, tonen advertentie-eenheden een fallback-afbeelding van het Roblox-logo aan die niet-geschikte gebruikers. Om deze advertentie-eenheden te verwijderen, kun je [advertentie-eenheden voor niet-geschikte gebruikers verwijderen](#advertentie-eenheden-voor-niet-geschikte-gebruikers-verwijderen) .

## [Advertentie-eenheden invoegen](#advertentie-eenheden-invoegen)[](#advertentie-eenheden-invoegen)

Wanneer je een advertentie-eenheid in een geschikte game invoegt, zorg er dan voor dat je elke afbeeldingsadvertentieoppervlak controleert om te bevestigen of deze geldig is en advertenties kan tonen. Je kunt bijvoorbeeld advertentie-eenheden schalen naar verschillende maten om aan te sluiten bij de esthetiek van je game, maar je kunt ze niet te klein of te groot maken, anders worden ze ongeldig en kunnen ze geen advertenties tonen.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Inserting-ImageAd.jpg) Deze advertentie-eenheid is geldig en kan advertenties tonen

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Inserting-PortalAd.jpg) Deze advertentie-eenheid is ongeldig omdat deze te klein is; het kan geen advertenties tonen totdat je het naar een geldige grootte schaalt

### [Billboards](#billboards)[](#billboards)

Billboards omvatten video- en afbeeldingsadvertenties.

##### Video-advertenties

Geschikte gebruikers kunnen twee soorten video-advertenties binnen Roblox-games zien, afhankelijk van hoe de adverteerder biedt:

-

Een klik-om-te-spelen  video-advertentie wordt weergegeven wanneer een adverteerder biedt op gebruikers die minstens 15 seconden naar de advertentie kijken. Gebruikers starten een video-advertentie door op de advertentie-eenheid te klikken, wat de video in volledig scherm met geluid activeert. Uitgevers worden betaald elke keer dat een video-advertentie minstens 15 seconden wordt bekeken.

-

Een automatisch afspelende  video-advertentie wordt weergegeven wanneer een adverteerder biedt op gebruikers die hun advertentie zien, en begint te spelen met het geluid uit wanneer een gebruiker ernaar kijkt. Als ze wegkijken, pauzeert de video. De video-advertentie bevat bedieningselementen om het geluid in te schakelen en uit te breiden naar volledig scherm. Uitgevers worden betaald op basis van het aantal impressies dat de advertentie ontvangt.

Om een video-advertentie in te voegen:

1.

Van de Home  of Model  tab toolbar, voeg een Block  onderdeel in je game in.

2.

Schaal het onderdeel tot minstens 8 studs breed en 4,5 studs hoog, maar niet meer dan 32 studs breed en 18 studs hoog.

3.

In het Explorer  venster, voeg een AdGui  object toe aan het onderdeel. Om dit te doen, zweef over het onderdeel en klik op de Toevoegen  knop, en voeg vervolgens een AdGui in.

4.

In het Properties  venster, met de nieuwe AdGui geselecteerd, ga naar de Face  eigenschap en kies een gezicht. Je kunt ook het standaard gezicht behouden.

5.

Zorg ervoor dat je het EnableVideoAds  selectievakje inschakelt om video-advertenties te tonen. Als je dit selectievakje uitgeschakeld laat, toont het onderdeel alleen afbeeldingsadvertenties.

Je kunt ook een beloningsmechanisme in je game implementeren om gebruikers te stimuleren om klik-om-te-spelen video-advertenties te bekijken met [beloningsvideo-advertenties](/docs/nl-nl/production/promotion/rewarded-video-ads) .

##### Afbeeldingsadvertenties

Een afbeeldingsadvertentie is een niet-klikbare statische afbeelding die advertenties levert via een [AdGui](/docs/nl-nl/reference/engine/classes/AdGui)  instantie die je op blok [Part](/docs/nl-nl/reference/engine/classes/Part)  instanties overal binnen de 3D-ruimte van een game kunt plaatsen, zolang niets het zicht op de advertentie voor gebruikers obstructeert. De beeldverhouding van de afbeelding schaalt met het gezicht van het blok dat je kiest om de advertentie-inhoud weer te geven.

Om ervoor te zorgen dat de advertentie-eenheid geldig is en advertenties kan tonen zodra je de game publiceert, moet je ervoor zorgen dat deze voldoet aan de volgende criteria:

-

Het blok bevindt zich binnen de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) .

-

Het blok is niet kleiner dan 8 bij 4,5 studs, en niet groter dan 32 bij 18 studs.

-

Het blok bevat geen andere [AdGui](/docs/nl-nl/reference/engine/classes/AdGui)  of [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  object op hetzelfde gezicht van de advertentie.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/ImageAds-Sample.jpg)

Om een afbeeldingsadvertentie in te voegen:

1.

Van de Home  of Model  tab toolbar, voeg een Block  onderdeel in je game in.

2.

Schaal het onderdeel tot minstens 8 studs breed en 4,5 studs hoog, maar niet meer dan 32 studs breed en 18 studs hoog.

3.

In het Explorer  venster, voeg een AdGui  object toe aan het onderdeel. Om dit te doen, zweef over het onderdeel en klik op de Toevoegen  knop, en voeg vervolgens een AdGui in.

4.

In het Properties  venster, ga naar de Face  eigenschap en kies een gezicht. Je kunt ook het standaard gezicht behouden.

Je kunt ook een afbeeldingsadvertentiepakket uit de Creator Store invoegen en deze aanpassen aan je game, zolang de advertentie-eenheid blijft voldoen aan de validatiecriteria. Voor meer informatie over hoe je advertentie-eenheden uit de Creator Store kunt invoegen, zie [Portal-advertenties](#portal-advertenties) .

Nadat je de game hebt gepubliceerd, kunnen gebruikers de advertentie-eenheid in een van de volgende staten zien:

| Staat | | Beschrijving | | Voorbeeld |
| --- | --- |
| Actief | | De advertentie-eenheid kan advertenties tonen en toont momenteel een advertentie aan een gebruiker. | | ![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/ImageAds-Active.jpg) |
| Inactief | | De advertentie-eenheid kan advertenties tonen, maar toont momenteel geen advertentie aan een gebruiker om een van de volgende redenen:
-

De gebruiker komt niet in aanmerking om advertenties te zien.

-

De gebruiker heeft te veel advertenties in een korte periode gezien.

-

Er is een lage vraag naar advertenties van adverteerders tijdens die periode.

-

Er zijn geen advertenties die zijn gericht op de criteria van de gebruiker, zoals hun geslacht, apparaat of land.

Roblox toont in plaats daarvan een standaard fallback-afbeelding. | | ![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/ImageAds-Inactive.jpg) |
| Ongeldig | | De advertentie-eenheid kan geen advertenties tonen omdat deze niet voldoet aan de validatiecriteria. | | ![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/ImageAds-Invalid.jpg) |

### [Portal-advertenties](#portal-advertenties)[](#portal-advertenties)

Een portal-advertentie bestaat uit twee kerncomponenten:

-

Een statische, niet-klikbare afbeelding.

-

Een deur die gebruikers naar de game van een adverteerder teleporteert.

De Creator Store bevat portal-advertenties die deze kerncomponenten vertegenwoordigen via een BasePortal  pakket. De enige wijzigingen die je aan dit pakket kunt aanbrengen, zijn het aanpassen van de schaal, positie en rotatie. Elke andere wijziging die je aanbrengt, maakt het pakket ongeldig en kan geen advertenties tonen.

Portal-advertenties bevatten ook een Decorative  map met zowel statische als dynamische visuele elementen. Je kunt deze elementen aanpassen zolang de kerncomponenten intact blijven.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Portal-Ads-BasePortal.png)

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/Portal-Ads-Decorative.png)

Bijvoorbeeld, de volgende twee portal-advertentie pakketten hebben exact dezelfde kerncomponenten, maar ze bevatten verschillende visuele elementen die je kunt aanpassen om te veranderen hoe deze advertentie-eenheden eruit zien en aanvoelen binnen je games.

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/PortalAds-Sample1.png)

![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/PortalAds-Sample2.jpg)

Om een portal-advertentie in te voegen:

1.

Open de Creator Store.

1.

Van het Window  menu of de Home  tab toolbar van Studio, open de [Toolbox](/docs/nl-nl/projects/assets/toolbox) .

2.

Selecteer de Creator Store  tab.

2.

In de sectie Categorieën , klik op de Bekijk Alles  knop. Alle categorieën worden weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Creator-Store-Categories-See-All.png)

3.

Klik op de Advertenties  tegel.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Creator-Store-Categories-Ads.png)

4.

Klik op een van de Portal  sjabloon pakketten.

5.

OPTIONEEL

 Pas de visuele elementen rondom de advertentie-eenheid aan door elementen binnen de Decorative  map van het pakket te wijzigen.

Zodra je de game publiceert, kunnen gebruikers de advertentie-eenheid in een van de volgende staten zien:

| Staat | | Beschrijving | | Voorbeeld |
| Actief | | De advertentie-eenheid kan advertenties tonen en toont momenteel een advertentie aan een gebruiker. | | ![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/PortalAds-Active.jpg) |
| Inactief | | De advertentie-eenheid kan advertenties tonen, maar toont momenteel geen advertentie aan een gebruiker om een van de volgende redenen:
-

De gebruiker komt niet in aanmerking om advertenties te zien.

-

De gebruiker heeft te veel advertenties in een korte periode gezien.

-

Er is een lage vraag naar advertenties van adverteerders tijdens die periode.

-

Er zijn geen advertenties die zijn gericht op de criteria van de gebruiker, zoals hun geslacht, apparaat of land.

Roblox toont in plaats daarvan een standaard fallback-afbeelding. | | ![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/PortalAds-Inactive.png) |
| Ongeldig | | De advertentie-eenheid kan geen advertenties tonen omdat deze niet voldoet aan de validatiecriteria. Het blokoppervlak dat advertenties toont, wordt zwart, en de deur wordt een betonnen muur. | | ![](https://prod.docsiteassets.roblox.com/assets/monetization/immersive-ads/PortalAds-Invalid.png) |

## [Advertentie-eenheden voor niet-geschikte gebruikers verwijderen](#advertentie-eenheden-voor-niet-geschikte-gebruikers-verwijderen)[](#advertentie-eenheden-voor-niet-geschikte-gebruikers-verwijderen)

Volgens de [Advertentienormen](https://en.help.roblox.com/hc/en-us/articles/13722260778260-Advertising-Standards)  van Roblox, moet je ofwel advertentie-inhoud verbergen, vervangen of blokkeren voor gebruikers die niet in aanmerking komen om advertenties te zien. Standaard behandelt de indringende advertentie-eenheden dit door advertenties te vervangen door een fallback-afbeelding van het Roblox-logo voor gebruikers die niet in aanmerking komen om advertenties te zien.

Om de advertentie-eenheden volledig te verbergen of te verwijderen, gebruik [GetPolicyInfoForPlayerAsync()](/docs/nl-nl/reference/engine/classes/PolicyService#GetPolicyInfoForPlayerAsync)  om een AreAdsAllowed  boolean terug te geven die de geschiktheid van elke gebruiker die toegang heeft tot je game om advertenties te zien bepaalt, en voeg vervolgens logica toe om de zichtbaarheid van advertenties voor niet-geschikte gebruikers aan te passen.

Bijvoorbeeld, het volgende codevoorbeeld gebruikt [GetPolicyInfoForPlayerAsync()](/docs/nl-nl/reference/engine/classes/PolicyService#GetPolicyInfoForPlayerAsync)  om de geschiktheid van elke gebruiker te controleren om advertenties te zien wanneer ze de game binnenkomen. Als AreAdsAllowed  waar is voor een gebruiker, blijven portal-advertenties zichtbaar, maar als het onwaar is, vernietigt het script ze allemaal. Hoewel dit een geweldige strategie is om advertentie-inhoud te verwijderen van gebruikers die niet in aanmerking komen om advertenties te zien, is het belangrijk op te merken dat het vernietigen van advertentie-eenheden de gameplay van je game kan veranderen als sommige gebruikers advertentie-eenheden kunnen zien terwijl anderen dat niet kunnen.

```

local Players = game:GetService("Players")

local PolicyService = game:GetService("PolicyService")

local Workspace = game:GetService("Workspace")

local player = Players.LocalPlayer

-- Voorbeeld gaat ervan uit dat er een "Main Portal Template" model onder Workspace bestaat

local mainPortal = Workspace:WaitForChild("Main Portal Template")

-- Verkrijg de beleidsinformatie voor de gebruiker

	local success, result = pcall(PolicyService.GetPolicyInfoForPlayerAsync, PolicyService, player)

	if success and result then

		if not result.AreAdsAllowed then

			-- Vernietig de "Main Portal Template" instantie op de client van de gebruiker als advertenties niet zijn toegestaan

			mainPortal:Destroy()

		end

	else

		print("Kon beleid voor speler niet verkrijgen", player.Name, "| Uitzondering:", result)

	end

```

## [Bekijk metrics van indringende advertenties](#bekijk-metrics-van-indringende-advertenties)[](#bekijk-metrics-van-indringende-advertenties)

Nadat je advertentie-eenheden in je game hebt ingevoegd, genereert het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  verschillende soorten metrische grafieken om je te helpen de algehele prestaties van je advertenties te analyseren.

Na 48 uur dat advertenties in je game draaien, kun je zien hoeveel video-weergaven, impressies en teleports je genereert via je gebruikersbasis, hoe elk advertentie-eenheidsformaat presteert, en hoeveel Robux je verdient met individuele advertentie-eenheden.

Door deze trends in de loop van de tijd te volgen, kun je strategische beslissingen nemen over het aantal advertentie-eenheden dat je per plaats opneemt, welk formaat advertentie-eenheid je wilt prioriteren, en waar je individuele advertentie-eenheden kunt plaatsen om video-weergaven, impressies en teleports te genereren.

Om metrics van indringende advertenties te bekijken:

1.

Ga naar Creations en selecteer een game.

2.

Ga naar Monetization  ⟩ Ads .

Metrische grafieken die impressies en teleports per advertentie-eenheid rapporteren, gebruiken de naam van elke advertentie-eenheid in Studio.

Roblox kan kleine "overlevering" aanpassingen aan impressies of teleports voor adverteerders maken om rekening te houden met mogelijke ongeldige video-weergaven, impressies of teleports. Dit kan resulteren in occasionele wijzigingen in je Verdiensten per Mille  of Verdiensten per Teleport  metrics.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
