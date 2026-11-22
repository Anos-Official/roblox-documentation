<!-- Source: https://create.roblox.com/docs/nl-nl/avatar -->

Avatar, een systeem van expressie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)

# Avatar, een systeem van expressie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Elke Roblox-gebruiker wordt vertegenwoordigd door een avatar  — een volledig aanpasbaar 3D-personage met cosmetica, kleding en accessoires die persistent zijn in verschillende games op het platform. In wezen zijn avatars diep persoonlijk omdat ze iemands digitale identiteit symboliseren, uniek vormgegeven door individuele aankopen op de [Marketplace](https://www.roblox.com/catalog)  of in games, of door giveaways.

Elke avatar is een systeem van componenten die samenwerken om een personage te creëren dat kan interageren met objecten in de 3D-ruimte en cosmetica, kleding en accessoires kan dragen. In grote lijnen kun je deze componenten scheiden in die welke wie je bent  en wat je draagt . Laten we het opsplitsen.

## [Wie je bent](#wie-je-bent)[](#wie-je-bent)

Er zijn vier hoofdlagen van het avatarlichaam die bepalen hoe het personage eruitziet en beweegt op het platform:

[Geometrie](#geometry)
Het visuele uiterlijk van de avatar.

[Rigging armatuur](#rigging-armature)
Hoe de avatar beweegt.

[Animaties](#animations)
Hoe de avatar zijn of haar persoonlijkheid uitdrukt.

[Bevestigingspunten en cage meshes](#attachment-points-and-cage-meshes)
Hoe de avatar accessoires bevestigt en kleding draagt.

Hoewel je elke van deze lagen handmatig kunt maken, hebben sommige strikte configuratievereisten om te voldoen aan de technische [karakter specificaties](/docs/nl-nl/avatar/character-bodies/specifications)  van Roblox die garanderen dat je avatar consistent functioneert van game tot game. Om je creatieve proces te ondersteunen en ervoor te zorgen dat je avatars aan deze specificaties voldoen, biedt Roblox het volgende:

-

[Avatar Setup](/docs/nl-nl/avatar-setup)  - Verwerkt automatisch 3D aangepaste activa in avataractiva met alle essentiële componenten voor publicatie op de Marketplace.

-

[Avatar referenties](/docs/nl-nl/avatar/resources#referenties)  met geometrie en rigging armaturen.

-

[Projectbestanden](/docs/nl-nl/avatar/resources#projectbestanden)  voor basis rigs, bevestigingspunten en cage meshes die je kunt gebruiken in externe modelleringsoftware.

-

[Mannequins](/docs/nl-nl/avatar/resources#mannequin-modellen)  die je kunt gebruiken als maatreferentie.

-

[Aanpasbare karaktertemplates](/docs/nl-nl/avatar/resources#sjablonen)  met voorgebakken avatarcomponenten.

### [Geometrie](#geometrie)[](#geometrie)

De [fysieke lichaams](/docs/nl-nl/avatar/character-bodies)  geometrie van de avatar bestaat uit 15 afzonderlijke mesh-lichaamsdelen die de vorm en contouren van het personage definiëren:

-

Hoofd

-

Boven- en onderlichaam

-

Linkerbovenarm, onderarm en hand

-

Rechterbovenarm, onderarm en hand

-

Linkerbovenbeen, onderbeen en voet

-

Rechterbovenbeen, onderbeen en voet

Wanneer gebruikers een avatarlichaam kopen, kunnen ze het als een set uitrusten of individuele lichaamsdelen van andere aankopen mixen en matchen.

In Studio worden deze lichaamsdelen weergegeven als [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten en zijn ze genest onder een enkel [Model](/docs/nl-nl/reference/engine/classes/Model) .

[Maak je eerste avatarlichaam](/docs/nl-nl/art/characters/creating/modeling-best-practices)

![Avatar lichaamsgeometrie](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/static-sections/geometry.png)

### [Rigging armatuur](#rigging-armatuur)[](#rigging-armatuur)

Binnen het fysieke lichaam van de avatar bevindt zich een niet-gerenderde [rigging armatuur](/docs/nl-nl/avatar/character-bodies/specifications#rigging)  die het personage in staat stelt zijn ledematen te articuleren. Vaak aangeduid als gewrichten of botten, omvat de rigging armatuur skinning-gegevens die verbindingen tussen ledematen organisch laten buigen, zoals de knieën en ellebogen van het personage.

Standaard avatar rigs  vereisen 15 poseerbare gewrichten om de 15 lichaamsdelen van het personage te articuleren. Als je echter hogere-fidelity personages wilt maken met een groter niveau van realisme, zijn er tot 37 extra optionele gewrichten voor geavanceerde R15 rigs  die je kunt maken voor gearticuleerde handen, schouders en wervelkolombewegingen. Elk gewricht moet een specifieke hiërarchie en naamgevingsconventie volgen om ervoor te zorgen dat de avatar goed functioneert in Studio en op de Marketplace.

Als de geometrie van je avatar geen rigging armatuur heeft, biedt Roblox [Avatar Setup](/docs/nl-nl/avatar-setup) , een tool die automatisch een rig genereert die klaar is voor de Marketplace voor het lichaamsmodel van het personage om beweging en animatie mogelijk te maken.

In Studio wordt elk gewricht van de rigging armatuur weergegeven door [Bone](/docs/nl-nl/reference/engine/classes/Bone)  objecten die de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten van het personage met elkaar verbinden.

[Maak je eerste karakter rig op een bestaand model](/docs/nl-nl/art/accessories/rig-and-cage-existing-models)

![Avatar rigging armatuur](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/static-sections/rigging.png)

### [Animaties](#animaties)[](#animaties)

Met behulp van de rigging armatuur van de avatar of gezichtsbones met [Facial Action Coding System](/docs/nl-nl/avatar/dynamic-heads/facs-poses-reference)  (FACS) gegevens, kun je poses creëren en interpoleren tussen hen om de volgende soorten aangepaste animaties te maken:

-

Emotes  - [Volledige lichaamsanimaties](/docs/nl-nl/avatar/emotes)  die spelers kopen op de Marketplace om te communiceren en te vieren met anderen in een game, zoals gebaren, reacties en dansen.

-

Gezichtsuitdrukkingen  - [Gezichtsanimaties](/docs/nl-nl/art/characters/facial-animation/animate-heads)  met de ogen, mond en tanden van het personage die spelers gebruiken om emoties uit te drukken.

Roblox biedt de volgende tools om het animatieproces van de avatar gemakkelijker te maken:

-

[Avatar Setup](/docs/nl-nl/avatar-setup)  - Genereert automatisch FACS-poses, gezichtsrigging, skinning en animatiegegevens die nodig zijn voor gezichtsanimatie en avatarchat.

-

[Adaptive Animation](/docs/nl-nl/characters/adaptive-animation)  - Pas gewrichten aan, wijzig ze en map ze zodat animaties naadloos kunnen afspelen tussen personages met unieke lichaamstypes, rigging armaturen en verhoudingen.

-

[Animatie-editor](/docs/nl-nl/animation/editor)  - Animeer handmatig de rig door poses te creëren op verschillende keyframes.

-

[Animatie-opname](/docs/nl-nl/animation/capture)  - Neem video-inhoud op of upload deze om beweging en uitdrukkingen vast te leggen als keyframes.

-

[Gezichtsanimatie-editor](/docs/nl-nl/art/characters/facial-animation/animate-heads#gebruik-de-face-animation-editor)  - Gebruik gezichtsregelaars om automatisch keyframes te creëren terwijl je regelaars voor verschillende gelaatskenmerken aanpast.

In Studio wordt elke emote weergegeven door een [Animation](/docs/nl-nl/reference/engine/classes/Animation)  object met zijn [AnimationId](/docs/nl-nl/reference/engine/classes/Animation#AnimationId)  eigenschap ingesteld op de assetID van je animatievolgorde, en FACS-waarden worden rechtstreeks gekoppeld aan de waarden van een dynamisch hoofd's [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls)  object.

[Maak je eerste volledige lichaamsanimatie](/docs/nl-nl/tutorials/use-case-tutorials/animation/create-an-animation)[Maak je eerste dynamische hoofd](/docs/nl-nl/art/characters/facial-animation/create-basic-heads)

![Avatar lichaamsgeometrie](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/static-sections/geometry.png)

Loopanimatie Schouderophalen emote Floss dans emote Gezichtsuitdrukkingen

Selecteer een optie om een voorbeeld te bekijken

### [Bevestigingspunten en cage meshes](#bevestigingspunten-en-cage-meshes)[](#bevestigingspunten-en-cage-meshes)

Buiten het fysieke lichaam van de avatar zijn er twee soorten niet-gerenderde componenten die het personage in staat stellen accessoires aan het lichaam te bevestigen en kleding te dragen:

-

Bevestigingspunten  - Stelt de specifieke punten in waar accessoires en in-game te dragen objecten aan het lichaam van het personage worden bevestigd.

-

Cage meshes  - Stelt de buitenste grens in voor kleding om uit te rekken en over het lichaam van het personage te passen.

Als de geometrie van je avatar geen bevestigingspunten of cage meshes heeft, biedt Roblox [Avatar Setup](/docs/nl-nl/avatar-setup) , een tool die automatisch de vereiste bevestigingspunten en cage meshes aan je avatar toevoegt. Daarnaast zijn er downloadbare Blender, Maya en .fbx  [projectbestanden](/docs/nl-nl/avatar/resources#projectbestanden)  die je kunt gebruiken om ervoor te zorgen dat je standaard bevestigingspunten en cage meshes voor humanoïde lichamen gebruikt.

In Studio worden externe cage mesh-objecten weergegeven door een [WrapTarget](/docs/nl-nl/reference/engine/classes/WrapTarget)  object, en bevestigingspunten worden weergegeven als [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten.

[Bewerk je eerste cage meshes op een bestaand model](/docs/nl-nl/art/accessories/rig-and-cage-existing-models)

![Avatar cage meshes en bevestigingspunten](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/static-sections/cages-attachments.png)

## [Wat je draagt](#wat-je-draagt)[](#wat-je-draagt)

Er zijn vier hoofdlagen van wat avatars kunnen dragen om hun unieke stijl uit te drukken:

[Make-up](#makeup)
2D cosmetische items die je op het gezicht van het personage kunt aanbrengen.

[Stijve accessoires](#rigid-accessories)
3D cosmetische items die aan het lichaam van het personage worden bevestigd, zoals hoeden, wapens en rekwisieten.

[Gelaagde accessoires](#layered-accessories)
3D cosmetische items die zich uitstrekken en passen over het lichaam van het personage, zoals broeken, t-shirts en jassen.

[Klassieke kleding](#classic-clothing)
2D cosmetische afbeeldingen die zich om het lichaam van het personage wikkelen.

Elke van deze lagen heeft strikte vereisten zodat gebruikers deze items kunnen uitrusten op personages van verschillende vormen en maten.

### [Make-up](#make-up)[](#make-up)

[Make-up](/docs/nl-nl/avatar/makeup)  is een cosmetisch item voor het gezicht voor extra creatieve expressie, zoals gezichtsschildering, strijdmarkeringen, camouflage en traditionele make-up kunst zoals oogschaduw, lippenstift en blush. Gebruikers kunnen make-up als een set op de Marketplace kopen en het aanbrengen als een complete samenhangende look, of individuele make-upcomponenten verwisselen voor anderen die passen bij de stijl van hun eigen avatar.

Roblox biedt [make-up templates](/docs/nl-nl/avatar/makeup#bronnen)  die je kunt gebruiken binnen je creatieproces, zoals:

-

Template-texturen die je kunt gebruiken in 2D-bewerkingssoftware om make-up te maken.

-

Template-hoofden die je kunt gebruiken om je make-up te bekijken en te testen voordat je exporteert.

-

Een referentie-ervaring die je kunt gebruiken om je make-upactiva op personages met verschillende huidtinten en lichaamstypes te importeren en te testen.

Je kunt deze templates gebruiken als een puur referentie om te zien hoe alles werkt, of je kunt ze allemaal gebruiken in elke stap van je creatieproces.

In Studio bestaat make-up uit meerdere gespecialiseerde textuurlagen die zijn gebakken in een [Decal](/docs/nl-nl/reference/engine/classes/Decal)  object, en elke textuurlaag bevat een unieke make-upcomponent zoals de lippen of het ooggebied.

[Maak je eerste make-uplook](/docs/nl-nl/avatar/makeup)

![Avatar zonder make-up](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/makeup/no-makeup.png)

Eyes Face Lips

Toggle Eyes, Face, Lips to preview

### [Stijve accessoires](#stijve-accessoires)[](#stijve-accessoires)

[Stijve accessoires](/docs/nl-nl/avatar/rigid-accessories)  worden aan de avatar bevestigd volgens de bevestigingspunten rond het lichaam van het personage. Wanneer gebruikers stijve accessoires op de Marketplace kopen, kunnen ze de positie en rotatie van het item aanpassen weg van het bevestigingspunt, afhankelijk van het lichaamstype van hun avatar.

Roblox biedt een [stapsgewijze tutorial](/docs/nl-nl/art/accessories/creating-rigid)  over hoe je je aangepaste 3D-modellen kunt omzetten in stijve accessoires, evenals de [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  in Studio om je aangepaste 3D-modellen te testen en te bewerken op meerdere combinaties van karakterlichamen, animaties en accessoires.

In Studio worden stijve accessoires weergegeven als [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  objecten.

[Maak je eerste stijve accessoire](/docs/nl-nl/art/accessories/creating-rigid)

![Avatar zonder stijve accessoires](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/rigid-accessories/no-accessories.png)

Back Neck Waist

Toggle Back, Neck, Waist to preview

### [Gelaagde accessoires](#gelaagde-accessoires)[](#gelaagde-accessoires)

[Gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories) , vaak aangeduid als gelaagde kleding, rekken zich uit en passen op de avatar volgens hun rigging armatuur en cage meshes. Wanneer gebruikers gelaagde accessoires op de Marketplace kopen, verwachten ze dat deze meebewegen met de animaties van het personage en zich op de juiste manier bovenop bestaande kleding die het personage draagt, lagen.

Roblox biedt een [stapsgewijze tutorial](/docs/nl-nl/art/accessories/creating)  over hoe je een Studio-klaar gelaagd t-shirt in Blender kunt maken, evenals de [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  in Studio om je aangepaste 3D-modellen te testen en te bewerken op meerdere combinaties van karakterlichamen, animaties en accessoires.

In Studio worden gelaagde accessoires weergegeven als [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  objecten met een kind [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  object.

[Maak je eerste gelaagd accessoire](/docs/nl-nl/art/accessories/creating)

![Avatar zonder gelaagde accessoires](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/layered-accessories/no-clothing.png)

Jacket 1 Jacket 2 Jacket 3 Jacket 4

Selecteer een optie om een voorbeeld te bekijken

### [Klassieke kleding](#klassieke-kleding)[](#klassieke-kleding)

[Klassieke kleding](/docs/nl-nl/avatar/classic-clothing)  wikkelt zich om specifieke gebieden van het lichaam van de avatar, zoals hun voorlichaam voor t-shirts of hun lichaam en benen voor broeken. Dit is het meest basale type avataritem dat je op Roblox kunt verkopen, omdat je alleen een afbeeldingseditor en webbrowser nodig hebt voor het creatieproces.

Roblox biedt een [stapsgewijze videotutorial](https://www.youtube.com/watch?v=r_unfGZT5Ps)  over hoe je een Studio-klaar klassiek t-shirt kunt maken met behulp van GNU Image Manipulation Program (GIMP), een gratis, externe afbeeldingseditor.

In Studio wordt klassieke kleding weergegeven als [ShirtGraphic](/docs/nl-nl/reference/engine/classes/ShirtGraphic)  objecten voor t-shirts, [Shirt](/docs/nl-nl/reference/engine/classes/Shirt)  objecten voor shirts, en [Pants](/docs/nl-nl/reference/engine/classes/Pants)  objecten voor broeken.

[Maak je eerste klassieke kledingitem](/docs/nl-nl/avatar/classic-clothing)

![Avatar zonder klassieke kleding](https://prod.docsiteassets.roblox.com/assets/avatar-anatomy/classic-clothing/no-clothes.png)

Pants Shirt

Toggle Pants, Shirt to preview

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
