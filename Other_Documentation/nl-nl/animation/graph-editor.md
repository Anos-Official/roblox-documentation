<!-- Source: https://create.roblox.com/docs/nl-nl/animation/graph-editor -->

Animatie Grafiek Editor | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Animatie](/docs/nl-nl/animation)
6. /
7. Animaties maken
8. /
9. [Grafiek-editor](/docs/nl-nl/animation/graph-editor)

# Animatie Grafiek Editor

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Animatie Grafiek Editor  is een visuele, op knooppunten gebaseerde tool die technische artiesten en animatoren in staat stelt om complexe animatielogica direct binnen Roblox Studio te bouwen. Door een gestroomlijnde interface te bieden voor het creëren van gedragingen zoals blend trees, verwijdert het de traditionele afhankelijkheid van handmatige scripting voor karakterbeweging.

Dit systeem werkt samen met je bestaande animatieworkflow:

-

Animatie Editor : Blijf de [Animatie Editor](/docs/nl-nl/animation/editor)  gebruiken als je primaire tool voor het maken van individuele clips en het verfijnen van keyframes en curves.

-

Animatie Grafiek Editor : Gebruik deze tool om die clips te nemen en ze te organiseren in een logische boom om geavanceerd gameplay-gedrag aan te sturen.

Ontworpen om samenwerking te verbeteren, stelt de visuele grafiek ontwikkelaars in staat om snel de logica die door animatoren is gemaakt te inspecteren, debuggen en begrijpen. Terwijl artiesten zich richten op het verfijnen van interactieve beweging, kunnen ontwikkelaars nog steeds programmatisch toegang krijgen tot animatie grafiek knooppunten voor directe controle over gemengde animaties en toestanden.

## [Bouw een grafiek](#bouw-een-grafiek)[](#bouw-een-grafiek)

Om te beginnen met het bouwen van logica voor een animeerbaar karakter, krijg je toegang tot de Animatie Grafiek editor via het Avatar-tabblad in de Studio-ribbon. De volgende stappen tonen hoe je een rig initialiseert en een basis knooppuntnetwerk bouwt met behulp van standaard loop- en zwaaianimaties.

