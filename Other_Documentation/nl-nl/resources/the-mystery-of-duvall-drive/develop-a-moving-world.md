<!-- Source: https://create.roblox.com/docs/nl-nl/resources/the-mystery-of-duvall-drive/develop-a-moving-world -->

Ontwikkel een bewegende wereld | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)
4. /
5. [Het mysterie van Duvall Drive](/docs/nl-nl/resources/the-mystery-of-duvall-drive)

# Ontwikkel een bewegende wereld

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Beweging creëren in elke omgeving binnen een spel helpt om het onmiddellijk meer meeslepend en realistisch te laten aanvoelen in onze wereld, of dat nu komt van de beweging van bomen, reactieve deuren door interactie van de speler, of zelfs dozen die bewegen wanneer ze tegen elkaar botsen. Studio heeft veel unieke methoden om beweging te creëren om werelden levendiger te laten aanvoelen, waaronder een fysicasysteem, [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  en animaties, en het analyseren van de specifieke behoeften van je spel kan je helpen bepalen welke je moet gebruiken. In dit gedeelte zullen we demonstreren hoe we hebben bepaald welk type beweging we wilden creëren in Studio, en welke tools we hebben gebruikt om deze verschillende doelen te bereiken.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/streaming-in-immersion/perspective-house.png)

## [Creëer de storm](#creëer-de-storm)[](#creëer-de-storm)

De storm heeft vele iteraties doorgemaakt voordat we ons vestigden op wat nu live is in The Mystery of Duvall Drive. In het begin dachten we aan de storm als een enorme obsidiaan pilaar, en in latere iteraties beschouwden we het als een gigantisch portaal naar de corrupte ruimte. Na te hebben geëxperimenteerd met veel verschillende stormen met unieke looks en gevoelens, kozen we voor een storm met een kleiner centraal "oog" omdat:

-

De storm moet spelers een gevoel geven van de impact van dit evenement op de wereld , inclusief bomen die waaien en puin dat rondvliegt.

-

De draaiende vortex van de wolken zelf moet spelers een glimp geven van het centrale portaal zonder alles te onthullen . Dit zou spelers aanmoedigen om dichterbij te onderzoeken wat er aan de hand is.

-

Het strakkere punt van licht zou ons in staat stellen om de compositie van het huis te focussen , dat zowel de hoofdpersoon is als waar het meeste gameplay zich bevindt.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/storm-iteration-1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/storm-iteration-2.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/storm-iteration-3.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/storm-iteration-4.png)

Om de storm dynamisch, agressief en voortdurend veranderend binnen zijn omgeving te laten aanvoelen, hebben we de volgende systemen en functies gebruikt:

1.

[TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  - Voor de beweging van de wolken.

2.

Verlichting veranderingen  - Voor het creëren van de wolk naar wolk bliksem.

3.

[Stralen](/docs/nl-nl/effects/beams)  - Voor de "volumetrische verlichting" en de bliksemschichten.

4.

[Deeltjesemitter](/docs/nl-nl/effects/particle-emitters)  - Voor puin dat omhoog vliegt naar het portaal en rondvliegt door de wind.

5.

[Animaties](/docs/nl-nl/animation)  - Voor de bomen die in de wind waaien.

### [Voeg wolken met texturen toe](#voeg-wolken-met-texturen-toe)[](#voeg-wolken-met-texturen-toe)

Hoewel [dynamische wolken](/docs/nl-nl/environment/clouds)  geweldig zijn voor normale, hoge realistische wolken, hadden we iets nodig dat dramatisch aanvoelde en dat we meer konden aansteken en aanpassen. Om dit te doen, hebben we [oppervlakteverschijning](/docs/nl-nl/art/modeling/surface-appearance)  objecten met semi-transparantie toegepast op een reeks zwaar gestapelde en gelaagde wolken meshes om wolkenbedekking te faken. Waarom hebben we ze zo zwaar gestapeld en gelaagd? Omdat wanneer elke wolken mesh met verschillende snelheden beweegt, ze elkaar kruisen en wolkenvormen creëren die in en uit elkaar gaan. Dit proces maakte de wolken een beetje dynamischer en natuurlijker, ondanks dat ze gewoon draaiende schijven waren. Het was ook belangrijk dat de wolken [semi-transparant](/docs/nl-nl/resources/beyond-the-dark/layered-clothing#importeren-in-studio-1)  waren, omdat we wilden dat spelers erdoorheen konden kijken om iets helders in het midden te zien voordat ze bij het huis aankwamen!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/single-cloud-mesh.png) Een enkele wolken mesh.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/layered-cloud-meshes.png) Gelaagde wolken meshes zonder hun texturen!

Aangezien elke wolken mesh enorm moest zijn om het huis volledig te omringen en over te brengen hoe enorm de storm was, wisten we dat we de textuur die we op de individuele wolken meshes wilden gebruiken moesten tegelen zodat deze zich sterk herhaalde over het oppervlak van de mesh. We testten de materialen die we voor de wolk maakten op deze eenvoudige onderdelen, en pasten ze vervolgens toe op de vortex!

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/cloud-texture-on-parts.png)

In tegenstelling tot deeltjesemitters of stralen, stelden meshes ons in staat om licht van elke mesh te weerkaatsen, wat belangrijk was toen we wolk-naar-wolk bliksem wilden implementeren. We modelleerden ook de draaiing zodat het licht dat ervan weerkaatste eruitzag alsof het diepte had! Dit was vooral belangrijk in situaties waarin de prestatie-eisen van het spel de kwaliteitsniveaus van onze oppervlakteverschijningsobjecten verlaagden.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/cloud-shading.png) Toen we begonnen met het toevoegen van verlichting, moesten we details aan de meshes toevoegen om ze beter te laten reageren op verlichting!

### [Rotate wolken meshes](#rotate-wolken-meshes)[](#rotate-wolken-meshes)

