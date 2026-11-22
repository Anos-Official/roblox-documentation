<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/makeup/import -->

Importeren in Studio | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Make-up

# Importeren in Studio

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Importer van Studio stelt je in staat om 3D-assets in je projecten te importeren, zoals avatar kleding, accessoires en Roblox's [template heads](/docs/nl-nl/avatar/makeup#sjabloonhoofden)  voor make-up. De volgende instructies beschrijven hoe je een .fbx  of .gltf  templatebestand vanuit het beste praktijk [creatieproces](/docs/nl-nl/avatar/makeup#creatieproces)  in Studio kunt importeren als een Model  object dat je kunt gebruiken in je games, uploaden naar de Marketplace of delen met andere makers.

Deze instructies zijn specifiek van toepassing op de [Makeup test plaats](https://github.com/Roblox/avatar/tree/main/Makeup)  die een script gebruikt om programmatic een decal op het gezicht van het bijbehorende karakter toe te passen.

Om je asset als een make-up model te importeren:

1.

Voordat je begint, is het belangrijk om ervoor te zorgen dat je templatebestand de volgende objecten bevat die correct zijn geconfigureerd om te voldoen aan Roblox's [make-up specificaties](/docs/nl-nl/avatar/makeup/specifications) , anders kun je fouten tegenkomen in latere stappen:

-

Doel hoofd mesh

-

Doel hoofd cage mesh

-

Indien gewijzigd, Lips  mesh en bijbehorende texturen.

-

Indien gewijzigd, Face  mesh en bijbehorende texturen.

-

Indien gewijzigd, Eyes  mesh en bijbehorende texturen.

2.

Open in Studio de [Makeup test plaats](https://github.com/Roblox/avatar/tree/main/Makeup) .

3.

Klik op de Home  tab op de Import  knop om de Importer te openen. Een bestandsbrowser opent.

4.

Selecteer het .fbx  of .gltf  bestand van je make-up. De Importer laadt een voorbeeld van je make-up.

5.

Controleer of er geen fouten zijn met de geïmporteerde componenten, klik vervolgens op Import  om het bestand in Studio toe te voegen. Een nieuw Model  wordt in de workspace gevuld.

6.

Breid in het Explorer  venster het nieuwe Model  uit en controleer of Decal  kindobjecten zijn gevuld, elk met hun eigen WrapTextureTransfer  kindobject.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Imported-DataModel.png) Bij import verschijnen make-up decals binnen het Model.

![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Studio-Datamodel.png) Elke decal heeft een WrapTextureTransfer object als ouder

7.

Kopieer je nieuwe Decal  objecten naar de Makeup  map van een karaktermodel.

8.

OPTIONEEL

 Als je wenkbrauwen of wimpers wilt toepassen, verplaats dan die [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten naar de Accessories  map van het karakter. Voor dit plaatsbestand hoef je wimpers en wenkbrauwen niet eerst in Accessoires om te zetten.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/Makeup-Character-Folders.png)

9.

Druk op Play  om te playtesten en te verifiëren dat het karakter de nieuwe make-up heeft toegepast.

## [Test met Avatar Setup](#test-met-avatar-setup)[](#test-met-avatar-setup)

Je kunt ook de Avatar Setup tool gebruiken om make-up assets te previewen zonder te playtesten.

1.

Open de Avatar Setup tool door te navigeren naar Avatar  > Setup .

2.

Selecteer het model waarop je je assets wilt previewen.

3.

Voor make-up decals , zoals ogen, gezicht en lippen:

1.

Selecteer in het Explorer  venster alle make-up decal assets die je wilt toevoegen aan de Avatar Setup preview. De preview ondersteunt alleen geldige make-up decals met een kind [WrapTextureTransfer](/docs/nl-nl/reference/engine/classes/WrapTextureTransfer) .

2.

Klik in het Avatar Setup paneel op het +  symbool om de assets aan de Avatar Setup tool toe te voegen.

3.

Geef in de nieuwe prompt het type make-up asset op (ogen, gezicht, lippen), voor elke geselecteerde decal.

4.

Voor make-up meshes , zoals wenkbrauwen en wimpers:

1.

Verplaats in het Explorer  venster de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  objecten als kinderen binnen het avatar model.

2.

Klik in het Avatar Setup paneel op het +  symbool om de assets aan de Avatar Setup tool toe te voegen.

5.

Navigeer in het Avatar Setup paneel naar het Face  > Makeup  tabblad, en valideer dat je assets correct zijn geïmporteerd in de tool.

6.

Klik op assets om ze in je preview uit te rusten.

1.

Verander de volgorde van de assets door hun iconen aan de rechterkant van het previewvak te slepen.

2.

Klik op X  om ze uit je avatar preview te verwijderen.

7.

Om te zien hoe make-up animeert, navigeer naar het Animations  tabblad, en test verschillende sequenties om te zien hoe je avatar eruitziet met de toegepaste make-up.

Voor de beste resultaten, gebruik de avatars die door Roblox in de testplaats worden geleverd. Je kunt ook een andere avatar meenemen, maar de kwaliteit van de make-up pasvorm hangt af van de onderliggende cage van het hoofd, wat kan resulteren in een variabele uitstraling als deze niet goed is uitgelijnd.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
