<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/dynamic-heads/specifications -->

Dynamische hoofd specificaties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Animations
6. /
7. Dynamic heads

# Dynamische hoofd specificaties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Lichaamsmodellen van karakters met dynamische hoofden vereisen een specifieke set componenten en configuratiestandaarden, zodat het gehele model naar verwachting werkt op het platform, inclusief universele ondersteuning voor hoofdaccessoires en gezichtsanimatie, en zodat de karakters op de Marketplace kunnen worden verkocht.

Voordat je begint met het exportproces, controleer of je model voldoet aan de volgende modellering specificaties en richtlijnen voor een goede Studio-compatibiliteit.

Validatie voor dynamische hoofden maakt gebruik van een gespecialiseerd proces dat kan vereisen dat je je bestaande dynamische hoofdasset moet aanpassen. Voor meer informatie, zie [Validatie van dynamische hoofden](/docs/nl-nl/avatar/dynamic-heads/validate) .

[Avatar Setup](/docs/nl-nl/avatar-setup)  genereert automatisch componenten voor je avatar karakters, inclusief de hoofdkooi en gezichtsanimatie  die vereist zijn voor de Marketplace. Je kunt tijd besparen door karaktermodellen zonder avatarcomponenten in Avatar Setup in te dienen en vervolgens de output aan te passen. Indien nodig kun je je output downloaden als een .gltf , en vervolgens de FACS- of kooi-gegevens aanpassen in je externe modelleringstool.

Voor problemen of feedback met betrekking tot Avatar Setup, dien een [bugrapport](https://devforum.roblox.com/c/bug-reports/10)  in.

## [Buitenkant kooi](#buitenkant-kooi)[](#buitenkant-kooi)

Net als alle avatar karakter [lichaamsdelen](/docs/nl-nl/avatar/character-bodies/specifications#lichaamsdelen) , vereisen dynamische hoofden een buitenkooi om ervoor te zorgen dat gelaagde accessoires goed werken. Bovendien dienen de buitenkooien van dynamische hoofden om gezichtslandmarks  voor de ogen en mond van het gezicht vast te stellen voor het validatieproces.

Voor informatie over hoe je fouten met de buitenkooi van je dynamische hoofd kunt verbeteren of oplossen, zie [Beste praktijken voor het cagen van dynamische hoofden](/docs/nl-nl/avatar/dynamic-heads/caging-best-practices) .

### [Gezichtslandmarks](#gezichtslandmarks)[](#gezichtslandmarks)

Tijdens de validatie projecteert Roblox de oog/mondgebieden van de kooi op het basismesh om de oog- en mondgebieden van je karakterhoofd te identificeren. Roblox verwacht de volgende 3 verschillende landmarks in je kooien:

-

Linker oog landmark

-

Rechter oog landmark

-

Mond landmark

Zelfs voor niet-humanoïde gezichten die geen visuele ogen of monden bevatten, is het belangrijk om ervoor te zorgen dat deze landmarks nog steeds bestaan en over je basismesh kunnen worden geprojecteerd. Voor meer informatie over dit proces, zie [Validatie van dynamische hoofden](/docs/nl-nl/avatar/dynamic-heads/validate) .

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Landmark-A.png) Voorbeeld gezicht kooi UV

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Landmark-B.png) Gemarkeerde vertices van de kooi worden gebruikt om ogen/mond op het basismesh te volgen

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Cage-Landmark-C.png) Landmarks van de kooi toegepast op het basismesh, gebruikt als indicator voor basisanimatieondersteuning tijdens validatie

