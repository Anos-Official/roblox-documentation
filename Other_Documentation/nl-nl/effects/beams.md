<!-- Source: https://create.roblox.com/docs/nl-nl/effects/beams -->

Stralen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Effecten](/docs/nl-nl/effects)

# Stralen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een [Beam](/docs/nl-nl/reference/engine/classes/Beam)  is een object dat een [Texture](/docs/nl-nl/reference/engine/classes/Texture)  weergeeft tussen twee [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten. Door de eigenschappen van de straal in te stellen, kun je:

-

Een [textuur](#textuur)  en [kleurverloop](#kleur)  toevoegen om interessante visuals te creëren zoals watervallen en krachtvelden.

-

De [doorzichtigheid](#doorzichtigheid)  van een straal aanpassen zodat deze in de loop van de tijd vervaagt.

-

De vorm vervormen door de [breedte](#breedte)  of [bocht](#bocht)  van elk bevestigingspunt te veranderen.

-

De [lengte en modus](#textuurlengtemodus)  van de textuur specificeren om te beïnvloeden hoe deze zich herhaalt over de lengte van de straal.

## [Stralen maken](#stralen-maken)[](#stralen-maken)

Voordat je begint met het maken van een straal, is het handig om de zichtbaarheid van de bevestigingen in te schakelen, zodat je kunt zien waar de straal begint en eindigt. Dit kun je doen door Toon Beperkingsdetails  in het Weergave  menu van Studio in te schakelen.

Om een straal te maken:

1.

Maak twee onderdelen en positioneer ze op een korte afstand van elkaar. Eén zal fungeren als het begin van de straal en de andere als het einde van de straal. Groepeer de onderdelen in een [Model](/docs/nl-nl/reference/engine/classes/Model) .

2.

Voeg in het Explorer  venster een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  object toe aan elk onderdeel:

1.

Beweeg de muis boven een onderdeel en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het contextmenu voor Bevestiging .

3.

Herhaal dit voor het andere onderdeel.

3.

Voeg in het Explorer  venster een [Beam](/docs/nl-nl/reference/engine/classes/Beam)  object toe aan het model:

1.

Beweeg de muis boven het model en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het contextmenu voor Straal .

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Model-Beam-Setup.png)

4.

Selecteer het nieuwe Straal  object en wijs de bevestigingen toe. Zorg ervoor dat je elke bevestigingsproperty aan een ander [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  object toewijst.

1.

Selecteer in het Eigenschappen  venster de Attachment0  property. Je cursor verandert.

2.

Selecteer in het Explorer  venster de bevestiging van het onderdeel dat je als het begin van je straal wilt hebben.

3.

Ga terug naar het Eigenschappen  venster en selecteer de Attachment1  property. Je cursor verandert.

4.

Selecteer in het Explorer  venster de bevestiging van het onderdeel dat je als het einde van je straal wilt hebben.

![](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/beam/Default-Beam.png) Standaard straal tussen twee bevestigingen

Stralen hebben bevestigingen nodig om goed te functioneren. Als je een van de bevestigingsobjecten uit stap 4 verwijdert, stopt de straal met het weergeven van zijn textuur.

## [Stralen aanpassen](#stralen-aanpassen)[](#stralen-aanpassen)

Door te experimenteren met de volgende eigenschappen, kun je het visuele uiterlijk van een straal aanpassen om unieke gameplay-elementen te maken zoals krachtvelden, watervallen en padobstakels.

De visuele kwaliteit van je stralen kan veranderen afhankelijk van de grafische instellingen op het apparaat van de speler. Om je straal over kwaliteitsniveaus te bekijken, wordt aanbevolen om [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing)  te openen, te zoeken naar Editor Kwaliteitsniveau , en dit in te stellen op zowel het laagste als het hoogste niveau nadat je klaar bent met het aanpassen van je straal.

### [Textuur](#textuur)[](#textuur)

De [Texture](/docs/nl-nl/reference/engine/classes/Beam#Texture)  property geeft die textuur weer over de lengte van de straal. Je kunt de [Texture](/docs/nl-nl/reference/engine/classes/Beam#Texture)  property van een straal instellen op elk asset ID. Voor meer informatie, inclusief hoe je je eigen texturen kunt toevoegen of uploaden, zie [hier](/docs/nl-nl/projects/assets/manager#asset-import) .

 ![Een textuur van donkere grijze cirkels tegen een grijze achtergrond wordt tussen twee bevestigingen weergegeven.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/beam/Texture-Applied.png)

Een straal geeft zijn textuur weer met behulp van twee driehoeken die zijn getekend tussen [Segments](/docs/nl-nl/reference/engine/classes/Beam#Segments) , en de segmenten zijn gerangschikt tussen de oriëntatie van de twee bevestigingspunten. Wanneer je bevestigingspunten in verschillende richtingen draait, draaien de segmenten ook.

 ![Dezelfde textuur van de vorige afbeelding is nu gebogen omdat de bevestigingen in verschillende oriëntaties staan.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/beam/Attachments-Rotated.png)

### [Kleur](#kleur)[](#kleur)

De [Color](/docs/nl-nl/reference/engine/classes/Beam#Color)  property tint de textuur van de straal naar een specifieke tint, of naar een kleurverloop [ColorSequence](/docs/nl-nl/reference/engine/datatypes/ColorSequence)  over zijn gehele lengte.

Constante Kleur Kleurverloop

1.

Selecteer in het Explorer  venster de straal.

2.

Selecteer in het Eigenschappen  venster de Kleur  property. Je kunt ofwel:

1.

Klik op het kleurvak om het Kleuren  pop-upvenster te openen en een kleur te selecteren.

2.

Drie nummers invoeren in het RGB-kleurwaardeveld.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Color-Input-Options.png)

### [Doorzichtigheid](#doorzichtigheid)[](#doorzichtigheid)

De [Transparency](/docs/nl-nl/reference/engine/classes/Beam#Transparency)  property stelt de doorzichtigheid van de straal in als een constante waarde of als een [NumberSequence](/docs/nl-nl/reference/engine/datatypes/NumberSequence)  met waarden van 0  (volledig ondoorzichtig) tot 1  (volledig doorzichtig).

Constante Opacity Nummerreeks

1.

Selecteer in het Explorer  venster de straal.

2.

Selecteer in het Eigenschappen  venster de Doorzichtigheid  property.

3.

Voer de gewenste doorzichtigheid voor de straal in.

### [Breedte](#breedte)[](#breedte)

Je kunt de breedte van de straal in studs aan elk uiteinde instellen door de [Width0](/docs/nl-nl/reference/engine/classes/Beam#Width0)  en [Width1](/docs/nl-nl/reference/engine/classes/Beam#Width1)  properties te configureren. Een hogere waarde staat gelijk aan een grotere breedte en een lagere waarde staat gelijk aan een kleinere breedte. Als je een van de waarden kleiner dan 0 instelt, stelt Studio deze terug in op 0 .

De straal hieronder heeft een [Width0](/docs/nl-nl/reference/engine/classes/Beam#Width0)  waarde van 0.5  en een [Width1](/docs/nl-nl/reference/engine/classes/Beam#Width1)  waarde van 3 .

 ![Een textuur wordt tussen twee bevestigingen weergegeven. De textuur begint met een kleine breedte en eindigt met een grote breedte.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/beam/Width-Adjusted.png)

### [Textuurlengte/modus](#textuurlengtemodus)[](#textuurlengtemodus)

De [TextureLength](/docs/nl-nl/reference/engine/classes/Beam#TextureLength)  en [TextureMode](/docs/nl-nl/reference/engine/classes/Beam#TextureMode)  van een straal bepalen hoe zijn [textuur](#textuur)  zich herhaalt over zijn lengte.

Wanneer [TextureMode](/docs/nl-nl/reference/engine/classes/Beam#TextureMode)  is ingesteld op [Enum.TextureMode.Wrap](/docs/nl-nl/reference/engine/enums/TextureMode#Wrap)  of [Enum.TextureMode.Static](/docs/nl-nl/reference/engine/enums/TextureMode#Static) , zullen de herhalingen van de textuur gelijk zijn aan de totale lengte van de straal (in studs) gedeeld door zijn [TextureLength](/docs/nl-nl/reference/engine/classes/Beam#TextureLength) .

 ![TextureMode diagram met Wrap of Static modus](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/TextureMode/Wrap-Static.png)

Wanneer [TextureMode](/docs/nl-nl/reference/engine/classes/Beam#TextureMode)  is ingesteld op [Enum.TextureMode.Stretch](/docs/nl-nl/reference/engine/enums/TextureMode#Stretch) , zal de textuur [TextureLength](/docs/nl-nl/reference/engine/classes/Beam#TextureLength)  keer herhaald worden over de totale lengte van de straal.

![TextureMode diagram met Stretch modus](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/TextureMode/Stretch.png)

### [Kijken](#kijken)[](#kijken)

Een straal is een 2D-projectie die bestaat in 3D-ruimte, wat betekent dat deze mogelijk niet vanuit elke hoek zichtbaar is. De [FaceCamera](/docs/nl-nl/reference/engine/classes/Beam#FaceCamera)  property, wanneer ingesteld op true , zorgt ervoor dat de straal altijd naar de [CurrentCamera](/docs/nl-nl/reference/engine/classes/Workspace#CurrentCamera)  kijkt, ongeacht de oriëntatie.

Standaard vs. FaceCamera

### [Bocht](#bocht)[](#bocht)

Stralen zijn geconfigureerd om een kubische Bézier-curve te gebruiken die is gevormd door vier controlepunten. Dit betekent dat ze niet beperkt zijn tot rechte lijnen en de curve van de straal kan worden aangepast door [CurveSize0](/docs/nl-nl/reference/engine/classes/Beam#CurveSize0) , [CurveSize1](/docs/nl-nl/reference/engine/classes/Beam#CurveSize1) , en de oriëntatie van de [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  van de straal te veranderen.

-

P0  — Het begin van de straal; positie van [Attachment0](/docs/nl-nl/reference/engine/classes/Beam#Attachment0) .

-

P1  — [CurveSize0](/docs/nl-nl/reference/engine/classes/Beam#CurveSize0)  studs van [Attachment0](/docs/nl-nl/reference/engine/classes/Beam#Attachment0) , in de positieve X  richting van [Attachment0](/docs/nl-nl/reference/engine/classes/Beam#Attachment0) .

-

P2  — [CurveSize1](/docs/nl-nl/reference/engine/classes/Beam#CurveSize1)  studs van [Attachment1](/docs/nl-nl/reference/engine/classes/Beam#Attachment1) , in de negatieve X  richting van [Attachment1](/docs/nl-nl/reference/engine/classes/Beam#Attachment1) .

-

P3  — Het einde van de straal; positie van [Attachment1](/docs/nl-nl/reference/engine/classes/Beam#Attachment1) .

 ![Diagram van de kromming van de straal](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/Beam/Curvature-Diagram.png)  ![](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/beam/Curves-Applied.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
