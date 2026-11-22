<!-- Source: https://create.roblox.com/docs/nl-nl/production/publishing/accessibility -->

Toegankelijkheidsrichtlijnen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Game-ontwerp](/docs/nl-nl/production/game-design)
6. /
7. Je ervaring bouwen

# Toegankelijkheidsrichtlijnen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Toegankelijkheid  is de praktijk van het ontwerpen van producten en diensten die bruikbaar zijn voor mensen met een handicap. Recente statistieken geven aan dat meer dan 26% van de mensen een of andere vorm van handicap heeft, dus het toegankelijk maken van je Roblox-spel kan je helpen een breder publiek te bereiken.

## [Tekstgrootte](#tekstgrootte)[](#tekstgrootte)

Spelers kunnen het moeilijk vinden om kleine tekst te lezen. Vergelijk het volgende in-game winkelmenu met een vervaging toegepast, wat simuleert hoe het eruit zou kunnen zien voor iemand met een verminderd gezichtsvermogen.

Zichtbaar Laag Gezicht

![Voorbeeld van kleine tekst op gebruikersinterface](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Text-Size-SM.jpg)

Als je de grootte van de kleinere letterlabels vergroot, zal het voor de meeste spelers duidelijker zijn.

Zichtbaar Laag Gezicht

![Voorbeeld van grotere tekst op gebruikersinterface](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Text-Size-LG.jpg)

## [Kleurcontrast](#kleurcontrast)[](#kleurcontrast)

Spelers kunnen het moeilijk vinden om lichte tekst op een lichte achtergrond te lezen, of donkere tekst op een donkere achtergrond. Om de toegankelijkheid te verbeteren, wordt aanbevolen om tekst- en achtergrondkleuren te kiezen met voldoende kleurcontrast.

![Voorbeeld van UI-elementen met hoog contrast](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Color-Contrast-High.png)

Hoog contrast

![Voorbeeld van UI-elementen met laag contrast](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Color-Contrast-Low.png)

Laag contrast

## [Kleurafhankelijkheid](#kleurafhankelijkheid)[](#kleurafhankelijkheid)

Meer dan 5% van de mensen in de wereld heeft een vorm van kleurenblindheid. Hoewel het zeldzaam is dat iemand alleen  in zwart-wit ziet, stel je voor dat je een spel in grijstinten bekijkt:

Geen Kleurblindheid Kleurblindheid

![Voorbeeld gebruikersinterface weergegeven in volle kleur](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Color-Normal.jpg)

Door de afbeelding te wijzigen om verschillende symbolen  naast kleuren te gebruiken, kunnen meer spelers het verschil in gameplay en in andere contexten zien:

Geen Kleurblindheid Kleurblindheid

![Voorbeeld gebruikersinterface weergegeven in volle kleur](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Color-Symbols-Normal.jpg)

## [Geluidafhankelijkheid](#geluidafhankelijkheid)[](#geluidafhankelijkheid)

Geluid is een uitstekende aanvulling voor meeslepende spellen, maar spelers met gehoorproblemen of iedereen die het volume uit heeft, zal in-game gebeurtenissen die alleen  met geluid worden overgebracht, verwarrend vinden.

Overweeg de volgende scène waarin een bel die rinkelt alleen door geluid wordt aangegeven, en vervolgens wordt aangegeven met zowel geluid als  visuele hulpmiddelen.

## [Speler voorkeuren](#speler-voorkeuren)[](#speler-voorkeuren)

Verschillende visuele instellingen zijn beschikbaar voor spelers vanuit de Roblox- en in-game Instellingen  menu's, inclusief [voorkeursdoorzichtigheid](#voorkeursdoorzichtigheid) , [voorkeurs tekstgrootte](#voorkeurs-tekstgrootte) , en [verminderde beweging](#verminderde-beweging) . Voor optimale toegankelijkheid zou je [gebruikersinterface](/docs/nl-nl/ui)  aan elke voorkeur moeten voldoen.

### [Voorkeursdoorzichtigheid](#voorkeursdoorzichtigheid)[](#voorkeursdoorzichtigheid)

