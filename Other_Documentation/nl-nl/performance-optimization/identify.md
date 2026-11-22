<!-- Source: https://create.roblox.com/docs/nl-nl/performance-optimization/identify -->

Identificeer prestatieproblemen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization)

# Identificeer prestatieproblemen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het identificeren van prestatieproblemen betekent over het algemeen dat je je richt op een van de drie categorieën: frame rate (berekeningen), geheugen of laadtijd.

Roblox heeft een aantal tools voor het identificeren van prestatieproblemen, waarvan sommige beschikbaar zijn in de Roblox-client (en dus ook in Studio) en sommige alleen in Studio beschikbaar zijn. Terwijl je het gedrag van de client direct kunt observeren, moet je tools gebruiken om serverproblemen te diagnosticeren.

## [Diagnosetools](#diagnosetools)[](#diagnosetools)

| Tool | | Beschrijving | | Locatie | | Sneltoets | | Omgeving |
| --- | --- |
| [Ontwikkelaarsconsole](/docs/nl-nl/studio/developer-console) | | Een console met realtime logberichten, fouten en gedetailleerde informatie over geheugen, netwerken en scriptprestaties. Het is nuttig voor het bekijken van geheugengebruik, belangrijke servergezondheidsstatistieken, scriptprestaties en om de client of server MicroProfiler te starten. | |

Studio

In-Game

 | | F9 | |

Studio Testing

Live Sessions

 |
| [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler) | | Een debugtool die in kaart brengt hoeveel rekentijd aan taken per frame wordt besteed. Het kan dumps genereren voor analyse die een nauwkeurige uitsplitsing van individuele frames tonen, waardoor het nuttig is voor het identificeren van de specifieke taak die prestatieproblemen veroorzaakt. Je kunt de profiler op de client of de server uitvoeren, afhankelijk van welke kant een probleem heeft. | |

Studio

In-Game

 | | Ctrl Alt F6  (⌘ ⌥ F6 ) | |

Studio Testing

Live Sessions

 |
| [Scene-analyse](/docs/nl-nl/performance-optimization/scene-analysis) | | Biedt op een glimp vergelijkende informatie over de middelen die je client en server scènes gebruiken en welke instanties verantwoordelijk zijn voor dat middelengebruik. | | Studio | | N/A | |

Studio Testing

 |
| Prestatiestatistieken | | Een werkbalk met basis prestatiestatistieken, waaronder geheugengebruik, CPU, GPU, verzonden en ontvangen netwerkgegevens, en pingtijd. | |

In-Game

 | | Ctrl Alt F7  (⌘ ⌥ F7 ) | |

Studio Testing

Live Sessions

 |
| Debug-statistieken | | Overlay met gedetailleerde informatie over graphics, fysica, netwerkverkeer en FPS. | |

Studio

In-Game

 | | Shift Ctrl F1  (Shift ⌘ F1 ), Shift Ctrl F2  (Shift ⌘ F2 ), Shift Ctrl F3  (Shift ⌘ F3 ), Shift Ctrl F4  (Shift ⌘ F4 ), Shift Ctrl F5  (Shift ⌘ F5 ) | |

Studio Testing

Live Sessions

 |