De mond landmark vertices bevinden zich op de tweede lus  van vertices vanaf de mondopening. Deze precisie kan helpen om problemen met [landmarkvalidatie](/docs/nl-nl/avatar/dynamic-heads/validate#stap-2-landmarkprojectie)  te voorkomen.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/Mouth-Vertices-Warning.png)

## [FACS-poses](#facs-poses)[](#facs-poses)

Dynamische hoofden ondersteunen gezichtsanimatie en kunnen veel verschillende basisposes bevatten om te voldoen aan de behoeften van je karakterontwerp. Dat gezegd hebbende, vereisen avatar karakterlichamen ten minste de volgende 17 [FACS-poses](/docs/nl-nl/avatar/dynamic-heads/facs-poses-reference)  om avatar chat te ondersteunen:

-

LeftEyeClosed

-

RightEyeClosed

-

EyesLookDown

-

JawDrop

-

Pucker

-

LeftLipCornerPuller

-

RightLipCornerPuller

-

ChinRaiser

-

ChinRaiserUpperLip

-

LeftCheekRaiser

-

RightCheekRaiser

-

LeftInnerBrowRaiser

-

RightInnerBrowRaiser

-

LeftLipCornerDown

-

RightLipCornerDown

-

LeftLowerLipDepressor

-

RightLowerLipDepressor

Hoewel deze 17 poses een vereiste zijn, wordt aanbevolen om zoveel mogelijk gezichtsposes in je asset op te nemen om de expressiviteit en de nauwkeurigheid van gezichtsanimaties te verbeteren.

Om het dynamische hoofd [validatieproces](/docs/nl-nl/avatar/dynamic-heads/validate)  te doorstaan, moet het hoofd van je karakter succesvol de volgende 5 gezichtsacties uitvoeren. Als het dynamische hoofd zich niet kan vervormen op de punten van de kooien [gezichtslandmarks](#gezichtslandmarks)  voor deze acties, faalt de validatie voor de asset.

| Actie-eenheidstest | | Niet-nul controlewaarden |
| --- | --- |
| Linker oogknipper | | LeftEyeClosed  = 1
EyesLookDown  = 1 |
| Rechter oogknipper | | RightEyeClosed  = 1
EyesLookDown  = 1 |
| Mond opent | | JawDrop  = 1 |
| Blije uitdrukking | | Pucker  = 1
LeftLipCornerPuller  = 1
RightLipCornerPuller  = 1 |
| Verdrietige uitdrukking | | ChinRaiser  = 1
ChinRaiserUpperLip  = 1
LeftCheekRaiser  = 0.85
RightCheekRaiser  = 0.85
LeftInnerBrowRaiser  = 1
RightInnerBrowRaiser  = 1
LeftLipCornerDown  = 1
RightLipCornerDown  = 1
LeftLowerLipDepressor  = 1
RightLowerLipDepressor  = 1 |

## [Marketplace vereisten](#marketplace-vereisten)[](#marketplace-vereisten)

Naast de andere vermelde technische vereisten, moeten je karakterlichamen met dynamische hoofden voldoen aan de volgende aanvullende specificaties voordat je ze naar de Marketplace uploadt om te verkopen:

-

Zorg ervoor dat je karakterlichamen voldoen aan de [Marketplace-beleidsregels](/docs/nl-nl/marketplace/marketplace-policy) .

-

Zorg ervoor dat je karakterlichamen voldoen aan Roblox's [aangepaste mesh specificaties](/docs/nl-nl/art/modeling/specifications)  en [karakterlichaam specificaties](/docs/nl-nl/avatar/character-bodies/specifications) , waar van toepassing.

-

Object [Material](/docs/nl-nl/reference/engine/classes/MeshPart#Material)  is ingesteld op Plastic .

-

Object [Transparency](/docs/nl-nl/reference/engine/classes/MeshPart#Transparency)  is ingesteld op 0 .

-

Object [VertexColor](/docs/nl-nl/reference/engine/classes/MeshPart#VertexColor)  is de standaard 1, 1, 1 .

-

Als het hoofd van je karakter aparte wimpers en wenkbrauw-assets bevat, moet je ze toevoegen aan je karakterlichaamsmodel als [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  objecten. Voor meer informatie, zie [Publiceer lichamen met wimpers en wenkbrauwen](/docs/nl-nl/art/accessories/publish-eyebrows-eyelashes) .

-

Je [Model](/docs/nl-nl/reference/engine/classes/Model)  instantie bevat geen overbodige objecten, zoals [Script](/docs/nl-nl/reference/engine/classes/Script)  of extra [Part](/docs/nl-nl/reference/engine/classes/Part)  instanties.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
