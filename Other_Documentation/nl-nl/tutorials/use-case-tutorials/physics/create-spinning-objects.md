<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/physics/create-spinning-objects -->

Maak draaiende objecten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Fysica

# Maak draaiende objecten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Draaiende objecten  zijn objecten die om een of meer assen binnen de 3D-ruimte draaien. Met de ingebouwde kracht van de simulatiemotor van Roblox kun je objecten laten draaien en interactie laten hebben met hun omgeving op een manier die het gedrag van de echte wereld emuleert, wat vertrouwd en intuïtief is voor spelers, zoals zwaartekracht, aerodynamica en wrijving.

Met het [Draaiende Objecten](https://www.roblox.com/games/16550477904/Spinning-Objects)  .rbxl -bestand als referentie, legt deze tutorial uit hoe fysieke krachten de hoeksnelheid in Studio beïnvloeden, en laat je verschillende technieken zien om objecten in je spellen te laten draaien met verschillende draai-gedragingen, inclusief richtlijnen over:

-

Het gebruik van een [AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity)  mover-constraint om een hele assemblage met een constante hoeksnelheid te laten draaien.

-

Het gebruik van een [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  mechanische constraint om een onderdeel binnen een assemblage met een constante hoeksnelheid te laten draaien terwijl de rest van de assemblage stil blijft staan.

-

Het gebruik van de [ApplyAngularImpulse](/docs/nl-nl/reference/engine/classes/BasePart#ApplyAngularImpulse)  methode om een assemblage te laten draaien met een initiële impuls van hoekkracht, zodat de assemblage in de loop van de tijd langzaam afremt.

Je kunt je eigen assemblages maken met basisonderdelen of meshes van externe modelleringstools, en vervolgens met je eigen assets aan de slag gaan. Voor informatie over het exporteren van meshes voor gebruik in Studio, zie [Exportvereisten](/docs/nl-nl/art/modeling/export-requirements) .

## [Hoeksnelheid en fysieke krachten](#hoeksnelheid-en-fysieke-krachten)[](#hoeksnelheid-en-fysieke-krachten)

Roblox Studio is een simulatiemotor die het fysieke gedrag in real-time emuleert, dus om het gedrag van draaiende objecten in spellen te voorspellen, is het belangrijk om een algemeen begrip te hebben van hoe objecten in het echte leven draaien met hoeksnelheid.

Hoeksnelheid , of rotatiebeweging, is beweging rond een vast punt of as. Bijvoorbeeld, wanneer een propeller hoeksnelheid heeft, draait deze rond zijn rotatie-as in het midden van de propeller.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/Rotational-Axis.png)

Hoeksnelheid kan niet bestaan zonder externe, fysieke krachten die objecten duwen of trekken om te draaien. Volgens de [eerste wet van Newton](https://en.wikipedia.org/wiki/Newton%27s_laws_of_motion#First_law)  blijven stilstaande objecten stil en bewegende objecten blijven in beweging met een constante snelheid, tenzij ze worden beïnvloed door een externe kracht. Bijvoorbeeld, een stilstaande propeller blijft stil tenzij een fysieke kracht zoals wind deze duwt om te draaien.

Koppel  is de maat voor de fysieke kracht die objecten laat draaien, en het is verantwoordelijk voor het verkrijgen van hoeksnelheid. Dit concept is bijzonder belangrijk voor objecten om te draaien in Studio; hoe meer koppel je op objecten toepast, hoe sneller ze kunnen versnellen.

Dit komt omdat koppel * groter*  moet zijn dan alle directionele fysieke krachten die tegen het object inwerken, zoals zwaartekracht of wrijving. Bijvoorbeeld, als je de propeller in de grond plaatst, moet de fysieke kracht van de wind de hoeveelheid wrijving van de grond overwinnen om de draaiende propeller te blijven versnellen. Als de kracht van de wind niet veel groter is dan de wrijving van de grond, versnelt de propeller, maar langzamer dan in het vorige voorbeeld.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/Dirt-Friction.png)

Hoeksnelheid  is de maat voor de rotatiesnelheid van een object, of hoe snel het object rond een vast punt of as draait over een bepaalde tijd. Studio meet hoeksnelheid aan de hand van hoeveel [radians](https://en.wikipedia.org/wiki/Radian)  een object per seconde draait. Er zijn 2π radians (6.283) in één rotatie, dus om een object een volledige rotatie per seconde te laten maken, moet het genoeg koppel hebben om ongeveer 6 radians te draaien. Het begrijpen van hoeksnelheid is belangrijk voor het ontwerpen van gameplay in je spellen, omdat het je helpt bepalen hoeveel koppel je nodig hebt om een bepaalde versnelling voor je draaiende objecten te bereiken.

De volgende secties gaan dieper in op deze concepten terwijl je leert hoe je objecten kunt laten draaien met een constante of initiële hoeksnelheid met het nodige koppel om eventuele tegenwerkende fysieke krachten in de omgeving te overwinnen. Terwijl je deze fysica-concepten met de komende technieken bekijkt, kun je nauwkeuriger voorspellen hoe je eigenschapswaarden kunt aanpassen om een ideaal draai-gedrag in Studio te bereiken.

## [Handhaaf een constante hoekkracht](#handhaaf-een-constante-hoekkracht)[](#handhaaf-een-constante-hoekkracht)

Om een object een constante hoeksnelheid te laten bereiken en handhaven, heeft het een hoekkracht nodig om eventuele tegenwerkende fysieke krachten te overwinnen die de hoeksnelheid van het object afremmen of ervoor zorgen dat het object stil blijft staan. Bijvoorbeeld, als je wilt dat een object een hoeksnelheid van [0, 12, 0]  in Studio heeft, heb je genoeg koppel nodig zodat het object 12  radians per seconde langs de Y-as in zijn omgeving kan bereiken en handhaven, of ongeveer twee volledige rotaties per seconde.

De hoeveelheid koppel die je op je objecten toepast, hangt niet alleen af van tegenwerkende fysieke krachten binnen de omgeving zelf, zoals zwaartekracht en wrijving, maar ook van het object zelf. Bijvoorbeeld, als je twee objecten van dezelfde vorm hebt die op dezelfde as draaien, vereist het grotere object met een grotere [traagheidsmoment](https://en.wikipedia.org/wiki/Moment_of_inertia)  meer koppel om dezelfde hoeksnelheid te bereiken.

Het kleine driehoekige onderdeel heeft een lager traagheidsmoment, dus het heeft minder hoekkracht nodig om dezelfde versnelling te bereiken.

Het grote driehoekige onderdeel heeft een groter traagheidsmoment, dus het heeft meer hoekkracht nodig om dezelfde versnelling te bereiken.

De volgende subsections gebruiken assemblages van verschillende vormen en maten om je te leren hoe je ofwel een heel object of alleen een deel van het object kunt laten draaien. Terwijl je experimenteert met verschillende eigenschapswaarden, leer je hoe je de maximale hoeveelheid koppel kunt schatten die je nodig hebt voor assemblages in je eigen spellen.

### [Gebruik AngularVelocity-constraints](#gebruik-angularvelocity-constraints)[](#gebruik-angularvelocity-constraints)

[AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity)  objecten zijn een type [mover constraint](/docs/nl-nl/physics/mover-constraints)  die koppel toepassen op een hele assemblage om een constante hoeksnelheid te handhaven. Om de assemblage te laten draaien, moet de [AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity)  constraint weten:

-

Het punt en de positieve of negatieve richting om een hoekkracht toe te passen.

-

De hoeveelheid radians die je wilt dat de assemblage per seconde draait.

-

De maximale hoeveelheid koppel die de motor kan toepassen zodat de assemblage een constante hoeksnelheid kan bereiken.

Om dit proces te demonstreren, voeg je een blok toe aan je werkruimte met een attachment waar een [AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity)  constraint naar verwijst om het blok 6  radians per seconde langs de Y-as van de wereld met een constante hoeksnelheid te laten draaien, of ongeveer één volledige rotatie.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/AV-Constraint-2.jpg)

#### [Voeg attachment toe](#voeg-attachment-toe)[](#voeg-attachment-toe)

Je kunt het vaste punt om een assemblage te laten draaien specificeren door een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  object aan de assemblage toe te voegen en vervolgens de positie van de attachment in de 3D-ruimte te configureren. Het voorbeeld [Draaiende Objecten](https://www.roblox.com/games/16550477904/Spinning-Objects)  spel plaatst een attachment in het midden van een blokonderdeel zodat de constraint het onderdeel tegen de klok in kan laten draaien rond het midden van zichzelf.

Attachments bevatten visuele hulpmiddelen om je te helpen hun rotatieassen te visualiseren. De gele pijl geeft de primaire as van de attachment aan, en de oranje pijl geeft de secundaire as van de attachment aan. Hoewel geen van beide rotatieassen de rotatie van het blok beïnvloedt in de stappen van deze techniek, is het belangrijk om deze visuele hulpmiddelen te begrijpen voor toekomstige referentie, omdat ze je kunnen helpen bij het bepalen van ideaal gedrag voor verschillende soorten constraints, zoals de [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  in de volgende techniek.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/Attachment-Visual-Aids.png)

Om een attachment toe te voegen:

1.

In het Explorer  venster, voeg een blok  onderdeel toe aan de Workspace .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/AV-Attachment-2.jpg)

2.

Voeg een attachment toe aan het nieuwe onderdeel.

1.

In het Explorer  venster, beweeg over het onderdeel en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu voor een Attachment . De attachment verschijnt in het midden van het onderdeel.

3.

Hernoem de attachment naar SpinAttachment .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/AV-Attachment-3.jpg)

#### [Configureer constraint](#configureer-constraint)[](#configureer-constraint)

Nu je blok een vast punt heeft om het blok te laten draaien, kun je de eigenschappen van een [AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity)  constraint configureren om de rotatierichting, as of assen voor het toepassen van een doel constante hoeksnelheid, de hoeveelheid radians die je wilt dat het blok per seconde draait, en de maximale hoeveelheid koppel die de motor kan toepassen voor het blok om een constante hoeksnelheid te bereiken, op te geven.

Het voorbeeld [Draaiende Objecten](https://www.roblox.com/games/16550477904/Spinning-Objects)  spel past tot 1000 Rowton-studs constante hoekkracht toe om het blok 6 radians per seconde langs de Y-as van de wereld met een constante hoeksnelheid te laten draaien. Rowton-studs zijn de primaire fysieke eenheden van Roblox voor het meten van koppel. Voor informatie over Roblox fysieke eenheden en hoe ze omgezet worden naar metrische eenheden, zie [Roblox Eenheden](/docs/nl-nl/physics/units) .

Om een [AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity)  constraint te configureren:

1.

Om de constraint zichtbaar te maken in de viewport zodat je de rotatierichting kunt refereren, schakel Toon Constraint Details  in vanuit het Weergave  menu van Studio.

2.

Voeg een [AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity)  constraint toe aan het onderdeel.

1.

In het Explorer  venster, beweeg over het onderdeel en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het contextmenu voor AngularVelocity . De visuele hulp van de constraint verschijnt in het midden van het onderdeel.

3.

Wijs de attachment van het onderdeel toe aan de nieuwe constraint.

1.

In het Explorer  venster, selecteer de constraint.

2.

In het Eigenschappen  venster,

1.

Stel Attachment0  in op SpinAttachment .

2.

Stel AngularVelocity  in op 0, 6, 0  om het onderdeel 6 radians per seconde langs de Y-as te laten draaien. Merk op dat als je deze eigenschap zou instellen op 0, -6, 0 , het blok met de klok mee zou draaien.

3.

Stel MaxTorque  in op 1000  om tot 1000 Rowton-studs constante hoekkracht per seconde toe te passen om de doel hoeksnelheid te bereiken.

4.

Houd RelativeTo  op World  om het blok relatief aan de positie en oriëntatie van de wereld te laten draaien.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/AV-Constraint-2.jpg)

4.

Controleer of de hoeveelheid koppel die je hebt ingesteld het blok 6 radians per seconde langs de Y-as van de wereld laat draaien.

-

Selecteer de Run  simulatiemodus uit het dropdownmenu van de mezzanine en klik op de Speel  knop om te beginnen. Studio simuleert het spel vanuit de huidige camerastandpunt zonder je avatar in de 3D-ruimte.

 ![Run optie in het dropdownmenu van de testmodi van Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Run.png)

Je moet mogelijk je koppel aanpassen afhankelijk van de schaal van je blok en eventuele tegenwerkende fysieke krachten in je omgeving. Bijvoorbeeld, de eigenschappen van de [AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity)  constraint in het voorbeeldspel werken voor een blokonderdeel met een standaardgrootte van 4, 1, 2  op een vlak platform met een plastic materiaal, en een omgeving met de klassieke standaard zwaartekracht.

Echter, als je blok een grotere maat heeft en op gras ligt, moet je je [AngularVelocity.MaxTorque](/docs/nl-nl/reference/engine/classes/AngularVelocity#MaxTorque)  eigenschap verhogen omdat de hoekkracht zowel de massa van het blok als de wrijving van de omgeving moet overwinnen. Bijvoorbeeld, het grote blokonderdeel dat vier keer zo groot is als dat van het voorbeeld heeft minstens 300000  Rowton-studs constante hoekkracht nodig om de ingestelde hoeksnelheid te bereiken!

### [Gebruik HingeConstraint constraints](#gebruik-hingeconstraint-constraints)[](#gebruik-hingeconstraint-constraints)

[HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  objecten zijn een type [mechanische constraint](/docs/nl-nl/physics/mechanical-constraints)  die het mogelijk maakt dat twee attachments rond één as draaien, waarbij de attachments op dezelfde positie en hun primaire assen in dezelfde richting worden beperkt. Wanneer je [HingeConstraint.ActuatorType](/docs/nl-nl/reference/engine/classes/HingeConstraint#ActuatorType)  instelt op Motor , past deze constraint koppel toe op de twee attachments met als doel dat de attachments een constante hoeksnelheid bereiken en handhaven.

Bovendien, wanneer je attachments in een assemblage met twee objecten plaatst, vergrendelen de objecten samen en proberen ze samen te draaien volgens de vaste primaire as van de attachment. Als je een van deze objecten verankert, blijft de hoekkracht de andere object draaien met een constante hoeksnelheid terwijl de rest van de assemblage stil blijft staan.

Bijvoorbeeld, om een bepaald object binnen een assemblage te laten draaien, moet de [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  constraint weten:

-

De positie waar je wilt dat de attachments overlappen.

-

Het punt en de positieve of negatieve richting om een hoekkracht toe te passen.

-

De hoeveelheid radians die je wilt dat de attachment per seconde draait.

-

De maximale hoeveelheid koppel die de motor kan toepassen voor de attachment om een constante hoeksnelheid te bereiken.

Om dit proces te demonstreren, voeg je een propeller-assemblage met twee objecten toe aan je werkruimte met attachments in beide objecten waar een [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  constraint naar verwijst om de propeller 3  radians per seconde (ongeveer de helft van een volledige rotatie per seconde) langs de Y-as met een constante hoeksnelheid te laten draaien terwijl de basis van de propeller stil blijft staan.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/HC-Hinge-3.jpg)

#### [Verkrijg propeller asset](#verkrijg-propeller-asset)[](#verkrijg-propeller-asset)

De Creator Store  is een tabblad van de Toolbox  dat je kunt gebruiken om alle assets te vinden die zijn gemaakt door Roblox en de Roblox-gemeenschap voor gebruik binnen je projecten, inclusief model-, afbeelding-, mesh-, audio-, plugin-, video- en lettertype-assets. Je kunt de Creator Store gebruiken om een individuele asset of assetbibliotheek rechtstreeks in een open spel toe te voegen.

Deze tutorial verwijst naar een propeller-model dat je kunt gebruiken terwijl je elke stap van de [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  techniek van draaiende objecten repliceert. Om deze propeller asset uit je inventaris in je spel te krijgen:

1.

Voeg de propeller toe aan je inventaris.

1.

Navigeer naar de [detailpagina](https://create.roblox.com/store/asset/16558528602)  van de asset op de Creator Store.

2.

Klik in de rechterbovenhoek op de Model Krijgen  knop. De propeller asset is nu in je inventaris, en je kunt deze hergebruiken in elk project op het platform.

2.

Navigeer in Studio naar het Start  tabblad en klik op de Toolbox  knop. Het Toolbox  venster opent.

 ![Toolbox gemarkeerd in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Toolbox.png)

3.

Klik in het Toolbox  venster op het Inventaris  tabblad. De Mijn Modellen  sortering wordt weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Inventory-Tab.png)

4.

Klik op de Propeller  tegel. Het model wordt weergegeven in je viewport.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/Propeller.jpg)

#### [Configureer attachments](#configureer-attachments)[](#configureer-attachments)

Je kunt zowel de positie specificeren waar je wilt dat de attachments overlappen als de richting van de rotatiebeweging om een bepaald object binnen een assemblage te laten draaien door twee [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten aan de assemblage toe te voegen en vervolgens hun uitlijning en oriëntatie in de 3D-ruimte te configureren.

Het voorbeeld [Draaiende Objecten](https://www.roblox.com/games/16550477904/Spinning-Objects)  spel stelt twee attachments in de buurt van de positie uit waar de niet-verankerde propeller overlapt met de verankerde basis, en oriënteert hun primaire rotatie-as omhoog zodat ze tegen de klok in draaien. De basisattachment kan in dit voorbeeld niet draaien omdat de basis verankerd is.

Om attachments voor de scharnierconstraint te configureren:

1.

Voeg een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  object toe aan Hoofd  en Basis .

1.

In het Explorer  venster, beweeg over Hoofd  en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu voor een Attachment .

3.

Herhaal dit proces voor Basis .

4.

Hernoem beide attachments naar HeadAttachment  en BaseAttachment , respectievelijk.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/HC-Attachments-2.jpg)

2.

Draai HeadAttachment  en BaseAttachment  zodat de primaire as van elke attachment omhoog wijst langs de Y-as. Dit vertelt Studio om de attachments tegen de klok in te draaien.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/HC-Attachments-3.jpg)

3.

Verplaats BaseAttachment  naar de bovenkant van Basis , en HeadAttachment  naar de onderrand van Propeller . Dit vertelt Studio waar de scharnier zelf moet worden verbonden, en overlapt beide attachments tijdens runtime.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/HC-Attachments-4.jpg)

#### [Configureer constraint](#configureer-constraint-1)[](#configureer-constraint-1)

Nu je attachments een positie hebben om te overlappen en een richting van rotatiebeweging, kun je de eigenschappen van een [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  constraint configureren om de hoeveelheid radians die je wilt dat de attachment per seconde draait, en de maximale hoeveelheid koppel die de motor kan toepassen voor de attachment om een constante hoeksnelheid te bereiken, op te geven.

Net als bij de vorige techniek past het voorbeeld [Draaiende Objecten](https://www.roblox.com/games/16550477904/Spinning-Objects)  spel tot 1000 Rowton-studs constante hoekkracht toe om de attachment 3 radians per seconde langs de Y-as met een constante hoeksnelheid te laten draaien. Echter, omdat de basisattachment zich in een verankerd object bevindt, kan alleen de attachment van de propeller draaien.

Om een scharnierconstraint te configureren:

1.

Voeg een [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  object toe aan Hoofd .

1.

In het Explorer  venster, beweeg over Hoofd , en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het contextmenu voor een HingeConstraint .

2.

Wijs de attachments van de propeller toe aan de nieuwe constraint zodat de propeller draait in relatie tot  de verankerde basis.

1.

In het Explorer  venster, selecteer de constraint.

2.

In het Eigenschappen  venster,

1.

Stel Attachment0  in op BaseAttachment .

2.

Stel Attachment1  in op HeadAttachment . Het scharnier wordt weergegeven in de viewport.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/HC-Hinge-2.jpg)

3.

In het Explorer  venster, selecteer de constraint, en in het Eigenschappen  venster,

1.

Stel ActuatorType  in op Motor . Nieuwe eigenschapsvelden worden weergegeven.

2.

Stel MotorMaxTorque  in op 1000  om tot 1000 Rowton-studs constante hoekkracht toe te passen om de doel hoeksnelheid te bereiken.

3.

Stel AngularVelocity  in op 3  om de kop van de propeller 3 radians per seconde te laten draaien.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/HC-Hinge-3.jpg)

4.

Controleer of de hoeveelheid koppel die je hebt ingesteld de propeller 3 radians per seconde langs de Y-as laat draaien.

-

Selecteer de Run  simulatiemodus uit het dropdownmenu van de mezzanine en klik op de Speel  knop om te beginnen. Studio simuleert het spel vanuit de huidige camerastandpunt zonder je avatar in de 3D-ruimte.

 ![Run optie in het dropdownmenu van de testmodi van Studio's mezzanine.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Run.png)

## [Pas een initiële hoekkracht toe](#pas-een-initiële-hoekkracht-toe)[](#pas-een-initiële-hoekkracht-toe)

Een andere manier om de hoeksnelheid van een object te veranderen, is door een impuls van hoekkracht toe te passen. Na de impuls van hoekkracht, remt het object af totdat het stil komt te staan als er een tegenwerkende kracht zoals wrijving is, of blijft het in beweging met constante snelheid als er geen tegenwerkende krachten zijn.

Deze techniek is nuttig om objecten te laten draaien na een significante gameplay- of weersgebeurtenis, zoals een sterke windvlaag, omdat het spelers onmiddellijke feedback geeft. Om dit te demonstreren, leert de volgende subsectie je hoe je een assemblage kunt laten draaien met een initiële willekeurige hoekkracht die je kunt aanpassen met nieuwe waarden om aan je eigen gameplay-eisen te voldoen.

### [Gebruik ApplyAngularImpulse](#gebruik-applyangularimpulse)[](#gebruik-applyangularimpulse)

De [ApplyAngularImpulse](/docs/nl-nl/reference/engine/classes/BasePart#ApplyAngularImpulse)  methode past koppel toe op een hele assemblage om een initiële hoeksnelheid te verkrijgen voordat deze afremt. Om de assemblage te laten draaien, moet de methode weten:

-

De assemblage die moet draaien.

-

De as waarop koppel moet worden toegepast om een initiële hoeksnelheid te bereiken.

-

De hoeveelheid koppel die op elke as moet worden toegepast.

Je kunt al deze waarden in een script definiëren. Bijvoorbeeld, het voorbeeldscript definieert de assemblage die moet draaien als de ouder van het script, en past vervolgens een willekeurige impuls van hoekkracht tussen 0  en 100  Rowton-studs op de Y-as toe.

Om een assemblage te laten draaien met [ApplyAngularImpulse](/docs/nl-nl/reference/engine/classes/BasePart#ApplyAngularImpulse) :

1.

Voeg een bol  onderdeel toe aan de Workspace . Het voorbeeld gebruikt een bol met een [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  zodat je de beweging van de bol duidelijk kunt visualiseren.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/Impulse-1.jpg)

2.

Voeg een script toe aan het nieuwe onderdeel.

1.

In het Explorer  venster, beweeg over het onderdeel en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu voor een Script .

3.

Vervang de standaardcode door de volgende code:

```

local part = script.Parent

local impulse = Vector3.new(0, math.random(0, 100), 0)

part:ApplyAngularImpulse(impulse)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
