<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/dynamic-heads/test -->

Test dynamische hoofden in Studio | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Animations
6. /
7. Dynamic heads

# Test dynamische hoofden in Studio

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Als je snel de hoofdanimatie van een karakter wilt testen, gebruik dan [Avatar Setup](/docs/nl-nl/avatar-setup)  om je karakter te laden en gebruik de presets om verschillende gezichtsanimaties en hoofdaccessoires te bekijken.

Test handmatig je dynamische hoofdcreaties door karaktermodellen met dynamische hoofden in Studio te importeren en de gegenereerde [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls)  instantie te gebruiken om het gezicht te poseren of te animeren.

Bij het importeren van een dynamisch hoofd in Studio, maakt Studio een [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls)  instantie aan die je kunt gebruiken om toegang te krijgen tot en deze individuele poses te combineren om uitdrukkingen en animaties te creëren. In tegenstelling tot typische gerigde modellen, kun je de gezichts [Bones](/docs/nl-nl/reference/engine/classes/Bone)  van een hoofdmesh niet rechtstreeks in Studio benaderen.

Om dynamische hoofden met gezichtsanimatiegegevens in je spel in te stellen:

1.

[Importeer een model met een dynamisch hoofd](/docs/nl-nl/avatar/character-bodies/import) . Je kunt je eigen model maken of een van de meegeleverde referentiemodellen gebruiken.

2.

