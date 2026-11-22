<!-- Source: https://create.roblox.com/docs/nl-nl/characters/character-controller-library -->

Karaktercontrollerbibliotheek | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Personages](/docs/nl-nl/characters)
6. /
7. [Bibliotheek met personagecontrollers](/docs/nl-nl/characters/character-controller-library)

# Karaktercontrollerbibliotheek

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Karaktercontrollerbibliotheek  (CCL) is een modulair framework voor het bouwen van karakterbeweging en -gedrag via attributen en Luau-scripts. Deze architectuur vervangt rigide [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  toestandsmachines door een flexibel, uitbreidbaar systeem voor karaktermechanica.

De CCL is momenteel in bèta. Schakel het in via Bestand  ⟩ Bèta-functies  ⟩ AvatarAbilities Karaktercontrollerbibliotheek  en schakel het vervolgens in zoals beschreven in de volgende sectie.

## [CCL inschakelen](#ccl-inschakelen)[](#ccl-inschakelen)

De CCL is opt-in  via het [Avatar-instellingen](/docs/nl-nl/studio/avatar-settings)  venster in Studio. Om het in te schakelen:

1.

Ga naar het Avatar  tabblad en open [Avatar-instellingen](/docs/nl-nl/studio/avatar-settings) .

 ![Avatar-instellingen aangegeven in de werkbalk van Studio](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Avatar-Settings.png)

2.

Selecteer het Beweging  tabblad aan de linkerkant van het venster en selecteer in de sectie Vaardigheden  de Character Controller Library .

 ![Character Controller Library schakelaar in het Avatar-instellingen venster](https://prod.docsiteassets.roblox.com/assets/studio/general/Avatar-Settings-CCL.png)

3.

Alle standaardvaardigheden zoals Rennen , Springen  en Klimmen  zijn standaard ingeschakeld. Om een van deze tijdens runtime uit te schakelen, vink je het bijbehorende vakje uit.

Het wordt niet aanbevolen om Rennen  uit te schakelen, omdat dit voorkomt dat personages zich over de grond kunnen bewegen. Daarnaast moet je altijd Opstaan  ingeschakeld houden als Vallen  is ingeschakeld, omdat een mismatch ervoor zorgt dat personages kunnen vallen (struikelen) maar nooit weer opstaan.

## [Vaardigheden](#vaardigheden)[](#vaardigheden)

Vaardigheden evalueren wat een karakter kan doen, zoals de mogelijkheid om te rennen, springen, klimmen en zwemmen. In plaats van te vertrouwen op een vaste set van door de engine gedefinieerde karaktertoestanden zoals die in [Enum.HumanoidStateType](/docs/nl-nl/reference/engine/enums/HumanoidStateType) , bepalen CCL-vaardigheden dynamisch wat een karakter kan doen en hoe het moet reageren op spelersinvoer.

Structueel is een vaardigheid een zelfvoorzienende Luau-tabel die voornamelijk het volgende specificeert:

| Tabelvelden | | Doel |
| --- | --- |
| Naam | | De unieke identiteit van de vaardigheid; [voorwaarden](#voorwaarden)  en [conflicten](#conflicten)  verwijzen ernaar bij naam. Het registreren van twee vaardigheden met dezelfde Naam  genereert een fout. Voor een paar vergelijkbare vaardigheden, geef elke een andere Naam  en deel een gemeenschappelijk [label](#labels)  in Labels . De naam van de [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  bepaalt de unieke configuratiesleutel. |
| Labels , TimedLabels | | Genomineerde bits in een gedeelde 64-bits masker die fungeert als de coördinatiebus tussen vaardigheden; zie [labels](#labels) . |
| StartsWhen , RunsWhile | | Voorwaarden die definiëren wanneer de vaardigheid moet starten en wanneer deze actief moet blijven, respectievelijk; zie [voorwaarden](#voorwaarden) . |
| Blocks , Stops , Suspends , ExclusiveGroup | | Hoe om te gaan met [conflicten](#conflicten)  tussen vaardigheden die niet tegelijkertijd actief kunnen zijn. |
| Input | | De invoer die de vaardigheid activeert. Input.Mode  controleert hoe de invoer de vaardigheid start en stopt; RunsWhile  bevat alleen wereldvoorwaarden, nooit de invoer zelf; zie [invoeren](#invoeren) . |
| Config , State | | Standaardconfiguratiewaarden en gerepliceerde status voor elke vaardigheidsregistratie. Callbacks lezen configuratie van abilityCtx.Config  en lezen of schrijven gerepliceerde status via abilityCtx.State . |
| OnSetup , OnStart , OnStop , OnUpdate , OnTeardown | | Levenscycluscallbacks waar het daadwerkelijke gedrag van de vaardigheid is geprogrammeerd; zie [callbacks](#callbacks) . |

### [Labels](#labels)[](#labels)

Een label  is een genomineerde bit in een gedeelde 64-bits masker die fungeert als de coördinatiebus tussen vaardigheden. Essentieel:

-

Een actieve vaardigheid zendt  zijn Labels  en TimedLabels  uit naar de wereldmasker.

-

Vaardigheid [voorwaarden](#voorwaarden)  (StartsWhen , RunsWhile ) testen  de wereldmasker en reageren.

-

Vaardigheid [conflicten](#conflicten)  definiëren welke andere  vaardigheden geblokkeerd, gestopt of opgeschort zijn bij activatie.

In de volgende opstelling wordt het label "CanFallDown"  uitgezonden naar de wereldmasker wanneer Running  actief is. De FallingDown  vaardigheid met zijn [voorwaarde](#voorwaarden)  van StartsWhen = All( "CanFallDown", "Stunned" )  wordt automatisch een kandidaat, maar "Stunned"  moet ook naar de wereldmasker worden uitgezonden voordat FallingDown  plaatsvindt.

Running Ability

```

local AvatarAbilities = require("@rbx/AvatarAbilities")

local Identifiers = AvatarAbilities.Identifiers

local Ability = Identifiers.Ability

local Rule = AvatarAbilities.Rule

local Sensor = Identifiers.Sensor

local All, Any, Not = Rule.All, Rule.Any, Rule.Not

local Running: AvatarAbilities.AbilityDefinition = {

	Name = Ability.Running,

	Labels = { "CanFallDown" }, -- Labels worden uitgezonden wanneer de vaardigheid actief is

	StartsWhen = Sensor.Ground,

	RunsWhile = Sensor.Ground,

}

```

FallingDown Ability

```

local AvatarAbilities = require("@rbx/AvatarAbilities")

local Identifiers = AvatarAbilities.Identifiers

local Ability = Identifiers.Ability

local Rule = AvatarAbilities.Rule

local Sensor = Identifiers.Sensor

local All, Any, Not = Rule.All, Rule.Any, Rule.Not

local FallingDown: AvatarAbilities.AbilityDefinition = {

	Name = Ability.FallingDown,

	StartsWhen = All( "CanFallDown", "Stunned" ), -- Labels die nodig zijn om de vaardigheid te starten

	Blocks = { Ability.Running }

}

```

Labels kunnen ook op een getimede  manier worden uitgezonden of geconsumeerd met behulp van de TimedLabels  woordenboek.

| Sleutel | | Beschrijving |
| TimedLabels.OnStart | | Woordenboek met labels (sleutels) en bijbehorende duur. Label(s) worden uitgezonden wanneer de vaardigheid begint en vervallen automatisch wanneer hun duur eindigt. Bijvoorbeeld, OnStart = { Dashing = 1 }  zendt het Dashing  label uit voor 1 seconde wanneer de vaardigheid begint. |
| TimedLabels.OnStop | | Woordenboek met labels (sleutels) en bijbehorende duur. Label(s) worden uitgezonden wanneer de vaardigheid stopt en vervallen automatisch wanneer hun duur eindigt. Bijvoorbeeld, OnStop = { DashCooldown = 2 }  zendt het DashCooldown  label uit voor 2 seconden wanneer de vaardigheid stopt. |
| TimedLabels.Consumes | | Lijst van labels die moeten worden verwijderd (geconsumeerd) wanneer de vaardigheid activeert. Bijvoorbeeld, als een vechtspel spelers toestaat om tegenaanvallen uit te voeren na het blokkeren van een aanval van een tegenstander, kan de CounterAttack  vaardigheid zowel StartsWhen = "AfterBlock"  als TimedLabels = { Consumes = { "AfterBlock" } }  bevatten om dubbele activering van de CounterAttack  vaardigheid te voorkomen. |

Timed Labels

```

local AvatarAbilities = require("@rbx/AvatarAbilities")

local Identifiers = AvatarAbilities.Identifiers

local Rule = AvatarAbilities.Rule

local Sensor = Identifiers.Sensor

local All, Any, Not = Rule.All, Rule.Any, Rule.Not

local Dash: AvatarAbilities.AbilityDefinition = {

	Name = "Dash",

	StartsWhen = All( Sensor.Ground, Not("DashCooldown") ),

	RunsWhile = "Dashing",

	TimedLabels = {

		OnStart = { Dashing = 1 },

		OnStop = { DashCooldown = 2 },

	},

}

```

### [Voorwaarden](#voorwaarden)[](#voorwaarden)

Een voorwaarde  is een of meer [labels](#labels) , [sensoren](#sensoren) , of een invoerverwijzing, gebruikt door StartsWhen  en RunsWhile . Voorwaarden compileren tot bitmaskeroperaties tijdens runtime en evaluatie is gehele getallen wiskunde — geen tabelwandelingen en geen stringvergelijkingen.

| Doel | | Syntax | | Voorbeeld |
| Één vereiste voorwaarde. | |  | | StartsWhen = Sensor.Ground |
| EN  logica voor wanneer alle  labels bestaan in de wereldmasker en alle  sensoren actief zijn. | | All() | | StartsWhen = All( "CanFallDown", "Stunned" ) |
| OF  logica voor wanneer een van  de labels bestaat in de wereldmasker of een van  de sensoren actief is. | | Any() | | StartsWhen = Any( "WallClimbing", "Climbing" ) |
| Negatie zodat de labels niet  kunnen bestaan in de wereldmasker en de sensoren niet  actief kunnen zijn. | | Not() | | RunsWhile = Not("Stunned") |

Not()  neemt precies één  label/sensor, niet een groep. Om meerdere te negateren, gebruik All( Not(), Not() ) .

Voorwaardelijke evaluatie kan worden gecombineerd voor complexere logica, zoals All()  chaining plus Not()  om aan te geven dat een sensor actief moet zijn terwijl een label niet mag bestaan:

```

local AvatarAbilities = require("@rbx/AvatarAbilities")

local Identifiers = AvatarAbilities.Identifiers

local Rule = AvatarAbilities.Rule

local Sensor = Identifiers.Sensor

local All, Any, Not = Rule.All, Rule.Any, Rule.Not

local Dive: AvatarAbilities.AbilityDefinition = {

	Name = "Dive",

	StartsWhen = All( Sensor.WaterSurface, Not("Recovering") ),

}

```

### [Conflicten](#conflicten)[](#conflicten)

Sommige vaardigheden kunnen niet actief zijn wanneer een andere vaardigheid actief is; bijvoorbeeld, karakters kunnen niet springen terwijl ze zwemmen, en ze kunnen niet rennen terwijl ze vallen. De engine lost deze conflicten declaratief op binnen de definitie van een vaardigheid:

| Conflict Sleutel | | Doel |
| Blocks | | Terwijl de bezittende vaardigheid actief is, kunnen de vermelde andere vaardigheden niet starten. Bijvoorbeeld, een ScopeAim  vaardigheid kan Blocks = { Ability.Running, Ability.Jumping }  bevatten om te voorkomen dat karakters rennen of springen terwijl ze zorgvuldig door de richtkijker van hun wapen richten. |
| Stops | | Wanneer de bezittende vaardigheid start, forceert  de vermelde andere vaardigheden om te stoppen en moeten ze opnieuw worden geactiveerd. Bijvoorbeeld, een Hover  vaardigheid kan Stops = { Ability.Running }  bevatten om onmiddellijk de loopbeweging van een karakter te stoppen wanneer ze beginnen te zweven. |
| Suspends | | Wanneer de bezittende vaardigheid start, pauzeren  de vermelde andere vaardigheden en herstarten  automatisch wanneer de bezittende vaardigheid stopt. Bijvoorbeeld, een aangepaste sprintvaardigheid kan Suspends = { Ability.Running }  bevatten zodat rennen 🄐 pauzeert bij het starten van de sprint, 🄑 wordt geblokkeerd tijdens de sprint, en 🄒 herstart bij het stoppen van de sprint. |

Een unieke conflict sleutel is ExclusiveGroup  die meerdere vaardigheden in een groep plaatst, elk met een Priority  waarde. Slechts één vaardigheid per groep kan actief zijn en hogere prioriteit wint. Echter, als een uitdager Stops  verklaart die gericht is op de naam/label van de houder, wint deze ongeacht de prioriteit.

In de volgende opstelling worden drie vaardigheden (Sprinting , Crouching , Stagger ) toegevoegd aan een Locomotion  exclusieve groep. Sprinting  heeft de hoogste prioriteit (200 ) zodat het wint van Crouching  (100 ) en de twee nooit tegelijkertijd draaien. Echter, Stagger  stopt de sprint gedwongen (Stops = { Ability.Sprinting } ), zodat het Sprinting  kan onderbreken en supersede, ook al is de prioriteit (150 ) lager.

```

local AvatarAbilities = require("@rbx/AvatarAbilities")

local Identifiers = AvatarAbilities.Identifiers

local Ability = Identifiers.Ability

local Rule = AvatarAbilities.Rule

local Sensor = Identifiers.Sensor

local All, Any, Not = Rule.All, Rule.Any, Rule.Not

local Sprinting: AvatarAbilities.AbilityDefinition = {

	Name = Ability.Sprinting,

	ExclusiveGroup = { Name = "Locomotion", Priority = 200 },

}

local Crouching: AvatarAbilities.AbilityDefinition = {

	Name = Ability.Crouching,

	ExclusiveGroup = { Name = "Locomotion", Priority = 100 },

}

-- Een vaardigheid met lagere prioriteit kan een vaardigheid met hogere prioriteit overschrijven door deze te stoppen

local Stagger: AvatarAbilities.AbilityDefinition = {

	Name = "Stagger",

	ExclusiveGroup = { Name = "Locomotion", Priority = 150 },

	Stops = { Ability.Sprinting },

}

```

### [Invoeren](#invoeren)[](#invoeren)

De Input  definitie van een vaardigheid specificeert de invoer die wordt gebruikt om te proberen de vaardigheid te activeren. Het neemt sleutel-waarde paren die het invoergedrag, de actielocatie en optionele aanraakknopiconen configureren.

```

local AvatarAbilities = require("@rbx/AvatarAbilities")

local Identifiers = AvatarAbilities.Identifiers

local Rule = AvatarAbilities.Rule

local Sensor = Identifiers.Sensor

local All, Any, Not = Rule.All, Rule.Any, Rule.Not

local Dash: AvatarAbilities.AbilityDefinition = {

	Name = "Dash",

	Input = { InputName = "Dash", Mode = "Press", ActionSlot = 5 }

}

```

-

InputName  is een logische naam, geen sleutel. De CCL genereert een invoersensor en AND't deze altijd in StartsWhen .

-

Mode  definieert hoe deze invoer de vaardigheid start en stopt. RunsWhile  bevat nooit de invoer zelf; het bevat alleen wereldvoorwaarden, zoals op de grond staan of in water zijn, zodat Mode  de enige bron is van invoergestuurde start en stop:

| Mode | | Start | | Stop Van Invoer |
| Press | | Bij indrukken. | | Nooit. De vaardigheid eindigt zichzelf via een conflict, zijn eigen RunsWhile , of door Stop()  aan te roepen. |
| Hold | | Bij indrukken. | | Bij loslaten. |
| Hold  met Repeats | | Bij indrukken. | | Loslaten beëindigt de heractivatie, niet de cyclus die al in de lucht is. |
| Toggle | | Bij inschakelen. | | Bij uitschakelen. |

Press  is geschikt voor discrete acties zoals dashen, aanvallen en gooien. Hold  en Toggle  zijn geschikt voor aanhoudende acties zoals sprinten, richten, blokkeren, hurken en zweven. Hold  met Repeats  is geschikt voor acties die zichzelf stoppen en opnieuw activeren terwijl ze worden vastgehouden, zoals herhaald springen.

-

Repeats  (boolean, alleen Hold ) maakt de vaardigheid zelf-terminerend in elke cyclus en heractiveert terwijl de invoer vastgehouden blijft, in plaats van continu te draaien voor de hele houdperiode.

-

OutlivesInputWhile  (Hold / Toggle  alleen) is een [voorwaarde](#voorwaarden)  waaronder de vaardigheid blijft draaien na loslaten of uitschakelen, en stopt zodra de voorwaarde is opgeheven. Gebruik het wanneer een vaardigheid langer moet duren dan zijn invoer onder een specifieke wereldvoorwaarde.

-

ActionSlot  definieert een actielocatie  die is gekoppeld aan een lijst van [InputActions](/docs/nl-nl/reference/engine/classes/InputAction)  en [InputBindings](/docs/nl-nl/reference/engine/classes/InputBinding)  binnen het [Input Action System](/docs/nl-nl/input/input-action-system) .

Verschillende actie slot invoerbindingen zijn vooraf gedefinieerd door Roblox en, in de toekomst, zal de [Input Action Manager](/docs/nl-nl/characters/input/input-action-system#input-action-manager)  je in staat stellen om standaard invoerbindingen voor actie slots naar wens opnieuw te configureren. Het instellen van ActionSlot  op 0  kiest de volgende beschikbare lege slot. Op mobiele apparaten vullen slots 1 - 7  zich met knoppen op het scherm (zie diagram hieronder).

| Slot | | Toetsenbord & Muis | | Gamepad | | Touch | | Standaard Toewijzing |
| 1 | | [Space](/docs/nl-nl/reference/engine/enums/KeyCode#Space) | | [ButtonA](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonA) | | ① | | Springen |
| 2 | | [LeftShift](/docs/nl-nl/reference/engine/enums/KeyCode#LeftShift) | | [ButtonL1](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonL1) | | ② | | Rennen |
| 3 | | [LeftControl](/docs/nl-nl/reference/engine/enums/KeyCode#LeftControl) | | [ButtonB](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonB) | | ③ | | Hurken |
| 4 | | [R](/docs/nl-nl/reference/engine/enums/KeyCode#R) | | [ButtonX](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonX) | | ④ | |  |
| 5 | | [MouseLeftButton](/docs/nl-nl/reference/engine/enums/KeyCode#MouseLeftButton) | | [ButtonR2](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonR2) | | ⑤ | |  |
| 6 | | [Q](/docs/nl-nl/reference/engine/enums/KeyCode#Q) | | [ButtonY](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonY) | | ⑥ | |  |
| 7 | | [X](/docs/nl-nl/reference/engine/enums/KeyCode#X) | | [ButtonR1](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonR1) | | ⑦ | |  |
| 8 | | [C](/docs/nl-nl/reference/engine/enums/KeyCode#C) | | [ButtonL2](/docs/nl-nl/reference/engine/enums/KeyCode#ButtonL2) | |  | |  |
| 9 | | [F](/docs/nl-nl/reference/engine/enums/KeyCode#F) | | [DPadLeft](/docs/nl-nl/reference/engine/enums/KeyCode#DPadLeft) | |  | |  |
| 10 | | [G](/docs/nl-nl/reference/engine/enums/KeyCode#G) | | [DPadRight](/docs/nl-nl/reference/engine/enums/KeyCode#DPadRight) | |  | |  |
| 11 | | [V](/docs/nl-nl/reference/engine/enums/KeyCode#V) | | [DPadDown](/docs/nl-nl/reference/engine/enums/KeyCode#DPadDown) | |  | |  |

 ![](https://prod.docsiteassets.roblox.com/assets/scripting/input/Action-Slots-Diagram.png)

-

CustomIcon , CustomIconActive , en CustomIconInvalid  specificeren Roblox asset-ID's voor de aanraakknop wanneer de vaardigheid inactief, actief of niet beschikbaar is, respectievelijk.

RunsWhile  bevat alleen wereldvoorwaarden. De compiler stelt het effect van de invoer samen in de daadwerkelijke voortzetting van de vaardigheid achter de schermen op basis van Mode , dus het invoeren zelf in StartsWhen  of RunsWhile  genereert een fout (verwijs daar niet naar Rule.Input ). Hold  en Toggle  vaardigheden stoppen al bij loslaten of uitschakelen, dus je hoeft dat niet te dupliceren in RunsWhile :

```

local AvatarAbilities = require("@rbx/AvatarAbilities")

local Rule = AvatarAbilities.Rule

local Sensor = AvatarAbilities.Identifiers.Sensor

local All, Any, Not = Rule.All, Rule.Any, Rule.Not

local Glide: AvatarAbilities.AbilityDefinition = {

	Name = "Glide",

	Input = { InputName = "Glide", Mode = "Hold", ActionSlot = 6 },

	StartsWhen = Not(Sensor.Ground),

	RunsWhile = Not(Sensor.Ground),

}

```

Om een Hold  of Toggle  vaardigheid langer te laten duren dan zijn invoer onder een wereldvoorwaarde, stel je OutlivesInputWhile  in in plaats van de invoer toe te voegen aan RunsWhile . De volgende Crouching  vaardigheid blijft hurken nadat de speler de hurkinvoer loslaat, zolang er iets boven blijft:

```

local AvatarAbilities = require("@rbx/AvatarAbilities")

local Identifiers = AvatarAbilities.Identifiers

local Sensor = Identifiers.Sensor

local Crouching: AvatarAbilities.AbilityDefinition = {

	Name = "Crouching",

	Input = { InputName = "Crouch", Mode = "Hold", OutlivesInputWhile = Sensor.Ceiling, ActionSlot = 3 },

	RunsWhile = Sensor.Ground,

}

```

### [Sensoren](#sensoren)[](#sensoren)

Een sensor  is een genomineerde waarde over de wereld die de engine voor je leest. Je leest meestal sensoren in plaats van ze te schrijven. Voor de gemak zijn verschillende sensoren vooraf geregistreerd:

| Sensor | | Beschrijving |
| Sensor.Ground | | Staan op een oppervlak |
| Sensor.IsMoving | | Bewegingsinvoer wordt toegepast |
| Sensor.MoveInput | | De bewegingsvector zelf |
| Sensor.Ceiling | | Iets is direct boven je |
| Sensor.Climb | | Een klimoppervlak is binnen bereik |
| Sensor.Water  / Sensor.WaterSurface | | In water / aan het oppervlak |
| Sensor.Sit | | Zittend |
| Sensor.Tipped | | Omgevallen |
| Sensor.Tool | | Een [Tool](/docs/nl-nl/reference/engine/classes/Tool)  vasthouden |
| Sensor.LookDirectionInput | | De opgegeven kijkrichting |
| Sensor.RotateToLookDirectionInput | | Of het karakter naar de opgegeven kijkrichting moet draaien |

### [Callbacks](#callbacks)[](#callbacks)

Vaardigheid callback-functies  stellen je in staat om specifiek gedrag te programmeren:

Hoewel je aangepaste vaardigheden op de server registreert, worden hun callbacks uitgevoerd in zowel de voorspelde client-simulatie als de autoritatieve server-simulatie. Houd het callback-gedrag deterministisch zodat beide simulaties hetzelfde resultaat opleveren.

| Callback | | Voert uit | | Gebruikscases |
| OnSetup(managerCtx, abilityCtx) | | Eén keer, wanneer de vaardigheid is geregistreerd. | | Referenties cachen, status initialiseren, enz. |
| OnStart(managerCtx, abilityCtx, hadLabel) | | Elke keer dat de vaardigheid wordt geactiveerd. | | Een effect toepassen zoals een impuls. De hadLabel()  functie rapporteert of een specifieke label aanwezig was toen de activatie begon, vóór de conflictoplossing. |
| OnUpdate(managerCtx, abilityCtx) | | Elke actieve frame. | | Continue werkzaamheden zoals timers of per-frame krachten. |
| OnStop(managerCtx, abilityCtx) | | Elke deactivatie, vrijwillig of gedwongen. | | Wat OnStart()  deed ongedaan maken. |
| OnTeardown(managerCtx, abilityCtx) | | Bij het verwijderen van de vaardigheid. | | Verbindingen ontkoppelen, instanties vernietigen, enz. |

Elke callback-functie heeft als eerste parameter managerCtx , een ManagerContext  object met gedeelde karakter- en manager-eigenschappen, waaronder:

-

managerCtx.AbilityOwner  — Het karakter [Model](/docs/nl-nl/reference/engine/classes/Model)  zodat managerCtx.AbilityOwner.PrimaryPart  het wortelonderdeel is.

-

managerCtx.AbilityManager  — Een verkorte weergave van de manager zodat een vaardigheid vaardigheden kan toevoegen, verwijderen en opvragen vanuit zijn eigen callbacks.

-

managerCtx.BodyParts  — De lichaamsdelen van het karakter, met helpers voor het in- en uitschakelen van botsingen per ledemaat.

-

managerCtx.ControllerManager  — De [ControllerManager](/docs/nl-nl/reference/engine/classes/ControllerManager)  van het karakter voor fysica-controle. Het kan nil  zijn wanneer geen geregistreerde vaardigheid fysica vereist.

-

managerCtx.RootCFrame  — De [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  van het wortelonderdeel, eenmaal vastgelegd aan het begin van het frame zodat callbacks niet elk zelf hoeven te fetchen.

-

managerCtx.RootLookVector  — Richting waarin het wortelonderdeel van het karakter kijkt.

-

managerCtx.RootUpVectorY  — De Y  component van de opwaartse vector van het wortelonderdeel.

-

managerCtx.TaskSynchronize()  — Synchroniseert een callback vóór toegang tot het DataModel wanneer parallelle callback-ondersteuning is ingeschakeld. Momenteel wordt OnUpdate  niet uitgevoerd in een parallelle context, dus deze functie heeft geen effect. Volledige Parallel Luau-ondersteuning is gepland voor een toekomstige update.

De tweede parameter, abilityCtx , is een AbilityContext  object met door de engine beheerde tabellen voor de huidige vaardigheidsregistratie:

-

abilityCtx.Config  — Alleen-lezen configuratiewaarden voor deze vaardigheidsregistratie.

-

abilityCtx.State  — Veranderlijke status die door het DataModel wordt gerepliceerd. [Server Authority](/docs/nl-nl/projects/server-authority)  herstelt deze waarden tijdens terugrol en hersimulatie.

-

abilityCtx.Local  — Veranderlijke tijdelijke status die niet gerepliceerd wordt of deelneemt aan terugrol.

Sla aangepaste callback-gegevens op in abilityCtx.State  of abilityCtx.Local . Het rechtstreeks schrijven van aangepaste velden naar abilityCtx  is een fout.

Callbacks mogen nooit  yielden, omdat ze binnen de synchrone stap van de engine draaien en yielden de frame breekt. Voeg geen  yield-functies toe zoals [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  of [WaitForChild()](/docs/nl-nl/reference/engine/classes/Instance#WaitForChild) . Simulatiecallbacks beperken ook sommige DataModel-operaties, waaronder [Destroy()](/docs/nl-nl/reference/engine/classes/Instance#Destroy) . Je kunt attributen instellen en fysica bijwerken in een callback. Voor bijvoorbeeld levenscyclus of ander beperkt werk, stel een attribuut in de callback in en reageer daarop vanuit een regulier script.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
