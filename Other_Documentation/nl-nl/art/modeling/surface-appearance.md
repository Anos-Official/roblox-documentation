<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/surface-appearance -->

PBR-texturen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Textureren

# PBR-texturen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Fysiek-gebaseerde weergave  (PBR) texturen stellen je in staat om realistische schaduwen en verlichting weer te geven door meerdere soorten textuurafbeeldingen, of kaarten , op een enkel object te gebruiken. Het combineren van meerdere textuurkaarten kan kleur, ruwheid en reflectiviteit nauwkeuriger simuleren in elke verlichtingsomgeving en kan de visuele elementen van je activa en omgeving verbeteren.

Kleding Omgeving

![Een humanoïde avatar met dreadlocks, een glanzende jas, jeans met decals en laarzen.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Layered-Clothing-Example.png)

![Een humanoïde avatar met een kort kapsel, leren jas, capri-broek en oranje schoenen.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Layered-Clothing-Example-2.jpg)

Er zijn verschillende toepassingen en workflows beschikbaar voor het maken van PBR-texturen. Je kunt deze gebruiken tijdens de modellering en texturering van aangepaste 3D-objecten, op voorwaarde dat Roblox Studio [de specifieke textuurkaarten ondersteunt](/docs/nl-nl/avatar/character-bodies/specifications#texturen)  die je gebruikt.

Voor informatie over hoe je PBR-texturen correct aan je model in Blender en Maya kunt koppelen voor import in Studio, zie [Blender / Maya textuurinstellingen](/docs/nl-nl/art/modeling/assign-textures) .

Deze gids biedt instructies over [het instellen](#surface-appearance-inschakelen)  van je mesh-objecten om PBR-textuurkaarten te gebruiken en beschrijft veelvoorkomende gebruikssituaties en best practices voor de door Roblox ondersteunde PBR [textuurkaarten](#textuurkaarten) . Wanneer je je eigen oppervlakken maakt, zie [materiaalreferenties](/docs/nl-nl/art/modeling/material-reference)  voor veelvoorkomende materiaalwaarden, afbeeldingsvergelijkingen en kledingvoorbeelden.

## [Surface appearance inschakelen](#surface-appearance-inschakelen)[](#surface-appearance-inschakelen)

Je kunt PBR-texturen toevoegen aan elke [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  door een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object toe te voegen dat de oorspronkelijk toegewezen textuur overschrijft. In het algemeen kun je [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) -eigenschappen niet wijzigen via scripts tijdens een spel, omdat de engine enige preprocessing vereist om deze graphics weer te geven. Net als bij het toevoegen van een basis textuur, moet elke textuurafbeeldingskaart naar de juiste geüploade afbeeldingsasset-ID verwijzen.

Om de surface appearance voor een [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  in te schakelen:

1.

In het Explorer -venster, beweeg de muis over de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  en klik op de ⊕ knop.

2.

Voeg een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  toe vanuit het contextmenu.

 ![Een SurfaceAppearance-object dat binnen een MeshPart in het Explorer-venster van Studio is geplaatst.](https://prod.docsiteassets.roblox.com/assets/studio/explorer/MeshPart-SurfaceAppearance.png)

Wanneer je klaar bent om textuurkaarten aan het [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) -object toe te voegen, kun je op elke kaart-eigenschap in het Eigenschappen -venster klikken en een asset-ID invoeren.

## [Textuurkaarten](#textuurkaarten)[](#textuurkaarten)

Studio ondersteunt momenteel 5 soorten PBR-textuurkaarten: [kleur](#kleur-albedo) , [normaal](#normaal) , [ruwheid](#ruwheid) , [metaalheid](#metaalheid)  en [emissief](#emissief-masker) . Elke van deze kaarten komt overeen met een belangrijk aspect van het uiterlijk van het objectoppervlak. Textuurkaarten veranderen alleen het visuele uiterlijk en hebben geen invloed op de geometrie van het [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) -object.

Vermijd het aanpassen van materiaalwaarden om er beter uit te zien in één specifieke verlichtingssituatie. Je moet je materiaalwaarden baseren op de fysieke kenmerken en testen en itereren om een resultaat te bereiken dat visueel nauwkeurig blijft in verschillende verlichtingsomgevingen.

Zie de volgende voorbeelden voor een overzicht van de door Roblox ondersteunde textuurkaarten en aanvullende bronnen:

Kleur Normaal Ruwheid Metaalheid Emissieve Masker

De [ColorMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#ColorMap)  eigenschap stelt de kleurgegevens van het oppervlak in, inclusief eventuele transparantie die in de kaart aanwezig is. Zie [kleur (albedo)](#kleur-albedo)  voor aanvullende informatie.

![Een volledig gevulde afbeelding, voornamelijk rood met verschillende zwarte vlekken en witte krassen.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-ColorMap.jpg) Voorbeeldkaart

![Een lege witte bol met een donkere achtergrond.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-ColorMap-Before.jpg) Voorbeeldmesh

![Een rode bol met zwarte vlekken en witte krassen met een donkere achtergrond.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-ColorMap-After.jpg) Mesh en textuur

Voor technische details over de vereisten voor textuurbestanden, zie [textuurvereisten](/docs/nl-nl/art/modeling/texture-specifications) .

### [Kleur (albedo)](#kleur-albedo)[](#kleur-albedo)

De kleur , of albedo , kaart bepaalt de kleur van je textuur en bestaat voornamelijk uit kleurinformatie met weinig tot geen verlichting of textuurinformatie. Voor aanvullende aanpassing kun je ook [transparantie](#alpha-modi)  aan je albedo-textuur toevoegen door opaciteit aan je afbeeldingskaart toe te voegen.

Hoewel albedo-kaarten en generieke [niet-PBR textuurkaarten](/docs/nl-nl/parts/textures-decals) , vaak bekend als diffuse kaarten , zeer vergelijkbare basis kleurgegevens voor een oppervlak bevatten, bevatten diffuse kaarten vaak schaduw- en verlichtingswaarden om een specifiek visueel element na te bootsen dat effectiever wordt behandeld door PBR's [normaal](#normaal) , [ruwheid](#ruwheid)  en [metaalheid](#metaalheid)  kaarten. Het gebruik van een typische diffuse kaart in plaats van een albedo-kaart kan er vaak verkeerd uitzien wanneer de verlichting niet overeenkomt met deze toegevoegde ingebakken textuurelementen.

#### [Alpha-modi](#alpha-modi)[](#alpha-modi)

Voor objecten die gedeeltelijke of volledige transparante secties vereisen, zoals gras, bladeren, kant of decals zoals vuil of grunge, kun je verschillende alpha-modi  gebruiken om transparantie op je kleurkaart toe te passen. Als je afbeeldingsformaat voor de kleurkaart alpha-kanalen ondersteunt, kun je een grijswaarden alpha-kaart toepassen waarbij 0.0  transparant is en 1.0  ondoorzichtig. Evenzo, wanneer je een afbeeldingsformaat zoals een .png  gebruikt, wordt elke opaciteit op de kleurkaart toegepast als transparantie op het asset.

Je kunt transparantie op twee verschillende manieren toepassen door de volgende [AlphaMode](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#AlphaMode)  waarden in te stellen:

-

[Opaque](#opaque)  — Negeert het alpha-kanaal van de [ColorMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#ColorMap)  en gebruikt de kleurwaarde rechtstreeks van de kleurkaart.

-

[Overlay](#overlay)  — Overlayt de [ColorMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#ColorMap)  over de onderliggende kleur van de mesh [MeshPart.Color](/docs/nl-nl/reference/engine/classes/MeshPart#Color) . Kleurkaarten die de overlay-modus gebruiken onthullen de basiskleur van de mesh waar transparantie aanwezig is. Dit is de standaardinstelling.

-

[Transparantie](#alpha-modi)  — Verwijdert de zichtbare mesh op basis van transparantie in de ColorMap . Dit maakt de mesh doorzichtig en onthult niet de oorspronkelijke kleur van de mesh wanneer transparantie aanwezig is.

-

[Tintmasker](#tintmasker)  — Mengt de getinte [ColorMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#ColorMap)  over de ongekleurde [ColorMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#ColorMap) .

##### [Opaque](#opaque)[](#opaque)

Deze modus is momenteel in bèta. Schakel het in via Bestand  ⟩ Bèta-functies  ⟩ MaterialVariant Alpha Mode .

Je kunt de [Enum.AlphaMode.Opaque](/docs/nl-nl/reference/engine/enums/AlphaMode#Opaque)  modus gebruiken om het alpha-kanaal van de [ColorMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#ColorMap)  volledig te negeren. In dit geval wordt de alpha-waarde verondersteld 1 (volledig ondoorzichtig) te zijn.

Het volgende voorbeeld demonstreert hoe de [Opaque](/docs/nl-nl/reference/engine/enums/AlphaMode#Opaque)  modus werkt met een blauwe object als referentie:

![Een stippen textuur met transparantie. De achtergrond is volledig transparant.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Opaque-ColorMap.png) Kleur/albedo kaart met transparantie

![Een blauwe bol op een vlak.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Opaque-Before.jpg) Voorbeeldmesh-object

![De bol heeft de stippenpatronen verspreid over zijn oppervlak. De transparantiewaarde wordt genegeerd.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-Opaque-After.jpg)[AlphaMode](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#AlphaMode)  ingesteld op [Opaque](/docs/nl-nl/reference/engine/enums/AlphaMode#Opaque)

##### [Overlay](#overlay)[](#overlay)

Je kunt [Enum.AlphaMode.Overlay](/docs/nl-nl/reference/engine/enums/AlphaMode#Overlay)  gebruiken om secties van de oorspronkelijke kleur van de mesh te onthullen. Aangezien de transparante gebieden van de kleurkaart de onderliggende kleur blootleggen, kun je een unieke textuurkaart ontwerpen die gedeeltelijk of volledig de [Color](/docs/nl-nl/reference/engine/classes/MeshPart#Color)  eigenschap van de mesh onthult voor aangepaste huidskleuren of andere situaties met unieke kleuren.

Het volgende voorbeeld demonstreert hoe de [Overlay](/docs/nl-nl/reference/engine/enums/AlphaMode#Overlay)  modus werkt met een lichtblauwe bol als referentie:

![Een volledig gevulde afbeelding van een semi-herhalend patroon met kleine lichtblauwe vierkanten. De achtergrond is geblokt om transparantie aan te geven.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-AlphaMode-ColorMap.png) Kleur/albedo kaart met transparantie

![Een lege cyaan bol op een donkere achtergrond.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-ColorMap-Before.jpg) Voorbeeldmesh-object

![Een witte bol met kleine blauwe vierkanten verspreid over het oppervlak.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-AlphaMode-Overlay.jpg)[AlphaMode](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#AlphaMode)  ingesteld op [Overlay](/docs/nl-nl/reference/engine/enums/AlphaMode#Overlay)

Het volgende voorbeeld gebruikt de [Overlay](/docs/nl-nl/reference/engine/enums/AlphaMode#Overlay)  modus voor aangepaste karakters, waarbij de oorspronkelijke huidskleur van het karakter wordt onthuld:

![Een volledig gevulde afbeelding van een textuurkaart voor een 3D-humanoïde model. Verschillende delen van de afbeelding zijn geblokt of gedeeltelijk geblokt om verschillende niveaus van transparantie aan te geven.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Custom-Skin-Tone-Map.png) Kleurkaart met transparantie in secties om de oorspronkelijke kleur van de mesh bloot te leggen

![Vier van dezelfde humanoïde modellen met verschillende huidskleuren: lichtbruin, zwart, wit, donkergroen.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Custom-Skin-Tone-Example.png) Verschillende variaties van karakters met een enkele kleurkaart die de [Overlay](/docs/nl-nl/reference/engine/enums/AlphaMode#Overlay)  modus gebruikt

Zie [aangepaste huidskleur](/docs/nl-nl/avatar/character-bodies/specifications#aangepaste-huidskleur)  voor aanvullende details over het optimaliseren van een overlay voor huid en soortgelijke toepassingen.

##### [Transparantie](#transparantie)[](#transparantie)

Je kunt de [Enum.AlphaMode.Transparency](/docs/nl-nl/reference/engine/enums/AlphaMode#Transparency)  modus gebruiken om complexe of extreem fijne objecten, zoals kant of net, te creëren door zichtbare delen van de mesh te verwijderen als alternatief voor het sculpturen van de mesh-geometrie. Aangezien dit geen invloed heeft op de geometrie van het mesh-object, kan dit je in staat stellen om gedetailleerde objecten te creëren zonder de prestatie-impact van een ingewikkeld mesh-model.

Het volgende voorbeeld demonstreert hoe een gedeeltelijke en volledige transparantie in deze modus visueel secties van de mesh verwijdert:

Voorbeeld Meshes Afbeeldingskaarten

![Een bol met een mandachtige oppervlakte.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Opacity-0.png) Geen transparantie

![Een bol met reguliere driehoekige patronen op zijn oppervlak gedeeltelijk onzichtbaar.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Opacity-Half.png) Half transparantie in secties

![Een bol met reguliere driehoekige patronen op zijn oppervlak volledig onzichtbaar.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Opacity-1.png) Volledige transparantie in secties

Er zijn twee uitkomsten van de [Transparency](/docs/nl-nl/reference/engine/enums/AlphaMode#Transparency)  modus, afhankelijk van of de [MeshPart.Transparency](/docs/nl-nl/reference/engine/classes/MeshPart#Transparency)  is ingesteld op 0  of minimaal  0.02 , hoewel numerieke precisie kan resulteren in kleine waarden zoals 0.01  die de ondoorzichtige transparantie activeren.

-

Wanneer alpha wordt gebruikt om de vorm van voornamelijk ondoorzichtige objecten met scherpe randen zoals loof, kantstof en netten uit te snijden, stel je de [MeshPart.Transparency](/docs/nl-nl/reference/engine/classes/MeshPart#Transparency)  in op 0 . Wanneer delen van het oppervlak volledig ondoorzichtig zijn, kan de Roblox-engine ze renderen met de juiste diepte-gebaseerde occlusie. Ondoorzichtige oppervlakken werken ook over het algemeen beter met diepte-gebaseerde effecten zoals [DepthOfFieldEffect](/docs/nl-nl/reference/engine/classes/DepthOfFieldEffect) , glas- en waterbreking, en waterreflectie.

-

Wanneer alpha wordt gebruikt om detail toe te voegen aan semi-transparante objecten of objecten met gladde overgangen van transparantie, stel je de [MeshPart.Transparency](/docs/nl-nl/reference/engine/classes/MeshPart#Transparency)  in op minimaal  0.02 . Dit verbetert de kwaliteit van de menging voor objecten zoals vuile ramen en zachtgezoomde veren, maar het werkt mogelijk niet met alle effecten.

##### [Tintmasker](#tintmasker)[](#tintmasker)

Je kunt de [Enum.AlphaMode.TintMask](/docs/nl-nl/reference/engine/enums/AlphaMode#TintMask)  modus gebruiken om [SurfaceAppearance.Color](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#Color)  tinting toe te passen op selectieve gebieden van een oppervlak. De tinting is het sterkst waar het alpha-kanaal volledig zichtbaar is en niet toegepast waar het alpha-kanaal transparant is.

ColorMap RGB ColorMap Alpha Voorbeeldresultaten

![Een warme, lichtgekleurde baksteen textuur met donkergrijze textuurvoegen tussen de stenen.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-AlphaMode-TintMask-Bricks-Albedo.jpg)

Voorbeeld baksteen textuur, die de kleurdetails op de bakstenen gezichten toont evenals in de voegen tussen de stenen.

Bij het maken van [SurfaceAppearance.ColorMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#ColorMap)  texturen voor gebruik met een tintmasker, behoud kleur in de transparante gebieden en zet opties zoals voorvermenigvuldigde alpha uit die de kleur in transparante gebieden verduisteren. De alpha-waarden kunnen ook semi-transparant zijn om een gedeeltelijke tint op gebieden van de textuur toe te passen.

#### [Kleur tinting](#kleur-tinting)[](#kleur-tinting)

Je kunt een tint aan je kleurkaart toepassen door de [SurfaceAppearance.Color](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#Color)  eigenschap te wijzigen. Tinting heeft geen invloed op de prestaties en je kunt geheugen besparen door een enkele kleurkaart met verschillende tinten opnieuw te gebruiken. Gebruik kleur tinting om extra goedkope variatie te creëren tussen je [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  PBR-texturen of om je PBR-oppervlaktekleuren in realtime programmatisch te wijzigen.

![Een standbeeld met een standaard gele tint en reflecterende jade-achtige eigenschappen.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Tinting-None.png) Standbeeld mesh van [The Mystery of Duvall Drive](/docs/nl-nl/resources/the-mystery-of-duvall-drive)  zonder tinting.

![Een standbeeld met een rode tint en blijft glanzende reflecterende eigenschappen behouden van zijn andere textuurkaarten.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Tinting-Red.png) Standbeeld mesh met [Color](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#Color)  ingesteld op rood.

![Een standbeeld met een groene tint en blijft glanzende reflecterende eigenschappen behouden van zijn andere textuurkaarten.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Tinting-Green.png) Standbeeld mesh met [Color](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#Color)  ingesteld op groen.

[SurfaceAppearance.Color](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#Color)  tinting wordt toegepast als een vermenigvuldiger, dus het uiteindelijke uiterlijk is een functie van [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  (texel kleur) keer [SurfaceAppearance.Color](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#Color) . Dit betekent dat het maken van je oorspronkelijke [SurfaceAppearance.ColorMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#ColorMap)  in bijna-witte grijswaarden kleuren het sterkste tintingseffect creëert wanneer deze eigenschap wordt toegepast.

Tinting geldt alleen voor de [SurfaceAppearance.ColorMap](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#ColorMap)  en niet voor de [MeshPart.Color](/docs/nl-nl/reference/engine/classes/MeshPart#Color) . Je kunt alpha-kanalen blijven gebruiken bij het toepassen van [transparantie](#transparantie) .

Wanneer [SurfaceAppearance.AlphaMode](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#AlphaMode)  is ingesteld op [Overlay](/docs/nl-nl/reference/engine/enums/AlphaMode)  en een alpha-kanaal aanwezig is, wordt de onderliggende [MeshPart.Color](/docs/nl-nl/reference/engine/classes/MeshPart#Color)  onthuld en geldt de [SurfaceAppearance.Color](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#Color)  tinting alleen voor de zichtbare [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  kleurkaart.

Wanneer [SurfaceAppearance.AlphaMode](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#AlphaMode)  is ingesteld op [TintMask](/docs/nl-nl/reference/engine/enums/AlphaMode)  en een alpha-kanaal aanwezig is, controleert het alpha-kanaal de hoeveelheid [SurfaceAppearance.Color](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#Color)  tinting. De tinting is het sterkst waar het alpha-kanaal volledig zichtbaar is en niet toegepast waar het alpha-kanaal transparant is.

Transparantie AlphaMode Overlay AlphaMode TintMask AlphaMode

![Een zwevende vierkante plaat met een cyaan leisteen textuur, die geleidelijk verandert van volledig transparant aan de linkerkant naar volledig ondoorzichtig aan de rechterkant. Een dunne horizontale balk onder de zwevende plaat heeft een verloop met zwart aan de linkerkant en wit aan de rechterkant.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/SurfaceAppearance-AlphaMode-Gradient-Transparency.jpg)

[AlphaMode](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#AlphaMode)  ingesteld op [Transparency](/docs/nl-nl/reference/engine/enums/AlphaMode) . De grijswaarden verloopbalk onderaan geeft de alpha-waarde aan. [MeshPart.Color](/docs/nl-nl/reference/engine/classes/MeshPart#Color)  is ingesteld op rood en [SurfaceAppearance.Color](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#Color)  is ingesteld op cyaan.

### [Normaal](#normaal)[](#normaal)

De normaal , of oppervlak , kaart voegt textuurdiepte toe aan je oppervlak en gedraagt zich vergelijkbaar met een [hoogtekaart](/docs/nl-nl/parts/terrain#heightmaps) . Als gevolg hiervan kan het effect vervagen of intensiveren, afhankelijk van de kijkhoek en verlichtingsomgeving.

In de volgende figuur kun je schakelen tussen de mesh-referentie en de kaartreferentie voor vergelijkingen van normaal kaartwaarden:

Voorbeeld Meshes Afbeeldingskaarten

![Een kleikleurige gladde bol.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Normal-0.png)

![Een kleikleurige bol met een gematigd rotsachtig oppervlak.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Normal-Half.png)

![Een kleikleurige bol met een extreem rotsachtig oppervlak](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Normal-1.png)

De R , G  en B  kanalen van de afbeelding komen respectievelijk overeen met de X , Y  en Z  componenten van de lokale oppervlakvector. Een uniforme afbeelding van kleur [127, 127, 255]  vertaalt naar een volledig vlakke normaal kaart. Roblox ondersteunt alleen OpenGL-formaat - Tangent Space  normaal kaarten.

Normaal kaarten beïnvloeden prominent het visuele oppervlak van een mesh en kunnen ongemakkelijke naden in je textuur accentueren. Wanneer mogelijk, houd je textuurnaden verborgen om visuele problemen met je mesh te voorkomen.

### [Ruwheid](#ruwheid)[](#ruwheid)

Ruwheid , of microsurface , kaarten bepalen hoe licht over het oppervlak van je model wordt verspreid. Wanneer de ruwheid op 0% staat, verspreidt het oppervlak helemaal geen licht, wat resulteert in een veel scherpere en helderdere reflectie en glans op je materiaal. Bij 100% verspreidt licht en reflecties zich gelijkmatig over het model, wat resulteert in een minder reflectief matachtig oppervlak.

De volgende figuur toont vergelijkingen van verschillende ruwheid kaartwaarden:

![Een blauwe glanzende bol.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Roughness-0.png) 0%

![Een blauwe semi-glanzende bol.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Roughness-Half.png) 50%

![Een blauwe matte bol.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Roughness-1.png) 100%

Ruwheid kan van invloed zijn op hoe reflectief een object is vanuit verschillende hoeken, wat de Fresnel -effect wordt genoemd. De fresnelverwerking van Studio streeft naar fysieke nauwkeurigheid in de echte wereld, hoewel je mogelijk onverwachte speculaire bijdragen kunt krijgen onder bepaalde hoeken, zelfs met ruwe oppervlakken. In sommige gevallen kun je compenseren door je ruwheid kaartwaarde met ongeveer 0.1  ruwer te verhogen om een consistente lichtrespons met je materialen te bereiken.

Hoewel Roblox dit lichteffect nauwkeurig weergeeft, reageert de helderheid en reflectiviteit van een oppervlak mogelijk niet consistent tussen je textuurinhoudcreatiesoftware, zoals Substance Painter, en Studio. Zie [kledingvoorbeelden](/docs/nl-nl/art/modeling/material-reference#kledingvoorbeelden)  voor verschillen in rendering tussen toepassingen.

Verschillende combinaties van de ruwheid en metaalheid kunnen bijna elk mogelijk echt materiaaloppervlak vertegenwoordigen. Zie [materiaalreferenties](/docs/nl-nl/art/modeling/material-reference)  voor voorbeelden en referenties van hoe combinaties van materiaalwaarden verschillende oppervlaktes kunnen creëren.

### [Metaalheid](#metaalheid)[](#metaalheid)

Metaalheid  bepaalt de reflectiviteit van een oppervlak. In de meeste gevallen moet je deze waarde instellen op ofwel 0% (niet-metaal) of 100% (metaal), hoewel je gedeeltelijke metaalheidwaarden kunt gebruiken bij het creëren van oppervlakken met gematigde reflectieve eigenschappen zoals satijn of zijde. Deze praktijk kan subtiel de reflecties in het materiaal faken om de kleur van de [kleur/albedo kaart](#kleur-albedo)  te benadrukken boven kleuren die in de omgeving worden gereflecteerd.

Zie de volgende figuur voor vergelijkingen van verschillende metaalheid kaartwaarden:

![Een bruine bol met lichte vlekken.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Metalness-0.png) 0%

![Een bruine bol met lichte vlekken en enige reflectiviteit.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Metalness-Half.png) 50%

![Een bruine bol met gematigde vlekken en veel reflectiviteit.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/Metalness-1.png) 100%

Verschillende PBR-renderers gebruiken verschillende workflows voor het verwerken van reflectiviteit. Studio gebruikt alleen de metaalheid workflow  die bepaalt of een materiaal een niet-metaal  of een metaal  is, soms aangeduid als een isolator  of geleider .

Verschillende combinaties van de ruwheid en metaalheid kunnen bijna elk mogelijk echt materiaaloppervlak vertegenwoordigen. Zie [materiaalreferenties](/docs/nl-nl/art/modeling/material-reference)  voor voorbeelden en referenties van hoe combinaties van materiaalwaarden verschillende oppervlaktes kunnen creëren.

### [Emissief masker](#emissief-masker)[](#emissief-masker)

Een grijswaarden [EmissiveMaskContent](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#EmissiveMaskContent)  inhoudtextuur past een emissief masker  toe over het oppervlak. Dit stelt je in staat om een textuur te gebruiken om emissiviteit te regelen voor meer artistieke controle dan het alles-of-niets [Neon](/docs/nl-nl/reference/engine/enums/Material#Neon)  materiaal en stelt je in staat om gedetailleerde gloeiende effecten te creëren zoals verlichte tekst, futuristische harnassen of bioluminescente wezens.

De bijbehorende [EmissiveTint](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#EmissiveTint)  eigenschap bepaalt de tintkleur voor emissieve bijdrage, en [EmissiveStrength](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#EmissiveStrength)  bepaalt de sterkte van de emissieve bijdrage.

Je kunt emissieve maskers gebruiken op avatar-items die op de Marketplace zijn gepubliceerd, niet alleen op objecten binnen ervaringen. Dit geldt voor 3D-accessoires en gelaagde kleding, en voor avatarlichamen, waarbij elk enkel emissief lichaamsdeel het hele lichaam als een emissief item classificeert. 2D-kleding ondersteunt geen emissieve kwaliteiten. Emissieve ondersteuning strekt zich nog niet uit tot make-up, hoewel Face Makeup, Lip Makeup en Eye Makeup in een toekomstige update ondersteuning zullen krijgen voor emissieve kwaliteiten. Het creëren van emissieve items via In-Experience Creation (IEC) wordt ook niet ondersteund bij de lancering en is gepland als een vervolguitgave. Items die op de Marketplace zijn gepubliceerd, moeten [EmissiveStrength](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#EmissiveStrength)  tussen 0 en 40 houden om validatie te doorstaan.

![Een oranje bol met een pompoen emissief masker op 50% sterkte.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/EmissiveStrength-Half.png)[EmissiveStrength](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#EmissiveStrength)  op 50%

![Een oranje bol met een pompoen emissief masker op 100% sterkte.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/EmissiveStrength-Full.png)[EmissiveStrength](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#EmissiveStrength)  op 100%

![Een oranje bol met een pompoen emissief masker getint naar magenta.](https://prod.docsiteassets.roblox.com/assets/modeling/surface-appearance/EmissiveTint-Magenta.png)[EmissiveTint](/docs/nl-nl/reference/engine/classes/SurfaceAppearance#EmissiveTint)  = [255, 0, 255]

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
