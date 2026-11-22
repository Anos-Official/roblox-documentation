<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/physics/create-moving-objects -->

Maak bewegende objecten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Fysica

# Maak bewegende objecten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Bewegende objecten  zijn objecten die zich op een of meer assen binnen de 3D-ruimte verplaatsen. Met de ingebouwde kracht van de simulatiemotor van Roblox kun je objecten laten bewegen en interageren met hun omgeving op een manier die het gedrag van echte fysieke objecten emuleert, wat vertrouwd en intuïtief is voor spelers, zoals zwaartekracht, aerodynamica en wrijving.

Met het [Bewegende Objecten](https://www.roblox.com/games/17560154079/UCT-Linear-Movement)  .rbxl -bestand als referentie, legt deze tutorial uit hoe fysieke krachten de lineaire beweging in Studio beïnvloeden en toont je verschillende technieken om objecten van punt A naar punt B in je spellen te verplaatsen met verschillende bewegingsgedragingen, inclusief richtlijnen over:

-

Het gebruik van een [LinearVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity)  mover constraint om een hele assemblage met een constante lineaire snelheid te verplaatsen.

-

Het gebruik van een [PrismaticConstraint](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  om een assemblage aan een enkele as te binden en deze met een constante lineaire snelheid ten opzichte van een punt in de 3D-ruimte te verplaatsen.

-

Het gebruik van de [ApplyImpulse](/docs/nl-nl/reference/engine/classes/BasePart#ApplyImpulse)  methode om een assemblage te verplaatsen met een initiële impuls van kracht, zodat de assemblage in de loop van de tijd langzaam afremt.

Je kunt je eigen assemblages maken met basisdelen of meshes van externe modelleringstools, en vervolgens met je eigen assets aan de slag gaan. Voor informatie over het exporteren van meshes voor gebruik in Studio, zie [Exportvereisten](/docs/nl-nl/art/modeling/export-requirements) .

## [Lineaire beweging en fysieke krachten](#lineaire-beweging-en-fysieke-krachten)[](#lineaire-beweging-en-fysieke-krachten)

Roblox Studio is een simulatiemotor die het gedrag van de echte wereld in realtime emuleert, dus om te voorspellen hoe objecten die lineair bewegen zich in spellen kunnen gedragen, is het belangrijk om een hoog niveau van begrip te hebben van hoe objecten in het echte leven met lineaire beweging bewegen.

Lineaire beweging  is beweging langs een as. Bijvoorbeeld, wanneer een blok lineaire beweging heeft, beweegt het langs een bepaalde as.

![Een grijs blok voor een donkere achtergrond. De bewegingsas is gemarkeerd en wijst naar links van het scherm om aan te geven dat het blok langs de Y-as van de wereld zal bewegen.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-moving-objects/Movement-Axis.jpg)

Lineaire beweging kan niet bestaan zonder externe, fysieke krachten die objecten duwen of trekken om te bewegen. Volgens de [eerste wet van Newton](https://en.wikipedia.org/wiki/Newton%27s_laws_of_motion#First_law)  blijven stilstaande objecten stil en blijven bewegende objecten in beweging met een constante snelheid, tenzij ze worden beïnvloed door een externe kracht. Bijvoorbeeld, een stilstaand blok blijft stil, tenzij een fysieke kracht zoals wind het duwt om te bewegen.

Kracht  is de maat voor de richting en de grootte van een fysieke duw of trek die ervoor zorgt dat objecten hun lineaire snelheid langs een as veranderen. Een verandering in snelheid staat bekend als versnelling . Dit concept is bijzonder belangrijk voor objecten om te bewegen in Studio; hoe meer kracht je op objecten uitoefent, hoe sneller ze versnellen.

Dit komt omdat de kracht groter moet zijn dan de fysieke krachten die tegen het object in werken, zoals zwaartekracht of wrijving. Bijvoorbeeld, als je het blok op een metalen plaat zou plaatsen, moet de fysieke kracht van de wind de hoeveelheid wrijving van de metalen plaat overwinnen om het blok te blijven versnellen. Als de kracht van de wind niet veel groter is dan de wrijving van de metalen plaat, versnelt het blok, maar langzamer dan in het vorige voorbeeld.

![Een grijs blok voor een donkergrijze metalen plaat met een diagram dat aangeeft dat het blok een plaatwrijving zal hebben om de beweging van het blok door de wind te vertragen.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-moving-objects/Plate-Friction.jpg)

Lineaire snelheid  is de maat voor de beweging van een object, of hoe snel het object zijn positie langs een as verandert over een bepaalde tijd. Studio meet lineaire snelheid aan de hand van het aantal studs dat een object per seconde beweegt. Studs zijn de primaire fysieke eenheden van Roblox voor het meten van lengte, en elke stud komt overeen met ongeveer 28 cm in de echte wereld.

![Een grijs blok voor de 4x4 gridtextuur van de standaard basisplaat. Een enkele stud kubus rechthoek is gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-moving-objects/One-Stud.jpg)

Het begrijpen van lineaire snelheid is belangrijk voor het ontwerpen van gameplay, omdat het je helpt bepalen hoeveel kracht je nodig hebt om een bepaalde snelheid voor je bewegende objecten te bereiken. Bijvoorbeeld, wanneer je objecten omhoog wilt stuwen, is het belangrijk om te overwegen hoe je je kracht moet aanpassen om de zwaartekracht binnen de omgeving te overwinnen, zodat de objecten nauwkeurig bewegen.

De volgende secties duiken dieper in deze concepten terwijl je leert hoe je objecten kunt verplaatsen met een constante of initiële lineaire snelheid met de nodige kracht om eventuele tegenwerkende fysieke krachten binnen de omgeving te overwinnen. Terwijl je deze fysica-concepten met de komende technieken beoordeelt, kun je nauwkeuriger voorspellen hoe je eigenschapswaarden moet aanpassen om elk ideaal lineair bewegingsgedrag in Studio te bereiken.

## [Handhaaf een constante lineaire snelheid](#handhaaf-een-constante-lineaire-snelheid)[](#handhaaf-een-constante-lineaire-snelheid)

Om een object een constante lineaire snelheid te laten bereiken en handhaven, heeft het een kracht nodig om eventuele tegenwerkende fysieke krachten te overwinnen die de lineaire snelheid van het object vertragen of ervoor zorgen dat het object stil blijft staan. Bijvoorbeeld, als je wilt dat een object een lineaire snelheid van [0, 12, 0]  in Studio heeft, heb je genoeg kracht nodig zodat het object 12 studs per seconde langs de Y-as in zijn omgeving kan bereiken en handhaven.

De hoeveelheid kracht die nodig is, hangt niet alleen af van de tegenwerkende fysieke krachten binnen de omgeving zelf, zoals zwaartekracht en wrijving, maar ook van het object zelf. Bijvoorbeeld, als je twee objecten van dezelfde vorm hebt die zich op dezelfde as bewegen, heeft het object met de grotere massa meer kracht nodig om dezelfde lineaire versnelling te bereiken.

Het kleine driehoekige deel heeft een kleine massa, dus het heeft minder kracht nodig om dezelfde versnelling te bereiken.

Het grote driehoekige deel heeft een grote massa, dus het heeft meer kracht nodig om dezelfde versnelling te bereiken.

De volgende subsections gebruiken assemblages van verschillende vormen en maten om je te leren hoe je ofwel een heel object of slechts een deel van het object met een constante lineaire snelheid kunt verplaatsen. Terwijl je experimenteert met verschillende eigenschapswaarden, leer je hoe je de maximale hoeveelheid kracht die je nodig hebt voor assemblages in je eigen spellen kunt inschatten.

### [Gebruik LinearVelocity constraints](#gebruik-linearvelocity-constraints)[](#gebruik-linearvelocity-constraints)

[LinearVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity)  objecten zijn een type [mover constraint](/docs/nl-nl/physics/mechanical-constraints)  die kracht uitoefenen op een hele assemblage om een constante lineaire snelheid te handhaven. Door de positie van de assemblage niet aan een as te vergrendelen tijdens de beweging, is de assemblage vrij om te draaien terwijl deze met andere objecten in de 3D-ruimte botst. Dit type beweging leidt tot verrassende gameplay-scenario's die moeilijker te voorspellen zijn voor spelers.

  Terwijl de leliebladen met elkaar botsen, veranderen ze van oriëntatie maar blijven ze met een constante lineaire snelheid de rivier afstromen.

Om de assemblage te beginnen verplaatsen, moet de [LinearVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity)  constraint weten:

-

Het punt en de positieve of negatieve richting om een kracht toe te passen.

-

De hoeveelheid studs die je wilt dat de assemblage per seconde beweegt.

-

De maximale hoeveelheid kracht die de motor kan toepassen zodat de assemblage de constante lineaire snelheid kan bereiken.

Om dit proces te demonstreren, ga je een lelieblad configureren met een attachment waar een [LinearVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity)  constraint naar verwijst om het lelieblad 15  studs per seconde langs de negatieve X-as van de wereld te verplaatsen met een constante lineaire snelheid.

 ![Een close-up van een lelieblad. De visuele hulp van de constraint van het lelieblad is zichtbaar en wijst naar rechts, wat de negatieve X-as van de wereld is.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-moving-objects/LV-3.jpg)

#### [Voeg een attachment toe](#voeg-een-attachment-toe)[](#voeg-een-attachment-toe)

Je kunt het punt om kracht toe te passen specificeren door een [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  object aan de assemblage toe te voegen en vervolgens de positie van de attachment in de 3D-ruimte te configureren. Het voorbeeld [Bewegende Objecten](https://www.roblox.com/games/17560154079/UCT-Linear-Movement)  spel plaatst een attachment in het midden van het lelieblad, zodat de constraint de mesh vanaf de attachment langs een bepaalde as kan verplaatsen.

Attachments bevatten visuele hulpmiddelen om je te helpen hun assen van beweging te visualiseren. De gele pijl geeft de primaire as van de attachment aan, en de oranje pijl geeft de secundaire as van de attachment aan. Hoewel geen van beide bewegingsassen de beweging van het lelieblad beïnvloedt in de stappen van deze techniek, is het belangrijk om deze visuele hulpmiddelen te begrijpen voor toekomstige referentie, omdat ze je kunnen helpen bij het bepalen van ideaal gedrag voor verschillende soorten constraints, zoals de [PrismaticConstraint](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  in de volgende techniek.

 ![De visuele hulp pijlen van een attachment. De gele pijl die de primaire as van de attachment aangeeft, wijst omhoog, en de oranje pijl die de secundaire as van de attachment aangeeft, wijst naar rechts.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-spinning-objects/Attachment-Visual-Aids.png)

Om een attachment toe te voegen:

1.

In het Explorer  venster, vouw de LinearVelocityExample  map uit en vouw het kindmodel LilyPad_DIY  uit.

2.

Voeg een attachment toe aan de Pad  mesh.

1.

Beweeg over de mesh en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu voor het invoegen van een Attachment . De attachment verschijnt in het midden van het deel.

3.

Hernoem de attachment naar MoveAttachment .

 ![Een close-up van een lelieblad en zijn visuele hulp van de attachment. De primaire as wijst van de camera af, en de secundaire as wijst omhoog.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-moving-objects/LV-Attachment-2.jpg)

#### [Configureer de constraint](#configureer-de-constraint)[](#configureer-de-constraint)

Nu je mesh een vast punt heeft om het lelieblad te verplaatsen, kun je de eigenschappen van een [LinearVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity)  constraint configureren om de richting en grootte voor de constante lineaire snelheid, de hoeveelheid studs die je wilt dat de mesh per seconde beweegt, en de maximale hoeveelheid kracht die de motor kan toepassen zodat de mesh een constante lineaire snelheid kan bereiken, op te geven.

Het voorbeeld [Bewegende Objecten](https://www.roblox.com/games/17560154079/UCT-Linear-Movement)  spel past tot 5000 Rowtons constante kracht toe om het lelieblad 15 studs per seconde langs de negatieve X-as van de wereld te verplaatsen met een constante lineaire snelheid. Rowtons zijn de primaire fysieke eenheden van Roblox voor het meten van kracht. Voor informatie over Roblox fysieke eenheden en hoe ze omgezet worden naar metrische eenheden, zie [Roblox Eenheden](/docs/nl-nl/physics/units) .

Om een [LinearVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity)  constraint te configureren:

1.

Om de constraint zichtbaar te maken in de viewport zodat je de lineaire richting kunt refereren, schakel je Show Constraint Details  in het View  menu van Studio in.

2.

Voeg een [LinearVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity)  constraint toe aan de Pad  mesh.

1.

In het Explorer  venster, beweeg over de mesh en klik op het ⊕ icoon. Een contextmenu verschijnt.

2.

Kies in het contextmenu voor het invoegen van LinearVelocity .

3.

Wijs de attachment van de mesh toe aan de nieuwe constraint.

1.

In het Explorer  venster, selecteer de constraint.

2.

In het Properties  venster,

1.

Stel Attachment0  in op MoveAttachment .

2.

Stel MaxForce  in op 5000  om tot 5000 Rowtons constante kracht toe te passen om de doel lineaire snelheid te bereiken.

3.

Houd RelativeTo  op World  om het lelieblad ten opzichte van de positie en oriëntatie van de wereld te verplaatsen.

4.

Stel VelocityConstraint  in op Line  om de kracht langs een lijn van de attachment te beperken.

5.

Stel LineDirection  in op -1, 0, 0  om het lelieblad langs de negatieve X-as van de wereld te verplaatsen. Merk op dat als je deze eigenschap zou instellen op 1, 0, 0 , het lelieblad langs de positieve X-as van de wereld zou bewegen.

6.

Stel LineVelocity  in op 15  om het lelieblad 15 studs per seconde te verplaatsen.

Als je RelativeTo  zou instellen op Attachment , zou de constraint het lelieblad verplaatsen in relatie tot de oriëntatie van de attachment. Echter, zodra het lelieblad met objecten botst, zou de attachment ook draaien en het lelieblad langs een nieuwe oriëntatie verplaatsen.

 ![Een close-up van een lelieblad en zijn visuele hulp van de constraint die naar rechts wijst, of de negatieve X-as van de wereld.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-moving-objects/LV-3.jpg)

4.

Controleer of de hoeveelheid kracht die je hebt ingesteld de mesh 15 studs per seconde langs de negatieve X-as van de wereld verplaatst.

-

Selecteer de Run  simulatiemodus uit het dropdownmenu van de mezzanine en klik op de Play  knop om te beginnen. Studio simuleert het spel vanuit de huidige camerastandpunt zonder je avatar in de 3D-ruimte.

 ![Run optie in het dropdownmenu van de testmodi van de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Run.png)

### [Gebruik PrismaticConstraint constraints](#gebruik-prismaticconstraint-constraints)[](#gebruik-prismaticconstraint-constraints)

[PrismaticConstraint](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  objecten zijn een type [mechanische constraint](/docs/nl-nl/physics/mechanical-constraints)  die een rigide verbinding creëren tussen twee attachments, waardoor hun ouderassemblages langs één as ten opzichte van elkaar  kunnen bewegen. Door de positie van beide assemblages aan een enkele as te vergrendelen, kan elke assemblage alleen draaien als ze samen in dezelfde richting draaien.

Dit type beweging leidt tot stabiele gameplay-scenario's die gemakkelijker te voorspellen zijn voor spelers. Bijvoorbeeld, het voorbeeld [Bewegende Objecten](https://www.roblox.com/games/17560154079/UCT-Linear-Movement)  spel gebruikt [PrismaticConstraint](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  objecten om logplatforms te verplaatsen die spelers kunnen gebruiken om voorzichtig een enorme rivier over te steken.

Wanneer je [PrismaticConstraint.ActuatorType](/docs/nl-nl/reference/engine/classes/PrismaticConstraint#ActuatorType)  instelt op Motor , past deze constraint kracht toe op de twee attachments met als doel dat de attachments een constante lineaire snelheid bereiken en handhaven. Als je een van de attachments' ouderassemblages verankert, blijft de kracht de niet-verankerde assemblage met een constante lineaire snelheid verplaatsen terwijl de verankerde assemblage stil blijft staan.

Om de assemblage te beginnen verplaatsen, moet de [PrismaticConstraint](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  constraint weten:

-

Het punt en de positieve of negatieve richting om een kracht toe te passen.

-

De hoeveelheid studs die je wilt dat de attachments per seconde bewegen.

-

De maximale hoeveelheid kracht die de motor kan toepassen voor de attachments en hun ouderassemblages om een constante lineaire snelheid te bereiken.

Om dit proces te demonstreren, ga je een logassemblage configureren met twee objecten die child attachments hebben waar een [PrismaticConstraint](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  naar verwijst om de log 40 studs per seconde langs de negatieve X-as van de wereld te verplaatsen met een constante lineaire snelheid.

 ![Een close-up van een bruine log bovenop een rivier. De visuele hulp van de constraint van de log is zichtbaar en wijst naar rechts, of de negatieve X-as van de wereld.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-moving-objects/PC-3.jpg)

#### [Configureer attachments](#configureer-attachments)[](#configureer-attachments)

Je kunt de richting specificeren om een bepaald object binnen een assemblage te verplaatsen door twee [Attachment](/docs/nl-nl/reference/engine/classes/Attachment)  objecten aan de assemblage toe te voegen en vervolgens hun uitlijning en oriëntatie in de 3D-ruimte te configureren. Het voorbeeld [Bewegende Objecten](https://www.roblox.com/games/17560154079/UCT-Linear-Movement)  spel stelt twee attachments uit langs de X-as van de wereld in de buurt van de positie waar de niet-verankerde log overlapt met het verankerde deel, en oriënteert de primaire as van elke attachment om naar de negatieve X-as van de wereld te wijzen.

Wanneer je je PrismaticConstraint constraint in de volgende sectie configureert, zal het de log ten opzichte van  het verankerde deel verplaatsen. Met andere woorden, de log zal zich verwijderen van het stilstaande deel dat niet kan bewegen omdat het verankerd is in de 3D-ruimte.

Om attachments voor de prismatic constraint te configureren:

1.

In het Explorer  venster, vouw de PrismaticConstraintExample  map uit en vouw het kindmodel Log_DIY  uit.

2.

Voeg een attachment toe aan de Log  mesh.

1.

Beweeg over de mesh en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu voor het invoegen van een Attachment . De attachment verschijnt in het midden van het deel.

3.

Hernoem de attachment naar LogAttachment .

 ![Een close-up van een log en zijn visuele hulp van de attachment. De primaire as wijst naar de camera, en de secundaire as wijst omhoog.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-moving-objects/PC-Attachment-2.jpg)

3.

Gebruik hetzelfde proces om een attachment toe te voegen aan het Anchor  deel, en hernoem de attachment naar AnchorAttachment .

 ![Een close-up van een log en twee visuele hulp attachments. De primaire as van de nieuwe visuele hulp attachment wijst naar rechts, en de secundaire as wijst omhoog.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-moving-objects/PC-Attachment-3.jpg)

4.

Gebruik de View Selector  tool als referentie voor de coördinaten van de wereld, draai LogAttachment  en AnchorAttachment  totdat de primaire as van elke attachment naar de negatieve X-as van de wereld wijst.

 ![Een close-up van een log en zijn visuele hulp van de attachment. Beide attachments hebben een primaire as die naar rechts wijst, en een secundaire as die omhoog wijst.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-moving-objects/PC-Attachment-4.jpg)

5.

Verplaats AnchorAttachment  zodat beide attachments zijn uitgelijnd op de X-as van de wereld.

 ![Een close-up van een log en zijn visuele hulp attachments die nu horizontaal zijn gepositioneerd. Beide attachments hebben een primaire as die naar rechts wijst, en een secundaire as die omhoog wijst.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-moving-objects/PC-Attachment-5.jpg)

#### [Configureer de constraint](#configureer-de-constraint-1)[](#configureer-de-constraint-1)

Nu je attachments zijn uitgelijnd op dezelfde as en in de richting wijzen die je wilt dat de log beweegt, kun je de eigenschappen van een [PrismaticConstraint](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  constraint configureren om op te geven of de doel constante lineaire snelheid in de positieve of negatieve richting van de primaire as van elke attachment moet worden toegepast, de hoeveelheid studs die je wilt dat de attachments per seconde bewegen, en de maximale hoeveelheid kracht die de motor kan toepassen voor de log om een constante lineaire snelheid te bereiken.

Hoewel je verschillende waarden kunt kiezen voor je eigen gebruiksgevallen, past het voorbeeld [Bewegende Objecten](https://www.roblox.com/games/17560154079/UCT-Linear-Movement)  spel tot 50000 Rowtons constante kracht toe om de attachments 40 radians per seconde langs de negatieve X-as van de wereld te verplaatsen met een constante lineaire snelheid. Omdat de anchor attachment zich in een verankerd object bevindt, kan alleen de attachment van de log bewegen.

Om een prismatic constraint te configureren:

1.

Voeg een [PrismaticConstraint](/docs/nl-nl/reference/engine/classes/PrismaticConstraint)  object toe aan de Log  mesh.

1.

In het Explorer  venster, beweeg over de mesh en klik op het ⊕ icoon. Een contextmenu verschijnt.

2.

Kies in het contextmenu voor het invoegen van een PrismaticConstraint .

2.

Wijs de attachments van de log toe aan de nieuwe constraint zodat de log ten opzichte van  het verankerde blokdeel beweegt.

1.

In het Explorer  venster, selecteer de constraint.

2.

In het Properties  venster,

1.

Stel Attachment0  in op AnchorAttachment .

2.

Stel Attachment1  in op LogAttachment . De constraint verschijnt in de viewport.

 ![Een close-up van een log en zijn visuele hulp van de constraint. Het heeft nog geen pijl visuele hulp omdat het nog geen ingestelde snelheid heeft.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-moving-objects/PC-2.jpg)

3.

In het Explorer  venster, selecteer de constraint, en in het Properties  venster:

1.

Stel ActuatorType  in op Motor . Nieuwe eigenschapsvelden verschijnen.

2.

Stel MotorMaxForce  in op 50000  om tot 50000 Rowtons constante kracht toe te passen om de doel lineaire snelheid te bereiken.

3.

Stel Velocity  in op 40  om de log 40 studs per seconde te verplaatsen.

 ![Een close-up van een log en zijn visuele hulp van de constraint die naar rechts wijst, of de negatieve X-as van de wereld.](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-moving-objects/PC-3.jpg)

4.

Controleer of de hoeveelheid kracht die je hebt ingesteld de log 40 studs per seconde langs de negatieve X-as van de wereld verplaatst.

-

Selecteer de Run  simulatiemodus uit het dropdownmenu van de mezzanine en klik op de Play  knop om te beginnen. Studio simuleert het spel vanuit de huidige camerastandpunt zonder je avatar in de 3D-ruimte.

 ![Run optie in het dropdownmenu van de testmodi van de mezzanine van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Mezzanine-Testing-Mode-Run.png)

## [Pas een initiële lineaire kracht toe](#pas-een-initiële-lineaire-kracht-toe)[](#pas-een-initiële-lineaire-kracht-toe)

Een andere manier om de lineaire snelheid van een object te veranderen, is door een impuls van kracht toe te passen. Na de impuls van kracht, vertraagt het object of wordt het stilstaand als er een tegenwerkende kracht zoals wrijving is, of blijft het in beweging met een constante lineaire snelheid als er geen tegenwerkende krachten zijn.

Deze techniek is nuttig om objecten te verplaatsen na een significante gameplay-gebeurtenis, zoals een explosie of impactvolle botsing, omdat het spelers onmiddellijke feedback geeft. Om dit te demonstreren, leert de volgende subsectie je hoe je het personage van een speler omhoog de lucht in kunt lanceren wanneer ze met een springplaat botsen met een initiële impuls die je kunt aanpassen met nieuwe waarden om aan je eigen gameplay-eisen te voldoen.

### [Gebruik ApplyImpulse](#gebruik-applyimpulse)[](#gebruik-applyimpulse)

De [ApplyImpulse](/docs/nl-nl/reference/engine/classes/BasePart#ApplyImpulse)  methode past kracht toe op een hele assemblage om een initiële lineaire snelheid te verkrijgen voordat deze vertraagt tot stilstand wanneer er tegenwerkende krachten zijn. Om de assemblage te beginnen verplaatsen, moet de methode weten:

-

De assemblage die je wilt verplaatsen.

-

De as waarop kracht moet worden toegepast om een initiële lineaire snelheid te bereiken.

-

De hoeveelheid kracht die op elke as moet worden toegepast.

Je kunt al deze waarden in een script definiëren. Bijvoorbeeld, het voorbeeldscript definieert de assemblage die moet worden verplaatst als het [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  object van de speler, en past vervolgens een impuls van kracht toe die 2500 Rowton-seconden is om de speler omhoog te lanceren op de positieve Y-as van de wereld. Merk op dat spelerpersonages verschillende hoeveelheden massa hebben, dus je moet deze kracht mogelijk verhogen en balanceren om elke speler te lanceren zonder spelerpersonages met kleinere massa's te hoog te lanceren.

Om een assemblage te verplaatsen met [ApplyImpulse](/docs/nl-nl/reference/engine/classes/BasePart#ApplyImpulse) :

1.

In het Explorer  venster, vouw de ApplyImpulseExample  map uit en vouw het kindmodel JumpPad_DIY  uit.

2.

Voeg een script toe aan het JumpPad  deel.

1.

Beweeg over het deel en klik op de ⊕ knop. Een contextmenu verschijnt.

2.

Kies in het menu voor het invoegen van een Script . De attachment verschijnt in het midden van het deel.

3.

Hernoem het script naar JumpScript .

3.

Vervang de standaardcode door de volgende code:

```

local volume = script.Parent

local function onTouched(other)

  local impulse = Vector3.new(0, 2500, 0)

  local character = other.Parent

  local humanoid = character:FindFirstChildWhichIsA("Humanoid")

  if humanoid and other.Name == "LeftFoot" then

    other:ApplyImpulse(impulse)

  end

end

volume.Touched:Connect(onTouched)

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