OPTIONAL

 [Importeer gezichtaccessoires](#importeren-van-gezichtaccessoires)  die je wilt vervormen met de gezichtsuitdrukkingen van je hoofd. Je kunt je eigen accessoires maken of een van de meegeleverde referentieaccessoires gebruiken.

3.

[Animeer het hoofd](#animeer-hoofden)  in de Animatie-editor  door individuele animatietracks toe te voegen of door de Gezichtsanimatie-editor  te gebruiken.

Als je wilt experimenteren met kant-en-klare dynamische hoofden voordat je [je eigen maakt](/docs/nl-nl/art/characters/facial-animation/create-basic-heads) , biedt Roblox een referentiespel aan zodat je kunt zien hoe dynamische hoofden interageren met de interface van Studio, evenals twee referentiemodellen en accessoires die je rechtstreeks in je eigen spel kunt importeren:

| Referentiebestanden | | Beschrijving |
| --- | --- |
| [Hoofdanimatie In-Game Editor](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/reference-files/Dynamic-Head-Editor.rbxl) | | Een referentiespel waarmee je een Goblin- en Blocky-hoofd met verschillende accessoires kunt bekijken met behulp van een editor. |
| [Hoofd Schema Referentie](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/reference-files/Dynamic-Head-Schema.rbxl) | | Een referentiespel met een Blocky-hoofdmodel met [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls) . |
| [Goblin Karaktermodel](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/reference-files/GoblinCharacter.zip) | | Een Goblin-karaktermodel met een dynamisch hoofd. |
| [Blocky Karaktermodel](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/reference-files/BlockyCharacter.fbx) | | Een Blocky-karaktermodel met een dynamisch hoofd. |
| [Blocky Gezichtaccessoires en Kleding](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/reference-files/Blocky-Face-Accessories.zip) | | Een .zip -bestand met Blocky-specifieke accessoires, waaronder:
-

Gehoekte Wenkbrauwen

-

Ronde Wenkbrauwen

-

Rechthoekige Wenkbrauwen

-

Lange Wimpers

-

Korte Wimpers

-

Lange Ducktail Baard

-

Mutton Chops Baard en Haar

-

Shirt en Broek

 |

## [Importeren van gezichtaccessoires](#importeren-van-gezichtaccessoires)[](#importeren-van-gezichtaccessoires)

Je kunt gezichtaccessoires importeren en uitrusten die je wilt vervormen met de gezichtsuitdrukkingen van je dynamische hoofd. Bijvoorbeeld, wanneer je wenkbrauwen als gezichtaccessoire importeert en uitrust, kun je de wenkbrauwen animeren zodat ze bewegen met de ogen van het karakter.

Wanneer je een gezichtaccessoire importeert, wordt het standaard geïmporteerd als een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  object. Met behulp van de [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  (AFT) kun je de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  omzetten in een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  instantie die compatibel is met het dynamische hoofd.

Om een gezichtaccessoire te importeren:

1.

Gebruik het [Importer](/docs/nl-nl/studio/importer)  vanuit het Bestand  menu van Studio om het aangepaste model in de werkruimte te importeren.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/using-dynamic-heads-in-studio/Importing-Facial-Accessory-Final-Result.jpg)

2.

Gebruik de AFT om de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  om te zetten in een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  instantie.

1.

Klik op Accessoire  in het Avatar  tabblad van de werkbalk om de AFT te openen.

2.

Selecteer in het Explorer  venster de MeshPart  die je als gezichtaccessoire hebt geïmporteerd. De naam wordt weergegeven in het Deel  veld.

3.

Klik op de Volgende  knop.

4.

Selecteer in de categorie Kleding  de optie Gezicht , en klik vervolgens op de Volgende  knop.

5.

OPTIONAL

 Gebruik in het Bewerken  paneel de aanpassingsopties om ervoor te zorgen dat het accessoire goed past bij je model.

6.

Bekijk in het Voorbeeld  paneel het nieuwe gezichtaccessoire op je hoofd en klik vervolgens op de Volgende  knop. De tool transformeert de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  in een [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  instantie, en deze wordt weergegeven in het Explorer  venster.

Je kunt het accessoire op je geïmporteerde model bekijken door de [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  instantie een kind te maken van je karakter [Model](/docs/nl-nl/reference/engine/classes/Model) . Je kunt alleen karakter-specifieke gezichtaccessoires uitrusten met hun ontworpen karakter.

![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/using-dynamic-heads-in-studio/Facial-Accessory-In-Viewport.jpg) Uitrusting accessoire in viewport

![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/using-dynamic-heads-in-studio/Facial-Accessory-In-Property-Panel.jpg) Uitrusting Accessoire in Explorer

Je kunt de [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  instantie ook opslaan in je toolbox en de asset ID op elk moment in je spellen gebruiken. Voor informatie over het uitrusten van accessoires door een [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  toe te passen, zie [Pas karakters aan met humanoïde beschrijving](/docs/nl-nl/characters/appearance#set-multiple-accessories) .

### [AutoSkin eigenschap](#autoskin-eigenschap)[](#autoskin-eigenschap)

Je kunt de [WrapLayer.AutoSkin](/docs/nl-nl/reference/engine/classes/WrapLayer#AutoSkin)  eigenschap in de [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  instantie van het accessoire inschakelen om de skinning van het hoofd op het gezichtaccessoire toe te passen. Dit stelt een gezichtaccessoire in staat om te passen en de uitdrukkingen van een karakter te volgen zonder dat je tijdens het 3D-modelleringsproces skinning-invloeden hoeft toe te passen.

De volgende opties zijn beschikbaar voor de [WrapLayer.AutoSkin](/docs/nl-nl/reference/engine/classes/WrapLayer#AutoSkin)  eigenschap:

-

Uitgeschakeld : Schakelt het automatische skinningoverdrachtsproces uit. Dit is de standaardwaarde.

-

IngeschakeldOverride : Schakelt het Auto-Skin Transfer proces in en staat Studio toe om bestaande skinninginformatie op het accessoire te overschrijven. Kies deze instelling wanneer je de bestaande skinning van een accessoire wilt instellen of vervangen met de Auto-Skin Transfer versie.

-

IngeschakeldBewaren : Schakelt het automatische skinningoverdrachtsproces in, maar staat niet  toe dat het bestaande skinninginformatie op het accessoire overschrijft. Kies deze instelling wanneer je de bestaande skinning van een accessoire wilt behouden en onderhouden. Als er geen skinning is om te behouden, creëert de Auto-Skin Transfer automatisch nieuwe skinning.

## [Animeer hoofden](#animeer-hoofden)[](#animeer-hoofden)

Dynamische hoofd [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart)  bevatten een [FaceControls](/docs/nl-nl/reference/engine/classes/FaceControls)  instantie waarmee je toegang hebt tot je gezichtspositie-eigenschappen.

![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/using-dynamic-heads-in-studio/FaceControls-In-Explorer.jpg) FaceControls in Explorer

![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/using-dynamic-heads-in-studio/FaceControls-In-Property-Panel.jpg) FaceControls Eigenschappenpaneel

Je kunt deze eigenschappen aanpassen in de Animatie-editor  om je hoofd te animeren. Voor meer informatie, zie [Animeer hoofden](/docs/nl-nl/art/characters/facial-animation/animate-heads) .

## [Probleemoplossing](#probleemoplossing)[](#probleemoplossing)

Bij het importeren van aangepaste hoofdmodellen, toont het [Output venster](/docs/nl-nl/studio/output)  een fout- of waarschuwingsbericht als er problemen waren tijdens het configuratieproces.

### [Foutmeldingen](#foutmeldingen)[](#foutmeldingen)

Foutmeldingen geven aan dat het niet gelukt is om een model met een hoofd correct te importeren. Raadpleeg de volgende tabel voor een samenvatting van alle hoofd foutmeldingen en probleemoplossingstips:

| Foutmelding | | Probleemoplossing |
| Importeren van hoofd met gezichtsanimatie mislukt. | | Het .fbx  bestand is beschadigd. |
| Meer dan één gewricht genaamd X gevonden. Alle gewrichten moeten unieke namen hebben. | | Zorg ervoor dat elk gewricht dat je importeert een unieke naam heeft. |
| Importeren van hoofd met gezichtsanimatie mislukt: Correctives kunnen voor maximaal 3 controle namen zijn. | | Studio vond een corrective met meer dan 3 correctieve poses. Dit wordt niet ondersteund, dus je moet de corrective verwijderen. |
| Importeren van hoofd met gezichtsanimatie mislukt: Onbekende FACS controle naam X. | | X is een onbekende FACS pose naam. Zorg ervoor dat X is hernoemd naar een van de [standaard FACS poses](/docs/nl-nl/avatar/dynamic-heads/facs-poses-reference) . |
| Importeren van hoofd met gezichtsanimatie mislukt: Ongeldige corrective naam X: Neutraal kan geen deel uitmaken van een corrective. | | X is een ongeldige corrective naam. Zorg ervoor dat je het juiste naamgevingsformaat voor correctives volgt. |
| Importeren van hoofd met gezichtsanimatie mislukt: Dubbele FACS controle naam X gevonden voor corrective Y. | | X is een ongeldige corrective naam. Je kunt alleen een basispose die als onderdeel van een corrective is vermeld, eenmaal in de correctieve naam opnemen. |
| Importeren van hoofd met gezichtsanimatie mislukt: Kon het frame nummer in Extra Attribuut genaamd X niet parseren. | | Je moet extra attributen "Frame0", "Frame1", enz. noemen. |
| Importeren van hoofd met gezichtsanimatie mislukt: Lege waarde gevonden voor Extra Attribuut genaamd X. | | Het extra attribuut X heeft geen waarde. Voeg een basispose naam of corrective toe, of verwijder het extra attribuut. |
| Importeren van hoofd met gezichtsanimatie mislukt: Dubbele controle naam gevonden. | | Je hebt een FACS pose of corrective aan meerdere frames ingesteld. Zorg ervoor dat elke FACS pose of corrective slechts op één enkel frame is ingesteld. |
| Importeren van hoofd met gezichtsanimatie mislukt: Head_Geo heeft geen Extra Attributen die FACS controles aan animatieframes koppelen. | | De "Head_Geo" mesh in het FBX-bestand moet extra attributen hebben om gezichtsuitdrukkingen te animeren. De geïmporteerde avatar zal geen gezichtsuitdrukkingen animeren. |
| Importeren van hoofd met gezichtsanimatie mislukt: Geen frame was ingesteld op "Neutraal" in de animatie. | | Er moet één frame zijn ingesteld op "Neutraal" in de animatietijdlijn. |
| Importeren van hoofd met gezichtsanimatie mislukt: X is niet gespecificeerd. Dit is nodig voor corrective Y. | | Alle basisposes voor een corrective moeten in de extra attributen worden ingesteld. Bijvoorbeeld, als de Funneler_JawDrop  corrective is ingesteld, dan moeten er ** moeten**  poses zijn voor Funneler  en JawDrop  alleen. |
| Importeren van hoofd met gezichtsanimatie mislukt: Ontbrekend sleutelframe X voor Y. | | Er is een extra attribuut "FrameX" ingesteld op Y, maar de animatietijdlijn heeft geen frame X. |
| Importeren van hoofd met gezichtsanimatie mislukt: Geen gewrichten gevonden onder DynamicHead. | | Het .fbx  bestand heeft geen gewrichten onder het RootFaceJoint gewricht. |
| Kon FACS controle gegevens niet laden. | | Er zijn beschadigde gewrichtparameters in het .fbx  bestand. |

### [Waarschuwingsberichten](#waarschuwingsberichten)[](#waarschuwingsberichten)

Waarschuwingsberichten geven een potentieel probleem aan met een geïmporteerd hoofdmodel. Raadpleeg de volgende tabel voor een samenvatting van alle hoofd waarschuwingsberichten en probleemoplossingstips:

| Foutmelding | | Probleemoplossing |
| Je hebt corrective X, maar mist corrective Y om het te ondersteunen. Dit kan vreemde vervormingen veroorzaken. | | Je hebt een 3-corrective ingesteld zonder de basis 2-corrective in te stellen. Het geïmporteerde hoofd zal animeren, maar er kunnen vreemde vervormingen optreden. |
| Attribuut X overslaan: Y | | Studio vond een extra attribuut genaamd X, maar omdat het niet overeenkwam met het formaat van "Frame#", werd het genegeerd. |
| Controle X is bijna identiek aan Neutraal. | | De pose voor X is zeer vergelijkbaar met Neutraal. Studio meldt dit voor het geval dit een vergissing was, maar de import zal succesvol zijn zolang er geen andere fouten zijn. |
| Vond slechts N basisposes. Je karakter kan zich mogelijk niet uitdrukken. | | Je hebt slechts een subset van basisposes gedefinieerd in het .fbx  bestand. De import zal nog steeds succesvol zijn zolang er geen andere fouten zijn. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
