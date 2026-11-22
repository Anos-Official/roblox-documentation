<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/modeling/create-neon-signs -->

Maak neonreclames | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. Modellering

# Maak neonreclames

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Neonreclames  zijn heldere en kleurrijke elektrische borden die de aandacht vestigen op iets binnen een spel, zoals waar gebruikers een gebouw kunnen binnenkomen of een item kunnen kopen. Door modellering en verlichtings technieken te combineren, kun je neonreclames maken en gebruiken om de onderdompeling in je omgevingen te verhogen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-neon-signs/Overview.jpg)

Zoals bij alle 3D-creaties zijn er veel manieren om een bepaald doel te bereiken. In deze gids kun je snel je eigen neonreclame maken met tools en methoden die alleen binnen Studio beschikbaar zijn, met slechts een paar basisassets, waaronder een [.obj](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-neon-signs/open-text.obj)  bestand voor de 3D-tekst van het reclame model.

In de volgende methode om een neonreclame te maken, volg je elke sectie om te leren hoe je:

-

De achterwand en rand van de reclame maakt met basisdelen.

-

De reclame vormt met de solide modelleringstools van Studio.

-

3D-tekst in je reclame verwerkt en de reclame als een model opslaat.

Je kunt je eigen assets maken in externe modelleringstools en meedoen met je eigen ontwerp. Voor informatie over het exporteren van modellen voor gebruik in Studio, zie [Exportvereisten](/docs/nl-nl/art/modeling/export-requirements) .

## [Maak de achterwand en rand](#maak-de-achterwand-en-rand)[](#maak-de-achterwand-en-rand)

Een [Part](/docs/nl-nl/reference/engine/classes/Part)  is het primaire bouwblok van Roblox dat je kunt verplaatsen, vergroten, roteren en aanpassen om hun uiterlijk te veranderen, zoals hun kleur en materiaal. Het gebruik van [basisdelen](/docs/nl-nl/parts)  om de basis van neonreclames te creëren is nuttig omdat de achterwand en rand van de reclame alleen basisvormen vereisen.

Om de achterwand en rand te maken:

1.

Navigeer naar de Home  of Model  tabbladwerkbalk van Studio.

2.

Klik op de dropdown-pijl op de Part  knop en selecteer Block . Een blokdeel verschijnt in de werkruimte dat de achterwand van je neonreclame gaat worden.

3.

In het Explorer  venster, selecteer het blok, en in het Properties  venster,

1.

Stel BrickColor  in op Zwart .

2.

Stel Size  in op 8,4,1 .

3.

Stel Name  in op Achterwand .

4.

Schakel de Anchored  eigenschap in.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-neon-signs/Backboard.jpg)

4.

In het Explorer  venster, selecteer Achterwand , druk dan op Ctrl D  (⌘ D ) om het deel te dupliceren.

5.

In de werkbalk, selecteer de Verplaats  tool en gebruik een van de as-pijlen om het gedupliceerde achterwanddeel van de originele positie weg te trekken zodat je elk object kunt zien.

6.

In het Explorer  venster, selecteer het gedupliceerde achterwanddeel dat de rand van je neonreclame gaat worden, en in het Properties  venster,

1.

Stel BrickColor  in op Limoengroen .

2.

Stel Size  in op 7.75, 3.75, 0.25 .

3.

Stel Name  in op Rand .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-neon-signs/Border.jpg)

7.

In het Explorer  venster, selecteer Rand , druk dan op Ctrl D  (⌘ D ) om het deel te dupliceren. Verplaats dit nieuwe deel niet  omdat het in zijn huidige positie moet blijven voor de volgende sculptuurstap.

Nu je drie delen hebt die de basisvormen van je neonreclame vormen, kun je de vorm van de rand sculpturen.

## [Vorm de neonrand](#vorm-de-neonrand)[](#vorm-de-neonrand)

Met [solide modellering](/docs/nl-nl/parts/solid-modeling)  kun je delen op unieke manieren samenvoegen en scheiden om complexere vormen te vormen die bekend staan als unies . Dit proces stelt je in staat om het gedupliceerde randdeel te vergroten en te wijzigen zodat het de neonrand wordt.

