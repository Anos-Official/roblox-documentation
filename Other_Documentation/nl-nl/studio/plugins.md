<!-- Source: https://create.roblox.com/docs/nl-nl/studio/plugins -->

Studio-plugins | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)

# Studio-plugins

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een plugin  is een extensie die extra functies of functionaliteit aan Studio toevoegt. Je kunt [community-plugins installeren](/docs/nl-nl/production/creator-store#vind-assets)  vanuit de Creator Store, of je kunt [je eigen plugins maken](#nieuwe-plugins-maken)  en [publiceren](#plugins-uploaden)  naar de [Toolbox](/docs/nl-nl/projects/assets/toolbox)  om ze in al je games te gebruiken.

Als je ervoor kiest om je plugins ook te distribueren naar de Creator Store, kun je ze gratis aanbieden of verkopen voor Amerikaanse Dollars . Roblox biedt een marktleidend inkomstenmodel voor deze verkopen, aangezien alleen belastingen en verwerkingskosten voor betalingen worden afgetrokken. Voor meer informatie over het verkopen van plugins, zie [Creator Store - Distribueer en verkoop activa](/docs/nl-nl/production/creator-store#verspreiden-en-verkopen-van-assets) .

## [Nieuwe plugins maken](#nieuwe-plugins-maken)[](#nieuwe-plugins-maken)

Je kunt je eigen plugins maken om je workflow in Studio te verbeteren. Het volgende codevoorbeeld is een plugin genaamd AddEmptyScript  die een lege [Script](/docs/nl-nl/reference/engine/classes/Script)  invoegt als kind van een [Instance](/docs/nl-nl/reference/engine/classes/Instance)  of in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) . De volgende secties leggen de belangrijkste onderdelen uit voor het maken van deze plugin.

Om te beginnen, moet je Plugin Debugging Enabled  inschakelen in de Studio  sectie van de instellingen van Studio. Dit maakt de [PluginDebugService](/docs/nl-nl/reference/engine/classes/PluginDebugService)  zichtbaar in Studio, wat realtime debugging voor de code van je plugin biedt en het gemakkelijker maakt om je plugin opnieuw te laden en op te slaan.

AddEmptyScript Plugin

```

local ServerScriptService = game:GetService("ServerScriptService")

local Selection = game:GetService("Selection")

-- Maak een nieuwe toolbar sectie en Plugins menu map met de titel "Custom"

local toolbar = plugin:CreateToolbar("Custom")

-- Voeg een toolbar knop toe met het label "Empty Script"

local newScriptButton = toolbar:CreateButton("Empty Script", "Maak een lege script aan", "rbxassetid://14978048121")

-- Maak de knop klikbaar, zelfs als de 3D-weergave verborgen is

newScriptButton.ClickableWhenViewportHidden = true

local function onPluginButtonClicked()

	local selectedObjects = Selection:Get()

	local parent = selectedObjects[1] or ServerScriptService

	local newScript = Instance.new("Script")

	newScript.Source = ""

	newScript.Parent = parent

end

newScriptButton.Click:Connect(onPluginButtonClicked)

```

### [Plugin-script opslaan](#plugin-script-opslaan)[](#plugin-script-opslaan)

Om een plugin te maken, maak je eerst een [Script](/docs/nl-nl/reference/engine/classes/Script)  en sla je deze lokaal op.

1.

Voeg een nieuwe [Script](/docs/nl-nl/reference/engine/classes/Script)  toe in [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage)  en hernoem deze naar AddEmptyScript .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Plugin-Empty-Script-Adder.png)

2.

Kopieer en plak de AddEmptyScript Plugin  code hierboven in het nieuwe script.

3.

Met het nieuwe script geselecteerd in het Explorer  venster, selecteer Opslaan als Lokale Plugin  in het Plugins  menu van Studio.

4.

Klik in het pop-upvenster op Opslaan  om het plugin-script in je lokale Plugins  map van de Studio-installatie in te voegen.

5.

De plugin zou moeten verschijnen in [PluginDebugService](/docs/nl-nl/reference/engine/classes/PluginDebugService)  en beginnen met draaien.

6.

BELANGRIJK

 Verwijder het originele script in [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage)  en werk vanuit de AddEmptyScript  plugin binnen [PluginDebugService](/docs/nl-nl/reference/engine/classes/PluginDebugService) , anders loop je het risico wijzigingen aan het verkeerde script aan te brengen.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Plugin-Created.png)

