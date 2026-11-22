<!-- Source: https://create.roblox.com/docs/nl-nl/environment/skybox -->

Luchtdozen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelomgeving](/docs/nl-nl/environment)

# Luchtdozen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een luchtdoos  is een kubus die is samengesteld uit zes afzonderlijke afbeeldingen die een meeslepende luchtachtergrond in een spel creëren. Wanneer de afbeeldingen zijn ontworpen om perfect op elkaar aan te sluiten, lijkt de luchtdoos panoramisch zonder de indruk te wekken dat je binnen een kubus bent. Dit zorgt ervoor dat spellen groter aanvoelen dan ze werkelijk zijn, en het voegt diepte toe aan je sfeer, zoals het simuleren van de diepe ruimte of onderwateromgevingen.

Bovendien bevat het [Sky](/docs/nl-nl/reference/engine/classes/Sky)  object hemellichamen zoals een zon, maan en sterren die dynamisch verschijnen, opkomen en ondergaan op basis van de [TimeOfDay](/docs/nl-nl/reference/engine/classes/Lighting#TimeOfDay)  of [ClockTime](/docs/nl-nl/reference/engine/classes/Lighting#ClockTime) .

Ten slotte kan het [Sky](/docs/nl-nl/reference/engine/classes/Sky)  object worden gebruikt als een cubemap voor reflecties in [ViewportFrames](/docs/nl-nl/reference/engine/classes/ViewportFrame) . Voor details, zie [viewport frames](/docs/nl-nl/ui/viewport-frames) .

## [Constructie van luchtdozen](#constructie-van-luchtdozen)[](#constructie-van-luchtdozen)

Als je je eigen luchtdoosafbeeldingen hebt gemaakt, moet je ze eerst [importeren](/docs/nl-nl/projects/assets/manager#asset-import)  naar Roblox voordat je ze in een luchtdoos kunt gebruiken. Elke afbeelding moet naadloos zijn langs alle randen  van aangrenzende afbeeldingen wanneer ze "gevouwen" worden in een kubus.

Afbeelding Gezichts Luchtdoos "Gevoerd"

![](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/skybox/Skybox-Unfolded.png)

Om een luchtdoos te maken:

1.

In het Explorer  venster, voeg een [Sky](/docs/nl-nl/reference/engine/classes/Sky)  object toe aan de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Lighting-Sky.png)

2.

Selecteer het nieuwe [Sky](/docs/nl-nl/reference/engine/classes/Sky)  object, en wijs in het Properties  venster een textuur toe aan elk van de volgende lucht eigenschappen:

-

SkyboxBk  — Het achter  vierkant van de luchtdoos.

-

SkyboxDn  — Het onder  vierkant van de luchtdoos.

-

SkyboxFt  — Het voor  vierkant van de luchtdoos.

-

SkyboxLf  — Het linker  vierkant van de luchtdoos.

-

SkyboxRt  — Het rechter  vierkant van de luchtdoos.

-

SkyboxUp  — Het boven  vierkant van de luchtdoos.

 ![](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/skybox/Skybox-Property-Faces.png)

## [Hemellichamen](#hemellichamen)[](#hemellichamen)

Standaard bevat het [Sky](/docs/nl-nl/reference/engine/classes/Sky)  object hemellichamen zoals een zon, maan en sterren. Deze lichamen verschijnen dynamisch, komen op en gaan onder op basis van de [TimeOfDay](/docs/nl-nl/reference/engine/classes/Lighting#TimeOfDay)  of [ClockTime](/docs/nl-nl/reference/engine/classes/Lighting#ClockTime)  eigenschapswaarden.

Je kunt hemellichamen aanpassen via de volgende eigenschappen:

-

[SunTextureId](/docs/nl-nl/reference/engine/classes/Sky#SunTextureId)  — Stelt de textuur van de zon in.

-

[SunAngularSize](/docs/nl-nl/reference/engine/classes/Sky#SunAngularSize)  — Stelt de relatieve grootte van de zon in graden in.

-

[MoonTextureId](/docs/nl-nl/reference/engine/classes/Sky#MoonTextureId)  — Stelt de textuur van de maan in.

-

[MoonAngularSize](/docs/nl-nl/reference/engine/classes/Sky#MoonAngularSize)  — Stelt de relatieve grootte van de maan in graden in.

-

[StarCount](/docs/nl-nl/reference/engine/classes/Sky#StarCount)  — Stelt het aantal sterren in de luchtdoos in.

Om alle hemellichamen uit te schakelen, kun je de eigenschap [CelestialBodiesShown](/docs/nl-nl/reference/engine/classes/Sky#CelestialBodiesShown)  uitschakelen. Alternatief kun je alleen de zon en/of maan uitschakelen (terwijl je de sterren behoudt) door [SunAngularSize](/docs/nl-nl/reference/engine/classes/Sky#SunAngularSize)  of [MoonAngularSize](/docs/nl-nl/reference/engine/classes/Sky#MoonAngularSize)  op 0  te zetten.

## [Oriëntatie](#oriëntatie)[](#oriëntatie)

De eigenschap [SkyboxOrientation](/docs/nl-nl/reference/engine/classes/Sky#SkyboxOrientation)  verandert de oriëntatie van de luchtdoosoppervlakken. De eigenschap neemt een [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  van graadwaarden in de typische XYZ  volgorde, maar rotatie wordt toegepast  eerst rond de Y  as, dan X , en dan Z  om voorspelbare controle over complexe bewegingen mogelijk te maken.

Een gemakkelijke manier om een oriëntatie-animatie te script is om rond de Y  as te draaien (terwijl de horizon op niveau blijft), en deze as te kantelen door X  en Z  op een vaste waarde in te stellen. Het volgende script, bijvoorbeeld, animeert de Y  as voor draaien terwijl het een consistente kanteling van 30° op de X  as behoudt.

```

local Lighting = game:GetService("Lighting")

local RunService = game:GetService("RunService")

local sky = Lighting:FindFirstChild("Sky")

local ROTATION_SPEED = 5  -- In graden per seconde

RunService.Heartbeat:Connect(function(deltaTime)

	sky.SkyboxOrientation = Vector3.new(

		30,

		(sky.SkyboxOrientation.Y + ROTATION_SPEED * deltaTime) % 360,

		0

	)

end)

```

De modulo-operatie %  is optioneel maar aanbevolen. Je kunt waarden boven 360  of onder 0  gebruiken, maar het gebruik van kleinere getallen voorkomt problemen wanneer de animatie gedurende een zeer lange tijd draait (vanwege beperkte precisie).

Let op dat de oriëntatie van de luchtdoos een kosteneffectieve functie is die naadloos werkt op alle platforms en visuele kwaliteitsniveaus. Als gevolg hiervan zijn er enkele opzettelijke uitzonderingen:

-

Als de lucht zichtbaar is in binnenreflecties zoals een spiegeloppervlak door een open raam, zal dat specifieke gereflecteerde uitzicht niet worden gedraaid. Dit zou dure her-rendering en convolutie van cubemaps vereisen, wat de prestaties en brede beschikbaarheid aanzienlijk zou beïnvloeden.

-

Alleen de luchtdoosoppervlakken draaien; [hemellichamen](#hemellichamen)  worden niet beïnvloed door deze eigenschap.

-

Als je een [Sky](/docs/nl-nl/reference/engine/classes/Sky)  binnen een [ViewportFrame](/docs/nl-nl/reference/engine/classes/ViewportFrame)  gebruikt, zal het de globale [SkyboxOrientation](/docs/nl-nl/reference/engine/classes/Sky#SkyboxOrientation)  waarden reflecteren. Je kunt de hoek per [ViewportFrame](/docs/nl-nl/reference/engine/classes/ViewportFrame)  niet aanpassen.

-

De [dynamische wolken](/docs/nl-nl/environment/clouds)  functie onder [Terrain](/docs/nl-nl/reference/engine/classes/Terrain)  wordt niet beïnvloed.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