Nadat we tevreden waren met het algemene visuele uiterlijk van de wolken, moesten we ze in beweging krijgen! We hadden de algemene vormen van elke wolkenlaag op hun plaats, maar het kostte wat proberen en fouten om ervoor te zorgen dat het draai-effect er goed uitzag in de praktijk. We probeerden aanvankelijk [beperkingen](/docs/nl-nl/physics/mechanical-constraints)  te gebruiken om snelheid in te voeren die de wolken fysiek zou aandrijven om te bewegen. Dit was moeilijker dan we wilden dat het later zou zijn om te itereren, en de speler zou er nooit mee interageren, dus we hoefden het niet zo nauwkeurig te maken in zijn beweging.

We wilden een gebruiksvriendelijke methode om instanties te roteren die ofwel te ver weg waren om interactief te zijn, zoals wolken, of te klein of decoratief om belangrijk te zijn voor gameplay/fysica, zoals meubels binnenshuis zoals kleine lampen. We besloten om een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  te gebruiken om de client-server bandbreedte te verminderen, een soepelere beweging mogelijk te maken, en ervoor te zorgen dat elke wolken mesh een andere rotatiesnelheid en vertraging kon hebben. Om het algemener te maken, maakten we het ook mogelijk om de rotatie-as op te geven. Het is mogelijk om 3 attributen te gebruiken, maar voor onze zaak gebruikten we 3 waarden: Axis , Delay  en Speed .

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/main-vortex-settings.png)

