<!-- Source: https://create.roblox.com/docs/nl-nl/avatar-setup/auto-setup-requirements -->

Specificaties voor Avatar Setup | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Avatar instellen

# Specificaties voor Avatar Setup

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[Avatar Setup](/docs/nl-nl/avatar-setup)  ondersteunt de automatische conversie van basis aangepaste modellen naar Roblox-klaar lichaamsmodellen, starre accessoires en gelaagde accessoires. Door je modellen samen te [bundelen](#meerdere-assets-bundelen) , kun je automatisch meerdere aangepaste modellen instellen als avatar-items voor gebruik in de game of voor upload naar de Marketplace.

## [Karakterlichamen](#karakterlichamen)[](#karakterlichamen)

Avatar Setup kan proberen een 3D-model om te zetten in een Roblox-klaar karakterlichaam. Dit is een van de meest voorkomende gebruikssituaties voor Avatar Setup en kan je helpen tijd te besparen door het riggen, cagen en andere configuraties te automatiseren die nodig zijn om een Roblox-klaar avatar-karakter te maken dat je kunt uploaden naar de Marketplace.

Avatar-assets zoals [starre accessoires](#starre-accessoires)  en [gelaagde accessoires](#gelaagde-accessoires)  kunnen verwerking met een basislichaam vereisen. Avatar Setup kan dit basislichaam gebruiken als een mannequin, waardoor nauwkeurigere bevestigingspunten en andere componenten worden gecreëerd om een betere pasvorm te garanderen. Als je starre of gelaagde accessoires converteert, moet je ze [bundelen](#meerdere-assets-bundelen)  met een basislichaam voor de pasvorm.

### [Ondersteunde invoer](#ondersteunde-invoer)[](#ondersteunde-invoer)

Avatar Setup detecteert de volgende gedeeltelijke avatarlichaam invoer:

| ** Referentie-afbeelding** | | ** Ondersteuning van Avatar Setup** |
| --- | --- |
| ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Partial-Inputs-None-Rigged.png) | |

Een enkele of meerdere mesh-lichaam met geen rigging .

 De meest voorkomende invoer is een enkel mesh-object dat geen rigginggegevens of andere componenten bevat. Het invoer karakterlichaam moet voldoen aan de [modelvereisten](#karakterlichamen)  van Avatar Setup.
 In dit geval creëert Avatar Setup de rest van de avatarcomponenten automatisch.

 |
| ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Partial-Inputs-Body-Rigged.png) | |

Een enkele of meerdere mesh-lichaam met alleen lichaamsrigging .

 Als de geleverde meshes een compatibele [standaard](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  of [geavanceerde](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  R15 rigging armatuur bevatten, gebruikt Avatar Setup de geleverde rig en creëert een gezichtsrig en alle andere componenten.
 Het invoer karakterlichaam rig moet voldoen aan de [riggingconfiguratievereisten](/docs/nl-nl/avatar/character-bodies/specifications#rigging)  van Roblox, anders creëert Avatar Setup een gloednieuwe rig voor je.

 |
| ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Partial-Inputs-Head-Rigged.png)
 | |

Een meerdere mesh met alleen gezichtsrigging .

 Als je van plan bent je eigen aangepaste gezichtsrigging te gebruiken, stel dan de FaceRootJoint (en alle kindbotten) in als een kind van de [standaard](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  of [geavanceerde](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  rigging armatuur's hoofdjoint. Voor meer informatie, zie de optionele [rigvereisten](#rig-vereisten) .

 |
| ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Partial-Inputs-All-Rigged.png)
 | |

Een enkele mesh  lichaam met zowel lichaams- als gezichtsrigging .

 Als de rigging armatuur van het karakterlichaam, gezichtsrig en de juiste FACS-gegevens zijn inbegrepen, behoudt Avatar Setup die gegevens en genereert alleen de ontbrekende Roblox-specifieke componenten. Karakterlichamen die uit meerdere meshes bestaan, worden niet ondersteund voor deze invoer.
Voor meer informatie, zie de optionele [rigvereisten](#rig-vereisten) .

 |

### [Mesh-vereisten](#mesh-vereisten)[](#mesh-vereisten)

Om de beste resultaten te behalen bij het converteren van een model naar een Roblox-klaar avatar-karakterlichaam, is het belangrijk om je basismodel zo te configureren dat de tool de avatarcomponenten correct kan genereren.

Veel bestaande [downloadbare bronnen](/docs/nl-nl/avatar/resources)  voor avatar-karakterlichamen voldoen niet aan de onderstaande vereisten van Avatar Setup. Bestaande avatarreferenties moeten mogelijk worden aangepast om ervoor te zorgen dat het asset voldoet aan de modellen van Avatar Setup.

Zie de specifieke [karakterreferentiemodellen](/docs/nl-nl/avatar-setup#voer-avatar-setup-uit)  voor assets die zijn gemaakt voor de vereisten van Avatar Setup.

De volledige vereisten voor het invoer karakterlichaam model zijn als volgt:

1.

Enkele of meerdere mesh  — In de meeste gevallen accepteert Avatar Setup karakterlichamen die uit 1 of meer meshes bestaan. Als je karakterlichaam meerdere meshes bevat, combineert de tool automatisch alle geselecteerde meshes tot een enkele mesh, en reduceert vervolgens de gecombineerde delen tot de juiste [lichaamsdeel](/docs/nl-nl/avatar/character-bodies/specifications#lichaamsdelen)  structuur.

Wanneer je de standaard 15 lichaamsdeel meshes levert die voldoen aan de vereiste naamgevingsconventies voor lichaamsdelen, probeert Avatar Setup gewrichten te plaatsen volgens de door de gebruiker partitioneerde lichaamsdelen.

2.

5 verschillende hoofdcomponenten  — Of je nu een enkel of multi-mesh karakterlichaam model gebruikt, de volgende hoofdcomponenten zijn vereist:

-

2 ogen  — Hoofden moeten 2 verbonden oogzakken bevatten met halve bol ogen die geen enkele vertex delen met de hoofdcomponent.

-

3 monddelen  — Hoofden moeten een verbonden mondzak bevatten die de bovenste tanden , onderste tanden  en tong  herbergt. Elk van deze monddelen moet enkel verbonden zijn en geen enkele vertex met elkaar of met de hoofdmesh delen.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Mouthparts-1.png)

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Mouthparts-2.png)

3.

Hoofdgeometrie mag geen vertices delen  — Ogen, tanden en tong moeten deel uitmaken van het model zonder vertices met de lichaam mesh te delen.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Mouthparts-3.png)

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Mouthparts-4.png)

4.

Binnen de driehoekbudget  — De totale resolutie van de karakterlichaam mesh moet binnen 10.742 driehoeken liggen. Gebruik de volgende richtlijnen om ervoor te zorgen dat elk deel de verwachte polycounts niet overschrijdt:

| Groepering van lichaamsdelen | | Maximale driehoeken | | Maximale quads |
| Hoofd | | 4000 | | 2000 |
| Armen | | 1248 per arm | | 624 per arm |
| Beneden | | 1248 per been | | 624 per arm |
| Torso | | 1750 | | 875 |
| Totaal:  | | 10.742 | | 5495 |

Avatar Setup segmenteert en voegt [caps](/docs/nl-nl/avatar/character-bodies/specifications#lichaamsdelen)  toe aan de ledematen van het karakter, wat kan bijdragen aan je totale polycount. Als je karakterlichaam model dicht bij de polycount-limiet ligt, kan de extra geometrie leiden tot validatiefouten.

5.

Humanoïde vorm  — Het karakterlichaam moet een algemene humanoïde vorm volgen, met twee armen, twee benen, een torso en een hoofd.

6.

A-pose of T-Pose  — Het karakterlichaam moet een rechtopstaande A-pose of T-Pose vormen.

-

Karakterlichamen met I-pose kunnen lagere kwaliteit resultaten opleveren.

-

Zorg ervoor dat geen ledematen elkaar van de voorkant verbergen of overlappen.

7.

Negatieve Z-as  — De voorkant van het karakterlichaam moet naar de negatieve Z-as wijzen.

8.

Symmetrisch  — Asymmetrische karakterlichamen kunnen per geval werken. Positioneer het midden van het lichaam met de Y-as om de nauwkeurigheid van het resultaat te verbeteren. Als je asymmetrische model opzetproblemen ondervindt, probeer dan een meer symmetrische versie te gebruiken.

9.

Waterdicht  — Zorg ervoor dat het model waterdicht is in alle gebieden, met uitzondering van de ogen en mond. Waterdicht betekent dat er geen gaten in de mesh zijn en dat er geen achterkant zichtbaar is.

10.

Geen accessoires  — Voeg geen accessoires toe, inclusief gezichtaccessoires, zoals haar, wenkbrauwen, baarden en wimpers.

11.

Duidelijk nekgebied  — Houd de nek duidelijk en niet samengevoegd met de schouders of bovenlichaam.

12.

Bevat textuur  — Modellen moeten een of meer textuurkaarten bevatten. Als het invoer karakterlichaam meerdere texturen bevat, bakt de tool de texturen naar een enkele kaart. Dit geldt voor [PBR-texturen](/docs/nl-nl/art/modeling/surface-appearance)  waarbij de vier texturen zijn gebakken — één voor elke albedo, normaal, metalness en ruwheid.

13.

Voldoet aan de Gemeenschapsnormen en Marketplace-beleid  — Het model moet voldoen aan de [Gemeenschapsnormen](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  en [Marketplace-beleid](/docs/nl-nl/marketplace/marketplace-policy)  van Roblox.

### [Rig-vereisten](#rig-vereisten)[](#rig-vereisten)

Je hoeft geen  aangepaste rigging armatuur bij je karakterlichaam op te nemen om Avatar Setup te gebruiken. Als je de standaard 15 [lichaamsdeel](/docs/nl-nl/avatar/character-bodies/specifications#lichaamsdelen)  meshes levert die voldoen aan de vereiste naamgevingsconventies voor lichaamsdelen zonder een rig , probeert Avatar Setup gewrichten te genereren volgens de door de gebruiker partitioneerde lichaamsdelen.

Om ervoor te zorgen dat Avatar Setup je eigen aangepaste lichaamsrig  gebruikt in plaats van een nieuwe voor je te genereren:

-

Zorg ervoor dat je botten (Blender) of gewrichten (Maya) voldoen aan de [vereisten voor rigging armaturen](/docs/nl-nl/avatar/character-bodies/specifications#rigging)  van Roblox, en controleer de naamgevingsconventies en hiërarchie.

-

Lichaamsrigs mogen geen extra botten bevatten buiten de [standaard](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  of [geavanceerde](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  R15 rigging armatuur specificaties, en gezichtsrigs (geen botlimiet) moeten correct zijn gekoppeld aan een RootFaceJoint .

Om ervoor te zorgen dat Avatar Setup je eigen aangepaste gezichtsrig met FACS-gegevens  gebruikt:

-

Een [standaard](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  of [geavanceerde](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  R15 rigging armatuur is vereist bij het indienen van aangepaste gezichtsrigs en gezichtsanimatiegegevens. Bekijk de [ondersteunde karakterlichaam invoer](#karakterlichamen)  om ervoor te zorgen dat je een ondersteunde lichaamsinvoer en gezichtsrig-combinatie indient.

-

De gezichtsrig moet een RootFaceJoint  bot bevatten (meestal [gemapt](/docs/nl-nl/art/characters/facial-animation/create-basic-heads#map-elke-pose)  als DynamicHead ) waarvan de ouder de Head  joint van de standaard rigging armatuur is.

-

Alle andere gezichtsanimatie gewrichten zijn afstammelingen van de RootFaceJoint , en geen directe kinderen van de Head  joint.

-

Animaties moeten worden geleverd voor de [17 vereiste poses](/docs/nl-nl/avatar/character-bodies/specifications#facial-animations) , minimaal.

-

Neutrale animatie moet worden gemapt naar frame 0 .

-

Aangezien het hoofd deel uitmaakt van de enkele mesh met het lichaam, moeten de gezichtsanimatiemappingen worden opgenomen met de enkele karakterlichaam mesh:

-

De mapping tussen animatieframes en gezichtsposes worden opgeslagen in de extra attributen / aangepaste eigenschappen van de geleverde enkele mesh.

-

De naam van de root face joint wordt opgeslagen in de extra attributen / aangepaste eigenschappen van de enkele mesh, waarbij RootFaceJoint  naar de overeenkomstige naam wordt gemapt (meestal DynamicHead ).

### [Voorbeelden van niet-ondersteunde lichamen](#voorbeelden-van-niet-ondersteunde-lichamen)[](#voorbeelden-van-niet-ondersteunde-lichamen)

De volgende zijn veelvoorkomende voorbeelden van lichamen die mogelijk niet de verwachte resultaten opleveren met Avatar Setup:

Voorbeelden van niet-ondersteunde modellen

|

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Assymetry.png) Extreme asymmetrie  — Als je problemen hebt met een asymmetrisch model, probeer dan een meer symmetrische versie te gebruiken en maak kleine aanpassingen.

 |
|

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/I-pose.png) I-pose  — Als je problemen ondervindt met je model in een I-pose, probeer dan opnieuw in te dienen met A-pose of T-pose.

 |
|

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Non-Contiguous.png) Niet-continue mesh  — de setup-tool verwacht dat de lichaam mesh volledig aaneengeschakeld is.

 |
|

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/No-Neck.png) Geen nek  — de setup-tool verwacht een nek die een hoofd met de torso verbindt.

 |
|

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Long-Neck.png) Onevenredige ledematen  — de setup-tool verwacht een meer realistisch humanoïde stijl karaktermodel.

 |
|

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Non-Proportional-Limbs.png) Onevenredige ledematen  — de setup-tool verwacht een meer realistisch humanoïde stijl karaktermodel.

 |

## [Starre accessoires](#starre-accessoires)[](#starre-accessoires)

Je moet je starre en gelaagde accessoiremodellen [bundelen](#meerdere-assets-bundelen)  met een basislichaam om Avatar Setup te kunnen gebruiken. Voor meer informatie, zie [ondersteunde invoer](#ondersteunde-invoer-1) .

Avatar Setup kan modellen omzetten in starre accessoires en hun schaaltype en bevestigingspuntvereisten configureren.

Om een mesh-model om te zetten in een starre accessoire:

1.

Pas het model aan op een basislichaam in Studio of je 3D-modelleringssoftware.

2.

[Bundel](#meerdere-assets-bundelen)  de assets samen in een enkele [Folder](/docs/nl-nl/reference/engine/classes/Folder) .

3.

Gebruik Avatar Setup  op je map met assets.

Tijdens dit proces kun je individuele meshes of modellen aanwijzen als starre accessoires, gelaagde accessoires of lichaamsdelen. Na conversie verschijnt er een prompt waarmee je het specifieke Asset Type  kunt selecteren.

Voor de beste resultaten, zorg ervoor dat je modellen voldoen aan de [geometriespecificaties voor starre accessoires](/docs/nl-nl/avatar/rigid-accessories/specifications#geometrie-en-budgetten)  van Roblox.

### [Ondersteunde invoer](#ondersteunde-invoer-1)[](#ondersteunde-invoer-1)

Starre accessoire meshes moeten worden gebundeld met een karakterlichaam zodat Avatar Setup correct kan configureren. Zie de volgende ondersteunde invoer voor starre accessoire meshes:

| Invoervoorwerp | | Avatar Setup genereert |
|
-

Folder  [bundel](#meerdere-assets-bundelen)  met:

-

[Model](/docs/nl-nl/reference/engine/classes/Model)  met volledig of gedeeltelijk geconfigureerd karakterlichaam

-

[Model](/docs/nl-nl/reference/engine/classes/Model)  met accessoire mesh-object (dit is het object dat wordt gemaakt bij het importeren van een aangepast 3D-object)

 | | [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  met gelaagde accessoire mesh, BodyPartScaleType , en bevestigingspunten |

## [Gelaagde accessoires](#gelaagde-accessoires)[](#gelaagde-accessoires)

Avatar Setup kan modellen omzetten in gelaagde accessoires en rigging- en caging-gegevens toevoegen die normaal gesproken handmatige configuratie in een aparte software vereisen.

Om een mesh-model om te zetten in een accessoire met Avatar Setup:

1.

Pas het model aan op een basis karakterlichaam in Studio of je 3D-modelleringssoftware.

2.

(Optioneel) Voor de beste resultaten, [bundel](#meerdere-assets-bundelen)  de assets samen in een enkele [Folder](/docs/nl-nl/reference/engine/classes/Folder) .

3.

Gebruik Avatar Setup  op je map met assets.

Tijdens dit proces kun je individuele meshes of modellen aanwijzen als starre accessoires, gelaagde accessoires of lichaamsdelen. Na conversie verschijnt er een prompt waarmee je het specifieke Asset Type  kunt selecteren.

Voor de beste resultaten, zorg ervoor dat je modellen voldoen aan de [geometriespecificaties voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications#geometrie-en-budgetten)  van Roblox.

### [Ondersteunde invoer](#ondersteunde-invoer-2)[](#ondersteunde-invoer-2)

Avatar Setup kan gelaagde accessoiremodellen configureren in een gelaagde [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  compleet met caging- en rigginggegevens. Hoewel Avatar Setup modellen kan configureren zonder een gebundeld lichaam, kun je betere resultaten vinden als je een basis karakterlichaam voor de setup opneemt.

| Invoervoorwerp | | Avatar Setup genereert |
| [Model](/docs/nl-nl/reference/engine/classes/Model)  met gelaagde accessoire mesh-object zonder extra componenten (dit is het object dat wordt gemaakt bij het importeren van een aangepast 3D-object)  | |
-

[Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  met gelaagde accessoire mesh en de volgende gegenereerde componenten:

-

Inner en outer cage-gegevens

-

Bevestigingspunten

Zonder een bijbehorend karakterlichaam asset, doet Avatar Setup een beste poging om cage-gegevens te genereren.

 |
|
-

Folder  [bundel](#meerdere-assets-bundelen)  met:

-

[Model](/docs/nl-nl/reference/engine/classes/Model)  met volledig of gedeeltelijk geconfigureerd karakterlichaam

-

[Model](/docs/nl-nl/reference/engine/classes/Model)  met accessoire mesh-object (dit is het object dat wordt gemaakt bij het importeren van een aangepast 3D-object)

 | |
-

[Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  met kledingmesh en de volgende gegenereerde componenten:

-

Inner en outer cage-gegevens

-

Bevestigingspunten

 |

## [Meerdere assets bundelen](#meerdere-assets-bundelen)[](#meerdere-assets-bundelen)

Avatar Setup kan meerdere starre of gelaagde accessoiremodellen verwerken met een enkel karakterlichaam model. Om meerdere modellen in de Avatar Setup  tool in te dienen, plaats je je modellen binnen een enkele map.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-setup/Folder-Hierarchy.png) Een Folder  met de verschillende Model  objecten die klaar zijn om door Avatar Setup te worden verwerkt tot een karakterlichaam, starre accessoire en gelaagde accessoire assets.

Om je objecten aan de map te koppelen:

1.

In het Explorer -venster, houd Shift  ingedrukt en selecteer de [Model](/docs/nl-nl/reference/engine/classes/Model)  objecten die je van plan bent te verwerken met Avatar Setup. Zorg ervoor dat je een [ondersteund basis karakterlichaam](#karakterlichamen)  selecteert als een van de [Model](/docs/nl-nl/reference/engine/classes/Model)  objecten.

2.

Klik met de rechtermuisknop en selecteer Groep als map .

3.

Selecteer de [Folder](/docs/nl-nl/reference/engine/classes/Folder)  en selecteer vervolgens de Avatar Setup  tool om te beginnen met verwerken.

Je moet je starre en gelaagde accessoiremodellen bundelen met een basis karakterlichaam om Avatar Setup te kunnen gebruiken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
