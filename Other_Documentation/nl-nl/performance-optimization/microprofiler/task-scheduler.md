<!-- Source: https://create.roblox.com/docs/nl-nl/performance-optimization/microprofiler/task-scheduler -->

Taakplanner | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization)
6. /
7. [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler)

# Taakplanner

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De taakplanner  coördineert taken die in elk frame worden uitgevoerd terwijl het spel draait, zelfs wanneer het is gepauzeerd. Deze taken omvatten het detecteren van spelersinvoer, het animeren van personages, het bijwerken van de fysica-simulatie en het hervatten van scripts in een [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait) -toestand.

Hoewel er meerdere taken tegelijk kunnen worden uitgevoerd, kan de taakplanner mogelijk overbelast raken, vooral in de volgende situaties:

-

Het gebruik van een aangepaste karakterrig of invoerschema.

-

Het zelf animeren van onderdelen (in plaats van een [Animator](/docs/nl-nl/reference/engine/classes/Animator)  te gebruiken).

-

Sterk afhankelijk zijn van nauwkeurige fysica.

-

Regelmatig objecten repliceren.

## [RunService](#runservice)[](#runservice)

De meest directe manier om frame-voor-frame taken toe te voegen, is via de volgende leden van [RunService](/docs/nl-nl/reference/engine/classes/RunService) :

-

[RunService.PreAnimation](/docs/nl-nl/reference/engine/classes/RunService#PreAnimation)

-

[RunService.PreSimulation](/docs/nl-nl/reference/engine/classes/RunService#PreSimulation)

-

[RunService.PostSimulation](/docs/nl-nl/reference/engine/classes/RunService#PostSimulation)

-

[RunService.Heartbeat](/docs/nl-nl/reference/engine/classes/RunService#Heartbeat)

-

[RunService:BindToRenderStep()](/docs/nl-nl/reference/engine/classes/RunService#BindToRenderStep)

-

[RunService.PreRender](/docs/nl-nl/reference/engine/classes/RunService#PreRender)

## [Plannerprioriteit](#plannerprioriteit)[](#plannerprioriteit)

De taakplanner categoriseert en voltooit taken in de volgende volgorde. Sommige taken voeren mogelijk geen werk uit in een frame, terwijl andere meerdere keren kunnen worden uitgevoerd.

 ![](https://prod.docsiteassets.roblox.com/assets/optimization/task-scheduler/task-scheduler.svg)

* Scriptuitvoering tijdens [RunService.Heartbeat](/docs/nl-nl/reference/engine/classes/RunService#Heartbeat)  verschilt afhankelijk van de instelling van [Workspace.SignalBehavior](/docs/nl-nl/reference/engine/classes/Workspace#SignalBehavior)  in jouw spel. Zie [Uitgestelde evenementen](/docs/nl-nl/scripting/events/deferred) .

## [Beste praktijken](#beste-praktijken)[](#beste-praktijken)

Om prestatiegerichte spellen met efficiëntie in gedachten te bouwen, let op het volgende:

-

Verbind/bind geen functies aan de renderstap, tenzij absoluut noodzakelijk.  Alleen taken die moeten worden uitgevoerd na invoer maar vóór rendering, zoals camerabeweging, moeten op deze manier worden uitgevoerd. Voor strikte controle over de volgorde, gebruik [BindToRenderStep()](/docs/nl-nl/reference/engine/classes/RunService#BindToRenderStep)  in plaats van [PreRender](/docs/nl-nl/reference/engine/classes/RunService#PreRender) .

-

Beheer fysieke toestanden zorgvuldig.  [PreSimulation](/docs/nl-nl/reference/engine/classes/RunService#PreSimulation)  gebeurt voor  de fysica, terwijl [PostSimulation](/docs/nl-nl/reference/engine/classes/RunService#PostSimulation)  gebeurt na  de fysica. Daarom moet gameplay-logica die de fysica-toestand beïnvloedt, worden uitgevoerd in [PreSimulation](/docs/nl-nl/reference/engine/classes/RunService#PreSimulation) , zoals het instellen van de [Velocity](/docs/nl-nl/reference/engine/classes/BasePart#Velocity)  van onderdelen. In tegenstelling hiermee moet gameplay-logica die afhankelijk is van of reageert op de fysica-toestand, worden afgehandeld in [PostSimulation](/docs/nl-nl/reference/engine/classes/RunService#PostSimulation) , zoals het lezen van de [Position](/docs/nl-nl/reference/engine/classes/BasePart#Position)  van onderdelen om te detecteren wanneer ze gedefinieerde zones binnenkomen.

-

Motor6D-transformatiewijzigingen moeten worden gedaan tijdens het PreSimulation-evenement.  Als je dat niet doet, zullen [Animators](/docs/nl-nl/reference/engine/classes/Animator)  wijzigingen overschrijven in het volgende frame. Zelfs zonder een [Animator](/docs/nl-nl/reference/engine/classes/Animator)  is [PreSimulation](/docs/nl-nl/reference/engine/classes/RunService#PreSimulation)  het laatste Luau-evenement dat wordt geactiveerd voordat [Motor6D.Transform](/docs/nl-nl/reference/engine/classes/Motor6D#Transform)  wordt toegepast op de posities van onderdelen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
