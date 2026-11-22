<!-- Source: https://create.roblox.com/docs/nl-nl/performance-optimization/microprofiler/tag-table -->

Tagreferentie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization)
6. /
7. [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler)

# Tagreferentie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De volgende is een lijst van veelvoorkomende tags in de [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler) , gegroepeerd per categorie. Tags worden ook wel taken, timers, scopes, processen en labels genoemd. Wat de naam ook is, ze vertegenwoordigen een eenheid van werk.

Het begrijpen van deze tags kan je helpen om problematische code in je spel te identificeren. De tabellen bevatten taglabels, beschrijvingen en advies voor het verbeteren van de prestaties en het optimaliseren van je spel.

Voor een complete lijst van alle MicroProfiler-tags en hun beschrijvingen, zie de [LibMP-documentatie](https://github.com/Roblox/libmp/blob/main/docs/ALL-SCOPES%2Emd)  op GitHub.

## [Slaap](#slaap)[](#slaap)

Wanneer threads niet actief taken uitvoeren, komen ze in een slaaptoestand, met tags om aan te geven hoe lang de thread heeft geslapen. Op elk gegeven moment is het uiterst gebruikelijk dat de meeste werkthreads in een slaaptoestand verkeren.

## [Navigatie](#navigatie)[](#navigatie)

| Label | | Beschrijving | | Prestatieadvies |
| --- | --- |
| rasterizeTile | | Bijwerkt navigatietegels die nodig zijn voor een padvindverzoek, meestal gevolgd door computePath  dat vereist dat die tegels up-to-date zijn. Volgt NavigationJob/preprocess  op de hoofdthread. | | Verminder het aantal ongeldig verklaarde padvindtegels, aangezien dit ervoor zorgt dat die paden opnieuw moeten worden berekend. Dit wordt veroorzaakt door niet-navigabele delen die bewegen. |
| computePath | |

Berekent paden, meestal na rasterizeTile .

 | | Verminder het aantal en de wereldextensies van [Path:ComputeAsync()](/docs/nl-nl/reference/engine/classes/Path#ComputeAsync) -aanroepen. Probeer paden voor meerdere agenten te hergebruiken als ze naar ongeveer vergelijkbare locaties worden verwacht te starten/eindigen. |
| preprocess/getPrimitivesOverlapping | | Verzamelt de wereldgeometrie voor elke padvindtegel en plant de rasterisatietaken die door de padvindthread moeten worden uitgevoerd. | | Verminder het aantal onderdelen. |

## [Animatie en humanoïden](#animatie-en-humanoïden)[](#animatie-en-humanoïden)

| Label | | Beschrijving | | Prestatieadvies |
| Simulation/gameStepped | | Verwerking van spel-specifieke objecten zoals [Humanoids](/docs/nl-nl/reference/engine/classes/Humanoid) , [Animations](/docs/nl-nl/reference/engine/classes/Animation)  en hartslagcallbacks. | | Zie gameStepped  labels hieronder. |
| Simulation/gameStepped/stepHumanoid | | Veranderingen in de staat van [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  en beweging. | | Verminder het aantal [Humanoids](/docs/nl-nl/reference/engine/classes/Humanoid)  of schakel [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid) -toestanden uit op NPC's die ze niet nodig hebben, zoals [Climbing](/docs/nl-nl/reference/engine/enums/HumanoidStateType)  of [Swimming](/docs/nl-nl/reference/engine/enums/HumanoidStateType) . Verminder callbacks naar [Humanoid.StateChanged](/docs/nl-nl/reference/engine/classes/Humanoid#StateChanged)  of toestandsveranderingen zoals [Running](/docs/nl-nl/reference/engine/classes/Humanoid#Running)  of [Died](/docs/nl-nl/reference/engine/classes/Humanoid#Died) . |
| Simulation/gameStepped/stepAnimation | | [Animators](/docs/nl-nl/reference/engine/classes/Animator)  zullen vooruit stappen in momenteel afspelende animaties. | | Verminder het aantal [Animators](/docs/nl-nl/reference/engine/classes/Animator)  of geanimeerde gewrichten om de werklast van deze stap te verlagen. Verminder het aantal callbacks naar animatie-evenementen zoals [AnimationTrack.KeyframeReached](/docs/nl-nl/reference/engine/classes/AnimationTrack#KeyframeReached)  of [AnimationTrack.Ended](/docs/nl-nl/reference/engine/classes/AnimationTrack#Ended) . |
| Simulation/gameStepped/RunService.Stepped | | Voert functies uit die zijn verbonden met het [RunService.Stepped](/docs/nl-nl/reference/engine/classes/RunService#Stepped) -evenement. | | Verminder het aantal of de werklast van functies die aan dit evenement zijn verbonden. Overweeg om dure berekeningen uit te stellen of te vervangen of om berekeningen over meerdere frames te verspreiden. |

## [Audio](#audio)[](#audio)

| Label | | Beschrijving | | Prestatieadvies |
| Sound | | Verwerkt akoestische simulatie en werkt geluiden in actieve afspelen bij. | | Zie Sound  labels hieronder. |
| Sound/stepInstances | | Werkt het volume van actieve geluiden in de werkruimte bij. | | Verminder het aantal geluiden in actieve afspelen. |

## [Netwerken](#netwerken)[](#netwerken)

| Label | | Beschrijving | | Prestatieadvies |
| Net PacketReceive | | Ontvangt netwerkpakketten. Als veel objecten of evenementen worden gerepliceerd, duurt deze stap langer. | | Repliceer minder objecten of evenementen. |
| Replicator/ProcessPackets | | Verwerkt de inhoud van netwerkpakketten, zoals beweging, evenementaanroepen en eigenschapswijzigingen. | | Verminder het aantal of de grootte van objecten die worden gerepliceerd, of doe dit in incrementele stappen. Kan toenemen als de kaartgrootte toeneemt, omdat grotere kaarten doorgaans meer algehele activiteit hebben. |
| Allocate Bandwidth and Run Senders/Dispatch Physics Senders and TouchSenders | | Verzendt gegevens over activiteit in het spel. | | Verminder het aantal bewegende objecten en/of aanrakingen. Zie de volgende secties. |
| Allocate Bandwidth and Run Senders/Dispatch StreamJob | | Verzendt overeenkomstige specifieke gebieden naar specifieke clients in de streamingfunctie. | | Verminder de minimale en doel streamingstralen. |
| Allocate Bandwidth and Run Senders/Dispatch Data Senders | | Verzendt eigenschapswijzigingen, aanroepen van externe evenementen, veranderingen in de staat van [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid) , veranderingen in animatiestanden en replicatie van nieuwe instanties. | | Verminder het aantal gerepliceerde wijzigingen aan het datamodel. |
| Replicator SendCluster | | Verzendt [Terrain](/docs/nl-nl/parts/terrain)  gegevens naar clients. | | Verminder het aantal of de grootte van terreinwijzigingen. |
| ModelCompleteness Mega Job | | Server alleen: volledigheid is een intern concept. Wanneer modellen volledig zijn verzonden, worden modelvolledigheidsevents verzonden. | | Voeg minder instanties toe of verwijder ze. |
| deserializePacket | | Laag-niveau netwerkpakketverwerking. Bereidt voor op Replicator/ProcessPackets . | | Verzend minder of kleinere updates. |

## [Rendering](#rendering)[](#rendering)

| Label | | Beschrijving | | Prestatieadvies |
| Prepare | | Informatie wordt verzameld van de hoofdthread en werkt verschillende datastructuren bij die voor rendering worden gebruikt. | | Zie Prepare  labels hieronder. |
| Prepare/Pass3dAdorn | | Behandelt de rendering van verschillende objectversieringen, zoals tekstlabels boven objecten. Voor [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid) -labels met occlusie omvat deze stap raycasting om te bepalen of dergelijke objecten zichtbaar zijn. Dit omvat niet-transparante delen om debugvisualisaties te vergemakkelijken. | | Verminder het aantal zichtbare versierde objecten, zoals [BillboardGuis](/docs/nl-nl/reference/engine/classes/BillboardGui) , [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  naam/gezondheidslabels, enz. Verminder het aantal zichtbare delen. |
| Prepare/Pass2d | | Bereidt 2D UI-rendering voor (zowel speler- als Roblox UI). | | Verminder het aantal of de complexiteit van UI-elementen. |
| Prepare/UpdatePrepare/updateInvalidParts | | Werkt delen bij die een eigenschap hebben gewijzigd of toegevoegd. | | Verminder het aantal eigenschapswijzigingen in de wereld. Als een script een grote set objecteigenschappen bijwerkt, verdeel het dan over frames. |
| Prepare/UpdatePrepare/updateInvalidatedFastClusters | | Bereidt "FastCluster" geometrieën voor die worden gebruikt om [Humanoids](/docs/nl-nl/reference/engine/classes/Humanoid)  en [skinned](/docs/nl-nl/art/modeling/rigging)  [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart)  te renderen. Labels specificeren het aantal delen, vertices en de grootte van vertices. | | Verminder visuele wijzigingen aan modellen met [Humanoids](/docs/nl-nl/reference/engine/classes/Humanoid)  of skinned [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart) . |
| Prepare/UpdatePrepare/updateDynamicParts | | Bereidt [Beams](/docs/nl-nl/reference/engine/classes/Beam) , [ParticleEmitters](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  en [Humanoids](/docs/nl-nl/reference/engine/classes/Humanoid)  voor op rendering. | | Verminder het aantal zichtbare [Beams](/docs/nl-nl/reference/engine/classes/Beam) , [ParticleEmitters](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  en [Humanoids](/docs/nl-nl/reference/engine/classes/Humanoid) . |
| Prepare/UpdatePrepare/updateInstancedClusters | | Werkt geometrie bij die instanced rendering gebruikt, zoals delen. Labels Clusters  en Instances  geven het aantal bijwerkingen aan. | | Verminder werk dat impliciet de begrenzingsdoos van het deel bijwerkt, zoals [BasePart.CFrame](/docs/nl-nl/reference/engine/classes/BasePart#CFrame) , [BasePart.Size](/docs/nl-nl/reference/engine/classes/BasePart#Size)  of [Motor6D.Transform](/docs/nl-nl/reference/engine/classes/Motor6D#Transform) . Creatieve eigenschapsupdates zoals [Bone.Transform](/docs/nl-nl/reference/engine/classes/Bone#Transform)  kunnen helpen. |
| Perform | | Wanneer daadwerkelijke renderopdrachten worden aangemaakt en uitgegeven. | | Zie Perform  labels hieronder. |
| Perform/fillGuiVertices | | Vult buffers met UI-vertices ter voorbereiding op rendering. gui count  label geeft het aantal [LayerCollectors](/docs/nl-nl/reference/engine/classes/LayerCollector)  aan dat zichtbaar is in het frame. | | Als de kosten hoog zijn, verminder dan het aantal, de dichtheid en de ruimte die door UI-elementen wordt ingenomen. Als er te veel Process GuiEffect  labels zijn, overweeg dan om het gebruik van [UIGradient](/docs/nl-nl/reference/engine/classes/UIGradient)  en [UICorner](/docs/nl-nl/reference/engine/classes/UICorner)  op tekstlabels te verminderen. |
| Perform/Scene/queryFrustumOrdered | | Past frustum culling toe zodat niet-zichtbare objecten niet worden gerenderd. | | Als er hoge kosten zijn, betekent dit dat er veel elementen zijn. Misschien kun je grotere meshes gebruiken waar een enkele mesh meer details heeft in plaats van veel kleine individuele stukken. |
| Perform/Scene/computeLightingPerform | | Berekening van verlichting nabij de camera. | | Manipuleer het aantal lichtbronnen of beweeg de camera minder om de tijd die nodig is om verlichting opnieuw te berekenen te verminderen. |
| Perform/Scene/computeLightingPerform/LightGridCPU | | Werkt de voxelverlichting bij, die wordt gebruikt op lagere kwaliteitsniveaus. | | Als het bijwerken van chunkbezetting te lang duurt, overweeg dan om geometrie met een lagere resolutie te gebruiken, het aantal delen te verminderen of delen te verankeren. Als de andere labels te lang duren, overweeg dan om het aantal lichten te verminderen en niet-schaduw werpende geometrie te gebruiken voor objecten die bewegen en de bezetting ongeldig maken. |
| Perform/Scene/computeLightingPerform/ShadowMapSystem | | Werkt schaduwkaarten bij. Niet uitgevoerd op kwaliteitsniveaus onder 4. | | Verminder het aantal lichten. Je kunt ook [Light.Shadows](/docs/nl-nl/reference/engine/classes/Light#Shadows)  en [BasePart.CastShadow](/docs/nl-nl/reference/engine/classes/BasePart#CastShadow)  gebruiken om schaduwwerping op minder belangrijke instanties uit te schakelen. Zie [Verbeter prestaties](/docs/nl-nl/performance-optimization/improve#mitigatie-4) . |
| Perform/Scene/Glow, ColorCorrection, MSAA, SSAO, en SSAOApply | | Post-processing rendering. | | Verminder het aantal post-processing effecten. Gewoonlijk is dit niet significant. |
| Perform/Scene/UI | | UI-rendering. In Id_Screen  is er een label met het aantal batches, materialen en driehoeken die worden gebruikt. | | Verminder het aantal zichtbare UI-elementen. Het gebruik van [CanvasGroups](/docs/nl-nl/reference/engine/classes/CanvasGroup)  kan helpen ten koste van een verhoogd geheugengebruik. |
| Perform/Scene/UpdateView/updateParticles, updateParticleBoundings | | Update de positie en grenzen van de deeltjes. | | Verminder het aantal [ParticleEmitters](/docs/nl-nl/reference/engine/classes/ParticleEmitter) , emissiesnelheden, levensduur, enz. Beperk de beweging van emitters. |
| Scene/Id_Opaque, RenderView/Id_Opaque | | Delen in de scène met een algehele transparantie van 0.01  of lager. | | Verminder het gebruik en de dichtheid van delen. |
| Scene/Id_Transparent, RenderView/Id_Transparent | | Delen in de scène met een algehele transparantie tussen 0.01  en 1 . | | Verminder het gebruik van gedeeltelijke transparantie. |
| Scene/Id_Decals, RenderView/Id_Decals | | Decals in de scène. | | Verminder het gebruik van decals op complexe meshes. |
| Scene/Shadows | | Herberekening van schaduwen in de scène, meestal uitgevoerd op dynamische scènes en typische gameplay. Delen, ongeacht de transparantie, werpen schaduwen onder de veronderstelling dat ze decals bevatten. Niet uitgevoerd op kwaliteitsniveaus onder 4. | | Als deze stap te lang duurt, overweeg dan om [BasePart.CastShadow](/docs/nl-nl/reference/engine/classes/BasePart#CastShadow)  uit te schakelen voor complexe meshes, delen met hoge gedeeltelijke transparantie en minder belangrijke instanties. Volledig transparante delen die geen decals hebben of geen decal-schaduwen nodig hebben, moeten [BasePart.CastShadow](/docs/nl-nl/reference/engine/classes/BasePart#CastShadow)  uitgeschakeld hebben. Zie [Verbeter prestaties](/docs/nl-nl/performance-optimization/improve#mitigatie-4) . |
| Perform/Present | | Verzendt naar de GPU-thread om renderopdrachten uit te voeren. | | Verminder de complexiteit van de scène in het algemeen. Als deze stap lang duurt, ben je mogelijk beperkt door de GPU. |
| Perform/Present/waitUntilCompleted | | Wacht tot de GPU klaar is met het renderen van het vorige frame. | | Als dit over het algemeen vaak gebeurt, is het aantal gerenderde dingen te hoog. De Frame Rate Manager helpt bij het balanceren hiervan, maar als het hoog blijft, probeer dan de prestatieadviezen van de individuele Scene -tags op te volgen. |
| LoadImage | | Verwerkt afbeeldingen in een formaat dat de engine kan gebruiken. | | Verminder het gebruik van grote afbeeldingen. |

## [Scripts](#scripts)[](#scripts)

| Label | | Beschrijving | | Prestatieadvies |
| Render/PreRender/fireBindToRenderSteppedCallbacks | | Voert functies uit die zijn gebonden aan de renderstap via [RunService:BindToRenderStep()](/docs/nl-nl/reference/engine/classes/RunService#BindToRenderStep) . | | Zorg ervoor dat functies die aan dit evenement zijn verbonden zo min mogelijk werk doen. |
| Render/PreRender/RunService.RenderStepped | | Voert functies uit die zijn verbonden aan het [RunService.RenderStepped](/docs/nl-nl/reference/engine/classes/RunService#RenderStepped) -evenement. | | Zorg ervoor dat functies die aan dit evenement zijn verbonden zo min mogelijk werk doen. |
| WaitingHybridScriptJob | | Herstart scripts die wachten met [Instance:WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild)  of Globals.Roblox.wait() . Gewoonlijk 30 keer per seconde uitgevoerd. Deze stap heeft een uitvoeringstijdbudget om wachtende scripts uit te voeren. | | Als je te veel wachtende scripts of scripts met een lange runtime hebt voordat ze yielden, wordt deze stap beperkt en wacht langer voordat hij opnieuw kan worden uitgevoerd. Verminder het aantal gebonden functies of lange berekeningen in deze stap. |
| GC | | Luau's garbage collection-cyclus. | | Pool tabellen en andere verzamelbare objecten of probeer het creëren van tijdelijke tabellen te verminderen. |
| Heartbeat/RunService.Heartbeat | | Voert functies uit die zijn verbonden aan het [RunService.Heartbeat](/docs/nl-nl/reference/engine/classes/RunService#Heartbeat) -evenement. | | Verminder het aantal of de werklast van functies die aan dit evenement zijn verbonden. Overweeg om dure berekeningen uit te stellen of te vervangen of om berekeningen over meerdere frames te verspreiden. |

## [Simulatie](#simulatie)[](#simulatie)

| Label | | Beschrijving | | Prestatieadvies |
| Distributed Physics Ownership | | Bepaalt of de server of een client autoriteit heeft over bepaalde instanties zoals delen. | | Verminder het aantal delen dat vaak van netwerkbezit wisselt, vooral die met veel interactie. |
| Simulation/assemble | | Werkt een boom van verbonden objecten (assemblages) bij die door de fysica-engine worden gebruikt. | | Verminder het aantal gewrichten dat wordt gemaakt of vernietigd. |
| Simulation/physicsSteppedTotal/physicsStepped | | Voert de fysica-simulatie uit. | | Verminder het aantal en de complexiteit van fysiek gesimuleerde lichamen. |
| Simulation/physicsSteppedTotal/physicsStepped/SpatialFilter/filterStep | | Werkt simulatie-eilanden bij, rangschikt delen volgens netwerkbezit, lokale simulatie. Eilanden zijn niet-interagerende groepen van delen die onafhankelijk kunnen worden gesimuleerd. | | Vermijd het vaak instellen van netwerkbezit. Houd groepen delen ver genoeg van elkaar zodat ze afzonderlijk kunnen worden gesimuleerd. |
| Simulation/physicsSteppedTotal/physicsStepped/worldStep/stepContacts | | Werkt contacten tussen objecten bij. | | Verminder het aantal lichamen dat tegelijkertijd botst, of gebruik eenvoudigere botsingsdozen. Vieren zijn beter dan complexe meshes. |
| Simulation/physicsSteppedTotal/physicsStepped/worldStep/stepWorld OF  stepWorldThrottled | | Lost fysica-vergelijkingen op die verband houden met connectoren, drijfvermogen en [Humanoids](/docs/nl-nl/reference/engine/classes/Humanoid) . Wanneer de engine overbelast is en niet in staat is om alles in realtime te simuleren, kunnen sommige stappen worden beperkt (stepWorldThrottled ) en worden alleen "realtime assemblages" zoals [Humanoids](/docs/nl-nl/reference/engine/classes/Humanoid)  gesimuleerd. | | Hangt af van waar de tijd naartoe gaat op basis van de volgende drie fasen: stepContacts : smalle fase botsingsdetectie geometrie tests. Solver stap : integreer tijd en los botsingen en andere beperkingen op updateBroadphase : werk posities van assemblages bij in het botsingsdetectiesysteem en vind mogelijk botsende smalle fase paren. |
| notifyMovingAssemblies | | Helpt bij het bijhouden hoe lang primitieve objecten hebben geslapen. | |  |
| Simulation/physicsSteppedTotal/physicsStepped/interpolateNetworkedAssemblies | | Interpoleert assemblages die niet door de huidige speler worden bestuurd. | | Stel de netwerkbezit van delen in op de huidige speler om dit te verminderen; hoewel dit meestal meer fysica-werk elders zal veroorzaken. |
| Simulation/handleFallenParts | | Verwijdert delen die onder [Workspace.FallenPartsDestroyHeight](/docs/nl-nl/reference/engine/classes/Workspace#FallenPartsDestroyHeight)  zijn gevallen. | | Verlaag de vernietigingshoogte of verminder het aantal delen dat naar de vernietigingshoogte valt. |
| Heartbeat/heartbeatInternal/workspaceOnHeartbeat/updateVisuallySleeping | | Tweede deel van notifyMovingAssemblies . | |  |
| Heartbeat/RunService.Heartbeat | | Voert functies uit die zijn verbonden aan het [RunService.Heartbeat](/docs/nl-nl/reference/engine/classes/RunService#Heartbeat) -evenement voor simulatie en scripts contacten. De huidige beschrijving is algemeen genoeg om niet fout te zijn. | | Verminder het aantal of de werklast van functies die zijn verbonden aan [RunService.Heartbeat](/docs/nl-nl/reference/engine/classes/RunService#Heartbeat) . |
| worldStep/stepContacts | | Helpt de fysica-simulatie om veel contacten tegelijk te verwerken. | | Verminder het aantal botsende objecten. |
| SolveBatch | | Helpt de fysica-simulatie om batches van objectbeweging op te lossen. | |  |

## [UI](#ui)[](#ui)

| Label | | Beschrijving | | Prestatieadvies |
| Render/PreRender/UpdateInput | | Werkt bij en activeert alle gebruikersinvoergebeurtenissen als de gebruiker invoer heeft uitgevoerd sinds het laatste frame. | | Probeer niet te veel werk direct te doen terwijl je de invoer krijgt. Overweeg om een minimale hoeveelheid verwerking voor de invoer te doen, en grotere berekeningen moeten worden uitgesteld naar een andere thread die later plaatsvindt. |
| Render/PreRender/TweenService | | Werkt objecten bij die worden getweend met [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  en roept voltooiingscallbacks aan, zoals die gebruikt worden bij [GuiObject:TweenSize()](/docs/nl-nl/reference/engine/classes/GuiObject#TweenSize)  of [GuiObject:TweenPosition()](/docs/nl-nl/reference/engine/classes/GuiObject#TweenPosition) . | | Verminder het aantal objecten dat wordt getweend met [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  en zorg ervoor dat callbacks zo min mogelijk werk doen. |
| Heartbeat/TweenService | | In de server draait [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  in [RunService.Heartbeat](/docs/nl-nl/reference/engine/classes/RunService#Heartbeat)  in plaats van [RunService.PreRender](/docs/nl-nl/reference/engine/classes/RunService#PreRender) . | | Verminder het aantal objecten dat wordt getweend met [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  en zorg ervoor dat callbacks zo min mogelijk werk doen. |
| Render/PreRender/UpdateUILayouts | | Werkt positie en grootte bij voor UI-elementen op alle ingeschakelde [LayerCollectors](/docs/nl-nl/reference/engine/classes/LayerCollector) . | | Zie UpdateUILayouts  labels hieronder. |
| Render/PreRender/UpdateUILayouts/Rebuild Z-order list | | Herbouwt de interne Z-volgorde lijst van UI-elementen (niet te verwarren met [GuiObject.ZIndex](/docs/nl-nl/reference/engine/classes/GuiObject#ZIndex) ) in een [LayerCollector](/docs/nl-nl/reference/engine/classes/LayerCollector)  bij de eerste render of wanneer een nieuw element wordt toegevoegd, verwijderd of wanneer de [GuiObject.ZIndex](/docs/nl-nl/reference/engine/classes/GuiObject#ZIndex)  is gewijzigd. | | Verminder het aantal UI-elementen in [LayerCollectors](/docs/nl-nl/reference/engine/classes/LayerCollector)  voor de eerste render en vermijd het vaak wijzigen van de ouder en [GuiObject.ZIndex](/docs/nl-nl/reference/engine/classes/GuiObject#ZIndex)  van UI-elementen binnenin. Hoe meer elementen een [LayerCollector](/docs/nl-nl/reference/engine/classes/LayerCollector)  heeft, hoe slechter de prestaties. |
| Render/PreRender/UpdateUILayouts/Layout | |

Werkt positie en grootte bij voor UI-elementen in een individuele [LayerCollector](/docs/nl-nl/reference/engine/classes/LayerCollector) . Kan een label bevatten met informatie over de relevante UI, samen met het aantal Relayouts, Updates en Resizes.

 | | Verminder het aantal UI-elementen dat wordt gewijzigd of verplaatst, zoals die beheerd door [UILayout](/docs/nl-nl/reference/engine/classes/UILayout)  en die getweend zijn met [TweenService](/docs/nl-nl/reference/engine/classes/TweenService) , [GuiObject:TweenSize()](/docs/nl-nl/reference/engine/classes/GuiObject#TweenSize) , of [GuiObject:TweenPosition()](/docs/nl-nl/reference/engine/classes/GuiObject#TweenPosition) . Overweeg om vaste maten te gebruiken voor [BillboardGuis](/docs/nl-nl/reference/engine/classes/BillboardGui) . |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
