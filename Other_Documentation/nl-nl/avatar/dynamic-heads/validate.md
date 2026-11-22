<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/dynamic-heads/validate -->

Dynamische hoofdvalidatie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Animations
6. /
7. Dynamic heads

# Dynamische hoofdvalidatie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze inhoud is voor makers die van plan zijn dynamische hoofden te creëren die bestemd zijn voor de Marketplace, of voor karakterhoofden die activa van de Marketplace ondersteunen.

Roblox voert een rigoureuze validatie uit om ervoor te zorgen dat elk actief dat je uploadt naar de Marketplace compatibel is met alle andere activa op de Marketplace. Voor dynamische hoofden zorgt de validatie er voornamelijk voor dat het hoofdactief het volgende bevat:

-

Zichtbaar waarneembare gelaatskenmerken , zoals ogen en een mond.

-

Een correct geconfigureerd buitenframe  om kleding en accessoires te dragen.

-

Correct geconfigureerde gezichtsanimatieposes  om basis universele uitdrukkingen uit te voeren, zoals knipperen en glimlachen.

De validatie voor dynamische hoofden gebeurt in drie stappen: [detectie van gelaatskenmerken](#stap-1-detectie-van-gelaatskenmerken) , [landmarkprojectie](#stap-2-landmarkprojectie)  en [betekenisvolle animatiebeoordeling](#stap-3-betekenisvolle-animatiebeoordeling) . Zie hieronder voor een referentie van hoe de validatieprocessen werken, evenals [veelvoorkomende problemen](#veelvoorkomende-problemen) .

 ![Diagram van de drie stappen voor dynamische hoofdvalidatie: detectie van gelaatskenmerken, landmarkprojectie en betekenisvolle animatiebeoordeling.](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/Dynamic-Head-Validation-Steps.png)

De validatie controleert ook op andere problemen, zoals slechte omheining of ontbrekende vereiste FACS-poses. Voor meer informatie, zie [veelvoorkomende problemen](#veelvoorkomende-problemen) .

[Avatar Setup](/docs/nl-nl/avatar-setup)  genereert automatisch componenten voor je avatarpersonages, inclusief het hoofdframe en de gezichtsanimatie  die vereist zijn voor de Marketplace. Je kunt tijd besparen door karaktermodellen zonder avatarcomponenten in Avatar Setup in te dienen en vervolgens de output aan te passen. Indien nodig kun je je output downloaden als een .gltf , en vervolgens de FACS- of omheininggegevens aanpassen in je externe modelleringstool.

Voor problemen of feedback met betrekking tot Avatar Setup, dien een [bugrapport](https://devforum.roblox.com/c/bug-reports/10)  in.

## [Stap 1: Detectie van gelaatskenmerken](#stap-1-detectie-van-gelaatskenmerken)[](#stap-1-detectie-van-gelaatskenmerken)

Voordat de gezichtsanimatie wordt gecontroleerd, controleert de validatie of het hoofd leesbare ogen en een mond heeft. Het rendert het hoofd vanuit meerdere hoeken om de kenmerken te beoordelen: de validatie controleert de ogen in de neutrale uitdrukking en controleert de mond in de mond-open uitdrukking, zodat een mond die niet duidelijk zichtbaar is in rust nog steeds kan worden gedetecteerd.

Als de ogen of mond ontbreken, slaat het hoofd deze controle niet over en stopt de validatie voordat de animatiecontroles plaatsvinden. Dit voorkomt dat een hoofd alleen op basis van beweging in zijn omheining of mesh slaagt wanneer het hoofd niet de vereiste gelaatskenmerken heeft.

## [Stap 2: Landmarkprojectie](#stap-2-landmarkprojectie)[](#stap-2-landmarkprojectie)

De validatie gebruikt het hoofdframe om landmarks op de hoofdmesh te projecteren. Dit helpt Roblox vast te stellen waar de ogen en mond zich bevinden en helpt bij het begeleiden van de gezichtsanimatietest.

In de UGC Validatievisualisatietool geven rode landmarks het linkeroog omheinde gebied op de mesh aan en reageren ze op de rechteroog FACS van de avatar. Blauwe landmarks geven het rechteroog omheinde gebied op de mesh aan en reageren op de linkeroog FACS van de avatar. Groene landmarks geven de waarneembare mond van de avatar, mond FACS en mond omheinde gebied op de mesh aan.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-With-Landmarks.png) Omheining mesh: Specifieke vertices van de omheining markeren ogen en mond.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Projection-Side.png) Roblox validatie projecteert deze punten op de hoofdmesh.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Face-Landmarks.png) Hoofdmesh: Alle landmarks geprojecteerd van omheining mesh naar hoofdmesh.

