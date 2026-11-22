<!-- Source: https://create.roblox.com/docs/nl-nl/effects/particle-emitters -->

Deeltjesemitter | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Effecten](/docs/nl-nl/effects)

# Deeltjesemitter

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  is een object dat aanpasbare 2D-afbeeldingen (deeltjes) in de wereld uitstraalt, nuttig voor het simuleren van speciale effecten zoals vuur, rook en vonken.

Je kunt een [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  aan een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  of een object van de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) -klasse koppelen. Wanneer het aan een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  is gekoppeld, verschijnen deeltjes willekeurig binnen de begrenzingsdoos of [vorm](#vorm)  van het onderdeel; wanneer het aan een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  is gekoppeld, komen deeltjes uit de positie van de attachment.

Bovendien bepaalt de eigenschap [EmissionDirection](/docs/nl-nl/reference/engine/classes/ParticleEmitter#EmissionDirection)  de zijde ([Enum.NormalId](/docs/nl-nl/reference/engine/enums/NormalId) ) van de emissie wanneer de emitter aan een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  is gekoppeld. Wanneer je deze eigenschap wijzigt, wijzig je ook de richting van de deeltjesemissie.

Wanneer je de ouder [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  van een emitter draait, verandert de oriëntatie van zijn zijde ook, waardoor de richting van de deeltjesemissie verandert. Als alternatief, als je een emitter aan een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  toevoegt, kun je de attachment zelf draaien in plaats van [EmissionDirection](/docs/nl-nl/reference/engine/classes/ParticleEmitter#EmissionDirection)  te gebruiken.

## [Pas deeltjes aan](#pas-deeltjes-aan)[](#pas-deeltjes-aan)

Door te experimenteren met de volgende eigenschappen, kun je het visuele uiterlijk van een deeltje aanpassen om unieke gameplay-elementen te creëren zoals uitbarstende vulkanen, magische stof en stofdeeltjes.

De visuele kwaliteit van je deeltjes kan veranderen afhankelijk van de grafische instellingen op het apparaat van de speler. Om je deeltjes over kwaliteitsniveaus te bekijken, wordt aanbevolen om [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing)  te openen, te zoeken naar Editor Quality Level  en deze in te stellen op zowel het laagste als het hoogste niveau nadat je klaar bent met het aanpassen van je deeltjes.

### [Textuur](#textuur)[](#textuur)

De [Texture](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Texture)  eigenschap rendert de afbeelding die elk deeltje weergeeft. Standaard hebben deeltjesemitters deeltjes met een witte sparkle-textuur, maar je kunt deze wijzigen in elke textuur om interessante effecten te bereiken.

Drie vergelijkbare deeltjesemitters met verschillende [Texture](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Texture) -assets

Als je een afbeelding maakt om als deeltje-textuur te gebruiken, is het het beste om het .png-formaat met een transparante achtergrond te gebruiken. Als je textuur grijswaarden heeft zonder alpha-kanaal, probeer dan de eigenschap [LightEmission](/docs/nl-nl/reference/engine/classes/ParticleEmitter#LightEmission)  van de deeltjesemitter in te stellen op 1  om de donkerdere gebieden te verbergen.

Voor stappen over hoe je een afbeelding kunt importeren voor gebruik als deeltje-textuur, zie [hier](/docs/nl-nl/projects/assets/manager#asset-import) .

### [Kleur](#kleur)[](#kleur)

De [Color](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Color)  eigenschap kleurt de textuur van elk deeltje naar een specifieke tint of naar een kleurverloop over zijn [levensduur](#levensduur) .

Scripting Studio

In een script, stel een [ColorSequence](/docs/nl-nl/reference/engine/datatypes/ColorSequence)  in voor de [Color](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Color)  eigenschap van de emitter:

```

local emitter = Instance.new("ParticleEmitter")

-- Constante kleur

emitter.Color = ColorSequence.new(Color3.fromRGB(255, 0, 40))

-- Verloopsequentie

emitter.Color = ColorSequence.new{

	ColorSequenceKeypoint.new(0, Color3.fromRGB(255, 0, 0)),

	ColorSequenceKeypoint.new(0.5, Color3.fromRGB(255, 125, 0)),

	ColorSequenceKeypoint.new(1, Color3.fromRGB(255, 200, 0))

}

```

### [Grootte](#grootte)[](#grootte)

De [Size](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Size)  eigenschap stelt de grootte van elk deeltje in op een constante grootte of op een numerieke sequentie over zijn [levensduur](#levensduur) .

Scripting Studio

In een script, stel een [NumberSequence](/docs/nl-nl/reference/engine/datatypes/NumberSequence)  in voor de [Size](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Size)  eigenschap van de emitter:

```

local emitter = Instance.new("ParticleEmitter")

-- Constante grootte

emitter.Size = NumberSequence.new(3)

-- Numerieke sequentie

emitter.Size = NumberSequence.new{

	NumberSequenceKeypoint.new(0, 1),

	NumberSequenceKeypoint.new(0.2, 4),

	NumberSequenceKeypoint.new(1, 0)

}

```

De grootte van de deeltjes kan de prestaties beïnvloeden vanwege de vulgraad. Hoe meer pixels deeltjes op het scherm van een speler innemen, hoe kostbaarder het is voor de GPU.

### [Transparantie](#transparantie)[](#transparantie)

De [Transparency](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Transparency)  eigenschap stelt de opaciteit van elk deeltje in als een constante waarde of als een opaciteitssequentie over zijn [levensduur](#levensduur) . Opaciteit kan variëren van 0  (volledig ondoorzichtig) tot 1  (volledig doorzichtig). Voor details over hoe je deeltjes kunt instellen op een specifieke opaciteit of op een nummersequentie, volg je het proces bij het aanpassen van [Grootte](#grootte)  maar gebruik je het veld van de [Transparency](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Transparency)  eigenschap van de emitter in plaats daarvan.

De [Transparency](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Transparency)  eigenschap is een van de belangrijkste eigenschappen van een deeltjesemitter. Het vervagen van deeltjes nabij het begin en/of het einde van hun levensduur voorkomt een pop-in/out effect en zorgt voor een realistischer effect.

Statische transparantie vs. vervagen in/uit

### [Levensduur](#levensduur)[](#levensduur)

De [Lifetime](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Lifetime)  eigenschap stelt de levensduur van een deeltje in seconden in. Je kunt deze eigenschap instellen als een constante waarde, of een [Min](/docs/nl-nl/reference/engine/datatypes/NumberRange#Min)  en [Max](/docs/nl-nl/reference/engine/datatypes/NumberRange#Max)  bereik opgeven waaruit een willekeurige levensduur voor elk deeltje zal worden gekozen.

Deeltjes hebben een maximale levensduur van 20 seconden. [Lifetime](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Lifetime)  waarden hoger dan dit worden intern beperkt tot 20 .

### [Snelheid](#snelheid)[](#snelheid)

De [Speed](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Speed)  eigenschap bepaalt een willekeurig bereik van snelheden (minimum tot maximum) waarmee nieuwe deeltjes worden uitgezonden, gemeten in studs per seconde. De snelheid van elk deeltje wordt gekozen bij de emissie en deze geldt in de [EmissionDirection](/docs/nl-nl/reference/engine/classes/ParticleEmitter#EmissionDirection) . Negatieve waarden zorgen ervoor dat deeltjes achteruit bewegen.

Houd er rekening mee dat het wijzigen van [Speed](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Speed)  geen invloed heeft op actieve deeltjes en dat ze de snelheid behouden die ze al hebben. Echter, [Acceleration](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Acceleration) , [Drag](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Drag) , en [VelocityInheritance](/docs/nl-nl/reference/engine/classes/ParticleEmitter#VelocityInheritance)  kunnen worden gebruikt om de snelheid van actieve deeltjes gedurende hun levensduur te beïnvloeden.

### [Frequentie](#frequentie)[](#frequentie)

De [Rate](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Rate)  eigenschap stelt het aantal deeltjes in dat per seconde wordt uitgezonden. Een enkele deeltjesemitter kan tot 400 deeltjes per seconde creëren (100 per seconde op mobiel). Voor de beste prestaties, houd de deeltjesfrequentie zo laag mogelijk en experimenteer met [grootte](#grootte)  en [andere eigenschappen](#andere-eigenschappen)  om het gewenste visuele effect te bereiken.

Het aantal deeltjes kan de prestaties beïnvloeden vanwege overtekening, vooral wanneer deeltjes overlappen. Hoe meer lagen van transparante effecten op het scherm, hoe kostbaarder het is voor de GPU.

### [Oriëntatie](#oriëntatie)[](#oriëntatie)

De [Orientation](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Orientation)  eigenschap bepaalt welke oriëntatiemodus moet worden gebruikt voor de geometrie van de deeltjes van een emitter.

| Oriëntatie | | Deeltjesgedrag |
| --- | --- |
| [FacingCamera](/docs/nl-nl/reference/engine/enums/ParticleOrientation) | | Standaard billboard quad die naar de camera kijkt; standaardgedrag. |
| [FacingCameraWorldUp](/docs/nl-nl/reference/engine/enums/ParticleOrientation) | | Deelt naar de camera, maar draait alleen op de verticale opwaartse wereld Y -as. |
| [VelocityParallel](/docs/nl-nl/reference/engine/enums/ParticleOrientation) | | Uitgelijnd parallel aan hun bewegingsrichting. |
| [VelocityPerpendicular](/docs/nl-nl/reference/engine/enums/ParticleOrientation) | | Uitgelijnd loodrecht op hun bewegingsrichting. |

Verwachte uitkomst van de oriëntatie van deeltjes

### [Lichtemissie](#lichtemissie)[](#lichtemissie)

De [LightEmission](/docs/nl-nl/reference/engine/classes/ParticleEmitter#LightEmission)  eigenschap bepaalt de menging van de kleuren van deeltjes [Texture](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Texture)  met de kleuren erachter. Een waarde van 0  gebruikt de normale mengmodus terwijl een waarde van 1  additieve menging gebruikt. Hogere waarden kunnen ervoor zorgen dat deeltjes zelfs in omgevingen met weinig licht gloeien.

### [Spreidingshoek](#spreidingshoek)[](#spreidingshoek)

De [SpreadAngle](/docs/nl-nl/reference/engine/classes/ParticleEmitter#SpreadAngle)  eigenschap heeft een X  en een Y  waarde die het bereik van hoeken bepalen waaruit een deeltje kan worden uitgezonden. Het bereik wordt berekend vanaf beide zijden rond de assen; bijvoorbeeld, een waarde van (45, 0)  zendt deeltjes uit in een bereik van 0° tot 45° weg van de [EmissionDirection](/docs/nl-nl/reference/engine/classes/ParticleEmitter#EmissionDirection)  over de X -as.

### [WindBeïnvloedtDrag](#windbeïnvloedtdrag)[](#windbeïnvloedtdrag)

Als je [globale wind](/docs/nl-nl/environment/global-wind)  in een spel hebt ingeschakeld, volgen deeltjes de globale windvector zolang de [WindAffectsDrag](/docs/nl-nl/reference/engine/classes/ParticleEmitter#WindAffectsDrag)  eigenschap van de emitter is ingeschakeld en de [Drag](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Drag)  eigenschap groter is dan 0 .

### [Vorm](#vorm)[](#vorm)

De [Shape](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Shape)  eigenschap stelt de vorm van de deeltjesemitter in op een [Box](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape) , [Sphere](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape) , [Cylinder](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape) , of [Disc](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape) .

![Emitter van Box-vorm](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Shape-Box.jpg)[Box](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape)

![Emitter van Sphere-vorm](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Shape-Sphere.jpg)[Sphere](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape)

![Emitter van Cylinder-vorm](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Shape-Cylinder.jpg)[Cylinder](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape)

![Emitter van Disc-vorm](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Shape-Disc.jpg)[Disc](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape)

Nadat je een vorm voor je deeltjesemitter hebt geselecteerd, kun je experimenteren met de [ShapeStyle](#shapestyle) , [ShapeInOut](#shapeinout) , en [ShapePartial](#shapepartial)  eigenschappen om de deeltjesemissie verder aan te passen.

Als je een deeltjesemitter aan een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  koppelt, worden de [Sphere](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape)  en [Cylinder](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape)  vormen niet correct weergegeven. Deze vormen mogen alleen worden gebruikt als de emitter aan een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  is gekoppeld.

#### [ShapeStyle](#shapestyle)[](#shapestyle)

De [ShapeStyle](/docs/nl-nl/reference/engine/classes/ParticleEmitter#ShapeStyle)  eigenschap stelt het emissietype in op:

-

[Volume](/docs/nl-nl/reference/engine/enums/ParticleEmitterShapeStyle)  — Deeltjes worden overal binnen de vorm uitgezonden.

-

[Surface](/docs/nl-nl/reference/engine/enums/ParticleEmitterShapeStyle)  — Deeltjes worden alleen van de buitenkant van de vorm uitgezonden.

![Emitter van Cylinder-vorm met Volume-vormstijl](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Cylinder-Volume.jpg)[Cylinder](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape)  + [Volume](/docs/nl-nl/reference/engine/enums/ParticleEmitterShapeStyle)

![Emitter van Cylinder-vorm met Surface-vormstijl](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Cylinder-Surface.jpg)[Cylinder](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape)  + [Surface](/docs/nl-nl/reference/engine/enums/ParticleEmitterShapeStyle)

#### [ShapeInOut](#shapeinout)[](#shapeinout)

De [ShapeInOut](/docs/nl-nl/reference/engine/classes/ParticleEmitter#ShapeInOut)  eigenschap stelt de emissie als volgt in:

-

[Inward](/docs/nl-nl/reference/engine/enums/ParticleEmitterShapeInOut)  — Deeltjes worden naar de vorm uitgezonden.

-

[Outward](/docs/nl-nl/reference/engine/enums/ParticleEmitterShapeInOut)  — Deeltjes worden van de vorm weg uitgezonden.

-

[InAndOut](/docs/nl-nl/reference/engine/enums/ParticleEmitterShapeInOut)  — Deeltjes gedragen zich willekeurig als zowel [Inward](/docs/nl-nl/reference/engine/enums/ParticleEmitterShapeInOut)  als [Outward](/docs/nl-nl/reference/engine/enums/ParticleEmitterShapeInOut) .

#### [ShapePartial](#shapepartial)[](#shapepartial)

De [ShapePartial](/docs/nl-nl/reference/engine/classes/ParticleEmitter#ShapePartial)  eigenschap is een factor die je kunt gebruiken om [Cylinder](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape) , [Disc](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape) , en [Sphere](/docs/nl-nl/reference/engine/enums/ParticleEmitterShape)  vormen verder te wijzigen.

Cylinder Disc Sphere

Voor cilinders, vermenigvuldigt [ShapePartial](/docs/nl-nl/reference/engine/classes/ParticleEmitter#ShapePartial)  de straal van de cilinder aan de kant van zijn [EmissionDirection](/docs/nl-nl/reference/engine/classes/ParticleEmitter#EmissionDirection) .

![Emitter van Cylinder-vorm met ShapePartial-waarde van 0.5](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Cylinder-ShapePartial-0.5.jpg)[ShapePartial](/docs/nl-nl/reference/engine/classes/ParticleEmitter#ShapePartial)  = 0.5

![Emitter van Cylinder-vorm met ShapePartial-waarde van 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/Cylinder-ShapePartial-0.jpg)[ShapePartial](/docs/nl-nl/reference/engine/classes/ParticleEmitter#ShapePartial)  = 0

### [Samensmelting](#samensmelting)[](#samensmelting)

De [Squash](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Squash)  eigenschap maakt niet-uniforme schaling van deeltjes mogelijk, curve-gestuurd over hun levensduur. Waarden groter dan 0  zorgen ervoor dat deeltjes zowel horizontaal krimpen als verticaal groeien, terwijl waarden kleiner dan 0  ervoor zorgen dat deeltjes zowel horizontaal groeien als verticaal krimpen. Voor details over hoe je de samensmeltingshoeveelheid kunt instellen op een constante of op een [NumberSequence](/docs/nl-nl/reference/engine/datatypes/NumberSequence) , volg je het proces bij het aanpassen van [Grootte](#grootte)  maar gebruik je het veld van de [Squash](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Squash)  eigenschap van de emitter in plaats daarvan.

Samensmelting is vooral nuttig voor regen. Het uitrekken van een deeltje maakt de textuur veel minder herkenbaar, zodat zelfs de standaard sparkle-textuur kan doorgaan als een vallende regendruppel. Voor details, zie [regen simuleren](#simuleer-regen) .

### [Flipbooks](#flipbooks)[](#flipbooks)

Deeltjes flipbook-texturen stellen je in staat om de textuur van een deeltje over zijn levensduur te animeren.

De flipbook-textuur kan een frame-indeling van 2×2, 4×4, 8×8 of aangepast hebben. Bijvoorbeeld, de volgende afbeelding van 1024×1024 heeft een 8×8-indeling, dus het is geschikt voor een 64-frame animatie.

 ![Voorbeeldtextuur voor deeltjes flipbooks](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/particle-emitter/8x8-Explosion.png)

Wanneer je een flipbook-textuur maakt, zorg ervoor dat je ruimte tussen elk van de deeltjesframes opneemt. In sommige gevallen kan mip-filtering zelfs meer ruimte vereisen. De vorige afbeelding heeft transparante ruimte rond elk frame voor de flipbook-textuur.

Functies met aangepaste texturen zoals flipbooks kosten geheugen om te renderen. Als je veel flipbooks gebruikt met andere functies die veel geheugen gebruiken, deactiveert de client automatisch flipbooks wanneer ze weinig geheugen hebben, wat waarschijnlijk is voor oudere mobiele telefoons. Om het geheugengebruik van flipbooks te verminderen, gebruik je minder unieke geanimeerde deeltjeseffecten of kies je een textuur van kleinere resolutie wanneer mogelijk. Het hergebruiken van texturen kost minder geheugen dan het gebruiken van unieke texturen.

Zodra je een geldige flipbook [textuur](#textuur)  voor de [Texture](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Texture)  eigenschap van de emitter hebt opgegeven, bepaalt de [FlipbookLayout](/docs/nl-nl/reference/engine/classes/ParticleEmitter#FlipbookLayout)  eigenschap de indeling van de textuur. Het kan elke waarde van de [Enum.ParticleFlipbookLayout](/docs/nl-nl/reference/engine/enums/ParticleFlipbookLayout)  enum zijn:

-

[None](/docs/nl-nl/reference/engine/enums/ParticleFlipbookLayout)  — Schakel flipbook-functies uit en gebruik de textuur als een enkele statische textuur over de levensduur van het deeltje.

-

[Grid2x2](/docs/nl-nl/reference/engine/enums/ParticleFlipbookLayout)  — 2×2 frames voor een 4-frame animatie.

-

[Grid4x4](/docs/nl-nl/reference/engine/enums/ParticleFlipbookLayout)  — 4×4 frames voor een 16-frame animatie.

-

[Grid8x8](/docs/nl-nl/reference/engine/enums/ParticleFlipbookLayout)  — 8×8 frames voor een 64-frame animatie.

-

[Custom](/docs/nl-nl/reference/engine/enums/ParticleFlipbookLayout)  — Een aangepaste gridgrootte gedefinieerd door [FlipbookSizeX](/docs/nl-nl/reference/engine/classes/ParticleEmitter#FlipbookSizeX)  en [FlipbookSizeY](/docs/nl-nl/reference/engine/classes/ParticleEmitter#FlipbookSizeY) .

Om het flipbookgedrag verder aan te passen, kun je de volgende eigenschappen aanpassen:

FlipbookFramerate FlipbookMode FlipbookStartRandom

De [FlipbookFramerate](/docs/nl-nl/reference/engine/classes/ParticleEmitter#FlipbookFramerate)  eigenschap bepaalt hoe snel de flipbook-textuur animeert in frames per seconde. Net als [Lifetime](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Lifetime) , kun je een minimum- en maximumbereik instellen om de framerate van het flipbook te randomiseren, met een maximum van 30 frames per seconde.

### [Andere eigenschappen](#andere-eigenschappen)[](#andere-eigenschappen)

Om deeltjes verder aan te passen, overweeg de volgende emitter-eigenschappen en klik door naar de [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  referentiepagina voor meer details.

Uiterlijk Emissie Beweging

De volgende uiterlijk-eigenschappen zijn naast [kleur](#kleur) , [lichtemissie](#lichtemissie) , [oriëntatie](#ori%C3%ABntatie) , [grootte](#grootte) , [textuur](#textuur) , [transparantie](#transparantie) , [samensmelting](#samensmelting) , en [flipbooks](#flipbooks) .

| Eigenschap | | Beschrijving |
| [LightInfluence](/docs/nl-nl/reference/engine/classes/ParticleEmitter#LightInfluence) | | Bepaalt hoeveel omgevingslicht de kleur van individuele deeltjes beïnvloedt. |
| [Brightness](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Brightness) | | Schaling van het licht dat door de emitter wordt uitgezonden wanneer [LightInfluence](/docs/nl-nl/reference/engine/classes/ParticleEmitter#LightInfluence)  0  is. |
| [ZOffset](/docs/nl-nl/reference/engine/classes/ParticleEmitter#ZOffset)   | | Bepaalt de voor-achter renderpositie van deeltjes, in studs, zonder hun grootte op het scherm te veranderen. Dit maakt het mogelijk om meerdere emitters te stapelen, of om deeltjes voor of achter het ouderobject te renderen. |

## [Simuleer regen](#simuleer-regen)[](#simuleer-regen)

Het simuleren van elke regendruppel is niet praktisch, maar deeltjesemitters kunnen een overtuigende illusie van regen in een 3D-wereld creëren:

1.

Plaats een [Part](/docs/nl-nl/reference/engine/classes/Part)  boven het gebied waar je wilt dat de regen valt. Veranker het, stel de [Transparency](/docs/nl-nl/reference/engine/classes/BasePart#Transparency)  in op 1 , en schakel [CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide)  uit.

2.

Plaats een [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  in het onderdeel en stel de [EmissionDirection](/docs/nl-nl/reference/engine/classes/ParticleEmitter#EmissionDirection)  in op [Bottom](/docs/nl-nl/reference/engine/enums/NormalId#Bottom) . Een enkele emitter kan een beperkt aantal deeltjes per seconde creëren (zie [Frequentie](#frequentie) ), dus zwaardere regen of een groter gebied vereist veel onderdelen met emitters die in een raster over het gewenste gebied zijn gerangschikt.

3.

Stel [Squash](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Squash)  in op een positieve waarde, zoals 3 , om elk deeltje in een streak te rekken. Hogere waarden maken deeltjes dunner, dus je moet mogelijk ook de [grootte](#grootte)  verhogen.

Als je [Orientation](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Orientation)  instelt op [VelocityParallel](/docs/nl-nl/reference/engine/enums/ParticleOrientation#VelocityParallel)  zodat streaks zich aligneren met hun bewegingsrichting, gebruik dan in plaats daarvan een negatieve [Squash](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Squash)  waarde.

4.

Donker [Color](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Color) , verhoog [LightInfluence](/docs/nl-nl/reference/engine/classes/ParticleEmitter#LightInfluence)  zodat de regen reageert op de verlichting eromheen, verhoog [Speed](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Speed) , en verlaag [Lifetime](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Lifetime)  zodat deeltjes nabij de grond verdwijnen.

5.

Om de regen te kantelen, stel je een kleine [Rotation](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Rotation)  in of schakel je [WindAffectsDrag](/docs/nl-nl/reference/engine/classes/ParticleEmitter#WindAffectsDrag)  in zodat deeltjes de [globale wind](/docs/nl-nl/environment/global-wind)  volgen. [Drag](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Drag)  vertraagt de val naast het toepassen van de wind, dus je moet mogelijk de neerwaartse [Acceleration](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Acceleration)  verhogen om de regen snel te laten vallen.

Om de regen die landt te tonen, plaats je transparante onderdelen op de grond met emitters waarvan de [EmissionDirection](/docs/nl-nl/reference/engine/classes/ParticleEmitter#EmissionDirection)  is [Top](/docs/nl-nl/reference/engine/enums/NormalId#Top) . Spetterdeeltjes worden niet uitgerekt zoals vallende regen, dus ze hebben meestal een aangepaste [textuur](#textuur)  en een [transparantie](#transparantie)  sequentie nodig die ervoor zorgt dat elke spetter lijkt te vervagen. Spetters zien er alleen goed uit op oppervlakken waar je ze zorgvuldig hebt geplaatst. Als je ze niet met de hand kunt plaatsen, is laaghangende mist veel vergevingsgezinder.

### [Beheer deeltjeslimieten](#beheer-deeltjeslimieten)[](#beheer-deeltjeslimieten)

Regen die een groot gebied bedekt, bereikt snel de deeltjeslimieten, en mobiele apparaten hebben veel lagere limieten dan desktops. Als deeltjes in de verte knipperen, verminder dan hoeveel er tegelijkertijd op het scherm staan:

-

Plaats de emitteronderdelen lager in de lucht en verkort [Lifetime](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Lifetime)  om overeen te komen.

-

Verlaag [Rate](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Rate)  om een stortbui in een lichtere bui te veranderen.

-

Bedek een kleiner gebied met minder emitteronderdelen.

### [Regenvoorbeelden](#regenvoorbeelden)[](#regenvoorbeelden)

-

Voor een handgemaakt voorbeeld, zie [The Mystery of Duvall Drive](/docs/nl-nl/resources/the-mystery-of-duvall-drive) . Het gebruikt emitters voor [regen, mist, spetters en water dat van luifels druppelt](/docs/nl-nl/resources/the-mystery-of-duvall-drive/develop-a-moving-world#maak-stormpuin) .

-

Voor een gescript voorbeeld, zie het [weather-island](https://github.com/Roblox/resources/tree/main/experiences/weather-island)  project. Het plant stormen, schakelt [wolken](/docs/nl-nl/environment/clouds)  en wind over, spawnt regen- en mistemitters, en voert dakdetectie uit.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
