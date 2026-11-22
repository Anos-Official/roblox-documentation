<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/vfx/laser-traps-with-beams -->

Maak laserstralen met VFX | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. VFX

# Maak laserstralen met VFX

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een laserstraal  is een lichtstraal. Hoewel ze in het echte leven zelden gevaarlijk zijn, worden laserstralen in sci-fi games vaak gebruikt als een mechanisme om spelers bij impact schade toe te brengen. Vanwege hun veelzijdigheid en prominente rol in futuristische media zijn laserstralen echter nuttig voor allerlei gameplay-mechanismen, zoals blasterwapens, puzzels, obstakels en esthetiek van de omgeving.

Met behulp van een voorbeeld [Laser Beam Blaster](https://create.roblox.com/store/asset/16382650186)  model laat deze tutorial je zien hoe je een laserstraal speciale effect kunt creëren met een optioneel script om de gezondheid van de speler op nul te zetten bij een botsing, inclusief richtlijnen over:

-

Het opzetten van een onzichtbare botsingsdoos die detecteert wanneer een speler met de laserstraal botst.

-

Het configureren van bevestigingen die de reikwijdte van de emissie van de laserstraal vertegenwoordigen.

-

Het aanpassen van een straal die de visuele kenmerken van een futuristische laserstraal emuleert.

-

Het scriptgedrag voor de botsingsdoos dat de gezondheid van de speler beschadigt.

Je kunt je eigen assets maken in externe modelleringstools en meedoen met je eigen ontwerp. Voor informatie over het exporteren van modellen voor gebruik in Studio, zie [Exportvereisten](/docs/nl-nl/art/modeling/export-requirements) .

## [Verkrijg blaster asset](#verkrijg-blaster-asset)[](#verkrijg-blaster-asset)

De Creator Store  is een tabblad van de Toolbox  dat je kunt gebruiken om alle assets te vinden die zijn gemaakt door Roblox en de Roblox-gemeenschap voor gebruik binnen je projecten, inclusief model-, afbeelding-, mesh-, audio-, plugin-, video- en lettertype-assets. Je kunt de Creator Store gebruiken om een individuele asset of assetbibliotheek rechtstreeks in een open spel toe te voegen.

Deze tutorial verwijst naar een hoogwaardig laserstraal blastermodel dat je kunt gebruiken terwijl je elke stap in de volgende secties herhaalt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/laser-traps-with-beams/LaserBlasterAsset.png)

Om deze blasterasset vanuit je inventaris in je spel te krijgen:

1.

Voeg de blaster toe aan je inventaris.

1.

Navigeer naar de [detailpagina](https://create.roblox.com/store/asset/16382650186)  van de asset in de Creator Store.

2.

Klik in de rechterbovenhoek op de knop Model Krijgen . De blasterasset staat nu in je inventaris en je kunt deze opnieuw gebruiken in elk project op het platform.

2.

Navigeer in Studio naar het tabblad Start  en klik vervolgens op de knop Toolbox . Het venster Toolbox  opent.

 ![Toolbox gemarkeerd in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Toolbox.png)

3.

Klik in het venster Toolbox  op het tabblad Inventaris . De sortering Mijn Modellen  wordt weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Inventory-Tab.png)

4.

Klik op de tegel Laser Beam Blaster . Het model wordt weergegeven in je viewport.

## [Stel een botsingsdoos in](#stel-een-botsingsdoos-in)[](#stel-een-botsingsdoos-in)

De complete laserstraal die de gezondheid van spelers op nul zet bij impact moet in staat zijn te detecteren wanneer spelers met de laser botsen. Omdat [Beam](/docs/nl-nl/reference/engine/classes/Beam)  objecten geen standaard botsingsdetectiecapaciteiten hebben, moet je botsingsdetectie instellen met basisdelen.

Bijvoorbeeld, deze tutorial gebruikt een onzichtbaar blokdeel met een [Beam](/docs/nl-nl/reference/engine/classes/Beam)  object als een botsingsdoos die detecteert wanneer het [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  object van een karakter de laserstraal aanraakt. In de laatste sectie van de tutorial maak je een script dat deze informatie gebruikt om schade toe te brengen aan de gezondheid van de speler.

Om de botsingsdoos in te stellen:

1.

Voeg een blok  deel toe aan LaserBeamBlaster .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/laser-traps-with-beams/CollisionBox-1.jpg)

