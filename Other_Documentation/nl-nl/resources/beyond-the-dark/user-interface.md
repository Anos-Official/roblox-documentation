<!-- Source: https://create.roblox.com/docs/nl-nl/resources/beyond-the-dark/user-interface -->

Gebruikersinterface | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)
4. /
5. [Beyond The Dark](/docs/nl-nl/resources/beyond-the-dark)

# Gebruikersinterface

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

We wilden een interactieve kaart-UI toevoegen zodat gebruikers informatie in het ruimtestation konden consumeren die eruitzag en aanvoelde alsof het in deze wereld leefde. We besloten de kaart binnen de 3D-ruimte te bouwen in plaats van op een scherm dat de ervaring overlayt. Dit type diegetische visualisatie zorgt voor meer onderdompeling in de wereld in plaats van dat het aanvoelt als een volledig aparte ervaring.

## [Ontwerp de kaart](#ontwerp-de-kaart)[](#ontwerp-de-kaart)

Om de kaart te ontwerpen:

1.

We hebben de UI in een externe applicatie gemockt en kwamen met een ruw idee van hoe we wilden dat het eruitzag.

 ![UI Mock](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/user-interface/UI-Mock.png)

2.

We exporteerden de individuele onderdelen van de kaart als .png  en importeerden ze in Studio.

 ![UI Elementen Geëxporteerd](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/user-interface/UI-Export.png)

## [Bouw de kaart](#bouw-de-kaart)[](#bouw-de-kaart)

Het bouwen van de kaart binnen Studio omvatte het gebruik van [Parts](/docs/nl-nl/reference/engine/classes/Part)  en [SurfaceGuis](/docs/nl-nl/reference/engine/classes/SurfaceGui) .

1.