Voor een diepere duik in praktische toepassingen kun je de [Animatie Grafiek Referentiebestand](https://www.roblox.com/games/92493993350916/Animation-Graph-Editor-Simple-Demo)  verkennen, dat zowel fundamentele als complexe implementatievoorbeelden bevat.

Om je eigen animatie grafiek te maken, vergelijkbaar met het basisvoorbeeld dat in de referentie wordt gegeven, gebruik je de volgende stappen:

1.

Voeg in Studio een animeerbare rig toe door naar het Avatar -tabblad te navigeren en Character  ⟩ My Avatar  te selecteren.

 ![Karakterknop gemarkeerd in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Character.png)

2.

Open de Animatie Grafiek Editor door naar Grafiek Editor  in het Avatar -tabblad te navigeren.

 ![Animatie Grafiek Editor aangegeven in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Graph-Editor.png)

3.

Selecteer de animeerbare rig in de 3D-weergave. In de grafiekeditorweergave, selecteer Grafiek  in de linkerbovenhoek en selecteer Nieuw  om een nieuwe grafiek te maken.

4.

In de Grafiek Editor, klik met de rechtermuisknop en selecteer Knoop Invoegen  ⟩ Clip .

 ![Lijst van knopen in een rechtermuisklikmenu](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor/Node-List.png)

5.

Stel in de nieuwe Clip-knoop de Animatie-ID in.

1.

Selecteer de Animatie-ID  dropdown.

2.

Om een specifieke animatie asset-ID in te dienen, klik op Importeren .

 ![Aangegeven een veld op de animatie-importmodule om Animatie-ID toe te voegen](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor/Import-AnimationID.png)

3.

Voeg in het Animatie-ID -veld de standaard Loop-animatie toe: 507777826 .

4.

Selecteer Importeren .

6.

Voeg een andere clipknoop toe door stappen 4-5 te herhalen met de standaard Zwaaianimatie: 507770239 .

 ![Twee clipknopen met een ingevulde Animatie-ID](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor/Clip-Nodes-With-IDs.png)

7.

In de Grafiek Editor, klik met de rechtermuisknop en selecteer Toevoegen .

 ![Voeg knoop toe](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor/Add-Node.png)

8.

Verbind de Clip-knopen met de Toevoegen-knoop  door de rechterbovenste uitvoerconnector naar de juiste poort te slepen:

1.

Verbind de Clip -knoop met de Loop-animatie met de Basis -poort.

2.

Verbind de Clip -knoop met de Zwaaianimatie met de Additieve -poort.

 ![Beide clipknopen verbonden met de voegknop](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor/Connect-To-Add.png)

9.

Verbind vanaf de Voeg-knoop de rechterbovenste uitvoerconnector met de Grafiekuitvoer Pose -poort.

 ![Alle knopen verbonden met een laatste uitvoerknop](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor/Connect-The-Clip-Nodes.png)

10.

OPTIONEEL

 Wijs een parameter toe aan je Snelheid -variabele.

1.

Klik en sleep de groene Snelheid-poort naar een leeg gebied. Een nieuwe parameterknoop wordt weergegeven.

 ![Klik en sleep connector van Snelheid-poort van Clip-knoop.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor/Parameter-Noodle.png)

2.

Gebruik in de linkerbovenhoek van de grafiekeditor het parameterpaneel om snel parameters in je knopen te wijzigen. Je kunt ook [programmatig](#api-integratie)  toegang krijgen.

 ![Parameterpaneel, parameterknoop en clipknoop die gedeelde waarden tonen.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor/Parameter-Pane.png)

11.

Test de animatie door op de afspeelknop  te drukken.

 ![Afspelen knopicoon voor het previewen van animaties](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor/Play-Preview-Button.png)

12.

Probeer verschillende gewichten, snelheden, speelmodi en andere animaties uit. Voor meer informatie over individuele knopen, zie de [Knoopreferentie](#knoopreferentie) .

Bekijk de [referentieplaats](https://www.roblox.com/games/92493993350916/Animation-Graph-Editor-Simple-Demo)  voor verschillende voorbeelden van verschillende animatie grafiekconfiguraties.

## [API-integratie](#api-integratie)[](#api-integratie)

Het maken en implementeren van een Animatie Grafiek volgt de standaard Roblox animatiepipeline. Nadat je een rig in de Animatie Grafiek Editor hebt geselecteerd, wordt er een nieuwe AnimationGraphDefinition  asset aangemaakt. Deze asset dient als de container voor je knopen, verbindingen en parameters. Zodra je logica is afgerond, publiceer je de grafiek om een standaard Asset-ID te ontvangen.

In je scripts interacteer je met deze grafieken door ze te laden op een [Animator](/docs/nl-nl/reference/engine/classes/Animator)  zoals je dat zou doen met een traditionele animatie. Om de interne logica van de grafiek aan te sturen, gebruik je [AnimationTrack:SetParameter()](/docs/nl-nl/reference/engine/classes/AnimationTrack#SetParameter)  om realtime waarden - zoals bewegingssnelheid of staat booleans - direct in de variabelen van de grafiek door te geven.

```

local animation = Instance.new("Animation")

animation.AnimationId = "rbxassetid://123456789" -- Je Gepubliceerde Grafiek ID

local animationTrack = animator:LoadAnimation(animation)

animationTrack:Play()

-- Dynamische parameterupdates via RunService

game:GetService("RunService").Stepped:Connect(function(_, dt)

    local currentSpeed = humanoidRootPart.AssemblyLinearVelocity.Magnitude

    animationTrack:SetParameter("humanoidSpeed", currentSpeed)

end)

```

## [Knoopreferentie](#knoopreferentie)[](#knoopreferentie)

Voor details over elk knooptype, zie [Enum.AnimationNodeType](/docs/nl-nl/reference/engine/enums/AnimationNodeType) .

### [Globale evenementregels](#globale-evenementregels)[](#globale-evenementregels)

Voor alle knopen en [overgangen](#overgangen)  gelden standaard de volgende regels:

-

Evenementen verspreiden zich omhoog vanuit hun bronknoop door de grafiek. Elk evenement draagt een gewicht dat de invloed van de bron in de uiteindelijke mix vertegenwoordigt. Als het gewicht op enig moment nul bereikt, wordt het evenement gedempt.

-

Knopen zonder aangepaste evenementlogica geven alle evenementen onveranderd door; knopen die mengen of selecteren tussen invoer kunnen het gewicht schalen of evenementen van niet-primaire invoer blokkeren (zie per-knoop Evenementsectie).

-

Marker evenementen die de top van de grafiek bereiken, kunnen worden waargenomen via [AnimationTrack:GetMarkerReachedSignal()](/docs/nl-nl/reference/engine/classes/AnimationTrack#GetMarkerReachedSignal) .

## [Overgangen](#overgangen)[](#overgangen)

Verschillende knopen in de Animatie Grafiek (zoals Select , Priority Select , Sequence , en Random Sequence ) beheren hoe animaties mengen bij het schakelen tussen actieve invoer. Om redundantie in de knoopreferentie te voorkomen, worden deze gedragingen gedefinieerd door gestandaardiseerde overgangseigenschappen.

### [Standaardovergang](#standaardovergang)[](#standaardovergang)

 ![Standaard Overgang](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor/Transition-Default.png)

Het basis menggedrag dat op de knoop wordt toegepast telkens wanneer deze overschakelt naar een nieuwe actieve invoer.

-

DefaultTransitionDuration  (nummer): De tijd (in seconden) die nodig is om volledig in de nieuwe pose te mengen.

-

DefaultTransitionCurve  ([Enum.PoseEasingStyle](/docs/nl-nl/reference/engine/enums/PoseEasingStyle) ): De versnellingsfunctie die tijdens de mix wordt toegepast. Ondersteunt momenteel alleen [Enum.PoseEasingStyle.Linear](/docs/nl-nl/reference/engine/enums/PoseEasingStyle#Linear)  en [Enum.PoseEasingStyle.CubicV2](/docs/nl-nl/reference/engine/enums/PoseEasingStyle#CubicV2) .

### [Overgangsoverschrijving](#overgangsoverschrijving)[](#overgangsoverschrijving)

 ![Overgangsoverschrijving](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor/Transition-Override.png)

Invoerspecifieke koppelingseigenschappen die de standaardovergang overschrijven. Duur en curve-overschrijvingen worden toegepast wanneer de knoop naar  die invoer overgaat, behalve voor BeforeFinished -overgangen, die de overschrijvingen van de uitgaande invoer gebruiken.

-

TransitionOverrideDuration  (nummer): Overschrijft de standaardovergangsduur.

-

TransitionOverrideCurve  ([Enum.PoseEasingStyle](/docs/nl-nl/reference/engine/enums/PoseEasingStyle) ): Overschrijft de standaardovergangscurve. Ondersteunt momenteel alleen [Enum.PoseEasingStyle.Linear](/docs/nl-nl/reference/engine/enums/PoseEasingStyle#Linear)  en [Enum.PoseEasingStyle.CubicV2](/docs/nl-nl/reference/engine/enums/PoseEasingStyle#CubicV2) .

### [Overgangstiming](#overgangstiming)[](#overgangstiming)

Voor sequentieknooptypes regelen de volgende instellingen wanneer de sequentie naar de volgende invoer overgaat:

-

WaitFor  (Enum.AnimationNodeWaitFor ): Stelt de voorwaarde in voor vooruitgang. Gebruik Enum.AnimationNodeWaitFor|Finished  (standaard) om te wachten tot de huidige invoer is voltooid of een lus is voltooid, of Enum.AnimationNodeWaitFor|Trigger  om vooruit te gaan wanneer WaitForTrigger  waar  is. Stel de knoopniveau standaard in met DefaultWaitFor , of overschrijf deze voor een invoer met TransitionOverrideWaitFor .

-

Wanneer  (Enum.AnimationNodeTransitionWhen ): Toegepast wanneer Wacht Voor  Enum.AnimationNodeWaitFor|Finished  is. Stel de knoopniveau standaard in met DefaultTransitionWhen , of overschrijf deze voor de uitgaande invoer met TransitionOverrideWhen .

-

Enum.AnimationNodeTransitionWhen|Finished  (standaard): Begint te mengen nadat de huidige invoer is voltooid.

-

Enum.AnimationNodeTransitionWhen|BeforeFinished : Begint te mengen één overgangsduur voordat de huidige invoer is voltooid, zodat de mix overlapt met het einde van zijn animatie. Bijvoorbeeld, een overgang van 0,2 seconden begint tijdens de laatste 0,2 seconden van de animatie.

[RandomSequenceNode](/docs/nl-nl/reference/engine/enums/AnimationNodeType)  ondersteunt ook DefaultTransitionWhen  en TransitionOverrideWhen  om te regelen wanneer de mix begint.

Voor toestandsmachineovergangen, zie [Overgangseigenschappen](/docs/nl-nl/animation/graph-editor-state-machine#overgangseigenschappen) .

## [Replicatie](#replicatie)[](#replicatie)

Animatie grafiekparameters en interne knoopstatus repliceren automatisch. De replicatiemodus wordt bepaald door [Workspace.AuthorityMode](/docs/nl-nl/reference/engine/classes/Workspace#AuthorityMode)  op het moment dat het Animate-script wordt aangemaakt:

-

In [Enum.AuthorityMode.Automatic](/docs/nl-nl/reference/engine/enums/AuthorityMode#Automatic) : Parameters ingesteld via [AnimationTrack:SetParameter()](/docs/nl-nl/reference/engine/classes/AnimationTrack#SetParameter)  repliceren automatisch naar andere peers.

-

In [Enum.AuthorityMode.Server](/docs/nl-nl/reference/engine/enums/AuthorityMode#Server) : De server stuurt de volledige grafieksimulatie aan. Alle knoopstatussen, zoals verstreken tijd voor [Enum.AnimationNodeType.ClipNode](/docs/nl-nl/reference/engine/enums/AnimationNodeType#ClipNode) , en grafiekparameters repliceren automatisch van server naar clients. De client van de eigenaar speler gebruikt voorspelling voor soepele lokale afspelen.

### [Voorbeeld Animate Scripts](#voorbeeld-animate-scripts)[](#voorbeeld-animate-scripts)

Om voorbeeldscripts te genereren om een animatie grafiek voor een rig aan te sturen, gebruik je Grafiek -> Maak Animate-script  in de Animatie Grafiek Editor. Dit produceert een scriptstructuur die onder [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts)  (voor spelerskarakters) of direct op de rig (voor NPC's) wordt geplaatst:

```

Animate (ModuleScript)

├── RunClient (LocalScript)

└── RunServer (Script, RunContext = Legacy)

```

De Animate  [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  bevat de logica voor het laden van de grafiek. De RunClient  en RunServer  scripts roepen het aan in de juiste context. Welke scripts zijn inbegrepen, hangt af van de gebruikscontext:

| Gebruikscase | | Inbegrepen Scripts | | Gedrag |
| --- | --- |
| NPC  (elke modus) | | RunServer | | Server laadt en speelt de grafiek af. Status repliceren naar alle clients automatisch. |
| Speler + [Enum.AuthorityMode.Server](/docs/nl-nl/reference/engine/enums/AuthorityMode#Server) | | RunServer + RunClient | | Server stuurt de grafiek autoritatief aan. De eigenaar client schakelt [Enum.PredictionMode](/docs/nl-nl/reference/engine/enums/PredictionMode)  in voor rollback-gebaseerde lokale voorspelling. |
| Speler + [Enum.AuthorityMode.Automatic](/docs/nl-nl/reference/engine/enums/AuthorityMode#Automatic) | | RunClient | | Eigenaar client laadt en speelt de grafiek af. Parameters repliceren automatisch naar de server en andere clients. |

De volgende attributen worden opgeslagen op het Animate-script en configureren het gedrag ervan:

| Attribuut | | Type | | Beschrijving |
| GraphName | | String | | Naam van de animatie grafiek asset. |
| CharacterName | | String | | Naam van de rig waarop de grafiek gericht is. |
| SourceAssetId | | String | | De gepubliceerde Asset-ID van de grafiek. Gebruikt tijdens runtime in gepubliceerde games. |
| IsServerAuthority | | Boolean | | Of het script is aangemaakt met [Workspace.AuthorityMode](/docs/nl-nl/reference/engine/classes/Workspace#AuthorityMode)  ingesteld op Server . Bepaalt de replicatiestrategie. |
| PreviewInStudio | | Boolean | | Wanneer waar (standaard), laadt Studio play-testing de ongepubliceerde grafiek lokaal zodat je kunt itereren zonder te publiceren. Stel in op onwaar om de gepubliceerde asset in Studio te testen. Merk op dat dit momenteel niet wordt ondersteund in [Enum.AuthorityMode.Server](/docs/nl-nl/reference/engine/enums/AuthorityMode#Server) . |

### [Parameterreplicatie in Automatische modus](#parameterreplicatie-in-automatische-modus)[](#parameterreplicatie-in-automatische-modus)

Wanneer [Workspace.AuthorityMode](/docs/nl-nl/reference/engine/classes/Workspace#AuthorityMode)  Automatisch  is:

-

De eigenaar client  stuurt de grafieken van spelerskarakters aan; de server  stuurt de grafieken van NPC's aan.

-

Parameters ingesteld via [AnimationTrack:SetParameter()](/docs/nl-nl/reference/engine/classes/AnimationTrack#SetParameter)  worden automatisch gerepliceerd naar andere peers. Meerdere SetParameter -aanroepen binnen een enkel frame worden samengevoegd (laatste schrijver wint).

-

Geen extra scripting is nodig voor parametertransport - de engine behandelt replicatie intern.

-

Andere clients zien parameterupdates met een kleine vertraging (één verzendinterval plus netwerklatentie).

### [Serverautoriteit](#serverautoriteit)[](#serverautoriteit)

Wanneer [Workspace.AuthorityMode](/docs/nl-nl/reference/engine/classes/Workspace#AuthorityMode)  Server  is:

-

De server  is autoritatief voor alle grafieken - hij draait de simulatie en repliceert de volledige grafiekstatus.

-

Wat wordt gerepliceerd : Zowel parameters als interne knoopstatus, inclusief verstreken tijd, huidige selecties, overgangsvoortgang, luscounts en RNG-zaden. Dit zorgt ervoor dat alle clients identiek animatiegedrag zien.

-

Spelerskarakters : De server stuurt de grafiek aan. Het RunClient -script van de eigenaar client schakelt automatisch [Enum.PredictionMode](/docs/nl-nl/reference/engine/enums/PredictionMode)  in op de [Animator](/docs/nl-nl/reference/engine/classes/Animator) , zodat de lokale speler soepele, voorspelde animatie ziet die wordt verzoend met de server bij een mismatch.

-

NPC's : De server stuurt de grafiek exclusief aan; clients observeren de gerepliceerde status zonder lokale simulatie.

### [Parameters aansturen](#parameters-aansturen)[](#parameters-aansturen)

Gebruik [AnimationTrack:SetParameter()](/docs/nl-nl/reference/engine/classes/AnimationTrack#SetParameter)  vanuit elk script dat de grafiek draait:

-

NPC (elke modus) : Roep SetParameter  aan vanuit RunServer  (of een andere server [Script](/docs/nl-nl/reference/engine/classes/Script)  met toegang tot de [AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack) ).

-

Spelerskarakter in [Enum.AuthorityMode.Server](/docs/nl-nl/reference/engine/enums/AuthorityMode#Server) : Roep SetParameter  aan vanuit zowel  RunServer  als RunClient . De server heeft parameters nodig om de autoritatieve simulatie aan te sturen, en de eigenaar client heeft dezelfde parameters nodig om zijn lokale voorspelling aan te sturen.

-

Spelerskarakter in [Enum.AuthorityMode.Automatic](/docs/nl-nl/reference/engine/enums/AuthorityMode#Automatic) : Roep SetParameter  aan vanuit RunClient  (of een andere client [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  met toegang tot de [AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack) ).

Het gegenereerde Animate-script bevat een uitgecommentarieerde SetParameter -blok als startpunt. Verwijder de commentaar en wijzig het om parameters aan te sturen vanuit de gameplaystatus (bewegingssnelheid, humanoïde status, invoerrichting, enz.).

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
