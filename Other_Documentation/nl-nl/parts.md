<!-- Source: https://create.roblox.com/docs/nl-nl/parts -->

Onderdelen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Delen](/docs/nl-nl/parts)

# Onderdelen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[Onderdelen](/docs/nl-nl/reference/engine/classes/Part)  zijn afstammelingen van de [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  klasse en zijn de primitieve bouwstenen van Roblox met eigenschappen zoals positie, grootte, oriëntatie en kleur. Je kunt basisonderdelen gebruiken zoals ze zijn, of je kunt [solide modellering](/docs/nl-nl/parts/solid-modeling)  operaties toepassen om onderdelen te combineren tot complexere vormen.

Voor geavanceerde en ingewikkelde 3D-modellen kun je ook modelbestanden van derden importeren als [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart) , zoals beschreven in [Meshes](/docs/nl-nl/parts/meshes) .

![Een enkele grijze bolvormige onderdeel](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Sphere.png) Basis bolvormig onderdeel

![Een heldere blauwe holle kom die is gemaakt met solide modellering operaties.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Part-Example-CSG.jpg) Kom gemaakt met solide modellering

![Een hoogwaardige schatkist mesh met een textuur.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Mesh-Example.jpg) Mesh met textuur

Standaard zijn onderdelen stijve lichamen die de fysieke mechanica van de echte wereld volgen, inclusief zwaartekracht, botsingen en momentum. Je kunt gerelateerde onderdelen aan elkaar verbinden als een enkele [assemblage](/docs/nl-nl/physics/assemblies)  met behulp van een [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint) , of een gewricht zoals [Motor6D](/docs/nl-nl/reference/engine/classes/Motor6D)  of [Bone](/docs/nl-nl/reference/engine/classes/Bone) . Als een assemblage fungeren de verbonden onderdelen als één stijve entiteit, die verwijst naar een gemeenschappelijke positie, oriëntatie en schaal.

Je kunt een [Model](/docs/nl-nl/reference/engine/classes/Model)  container gebruiken om gerelateerde onderdelen samen te groeperen en de groep als een enkele assemblage in de [Explorer](/docs/nl-nl/studio/explorer)  te benaderen. Zie [Modellen](/docs/nl-nl/parts/models)  voor meer informatie.

## [Basis onderdeel types](#basis-onderdeel-types)[](#basis-onderdeel-types)

[Part](/docs/nl-nl/reference/engine/classes/Part)  objecten kunnen de vorm aannemen van blokken, bollen, cilinders, wiggen of hoekwiggen. Daarnaast fungeert [TrussPart](/docs/nl-nl/reference/engine/classes/TrussPart)  als een trussbalk waar karakters op kunnen klimmen als een ladder.

![Een enkele blok onderdeel.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Block.png) Blok

![Een enkele bol onderdeel.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Sphere.png) Bol

![Een enkele cilinder onderdeel.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Cylinder.png) Cilinder

![Een enkele wig onderdeel.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Wedge.png) Wig

![Een enkele hoekwig onderdeel.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Basic-Part-Corner-Wedge.png) Hoekwig

## [Onderdeel eigenschappen](#onderdeel-eigenschappen)[](#onderdeel-eigenschappen)

Elk onderdeel heeft een verscheidenheid aan eigenschappen die je kunt aanpassen via het [Eigenschappen](/docs/nl-nl/studio/properties)  venster.

 ![Een close-up van het Eigenschappen venster met de Verschijning en Transform eigenschappen gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Sections-Example.png)

De volgende zijn veelgebruikte eigenschappen:

-

[Anchored](/docs/nl-nl/reference/engine/classes/BasePart)  bepaalt of de fysica de positie van het onderdeel beïnvloedt. Wanneer deze eigenschap is ingesteld op waar, verandert de positie van het onderdeel nooit door zwaartekracht of enige andere kracht. Je moet de meeste onderdelen in je spel verankeren, anders zullen zwaartekracht en fysica je onderdelen beïnvloeden zodra het spel draait.

