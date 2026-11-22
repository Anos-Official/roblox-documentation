<!-- Source: https://create.roblox.com/docs/nl-nl/ui/buttons -->

Tekst- en afbeeldingsknoppen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. UI-objecten

# Tekst- en afbeeldingsknoppen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[GuiButtons](/docs/nl-nl/reference/engine/classes/GuiButton)  zijn [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  die spelers in staat stellen om een actie uit te voeren. Je kunt deze knoppen aanpassen om context en feedback te bieden, zoals het veranderen van het visuele uiterlijk of [scripting](#scriptknoppen)  van hoorbare feedback wanneer een speler met een knop interacteert.

Er zijn twee soorten knoppen die je kunt plaatsen [op het scherm](/docs/nl-nl/ui/on-screen-containers)  of [in het spel](/docs/nl-nl/ui/in-experience-containers) :

-

Een [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  is een rechthoek met tekst die de [Activated](/docs/nl-nl/reference/engine/classes/GuiButton#Activated)  en/of [SecondaryActivated](/docs/nl-nl/reference/engine/classes/GuiButton#SecondaryActivated)  gebeurtenis activeert bij klikken/tikken.

-

Een [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  is een rechthoek met een afbeelding die de [Activated](/docs/nl-nl/reference/engine/classes/GuiButton#Activated)  en/of [SecondaryActivated](/docs/nl-nl/reference/engine/classes/GuiButton#SecondaryActivated)  gebeurtenis activeert bij klikken/tikken. Het heeft extra toestanden voor het wisselen van de afbeelding bij het hoveren of indrukken door de speler.

## [Knoppen op het scherm](#knoppen-op-het-scherm)[](#knoppen-op-het-scherm)

Knoppen [op het scherm](/docs/nl-nl/ui/on-screen-containers)  zijn nuttig om spelers snel naar verschillende menu's of pagina's te leiden. Om dit type knop toe te voegen:

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, beweeg over [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) , klik op de ⊕ knop en voeg een [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui)  toe.

2.

Beweeg over de nieuwe [ScreenGui](/docs/nl-nl/reference/engine/classes/ScreenGui) , klik op de ⊕ knop en voeg een [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  of [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  toe.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-Screen-New.jpg)

## [Knoppen op de gezichten van onderdelen](#knoppen-op-de-gezichten-van-onderdelen)[](#knoppen-op-de-gezichten-van-onderdelen)

Knoppen op een onderdeel zijn nuttig om spelers in staat te stellen om met onderdelen te interageren. Bijvoorbeeld, je kunt spelers laten staan op een knop om een actie te voltooien.

Om een knop toe te voegen aan het gezicht van een onderdeel:

1.

In het [Explorer](/docs/nl-nl/studio/explorer)  venster, beweeg over het onderdeel , klik op de ⊕ knop en voeg een [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui)  toe.

2.

Beweeg over de nieuwe [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui) , klik op de ⊕ knop en voeg een [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  of [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  toe.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-SurfaceGui-New.jpg)

Als je de knop niet ziet, probeer dan een ander gezicht te kiezen ([Top](/docs/nl-nl/reference/engine/enums/NormalId#Top) , [Bottom](/docs/nl-nl/reference/engine/enums/NormalId#Bottom) , [Front](/docs/nl-nl/reference/engine/enums/NormalId#Front) , [Back](/docs/nl-nl/reference/engine/enums/NormalId#Back) , [Left](/docs/nl-nl/reference/engine/enums/NormalId#Left) , of [Right](/docs/nl-nl/reference/engine/enums/NormalId#Right) ) voor de [Face](/docs/nl-nl/reference/engine/classes/SurfaceGui#Face)  eigenschap van de [SurfaceGui](/docs/nl-nl/reference/engine/classes/SurfaceGui) .

## [Uiterlijk van knoppen](#uiterlijk-van-knoppen)[](#uiterlijk-van-knoppen)

Zowel [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  als [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  erven van [GuiObject](/docs/nl-nl/reference/engine/classes/GuiObject)  dat eigenschappen bevat zoals [BackgroundColor3](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundColor3) , [Rotation](/docs/nl-nl/reference/engine/classes/GuiObject#Rotation) , en [Size](/docs/nl-nl/reference/engine/classes/GuiObject#Size) . Knoppen accepteren ook de [uiterlijkmodificatoren](/docs/nl-nl/ui/appearance-modifiers)  die gebruikelijk zijn voor de meeste UI-objecten.

Uniek voor [TextButton](/docs/nl-nl/reference/engine/classes/TextButton)  zijn verschillende eigenschappen om het visuele uiterlijk te veranderen:

-

[FontFace](/docs/nl-nl/reference/engine/classes/TextButton#FontFace)  — Het lettertype dat wordt gebruikt om tekst weer te geven.

-

[Text](/docs/nl-nl/reference/engine/classes/TextButton#Text)  — De tekststring die op de knop wordt weergegeven.

-

[TextSize](/docs/nl-nl/reference/engine/classes/TextButton#TextSize)  — De regelhoogte van tekst in offsets.

-

[TextColor3](/docs/nl-nl/reference/engine/classes/TextButton#TextColor3)  — Kleur van de weergegeven tekst.

Een [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  heeft verschillende eigenschappen om het visuele uiterlijk te veranderen, inclusief hover- en ingedrukte afbeeldingsvarianten om de interactie van een speler met de knop aan te geven:

-

[Image](/docs/nl-nl/reference/engine/classes/ImageButton#Image)  — De afbeelding die wordt weergegeven wanneer een speler niet met de [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  interageert.

-

[HoverImage](/docs/nl-nl/reference/engine/classes/ImageButton#HoverImage)  — De afbeelding die wordt weergegeven wanneer een speler zijn cursor boven de [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  houdt.

-

[PressedImage](/docs/nl-nl/reference/engine/classes/ImageButton#PressedImage)  — De afbeelding die wordt weergegeven wanneer een speler op de [ImageButton](/docs/nl-nl/reference/engine/classes/ImageButton)  klikt/tikt.

![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-State-Normal.png) Normaal

![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-State-Hover.png) Hover

![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-State-Pressed.png) Ingedeukt

## [Scriptknoppen](#scriptknoppen)[](#scriptknoppen)

Je kunt een actie scriptten wanneer een speler op een knop drukt door de knop te verbinden met de [GuiButton.Activated](/docs/nl-nl/reference/engine/classes/GuiButton#Activated)  gebeurtenis, of met [GuiButton.SecondaryActivated](/docs/nl-nl/reference/engine/classes/GuiButton#SecondaryActivated)  voor cross-platform secundaire invoer zoals rechtsklikken op desktop en lang indrukken op mobiel. Bijvoorbeeld, wanneer je de volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  aan een knop toevoegt, verandert de knop elke keer dat een speler erop klikt/tikt in een willekeurige kleur.

```

local button = script.Parent

local RNG = Random.new()

local function onButtonActivated()

	-- Randomiseer de knopkleur

	button.BackgroundColor3 = Color3.fromHSV(RNG:NextNumber(), 1, 1)

end

button.Activated:Connect(onButtonActivated)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
