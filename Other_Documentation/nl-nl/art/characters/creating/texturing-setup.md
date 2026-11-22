<!-- Source: https://create.roblox.com/docs/nl-nl/art/characters/creating/texturing-setup -->

Textuurinstelling | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Textuurinstelling

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Textureren  is het proces van het aanpassen van de kleur, toon en schaduw van het oppervlak van je model. Aangepaste meshes en modellen gebruiken een 2D-afbeelding, bekend als een textuurmap, om verschillende elementen van het oppervlak uiterlijk op je 3D-object te projecteren.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Pre-Texturing.png)  Model na aangepaste sculpting

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Post-Texturing.png) Model na textureren

Elk sjabloon wordt geleverd met een kleurtextuurmap, die je kunt aanpassen en wijzigen met de textuurbewerkingshulpmiddelen van Blender. Aangezien de meeste Roblox-avatar's kunnen profiteren van aangepaste huidskleuren, is het belangrijk om te begrijpen hoe je [aangepaste huidskleuren kunt bekijken](/docs/nl-nl/art/characters/creating/blender-configurations#voorbeeld-huidtinten)  in Blender om te verifiëren hoe je uiteindelijke asset eruit zal zien in een Roblox-spel.

Met het oog op het demonstreren van het basis textureringsproces, behandelt deze tutorial de basisinstelling voor textuurschilderen, past een volledig ondoorzichtige textuur toe op delen van de ogen van de karakter, en gedeeltelijk ondoorzichtige details op het gezicht. Je kunt dezelfde technieken toepassen op andere delen van de geometrie van je karakter.

Wanneer je delen van het lichaam van je karaktermodel texturiseert, zorg er dan voor dat je karaktermodel een bescheidenheid laag over gevoelige gebieden heeft. Voor meer informatie, zie [Marktplaatsbeleid - Bescheidenheid lagen](/docs/nl-nl/marketplace/marketplace-policy#bescheidenheid-lagen) .

## [Textuurinstellingen](#textuurinstellingen)[](#textuurinstellingen)

Als je een downloadbaar sjabloon van Blender gebruikt, is het belangrijk om in gedachten te houden dat Blender je vereist om je texturen handmatig  op te slaan in het 2D-weergavevenster van het Textuur Schilderen-tabblad. Als je alleen je .blend  projectbestand opslaat, worden je texturen * niet*  samen met het bestand opgeslagen. Dit kan ervoor zorgen dat je uren werk verliest als je je voortgang niet periodiek opslaat terwijl je bezig bent.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Blender-Save-Image.png)

Blender 5.2 en latere versies bieden een textuurinstelling om dit gedrag te overschrijven:

1.

Navigeer in de bovenbalk naar Bewerken  > Voorkeuren . Het Voorkeuren  venster wordt weergegeven.

2.

Selecteer in de verticale navigatie het tabblad Opslaan & Laden .

3.

Stel in de sectie Blend-bestanden  Bewaar Gewijzigde Afbeeldingen  in op Altijd Opslaan .

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Blender-Always-Save-Setting.png)

## [Stel textuurresolutie in](#stel-textuurresolutie-in)[](#stel-textuurresolutie-in)

Roblox Studio ondersteunt een textuurresolutie van 1024 x 1024  voor albedo textuurkaarten. Bij het gebruik van applicaties zoals Blender of Maya om direct op een model te textureren, kunnen extreem fijne details mogelijk niet worden geschilderd zoals verwacht vanwege de resolutie en het detailniveau van de schildering.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Texture-Resolution-A.png)  Textuurschilderen op 1024 x 1024 resolutie

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Texture-Resolution-B.png) Textuurschilderen op 2048 x 2048 resolutie

Wanneer je fijne details aan je textuur toevoegt, verhoog dan tijdelijk de afbeeldingsresolutie van je textuurmap naar 2048 x 2048  of 4096 x 4096 . Nadat je met textureren klaar bent, wijzig je de afbeeldingsresolutie terug naar 1024 x 1024  om de wijzigingen vast te leggen.

Om de afbeeldingsresolutie van je textuur te wijzigen:

1.

Selecteer in het Indeling  tabblad de Head_Geo .

2.

Schakel over naar het Textuur Schilderen  tabblad, selecteer vervolgens in het 2D-weergavevenster Afbeelding  > Grootte Wijzigen .

3.

Stel de textuurgrootte in:

-

Gebruik 2048  of 4096  voor een hogere resolutie bij het maken van gedetailleerd textuurwerk.

-

Gebruik 1024  voor de standaard Roblox-ondersteunde resolutie.

[Volgende](/docs/nl-nl/art/characters/creating/texturing-eyes)[Vorige](/docs/nl-nl/art/characters/creating/sculpting)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
