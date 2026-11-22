<!-- Source: https://create.roblox.com/docs/nl-nl/ui/labels -->

Tekst- en afbeeldingslabels | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. UI-objecten

# Tekst- en afbeeldingslabels

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Labels  zijn [GuiObjects](/docs/nl-nl/reference/engine/classes/GuiObject)  die je in staat stellen om aanpasbare tekst en afbeeldingen [op het scherm](/docs/nl-nl/ui/on-screen-containers)  of [in de game](/docs/nl-nl/ui/in-experience-containers)  weer te geven. Er zijn twee soorten labels:

-

Een [TextLabel](/docs/nl-nl/reference/engine/classes/TextLabel)  is een rechthoek met tekst die je kunt stylen via aanpasbare eigenschappen. Dit is de primaire manier om tekst in een game weer te geven.

-

Een [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel)  is een rechthoek met een afbeeldings [asset](/docs/nl-nl/projects/assets)  die je kunt stylen via aanpasbare eigenschappen. Samen met [texturen en decals](/docs/nl-nl/parts/textures-decals)  stelt dit je in staat om afbeeldingen in een game weer te geven.

## [Labels op het scherm maken](#labels-op-het-scherm-maken)[](#labels-op-het-scherm-maken)

Labels op een scherm zijn nuttig voor dingen zoals het weergeven van afbeeldingen van personages met dialoog.

Om een label aan een scherm toe te voegen:

1.

Selecteer in het Explorer -venster StarterGui  en voeg een ScreenGui  toe.

1.

Beweeg de muis over StarterGui en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu een ScreenGui .

2.

Selecteer de nieuwe ScreenGui  en voeg een label toe.

1.

Beweeg de muis over ScreenGui  en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu een TextLabel  of ImageLabel .

 ![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-Screen-New.jpg)

## [Labels op de gezichten van onderdelen maken](#labels-op-de-gezichten-van-onderdelen-maken)[](#labels-op-de-gezichten-van-onderdelen-maken)

Labels op een onderdeel zijn nuttig voor dingen zoals het maken van billboards, posters en wallpapers.

Om een label aan het gezicht van een onderdeel toe te voegen:

1.

Voeg in het Explorer -venster een SurfaceGui  toe aan het onderdeel.

1.

Beweeg de muis over de onderdeelinstantie en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu een SurfaceGui .

2.

Selecteer de nieuwe SurfaceGui  en voeg een label toe.

1.

Beweeg de muis over de SurfaceGui  en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu een TextLabel  of ImageLabel .

 ![](https://prod.docsiteassets.roblox.com/assets/ui/button-text-input/ImageButton-SurfaceGui-New.jpg)

Als je de knop niet ziet, probeer dan [een ander gezicht te kiezen](/docs/nl-nl/parts/textures-decals#choose-a-face)  in de ** Face**  eigenschap van de ** SurfaceGui** .

## [Eigenschappen van ImageLabel aanpassen](#eigenschappen-van-imagelabel-aanpassen)[](#eigenschappen-van-imagelabel-aanpassen)

Alle afbeeldingen binnen een [ImageLabel](/docs/nl-nl/reference/engine/classes/ImageLabel)  moeten assets zijn die zijn [geïmporteerd](/docs/nl-nl/projects/assets/manager#asset-import)  naar Studio. Terwijl de afbeelding automatisch schaalt om in het gebied van de rechthoek te passen, ziet de afbeelding er het beste uit wanneer deze op zijn oorspronkelijke resolutie wordt weergegeven.

Je kunt het visuele uiterlijk van een afbeelding aanpassen met de volgende eigenschappen:

-

[ImageColor3](/docs/nl-nl/reference/engine/classes/ImageLabel#ImageColor3)

-

[ImageTransparency](/docs/nl-nl/reference/engine/classes/ImageLabel#ImageTransparency)

-

[BackgroundTransparency](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundTransparency)

Bijvoorbeeld, om alleen de afbeelding weer te geven en de rechthoek te verbergen, stel je de [BackgroundTransparency](/docs/nl-nl/reference/engine/classes/GuiObject#BackgroundTransparency)  eigenschap in op 1 .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
