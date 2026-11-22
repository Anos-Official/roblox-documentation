<!-- Source: https://create.roblox.com/docs/nl-nl/ui/animation -->

UI-animatie/tweens | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)

# UI-animatie/tweens

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In animatie is tweening  het proces van het genereren van tussenliggende frames tussen twee sleutelpunten in een reeks. Bij het ontwerpen van een gebruikersinterface kun je tweening gebruiken om een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  soepel van de ene staat naar de andere over te brengen, zoals:

-

Het soepel vergroten van de grootte van een knop wanneer een gebruiker deze selecteert.

-

UI-menu's in en uit de schermranden schuiven.

-

Een gezondheidsbalk geleidelijk animeren tussen twee breedtes wanneer een gebruiker een gezondheidsboost ontvangt.

## [Enkelvoudige property tweens](#enkelvoudige-property-tweens)[](#enkelvoudige-property-tweens)

### [Positie](#positie)[](#positie)

Om de positie  van een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  te tweenen:

1.

Stel het [AnchorPoint](/docs/nl-nl/reference/engine/classes/GuiObject#AnchorPoint)  voor het object in.

2.

Bepaal de [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  coördinaten voor de doelpositie van het object, gebruikmakend van de schaal  parameters van [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  in plaats van exacte pixelwaarden, zodat het object naar het exacte midden van het scherm tweened.

3.

Geef een [TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo)  en de doelpositie door aan [TweenService:Create()](/docs/nl-nl/reference/engine/classes/TweenService#Create) .

4.

Speel de tween af met [Tween:Play()](/docs/nl-nl/reference/engine/classes/Tween#Play) .

De volgende codefragment verplaatst een [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel)  binnen een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  naar het exacte midden van het scherm:

UI Tween - Positie

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

object.AnchorPoint = Vector2.new(0.5, 0.5)

local targetPosition = UDim2.new(0.5, 0, 0.5, 0)

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {Position = targetPosition})

tween:Play()

```

### [Grootte](#grootte)[](#grootte)

Om de grootte  van een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  te tweenen:

1.

Bepaal de [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  coördinaten voor de doelgrootte van het object, gebruikmakend van de schaal  parameters van [UDim2](/docs/nl-nl/reference/engine/datatypes/UDim2)  in plaats van exacte pixelwaarden, zodat het object naar een relatieve percentage van de schermgrootte tweened.

2.

Bevestig een [UIAspectRatioConstraint](/docs/nl-nl/reference/engine/classes/UIAspectRatioConstraint)  aan het object om de ontworpen aspectverhouding te behouden tijdens het tweenen.

3.

Geef een [TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo)  en de doelgrootte door aan [TweenService:Create()](/docs/nl-nl/reference/engine/classes/TweenService#Create) .

4.

Speel de tween af met [Tween:Play()](/docs/nl-nl/reference/engine/classes/Tween#Play) .

De volgende codefragment schaalt een [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel)  binnen een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  naar 40% van de schermbreedte of -hoogte (wat het kleinste is) vanaf het middelpunt van het object:

UI Tween - Grootte

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

object.AnchorPoint = Vector2.new(0.5, 0.5)

local aspectRatioConstraint = Instance.new("UIAspectRatioConstraint")

aspectRatioConstraint.Parent = object

local targetSize = UDim2.new(0.4, 0, 0.4, 0)

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {Size = targetSize})

tween:Play()

```

### [Rotatie](#rotatie)[](#rotatie)

Om de rotatie  van een [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  te tweenen:

1.

Stel het [AnchorPoint](/docs/nl-nl/reference/engine/classes/GuiObject#AnchorPoint)  voor het object in om rond te draaien.

2.

Bepaal de doel [Rotation](/docs/nl-nl/reference/engine/classes/GuiObject#Rotation)  voor het object.

3.

Geef een [TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo)  en de doelrotatie door aan [TweenService:Create()](/docs/nl-nl/reference/engine/classes/TweenService#Create) .

4.

Speel de tween af met [Tween:Play()](/docs/nl-nl/reference/engine/classes/Tween#Play) .

UI Tween - Rotatie

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

object.AnchorPoint = Vector2.new(0.5, 0.5)

local targetRotation = 45

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {Rotation = targetRotation})

tween:Play()

```

### [Transparantie](#transparantie)[](#transparantie)

Meerdere eigenschappen regelen de UI-transparantie, afhankelijk van het type object. Je kunt elk van deze eigenschappen afzonderlijk tweenen of gecombineerd via een [multi-property tween](#multi-property-tweens) . Alternatief kun je de algehele transparantie van een object tweenen door het in een [CanvasGroup](/docs/nl-nl/reference/engine/classes/CanvasGroup)  te plaatsen en de [GroupTransparency](/docs/nl-nl/reference/engine/classes/CanvasGroup#GroupTransparency)  van de groep te tweenen.

| UI-object | | Eigenschappen |
| --- | --- |
| [Frame](/docs/nl-nl/reference/engine/classes/Frame) | | [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundTransparency) |
| [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel) | | [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundTransparency) , [TextTransparency](/docs/nl-nl/reference/engine/classes/TextLabel#TextTransparency) , [TextStrokeTransparency](/docs/nl-nl/reference/engine/classes/TextLabel#TextStrokeTransparency) |
| [TextButton](/docs/nl-nl/reference/engine/classes/TextButton) | | [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundTransparency) , [TextTransparency](/docs/nl-nl/reference/engine/classes/TextButton#TextTransparency) , [TextStrokeTransparency](/docs/nl-nl/reference/engine/classes/TextButton#TextStrokeTransparency) |
| [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel) | | [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundTransparency) , [ImageTransparency](/docs/nl-nl/reference/engine/classes/ImageLabel#ImageTransparency) |
| [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton) | | [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundTransparency) , [ImageTransparency](/docs/nl-nl/reference/engine/classes/ImageButton#ImageTransparency) |

Als een moderne alternatieve voor [TextLabel.TextStrokeTransparency](/docs/nl-nl/reference/engine/classes/TextLabel#TextStrokeTransparency)  en [TextButton.TextStrokeTransparency](/docs/nl-nl/reference/engine/classes/TextButton#TextStrokeTransparency) , kun je de stroke-transparantie op een [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  object tweenen zoals beschreven in [Stroke](#stroke) .

UI Tween - Afbeelding Transparantie

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

local targetTransparency = 0.8

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {ImageTransparency = targetTransparency})

tween:Play()

```

UI Tween - Canvas Groep Transparantie

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local canvasGroup = ScreenGui:WaitForChild("CanvasGroup")

local targetTransparency = 0.8

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(canvasGroup, tweenInfo, {GroupTransparency = targetTransparency})

tween:Play()

```

### [Kleur](#kleur)[](#kleur)

Meerdere eigenschappen regelen de UI-kleur, afhankelijk van het type object. Je kunt elk van deze eigenschappen afzonderlijk tweenen of gecombineerd via een [multi-property tween](#multi-property-tweens) . Alternatief kun je de algehele kleur van een object tweenen door het in een [CanvasGroup](/docs/nl-nl/reference/engine/classes/CanvasGroup)  te plaatsen en de [GroupColor3](/docs/nl-nl/reference/engine/classes/CanvasGroup#GroupColor3)  van de groep te tweenen.

| UI-object | | Eigenschappen |
| [Frame](/docs/nl-nl/reference/engine/classes/Frame) | | [BackgroundColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundColor3) , [BorderColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BorderColor3) |
| [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel) | | [BackgroundColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundColor3) , [BorderColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BorderColor3) , [TextColor3](/docs/nl-nl/reference/engine/classes/TextLabel#TextColor3) , [TextStrokeColor3](/docs/nl-nl/reference/engine/classes/TextLabel#TextStrokeColor3) |
| [TextButton](/docs/nl-nl/reference/engine/classes/TextButton) | | [BackgroundColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundColor3) , [BorderColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BorderColor3) , [TextColor3](/docs/nl-nl/reference/engine/classes/TextButton#TextColor3) , [TextStrokeColor3](/docs/nl-nl/reference/engine/classes/TextButton#TextStrokeColor3) |
| [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel) | | [BackgroundColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundColor3) , [BorderColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BorderColor3) , [ImageColor3](/docs/nl-nl/reference/engine/classes/ImageLabel#ImageColor3) |
| [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton) | | [BackgroundColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundColor3) , [BorderColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BorderColor3) , [ImageColor3](/docs/nl-nl/reference/engine/classes/ImageButton#ImageColor3) |

Als een moderne alternatieve voor [GuiObject.BorderColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BorderColor3) , [TextLabel.TextStrokeColor3](/docs/nl-nl/reference/engine/classes/TextLabel#TextStrokeColor3) , en [TextButton.TextStrokeColor3](/docs/nl-nl/reference/engine/classes/TextButton#TextStrokeColor3) , kun je de stroke-kleur op een [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  object tweenen zoals beschreven in [Stroke](#stroke) .

UI Tween - Afbeelding Kleur

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

local targetColor = Color3.fromRGB(255, 0, 0)

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {ImageColor3 = targetColor})

tween:Play()

```

UI Tween - Canvas Groep Kleur

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local canvasGroup = ScreenGui:WaitForChild("CanvasGroup")

local targetColor = Color3.fromRGB(255, 0, 0)

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(canvasGroup, tweenInfo, {GroupColor3 = targetColor})

tween:Play()

```

### [Stroke](#stroke)[](#stroke)

Meerdere eigenschappen regelen de UI-randen, afhankelijk van het type object.

| UI-object | | Eigenschappen |
| [Frame](/docs/nl-nl/reference/engine/classes/Frame) | | [BorderSizePixel](/docs/nl-nl/reference/engine/classes/GuiObject#BorderSizePixel) , [BorderColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BorderColor3) |
| [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel) | | [BorderSizePixel](/docs/nl-nl/reference/engine/classes/GuiObject#BorderSizePixel) , [BorderColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BorderColor3) , [TextStrokeColor3](/docs/nl-nl/reference/engine/classes/TextLabel#TextStrokeColor3) , [TextStrokeTransparency](/docs/nl-nl/reference/engine/classes/TextLabel#TextStrokeTransparency) |
| [TextButton](/docs/nl-nl/reference/engine/classes/TextButton) | | [BorderSizePixel](/docs/nl-nl/reference/engine/classes/GuiObject#BorderSizePixel) , [BorderColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BorderColor3) , [TextStrokeColor3](/docs/nl-nl/reference/engine/classes/TextButton#TextStrokeColor3) , [TextStrokeTransparency](/docs/nl-nl/reference/engine/classes/TextButton#TextStrokeTransparency) |
| [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel) | | [BorderSizePixel](/docs/nl-nl/reference/engine/classes/GuiObject#BorderSizePixel) , [BorderColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BorderColor3) |
| [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton) | | [BorderSizePixel](/docs/nl-nl/reference/engine/classes/GuiObject#BorderSizePixel) , [BorderColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BorderColor3) |

Alternatief kun je een [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke)  kind toepassen en de dikte, kleur en/of transparantie tweenen.

| UI-object | | Eigenschappen |
| [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke) | | [Color](/docs/nl-nl/reference/engine/classes/UIStroke#Color) , [Thickness](/docs/nl-nl/reference/engine/classes/UIStroke#Thickness) , [Transparency](/docs/nl-nl/reference/engine/classes/UIStroke#Transparency) |

UI Tween - UIStroke Kleur & Dikte

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("TextLabel")

local stroke = Instance.new("UIStroke")

stroke.Color = Color3.fromRGB(255, 255, 255)

stroke.Thickness = 5

stroke.Parent = object

local targetColor = Color3.fromRGB(255, 0, 0)

local targetThickness = 10

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(stroke, tweenInfo, {Color = targetColor, Thickness = targetThickness})

tween:Play()

```

## [Multi-property tweens](#multi-property-tweens)[](#multi-property-tweens)

Je kunt elke van de [enkelvoudige property tweens](#enkelvoudige-property-tweens)  combineren in complexere tweens door meerdere doel-eigenschappen door te geven aan [TweenService:Create()](/docs/nl-nl/reference/engine/classes/TweenService#Create) , bijvoorbeeld positie + rotatie  of grootte + transparantie .

UI Tween - Positie & Rotatie

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

object.AnchorPoint = Vector2.new(0.5, 0.5)

local targetPosition = UDim2.new(0.5, 0, 0.5, 0)

local targetRotation = 45

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {Position = targetPosition, Rotation = targetRotation})

tween:Play()

```

UI Tween - Grootte & Transparantie

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

object.AnchorPoint = Vector2.new(0.5, 0.5)

local aspectRatioConstraint = Instance.new("UIAspectRatioConstraint")

aspectRatioConstraint.Parent = object

local targetSize = UDim2.new(0.4, 0, 0.4, 0)

local targetTransparency = 0.8

local tweenInfo = TweenInfo.new(2)

local tween = TweenService:Create(object, tweenInfo, {Size = targetSize, ImageTransparency = targetTransparency})

tween:Play()

```

## [Tween-sequenties](#tween-sequenties)[](#tween-sequenties)

Je kunt UI-animaties aan elkaar koppelen zodat ze één voor één plaatsvinden door opeenvolgende tweens af te spelen bij het [Completed](/docs/nl-nl/reference/engine/classes/TweenBase#Completed)  evenement van de vorige tween. Bijvoorbeeld, het volgende script verplaatst een object naar het midden van het scherm en roteert het vervolgens met 45°.

UI Tween Sequentie

```

local TweenService = game:GetService("TweenService")

local Players = game:GetService("Players")

local PlayerGui = Players.LocalPlayer:WaitForChild("PlayerGui")

local ScreenGui = PlayerGui:WaitForChild("ScreenGui")

local object = ScreenGui:WaitForChild("ImageLabel")

object.AnchorPoint = Vector2.new(0.5, 0.5)

local targetPosition = UDim2.new(0.5, 0, 0.5, 0)

local targetRotation = 45

local tweenInfo = TweenInfo.new(2)

local positionTween = TweenService:Create(object, tweenInfo, {Position = targetPosition})

local rotationTween = TweenService:Create(object, tweenInfo, {Rotation = targetRotation})

-- Speel aanvankelijk de positie tween af

positionTween:Play()

-- Speel de rotatie tween af na voltooiing van de positie tween

positionTween.Completed:Connect(function()

	rotationTween:Play()

end)

```

## [Stijlovergangen](#stijlovergangen)[](#stijlovergangen)

UI-objecten kunnen ook worden geanimeerd via stijlovergangen , vergelijkbaar met [CSS-overgangen](/docs/nl-nl/ui/styling/css-comparisons#overgangen) , waarbij een of meer UI-eigenschappen worden tweened via [StyleRule](/docs/nl-nl/reference/engine/classes/StyleRule)  definities. Zie de [Stijl Editor](/docs/nl-nl/ui/styling/editor#stijl-overgangen)  gids voor details.

 ![Eind gestileerde staat regel in de Stijl Editor.](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/SE-Transition-Rule-Result.png)

## [Easing-opties](#easing-opties)[](#easing-opties)

Met de easing-opties van [TweenInfo](/docs/nl-nl/reference/engine/datatypes/TweenInfo)  kun je de easing stijl  en richting  van UI-animaties regelen.

### [Stijl](#stijl)[](#stijl)

[Enum.EasingStyle](/docs/nl-nl/reference/engine/enums/EasingStyle)  stelt de snelheid van interpolatie van begin tot eind in. Standaard is de easingstijl ingesteld op [Enum.EasingStyle.Quad](/docs/nl-nl/reference/engine/enums/EasingStyle#Quad) .

| Stijl | | Beschrijving |
| Lineair | | Beweegt met een constante snelheid. |
| Sinus | | Snelheid wordt bepaald door een sinusgolf voor een zachte easingbeweging. |
| Quad | | Vergelijkbaar met Sinus  maar met een iets scherpere curve op basis van kwadratische interpolatie. |
| Cubic | | Vergelijkbaar met Quad  maar met een iets scherpere curve op basis van kubieke interpolatie. |
| Quart | | Vergelijkbaar met Cubic  maar met een nog scherpere curve op basis van quartische interpolatie. |
| Quint | | Vergelijkbaar met Quart  maar met een nog scherpere curve op basis van quintische interpolatie. |
| Exponential | | De scherpste curve op basis van exponentiële interpolatie. |
| Cirkelvormig | | Volgt een cirkelboog, zodat versnelling plotselinger is en vertraging geleidelijker in vergelijking met Quint  of Exponential . |
| Terug | | Overschrijdt iets het doel, en komt dan terug op zijn plaats. |
| Stuiter | | Stuitert meerdere keren achteruit na het bereiken van het doel, voordat het uiteindelijk tot rust komt. |
| Elastisch | | Beweegt alsof het aan een rubberen band is bevestigd, overschrijdt het doel meerdere keren. |

EasingDirection = In EasingDirection = Out EasingDirection = InOut

![Grafieken van EasingStyle-variaties met een 'In' EasingDirection.](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/EasingStyle/Easing-Styles-In.png)

Easing Stijl - Cubic

```

local tweenInfo = TweenInfo.new(2, Enum.EasingStyle.Cubic)

local tween = TweenService:Create(object, tweenInfo, {Rotation = 45})

```

### [Richting](#richting)[](#richting)

[Enum.EasingDirection](/docs/nl-nl/reference/engine/enums/EasingDirection)  definieert hoe de [easingstijl](#stijl)  interpolatie op een object wordt toegepast, met een standaard van Out . Merk op dat een tween met Lineaire  easingstijl niet wordt beïnvloed, aangezien lineaire interpolatie constant is van begin tot eind.

| Richting | | Beschrijving |
| In | | De easingstijl wordt in een voorwaartse richting toegepast. |
| Out | | De easingstijl wordt in een omgekeerde richting toegepast. |
| InOut | | De easingstijl wordt voorwaarts toegepast voor de eerste helft en in omgekeerde richting voor de tweede helft. |

Easing richting - InOut

```

local tweenInfo = TweenInfo.new(2, Enum.EasingStyle.Cubic, Enum.EasingDirection.InOut)

local tween = TweenService:Create(object, tweenInfo, {Rotation = 45})

```

## [Typewriter-effect op tekst](#typewriter-effect-op-tekst)[](#typewriter-effect-op-tekst)

Je kunt tekstgebaseerde UI, zoals cutscene-banners, spelersinstructies en prompts, eenvoudig verbeteren met geanimeerde effecten. Het "typewriter"-effect is ideaal voor [TextLabels](/docs/nl-nl/reference/engine/classes/TextLabel)  die een verhaal vertellen, NPC-gesprekken weergeven, enz.

1.

Maak een nieuwe [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  binnen ReplicatedStorage .

2.

Hernoem het nieuwe script naar AnimateUI .

 ![](https://prod.docsiteassets.roblox.com/assets/ui/ui-animation/ModuleScript-AnimateUI.png)

3.

Plak de volgende code in het script:

ModuleScript - AnimateUI

```

local LocalizationService = game:GetService("LocalizationService")

local Players = game:GetService("Players")

local SOURCE_LOCALE = "en"

local translator = nil

local AnimateUI = {}

function AnimateUI.loadTranslator()

	pcall(function()

		translator = LocalizationService:GetTranslatorForPlayerAsync(Players.LocalPlayer)

	end)

	if not translator then

		pcall(function()

			translator = LocalizationService:GetTranslatorForLocaleAsync(SOURCE_LOCALE)

		end)

	end

end

function AnimateUI.typeWrite(guiObject, text, delayBetweenChars)

	guiObject.Visible = true

	guiObject.AutoLocalize = false

	local displayText = text

	-- Vertaal tekst indien mogelijk

	if translator then

		displayText = translator:Translate(guiObject, text)

	end

	-- Vervang regelafbrekingstags zodat de grapheloop deze tekens niet mist

	displayText = displayText:gsub("<br%s*/>", "\n")

 	-- Verwijder RichText-tags omdat animatie per teken de tags zou breken

	displayText = displayText:gsub("<[^<>]->", "")

	-- Stel de vertaalde/aangepaste tekst in op de ouder

	guiObject.Text = displayText

	local index = 0

	for first, last in utf8.graphemes(displayText) do

		index += 1

		guiObject.MaxVisibleGraphemes = index

		task.wait(delayBetweenChars)

	end

end

return AnimateUI

```

Als de brontaal  van je spel niet Engels ("en" ) is, wijzig dan de locale-code voor SOURCE_LOCALE  om overeen te komen met de brontaal in de [lokalisatie-instellingen](/docs/nl-nl/production/localization#lokalisatie-instellingen) .

4.

Maak een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  op een geschikte locatie, zoals binnen een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  die is gekoppeld aan [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) .

5.

Voeg een nieuwe [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  toe als directe kind van het label en plak de volgende code erin. Merk op dat elk bericht wordt weergegeven door AnimateUI.typeWrite()  aan te roepen met parameters voor het ouderobject, de string die moet worden weergegeven en de vertraging tussen de tekens.

LocalScript

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local AnimateUI = require(ReplicatedStorage:WaitForChild("AnimateUI"))

local label = script.Parent

-- Laad vertaler als het spel gelokaliseerd is

--AnimateUI.loadTranslator()

local message1 = [[Achter deze deur is de<br /><font size="46" color="rgb(255,50,25)">Grote Zorgoth...</font> <font size="40">🗡</font>]]

AnimateUI.typeWrite(label, message1, 0.05)

task.wait(1)

local message2 = [[...die deze kerker <font color="rgb(255,200,50)">onbetwist heerst!</font> <font size="30">😈</font>]]

AnimateUI.typeWrite(label, message2, 0.05)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
