<!-- Source: https://create.roblox.com/docs/nl-nl/ui/styling/css-comparisons -->

CSS Vergelijkingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. UI-styling

# CSS Vergelijkingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De meeste CSS-concepten komen overeen met Roblox-stylingconcepten. De volgende voorbeelden laten zien hoe CSS en HTML zich verhouden tot Luau en Roblox-klassen/eigenschappen.

Om elk van de volgende Luau-scriptvoorbeelden te testen:

1.

Maak in de [Explorer](/docs/nl-nl/studio/explorer)  het volgende aan:

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/CSS-Test-Setup.png)

1.

[StyleSheet](/docs/nl-nl/reference/engine/classes/StyleSheet)  instantie binnen [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) .

2.

[ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  container in [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) .

3.

[LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  instantie binnen de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui) .

4.

[StyleLink](/docs/nl-nl/reference/engine/classes/StyleLink)  object binnen de [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui) .

2.

Plak in de [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  de volgende ondersteunende code:

LocalScript

```

local CollectionService = game:GetService("CollectionService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local coreSheet = ReplicatedStorage:FindFirstChildWhichIsA("StyleSheet")

local screenGui = script.Parent

local styleLink = screenGui:FindFirstChildWhichIsA("StyleLink")

styleLink.StyleSheet = coreSheet

```

3.

Voor elk voorbeeld hieronder, plak de Luau  code regels na de ondersteunende regels 1–7.

## [Selectors](#selectors)[](#selectors)

De [Selector](/docs/nl-nl/reference/engine/classes/StyleRule#Selector)  eigenschap van een [StyleRule](/docs/nl-nl/reference/engine/classes/StyleRule)  specificeert welke instanties de regel moet beïnvloeden. De volgende selectortypes komen van CSS naar Luau en kunnen worden gebruikt met combinatoren.

### [Element](#element)[](#element)

Equivalent aan CSS-elementselectoren zijn Roblox class selectors  die alle instanties van een gegeven [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  klasse selecteren, bijvoorbeeld [Frame](/docs/nl-nl/reference/engine/classes/Frame) , [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel) , [TextButton](/docs/nl-nl/reference/engine/classes/TextButton) , enz.

CSS

```

button {

	background-color: #335FFF;

	color: #E1E1E1;

	width: 15%;

	height: 40px;

	border: none;

}

```

HTML

```

<button>Hoofdmenu</button>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = "TextButton" -- Roblox class selector

rule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	Size = UDim2.new(0.15, 0, 0, 40),

	BorderSizePixel = 0

})

local button = Instance.new("TextButton")

button.Text = "Hoofdmenu"

button.Parent = screenGui

```

### [Class](#class)[](#class)

De Roblox-equivalent van CSS class  selectors zijn tag selectors  die gebruik maken van [tags](/docs/nl-nl/studio/properties#instantie-tags)  die zijn toegepast via [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService) .

CSS

```

.button-primary {

	background-color: #335FFF;

	color: #E1E1E1;

}

```

HTML

```

<button class="button-primary">Hoofdmenu</button>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = ".ButtonPrimary" -- Roblox tag selector

rule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	AutomaticSize = Enum.AutomaticSize.XY

})

local button = Instance.new("TextButton")

button.Text = "Hoofdmenu"

button.Parent = screenGui

-- Tag toepassen op knop

CollectionService:AddTag(button, "ButtonPrimary")

```

### [Identifier](#identifier)[](#identifier)

De dichtstbijzijnde Roblox vergelijking met CSS id  is de #[name]  selector die selecteert op basis van de waarde van [Instance.Name](/docs/nl-nl/reference/engine/classes/Instance#Name) . In tegenstelling tot de W3C-specificatie van de id -attribuut, wordt niet verwacht dat namen uniek zijn.

CSS

```

#modal-frame {

	background-color: #000022;

	opacity: 0.5;

	width: 50%;

	min-height: 100px;

}

```

HTML

```

<div id="modal-frame"></div>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = "#ModalFrame" -- Instance name selector

rule:SetProperties({

	BackgroundColor3 = Color3.fromHex("000022"),

	BackgroundTransparency = 0.5,

	Size = UDim2.new(0.5, 0, 0, 100),

	AutomaticSize = Enum.AutomaticSize.Y

})

local frame = Instance.new("Frame")

frame.Parent = screenGui

-- Hernoem frame om overeen te komen met selector

frame.Name = "ModalFrame"

```

## [Combinators](#combinators)[](#combinators)

Combinators laten je basis [selectors](#selectors)  mixen om diepere hiërarchische relaties te matchen.

### [Child](#child)[](#child)

De child selector van >  is identiek tussen CSS en Roblox.

CSS

```

.menu-container {

	width: 25%;

}

.menu-container > button {

	background-color: #335FFF;

	color: #E1E1E1;

	width: 80%;

	height: 40px;

	border: none;

}

```

HTML

```

<div class="menu-container">

	<button>Opties</button>

</div>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = ".MenuContainer > TextButton" -- Child selector

rule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	Size = UDim2.new(0.8, 0, 0, 40),

	BorderSizePixel = 0

})

-- Maak menu container

local menuContainer = Instance.new("Frame")

menuContainer.Size = UDim2.new(0.25, 0, 0, 0)

menuContainer.AutomaticSize = Enum.AutomaticSize.Y

menuContainer.Parent = screenGui

-- Tag toepassen

CollectionService:AddTag(menuContainer, "MenuContainer")

-- Maak knop

local button = Instance.new("TextButton")

button.Text = "Opties"

-- Stel menu container in als ouder van knop

button.Parent = menuContainer

```

### [Descendant](#descendant)[](#descendant)

In tegenstelling tot de CSS-witruimtesyntaxis, bijvoorbeeld .menu-container button  die hier te zien is, gebruikt Roblox de >>  combinator om een afstammingsrelatie aan te geven.

CSS

```

.menu-container {

	width: 25%;

}

.sub-container {

	width: 75%;

}

.menu-container button {

	background-color: #335FFF;

	color: #E1E1E1;

	width: 80%;

	height: 40px;

	border: none;

}

```

HTML

```

<div class="menu-container">

	<div class="sub-container">

		<button>Opties</button>

	</div>

</div>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = ".MenuContainer >> TextButton" -- Descendant selector

rule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	Size = UDim2.new(0.8, 0, 0, 40),

	BorderSizePixel = 0

})

-- Maak menu container

local menuContainer = Instance.new("Frame")

menuContainer.Size = UDim2.new(0.25, 0, 0, 0)

menuContainer.AutomaticSize = Enum.AutomaticSize.Y

menuContainer.Parent = screenGui

-- Tag toepassen

CollectionService:AddTag(menuContainer, "MenuContainer")

-- Maak sub-container

local subContainer = Instance.new("Frame")

subContainer.Size = UDim2.new(0.75, 0, 0, 0)

subContainer.AutomaticSize = Enum.AutomaticSize.Y

-- Stel menu container in als ouder van sub-container

subContainer.Parent = menuContainer

-- Maak knop

local button = Instance.new("TextButton")

button.Text = "Opties"

-- Stel sub-container in als ouder van knop

button.Parent = subContainer

```

### [Selector list](#selector-list)[](#selector-list)

Meerdere selectors (inclusief selectors met combinatoren) kunnen worden gedeclareerd met hetzelfde eigenschapsblok, gescheiden door komma's, om redundantie te verminderen.

CSS

```

img, p {

	background-color: #FF0033;

}

```

HTML

```

<img src="gear.png" width="100" height="100">

<p>Hoofdmenu</p>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = "ImageLabel, TextLabel" -- Selector voor afbeeldingslabels EN tekstlabels

rule:SetProperty("BackgroundColor3", Color3.fromHex("ff0033"))

-- Maak afbeeldingslabel

local imageLabel = Instance.new("ImageLabel")

imageLabel.Image = "rbxassetid://104919049969988"

imageLabel.Size = UDim2.new(0, 100, 0, 100)

imageLabel.Parent = screenGui

-- Maak tekstlabel

local textLabel = Instance.new("TextLabel")

textLabel.Size = UDim2.new(1, 0, 0, 0)

textLabel.AutomaticSize = Enum.AutomaticSize.Y

textLabel.TextXAlignment = Enum.TextXAlignment.Left

textLabel.TextYAlignment = Enum.TextYAlignment.Top

textLabel.Text = "Hoofdmenu"

textLabel.Parent = screenGui

```

## [Pseudo-classes](#pseudo-classes)[](#pseudo-classes)

De Roblox-equivalent van CSS [pseudo-class](https://developer.mozilla.org/docs/Web/CSS/Pseudo-classes)  selectors zijn state selectors  die overeenkomen met een van de vier [Enum.GuiState](/docs/nl-nl/reference/engine/enums/GuiState)  waarden zoals [Hover](/docs/nl-nl/reference/engine/enums/GuiState)  of [Press](/docs/nl-nl/reference/engine/enums/GuiState) .

CSS

```

img:hover {

	opacity: 0.5;

}

```

HTML

```

<img src="gear.png" width="100" height="100">

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = "ImageLabel:Hover" -- State selector

rule:SetProperty("ImageTransparency", 0.5)

-- Maak afbeeldingslabel

local imageLabel = Instance.new("ImageLabel")

imageLabel.Image = "rbxassetid://104919049969988"

imageLabel.Size = UDim2.new(0, 100, 0, 100)

imageLabel.BackgroundTransparency = 1

imageLabel.Parent = screenGui

```

## [Pseudo-instances](#pseudo-instances)[](#pseudo-instances)

Vergelijkbaar met hoe CSS [pseudo-elements](https://developer.mozilla.org/docs/Web/CSS/Pseudo-elements)  specifieke delen van een element kan wijzigen, kan Roblox fantoom [UIComponents](/docs/nl-nl/reference/engine/classes/UIComponent)  creëren via de [Selector](/docs/nl-nl/reference/engine/classes/StyleRule#Selector)  eigenschap van een stijlregel. Bijvoorbeeld, de volgende regel creëert effectief een [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  modifier onder elke [Frame](/docs/nl-nl/reference/engine/classes/Frame)  getagd met RoundedCorner20  en stelt de [CornerRadius](/docs/nl-nl/reference/engine/classes/UICorner#CornerRadius)  van elke modifier in op 20  pixels.

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

rule.Selector = "Frame.RoundedCorner20::UICorner" -- UI component selector

rule:SetProperty("CornerRadius", UDim.new(0, 20))

-- Maak frame

local frame = Instance.new("Frame")

frame.Size = UDim2.new(0.4, 0, 0.2, 0)

frame.Parent = screenGui

-- Tag toepassen op frame

CollectionService:AddTag(frame, "RoundedCorner20")

```

## [Queries](#queries)[](#queries)

Roblox style queries  overbruggen de kloof tussen CSS [media queries](https://developer.mozilla.org/docs/Web/CSS/CSS_media_queries)  en [container queries](https://developer.mozilla.org/docs/Web/CSS/CSS_containment/Container_queries) . Met de @  prefix kun je stijlen in- of uitschakelen op basis van de afmetingen van de ouder, typen invoerapparaten of gebruikers toegankelijkheidsinstellingen.

In CSS past @container  stijlen toe op basis van de grootte van een bovenliggend element. In Roblox definieer je een pseudo-instantiequery met ::StyleQuery  gevolgd door een [identifier](#identifier)  voor de [Selector](/docs/nl-nl/reference/engine/classes/StyleRule#Selector)  eigenschap van de voorwaarde, bijvoorbeeld "::StyleQuery #WideContainer" , samen met een [StyleQuery](/docs/nl-nl/reference/engine/classes/StyleQuery)  voorwaarde naam zoals "MinSize"  om de [GuiObject.AbsoluteSize](/docs/nl-nl/reference/engine/classes/GuiObject#AbsoluteSize)  van de ouder te evalueren. Vervolgens, om stijlen toe te passen op de instantie of zijn kinderen wanneer de query actief is, maak je een [StyleRule](/docs/nl-nl/reference/engine/classes/StyleRule)  met de @[identifier]  prefix als zijn [Selector](/docs/nl-nl/reference/engine/classes/StyleRule#Selector) , bijvoorbeeld @WideContainer .

CSS

```

.container {

	container-type: inline-size;

	background-color: rgba(0, 0, 34, 0.5);

}

button {

	background-color: #335FFF;

	color: #E1E1E1;

	width: 75%;

	height: 40px;

	border: none;

}

@container (min-width: 400px) {

	button {

		background-color: #cc0033;

	}

}

```

HTML

```

<div class="container" style="width: 80%; height: 200px;">

	<button>Hoofdmenu</button>

</div>

```

Luau

```

-- Container regel

local containerRule = Instance.new("StyleRule")

containerRule.Selector = "Frame" -- Roblox class selector

containerRule:SetProperties({

	BackgroundColor3 = Color3.fromRGB(0, 0, 34),

	BackgroundTransparency = 0.5,

	BorderSizePixel = 0

})

containerRule.Parent = coreSheet

-- Knopregel

local buttonRule = Instance.new("StyleRule")

buttonRule.Selector = "TextButton" -- Roblox class selector

buttonRule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	Size = UDim2.new(0.75, 0, 0, 40),

	BorderSizePixel = 0

})

buttonRule.Parent = containerRule -- Kind van containerregel

-- Query voorwaarde (#WideContainer)

local queryCondition = Instance.new("StyleRule")

queryCondition.Selector = "::StyleQuery #WideContainer"

queryCondition:SetProperty("MinSize", Vector2.new(400, 0))

queryCondition.Parent = containerRule -- Kind van containerregel

-- Regel die wordt toegepast wanneer de voorwaarde actief is (@WideContainer)

local queryStyle = Instance.new("StyleRule")

queryStyle.Selector = "@WideContainer Frame > TextButton" -- Child selector

queryStyle:SetProperty("BackgroundColor3", Color3.fromHex("CC0033"))

queryStyle.Parent = containerRule -- Kind van containerregel

-- Maak instanties

local container = Instance.new("Frame")

container.Size = UDim2.new(0.8, 0, 0, 200)

container.Parent = screenGui

local button = Instance.new("TextButton")

button.Text = "Hoofdmenu"

button.Parent = container

```

Roblox biedt ook ingebouwde queries  die direct overeenkomen met globale omgevingsstatussen zoals [ViewportDisplaySize](/docs/nl-nl/reference/engine/classes/GuiService#ViewportDisplaySize)  of [ReducedMotionEnabled](/docs/nl-nl/reference/engine/classes/GuiService#ReducedMotionEnabled) . Deze vereisen geen ::StyleQuery  definitie en kunnen direct worden gebruikt met een @  prefix.

| CSS Media Feature | | Roblox Style Query Selector |
| --- | --- |
| (max-width: 600px) | | @ViewportDisplaySizeSmall |
| (min-width: 601px) and (max-width: 1200px) | | @ViewportDisplaySizeMedium |
| (min-width: 1201px) | | @ViewportDisplaySizeLarge |
| (pointer: fine) | | @PreferredInputKeyboardAndMouse |
| (pointer: coarse) | | @PreferredInputTouch |
| (any-pointer: coarse) | | @PreferredInputGamepad |
| (prefers-reduced-motion: reduce) | | @ReducedMotionEnabledTrue |
| (prefers-reduced-motion: no-preference) | | @ReducedMotionEnabledFalse |

CSS

```

.container {

	container-type: inline-size;

	background-color: rgba(0, 0, 34, 0.5);

}

@media (prefers-reduced-motion: reduce) {

	.container {

		background-color: rgba(0, 0, 34, 1);

	}

}

```

HTML

```

<div class="container" style="width: 80%; height: 200px;">

</div>

```

Luau

```

-- Container regel

local containerRule = Instance.new("StyleRule")

containerRule.Selector = "Frame" -- Roblox class selector

containerRule:SetProperties({

	BackgroundColor3 = Color3.fromRGB(0, 0, 34),

	BackgroundTransparency = 0.5,

	BorderSizePixel = 0

})

containerRule.Parent = coreSheet

-- Ingebouwde query

local motionRule = Instance.new("StyleRule")

motionRule.Selector = "@ReducedMotionEnabledTrue Frame"

motionRule:SetProperty("BackgroundTransparency", 0)

motionRule.Parent = containerRule -- Kind van containerregel

-- Maak instanties

local container = Instance.new("Frame")

container.Size = UDim2.new(0.8, 0, 0, 200)

container.Parent = screenGui

```

## [Variabelen](#variabelen)[](#variabelen)

CSS laat je [variabelen](https://developer.mozilla.org/docs/Web/CSS/--*)  declareren en refereren door het hele stijlsysteem. Roblox bereikt dit via tokens en het [instance attributes](/docs/nl-nl/studio/properties#instantie-attributen)  systeem. Door $  als prefix te gebruiken, kun je verwijzen naar attributen die zijn gedeclareerd in een [StyleRule](/docs/nl-nl/reference/engine/classes/StyleRule)  of [StyleSheet](/docs/nl-nl/reference/engine/classes/StyleSheet)  erfgoedketen bij het instellen van stijl eigenschappen.

CSS

```

:root {

	--button-bg-color: #335FFF;

	--button-text-color: #E1E1E1;

}

button {

	background-color: var(--button-bg-color);

	color: var(--button-text-color);

}

```

HTML

```

<button>Hoofdmenu</button>

```

Luau

```

local rule = Instance.new("StyleRule")

rule.Parent = coreSheet

-- Stel stijlblad tokens in met behulp van attributen

coreSheet:SetAttribute("ButtonBgColor", Color3.fromHex("335FFF"))

coreSheet:SetAttribute("ButtonTextColor", Color3.fromHex("E1E1E1"))

rule.Selector = "TextButton" -- Class selector

rule:SetProperties({

	BackgroundColor3 = "$ButtonBgColor",

	TextColor3 = "$ButtonTextColor"

})

-- Maak knop

local button = Instance.new("TextButton")

button.AutomaticSize = Enum.AutomaticSize.XY

button.Text = "Hoofdmenu"

button.Parent = screenGui

```

## [Overgangen](#overgangen)[](#overgangen)

CSS [overgangen](https://developer.mozilla.org/docs/Web/CSS/Guides/Transitions)  laten je eigenschapswaarden over een bepaalde duur tweenen. Je kunt dit in Roblox bereiken door eigenschapsovergangen in te stellen op een [StyleRule](/docs/nl-nl/reference/engine/classes/StyleRule)  via [SetPropertyTransition()](/docs/nl-nl/reference/engine/classes/StyleRule#SetPropertyTransition)  (enkele) of [SetPropertyTransitions()](/docs/nl-nl/reference/engine/classes/StyleRule#SetPropertyTransitions)  (meerdere).

CSS

```

button {

	background-color: #335FFF;

	color: #E1E1E1;

	width: 15%;

	height: 40px;

	border: none;

	transition:

		background-color 1s ease-out,

		transform 1.25s ease-out

}

button:hover {

	background-color: #33AAFF;

	transform: rotate(-5deg);

}

```

HTML

```

<button>Hoofdmenu</button>

```

Luau

```

-- Knopregel

local buttonRule = Instance.new("StyleRule")

buttonRule.Selector = "TextButton" -- Roblox class selector

buttonRule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	Size = UDim2.new(0.15, 0, 0, 40),

	BorderSizePixel = 0

})

-- Stel eigenschapsovergangs gedragingen in

buttonRule:SetPropertyTransitions({

	BackgroundColor3 = TweenInfo.new(1, Enum.EasingStyle.Cubic, Enum.EasingDirection.Out),

	Rotation = TweenInfo.new(1.25, Enum.EasingStyle.Cubic, Enum.EasingDirection.Out)

})

buttonRule.Parent = coreSheet

-- Knop hover regel

local hoverRule = Instance.new("StyleRule")

hoverRule.Selector = "TextButton:Hover" -- State selector

hoverRule:SetProperties({

	AutoButtonColor = false,

	BackgroundColor3 = Color3.fromHex("33AAFF"),

	Rotation = -5

})

hoverRule.Parent = coreSheet

-- Maak tekstknop

local button = Instance.new("TextButton")

button.Text = "Hoofdmenu"

button.Parent = screenGui

```

## [Nesting en samenvoegen](#nesting-en-samenvoegen)[](#nesting-en-samenvoegen)

Een concept lenen van [SCSS](https://sass-lang.com/guide/#nesting) , [StyleRules](/docs/nl-nl/reference/engine/classes/StyleRule)  kunnen genest worden en hun selectors zullen samenvoegen .

SCSS

```

#menu-frame {

	background-color: #000022;

	width: 25%;

	min-height: 200px;

	display: flex;

	flex-direction: column;

	justify-content: space-evenly;

	align-items: center;

	> button {

		background-color: #335FFF;

		color: #E1E1E1;

		width: 80%;

		height: 40px;

		border: none;

		&:hover {

			opacity: 0.5;

		}

	}

}

```

HTML

```

<div id="menu-frame">

	<button>Charms</button>

	<button>Mana</button>

	<button>Scrolls</button>

</div>

```

Luau

```

-- Menu frame regel

local menuFrameRule = Instance.new("StyleRule")

menuFrameRule.Selector = "#MenuFrame"

menuFrameRule:SetProperties({

	BackgroundColor3 = Color3.fromHex("000022"),

	Size = UDim2.new(0.25, 0, 0, 200),

	AutomaticSize = Enum.AutomaticSize.Y

})

menuFrameRule.Parent = coreSheet

-- Menu lay-out regel

local menuLayoutRule = Instance.new("StyleRule")

menuLayoutRule.Selector = "::UIListLayout"

menuLayoutRule:SetProperties({

	FillDirection = Enum.FillDirection.Vertical,

	VerticalFlex = Enum.UIFlexAlignment.SpaceEvenly,

	HorizontalAlignment = Enum.HorizontalAlignment.Center

})

menuLayoutRule.Parent = menuFrameRule -- Stel menu frame regel in als ouder

-- Knopregel

local buttonRule = Instance.new("StyleRule")

buttonRule.Selector = "> TextButton"

buttonRule:SetProperties({

	BackgroundColor3 = Color3.fromHex("335FFF"),

	TextColor3 = Color3.fromHex("E1E1E1"),

	Size = UDim2.new(0.8, 0, 0, 40),

	BorderSizePixel = 0

})

buttonRule.Parent = menuFrameRule -- Stel menu frame regel in als ouder

-- Knop hover regel

local buttonHoverRule = Instance.new("StyleRule")

buttonHoverRule.Selector = ":Hover"

buttonHoverRule:SetProperties({

	AutoButtonColor = false,

	BackgroundTransparency = 0.5,

	TextTransparency = 0.5

})

buttonHoverRule.Parent = buttonRule -- Stel knopregel in als ouder

-- Maak bovenste frame

local menuFrame = Instance.new("Frame")

menuFrame.Name = "MenuFrame"

menuFrame.Parent = screenGui

-- Maak knoppen binnen frame

local button1 = Instance.new("TextButton")

button1.Text = "Charms"

button1.Parent = menuFrame

local button2 = Instance.new("TextButton")

button2.Text = "Mana"

button2.Parent = menuFrame

local button3 = Instance.new("TextButton")

button3.Text = "Scrolls"

button3.Parent = menuFrame

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
