<!-- Source: https://create.roblox.com/docs/nl-nl/workspace/camera -->

Pas de camera aan | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Camera](/docs/nl-nl/workspace/camera)

# Pas de camera aan

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De ingebouwde camera van Roblox ondersteunt een standaard derde persoon  modus en een optionele eerste persoon  modus, zodat je je eigen volgcamera niet hoeft te bouwen. Voor meer aangepaste scenario's kun je de standaard eigenschappen in [Camera](/docs/nl-nl/reference/engine/classes/Camera)  aanpassen of deze volledig vervangen, zoals voor over-de-schouder, isometrische en wapen-scoping weergaven.

## [Basisinstellingen](#basisinstellingen)[](#basisinstellingen)

Je kunt veelvoorkomende camera-instellingen direct binnen het [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer)  object in Studio configureren. Deze instellingen omvatten [zoomafstand](#zoomafstand)  en verschillende [camera](#cameramodus) , [occlusie](#occlusiemodus) , en [bewegings](#bewegingsmodus)  modi.

1.

Selecteer het StarterPlayer  object in het Explorer  venster.

 ![StarterPlayer in Explorer](https://prod.docsiteassets.roblox.com/assets/studio/explorer/StarterPlayer.png)

2.

Scroll in het Properties  venster naar beneden om de Camera  sectie te vinden. Je kunt de volgende eigenschappen direct of via een script configureren.

 ![Camera-eigenschappen op StarterPlayer in het Properties-venster](https://prod.docsiteassets.roblox.com/assets/studio/properties/StarterPlayer-Camera-Group.png)

### [Zoomafstand](#zoomafstand)[](#zoomafstand)

Samen bepalen [CameraMaxZoomDistance](/docs/nl-nl/reference/engine/classes/StarterPlayer#CameraMaxZoomDistance)  en [CameraMinZoomDistance](/docs/nl-nl/reference/engine/classes/StarterPlayer#CameraMinZoomDistance)  het bereik waarin spelers de camera kunnen in- en uitzoomen ten opzichte van hun speler karakter. Het instellen van een zeer hoge maximum zoals 500 stelt spelers in staat om de camera ver weg in de ruimte te zoomen. Als je de camera op een specifieke afstand van het karakter wilt vergrendelen en inzoomen wilt voorkomen, stel je beide eigenschappen in op dezelfde waarde.

LocalScript - Camera Zoom Bereik

```

local Players = game:GetService("Players")

local player = Players.LocalPlayer

player.CameraMaxZoomDistance = 25

player.CameraMinZoomDistance = 50

```

### [Cameramodus](#cameramodus)[](#cameramodus)

De [CameraMode](/docs/nl-nl/reference/engine/classes/StarterPlayer#CameraMode)  eigenschap stelt het algemene gedrag van de camera in tussen twee opties:

| Instelling | | Beschrijving |
| --- | --- |
| Classic | | De klassieke Roblox derde-persoon camera die kan worden ingezoomd naar eerste persoon. Hiermee kunnen spelers in- en uitzoomen (tenzij inzoomen is vergrendeld) en de camera rond hun karakter draaien. |
| LockFirstPerson | | Vergrendelt de camera in de eerste-persoon modus. Wanneer in deze modus zijn alle delen/elementen van het karakter van de speler onzichtbaar voor hen, behalve voor uitgeruste [Tools](/docs/nl-nl/reference/engine/classes/Tool) . |

### [Occlusiemodus](#occlusiemodus)[](#occlusiemodus)

De [DevCameraOcclusionMode](/docs/nl-nl/reference/engine/classes/StarterPlayer#DevCameraOcclusionMode)  eigenschap controleert het camera gedrag wanneer de speler hun karakter niet kan zien, zoals wanneer het wordt verborgen door een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) .

| Instelling | | Beschrijving |
| Zoom | | Als het karakter van de speler achter een object met [Transparency](/docs/nl-nl/reference/engine/classes/BasePart#Transparency)  lager dan 0.25 beweegt, zoomt de camera heel dicht in op het karakter zodat het kan worden gezien. Zodra het karakter weer in een zichtbare positie beweegt, zoomt de camera weer uit. |
| Invisicam | | Als het karakter van de speler achter een object met [Transparency](/docs/nl-nl/reference/engine/classes/BasePart#Transparency)  lager dan 0.75 beweegt, blijft de camera onveranderd maar wordt het object semi-transparant zodat het karakter kan worden gezien. Zodra het karakter weer in een zichtbare positie beweegt, keert het object terug naar zijn normale opaciteit. |

Zoom  en Invisicam  occlusiemodi

### [Bewegingsmodus](#bewegingsmodus)[](#bewegingsmodus)

De [DevComputerCameraMovementMode](/docs/nl-nl/reference/engine/classes/StarterPlayer#DevComputerCameraMovementMode)  (computer) en [DevTouchCameraMovementMode](/docs/nl-nl/reference/engine/classes/StarterPlayer#DevTouchCameraMovementMode)  (telefoon/tablet) bepalen hoe de speler de camera kan verplaatsen.

| Instelling | | Beschrijving |
| UserChoice | | De camera beweegt op basis van de camera-instellingen van de speler in het spel. |
| Classic | | De camera blijft op zijn [zoomafstand](#zoomafstand) , en volgt het karakter van de speler terwijl het zich door de wereld beweegt. Spelers kunnen ook de camerastandpunt omhoog/omlaag kantelen en het rond hun karakter draaien. |
| Follow | | Vergelijkbaar met Classic , maar de camera kan iets draaien om het karakter van de speler te volgen als ze zich in een richting bewegen die niet parallel is aan de kijkrichting van de camera. |
| Orbital | | De camera blijft op een vaste zoomafstand en volgt het karakter van de speler terwijl het zich door de wereld beweegt. Spelers kunnen de camera rond hun karakter draaien, maar kunnen het zicht niet omhoog of omlaag kantelen. |
| CameraToggle | | Alleen functioneel op computers (niet op telefoons/tablets) via [DevComputerCameraMovementMode](/docs/nl-nl/reference/engine/classes/StarterPlayer#DevComputerCameraMovementMode) . Wanneer de speler met de rechtermuisknop klikt, schakelt de camera tussen de Classic  modus en een "vrije kijk" modus waarin het bewegen van de muis om zich heen kijkt in de wereld. |

## [Script de camera](#script-de-camera)[](#script-de-camera)

Elke speler [client](/docs/nl-nl/projects/client-server)  heeft zijn eigen [Camera](/docs/nl-nl/reference/engine/classes/Camera)  object dat zich in de lokale [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  bevindt, toegankelijk via de [Workspace.CurrentCamera](/docs/nl-nl/reference/engine/classes/Workspace#CurrentCamera)  eigenschap. Je kunt de standaard camera scripts van Roblox overschrijven door de [CameraType](/docs/nl-nl/reference/engine/classes/Camera#CameraType)  in te stellen op [Scriptable](/docs/nl-nl/reference/engine/enums/CameraType)  en vervolgens, het meest gebruikelijk, de camera te besturen via de volgende eigenschappen.

| Eigenschap | | Beschrijving |
| [Camera.CFrame](/docs/nl-nl/reference/engine/classes/Camera#CFrame) | | De [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  van de camera. Dit is de meest gebruikte eigenschap voor het positioneren en oriënteren van een [Scriptable](/docs/nl-nl/reference/engine/enums/CameraType)  camera in een spel. |
| [Camera.FieldOfView](/docs/nl-nl/reference/engine/classes/Camera#FieldOfView) | | De omvang van de observeerbare 3D ruimte die op het scherm kan worden gezien, gemeten tussen 1–120 graden in de richting gedefinieerd door [Camera.FieldOfViewMode](/docs/nl-nl/reference/engine/classes/Camera#FieldOfViewMode) . Standaard is 70. |
| [Camera.CameraType](/docs/nl-nl/reference/engine/classes/Camera#CameraType) | | Schakelt tussen de verschillende camera gedragingen zoals beschreven in [Enum.CameraType](/docs/nl-nl/reference/engine/enums/CameraType) , waarvan sommige de selecteerbare [bewegingsmodi](#bewegingsmodus)  nabootsen. Dit instellen op [Scriptable](/docs/nl-nl/reference/engine/enums/CameraType)  geeft je volledige controle over de camera. |
| [Camera.Focus](/docs/nl-nl/reference/engine/classes/Camera#Focus) | | Het punt in 3D ruimte waar de camera naar kijkt. Als je [Camera.CameraType](/docs/nl-nl/reference/engine/classes/Camera#CameraType)  hebt ingesteld op [Scriptable](/docs/nl-nl/reference/engine/enums/CameraType) , moet je deze eigenschap elke frame bijwerken omdat bepaalde visuals gedetailleerder zijn afhankelijk van hoe dicht ze bij het focuspunt zijn. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
