<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/assign-textures -->

Blender en Maya textuurinstellingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Textureren

# Blender en Maya textuurinstellingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze gids behandelt het proces om textuurafbeeldingen in Blender of Maya aan je 3D-model toe te wijzen, zodat ze naadloos in Studio worden geïmporteerd. Het importproces ondersteunt zowel basistexturen als realistische PBR-texturen, zolang ze voldoen aan de [textuurspecificaties](/docs/nl-nl/art/modeling/texture-specifications)  van Roblox.

De volgende informatie is specifiek voor het toepassen van make-uptexturen op generieke meshes . Voor meer informatie over het opnieuw toewijzen van texturen voor make-upassets, zie [Texturen opnieuw toewijzen in Blender en Maya](/docs/nl-nl/avatar/makeup/reassign-textures) .

## [Blender](#blender)[](#blender)

Om Roblox-ondersteunde texturen aan je 3D-model in Blender toe te wijzen:

1.

Selecteer je mesh-object in de Outliner.

2.

Navigeer in het Eigenschappenpaneel naar het Materialen-tabblad .

3.

Controleer of je object een Materiaal heeft toegewezen met de Oppervlakte ingesteld op Principled BSDF .

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Blender-Material-Check.png)

4.

Als er geen materiaal is toegewezen, klik dan op het + symbool om een materiaal toe te voegen.

1.

Klik op de Nieuwe knop. Een nieuw Principled BSDF -materiaal wordt aangemaakt.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Blender-Create-New-Material.png)

5.

Navigeer naar het Shading-tabblad .

6.

Met je mesh-object geselecteerd, controleer je de nodegrafiek. Er kunnen al textuurafbeeldingsnodes zijn verbonden met de Principled BSDF -node.

7.

Voeg in het nodegrafiekgebied een textuurafbeeldingsnode toe met rechtsklik ⟩ Toevoegen  ⟩ Textuur  ⟩ Afbeelding Textuur .

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Blender-Add-Image-Texture.png)

8.

Klik in de nieuwe Afbeelding Textuur-node op Openen om een bestandsbrowser te openen en je aangepaste textuur in te voegen.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Blender-Image-Texture-No-Assignment.png)

Als alternatief voor stappen 7-8 kun je een slepen en neerzetten  textuurbestand vanuit een ander venster in de grafiekeditor slepen.

9.

Nadat je de afbeeldingsnodes hebt toegevoegd en de juiste bestanden hebt toegewezen, sleep je de Image Texture -sockets naar de juiste sockets in de Principled BSDF -node:

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Blender-Expected-Nodes.png)

-

Basis textuur  of PBR kleur/albedo : verbind Kleur  met Basis Kleur .

-

Metaal textuur : verbind Kleur  met Metaal .

-

Ruwheid textuur : verbind Kleur  met Ruwheid .

-

Normaal textuur  afbeeldingen moeten worden toegevoegd aan een NormalMap-node:

1.

Rechtsklik in het grafiekeditorgebied en selecteer Toevoegen  ⟩ Vector  ⟩ Normal Map .

2.

Verbind de Kleur van de Afbeelding Textuur met de Kleur van de NormalMap.

3.

Verbind de Normaal van de NormalMap met de Normaal-socket van de PrincipledBSDF.

Na het vervangen van je PBR-texturen, [exporteer het hele model](/docs/nl-nl/art/modeling/export-requirements#blender)  en volg de instructies om [in Studio te importeren](/docs/nl-nl/studio/importer)

## [Maya](#maya)[](#maya)

Om Roblox-ondersteunde texturen aan je 3D-model in Maya toe te wijzen:

1.

Klik in de Statusbalk nabij de bovenkant van de standaardlay-out op het Hypershade-pictogram.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Select-Hypershade.png)

2.

Navigeer in het Maakvenster-paneel op de Hypershade-popup naar Maya  ⟩ Oppervlak  en klik op Standaard Oppervlak . Een oppervlaknode verschijnt in de node-editor.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Maya-Create-Surface.png)

1.

Als je een normaalmap toevoegt, navigeer dan naar Maya  ⟩ Hulpmiddelen  en klik op Bump 2d . Een node die vereist is voor normaalkaarten verschijnt in de node-editor.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Maya-Bump-2D.png)

3.

Sleep en zet je PBR-texturen in het grafieknetwerk.

 ![](https://prod.docsiteassets.roblox.com/assets/makeup/resources/Maya-Select-Graph-Network.png)

1.

Als je een normaalmap toevoegt, selecteer dan de Bump 2d-node en wijzig deze in Tangent Space Normals.

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Maya-Tangent-Space-Normals.png)

4.

Selecteer je model en navigeer naar het materiaal dat je wilt toewijzen. Rechtsklik en houd vast boven het materiaal en selecteer Materiaal toewijzen aan selectie .

 ![](https://prod.docsiteassets.roblox.com/assets/modeling/textures-decals/Maya-Assign-Material.png)

Na het vervangen van je PBR-texturen, [exporteer het model](/docs/nl-nl/art/modeling/export-requirements#maya)  en volg de instructies om [in Studio te importeren](/docs/nl-nl/studio/importer) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