Zodra de validatie verifieert dat de projectie succesvol is en alle landmarks op de hoofdmesh zijn vastgesteld, kan het doorgaan met het testen van gezichtsanimaties.

## [Stap 3: Betekenisvolle animatiebeoordeling](#stap-3-betekenisvolle-animatiebeoordeling)[](#stap-3-betekenisvolle-animatiebeoordeling)

Nadat de eerdere validatiecontroles zijn geslaagd, rendert de validatie een korte reeks uitdrukkingen, waaronder knipperen, mondbeweging, een glimlach en een frons, vanuit meerdere hoeken. De validatie evalueert of het gezicht de uitdrukkingen uitvoert, in plaats van simpelweg te detecteren dat pixels of geometrie zijn veranderd.

Het hoofd moet de vereiste uitdrukkingen duidelijk tonen. Starre beweging, geometriewisselingen, willekeurig rekken of andere veranderingen die niet als gelaatsuitdrukkingen worden gelezen, zijn mogelijk niet voldoende om te slagen.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/dynamic-heads/Meaningful-Animation-Neutral.png) Neutraal: beide ogen open, mond gesloten
Alle FACS-poses = 0

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/dynamic-heads/Meaningful-Animation-Right-Eye-Closed.png) Rechteroog knipperen
RightEyeClosed  = 1
EyesLookDown  = 1 .

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/dynamic-heads/Meaningful-Animation-Left-Eye-Closed.png) Linkeroog knipperen
LeftEyeClosed  = 1
EyesLookDown  = 1 .

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/dynamic-heads/Meaningful-Animation-Mouth-Open.png) Mond open
JawDrop  = 1

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/dynamic-heads/Meaningful-Animation-Happy.png) Geluk: mondhoeken krommen omhoog in een glimlach
Pucker  = 1
LeftLipCornerPuller  = 1 .
RightLipCornerPuller  = 1

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/dynamic-heads/Meaningful-Animation-Sad.png) Verdriet: mondhoeken krommen omlaag in een frons
ChinRaiser  = 1
ChinRaiserUpperLip  = 1
LeftCheekRaiser  = 0.85
RightCheekRaiser  = 0.85
LeftInnerBrowRaiser  = 1
RightInnerBrowRaiser  = 1
LeftLipCornerDown  = 1
RightLipCornerDown  = 1
LeftLowerLipDepressor  = 1
RightLowerLipDepressor  = 1

## [Test gezichtsanimaties](#test-gezichtsanimaties)[](#test-gezichtsanimaties)

Nu de validatiesysteem weet waar het moet controleren op de ogen en mond, controleert de validatie op gezichtsanimaties om ervoor te zorgen dat de volgende basisacties mogelijk zijn:

-

Linker- en rechterogen kunnen sluiten

-

Mond kan openen en sluiten

-

Basis gelukkige en verdrietige uitdrukkingen

Voor een volledige lijst van de minimale FACS-poses die je dynamische hoofden nodig hebben om de validatie te doorstaan, zie [Dynamische hoofd specificaties - FACS-poses](/docs/nl-nl/avatar/dynamic-heads/specifications#facs-poses) .

De validatie zoekt naar de relatieve verandering in de landmarks . Bijvoorbeeld, bij het testen op het sluiten van het rechteroog (FACS-positie: RightEyeClosed ), controleert de validatie of de landmarks zich overeenkomstig verplaatsen vanuit hun oorspronkelijke neutrale staat.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Face-Landmarks.png)

Gezicht mesh met alle geprojecteerde landmarks toegepast vanuit de omheining.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Eye-Closed-Success.png)

