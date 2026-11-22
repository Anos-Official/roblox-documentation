<!-- Source: https://create.roblox.com/docs/nl-nl/resources/beyond-the-dark/custom-characters -->

Aangepaste karakters | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)
4. /
5. [Beyond The Dark](/docs/nl-nl/resources/beyond-the-dark)

# Aangepaste karakters

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt aangepaste meshes importeren om alles te creëren, van NPC's tot een geanimeerd doek van een zeilboot. We hebben de aangepaste instelling van de [Importer](/docs/nl-nl/studio/importer)  gebruikt om meer exotische aangepaste karakters binnen te halen, zoals de mysterieuze zwarte gatenwezens en de vriendelijke, zij het onbewuste, service droids.

De volgende secties gaan over hoe we [rigging en skinning](/docs/nl-nl/art/modeling/rigging) , [PBR (oppervlakte-uiterlijk)](/docs/nl-nl/art/modeling/surface-appearance)  en VFX hebben gebruikt om een van onze meer gecompliceerde karakters te bouwen die we de "Creature" hebben genoemd. We wilden dat het zou gloeien, wat licht zou uitstralen, rooksporen zou achterlaten en een vloeiende beweging zou hebben die het skinnen van een rig met voldoende gewrichten vereiste om de overtuigende golven van zijn tentakels te creëren.

 ![Creature Banner](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Creature_Banner.png)

## [Rig](#rig)[](#rig)

Toen we de Creature aan het riggen waren, vonden we het het beste om het karakter in een neutrale pose te modelleren, omdat die pose het beste geschikt is om in meerdere richtingen te buigen. Als we de Creature met zijn tentakels al gekruld hadden gemodelleerd, zou dat tot rekken hebben geleid als we de tentakels in de tegenovergestelde richting zouden animeren. De volgende screenshots tonen de Creature in zijn natuurlijke staat:

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Rigging_Neutral_1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Rigging_Neutral_2.png)

Vanuit een neutrale pose hebben we gewrichten economisch toegevoegd, met de focus op de gebieden die de meeste beweging nodig hadden. Hoe minder gewrichten, hoe beter, omdat je ze moet beheren bij het skinnen van je karakter, en je hebt minder te controleren wanneer je ze animeert. In de vorige screenshots lijkt de Creature veel gewrichten in het midden te hebben, maar het hoofdlichaam heeft slechts één gewricht.

De meeste andere gewrichten bevinden zich bij de tentakels en kaken. Met de tentakels wilden we veel secundaire beweging, of beweging die gelaagd is, om een overtuigend effect te creëren dat ze allemaal op zichzelf bewegen. Echter, de centrale massa van tentakels was zo dicht bij elkaar dat het zonde voelde om gewrichten voor allemaal te maken, zowel qua prestaties als moeite om te animeren. In plaats daarvan behandelden we de centrale massa als een enkele grote tentakel met kleinere "staarten" waar de punten de centrale massa verlieten.

 ![Creature Front, Maya](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Creature_Front.png)

Het helpt soms om een "control rig" te maken die je bespaart van het handmatig animeren van elk gewricht. Je kunt zoeken naar uitstekende tutorials over control rigs die geschikt zijn voor jouw karakter en bijbehorende DCC-toepassing.

We vonden de volgende richtlijnen nuttig, zodat de karaktermesh correct in Studio wordt geïmporteerd:

-

Individuele gewrichten en botten moeten unieke namen hebben.

-

Meshes mogen niet dezelfde naam hebben als gewrichten en botten.

-

Meshes mogen geen transformaties hebben vóór het skinnen/binden; met andere woorden, transformaties moeten 0 zijn en schalen moeten 1 zijn.

-

Mesh-normals moeten naar buiten wijzen (het model mag niet binnenstebuiten lijken).

-

Skeletten mogen geen schaalfactor hebben; alle gewrichten moeten [1, 1, 1] zijn.

## [Skin](#skin)[](#skin)

Toen we het skelet van de Creature hadden voltooid, was de volgende stap om de mesh te skinnen. Skinning kan een moeizame taak zijn, dus om het gemakkelijker te maken, is het het beste om vertrouwd te zijn met de verschillende initiële skinning-instellingen van jouw DCC-toepassing om degene te vinden die je leuk vindt. Aangezien dit een organisch karakter is, hebben we het geskinnd met veel verval op elk gewricht en overlap tussen hen. Op deze manier voelt het buigen soepel en niet scherp aan. De volgende screenshots tonen respectievelijk slecht skinnen en soepel skinnen:

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Bad_Skinning_Example.png) Slecht Skinnen

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Smooth_Skinning_Example.png) Soepel Skinnen

We vonden de volgende richtlijnen het beste resultaat opleveren voor skinning:

-

