<!-- Source: https://create.roblox.com/docs/nl-nl/ui/text-input -->

Tekstinvoervelden | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. UI-objecten

# Tekstinvoervelden

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een [TextBox](/docs/nl-nl/reference/engine/classes/TextBox)  is een rechthoek die een gebruiker in staat stelt om tekstinvoer te geven terwijl deze in focus is. Wanneer je een [TextBox](/docs/nl-nl/reference/engine/classes/TextBox)  [script](#script-tekstinvoeren) , kun je het gebruiken als een zoekbalk of een invoerveld op een formulier. Om gebruikers te helpen weten welk type tekst ze moeten invoeren, kun je ook een prompt geven via de [PlaceholderText](/docs/nl-nl/reference/engine/classes/TextBox#PlaceholderText)  eigenschap.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/ui-objects/TextBox-Example.jpg)

Omdat deze objecten [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  zijn, kun je eigenschappen zoals [BackgroundColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundColor3) , [BorderMode](/docs/nl-nl/reference/engine/classes/GuiObject#BorderMode) , [Transparency](/docs/nl-nl/reference/engine/classes/GuiObject#Transparency) , en [Rotation](/docs/nl-nl/reference/engine/classes/GuiObject#Rotation)  aanpassen om aan te sluiten bij de esthetiek van je spel.

## [Maak tekstinvoeren op het scherm](#maak-tekstinvoeren-op-het-scherm)[](#maak-tekstinvoeren-op-het-scherm)

Een [TextBox](/docs/nl-nl/reference/engine/classes/TextBox)  op een scherm is nuttig voor dingen zoals een invoerveld voor een formulier.

Om een [TextBox](/docs/nl-nl/reference/engine/classes/TextBox)  aan een scherm toe te voegen:

1.

Selecteer in het Explorer -venster StarterGui  en voeg een ScreenGui  toe.

1.

Beweeg de muis over StarterGui en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Voeg een ScreenGui  toe.

2.

Selecteer de nieuwe ScreenGui  en voeg een TextBox  toe.

1.

Beweeg de muis over ScreenGui  en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Voeg een TextBox  toe.

## [Maak tekstinvoeren op de gezichten van onderdelen](#maak-tekstinvoeren-op-de-gezichten-van-onderdelen)[](#maak-tekstinvoeren-op-de-gezichten-van-onderdelen)

Om een [TextBox](/docs/nl-nl/reference/engine/classes/TextBox)  aan het gezicht van een onderdeel toe te voegen:

1.

Selecteer in het Explorer -venster StarterGui  en voeg een SurfaceGui  toe.

1.

Beweeg de muis over StarterGui en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Voeg een ScreenGui  toe.

2.

Selecteer de nieuwe SurfaceGui  en voeg een TextBox  toe.

1.

Beweeg de muis over SurfaceGui  en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Voeg een TextBox  toe.

3.

Bevestig de SurfaceGui  aan het onderdeel  waarop je de TextBox  wilt weergeven.

1.

Selecteer in het Properties -venster de Adornee  eigenschap. Je cursor verandert.

2.

Selecteer in het Explorer -venster het onderdeel.

Als je de [TextBox](/docs/nl-nl/reference/engine/classes/TextBox)  niet ziet, probeer dan [een ander gezicht te kiezen](/docs/nl-nl/parts/textures-decals#choose-a-face)  in de ** Face**  eigenschap van de ** SurfaceGui** .

## [Script tekstinvoeren](#script-tekstinvoeren)[](#script-tekstinvoeren)

Net als bij [knoppen](/docs/nl-nl/ui/buttons) , kun je elke actie scriptten voor een [TextBox](/docs/nl-nl/reference/engine/classes/TextBox)  object wanneer een gebruiker ermee interacteert. Bijvoorbeeld, het volgende script verbindt de [FocusLost](/docs/nl-nl/reference/engine/classes/TextBox#FocusLost)  gebeurtenis die wordt geactiveerd wanneer de gebruiker op de Enter  toets drukt of buiten het vak klikt. Als enterPressed  true  is, wat betekent dat de gebruiker de invoer heeft ingediend in plaats van alleen maar buiten het vak te klikken, print het script de inhoud van de invoer naar het [Output](/docs/nl-nl/studio/output)  venster.

Basis Tekst Invoer Behandeling

```

local textBox = script.Parent

local function onFocusLost(enterPressed, inputObject)

	if enterPressed then

		print(textBox.Text)

	end

end

textBox.FocusLost:Connect(onFocusLost)

```

Als een ander voorbeeld, je wilt misschien alleen cijfers toestaan in een [TextBox](/docs/nl-nl/reference/engine/classes/TextBox) . De volgende code gebruikt de [TextBox.GetPropertyChangedSignal](/docs/nl-nl/reference/engine/classes/TextBox#GetPropertyChangedSignal)  gebeurtenis om te detecteren wanneer de [TextBox.Text](/docs/nl-nl/reference/engine/classes/TextBox#Text)  verandert, zoals wanneer een gebruiker begint te typen, en gebruikt vervolgens de [string.gsub()](/docs/nl-nl/reference/engine/libraries/string#gsub)  functie om niet-cijfers niet toe te staan.

Beperken van Tekst Invoer tot Cijfers

```

local textBox = script.Parent

local function allowOnlyNumbers()

	textBox.Text = string.gsub(textBox.Text, "%D", "")

end

textBox:GetPropertyChangedSignal("Text"):Connect(allowOnlyNumbers)

```

## [Tekstfiltering](#tekstfiltering)[](#tekstfiltering)

Applied to various sources and inputs, [text filtering](/docs/nl-nl/ui/text-filtering)  prevents users from seeing inappropriate language and personally identifiable information such as phone numbers. Roblox automatically filters common text outputs such as messages that have passed through [in-game text chat](/docs/nl-nl/chat/in-experience-text-chat) , but you are responsible for filtering any displayed text that you don't have explicit control over , including tekens/strings die gebruikers invoeren via tekstinvoeren .

Because filtering is crucial for a safe environment, Roblox actively moderates the content of games to make sure they meet [community standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards) . If Roblox receives reports or automatically detects that your game doesn't apply text filtering, then the system removes the game until you add filtering.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
