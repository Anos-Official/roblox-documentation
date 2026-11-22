<!-- Source: https://create.roblox.com/docs/nl-nl/parts/procedural-models -->

Procedurele modellen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)

# Procedurele modellen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[ProcedureleModellen](/docs/nl-nl/reference/engine/classes/ProceduralModel)  zijn een type parameter-gestuurde [Model](/docs/nl-nl/reference/engine/classes/Model)  waarmee je 3D-objecten kunt bouwen en genereren met behulp van code. In plaats van handmatig de inhoud van een model te bewerken, definieer je de structuur ervan via een generator module  en een set attributen. Wanneer die attributen veranderen, of wanneer het model wordt vergroot, wordt de generator automatisch uitgevoerd om het model bij te werken.

Procedurele modellen maken het gemakkelijker om:

-

Modellen niet-destructief aan te passen door parameters te wijzigen in plaats van ze opnieuw op te bouwen. Bijvoorbeeld, het wijzigen van de waarde van StepSize  op een spiraaltrap genereert automatisch de trap opnieuw met het bijgewerkte aantal treden.

-

Automatisch te integreren met bestaande Studio-systemen zoals ongedaan maken/terugzetten, Team Create en sleepgereedschappen door een enkele OnGenerate  functie te implementeren.

-

De prestaties hoog te houden, met modellen die zich gedragen als standaardobjecten totdat hun parameters veranderen.

-

Inhoud zowel tijdens de bewerkingstijd als tijdens de runtime te genereren, met hetzelfde systeem in Studio en in-game.

-

Geparametriseerde modellen te delen op de Creator Store, waardoor activa flexibeler en aanpasbaarder worden.

 Voorbeeld: Procedureel model dat dynamisch meer stoelen toevoegt naarmate de breedte of lengte van de tafel toeneemt.

## [Procedurele modellen invoegen](#procedurele-modellen-invoegen)[](#procedurele-modellen-invoegen)

Je kunt procedurele modellen op de volgende manieren aan je game toevoegen:

-

