<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/rig-a-humanoid-model -->

Rig een humanoïde model | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Animatie
6. /
7. In Blender

# Rig een humanoïde model

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een R15 humanoïde karaktermodel, zoals die welke de gebruikersavatar-characters vormen, bestaat uit 15 individuele mesh-objecten. Net als bij het riggen van een eenvoudige mesh, kun je een groep meshes binden of koppelen aan een interne rig. Modellen die uit meerdere meshes bestaan, vereisen extra stappen om te riggen in een externe modelleringstool zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) .

Deze geavanceerde gids behandelt het proces van het riggen van een humanoïde model in Blender met behulp van een meegeleverde sjabloon en humanoïde model. Deze riggingstap is vereist voordat je [de humanoïde model skinning](/docs/nl-nl/art/modeling/skin-a-humanoid-model)  uitvoert. Je moet bekend zijn met [het riggen van een basis model](/docs/nl-nl/art/modeling/rig-a-simple-mesh)  voordat je verdergaat.

Om een humanoïde model in Blender te riggen:

-

[Importeer een karaktermodel](#importeer-model)  in een sjabloonbestand om eenvoudig toegang te krijgen tot een vooraf gemaakte [standaard R15 rig](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs) .

-

[Maak, schaal en positioneer botten](#stel-botten-en-armature-in)  symmetrisch voor een humanoïde karakter.

-

[Koppel](#koppel-armature)  meerdere meshes aan een enkele armature om de skelet-rig te binden.

-

[Wijs volledige invloed toe](#wijs-meshes-toe-aan-botten)  aan elk mesh-object en bot door invloeden toe te wijzen.

Deze gids maakt gebruik van een downloadbaar [Rig and Attachment Template Blender Project](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/Rig_and_Attachments_Templates.zip) , een referentie [Lola Character model](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/lola-base-model.fbx) , en [Blender versie 3.0](https://www.blender.org/download/releases/3-0/) . Als je een andere versie van Blender gebruikt, kunnen er kleine verschillen zijn in de gebruikersinterface en instellingen.

## [Stel Blender in](#stel-blender-in)[](#stel-blender-in)

Om te beginnen met het maken van een humanoïde rigged mesh, stel je eerst het volgende in je Blender-project in:

-

[Importeer](#importeer-model)  het Lola karaktermodel in het Mannequin Template Blender-project.

-

Stel je [Viewport-visualisaties](#viewport-visualisaties)  in om het riggen te optimaliseren.

### [Importeer model](#importeer-model)[](#importeer-model)

Bij het riggen van een model, zorg ervoor dat het karaktermodel dat je gebruikt voldoet aan de [Avatar karakter specificaties](/docs/nl-nl/avatar/character-bodies/specifications)  van Studio. Voor deze gids, importeer een [Lola referentiemodel](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/lola-base-model.fbx)  in het mannequin-sjabloonproject.

Om je model te importeren:

1.

Navigeer in Blender naar Bestand  > Openen  en selecteer Rig_and_Attachments_Template.blend .

2.

Navigeer naar Bestand  > Importeren  > FBX (.fbx)  en importeer het referentie Lola modelbestand.

3.

Indien nodig, schaal het model om ruwweg overeen te komen met de schaal van de armature-bonestructuur. Je kunt alle mesh-geometrieën in de Outliner selecteren en G  indrukken om te verplaatsen en S  om de mesh-objecten te schalen door je muis te slepen.

### [Viewport-visualisaties](#viewport-visualisaties)[](#viewport-visualisaties)

Voor betere visualisatie en toegang tot je botobjecten, stel je in dat je botobjecten altijd voor de Viewport worden weergegeven.

Om de botvisualisatie in te stellen:

1.

Klik in de Viewport  op een van de botten in je armature.

2.

In het Eigenschappen-editor  paneel, selecteer je het tabblad Objectgegevens .

3.

Vouw Viewport-weergave  uit, navigeer naar de Toon  eigenschap en schakel Voor  in.

Op elk moment tijdens het skinning-proces kun je ook een van de verschillende materiaalvoorvertoningsopties in de rechterbovenhoek van je 3D Viewport inschakelen om de visualisatie van je karaktermodel te veranderen, zoals het inschakelen van röntgen- of textuurweergave.

## [Stel botten en armature in](#stel-botten-en-armature-in)[](#stel-botten-en-armature-in)

In deze gids stel je X-Axis Mirroring in om symmetrische wijzigingen aan de linker- en rechterbotten aan te brengen voordat je de botten opnieuw positioneert naar het geïmporteerde model. Probeer symmetrie te behouden wanneer mogelijk bij het riggen van een model.

Als je botten wijzigt of een nieuwe botstructuur maakt, is het belangrijk om ervoor te zorgen dat deze voldoet aan de gestandaardiseerde bot-hiërarchie en naamgevingsconventies voor een [standaard](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  of [geavanceerde](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  R15 rigging armature voor avatar karaktermodellen.

### [Schakel x-as spiegeling in](#schakel-x-as-spiegeling-in)[](#schakel-x-as-spiegeling-in)

De X-Axis Mirror-instelling stelt je in staat om symmetrie te behouden met je linker- en rechterbotten door wijzigingen in hun posities te spiegelen. Om problemen met poseren en animeren te verminderen, is het belangrijk om symmetrie met je botstructuur te behouden wanneer mogelijk.

Om X-Axis Mirror in te stellen:

1.

Selecteer in Objectmodus  je armature  door op een bot te klikken.

2.

Schakel over naar Bewerkmodus  (Tab ).

3.

In de rechterzijbalk van de Viewport, vouw het gereedschapspaneel uit en schakel X-Axis Mirror  in.

### [Positioneer botten](#positioneer-botten)[](#positioneer-botten)

Met het model dat aan het project is toegevoegd, kun je de botten die in de sjabloon zijn gegeven opnieuw positioneren om overeen te komen met de karakterstructuur. In de meeste gevallen moet elk bot in het midden van hun overeenkomstige mesh-objecten worden gepositioneerd, zoals de Head-bot die gecentreerd is binnen het Head_Geo mesh-object.

De positionering van botten kan verschillen op basis van het gebruik en moet mogelijk opnieuw worden bekeken na het gewicht schilderen en testen als een bepaalde pose of animatie niet werkt zoals bedoeld.

Om je individuele botten te positioneren:

1.

Klik in Objectmodus op de bot  die je wilt verplaatsen om deze te markeren.

2.

Schakel over naar Bewerkmodus .

3.

Klik op de punt  van de bot zodat de punt gemarkeerd is en druk op G . De bovenkant van de bot beweegt met je cursor.

4.

Trek deze bot om uit te lijnen met het binnenste midden van het model en klik vervolgens om de positie van de bot in te stellen.

5.

Klik en houd de scrollwiel van je muis ingedrukt of gebruik een van de verschillende perspectiefweergaven om te verifiëren dat de bot zich binnen het mesh-object bevindt.

### [Koppel armature](#koppel-armature)[](#koppel-armature)

Nadat je de botstructuur hebt gepositioneerd, moet je de botarmature aan het model koppelen. Je moet alle 15 mesh-objecten aan één armature koppelen.

Voor dit voorbeeld zijn de mesh-objecten aan de armature gekoppeld met lege groepen om het proces van het toewijzen van vertexgroepen en gewicht schilderen in de volgende [Skin een humanoïde model](/docs/nl-nl/art/modeling/skin-a-humanoid-model)  gids te illustreren.

Om het model aan de armature te koppelen:

1.

Schakel over naar Objectmodus .

2.

Filter je mesh-objecten in de Outliner door "geo"  in de zoekbalk te typen.

3.

Selecteer alle mesh-objecten in de Outliner door Shift  ingedrukt te houden en op het eerste en laatste mesh-object te klikken.

4.

Met de gemarkeerde meshes, houd Shift  ingedrukt en klik op het Armature-object in de Viewport of Outliner.

5.

Klik met de rechtermuisknop in de Viewport en selecteer Ouder  > Met lege groepen .

## [Wijs meshes toe aan botten](#wijs-meshes-toe-aan-botten)[](#wijs-meshes-toe-aan-botten)

Nu je je armature aan het mesh-object hebt verbonden, kun je de vertices van je individuele ledematen volledig beïnvloeden door één overeenkomstig bot. Nadat dit proces is voltooid, is het model klaar voor skinning. Zie [Skin een humanoïde model](/docs/nl-nl/art/modeling/skin-a-humanoid-model)  voor instructies over het toepassen van meerdere botinvloeden op een mesh.

De Root  en HumanoidRootNode  ouderbotten in een humanoïde rig mogen geen invloeden toegewezen krijgen. Toegevoegde invloeden worden verwijderd bij het importeren in Studio.

Om volledige invloed toe te wijzen aan het hoofdmesh:

1.

Klik in Objectmodus  op het hoofdmesh-object  om het te markeren.

2.

Schakel over naar Bewerkmodus .

3.

Selecteer alle vertices van je mesh-object door A  in te drukken.

4.

Nadat alle hoofdvertices zijn gemarkeerd, navigeer je naar het Objecteigenschappen  paneel aan de rechterkant van het scherm.

5.

In de sectie Vertexgroep  van het paneel, selecteer je de naam van de bot waaraan je de Head-geometrie wilt toewijzen en klik je op Toewijzen .

Je kunt snel door al je mesh-objecten in deze modus itereren door het volgende mesh-object in de Outliner te selecteren en het aan de juiste Vertexgroep toe te wijzen. Voor deze gids, wijs al je karakter's mesh-objecten toe aan hun overeenkomstige bot .

Om snel vertexgroepen toe te wijzen aan de rest van de lichaamsmeshes:

1.

Klik in het Outliner  paneel op de stip naast het object dat je wilt bewerken. De stip schakelt over naar het actieve bewerkingsicoon wanneer je erop drukt.

2.

Als de vertices niet zijn gemarkeerd, druk dan op A  om alle vertices te selecteren.

3.

In het Objecteigenschappen  paneel > sectie Vertexgroepen , selecteer de juiste vertexgroep en klik op Toewijzen . Je kunt de zoekbalk gebruiken om de specifieke naam van de vertexgroep te vinden.

## [Test](#test)[](#test)

Je kunt botten en hun toegewezen mesh-objecten testen en poseren in de Pose-modus. Het is belangrijk om je model te testen na het toepassen of bewerken van invloeden.

Om naar de Pose-modus te navigeren en je poses te testen:

1.

Selecteer in Objectmodus  een deel van je model.

2.

Klik op de modus dropdown en schakel over naar Pose -modus.

3.

Houd Shift  ingedrukt en klik op de bot die je wilt testen om deze te markeren, druk vervolgens op R  om de rotatie te testen.

4.

Druk op Alt A  (⌥ A ) om de huidige bot te deselecteren, selecteer vervolgens opnieuw en test een andere bot.

Om de rotatie van een geselecteerde bot naar neutraal te resetten, druk op Alt + R . Terwijl je roteert, kun je ook het scrollwiel van je muis indrukken om de assen van je rotatie te veranderen.

In deze fase, als al je mesh-objecten worden beïnvloed door hun overeenkomstige botten, kun je dit rigged model [exporteren](/docs/nl-nl/art/modeling/export-requirements)  als een .fbx  voor gebruik in Studio of doorgaan naar de volgende fase van [Skin een humanoïde model](/docs/nl-nl/art/modeling/skin-a-humanoid-model) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
