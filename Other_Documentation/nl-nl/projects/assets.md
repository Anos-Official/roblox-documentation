<!-- Source: https://create.roblox.com/docs/nl-nl/projects/assets -->

Activa | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)

# Activa

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Bijna alles in Roblox wordt weergegeven als een cloud-gebaseerde activa met een unieke bijbehorende ID. Deze ID is meestal in de vorm van rbxassetid://[ID] , die wordt toegepast op verschillende instanties als een eigenschap die geschikt is voor dat specifieke activatype. Bijvoorbeeld, [Texture](/docs/nl-nl/reference/engine/classes/Texture) , [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  en [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  instanties verwijzen naar afbeelding-, mesh- en audio-activa via hun respectieve [ColorMapContent](/docs/nl-nl/reference/engine/classes/Texture#ColorMapContent) , [MeshId](/docs/nl-nl/reference/engine/classes/MeshPart#MeshId)  en [Asset](/docs/nl-nl/reference/engine/classes/AudioPlayer#Asset)  eigenschappen.

rbxassetid://7229442422

![Een decal activa van een jonge vrouw met een knop voor een oog.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-Example-Grafitti04.png)

rbxassetid://6768917255

![Een ongekleurde schatkist MeshPart activa.](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/Base-Mesh-In-Marketplace.png)

rbxassetid://9125402735