Validatie verifieert dat het rechteroog kan sluiten op basis van de verplaatsing van landmarks.

## [Veelvoorkomende problemen](#veelvoorkomende-problemen)[](#veelvoorkomende-problemen)

De validatie controleert verschillende aspecten van je hoofdactief. Als je een fout ontvangt met betrekking tot dynamische hoofdanimatie, gebruik dan de volgende tabel voor mogelijke oorzaken:

| Probleem | | Mogelijke oplossingen |
| --- | --- |
| De validatietool is niet in staat om gelaatskenmerken te herkennen .
Zie [Detectie van gelaatskenmerken](#stap-1-detectie-van-gelaatskenmerken)  en de gerelateerde [validatiefouten](/docs/nl-nl/marketplace/validation-system#validatiecontroles) . | | - Controleer of de ogen zichtbaar zijn  in de standaardstemming en vanuit meerdere hoeken, en dat de mond zichtbaar is  tijdens de mond-open animatie en vanuit meerdere hoeken.
- Controleer of er hoog contrast is tussen de gelaatskenmerken en de rest van het hoofd . |
| De validatietool is niet in staat om landmarks succesvol toe te passen .
Zie [Niet in staat om landmarks te projecteren](#niet-in-staat-om-landmarks-te-projecteren) . | | - Controleer of de omheining landmark vertices direct boven de overeenkomstige gebieden van het gezicht zijn gepositioneerd .
- Controleer of de omheining niet intersecteert met de hoofdmesh . Landmarkprojectie verwacht dat de omheining boven de hoofdmesh is.
- Controleer op eventuele gaten, openingen of moeilijke oppervlakken  van het gezicht waar landmarks mogelijk niet kunnen projecteren. |
| De validatietool kan landmarks toepassen, maar kan geen animatie detecteren .
Zie [Animaties verplaatsen geen landmarks](#animaties-verplaatsen-geen-landmarks) . | | - Controleer of landmarks zich bevinden op de gebieden van de ogen en mond die bewegen tijdens de animatie .
- Controleer of de omheining niet intersecteert met de hoofdmesh . Landmarkprojectie verwacht dat de omheining boven de hoofdmesh is.
- Als je aparte meshes voor oogballen en mondzakken gebruikt , zorg ervoor dat je landmarks zijn toegepast op de hoofdmesh, niet op de oogballen of mondzak. Dit kan worden bereikt door het gebied waar je omheiningen landmarks projecteren iets te verbreden. |
| De validatietool detecteert geen [FACS-animaties](#animatiegegevens-ontbreken) . | | - Je hoofd bevat geen FACS-animatie. Controleer of je hoofd FACS-poses en mapping bevat. |
| De validatietool is niet in staat om een of meer uitdrukkingen te herkennen .
Zie [Betekenisvolle animatiebeoordeling](#stap-3-betekenisvolle-animatiebeoordeling)  en de gerelateerde [validatiefouten](/docs/nl-nl/marketplace/validation-system#validatiecontroles) . | | - Controleer of de animatie voor elke uitdrukking overeenkomt met de beweging van de FACS-poses  vanuit meerdere hoeken.
- Voor de linker- en rechterknipper  animaties, zorg ervoor dat het juiste oog verticaal plat wordt.
- Voor de mond open en sluiten  animaties, zorg ervoor dat het mondgebied van de mesh merkbaar opent in de verticale richting, en dat de sluitanimatie het omgekeerde doet.
- Voor de gelukkige en verdrietige  uitdrukkingen, krom de mondhoeken omhoog in een glimlach en omlaag in een frons. |

### [Niet in staat om landmarks te projecteren](#niet-in-staat-om-landmarks-te-projecteren)[](#niet-in-staat-om-landmarks-te-projecteren)

Als de validatie niet in staat is om de projectie correct op het oppervlak van het hoofd toe te passen, faalt de validatie. Dit gebeurt vaak als je omheining verder dan je hoofdmesh uitsteekt , of als je hoofdmesh een gat of opening  heeft die de toepassing van de landmark verhindert. Zie de volgende voorbeelden:

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Missing-Landmarks-A.png)

Omheining steekt te ver uit de mesh  en de validatie kan 3 landmarks niet op de basismesh toepassen.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Missing-Landmarks-B.png)

Basismesh heeft een holle opening  in het ontwerp, waardoor validatie 3 landmarks niet kan toepassen om het ooggebied aan te geven.

In beide gevallen zou het aanpassen van de omheining om de juiste projectie van landmarks naar de basismesh mogelijk te maken dit probleem oplossen.

### [Animaties verplaatsen geen landmarks](#animaties-verplaatsen-geen-landmarks)[](#animaties-verplaatsen-geen-landmarks)

In het geval dat landmarks correct zijn toegepast op de basismesh en de basismesh FACS-gegevens bevat, is het mogelijk dat de gezichtsanimaties de landmarks niet voldoende verplaatsen om de validatie te doorstaan. Zie het volgende voorbeeld:

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Face-Landmarks-Poor.png)

Landmarks succesvol vastgesteld op basismesh, maar zijn niet in de verwachte gebieden.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Landmarks-Fail-B.png)

Bij het testen van animaties detecteert de validatie niet de verwachte verandering in de landmarkgebieden.

In het voorbeeld zou het aanpassen van de omheining om de juiste projectie van landmarks op de juiste gebieden mogelijk te maken dit probleem oplossen.

Er kunnen ook gevallen zijn waarin de landmarks correct zijn, maar de animatie zelf de geprojecteerde landschappen niet voldoende verandert om de validatie te doorstaan. In deze gevallen kan het repareren van de animatie en/of het optimaliseren van de omheining helpen dat de validatie de gezichtsanimatie correct identificeert.

### [Animatiegegevens ontbreken](#animatiegegevens-ontbreken)[](#animatiegegevens-ontbreken)

Hoofden vereisen [17 specifieke FACS-poses](/docs/nl-nl/avatar/dynamic-heads/specifications#facs-poses)  die worden gebruikt om de 5 basisacties te testen. Ongeacht landmarks of andere FACS-animaties, faalt de validatie onmiddellijk als de minimale 17 poses niet zijn gedetecteerd.

Voor informatie over hoe je dynamische hoofden kunt poseren en mappen, zie [Maak basis dynamische hoofden](/docs/nl-nl/art/characters/facial-animation/create-basic-heads) .

## [Werken met niet-humanoïden](#werken-met-niet-humanoïden)[](#werken-met-niet-humanoïden)

Sommige karaktermodellen, meestal niet-humanoïden, hebben onnatuurlijke of ontbrekende ogen en monden. De meest voorkomende gevallen hiervan zijn de klassieke blokachtige kenmerken.

In dit geval past de omheining nog steeds de verwachte landschappen toe op het hoofdoppervlak, en Roblox valideert of gezichtsanimaties de gezichtsanimaties correct verplaatsen.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Blocky-Cage.png) De omheining voor een blokachtig karakter past landmarks toe op het oppervlak van het hoofd.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Blocky-All.png) Zorg ervoor dat de landmarks zijn toegepast in gebieden waar animatie de landmarks effectief kan verplaatsen.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Blocky-Head.png) Validatie controleert de verplaatsing van de landmarks om de gezichtsanimatie te verifiëren.
Zorg ervoor dat je [FACS-animaties](/docs/nl-nl/avatar/dynamic-heads/specifications#facs-poses)  de regio waar landmarks zijn toegepast correct beïnvloeden.

In gevallen waarin ogen en monden mogelijk ontbreken, projecteert de validatie nog steeds landmarks en verwacht gezichtsanimatie in die gebieden.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Horn-Cage.png) Hoewel dit karakter geen ogen of mond heeft, probeert de omheining nog steeds landmarks voor die kenmerken te projecteren.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Horn-All.png) In dit voorbeeld passen de omheining landmarks toe op het oppervlak van het hoofd van deze oogloze karakter.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Horn-Head.png) Validatie controleert de verplaatsing van de landmarks om de gezichtsanimatie te verifiëren.
Zorg ervoor dat je [FACS-animaties](/docs/nl-nl/avatar/dynamic-heads/specifications#facs-poses)  de regio's waar de landmarks zijn toegepast correct beïnvloeden.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
