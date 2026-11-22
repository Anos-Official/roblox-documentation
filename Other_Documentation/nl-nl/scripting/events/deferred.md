<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/events/deferred -->

Uitgestelde engine-evenementen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Evenementen](/docs/nl-nl/scripting/events)

# Uitgestelde engine-evenementen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [Workspace.SignalBehavior](/docs/nl-nl/reference/engine/classes/Workspace#SignalBehavior)  eigenschap bepaalt of gebeurtenishandlers onmiddellijk of uitgesteld worden uitgevoerd. De [Enum.SignalBehavior.Deferred](/docs/nl-nl/reference/engine/enums/SignalBehavior#Deferred)  optie wordt aanbevolen omdat deze helpt de prestaties en correctheid van de engine te verbeteren. De gebeurtenishandlers voor uitgestelde evenementen  worden hervat op het volgende [hervattingpunt](#hervattingpunten) , samen met eventuele nieuw geactiveerde gebeurtenishandlers.

De [Enum.SignalBehavior.Default](/docs/nl-nl/reference/engine/enums/SignalBehavior#Default)  waarde van [Workspace.SignalBehavior](/docs/nl-nl/reference/engine/classes/Workspace#SignalBehavior)  is momenteel gelijk aan [Enum.SignalBehavior.Immediate](/docs/nl-nl/reference/engine/enums/SignalBehavior#Immediate) , maar zal uiteindelijk veranderen naar [Enum.SignalBehavior.Deferred](/docs/nl-nl/reference/engine/enums/SignalBehavior#Deferred) . Plaatsen in de template zijn standaard direct ingesteld op [Enum.SignalBehavior.Deferred](/docs/nl-nl/reference/engine/enums/SignalBehavior#Deferred) .

De volgende diagram vergelijkt het gedrag van het [Immediate](/docs/nl-nl/reference/engine/enums/SignalBehavior#Immediate)  evenement en het [Deferred](/docs/nl-nl/reference/engine/enums/SignalBehavior#Deferred)  evenement.

-

Met het Immediate  gedrag, als een evenement een ander evenement activeert, wordt de tweede gebeurtenishandler onmiddellijk uitgevoerd.

-

Met het Deferred  gedrag wordt het tweede evenement aan het einde van een wachtrij toegevoegd en later uitgevoerd.

De totale tijd die nodig is verandert niet, maar de volgorde is anders.

 ![Een vergelijking van drie gebeurtenishandlers die worden uitgevoerd met Immediate en Deferred gedrag](https://prod.docsiteassets.roblox.com/assets/scripting/scripts/ImmediateVsDeferredEvents.png)

"Her-invoeren" voorkomt dat evenementen elkaar continu activeren wanneer ze een bepaalde diepte bereiken. De huidige limiet hiervoor is 10.

## [Voordelen van uitgestelde evenementen](#voordelen-van-uitgestelde-evenementen)[](#voordelen-van-uitgestelde-evenementen)

Het Immediate  gedrag heeft enkele nadelen. Voor elke instantie die aan je spel wordt toegevoegd, elke eigenschap die verandert, of een andere trigger die wordt geactiveerd, moet de engine Luau-code uitvoeren voordat er iets anders gebeurt.

-

Om 1.000 eigenschappen te veranderen, moeten er mogelijk 1.000 codefragmenten worden uitgevoerd na elke wijziging.

-

Vreemde, moeilijk te diagnosticeren bugs kunnen optreden, zoals een verwijderingsgebeurtenis die wordt geactiveerd voordat iets zelfs maar is toegevoegd.

-

Prestatiekritische systemen kunnen evenementen activeren die vereisen dat ze heen en weer naar Luau moeten terugkeren.

-

Gebeurtenishandlers kunnen wijzigingen aanbrengen in de plaats of andere evenementen activeren elke keer dat een evenement wordt geactiveerd.

-

Een evenement kan meerdere keren worden geactiveerd ondanks dat het overbodig is, zoals een eigenschap die twee keer verandert.

Door specifieke delen van de levenscyclus van de engine te hebben waarin Luau kan draaien, kan de engine verbeterde prestaties behalen door gebruik te maken van een aantal aannames:

-

Prestatiekritische systemen hoeven niet naar Luau te wachten, wat leidt tot prestatieverbeteringen.

-

Tenzij de engine zelf het verandert, verandert de plaats nooit buiten een hervattingspunt.

## [Hervattingpunten](#hervattingpunten)[](#hervattingpunten)

Na uitstel wordt een gebeurtenishandler hervat op het volgende hervattingspunt. Momenteel omvat de set van hervattingpunten:

-

Invoerverwerking (wordt hervat eenmaal per invoer die moet worden verwerkt, zie [UserInputService](/docs/nl-nl/reference/engine/classes/UserInputService) )

-

[RunService.PreRender](/docs/nl-nl/reference/engine/classes/RunService#PreRender)

-

Legacy wachtende script-hervatting zoals wait() , spawn() , en delay()

-

[RunService.PreAnimation](/docs/nl-nl/reference/engine/classes/RunService#PreAnimation)

-

[RunService.PreSimulation](/docs/nl-nl/reference/engine/classes/RunService#PreSimulation)

-

[RunService.PostSimulation](/docs/nl-nl/reference/engine/classes/RunService#PostSimulation)

-

Wachtende script-hervatting zoals [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait) , [task.spawn()](/docs/nl-nl/reference/engine/libraries/task#spawn) , en [task.delay()](/docs/nl-nl/reference/engine/libraries/task#delay)

-

[RunService.Heartbeat](/docs/nl-nl/reference/engine/classes/RunService#Heartbeat)

-

[DataModel.BindToClose](/docs/nl-nl/reference/engine/classes/DataModel#BindToClose)

## [Veelvoorkomende aangetaste codepatronen](#veelvoorkomende-aangetaste-codepatronen)[](#veelvoorkomende-aangetaste-codepatronen)

Met externe evenementen werken de volgende voorbeelden of stoppen met correct functioneren of hebben subtiel ander gedrag; ze zijn afhankelijk van evenementen die onmiddellijk worden hervat.

### [Trigger en vang evenementen halverwege de uitvoering](#trigger-en-vang-evenementen-halverwege-de-uitvoering)[](#trigger-en-vang-evenementen-halverwege-de-uitvoering)

In dit voorbeeld wordt altijd false  geretourneerd wanneer uitgestelde evenementen zijn ingeschakeld omdat de callback nog niet is uitgevoerd. Om correct te werken, moet de thread wachten totdat het evenement ten minste had moeten worden geactiveerd.

```

local success = false

event:Connect(function ()

   success = true

end)

doSomethingToTriggerEvent() -- Zorgt ervoor dat `event` wordt geactiveerd

return success

```

### [Luister naar de eerste keer dat een evenement voorkomt](#luister-naar-de-eerste-keer-dat-een-evenement-voorkomt)[](#luister-naar-de-eerste-keer-dat-een-evenement-voorkomt)

```

connection = event:Connect(function ()

   connection:Disconnect()

   -- doe iets

end)

```

Met uitgestelde evenementen ingeschakeld, kunnen meerdere aanroepen van de gebeurtenishandler in de wachtrij worden geplaatst voordat je de verbinding met het evenement verbreekt. Het aanroepen van [Disconnect()](/docs/nl-nl/reference/engine/classes/Instance#Disconnect)  laat alle uitstaande aanroepen van de gebeurtenishandler vallen—dezelfde gedrag dat bestaat voor onmiddellijke evenementen.

Elke andere methode van ontkoppeling naast [Disconnect()](/docs/nl-nl/reference/engine/classes/Instance#Disconnect) , zoals het aanroepen van [Destroy()](/docs/nl-nl/reference/engine/classes/Instance#Destroy)  op de [Instance](/docs/nl-nl/reference/engine/classes/Instance) , ontkoppelt het signaal onmiddellijk, maar voert de bijbehorende gebeurtenishandler uit voor alle evenementen die nog in behandeling zijn.

Als alternatief kun je [Once()](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal#Once)  gebruiken als een handigere methode om verbinding te maken met een evenement waarvan je alleen de eerste aanroep nodig hebt.

### [Evenementen die afstamming of eigenschappen veranderen](#evenementen-die-afstamming-of-eigenschappen-veranderen)[](#evenementen-die-afstamming-of-eigenschappen-veranderen)

Uitgestelde evenementen zorgen ervoor dat evenementen die een verandering in afstamming of een eigenschap afhandelen, worden geactiveerd nadat de afstamming of eigenschap is veranderd:

```

local part = Instance.new("Part", workspace)

local function onPartDestroying()

	print("In signaal:", part:GetFullName(), #part:GetChildren())

end

part.Destroying:Connect(onPartDestroying)

part:Destroy()

```

Omdat [Destroy()](/docs/nl-nl/reference/engine/classes/Instance#Destroy)  onmiddellijk werkt nadat het script dat het aanroept wacht, is de instantie al vernietigd tegen de tijd dat onPartDestroying()  wordt aangeroepen. Voor meer voorbeelden, zie [Instance.Destroying](/docs/nl-nl/reference/engine/classes/Instance#Destroying) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
