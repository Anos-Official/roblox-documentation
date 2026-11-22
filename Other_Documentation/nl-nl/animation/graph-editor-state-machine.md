<!-- Source: https://create.roblox.com/docs/nl-nl/animation/graph-editor-state-machine -->

Grafiekeditor toestandsmachines | Documentatie - Roblox Creator Hub

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

# Grafiekeditor toestandsmachines

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een toestandsmachine  combineert animatienodes in benoemde toestanden, zoals Idle , Walk , Run  en Jump . Het speelt de actieve toestand en mengt naar een andere toestand wanneer een overgangsvoorwaarde evalueert naar true . Gebruik een toestandsmachine om te definiëren welke animaties elkaar kunnen opvolgen zonder overgangslogica in Luau te schrijven.

Elke toestand is verbonden met een invoer op de toestandsmachine. Een toestand kan een clip, een blendnode of een andere toestandsmachine zijn. De toestandsmachine geeft de actieve animatiepose of een mengsel tussen twee poses weer als er een overgang plaatsvindt, die je verbindt met de volgende node in de grafiek.

## [Vereisten](#vereisten)[](#vereisten)

Voordat je een toestandsmachine maakt, maak je jezelf vertrouwd met de [Animatie Grafiekeditor](/docs/nl-nl/animation/graph-editor) , inclusief hoe je [deze opent en een animatiegrafiek maakt](/docs/nl-nl/animation/graph-editor#bouw-een-grafiek) .

## [Maak een toestandsmachine](#maak-een-toestandsmachine)[](#maak-een-toestandsmachine)

Het volgende voorbeeld gebruikt drie toestanden van JumpFallLandRunExample : Locomotion , Fall  en LandIdle . Het personage beweegt normaal, schakelt over naar een vallende animatie wanneer het in de lucht is, en speelt een landinganimatie voordat het terugkeert naar locomotie. Deze stappen richten zich op de toestandsmachine; begin met animatienodes voor locomotie, vallen en landen.

1.

In de Grafiekeditor , klik met de rechtermuisknop en selecteer Node Invoegen  ⟩ Toestandsmachine .

 ![Grafiekeditor contextmenu met het submenu Node Invoegen geopend en Toestandsmachine geselecteerd.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-state-machine/Insert-State-Machine.png)

2.

Klik op de toestandsmachinenode op Openen . In de Toestandsmachine -weergave, gebruik Toestand Maken  om drie toestanden toe te voegen met de namen Locomotion , Fall  en LandIdle .

 ![Toestandsmachineweergave met de knop Toestand Maken en de Entry- en Any-toestandsnodes.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-state-machine/Add-A-State.png)

3.

Klik op Terug naar Grafiek  en verbind je animatienodes met de bijbehorende invoeren van de toestandsmachine:

-

Locomotion : Verbind je locomotie-animatie. De referentiegrafiek gebruikt een [Blend1DNode](/docs/nl-nl/reference/engine/enums/AnimationNodeType)  genaamd IdleRunBlend  om idle- en loopanimaties te mengen op basis van Speed .

-

Fall : Verbind een vallende [ClipNode](/docs/nl-nl/reference/engine/enums/AnimationNodeType)  en stel Afspeelmodus  in op Enum.AnimationNodePlayMode|OnceAndHold , zodat het zijn laatste pose vasthoudt totdat het personage landt.

-

LandIdle : Verbind een landingclip en stel Afspeelmodus  in op Enum.AnimationNodePlayMode|OnceAndHold , zodat het kan eindigen en terug kan overgaan naar locomotie.

Verbind de uitvoer van de toestandsmachine met de Pose -invoer van Grafiekuitvoer .

 ![IdleRunBlend, Fall en LandIdle nodes verbonden met de Locomotion, Fall en LandIdle invoeren van een toestandsmachinenode, waarvan de uitvoer is verbonden met Grafiekuitvoer.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-state-machine/Wire-Nodes-To-State-Machine.png)

4.

Open de Toestandsmachine -weergave opnieuw en sleep een overgang van (Entry)  naar Locomotion . De toestandsmachine begint in deze toestand wanneer de grafiek start.

 ![Entry-node verbonden met de Locomotion-toestand.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-state-machine/Entry-State-To-Locomotion.png)

5.

Voeg een Booleaanse grafiekparameter toe met de naam Grounded  en stel deze in op true . Deze parameter geeft aan of het personage op de grond staat.

6.

Voeg de volgende overgangen toe door een verbinding van de brontoestand naar de bestemmingsstaat te slepen en configureer elke overgang:

-

Locomotion  naar Fall : Stel Wacht Op  in op [Expressie](/docs/nl-nl/animation/expressions) , Expressie  op not Grounded , en Lengte  op 0.2  seconden. De vallende animatie begint wanneer het personage de grond verlaat.

-

Fall  naar LandIdle : Stel Wacht Op  in op Expressie , Expressie  op Grounded , en Lengte  op 0.1  seconden. De landinganimatie begint wanneer het personage de grond raakt.

-

LandIdle  naar Locomotion : Stel Wacht Op  in op Voltooid , Wanneer  op Enum.AnimationNodeTransitionWhen|BeforeFinished , en Lengte  op 0.2  seconden. De toestandsmachine begint terug te mengen naar locomotie tijdens de laatste 0.2 seconden van de landinganimatie.

 ![Overgangsinstellingen voor LandIdle naar Locomotion, met Lengte ingesteld op 0.2, Curve op Lineair, Wacht Op op Voltooid, en Wanneer op Voor Voltooid.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-state-machine/Transition-Settings.png)

7.

Laat Curve  als standaard ([Linear](/docs/nl-nl/reference/engine/enums/PoseEasingStyle) ) voor alle drie de overgangen. Bekijk de grafiek en wijzig Grounded  naar false  om Fall  in te gaan, en vervolgens terug naar true  om LandIdle  af te spelen en terug te keren naar Locomotion .

8.

Werk Grounded  bij vanuit je gameplaycode terwijl het personage de grond verlaat en raakt. Als je locomotieblend Speed  gebruikt, werk dan die parameter bij terwijl het personage beweegt. Voor de parameterworkflow, zie [API-integratie](/docs/nl-nl/animation/graph-editor#api-integratie) .

9.

Breid de toestandsmachine uit met springen en extra landingsstaten om de volledige bewegingsgrafiek te creëren. JumpFallLandRunExample  bevat aparte sprongen voor staan en rennen, plus verschillende landingen op basis van beweging en val snelheid.

Voor de volledige toestandsmachine, open JumpFallLandRunExample  in de [referentieplaats](https://www.roblox.com/games/116845448376632) .

## [Toestandsmachine-eigenschappen](#toestandsmachine-eigenschappen)[](#toestandsmachine-eigenschappen)

### [Eigenschappen van de toestandsmachinenode](#eigenschappen-van-de-toestandsmachinenode)[](#eigenschappen-van-de-toestandsmachinenode)

Invoeren

-

State1...StateN : De animatienodes die elke toestand definiëren. De naam van de toestand moet overeenkomen met de naam van de invoer naar de toestandsmachinenode.

Eigenschappen

| Eigenschap | | Type | | Beschrijving |
| --- | --- |
| EntryState | | [ObjectValue](/docs/nl-nl/reference/engine/classes/ObjectValue) | | Een [ObjectValue](/docs/nl-nl/reference/engine/classes/ObjectValue)  waarvan de [Value](/docs/nl-nl/reference/engine/classes/ObjectValue#Value)  verwijst naar de [AnimationNodeDefinition](/docs/nl-nl/reference/engine/classes/AnimationNodeDefinition)  voor de toestand die actief is wanneer de grafiek start. |

Evenementgegevens

-

Evenementverwerking:  Evenementen van de actieve toestand gaan door met hun gewicht onveranderd.

-

Evenementuitstoot:  Laat alleen evenementen van de actieve toestand door. Tijdens een overgang volgt de evenementuitstoot de [globale evenementregels](/docs/nl-nl/animation/graph-editor#globale-evenementregels) .

### [Overgangseigenschappen](#overgangseigenschappen)[](#overgangseigenschappen)

Een overgang heeft een of meer brontoestanden, een bestemmingsstaat en een voorwaarde. Wanneer de actieve toestand overeenkomt met een brontoestand, controleert de toestandsmachine de voorwaarde. Het mengt naar de bestemmingsstaat wanneer de voorwaarde evalueert naar true .

Wacht Op  bepaalt de overgangsvoorwaarde UI. Selecteer [Expressie](/docs/nl-nl/animation/expressions)  (Enum.AnimationNodeWaitFor|Trigger ) om een Expressie -vak weer te geven. Een Expressie  kan een Booleaanse grafiekparameter rechtstreeks verwijzen, zoals ShouldJump , of een voorwaarde evalueren, zoals Speed >= 12 . Selecteer Voltooid  (Enum.AnimationNodeWaitFor|Finished ) om de Wanneer  dropdown weer te geven.

Als meer dan één overgang een ware Expressie  heeft, evalueert de toestandsmachine eerst de overgang met de hoogste Prioriteit  waarde. Wanneer prioriteiten gelijk zijn, selecteert het willekeurig een overgang. Ken verschillende prioriteiten toe aan concurrerende overgangen om het resultaat voorspelbaar te maken.

| Eigenschap | | Type | | Beschrijving |
| Van | | [ObjectValue](/docs/nl-nl/reference/engine/classes/ObjectValue) | | Een [ObjectValue](/docs/nl-nl/reference/engine/classes/ObjectValue)  waarvan de [Value](/docs/nl-nl/reference/engine/classes/ObjectValue#Value)  verwijst naar de [AnimationNodeDefinition](/docs/nl-nl/reference/engine/classes/AnimationNodeDefinition)  voor de toestand die de overgang kan beginnen. Laat deze eigenschap leeg voor een (Any)  overgang. |
| Naar | | [ObjectValue](/docs/nl-nl/reference/engine/classes/ObjectValue) | | Een [ObjectValue](/docs/nl-nl/reference/engine/classes/ObjectValue)  waarvan de [Value](/docs/nl-nl/reference/engine/classes/ObjectValue#Value)  verwijst naar de [AnimationNodeDefinition](/docs/nl-nl/reference/engine/classes/AnimationNodeDefinition)  voor de bestemmingsstaat. |
| WachtOp | | Enum.AnimationNodeWaitFor | | Bepaalt welke overgangsvoorwaarde UI verschijnt. Enum.AnimationNodeWaitFor|Trigger  toont het Expressie -vak. Enum.AnimationNodeWaitFor|Finished  toont de Wanneer  dropdown. |
| Wanneer | | Enum.AnimationNodeTransitionWhen | | Beschikbaar wanneer Wacht Op  Voltooid  is. Selecteer Enum.AnimationNodeTransitionWhen|Finished  om te beginnen nadat de brontoestand is voltooid, of Enum.AnimationNodeTransitionWhen|BeforeFinished  om te beginnen met mengen één Duur  voordat de brontoestand voltooid is. |
| Expressie | | String | | Beschikbaar wanneer Wacht Op  [Expressie](/docs/nl-nl/animation/expressions)  is. Een Booleaanse grafiekparameter of expressie die, wanneer deze evalueert naar true , de overgang begint. Zie [Expressie](/docs/nl-nl/animation/expressions)  voor wat ondersteund wordt. |
| Prioriteit | | Nummer | | De volgorde die wordt gebruikt wanneer meer dan één Expressie  waar is. Hogere waarden hebben voorrang. Geldige waarden variëren van 0 tot 65.535. |
| Duur | | Nummer | | De tijd, in seconden, om in de bestemmingsstaat te mengen. De standaard is 0,15 seconden. |
| Curve | | [Enum.PoseEasingStyle](/docs/nl-nl/reference/engine/enums/PoseEasingStyle) | | De easing die wordt gebruikt tijdens de menging. Alleen [Linear](/docs/nl-nl/reference/engine/enums/PoseEasingStyle)  en [CubicV2](/docs/nl-nl/reference/engine/enums/PoseEasingStyle)  worden ondersteund. De standaard is [Linear](/docs/nl-nl/reference/engine/enums/PoseEasingStyle) . |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