Voor niet-interactieve elementen hoefden we alleen maar een [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  object aan het onderdeel toe te voegen.

2.

Voor interactieve elementen moet de [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  ook binnen de [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui)  container zijn, met de Adornee  eigenschap gekoppeld aan het juiste onderdeel in de 3D-werkruimte. Dit stelt je in staat om knopgebeurtenissen toe te voegen.

3.

Om een parallax-effect te bereiken, gebruikten we drie aparte [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  instanties die aan drie unieke Parts  met verschillende X  waarden waren toegewezen.

 ![Parallax Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/user-interface/Parallax-Example.png)

4.

We voegden vervolgens een gloei-effect toe met de [SurfaceGui.LightInfluence](/docs/nl-nl/reference/engine/classes/SurfaceGui#LightInfluence)  eigenschap. Als je de eigenschapswaarde op minder dan 1 instelt, wordt de [SurfaceGui.Brightness](/docs/nl-nl/reference/engine/classes/SurfaceGui#Brightness)  eigenschap ingeschakeld. Door de helderheid aan te passen, kun je de gloed die uit de afbeelding komt verhogen.

5.

Om gebruikers de mogelijkheid te geven om de weergave van de kaart in te schakelen, gebruikten we een [ProximityPrompt](/docs/nl-nl/reference/engine/classes/ProximityPrompt)  die we aan een 3D-model bevestigden. Dit is een gemakkelijke manier om gebruikersinteractie met wereldelementen toe te staan.

 ![Proximity Prompt in Explorer](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/user-interface/Proximity-Prompt.png)

6.

Ten slotte, met behulp van een UITweenModule ModuleScript binnen ReplicatedStorage, animeerden we het verbergen en tonen van de UI met TweenService en een beetje logica om de staat te bepalen. Door bij te houden wat de gebruiker klikte, konden we elementen verbergen en tonen door verschillende eigenschappen zoals alpha, positie en grootte te tweenen.

 ![PUI Tween Module in Explorer](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/user-interface/UITweenModule.png)

UITweenModule ModuleScript

```

local TweenService = game:GetService("TweenService")

local UITween = {}

-- voor het vervagen van afbeeldingen

function UITween.fadePart(object, amount, time, delay)

	local tweenAlpha = TweenInfo.new(

		time, --Tijd

		Enum.EasingStyle.Quad, --EasingStyle

		Enum.EasingDirection.Out, --EasingDirection

		0, --Herhalingsaantal

		false, --Keert om als waar

		delay --Vertragingstijd

	)

	local tween = TweenService:Create(object, tweenAlpha, {Transparency = amount})

	tween:Play()

end

function UITween.fade(object, amount, time, delay)

	local tweenAlpha = TweenInfo.new(

		time, --Tijd

		Enum.EasingStyle.Quad, --EasingStyle

		Enum.EasingDirection.Out, --EasingDirection

		0, --Herhalingsaantal

		false, --Keert om als waar

		delay --Vertragingstijd

	)

	local tween = TweenService:Create(object, tweenAlpha, {ImageTransparency = amount})

	tween:Play()

end

-- voor het vervagen van afbeeldingen

function UITween.fadeBackground(object, amount, time, delay)

	local tweenAlpha = TweenInfo.new(

		time, --Tijd

		Enum.EasingStyle.Quad, --EasingStyle

		Enum.EasingDirection.Out, --EasingDirection

		0, --Herhalingsaantal

		false, --Keert om als waar

		delay --Vertragingstijd

	)

	local tween = TweenService:Create(object, tweenAlpha, {BackgroundTransparency = amount})

	tween:Play()

end

-- voor het vervagen van tekst

function UITween.fadeText(object, amount, time, delay)

	local tweenAlpha = TweenInfo.new(

		time, --Tijd

		Enum.EasingStyle.Quad, --EasingStyle

		Enum.EasingDirection.Out, --EasingDirection

		0, --Herhalingsaantal

		false, --Keert om als waar

		delay --Vertragingstijd

	)

	local tween1 = TweenService:Create(object, tweenAlpha, {TextTransparency = amount})

	tween1:Play()

end

-- voor het verplaatsen van tekst en afbeeldingen

function UITween.move(object, position, time, delay)

	task.wait(delay)

	object:TweenPosition(position, Enum.EasingDirection.Out, Enum.EasingStyle.Quint, time)

end

-- voor het veranderen van grootte

function UITween.size(object, size, time, delay, override, callback)

	local tweenSize = TweenInfo.new(

		time, --Tijd

		Enum.EasingStyle.Quint, --EasingStyle

		Enum.EasingDirection.Out, --EasingDirection

		0, --Herhalingsaantal

		false, --Keert om als waar

		delay, --Vertragingstijd

		override,

		callback

	)

	local tween = TweenService:Create(object, tweenSize, {Size = size})

	tween:Play()

end

function UITween.rotate(object, rotation, time, delay, override, callback)

	local tweenSize = TweenInfo.new(

		time, --Tijd

		Enum.EasingStyle.Quint, --EasingStyle

		Enum.EasingDirection.Out, --EasingDirection

		0, --Herhalingsaantal

		false, --Keert om als waar

		delay, --Vertragingstijd

		override,

		callback

	)

	local tween = TweenService:Create(object, tweenSize, {Rotation = rotation})

	tween:Play()

end

-- voor het vervagen van de gamecamera

function UITween.blur(object, amount, time)

	local tweenInfo = TweenInfo.new(time, Enum.EasingStyle.Linear, Enum.EasingDirection.Out, 0, false, 0)

	local tween = TweenService:Create(object, tweenInfo, {Size = amount})

	tween:Play()

end

-- voor het inschakelen van de helderheid

function UITween.turnOn(object, amount, time)

	local tweenInfo = TweenInfo.new(time, Enum.EasingStyle.Linear, Enum.EasingDirection.Out, 0, false, 0)

	local tween = TweenService:Create(object, tweenInfo, {Brightness = amount})

	tween:Play()

end

return UITween

```

Toepassen van UI Tween op Objecten

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Voeg UITween Module toe

local UITween = require(ReplicatedStorage.UITweenModule)

-- Vind speler Guis en UI-objecten

local playerGui = game:GetService('Players').LocalPlayer:WaitForChild('PlayerGui')

local screenGuiMapUIFrame = playerGui:WaitForChild("ScreenGuiMapUIFrame").SurfaceGui

local mapUIFrameStroke = screenGuiMapUIFrame.FrameStroke

local mapUIFrameFill = screenGuiMapUIFrame.FrameFill

-- Groottes gebruikt voor tweening

local frameSizeStart = UDim2.new(0, 0, 0, 0)

local frameSizeMid = UDim2.new(1, 0, 0.05, 0)

local frameSizeEnd = UDim2.new(1, 0, 1, 0)

-- Voorbeeld Tweening

UITween.fade(mapUIFrameStroke, 0, 2, 0)

UITween.size(mapUIFrameStroke, frameSizeMid, 0.4, 0)

UITween.fade(mapUIFrameFill, 0, 2, 0.5)

UITween.size(mapUIFrameFill, frameSizeEnd, 0.4, 0.25)

task.wait(0.25)

UITween.size(mapUIFrameStroke, frameSizeMid, 0.4, 0)

UITween.size(mapUIFrameFill, frameSizeMid, 0.4, 0.25)

task.wait(0.25)

UITween.size(mapUIFrameStroke, frameSizeEnd, 0.4, 0)

UITween.size(mapUIFrameFill, frameSizeEnd, 0.4, 0.25)

```

Hier is het eindresultaat van de interactieve kaart:

[Vorige](/docs/nl-nl/resources/beyond-the-dark/sound-design)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
