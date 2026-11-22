<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/character-bodies/specifications -->

Specificaties voor het lichaam van een karakter | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Lichamen

# Specificaties voor het lichaam van een karakter

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Modellen van karakterlichamen vereisen een specifieke set componenten en configuratiestandaarden om ervoor te zorgen dat alle avatarfuncties naar verwachting werken op het platform. Voordat je begint met het exportproces, controleer of je model voldoet aan de volgende modellingsspecificaties en richtlijnen voor een goede Studio-compatibiliteit.

Wanneer je klaar bent om je karakterlichaam te exporteren, raadpleeg dan alle [vereisten voor exportinstellingen](/docs/nl-nl/avatar/character-bodies/export)  voor Blender en Maya.

Voor andere soorten 3D-modellen:

-

[Algemene mesh](/docs/nl-nl/art/modeling/specifications)  specificaties.

-

[Stijve accessoire](/docs/nl-nl/avatar/rigid-accessories/specifications)  specificaties.

-

[Gelaagde accessoire](/docs/nl-nl/avatar/layered-accessories/specifications)  specificaties.

## [Geometrie](#geometrie)[](#geometrie)

Modellen van karakterlichamen voor avatars bestaan uit 15 afzonderlijke mesh-objecten en vereisen aanvullende geometrievereisten om succesvol in Studio te importeren en te publiceren. Naast de specificaties voor [lichaamschaaltypes](#lichaamschaal) , [lichaamsdelen](#lichaamsdelen)  en [driehoekbudgetten](#driehoekbudgetten) , zorg ervoor dat je modellen ook voldoen aan de volgende algemene vereisten bij het modelleren van het lichaam van je karakter:

-

Waterdicht  - Alle geometrie moet waterdicht zijn zonder blootgestelde gaten of achterkanten. Meshes die als buitenste omhulsels worden gebruikt, hoeven niet waterdicht te zijn.

-

Geen N-gons  - Model je activa in quads waar mogelijk.

-

Transformaties  - Alle translatie-, rotatie- en schaalwaarden moeten bevroren zijn en de pivots moeten zijn ingesteld op 0 , 0 , 0 .

-

Oriëntatie  - Karakters moeten naar positieve Z gericht zijn en rechtop staan in positieve Y.

-

Pose  - Stel je karakter in op een I-Pose, A-Pose of T-Pose wanneer mogelijk voordat je exporteert.

### [Lichaamschaal](#lichaamschaal)[](#lichaamschaal)

Roblox ondersteunt drie standaarden voor de lichaamschalen van karakters: Normaal , Slank  en Klassiek . Deze standaarden stellen ontwikkelaars in staat om games en ruimtes te creëren met consistente lichaamsgroottes voor het standaardiseren van beweging en interacties. Je kunt een lichaamschaal selecteren bij het importeren met behulp van [Rig Scale-opties](/docs/nl-nl/studio/importer#algemeen-rig) , of de [lichaamschaal handmatig aanpassen](/docs/nl-nl/avatar/rigid-accessories/specifications#avatarpartscaletype) . De lichaamschaal blijft bestaan wanneer het activum [wordt geüpload naar de Marketplace](/docs/nl-nl/marketplace/publish-to-marketplace#upload-een-activum) .

![](https://prod.docsiteassets.roblox.com/assets/art/Body-Scale-Diagram.png)

Een visualisatie van hoe Roblox de 15 lichaamsdelen combineert tot 6 verschillende activa.

Aangezien lichaamsactiva gedeeltelijk met elkaar overlappen, vertegenwoordigen de totale lichaamsafmetingen niet de som van de afmetingen van de avataractiva. De totale lichaamsafmeting is de belangrijkste factor om een standaard avatarformaat en -schaal te waarborgen.

Dezelfde begrenzingsdozenlimieten zijn van toepassing op de Normale, Slanke en Klassieke lichaamschalen. Tijdens de validatie roteert Roblox elke ledemaat naar een standaardoriëntatie. De validator meet de lengte van het geroteerde deel en berekent de breedte en diepte op basis van de dwarsdoorsnede van het deel.

#### [Begrenzingsdozenlimieten](#begrenzingsdozenlimieten)[](#begrenzingsdozenlimieten)

Minimaal (in studs)

| Deel | | Breedte | | Lengte | | Diepte |
| --- | --- |
| Hoofd | | 0.05 | | 0.5 | | 0.05 |
| Arm | | 0.05 | | 0.5 | | 0.05 |
| Torso | | 0.05 | | 0.65 | | 0.05 |
| Been | | 0.05 | | 0.5 | | 0.05 |
| Totaal | | 1.0 | | 4.0 | | 0.5 |

Maximaal (in studs)

| Deel | | Breedte | | Lengte | | Diepte |
| Hoofd | | 4.0 | | 2.0 | | 4.0 |
| Arm | | 4.0 | | 4.5 | | 4.0 |
| Torso | | 4.0 | | 4.0 | | 4.0 |
| Been | | 4.0 | | 4.5 | | 4.0 |
| Totaal | | 8.0 | | 10.0 | | 4.0 |

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Body-Scale-Rthro-Normal.png)

Normaal
Een Rthro Normaal lichaamschaal [downloadbaar mannequin](/docs/nl-nl/avatar/resources#referenties) .
In de [Importer](/docs/nl-nl/studio/importer#avatar-general) , gebruik Rig Type  > Rthro  om je model als een Normaal lichaamschaal te importeren.

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Body-Scale-Rthro-Slender.png)

Slank
Een Rthro Slank (Smalle) lichaamschaal [downloadbaar mannequin](/docs/nl-nl/avatar/resources#referenties) .
In de [Importer](/docs/nl-nl/studio/importer#avatar-general) , gebruik Rig Type  > Rthro Smal  om je model als een Slank lichaamschaal te importeren.

![](https://prod.docsiteassets.roblox.com/assets/art/resources/Body-Scale-Classic.png)

Klassiek
Een Klassieke lichaamschaal [downloadbaar mannequin](/docs/nl-nl/avatar/resources#referenties) .
In de [Importer](/docs/nl-nl/studio/importer#avatar-general) , gebruik Rig Type  > Standaard  om je model als een Klassieke lichaamschaal te importeren.

### [Driehoekbudgetten](#driehoekbudgetten)[](#driehoekbudgetten)

Hoewel geometrieën van modellen van karakterlichamen doorgaans worden gemaakt met quads, converteert de Roblox-engine geïmporteerde activa naar tris. Elk activum van je karaktermodel mag ons maximale driehoekbudget niet overschrijden. Om snel het aantal verwachte tris in je externe modelleringstoepassing te krijgen, kun je het aantal quads in je model verdubbelen.

Wanneer modellen van karakterlichamen naar Studio worden geüpload en worden omgezet in activa voor de Marketplace, wordt het lichaam opgesplitst in 6 afzonderlijke activa: DynamicHead , Torso , LeftArm , RightArm , LeftLeg , RightLeg .

| Activumtype | | Inbegrepen mesh-objecten | | Maximale driehoeken |
| DynamicHead | | Hoofd | | 4000 |
| Torso | | BovensteTorso, OndersteTorso | | 1750 |
| LinkerArm | | LinkerBovenarm, LinkerOnderarm, LinkerHand | | 1248 |
| RechterArm | | RechterBovenarm, RechterOnderarm, RechterHand | | 1248 |
| LinkerBeen | | LinkerBovenbeen, LinkerOnderbeen, LinkerVoet | | 1248 |
| RechterBeen | | RechterBovenbeen, RechterOnderbeen, RechterVoet | | 1248 |
| Totaal | | Hoofd, BovensteTorso, OndersteTorso, LinkerBovenarm, LinkerOnderarm, LinkerHand, RechterBovenarm, RechterOnderarm, RechterHand, LinkerBovenbeen, LinkerOnderbeen, LinkerVoet, RechterBovenbeen, RechterOnderbeen, RechterVoet | | 10.742 |

### [Lichaamsdelen](#lichaamsdelen)[](#lichaamsdelen)

Zie de volgende specificaties voor de individuele mesh-objecten die een model van een karakterlichaam vormen:

-

Naamgevingsconventie  - Ledematen moeten allemaal specifiek worden genoemd:

-

BovensteTorso_Geo

-

OndersteTorso_Geo

-

LinkerBovenarm_Geo

-

LinkerOnderarm_Geo

-

LinkerHand_Geo

-

RechterBovenarm_Geo

-

RechterOnderarm_Geo

-

RechterHand_Geo

-

LinkerBovenbeen_Geo

-

LinkerOnderbeen_Geo

-

LinkerVoet_Geo

-

RechterBovenbeen_Geo

-

RechterOnderbeen_Geo

-

RechterVoet_Geo

-

Hoofd_Geo

-

Kappen  - Ledematen moeten zijn afgedekt, zodat ze een volledige waterdichte mesh vormen wanneer ze van het lichaam zijn gescheiden. Kappen kunnen rond of plat zijn, afhankelijk van het ontwerp.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Modeling-Requirements-Caps.png)

Geïnteresseerd in het maken van een avatar met hogere precisie?

Karakterlichaam modellen met hogere precisie vereisen dezelfde 15 mesh-objecten en naamstructuur. Het enige verschil is dat de mesh-objecten in modellen van karakterlichamen met hogere precisie [extra interne gewrichten](#geavanceerde-r15-rigs)  in hun rigging-structuren kunnen hebben. Wanneer deze gewrichten aanwezig zijn in een model van een karakterlichaam, moeten de bijbehorende mesh-objecten [gekleed](#skinning)  worden voor nauwkeurige vervorming.

### [Gezichtsaccessoires](#gezichtsaccessoires)[](#gezichtsaccessoires)

Gezichtsaccessoires, zoals wenkbrauwen en wimpers, zijn unieke gelaagde accessoires die je kunt bundelen met een upload van een avatar karakterlichaam. Wenkbrauwen en wimpers kunnen niet als zelfstandige accessoires worden geüpload en moeten worden gebundeld met een karakterlichaam of [make-up activa](/docs/nl-nl/avatar/makeup/specifications) . Voor meer informatie over gezichtsaccessoires, zie [Specificaties voor gelaagde accessoires - Gezichtsaccessoires](/docs/nl-nl/avatar/layered-accessories/specifications#gezichtsaccessoires) .

### [Zichtbaarheid](#zichtbaarheid)[](#zichtbaarheid)

Om ervoor te zorgen dat de afmetingen van avatars visueel consistent zijn, moet je de zichtbaarheid van lichaamsdelen standaardiseren met de volgende vereisten:

-

Opaciteit  - Lichaamsdelen moeten volledig ondoorzichtig zijn.

-

Begrenzingsdozen  - Activa van lichaamsdelen moeten een aanzienlijk zichtbaar deel van hun begrenzingsdoos innemen in een vooraanzicht, zijaanzicht en achteraanzicht.

-

Lichaamsdelen, zoals Torso, Linker Arm, Rechter Been, moeten minstens 50% van de begrenzingsdoos van het lichaamsdeel innemen.

-

Het hoofddeel moet minstens 50% van de begrenzingsdoos van de mesh innemen.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Valid-Visibility.png) Een acceptabel voorbeeld van een hoofdmesh die de meerderheid van de begrenzingsdoos in het vooraanzicht inneemt

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Invalid-Visibility.png) Een niet-acceptabel voorbeeld van een hoofdmesh die niet de juiste hoeveelheid ruimte in de begrenzingsdoos in het vooraanzicht inneemt

## [Bevestigingen](#bevestigingen)[](#bevestigingen)

Bevestigingen zijn punten die de specifieke locatie bepalen waar accessoires en in-game te dragen objecten aan het lichaam van het karakter worden bevestigd. Net als veel [karaktercomponenten](/docs/nl-nl/avatar/character-bodies#componenten-van-het-lichaamsmodel) , worden bevestigingspunten ingesteld in externe modelleringsoftware en geïmporteerd als [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten.

De Importer herkent en converteert mesh-objecten automatisch als bevestigingspunten als de objecten de affix \_Att  bevatten en voldoen aan de onderstaande naamgevingsconventies. Dit geldt alleen bij het importeren van meshes met omhulselgegevens, zoals lichamen (bevestigingspunten voor accessoires worden gemaakt met de Accessory Fitting Tool). Bekijk voorbeelden van deze implementatie in een van Roblox's [downloadbare referentiemodellen](/docs/nl-nl/avatar/resources#referenties) .

Over het algemeen, wanneer je bevestigingspunten plaatst, positioneer ze zodat ze halverwege overlappen met het mesh-deel van het karaktermodel.

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Collar-Attachment-1.png) Onjuiste plaatsing van kraagbevestigingen

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Collar-Attachment-2.png) Correcte plaatsing van kraagbevestigingen

Voor accessoires die aan het hoofd zijn bevestigd, positioneer het bevestigingspunt zodat het op het zichtbare oppervlak van de hoofdmesh past. Bevestigingspunten die van het zichtbare hoofd afdrijven, schenden de [Marketplace-beleid](/docs/nl-nl/marketplace/marketplace-policy#algemene-richtlijnen-voor-creatie) .

![](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/Correct-Head-Attachment.png) Correcte plaatsing van hoofdbevestigingen

![](https://prod.docsiteassets.roblox.com/assets/avatar/character-bodies/Incorrect-Head-Attachment.png) Onjuiste plaatsing van hoofdbevestigingen

Bevestigingen moeten voldoen aan een specifieke naamgevingsconventie en positionele consistentie:

| Mesh-deel | | Bevestigingsnaam | | Details |
| Hoofd | | FaceCenter_Att | | Waar dan ook binnen de mesh-begrenzingsdoos |
| FaceFront_Att | | Voorkant van de mesh-begrenzingsdoos |
| Hat_Att | | Bovenste helft van de mesh-begrenzingsdoos, kan overlappen met Hair_Att |
| Hair_Att | | Bovenste helft van de mesh-begrenzingsdoos, kan overlappen met Hat_Att |
| BovensteTorso | | LeftCollar_Att | | Linker bovenste helft van de mesh-begrenzingsdoos |
| RightCollar_Att | | Rechter bovenste helft van de mesh-begrenzingsdoos |
| Neck_Att | | Bovenste helft van de mesh-begrenzingsdoos |
| BodyBack_Att | | Achterste helft van de mesh-begrenzingsdoos |
| BodyFront_Att | | Voorkant van de mesh-begrenzingsdoos |
| OndersteTorso | | Root_Att | | Moet ingesteld zijn op 0 , 0 , 0  positie |
| WaistFront_Att | | Voorkant van de mesh-begrenzingsdoos, kan overlappen met WaistCenter_Att |
| WaistBack_Att | | Achterkant van de mesh-begrenzingsdoos |
| WaistCenter_Att | | Waar dan ook in de mesh-begrenzingsdoos, kan overlappen met WaistFront_Att |
| RechterBovenarm | | RightShoulder_Att | | Bovenste helft van de mesh-begrenzingsdoos |
| RechterHand | | RightGrip_Att | | Waar dan ook in de mesh-begrenzingsdoos.
Oriënteer gripbevestigingen loodrecht  op het onderarmbeen. Bijvoorbeeld, voor I-Pose (armen naar beneden), stel de gripbevestiging in op 90 , 0 , 0  (gripbevestiging wijst naar voren).
![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Grip-Attachments-Right.png) |
| LinkerBovenarm | | LeftShoulder_Att | | Bovenste helft van de mesh-begrenzingsdoos |
| LinkerHand | | LeftGrip_Att | | Waar dan ook in de mesh-begrenzingsdoos.
Oriënteer gripbevestigingen loodrecht  op het onderarmbeen. Bijvoorbeeld, voor I-Pose (armen naar beneden), stel de gripbevestiging in op 90 , 0 , 0  (gripbevestiging wijst naar voren).
![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Grip-Attachments-Left.png) |
| RechterVoet | | RightFoot_Att | | Waar dan ook in de mesh-begrenzingsdoos |
| LinkerVoet | | LeftFoot_Att | | Waar dan ook in de mesh-begrenzingsdoos |

## [Rigging](#rigging)[](#rigging)

In tegenstelling tot generieke rigs, vereisen humanoïde modellen een specifieke hiërarchie en naamgevingsconventies voor de interne bot- of gewrichtstructuur.

![](https://prod.docsiteassets.roblox.com/assets/animation/importing-custom-3d-rigs/Birdcaller-Imported.jpeg) Humanoïde rig-model

![](https://prod.docsiteassets.roblox.com/assets/animation/importing-custom-3d-rigs/Rig-Hierarchy-Birdcaller-Blender-Bones.png) Humanoïde rig-botstructuur (Blender)

### [Standaard R15 rigs](#standaard-r15-rigs)[](#standaard-r15-rigs)

De volgende vereisten zijn voor standaard R15  rigs.

-

Rig-hiërarchie  - Humanoïde rigs vereisen een specifieke bot- of gewricht-hiërarchie en naamgevingsconventie:

-

Root

-

HumanoidRootNode

-

OndersteTorso

-

BovensteTorso

-

Hoofd (vertegenwoordigt de basis van de nek)

-

LinkerBovenarm

-

LinkerOnderarm

-

LinkerHand

-

RechterBovenarm

-

RechterOnderarm

-

RechterHand

-

LinkerBovenbeen

-

LinkerOnderbeen

-

LinkerVoet

-

RechterBovenbeen

-

RechterOnderbeen

-

RechterVoet

Blender standaard humanoïde rig-hiërarchie met alle botten

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Rig-Hierarchy-Blender.png)

Maya standaard humanoïde rig-hiërarchie met alle gewrichten

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/Rig-Hierarchy-Maya.png)

-

OndersteTorso en Root  - De positie van de OndersteTorso en Root-bot of gewricht moet worden ingesteld op 0 , 0 , 0 .

-

Pose  - Exporteer je karaktermodel in een I-Pose, A-Pose of T-Pose voor de beste Studio-compatibiliteit. De LinkerBovenarm en RechterBovenarm-botten kunnen worden geëxporteerd met rotatiewaarden om aan deze vereiste te voldoen.

### [Geavanceerde R15 rigs](#geavanceerde-r15-rigs)[](#geavanceerde-r15-rigs)

Geavanceerde R15  rigs hebben dezelfde vereisten als standaard rigs, maar ze ondersteunen tot 37 extra optionele botten of gewrichten voor een hoger niveau van realisme met gearticuleerde handen, schouders en ruggengraatbewegingen.

Je hoeft niet elk optioneel bot of gewricht voor een geavanceerde R15 rig op te nemen, maar elk optioneel bot of gewricht dat je opneemt, moet voldoen aan een specifieke hiërarchie en naamgevingsconventie voor het respectieve lichaamsdeel.

Torso LinkerHand RechterHand LinkerVoet RechterVoet

| Hiërarchie | | Voorbeeld Rig Setup |
|
-

BovensteTorso
-

Ruggengraat
-

Borst
-

Hoofd
-

HoofdBasis

-

RechterClavicula
-

RechterBovenarm

-

LinkerClavicula
-

LinkerBovenarm

 | | ![](https://prod.docsiteassets.roblox.com/assets/avatar/specifications/High-Fidelity-Torso.png) |

Blender humanoïde rig-hiërarchie met alle optionele botten

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/R15Plus-Rig-Hierarchy-Blender.png)

Maya humanoïde rig-hiërarchie met alle optionele gewrichten

![](https://prod.docsiteassets.roblox.com/assets/modeling/skinned-meshes/R15Plus-Rig-Hierarchy-Maya.png)

Zorg ervoor dat je elk extra bot of gewrichts bijbehorende mesh-object voor nauwkeurige vervorming kleedt.

Nadat je een [geavanceerde R15 karakter rig](/docs/nl-nl/avatar/character-bodies/import)  in Studio hebt geïmporteerd, moet je [HumanoidRigDescription](/docs/nl-nl/reference/engine/classes/HumanoidRigDescription)  en/of [DigitsRigDescription](/docs/nl-nl/reference/engine/classes/DigitsRigDescription)  objecten in je rig invoegen om je karakter op de Marketplace te kunnen verkopen, en zodat je animaties goed werken:

-

[HumanoidRigDescription](/docs/nl-nl/reference/engine/classes/HumanoidRigDescription)  objecten zijn noodzakelijk voor het animeren van individuele lichaamsdelen en het aanpassen van gedragskenmerken van de rig, zoals de grootte en bewegingsbereik van elk bot of gewricht.

-

[DigitsRigDescription](/docs/nl-nl/reference/engine/classes/DigitsRigDescription)  objecten zijn noodzakelijk voor handarticulatie. Je karakter heeft er één nodig voor elke hand met optionele botten of gewrichten.

Beide objecttypen detecteren botten of gewrichten op basis van hun naamgevingsconventies, dus het is erg belangrijk om ervoor te zorgen dat elk optioneel bot of gewricht correct is genoemd volgens de bovenstaande tabel voordat  je je karakter rig in Studio importeert. Voor een set geavanceerde R15 rigs die je kunt raadplegen, zie [Hulpmiddelen - Geavanceerde R15 rigs](/docs/nl-nl/avatar/resources#geavanceerde-r15-rigs) .

## [Skinning](#skinning)[](#skinning)

Roblox ondersteunt skinning voor gerigde meshes. Voor meer details over het implementeren van geklede meshes in Studio, zie [Rigging en Skinning](/docs/nl-nl/art/modeling/rigging) .

De volgende vereisten zijn voor het skinnen van karakterlichamen:

-

Max Invloeden  - Een vertex kan niet door meer dan 4 botten of gewrichten worden beïnvloed.

-

Geen Root-invloeden  - Pas geen invloeden toe op het Root-bot of gewricht.

-

Symmetrie  - Behoud waar mogelijk symmetrie bij het toepassen van invloeden op een rig.

## [Gezichtsanimatie](#gezichtsanimatie)[](#gezichtsanimatie)

Voor informatie over vereiste ondersteuning voor gezichtsanimatie, zie [hoofd specificaties](/docs/nl-nl/avatar/dynamic-heads/specifications#facs-poses) .

## [Texturen](#texturen)[](#texturen)

-

Texturen voor Marketplace-activa mogen niet groter zijn dan 2048x2048 resolutie.

-

Texturen die zijn gemaakt voor accessoires moeten voldoen aan Roblox's [textuurspecificaties](/docs/nl-nl/art/modeling/texture-specifications) . Hoge resolutietexturen worden automatisch omgezet naar lagere resolutietexturen om de prestaties te optimaliseren.

-

Avatar-karakters moeten voldoen aan Roblox's [textuurspecificaties](/docs/nl-nl/art/modeling/texture-specifications) . Karakters die zijn gemaakt voor de Marketplace kunnen profiteren van [aangepaste huidtinten](#aangepaste-huidtint) , die alfalagen gebruiken om gebruikers in staat te stellen hun eigen basiskleur te selecteren.

### [Aangepaste huidtint](#aangepaste-huidtint)[](#aangepaste-huidtint)

Bij het textureren van een avatar karakterlichaam model waar de gebruiker zijn eigen huidtint kan instellen, stel je de blootgestelde huidgebieden in als transparant zodat een standaardkleur of -textuur niet in de textuur is gebakken. Bij het renderen past Studio de transparante laag bovenop toe zonder enige laag effecten. Deze stap geldt voornamelijk voor mensachtige karakters met blootgestelde huid die je wilt dat gebruikers aanpassen.

De volgende zijn voorbeelden van huidtint schaduw voor het gezicht, en je kunt dit proces toepassen op elk deel van een avatar met blootgestelde huid:

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/mesh-requirements/Face-Tone-Transparent.png)

-

Gebruik 100% opaciteit voor gebieden die niet gerelateerd zijn aan een aangepaste huidtint, zoals ogen en wenkbrauwen.

-

Bij het toepassen van schaduw, gebruik zwart met een lage opaciteit en pas de opaciteit aan wanneer nodig.

-

Voor gebieden die gedeeltelijk doorschijnend zijn, zoals schaduwcontouren of bepaalde cosmetische kenmerken, laat wat transparantie voor gedeeltelijke zichtbaarheid van de huidtint.

-

Je moet consistent testen hoe verschillende kleurenlagen kunnen interageren met je schaduw.

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/mesh-requirements/Face-Tone-Beige.png) Beige

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/mesh-requirements/Face-Tone-Blue.png) Blauw

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/mesh-requirements/Face-Tone-Brown.png) Bruin

![](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/mesh-requirements/Face-Tone-Pink.png) Roze

## [Buitenste omhulsels](#buitenste-omhulsels)[](#buitenste-omhulsels)

Buitenste omhulsels op je karaktermodel stellen je karakter in staat om gelaagde accessoires te dragen, zoals shirts en jassen die zich om het lichaam rekken en wikkelen. Bekijk de volgende lijst voor vereisten voor het toevoegen van buitenste omhulsel-meshes aan je karakterlichaam model:

-

Gebruik Roblox's [Avatar Setup](/docs/nl-nl/avatar-setup)  of Roblox's [lichaam omhulsel sjablonen](/docs/nl-nl/avatar/resources#projectbestanden)  om ervoor te zorgen dat naamgevingsconventies en andere configuraties correct zijn.

-

Naamgevingsconventies  - De buitenste omhulsel van een lichaamsdeel moet worden genoemd naar het primaire mesh-object met _OuterCage  toegevoegd, bijvoorbeeld LinkerBovenarm_OuterCage .

-

Vertices en UV-kaart  - Verwijder geen vertices of wijzig de UV's op buitenste omhulsels, aangezien dit fouten kan veroorzaken bij het importeren in Studio of bij het uitrusten op een karakter. Gebruik de door Roblox geleverde sjablonen voor omhulsel-meshes om compatibiliteit met andere gelaagde activa te waarborgen.

-

Symmetrie en consistentie  - Houd elke zijde van je geometrie consistent van grootte en behoud symmetrie waar mogelijk door symmetrie-tools in je modelleringsoftware te gebruiken.

-

Voor informatie over dynamische hoofdomhulsels en beste praktijken bij het omhulsen, zie [Dynamische hoofd specificaties](/docs/nl-nl/avatar/dynamic-heads/specifications#buitenkant-kooi) .

Karakterlichamen vereisen alleen een buitenste omhulsel, maar gelaagde accessoires vereisen zowel een binnen- als een buitenomhulsel om goed te vervormen. Voor meer informatie, zie [Specificaties voor gelaagde accessoires - Omhulsel-meshes](/docs/nl-nl/avatar/layered-accessories/specifications#cage-meshes) .

## [Marketplace-vereisten](#marketplace-vereisten)[](#marketplace-vereisten)

Naast de andere technische vereisten die zijn opgesomd, moeten je items voldoen aan de volgende aanvullende specificaties voordat je ze naar de Marketplace uploadt om te verkopen:

-

Zorg ervoor dat je karakterlichamen voldoen aan de [Marketplace-beleid](/docs/nl-nl/marketplace/marketplace-policy) .

-

Zorg ervoor dat je karakterlichamen voldoen aan Roblox's [aangepaste mesh specificaties](/docs/nl-nl/art/modeling/specifications)  waar van toepassing.

-

Object [Material](/docs/nl-nl/reference/engine/classes/MeshPart#Material)  is ingesteld op Plastic .

-

Object [Transparency](/docs/nl-nl/reference/engine/classes/MeshPart#Transparency)  is ingesteld op 0 .

-

Object [VertexColor](/docs/nl-nl/reference/engine/classes/MeshPart#VertexColor)  is de standaard 1, 1, 1 .

-

Als het hoofd van je karakter aparte wimpers en wenkbrauwactiva bevat, moet je ze toevoegen aan je karakterlichaam model als [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  objecten. Voor meer informatie, zie [Publiceer lichamen met wimpers en wenkbrauwen](/docs/nl-nl/art/accessories/publish-eyebrows-eyelashes) .

-

Je [Model](/docs/nl-nl/reference/engine/classes/Model)  instantie bevat geen overbodige objecten, zoals [Script](/docs/nl-nl/reference/engine/classes/Script)  of extra [Part](/docs/nl-nl/reference/engine/classes/Part)  instanties.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