Dit cloud-gebaseerde activa-systeem stelt je in staat om activa op Roblox op te slaan en ze in verschillende contexten op het platform opnieuw te gebruiken, zoals in verschillende objecten en plaatsen, zonder lokale kopieën te onderhouden als onderdeel van elk opgeslagen Studio-spel. Je kunt miljoenen projectactiva vinden in de [Creator Store](https://create.roblox.com/store) , avataractiva uitrusten in de [Marketplace](https://www.roblox.com/catalog) , of je kunt je eigen activa maken en ze [importeren](#activa-beheer)  rechtstreeks in Studio via de activa-beheer tools.

Wanneer je activa importeert, moeten ze een [moderatie](#activa-moderatie)  controle doorstaan voordat gebruikers ze kunnen zien en ermee kunnen interageren in gepubliceerde spellen. Nadat Roblox geïmporteerde activa heeft goedgekeurd, kun je ervoor kiezen om het eigendom van hun gebruik op het platform te behouden of ze openbaar beschikbaar te maken zoals beschreven in [Activa machtigingen](#activa-machtigingen) .

## [Activatypes](#activatypes)[](#activatypes)

Alle [activatypes](/docs/nl-nl/reference/engine/enums/AssetType)  die beschikbaar zijn op het platform vallen over het algemeen in een van de drie categorieën:

-

Activa die overeenkomen met projectniveau-items. Je kunt deze activa vinden en configureren voor specifieke spellen op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

-

Activa die objecten zijn, of die het uiterlijk of gedrag van objecten binnen plaatsen veranderen. Je kunt deze activa [importeren](#activa-beheer)  of ze vinden in de [Creator Store](https://create.roblox.com/store) .

-

Activa die het lichaam, kleding of animatie van avatars en niet-speelbare personages veranderen. Je kunt deze activa vinden in de [Marketplace](https://www.roblox.com/catalog) .

Elk activatype werkt anders, afhankelijk van waar het zich op het platform bevindt. Zie de volgende secties voor informatie over hoe je elk activatype kunt gebruiken voor [spellen](#voor-spellen) , [plaatsen](#voor-plaatsen)  en [avatars](#voor-avatars) .

### [Voor spellen](#voor-spellen)[](#voor-spellen)

Er zijn drie activatypes die overeenkomen met projectniveau-items. Deze activatypes zijn uniek voor het spel waar ze aan zijn gekoppeld, wat betekent dat ze niet overdraagbaar zijn naar andere projecten.

-

Plaatsen  — Elk spel heeft een of meer [plaatsen](/docs/nl-nl/projects#plaatsen) , of individuele 3D-werelden. Elke plaats wordt weergegeven door een [datamodel](/docs/nl-nl/projects/data-model)  dat de 3D-wereld en logica van de plaats beschrijft.

-

Badges  — Een [badge](/docs/nl-nl/production/publishing/badges)  is een speciale prijs die je aan gebruikers kunt geven wanneer ze een doel binnen een spel bereiken, zoals het voltooien van een moeilijk doel of het spelen gedurende een bepaalde tijd.

-

Passes  — Een [pass](/docs/nl-nl/production/monetization/passes)  is een monetisatieproduct waarmee je een eenmalige Robux-kosten kunt vragen zodat gebruikers toegang krijgen tot speciale privileges binnen een spel, zoals toegang tot een beperkt gebied, een in-game avatar-item of een permanente power-up.

### [Voor plaatsen](#voor-plaatsen)[](#voor-plaatsen)

In het algemeen zijn er twee categorieën van activatypes voor plaatsen die je kunt [importeren](#activa-beheer)  of vinden in de [Creator Store](https://create.roblox.com/store) :

-

Activa die bestaan als objecten binnen het datamodel, zoals [modellen](/docs/nl-nl/parts/models)  en [meshes](/docs/nl-nl/parts/meshes) .

-

Activa die je toepast als een eigenschap van een object, zoals audio, afbeeldingen, lettertypen en video's.

Voor meer informatie over beide typen activa voor plaatsen, zoals waar en hoe je ze in Studio kunt gebruiken, raadpleeg de volgende tabel.

| Activa Type | | Beschrijving |
| --- | --- |
| Model | | Een [Model](/docs/nl-nl/reference/engine/classes/Model)  is een containerobject voor geometrische groeperingen zoals [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart) , [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart) , en andere [Model](/docs/nl-nl/reference/engine/classes/Model)  objecten. Modellen kunnen ook objecten bevatten zoals [Scripts](/docs/nl-nl/reference/engine/classes/Script) . Wanneer je objecten in Studio groepeert, worden ze automatisch een [Model](/docs/nl-nl/reference/engine/classes/Model)  object. Voor meer informatie, zie [modellen](/docs/nl-nl/parts/models) . |
| Mesh | | Een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  is een type onderdeelobject dat een fysiek gesimuleerde aangepaste mesh bevat. Voor meer informatie, zie [meshes](/docs/nl-nl/parts/meshes) . |
| Audio | | Een [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  instantie laadt en speelt een audiobestand en geeft de output door via een [Wire](/docs/nl-nl/reference/engine/classes/Wire)  naar een [AudioEmitter](/docs/nl-nl/reference/engine/classes/AudioEmitter)  of [AudioDeviceOutput](/docs/nl-nl/reference/engine/classes/AudioDeviceOutput) . Voor meer informatie, zie [audio-activa](/docs/nl-nl/audio/assets)  en [audio-objecten](/docs/nl-nl/audio/objects) . |
| Afbeelding | | Afbeeldingen worden op verschillende manieren binnen een plaats gebruikt, waaronder [texturen/decal](/docs/nl-nl/parts/textures-decals)  op onderdelen, [afbeelding labels](/docs/nl-nl/ui/labels) , [mesh texturen](/docs/nl-nl/parts/meshes#adding-textures) , texturen voor [aangepaste materialen](/docs/nl-nl/parts/materials) , texturen voor [speciale effecten](/docs/nl-nl/environment#special-effects) , en meer. |
| Lettertype | | [TextButton](/docs/nl-nl/reference/engine/classes/TextButton) , [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel) , en [TextBox](/docs/nl-nl/reference/engine/classes/TextBox)  objecten tonen typografie in een specifieke stijl wanneer je een lettertype activa ID toepast. Je kunt geen lettertypen importeren, maar de [Creator Store](https://create.roblox.com/store)  biedt meer dan 80 verschillende lettertypen voor jouw gebruik. |
| Video | | Een [VideoFrame](/docs/nl-nl/reference/engine/classes/VideoFrame)  object toont een video via zijn [Video](/docs/nl-nl/reference/engine/classes/VideoFrame#Video)  activa-eigenschap. Zie [video frames](/docs/nl-nl/ui/video-frames)  voor meer informatie. |

### [Voor avatars](#voor-avatars)[](#voor-avatars)

Er zijn drie categorieën van activatypes voor avatars die je kunt vinden in de [Marketplace](https://www.roblox.com/catalog)  en aan avatars kunt uitrusten:

-

Lichaamsdelen  — Activa die secties van het avatar karaktermodel vertegenwoordigen, zoals het hoofd, de romp of de benen.

-

Kleding en Accessoires  — Activa die kleding en accessoires bovenop lichaamsdelen vertegenwoordigen.

-

Animaties  — Activa die het avatar karaktermodel animeren, zoals hoe het rent, springt of zwemt.

Elk [karakter](/docs/nl-nl/characters)  model bevat een [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  object met activa-ID's voor de lichaamsdelen, kleding, accessoires en animaties van het karakter. Standaard verwijst een speelbare karakter van een gebruiker naar hun persoonlijke Roblox-avatar, maar je kunt een aangepaste [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  toepassen indien gewenst. Voor meer informatie, zie [karakter uiterlijk](/docs/nl-nl/characters/appearance) .

## [Pakketten](#pakketten)[](#pakketten)

Binnen Studio kun je enkele activa of activa-hiërarchieën omzetten in pakketten  en ze in meerdere spellen hergebruiken, zodat je het activa-beheer voor je hele team of voor meerdere projecten kunt optimaliseren. Wanneer een pakket wordt bijgewerkt, kunnen jij of je teamleden specifieke kopieën bijwerken naar de meest actuele versie, alle kopieën in een spel bijwerken, of specifieke kopieën instellen om automatisch bij te werken.

Voor meer informatie, zie [pakketten](/docs/nl-nl/projects/assets/packages) .

## [Activa URI's](#activa-uris)[](#activa-uris)

Activa en andere inhoud die buiten de huidige plaats zijn opgeslagen, worden geïdentificeerd door Uniform Resource Identifiers  (URI's) die geformatteerde strings zijn die naar een bestand verwijzen dat online is opgeslagen, binnen het Roblox-applicatiepakket, of opgeslagen op het apparaat van de cliënt.

De basisstructuur is een schema  gevolgd door ://  en een pad  dat varieert afhankelijk van het schema.

[Schema]://[Pad]

De Roblox Engine ondersteunt verschillende aangepaste URI-schema's voor het verwijzen naar inhoud die op het platform is opgeslagen.

### [rbxassetid](#rbxassetid)[](#rbxassetid)

rbxassetid  verwijst naar een door de gebruiker geüpload activa op Roblox. Dit formaat is een gangbare standaard voor eigenschappen zoals [Decal.ColorMapContent](/docs/nl-nl/reference/engine/classes/Decal#ColorMapContent) , [ParticleEmitter.Texture](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Texture) , en [AudioPlayer.Asset](/docs/nl-nl/reference/engine/classes/AudioPlayer#Asset) .

rbxassetid://7229442422

![Een decal activa van een jonge vrouw met een knop voor een oog.](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Texture-Example-Grafitti04.png)

rbxassetid://3845386987

![Drie deeltjesemitteren stoten rode, blauwe en gele deeltjes uit over potactiva die bovenop een stenen toren staan. De rode deeltjes zijn gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Texture-Indicated.jpg)

rbxassetid://9125402735

### [rbxasset](#rbxasset)[](#rbxasset)

rbxasset  verwijst naar de inhoudsmap van Roblox op het apparaat van de gebruiker, bijvoorbeeld:

rbxasset://textures/face.png

De locatie van de inhoudsmap hangt af van het besturingssysteem van de gebruiker:

Windows Mac

%LOCALAPPDATA%\Roblox\Versions\<version>\content
 (alternatief C:\Program Files (x86)\Roblox\Versions\<version>\content )

### [rbxthumb](#rbxthumb)[](#rbxthumb)

rbxthumb  verwijst naar een thumbnail-afbeelding voor de opgegeven activa. Het stringformaat neemt een thumbnail-type (type ), een activa-ID (id ), en breedte/hoogte (w / h ).

rbxthumb://type=Asset&id=24813339&w=150&h=150

| Type (type ) | | Verwachte id  Waarde | | Ondersteunde Groottes (w × h ) |
| Asset | | ID voor een 2D of 3D activa | | 150×150, 420×420 |
| Avatar | | ID voor een Roblox-gebruiker ([Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId) ) | | 48×48, 60×60, 100×100, 150×150, 180×180, 352×352, 420×420, 720×720 |
| AvatarBust | | ID voor een Roblox-gebruiker ([Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId) ) | | 50×50, 60×60, 75×75, 100×100, 150×150, 180×180, 352×352, 420×420 |
| AvatarHeadShot | | ID voor een Roblox-gebruiker ([Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId) ) | | 48×48, 60×60, 100×100, 150×150, 180×180, 352×352, 420×420 |
| BadgeIcon | | ID voor een [badge](/docs/nl-nl/production/publishing/badges#locating-badge-ids) | | 150×150 |
| BundleThumbnail | | ID voor een [Marketplace](https://www.roblox.com/catalog)  bundel zoals een [karakter](https://www.roblox.com/catalog?Category=17) , [hoofd](https://www.roblox.com/catalog?Category=4&Subcategory=66) , of [schoenen](https://www.roblox.com/catalog?Category=3&Subcategory=64) | | 150×150, 420×420 |
| FontFamily | | ID voor een lettertype in de [Creator Store](/docs/nl-nl/production/creator-store)  of [Toolbox](/docs/nl-nl/projects/assets/toolbox)  inventaris | | 1200×80 |
| GameIcon | | ID voor een spel ([DataModel.GameId](/docs/nl-nl/reference/engine/classes/DataModel#GameId) ); toont het [icoon](/docs/nl-nl/production/publishing/experience-icons)  van het spel | | 50×50, 150×150 |
| GamePass | | ID voor een [pass](/docs/nl-nl/production/monetization/passes#locating-pass-ids) | | 150×150 |
| GameThumbnail | | ID voor een spel ([DataModel.PlaceId](/docs/nl-nl/reference/engine/classes/DataModel#PlaceId) ); toont de primaire [thumbnail](/docs/nl-nl/production/publishing/thumbnails)  van het spel | | 256×144, 384×216, 480×270, 576×324, 768×432 |
| GroupIcon | | ID voor een [groep](/docs/nl-nl/projects/groups) | | 150×150, 420×420 |
| Outfit | | ID verzameld uit een [OutfitPages](/docs/nl-nl/reference/engine/classes/OutfitPages)  tabel | | 150×150, 420×420 |

Pas Avatar Hoofdshot Thumbnail toe

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local playerGui = player.PlayerGui

local screenGui = Instance.new("ScreenGui")

screenGui.Parent = playerGui

local imageLabel = Instance.new("ImageLabel")

imageLabel.AnchorPoint = Vector2.new(0, 0)

imageLabel.Size = UDim2.new(0, 150, 0, 150)

imageLabel.Position = UDim2.new(0, 16, 0, 16)

imageLabel.BorderSizePixel = 0

imageLabel.BackgroundColor3 = Color3.new(0, 0, 0)

imageLabel.BackgroundTransparency = 0.8

imageLabel.Parent = screenGui

local success, content, isReady = pcall(function()

	return Players:GetUserThumbnailAsync(player.UserId, Enum.ThumbnailType.HeadShot, Enum.ThumbnailSize.Size352x352)

end)

if success then

	-- Pas thumbnailinhoud toe aan afbeeldingslabel

	imageLabel.Image = content

	-- Crop thumbnail naar cirkel

	local corner = Instance.new("UICorner")

	corner.CornerRadius = UDim.new(1, 0)

	corner.Parent = imageLabel

end

```

### [rbxgameasset](#rbxgameasset)[](#rbxgameasset)

rbxgameasset  verwijst naar een activa geüpload via de [Asset Manager](/docs/nl-nl/projects/assets/manager) . Het maakt toegang mogelijk tot activa via een gebruiksvriendelijke naam in plaats van ID, dus als je een afbeelding uploadt met de naam Potion.png , kun je deze verwijzen als:

rbxgameasset://Images/Potion

In het bovenstaande voorbeeld is Images  de categorie/map die verschijnt in de [Asset Manager](/docs/nl-nl/projects/assets/manager)  en Potion  is de activanaam, minus de extensie.

rbxgameasset  werkt alleen voor het huidige spel. Als je een bovenliggend object dat het activa gebruikt in een ander spel plakt, zal het activa niet laden (of zal een ander activa laden als je er een met dezelfde naam in dat andere spel hebt geüpload). Als je een activa nodig hebt die in meerdere spellen werkt, gebruik dan rbxassetid  in plaats van rbxgameasset .

### [rbxhttp](#rbxhttp)[](#rbxhttp)

rbxhttp  is een afkorting voor [ContentProvider.BaseUrl](/docs/nl-nl/reference/engine/classes/ContentProvider#BaseUrl) , bijvoorbeeld:

rbxhttp://Thumbs/Avatar.ashx?x=100&y=100&format=png

### [rbxtemp](#rbxtemp)[](#rbxtemp)

rbxtemp  stelt je in staat om [Files](/docs/nl-nl/reference/engine/classes/File)  te verwijzen. Gebruik [File:GetTemporaryId()](/docs/nl-nl/reference/engine/classes/File#GetTemporaryId)  om een geldige rbxtemp  URL te genereren. Bijvoorbeeld:

rbxtemp://1

### [https / http](#https--http)[](#https--http)

https  of http  verwijst naar de exacte locatie van iets op het internet. Het werkt alleen op door Roblox goedgekeurde domeinen en geeft een foutmelding als je het elders gebruikt.

https://www.roblox.com/asset/?id=9723979220

## [Activa machtigingen](#activa-machtigingen)[](#activa-machtigingen)

De privacystatus van een activa bepaalt wie toestemming heeft om de activa binnen hun spellen te gebruiken. Standaard zijn alle activa privé  wanneer jij of je [groep](/docs/nl-nl/projects/groups)  leden ze in Studio importeren. Als je iedereen toegang wilt geven tot de activa-ID, moet je de activa verspreiden naar de [Creator Store](https://create.roblox.com/store) .

Speciale privacyregels en workflows zijn van toepassing op audio  en video  activa. Zie [activa privacy](/docs/nl-nl/projects/assets/privacy)  voor details over het delen van deze activatypes onder vrienden en spellen.

## [Activa moderatie](#activa-moderatie)[](#activa-moderatie)

Roblox voert zowel menselijke als geautomatiseerde activa-moderatie uit op een proactieve en reactieve basis om ervoor te zorgen dat activa voldoen aan de [Gemeenschapsregels](https://en.help.roblox.com/hc/articles/203313410) , [Gebruiksvoorwaarden](https://en.help.roblox.com/hc/articles/115004647846) , en [Intellectuele Eigendom richtlijnen](/docs/nl-nl/production/publishing/ip-guidelines) . Als een activa deze moderatiebeleid schendt, zoals het opnemen van discriminerende of volwassen inhoud, markeert en verwijdert het moderatorteam de activa om gebruikers te beschermen tegen schadelijke of niet-conforme inhoud. Dit proces gebeurt doorgaans binnen enkele uren nadat je de activa hebt geïmporteerd.

Als een activa nog in de moderatiewachtrij staat wanneer je je spel publiceert, kunnen gebruikers de activa niet zien of ermee interageren totdat Roblox deze goedkeurt. Als de activa niet door de moderatie komt, ontvang je een [melding](https://en.help.roblox.com/hc/en-us/articles/360020870412-Understanding-Moderation-Messages)  waarin wordt uitgelegd waarom de activa niet op het platform kan staan in de huidige staat. Voor meer informatie, zie Werken met Activa - Activa Moderatie.

Om de veiligheid en beleefdheid van de gemeenschap te waarborgen, kan Roblox spellen verwijderen en/of accounts beëindigen die opzettelijk niet-conforme activa importeren of publiceren.

## [Activa beheer](#activa-beheer)[](#activa-beheer)

Roblox biedt verschillende tools om je activa te importeren, op te slaan en te publiceren:

| Tool | | Beschrijving |
| [Asset Manager](/docs/nl-nl/projects/assets/manager) | | Importeert en slaat [afbeeldingen](/docs/nl-nl/parts/textures-decals) , [meshes](/docs/nl-nl/parts/meshes) , [audio](/docs/nl-nl/audio/assets) , en meer op. Toont alleen activa die je in het momenteel geopende spel hebt geïmporteerd. |
| [Toolbox](/docs/nl-nl/projects/assets/toolbox) | | Bewaart elke activa die jij of je [groepen](/docs/nl-nl/projects/groups)  ooit in Studio hebben geïmporteerd, ongeacht welk spel je momenteel geopend hebt. Bevat ook activa van de [Creator Store](https://create.roblox.com/store) , zodat je snel door gebruikers gegenereerde activa rechtstreeks in je spellen kunt plaatsen. |
| [Importer](/docs/nl-nl/studio/importer) | | Importeert 3D-modellen van derde partij modelleringstools als een aangepaste [Model](/docs/nl-nl/reference/engine/classes/Model)  instantie.  |

## [Archiveer activa](#archiveer-activa)[](#archiveer-activa)

Om verder te helpen met organisatie, kun je de meeste activatypes archiveren in de sectie Creations  ⟩ Development Items  van het [Creator Dashboard](https://create.roblox.com/dashboard/creations) . Om een item te archiveren, beweeg je de muis over de thumbnail van een activa, klik je op de ⋯  knop, en selecteer je Archive  in het contextmenu.

 ![Optiesknop aangegeven voor een activa.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Options-Button-Asset.png)

Nadat je een activa hebt gearchiveerd, verdwijnt deze van de website en is deze niet langer bruikbaar of zichtbaar in Roblox-spellen, inclusief je eigen.

Voor meer informatie over hoe archiveren werkt met Marketplace-items, zie [moderatie](/docs/nl-nl/marketplace/moderation#archiveren-van-assets) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
