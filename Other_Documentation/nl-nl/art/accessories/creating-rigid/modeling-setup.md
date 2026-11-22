<!-- Source: https://create.roblox.com/docs/nl-nl/art/accessories/creating-rigid/modeling-setup -->

Dozenmodellering | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Dozenmodellering

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

![Een screenshot van Blender die de uiteindelijke 3D-vorm van een schatkist in de viewport toont](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/Modeling-Complete.png)

Modelleren  is het proces van het creëren en vormen van de 3D-geometrie van een object. Dozenmodellering  is een fundamentele techniek in 3D-modellering die basisvormen en stappen combineert om een complexer object te creëren.

De volgende instructies zijn gebaseerd op het [Box Modeling 101 personeel artikel](https://devforum.roblox.com/t/modeling-101-in-blender-box-modeling/2963814) . Het originele artikel bevat aanvullende informatie, evenals instructies voor het instellen van Blender, beste praktijken en geavanceerde modelleervoorbeelden die niet zijn opgenomen in deze accessoirehandleiding.

Of je nu een bestaande vorm gebruikt of je eigen 3D-object maakt, het is belangrijk om rekening te houden met [technische vereisten](/docs/nl-nl/avatar/rigid-accessories/specifications) , zoals het houden van je geometrie binnen een polycount-budget, en [beleidsvereisten](/docs/nl-nl/marketplace/marketplace-policy) , zoals ervoor zorgen dat je ontwerp geen inbreuk maakt op het IP van andere makers, zowel binnen als buiten het Roblox-ecosysteem.

## [Algemene vorm](#algemene-vorm)[](#algemene-vorm)

In een nieuw Blender-bestand, verwijder alles behalve de startkubus, en maak vervolgens de basisvorm van de schatkist.

1.

In een nieuw project, selecteer alle niet-kubusobjecten en druk op X  om te verwijderen.

2.

Zet de kubus om in een rechthoek.

1.

Selecteer de kubus en druk op S  voor schalen.

2.

Druk op Y  om de schaling op de Y-as te vergrendelen.

3.

Sleep met de muis om een rechthoek te maken.

3.

Maak de bovenkant van de schatkist.

1.

Schakel over naar Bewerken -modus, druk vervolgens op 3  om over te schakelen naar vlakkenselectie.

2.

Selecteer het bovenste vlak van de doos en druk op E  om de Extrude -tool te activeren.

3.

Sleep je muis om het deksel te extruderen. Verleng het deksel tot ongeveer de helft van de hoogte van het hoofdlichaam.

## [Afgerond deksel](#afgerond-deksel)[](#afgerond-deksel)

Maak de afgeronde dekselvorm met segmentatie:

1.

Druk op 2  om over te schakelen naar randselectie.

2.

Houd Shift  ingedrukt en klik op de bovenste voor- en achterranden van je kist.

3.

Met beide randen geselecteerd, druk op Ctrl B / ⌘ B  om de Bevel -tool te activeren.

4.

Navigeer naar het contextmenu rechtsonder, stel het aantal segmenten in op 6  en schakel Clamp Overlap  in.

### [Verbind vertices](#verbind-vertices)[](#verbind-vertices)

Soms kunnen tools zoals de Bevel -tool vertices heel dicht bij elkaar verplaatsen zonder ze te verbinden. Gebruik de functie Verbind Vertices  om ervoor te zorgen dat je object vertices deelt waar mogelijk.

1.

Druk op 1  om over te schakelen naar vertexselectie, druk vervolgens op A  om alle vertices van je object te selecteren.

2.

Klik met de rechtermuisknop ergens in de viewport, selecteer vervolgens Verbind Vertices op Afstand  uit het contextmenu.

3.

Stel in de pop-upmodal de afstand in op .01 .

## [Zijkanten insetten](#zijkanten-insetten)[](#zijkanten-insetten)

Maak de linker- en rechterinzetten van je kist:

1.

Druk op 3  om over te schakelen naar vlakkenselectie.

2.

Houd Shift  ingedrukt en klik op beide zijden van je vorm. Dit selecteert zowel de linker- als de rechtervlakken.

3.

Druk op I  om de Inset -tool te activeren. Sleep de muis om de hoeveelheid inset voor het nieuwe vlak in te stellen tot ongeveer de grootte van je bevel-segmenten.

4.

Met je nieuwe insets geselecteerd, klik met de rechtermuisknop ergens in de viewport, selecteer vervolgens Extrude Along Normals  uit het contextmenu.

5.

Gebruik de muis om te slepen en de afstand van de extrusie in de kist aan te passen.

## [Voorkant insets](#voorkant-insets)[](#voorkant-insets)

Maak de voor- en achterkant van je kist door nieuwe lijnen te maken en vervolgens je vlakken tussen die lijnen te extruderen.

### [Verticale lus sneden](#verticale-lus-sneden)[](#verticale-lus-sneden)

Om je verticale lus sneden te maken:

1.

Druk op 2  om over te schakelen naar randselectie, druk vervolgens op A  om de hele kist te selecteren.

2.

Gebruik Ctrl R / ⌘ R  om een lus snede te maken.

3.

Gebruik je muis om over het object te zweven totdat de gemarkeerde snede verticaal is, klik vervolgens om te bevestigen.

4.

Stel in het contextmenu het aantal sneden in op 2 .

5.

Met de nieuwe lijnen geselecteerd, druk op S  om te schalen en Y  om binnen de Y-as te schalen.

6.

Gebruik de muis om de lijnen te slepen totdat ze bijna de randen van je kist bereiken, klik vervolgens om te bevestigen.

### [Horizontale lus sneden](#horizontale-lus-sneden)[](#horizontale-lus-sneden)

Om je horizontale lus sneden te maken:

1.

Selecteer de kist en druk op Ctrl R / ⌘ R  om een lus snede te maken, klik vervolgens om een horizontale snede te bevestigen.

2.

Stel in het contextmenu het aantal sneden in op 2 .

3.

Om elke lijn over je object recht te maken:

1.

Klik op een van je nieuwe lijnen.

2.

Druk op S  voor schalen.

3.

Druk op Z  om binnen de Z-as te schalen.

4.

Druk op 0  om de schaalwaarde op 0  in te stellen over de Z-as.

5.

Herhaal dit voor de andere lijn.

4.

Positioneer de bovenste lijn dicht bij de bovenkant onder de segmentaties.

5.

Positioneer de onderste lijn dicht bij de onderkant.

6.

Schakel Magnet Snapping  in zodat de onderste lijn samensmelt met de bestaande vertices en lijnen van de zijkanten insets.

### [Extrusies](#extrusies)[](#extrusies)

Maak de extrusies voor de voorkant, bovenkant en achterkant van de kist.

1.

Druk op 3  om over te schakelen naar vlakkenselectie.

2.

Houd Alt / ⌥  ingedrukt en klik op je voorkantvlakken om de voorkant, bovenkant en achterkant te selecteren.

3.

Met de geselecteerde vlakken, houd Shift  ingedrukt en klik op de metalen randen om ze te deselecteren. De voor- en achterkant, en de bovenste segmentaties, moeten geselecteerd blijven.

4.

Klik met de rechtermuisknop ergens in de viewport, selecteer vervolgens Extrude Faces Along Normals  uit het contextmenu.

5.

Sleep de muis om de vlakken ongeveer dezelfde breedte als de metalen randen te extruderen.

## [Volledige rand](#volledige-rand)[](#volledige-rand)

De kist is bijna klaar, maar mist nog de continue metalen rand over de bovenrand. Verwijder de bestaande vlakken en voeg nieuwe geometrie toe aan de schatkist.

### [Verwijder vlakken](#verwijder-vlakken)[](#verwijder-vlakken)

Verwijder de vlakken van de bovenste metalen randen:

1.

Begin aan een kant, houd Shift  ingedrukt en klik op de drie vlakken van de bovenste metalen rand.

2.

Druk op X  om te verwijderen.

3.

Herhaal dit proces voor de andere kant.

### [Voeg vlakken toe](#voeg-vlakken-toe)[](#voeg-vlakken-toe)

Voeg nieuwe vlakken toe aan de zijkanten die de geometrie van de schatkistdoos compleet maken.

1.

Druk op 2  om over te schakelen naar randselectie.

2.

Begin met een kant, houd Shift  ingedrukt en klik op de twee bovenste hoekranden van het ontbrekende vlak.

3.

Klik met de rechtermuisknop ergens in de viewport, selecteer vervolgens Nieuw Vlak van Randen  uit het contextmenu om een bovenvlak te maken.

4.

Herhaal stappen 2-3 met de onderste hoekranden om een ondervlak te maken.

5.

Aan de andere kant van de kist, herhaal stappen 2-4 om de metalen rand compleet te maken.

Je hebt de modelleersectie van deze tutorial voltooid. Indien gewenst, download een [referentieversie](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/Chest-Modeling-Complete.blend)  van deze fase van het project voor vergelijking.

Deze tutorial vertegenwoordigt een uiterst basisoverzicht van het 3D-modelleringsproces. Tools zoals Blender bieden veel functies, workflows en technieken om unieke en complexe modellen te creëren. Bekijk de officiële en community-tutorials van Blender voor aanvullende instructieve inhoud.

[Volgende](/docs/nl-nl/art/accessories/creating-rigid/texturing)[Vorige](/docs/nl-nl/art/accessories/creating-rigid)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
