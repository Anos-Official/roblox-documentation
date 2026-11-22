<!-- Source: https://create.roblox.com/docs/nl-nl/characters/adaptive-animation -->

Adaptieve Animatie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Personages](/docs/nl-nl/characters)

# Adaptieve Animatie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox's Adaptieve Animatie  systeem maakt het mogelijk om animaties naadloos af te spelen tussen aangepaste karakters met unieke lichaamstypes, rigs en proporties. Deze functie maakt gebruik van [HumanoidRigDescription](/docs/nl-nl/reference/engine/classes/HumanoidRigDescription)  en [DigitsRigDescription](/docs/nl-nl/reference/engine/classes/DigitsRigDescription)  objecten binnen je karaktermodel, zodat je de interne gewrichten van je aangepaste karakter kunt aanpassen, wijzigen en in kaart brengen voor universele animatieondersteuning.

Na het importeren van een karakterrig, kun je verschillende Studio-tools gebruiken om je gewrichten opnieuw in te delen en een basis T-pose referentie in te stellen om animaties beter te ondersteunen. Nadat je je rig hebt geconfigureerd, kan je aangepaste karakter elke R15 animatie afspelen, of elke animatie die is gepubliceerd vanuit een karakter met [HumanoidRigDescription](/docs/nl-nl/reference/engine/classes/HumanoidRigDescription)  en [DigitsRigDescription](/docs/nl-nl/reference/engine/classes/DigitsRigDescription)  objecten.

