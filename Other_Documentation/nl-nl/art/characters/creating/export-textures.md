<!-- Source: https://create.roblox.com/docs/nl-nl/art/characters/creating/export-textures -->

Textures exporteren | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Textures exporteren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het is belangrijk om je assets meerdere keren te testen op elk punt van het creatieproces, of het nu binnen Blender is of na het importeren in Studio. Voor meer informatie, zie [Test karakterlichamen](/docs/nl-nl/avatar/character-bodies/test) .

Of je nu je karakter exporteert voor testen, of een finale export uit Blender uitvoert, je moet de juiste exportinstellingen toepassen om ervoor te zorgen dat Blender de juiste karaktergegevens exporteert.

## [Textures exporteren](#textures-exporteren)[](#textures-exporteren)

Naast de standaard PBR-texturen, bevat je sjabloonkarakter vier aparte afbeeldingskaarten die de oppervlakte-uiterlijk vormen. Afhankelijk van je workflow, kun je ervoor kiezen om de afbeeldingskaarten in je exportbestand in te voegen of de texturen afzonderlijk als afbeeldingsbestanden te exporteren. Beide methoden hebben voordelen:

-

[Texturen inbedden](#texturen-inbedden)  vereenvoudigt je export door al je texturen binnen het enkele .fbx -bestand te verpakken.

-

[Textuurafbeeldingen exporteren](#textures-exporteren)  geeft je directe toegang tot de afbeeldingstexturen, zodat je ze sneller kunt testen en verwisselen.

### [Texturen inbedden](#texturen-inbedden)[](#texturen-inbedden)

Het inbedden van de textuurkaarten in je .fbx -export kan het exporteren vanuit Blender en het importeren in Studio vereenvoudigen. Wanneer je je texturen inbedt met de sjabloonbestanden van Roblox, moet je een snelle aanpassing maken aan de shader-nodes voor de aangepaste huidskleur in het Blender-bestand.

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Cleanup-Node-A.png) Standaard node-configuratie: Mix-node verbonden met Basis Kleur

![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Cleanup-Node-B.png) Exportabele node-configuratie: Kleur-node direct verbonden met Basis Kleur

Om je texturen voor te bereiden om in te bedden met de export:

1.

Selecteer in Object -modus een deel van het karakter.

2.

Navigeer naar het Shading -tabblad, en stel in de node-editor het Shader Type  in op Object .

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Cleanup-Object-Select.png)

3.

Zoek de node die is verbonden met de Basis Kleur -node van de Principled BSDF .

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Cleanup-Mix-Node.png)

4.

Klik en sleep de lijn van Basis Kleur  om de node los te koppelen.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Cleanup-Disconnect-Node.png)

5.

Zoek de file26 -node met de kleurtextuurkaart en klik en sleep de Kleur  naar de Basis Kleur -node van de Principled BSDF .

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Cleanup-Node-B.png)

### [Afbeeldingsbestanden uitpakken](#afbeeldingsbestanden-uitpakken)[](#afbeeldingsbestanden-uitpakken)

Als alternatief voor het inbedden van texturen, kun je je textuurbestanden exporteren als aparte .png -afbeeldingsbestanden, wat je in staat stelt om snel toegang te krijgen tot en afbeeldingskaarten te verwisselen.

Om je textuurafbeeldingsbestanden te exporteren:

1.

Navigeer naar Bestand  > Externe Gegevens  > Hulpmiddelen Uitpakken .

2.

Selecteer Gebruik bestanden in huidige map  om op te slaan in dezelfde map als je project. Blender exporteert je afbeeldingsbestanden naar een textures-map in de bovenliggende map van je project.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Exporting-Pack-Resources.png)

[Volgende](/docs/nl-nl/art/characters/creating/export-character)[Vorige](/docs/nl-nl/art/characters/creating/final-checks)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
