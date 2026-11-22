<!-- Source: https://create.roblox.com/docs/nl-nl/art/characters/creating/caging -->

Het omheinen van het hoofd van een karakter | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Het omheinen van het hoofd van een karakter

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Omheinen  is het proces van het bijwerken van de [omheining mesh component](/docs/nl-nl/avatar/character-bodies#cage-meshes)  van je avatarpersonage. Om ervoor te zorgen dat je personage correct laagbare accessoires kan dragen, moet je het standaard sjabloon omheining mesh object bijwerken om overeen te komen met de sculptuurwijzigingen die je hebt aangebracht aan je aangepaste personage.

Aangezien deze tutorial alleen modelleerwijzigingen op het hoofd toepast, zijn de omheiningsinstructies hieronder alleen van toepassing op het Head_OuterCage  object. Als je geometriewijzigingen aan andere delen van het personage aanbrengt, moet je ook die specifieke _OuterCage  objecten aanpassen om overeen te komen met je sculptuurwijzigingen.

Verwijder geen enkele vertex of vlak van de geleverde omheiningen. Destructieve wijziging van de omheiningen kan importproblemen veroorzaken en voorkomen dat het personagemodel kleding en cosmetica kan dragen.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Pre-Caging.png)  Standaard hoofd omheining mesh past niet meer over het gesculpte hoofd

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Post-Caging.png) Hoofd omheining mesh na aanpassing

Als de lichaamsvorm van je personage veel wijzigingen met verschillende lichaamsdelen omvat, kan het efficiënter zijn om het [Blender Cage Template](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Body_Cage_Templates.zip)  te gebruiken. Dit Blender-projectbestand bevat een helper full-body std_cage_deformable  mesh om automatisch vertexwijzigingen toe te passen op de individuele lichaamsdeelomheiningen tegelijk.

Om te beginnen met het omheinen van je personage:

1.

In het Layout  tabblad, verberg alles in de Outliner behalve de Head_OuterCage  en de Head_Geo  objecten.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Caging-Outer-Cage-Objects.png)

2.

Met Head_OuterCage  geselecteerd, ga naar Object Properties  > Viewport Display  en stel de Display As  in op Wire .

3.

Schakel over naar Edit  modus, schakel vervolgens X-Axis symmetry  en Topology Mirror  in om ervoor te zorgen dat je symmetrische vertexwijzigingen aanbrengt aan je omheining.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Caging-Symmetry-Settings.png)

4.

Gebruik de Grab  tool (G ), klik en pak delen van de omheining mesh en pas deze aan zodat ze strak over de goblin hoofd mesh passen. Houd het volgende in gedachten:

-

Verwijder nooit een van de omheining vertices.  Ontbrekende vertices kunnen fouten en problemen veroorzaken bij het dragen van kledingaccessoires.

-

Als je de basis van je hoofd omheining bewerkt, zorg er dan voor dat de basis van de Head  omheining uitgelijnd is met de bovenkant van de UpperTorso  omheining.

-

In verschillende Select-modus, houd Shift  ingedrukt en klik op meerdere vertices/randen/vlakken om de geometrie te selecteren en te bewerken.

-

Je kunt een strakke pasvorm verifiëren door vertices te pakken en ze in de Head_Geo  mesh te verplaatsen om te controleren waar de meshes elkaar kruisen en de omheining vertices te verplaatsen totdat de omheining mesh net over de hoofd mesh past.

-

Schakel de zichtbaarheid van je verschillende mesh objecten in en uit om de zichtbaarheid en toegang tot vertices te verbeteren.

5.

Nadat het draadframe strak over de hoofd mesh is gepast, stel je de Display As  weer in op Solid  en controleer en repareer eventuele intersecterende vertices.

Je eindproduct moet een omheining mesh bevatten die direct over de hoofd mesh zit zonder dat enige van de Head_Geo  geometrie door de solide secties van de omheining steekt.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Post-Caging.png)

Voor een vergelijkingsreferentie kun je [deze versie van het tutorialproject met voltooide omheining downloaden](https://prod.docsiteassets.roblox.com/assets/art/reference-files/checkpoint/3_Goblin-caged.blend) .

[Volgende](/docs/nl-nl/art/characters/creating/combine-head-geometry)[Vorige](/docs/nl-nl/art/characters/creating/texturing-pbr)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
