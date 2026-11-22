<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/automatic-skinning-transfer -->

Automatische Skinning Overdracht | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)

# Automatische Skinning Overdracht

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Automatische Skinning Overdracht  stelt gelaagde accessoires en gezichtsaccessoires in staat om nauwkeurig te vervormen samen met het karaktermodel waaraan ze zijn bevestigd, zonder dat je de accessoire zelf hoeft te skinnen. In plaats van de complexe taak van handmatig [riggen en skinnen](/docs/nl-nl/art/modeling/rigging)  van modellen in 3D-modelleringssoftware, kun je deze functie gebruiken om skinninggegevens naar de accessoire over te dragen of te genereren. Bij het gebruik van Automatische Skinning Overdracht creëert en past de Roblox-engine skinning toe tijdens runtime.

Er is geen skinning van accessoire-geometrie vereist om Automatische Skinning Overdracht te gebruiken . In feite werken automatisch geskinte accessoires goed en bewegen ze nauwkeurig met de meeste karakters waaraan ze zijn bevestigd terwijl ze animeren, zelfs als die karakters een ander aantal gewrichten, botten hebben of een ander soort skinning gebruiken.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Automatic-Skinning-Transfer-Intro.jpg)

Skinning is nog steeds een belangrijk concept voor karaktercreatie, en als je aangepaste karakters maakt, wil je misschien skinninggegevens op het model toepassen om een karakter te creëren met natuurlijker uitziende poses en animaties. Voor informatie over hoe je een mesh kunt skinnen, zie [Skin een humanoïde model](/docs/nl-nl/art/modeling/skin-a-humanoid-model) .

## [Automatische Skinning Overdracht inschakelen](#automatische-skinning-overdracht-inschakelen)[](#automatische-skinning-overdracht-inschakelen)

Om het proces van Automatische Skinning Overdracht in te schakelen, moet je:

1.

