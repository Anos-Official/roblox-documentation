<!-- Source: https://create.roblox.com/docs/nl-nl/projects/assets/packages -->

Pakketten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)

# Pakketten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Om assets georganiseerd en herbruikbaar te houden binnen je team of over meerdere projecten, kun je je instanties groeperen en omzetten in herbruikbare pakketten . Pakketten maken het algehele proces van het bouwen van werelden sneller en ergonomischer, maar ze helpen ook met consistentie, deduplicatie, samenwerking en versiebeheer:

-

Eenvoudig [alle kopieën](#massale-updates)  van een pakket bijwerken naar de nieuwste versie, of alleen [specifieke kopieën](#update-verouderde-kopie%C3%ABn)  bijwerken.

-

Pakketten instellen om [automatisch bij te werken](#automatische-updates)  wanneer er een nieuwe versie beschikbaar is.

-

Samenwerkers Bewerken  of Gebruik  rechten geven voor de inhoud van een pakket.

-

De volledige versiegeschiedenis van een pakket bekijken, versies vergelijken en oude versies herstellen.

De meest efficiënte workflow is om een [pakket te maken](#pakketten-maken) , het [te delen](#delen-en-toegangslevels)  met eventuele samenwerkers, en het [in te stellen op automatische updates](#automatische-updates) . En je hoeft niet te wachten tot een model "af" is voordat je het in een pakket gebruikt. Zelfs als het pakket een tijdelijke aanduiding bovenop een eenvoudige vorm is, kun je het gebruiken om je [omgeving te greyboxen](/docs/nl-nl/tutorials/curriculums/environmental-art/greybox-your-environment)  en vervolgens zullen de tijdelijke aanduidingen automatisch worden bijgewerkt terwijl je meer gedetailleerde versies publiceert.

## [Pakketten maken](#pakketten-maken)[](#pakketten-maken)

Als je een pakket wilt maken met beperkte assets waarvoor je geen [expliciete toestemming](/docs/nl-nl/projects/assets/privacy#bekijk-machtigingen)  hebt om te gebruiken, kun je het pakket nog steeds maken, maar die specifieke beperkte assets zullen niet  zichtbaar of hoorbaar zijn tijdens runtime, tenzij het spel zelf toestemming heeft om die assets te gebruiken.

Je kunt een pakket maken van elk enkel object of elke enkele ouder en kinderen tak van objecten. Als je een pakket voor een enkel object wilt maken, voeg het dan eerst toe aan een [Model](/docs/nl-nl/reference/engine/classes/Model)  groepering, zodat je later kindobjecten binnen het pakket kunt toevoegen, verwijderen of schalen zonder het pakket te breken.

Om een pakket te maken:

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster of 3D viewport, klik met de rechtermuisknop op het object(en) dat je in een pakket wilt omzetten en selecteer in het contextmenu Converteren naar Pakket .

2.

Vul in het nieuwe venster de pakketdetails in. In het bijzonder, als je in een [groep](/docs/nl-nl/projects/groups)  werkt, stel dan Eigendom  in op de juiste groep waarvoor je toestemming hebt om groepsgames te maken/bewerken.

Eigendomsoverdrachten worden niet  ondersteund door het assetsysteem, dus overweeg zorgvuldig de eigenaar bij het maken van een pakket.

3.

Klik op Indienen .

4.

Nadat de conversie is voltooid, ontvangt het object een "kettinglink" symbool in het [Explorer](/docs/nl-nl/studio/explorer)  venster om het als een pakket te identificeren. Daarnaast kun je een nieuw [PackageLink](/docs/nl-nl/reference/engine/classes/PackageLink)  object zien dat aan het object is gekoppeld.

 ![Een esdoornboom model in het Explorer venster met het pakketicoon ernaast.](https://prod.docsiteassets.roblox.com/assets/studio/packages/Package-Structure-Explorer.png)

5.

OPTIONEEL

 Selecteer het [PackageLink](/docs/nl-nl/reference/engine/classes/PackageLink)  object en schakel [AutoUpdate](/docs/nl-nl/reference/engine/classes/PackageLink#AutoUpdate)  in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster in. Let op hoe het icoon verandert om aan te geven dat het pakket is ingesteld om automatisch bij te werken.

Verwijder of verplaats het [PackageLink](/docs/nl-nl/reference/engine/classes/PackageLink)  object niet! Dit zou elke pakketkopie terug omzetten naar een normaal object en de pakketcapaciteiten verliezen, zoals de mogelijkheid om zichzelf bij te werken wanneer er een nieuwe versie is.

## [Pakketten invoegen](#pakketten-invoegen)[](#pakketten-invoegen)

Om een pakket in te voegen dat nog niet bestaat in de huidige plaats, moet je het aanvankelijk  invoegen vanuit de [Toolbox](/docs/nl-nl/projects/assets/toolbox) :

-

Vanuit Inventaris  ⟩ Mijn Pakketten  voor pakketten die je hebt gepubliceerd of verkregen uit de [Creator Store](/docs/nl-nl/production/creator-store) , evenals pakketten die een vriend bezit en jou [toestemming](#delen-en-toegangslevels)  heeft gegeven om te gebruiken.

-

Vanuit Creaties  ⟩ Groep Pakketten  voor pakketten gepubliceerd door leden van je [groep](/docs/nl-nl/projects/groups)  (inclusief jezelf).

![Een close-up van de Toolbox met zowel het Inventaris tabblad als het dropdownmenu voor assets gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Inventory-My-Packages.png) Toolbox ⟩ Inventaris ⟩ Mijn Pakketten

![Een close-up van de Toolbox met het Creaties tabblad gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Creations-Group-Packages.png) Toolbox ⟩ Creaties ⟩ Groep Pakketten

Zodra je een pakket in het datamodel van een gepubliceerde plaats hebt ingevoegd, verschijnt het in de [Asset Manager](/docs/nl-nl/projects/assets/manager)  en blijft daar zelfs als je later alle kopieën ervan verwijdert.

Wees voorzichtig bij het invoegen van assets die je niet hebt gemaakt in je games, aangezien ze kwaadaardige scripts kunnen bevatten. Sla je spel eerst op en onderzoek vervolgens eventuele scripts binnen onbekende assets, zodat je gemakkelijk kunt terugkeren naar de plaatsversie.

## [Pakketten wijzigen](#pakketten-wijzigen)[](#pakketten-wijzigen)

Je kunt pakketten en hun kinderen bewerken zoals andere objecten. Het wijzigen van pakketten schakelt [auto-update](#automatische-updates)  uit totdat je de wijzigingen [publiceert](#publiceer-pakketwijzigingen)  of [herstelt](#herstel-pakketwijzigingen) .

De meeste bewerkingen markeren het pakket als gewijzigd, hoewel de volgende wijzigingen niet  als pakketwijzigingen worden beschouwd:

-

Het naam  van de rootnode wijzigen.

-

De positie  of rotatie  van de rootnode van een pakket dat een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , [Model](/docs/nl-nl/reference/engine/classes/Model) , of [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  is wijzigen.

-

De [Enabled](/docs/nl-nl/reference/engine/classes/LayerCollector#Enabled)  eigenschap van een rootnode [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  zoals een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui) , [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui) , of [BillboardGui](/docs/nl-nl/reference/engine/classes/BillboardGui)  wijzigen.

-

Een deelreferentie van een [Weld](/docs/nl-nl/reference/engine/classes/Weld)  binnen het pakket wijzigen die een instantie buiten het pakket verwijst.

Zodra gewijzigd, krijgen pakketten met niet-gepubliceerde wijzigingen een gewijzigd icoon in het [Explorer](/docs/nl-nl/studio/explorer)  venster:

 ![Het Explorer venster met een icoon dat niet-gepubliceerde pakketwijzigingen identificeert.](https://prod.docsiteassets.roblox.com/assets/studio/packages/Package-Modified.png)

### [Configuraties toevoegen of bijwerken](#configuraties-toevoegen-of-bijwerken)[](#configuraties-toevoegen-of-bijwerken)

Je kunt [instantiekenmerken](/docs/nl-nl/studio/properties#instantie-attributen)  aan de root van een pakket toevoegen om het gedrag ervan aan te passen. Wanneer je een pakket publiceert, wordt de huidige set van kenmerken/waarden de standaardconfiguraties  van het pakket. Op elke gegeven kopie  van een pakket kunnen die kenmerkwaarden per instantie worden gewijzigd, en die wijzigingen worden genoteerd door vet cursief . Wanneer pakketkopieën worden [geüpdatet](#update-verouderde-kopie%C3%ABn) , worden gewijzigde configuratiewaarden behouden, terwijl andere kenmerken worden bijgewerkt naar de nieuwste standaardwaarde.

 ![De sectie Kenmerken van het Eigenschappen venster met één kenmerkwaarde gewijzigd en genoteerd door vet cursief.](https://prod.docsiteassets.roblox.com/assets/studio/packages/Package-Configured-Attributes.png)

Momenteel is de enige manier om configuratiewaarden te beheren het toevoegen van scripts in het pakket die gedrag lezen en toepassen op basis van de configuratie tijdens runtime.

Als je eenvoudig de standaard waarden  voor configuraties wilt bijwerken, kun je die kenmerkwaarden wijzigen en het pakket opnieuw publiceren (het pakket zal in dit geval niet  als gewijzigd worden gemarkeerd). Als je andere wijzigingen wilt publiceren maar de standaard configuratiewaarden niet wilt wijzigen, moet je publiceren op een pakket zonder waarde wijzigingen, of de configuraties terugzetten naar hun standaardwaarden voordat je publiceert.

### [Geneste pakketten](#geneste-pakketten)[](#geneste-pakketten)

Je kunt pakketten binnen andere pakketten nestelen om complexe hiërarchieën te onderhouden en samen te werken, zoals een reeks voertuigmechanica die onafhankelijk van het bovenliggende pakket van het voertuig kunnen worden gewijzigd.

Als je een genest pakket wijzigt, worden zowel het geneste pakket als  het bovenliggende pakket als gewijzigd beschouwd. Je moet [wijzigingen publiceren](#publiceer-pakketwijzigingen)  naar elk genest  pakket voordat je wijzigingen naar het bovenliggende  pakket kunt publiceren, aangezien het publiceren van het bovenliggende pakket het als actueel/ongewijzigd zou markeren en in conflict zou komen met de wijzigingen van het geneste pakket.

### [Pakket scripts](#pakket-scripts)[](#pakket-scripts)

Elk script binnen een ongewijzigd  pakket is alleen-lezen en toont een melding bovenaan met een hyperlink om het script te ontgrendelen.

 ![Een script tabblad met een gele melding die je kunt klikken om het script te wijzigen dat zich binnen een ongewijzigd pakket bevindt.](https://prod.docsiteassets.roblox.com/assets/studio/packages/Script-Unlock-Link.png)

Als je op de hyperlink klikt:

-

Markeert het pakket als gewijzigd, ongeacht of je het script bewerkt.

-

Verwijdert de melding/hyperlink van andere  scripts binnen het pakket.

Zodra het pakket is gepubliceerd en naar een ongewijzigde  staat is verplaatst, worden de scripts eronder alleen-lezen met een hyperlink om te wijzigen.

## [Publiceer pakketwijzigingen](#publiceer-pakketwijzigingen)[](#publiceer-pakketwijzigingen)

Je kunt elke wijziging aan een pakket publiceren als een nieuwe versie, waardoor je updates beschikbaar maakt voor andere pakketkopieën in de plaats en in alle games. Het is niet  vereist om een gewijzigd pakket te publiceren voordat je een plaats publiceert, omdat de gewijzigde versie samen met de plaats wordt opgeslagen voor toekomstige iteratie.

Om wijzigingen aan een pakket te publiceren:

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster of 3D viewport, klik met de rechtermuisknop op de gewijzigde kopie en selecteer Publiceer naar Pakket .

2.

Als een pakketkopie [auto-update](#automatische-updates)  ingeschakeld heeft, haalt het onmiddellijk de bijgewerkte versie binnen wanneer je de plaats opent die ze bevat. Andere kopieën krijgen een "download" symbool dat aangeeft dat er een update beschikbaar is. Je kunt [individueel bijwerken](#update-verouderde-kopie%C3%ABn)  of [massaal bijwerken](#massale-updates)  alle kopieën.

 ![Iconen naast pakketten die een potentiële update hebben.](https://prod.docsiteassets.roblox.com/assets/studio/packages/Package-Update-Available.png)

3.

OPTIONEEL

 Voeg een beschrijving van je wijzigingen toe:

1.

Klik met de rechtermuisknop op het pakket en selecteer Pakketdetails .

2.

In het Asset Configuratie  venster, selecteer Versies .

3.

Onder je meest recente wijziging, selecteer Toevoegen .

4.

Beschrijf je wijzigingen en klik vervolgens op de Indienen  knop.

## [Update verouderde kopieën](#update-verouderde-kopieën)[](#update-verouderde-kopieën)

Je kunt verouderde pakketkopieën bijwerken naar de meest recente versie, of je kunt de oudere versie blijven gebruiken.

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, zoek verouderde kopieën aan de hand van het "download" symbool. Je kunt ook de verouderde kopie in de 3D viewport selecteren.

 ![Iconen naast pakketten die een potentiële update hebben.](https://prod.docsiteassets.roblox.com/assets/studio/packages/Package-Update-Available.png)

2.

Klik met de rechtermuisknop op een verouderde kopie en selecteer Krijg Laatste Pakket . Je kunt ook meerdere pakketten selecteren, met de rechtermuisknop klikken en Krijg Laatste Voor Geselecteerde Pakketten .

### [Massale updates](#massale-updates)[](#massale-updates)

Uitgebreid gebruik van pakketten kan resulteren in veel pakketkopieën over meerdere plaatsen in een game. Naast [individuele synchronisatie](#update-verouderde-kopie%C3%ABn)  en [automatische updates](#automatische-updates) , kun je alle kopieën van een pakket bijwerken via massale updates .

1.

AANBEVOLEN

 Sluit andere Studio-instanties met een van de game's plaatsen open; dit voorkomt dat een andere niet-opgeslagen instantie van een plaats mogelijk je updates overschrijft.

2.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster of 3D viewport, klik met de rechtermuisknop op het gewenste pakket en selecteer Update Alles .

3.

Kies alle plaatsen in de game of een subset van plaatsen en klik op Update .

Massale updates van pakketten slaat  de geselecteerde plaatsen automatisch op, maar publiceert ze niet. Bovendien, om onbedoelde overschrijvingen te voorkomen, heeft massaal bijwerken geen invloed op [gewijzigde](#pakketten-wijzigen)  versies van een pakket; nadat de massale update is voltooid, toont Studio een waarschuwing met het aantal pakketten dat het niet  heeft bijgewerkt, indien van toepassing.

### [Automatische updates](#automatische-updates)[](#automatische-updates)

Om synchronisatie gemakkelijker te maken, kun je een pakketkopie instellen om automatisch bij te werken telkens wanneer er een nieuwere versie wordt gepubliceerd. Auto-update van de pakketkopieën vindt plaats wanneer een plaats in Studio wordt geopend.

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, vouw de hiërarchiebomen van het pakket uit en selecteer het [PackageLink](/docs/nl-nl/reference/engine/classes/PackageLink)  object.

 ![Een close-up van een pakket in het Explorer venster met het PackageLink object gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/packages/PackageLink-Explorer.png)

2.

In het [Eigenschappen](/docs/nl-nl/studio/properties)  venster, schakel de [AutoUpdate](/docs/nl-nl/reference/engine/classes/PackageLink#AutoUpdate)  eigenschap in. Als je [geneste pakketten](#geneste-pakketten)  hebt, geldt deze eigenschap alleen voor het bovenste niveau bovenliggende pakket, wat betekent dat automatische updates alleen plaatsvinden wanneer het bovenliggende  pakket wordt bijgewerkt.

Automatische updates zijn niet van toepassing op [gewijzigde](#pakketten-wijzigen)  pakketkopieën. Zodra je een pakketinstantie wijzigt, wordt de AutoUpdate  eigenschap uitgeschakeld en genegeerd.

## [Delen en toegangslevels](#delen-en-toegangslevels)[](#delen-en-toegangslevels)

Je kunt toestemming geven aan vrienden, games, groepen of specifieke gebruikersrollen binnen een groep, zodat ze je pakketten vrijelijk kunnen gebruiken in hun creaties. Voor meer informatie over assettoegang, zie [Asset privacy](/docs/nl-nl/projects/assets/privacy) .

Als je een pakket deelt met beperkte assets waarvoor je geen [expliciete toestemming](/docs/nl-nl/projects/assets/privacy#bekijk-machtigingen)  hebt om te gebruiken, kun je het pakket nog steeds delen, maar die specifieke beperkte assets zullen niet  zichtbaar of hoorbaar zijn tijdens runtime, tenzij de vriend, game of groep toestemming heeft om die assets te gebruiken.

Aan samenwerkers Aan games

Om pakketrechten voor een samenwerker, zoals een vriend of groep, te wijzigen:

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, [Toolbox](/docs/nl-nl/projects/assets/toolbox) , of [Asset Manager](/docs/nl-nl/projects/assets/manager) , klik met de rechtermuisknop op het gewenste pakket en selecteer Pakketopties  ⟩ Pakketdetails .

2.

In het Asset Configuratie  venster, selecteer Rechten .

3.

Gebruik de zoekbalk, voer een samenwerker in die je toestemming wilt geven om je pakket te gebruiken, en kies vervolgens een toegangslevel.

| Toestemming | | Beschrijving |
| --- | --- |
| Gebruik & Bekijken | | De samenwerker kan de huidige en vorige pakketversies gebruiken en bekijken (maar niet bewerken). Zodra je een samenwerker deze mogelijkheid geeft, kun je de toegang tot een kopie die ze al in hun game hebben ingevoegd niet intrekken; het intrekken van toegang voorkomt herinvoeging of pakketupdates, maar pakketkopieën in hun datamodel blijven intact. |
| Bewerken | | De samenwerker kan de huidige en vorige pakketversies gebruiken, bekijken en bewerken, inclusief het publiceren van wijzigingen eraan. |

## [Herstel pakketwijzigingen](#herstel-pakketwijzigingen)[](#herstel-pakketwijzigingen)

In plaats van een hele reeks pakketwijzigingen één voor één ongedaan te maken, kun je [niet-gepubliceerde wijzigingen](#ongedaan-maken-van-niet-gepubliceerde-wijzigingen)  in één actie terugdraaien, een pakket herstellen naar een eerdere [versie](#herstel-naar-gepubliceerde-versie) , of wijzigingen aan specifieke [configuraties](#herstel-configuraties)  terugdraaien.

### [Ongedaan maken van niet-gepubliceerde wijzigingen](#ongedaan-maken-van-niet-gepubliceerde-wijzigingen)[](#ongedaan-maken-van-niet-gepubliceerde-wijzigingen)

Om een hele reeks niet-gepubliceerde  wijzigingen ongedaan te maken:

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, zoek gewijzigde kopieën aan de stip op hun pakketiconen. Je kunt ook gewijzigde kopieën in de 3D viewport selecteren.

 ![Het Explorer venster met een icoon dat niet-gepubliceerde pakketwijzigingen identificeert.](https://prod.docsiteassets.roblox.com/assets/studio/packages/Package-Modified.png)

2.

Klik met de rechtermuisknop op een enkele gewijzigde kopie en selecteer Wijzigingen ongedaan maken voor Pakket , of selecteer meerdere kopieën (minstens één daarvan gewijzigd), klik met de rechtermuisknop en selecteer Wijzigingen ongedaan maken voor Geselecteerde Pakketten .

### [Herstel naar gepubliceerde versie](#herstel-naar-gepubliceerde-versie)[](#herstel-naar-gepubliceerde-versie)

Om een pakket te herstellen naar een eerder gepubliceerde  versie:

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, [Toolbox](/docs/nl-nl/projects/assets/toolbox) , of [Asset Manager](/docs/nl-nl/projects/assets/manager) , klik met de rechtermuisknop op het gewenste pakket en selecteer Pakketopties  ⟩ Pakketdetails .

2.

In het Asset Configuratie  venster, selecteer Versies . Het venster toont details voor elke gepubliceerde versie, inclusief de datum en tijd van publicatie, samen met eventuele beschrijvingen van de wijzigingen.

3.

Klik op het vinkje naast de versie die je wilt herstellen en klik op Indienen .

Het terugdraaien van wijzigingen aan een pakket reset de configuratie niet naar de standaard. Zie [herstel configuraties](#herstel-configuraties) .

### [Herstel configuraties](#herstel-configuraties)[](#herstel-configuraties)

Om een [configuratie](#configuraties-toevoegen-of-bijwerken)  kenmerk naar zijn standaard terug te zetten, selecteer Reset  in het optiesmenu in de Kenmerken  sectie van het [Eigenschappen](/docs/nl-nl/studio/properties)  venster.

 ![De Kenmerken sectie van het Eigenschappen venster met het optiesmenu van het kenmerk uitgebreid.](https://prod.docsiteassets.roblox.com/assets/studio/packages/Package-Configured-Attributes-Reset.png)

## [Vergelijk pakketversies](#vergelijk-pakketversies)[](#vergelijk-pakketversies)

Wanneer een pakket meerdere versies heeft, kun je wijzigingen tussen versies vergelijken met behulp van de diff viewer. De tool heeft een pakket hiërarchiemenu dat alle toegevoegde, verwijderde of gewijzigde instanties tussen versies aangeeft met bijbehorende iconen, inclusief de volgende functies:

-

Visueel Overzicht  toont de visuele verschillen van de 3D-rendering onder verschillende cameraposities. Het is de standaardweergave voor pakketten met een 3D-object (modellen, delen) als het rootobject, en het is momenteel alleen beschikbaar voor het rootobject.

-

Eigenschappen  toont wijzigingen van eigenschappen en kenmerken. Het is de standaardweergave voor pakketten met een niet-3D-object (scripts, lichten, 2D-objecten) als het rootobject, en het is beschikbaar voor alle instanties in een pakket.

-

Script  toont regel-voor-regel scriptverschillen. Het is beschikbaar voor pakketten die scripts bevatten, ongeacht of het script het rootobject is of niet.

Om pakketversies te vergelijken:

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  of 3D viewport, klik met de rechtermuisknop op het doelpakket en selecteer Pakketopties  ⟩ Vergelijk Pakketversies .

2.

Standaard vergelijkt het venster wijzigingen tussen je lokale kopie en de nieuwste versie. Gebruik de twee dropdownmenu's om verschillende versies te vergelijken.

 ![Een close-up van een voorbeeld diff viewer. De vergelijkinstellingen zijn gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/packages/Compare-Versions-Selector.png)

Sommige oudere versies zijn mogelijk niet compatibel met de pakket diff-tool.

3.

Nadat je versies hebt geselecteerd:

1.

Om de visuele weergaven van het rootmodel te vergelijken, indien van toepassing, selecteer het tabblad Visueel Overzicht  en pas de camerabesturing aan voor de gewenste hoek. Besturingselementen zijn gesynchroniseerd over weergaven:

-

Pan de camera met de linkermuisklik.

-

Draai de camera met de rechtermuisklik.

-

Zoom in en uit met het muiswiel.

-

Hercenter met de sneltoets F .

2.

Om eigenschappen en kenmerken van een instantie te vergelijken, selecteer de instantie en het tabblad Eigenschappen .

3.

Om scriptverschillen voor een pakket dat een script is of scripts bevat te vergelijken, gebruik het tabblad Script .

Deze tool staat alleen toe om scriptwijzigingen tussen de huidige versie en de nieuwste gepubliceerde of lokale versie te vergelijken, zonder de samenwerkers die de wijziging hebben aangebracht aan te geven.

Alternatief kun je de script diff-tool rechtstreeks openen door met de rechtermuisknop op het doelpakket in het [Explorer](/docs/nl-nl/studio/explorer)  venster of 3D viewport te klikken en Bekijk Scriptwijzigingen  te selecteren.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