Skinning-invloeden (wat betekent dat ze een deel van het model beïnvloeden wanneer ze worden verplaatst) moeten maximaal 4 invloeden per vertex zijn.

-

Gewricht- en mesh-namen moeten uniek zijn, zowel binnen elkaar als tussen elkaar.

-

Elk gewricht dat je in Studio wilt importeren, moet enige invloed hebben op de skinning van het model, anders importeert de engine het niet. Wanneer mogelijk, skin je model in zijn originele of "bind" pose.

## [Importeer de mesh naar Studio](#importeer-de-mesh-naar-studio)[](#importeer-de-mesh-naar-studio)

Het importeren van je aangepaste karakters in Studio is een van de spannendere delen van het proces, omdat je je creaties in het spel dat je aan het bouwen bent kunt zien!

Om de mesh in Studio te importeren:

1.

Exporteer het karakter vanuit de DCC-toepassing en zorg ervoor dat het volgende klopt:

-

Alle normals, schalen en namen zijn correct.

-

Het karakter heeft alle gewricht- en botstructuren en alle meshes.

-

Meshes zijn allemaal onder de 10.000 driehoeken voor elk deel van de mesh.

-

De totale grootte van de mesh is niet meer dan 2000 eenheden op een as.

-

Zie [Mesh Vereisten](/docs/nl-nl/avatar/character-bodies/specifications)  voor een complete lijst van model specificaties.

 ![Creature in DCC Tool](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Creature-In-Maya.png)

2.

In de [Importer](/docs/nl-nl/studio/importer) , importeer het aangepaste .fbx  of .obj  bestand.

 ![Creature Geïmporteerd In Studio](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Custom-Import-2.png)

## [Laat het wezen gloeien](#laat-het-wezen-gloeien)[](#laat-het-wezen-gloeien)

Zodra het model van de Creature stabiel was en geen verdere onmiddellijke import in Studio vereiste, begonnen we met het samenstellen van de SurfaceAppearance-objecten, lichten en visuele effecten. We deden dit om ervoor te zorgen dat de kwaliteit van het model goed genoeg was voordat we verder gingen met het plaatsen en bewerken van een aspect ervan.

 ![Glowing Creature Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Glowing-Creature.png)

We wisten dat we wilden dat de Creature donker was, en de brandpunten moesten de ogen en zijn "grijpende" tentakels zijn. Hoge contrastpunten trekken vaak de aandacht, dus het hebben van een paar sterke zorgt ervoor dat de kijker weet waar hij op moet focussen. Studio ondersteunt neonmaterialen die zelfverlichtend zijn, dus in het begin hebben we de ogen gescheiden zodat ze hun eigen materiaal konden zijn van de rest van het karakter. We deden iets soortgelijks voor de tentakels, zodat ze alleen aan de punten zouden gloeien.

 ![Creature Ogen in Studio](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Creature-Eyes.jpeg)

Neonmateriaal straalt geen echt licht uit, dus na wat testen hebben we aparte delen toegevoegd om de plaatsing en richting van de lichtuitstraling te regelen. Dit zorgde ervoor dat de verlichting op een manier werd gericht die de gloed van de ogen versterkte en ook zijn eigen lichtbron projecteerde.

 ![Punt Licht in Studio](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Light-Emission.jpeg)

Let op dat de SpotLights  visuele flair aan de Creature toevoegen in de buurt van andere oppervlakken of een speler.

 ![Creature Licht Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Spotlights.png)

Daarnaast wilden we dat de tentakels van de Creature wat deeltjes zouden uitstralen, zodat het een rookspoor achterliet wanneer het bewoog. Omdat de tentakels erg lang zijn, zou het toevoegen van de [ParticleEmitter](/docs/nl-nl/reference/engine/classes/ParticleEmitter)  aan de hele tentakel ervoor zorgen dat de deeltjes van de hele tentakel in plaats van de punt zouden uitstralen. Om dit te bestrijden, gebruikten we een klein deel dat dicht bij het einde van de tentakel was gepositioneerd, zodat we de emissiegrootte, plaatsing en richting van de deeltjes konden regelen.

 ![Deeltje Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Particle-Emitter.jpeg)

## [Laat de VFX het karakter volgen](#laat-de-vfx-het-karakter-volgen)[](#laat-de-vfx-het-karakter-volgen)

De meshposities van het geskinnde karakter worden niet bijgewerkt wanneer de Creature animeert, dus we hadden een methode nodig om ervoor te zorgen dat de VFX, SFX en lichten allemaal de Creature goed volgden. Om dit te bereiken, hebben we een VFX-controller-script gemaakt en CollectionService gebruikt om de delen die de VFX bevatten te informeren waar de botten van de Creature waren en om ze te volgen.

1.