[StarterPlayer.LoadCharacterLayeredClothing](/docs/nl-nl/reference/engine/classes/StarterPlayer#LoadCharacterLayeredClothing)  in je game inschakelen.

2.

De [AutoSkin](/docs/nl-nl/reference/engine/classes/WrapLayer#AutoSkin)  eigenschap binnen de [WrapLayer](/docs/nl-nl/reference/engine/classes/WrapLayer)  instantie van de gelaagde [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  die je automatisch wilt skinnen inschakelen, en deze instellen op een van de volgende waarden:

-

EnabledOverride : Schakelt het proces van Automatische Skinning Overdracht in en staat het toe om bestaande skinninginformatie die op de accessoire is gevonden tijdens runtime te overschrijven.

-

EnabledPreserve : Schakelt het proces van Automatische Skinning Overdracht in, maar staat niet toe dat het bestaande skinninginformatie die op de accessoire is gevonden tijdens runtime overschrijft. Als er geen skinning is om te behouden, creëert het proces van Automatische Skinning Overdracht automatisch nieuwe skinninggegevens.

Wanneer er geen skinninggegevens op de accessoire zijn, of als je ervoor kiest om bestaande skinninggegevens die aan de accessoire zijn gekoppeld te overschrijven, berekent de Roblox-engine skinninggegevens op basis van de geometrie en kooien van het karakter, waarna de nieuwe skinninggegevens en rig die aan de accessoire zijn gekoppeld de vervormingen en bewegingen van de accessoire aansturen in sync met de brongeometrie zelf.

## [Beste praktijken](#beste-praktijken)[](#beste-praktijken)

Omdat het proces van Automatische Skinning Overdracht gebruikmaakt van de buitenste kooi van het karakterlichaam om te helpen bij het berekenen van skinninggegevens die op de accessoire moeten worden toegepast, is het belangrijk dat aan alle [vereisten voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications)  wordt voldaan bij het maken van accessoires.

Hoewel Automatische Skinning Overdracht vaak beter werkt dan handmatig skinnen, zijn er enkele beste praktijken om onverwacht gedrag met het skinningproces van gelaagde accessoires te verminderen. Zoals bij alle modelleringsprocessen, test je gelaagde accessoires en gezichtsaccessoires voortdurend op verschillende avatar-types om de gewenste resultaten te bereiken.

### [Speciale skinning overdracht gewrichten](#speciale-skinning-overdracht-gewrichten)[](#speciale-skinning-overdracht-gewrichten)

Automatische Skinning Overdracht werkt mogelijk niet goed voor bepaalde gedetailleerde accessoiretypes, zoals wimpers of wenkbrauwen. Om een meer gecontroleerd skinningoverdrachtresultaat te krijgen, heb je de optie om accessoire-geometrie te skinnen naar een van de twee speciaal benoemde gewrichten: RBX_Leader  en RBX_Follower .

Het is het beste om deze gewrichten/botten direct onder het Root  gewricht in je hiërarchie te creëren voor eenvoud en duidelijkheid. Deze gewrichten/botten worden niet gedetecteerd als onderdeel van het [rigging armature](/docs/nl-nl/avatar/character-bodies/specifications#rigging)  van je karaktermodel bij import.

Alle vertices die zijn geskinnd naar RBX_Leader  ondergaan hetzelfde overdrachtsproces dat vandaag de dag bestaat. Echter, alle vertices die zijn geskinnd naar RBX_Follower  worden overgedragen op basis van hun dichtstbijzijnde leider-vertex. Dit zorgt voor betere resultaten in situaties zoals een wimper waarbij de punt van een wimperstreng normaal gesproken naar een plek op het wenkbrauwgebied zou overdragen in plaats van de basis van de wimperstreng te volgen bij beweging.

De bovenste wimpers nabij de brug van de neus volgen de oogleden niet zoals verwacht omdat ze geen overdrachtsgewrichten bevatten.

Alle wimpers volgen de leidende vertices die het dichtst bij de ogen liggen omdat ze overdrachtsgewrichten bevatten.

Voor wimpers zijn goede kandidaten voor RBX_Leader  degenen die bedoeld zijn om direct op het ooglid van het karakter te zitten. De overige vertices kunnen worden geskinnd naar RBX_Follower .

![Screenshot van vertices toegewezen als leider.](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Vertices-Group-Leader.png) Vertices van een wimper toegewezen aan een RBX_Leader  bot-vertexgroep.

![Screenshot van vertices toegewezen als volger.](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Vertices-Group-Follower.png) Vertices van een wimper toegewezen aan een RBX_Follower  bot-vertexgroep.

Voor wenkbrauwen zijn goede kandidaten voor RBX_Leader  vertices langs de randen die de wenkbrauwlijn overspannen.

![Screenshot van vertices toegewezen als leider.](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Eyebrows-Follower-Vertices.png) Vertices van een wenkbrauw toegewezen aan een RBX_Leader  bot-vertexgroep.

![Screenshot van vertices toegewezen als volger.](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Eyebrows-Leader-Vertices.png) Vertices van een wenkbrauw toegewezen aan een RBX_Follower  bot-vertexgroep.

In Blender, gebruik de Object Data Properties  > Vertex Groups  om je vertexgroeptoewijzingen te beheren en te bekijken.

 ![Screenshot van eigenschappenpaneel met vertexgroeptoewijzingen](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Vertices-Group-Assign.png)

In Blender worden vertexgroepen automatisch aangemaakt nadat je een botobject hebt gemaakt. Dit stelt je in staat om snel vertices aan een specifieke bot-vertexgroep toe te wijzen.

Er is geen extra werk nodig in Studio om deze methode te ondersteunen. Als je gelaagde accessoire is ingesteld op Class.WrapLayer.AutoSkin.EnabledOverride  en deze gewrichten bestaan met vertices die aan hen zijn toegewezen, is deze skinningoverdrachtsvariant van kracht.

Als je een accessoire wilt uploaden met deze gewrichten als een UGC-item, zijn er een paar regels waar je rekening mee moet houden:

-

Vertices kunnen niet gedeeltelijk aan deze gewrichten zijn gewogen. Als je ze wilt gebruiken, moet je de vertex aan het gewricht skinnen met een gewicht van 1.0 .

-

Als deze gewrichten aanwezig zijn in de mesh, moet de accessoire zijn ingesteld op WrapLayerAutoSkin.EnabledOverride .

-

Meshes van lichaamsdelen die deze gewrichten bevatten, worden afgewezen door validatie.

-

Wenkbrauw- en wimperaccessoiretypes moeten de speciale skinninggewrichten hebben en zijn ingesteld op WrapLayerAutoSkin.EnabledOverride .

### [Wijzig karakterkooien](#wijzig-karakterkooien)[](#wijzig-karakterkooien)

Je kunt geen activa met een gedeeltelijke kooi uploaden naar de Marketplace. Je kunt gedeeltelijke kooien gebruiken voor activa die bedoeld zijn voor gebruik in de game, maar het validatieproces van de Marketplace zal activa met gedeeltelijke kooien afwijzen.

Je kunt de kooien van het karakterlichaam aanpassen voor gelaagde accessoires om nauwkeurig te vervormen naar de verwachte oppervlakken van het karakter met behulp van Automatische Skinning Overdracht. Bijvoorbeeld, auto-skinning kan ervoor zorgen dat gelaagde accessoires vervormen op basis van een onjuiste lichaamsdeel omdat het overdrachtsproces is gebaseerd op de dichtstbijzijnde afstand tussen de accessoire en zijn binnenste kooi.

Om dit te demonstreren, is de volgende baardaccessoire gemodelleerd met behulp van een blokachtige volledige lichaam kooi. Dit zorgt ervoor dat de baard onjuist vervormt omdat delen van de baard dichter bij de bovenborst van de karakterkooi liggen in plaats van bij de kin:

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Full-Body-Cage.png)

Om te voorkomen dat een gelaagde accessoire skinninggegevens gebruikt van een ongewenst gebied van de geometrie van het karakter, kun je je activa modelleren op een andere karaktermannequin kooi. Bijvoorbeeld, een blokachtige karakter zal moeite hebben met een baard die naar de torso is geskinnd, maar een karakter met een echte nek, zoals een humanoïde, zal dit probleem niet hebben.

Alternatief kun je delen van de buitenste kooi verwijderen waar de gelaagde accessoire niet aan geskinnd moet worden. Dit is geen geldige workflow voor activa die bedoeld zijn voor de Marketplace , maar je kunt dit gebruiken voor activa in de game. Bijvoorbeeld, de volgende afbeelding toont hoe de buitenste kooi is aangepast zodat deze alleen de hoofdgeometrie bevat. Met deze verbetering aan de buitenste kooi, wanneer je automatisch skinninggegevens overdraagt, worden de baard en de gedeeltelijke kooi nu correct geskinnd alleen van de hoofdgeometrie.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Head-Cage-Only.png)

Het is belangrijk op te merken dat je ook het vervormingsprobleem van het vorige voorbeeld zou kunnen oplossen door een andere kooi helemaal te gebruiken. Bijvoorbeeld, als je een humanoïde kooi gebruikt met meer ruimte tussen de borst en de kin, is de baard dichter bij het hoofd in plaats van dicht bij de borst of nek, zodat de Automatische Skinning Overdracht geen skinninggegevens uit die gebieden overdraagt.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Beard-Humanoid-Cage.jpg)