Handmatig een ProceduralModel  object in de Workspace invoegen. Deze optie bevat een sjabloon generator ModuleScript  om je op weg te helpen.

 ![Een close-up van het Explorer-venster. Een Model-object is gemarkeerd met drie geneste kinderen.](https://prod.docsiteassets.roblox.com/assets/modeling/procedural-models/Procedural-Model-Explorer.png)

-

Een procedureel model genereren met behulp van [Assistant](/docs/nl-nl/assistant/guide#generate-procedural-models)  of de [Roblox Studio MCP-server](/docs/nl-nl/studio/mcp) .

-

Een procedureel model uit de Creator Store invoegen om een bestaand model te gebruiken of aan te passen.

Procedurele modellen kunnen permanente wijzigingen aan je game aanbrengen tijdens de bewerkingstijd. Om je te beschermen tegen ongewenste wijzigingen, heeft elk procedureel model dat uit de Creator Store is ingevoegd automatisch Sandboxed = true  ingeschakeld op zijn generator module.

Om aan te passen hoe procedurele modellen worden gegenereerd, kun je je eigen generator modules definiëren.

## [OnGenerate functie](#ongenerate-functie)[](#ongenerate-functie)

De OnGenerate  functie is de kern van elk ProceduralModel  in de vorm van OnGenerate(params, targetContainer) .

Deze door de ontwikkelaar gedefinieerde functie is verantwoordelijk voor het genereren van de inhoud van het model op basis van de opgegeven parameters en het schrijven van de resultaten in de gegeven container.

OnGenerate  heeft twee primaire verantwoordelijkheden:

-

Verwerk de invoerparameters om de structuur van het model te bepalen

-

Schrijf de gegenereerde resultaten volgens die structuur in de opgegeven targetContainer

De volgende secties beschrijven:

-

Wanneer en hoe de engine OnGenerate  aanroept

-

Hoe de engine de inhoud verwerkt die naar de targetContainer  is geschreven

### [Generator modules](#generator-modules)[](#generator-modules)

De OnGenerate  functie is gedefinieerd binnen een ModuleScript  dat bekend staat als een generator module . Het ProceduralModel  identificeert welke generator module moet worden gebruikt via zijn Generator  eigenschap.

Generator modules zijn standaard Luau-modules, maar worden rechtstreeks door de engine vereist als onderdeel van het generatieproces. Ze volgen een gedefinieerde structuur en retourneren een tabel met gestandaardiseerde velden.

Generator module structuur

```

local MyGenerator = {}

MyGenerator.Attributes = {

    DoSomething = true,

    AmountOfSomething = 137,

}

type Params = {

    Size: Vector3,

    Attributes: typeof(MyGenerator.Attributes),

    Pause: (self: any) -> (),

}

function MyGenerator.OnGenerate(params: Params, targetContainer: GeneratedFolder)

end

return MyGenerator

```

De gestandaardiseerde velden omvatten:

-

Attributes : Een map die parameter namen en hun standaardwaarden definieert.

-

OnGenerate : De functie die een params  tabel en een targetContainer  ontvangt.

De params  tabel binnen OnGenerate  omvat:

-

Attributes : Een tabel die ofwel de module-gedefinieerde attributen bevat of alle modelattributen als er geen zijn opgegeven.

-

Size : Een parameter die de afmetingen van het model weergeeft op een schaal van één.

-

Pause : Een methode die het mogelijk maakt om de generatie efficiënt te onderbreken tijdens complexe generatie taken.

De OnGenerate  functie moet inhoud genereren rond de oorsprong in de targetContainer . Het mag de hoofd DataModel  hiërarchie nooit direct wijzigen.

### [Parameters](#parameters)[](#parameters)

Parameters  zijn de invoerwaarden die de generatie aansturen. Deze omvatten de ingebouwde Size  eigenschap van ProceduralModel , evenals aangepaste attributen die in de generator module zijn gespecificeerd. Deze expliciete parameters  worden direct aan OnGenerate  doorgegeven. Impliciete parameters , zoals de broncode van de module of de sandboxstatus, triggeren ook regeneratie wanneer ze veranderen, maar worden niet aan OnGenerate  doorgegeven.

De volledige set parameters omvat:

-

Expliciet:

-

Size : Definieert het gebied rond de oorsprong waar inhoud wordt gegenereerd.

-

Attributes : Een map met de huidige invoerwaarde van attributen.

-

Impliciet:

-

Generator: De module die de generatie logica levert.

-

Broncode: Wijzigingen in de Luau-code van de generator module.

-

Sandboxing: Wijzigingen in de sandboxstatus van de generator module.

## [Regeneratiegedrag](#regeneratiegedrag)[](#regeneratiegedrag)

Om de prestaties te behouden en API-interacties te vereenvoudigen, wordt OnGenerate  niet  onmiddellijk aangeroepen wanneer parameters veranderen. In plaats daarvan wordt het ProceduralModel  gemarkeerd als dirty , wat aangeeft dat regeneratie in behandeling is. Deze uitgestelde regeneratie vindt meestal later in hetzelfde frame plaats.

Als regeneratie mislukt, wordt de dirty-status gewist totdat er een andere parameterwijziging plaatsvindt. Als een plaats wordt opgeslagen terwijl het model dirty is, blijft de status bestaan en wordt het model toegevoegd aan de generatiewachtrij de volgende keer dat het spel wordt geladen.

### [Uitvoeringsproces](#uitvoeringsproces)[](#uitvoeringsproces)

Wanneer er verwerkings tijd beschikbaar is, regenerert de engine dirty modellen door de volgende stappen uit te voeren:

1.

Vereist de generator module, waarbij het indien nodig yield.

2.

Start een nieuwe thread voor het generatieproces.

3.

Bouwt de parameter tabel, normaliseert de Size  op basis van de huidige schaal van het model.

4.

Past standaardattributen toe op eventuele ontbrekende attributen.

5.

Initialiseert een tijdelijke [GeneratedFolder](/docs/nl-nl/reference/engine/classes/GeneratedFolder)  als de targetContainer .

6.

Roept OnGenerate  aan.

7.

Nadat OnGenerate  retourneert:

-

Als het succesvol is, migreert het de resultaten in de targetContainer  naar het ProceduralModel .

-

Als de generatie mislukt, wordt in plaats daarvan een foutplaceholder gebruikt.

Als parameters opnieuw veranderen terwijl een generatie thread is yielded, wordt de uitstaande generatie geannuleerd en opnieuw gestart met de bijgewerkte parameters.

### [Generatieresultaten](#generatieresultaten)[](#generatieresultaten)

Het plaatsen van gegenereerde resultaten in het model omvat de volgende stappen:

1.

Beëindigt eventuele kindthreads die tijdens de generatie zijn gelekt.

2.

Positioneert de resultaten met PivotTo .

3.

Als de Scale  van het model niet 1 is, gebruikt het ScaleTo  om de grootte normalisatie ongedaan te maken.

4.

Plaatst de resultaten in de GeneratedFolder  van het model.

5.

Als de generator module is gesandboxed, zorgt het ervoor dat de ModuleScripts  in het resultaat de mogelijkheden van de generator module niet overschrijden.

6.

Vul eventuele ontbrekende attributen op het model aan met hun standaardwaarden.

7.

Wis de dirty-status van het model.

## [Generatiedetails](#generatiedetails)[](#generatiedetails)

Naast de kern generatieflow beschrijven de volgende details gedragingen en overwegingen die van invloed zijn op hoe ProceduralModel  generatie werkt.

### [Schalen](#schalen)[](#schalen)

Vanwege de schaalnormalisatie die tijdens de generatie wordt toegepast, ondersteunt ProceduralModel  meerdere schaalwerkstromen:

-

Het wijzigen van de Size  eigenschap genereert het model met nieuwe inhoud.

-

Het wijzigen van de Scale  schaalt de bestaande resultaten uniform met behulp van ScaleTo .

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/procedural-models/ProceduralModel-Sizing.png)

### [Time-outs](#time-outs)[](#time-outs)

Als failsafe wordt een generator module die te veel werk zonder te yielden uitvoert beëindigd. Als de generatie een "Script Timeout" fout tegenkomt, voeg dan extra aanroepen toe aan parameters:Pause()  om de engine in staat te stellen het resterende werk naar een later frame uit te stellen.

Het aanroepen van parameters:Pause()  is zeer goedkoop en retourneert meestal onmiddellijk tijdens normale generatoruitvoering, dus het kan royaal aan het begin van lussen worden aangeroepen zonder de prestaties te beïnvloeden.

### [Ongedaan maken geschiedenis](#ongedaan-maken-geschiedenis)[](#ongedaan-maken-geschiedenis)

Gegenereerde resultaten worden gegroepeerd met de parameterwijziging die ze heeft getriggerd met behulp van ongedaan maken waypoint overrides. Als meerdere parameterwijzigingen in een enkel frame plaatsvinden, worden de resultaten geassocieerd met het meest recente waypoint.

### [Sandboxing](#sandboxing)[](#sandboxing)

ProceduralModel  ondersteunt sandboxing. Alle procedurele modellen van derden die je uit de Creator Store invoegt, zijn standaard gesandboxed om ongewenste wijzigingen aan je game te helpen voorkomen.

Generatiecode draait in de context van de generator module en gebruikt de sandboxstatus van die module. Deze instellingen zijn standaard niet zichtbaar. Om ze te bekijken of te wijzigen, stel je Workspace.SandboxedInstanceMode = Experimental  in. Dit maakt de Sandboxed  en Capabilities  eigenschappen op de ModuleScript  zichtbaar.

Een gesandboxed generator module vereist doorgaans ten minste de volgende mogelijkheden:

-

RunServerScript  (om de module uit te voeren)

-

CreateInstances

-

Basic

Sandboxing voor de ProceduralModel en zijn generator module zijn onafhankelijk van elkaar. Wanneer toegepast op de generator module, heeft sandboxing geen invloed op normale runtime-scripts binnen de ProceduralModel . Dit stelt je in staat om de generatie tijdens de bewerkingstijd strikt te beperken zonder de in-game gedrag te beïnvloeden.

### [Nesting](#nesting)[](#nesting)

ProcedureleModellen  kunnen andere ProcedureleModellen  genereren. Wanneer dit gebeurt, verwerkt de engine de hiërarchie van boven naar beneden binnen dezelfde generatie stap wanneer mogelijk, met dieper geneste modellen die als laatste worden gegenereerd.

## [Beperkingen](#beperkingen)[](#beperkingen)

-

Generatie wordt niet ondersteund binnen Actor  instanties.

-

Modellen kunnen niet worden omgezet in pakketten.

-

Gewrichten die zijn gemaakt bij het gebruik van sleepgereedschappen met Joint Surfaces  ingeschakeld, worden niet behouden tijdens ProceduralModel  regeneraties.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
