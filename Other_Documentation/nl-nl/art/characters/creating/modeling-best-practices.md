<!-- Source: https://create.roblox.com/docs/nl-nl/art/characters/creating/modeling-best-practices -->

Modelleren beste praktijken | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Modelleren beste praktijken

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Modelleren, soms bekend als sculpting , is het proces van het vormen van de geometrie van je model of mesh. Deze gids behandelt belangrijke concepten en tips die je moet doornemen voordat je je eigen unieke karaktervorm creëert.

Door te begrijpen hoe je niet-destructieve sculptingwijzigingen aan het hoofd kunt aanbrengen, het deel van het karakter dat de meest complexe componenten bevat, kun je deze technieken en concepten blijven toepassen op andere delen van het karaktermodel.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Pre-Sculpting.png)  Starttemplate model

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Post-Sculpting.png) Model na aangepaste sculpting

Bij het bewerken van sjablonen, verwijder of voeg geen vertices toe aan het lichaam van je karakter . Dit zorgt ervoor dat de skinning en gezichtsanimatiegegevens van je karakter ongewijzigd en volledig functioneel blijven.

## [Niet-destructief modelleren](#niet-destructief-modelleren)[](#niet-destructief-modelleren)

Niet-destructief modelleren betekent het gebruik van een proces dat de fysieke vorm of constructie van het basismeshobject niet verandert. Wanneer je een sjabloonmodel wijzigt, gebruik dan geen tools of functies die vertices uit je meshes verwijderen of toevoegen. Gebruik in plaats daarvan de sculptingtools van Blender om de vorm van je karakter te veranderen door alleen de positie van bestaande vertices te wijzigen . Dit zorgt ervoor dat vertices en vlakken die aan skinning of animatiegegevens zijn gekoppeld, die belangrijke karaktergegevens behouden.

Extreme geometrische veranderingen, zelfs als de vertices niet worden verwijderd, kunnen nog steeds een nadelige invloed hebben op je rigging en skinning. Het is belangrijk om een starttemplate-bestand te kiezen dat dicht bij je uiteindelijke ontwerp ligt en om consistente en proportionele wijzigingen aan te brengen tijdens het sculpten.

## [Randflow](#randflow)[](#randflow)

Randflow is een veelvoorkomend modelleringconcept dat ervoor zorgt dat de vertices van je model natuurlijk de organische kromming van de vorm van je model volgen. Bij het aanbrengen van wijzigingen in de topologie van je model, moet je een natuurlijke randflow behouden door ervoor te zorgen dat je vertices een proportionele afstand van elkaar behouden en de gebruikelijke spiergroepen en contouren van je model volgen.

Zelfs bij het behouden van randflow, moet je bepaalde gebieden van het karaktermodel vermijden om te sculpten. De volgende zijn voorbeelden van belangrijke secties van het gezicht die een natuurlijke randflow volgen en in een vergelijkbare vorm moeten worden gehouden:

| Ronde hoofdregio | | Randflow notities |
| --- | --- |
|

Rond Smalle

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Edge-Flow-Nasolabial-A.png) | | Voorhoofd Rimpels en Nasolabiale Randen : De randlijnen voor de voorhoofd rimpels en nasolabiale randen zijn essentieel voor verschillende uitdrukkingen die de mond, voorhoofdfrons, wenkbrauwbeweging en wangen omvatten.

Als je deze secties van je topologie wijzigt, zorg er dan voor dat je de oorspronkelijke vorm zoveel mogelijk behoudt, en dat ze een vergelijkbare relatieve relatie tot elkaar behouden.

 |
|

Rond Smalle

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Edge-Flow-Mouth-A.png) | | Mond en Lippen Randen : De topologie rond de lippen en mond heeft cirkelvormige meshstructuren zodat de mond kan openen en sluiten. Deze structuur kan de mesh vouwen om de lippen op een natuurlijke manier de klinkers * a* , * e* , * i* , * o*  en * u*  te visualiseren. De neutrale vorm is een gesloten mond, en de randflow rond de mond is een doorlopende lijn om de verwachte mondvormen nauwkeurig te vouwen en te vervormen.

Voor deze tutorial wordt aanbevolen om dit gebied van de gezichts topologie niet te wijzigen vanwege het risico dat de onderliggende tong, boven- en onderkaak, en opgeslagen gezichtsgegevens negatief worden beïnvloed. Je kunt een sculptingmasker gebruiken om ervoor te zorgen dat dit gebied niet wordt beïnvloed door enige modelleringwijzigingen.

 |
|

Rond Smalle

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Edge-Flow-Eyes-A.png) | | Ogen : De oogleden hebben voldoende meshlijnen om de ogen te sluiten. De doorlopende lijnen op de oogleden stellen de oogleden in staat om te vervormen en te vouwen zoals verwacht bij het knipperen of verwijden.

Voor deze tutorial wordt aanbevolen om dit gebied van de gezichts topologie niet te wijzigen vanwege het risico dat de onderliggende oogbol meshes en opgeslagen gezichtsgegevens die bijdragen aan nauwkeurige uitdrukkingen negatief worden beïnvloed. Je kunt een sculptingmasker gebruiken om ervoor te zorgen dat dit gebied niet wordt beïnvloed door enige modelleringwijzigingen.

 |
|

Rond Smalle

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Edge-Flow-Eyebrow-A.png) | | Oogleden en Wenkbrauwen : De oogleden en wenkbrauwen vereisen voldoende ruimte tussen de twee gebieden.

Als je de topologie boven de ogen wijzigt, houd er dan rekening mee dat de oogleden en wenkbrauwen een natuurlijke ruimte tussen de twee gebieden vereisen. Zowel de oogleden als de wenkbrauwen kunnen verschuiven en van positie veranderen met verschillende gezichtsuitdrukkingen en, als ze niet goed zijn gemodelleerd, kunnen ze in elkaar botsen tijdens een gezichtspositie.

 |

Het niet volgen van randflowconcepten kan ertoe leiden dat de topologie van je model met elkaar in conflict komt tijdens animaties, wat soms bekend staat als crashen.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Sculpting-Crash-Example.png)  In dit voorbeeld bewegen de bovenste en onderste oogleden langs elkaar wanneer ze sluiten, wat leidt tot gekartelde artefacten waar de vertices botsen en crashen.

Door zorgvuldig je template mesh te sculpten, kun je voorkomen dat je deze topologiebotsingen later moet corrigeren, wat vaak handmatige correcties van rig, skinning en/of gezichtsanimatiegegevens vereist.

[Volgende](/docs/nl-nl/art/characters/creating/modeling-tips)[Vorige](/docs/nl-nl/art/characters/creating/blender-configurations)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