Om een specifieke plugin binnen [PluginDebugService](/docs/nl-nl/reference/engine/classes/PluginDebugService)  bij te werken, klik je met de rechtermuisknop en selecteer je Opslaan en Herlaad Plugin  in het contextmenu. Als je de plugin gewoon wilt herladen, bijvoorbeeld om door een sectie van de code te stappen met een breakpoint zonder de plugin op te slaan, klik je met de rechtermuisknop en selecteer je Herlaad Plugin .

Op het breedste niveau kun je ook alle  plugins bijwerken door met de rechtermuisknop op [PluginDebugService](/docs/nl-nl/reference/engine/classes/PluginDebugService)  te klikken en Opslaan en Herlaad Alle Plugins in Debugger  te selecteren (sneltoets Ctrl Shift L  of ⌘ Shift L ).

### [Knop aan de werkbalk toevoegen](#knop-aan-de-werkbalk-toevoegen)[](#knop-aan-de-werkbalk-toevoegen)

Om een knop voor je plugin toe te voegen aan het Plugins  tabblad van de Studio werkbalk, gebruik je de [Plugin:CreateToolbar()](/docs/nl-nl/reference/engine/classes/Plugin#CreateToolbar)  en [PluginToolbar:CreateButton()](/docs/nl-nl/reference/engine/classes/PluginToolbar#CreateButton)  methoden. In de code voor AddEmptyScript  maakt regel 5 een nieuwe sectie in de werkbalk en Plugins  menu map met de titel Custom , terwijl regel 8 een knop met het label Empty Script  maakt.

 ![Nieuwe plugin knop toegevoegd aan de werkbalk in Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Custom-Plugin-Button.png)

### [Code uitvoeren bij klikken](#code-uitvoeren-bij-klikken)[](#code-uitvoeren-bij-klikken)

Om de plugin code te laten uitvoeren wanneer een gebruiker op de werkbalkknop klikt, verbind je een functie met het [PluginToolbarButton.Click](/docs/nl-nl/reference/engine/classes/PluginToolbarButton#Click)  evenement van de knop. In de code voor AddEmptyScript  is de verbindingsfunctie onPluginButtonClicked() .

### [Controleer de selectie van de gebruiker](#controleer-de-selectie-van-de-gebruiker)[](#controleer-de-selectie-van-de-gebruiker)

Om het gedrag van een plugin aan te passen op basis van wat de gebruiker heeft geselecteerd, gebruik je de [Selection](/docs/nl-nl/reference/engine/classes/Selection)  service. De functie onPluginButtonClicked()  controleert of de gebruiker iets heeft geselecteerd en maakt het nieuwe script als kind daarvan in plaats van binnen [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) . Als de gebruiker niets heeft geselecteerd, wordt het nieuwe script in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  gemaakt.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Plugin-Inserted-Script.png)

### [Ondersteun ongedaan maken en opnieuw doen](#ondersteun-ongedaan-maken-en-opnieuw-doen)[](#ondersteun-ongedaan-maken-en-opnieuw-doen)

Gebruik [ChangeHistoryService](/docs/nl-nl/reference/engine/classes/ChangeHistoryService)  om gebruikers in staat te stellen wijzigingen die door een plugin binnen een game zijn aangebracht ongedaan te maken en opnieuw te doen. In je script stel je de plugin in om [TryBeginRecording()](/docs/nl-nl/reference/engine/classes/ChangeHistoryService#TryBeginRecording)  aan te roepen en sla je de identificatie op die aan de API-aanroep is toegewezen voordat je wijzigingen aanbrengt. Stel vervolgens de plugin in om [FinishRecording()](/docs/nl-nl/reference/engine/classes/ChangeHistoryService#FinishRecording)  aan te roepen na het aanbrengen van wijzigingen, zodat het eventuele wijzigingen die tijdens de opname zijn aangebracht voor ongedaan maken en opnieuw doen vastlegt.

Het volgende codevoorbeeld maakt een voorbeeldplugin die het neonmateriaal op geselecteerde onderdelen kan toepassen. Het gebruikt [ChangeHistoryService](/docs/nl-nl/reference/engine/classes/ChangeHistoryService)  om de wijzigingen die door de plugin zijn aangebracht vast te leggen en te beheren:

Voorbeeldmateriaal Plugin met Opnames voor Ongedaan maken en Opnieuw doen

```

local ChangeHistoryService = game:GetService("ChangeHistoryService")

local Selection = game:GetService("Selection")

-- Maak een voorbeeldplugin

local toolbar = plugin:CreateToolbar("Voorbeeld Plugin")

local button = toolbar:CreateButton("Neon het op", "", "")

-- Verbind een functie met het klik evenement

button.Click:Connect(function()

	-- Probeer een opname te beginnen met een specifieke identificatie

	local recording = ChangeHistoryService:TryBeginRecording("Stel selectie in op neon")

	-- Controleer of de opname succesvol is gestart

	if not recording then

		-- Dit geeft aan dat je plugin een eerdere opname is begonnen en deze nooit heeft voltooid

		-- Je kunt per plugin slechts één opname tegelijk actief hebben

		return

	end

	-- Itereer door de geselecteerde instanties

	for _, instance in Selection:Get() do

		-- Controleer of de instantie een BasePart is

		if instance:IsA("BasePart") then

			instance.Material = Enum.Material.Neon -- Stel het materiaal van het onderdeel in op Neon

		end

	end

	-- Voltooi de opname, commit de wijzigingen naar de geschiedenis

	ChangeHistoryService:FinishRecording(recording, Enum.FinishRecordingOperation.Commit)

end)

```

Let op de volgende aandachtspunten met [ChangeHistoryService](/docs/nl-nl/reference/engine/classes/ChangeHistoryService)  opnames:

-

Als je de [Multi-line Command Bar](/docs/nl-nl/studio/overview#opdrachtbalk)  gebruikt, voer dan geen code uit in de commandobar die altijd actief zal zijn terwijl je een plaats open hebt, aangezien de commandobar [ChangeHistoryService](/docs/nl-nl/reference/engine/classes/ChangeHistoryService)  opnames gebruikt om ongedaan maken/opnieuw doen mogelijk te maken met commando's die wijzigingen aanbrengen in het [DataModel](/docs/nl-nl/reference/engine/classes/DataModel) .

-

Het herladen van een plugin annuleert geen lopende [ChangeHistoryService](/docs/nl-nl/reference/engine/classes/ChangeHistoryService)  opnames, dus maak gebruik van [attributen](/docs/nl-nl/scripting/attributes#attributen-aanmaken)  om de laatste opname-identificatie op te slaan, zodat deze door de plugin kan worden geannuleerd wanneer deze opnieuw laadt.

## [Plugins uploaden](#plugins-uploaden)[](#plugins-uploaden)

Nadat je een plugin hebt gemaakt, kun je deze uploaden naar je inventaris zodat deze toegankelijk is in al je projecten.

Om een plugin te uploaden:

1.

Selecteer in het Explorer  venster een plugin-script.

2.

Navigeer naar het Plugins  menu van Studio en selecteer Publiceren als Plugin .

3.

OPTIONEEL

 Klik in de linkerbovenhoek van het venster voor activa-configuratie op de standaard puzzelstukafbeelding om een 512×512 afbeelding miniatuur voor je plugin te uploaden.

4.

Vul de volgende velden in:

-

Naam  — Een titel voor je plugin.

-

Beschrijving  — Een beschrijving die beschrijft wat een potentiële gebruiker kan verwachten dat de plugin doet.

-

Maker  — De maker of groep die je wilt toeschrijven als de maker van de plugin.

5.

Klik op de Indienen  knop. Je plugin is nu beschikbaar voor jou in de [Toolbox](/docs/nl-nl/projects/assets/toolbox)  onder de tabbladen Inventaris  en Creaties .

## [Distribueer en verkoop plugins](#distribueer-en-verkoop-plugins)[](#distribueer-en-verkoop-plugins)

Je kunt je eigen plugins openbaar distribueren en verkopen in de Creator Store zodat anderen deze kunnen gebruiken binnen hun eigen game-ontwikkeling. Deze monetisatiemethode stelt je in staat om 100% van de netto-opbrengsten van transacties te verdienen, waarbij platformkosten en DevEx-tarieven worden omzeild. Voor meer informatie over dit proces, inclusief hoe je een verkopersaccount kunt instellen om prijzen in te stellen en uitbetalingen te ontvangen, zie [Creator Store - Distribueer en verkoop activa](/docs/nl-nl/production/creator-store#verspreiden-en-verkopen-van-assets) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
