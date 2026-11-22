<!-- Source: https://create.roblox.com/docs/nl-nl/ui/styling -->

UI-styling | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. UI-styling

# UI-styling

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

UI-styling is een Roblox-oplossing voor stylesheets, [vergelijkbaar met CSS](/docs/nl-nl/ui/styling/css-comparisons) , die je in staat stelt om overrides voor UI-instantie-eigenschappen te declareren en globaal toe te passen. Deze engine-niveau ondersteuning vormt de basis voor de [Style Editor](/docs/nl-nl/ui/styling/editor)  en de end-to-end tokenpipeline.

## [Concepten](#concepten)[](#concepten)

Stijl regels  (onderdeel van een [StyleSheet](/docs/nl-nl/reference/engine/classes/StyleSheet) ) zijn van toepassing op elke instantie die overeenkomt met de definitie van de regel's [Selector](/docs/nl-nl/reference/engine/classes/StyleRule#Selector)  om kenmerken zoals de klassenaam, instantienaam en hiërarchische relaties te matchen. Zie de documentatie van [Selector](/docs/nl-nl/reference/engine/classes/StyleRule#Selector)  voor details.

Stijl tokens , gedefinieerd via [attributen](/docs/nl-nl/studio/properties#instantie-attributen)  van een token [StyleSheet](/docs/nl-nl/reference/engine/classes/StyleSheet) , vertegenwoordigen UI-eigenschap variabelen die kunnen worden gebruikt in stijlen en componenten, bijvoorbeeld een gemeenschappelijke kleur voor een [Frame.BackgroundColor3](/docs/nl-nl/reference/engine/classes/Frame#BackgroundColor3) , [TextLabel.TextColor3](/docs/nl-nl/reference/engine/classes/TextLabel#TextColor3) , en [UIStroke.Color](/docs/nl-nl/reference/engine/classes/UIStroke#Color) . Tokens zijn vergelijkbaar met CSS [variabelen](/docs/nl-nl/ui/styling/css-comparisons#variabelen) .

Stijl thema's , geconfigureerd via [attributen](/docs/nl-nl/studio/properties#instantie-attributen)  van een thema [StyleSheet](/docs/nl-nl/reference/engine/classes/StyleSheet) , bestaan uit sets van specifieke tokens die kunnen worden verwisseld, bijvoorbeeld kleurtokens die een "lichte" en "donkere" thema definiëren. Gerelateerde thema's moeten dezelfde set tokens hebben om correct te functioneren.

Stijl queries  stellen je in staat om stijlen conditioneel toe te passen op basis van de context of omgeving van de UI. Deze zijn vergelijkbaar met CSS [container queries en media queries](/docs/nl-nl/ui/styling/css-comparisons#queries) , waardoor de UI kan aanpassen aan schermgrootte, invoertypen of gebruikers toegankelijkheidsinstellingen.

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Styling-Hierarchy.png)

## [Regelpropagatie](#regelpropagatie)[](#regelpropagatie)

Een [StyleLink](/docs/nl-nl/reference/engine/classes/StyleLink)  instantie koppelt een [StyleSheet](/docs/nl-nl/reference/engine/classes/StyleSheet)  en de bijbehorende regels aan een ouder [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  en alle [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  daarin. Slechts één [StyleSheet](/docs/nl-nl/reference/engine/classes/StyleSheet)  kan van toepassing zijn op een gegeven boom.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StyleLink-Propagation.png)

## [Selector definities](#selector-definities)[](#selector-definities)

Op hoog niveau werkt het matchen en wijzigen van instanties via de definitie van een regel's [Selector](/docs/nl-nl/reference/engine/classes/StyleRule#Selector)  door:

-

Roblox klasse  selectors die alle instanties van een gegeven [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  klasse targeten, bijvoorbeeld [Frame](/docs/nl-nl/reference/engine/classes/Frame) , [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel) , [TextButton](/docs/nl-nl/reference/engine/classes/TextButton) , enz.

-

Instantie [tags](/docs/nl-nl/studio/properties#instantie-tags)  toegepast op specifieke UI-objecten via [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService) .

-

Instantie naam  selectie volgens de waarde van de UI-object's [Instance.Name](/docs/nl-nl/reference/engine/classes/Instance#Name) .

-

Instantie modifiers , vergelijkbaar met [CSS pseudo-elementen](/docs/nl-nl/ui/styling/css-comparisons#pseudo-instances) , toegepast via phantom [UIComponents](/docs/nl-nl/reference/engine/classes/UIComponent)  zoals [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  of [UIStroke](/docs/nl-nl/reference/engine/classes/UIStroke) .

-

[GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  staat  selectors, vergelijkbaar met [CSS pseudo-class](/docs/nl-nl/ui/styling/css-comparisons#pseudo-classes)  selectors, die overeenkomen met een van de vier [GuiState](/docs/nl-nl/reference/engine/enums/GuiState)  enum waarden zoals [Hover](/docs/nl-nl/reference/engine/enums/GuiState) .

-

Roblox query  selectors, vergelijkbaar met [CSS container en media queries](/docs/nl-nl/ui/styling/css-comparisons#queries) , die de @  prefix gebruiken om stijlen alleen toe te passen terwijl een [StyleQuery](/docs/nl-nl/reference/engine/classes/StyleQuery)  instantie of pseudo-instantie met dezelfde naam actief is.

Class Selector Tag Selector UI Modifier Selector

De volgende setup toont hoe grootte- en kleurtokens, een thema, en een klasse-selector van "Frame"  een magenta [Frame](/docs/nl-nl/reference/engine/classes/Frame)  van grootte 200×200 pixels produceert.

![](https://prod.docsiteassets.roblox.com/assets/ui/ui-styling/Styling-Flowchart-Class.png)

Code Equivalent

UI Class Selector

```

local CollectionService = game:GetService("CollectionService")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local screenGui = script.Parent

-- Tokens

local tokens = Instance.new("StyleSheet")

tokens.Name = "Tokens"

tokens.Parent = ReplicatedStorage

tokens:SetAttribute("SquareS", UDim2.fromOffset(50, 50))

tokens:SetAttribute("SquareM", UDim2.fromOffset(100, 100))

tokens:SetAttribute("SquareL", UDim2.fromOffset(200, 200))

tokens:SetAttribute("Fit", UDim2.fromScale(1, 1))

tokens:SetAttribute("Magenta", Color3.fromHex("FF0099"))

tokens:SetAttribute("Gold", Color3.fromHex("FFCC00"))

tokens:SetAttribute("Aqua", Color3.fromHex("0093F0"))

-- ThemeA

local themeA = Instance.new("StyleSheet")

themeA.Name = "ThemeA"

themeA.Parent = ReplicatedStorage

local tokensDerive = Instance.new("StyleDerive")

tokensDerive.StyleSheet = tokens  -- Derive global tokens

tokensDerive.Parent = themeA

themeA:SetAttribute("FrameSize", "$SquareM")

themeA:SetAttribute("FrameColor", "$Aqua")

-- ThemeB

local themeB = Instance.new("StyleSheet")

themeB.Name = "ThemeB"

themeB.Parent = ReplicatedStorage

local tokensDerive = Instance.new("StyleDerive")

tokensDerive.StyleSheet = tokens  -- Derive global tokens

tokensDerive.Parent = themeB

themeB:SetAttribute("FrameSize", "$SquareL")

themeB:SetAttribute("FrameColor", "$Magenta")

-- DesignSheet

local designSheet = Instance.new("StyleSheet")

designSheet.Name = "DesignSheet"

designSheet.Parent = ReplicatedStorage

local themeDerive = Instance.new("StyleDerive")

themeDerive.StyleSheet = themeB  -- Derive from ThemeB

themeDerive.Parent = designSheet

-- Link DesignSheet to ScreenGui

local styleLink = Instance.new("StyleLink")

styleLink.StyleSheet = designSheet

styleLink.Parent = screenGui

-- Configure rule

local rule = Instance.new("StyleRule")

rule.Selector = "Frame"  -- Class selector

rule.Parent = designSheet

-- Set rule properties

rule:SetProperties({

	["BackgroundColor3"] = "$FrameColor",

	["Size"] = "$FrameSize",

	["BorderSizePixel"] = 0

})

local frame = Instance.new("Frame")

frame.Parent = screenGui

```

## [Gewijzigde eigenschappen](#gewijzigde-eigenschappen)[](#gewijzigde-eigenschappen)

Instantie-eigenschappen die door styling worden beïnvloed, zijn gemarkeerd met een ⚠  in het Eigenschappen  venster, en wanneer je met de muis over een beïnvloede eigenschap beweegt, wordt weergegeven welke stijl deze beïnvloedt. Bijvoorbeeld, als een stijlregel een getagde [Frame](/docs/nl-nl/reference/engine/classes/Frame)  vertelt om een [AnchorPoint](/docs/nl-nl/reference/engine/classes/Frame#AnchorPoint)  van 0.5, 0.5  te gebruiken, zal die objecteigenschap de standaard  waarde van 0, 0  tonen, maar zijn werkelijke [AnchorPoint](/docs/nl-nl/reference/engine/classes/Frame#AnchorPoint)  zal de gestylede  waarde van de regel gebruiken.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Styling-Modified-Property.png)

Wanneer een standaard of gestylede eigenschapswaarde verder wordt gewijzigd voor een specifiek UI-object, wordt deze vetgedrukt  om een overschreven waarde aan te geven. Bijvoorbeeld — aangenomen dat een standaard [AnchorPoint](/docs/nl-nl/reference/engine/classes/Frame#AnchorPoint)  van 0, 0  — het instellen van die eigenschap op 1, 1  voor een specifieke instantie onthult een override in vetgedrukt:

Standaard Eigenschapswaarde Overschreven Eigenschapswaarde

![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterGui-ScreenGui-HUDContainer.png)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/AnchorPoint-Default.png)

Voor elke overschreven eigenschapswaarde kun je er met de rechtermuisknop op klikken in het Eigenschappen  venster en Reset naar Standaard  selecteren om deze terug te zetten naar de gestylede waarde, of naar de standaard eigenschapswaarde als deze niet is gestyled.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