Om verlichte omtrekken rond de basis van verankerde onderdelen te bekijken om te visualiseren welke onderdelen niet kunnen bewegen onder zwaartekracht of fysica, schakel Verankerde onderdelen  in vanuit de [Visualisatie opties](/docs/nl-nl/studio/overview#visualisatie-opties)  widget in de rechterbovenhoek van het 3D-venster.

-

[CanCollide](/docs/nl-nl/reference/engine/classes/BasePart)  bepaalt of een onderdeel kan botsen met andere onderdelen. Wanneer deze eigenschap is ingesteld op waar, is het onderdeel ondoordringbaar en houdt de fysica-engine hier rekening mee binnen je spel. Omgekeerd, wanneer deze eigenschap is ingesteld op onwaar, kan het onderdeel door alles heen gaan, en houdt de fysica-engine hier geen  rekening mee.

-

[Transparency](/docs/nl-nl/reference/engine/classes/BasePart)  stelt de zichtbaarheid van een onderdeel in op een waarde tussen de standaardwaarde van 0 (volledig zichtbaar) en 1 (volledig transparant). Als je veel gedeeltelijk transparante onderdelen hebt, kan dit de prestaties vertragen. Om dit te verhelpen, kun je ze samenvoegen met behulp van [solide modellering](/docs/nl-nl/parts/solid-modeling) .

## [Onderdelen invoegen](#onderdelen-invoegen)[](#onderdelen-invoegen)

De Onderdeel  invoegknop, toegankelijk vanuit de Start  en Model  tabbladen, voegt een nieuw onderdeel toe aan de werkruimte. Klik en houd de kleine hoekpijl op de knop ingedrukt om te kiezen tussen Blok , Bol , Wig , Hoek Wig , of Cilinder .

 ![Onderdeel gereedschap en zijn onderdeel type keuzemenu.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Insert-Part-Widget.png)

Om een [TrussPart](/docs/nl-nl/reference/engine/classes/TrussPart)  in te voegen (niet beschikbaar in het invoegmenu), gebruik de [Explorer](/docs/nl-nl/studio/explorer)  zoals beschreven [hier](/docs/nl-nl/studio/explorer#insert-and-parent) .

## [Onderdelen selecteren](#onderdelen-selecteren)[](#onderdelen-selecteren)

Wanneer je over onderdelen in het 3D-venster beweegt, worden ze omrand om hun potentiële selectie aan te geven. Je kunt een omrand onderdeel selecteren door erop te klikken, of je kunt meerdere onderdelen selecteren door Shift , Ctrl , of ⌘  ingedrukt te houden terwijl je erover beweegt en erop klikt. Voor geavanceerde methoden om onderdelen in het venster te selecteren, zie [objectselectie](/docs/nl-nl/studio/overview#objectselectie) .

 ![Meerdere modellen geselecteerd in het 3D-venster](https://prod.docsiteassets.roblox.com/assets/studio/general/Editor-Window-Object-Selection.jpg)

## [Onderdelen transformeren](#onderdelen-transformeren)[](#onderdelen-transformeren)

Je kunt geselecteerde onderdelen verplaatsen, schalen en roteren, hetzij via modelleringstools of door een nieuwe positie, grootte of oriëntatie in te stellen in het [Eigenschappen](#onderdeel-eigenschappen)  venster.

 ![Transformeertools aangegeven in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Transform-Tools.png)

![Verplaatsingsdragers weergegeven op onderdeel in 3D-venster.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Move-SM.png) Verplaatsen

![Schaaldragers weergegeven op onderdeel in 3D-venster.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Scale-SM.png) Schaal

![Rotatiedragers weergegeven op onderdeel in 3D-venster.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Rotate-SM.png) Roteren

Bij het gebruik van de tools kun je onderdelen verplaatsen, schalen of roteren in wereld  oriëntatie of lokale  oriëntatie door Ctrl L  op Windows of ⌘ L  op Mac in te drukken. Wanneer je lokale oriëntatie inschakelt, veranderen de pijl-asindicatoren naar de lokale oriëntatie van een onderdeel, en wordt een L  indicator weergegeven.

Wereld Lokaal

![Een schuin blok onderdeel met dragers in Wereld oriëntatiemodus.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Move-World-Orientation.png)

De transformeer snapping  intervallen zijn gebaseerd op studs  voor verplaatsen/schalen of graden  voor roteren, elk aanpasbaar in de werkbalk. Tijdens het transformeren kun je tijdelijk snapping in- of uitschakelen door de Shift  toets ingedrukt te houden.

 ![Transformeer snapping tools aangegeven in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Transform-Snapping.png)

Om snel naar de verplaats/schaal  increment invoer te springen, druk op Shift 2 . Om snel naar de rotate  increment invoer te springen, druk op Alt R  (Windows) of ⌥ R  (Mac).

### [Verplaatsen](#verplaatsen)[](#verplaatsen)

Je kunt een geselecteerd onderdeel naar een nieuwe positie verplaatsen met behulp van de Verplaats  tool (standaard sneltoets 2 ) of door cursor verslepen . Terwijl je een onderdeel verplaatst, kun je tijdelijk snapping in- of uitschakelen door Shift  ingedrukt te houden.

Verplaats Tool Cursor Versleep

Om een onderdeel langs de X , Y , of Z  as te verplaatsen met een asdrager, klik/versleep een pijl die langs de gewenste bewegingsas wijst.

![Een blok onderdeel met de visuele hulpmiddelen van de Verplaats tool.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Move.png)

Na het loslaten van de sleep, blijft de numerieke afstandindicator  zichtbaar. Indien gewenst, kun je de afstand die is verplaatst verfijnen door op de indicator te klikken en een getal in te voeren.

![Een verplaatst onderdeel dat de verplaatste afstand in een indicator/invoerveld toont](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Move-Indicator.png)

Als je een onderdeel sleept via het [pivot](/docs/nl-nl/studio/pivot-tools)  punt terwijl de Verplaats  tool is geselecteerd, zal de pivot "zacht snappen" naar oppervlakken en randen van nabijgelegen onderdelen.

![Een blok onderdeel met een offset pivot die zacht-snap naar het oppervlak van een nabijgelegen onderdeel.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Move-Pivot-Snap.png)

### [Schalen](#schalen)[](#schalen)

Om een geselecteerd onderdeel langs de X , Y , of Z  as te schalen (vergroten/verkleinen), gebruik de Schaal  tool (standaard sneltoets 3 ) en klik/versleep een handvat. Terwijl je sleept, kun je tijdelijk snapping in- of uitschakelen door Shift  ingedrukt te houden.

 ![Een blok onderdeel met de visuele hulpmiddelen van de Schaal tool.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Scale.png)

### [Roteren](#roteren)[](#roteren)

Om een geselecteerd onderdeel rond de X , Y , of Z  as te roteren, gebruik de Roteren  tool (standaard sneltoets 4 ) en klik/versleep een rotatiering. Terwijl je sleept, kun je tijdelijk snapping in- of uitschakelen door Shift  ingedrukt te houden.

 ![Een blok onderdeel met de visuele hulpmiddelen van de Roteren tool.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Transform-Rotate.png)

Naast het gebruik van de Roteren  tool, kun je geselecteerde objecten snel 90° roteren rond hun X  as door Ctrl T  (⌘ T ) in te drukken of 90° rond hun Y  as door Ctrl R  (⌘ R ) in te drukken.

## [Andere acties](#andere-acties)[](#andere-acties)

### [Groeperen](#groeperen)[](#groeperen)

Je kunt objecten groeperen in een [model](/docs/nl-nl/parts/models)  door ze te selecteren en op de Groep  knop te klikken. Deze actie heeft een standaard sneltoets van Ctrl G  (Windows) of ⌘ G  (Mac).

Alternatief kun je objecten groeperen in een [map](/docs/nl-nl/studio/explorer#organizing-by-folders)  door de kleine hoekpijl op de knop ingedrukt te houden en Groep als Map  te selecteren (standaard sneltoets van Alt Ctrl G  of ⌥ ⌘ G ).

 ![Groep tool aangegeven in de werkbalk van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Group.png)

Om een bestaande model of map te ongroeperen , selecteer Ongroeperen  in het Bewerken  menu (standaard sneltoets van Ctrl U  of ⌘ U ).

### [Verankeren](#verankeren)[](#verankeren)

De Verankeren  schakelaar bepaalt of het onderdeel onverplaatsbaar  is door fysica. Wanneer [Verankerd](/docs/nl-nl/reference/engine/classes/BasePart#Anchored) , zal een onderdeel nooit van positie veranderen door zwaartekracht, botsingen met andere onderdelen, overlappen met andere onderdelen, of enige andere fysica-gerelateerde oorzaken. Deze actie heeft een standaard sneltoets van Alt A  (Windows) of ⌥ A  (Mac).

 ![Verankeren schakelaar aangegeven in de werkbalk van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Anchor.png)

Als je de voorkeur geeft aan een klik-om-te-schakelen workflow in het 3D-venster, klik en houd de kleine hoekpijl op de Verankeren  knop ingedrukt en schakel Klik object om te verankeren  in. Zodra dit is ingeschakeld, werkt de tool als een "sleutel" voor beide toestanden — klikken op een niet-verankerd object in het venster verankert het, terwijl klikken op een verankerd object het ontverankert.

### [Kleur](#kleur)[](#kleur)

Terwijl een onderdeel standaard grijs is, kun je het veranderen in elke kleur via de volgende methoden.

Kleurknop Kleur Popup RGB Waarde

Door op de Kleur  knop te klikken, wordt de geselecteerde kleur toegepast op alle geselecteerde onderdelen. Je kunt een kleur kiezen door de kleine hoekpijl op de Kleur  knop ingedrukt te houden om een hexagonale picker te onthullen.

![Hexagonale picker van de kleur widget.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Color-Picker.png)

Als je de voorkeur geeft aan een vul/verf workflow in het 3D-venster, schakel dan Klik object om kleur toe te passen  in onderaan de popup van de hexagonale picker en klik vervolgens op onderdelen in het venster om de gekozen kleur toe te passen.

### [Materiaal](#materiaal)[](#materiaal)

Vergelijkbaar met [kleur](#kleur) , kun je het [materiaal](/docs/nl-nl/parts/materials)  van een onderdeel aanpassen om echte materialen zoals hout, glas of stof te simuleren. Door de kleine hoekpijl op de Materiaal  knop ingedrukt te houden, wordt de [materiaal](/docs/nl-nl/parts/materials)  picker onthuld.

 ![Picker van de materiaal widget gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Material-Picker.png)

Bij het selecteren van een materiaal, houd rekening met het volgende:

-

Materiaal beïnvloedt de fysieke eigenschappen van een onderdeel, niet alleen het uiterlijk . Bijvoorbeeld, het [Beton](/docs/nl-nl/reference/engine/enums/Material#Concrete)  materiaal is zwaarder dan het [Plastic](/docs/nl-nl/reference/engine/enums/Material#Plastic)  materiaal, dus een betonnen baksteen zal een hogere dichtheid hebben dan een plastic baksteen en sneller in water zinken.

-

Sommige materialen hebben speciale fysieke effecten. Bijvoorbeeld, onderdelen zullen lijken te gloeien als ze zijn ingesteld op het [Neon](/docs/nl-nl/reference/engine/enums/Material#Neon)  materiaal.

![Een schuin rood blok onderdeel met een glad plastic materiaal.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Material-SmoothPlastic.png) GladPlastic

![Een schuin rood blok onderdeel met een gloeiend neon materiaal.](https://prod.docsiteassets.roblox.com/assets/modeling/parts/Material-Neon.png) Neon

Zie [Materialen](/docs/nl-nl/parts/materials)  voor meer informatie over hoe je zowel standaard als aangepaste materialen op onderdelen kunt toepassen.

### [Vergrendelen](#vergrendelen)[](#vergrendelen)

De Vergrendelen  schakelaar bepaalt of het onderdeel kan worden geselecteerd vanuit het 3D-venster. Deze actie heeft een standaard sneltoets van Alt L  (Windows) of ⌥ L  (Mac).

 ![Vergrendel tool aangegeven in de werkbalk van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Lock.png)

Als je de voorkeur geeft aan een klik-om-te-schakelen workflow in het 3D-venster, klik en houd de kleine hoekpijl op de Vergrendelen  knop ingedrukt en schakel Klik object om te vergrendelen  in. Zodra dit is ingeschakeld, werkt de tool als een "sleutel" voor beide toestanden — klikken op een ontgrendeld object in het venster vergrendelt het, terwijl klikken op een vergrendeld object het ontgrendelt.

Om alle objecten te ontgrendelen, selecteer Ontgrendel Alles  in het Bewerken  menu.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
