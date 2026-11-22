<!-- Source: https://create.roblox.com/docs/nl-nl/effects/light-sources -->

Lichtbronnen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Effecten](/docs/nl-nl/effects)

# Lichtbronnen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Lokale lichtbronnen simuleren realistische verlichting van objecten zoals lampen, fakkels, schijnwerpers en tv-schermen. Door de verschillende soorten lichtbronnen te gebruiken in plaats van alleen algemene globale verlichting via de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service, kun je meeslepende omgevingen creëren zoals cyberpunk-steden, traditionele lichtfestivals en sfeervolle detective-scènes.

 ![Een verre blik op een dinergebouw in het midden van een nachtelijke stad. Het diner maakt gebruik van verschillende lokale lichtbronnen.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/Showcase.jpg)

De [LightingStyle](/docs/nl-nl/reference/engine/classes/Lighting#LightingStyle)  eigenschap, alleen aanpasbaar in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster voor het globale [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  object, stelt de verlichtingsstijl van je spel in. Voor meer informatie, zie [Uiterlijk](/docs/nl-nl/environment/lighting#uiterlijk) .

Om lichtgidsen  te bekijken die de kleur en het effectgebied van lichtbronnen aangeven, zoals de hoek van lichtemissie vanuit de top van de kegel van een [SpotLight](/docs/nl-nl/reference/engine/classes/SpotLight) , open je [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing)  en zet je Toon Lichtgidsen  aan.

## [Lichttypes](#lichttypes)[](#lichttypes)

Lokale lichtbronnen omvatten [PointLight](#pointlight) , [SpotLight](#spotlight)  en [SurfaceLight](#surfacelight) . Elke [deelt verschillende eigenschappen](#gedeelde-eigenschappen)  van de [Light](/docs/nl-nl/reference/engine/classes/Light)  klasse, waaronder [Color](/docs/nl-nl/reference/engine/classes/Light#Color) , [Brightness](/docs/nl-nl/reference/engine/classes/Light#Brightness)  en [Shadows](/docs/nl-nl/reference/engine/classes/Light#Shadows) .

### [PointLight](#pointlight)[](#pointlight)

Een [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  straalt licht sferisch uit vanaf een enkel punt. Dit object is ideaal voor niet-directionele  lichten zoals gloeilampen, fakkels en vuurballen.

Om een puntlicht in Studio te maken, voeg je een [PointLight](/docs/nl-nl/reference/engine/classes/PointLight)  toe aan een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  of een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  (het wordt aanbevolen om [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  te gebruiken voor punt-specifieke lichtemissie). Pas vervolgens de [Range](/docs/nl-nl/reference/engine/classes/PointLight#Range)  van het object aan, evenals de [gedeelde eigenschappen](#gedeelde-eigenschappen)  zoals [Brightness](/docs/nl-nl/reference/engine/classes/PointLight#Brightness)  en [Color](/docs/nl-nl/reference/engine/classes/PointLight#Color) .

#### [Bereik](#bereik)[](#bereik)

De [Range](/docs/nl-nl/reference/engine/classes/PointLight#Range)  eigenschap van een puntlicht definieert de radiale afstand van verlichting vanaf de positie van het licht, gemeten in studs.

8 12

![Een straatlamp puntlicht met een klein bereik.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/PointLight-Range-8.jpg)

### [SpotLight](#spotlight)[](#spotlight)

Een [SpotLight](/docs/nl-nl/reference/engine/classes/SpotLight)  straalt licht uit in de vorm van een kegel met een sferische basis. Dit object is ideaal voor directionele lichten zoals straatlampen, zaklampen en koplampen.

Om een schijnwerper in Studio te maken, voeg je een [SpotLight](/docs/nl-nl/reference/engine/classes/SpotLight)  toe aan een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  of een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  en stel je de [Face](/docs/nl-nl/reference/engine/classes/SpotLight#Face)  eigenschap in om te specificeren vanuit welke richting het licht uitstraalt. Pas vervolgens de [Angle](/docs/nl-nl/reference/engine/classes/SpotLight#Angle)  en [Range](/docs/nl-nl/reference/engine/classes/SpotLight#Range)  aan, evenals de [gedeelde eigenschappen](#gedeelde-eigenschappen)  zoals [Brightness](/docs/nl-nl/reference/engine/classes/SpotLight#Brightness)  en [Color](/docs/nl-nl/reference/engine/classes/SpotLight#Color) .

#### [Gezicht](#gezicht)[](#gezicht)

De [Face](/docs/nl-nl/reference/engine/classes/SpotLight#Face)  eigenschap van een schijnwerper bepaalt welke kant/as het licht uitstraalt, zoals weergegeven vanuit het gloeiende lichtdeel van de volgende straatlamp:

Onder Links

![Een straatlamp schijnwerper die licht uitstraalt vanuit zijn onderkant.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/SpotLight-Face-Bottom.jpg)

#### [Hoek](#hoek)[](#hoek)

De [Angle](/docs/nl-nl/reference/engine/classes/SpotLight#Angle)  eigenschap van een schijnwerper definieert de hoek van lichtemissie vanuit de top van de kegel. De maximale waarde is 180 , wat een volledige halve bol verlicht vanuit de top.

30 75

![Een straatlamp schijnwerper met een hoek van 30 graden van emissie.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/SpotLight-Angle-30.jpg)

### [SurfaceLight](#surfacelight)[](#surfacelight)

Een [SurfaceLight](/docs/nl-nl/reference/engine/classes/SurfaceLight)  straalt licht uit vanaf de oppervlakte van een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) . Dit object is ideaal voor verlichting van computerschermen, reclameborden, borden en fluorescentiepanelen.

Om een oppervlakte licht in Studio te maken, voeg je een [SurfaceLight](/docs/nl-nl/reference/engine/classes/SurfaceLight)  toe aan een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  en stel je de [Face](/docs/nl-nl/reference/engine/classes/SurfaceLight#Face)  eigenschap in om te specificeren van welke oppervlakte het licht uitstraalt. Pas vervolgens de [Angle](/docs/nl-nl/reference/engine/classes/SurfaceLight#Angle)  en [Range](/docs/nl-nl/reference/engine/classes/SurfaceLight#Range)  aan, evenals de [gedeelde eigenschappen](#gedeelde-eigenschappen)  zoals [Brightness](/docs/nl-nl/reference/engine/classes/SurfaceLight#Brightness)  en [Color](/docs/nl-nl/reference/engine/classes/SurfaceLight#Color) .

#### [Gezicht](#gezicht-1)[](#gezicht-1)

De [Face](/docs/nl-nl/reference/engine/classes/SurfaceLight#Face)  eigenschap van een oppervlakte licht bepaalt de kant van de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  waaruit het licht straalt. Merk op dat het licht uit de gehele oppervlakte straalt, niet alleen een punt op de oppervlakte.

Onder Rechts

![Een bord oppervlakte licht dat licht uitstraalt vanuit zijn onderkant.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/SurfaceLight-Face-Bottom.jpg)

#### [Hoek](#hoek-1)[](#hoek-1)

De [Angle](/docs/nl-nl/reference/engine/classes/SurfaceLight#Angle)  eigenschap van een oppervlakte licht definieert de hoek van lichtemissie vanuit het oppervlak van het deel. Een hoek van 0  betekent dat het licht recht naar buiten van het oppervlak reist, terwijl een hoek van 180  betekent dat het licht recht naar buiten reist, loodrecht op het oppervlak.

0 60

![Een bord oppervlakte licht met een hoek van 0 graden van emissie.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/SurfaceLight-Angle-0.jpg)

## [Gedeelde eigenschappen](#gedeelde-eigenschappen)[](#gedeelde-eigenschappen)

Alle lichtbronnen delen verschillende eigenschappen van de [Light](/docs/nl-nl/reference/engine/classes/Light)  klasse, waaronder [kleur](#kleur) , [helderheid](#helderheid)  en [schaduwen](#schaduwen) .

### [Kleur](#kleur)[](#kleur)

De [Color](/docs/nl-nl/reference/engine/classes/Light#Color)  eigenschap stelt de [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  waarde in van het uitgezonden licht.

[255, 100, 50] [0, 255, 125] [75, 150, 255]

![Een fakkel die rood licht uitstraalt.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/Light-Color-255-100-50.jpg)

### [Helderheid](#helderheid)[](#helderheid)

De [Brightness](/docs/nl-nl/reference/engine/classes/Light#Brightness)  eigenschap stelt de helderheid van het licht in, met maximaal effect in het midden van het licht. Merk op dat [Brightness](/docs/nl-nl/reference/engine/classes/Light#Brightness)  nog steeds beperkt is tot het gedefinieerde bereik van het licht, dus een hogere waarde voor [Brightness](/docs/nl-nl/reference/engine/classes/Light#Brightness)  verlicht geen groter gebied rond het licht.

2 10 50

![Een fakkel die weinig licht uitstraalt.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/Light-Brightness-2.jpg)

### [Schaduwen](#schaduwen)[](#schaduwen)

De [Shadows](/docs/nl-nl/reference/engine/classes/Light#Shadows)  eigenschap projecteert schaduwen waar licht wordt geblokkeerd door een obstakel.

Ingeschakeld Uitgeschakeld

![Een hoekzicht van het diner met schaduwen ingeschakeld.](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/light-sources/Light-Shadows-True.jpg)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