Door verschillende gebieden van de kooi van het karakter aan te passen, kun je ervoor zorgen dat je gelaagde accessoires en gezichtsaccessoires vervormen in relatie tot het juiste gebied van het lichaam of hoofd, zoals het aanpassen van de armen van het karaktermodel zodat jurken zich niet onjuist aan hen hechten terwijl een karakter rent, of het aanpassen van broeken die zich onjuist aan voeten toewijzen.

Om dit te demonstreren, bekijk hoe de kraag van de volgende jas onjuist beweegt met het hoofd terwijl de gelaagde accessoire vervormt in het kraaggebied, dat het dichtst bij het hoofd van de kooi ligt. Om dit op te lossen, kun je het hoofdgedeelte van de kooi verwijderen zodat de jas zich helemaal niet onjuist vervormt in relatie tot het hoofd. In plaats daarvan zal het vervormen in relatie tot het schoudergebied, wat veel geschikter is voor dit kledingstuk.

  ![](https://prod.docsiteassets.roblox.com/assets/avatar/dynamic-heads/creating-face-accessories/Jacket-Cage-Comparison.jpg)

Tijdens het proces van activa maken is het belangrijk om te verifiëren welke skinningoplossing het beste werkt voor jouw ontwerp door je individuele activa op meerdere modellen en animaties te testen. Je kunt altijd je activa handmatig skinnen en later kiezen om de Automatische Skinning Overdracht te gebruiken.

### [Verschillende accessoirecategorieën](#verschillende-accessoirecategorieën)[](#verschillende-accessoirecategorieën)

Automatische Skinning Overdracht werkt mogelijk niet goed voor bepaalde accessoirecategorieën, zoals hoed- en brillentypes. Bijvoorbeeld, hoed- of brillenaccessoires kunnen vervorming introduceren in gebieden die normaal gesproken rigide zouden moeten zijn. Over het algemeen moeten die accessoires rigide blijven, en je zou geen skinninggegevens aan hen moeten associëren.

Voor een samenvatting van de voorgestelde [WrapLayer.AutoSkin](/docs/nl-nl/reference/engine/classes/WrapLayer#AutoSkin)  parameters voor verschillende accessoirecategorieën, bekijk de volgende tabel:

| Accessoirecategorie | | Aangeraden parameter |
| --- | --- |
| Baard | | EnabledOverride |
| Wenkbrauw | | EnabledOverride |
| Wimper | | EnabledOverride |
| Haar | | Disabled |
| Hoed | | Disabled |
| Bril | | Disabled |
| Shirt | | EnabledOverride  of EnabledPreserve |
| Broek | | EnabledOverride  of EnabledPreserve |
| Schoenen | | EnabledOverride  of EnabledPreserve |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
