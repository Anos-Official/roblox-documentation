<!-- Source: https://create.roblox.com/docs/nl-nl/parts/custom-terrain-materials -->

Aangepaste terreinmaterialen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)

# Aangepaste terreinmaterialen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Aangepaste terreinmaterialen  stellen je in staat om tot 62 schilderbare materialen voor terrein te definiëren, zodat je onderscheidende omgevingen binnen een enkele plaats kunt bouwen of meer kleur en variëteit aan een bestaand landschap kunt toevoegen. Elk materiaal kan een aangepaste kleur en een optionele [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  voor aangepaste texturen gebruiken.

## [Schakel Uitgebreid Terrein in](#schakel-uitgebreid-terrein-in)[](#schakel-uitgebreid-terrein-in)

Uitgebreid Terrein is standaard uitgeschakeld en wordt per plaats ingeschakeld. Het inschakelen ervan wisselt de terreinbackend, zodat de plaats opnieuw moet worden geopend om de wijziging van kracht te laten worden.

Naast aangepaste materialen omvat Uitgebreid Terrein verbeteringen in rendering, opslag en levering die de bijdrage van terrein aan de bestandsgrootte van de plaats aanzienlijk verminderen en de streaming en laadtijden van terrein verbeteren.

Als je een plaats met aangepaste terreinmaterialen hebt bewerkt tijdens het Early Access-programma, moet je nog steeds Uitgebreid Terrein  instellen op Ingeschakeld  op [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) . Anders kunnen aangepaste materialen als gras verschijnen.

Om aangepaste terreinmaterialen in een plaats in te schakelen:

1.

Ga in een plaats in Studio naar de [Explorer](/docs/nl-nl/studio/explorer)  en selecteer [Workspace](/docs/nl-nl/reference/engine/classes/Workspace) .

2.

Stel in het [Eigenschappen](/docs/nl-nl/studio/properties)  venster Uitgebreid Terrein  in op Ingeschakeld .

3.

Klik in de Plaats opnieuw opstarten  dialoog op Opnieuw opstarten .

Wanneer je deze functie in een nieuwe plaats inschakelt, slaat Studio de plaats op en sluit deze voor je. Je moet de plaats nog steeds opnieuw openen om de wijziging van kracht te laten worden.

## [Maak aangepaste terreinmaterialen](#maak-aangepaste-terreinmaterialen)[](#maak-aangepaste-terreinmaterialen)

Je kunt aangepaste terreinmaterialen maken met de materiaalkiezer van de Terrain Editor:

1.

Open de Terrain Editor  en kies een borstelgereedschap zoals Schilderen , Tekenen , Vullen  of Vormgeven .

2.

Open de materiaalkiezer naast Bronmateriaal .

3.

Klik op het +  pictogram om een nieuw terreinmateriaal te maken.

4.

Kies een naam en een basismateriaal. Je kunt een [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  selecteren om aangepaste texturen toe te passen of de Kleur  aanpassen om het materiaal te tinten.

5.

Schilder, teken, vul of vorm met het geselecteerde materiaal.

 ![Dialoog voor het maken van terreinmateriaal met een naam, basismateriaal, optionele materiaalvariant en kleurverf.](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Create-Terrain-Material.png)

Je kunt ook aangepaste terreinmaterialen gebruiken met het Vervangen  gereedschap om het ene materiaal door een ander te vervangen zonder de rest van het terrein te veranderen.

Aangepaste terreinmaterialen ondersteunen meerdere kleurvariaties van zowel standaard terreinmaterialen als aangepaste [MaterialVariants](/docs/nl-nl/reference/engine/classes/MaterialVariant) . Je kunt bijvoorbeeld verschillende tinten gras in dezelfde plaats creëren in plaats van een enkel basismateriaal globaal te overschrijven.

Om een [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  te maken voor gebruik met terreinmaterialen, zie [Aangepaste materialen](/docs/nl-nl/parts/materials#aangepaste-materialen) . Je kunt ook varianten genereren met de [Materiaalgenerator](/docs/nl-nl/studio/material-generator) .

## [Beheer terreinmaterialen](#beheer-terreinmaterialen)[](#beheer-terreinmaterialen)

Gebruik de Terrain Materials Manager  om aangepaste terreinmaterialen voor een plaats toe te voegen, te verwijderen of te bewerken.

Open de manager vanuit Venster  ⟩ 3D , of klik met de rechtermuisknop op een materiaal in de materiaalkiezer van de Terrain Editor en selecteer Openen in Terrain Material Manager .

 ![Venster van de Terrain Material Manager met terreinmaterialen gerangschikt op slot.](https://prod.docsiteassets.roblox.com/assets/modeling/terrain/Terrain-Material-Manager.png)

Wanneer je de instellingen van een materiaal wijzigt, zoals de kleur, wordt de update onmiddellijk toegepast op al het terrein dat dat materiaal gebruikt. Als je een materiaal verwijdert dat het terrein nog gebruikt, wordt het aangetaste terrein felpaars, zodat je het kunt identificeren en vervangen.

## [Beperkingen](#beperkingen)[](#beperkingen)

-

Aangepaste fysieke eigenschappen op een [MaterialVariant](/docs/nl-nl/reference/engine/classes/MaterialVariant)  worden nog niet gerespecteerd door aangepaste terreinmateriaal slots.

-

Het bewerken van terrein in Team Create kan meshing- of visuele bugs introduceren.

-

In Team Create plaatsen is de herstartprompt na het wijzigen van Uitgebreid Terrein  niet voldoende om de wijziging toe te passen. Verlaat de plaats en wacht ongeveer 15 seconden voordat je deze opnieuw opent.

-

Wanneer [streaming](/docs/nl-nl/../workspace/streaming)  is ingeschakeld met een kleine streamingradius, kunnen dunne terreineigenschappen (minder dan 16 voxels dik) verdwijnen op de client of tijdens het testen. Om dit op te lossen, voeg je dikte toe aan het terrein. Met Uitgebreid Terrein bespaart het maken van terrein dunner dan 16 voxels weinig of geen geheugen, dus het dunner maken van terrein wordt niet aanbevolen als geheugenoptimalisatie.

-

Het importeren van hoogtekaarten en kleurkaarten kan andere resultaten opleveren dan voorheen. Importeren met een kleurkaart is gevoeliger voor de kleuren van je materialen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