| [Netwerksimulatie](/docs/nl-nl/studio/testing-modes#netwerksimulatie) | | Eigenschappen die echte netwerkcondities simuleren, zoals latentie, jitter en pakketverlies om verbindingen te testen. | |

Studio

 | | Alt S (⌥ S ) | |

Studio Testing

 |
| [Prestatie-dashboard](/docs/nl-nl/production/analytics/performance) | | Een dashboard met aggregaatgrafieken voor client- en servergeheugengebruik, client frame rate, server hartslag en crashpercentages in realtime. Het is nuttig voor het analyseren van prestatiepatronen in de loop van de tijd. Zie [prestatie monitoren](/docs/nl-nl/performance-optimization/monitor) . | |

Creator Dashboard

 | | N/A | |

Live Sessions

 |

## [Serverberekeningen](#serverberekeningen)[](#serverberekeningen)

De serverhartslag is beperkt tot 60 FPS voor alle games, dus lagere waarden kunnen wijzen op een prestatieprobleem. Om de serverhartslag te controleren:

-

Met de [Ontwikkelaarsconsole](/docs/nl-nl/studio/developer-console)  - Ga naar het tabblad Server Jobs , vouw de rij Heartbeat  uit en controleer de waarde Steps Per Sec , die de hartslag van je game vertegenwoordigt.

-

Met de [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler)  kun je de grafiek controleren om te zien of het frame langer dan 16,67 ms duurt.

De MicroProfiler is bijzonder nuttig voor het identificeren van "spikes" in prestaties, waarbij sommige frames aanzienlijk langer duren om te verwerken dan andere.

Een ander symptoom van een verlaagde serverhartslag is verhoogde latentie (vaak ping genoemd). Hoe langer de server nodig heeft om zijn taken per frame te voltooien, hoe langer het duurt om netwerkgegevens die van clients zijn verzonden en ontvangen te verwerken. Om de gemiddelde ping voor alle spelers die verbonden zijn met een server te controleren, ga je naar het tabblad Server Stats  in de [Ontwikkelaarsconsole](/docs/nl-nl/studio/developer-console) .

Als de serverhartslag laag blijft nadat je de [prestaties hebt verbeterd](/docs/nl-nl/performance-optimization/improve) , heeft je game mogelijk meer CPU nodig dan zijn servers standaard krijgen. Je kunt meer reserveren met [Uitgebreide Diensten voor Berekeningen](/docs/nl-nl/cloud-services/extended-services#uitgebreide-diensten-voor-rekenkracht) .

## [Clientberekeningen](#clientberekeningen)[](#clientberekeningen)

De standaard client frame rate limiet is 60 FPS. Gebruikers kunnen echter hun frame rate limiet verhogen tot 240 FPS op Windows.

De frame rate verschilt sterk tussen apparaten. Een high-end pc kan bijvoorbeeld een rekenprobleem "brute-forcen" en alleen een onopvallende dip in de frame rate ervaren. Als je [test op lagere-end apparaten](/docs/nl-nl/performance-optimization/test-on-hardware) , zijn de problemen vaak ernstiger en dus gemakkelijker op te merken.

Om de frame rate van je game te controleren:

-

Druk in de client op Shift F5  om de samenvatting van de debugstatistieken weer te geven.

-

Ga vanuit het Venster  ⟩ Prestatie  menu van Studio naar Stats  om de debugstatistieken in te schakelen.

Prestatiestatistieken in Studio worden beïnvloed door de Studio-toepassing, dus je moet de frame rate op de client bekijken voor nauwkeurige cijfers.

-

Met de [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler)  kun je de grafiek controleren om te zien of het frame langer dan 16,67 ms duurt.

Bij het evalueren van de frame rate kan het helpen om de grafische kwaliteit op de maximale waarde in te stellen om het effect van de frame rate manager te verwijderen. Open in de client het menu, klik op Instellingen , wijzig Graphics Mode  in handmatig en verhoog de grafische kwaliteit.

## [Servergeheugen](#servergeheugen)[](#servergeheugen)

Probeer het geheugengebruik van de server onder de 50% te houden. Het totale servergeheugen gebruikt de volgende formule:

6.25 GiB + (100 MiB * grootste_aantal_verbonden_spelers)

Deze cijfers gebruiken machten van 2, dus 1 GiB verwijst naar 2^30 bytes en 1 MiB naar 2^20 bytes.

Bijvoorbeeld, een server met 30 verbonden spelers heeft ongeveer 9,18 GiB aan totaal geheugen. Servers winnen geheugen wanneer spelers verbinden, maar verliezen  het niet wanneer spelers disconnecten. Als 10 spelers vertrekken, heeft de server nog steeds 9,18 GiB aan geheugen in plaats van te krimpen naar 8,2 GiB.

Wanneer servers worden afgesloten (bijvoorbeeld wanneer ze leeg zijn of als onderdeel van het [updateproces](/docs/nl-nl/projects/update-games) ), beginnen hun vervangingen met de basis hoeveelheid geheugen en beginnen op te schalen naarmate spelers verbinden.

## [Clientgeheugen](#clientgeheugen)[](#clientgeheugen)

Er zijn verschillende manieren om het geheugengebruik voor een game te controleren:

1.

Open de [Ontwikkelaarsconsole](/docs/nl-nl/studio/developer-console)  en schakel over naar het tabblad Geheugen . Dit tabblad geeft een uitsplitsing van hoe geheugen wordt toegewezen. Gebruik de client in plaats van Studio om de meest nauwkeurige metingen te krijgen.

2.

Schakel de weergave Prestatiestatistieken  in vanuit het instellingenmenu in de client om een overlay te zien met het totale geheugengebruik van de client.

Hoog geheugengebruik is niet noodzakelijk indicatief voor een probleem, maar enkele aanwijzingen dat je mogelijk verder moet onderzoeken zijn:

-

Een aanzienlijk percentage van clientcrashes dat wordt weergegeven in het Prestatie-dashboard , met name een plotselinge stijging die samenvalt met een update. Een aantal crashes is te verwachten, maar je moet onderzoeken of je crashpercentages boven de 2-3% stijgen.

-

Een crash vindt plaats tijdens het testen op een apparaat dat je wilt dat je game ondersteunt.

Een aanzienlijk deel van het geheugengebruik van een game op de client komt van assets, zoals afbeeldingen, meshes en audiobestanden, die in het geheugen zijn geladen. Controleer in de Ontwikkelaarsconsole de volgende labels onder PlaceMemory :

-

GraphicsMeshParts  - Grafisch geheugen verbruikt door meshes.

-

GraphicsTexture  - Grafisch geheugen verbruikt door texturen.

-

Sounds  - Geheugen verbruikt door audiobestanden.

## [Laadtijden](#laadtijden)[](#laadtijden)

Laadtijd, ook wel join-tijd genoemd, is de totale tijd vanaf het moment dat een speler op Play  klikt tot het moment dat de wereld wordt weergegeven en ze kunnen beginnen met spelen. Nadat de client verbinding maakt met een server, gebeurt de join in de volgende volgorde:

1.

[ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  repliceert naar de client, en elke aangepaste [laadscherm](/docs/nl-nl/players/loading-screens)  daarin verschijnt.

2.

De rest van het datamodel repliceert, inclusief alles in [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  en [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) . Als je [instanties streaming](/docs/nl-nl/workspace/streaming)  inschakelt, repliceert alleen het gebied van de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  nabij het spawnpunt van de speler in deze fase.

3.

De avatar van de speler laadt. De laadtijd eindigt wanneer het laadscherm verdwijnt en de wereld begint met renderen.

Weten welke stap traag is, helpt je om de optimalisaties met de grootste impact te kiezen. Voor veelvoorkomende oorzaken en oplossingen, zie [Verbeter prestaties](/docs/nl-nl/performance-optimization/improve#laadtijden) .

Er zijn geen ingebouwde tools voor het controleren van laadtijden, maar omdat ze geen milliseconde-niveau precisie vereisen, is een stopwatch meestal alles wat je nodig hebt om je huidige basislijn te begrijpen en te controleren of je een substantiële verbetering hebt aangebracht. Je kunt een clientscript in [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  gebruiken om een idee te krijgen van hoe je wijzigingen de laadtijden beïnvloeden, maar dit script biedt geen volledige, end-to-end meting. Het begint met timen nadat [ReplicatedFirst](/docs/nl-nl/reference/engine/classes/ReplicatedFirst)  repliceert en stopt wanneer de initiële replicatie is voltooid en [DataModel.Loaded](/docs/nl-nl/reference/engine/classes/DataModel#Loaded)  wordt geactiveerd, zodat het de tijd om verbinding te maken met een server of de avatar te laden niet omvat:

```

local startTime = os.clock()

game.Loaded:Connect(function()

  local loadTime = os.clock() - startTime

  local roundedLoadTime = math.round(loadTime * 10000) / 10000 -- vier decimalen

  print("Game geladen in " .. roundedLoadTime .. " seconden.")

  print("Aantal geladen instanties: " .. #workspace:GetDescendants())

end)

```

Voor aanvullende inzichten, schakel Print Join Size Breakdown  in vanuit het Netwerk  tabblad van [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing)  om de top 20 instanties op grootte en een percentage uitsplitsing per instantie type af te drukken wanneer je de game in Studio start.

Als je laadtijd onverwacht hoog is in verhouding tot de schijnbare grootte van je game, inspecteer dan je plaats op niet-herkende of obfuscerende scripts. Sommige gratis modellen uit de Creator Store bevatten scripts die duizenden extra instanties genereren, wat de hoeveelheid gegevens die moet repliceren wanneer een speler zich aansluit, dramatisch verhoogt.

Meet de laadtijd voor en na elke optimalisatie of update, zodat je de impact ervan kunt bevestigen en regressies kunt opvangen. Een plotselinge stijging betekent vaak dat er recent inhoud is toegevoegd aan [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  of dat een wijziging in een asset de downloadgrootte heeft vergroot.

## [Ping](#ping)[](#ping)

De twee belangrijkste metingen van ping (latentie) zijn netwerkping  en gegevensping .

Netwerkping is de round-trip tijd gemeten vanaf het moment dat de client een netwerk datapakket verzendt tot het moment dat het de echo-antwoorden van de server ontvangt. Het is vergelijkbaar met wat zou worden gerapporteerd als time  door de algemene ping-netwerkutility.

Netwerkping is zichtbaar in de Prestatiestatistieken  balk. Het wordt voornamelijk beïnvloed door de lengte van het netwerkpad tussen de client en de server, en ligt buiten jouw controle. Je kunt echter ping en andere netwerkcondities simuleren met behulp van [netwerksimulatie](/docs/nl-nl/studio/testing-modes#netwerksimulatie)  tijdens het playtesten in Studio.

Gegevensping is de round-trip tijd gemeten vanaf het moment dat de client gegevens betrouwbaar door het replicatiesysteem verzendt tot het moment dat het een echo-antwoord ontvangt van het replicatiesysteem van de server. Het omvat de tijd die wordt besteed in zowel de replicatiewachtrijen van de client als de server, samen met TCP-achtige hertransmissies van verloren of beschadigde pakketten.

Gegevensping is vergelijkbaar met het verzenden van een betrouwbare externe gebeurtenis van de client, deze ontvangen op de server, en vervolgens een betrouwbare externe gebeurtenis van de server naar de client verzenden als reactie. Omdat gegevensping ook de tijd omvat die op het netwerk tussen de client en server wordt besteed, is het groter dan of gelijk aan netwerkping.

De gemiddelde gegevensping voor alle spelers die verbonden zijn met een server is zichtbaar in het tabblad Server Stats  van de Ontwikkelaarsconsole. Gegevensping voor een individuele client is zichtbaar met Shift F3  om netwerk debugstatistieken weer te geven.

Gegevensping wordt beïnvloed door zowel het netwerkpad als door vertragingen in de replicatiewachtrijen. Wanneer de server replicatiegegevens sneller genereert dan het netwerk kan verzenden (of sneller dan de client kan verwerken), moet de data wachten in replicatiewachtrijen. Een verschil tussen gegevensping en netwerkping is normaal vanwege zowel netwerkhertransmissies als de manier waarop netwerkgegevens door de Roblox-app worden verwerkt. Als gegevensping echter aanzienlijk hoger is dan netwerkping, gebruik dan de [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler/network)  om het netwerkverkeer te bekijken. Voor optimalisatievoorstellen, zie [netwerken en replicatie](/docs/nl-nl/performance-optimization/improve#netwerken-en-replicatie) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