Zoals in veel gevallen in de demo, gebruikten we een LocalSpaceRotation  tag zodat we de aangetaste instanties in Studio konden beheren met behulp van een instantie tagging plugin. We gebruikten slechts één [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  die alle getagde instanties beheerde met behulp van de [CollectionService](/docs/nl-nl/reference/engine/classes/CollectionService) , zodat we niet een heleboel scripts hoefden te onderhouden gedurende het ontwikkelingsproces.

In onze demo worden delen van de wereld gekloond van de [ServerStorage](/docs/nl-nl/reference/engine/classes/ServerStorage)  naar de werkruimte wanneer nodig, dus we moesten omgaan met gevallen waarin getagde objecten werden gemaakt en vernietigd. Met [LocalScripts](/docs/nl-nl/reference/engine/classes/LocalScript)  moeten we ook rekening houden met de streaming, waarbij meshes en hun kindwaarden mogelijk in en uit worden gestreamd. We verwerkten aanvankelijk geplaatste objecten in de Init()  functie, en verbonden met [CollectionService.GetInstanceAddedSignal](/docs/nl-nl/reference/engine/classes/CollectionService#GetInstanceAddedSignal)  en [CollectionService.GetInstanceRemovedSignal](/docs/nl-nl/reference/engine/classes/CollectionService#GetInstanceRemovedSignal)  voor getagde objecten om nieuw gemaakte/verwijderde objecten te verwerken. Dezelfde SetupObj  functie werd gebruikt om nieuwe objecten te initialiseren in Init()  en in [CollectionService.GetInstanceAddedSignal](/docs/nl-nl/reference/engine/classes/CollectionService#GetInstanceAddedSignal) .

```

local function Init()

	for _, obj in CollectionService:GetTagged("LocalSpaceRotation") do

		if obj:IsDescendantOf(workspace) then

			SetupObj(obj)

		end

	end

end

CollectionService:GetInstanceAddedSignal("LocalSpaceRotation"):Connect(function(obj)

	objInfoQueue[obj] = true

end)

CollectionService:GetInstanceRemovedSignal("LocalSpaceRotation"):Connect(function(obj)

	if objInfo[obj] then

		objInfo[obj] = nil

		if objInfoQueue[obj] then

			objInfoQueue[obj] = nil

		end

	end

end)

Init()

```

objInfo  is een map die informatie bevat voor alle relevante objecten, zoals hun rotatiesnelheid en as. Let op dat we SetupObj  niet onmiddellijk aanroepen vanuit [CollectionService.GetInstanceAddedSignal](/docs/nl-nl/reference/engine/classes/CollectionService#GetInstanceAddedSignal) , maar we voegden een object toe aan objInfoQueue . Met streaming en het klonen van objecten op de server, wanneer [CollectionService.GetInstanceAddedSignal](/docs/nl-nl/reference/engine/classes/CollectionService#GetInstanceAddedSignal)  wordt aangeroepen, hebben we mogelijk nog niet onze Axis , Delay , en Speed  waarden gehad, dus we voegen het object toe aan een wachtrij, en roepen SetupObj  aan in de volgende frames vanuit de Update  functie totdat de waarden daar waren en we ze konden lezen in de per object "info" structuur.

We roteerden de instanties in de Update  functie die verbonden was met de heartbeat. We kregen de transformatie van de ouder (parentTransform), accumuleerden een nieuwe rotatiehoek (curObjInfo.curAngle ) op basis van de rotatiesnelheid van dit object, berekenden de lokale transformatie (rotatedLocalCFrame ), en stelden deze uiteindelijk in op de [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) . Let op dat zowel de ouder als het object een [Model](/docs/nl-nl/reference/engine/classes/Model)  of [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  kunnen zijn, dus we moesten controleren of ze IsA("Model") zijn en of we een PrimaryPart.CFrame  of [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  moesten gebruiken.

```

local parentTransform

if parentObj:IsA("Model") then

	if not parentObj.PrimaryPart then

		-- primaire part is mogelijk nog niet gestreamd

		continue -- wacht tot primaire part is gerepliceerd

	end

	parentTransform = parentObj.PrimaryPart.CFrame

else

	parentTransform = parentObj.CFrame

end

curObjInfo.curAngle += dT * curObjInfo.timeToAngle

local rotatedLocalCFrame = curObjInfo.origLocalCFrame * CFrame.Angles( curObjInfo.axisMask.X * curObjInfo.curAngle, curObjInfo.axisMask.Y * curObjInfo.curAngle, curObjInfo.axisMask.Z * curObjInfo.curAngle )

if obj:IsA("Model") then

	obj.PrimaryPart.CFrame = parentTransform * rotatedLocalCFrame

else

	obj.CFrame = parentTransform * rotatedLocalCFrame

end

```

We controleerden of er een geldige [Model.PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  was ingesteld om streaming te verwerken. Als er een Update werd aangeroepen op ons object terwijl een [Model.PrimaryPart](/docs/nl-nl/reference/engine/classes/Model#PrimaryPart)  (die naar een kind mesh kan wijzen) nog niet was gestreamd, zouden we de update gewoon overslaan. Het huidige systeem is een tweede iteratie van objectrotatie, en het vorige systeem werkte anders: de waarden waren 12 keer anders! Om dezelfde gegevens te behouden, hebben we het in ons script geconverteerd, zoals "12 * obj.Speed.Value".

### [Ontwerp bliksemstrikes](#ontwerp-bliksemstrikes)[](#ontwerp-bliksemstrikes)

Omdat Studio geen kant-en-klare bliksemgenerator biedt, en het deeltjesysteem enkele beperkingen had die niet werkten voor de heldere bliksemstrikes, moesten we creatief worden met een oplossing voor de heldere bliksemstrikes. We besloten om twee hoofdsystemen te gebruiken om de bliksem te maken: getextureerde stralen voor de heldere bliksemstrikes die uit het oog van de storm komen zijn gescripte getextureerde stralen die onthullen en synchroniseren met audio en post-process effecten, en een eenvoudig deeltje-effect voor de verre wolk-naar-wolk bliksem.

#### [Textuurstralen](#textuurstralen)[](#textuurstralen)

We zouden normaal gesproken een sequencer of tijdlijn-tool gebruiken om de timing van een bliksemschicht-effect zoals dit aan te sturen, maar aangezien Studio deze functionaliteit nog niet biedt, besloten we om scripts te schrijven die de timing van de bliksemschichten zouden regelen. De scripting van dit effect is vrij eenvoudig, maar het bereikt de volgende belangrijke doelen:

1.

Elementen van de bliksemschichten, zoals hun texturen, helderheid en vertragingen, worden met elke schicht gerandomiseerd.

2.

Audio- en post-FX veranderingen zijn gesynchroniseerd met de schicht FX.

3.

Spelers die zich binnen of in het corrupte gebied bevinden, kunnen ze niet zien of horen.

We hebben een server-side [Script](/docs/nl-nl/reference/engine/classes/Script)  die verschillende parameters en timing berekent, deze naar alle clients verzendt, en wacht op een willekeurige tijd:

```

local function LightningUpdate()

	while true do

		task.wait(rand:NextNumber(3.0, 10.0))

		local info = CreateFXData()

		lightningEvent:FireAllClients(info)

	end

end

```

Binnen CreateFXData  vullen we de info-structuur in, zodat alle clients dezelfde parameters krijgen.

Aan de clientzijde (LightningVFXClient ), controleren we of deze client de FX moet uitvoeren:

```

local function LightningFunc(info)

	…

	-- geen FX wanneer binnen

	if inVolumesCheckerFunc:Invoke() then

		return

	end

	-- geen FX wanneer niet in de "normale" wereld

	if not gameStateInfoFunc:Invoke("IsInNormal") then

		return

	end

	…

```

Daarnaast voeren we de sequentie uit om texturen, posities en helderheid in te stellen, draaien tweens, en gebruiken [task.wait(number)](/docs/nl-nl/reference/engine/libraries/task#wait) . Gerandomiseerde parameters komen uit de info-structuur die we van de server hebben ontvangen, en sommige nummers zijn vast.

```

beam.Texture = textures[info.textIdx]

beamPart.Position = Vector3.new(info.center.X + og_center.X, og_center.Y, info.center.Y + og_center.Z)

-- Veeg

beam.Brightness = 10

ppCC.Brightness = maxPPBrightness

ppBloom.Intensity = 1.1

bottom.Position = top.Position

tweenBrightness:Play()

tweenPPBrightness:Play()

tweenPPBrightness:Play()

tweenBottomPos:Play()

tweenBrightness.Completed:Wait()

-- audio

if audioFolder and audioPart then

	if audioFolder.Value and audioPart.Value then

		audioUtils.PlayOneShot(audioObj, audioFolder.Value, audioPart.Value)

	end

end

task.wait(info.waitTillFlashes)

-- en zo verder

```

Om te controleren of een speler binnen is, gebruiken we een hulpfunctie inVolumesCheckerFunc , die over vooraf geplaatste volumes gaat die binnenruimtes benaderen, en controleert of de positie van de speler zich binnen een van hen bevindt (PointInABox). We hadden ook touch-gebaseerde detectie kunnen gebruiken, maar we ontdekten dat wanneer een speler in de volume gaat zitten, ze niet langer "aanraken" de volume. Het testen van een punt in een paar dozen is eenvoudiger, en we doen dit alleen wanneer een speler ver genoeg van de eerder geteste positie beweegt.

Om te controleren of een speler zich in corrupte gebieden bevindt, roepen we een hulpfunctie gameStateInfoFunc  aan, die de huidige spelstatus controleert. Om een willekeurig geluid uit een map af te spelen, gebruikten we ook een hulpfunctie PlayOneShot . Voor de bliksemschichten zelf was het super eenvoudig om ze in Photoshop te maken; we tekenden een kronkelige lijn, en voegden vervolgens een "Buiten Glans" laag effect toe.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/lightning-bolts.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/lightning-bolt-photoshop-settings.png)

#### [Gebruik deeltjesemitter systemen](#gebruik-deeltjesemitter-systemen)[](#gebruik-deeltjesemitter-systemen)

De heldere bliksemstrikes worden ondersteund door een deeltjesysteem dat verre bliksem suggereert door de indruk te wekken van een laag wolken op de achtergrond die licht opvangt van verre schichten, of wolk-naar-wolk bliksem. We hebben dit effect bereikt door een zeer eenvoudig deeltjesysteem dat periodiek een wolken billboard op de rand van de hoofd stormwolk flitst. Het systeem stoot een wolken deeltje periodiek uit met een gerandomiseerde transparantiecurve:

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/cloud-billboard.png)  ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/particle-emitter-settings.png)

### [Laat bomen in de wind waaien](#laat-bomen-in-de-wind-waaien)[](#laat-bomen-in-de-wind-waaien)

Nadat we de wolken en de bliksem hadden die werkten zoals we wilden, moesten we twee andere belangrijke componenten van een storm toevoegen: de wind en de regen! Deze elementen stelden een paar uitdagingen, waaronder dat ze moesten werken binnen de huidige beperkingen van onze fysica en speciale effecten systemen in Studio. Bijvoorbeeld, bomen laten bewegen met echte wind is niet mogelijk in de huidige engine, dus we gebruikten [deeltjesemitter](/docs/nl-nl/effects/particle-emitters)  effecten en [aangepaste karakteranimaties](/docs/nl-nl/animation/editor#maak-een-animatie)  voor de bomen.

We wisten dat om het effect van de wind en regen echt te verkopen, we de bomen zelf moesten laten bewegen. Er zijn een paar manieren waarop je dit binnen de engine kunt doen, waaronder het verplaatsen van onderdelen met behulp van [plugins](/docs/nl-nl/studio/plugins)  die openbaar beschikbaar zijn, het gebruik van [TweenService](/docs/nl-nl/reference/engine/classes/TweenService) , of het direct animeren van modellen. Voor onze doeleinden gaven animaties ons de mogelijkheid om de beweging te controleren die we uit onze bomen wilden, en het stelde ons in staat om een enkele animatie te gebruiken die we konden delen tussen alle bomen binnen het spel.

Er zijn voor- en nadelen aan elk van deze systemen, en een van de nadelen voor animaties is dat specifiek geskinnde meshes momenteel niet geïnstanced zijn. Dit betekent dat hoe meer geskinnde meshes je in je spel gebruikt, hoe groter de impact op de prestaties vanwege de geheugenkosten, dus we gebruikten ze spaarzaam voor het effect dat we wilden. Op een gegeven moment zal dit worden opgelost, dus zorg ervoor dat je de [documentatie over rigging en skinning](/docs/nl-nl/art/modeling/rigging)  controleert voor de meest actuele informatie.

We begonnen met het skinnen van verschillende bomen uit het [Endorse Model Pack - Forest Assets](https://www.roblox.com/library/6432306802/Forest-Pack) . Aangezien deze bomen al bestonden, en ons spel zich afspeelde in de Pacific Northwest, bespaarde het ons wat tijd in het begin om niet elk boommodel te hoeven maken.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/forest-pack.png) Het Forest pack bevat verschillende boomtypes, wat je tijd kan besparen in je eigen spellen.

Nadat we onze bomen hadden gekozen, wisten we dat we ze moesten skinnen. [Skinning een mesh](/docs/nl-nl/art/modeling/rigging)  is de handeling van het toevoegen van gewrichten (of botten) aan een mesh in een andere 3D-modelleringsapplicatie, zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) , en vervolgens invloed toepassen op die gewrichten/botten om de mesh te verplaatsen. Dit wordt het meest gebruikt in [humanoïde karakters](/docs/nl-nl/art/modeling/skin-a-humanoid-model) , maar met [aangepaste karakters](/docs/nl-nl/art/modeling/skin-a-simple-mesh)  kun je vrijwel alles skinnen.

We wisten dat we tijd wilden besparen en dezelfde animatie opnieuw wilden gebruiken, dus we bouwden onze eerste boom rig en zorgden ervoor dat de gewrichtnamen generiek waren omdat we dezezelfde namen in de rigs voor de andere bomen wilden gebruiken. We wisten ook dat we primaire, secundaire en tertiaire gewrichten/botten moesten opnemen zodat de stammen konden buigen met de wind, de takken konden zwaaien, en de bladeren leken te schudden als reactie. Voor dit proces moesten we een secundaire beweging  creëren, wat een animatieconcept is waarbij elke actie andere delen van het object laat reageren op die actie en lijkt bij te benen met de initiële beweging.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/tree-joints.png) De bomen hebben primaire, secundaire en tertiaire gewrichten zodat we geloofwaardige beweging konden hebben van het worden weggeblazen door de wind.

Zodra we onze gewrichten/botten hadden gemaakt, was het tijd om een testanimatie te maken om alle gewrichten en botten in Studio te verplaatsen om te zien of het bewoog zoals we wilden. Om dit te doen, moesten we [de boom in Studio importeren](/docs/nl-nl/resources/beyond-the-dark/custom-characters#importeer-de-mesh-naar-studio)  via de Custom Rig  instelling in de Importer , en vervolgens de mesh verplaatsen/animeren met behulp van de [Animatie-editor](/docs/nl-nl/resources/beyond-the-dark/custom-characters#importeer-de-mesh-naar-studio) . We stelden de materialen en texturen in na deze tests, maar je kunt het resultaat hieronder zien.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/tree-hierarchy.png) Dezelfde hiërarchie binnen Studio.

Nadat we tevreden waren met de resultaten op die boom, was het tijd om dezelfde animatie op een andere boom te testen! We wisten al dat het dezelfde animatie zou zijn tussen de verschillende rigs voor elk boomtype, dus we zorgden er gewoon voor dat onze animatie er algemeen genoeg uitzag om te werken tussen een hoge Redwood en een stevige Beukenboom!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/tree-animation-import.png) De animatie die we op de Redwood-boom hebben geïmporteerd.

Om dit te doen, namen we de Beukenboom uit dat Forest Pack en bouwden een vergelijkbare rig, waarbij we exact dezelfde naamgeving voor de gewrichten gebruikten. Dit was zodat de animatie die we eerder hadden geïmporteerd ook op deze boom kon worden toegepast. Aangezien de animaties allemaal gebaseerd waren op draaiende gewrichten, maakte het niet uit hoe groot, klein, hoog of breed de boom was!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/beechwood-joint-animation.png) De Beukenboom heeft exact dezelfde naamgeving voor zijn gewrichten, alleen niet dezelfde hoeveelheid. Dit is prima, aangezien het animatiesysteem alleen animatie toepast op die specifieke gewrichten die overeenkomen met de naam erin! Om deze reden konden we dezelfde animaties toepassen op alles wat overeenkwam met de gewrichtnamen!

Nadat we de [rig en skin](/docs/nl-nl/art/modeling/rigging)  van de Beukenboom hadden voltooid, konden we deze importeren en dezelfde animatie toepassen. Dit betekende dat iteratie en bewerking alleen op één bestand hoefden te worden gedaan, en het bespaarde ook op prestaties met minder animaties tijdens het spelen van het spel.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/redwood-tree-animation.png) Met behulp van de Animatie-editor  konden we dezelfde Redwood-boom animatie toepassen op de Beukenboom!

Zodra we alle boomtypes die we wilden animeren hadden, maakten we elk tot [pakketten](/docs/nl-nl/projects/assets/packages)  zodat we konden blijven bewerken en bijwerken terwijl we verschillende animaties rond het hoofdgebied van het spel afspeelden. Aangezien we wisten dat ze een prestatiekost hadden, gebruikten we ze spaarzaam rond het huis waar het effect het meest waardevol was! In de toekomst, naarmate dit meer performant wordt, zul je meer en meer geskinnde mesh-instanties kunnen toevoegen!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/animated-trees.png) We gebruikten geanimeerde bomen onmiddellijk rond het huis waar de vortex het sterkst was en het visuele effect het meest impactvol zou zijn voor spelers.

### [Maak stormpuin](#maak-stormpuin)[](#maak-stormpuin)

We wilden dat de regen zwaar leek, en dat de mist en het puin door de bomen waaiden. Om dit te doen, stelden we een paar onzichtbare onderdelen in om als deeltjesvolumes te fungeren met kind [deeltjesemitters](/docs/nl-nl/effects/particle-emitters)  direct onder de grote stormwolken. Vanwege de deeltjesaantal limiet in Studio, konden we niet één deeltjesemitter voor de hele ruimte gebruiken. In plaats daarvan voegden we verschillende toe die dezelfde grootte hadden in een rasterpatroon over het speelbare gebied, omdat de aanwezigheid van de bomen betekende dat de spelers niet ver konden zien.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/part-volumes.png) We gebruikten verschillende volumes om zowel de hoeveelheid regen te krijgen, als de specifieke dekking van regen die we wilden.

De regen deeltjes maakten gebruik van een nieuwe deeltjesemitter eigenschap [ParticleEmitter.Squash](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Squash)  die je in staat stelt om een deeltje langer of korter te maken. Het is bijzonder nuttig voor regen omdat het betekent dat we geen grote regen textuur nodig hadden, gewoon de aanwezige uitrekken. Weet gewoon dat als je de waarde van [ParticleEmitter.Squash](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Squash)  verhoogt, je mogelijk ook de algehele [ParticleEmitter.Size](/docs/nl-nl/reference/engine/classes/ParticleEmitter#Size)  eigenschap moet verhogen zodat het niet te dun is! Over het algemeen was het gewoon een kwestie van spelen met de waarden totdat we de regen zwaar genoeg kregen, maar niet zo veel dat het de zichtbaarheid van het spel blokkeerde!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/squash-3.png) Een Squash waarde van 3 begint de textuur langer te rekken.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/squash-20.png) Een Squash waarde van 20 rekt de deeltjes veel langer, maar we moesten ook de Size waarde verhogen.

Voor de mist, fog en bladeren die door de lucht waaien, was het veel eenvoudiger om een enkele grotere deelvolume toe te voegen die minder gebieden bedekte omdat we niet een ton deeltjes tegelijk nodig hadden. We begonnen met het opzetten van een volume en kregen de frequentie van de deeltjes waar we ze wilden.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/debris-volumes.png) Er waren uiteindelijk een paar deeltjesdeelvolumes zodat we geen deeltjes in het huis hadden, en omdat we niet vonden dat ze door de bomen moesten bewegen zoals de mist deed.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/fog-particle-volume.png) De mist deeltjesdeelvolume was veel groter omdat de deeltjes groot waren, en we niet zo precies hoefden te zijn met de locatie.