De Achtergrond Doorzichtigheid  instelling komt overeen met de [GuiService.PreferredTransparency](/docs/nl-nl/reference/engine/classes/GuiService#PreferredTransparency)  eigenschap. Een waarde van 1  geeft aan dat de speler de standaard achtergronddoorzichtigheid verkiest, terwijl een waarde van 0  aangeeft dat de speler de voorkeur geeft aan volledig ondoorzichtige (niet-doorzichtige) achtergronddoorzichtigheid voor verbeterde leesbaarheid en contrast.

Het vermenigvuldigen van de [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundTransparency)  van een UI-element met [PreferredTransparency](/docs/nl-nl/reference/engine/classes/GuiService#PreferredTransparency)  is de aanbevolen manier om deze instelling te gebruiken; achtergronden worden ondoorzichtiger naarmate [PreferredTransparency](/docs/nl-nl/reference/engine/classes/GuiService#PreferredTransparency)  dichter bij 0  komt.

1.

Gebruik het [tagging](/docs/nl-nl/studio/properties#instantie-tags)  systeem, pas een tag van TransparentBack  toe op alle UI-items met [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundTransparency)  zoals [TextLabels](/docs/nl-nl/reference/engine/classes/TextLabel)  of [Frames](/docs/nl-nl/reference/engine/classes/Frame) .

![Vier TextLabel-elementen met verschillende niveaus van BackgroundTransparency](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Preferred-Transparency-Labels.png) Vier [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  elementen met verschillende [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundTransparency)  niveaus

2.

Plak de volgende code in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  binnen [StarterPlayerScripts](/docs/nl-nl/reference/engine/classes/StarterPlayerScripts) .

Dynamische Aanpassing voor Voorkeursdoorzichtigheid

```

local GuiService = game:GetService("GuiService")

local CollectionService = game:GetService("CollectionService")

local TAG = "TransparentBack"

local transparentBackObjects = {}

local function onInstanceAdded(object)

	if object.BackgroundTransparency then

		local defaultTransparency = object.BackgroundTransparency

		transparentBackObjects[object] = defaultTransparency

		object.BackgroundTransparency = defaultTransparency * GuiService.PreferredTransparency

	end

end

local function onInstanceRemoved(object)

	transparentBackObjects[object] = nil

end

-- Sla de initiële getagde instanties op

for _, object in CollectionService:GetTagged(TAG) do

	onInstanceAdded(object)

end

-- Detecteer wanneer een getagde instantie wordt toegevoegd of verwijderd

CollectionService:GetInstanceAddedSignal(TAG):Connect(onInstanceAdded)

CollectionService:GetInstanceRemovedSignal(TAG):Connect(onInstanceRemoved)

-- Wanneer de in-game instelling wordt gewijzigd, pas getagde instanties aan

GuiService:GetPropertyChangedSignal("PreferredTransparency"):Connect(function()

	for object, defaultTransparency in transparentBackObjects do

		object.BackgroundTransparency = defaultTransparency * GuiService.PreferredTransparency

	end

end)

```

3.

Test het spel, open het Instellingen  menu en pas de Achtergrond Doorzichtigheid  aan. De getagde UI-elementen zouden moeten updaten tussen hun standaard [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundTransparency)  en volledig ondoorzichtig.

Standaard 50% Meer Ondoorzichtig Volledig Ondoorzichtig

![](https://prod.docsiteassets.roblox.com/assets/publishing/accessibility/Preferred-Transparency-Default.png)

### [Voorkeurs tekstgrootte](#voorkeurs-tekstgrootte)[](#voorkeurs-tekstgrootte)

De Tekstgrootte  instelling komt overeen met de [GuiService.PreferredTextSize](/docs/nl-nl/reference/engine/classes/GuiService#PreferredTextSize)  eigenschap die standaard is ingesteld op [Medium](/docs/nl-nl/reference/engine/enums/PreferredTextSize#Medium) . Spelers kunnen ervoor kiezen om de tekstgrootte te vergroten via de font-rendering pipeline van de engine naar [Large](/docs/nl-nl/reference/engine/enums/PreferredTextSize#Large) , [Larger](/docs/nl-nl/reference/engine/enums/PreferredTextSize#Larger) , of [Largest](/docs/nl-nl/reference/engine/enums/PreferredTextSize#Largest) .

Bij het werken met UI-elementen, let op de volgende gedragingen:

-

Tekst die is beperkt tot een minimum en/of maximum grootte via een [UITextSizeConstraint](/docs/nl-nl/reference/engine/classes/UITextSizeConstraint)  zal niet  krimpen onder of uitbreiden boven de ingestelde [MinTextSize](/docs/nl-nl/reference/engine/classes/UITextSizeConstraint#MinTextSize) /[MaxTextSize](/docs/nl-nl/reference/engine/classes/UITextSizeConstraint#MaxTextSize) , ongeacht de tekstgrootte-instelling van de speler.

-

Wanneer [TextScaled](/docs/nl-nl/reference/engine/classes/TextLabel#TextScaled)  is ingeschakeld voor een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel#TextScaled)  of [TextButton](/docs/nl-nl/reference/engine/classes/TextButton#TextScaled) , zal de tekst van het element niet  worden geschaald door de [PreferredTextSize](/docs/nl-nl/reference/engine/classes/GuiService#PreferredTextSize)  waarde.

-

UI-elementen met [AutomaticSize](/docs/nl-nl/reference/engine/classes/GuiObject#AutomaticSize)  ingeschakeld zullen krimpen/groeien naarmate [PreferredTextSize](/docs/nl-nl/reference/engine/classes/GuiService#PreferredTextSize)  afneemt/toeneemt (de grenzen van het element zullen worden aangepast om de vergrote tekst te passen).

-

Wanneer [TextWrapped](/docs/nl-nl/reference/engine/classes/TextLabel#TextWrapped)  is ingeschakeld voor een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel#TextWrapped)  of [TextButton](/docs/nl-nl/reference/engine/classes/TextButton#TextWrapped) , zal de tekst van het element naar extra regels worden gewikkeld naarmate [PreferredTextSize](/docs/nl-nl/reference/engine/classes/GuiService#PreferredTextSize)  toeneemt, binnen de limieten van de absolute grootte van het element.

-

De resultaten die worden geretourneerd door [TextService:GetTextSize()](/docs/nl-nl/reference/engine/classes/TextService#GetTextSize)  en [TextService:GetTextBoundsAsync()](/docs/nl-nl/reference/engine/classes/TextService#GetTextBoundsAsync)  houden rekening met wijzigingen met betrekking tot [PreferredTextSize](/docs/nl-nl/reference/engine/classes/GuiService#PreferredTextSize) .

### [Verminderde beweging](#verminderde-beweging)[](#verminderde-beweging)

De Verminder Beweging  schakelaar komt overeen met de [GuiService.ReducedMotionEnabled](/docs/nl-nl/reference/engine/classes/GuiService#ReducedMotionEnabled)  eigenschap. Een waarde van true  geeft aan dat de speler wil dat bewegingseffecten via [UI animaties/tweens](/docs/nl-nl/ui/animation)  worden verminderd of volledig verwijderd.

Een basisaanpak om beweging uit UI-tweens te verwijderen, is om de [Time](/docs/nl-nl/reference/engine/datatypes/TweenInfo#Time)  parameter van een [TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo)  in te stellen op 0  wanneer [ReducedMotionEnabled](/docs/nl-nl/reference/engine/classes/GuiService#ReducedMotionEnabled)  true  is, waardoor het UI-object onmiddellijk naar zijn doel springt.

UI Tween Snap-to-Target voor Verminderde Beweging

```

local GuiService = game:GetService("GuiService")

local Players = game:GetService("Players")

local TweenService = game:GetService("TweenService")

local player = Players.LocalPlayer

local playerGui = player.PlayerGui

local menuUI = playerGui:WaitForChild("MenuUI")

-- Gebruik tween tijd van 0.75 seconden tenzij verminderde beweging is ingeschakeld

local TWEEN_TIME = if GuiService.ReducedMotionEnabled then 0 else 0.75

local tweenInfo = TweenInfo.new(TWEEN_TIME, Enum.EasingStyle.Cubic, Enum.EasingDirection.Out)

local tween = TweenService:Create(menuUI.SettingsFrame, tweenInfo, {Position = UDim2.fromScale(0.5, 0.5)})

tween:Play()

```

Als alternatief voor instant springen, kun je [ReducedMotionEnabled](/docs/nl-nl/reference/engine/classes/GuiService#ReducedMotionEnabled)  met meer onderscheidende true / false  logica behandelen. Bijvoorbeeld, de volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  gebruikt standaard bewegings-tweening, maar schakelt over naar vervagen voor spelers die verminderde beweging inschakelen, wat resulteert in een elegantere overgang zonder positionele beweging.

Fallback naar Fade Tween voor Verminderde Beweging

```

local GuiService = game:GetService("GuiService")

local Players = game:GetService("Players")

local TweenService = game:GetService("TweenService")

local player = Players.LocalPlayer

local playerGui = player.PlayerGui

local menuUI = playerGui:WaitForChild("MenuUI")

-- Maak een canvasgroep om alle kinderen uniform te tweenen

local canvasGroup = Instance.new("CanvasGroup")

canvasGroup.Size = UDim2.fromScale(1, 1)

canvasGroup.BackgroundTransparency = 1

canvasGroup.Parent = menuUI

-- Voeg kinderen toe aan canvasgroep

menuUI.SettingsFrame.Parent = canvasGroup

local tweenInfo = TweenInfo.new(0.75, Enum.EasingStyle.Cubic, Enum.EasingDirection.Out)

local tween

-- Gebruik vervagende tween voor verminderde beweging, of een bewegings-tween anders

if GuiService.ReducedMotionEnabled then

	-- Stel canvasgroep aanvankelijk in op volledig transparant (onzichtbaar)

	canvasGroup.GroupTransparency = 1

	-- Vervag canvasgroep in

	tween = TweenService:Create(canvasGroup, tweenInfo, {GroupTransparency = 0})

else

	-- Stel canvasgroep aanvankelijk buiten het scherm in

	canvasGroup.Position = UDim2.fromScale(0, -1)

	-- Beweeg canvasgroep op het scherm

	tween = TweenService:Create(canvasGroup, tweenInfo, {Position = UDim2.fromScale(0, 0)})

end

tween:Play()

```

## [Volume-instellingen](#volume-instellingen)[](#volume-instellingen)

Verschillende geluiden die tegelijkertijd worden afgespeeld, kunnen overweldigend, afleidend of moeilijk te onderscheiden zijn. Het bieden van volumeregelingen voor verschillende "groepen" audio, zoals geluidseffecten, muziek en spraak, stelt gebruikers in staat om hun spel aan te passen en zich te concentreren op wat ze nodig hebben.

Overweeg het volgende voorbeeld van een zeer luidruchtig spel waarin de gebruiker de volumes van muziek en geluidseffecten afzonderlijk kan aanpassen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
