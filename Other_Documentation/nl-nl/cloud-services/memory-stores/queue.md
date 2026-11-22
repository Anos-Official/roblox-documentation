<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/memory-stores/queue -->

Geheugenopslag wachtrij | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Geheugenopslag](/docs/nl-nl/cloud-services/memory-stores)

# Geheugenopslag wachtrij

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een wachtrij  is een lineaire gegevensstructuur met een verzameling items die ofwel het first-in-first-out (FIFO) principe volgt of elementen prioriteert op basis van vooraf gedefinieerde criteria. [Geheugenopslag](/docs/nl-nl/cloud-services/memory-stores)  ondersteunt twee soorten wachtrijen, de FIFO [gewone wachtrijen](/docs/nl-nl/luau/queues#gewone-wachtrijen)  en [prioriteitswachtrijen](/docs/nl-nl/luau/queues#prioriteitswachtrijen) . Beide typen delen dezelfde set functies voor het initialiseren van een lege wachtrij, het toevoegen van gegevens aan de wachtrij, het lezen van gegevens uit de wachtrij en het verwijderen van gegevens uit de wachtrij.

Geheugenopslag wachtrijen zijn nuttig voor op volgorde gebaseerde verwerking en het opslaan van gebruikersinformatie, zoals vaardigheidsniveaus, om matchmaking op basis van jouw gewenste criteria te vergemakkelijken. Je kunt bijvoorbeeld een lobbyplaats toevoegen als de startplaats van je spel, geheugenopslag wachtrijen gebruiken als een gecentraliseerd systeem voor het opslaan van gebruikersinformatie dat toegankelijk is voor meerdere servers, de plaatsingsvolgorde van gebruikers beheren met behulp van de wachtrijen, en gebruikers die de matchmaking hebben voltooid naar de hoofdplaats van je spel teleporteren.

## [Verkrijg een wachtrij](#verkrijg-een-wachtrij)[](#verkrijg-een-wachtrij)

Om een wachtrij te verkrijgen, roep je [MemoryStoreService:GetQueue()](/docs/nl-nl/reference/engine/classes/MemoryStoreService#GetQueue)  aan met een naam , die globaal binnen het spel is voor elk script om toegang te krijgen, en een optionele onzichtbaarheidstime-out  in seconden, die voorkomt dat hetzelfde wachtrijitem dubbel wordt verwerkt. De onzichtbaarheidstime-out is standaard 30 seconden als je deze leeg laat, zoals in het volgende codevoorbeeld.

Een lege wachtrij verkrijgen

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local queue = MemoryStoreService:GetQueue("Queue1")

```

Wanneer een wachtrij een item aan het verwerken is, is de onzichtbaarheidstime-out van toepassing op het item, waardoor het onzichtbaar wordt voor verwerking door andere servers, aangezien meerdere servers de wachtrij gelijktijdig kunnen bijwerken. Hoewel het wordt verwacht dat zowel lees- als verwijderbewerkingen voor een item tijdens de duur van de onzichtbaarheidstime-out worden voltooid, als er een fout optreedt die ervoor zorgt dat het item in de wachtrij blijft nadat de time-out is verstreken, worden de items weer zichtbaar voor verwerking. Door dit te doen, garandeert de onzichtbaarheidstime-out dat alle items in een wachtrij nog steeds kunnen worden verwerkt, zelfs als er onverwachte problemen optreden.

Nadat je een wachtrij hebt verkregen, kun je een van de volgende functies aanroepen:

| Functie | | Actie |
| --- | --- |
| [MemoryStoreQueue:AddAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#AddAsync) | | [Voeg](#voeg-gegevens-toe)  een nieuw item toe aan de wachtrij. |
| [MemoryStoreQueue:ReadAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#ReadAsync) | | [Lees](#lees-en-verwijder-gegevens)  een of meer items uit de wachtrij als een enkele bewerking. |
| [MemoryStoreQueue:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#RemoveAsync) | | [Verwijder](#lees-en-verwijder-gegevens)  een of meer items die eerder uit de wachtrij zijn gelezen. |
| [MemoryStoreQueue:GetSizeAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#GetSizeAsync) | | [Krijg](#verkrijg-grootte)  het aantal items in de wachtrij. |

Alle functies die toegang hebben tot gegevensstructuren in geheugenopslag zijn asynchrone netwerkoproepen die af en toe kunnen mislukken. Je moet deze oproepen omhullen in [pcall()](/docs/nl-nl/reference/engine/globals/LuaGlobals#pcall)  om fouten op te vangen en af te handelen, zoals het codevoorbeeld in elke sectie laat zien.

## [Voeg gegevens toe](#voeg-gegevens-toe)[](#voeg-gegevens-toe)

Om een nieuw item aan de wachtrij toe te voegen, roep je [MemoryStoreQueue:AddAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#AddAsync)  aan met de itemwaarde, een vervaltijd in seconden en een optionele prioriteit van het item. Als je je wachtrij in de FIFO-volgorde wilt houden, kun je de prioriteit leeg laten of 0  doorgeven.

Gegevens toevoegen aan een wachtrij

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local queue = MemoryStoreService:GetQueue("Queue1")

local addSuccess, addError = pcall(function()

	queue:AddAsync("User_1234", 30, 1)

end)

if not addSuccess then

	warn(addError)

end

```

## [Lees en verwijder gegevens](#lees-en-verwijder-gegevens)[](#lees-en-verwijder-gegevens)

Om een of meer items tegelijk uit de wachtrij te lezen, roep je [MemoryStoreQueue:ReadAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#ReadAsync)  aan, wat een id  retourneert die het gelezen item vertegenwoordigt. Wanneer je klaar bent met het verwerken van items, roep je onmiddellijk [MemoryStoreQueue:RemoveAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#RemoveAsync)  aan om ze met hun id  uit de wachtrij te verwijderen. Dit zorgt ervoor dat je een item nooit meer dan eens verwerkt. Om alle items die continu aan een wachtrij worden toegevoegd vast te leggen en hierop te reageren, voeg je een [lus](/docs/nl-nl/luau/control-structures)  toe zoals in het volgende codevoorbeeld:

Gegevens lezen en verwijderen uit de wachtrij met een lus

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local queue = MemoryStoreService:GetQueue("Queue1")

local addSuccess, addError = pcall(function()

	queue:AddAsync("User_1234", 30, 1)

end)

if not addSuccess then

	warn(addError)

end

-- Wachtrijverwerkingslus

while true do

	local readSuccess, items, id = pcall(function()

		return queue:ReadAsync(1, false, 30)

	end)

	if not readSuccess then

		task.wait(1)

	elseif #items > 0 then

		print(items, id)

		local removeSuccess, removeError = pcall(function()

			queue:RemoveAsync(id)

		end)

		if not removeSuccess then

			warn(removeError)

		end

	end

end

```

## [Verkrijg grootte](#verkrijg-grootte)[](#verkrijg-grootte)

Om het aantal items in de wachtrij te krijgen, roep je [MemoryStoreQueue:GetSizeAsync()](/docs/nl-nl/reference/engine/classes/MemoryStoreQueue#GetSizeAsync)  aan. Deze methode neemt een optionele boolean excludeInvisible . Wanneer deze waar  is, worden onzichtbare items uitgesloten van de geretourneerde telling. Deze boolean is standaard onwaar .

De grootte van een wachtrij verkrijgen

```

local MemoryStoreService = game:GetService("MemoryStoreService")

local queue = MemoryStoreService:GetQueue("Queue1")

local addSuccess, addError = pcall(function()

	return queue:AddAsync("User_1234", 30, 1)

end)

if not addSuccess then

	warn(addError)

end

local size

local success, sizError = pcall(function()

	size = queue:GetSizeAsync(true)

end)

if success then

	print(size)

else

	warn(sizeError)

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