Daarna maakten we onze bladeren die waaien en windtexturen, en stelden de deeltjes in om allemaal met verschillende snelheden te draaien/bewegen en op verschillende snelheden te beginnen. Dit betekende dat de grotere mistdeeltjes natuurlijker zouden interageren en er niet zo veel uit zouden zien als een herhalende textuur, vooral gezien hun grootte.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/fog-particle.png) Fog deeltje

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/leaf-particle.png) Blad deeltje

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/particle-emitter-properties.png)

Het resultaat was een geweldige actie tussen de bomen die bewogen, de ramen die waaiden, en de bliksem om het effect van de storm rond het centrale oog van de storm te creëren.

### [Stel het oog van de storm in](#stel-het-oog-van-de-storm-in)[](#stel-het-oog-van-de-storm-in)

Het gebroken stenen oog met een gloeiende kern is bedoeld om spelers de eerste hint te geven dat er iets sinister en arcaan aan de hand is in het huis dat ze verder moeten verkennen. Aangezien onze scène donker is en het oog ver omhoog in de lucht is, was het belangrijk om een geloofwaardige gebroken stenen silhouet te creëren, maar het was niet zo belangrijk om geloofwaardige details van het stenen oppervlak te creëren omdat spelers dat niet zouden kunnen zien. Weten wat realistisch is voor je spelers om te zien binnen de verlichting van je scène voordat je veel tijd steekt in onnodige details kan je veel middelen besparen in het ontwikkelingsproces.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/eye-of-the-storm-1.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/eye-of-the-storm-2.png)

