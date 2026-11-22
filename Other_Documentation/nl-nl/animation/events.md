<!-- Source: https://create.roblox.com/docs/nl-nl/animation/events -->

Animatie-evenementen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Animatie](/docs/nl-nl/animation)
6. /
7. Animaties maken
8. /
9. [Animatie-editor](/docs/nl-nl/animation/editor)

# Animatie-evenementen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt animatie evenementmarkeringen  over de tijdlijn definiëren en gebruik maken van [GetMarkerReachedSignal()](/docs/nl-nl/reference/engine/classes/AnimationTrack#GetMarkerReachedSignal)  om die markeringen te detecteren terwijl de animatie draait.

Standaard is het evenementspoor niet zichtbaar. Om het evenementspoor weer te geven:

1.

Navigeer naar de rechterkant van de tijdlijn en klik op het instellingenpictogram. Een pop-upmenu verschijnt.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Timeline-Options-Menu.png)

2.

Selecteer Toon Animatie-evenementen . Dit opent de Animatie-evenementen -balk direct onder de media- en afspeelbesturingselementen.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Animation-Events-Bar.png)

## [Maak evenementen](#maak-evenementen)[](#maak-evenementen)

Evenementmarkeringen zijn visuele indicatoren van waar een animatie-evenement begint. Nadat je een evenementmarkering hebt gemaakt, kun je deze naar elke framepositie op de tijdlijn verplaatsen.

Om een nieuwe evenementmarkering te maken:

1.

Navigeer naar de tijdlijn en sleep de scrubber naar de framepositie waar het evenement moet plaatsvinden.

2.

Navigeer naar het evenementspoor  en klik op de knop Bewerk Animatie-evenementen .

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Animation-Events-Edit-Button.png)

3.

Klik in de dialoog op + Voeg Evenement Toe , en voer een evenementnaam in.

4.

OPTIONEEL

 Voer in het veld Parameter  een parameterstring voor het evenement in.

5.

Klik op de knop Opslaan . In de evenementenbalk binnen de tijdlijn verschijnt een nieuw markeringssymbool op de framepositie.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Animation-Events-Marker-In-Timeline.png)

## [Detecteer evenementen](#detecteer-evenementen)[](#detecteer-evenementen)

Om animatie-evenementen te detecteren in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) , verbind je een functie met de [GetMarkerReachedSignal()](/docs/nl-nl/reference/engine/classes/AnimationTrack#GetMarkerReachedSignal)  functie van [AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack) . Bijvoorbeeld:

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

local character = player.Character or player.CharacterAdded:Wait()

local humanoid = character:WaitForChild("Humanoid")

local animator = humanoid:WaitForChild("Animator")

-- Maak een nieuwe "Animatie" instantie

local walkAnim = Instance.new("Animation")

-- Stel de "AnimationId" in op de bijbehorende animatie asset ID

walkAnim.AnimationId = "rbxassetid://5432167890"

-- Laad animatie op de animator

local walkAnimTrack = animator:LoadAnimation(walkAnim)

-- Verbind "GetMarkerReachedSignal" evenement met een specifieke genaamde keyframe

walkAnimTrack:GetMarkerReachedSignal("FootStep"):Connect(function(paramString)

	print(paramString)

end)

```

Je kunt een Parameter  waarde specificeren voor elke evenementmarkering binnen de animatie-editor. Dit stelt je in staat om een aangepaste string  (enkele waarde, door komma's gescheiden string, enz.) door te geven aan de [GetMarkerReachedSignal()](/docs/nl-nl/reference/engine/classes/AnimationTrack#GetMarkerReachedSignal)  methode, zoals geïllustreerd door de paramString  argument in het bovenstaande codevoorbeeld. Deze string kan vervolgens worden geparsed of geconverteerd, indien nodig, en gebruikt voor welke actie je ook wilt uitvoeren in het evenement.

## [Dupliceer evenementen](#dupliceer-evenementen)[](#dupliceer-evenementen)

Naarmate je evenementen maakt, worden ze beschikbaar voor gebruik gedurende de hele animatie, niet alleen op de framepositie waar je ze oorspronkelijk hebt gemaakt. Bijvoorbeeld, je kunt een FootStep  evenementmarkering maken op het punt waar de linker  voet van een karakter neerkomt, en vervolgens hetzelfde evenement gebruiken wanneer de rechter  voet van het karakter neerkomt.

Om een evenement te dupliceren:

1.

Klik met de rechtermuisknop op een evenementmarkering  in de evenementenbalk en selecteer Geselecteerde Kopiëren  in het contextmenu.

 ![](https://prod.docsiteassets.roblox.com/assets/animation/animation-editor/Animation-Events-Marker-In-Timeline.png)

2.

Klik met de rechtermuisknop op een ander tijdstip langs de tijdlijn en selecteer Plak Evenementen . Het gekopieerde evenement wordt ingevoegd op de tijdpositie die het dichtst bij je klik ligt.

3.

OPTIONEEL

 Als het originele evenement een parameter  gebruikt, maar het gedupliceerde evenement een gewijzigde parameter moet gebruiken, voer dan de volgende stappen uit:

1.

Klik met de rechtermuisknop op de gedupliceerde evenementmarkering en selecteer Bewerk Animatie-evenement  in het contextmenu. De Bewerk Animatie-evenementen  dialoog verschijnt.

2.

Breng je wijzigingen aan en klik op de knop Opslaan .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
