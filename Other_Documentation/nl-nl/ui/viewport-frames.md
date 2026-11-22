<!-- Source: https://create.roblox.com/docs/nl-nl/ui/viewport-frames -->

Weergaveframes | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Gebruikersinterface](/docs/nl-nl/ui)
6. /
7. UI-objecten

# Weergaveframes

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een [ViewportFrame](/docs/nl-nl/reference/engine/classes/ViewportFrame)  gebruikt een camera om 3D-objecten in een 2D-weergave te renderen. Ideale gebruiksscenario's zijn onder andere:

-

Een minimap van je spel direct in de hoek van het scherm van een gebruiker.

-

3D-modellen van items in een inventaris menu.

-

Draaien objecten die een personage heeft uitgerust.

## [Weergaveconfiguraties](#weergaveconfiguraties)[](#weergaveconfiguraties)

3D-objecten die gebruikers bekijken via een [ViewportFrame](/docs/nl-nl/reference/engine/classes/ViewportFrame)  kunnen ofwel met hun camera bewegen, statisch blijven, of binnen de [ViewportFrame](/docs/nl-nl/reference/engine/classes/ViewportFrame)  draaien. Dit object kan ook een [Sky](/docs/nl-nl/reference/engine/classes/Sky)  kind bevatten als een cubemap voor reflecties.

Met Camera Statisch Rotatie Skybox Reflecties

Als je wilt dat een 3D-object met de camera beweegt:

1.

Positioneer je camerabeeld binnen het spel zodat het object dat je binnen het frame wilt zien zichtbaar is.

2.

Voeg een nieuwe [ViewportFrame](/docs/nl-nl/reference/engine/classes/ViewportFrame)  toe aan het [scherm](/docs/nl-nl/ui/on-screen-containers)  en zorg ervoor dat deze is geselecteerd in de Explorer .

3.

In het Eigenschappen  venster, wijs de [CurrentCamera](/docs/nl-nl/reference/engine/classes/ViewportFrame#CurrentCamera)  eigenschap toe aan de camera:

1.

Selecteer de [CurrentCamera](/docs/nl-nl/reference/engine/classes/ViewportFrame#CurrentCamera)  eigenschap. Je cursor verandert.

2.

Klik in het Explorer  venster op het bovenste [Camera](/docs/nl-nl/reference/engine/classes/Camera)  object.

4.

Maak het gewenste 3D-object een kind van de nieuwe [ViewportFrame](/docs/nl-nl/reference/engine/classes/ViewportFrame) . Let op dat als je het object nog steeds binnen je spel wilt zien, je het moet dupliceren in de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  en vervolgens het gedupliceerde  object aan de [ViewportFrame](/docs/nl-nl/reference/engine/classes/ViewportFrame)  moet koppelen.

Wanneer je je camera verplaatst, zal het object ook binnen de [ViewportFrame](/docs/nl-nl/reference/engine/classes/ViewportFrame)  bewegen.

Wanneer je de weergave van je [ViewportFrame](/docs/nl-nl/reference/engine/classes/ViewportFrame)  wilt bijwerken, zorg er dan voor dat je de camera bijwerkt, niet  de objecten binnen de weergave.

## [Verlichting en uiterlijk](#verlichting-en-uiterlijk)[](#verlichting-en-uiterlijk)

Verlichting binnen een [ViewportFrame](/docs/nl-nl/reference/engine/classes/ViewportFrame)  wordt geregeld via drie eigenschappen:

| Eigenschap | | Beschrijving |
| --- | --- |
| [Ambient](/docs/nl-nl/reference/engine/classes/ViewportFrame#Ambient) | | Bepaalt de algehele lichtkleur die op het gebied binnen het viewport frame wordt toegepast. Standaard is dit [Color3.fromRGB(200, 200, 200)](/docs/nl-nl/reference/engine/datatypes/Color3#fromRGB)  (spookgrijs). |
| [LightDirection](/docs/nl-nl/reference/engine/classes/ViewportFrame#LightDirection) | | Een [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  die de richting van de lichtbron vanuit positie (0, 0, 0)  vertegenwoordigt. Standaard is dit (-1, -1, -1) . |
| [LightColor](/docs/nl-nl/reference/engine/classes/ViewportFrame#LightColor) | | Kleur van het directionele licht. Standaard is dit [Color3.fromRGB(140, 140, 140)](/docs/nl-nl/reference/engine/datatypes/Color3#fromRGB)  (zilver). |

Daarnaast kun je het algehele weergegeven uiterlijk van de viewport aanpassen via de volgende eigenschappen:

| Eigenschap | | Beschrijving |
| [ImageColor3](/docs/nl-nl/reference/engine/classes/ViewportFrame#ImageColor3) | | Verandert de kleur/tint van de afbeelding zonder het weergegeven object te wijzigen. De standaard kleurwaarde is [Color3.new(1, 1, 1)](/docs/nl-nl/reference/engine/datatypes/Color3#new)  (wit) waarbij er geen kleurwijziging plaatsvindt. |
| [ImageTransparency](/docs/nl-nl/reference/engine/classes/ViewportFrame#ImageTransparency) | | Verandert de transparantie van de afbeelding zonder het weergegeven object te wijzigen. Een waarde van 0  (standaard) is volledig ondoorzichtig en een waarde van 1  is volledig transparant (onzichtbaar). |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
