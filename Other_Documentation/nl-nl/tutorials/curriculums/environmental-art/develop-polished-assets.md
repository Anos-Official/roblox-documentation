<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/environmental-art/develop-polished-assets -->

Ontwikkel gepolijste assets | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Ontwikkel gepolijste assets

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het ontwikkelen van gepolijste assets  is het proces van het plannen en creëren van hoogwaardige assets om de greybox-omgeving te vervangen of om te zetten en om te voldoen aan de esthetische doelen en ontwerpeisen van je spel. Nadat je de basis hebt gelegd voor hoe je je assets in de 3D-ruimte wilt indelen vanuit het greybox-proces, is het veel gemakkelijker om te visualiseren welke assets nodig zijn om je omgeving tot leven te brengen.

Met behulp van de [Environment Art Asset Library](https://www.roblox.com/library/14447738661/Environment-Art-Asset-Library)  als referentie, laat deze sectie van het curriculum voor milieukunst je zien hoe je je moet voorbereiden om je basis greybox-indeling om te zetten in een futuristische laser tag-omgeving, inclusief richtlijnen over:

-

Het kiezen van een kunststijl die elke beslissing die je neemt voor je assets in het ontwerpproces beïnvloedt.

-

Het ontwerpen van tegelbare texturen, trim sheets, een modulaire kit en props die samenhangend zijn met elkaar en in overeenstemming met je kunststijl.

Nadat je deze sectie hebt voltooid, leer je hoe je al je gepolijste assets in de 3D-ruimte kunt trekken met extra terrein, lichtbronnen en speciale effecten om karakter en verhaalelementen aan je omgeving toe te voegen.

 ![Een gepolijste groep assets die een toegangspoort vormen.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/Overview.png)

Het is belangrijk op te merken dat het proces tussen het polijsten van assets en het construeren van je omgeving zelden een rechte lijn van je oorspronkelijke idee naar de uiteindelijke kunst is. Iteratie tussen elke stap en over stappen heen is normaal en bijna altijd noodzakelijk in het ontwikkelingsproces.

## [Kies een kunststijl](#kies-een-kunststijl)[](#kies-een-kunststijl)

Het kiezen van een kunststijl aan het begin van je ontwerpproces stelt je in staat om een belangrijke bron van waarheid te hebben voor de esthetische behandeling van je assets. Je kunt het beschouwen als je visuele basisregels, die je constant raadpleegt terwijl je je assets ontwerpt om ervoor te zorgen dat ze altijd de gebruikers informeren over wat je wilt dat je omgeving communiceert. Een effectieve kunststijl biedt gebruikers informatie over de wereld waarin ze spelen, zoals het klimaat, rijke geschiedenis of de relatie tot technologie.

Veel ontwikkelaars kiezen ervoor om een moodboard of themabord te maken, en voegen zoveel afbeeldingen toe als nodig is totdat ze het gevoel hebben dat ze een visuele representatie hebben van hoe ze willen dat hun wereld eruitziet. Bijvoorbeeld, de uiteindelijke voorbeeld laser tag-omgeving's kunststijl verwijst naar de volgende afbeeldingen om referenties te trekken voor de focus elementen van de 3D-ruimte, zoals weelderig loof, ronde frames, rechthoekige betonnen vormen en stijlvol uniforme metalen versieringen. Hoewel gebruikers je referentieafbeeldingen misschien nooit zien, zullen ze de impact van hun invloed voelen in de samenhang van de identiteit van je wereld.

 ![Een collage van referentieafbeeldingen voor de voorbeeld laser tag-game.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/Art-Style.png)

## [Ontwerp texturen](#ontwerp-texturen)[](#ontwerp-texturen)

Nu je een kunststijl voor je spel hebt, is het tijd om je indeling te herzien en uit te zoeken welke texturen je nodig hebt om materialen voor de 3D-ruimte te creëren. Omgevingen vereisen vaak texturen die grote oppervlakken kunnen bedekken, evenals texturen die een niveau van detail aan je assets kunnen bieden zonder extra geometrie toe te voegen. Bijvoorbeeld, je greybox-omgeving heeft texturen nodig die de buitenruimte kunnen bedekken, zoals mos, bloemen en stenen, evenals texturen om details aan de gevechtspockets te geven, zoals panelen en bouten om deuropeningen te omlijsten.

Er zijn twee hoog-niveau texturering methoden die je kunt gebruiken om aan deze vereisten te voldoen: tegelbare texturen en trim sheets. De volgende secties bieden informatie en richtlijnen over beide textuurmethoden, inclusief wat je moet overwegen terwijl je texturen vindt in de [Creator Store](/docs/nl-nl/production/creator-store) , of ze ontwerpt in derde-partij tools.

### [Tegelbare texturen](#tegelbare-texturen)[](#tegelbare-texturen)

Tegelbare texturen  zijn texturen die zowel op de X als  Y-as tegelbaar zijn, en ze stellen je in staat om grote oppervlakken in je omgeving te bedekken, zoals vloeren, muren en terrein. Dit type textuur vereist minimale handmatige aanpassingen nadat je ze hebt toegepast op blok [Parts](/docs/nl-nl/reference/engine/classes/Part)  omdat blokken vlakke oppervlakken hebben, wat betekent dat je geen rekening hoeft te houden met hoe de textuur zich kan vervormen op complexere geometrie. Bovendien kun je tegelbare texturen [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  objecten binnen de [MaterialService](/docs/nl-nl/reference/engine/classes/MaterialService)  importeren om op je terrein toe te passen, wat een proces is dat je zult leren in [Maak aangepaste materialen](/docs/nl-nl/tutorials/curriculums/environmental-art/assemble-an-asset-library#maak-aangepaste-materialen)  in de volgende sectie van deze tutorial.

 ![Een bovenaanzicht van een blokdeel met een tegelbare mos met bloemen materiaal toegepast.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TileableTextures-Part.png)

De meest fundamentele regel voor tegelbare texturen is dat ze geen naad mogen hebben , anders is het waar de textuur begint en eindigt op een oppervlak merkbaar voor gebruikers, wat hun gevoel van onderdompeling in het spel kan verstoren. Om deze reden werken tegelbare texturen goed voor natuurlijke materialen, zoals gras en steen, die naadloos zijn van aard in de echte wereld. In feite gebruikt de laser tag voorbeeldgame de volgende vier organische tegelbare texturen om natuurlijke materialen voor de buitenruimte te vertegenwoordigen, die je kunt gebruiken in de [wereldbouw](/docs/nl-nl/tutorials/curriculums/environmental-art/construct-your-world)  sectie van deze tutorial.

![Een bolvormig deel met een tegelbare mos materiaal toegepast.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TileableTextures-Moss.png) Mos

![Een bolvormig deel met een tegelbare mos met bloemen materiaal toegepast.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TileableTextures-MossFlowers.png) MosBloemen

![Een bolvormig deel met een tegelbare mos met stenen materiaal toegepast.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TileableTextures-MossStones.png) MosStenen

![Een bolvormig deel met een tegelbare stenen materiaal toegepast.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TileableTextures-Stones.png) Stenen

Let op hoe al deze voorbeeld tegelbare texturen een gelijke zichtbare verdeling van hun mos-, bloem- en steen-elementen hebben. Als je enige onderscheidende elementen zou opnemen, zoals een enorme steen of een patch bloemen, zou dit de aandacht van de gebruiker trekken naar het feit dat de textuur herhaald wordt. Bijvoorbeeld, de eerste afbeelding in de volgende twee afbeeldingen heeft een merkbare patch van vuil die het oog naar de herhaling van de textuur trekt. De tweede afbeelding maakt deze patch veel kleiner, wat de elementen van de textuur in balans brengt en de herhaling veel minder merkbaar maakt.

![Een tegelbare rots textuur met een onderscheidende patch van rotsen gemarkeerd om te laten zien dat de herhaling van het onderscheidende element merkbaar is.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TileableTextures-WithElement.jpg)

![Een tegelbare rots textuur zonder onderscheidende elementen om te laten zien dat deze techniek de herhaling van elementen niet merkbaar maakt.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TileableTextures-NoElement.jpg)

Als je besluit om je eigen tegelbare texturen te ontwerpen in derde-partij modelleringstools zoals [Substance Designer](https://www.adobe.com/products/substance3d-designer)  of [Blender](https://www.blender.org/) , houd dan het volgende in gedachten:

-

Je kunt texturen maken tot 1024x1024, maar hoe dichter je bij deze maximale grootte komt, hoe hoger de prestatiekosten.

-

Creëer een gelijke zichtbare verdeling zodat geen enkel element meer onderscheidend is dan de anderen.

-

Zelfs als een tegelbare textuur technisch naadloos is, bekijk de algehele afbeelding om ervoor te zorgen dat deze geen element heeft dat zo uitgesproken is dat de herhaling van de textuur merkbaar is.

Het vorige punt is bijna onmogelijk om volledig te verwijderen, maar je kunt de Studio-materiaal instellen om organisch te tegel, of extra decal overlays toevoegen om de herhaling effectief te verbergen. Voor meer informatie over deze technieken, zie [Assemble an asset library - Creating custom materials](/docs/nl-nl/tutorials/curriculums/environmental-art/assemble-an-asset-library#maak-aangepaste-materialen)  en [Assemble modular environments - Reduce visible repetition](/docs/nl-nl/tutorials/use-case-tutorials/modeling/assemble-modular-environments#verminder-zichtbare-herhaling) , respectievelijk.

### [Trim sheets](#trim-sheets)[](#trim-sheets)

Trim sheets  zijn texturen die tegelbaar zijn op de X of  Y-as, en ze stellen je in staat om aanzienlijk meer visuele complexiteit aan je spel toe te voegen zonder extra texturen te hoeven importeren, wat je een negatieve impact op het geheugen bespaart. Elke rij of kolom van een trim sheet heeft een unieke visuele uitstraling, waardoor je veel verschillende oppervlaktebehandelingen kunt kiezen wanneer je UV-gegevens aan een mesh toewijst. Bijvoorbeeld, de deurframe- en plafond-assets in de volgende twee afbeeldingen gebruiken verschillende lagen van dezelfde trim sheet om detailwerk aan de ruimte toe te voegen.

![Een deur met trim sheet texturen toegepast.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TrimSheets-Doorway.jpg)

![Een groep plafondtegels met trim sheet texturen toegepast.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TrimSheets-Ceiling.jpg)

De meest fundamentele regel voor trim sheets is om contextuele details te vermijden die je alleen op een enkel object kunt toepassen. Dit komt omdat trim sheets bruikbaar moeten zijn voor veel soorten objecten in je wereld, en zeer specifieke details zijn ook voor gebruikers herkenbaar naarmate ze zich herhalen in de 3D-ruimte. Bijvoorbeeld, in de volgende afbeelding van de [Mystery of Duvall showcase](/docs/nl-nl/resources/the-mystery-of-duvall-drive/materialize-the-world#oppervlakteverschijning-en-trimkaarten) , bevat de trim sheet van de meubelset aan de linkerkant meer vlekdetails dan de trim sheet van de meubelset aan de rechterkant. Let op hoe de extra vlekdetails de herhaling prominent maken in vergelijking met de meubelset aan de rechterkant.

 ![Dezelfde meubelset heeft verschillende trim sheets toegepast. De meubelset aan de linkerkant met meer onderscheidende vlek-elementen heeft merkbare herhaling.](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/materializing-the-world/furniture-set-stain.png)

Volg deze fundamentele regel, de uiteindelijke voorbeeld laser tag-omgeving gebruikt de volgende trim sheet textuurkaarten met zes rijen van eenvoudige detailwerk om visuele interesse en samenhang aan zijn modulaire kit en props toe te voegen. Je kunt deze [trim sheet](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TrimSheetTextureMaps.zip)  gebruiken voor UV-unwrapping in derde-partij modelleringstools, en vervolgens de textuurkaarten in een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object gebruiken wanneer je je assetbibliotheek samenstelt. Voor meer informatie over wat elke van deze textuurkaarten aan meshes biedt, zie [PBR textures - Texture maps](/docs/nl-nl/art/modeling/surface-appearance#textuurkaarten) .

Dit trim sheet-bestand is alleen nuttig voor UV-unwrapping processen in derde-partij modelleringstools. Als je probeert de textuurkaarten naar een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  object te uploaden zonder een UV-unwrapping proces te voltooien, is er geen data voor Studio om aan de textuur zelf te koppelen.

 ![Het trim sheet van de voorbeeld laser tag-game.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/Trimsheet.png)

![De albedo textuurkaart van het trim sheet van de voorbeeld laser tag-game.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TrimSheets-Albedo.png) Albedo

![De normale textuurkaart van het trim sheet van de voorbeeld laser tag-game.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TrimSheets-Normal.png) Normaal

![De ruwheid textuurkaart van het trim sheet van de voorbeeld laser tag-game.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TrimSheets-Roughness.png) Ruwheid

![De metalness textuurkaart van het trim sheet van de voorbeeld laser tag-game.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/TrimSheets-Metalness.png) Metalness

Als je besluit om je eigen trim sheets te ontwerpen in derde-partij modelleringstools zoals [Substance Designer](https://www.adobe.com/products/substance3d-designer) , [Blender](https://www.blender.org/)  of [ZBrush](https://www.maxon.net/en/zbrush) , houd dan het volgende in gedachten:

-

Je kunt texturen maken tot 1024x1024, maar hoe dichter je bij deze maximale grootte komt, hoe hoger de prestatiekosten.

-

Het trim sheet moet gelijk zijn in lengte zowel langs de X- als Y-as.

-

Je kunt verschillende ontwerpkeuzes maken om meer contextuele details op te nemen, maar zodra de details op het trim sheet staan, kun je ze niet gemakkelijk verbergen.

-

Exporteer de textuurkaarten van je trim sheet naar een locatie die gemakkelijk te refereren is wanneer je een assetbibliotheek aanmaakt.

Voor meer informatie over deze techniek, zie [Bouwarchitectuur - Trim sheets maken](/docs/nl-nl/resources/beyond-the-dark/building-architecture#maak-trim-sheets) .

## [Ontwerp modulaire kits](#ontwerp-modulaire-kits)[](#ontwerp-modulaire-kits)

Modulaire kits zijn sets van assets die naadloos in elkaar klikken om variaties van een groter complex object te creëren. Het ontwerpen en gebruiken van modulaire kits als onderdeel van je ontwikkelingsproces is nuttig omdat je niet handmatig elke individuele asset in je spel hoeft te maken. In plaats daarvan hoef je alleen een paar assets te maken die je kunt hergebruiken en aanpassen om variëteit door de scène te creëren.

Dit proces versnelt niet alleen hoe snel je de greybox-omgeving kunt vervangen of omzetten, maar wanneer je een trim sheet UV-wrapped op de meshes in je modulaire kit voor detailwerk, kan het ook helpen om elk afzonderlijk object in het spel samenhangend te laten aanvoelen. Bijvoorbeeld, de uiteindelijke voorbeeld laser tag-omgeving maakt gebruik van een enkele SA_EC_Trim_Metal_A  trimsheet om UV-wrapping toe te passen op al zijn modulaire assets die het algemene gebouw creëren waar het meeste gameplay plaatsvindt, inclusief assets die een stijging in hoogte tussen de eerste en tweede verdieping accommoderen.

 ![De modulaire kit van de voorbeeld laser tag-game.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/DesigningModularKits-ModularKit.jpg)

Elke asset in deze modulaire kit heeft een consistente pivotpuntlocatie, hetzij in de voorste, onderste hoek, of op een locatie die hen in staat stelt om op een logische positie op het gebouw in 5 stud-incrementen te klikken wanneer je grid-snapping inschakelt, zoals trimstukken op muren, of deuren in hun deuropeningpositie. Bovendien is elke asset minstens 5 studs hoog en breed, zodat er nooit conflicterende geometrie is, zelfs niet wanneer je de assets draait en verplaatst. Voor meer informatie over dit concept, zie [Assemble modular environments - The importance of consistent pivot point locations](/docs/nl-nl/tutorials/use-case-tutorials/modeling/assemble-modular-environments#het-belang-van-consistente-pivotpuntlocaties) .

Je kunt de [voorbeeld modulaire kit](https://www.roblox.com/library/14447738661/Environment-Art-Asset-Library)  gebruiken of aanpassen voor het vervangen van greybox-geometrie in de [wereldbouw](/docs/nl-nl/tutorials/curriculums/environmental-art/construct-your-world)  sectie van deze tutorial. Als je echter besluit om je eigen modulaire kit te ontwerpen in derde-partij modelleringstools zoals [Blender](https://www.blender.org/)  of [Maya](https://www.autodesk.com/products/maya/overview) , houd dan het volgende in gedachten:

-

Het is van vitaal belang dat modulaire assets een consistente pivotlocatie hebben, zodat ze op vooraf bepaalde, incrementele afstanden ten opzichte van elkaar kunnen verbinden wanneer je grid-snapping inschakelt.

-

Elke asset moet een maximale hoogte en breedte hebben die deelbaar is door de kleinste hoogte en breedte in de kit, zodat ze zich in incrementele afstanden kunnen verplaatsen en draaien. Bijvoorbeeld, de hoogste en breedste asset van de voorbeeldkit is 15 bij 5 studs, wat deelbaar is door de kleinste asset van 5 bij 5 studs.

-

Het is nuttig om grotere assets zoals gangen in aparte meshes onder een model met zorgvuldige naamgevingsconventies te scheiden, zoals een gang [Model](/docs/nl-nl/reference/engine/classes/Model)  met kind UpperTrim , LowerTrim , en Wall  [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten. Dit stelt je in staat om elke mesh van het algemene model aan te passen, zoals het wijzigen van hun individuele materiaal-, botsing- en renderparameters, of het verwijderen van onnodige geometrie afhankelijk van waar het model zich binnen het spel bevindt.

Ongeacht welke modulaire kit je gebruikt, is het belangrijk om vaak te testen en je assets vanuit meerdere perspectieven te bekijken om te zien of er conflicterende geometrie is. Als dat zo is, betekent dit vaak dat een van de pivotpuntlocaties van de asset niet relatief consistent is met de andere.

## [Ontwerp props](#ontwerp-props)[](#ontwerp-props)

Props zijn niet-modulaire assets die het niveau van visueel vertellen in een omgeving verbeteren terwijl ze gebruikers belangrijke context bieden over de wereld waarin ze zich bevinden. Bijvoorbeeld, als gebruikers een grot verkennen en props zoals gloeiende bollen en skeletten zien, kunnen ze afleiden dat hun omgeving zowel magisch als gevaarlijk is, dus het kan verstandig zijn om voorzichtig verder te gaan.

Props zijn het meest effectief wanneer ze verbonden zijn met grotere thema's in de kunststijl van je spel. Bijvoorbeeld, de uiteindelijke voorbeeld laser tag-omgeving maakt gebruik van props om gebruikers context te bieden over de relatie van de omgeving met technologie en natuur. In het bijzonder bevat de props kit schone, high-tech panelen, kratten, brandblussers en beveiligingscamera's naast grote stenen en een verscheidenheid aan planten, wat gebruikers informeert dat de wereld technologische vooruitgang waardeert, maar niet ten koste van de aarde.

 ![De props kit van de voorbeeld laser tag-game.](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/DesigningProps-PropsKit.png)

In tegenstelling tot modulaire assets, hoeven props geen consistente pivotpuntlocaties te hebben omdat ze niet samen hoeven te klikken om een groter complex object te creëren. Ze moeten echter wel logische pivotpuntlocaties hebben afhankelijk van waar je ze in de 3D-ruimte moet plaatsen. Bijvoorbeeld, in de volgende afbeelding heeft de brandblusser prop een pivotpuntlocatie aan de achterkant van het object zodat het op muren kan klikken, en de crate heeft een pivotpuntlocatie aan de onderkant van het object zodat het op vloeren kan klikken. Dit maakt universele contextuele plaatsing mogelijk, ongeacht de respectieve muur of vloer.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/environmental-art-curriculum/Section2/DesigningProps-Scale.jpg)

Je kunt props gebruiken of aanpassen van de [Environment Art Asset Library](https://www.roblox.com/library/14447738661/Environment-Art-Asset-Library)  in de wereldbouwsectie van deze tutorial. Als je echter besluit om je eigen props te ontwerpen in derde-partij modelleringstools zoals [Blender](https://www.blender.org/)  of [Maya](https://www.autodesk.com/products/maya/overview) , houd dan het volgende in gedachten:

-

Gebruikers zien props vaak vanuit meerdere hoeken, dus het is belangrijk om voldoende detail op te nemen zodat gebruikers kunnen begrijpen wat de prop is, maar niet te veel detail zodat het de prestaties beïnvloedt. Een goede regel is om alleen genoeg geometrie op te nemen zodat gebruikers kunnen zien wat een prop is vanuit zijn silhouet. Voor meer informatie over dit concept, zie [Een bewegende wereld ontwikkelen - Het opzetten van de oog van de storm](/docs/nl-nl/resources/the-mystery-of-duvall-drive/develop-a-moving-world) .

-

Je kunt dezelfde trim sheet gebruiken die je voor je modulaire assets hebt gebruikt, zodat je efficiënt gebruik maakt van texturen die al binnen je omgeving zijn, en zodat elke asset stylistisch samenhangend blijft.

-

Onderscheidende visuele markers in props zijn meer merkbaar naarmate je ze meer hergebruikt in je omgeving.

Zodra je al de hoogwaardige assets hebt die je nodig hebt om de greybox-omgeving te vervangen of om te zetten, kun je doorgaan naar de volgende sectie van de tutorial om te leren hoe je een assetbibliotheek binnen je plaatsbestand kunt samenstellen die je kunt gebruiken om je greybox-omgeving in een esthetisch aangename setting te veranderen.

[Volgende](/docs/nl-nl/tutorials/curriculums/environmental-art/assemble-an-asset-library)[Vorige](/docs/nl-nl/tutorials/curriculums/environmental-art/greybox-your-environment)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
