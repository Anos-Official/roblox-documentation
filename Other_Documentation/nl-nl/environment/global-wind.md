<!-- Source: https://create.roblox.com/docs/nl-nl/environment/global-wind -->

Globale wind | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelomgeving](/docs/nl-nl/environment)

# Globale wind

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [GlobalWind](/docs/nl-nl/reference/engine/classes/Workspace#GlobalWind)  vector stelt de richting en sterkte in waarin de wind door een spel waait, wat invloed heeft op [terrein gras](/docs/nl-nl/parts/terrain#grasanimatie)  en [dynamische wolken](/docs/nl-nl/environment/clouds) . Je kunt het instellen als een [constante vector](#globale-windvector) , of het aanpassen via [scripting](#gescripte-effecten)  om cyclische windstoten te creëren. Daarnaast kun je [deeltjes](#deeltjesinvloed)  beïnvloeden om de globale windvector te volgen.

## [Globale windvector](#globale-windvector)[](#globale-windvector)

De globale wind wordt gecontroleerd via De [GlobalWind](/docs/nl-nl/reference/engine/classes/Workspace#GlobalWind)  vector is een eigenschap van [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  en je kunt deze direct in Studio bewerken, of instellen via [scripting](#gescripte-effecten) .

Om de globale windvector in Studio in te stellen:

1.

Selecteer in het Explorer  venster de bovenste [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  service.

 ![Workspace-object weergegeven in het Explorer-venster van Studio](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Workspace.png)

2.

Zoek in het Properties  venster de [GlobalWind](/docs/nl-nl/reference/engine/classes/Workspace#GlobalWind)  eigenschap en stel een X , Y  en Z  waarde in voor de richting en sterkte.

 ![GlobalWind-eigenschap weergegeven in het Properties-venster van Studio](https://prod.docsiteassets.roblox.com/assets/studio/properties/Workspace-GlobalWind.png)

Houd er rekening mee dat de snelheid van [geanimeerd gras](/docs/nl-nl/parts/terrain#grasanimatie)  — maar niet de vectorrichting — zal worden verminderd als de speler de Verminder Beweging  [toegankelijkheid](/docs/nl-nl/production/publishing/accessibility#verminderde-beweging)  instelling heeft ingeschakeld vanuit het Roblox of in-game Instellingen  menu.

## [Deeltjesinvloed](#deeltjesinvloed)[](#deeltjesinvloed)

Deeltjes die door een [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  worden uitgezonden, volgen de globale windvector zolang de [WindAffectsDrag](/docs/nl-nl/reference/engine/classes/ParticleEmitter#WindAffectsDrag)  eigenschap van de emitter is ingeschakeld en de [Drag](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Drag)  eigenschap groter is dan 0 , wat nuttig is voor [het simuleren van regen](/docs/nl-nl/effects/particle-emitters#simuleer-regen) . [Fire](/docs/nl-nl/reference/engine/classes/Fire)  en [Smoke](/docs/nl-nl/reference/engine/classes/Smoke)  instanties volgen standaard de windvector.

 ![Drag en WindAffectsDrag-eigenschappen weergegeven in het Properties-venster van Studio](https://prod.docsiteassets.roblox.com/assets/studio/properties/ParticleEmitter-WindAffectsDrag.png)

## [Windrichting widget](#windrichting-widget)[](#windrichting-widget)

Om het gemakkelijker te maken om de globale wind af te stemmen, kun je de Windrichting  widget gebruiken, toegankelijk vanuit het View  menu van Studio. De widget laat je visualiseren hoe de wind waait met behulp van een windzakmodel, en je kunt dynamisch de Snelheid , Yaw  en Pitch  van de wind instellen door op de gewenste aspectnaam te klikken en de schuifregelaar onderaan te verschuiven, of je kunt yaw of pitch aanpassen door de groene ring en blauwe pijl op het geanimeerde gedeelte te manipuleren. Je kunt ook op de widget klikken en deze slepen om deze ergens in de 3D-weergave opnieuw te positioneren.

 ![Windrichting widget weergegeven in de 3D-weergave van Studio](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/aero-fluid-dynamics/Wind-Direction-Widget.jpg)

## [Gescripte effecten](#gescripte-effecten)[](#gescripte-effecten)

Scripting van de [GlobalWind](/docs/nl-nl/reference/engine/classes/Workspace#GlobalWind)  eigenschap opent een hele reeks mogelijkheden. Je kunt bijvoorbeeld de volgende codevoorbeeld gebruiken om cyclische windstoten te veroorzaken die in- en uitfaden met behulp van de [math.sin()](/docs/nl-nl/reference/engine/libraries/math#sin)  functie.

Script - Cyclische Windstoten

```

local gustCycleDelay = 5  -- Max duur tussen windcycli in seconden

local gustCycleDuration = 3.5  -- Duur van elke windcyclus in seconden

-- Tijdens elke windcyclus zal een deel van "gust" aan "baseWind" worden toegevoegd op een geleidelijke manier

local baseWind = Vector3.new(5, 0, 2)  -- Basis windsnelheid en richting

local gust = Vector3.new(25, 0, 10)  -- Windstoot snelheid en richting

local gustIntervals = 100  -- Aantal iteraties gebruikt om elke windinterval te berekenen

local dg = gustCycleDuration / gustIntervals

local dgf = dg / gustCycleDuration

-- Stel de globale wind in op de basiswind in eerste instantie

workspace.GlobalWind = baseWind

-- Wacht vertraging voordat de windstoten beginnen

task.wait(gustCycleDelay)

while true do

	for i = 1, gustIntervals do

		local f = math.sin(math.pi * dgf * i)  -- Gebruik sin() functie om windstoot te geleiden

		workspace.GlobalWind = baseWind + f * gust  -- Stel de globale wind in op basiswind + windstoot

		task.wait(dg)

	end

	workspace.GlobalWind = baseWind  -- Reset de globale wind naar basiswind aan het einde van de windcyclus

	task.wait(math.random() * gustCycleDelay)  -- Wacht een willekeurige fractie van de vertraging voordat de volgende windcyclus begint

end

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