Het vroeg opzetten van de uiteindelijke verlichting in je scène kan je veel onnodig werk besparen. Je zou geen oppervlakdetails op de ringen kunnen zien met de uiteindelijke verlichting van onze scène, dus er was geen behoefte om tijd te besteden aan het plaatsen ervan!

De afstand van de speler betekende ook dat we volledig op een normaal kaart konden vertrouwen voor de oppervlakdetails van het oog, zodat de mesh gewoon een gewone bol is! We hebben de details in een hoog poly mesh gesculpteerd en de normaal kaart op een veel lagere poly bol gebakken, zodat we al die mooie details konden krijgen zonder de enorme prestatiekosten.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/high-poly-sculpt.png) Hoog poly sculpt

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/low-poly-mesh.png) Laag poly mesh

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/low-poly-mesh-with-normal-info.png) De laag poly mesh met de normaal informatie van de hoog poly sculpt gebakken

Om een bovennatuurlijk gevoel aan het oog toe te voegen en de aanwezigheid ervan te benadrukken, besloten we om een gloeiende, neon magma te creëren die door de scheuren sijpelde. Hoewel er geen emissiefunctie is voor oppervlakteverschijning, overkwamen we deze hindernis door het oog uit 2 bollen te maken: één voor het rotsachtige buitenoppervlak en een tweede, iets kleinere voor de gloeiende magma. In [Substance Painter](https://www.substance3d.com/)  creëerden we een basis kleurtextuur voor de buitenste bol met transparantie in de gebieden waar we wilden dat de binnenste kern doorheen kwam. In [Blender](https://www.blender.org)  "vertex painted" we de binnenste bol voor een goedkope en gemakkelijke manier om wat kleurvariatie erop te krijgen.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/vertex-painting.png) De vertex painting op de binnenste bol. We creëerden een gradient die het lichtste was rond het oog om een groter gevoel van diepte en visuele interesse te geven.

Een andere uitdaging waarmee we te maken kregen bij het creëren van het oog werd opgelegd door ons gebruik van [streaming](/docs/nl-nl/workspace/streaming)  in combinatie met de afstand van het oog van de speler. Gezien de centraliteit van deze structuur, wilden we dat deze altijd zichtbaar was ondanks de afstand, maar zonder enige hacks aan de mesh konden spelers het oog niet zien tenzij ze in de solarium waren. We konden de constante aanwezigheid van het oog in de scène afdwingen door wat geometrie aan het oog en zijn ringen toe te voegen. Deze geometrie zit net onder het oppervlak van het terrein, en dit is genoeg om de engine te misleiden om te denken dat de bol dichter bij de speler is dan hij is en altijd te streamen. Dit moet echter vrij spaarzaam worden gedaan, aangezien het forceren van te veel grote objecten om te worden gestreamd de voordelen van streaming kan tenietdoen en de prestaties negatief kan beïnvloeden.

We konden beweging aan het oog en zijn ringen toevoegen dankzij hetzelfde script dat we gebruikten om [de wolken meshes te roteren](#rotate-wolken-meshes) . Voor een laatste touch besloten we om een hint toe te voegen aan de aanwezigheid van een andere wereld achter de wolken, maar we moesten een creatieve benadering nemen om te voorkomen dat we meer geometrie aan de scène toevoegden en bovendien om te gaan met de eerder genoemde hindernissen die door streaming werden opgelegd. We creëerden een scène die veel diepte had door de relatieve grootte en afstand van objecten, renderden een afbeelding van deze scène, en gebruikten die afbeelding als een [decal](/docs/nl-nl/parts/textures-decals)  op een onderdeel dat net achter het oog van de storm was geplaatst. We gebruikten dezelfde methode voor het roteren van dit onderdeel als we gebruikten voor het oog en zijn ringen.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/illusion-image.png) De afbeelding die we gebruikten om een illusie van een wereld achter de wolken te creëren. Wanneer spelers ver weg zijn van iets, kan een eenvoudige afbeelding voldoende zijn om de illusie van meer diepte en complexiteit in je scène te creëren!

## [Maak de uitbreidbare voorraadkast](#maak-de-uitbreidbare-voorraadkast)[](#maak-de-uitbreidbare-voorraadkast)

Een van de leukste dingen om te produceren waren de corrupte ruimtes, waar we de verwachtingen van spelers over de realiteit letterlijk om hen heen konden ondermijnen. Bijvoorbeeld, in de puzzel van de vader wilden we een moment emuleren dat lijkt op een nachtmerrie waarin, ongeacht hoe snel je rent, de kamer lijkt steeds langer te worden. We besloten om een uitbreidbare voorraadkast te maken die van spelers weg zou rennen terwijl ze op zoek waren naar ingrediënten om de kamer weer in zijn normale staat te brengen.

We stelden dit in met een eenvoudige beweging van de muren, en een slimme indeling van onze kamers die aan beide zijden van de voorraadkast zouden verschijnen. In de normale staat van de kamer was de voorraadkast een eenvoudige gang, maar in de corrupte ruimte was het eigenlijk veel langer met verschillende vleugels en een valse muur!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/pantry-corrupt-state.png) De corrupte staat van de keuken voorraadkast.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/false-wall.png) De valse muur die van spelers weg beweegt.

