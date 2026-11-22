<!-- Source: https://create.roblox.com/docs/nl-nl/physics/assemblies -->

Assemblages | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Fysica](/docs/nl-nl/physics)

# Assemblages

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een assemblage  is een of meer [onderdelen](/docs/nl-nl/parts)  die zijn gelast door een rigide [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint)  of verbonden zijn via beweegbare gewrichten, zoals [Motor6Ds](/docs/nl-nl/reference/engine/classes/Motor6D) . Je kunt een assemblage van onderdelen groeperen in een [model](/docs/nl-nl/parts/models)  container om de onderdelen en gerelateerde objecten snel te organiseren als een enkele asset.

![Een lichtblauwe kubus tegen een donkerblauwe achtergrond die een assemblage van 1 onderdeel vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Example-Block.png) 1 assemblage; 1 onderdeel

![Een humanoïde karaktermodel tegen een donkerblauwe achtergrond die een assemblage van 18 onderdelen vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Example-Avatar.png) 1 assemblage; 18 onderdelen

![Een piratenschip dat een assemblage van 179 onderdelen vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Example-Ship.png) 1 assemblage; 179 onderdelen

Vanuit een fysisch perspectief wordt een assemblage beschouwd als een enkele rigide lichaam , wat betekent dat geen enkele kracht de verbonden onderdelen van elkaar kan duwen of trekken, en ze zullen als een enkele eenheid bewegen. Alle krachten die op een specifiek [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  worden toegepast, worden op zijn assemblage toegepast — bijvoorbeeld, [BasePart:ApplyImpulse()](/docs/nl-nl/reference/engine/classes/BasePart#ApplyImpulse)  past een impuls toe op de assemblage bij [BasePart.AssemblyCenterOfMass](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyCenterOfMass) .

De gewrichten die meerdere onderdelen in assemblages combineren, zijn alleen actief in de [Workspace](/docs/nl-nl/reference/engine/classes/Workspace)  of een andere [WorldModel](/docs/nl-nl/reference/engine/classes/WorldModel)  instantie. Als de onderdelen elders zijn opgeslagen, zullen alle lasverbindingen/verbindingen die onderdelen in assemblages combineren niet functioneren.

Om gekleurde omtrekken rond onderdelen te bekijken om enkele rigide lichaam assemblages te visualiseren, schakel Assemblages  in vanuit de [Visualisatie Opties](/docs/nl-nl/studio/overview#visualisatie-opties)  widget in de rechterbovenhoek van het 3D-venster.

## [Assemblage-eigenschappen](#assemblage-eigenschappen)[](#assemblage-eigenschappen)

De volgende [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  eigenschappen tonen gegevens met betrekking tot zijn assemblage. Hun waarden zullen hetzelfde zijn voor elk onderdeel in dezelfde assemblage, dus het maakt niet uit welk onderdeel je gebruikt.

| Eigenschap | | Beschrijving |
| --- | --- |
| [BasePart.AssemblyLinearVelocity](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyLinearVelocity) | | De lineaire snelheidsvector van de assemblage van het onderdeel. Het direct instellen van de snelheid kan leiden tot onrealistische beweging, dus het gebruik van een [VectorForce](/docs/nl-nl/reference/engine/classes/VectorForce)  of [LinearVelocity](/docs/nl-nl/reference/engine/classes/LinearVelocity)  beperking heeft de voorkeur, of [BasePart:ApplyImpulse()](/docs/nl-nl/reference/engine/classes/BasePart#ApplyImpulse)  voor een onmiddellijke verandering in lineaire snelheid. |
| [BasePart.AssemblyAngularVelocity](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyAngularVelocity) | | De hoeksnelheidsvector van de assemblage van het onderdeel. Het direct instellen van de snelheid kan leiden tot onrealistische beweging, dus het gebruik van een [Torque](/docs/nl-nl/reference/engine/classes/Torque)  of [AngularVelocity](/docs/nl-nl/reference/engine/classes/AngularVelocity)  beperking heeft de voorkeur, of [BasePart:ApplyAngularImpulse()](/docs/nl-nl/reference/engine/classes/BasePart#ApplyAngularImpulse)  voor een onmiddellijke verandering in hoeksnelheid. |
| [BasePart.AssemblyCenterOfMass](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyCenterOfMass) | | Een alleen-lezen positie die is berekend via de massa en positie van alle onderdelen in de assemblage. Een kracht die op het zwaartepunt wordt toegepast, zal geen hoeksversnelling veroorzaken, alleen lineaire. |
| [BasePart.AssemblyMass](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyMass) | | De som van de [BasePart.Mass](/docs/nl-nl/reference/engine/classes/BasePart#Mass)  van alle onderdelen in de assemblage. Als de assemblage een verankerd onderdeel heeft, wordt de massa van de assemblage als oneindig beschouwd. |
| [BasePart.AssemblyRootPart](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyRootPart) | | Het onderdeel dat automatisch is gekozen om het [wortelonderdeel](#wortelonderdeel-van-de-assemblage)  van de assemblage weer te geven. |

## [Wortelonderdeel van de assemblage](#wortelonderdeel-van-de-assemblage)[](#wortelonderdeel-van-de-assemblage)

Elke assemblage heeft een wortelonderdeel  dat wordt aangegeven door zijn [AssemblyRootPart](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyRootPart)  eigenschap. Dit is het onderdeel dat niet beweegt wanneer [Motor6D](/docs/nl-nl/reference/engine/classes/Motor6D)  transformaties worden bijgewerkt, evenals het onderdeel dat wordt gebruikt om consistente fysica-replicatie en netwerkbezit te behouden.

Je kunt het wortelonderdeel niet expliciet instellen, maar de volgende factoren beïnvloeden de waarschijnlijkheid van hoog naar laag:

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Higher.png)

Een [Anchored](/docs/nl-nl/reference/engine/classes/BasePart#Anchored)  onderdeel zal altijd worden toegewezen als het wortelonderdeel.

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-High.png)

Onderdelen met [Massless](/docs/nl-nl/reference/engine/classes/BasePart#Massless)  ingesteld op false  (standaard) hebben voorrang.

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Low.png)

Hogere [RootPriority](/docs/nl-nl/reference/engine/classes/BasePart#RootPriority)  waarden hebben voorrang.

![](https://prod.docsiteassets.roblox.com/assets/misc/Arrow-Lower.png)

Voorrang op basis van de grootte van het onderdeel (grootste oppervlakte), met vermenigvuldigers voor specifieke onderdeeltypes. [Seats](/docs/nl-nl/reference/engine/classes/Seat)  en [VehicleSeats](/docs/nl-nl/reference/engine/classes/VehicleSeat)  ontvangen de hoogste vermenigvuldiger, gevolgd door onderdelen genaamd HumanoidRootPart , en dan onderdelen genaamd Torso .

## [Gedrag bij verankering](#gedrag-bij-verankering)[](#gedrag-bij-verankering)

Wanneer een van de onderdelen van een assemblage is verankerd, wordt dat onderdeel het wortelonderdeel en worden alle andere onderdelen impliciet met het verankerde onderdeel verankerd. De volgende volgorde illustreert dit gedrag.

1.

Hieronder zijn vier onderdelen aan elkaar gelast met [WeldConstraints](/docs/nl-nl/reference/engine/classes/WeldConstraint)  (groene stangen) om een enkele assemblage te vormen, zoals aangegeven door de bijpassende gekleurde omtrekken.

![](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Anchor-Diagram-1.png) Vier onderdelen gelast om een enkele assemblage te worden

2.

Als slechts één  onderdeel in de assemblage is verankerd, zal de assemblage niet veranderen, behalve dat het wortelonderdeel mogelijk verandert (het verankerde onderdeel heeft altijd de hoogste [prioriteit](#wortelonderdeel-van-de-assemblage)  om het wortelonderdeel te worden).

![](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Anchor-Diagram-2.png) Verankerd onderdeel (aangegeven met een ankericoon) wordt het nieuwe wortelonderdeel

3.

Als meer dan één onderdeel is verankerd, zal de assemblage splitsen . Hieronder zijn zowel de linker als de bovenste onderdelen verankerd, zodat de oorspronkelijke assemblage in twee assemblages splitst zoals weergegeven door de gekleurde omtrekken. Ook de [WeldConstraint](/docs/nl-nl/reference/engine/classes/WeldConstraint)  tussen de twee assemblages deactiveert, aangezien je geen actieve lasverbinding kunt hebben tussen twee verankerde assemblages.

![](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Anchor-Diagram-3.png) Twee assemblages met verankerde onderdelen als hun respectieve wortelonderdelen

Als je alle onderdelen in een assemblage wilt verankeren, hoef je alleen het wortelonderdeel van de assemblage te verankeren. Het verankeren van alle onderdelen is eigenlijk minder efficiënt, omdat het meer assemblages creëert.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
