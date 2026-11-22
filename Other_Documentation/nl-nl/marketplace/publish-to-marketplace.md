<!-- Source: https://create.roblox.com/docs/nl-nl/marketplace/publish-to-marketplace -->

Publiceren op de Marketplace | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Marktplaats

# Publiceren op de Marketplace

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Om activa op de Marketplace te publiceren en te verkopen, moet je account of groep eerst voldoen aan [Roblox's Creator en Groep vereisten](/docs/nl-nl/marketplace/marketplace-policy#creator-and-group-requirements) . Gebruikers die aan de vereisten voldoen en hun [publicatielimieten](#upload--en-publicatielimieten)  niet hebben bereikt, kunnen hun activa uploaden en verkopen in de volgende algemene stappen:

1.

[Upload het activum](#upload-een-activum)  via Studio voor validatie en moderatie.

2.

[Publiceer het activum](#publiceer-een-activum)  op de Marketplace nadat je metadata en Marketplace-instellingen hebt geconfigureerd.

De volgende publicatie-instructies zijn van toepassing op 3D-accessoires en kledingactiva. Voor andere activumtypes:

-

Voor informatie over 2D klassieke kleding, zie [Klassieke kleding](/docs/nl-nl/avatar/classic-clothing) .

-

Voor informatie over locomotie-animatiesets, zie [Animatiepakketten](/docs/nl-nl/avatar/animation-packs) .

-

Voor informatie over achtergronden voor avatars, zie [Achtergronden](/docs/nl-nl/avatar/backgrounds) .

## [Upload- en publicatielimieten](#upload--en-publicatielimieten)[](#upload--en-publicatielimieten)

Er zijn limieten aan het aantal activa dat je kunt uploaden naar Roblox en dat je kunt inschakelen voor verkoop op de Marketplace:

|  | | Beperkte | | Lichamen of Hoofden |
| --- | --- |
| Uploaden en moderatie | | Geen limiet | | Geen limiet |
| Publiceren - Inschakelen voor verkoop † | | Geen limiet voor betaalde Beperkte. 50 per dag voor gratis Beperkte. | | Geen limiet |

†* Voor activa die van de verkoop kunnen worden gehaald, telt alleen de eerste keer dat het activum voor verkoop is ingeschakeld tegen deze limiet.*

## [Upload een activum](#upload-een-activum)[](#upload-een-activum)

Wanneer je je activum uploadt, controleert Studio je activum op technische problemen, zoals een onjuiste hiërarchie of accessoire-structuur. Je moet ook een [aangepaste miniatuur](/docs/nl-nl/marketplace/custom-thumbnails)  aan je activum toevoegen voordat je het uploadt om aan te passen hoe het item op de Marketplace wordt weergegeven.

-

Na het uploaden van je activum, wordt het item in de moderatiewachtrij geplaatst voordat je het kunt inschakelen voor verkoop. Zie [Moderatie](/docs/nl-nl/marketplace/moderation)  voor meer informatie over dit proces.

-

Voor details over vooruitbetalingen en kosten bij het publiceren van activa op de marketplace, zie [Kosten en commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions) .

Test al je activa grondig voordat je ze uploadt om ervoor te zorgen dat ze voldoen aan Roblox's [Marketplace beleid](/docs/nl-nl/marketplace/marketplace-policy) . Als je een 3D-accessoire of gelaagd kledingitem moet repareren na het uploaden, zie [Update een bestaand item](#update-een-bestaand-item) .

Om je activum te uploaden:

1.

Voeg in Studio het Marketplace-item toe aan je werkruimte.

-

Voor accessoires en kleding moet het item een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  object zijn. Voor informatie over de vereiste specificaties, zie [Rigid accessoire specificaties](/docs/nl-nl/avatar/rigid-accessories/specifications)  en [Gelaagde kleding specificaties](/docs/nl-nl/avatar/layered-accessories/specifications) .

-

Upload kleding en accessoires als een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory) . Voor informatie over het omzetten van je [Model](/docs/nl-nl/reference/engine/classes/Model)  naar een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory) , zie [Accessoire Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool) .

-

Als je schoenen uploadt, moet elke schoen zijn eigen accessoire-object zijn:

-

Noem de respectieve schoenaccessoires LeftShoeAccessory  en RightShoeAccessory .

-

Selecteer zowel de linker als de rechter schoenaccessoires en klik met de rechtermuisknop ⟩ Groep als een Model  voordat je stap 2 uitvoert.

-

Voor lichamen en hoofden moet het item een [Model](/docs/nl-nl/reference/engine/classes/Model)  zijn. Voor informatie over de vereiste specificaties, zie [Avatar karakter specificaties](/docs/nl-nl/avatar/character-bodies/specifications) .

-

Je kunt een standaard huidkleur aan je lichaam toevoegen door een [BodyColors](/docs/nl-nl/reference/engine/classes/BodyColors)  object aan je model toe te voegen.

2.

Klik met de rechtermuisknop op het object in het Explorer  venster en selecteer Opslaan naar Roblox .

3.

Selecteer in Indienen als  Avatar Activum .

4.

Selecteer in het dropdownmenu Activumtype  het juiste marketplace activumtype. Validatie begint bij selectie.

Als je dit dropdownmenu niet ziet, heeft je account mogelijk geen toegang om activa naar de Marketplace te uploaden. Voor meer informatie, zie [Creator vereisten](/docs/nl-nl/marketplace/marketplace-policy#creator-vereisten) .

![](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Publishing-Clothes.png) Een kledingaccessoire activum uploaden

![](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Publishing-Body.png) Een lichaam activum bundel uploaden

5.

Zodra de validatie succesvol is voltooid, verschijnt er een dialoogvenster voor itembeschrijving. Vul de volgende velden in en volg waar mogelijk de [metadata best practices](/docs/nl-nl/production/publishing/publish-games-and-places#publiceer-games) .

-

Titel : De naam van je activum op de Marketplace.

-

Maker : Je kunt je gebruiker of een van de bijbehorende groepen instellen als de maker van dit activum. De maker kan toegang krijgen tot het Marketplace-activum om prijzen, voordelen en verkoopinformatie in te stellen.

6.

Klik op Indienen  om eventuele toepasselijke uploadkosten te betalen en je activum ter goedkeuring voor moderatie in te dienen.

Na het uploaden van het activum, kun je het vinden in het Creations  tabblad van de [Creator Hub](https://create.roblox.com/dashboard/creations?activeTab=HairAccessory&filterIndex=0)  in een pre-gepubliceerde staat waar je de huidige moderatiestatus kunt bekijken of de titel en beschrijving kunt bewerken.

 ![Lijst van Hoed activa op de Creator Hub met de huidige status onder elk item weergegeven.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Creation-Page.png)

### [Organiseer avatar items](#organiseer-avatar-items)[](#organiseer-avatar-items)

In Creations  ⟩ Avatar Items , kun je je avatar items op de volgende manieren organiseren en doorbladeren:

-

Mappen : In het Alle  tabblad, maak een map aan en voeg vervolgens items toe vanuit het menu van elk item. Gebruik mappen om items te groeperen zoals je wilt, bijvoorbeeld per collectie, per drop, of per werk in uitvoering. Mappen werken voor zowel gebruikers- als groepscreaties, bevatten avataractiva en bundels, en zijn enkelvoudig zonder nesting. Een item kan in meer dan één map staan.

-

Recent : De Recent  weergave onder het Alle  tabblad toont je 50 meest recent geüploade avatar items en bundels.

-

Marketplace-categorieën : Standaard worden items gegroepeerd op dezelfde Marketplace-categorieën die kopers doorbladeren, in plaats van op activumtype. Items worden automatisch geclassificeerd, en één categorie kan verschillende activumtypes bevatten; bijvoorbeeld, gelaagde kleding shirts en broeken kunnen beide worden geclassificeerd als een Bodysuit . Nieuw geüploade items kunnen even duren om geclassificeerd te worden, maar verschijnen in Recent  in de tussentijd. Om items in plaats daarvan op activumtype te groeperen, schakel je Categorize by Taxonomy  uit in de rechterbovenhoek.

### [Update een bestaand item](#update-een-bestaand-item)[](#update-een-bestaand-item)

Je kunt een rigide of gelaagd accessoire dat je al hebt geüpload, inclusief items die op de Marketplace zijn gepubliceerd, bijwerken. De update behoudt de activum-ID van het item, de verkoopgeschiedenis en bestaande eigenaren, en eigenaren ontvangen automatisch de bijgewerkte versie. Een update moet hetzelfde activumtype zijn als het oorspronkelijke item.

Om een bestaand item bij te werken:

1.

Open in Studio je item en maak je aanpassingen.

2.

Klik met de rechtermuisknop op het object in het Explorer  venster en selecteer Opslaan naar Roblox .

3.

Zet Update een bestaand activum  aan en voer de activum-ID in van het item dat je vervangt.

4.

Klik op Indienen  om de uploadkosten te betalen en de update ter goedkeuring voor moderatie in te dienen.

Houd het volgende in gedachten bij het bijwerken van items:

-

Je kunt alles veranderen voordat een item is gepubliceerd. Nadat een item is gepubliceerd, zijn updates bedoeld voor fixes, zoals pasvorm, kooien, kleine mesh- of textuurproblemen, of de miniatuur. Het bijgewerkte item moet er nog steeds uitzien als het item dat eigenaren hebben gekocht, dus substantiële ontwerpwijzigingen zijn niet toegestaan.

-

Elke update kost dezelfde uploadkosten als een nieuw item van dat type, en elke update van een gepubliceerd item gaat door [moderatie](/docs/nl-nl/marketplace/moderation)  voordat het live gaat.

-

Als een update niet wordt goedgekeurd, ontvang je een melding in je inbox. Je oorspronkelijke item blijft ongewijzigd, zodat je je wijzigingen kunt aanpassen en opnieuw kunt indienen.

### [Probleemoplossing](#probleemoplossing)[](#probleemoplossing)

Tijdens het uploadproces kun je problemen tegenkomen die voorkomen dat een item wordt geüpload. Deze kunnen optreden door technische problemen met het activum zelf, of problemen met de metadata van het activum, zoals ongeldige eigendom of ongepaste tekststrings.

Voor technische problemen tijdens de validatiestap, beweeg je de muis over de fout om de specifieke foutuitvoer te zien. De meeste problemen vereisen mogelijk dat je je model aanpast in je externe modelleerapplicatie en opnieuw importeert in Studio.

Zie de modelleerspecificaties voor [rigide accessoires](/docs/nl-nl/avatar/rigid-accessories/specifications) , [gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications) , en [karakterlichamen](/docs/nl-nl/avatar/character-bodies/specifications)  voor technische vereisten.

![Een voorbeeldfout die aangeeft dat een FaceControls-object ontbreekt van een Avatar Hoofd.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Error-Example.png) Een fout die wordt weergegeven wanneer een FaceControls-object niet wordt gedetecteerd voor hoofdanimatie

Voor andere validatieproblemen, houd rekening met de volgende veelvoorkomende uploadconflicten:

-

De tekstfilter van Studio identificeert ongepaste strings in de naam of beschrijving.

-

Je item gebruikt een AssetID  of TextureID  die behoort tot een bestaand activum op de Marketplace, of behoort niet tot jou of een geschikte groep.

-

Je item gebruikt een AssetID  of TextureID  die nog in afwachting van moderatie is.

## [Publiceer een activum](#publiceer-een-activum)[](#publiceer-een-activum)

Je kunt geüploade activa openen in je [Creator Dashboard](https://create.roblox.com/dashboard/creations) . Elk item heeft een Beheer Item  pagina waar je metadata kunt wijzigen, verkoopgerelateerde instellingen kunt configureren en je activum op de Marketplace kunt publiceren.

Als je ontdekt dat je rigide of gelaagd accessoire kapot is of niet werkt zoals verwacht, kun je [het bestaande item bijwerken](#update-een-bestaand-item)  met een fix. Andere itemtypes, zoals bundels, kunnen niet worden bijgewerkt na upload.

Als een Roblox-update een bestaand activum kapot maakt, [dien een helpticket in](https://www.roblox.com/support)  met een link naar het kapotte item en een .rbxm  van de juiste versie.

Voordat je je activum publiceert, is het belangrijk om te overwegen of je je activum als een Beperkt of Niet-Beperkt item wilt verkopen.

Als je item gebruikmaakt van gelicentieerde IP, ga dan naar de sectie Itemattributen  van de Beheer Item  pagina, en selecteer je goedgekeurde licentie uit de licentiedropdown voordat je publiceert. Voor informatie over hoe je een licentie kunt aanvragen en hoe de omzetverdeling van toepassing is, zie [Marketplace-licenties](/docs/nl-nl/ip-licensing/creators#marketplace-licenties) .

### [Metadata](#metadata)[](#metadata)

Je kunt de metadata voor al je creaties op elk moment aanpassen. Houd er rekening mee dat de metadata, zoals de titel en beschrijving, moet voldoen aan [algemene best practices](/docs/nl-nl/production/publishing/publish-games-and-places#publiceer-games)  om moderatie te vermijden en de vindbaarheid te verbeteren.

 ![Beheer Item pagina met voorbeeldactivum.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Manage-Item-Page.png)

Op de Beheer Item pagina kun je de volgende velden bijwerken:

-

Titel : De naam van je activum op de Marketplace. Je kunt dit na publicatie wijzigen.

-

Beschrijving : De beschrijving van je activum op de Marketplace.

### [Itemattributen](#itemattributen)[](#itemattributen)

In Itemattributen  kun je de Beschikbaarheid  van je activum instellen als een Niet-Beperkt  of een Beperkt  item. Elk type beschikbaarheid verandert de beschikbare itemattribuutvelden die je kunt wijzigen.

-

Niet-Beperkt  items staan onbeperkte kopieën toe om te worden gekocht.

-

Beperkt  items staan slechts een vast aantal items toe om te worden gekocht, waardoor je een vastgesteld aantal exclusieve of evenement-specifieke digitale items kunt verkopen.

| Itembeschikbaarheid | | Verkoop eigenschappen |
| Niet-Beperkt
 | | — Onbeperkte kopieën beschikbaar om te kopen
— Kan het aantal kopieën per gebruiker niet beperken
— Kan gratis items niet verkopen
— Kan niet doorverkopen |
| Beperkt
 | | — Beperkt het totale aantal verkochte kopieën
— Kan het aantal originele kopieën per gebruiker beperken
— Kan gratis items verkopen, per-eenheidsvergoeding is van toepassing
— Doorverkoopbaar |

Voordat je een van beide opties selecteert, maak jezelf vertrouwd met de verschillende [kosten- en commissiestructuren](/docs/nl-nl/marketplace/marketplace-fees-and-commissions)  die betrokken zijn bij verschillende soorten items en eventuele toepasselijke landbeleidbeperkingen.

 ![Instellingen voor Item Attributen.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Item-Attributes.png)

De volgende itemattributen zijn alleen van toepassing als je je activum als een Beperkt item instelt:

-

Hoeveelheid : Het aantal activa dat beschikbaar is op de Marketplace. De maximale hoeveelheid voor betaalde Beperkte is 3000, terwijl gratis Beperkte geen maximale hoeveelheid hebben. Na publicatie van een gratis Beperkt item, kun je de hoeveelheid verhogen door het item te [herbevoorraden](/docs/nl-nl/marketplace/marketplace-fees-and-commissions#restocking) .

-

Beperk kopieën per gebruiker : (Optioneel) Stelt het aantal keren in dat een gebruiker dit activum kan kopen.

-

Kopie-limieten zijn gebaseerd op eigendom. Als een gebruiker het maximale aantal kopieën in zijn inventaris bezit, kan hij het activum niet langer kopen van de oorspronkelijke aanbieding. Als de gebruiker niet langer het maximale aantal kopieën bezit, kan hij de kopieën van de oorspronkelijke aanbieding kopen.

-

Na publicatie kun je deze waarde alleen verhogen, maar niet verlagen.

-

Gratis Item : Stelt de verkoopprijs van dit item op nul in. Gratis Beperkte items maken gebruik van een [per-eenheidsvergoedingstructuur](/docs/nl-nl/marketplace/marketplace-fees-and-commissions#per-eenheid-vergoeding) .

-

Doorverkoopbaar : Als ingeschakeld, kunnen gebruikers je Beperkte item doorverkopen. Als het doorverkocht wordt, kom je in aanmerking voor [doorverkoopcommissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions#doorverkopen) . Je kunt de Doorverkoopbare status  op een gepubliceerd item wijzigen. Als ingeschakeld op een item, kan het in de toekomst niet worden uitgeschakeld.

-

De doorverkoopbare eigenschap is niet beschikbaar voor accounts die in Japan zijn gevestigd.

-

Het inschakelen van doorverkoop schakelt permanent [herbevoorrading](/docs/nl-nl/marketplace/marketplace-fees-and-commissions#restocking)  voor het item uit.

##### Beperk kopieën per gebruiker

Als je een Beperkt item verkoopt, kun je Beperk Kopieën Per Gebruiker  inschakelen om het aantal keren in te stellen dat een gebruiker dit activum kan kopen. Dit heeft alleen invloed op de aankopen van de oorspronkelijke aanbieding en gebruikers kunnen nog steeds extra kopieën van hetzelfde Beperkte activum kopen van doorverkopers. Je kunt deze instelling niet wijzigen na publicatie.

Kopie-limieten zijn gebaseerd op eigendom. Als een gebruiker het maximale aantal kopieën in zijn inventaris bezit, kan hij het activum niet langer kopen van de oorspronkelijke aanbieding. Als de gebruiker niet langer het maximale aantal kopieën bezit, kan hij de kopieën van de oorspronkelijke aanbieding kopen.

### [Prijzen](#prijzen)[](#prijzen)

In de prijsectie kun je verschillende prijsinstellingen instellen. Bij het vermelden van je Marketplace-item, moet je je prijs instellen binnen het juiste [dynamische prijsbereik](/docs/nl-nl/marketplace/marketplace-fees-and-commissions#prijsklassen)  voor dat activumtype.

 ![Prijsinstellingen velden.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Pricing-Settings.png)

Je kunt twee soorten prijscontroles instellen op basis van de prijsvloer:

-

Bedrag Boven Prijsvloer (vereist)  is het bedrag in Robux dat het item boven de huidige prijsvloer zal zijn. Bijvoorbeeld, als de vloer 50 Robux is en je hier 5 Robux invoert, zal de prijs 55 Robux zijn. Je kunt ook kiezen om deze waarde op nul in te stellen als je wilt dat je item altijd tegen de vloerprijs wordt geprijsd.

-

Niet Prijzen Onder (optioneel)  is de laagste prijs waarvoor een item van een maker kan worden verkocht. Het is optioneel en zal altijd worden gerespecteerd. Deze invoer is nuttig als je je zorgen maakt over wat de laagste prijs is waarvoor je item kan worden verkocht. Bijvoorbeeld, als je hier 200 Robux invoert, zal je itemprijs nooit onder de 200 Robux dalen, ongeacht wat de prijsvloer is.

Als je een Marketplace-vermelding had vóór de implementatie van het dynamische prijsbereik, zijn de volgende prijscontroles nu van toepassing totdat ze worden gewijzigd:

-

Bedrag Boven Prijsvloer  is standaard 0 Robux.

-

Niet Prijzen Onder  is standaard de bestaande prijs van het item.

Bij het instellen van een prijs, kun je de percentageverdeling van commissies in het dialoogvenster zien. Een vergelijkbare verdeling van kosten, wanneer van toepassing, wordt onderaan de prompt weergegeven. Zie [Marketplace kosten en commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions)  voor meer informatie over de kosten en commissies voor Marketplace-items.

##### Regionale Prijzen voor Avatar items

Regionale Prijzen stellen je in staat om je item aan te bieden aan gebruikers tegen regio-specifieke prijzen. Nadat je de wereldwijde prijs van het item hebt bepaald, gebruikt Roblox een verscheidenheid aan signalen zoals de koopkracht van een regio, wisselkoersen en lokaal bestedingsgedrag om de meest geschikte prijs voor het item per regio in te stellen.

Regionale Prijzen zijn standaard ingeschakeld. Je kunt op elk moment afmelden. Voor meer informatie, zie [Regionale Prijzen](/docs/nl-nl/production/monetization/regional-pricing) .

### [Verkooplocatie](#verkooplocatie)[](#verkooplocatie)

De optie Verkooplocatie  stelt in waar je je activum kunt verkopen buiten de Marketplace. In sommige gevallen wil je misschien de beschikbaarheid van je activum beperken tot bepaalde games, of alleen de Marketplace.

 ![Velden voor verkooplocatie.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Sale-Location.png)

Games die Marketplace-items verkopen ontvangen een extra [commissie](/docs/nl-nl/marketplace/marketplace-fees-and-commissions)  inclusief transacties die zijn gemaakt via het [Inspect Menu](/docs/nl-nl/players/avatar-inspect-menu)  of [via de API](/docs/nl-nl/players/avatar-editor)  binnen een game.

De volgende locatie-opties zijn beschikbaar voor alle items:

| Locatie | | Beschrijving |
| Marketplace en Alle Ervaringen | | Gebruikers kunnen dit item kopen in de Marketplace of in alle games die Marketplace-aankopen aanbieden. Dit is de standaardinstelling. |
| Ervaring Per Plaats ID (Alleen API) | | Gebruikers kunnen alleen de originele voorraad van dit item kopen in de games die zijn gekoppeld aan de opgegeven Plaats ID. Slechts één Plaats ID per game is vereist en makers kunnen Plaats ID's op elk moment bijwerken en wijzigen.

Na het opslaan van een nieuwe Plaats ID, moet de game-eigenaar handmatig [het avataritem inschakelen](/docs/nl-nl/production/monetization/avatar-items)  voor hun game. |

### [Publiceer item](#publiceer-item)[](#publiceer-item)

Bij het eerste publiceren van je activum, selecteer je de Publiceer Item  knop aan het einde van het formulier om de [publicatiekosten](/docs/nl-nl/marketplace/marketplace-fees-and-commissions#publicatievoorschot)  te betalen en je item te vermelden voor verkoop.

### [Verkoop inschakelen](#verkoop-inschakelen)[](#verkoop-inschakelen)

 ![Verkoop inschakelen toggle rechtsboven op de pagina.](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Sale-Toggle.png)

Je kunt de verkoop van een gepubliceerd activum uitschakelen door de Te Koop  optie bovenaan de Beheer Item  pagina uit te schakelen.

Nadat je een item voor verkoop hebt ingeschakeld, kun je het item van de verkoop halen door de toggle uit te schakelen. Een publicatiekost is niet vereist om het opnieuw in te schakelen.

Om je activum permanent te archiveren, zie [Archive activa](/docs/nl-nl/marketplace/moderation#archiveren-van-assets) .

### [Plan de verkoop van een item](#plan-de-verkoop-van-een-item)[](#plan-de-verkoop-van-een-item)

Om de verkoop van je activum in de Beheer Item  pagina te plannen, klik je op Verkoop Plannen  onder de Te Koop  toggle en voer je een Verkoop Start  datum en een optionele Verkoop Eind  datum in. Als je geen einddatum invoert, is het item onbepaald te koop.

Je kunt planning gebruiken om zowel Beperkte als Niet-Beperkte activa te verkopen.

Je kunt verkopen tot 30 dagen van tevoren plannen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