De valse muur was een modelgroep die we naar achteren zouden verplaatsen op het moment dat spelers een triggervolume binnenkwamen, wat een transparant onderdeel was eerder in de voorraadkast waar ze doorheen zouden lopen. Die trigger werd ook gebruikt in een script dat vergelijkbaar was met die op al onze deuren, die de [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  aanriep om van het ene doel naar het andere te bewegen. We gebruikten deelvolumes om de tween-operatie te vertellen waar de start- en eindposities waren voor de muur.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/yellow-part-volume.png) Het deelvolume triggert een valse muur erachter om naar zijn eindpunt te bewegen. Het is zichtbaar gemaakt in deze afbeelding met een gele tint.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/target-closed.png) Target_Closed was een generiek doelonderdeel dat we op al onze deuren gebruikten voor waar ze moesten draaien. Hier werd het hergebruikt om de gangmuur te vertellen waarheen te gaan.

Omdat [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  zo'n algemeen systeem is, hoefde al onze muurgegevensmodellen alleen maar dezelfde componenten te bevatten. Bijvoorbeeld, een algemeen "Door_Script" script speelt een geluid dat is gedefinieerd door een "waarde" onder het "Grow_Wall" model. Datzelfde script, met enkele aanpassingen in het volgende codevoorbeeld, activeerde ook audio voor de voorraadkast die bewoog. Dit voegde veel toe aan de beweging!

```

local Players = game:GetService("Players")

local TweenService = game:GetService("TweenService")

local model = script.Parent

local sound = model.Sound.Value

local trigger = model.Trigger

local left = model.TargetL_Closed

local right = model.TargetR_Closed

local tweenInfo = TweenInfo.new(

	model.Speed.Value, -- Tijd/Snelheid van de Deur Tween

	Enum.EasingStyle.Quart, -- Easing Style

	Enum.EasingDirection.InOut, -- EasingDirection

	0, -- Herhaal aantal

	false, -- Omgekeerd waar

	0 -- Vertraging

)

local DoorState = {

	["Closed"] = 1,

	["Opening"] = 2,

	["Open"] = 3,

	["Closing"] = 4,

}

local doorState = DoorState.Closed

local playersNear = {}

local tweenL = TweenService:Create(left, tweenInfo, {CFrame = model.TargetL_Open.CFrame})

local tweenR = TweenService:Create(right, tweenInfo, {CFrame = model.TargetR_Open.CFrame})

local tweenLClose = TweenService:Create(left, tweenInfo, {CFrame = model.TargetL_Closed.CFrame})

local tweenRClose = TweenService:Create(right, tweenInfo, {CFrame = model.TargetR_Closed.CFrame})

local function StartOpening()

	doorState = DoorState.Opening

	sound:Play()

	tweenL:Play()

	tweenR:Play()

end

local function StartClosing()

	doorState = DoorState.Closing

	--model["Door"]:Play()

	tweenLClose:Play()

	tweenRClose:Play()

end

local function tweenOpenCompleted(playbackState)

	if next(playersNear) == nil then

		StartClosing()

	else

		doorState = DoorState.Open

	end

end

local function tweenCloseCompleted(playbackState)

	if next(playersNear) ~= nil then

		StartOpening()

	else

		doorState = DoorState.Closed

	end

end

tweenL.Completed:Connect(tweenOpenCompleted)

tweenLClose.Completed:Connect(tweenCloseCompleted)

local function touched(otherPart)

	if otherPart.Name == "HumanoidRootPart" then

		local player = Players:GetPlayerFromCharacter(otherPart.Parent)

		if player then

			--print("aanraken")

			playersNear[player] = 1

			if doorState == DoorState.Closed then

				StartOpening()

			end

		end

	end

end

```

Zodra we de valse muur naar de achterkant van de kamer hadden verplaatst, moesten we de rest van de inhoud met hem mee laten bewegen. Om dat te doen, moesten we alle losse items op de voorraadkast aan de muur lassen terwijl deze bewoog. Door gebruik te maken van [Weld Constraints](/docs/nl-nl/physics/mechanical-constraints#weldconstraint) , konden we snel alle objecten aan de voorraadkastwand lassen zodat ze als één object bewogen. Dit betekende dat we de optie hadden om deze items weer los te maken zodat spelers er tegenaan konden botsen en ze omver konden duwen!

## [Maak de corrupte boomhut](#maak-de-corrupte-boomhut)[](#maak-de-corrupte-boomhut)

Studio is een fantastische fysisch gebaseerde engine die je kunt gebruiken om alles te creëren, van een zwaaiende poort tot een draaiend platform. Met onze demo wilden we fysica gebruiken om een gevoel van realisme te creëren in een anders onrealistische set omgevingen. Met slechts een paar beperkingen  kun je enkele leuke en uitdagende hindernisbanen binnen je eigen spellen creëren!

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/obstacle-course.png)

[Beperkingen](/docs/nl-nl/physics/mechanical-constraints)  zijn een groep fysisch gebaseerde motoren die objecten uitlijnen en gedragingen beperken. Je kunt bijvoorbeeld een [stangbeperking](/docs/nl-nl/physics/mechanical-constraints#rodconstraint)  gebruiken om verbinding te maken met objecten om ze op een vaste afstand van elkaar te houden, of de [touwbeperking](/docs/nl-nl/physics/mechanical-constraints#ropeconstraint)  om een lamp aan het einde van de lijn te laten hangen. Voor de puzzel van de zoon waarin spelers worden getransporteerd naar de corrupte staat van de studeerkamer, wilden we de wereld letterlijk op zijn kant draaien. Dit zou de verwachtingen van spelers over de realiteit en de regels daaronder ondermijnen, terwijl we nog steeds het fysicasysteem gebruikten zoals het bedoeld was!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/son-puzzle.png) De puzzel van de zoon begon met de spelers in dezelfde kamer, maar alles was zijwaarts.

Zodra spelers naar het hoofdgebied van de puzzel werkten, werden ze begroet met een vertrouwd gezicht op Roblox: een hindernisbaan. Deze specifieke hindernisbaan bestond uit verschillende draaiende platforms en roterende muren, samen met "veilige gebieden" die het verhaal voortzetten. We zullen ons concentreren op de roterende/draaiende elementen.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/spinning-elements.png) Het geestverruimende uiterlijk verbergt het feit dat de gameplay hier heel eenvoudig was.

Waarom hebben we hier beperkingen gebruikt? Omdat [TweenService](/docs/nl-nl/reference/engine/classes/TweenService)  of andere methoden de speler niet zouden verplaatsen terwijl ze erop stonden. Zonder het object dat de speler beweegt, zou iemand op een platform kunnen springen en het zou onder hen wegdraaien. In plaats daarvan wilden we dat spelers door een draaiend platform navigeerden terwijl ze probeerden hun sprong naar de volgende te maken. Vanwege deze aanpak voelden spelers zich verankerd waar ze stonden terwijl ze een beslissing namen over hoe verder te gaan door de baan, en we hoefden niets speciaals te doen om ervoor te zorgen dat ze met een roterend oppervlak meebeweegen!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/friends-spinning.png) Je kon je vrienden zien draaien terwijl ze ook probeerden de hindernisbaan te navigeren.

