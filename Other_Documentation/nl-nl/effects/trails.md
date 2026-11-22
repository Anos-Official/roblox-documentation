<!-- Source: https://create.roblox.com/docs/nl-nl/effects/trails -->

Spooren | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Effecten](/docs/nl-nl/effects)

# Spooren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een [Trail](/docs/nl-nl/reference/engine/classes/Trail)  is een object dat een spoor creëert tussen en achter twee [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten terwijl ze door de ruimte bewegen. Spooren zijn nuttig om spelers te helpen beweging te visualiseren, zoals een zwaard dat door de lucht snijdt, projectielen die naar hun doel vliegen, of voetafdrukken die wegwandelen.

Nadat je een [spoor hebt gemaakt](#spooren-maken) , kun je:

-

Een [textuur](#textuur)  toevoegen om interessante visuals te creëren.

-

Een constante of gradient [kleur](#kleur)  en/of [transparantie](#transparantie)  instellen.

-

De [levensduur](#levensduur)  van een spoor aanpassen.

-

De [lengte en modus](#textuurlengtemodus)  van de textuur specificeren om te beïnvloeden hoe deze schaalt, herhaalt en meebeweegt met de bevestigingen van het spoor.

## [Spooren maken](#spooren-maken)[](#spooren-maken)

Voordat je begint met het maken van een spoor, is het nuttig om de zichtbaarheid van bevestigingen in te schakelen, zodat je gemakkelijker kunt zien hoe hun afstand het spoor beïnvloedt. Je kunt dit doen door Toon Constraint Details  in het Weergave  menu van Studio in te schakelen.

De volgende video toont hoe bevestigingen die dichter bij elkaar staan een spoor met een kleinere breedte creëren:

Om een spoor op een onderdeel te maken:

1.

In het Explorer  venster, voeg twee [Attachments](/docs/nl-nl/reference/engine/classes/Attachment)  en een [Trail](/docs/nl-nl/reference/engine/classes/Trail)  object toe aan het onderdeel.

1.

Hover over het onderdeel en klik op de ⊕  knop. Een contextmenu verschijnt.

2.

Kies in het menu om twee Attachments  en één Trail  toe te voegen.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Part-Trail-Setup.png)

2.

Selecteer het nieuwe Trail  object en wijs de bevestigingen toe. Zorg ervoor dat je elke bevestigingsproperty aan een ander [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  object toewijst.

1.

In het Properties  venster, selecteer de Attachment0  property. Je cursor verandert.

2.

In het Explorer  venster, selecteer de eerste bevestiging die je hebt gemaakt.

3.

Terug in het Properties  venster, selecteer de Attachment1  property. Je cursor verandert.

4.

In het Explorer  venster, selecteer de tweede bevestiging die je hebt gemaakt.

3.

Gebruik de [Verplaats](/docs/nl-nl/parts#verplaatsen)  tool om beide bevestigingen binnen het onderdeel te positioneren, afhankelijk van hoe breed je het spoor wilt hebben.

4.

Om het spoor te zien, verplaats het onderdeel in elke richting en het spoor volgt.

Spooren hebben bevestigingen nodig om goed te functioneren. Als je een van de [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten uit stap 2 verwijdert, stopt het spoor met het renderen van zijn textuur.

## [Spooren aanpassen](#spooren-aanpassen)[](#spooren-aanpassen)

Door te experimenteren met de volgende eigenschappen, kun je het visuele uiterlijk van een spoor aanpassen om unieke gameplay-elementen te maken zoals windstoten, zwaardslagen en bandenafdrukken van snelle auto's.

De visuele kwaliteit van je sporen kan veranderen afhankelijk van de grafische instellingen op het apparaat van de speler. Om je spoor over kwaliteitsniveaus te bekijken, wordt aanbevolen om [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing)  te openen, te zoeken naar Editor Quality Level , en deze in te stellen op zowel het laagste als het hoogste niveau nadat je je spoor hebt aangepast.

### [Textuur](#textuur)[](#textuur)

De [Texture](/docs/nl-nl/reference/engine/classes/Trail#Texture)  property rendert een textuur over de lengte van het spoor. Je kunt de [Texture](/docs/nl-nl/reference/engine/classes/Trail#Texture)  property van een spoor instellen op elk asset ID. Voor meer informatie, inclusief hoe je je eigen texturen kunt toevoegen of importeren, zie [hier](/docs/nl-nl/projects/assets/manager#asset-import) .

### [Kleur](#kleur)[](#kleur)

De [Color](/docs/nl-nl/reference/engine/classes/Trail#Color)  property tint de textuur van het spoor naar een specifieke tint of een [ColorSequence](/docs/nl-nl/reference/engine/datatypes/ColorSequence) . De video hieronder toont hoe een constante kleur zich verhoudt tot een gradientkleur over de [levensduur](#levensduur)  van het spoor.

Constante Kleur Kleurverloop

1.

In het Explorer  venster, selecteer het spoor.

2.

In het Properties  venster, selecteer de Color  property. Je kunt ofwel:

1.

Klik op het kleurvak om het Kleuren  pop-upvenster te openen en een kleur te selecteren.

2.

Drie nummers invoeren in het RGB-kleurwaardeveld.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Color-Input-Options.png)

### [Transparantie](#transparantie)[](#transparantie)

De [Transparency](/docs/nl-nl/reference/engine/classes/Trail#Transparency)  property stelt de transparantie van de segmenten van het spoor in over zijn [Lifetime](/docs/nl-nl/reference/engine/classes/Trail#Lifetime) . Het kan een consistente waarde zijn of een [NumberSequence](/docs/nl-nl/reference/engine/datatypes/NumberSequence)  met waarden van 0  (volledig ondoorzichtig) tot 1  (volledig doorzichtig).

Constante Opacity Nummerreeks

1.

In het Explorer  venster, selecteer het spoor.

2.

In het Properties  venster, selecteer de Transparency  property.

3.

Voer de gewenste opaciteit voor het spoor in.

### [Levensduur](#levensduur)[](#levensduur)

De [Lifetime](/docs/nl-nl/reference/engine/classes/Trail#Lifetime)  property stelt je in staat om de duur van het spoor in seconden in te stellen. Wanneer je de waarde van deze property verlaagt, beweegt het spoor sneller door de ruimte en verkort het daardoor de lengte van het spoor. Dit kan het object een snellere, meer geanimeerde visuele uitstraling geven.

Spoor met een levensduur van 0.5 (links) vs. spoor met een levensduur van 3.0 (rechts)

### [Textuurlengte/modus](#textuurlengtemodus)[](#textuurlengtemodus)

De [TextureLength](/docs/nl-nl/reference/engine/classes/Trail#TextureLength)  en [TextureMode](/docs/nl-nl/reference/engine/classes/Trail#TextureMode)  van een spoor bepalen hoe zijn [textuur](#textuur)  schaalt, herhaalt en meebeweegt met de bevestigingen van het spoor.

Schaal en Herhaling Beweging

Wanneer [TextureMode](/docs/nl-nl/reference/engine/classes/Trail#TextureMode)  is ingesteld op [Enum.TextureMode.Wrap](/docs/nl-nl/reference/engine/enums/TextureMode#Wrap)  of [Enum.TextureMode.Static](/docs/nl-nl/reference/engine/enums/TextureMode#Static) , stelt de [TextureLength](/docs/nl-nl/reference/engine/classes/Trail#TextureLength)  property de lengte van de textuur in terwijl deze herhaalt over de lengte van het spoor.

![TextureMode diagram met Wrap modus](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/TextureMode/Wrap-Static.png)

Wanneer [TextureMode](/docs/nl-nl/reference/engine/classes/Trail#TextureMode)  is ingesteld op [Enum.TextureMode.Stretch](/docs/nl-nl/reference/engine/enums/TextureMode#Stretch) , zal de textuur [TextureLength](/docs/nl-nl/reference/engine/classes/Trail#TextureLength)  keer herhalen over de totale lengte van het spoor.

![TextureMode diagram met Stretch modus](https://prod.docsiteassets.roblox.com/assets/engine-api/enums/TextureMode/Stretch.png)

### [Kijken](#kijken)[](#kijken)

Een spoor is een 2D-projectie die bestaat in 3D-ruimte, wat betekent dat het mogelijk niet vanuit elke hoek zichtbaar is. De [FaceCamera](/docs/nl-nl/reference/engine/classes/Trail#FaceCamera)  property, wanneer ingesteld op true , zorgt ervoor dat het spoor altijd naar de [CurrentCamera](/docs/nl-nl/reference/engine/classes/Workspace#CurrentCamera)  kijkt, ongeacht de oriëntatie.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
