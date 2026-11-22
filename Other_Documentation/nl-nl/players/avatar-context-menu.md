<!-- Source: https://create.roblox.com/docs/nl-nl/players/avatar-context-menu -->

Avatar Contextmenu | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelers](/docs/nl-nl/players)
6. /
7. UI voor spelers

# Avatar Contextmenu

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het Avatar Contextmenu  (ACM) maakt het gemakkelijker voor gebruikers om met elkaar te communiceren. Wanneer het ACM is ingeschakeld in jouw spel, kan een gebruiker naar het personage van een andere gebruiker lopen en op hen klikken om een klein menu met verschillende standaardopties te openen. De speler kan een vriendschapsverzoek sturen, een privégesprek beginnen, het profiel van de gebruiker bekijken of zwaaien.

Nadat je het [ACM hebt ingeschakeld](#schakel-het-avatar-contextmenu-in)  in jouw spel, kun je het ACM op de volgende manieren aanpassen:

-

Programmatig [openen en sluiten](#open-en-sluit-het-acm)  van het ACM voor specifieke gebruikers.

-

[Toevoegen](#menu-opties-toevoegen)  van aangepaste opties en [verwijderen](#menu-opties-verwijderen)  van bestaande opties in het ACM.

-

[Het uiterlijk van het ACM aanpassen](#pas-het-menu-uiterlijk-aan)  om een unieke gebruikersinterface te creëren.

## [Schakel het Avatar Contextmenu in](#schakel-het-avatar-contextmenu-in)[](#schakel-het-avatar-contextmenu-in)

Het Avatar Contextmenu moet worden ingeschakeld met de [StarterGui:SetCore()](/docs/nl-nl/reference/engine/classes/StarterGui#SetCore)  optie "AvatarContextMenuEnabled" in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) . Het ACM wordt het beste gebruikt in spellen waar er geen vooraf gedefinieerd gedrag is voor het klikken op andere gebruikers.

Gebruik het volgende codevoorbeeld om het ACM in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  in te schakelen:

```

-- Voer uit in een LocalScript, bij voorkeur binnen "StarterPlayerScripts"

local StarterGui = game:GetService("StarterGui")

StarterGui:SetCore("AvatarContextMenuEnabled", true)

```

Als je moet detecteren of het ACM is ingeschakeld, kun je de volgende code gebruiken om een boolean terug te geven over de huidige status van het ACM:

```

---Geeft een boolean terug die aangeeft of het ACM momenteel is ingeschakeld.

StarterGui:GetCore(AvatarContextMenuEnabled)

```

## [Open en sluit het ACM](#open-en-sluit-het-acm)[](#open-en-sluit-het-acm)

Zodra het is ingeschakeld, kun je het ACM programmatig openen en sluiten met [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) .

Om het ACM programmatig te openen, gebruik je de volgende code:

```

-- Gebruik StarterGui:SetCore waar targetPlayer een geldig Player-object is

StarterGui:SetCore("AvatarContextMenuTarget", targetPlayer)

```

Om het ACM programmatig te sluiten, gebruik je de volgende code:

```

StarterGui:SetCore("AvatarContextMenuTarget", nil)

```

## [Menu-opties](#menu-opties)[](#menu-opties)

Je kunt [acties toevoegen](#menu-opties-toevoegen)  en [verwijderen](#menu-opties-verwijderen)  via scripting. Standaard heeft het menu de volgende opties:

| Menu-optie | | Beschrijving |
| --- | --- |
| Vriend | | Stuurt een vriendschapsverzoek naar de geselecteerde gebruiker. |
| Chat | | Opent een privégesprek met de geselecteerde gebruiker in de in-game chat. |
| Bekijk | | Opent een venster om het uiterlijk van de geselecteerde gebruiker te inspecteren. |
| Zwaai | | Start een zwaai-animatie naar de geselecteerde gebruiker. |

Zodra het ACM is geopend, kan de gebruiker scrollen en andere gebruikers selecteren op de personage-selectiecarrousel. Personages worden gesorteerd op afstand tot het geselecteerde personage. Het menu wordt alleen bijgewerkt wanneer het is geopend en de lijst met beschikbare gebruikers zal herhalen bij het scrollen.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/context-menu/ACM-User-Selector.png)

### [Menu-opties toevoegen](#menu-opties-toevoegen)[](#menu-opties-toevoegen)

Zodra het is ingeschakeld, kunnen spel-specifieke acties aan het ACM worden toegevoegd. Een spel kan bijvoorbeeld handelsverzoeken, opties om toe te voegen aan een groep, of andere speciale interacties toestaan.

Het volgende voorbeeld laat zien hoe je een aangepaste actie aan het Avatar Contextmenu kunt toevoegen:

```

local Players = game:GetService("Players")

local StarterGui = game:GetService("StarterGui")

local player = Players.LocalPlayer

-- Verbind een functie met een "BindableEvent"

local bindableEvent = Instance.new("BindableEvent")

local function onCustomACMAction(targetPlayer)

	-- Op dit punt kun je InvokeServer() aanroepen op een RemoteFunction om de server te waarschuwen van de selectie

	print("ACM-evenement geselecteerd door " .. player.Name .. " op " .. targetPlayer.Name)

end

bindableEvent.Event:Connect(onCustomACMAction)

-- Voeg de ACM-optie toe met SetCore() met "AddAvatarContextMenuOption"

local options = {"Aangepaste ACM Actie", bindableEvent}

StarterGui:SetCore("AddAvatarContextMenuOption", options)

```

### [Menu-opties verwijderen](#menu-opties-verwijderen)[](#menu-opties-verwijderen)

Je kunt aangepaste en de standaard Vriend, Chat, Bekijk en Zwaai opties uit het ACM verwijderen door de naam van de aangepaste actie of de standaard [Enum.AvatarContextMenuOption](/docs/nl-nl/reference/engine/enums/AvatarContextMenuOption)  enum te verwijzen.

Gebruik de volgende code om een standaard en aangepaste menu-optie te verwijderen:

```

-- Verwijder de "Aangepaste ACM Actie" optie

StarterGui:SetCore("RemoveAvatarContextMenuOption", "Aangepaste ACM Actie")

-- Verwijder de standaard "Vriend" optie door te verwijzen naar de AvatarContextMenuOption.Friend Enum

StarterGui:SetCore("RemoveAvatarContextMenuOption", Enum.AvatarContextMenuOption.Friend)

```

Je kunt geen wijzigingen aanbrengen in het ACM terwijl het open is. Je code moet verifiëren dat een actie nog steeds relevant is voor het geval de actie uit het menu is verwijderd. Als een marktplaatsgebied bijvoorbeeld een optie toevoegt om handelsverzoeken te sturen, moet je verifiëren dat beide gebruikers zich nog steeds in de marktplaats bevinden.

## [Pas het menu-uiterlijk aan](#pas-het-menu-uiterlijk-aan)[](#pas-het-menu-uiterlijk-aan)

Om het uiterlijk van het Avatar Contextmenu te veranderen, roep je [StarterGui:SetCore()](/docs/nl-nl/reference/engine/classes/StarterGui#SetCore)  aan met de optie "AvatarContextMenuTheme", waarbij je een tabel van parameters en waarden opgeeft om het menu-uiterlijk aan te passen.

De gebruikersinterface van het ACM omvat de volgende secties:

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/context-menu/ACM-Sections-Labeled.png)

A. Naamlabel: De gebruikersnaam van het personage waarmee interactie wordt gehad.

B. Knopframe: Bevat al de ACM-knoppen.

C. Knoppen: Individuele knoppen voor de standaard of aangepaste ACM-acties.

### [Uiterlijkparameters](#uiterlijkparameters)[](#uiterlijkparameters)

Dit zijn de aanpassingsparameters voor het ACM:

#### [Achtergrond](#achtergrond)[](#achtergrond)

| Achtergrondkleur | | Een [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  voor de algehele achtergrond van het ACM (meest nuttig wanneer er geen achtergrondafbeelding wordt gebruikt). |
| Achtergrondtransparantie | | Transparantiewaarde (0–1) voor de algehele achtergrond van het ACM (meest nuttig wanneer er geen achtergrondafbeelding wordt gebruikt). |
| Achtergrondafbeelding | | Een geldige asset ID van een afbeelding voor de achtergrond van het ACM. |
| Achtergrondafbeeldingtransparantie | | Transparantiewaarde (0–1) voor de achtergrondafbeelding. |
| Achtergrondafbeeldingschaaltype | | Een [Enum.ScaleType](/docs/nl-nl/reference/engine/enums/ScaleType)  enum voor het schalen van de achtergrondafbeelding. |
| AchtergrondafbeeldingSliceCenter | | Een [Rect](/docs/nl-nl/reference/engine/datatypes/Rect)  die het midden van een negen-slice afbeelding specificeert wanneer Achtergrondafbeeldingschaaltype is ingesteld op [Enum.ScaleType.Slice](/docs/nl-nl/reference/engine/enums/ScaleType#Slice) . |

#### [Naamlabel](#naamlabel)[](#naamlabel)

| Naamlabelkleur | | Een [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  voor de balk die aangeeft met welke speler interactie wordt gehad. |
| Naamonderstrepingkleur | | Een [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  voor de dunne lijn tussen het naamlabel en de actieknoppen. |

#### [Knopframe](#knopframe)[](#knopframe)

| Knopframekleur | | Een [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  voor de sectie (frame) die de actieknoppen bevat. |
| Knopframetransparantie | | Transparantiewaarde (0–1) voor de knopframe-sectie. |

#### [Knop](#knop)[](#knop)

| Knopkleur | | Een [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  voor de achtergrond van de ACM-actieknoppen. |
| Knoptransparantie | | Transparantiewaarde (0–1) voor de achtergrondkleur van de actieknoppen. |
| Knophangkleur | | Een [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  voor de "hover"-toestand van de actieknoppen. |
| Knophangtransparantie | | Transparantiewaarde (0–1) voor de "hover"-kleur van de actieknoppen. |
| Knoponderstrepingkleur | | Een [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  voor de dunne lijn die elke actieknop scheidt. |
| Knopafbeelding | | Een geldige asset ID van een afbeelding voor de achtergrond van knoppen. |
| Knopafbeeldingschaaltype | | Een [Enum.ScaleType](/docs/nl-nl/reference/engine/enums/ScaleType)  enum voor het schalen van de knopafbeelding. |
| KnopafbeeldingSliceCenter | | Een [Rect](/docs/nl-nl/reference/engine/datatypes/Rect)  die het midden van een negen-slice afbeelding specificeert wanneer Knopafbeeldingschaaltype is ingesteld op [Enum.ScaleType.Slice](/docs/nl-nl/reference/engine/enums/ScaleType#Slice) . |

#### [Tekst](#tekst)[](#tekst)

| Lettertype | | Een [Enum.Font](/docs/nl-nl/reference/engine/enums/Font)  enumwaarde voor het naamlabel en de knoptekst. |
| Tekstkleur | | Een [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  voor alle tekst binnen het ACM. |
| Tekstschaal | | Een floatwaarde om de standaard tekstgroottes van elk element te schalen. |

#### [Diverse afbeeldingen](#diverse-afbeeldingen)[](#diverse-afbeeldingen)

| VerlaatMenuAfbeelding | | Een asset ID van een afbeelding voor de sluitknop van het ACM. |
| ScrollLinksAfbeelding | | Een asset ID van een afbeelding voor de carrousel "scroll links" knop. |
| ScrollRechtsAfbeelding | | Een geldige asset ID van een afbeelding voor de carrousel "scroll rechts" knop. |

#### [Geselecteerd personage](#geselecteerd-personage)[](#geselecteerd-personage)

| GeselecteerdPersonageIndicator | | De [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  die boven het hoofd van een personage zweeft om aan te geven dat ze zijn geselecteerd. |

#### [Grootte en positie](#grootte-en-positie)[](#grootte-en-positie)

| Grootte | | Een [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  voor de algehele grootte van het ACM. |
| MinGrootte | | Een [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  die de minimale grootte van het ACM specificeert. |
| MaxGrootte | | Een [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  die de maximale grootte van het ACM specificeert. |
| AspectRatio | | Een floatwaarde die de relatieve breedte en hoogte van het ACM specificeert. |
| AnchorPoint | | De [AnchorPoint](/docs/nl-nl/reference/engine/classes/GuiObject#AnchorPoint)  van het ACM. |
| OnScreenPosition | | Een [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  die de positie op het scherm van het ACM specificeert (de positie waar het naartoe tweent wanneer het wordt geopend). |
| OffScreenPosition | | Een [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  die de positie buiten het scherm van het ACM specificeert (de positie waar het van/naar tweent wanneer het wordt geopend/sluiten). |

### [Voorbeeld aanpassing](#voorbeeld-aanpassing)[](#voorbeeld-aanpassing)

Het volgende codevoorbeeld past het thema van het ACM aan met enkele basisparameters:

```

local StarterGui = game:GetService("StarterGui")

StarterGui:SetCore("AvatarContextMenuTheme", {

	BackgroundImage = "",

	BackgroundTransparency = 0.5,

	BackgroundColor = Color3.fromRGB(111, 145, 242),

	NameTagColor = Color3.fromRGB(0, 0, 200),

	NameUnderlineColor = Color3.fromRGB(213, 233, 255),

	ButtonFrameColor = Color3.fromRGB(15, 24, 65),

	ButtonFrameTransparency = 0.2,

	ButtonUnderlineColor = Color3.fromRGB(213, 233, 255),

	Font = Enum.Font.SciFi

})

```

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/context-menu/Custom-ACM.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