Om de neonrandvorm te creëren:

1.

In het Explorer  venster, selecteer het gedupliceerde randdeel, en in het Properties  venster, stel de Size  in op 7.5, 3.5, 1.0 .

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-neon-signs/Duplicate-Border.jpg)

2.

Met het gedupliceerde randdeel nog steeds geselecteerd, klik op de Negate  knop in de werkbalk. Het randdeel wordt doorschijnend en zijn Name  eigenschap verandert automatisch in NegativePart .

3.

Met NegativePart  nog steeds geselecteerd, houd Ctrl / ⌘  ingedrukt en klik op het originele randdeel om beide delen tegelijkertijd te selecteren.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-neon-signs/NegativePart.jpg)

4.

In de werkbalk, selecteer Union  om beide delen samen te voegen. Een randvormig deel verschijnt, en de Name  eigenschap verandert automatisch in Union .

5.

In het Explorer  venster, selecteer de unie, en in het Properties  venster,

1.

Stel Name  in op Rand . Dit helpt om alle objecten binnen de werkruimte te organiseren.

2.

Stel Material  in op Neon . Dit laat het deel gloeien.

6.

In de werkbalk, selecteer de Verplaats  tool en gebruik een van de as-pijlen om Rand  voor Achterwand  te trekken.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-neon-signs/Moving-Border.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-neon-signs/Border-Moved.jpg)

Nu je een complete achterwand en een gloeiende neonrand hebt, kun je extruderende neon 3D-tekst voor de woorden van de reclame maken.

## [Verwerk neon 3D-tekst](#verwerk-neon-3d-tekst)[](#verwerk-neon-3d-tekst)

Aangezien Studio geen 3D-tekst ondersteunt, biedt deze gids een open-text.obj bestand dat je in je scène kunt importeren en dat een 3D-model van tekst bevat dat het woord "OPEN" spelt. Je kunt ook andere methoden gebruiken om 3D-teksten of aangepaste ontwerpen voor dit proces te maken, zoals het gebruik van je eigen modellen uit externe modelleringsoftware, werken met community-plugins, of het handmatig maken van je eigen tekst in Studio via solide modellering.

Om neon 3D-tekst van het [open-text](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-neon-signs/open-text.obj)  .obj  bestand te verwerken:

1.

Importeer het open-text  .obj  bestand.

1.

Selecteer in het Bestand  menu van Studio Importeren . Een bestandsbrowser verschijnt.

2.

Selecteer het open-text  .obj  bestand, en klik dan op de Open  knop. Het Import Preview  venster verschijnt.

3.

Houd de standaard importinstellingen aan, en klik dan op de Importeer  knop. De open tekstmodellen verschijnen binnen de viewport.

2.

In de werkbalk, selecteer de Verplaats tool en gebruik een van de as-pijlen om de tekst in het midden van de reclame te plaatsen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-neon-signs/Final-Sign.jpg)

3.

In het Properties  venster,

1.

Stel Color  in op 170,0,0 .

2.

Stel Material  in op Neon .

4.

In het Explorer  venster, selecteer de tekstmodellen, Rand , en Achterwand , en druk dan op Ctrl G  (⌘ G ) om ze in een enkel [Model](/docs/nl-nl/reference/engine/classes/Model)  object te groeperen.

Voor een referentie van hoe deze neonreclame eruit ziet binnen Studio, kun je het [basisprojectbestand](https://prod.docsiteassets.roblox.com/assets/tutorials/creating-neon-signs/neon-sign-baseplate.rbxl)  downloaden en vergelijken met je model.

5.

Hernoem het nieuwe model naar NeonReclame .

6.

In het Explorer  venster, klik met de rechtermuisknop op NeonReclame . Een contextmenu verschijnt.

7.

Selecteer Opslaan naar Roblox .

Nadat je het asset in je [Toolbox](/docs/nl-nl/projects/assets/toolbox)  hebt opgeslagen, kun je het binnen al je spellen gebruiken. Bovendien kun je [je asset distribueren naar de Creator Store](/docs/nl-nl/production/creator-store)  om het openbaar beschikbaar te maken voor alle makers om het ook binnen hun spellen te gebruiken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
