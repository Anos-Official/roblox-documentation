<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/rig-a-simple-mesh -->

Rig een eenvoudige mesh | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Animatie
6. /
7. In Blender

# Rig een eenvoudige mesh

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt een gerigde mesh  maken met een externe modelleringstool zoals [Blender](https://www.blender.org)  of [Maya](https://www.autodesk.com/products/maya/overview) . Je zou een model moeten riggen na het ontwerpen, maar vóór het [exporteren](/docs/nl-nl/art/modeling/export-requirements) .

Om een eenvoudig model in Blender te riggen:

-

[Stel Blender in](#stel-blender-in)  op de relatieve scène-eenheden van Studio voordat je een model importeert om te riggen.

-

[Maak en repositioneer botten](#maak-een-botstructuur)  binnen het mesh-object.

-

[Koppel de mesh aan de armature](#koppel-armature)  om de bottenarmature aan het mesh-object te binden.

-

[Wijs vertices toe aan specifieke botten](#wijs-vertices-toe-aan-botten)  om te definiëren welke delen van de mesh door welke botten worden aangestuurd.

-

[Test je gerigde mesh](#test)  om ervoor te zorgen dat de botten goed gepositioneerd zijn en invloed hebben binnen de mesh.

Deze gids maakt gebruik van een downloadbaar [voorbeeld robotmodel](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/shoebot-base-model.fbx)  en [Blender versie 3.0](https://www.blender.org/download/releases/3-0/) . Als je een andere versie van Blender gebruikt, kunnen er kleine verschillen zijn in de gebruikersinterface en instellingen.

## [Stel Blender in](#stel-blender-in)[](#stel-blender-in)

Om te beginnen met het maken van een gerigde mesh, stel je eerst het volgende in je Blender-project in:

1.

Open een nieuw Algemeen  project in Blender.

2.

Selecteer de standaardvorm, camera en lichten, en druk vervolgens op Delete .

### [Importeer een model](#importeer-een-model)[](#importeer-een-model)

Voor dit voorbeeld, importeer een [robotmodel](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/shoebot-base-model.fbx)  in Blender als je mesh-object.

Om een bestaand .fbx  model te importeren:

1.

Klik in de bovenbalk op Bestand . Een pop-upmenu verschijnt.

2.

Selecteer Importeren , en vervolgens het bestandsformaat van het model dat je importeert. Voor dit voorbeeld, selecteer FBX (.fbx)  en het .fbx  referentiemodel. Het model verschijnt in de 3D-weergave.

 ![Geïmporteerd Model](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/rigging-simple/rigging-r1-imported.png)

## [Maak een botstructuur](#maak-een-botstructuur)[](#maak-een-botstructuur)

Nu je model zich binnen Blender bevindt, moet je een armature  en botten  aan je mesh-object toevoegen. Een armature  is een skeletachtig riggingobject dat fungeert als een container voor botten, terwijl botten  objecten zijn die de beweging en vervorming van de groep vertices, of vertexgroep , die de bot omringen, aansturen.

### [Voeg een armature toe](#voeg-een-armature-toe)[](#voeg-een-armature-toe)

Een armature is een structuur die nodig is om botten aan je mesh toe te voegen. Nadat je een armature hebt toegevoegd, kun je een onbeperkt aantal botten binnen je mesh-object maken en repositioneren.

Om een armature toe te voegen:

1.

Selecteer bovenaan de 3D-weergave Toevoegen  → Armature .

2.

Voor een betere visualisatie van de botten, navigeer in de linker navigatie van de Eigenschappen-editor  naar Armature Objecteigenschappen .

3.

In de sectie Weergave in het venster , navigeer naar de eigenschap Toon , en schakel Voor aan  in.

### [Voeg botten toe en positioneer ze](#voeg-botten-toe-en-positioneer-ze)[](#voeg-botten-toe-en-positioneer-ze)

Wanneer je een armature aan je project toevoegt, voegt Blender automatisch één bot toe aan de armature op een standaardpositie en -schaal die als de wortelbot zal fungeren.

Om twee extra botten toe te voegen en te positioneren:

1.

Klik op de bot  om deze te markeren.

2.

Klik bovenaan de 3D-weergave op de dropdown voor de modus, en schakel over naar Bewerkmodus .

3.

Klik in de weergave op Toevoegen  → Enkele Bot . Voer deze stap twee keer uit.

4.

Klik in de weergave of de Outliner op een nieuw gemaakte bot  om deze te markeren.

5.

Druk op G  en gebruik je muis om de bot naar de rechterarm  te slepen.

6.

Klik op de tweede bot en druk op G  om de bot naar de linkerarm  te slepen.

7.

Klik op de top van de rechter bot  zodat de punt gemarkeerd is. Druk op G  om de bot horizontaal naar rechts te slepen en te oriënteren.

8.

Klik op de top van de linker bot  zodat de punt gemarkeerd is. Druk op G  om de bot horizontaal naar links te slepen en te oriënteren.

9.

Dubbelklik in de Outliner en hernoem  je botten zodat ze later gemakkelijk kunnen worden verwezen.

## [Koppel armature](#koppel-armature)[](#koppel-armature)

Nadat je de botstructuur hebt gemaakt en gepositioneerd, moet je de armature aan het mesh-object koppelen door de armature aan het mesh-object te koppelen.

In deze gids moet je ook de functie Automatische Gewichten  van Blender gebruiken wanneer je een armature koppelt, omdat deze automatisch gewichten en invloeden aan je mesh toevoegt.

Om een armature aan een mesh te koppelen:

1.

Klik bovenaan de 3D-weergave op de dropdown voor de modus, en schakel terug naar Objectmodus .

2.

Druk op Alt A  (Windows) of ⌥ A  (Mac) om elk object te deselecteren.

3.

Houd Shift  ingedrukt en selecteer het mesh-object  en vervolgens de armature . De volgorde van selectie is belangrijk.

4.

Klik in de Weergave  met de rechtermuisknop op het mesh-object. Een pop-upmenu verschijnt.

5.

Selecteer Ouder , en vervolgens Met Automatische Gewichten .

## [Wijs vertices toe aan botten](#wijs-vertices-toe-aan-botten)[](#wijs-vertices-toe-aan-botten)

Met je armature verbonden met het mesh-object, kun je nu de mesh-vertices van je ledematen toewijzen zodat ze volledig worden beïnvloed door hun overeenkomstige botten. Als een rigide model zal elk lid volledig buigen en articuleren wanneer de botten worden gedraaid, wat ideaal is voor een niet-organisch karakter zoals een robot.

Om bot-invloed toe te wijzen aan de linker- en rechterarmen:

1.

Selecteer in Objectmodus het robotmesh-object .

2.

Schakel in de dropdown voor de modus over naar Bewerkmodus .

3.

Schakel rechtsboven in de weergave over naar X-Ray -weergave met de opties voor Materiaalvoorbeeld.

4.

Sleep en selecteer de vertices die je met de rechter bot wilt verplaatsen.

5.

Navigeer naar het Objecteigenschappen -paneel.

6.

In de sectie Vertexgroep , selecteer de naam van de bot die je wilt toewijzen en klik op Toewijzen .

7.

Herhaal stappen 4-6  voor de andere bot en arm-vertices.

8.

Sleep en selecteer de rest van de vertices in het midden van de robot.

9.

Navigeer naar het Objecteigenschappen -paneel.

10.

In de sectie Vertexgroep, selecteer de Middelste bot  en klik op Toewijzen .

## [Test](#test)[](#test)

Je kunt je rig in verschillende poses testen in de Pose-modus. Het is belangrijk om je rigs te testen na het toepassen of wijzigen van invloeden voordat je exporteert.

Om je toegepaste invloeden te testen:

1.

Selecteer in Objectmodus  een deel van je model.

2.

Klik bovenaan de 3D-weergave op de dropdown voor de modus, en schakel over naar Pose -modus.

3.

Houd Shift  ingedrukt en klik op de bot die je wilt testen om deze te markeren, druk vervolgens op R  om de rotatie te testen.

4.

Druk op Alt A  (⌥ A ) om de huidige bot te deselecteren, selecteer vervolgens opnieuw en test een andere bot.

Om de rotatie van een geselecteerde bot naar neutraal te resetten, druk op Alt + R . Terwijl je draait, kun je ook op het scrollwiel van je muis drukken om de assen van je rotatie te veranderen.

Het robotmodel is nu een gerigde mesh en klaar om te [exporteren](/docs/nl-nl/art/modeling/export-requirements)  naar Studio. Ter referentie kun je de [eindexport](https://prod.docsiteassets.roblox.com/assets/modeling/meshes/reference-files/shoebot-rigged-model.fbx)  (.fbx ) van het model dat in deze gids is gerigged downloaden.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