2.

Selecteer het deel, en stel in het venster Eigenschappen ,

1.

Naam  in op CollisionBox . De naam van het deel en de stijl van de hoofdletters zijn belangrijk voor het script later in de tutorial.

2.

Zet Verankerd  aan om ervoor te zorgen dat het fysicasysteem het deel niet verplaatst wanneer het spel begint.

3.

Schaal CollisionBox  naar de lengte die je wilt dat je laserstraal van de blaster afschiet. Deze tutorial schaalt het bijvoorbeeld zodat het dezelfde lengte heeft als de blaster.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/laser-traps-with-beams/CollisionBox-2.jpg)

4.

Verplaats CollisionBox  naar een positie waar het zich uitstrekt vanaf de emitterbol van de blaster. Je botsingsdoos vertegenwoordigt nu de reikwijdte van de laserstraal die van de blaster afkomt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/laser-traps-with-beams/CollisionBox-3.jpg)

## [Configureer bevestigingen](#configureer-bevestigingen)[](#configureer-bevestigingen)

Voordat je een [Beam](/docs/nl-nl/reference/engine/classes/Beam)  object aan je blaster toevoegt, is het belangrijk om twee [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten in de 3D-ruimte te configureren om de reikwijdte van de emissie van de laser van de emitterbol van de blaster te vertegenwoordigen. Stralen werken door een textuur tussen bevestigingen te renderen, dus als je geen bevestigingen hebt waar de straal naar kan verwijzen, kan deze helemaal niet functioneren.

Om bevestigingen voor de laserstraal te configureren:

1.

Om bevestigingen zichtbaar te maken in de viewport, zet Toon Constraint Details  aan in het Weergave  menu van Studio.

2.

Voeg twee bevestigingen toe aan de botsingsdoos.

1.

In het venster Explorer , beweeg de muis over CollisionBox , en klik vervolgens op het ⊕-icoon. Een contextmenu wordt weergegeven.

2.

Voeg vanuit het contextmenu een Bevestiging  toe.

3.

Herhaal dit proces zodat CollisionBox  twee bevestigingsobjecten heeft.

4.

Hernoem beide bevestigingen respectievelijk naar StartAttachment  en EndAttachment .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/laser-traps-with-beams/Attachments-2.jpg)

3.

Verplaats StartAttachment  naar de rand van CollisionBox  die overlapt met de emitterbol, en verplaats vervolgens EndAttachment  naar de rand van CollisionBox  die de reikwijdte van de laserstraal vertegenwoordigt.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/laser-traps-with-beams/Attachments-3.jpg)

4.

Maak de CollisionBox  transparant zodat je de textuur die de straal tussen de bevestigingen rendert zonder obstructie kunt zien.

1.

Selecteer in het venster Explorer  CollisionBox .

2.

Stel in het venster Eigenschappen  Transparantie  in op 1  om het deel volledig transparant te maken.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/laser-traps-with-beams/Attachments-4.jpg)

## [Pas de straal aan](#pas-de-straal-aan)[](#pas-de-straal-aan)

Nu je [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten in de 3D-ruimte hebt, kun je een [Beam](/docs/nl-nl/reference/engine/classes/Beam)  object toevoegen en aanpassen om de visuele kenmerken van een laserstraal te emuleren. Deze tutorial biedt richtlijnen over hoe je een futuristische, felroze straal kunt maken die snel animeert, maar door te experimenteren met dezelfde eigenschappen kun je een verscheidenheid aan verschillende speciale effecten creëren.

Om de straal aan te passen:

1.

Voeg een straal toe aan CollisionBox .

1.

In het venster Explorer , beweeg de muis over CollisionBox , en klik vervolgens op het ⊕-icoon. Een contextmenu wordt weergegeven.

2.

Voeg vanuit het contextmenu een Straal  toe.

2.

Wijs de bevestigingen van de botsingsdoos toe aan het nieuwe [Beam](/docs/nl-nl/reference/engine/classes/Beam)  object.

1.

Selecteer in het venster Explorer  de straal.

2.

In het venster Eigenschappen ,

1.

Stel Attachment0  in op StartAttachment .

2.

Stel Attachment1  in op EndAttachment . De straal rendert zijn standaardtextuur tussen de twee bevestigingen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/laser-traps-with-beams/Beam-2.jpg)