Om dit te doen, moesten we eerst activa uit onze huidige kit gebruiken en eventuele nieuwe inhoud toevoegen voor een visueel effect. We maakten een paar onvolledige muren en platforms met gaten erin om het verhaal van de grootmoeder die de boomhut bouwde te vertellen. Omdat we geen heleboel unieke platforms wilden maken, maakten we 4 verschillende basisstukken en leuningstukken afzonderlijk. Dit stelde ons in staat om individuele basis- en leuningstukken te mixen en matchen voor veel variatie.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/base-piece.png)

We wisten dat we, aangezien we beperkingen gebruikten, deze meshes niet konden verankeren omdat ze niet zouden bewegen, zelfs niet met de aanwezigheid van een beperking/motor die ze aandreef. De beperking moest een kind zijn van iets dat verankerd was om ervoor te zorgen dat het platform niet gewoon uit de wereld viel. We losten dit op door een onderdeel te maken dat we Motor_Anchor  noemden dat een [scharnierbeperking](/docs/nl-nl/physics/mechanical-constraints#hingeconstraint)  had om de algehele beweging van het platform aan te drijven. Daarna moesten we de twee meshes als één laten bewegen, dus we creëerden een onderdeel dat we Motor_Turn  noemden, en vervolgens lassen we de twee meshes eraan. Op deze manier kon de beperking op een enkel onderdeel werken, in plaats van meerdere scharnieren die met meerdere onderdelen werkten.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/unanchored-platform.png)

Het was nu tijd om het daadwerkelijke gedrag van de scharnierbeperking zelf in te stellen, en de bevestigingen toe te voegen die zouden fungeren als de oriëntatie van het onderdeel en de beperking samen. We plaatsten de draaiende bevestiging op de Motor_Turn, waaraan de loopbrugstukken waren gelast, en een andere bevestiging voor het anker gedrag op de Motor_Anchor zelf, naast de scharnierbeperking. Aangezien dit op zichzelf moest draaien, in plaats van beïnvloed te worden door de speler (zoals een deur scharnier), stelden we de [HingeConstraint.ActuatorType](/docs/nl-nl/reference/engine/classes/HingeConstraint#ActuatorType)  in op Motor , waarbij we de beperking als een zelfbewegende motor behandelden.

Om de platforms met een constante snelheid te laten draaien, stelden we vervolgens de [HingeConstraint.AngularVelocity](/docs/nl-nl/reference/engine/classes/HingeConstraint#AngularVelocity) , [HingeConstraint.MotorMaxAcceleration](/docs/nl-nl/reference/engine/classes/HingeConstraint#MotorMaxAcceleration) , en [HingeConstraint.MotorMaxTorque](/docs/nl-nl/reference/engine/classes/HingeConstraint#MotorMaxTorque)  eigenschappen in op waarden die beweging mogelijk maakten en onderbreking voorkwamen als een speler erop sprong.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/hingeconstraint-properties.png) Attachment0 was in wezen het anker voor de scharnier en Attachment1 vertegenwoordigde de scharnier zelf. We hadden de scharnier constant laten draaien, maar je kunt ook een scharnierbeperking voor deuren gebruiken.

Nu moesten we de roterende muren maken. De muren moesten draaien om hun schijnbare centrum, en we wisten dat we ze moesten kunnen laten omgaan met elke oriëntatie ten opzichte van de rest van het niveau. Net als de platforms, bouwden we deze zodat alle muren niet verankerd waren en aan de Motor_Turn waren gelast.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/treehouse-mesh.png) We wilden zoveel mogelijk van de daadwerkelijke boomhut meshes hergebruiken om op prestaties te besparen, dus volgden we een vergelijkbaar pad als de platforms. Verschillende muurtipes werden gemaakt die in verschillende combinaties aan elkaar konden plakken voor wat variatie.

We gebruikten [Texture](/docs/nl-nl/reference/engine/classes/Texture)  objecten bovenop [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  objecten om wat variatie aan onze basismaterialen toe te voegen. [Texturen](/docs/nl-nl/parts/textures-decals) , vergelijkbaar met Decals, stellen je in staat om een afbeelding op een vlak van een mesh te plaatsen. Dit kan nuttig zijn als je vuil aan een bakstenen muur wilt toevoegen, of hout er verouderd uit wilt laten zien terwijl je hetzelfde basishoutmateriaal gebruikt. [Texture](/docs/nl-nl/reference/engine/classes/Texture)  objecten hebben een iets ander gedrag dan [Decal](/docs/nl-nl/reference/engine/classes/Decal)  objecten in die zin dat je de afbeelding kunt tegelen en offsetten zoals je wilt, wat erg nuttig is als je je overlay-textuur wilt kunnen schalen en het niet erg vindt dat het herhaald wordt!

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/treehouse-texture.png) Je kunt zowel het vergelijkbare gedrag en de opstelling voor de scharnierbeperking zien, alsook hoe we [Texture](/docs/nl-nl/reference/engine/classes/Texture)  objecten gebruikten.

Zodra we een paar platforms en roterende muren hadden getest, maakten we verschillende variaties en speelden met hun plaatsing om ervoor te zorgen dat de hindernisbaan uitdagend, geestverruimend en ook duidelijk was waar de speler heen moest! Het kostte wat afstemming van zowel hun waarden als posities om ervoor te zorgen dat ze goed werkten. We hadden verschillende punten waar de platforms en muren elkaar of de omgeving raakten, maar met wat verplaatsingen en frequente tests konden we de instellingen vinden die we in de demo hebben!

Als je niet zeker weet wat je fysieke objecten raken, kun je Collision fidelity  inschakelen vanuit de [Visualisatie Opties](/docs/nl-nl/studio/overview#visualisatie-opties)  widget in de rechterbovenhoek van het 3D-viewport.

 ![Een close-up van het 3D-viewport met de Visualisatie Opties knop aangegeven in de rechterbovenhoek.](https://prod.docsiteassets.roblox.com/assets/studio/general/Visualization-Options.png)

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/show-decomposition-geometry-disabled.png) Wanneer de collision visualisatie is uitgeschakeld, zie je de normale geometrie representatie die in-game wordt weergegeven.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/show-decomposition-geometry-enabled.png) Wanneer de collision visualisatie is ingeschakeld, zie je dat de boombladeren geen botsingen hebben, zodat ze de draaiende platforms of muren niet kunnen verstoren.

Zoals je kunt zien, zijn de deur- en vensteropeningen zichtbaar, maar de kleinere details zoals de sub-paneling zijn dat niet. Dit komt omdat de CollisionFidelity  eigenschap voor de muren was ingesteld op Box . We hadden de precisie voor deze panelen niet nodig, dus om op prestatiekosten te besparen, was dit gedetailleerd genoeg voor spelers om op te springen. Met de platforms en roterende muren klaar, hoefden we alleen nog maar detailactiva zoals dozen en lampen toe te voegen, en toen was het klaar om gespeeld te worden!

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/developing-a-moving-world/collision-fidelity-treehouse.png)

[Volgende](/docs/nl-nl/resources/the-mystery-of-duvall-drive/design-dark-soundscapes)[Vorige](/docs/nl-nl/resources/the-mystery-of-duvall-drive/stream-in-immersion)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
