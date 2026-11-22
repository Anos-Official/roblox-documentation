<!-- Source: https://create.roblox.com/docs/nl-nl/studio/avatar-settings -->

Avatar-instellingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)

# Avatar-instellingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het Avatar-instellingen  venster, toegankelijk via het Bestand  menu van Studio of het Avatar  tabblad, stelt je in staat om de uitstraling en het gedrag van gebruikersavatars in je hele game te controleren.

 ![Avatar-instellingen aangegeven in de werkbalk van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Avatar-Settings.png)  ![Lay-out van het venster Avatar-instellingen](https://prod.docsiteassets.roblox.com/assets/studio/general/Avatar-Settings-Window.png)

Avatar-instellingen  wijzigt de onderliggende standaardinstellingen van de game die niet zichtbaar zijn buiten de instellingeninterface of toegankelijk zijn met scripts. Dit kan leiden tot moeilijk te debuggen gedragingen, vooral wanneer je samenwerkt met teams of aan een universum met meerdere plaatsbestanden werkt. Test je wijzigingen door gebruik te maken van de preview van het venster en door te playtesten in Studio, zodat je volledig begrijpt wat de impact is op spelersavatars voordat je wijzigingen publiceert in je live game.

De bovenste balk van het Avatar-instellingen  venster biedt gemakkelijke toegang om snel het type avatar in te stellen, een preset toe te wijzen en de preview in te schakelen.

| Instelling | | Beschrijving |
| --- | --- |
| Preset | | Toont welke instellingenpreset is ingeschakeld en stelt je in staat om tussen hen te schakelen (voor beschrijvingen van elke instelling, zie [Algemeen](#algemeen) ). Als de preset --  weergeeft, betekent dit dat de huidige instellingen zijn aangepast en niet overeenkomen met een preset. |
| Preview | | Schakelt een preview-opstelling van avatars in op basis van de toegepaste avatarinstellingen en maakt een AvatarPreview  map aan onder [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  ⟩ [Camera](/docs/nl-nl/reference/engine/classes/Camera)  met vier representatieve avatartypes. Je kunt avatars aan de opstelling toevoegen of verwijderen door ze in of uit de map te slepen. De map wordt verwijderd tijdens het playtesten in Studio en wordt niet opgeslagen in je plaatsbestand. |
| ⋯ | | Stelt spelerspersonages in op R6 Alleen , R15 Alleen , of R15 en R6 . Om een game van R6 Alleen  naar R15 Alleen  te converteren, zie [Converteer games van R6 Alleen naar R15 Alleen](/docs/nl-nl/characters/r6-only-to-r15-only) . |

## [Algemeen](#algemeen)[](#algemeen)

Het Algemeen  tabblad biedt eenvoudige presets die zijn afgestemd op de behoeften van de meeste games. In veel gevallen zal een van deze presets passen bij de avatargebruikscenario's van je game en is aanvullende configuratie niet nodig. Geavanceerde ontwikkelaars kunnen echter het gedrag van avatars verder aanpassen met behulp van de meer gedetailleerde instellingen die beschikbaar zijn in de andere tabbladen.

| Instelling | | Beschrijving |
| Spelerkeuze | | Laadt spelersavatars zonder enige aanpassingen. |
| Consistente Gameplay | | Stelt alle avatars in op dezelfde hoogte met dezelfde box collider voor consistente botsingsgedragingen. |

## [Lichaam](#lichaam)[](#lichaam)

Het Lichaam  tabblad bevat instellingen voor lichaamsverhoudingen, onderdelen, schaal.

| Instelling | | Beschrijving |
| Schaal | |
-

Spelerkeuze  (standaard): Wijzigt de schaal van de avatar niet.

-

Aangepaste schaal : Stelt je in staat om avatars naar een absolute hoogte in studs te schalen, maar behoudt hun verhoudingen. Je kunt een Minimum  en Maximum  bereik instellen.

Ter referentie, klassieke stijl avatars zijn ongeveer 5 studs hoog. Meer humanoïde stijl verhoudingen zijn ongeveer 6 tot 6.5 studs.

 |
| Uiterlijk | |
-

Spelerkeuze  (standaard): Wijzigt het uiterlijk van de avatar niet.

-

Aangepaste onderdelen : Laat je een standaard lichaamsdeel van een gebruiker vervangen door een aangepaste ID.

 |
| Bouw | |
-

Spelerkeuze  (standaard): Wijzigt de verhoudingen van de avatar niet.

-

Aangepaste bouw : Biedt aanpassingsopties die het lichaams type, de hoogte, de breedte, de hoofdgrootte en de verhoudingen van de avatar van de gebruiker beperken.

 |

## [Kleding](#kleding)[](#kleding)

Het Kleding  tabblad bevat bedieningselementen voor gelaagde en klassieke kleding.

| Instelling | | Beschrijving |
| Kleding schaal | |
-

Spelerkeuze  (standaard): Houdt de kleding van de avatar van de gebruiker.

-

Aangepaste limiet : Verwijdert kleding die de limiet van de avatar overschrijdt.

-

Limietgrenzen : De hoeveelheid lengte, breedte en diepte padding buiten de begrenzingsdoos van het avatarlichaam, uitgedrukt als een percentage. Deze limiet wordt weergegeven als een blauwe doos rond elke avatar in de preview-opstelling.
0% betekent geen padding en items moeten strikt binnen de begrenzingsdoos van het lichaam vallen en 100% voegt padding toe gelijk aan de begrenzingsdoos van de avatar aan alle zijden, waardoor items tot drie keer de lichaamsgrootte kunnen innemen.

 |
| Aangepaste kleding | |
-

Spelerkeuze  (standaard): Houdt de kleding van de avatar van de gebruiker.

-

Aangepaste kleding : Laat je een gelaagde accessoire-uitrustingsslot of klassiek kledingtype vervangen door een aangepaste ID. Als je het vakje aanvinkt om te overschrijven, maar het veld Asset ID  leeg laat, worden alle spelerskleding in die uitrustingsslot verwijderd.

 |

## [Accessoires](#accessoires)[](#accessoires)

Het Accessoires  tabblad bevat instellingen met betrekking tot accessoires in je game.

| Instelling | | Beschrijving |
| Accessoire schaal | |
-

Spelerkeuze  (standaard): Wijzigt de schaal van de door de gebruiker uitgeruste accessoires niet.

-

Aangepaste limiet : Stelt je in staat om accessoires te schalen , of accessoires te verwijderen  die de limiet overschrijden.

-

Limietmethode : Stelt je in staat om accessoires te schalen  om binnen de limietgrenzen te passen, of accessoires te verwijderen  die de limiet overschrijden.

-

Limietgrenzen : De hoeveelheid lengte, breedte en diepte padding buiten de begrenzingsdoos van het avatarlichaam, uitgedrukt als een percentage. De limietgrenzen worden weergegeven als een blauwe doos rond elke avatar in de preview-opstelling.
0% betekent geen padding en items moeten strikt binnen de begrenzingsdoos van het lichaam vallen en 100% betekent padding met 100% van de begrenzingsdoos aan elke kant, zodat items een gebied van drie keer de grootte van het lichaam kunnen innemen.

 |
| Aangepaste accessoires | |
-

Spelerkeuze  (standaard): Houdt de accessoires van de avatar van de gebruiker.

-

Aangepaste accessoires : Laat je de accessoiretypes van een gebruiker vervangen door een aangepaste ID. Als je het vakje aanvinkt om te overschrijven, maar het veld Asset ID leeg laat, worden alle spelersaccessoires van die categorie verwijderd.

 |
| Accessoiregedragingen | | Bedieningselementen om accessoiregedragingen zoals VFX , Geluid  en Emissives  in of uit te schakelen. |

## [Beweging](#beweging)[](#beweging)

Het Beweging  tabblad bevat instellingen voor botsing en animatie, evenals configuraties voor mogelijkheden voor de [Character Controller Library](/docs/nl-nl/characters/character-controller-library) .

| Instelling | | Beschrijving |
| Botsing | |
-

Standaard : Gebruik de [OuterBox](/docs/nl-nl/reference/engine/enums/R15CollisionType#OuterBox)  methode die botsingen berekent op basis van de begrenzingsdozen van avataronderdelen.

-

Enkele Collider : Gebruik een enkele consistent grote doos voor botsingen.

-

Grootte : Stel de lengte, breedte en diepte van de colliderdoos in.

-

Hit- en Aanraakdetectie : Stel hit- en aanraakevenementen in om avatar onderdelen  of colliders  te gebruiken.

-

Legacy : Gebruik de [InnerBox](/docs/nl-nl/reference/engine/enums/R15CollisionType#InnerBox)  botsingsmethode (alleen voor achterwaartse compatibiliteit).

 |
| Animatiepakketten | |
-

Spelerkeuze  (standaard): Houdt de animatiestijl van het platform van de gebruiker, inclusief stijl pakketten

-

Standaard R15 : Alle avatars gebruiken de standaard R15 platformanimaties.

-

Standaard R6 : Alle avatars gebruiken de standaard R6 platformanimaties.

 |
| Animatieclips | |
-

Spelerkeuze  (standaard): Houdt de animaties van het platform van de gebruiker.

-

Aangepaste clips : Laat je elke standaard animatietype vervangen en previewen met een aangepaste ID. Deze overschrijvingen worden bovenop je selectie van Animatiepakket  toegepast.

 |
| Vaardigheden | |
-

Legacy Humanoid  (standaard): Gebruik legacy karaktervaardigheden die zijn gebouwd op rigide [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  toestandsmachines.

-

Character Controller Library : Schakelt de [Character Controller Library](/docs/nl-nl/characters/character-controller-library)  in en laat je standaard karaktervaardigheden in of uitschakelen tijdens runtime.

 |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
