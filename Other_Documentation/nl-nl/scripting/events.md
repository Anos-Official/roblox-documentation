<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/events -->

Evenementen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Evenementen](/docs/nl-nl/scripting/events)

# Evenementen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Evenementen zijn gebeurtenissen binnen je spel waar je naar kunt luisteren en op kunt reageren. Veel Roblox-services en objecten hebben ingebouwde evenementen die automatisch afgaan  als reactie op specifieke acties of veranderingen.

Bijvoorbeeld, het aanraken van een [Character](/docs/nl-nl/reference/engine/classes/Player#Character)  door een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  activeert automatisch een [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  evenement. Elke keer dat een speler je spel betreedt, wordt het [Players.PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded)  evenement geactiveerd.

Vanwege het enorme aantal evenementen en de client-serverarchitectuur wordt Roblox-scripting vaak aangeduid als evenementgestuurd . Deze benadering verschilt van veel andere game-engines, die de nadruk leggen op het uitvoeren van code op basis van frames.

Je hoeft niet naar evenementen te luisteren of actie te ondernemen als reactie daarop, maar de evenementen worden toch geactiveerd en zijn beschikbaar. Wanneer je wel wilt reageren op een evenement, verbind je een functie eraan.

Uitgestelde evenementen kunnen je helpen om een betere prestatie en consistente evenementverwerking te waarborgen. Zie [hier](/docs/nl-nl/scripting/events/deferred)  voor meer informatie.

## [Verbind functies met evenementen](#verbind-functies-met-evenementen)[](#verbind-functies-met-evenementen)

Je verbindt een functie met een evenement met behulp van [Connect()](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal#Connect)  om code uit te voeren elke keer dat het evenement afgaat. De meeste evenementen geven argumenten door aan hun verbonden functies. Bijvoorbeeld, het [BasePart.Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  evenement geeft het object door dat het deel aanraakte (zoals een linkerhand of autoband), en het [Players.PlayerAdded](/docs/nl-nl/reference/engine/classes/Players#PlayerAdded)  evenement geeft de [Player](/docs/nl-nl/reference/engine/classes/Player)  door die je spel betrad.

De volgende codevoorbeeld toont hoe je een functie genaamd onPartTouched()  verbindt met het [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  evenement van een deel:

```

-- Gaat ervan uit dat het script aan het deel is gekoppeld

local part = script.Parent

-- De functie die je wilt uitvoeren

local function onPartTouched(object)

	print("Het deel is aangeraakt door", object:GetFullName())

end

-- Verbind de functie met het Touched evenement van het deel

part.Touched:Connect(onPartTouched)

```

Als beste praktijk en voor optimale prestaties is het aan te raden om functies te [ontkoppelen](#ontkoppel-functies-van-evenementen)  wanneer de verbinding niet langer nodig is. Houd er echter rekening mee dat dit niet altijd  nodig is, aangezien alle verbindingen met de [niet-uitgestelde](/docs/nl-nl/scripting/events/deferred)  evenementen van een object automatisch worden ontkoppeld als een object wordt vernietigd.

Je kunt ook [anonieme functies](/docs/nl-nl/luau/functions#anonieme-functies)  aan evenementen koppelen wanneer je variabelen in de bovenliggende scope wilt gebruiken en de functie niet elders nodig hebt. Bijvoorbeeld, dit codevoorbeeld vermijdt de ongemakkelijke tussenliggende functie van het vergelijkbare voorbeeld in [Services](/docs/nl-nl/scripting/services) :

```

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local SaveManager = require(ReplicatedStorage:WaitForChild("SaveManager"))

local function saveProgress(character)

	local position = character:FindFirstChild("HumanoidRootPart").Position

	SaveManager.saveData(character, position)

end

-- Anonieme functie die saveProgress() aanroept wanneer een karakter uit het spel wordt verwijderd

-- (in dit geval, wanneer de speler vertrekt).

Players.PlayerAdded:Connect(function(player)

	player.CharacterRemoving:Connect(saveProgress)

end)

```

## [Ontkoppel functies van evenementen](#ontkoppel-functies-van-evenementen)[](#ontkoppel-functies-van-evenementen)

De [Connect()](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal#Connect)  methode retourneert een [RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)  object. Als je een functie aan een evenement verbindt, maar de functie niet wilt aanroepen de volgende keer dat een evenement afgaat (bijvoorbeeld nadat aan een bepaalde voorwaarde is voldaan), ontkoppel het door [Disconnect()](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection#Disconnect)  aan te roepen op het [RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)  object.

De volgende codevoorbeeld toont hoe je een functie verbindt en ontkoppelt van het [Part.Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  evenement:

```

local Workspace = game:GetService("Workspace")

local part = Workspace.Part

local targetPart = Workspace.TargetPart

-- Verklaar een lege placeholder variabele voor de verbinding

local connection

local function onPartTouched(otherPart)

	if otherPart == targetPart then

		print("Het deel raakte het doel aan!")

		-- Ontkoppel de verbinding

		connection:Disconnect()

	end

end

-- Verbind de bovenstaande functie met het Touched evenement

connection = part.Touched:Connect(onPartTouched)

```

Als je alleen een functie eenmaal aan een evenement wilt verbinden — dat wil zeggen, de functie alleen de eerste keer laten uitvoeren dat het evenement afgaat — gebruik dan de [Once()](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal#Once)  methode als een handigere alternatieve manier om de functie te verbinden en te ontkoppelen.

Wanneer Luau een object van een evenement vernietigt, zoals het [Player](/docs/nl-nl/reference/engine/classes/Player)  object wanneer een gebruiker het spel verlaat, worden alle [niet-uitgestelde](/docs/nl-nl/scripting/events/deferred)  verbindingen automatisch ontkoppeld.

## [Wacht op evenementen om af te gaan](#wacht-op-evenementen-om-af-te-gaan)[](#wacht-op-evenementen-om-af-te-gaan)

Als je wilt dat een script wacht totdat een specifiek evenement afgaat, gebruik dan de [Wait()](/docs/nl-nl/reference/engine/datatypes/RBXScriptSignal#Wait)  methode. Deze methode retourneert de argumenten van het evenement, die je aan variabelen kunt toewijzen voor later gebruik:

```

local Workspace = game:GetService("Workspace")

local part = Workspace.Part

local touchedPart = part.Touched:Wait()

print("Het deel is aangeraakt door", touchedPart:GetFullName())

```

## [Andere soorten evenementen](#andere-soorten-evenementen)[](#andere-soorten-evenementen)

-

[Bindbare evenementen](/docs/nl-nl/scripting/events/bindable)  stellen je in staat om te communiceren tussen scripts aan de zelfde kant  van de client-servergrens.

-

[Remote evenementen](/docs/nl-nl/scripting/events/remote)  stellen je in staat om te communiceren over  de client-servergrens.

-

[Uitgestelde engine-evenementen](/docs/nl-nl/scripting/events/deferred)  stellen evenementhandlers uit tot bepaalde hervattingspunten.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