We plaatsten de volgende [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  in StarterPlayer  → StarterPlayerScripts . Dit voert in wezen de VFX-updatefunctie uit.

Local Script

```

-- Voeg deze snippet toe aan een bestaand lokaal script dat PreSimulation

-- verbindingen maakt

local RunService = game:GetService("RunService")

local vfx = require(workspace.VfxUpdateModule)

RunService.PreSimulation:Connect(vfx.updateVfx)

```

Module Script

```

-- Dit module voegt delen aan animaties toe zodat ze worden bijgewerkt terwijl de

-- animatie speelt. Het is een workaround voor de huidige beperkingen

-- met gewrichten en botten en zal niet altijd nodig zijn.

--

-- Voorwaarden:

-- Om opgenomen te worden, moeten modellen de tag "AnimatedVfxModel" hebben, en een map

-- van alle delen die je wilt synchroniseren met animatie. Elk deel moet

-- een attribuut hebben genaamd "AttachedBoneName" dat verwijst naar de naam van het

-- bot dat je wilt bevestigen. Delen moeten ook al in hun

-- juiste posities zijn ten opzichte van het gewenste bot.

--

-- Gebruik:

-- Een LocalScript moet deze module vereisen, en vervolgens

-- VfxUpdateModule.updateVfx verbinden met het RunService.PreSimulation-evenement.

local VfxUpdateModule = {}

local CollectionService = game:GetService("CollectionService")

-- SETUP - dit moet één keer op elke client worden uitgevoerd.

-- Verzamel alle modellen met de tag

local vfxModels = CollectionService:GetTagged("AnimatedVfxModel")

local vfxTable = {} -- waar we alle delen en offsets zullen opslaan

-- Wijs een tabel toe aan elk model die alle vfx-delen en offset zal bevatten

for _, model in vfxModels do

 vfxTable[model] = {}

 local vfxParts = model:FindFirstChild("VFX"):GetChildren() -- Vind de VFX-map

 -- Vind het bot via attribuut en bereken de offset voor elk deel.

 for _,part in vfxParts do

   local name = part:GetAttribute("AttachedBoneName")

   local bone = model:FindFirstChild(name, true)

   if bone then

     local offset = (bone.TransformedWorldCFrame:inverse() * part.CFrame)

     vfxTable[model][part] = {bone, offset}

   else

     warn("Vfx-deel verwijst naar bot dat niet kon worden gevonden.")

   end

 end

end

print(vfxTable)

-- UPDATE - Dit moet worden gekoppeld aan elke client's RunService.PreSimulation

-- Loop door alle modellen, en update dan alle delen op het model om overeen te komen met de botcframe.

function VfxUpdateModule.updateVfx()

 for model, vfxParts in vfxTable do

   for part, bone in vfxParts do

     part.CFrame = bone[1].TransformedWorldCFrame * bone[2]

   end

 end

end

return VfxUpdateModule

```

2.

We hebben een VFXUpdateModule  [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  gemaakt om te vertellen dat alle objecten die correct zijn getagd met AnimatedVfxModel  moeten worden bijgewerkt bij een speelevenement.

3.

We hebben de noodzakelijke modelgroepen getagd met AnimatedVfxModel  met behulp van de [Tags](/docs/nl-nl/studio/properties#instantie-tags)  sectie van hun eigenschappen. Het gebruik van tags stelt de VFXUpdateModule  in staat om te weten welk object als eerste VFX-kind moet worden gezocht en om de update toe te passen.

 ![VFX In Studio Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/In-Studio-VFX.jpeg)

4.

Ten slotte hebben we een AttachedBoneName  aangepast attribuut toegevoegd aan het deel dat we wilden animeren en de precieze naam van het gewricht toegevoegd dat we wilden dat het volgde.

## [Textuur het wezen](#textuur-het-wezen)[](#textuur-het-wezen)

Vervolgens hebben we de PBR (Physically Based Rendered) textuurkaarten ingesteld. Deze krachtige bitmaps geven het wezen de gevarieerde glans en oppervlaktevariaties om het eruit te laten zien alsof het veel kleine bultjes en imperfecties heeft. Dit visuele effect helpt de uitstraling van de Creature te verkopen wanneer deze dichter bij de speler is.

 ![Creature Texturering Vergelijking](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Surface-Appearance.png)

Hier is hoe we de oppervlakte-uiterlijk textuurkaarten hebben gemaakt:

1.

De textuurkaarten voor dit karakter stonden allemaal op één "blad" per kaart. Dit maakte de Creature efficiënter en betekende dat we met minder textuurkaarten of [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  objecten moesten omgaan.

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Texture-Map-1.jpeg)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Texture-Map-2.jpeg)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Texture-Map-3.jpeg)

![](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Texture-Map-4.jpeg)

2.

Voor gebieden die moesten gloeien of zelfverlichtend moesten zijn, zoals de "grijpende tentakels," hebben we ook transparantie op de [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  gebruikt om met die delen te mengen.

 ![Illuminatie Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Surface-Appearance-Transparency.jpeg)

We vonden het nuttig om deze richtlijnen te volgen bij het maken van oppervlakte-uiterlijk textuurkaarten:

-

Zorg ervoor dat je kaarten niet groter zijn dan 1024×1024.

-

Je groene kanaal moet mogelijk worden omgekeerd, afhankelijk van de toepassing waarin je hebt gewerkt.

## [Animeer het wezen](#animeer-het-wezen)[](#animeer-het-wezen)

Animeren is zeer subjectief en heeft een persoonlijke stijl. Opties zijn onder andere motion capture, handmatig "key frame" animeren in je DCC-toepassing, of het gebruik van Studio's krachtige Animatie-editor .

Zoals we eerder hebben vermeld, wilden we ervoor zorgen dat we voldoende gewrichten hadden voor vloeiende bewegingen, evenals voldoende ledematen, zodat de animatie van het wezen natuurlijk en "gelaagd" aanvoelde. Layering, ook wel bekend als secundaire beweging, is iets dat je in het dagelijks leven ziet — wanneer je je arm uitgooit, reageert elk gewricht op de initiële impuls van je bovenarm, en elk gewricht in je lichaam beweegt of rust niet tegelijkertijd.

We hebben deze techniek gebruikt om de Creature te animeren zodat het voelde alsof de ledematen reageerden op de beweging die door zijn lichaam werd aangedreven, zoals hier te zien is:

 ![Creature Animatie Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Animation-Example.gif)

Als je een externe DCC-toepassing voor animatie gebruikt, hebben we de volgende richtlijnen gevonden die het beste werken:

-

Stel de framerates in op ten minste 30 FPS.

-

Maak je animaties met hetzelfde karakter waarop je het toepast.

-

Exporteer je animatiegegevens als een apart .fbx  bestand.

Omdat we het karakter buiten Studio hebben geanimeerd, moesten we de Animatie-editor  gebruiken om het animatie .fbx  bestand te importeren. De editor laat je elk avatar met gewrichten of motoren selecteren en deze aansturen via punten in de tijdlijn.

Om een animatie te importeren:

1.

Klik in het Avatar  tabblad van de werkbalk op Clip Editor .

2.

Selecteer het gerigde karakter dat je in Roblox wilt animeren. Het karakter moet hetzelfde zijn als degene die je in je externe DCC-toepassing aan het riggen bent.

3.

Klik op de ⋯  knop in de linkerbovenhoek van het editorvenster, selecteer Import From FBX Animation , en zoek je geëxporteerde .fbx  animatiebestand.

 ![Animatie Import Voorbeeld 2](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Animation-Import-2.png)

Als je hebt geanimeerd met een andere framerate dan 30 FPS, kun je een waarschuwing krijgen over uitlijningsproblemen. Dit komt omdat de keyframes bij verschillende framerates niet zullen uitlijnen met de frame telling in Studio. Je kunt keys genereren op die tijdstippen, of het negeren. Hoe dan ook, je kunt exporteren, maar uitlijnen geeft je betere controle over het bewerken van de frames in Studio.

4.

Wanneer je tevreden bent met je animatie, kun je deze exporteren om de animatie-ID te ontdekken, die je vervolgens in Roblox-scripts kunt gebruiken om ze uit te voeren. Bijvoorbeeld, je kunt een [Script](/docs/nl-nl/reference/engine/classes/Script)  aan de modelgroep van het geïmporteerde karakter toevoegen en de volgende code gebruiken om de animatie uit te voeren:

 ![Animatie Script Voorbeeld](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Script-Example.jpeg)

```

local animationId = "YOUR_ANIMATION_ID"

local char = script.Parent

local animController = char:FindFirstChildWhichIsA("Humanoid") or char:FindFirstChildOfClass("AnimationController")

local animation = Instance.new("Animation")

animation.AnimationId = "rbxassetid://" .. tostring(animationId)

local animTrack = animController:LoadAnimation(animation)

animTrack:Play(0, 1, 1)

```

Controleer het karakter nadat je de Animatie-editor  hebt gesloten om ervoor te zorgen dat de AnimSaves  map is verwijderd, aangezien de bestanden alleen nuttig zijn tijdens het bewerken.

## [Eindresultaten](#eindresultaten)[](#eindresultaten)

Na een paar laatste aanpassingen aan kleuren, lichthelderheden en nog wat deeltjeseffecten om het een sterker halo-effect voor ramen te geven, is hier het eindresultaat in het ruimtestation!

 ![Eind Creature Rendering](https://prod.docsiteassets.roblox.com/assets/resources/beyond-the-dark/custom-characters/Final-Result.png)

[Volgende](/docs/nl-nl/resources/beyond-the-dark/layered-clothing)[Vorige](/docs/nl-nl/resources/beyond-the-dark/building-architecture)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