![](https://prod.docsiteassets.roblox.com/assets/avatar/adaptive-animation/Import-Custom-Humanoid.png) Importeer naadloos aangepaste karakters in Studio als een Custom Humanoid  rig type.

![](https://prod.docsiteassets.roblox.com/assets/avatar/adaptive-animation/Assign-Joints-A.png) Wijzig en pas de gegenereerde [HumanoidRigDescription](/docs/nl-nl/reference/engine/classes/HumanoidRigDescription)  aan om compatibiliteit met universele animaties te waarborgen.

## [Wijzig aangepaste karakterrig](#wijzig-aangepaste-karakterrig)[](#wijzig-aangepaste-karakterrig)

Bij het importeren van een rig als een Custom Humanoid , probeert Studio automatisch de [HumanoidRigDescription](/docs/nl-nl/reference/engine/classes/HumanoidRigDescription)  en [DigitsRigDescription](/docs/nl-nl/reference/engine/classes/DigitsRigDescription)  objecten van het model te configureren. Wanneer nodig, kun je de gewrichttoewijzing en T-pose tools gebruiken om de automatische wijzigingen te verfijnen of aan te passen.

Je kunt meedoen met je eigen aangepaste karakter of het [referentie karakter](https://prod.docsiteassets.roblox.com/assets/art/reference-files/Snow.fbx)  dat in deze gids wordt getoond. Het referentie karakter is een gemodificeerde versie van Blender Studio's [Snow](https://studio.blender.org/characters/snow/v4/)  karakter gecombineerd met Blender's [basis mesh](https://www.blender.org/download/demo-files/)  assets.

### [Importeer model](#importeer-model)[](#importeer-model)

Gebruik de 3D Importer om een karaktermodel te importeren, en gebruik vervolgens het Adaptieve Animatie systeem om [HumanoidRigDescription](/docs/nl-nl/reference/engine/classes/HumanoidRigDescription)  en [DigitsRigDescription](/docs/nl-nl/reference/engine/classes/DigitsRigDescription)  objecten toe te voegen:

1.

Klik op de Home  tab en klik op de Import  knop om de 3D Importer te openen. Een bestandsbrowser opent.

2.

Selecteer het .fbx  of .gltf  bestand van je gerigged karakter. De 3D Importer laadt een voorbeeld van het karaktermodel.

3.

Stel in de sectie Rig General  Rig Type  in op Custom .

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/adaptive-animation/Import-Custom-Humanoid.png)

1.

Selecteer de Import  knop. Het karakter wordt weergegeven in je werkruimte als een [Model](/docs/nl-nl/reference/engine/classes/Model) .

2.

Klik in de Avatar  tab op de Adaptieve Animatie  knop. Het Remap Rig  paneel wordt weergegeven.

3.

Klik in het Remap Rig  paneel op de Create  knop. Het Adaptieve Animatie systeem genereert een [HumanoidRigDescription](/docs/nl-nl/reference/engine/classes/HumanoidRigDescription)  object en een [DigitsRigDescription](/docs/nl-nl/reference/engine/classes/DigitsRigDescription)  voor elke hand.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/adaptive-animation/Rig-DataModel.png)

### [Wijs gewrichten toe](#wijs-gewrichten-toe)[](#wijs-gewrichten-toe)

Het Adaptieve Animatie systeem vereist dat ten minste 15 van de gewrichten van je karakter worden toegewezen aan Roblox's [gestandaardiseerde 15 gewrichten skelet](/docs/nl-nl/avatar/character-bodies/specifications) . Terwijl het automatische importproces probeert deze toewijzing automatisch te maken, kun je gewrichten verifiëren en opnieuw toewijzen met behulp van de gewrichttoewijzingstool.

Wanneer je de [HumanoidRigDescription](/docs/nl-nl/reference/engine/classes/HumanoidRigDescription)  of [DigitsRigDescription](/docs/nl-nl/reference/engine/classes/DigitsRigDescription)  objecten van je model selecteert, wordt de visuele picker  van de gewrichttoewijzingstool weergegeven in de rechterbovenhoek van het 3D viewport met een weergave van het standaard Roblox skelet. Om gewrichten toe te wijzen, kun je ofwel op de gewrichten in het 3D viewport of de visuele picker klikken, en vervolgens op het overeenkomstige gewricht in de andere weergave klikken. Wanneer een gewricht is toegewezen, verandert het gewrichtsicoon in oranje  in zowel het 3D viewport als de visuele picker.

Wanneer je de gewrichttoewijzingstool gebruikt, toont de visuele picker:

-

Alle 15 standaard gewrichttoewijzingen die je moet toewijzen aan de rig van je karakter als een ingevulde grijze cirkel.

-

Alle extra gewrichttoewijzingen die je niet verplicht hoeft toe te wijzen aan de rig van je karakter als lege cirkelomtrekken. Als je rig compatibel is met deze extra gewrichten, kun je ze dienovereenkomstig toewijzen om de animatiekwaliteit te verbeteren.

![](https://prod.docsiteassets.roblox.com/assets/avatar/adaptive-animation/Assign-Joints-B.png) Gewrichten die niet zijn toegewezen verschijnen als een grijze indicator op zowel de visuele picker als de 3D viewport mannelijken.

![](https://prod.docsiteassets.roblox.com/assets/avatar/adaptive-animation/Assign-Joints-A.png) Wanneer toegewezen, veranderen gewrichtindicatoren in oranje in zowel de visuele picker als de 3D viewport.

Om toegang te krijgen tot en de gewrichttoewijzingstool te gebruiken:

1.

Breid in het Explorer  venster het model uit dat je zojuist hebt geïmporteerd en selecteer het kind [HumanoidRigDescription](/docs/nl-nl/reference/engine/classes/HumanoidRigDescription) . De Adaptieve Animatie werkbalk wordt weergegeven met de gewrichttoewijzingstool actief, en de mesh-objecten van je karakter worden semi-translucent zodat je de interne gewrichten kunt bekijken.

2.

Klik in het 3D viewport op een gewricht binnen het lichaam van het karakter, en selecteer vervolgens in de visuele picker het overeenkomstige gewricht. De gewrichtindicator verandert in oranje om aan te geven dat het is toegewezen.

3.

Als de rig van je karakter optionele gewrichten in de handen bevat,

1.

Navigeer terug naar het Explorer  venster, en selecteer een van de kind [DigitsRigDescription](/docs/nl-nl/reference/engine/classes/DigitsRigDescription)  objecten van je model. De visuele picker wordt bijgewerkt om een weergave van de linker of rechterhand van je karakter weer te geven.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/adaptive-animation/Hand-Rig-View.png)

2.

Wijs elk optioneel gewricht toe door op een gewricht op de hand te klikken, en selecteer vervolgens het overeenkomstige gewricht in de visuele picker.

3.

Herhaal dit proces voor het andere kind [DigitsRigDescription](/docs/nl-nl/reference/engine/classes/DigitsRigDescription)  object van het karakter.

### [Maak t-pose](#maak-t-pose)[](#maak-t-pose)

Om universele animatieondersteuning te waarborgen, is het belangrijk om een standaard T-pose configuratie in te stellen als een basisreferentie voor je karakter. De Adaptieve Animatie werkbalk biedt een T-pose modus met tools om je karakter automatisch in te stellen om aan de T-pose vereisten te voldoen, of om de positie en rotatie van je gewrichten aan te passen voor de beste animatieresultaten.

![](https://prod.docsiteassets.roblox.com/assets/avatar/adaptive-animation/Tpose-Rotation-A.png)

![](https://prod.docsiteassets.roblox.com/assets/avatar/adaptive-animation/Tpose-Rotation-B.png)

 Om gewrichten te verplaatsen, selecteer het gewricht terwijl de T-pose tools actief zijn, en gebruik vervolgens de multi-transform tool om een positionele of roterende wijziging toe te passen.

Om een T-pose te creëren met behulp van de T-pose modus:

1.

Selecteer in de Adaptieve Animatie werkbalk de T-pose modus  knop om over te schakelen naar de T-pose modus.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/adaptive-animation/T-pose-mode.png)

2.

Selecteer de Enforce T-pose  knop om je karakter automatisch in te stellen voor T-pose vereisten.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/adaptive-animation/Enforce-tpose.png)

3.

Als je aanpassingen aan de T-pose van je karakter moet maken,

1.

Als je zowel de linker als rechter ledematen tegelijkertijd wilt roteren, schakel dan het symmetrie-icoon voor links en rechts in.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/adaptive-animation/Symmetry-Tool.png)

2.

Selecteer een van de bovenarm gewrichten nabij de schouder. Het gewricht wordt blauw om aan te geven dat het is geselecteerd.

3.

Gebruik de Rotate  tool om het gewricht in een T-pose te draaien.

4.

Indien nodig, positioneer de benen en andere delen van het lichaam totdat je rig in een T-pose staat.

4.

Om de T-pose van je rig te testen,

1.

Navigeer naar de Adaptieve Animatie werkbalk, en gebruik de dropdown om een animatie te selecteren.

2.

Druk op het afspeelpictogram. Als een animatie niet correct animeren, moet je mogelijk de rig van je karakter opnieuw in kaart brengen of opnieuw poseren.

Zodra de rig van je karakter is geconfigureerd en opgeslagen, kan dat karakter [afspelen ondersteunen](/docs/nl-nl/../animation)  van elke R15 animatie of animaties gepubliceerd vanuit een aangepast karakter met een [HumanoidRigDescription](/docs/nl-nl/reference/engine/classes/HumanoidRigDescription) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
