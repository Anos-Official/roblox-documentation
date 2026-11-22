<!-- Source: https://create.roblox.com/docs/nl-nl/production/localization/localize-with-scripting -->

Lokaliseren met scripting | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Lokalisatie

# Lokaliseren met scripting

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt lokalisatie-API's gebruiken voor gespecialiseerde vertaalopdrachten die niet automatisch worden afgehandeld door [vertalingen toe te voegen](/docs/nl-nl/production/localization/manual-translations)  aan de lokalisatietabel. Roblox biedt een [LocalizationService](/docs/nl-nl/reference/engine/classes/LocalizationService)  om aan al je lokalisatie-scriptingbehoeften te voldoen. Gebruik de [LocalizationService](/docs/nl-nl/reference/engine/classes/LocalizationService)  voor de volgende taken:

-

[Afbeeldingen en geluiden lokaliseren](#afbeeldingen-en-geluiden-lokaliseren)

-

[Een deel van individuele strings vertalen](#individuele-strings-vertalen)

-

[Vertalingen van meerdere talen toepassen](#talen-wisselen)

Als je lokalisatie-API's gebruikt bij het vertalen van je game, luister dan naar eventuele wijzigingen in de LocaleID van de gebruiker om [te reageren op gebruikers die hun taal wijzigen](#reageren-op-gebruikers-die-talen-wisselen)  terwijl ze in een game zijn.

Bij het hergebruiken van vertaalcode, moet je een [TranslationHelper ModuleScript](#maak-een-translationhelper-module)  gebruiken om fouten en ontbrekende vertalingen af te handelen.

## [Afbeeldingen en geluiden lokaliseren](#afbeeldingen-en-geluiden-lokaliseren)[](#afbeeldingen-en-geluiden-lokaliseren)

Voeg lokalisatie toe naast tekst in je game door unieke afbeeldingen en geluiden te bieden op basis van de locale van de gebruiker. Om assets te lokaliseren, voeg eerst de bron  en doel  asset-ID's toe aan de [lokalisatietabel](/docs/nl-nl/production/localization/manual-translations#cloudlokalisatietabel)  van je game en gebruik vervolgens de lokalisatie-API om de verschillende assets op te halen.

![](https://prod.docsiteassets.roblox.com/assets/localization/Localized-Image-English.png) Engels (Bron) - rbxassetid://2957093606

![](https://prod.docsiteassets.roblox.com/assets/localization/Localized-Image-Spanish.png) Spaans (es) - rbxassetid://2957093671

![](https://prod.docsiteassets.roblox.com/assets/localization/Localized-Image-Portuguese.png) Portugees (pt) - rbxassetid://2957093727

Om te beginnen met het lokaliseren van afbeeldingen en geluiden, voeg je je [bron en doel](/docs/nl-nl/production/localization/manual-translations)  asset-ID's toe aan je lokalisatietabel. Asset-ID-invoeren op de lokalisatietabel moeten een Sleutel  bevatten als identificator die door de API kan worden aangeroepen.

Het volgende is een voorbeeldinvoer op een lokalisatietabel met asset-ID's:

| Sleutel | | Bron | | es | | pt |
| --- | --- |
| Key_JewelsImage | | 2957093606 | | 2957093671 | | 2957093727 |

De volgende code vervangt de asset-ID van een [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel)  met de Spaanse asset-ID die in de lokalisatietabel is opgegeven:

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local LocalizationService = game:GetService("LocalizationService")

-- Lokale variabelen

local localizedImageID

local localizedImage = Instance.new("ImageLabel")

-- Laad vertaler voor "es". Wikkel de functie in een pcall() om te beschermen tegen fouten.

local res, translator = pcall(function()

	return LocalizationService:GetTranslatorForLocaleAsync("es")

end)

if res then

	-- Verkrijg asset-ID van de lokalisatietabel door de Sleutel te verwijzen

	localizedImageID = translator:FormatByKey("Key_JewelsImage")

	-- Stel de afbeelding in

	localizedImage.Image = "rbxassetid://" .. localizedImageID

else

	print('GetTranslatorForPlayerAsync is mislukt: ' .. translator)

end

```

[GetTranslatorForPlayerAsync()](/docs/nl-nl/reference/engine/classes/LocalizationService#GetTranslatorForPlayerAsync)  en [GetTranslatorForLocaleAsync()](/docs/nl-nl/reference/engine/classes/LocalizationService#GetTranslatorForLocaleAsync)  zijn asynchroon en kunnen af en toe falen door slechte connectiviteit of andere problemen. Het wordt aanbevolen om een [TranslationHelper ModuleScript](#create-a-translationhelper-module)  te maken om fouten op te vangen en fallback-vertalingsinstructies te bieden.

## [Individuele strings vertalen](#individuele-strings-vertalen)[](#individuele-strings-vertalen)

In sommige gevallen wil je misschien individuele strings targeten voor vertaling. [Translator:Translate()](/docs/nl-nl/reference/engine/classes/Translator#Translate)  kan individuele invoeren op de lokalisatietabel ophalen op basis van de bronsstring.

In het volgende voorbeeld wordt de volgende lokalisatie-invoer gebruikt:

| Bron | | es | | es | | pt |
| Scherm | | Pantalla | | 295093671 | | 2957093727 |

De volgende script zal de Spaanse vertaling van "Scherm" naar het Output  venster afdrukken:

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local LocalizationService = game:GetService("LocalizationService")

-- Laad vertaler voor "es". Wikkel de functie in een pcall() om te beschermen tegen fouten.

local res, translator = pcall(function()

	return LocalizationService:GetTranslatorForLocaleAsync("es")

end)

if res then

	-- Gebruik de Translate-functie, geef objectcontext en string op

	local sourceTranslation = translator:Translate(game, "Screen")

	print(sourceTranslation) -- Verwachte Output: "Pantalla"

else

	print('GetTranslatorForPlayerAsync is mislukt: ' .. translator)

end

```

### [Gebruik contextoverschrijvingen](#gebruik-contextoverschrijvingen)[](#gebruik-contextoverschrijvingen)

Er zijn enkele gevallen waarin dezelfde string meerdere betekenissen kan hebben. Bijvoorbeeld, het woord "Scherm" kan zowel een computerscherm als een raam scherm aanduiden, maar de Spaanse vertalingen zijn volledig verschillend.

De Context  kolom van de lokalisatietabel is bedoeld om vertalingen via contextoverschrijvingen te specificeren. Specificeer het in-game object op je lokalisatietabel zoals in het volgende voorbeeld:

| Context | | Bron | | es |
| workspace.WindowScreen.SurfaceGui.TextLabel | | Scherm | | Mosquitero |
|  | | Scherm | | Pantalla |

De volgende script gebruikt een contextoverschrijving om een specifieke vertaling te prioriteren:

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local LocalizationService = game:GetService("LocalizationService")

local Workspace = game:GetService("Workspace")

-- Laad vertaler voor "es". Wikkel de functie in een pcall() om te beschermen tegen fouten.

local res, translator = pcall(function()

	return LocalizationService:GetTranslatorForLocaleAsync("es")

end)

if res then

	-- gebruik de Translate-functie, geef objectcontext en string op

	local sourceTranslation = translator:Translate(Workspace.WindowScreen.SurfaceGui.TextLabel, "Screen")

	print(sourceTranslation) -- Verwachte Output: Mosquitero

else

	print('GetTranslatorForPlayerAsync is mislukt: ' .. translator)

end

```

#### [Meerdere contexten](#meerdere-contexten)[](#meerdere-contexten)

In het geval van meerdere contexten vergelijkt de lokalisatieservice objectrelaties in het Context-veld van rechts naar links , waarbij de dichtstbijzijnde overeenkomst wordt gebruikt.

Bijvoorbeeld, een lokalisatietabel in je game kan de volgende gedeelde Source strings-invoeren hebben:

| Context | | Bron | | es |
| workspace.WindowScreen.SurfaceGui.TextLabel | | Scherm | | Mosquitero |
| playerGui.ScreenGui.TextButton | | Scherm | | Pantalla |

Als de string "Scherm" wordt toegevoegd aan een playerGui.ScreenGui.TextLabel  object in je game, toont de lokalisatieservice "Mosquitero" als de Spaanse vertaling als de dichtstbijzijnde contextovereenkomst.

### [Parameters vervangen](#parameters-vervangen)[](#parameters-vervangen)

Bij het gebruik van parameters om [dynamische inhoud](/docs/nl-nl/production/localization/translate-dynamic-content)  te vertalen, stel je de waarden in op een [tabel](/docs/nl-nl/luau/tables)  en geef je de tabel door als een argument via de API.

In dit voorbeeld heeft de game een lokalisatietabel met de volgende invoeren:

| Sleutel | | Bron | | es |
| Key_Prize_1 | | {1:int} juwelen | | {1:int} joyas |
| Key_Prize_2 | | ${AmountCash:fixed} cash en {NumJewels:int} juwelen | | ${AmountCash:fixed} dinero y {NumJewels:int} joyas |

Gebruik de volgende code om deze strings met parameterwaarden te vertalen:

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local LocalizationService = game:GetService("LocalizationService")

-- Laad vertaler voor "es". Wikkel de functie in een pcall() om te beschermen tegen fouten.

local res, translator = pcall(function()

	return LocalizationService:GetTranslatorForLocaleAsync("es")

end)

if res then

	-- Stel de parameterwaarde in "Key_Prize_1" in op 100

	local keyTranslation1 = translator:FormatByKey("Key_Prize_1", {100})

	print(keyTranslation1) -- Verwachte Output: 100 joyas

	-- Stel meerdere parameters in op 500 en 100 bij naam

	local keyTranslation2 = translator:FormatByKey("Key_Prize_2", {AmountCash=500, NumJewels=100})

	print(keyTranslation2) -- Verwachte Output: $500.00 dinero y 100 joyas

else

	print('GetTranslatorForPlayerAsync is mislukt: ' .. translator)

end

```

## [Talen wisselen](#talen-wisselen)[](#talen-wisselen)

In sommige gevallen wil je misschien vertalingen van andere talen in je game weergeven. Je kunt een nieuwe vertaler instellen met een andere landcode met behulp van [LocalizationService:GetTranslatorForLocaleAsync()](/docs/nl-nl/reference/engine/classes/LocalizationService#GetTranslatorForLocaleAsync) .

De volgende code stelt één vertaler in met een handmatige landcode en een aanvullende vertaler op basis van de globale locale-instellingen van de gebruiker:

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local LocalizationService = game:GetService("LocalizationService")

local Players = game:GetService("Players")

-- Lokale variabelen

local player = Players.LocalPlayer

-- Laad vertaler voor "pt". Wikkel vertalerfuncties in een pcall() om te beschermen tegen fouten.

local res1, translator = pcall(function()

	return LocalizationService:GetTranslatorForLocaleAsync("pt")

end)

-- Laad tweede vertaler met de locale van de speler, in dit voorbeeld "es"

local res2, fallbackTranslator = pcall(function()

	return LocalizationService:GetTranslatorForPlayerAsync(player)

end)

-- Gebruik de Translate-functie met de eerste vertaler

if res1 then

	local translate1 = translator:Translate(game, "juwelen")

	print(translate1) -- Verwachte Output in pt: joyas

else

	print('GetTranslatorForPlayerAsync is mislukt: ' .. translator)

end

-- Gebruik de Translate-functie met de tweede vertaler

if res2 then

	local translate2 = fallbackTranslator:Translate(game, "juwelen")

	print(translate2) -- Verwachte Output in als de gebruiker is ingesteld op 'es': jóias

else

	print('GetTranslatorForPlayerAsync is mislukt: ' .. fallbackTranslator)

end

```

## [Reageren op gebruikers die talen wisselen](#reageren-op-gebruikers-die-talen-wisselen)[](#reageren-op-gebruikers-die-talen-wisselen)

Gebruikers kunnen hun taalinstellingen op elk moment wijzigen via hun in-game instellingenmenu. Deze wijziging in gebruikersinstellingen werkt automatisch niet-scripting lokalisatie-assets bij, zoals strings die worden afgehandeld door [automatische vertaling](/docs/nl-nl/production/localization/automatic-translations) , maar kunnen mogelijk geen gescripte lokalisatiewijzigingen bijwerken die al zijn weergegeven, zoals GUI-afbeeldingen of geluiden.

![](https://prod.docsiteassets.roblox.com/assets/localization/In-Experience-Language-Switcher.png) Taalinstelling in de game

![](https://prod.docsiteassets.roblox.com/assets/localization/In-Experience-Language-Switcher-Modal.png) Gebruikers kunnen beschikbare talen kiezen die in de game zijn ingesteld

Om ervoor te zorgen dat je gescripte gelokaliseerde assets correct worden bijgewerkt, luister je naar het [GetPropertyChangedSignal](/docs/nl-nl/reference/engine/classes/Instance#GetPropertyChangedSignal)  evenement voor wijzigingen in de LocaleID-eigenschap van de [Translator](/docs/nl-nl/reference/engine/classes/Translator)  instantie die wordt geretourneerd door [LocalizationService.GetTranslatorForPlayerAsync](/docs/nl-nl/reference/engine/classes/LocalizationService#GetTranslatorForPlayerAsync) . Wanneer je [LocalizationService.GetTranslatorForPlayerAsync](/docs/nl-nl/reference/engine/classes/LocalizationService#GetTranslatorForPlayerAsync)  gebruikt, wikkel je de functie in een [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  voor het geval er fouten optreden.

De volgende code print de Locale ID van de gebruiker en de Locale ID van de Translator-instantie voor de gebruiker wanneer de gebruiker van taal wisselt:

```

local LocalizationService = game:GetService("LocalizationService")

local Players = game:GetService("Players")

local player = Players.LocalPlayer

-- Als GetTranslatorForPlayerAsync slaagt, retourneert het een vertaler voor de huidige locale van de speler

local res, translator = pcall(function()

	return LocalizationService:GetTranslatorForPlayerAsync(player)

end)

-- Functie die wordt aangeroepen wanneer een wijziging in de locale-ID van de speler wordt gedetecteerd

local function OnLocaleIdChanged()

	print("Vertaler is veranderd naar: " .. translator.LocaleId)

	-- Je moet hier alle assets opnieuw vertalen die zijn vertaald met lokalisatie-API's naar de nieuwe taal van de speler

end

-- Controleer of GetTranslatorForPlayerAsync is geslaagd

if res then

	-- Als het is geslaagd, vertaal hier assets met behulp van de vertaler

	-- Luister naar een wijziging in de locale-ID van de speler

	translator:GetPropertyChangedSignal("LocaleId"):Connect(OnLocaleIdChanged)

else

	print('GetTranslatorForPlayerAsync is mislukt: ' .. translator)

end

```

## [Maak een TranslationHelper-module](#maak-een-translationhelper-module)[](#maak-een-translationhelper-module)

Wanneer je vertalers laadt op basis van de standaardlocale van de speler, wil je misschien code hergebruiken. Om code te hergebruiken, stel je een helper [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  in die veilig vertalers laadt op basis van de standaardlocale van de speler en functies bevat voor het bieden van specifieke vertalingen en het wisselen van talen.

De volgende code implementeert een TranslationHelper die je kunt kopiëren naar je eigen project als een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) :

```

local TranslationHelper = {}

local LocalizationService = game:GetService("LocalizationService")

local Players = game:GetService("Players")

-- Lokale variabelen

local player = Players.LocalPlayer

local sourceLanguageCode = "en"

-- Verkrijg vertalers

local playerTranslator, fallbackTranslator

local foundPlayerTranslator = pcall(function()

	playerTranslator = LocalizationService:GetTranslatorForPlayerAsync(player)

end)

local foundFallbackTranslator = pcall(function()

	fallbackTranslator = LocalizationService:GetTranslatorForLocaleAsync(sourceLanguageCode)

end)

-- Maak een methode TranslationHelper.setLanguage om een nieuwe vertaling voor de TranslationHelper te laden

function TranslationHelper.setLanguage(newLanguageCode)

	if sourceLanguageCode ~= newLanguageCode then

		local success, newPlayerTranslator = pcall(function()

			return LocalizationService:GetTranslatorForLocaleAsync(newLanguageCode)

		end)

		-- Alleen de huidige playerTranslator overschrijven als de nieuwe geldig is (fallbackTranslator blijft de brontaal van de game)

		if success and newPlayerTranslator then

			playerTranslator = newPlayerTranslator

			return true

		end

	end

	return false

end

-- Maak een Translate-functie die een fallback-vertaler gebruikt als de eerste niet kan worden geladen of succesvol kan retourneren. Je kunt ook het verwijzende object standaard instellen op het generieke object

function TranslationHelper.translate(text, object)

	if not object then

		object = game

	end

	if foundPlayerTranslator then

		return playerTranslator:Translate(object, text)

	end

	if foundFallbackTranslator then

		return fallbackTranslator:Translate(object, text)

	end

	return false

end

-- Maak een FormatByKey() functie die een fallback-vertaler gebruikt als de eerste niet kan worden geladen of succesvol kan retourneren

function TranslationHelper.translateByKey(key, arguments)

	local translation = ""

	local foundTranslation = false

	-- Probeert eerst te vertalen voor de taal van de speler (als er een vertaler is gevonden)

	if foundPlayerTranslator then

		foundTranslation = pcall(function()

			translation = playerTranslator:FormatByKey(key, arguments)

		end)

	end

	if foundFallbackTranslator and not foundTranslation then

		foundTranslation = pcall(function()

			translation = fallbackTranslator:FormatByKey(key, arguments)

		end)

	end

	if foundTranslation then

		return translation

	else

		return false

	end

end

return TranslationHelper

```

Als de brontaal van je game niet Engels is, wijzig dan de waarde van de sourceLanguageCode  variabele in de landcode van de brontaal van de game.

Zodra de module in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  staat, vereis je deze vanuit een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  om de functies van de module aan te roepen. De volgende code gebruikt de helperfunctie van deze module om een individuele string te vertalen:

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Vereis vertaalmodule

local TranslationHelper = require(ReplicatedStorage:WaitForChild("TranslationHelper"))

-- Gebruik de functies die in TranslationHelper worden aangeboden

TranslationHelper.setLanguage("es")

local sourceTranslation = TranslationHelper.translate("Screen")

print(sourceTranslation) -- Verwachte Output in 'es': "Pantalla"

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