3.

Pas het visuele uiterlijk van de straal aan zodat het eruitziet als een futuristische laserstraal.

1.

Controleer in het venster Explorer  of de straal nog steeds is geselecteerd.

2.

In het venster Eigenschappen ,

1.

Stel Textuur  in op rbxassetid://6060542021  om een nieuwe textuur te renderen die eruitziet als een laserstraal.

2.

Stel Kleur  in op 255, 47, 137  om de laser felroze te maken.

3.

Stel Lichtemissie  in op 0.5  om een zwakke gloed aan de laser toe te voegen.

4.

Stel Breedte0  en Breedte1  in op 4  om de laser te verbreden.

5.

Stel TextuurSnelheid  in op 2  om de laser sneller te laten animeren.

6.

Zet GezichtCamera  aan om ervoor te zorgen dat de laser zichtbaar is, ongeacht de hoek van de speler ten opzichte van de laser.

Voor meer informatie over alle straaleigenschappen die je kunt aanpassen, zie [Stralen](/docs/nl-nl/effects/beams) .

## [Script schadegedrag](#script-schadegedrag)[](#script-schadegedrag)

Je laserstraal is momenteel esthetisch aantrekkelijk voor zijn omgeving, maar het is ook volledig onschadelijk als blasterwapen. Om de laserblaster te wijzigen zodat deze schade kan toebrengen aan spelers, moet je een script aan de botsingsdoos toevoegen dat dit gedrag activeert.

Het voorbeeldscript werkt door te wachten om te zien welke objecten de botsingsdoos aanraken. Als een object dat de botsingsdoos aanraakt een kind [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  object bevat, stelt het script de [Gezondheids eigenschap](/docs/nl-nl/reference/engine/classes/Humanoid#Health)  in op 0 . Standaard bevat elk spelerskarakter een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  object, dus elke keer dat een speler met de botsingsdoos botst, stelt het script onmiddellijk hun gezondheid op nul in, en valt het karakter uit elkaar.

Om het gedrag te script dat de speler schade toebrengt:

1.

Voeg een script toe aan LaserBeamBlaster .

1.

In het venster Explorer , beweeg de muis over LaserBeamBlaster , en klik vervolgens op het ⊕-icoon. Een contextmenu wordt weergegeven.

2.

Voeg vanuit het contextmenu een Script  toe.

2.

Vervang de standaardcode door de volgende code:

```

local laserTrap = script.Parent

local collisionBox = laserTrap.CollisionBox

local function onTouch(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.Health = 0

	end

end

collisionBox.Touched:Connect(onTouch)

```

3.

Test het gedrag door in de laserstraal te lopen.

1.

Kies Test  uit het dropdownmenu en klik op de knop Speel  ernaast om de playtest te starten.

 ![Testoptie in de testmodi dropdown van de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Test.png)

2.

Loop in de laserstraal om te zien hoe je karakter uit elkaar valt. Wanneer je klaar bent, klik op de knop Stop . Studio verlaat de playtestmodus.

 ![Stopknop aangegeven in de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Stop.png)

Als het gedrag niet correct werkt, zorg er dan voor dat het script een kind is van LaserBeamBlaster , en dat de botsingsdoos CollisionBox  heet.

Je hebt nu een gevaarlijke laserstraal blaster! Met de vaardigheden in deze tutorial kun je allerlei soorten straal speciale effecten aanpassen, zoals gloeiende krachtvelden, snelle watervallen en snelheidshellingen. Je kunt bijvoorbeeld experimenteren met extra straaleigenschappen zoals CurveSize0  en CurveSize1 , [importeer](/docs/nl-nl/production/creator-store)  je eigen texturen, en combineer stralen met andere speciale effecten, zoals [Deeltjesemitter](/docs/nl-nl/effects/particle-emitters)  en [Lichtbronnen](/docs/nl-nl/effects/light-sources) . Veel plezier met creëren!

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
