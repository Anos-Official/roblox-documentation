<!-- Source: https://create.roblox.com/docs/nl-nl/art/accessories/publish-eyebrows-eyelashes -->

Publiceer lichamen met wimpers en wenkbrauwen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Avataritems

# Publiceer lichamen met wimpers en wenkbrauwen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Wimpers en wenkbrauwen zijn cosmetica die kunnen helpen om gelaatskenmerken te benadrukken en een unieke manier van het aanpassen van een karakter te creëren. Net als kleding zijn wimpers en wenkbrauwen [3D gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories)  die kunnen rekken en passen over verschillende gezichtsvormen en kunnen vervormen en rekken met de gezichtsanimaties van het karakter.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Nature-Girl-No-Accessories.png) Karakterlichaam zonder wimpers en wenkbrauwen

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Nature-Girl-With-Face-Accessories.png) Karakterlichaam met wimpers en wenkbrauwen

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Eyebrows-Eyelashes-Only.png) Standalone wimpers en wenkbrauwen

Bij het publiceren van wimpers en wenkbrauwen, moet je deze [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  objecten onder het avatar karakter's [Model](/docs/nl-nl/reference/engine/classes/Model)  plaatsen voordat je het karakter Model  naar de Marketplace uploadt. Deze Accessory  gezichtobjecten moeten voldoen aan de accessoires vereisten van Roblox en moeten gelaagde componenten bevatten zoals omheining, rigging en skinning componenten. Voor een overzicht van het maken van je eigen wimpers en wenkbrauwen, zie [Maak gezichtaccessoires](/docs/nl-nl/art/characters/facial-animation/create-face-accessories) . Wenkbrauwen en wimpers moeten gebruik maken van [Automatische Skinning Transfer](/docs/nl-nl/avatar/automatic-skinning-transfer)  met de RBX_Leader  en RBX_Follower  speciale gewrichten om op de marketplace gepubliceerd te worden.

Op dit moment kun je alleen wimpers , wenkbrauwen  en haar  bundelen met je lichaam bij het uploaden naar de Marketplace. Andere gezichtaccessoires, zoals hoorns, make-up, glitter of andere cosmetica zijn niet toegestaan. Zie [Marketplace beleid](/docs/nl-nl/marketplace/marketplace-policy)  voor specifieke informatie over toegestane cosmetica en andere beleidsregels en richtlijnen.

## [Configureer wimper- en wenkbrauwaccessoires](#configureer-wimper--en-wenkbrauwaccessoires)[](#configureer-wimper--en-wenkbrauwaccessoires)

Gebruik de volgende stappen om je gezichtaccessoire en lichaamsassets in Studio te importeren. Nadat je de wimpers en wenkbrauwen hebt omgezet naar Accessory  objecten, plaats je de Accessory  objecten binnen het karakter Model  voordat je het karakter naar de Marketplace uploadt.

Je kunt referentie .fbx  modellen van [wimpers](https://prod.docsiteassets.roblox.com/assets/art/reference-files/Eyelashes.fbx) , [wenkbrauwen](https://prod.docsiteassets.roblox.com/assets/art/reference-files/Eyebrows.fbx) , en een [avatarlichaam](https://prod.docsiteassets.roblox.com/assets/art/reference-files/AnimeFemale-Studio-Ready.fbx)  downloaden om dit proces te volgen.

1.

In de [Importer](/docs/nl-nl/studio/importer) , importeer de .fbx  bestanden van je gezichtaccessoire en lichaam. De wimpers, wenkbrauwen en het lichaam worden elk in je Workspace weergegeven als een Model .

1.

Als je het referentielichaam gebruikt, stel dan Rig General  > Rig Type  in op Rthro .

2.

Gebruik de [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  en selecteer het Wimper  of Wenkbrauw  model en klik op Volgende .

 ![](https://prod.docsiteassets.roblox.com/assets/art/accessories/AFT-Eyebrows-Example.png)

3.

Selecteer het juiste Accessory  > Wimper  of Accessory  > Wenkbrauw  assettype en klik op Volgende .

4.

OPTIONEEL

 Bekijk de pasvorm van je gezichtaccessoire.

1.

Als het gezichtaccessoire is gemodelleerd op een specifiek karakterlichaam, wil je misschien dat karakterlichaam in Studio importeren en gebruiken als een mannequin in de preview van de fitting tool. Zie [Accessory Fitting Tool](/docs/nl-nl/avatar/accessory-fitting-tool)  voor meer informatie over het toevoegen van aangepaste karakters.

2.

Als je het meegeleverde referentielichaam gebruikt, kun je doorgaan naar stap 5.

5.

Klik op Genereer MeshPart Accessory  om je MeshPart te maken.

6.

Herhaal stappen 2-5  voor het andere gezichtaccessoire.

7.

In de Outliner, sleep en laat  de gezicht Accessory  objecten binnen de karakter Model  instantie vallen. De accessoires worden automatisch uitgerust en bevestigd op de juiste gebieden van je avatar karakter.

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Anime-Girl-Eyebrows-Example.png) Workspace preview van lichaam met gezichtaccessoires

![](https://prod.docsiteassets.roblox.com/assets/art/accessories/Face-Accessory-Hierarchy.png) Outliner hiërarchie

8.

Indien nodig, hernoem de accessoireobjecten naar WimperAccessoire  of WenkbrauwAccessoire  overeenkomstig.

9.

Zodra je klaar bent om het avatar model met je gezichtaccessoires te uploaden, zie [Upload een asset](/docs/nl-nl/marketplace/publish-to-marketplace#upload-een-activum)  voor instructies over het uploaden en publiceren van je avatarlichaam met wimpers en wenkbrauwen naar de Marketplace.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
