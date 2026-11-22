<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/emotes/import -->

Emotes importeren | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Animations
6. /
7. Emotes

# Emotes importeren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Studio's [Animatie-editor](/docs/nl-nl/animation/editor)  stelt je in staat om animaties in je projecten te importeren. De volgende instructies beschrijven hoe je een .fbx -bestand met animatiegegevens in Studio importeert, het omzet in een CurveAnimation -object met een asset-ID, en vervolgens die asset-ID gebruikt in [Animation](/docs/nl-nl/reference/engine/classes/Animation) -objecten die je in je games kunt gebruiken, uploaden naar de Marketplace of delen met andere makers.

Het is belangrijk om ervoor te zorgen dat je emote voldoet aan de [emote-specificaties](/docs/nl-nl/avatar/emotes/specifications)  van Roblox om deze asset als een avatar-klaar emote te gebruiken of te verkopen, anders kun je op verschillende punten in de workflow fouten tegenkomen.

## [Importeren in Studio](#importeren-in-studio)[](#importeren-in-studio)

Om je asset als animatie te importeren:

1.

Als je nog geen karakterlichaam met een [standaard R15-rig](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  hebt, voeg er dan een toe aan je project in Studio.

1.

Klik in het tabblad Avatar  op de knop Character .

 ![Knop 'Character' gemarkeerd in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Character.png)

2.

Stel Rig Type  in op R15 .

3.

Stel Body Shape  in op Masculine  of Feminine .

4.

Selecteer een avatarstijl uit de aangeboden opties. Een avatar karakterlichaam met een standaard rigging armatuur wordt in de viewport weergegeven.

2.

Open de Animatie-editor.

1.

Klik in het tabblad Avatar  op de knop Clip Editor .

2.

Selecteer het karakter met een standaard rigging armatuur. De Animatie-editor wordt dienovereenkomstig bijgewerkt.

3.

Selecteer in de Animatie-editor  ⋯  > Importeren  > Van bestand  en selecteer je .fbx -bestand. Je animatie verschijnt in de tijdlijn van de Animatie-editor.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Editor-Import.png)

## [Genereer asset-ID](#genereer-asset-id)[](#genereer-asset-id)

Om een asset-ID voor je animatie te genereren, moet je eerst je animatiegegevens in de tijdlijn omzetten in een CurveAnimation -object. Wanneer je het CurveAnimation -object opslaat, maakt Roblox een cloud-gebaseerde asset-ID aan om je emote weer te geven.

De animatiegegevens voor emotes moeten een [CurveAnimation](/docs/nl-nl/reference/engine/classes/CurveAnimation) -object zijn in plaats van een [KeyframeSequence](/docs/nl-nl/reference/engine/classes/KeyframeSequence) -object.

Om een bestaande keyframe-sequentie om te zetten naar een CurveAnimation :

1.

Selecteer in de Animatie-editor  de knop Curve Editor  naast de tijdlijn. Een bevestigingsprompt verschijnt.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Editor-Curve-Animation-Icon.png)

2.

Druk op Bevestigen  om je keyframes om te zetten in een CurveAnimation -clip.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Editor-Curve-Prompt.png)

3.

Ga terug naar de Animatie-editor , selecteer ⋯  > Publiceren naar Roblox . Het venster Asset Configuration  verschijnt.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Editor-Publish.png)

4.

Voeg een titel en beschrijving toe en klik op de knop Opslaan . Het venster Asset Configuration  wordt bijgewerkt met een kopieerbare asset-ID.

 ![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Generate-Asset-ID-Success.png)

## [Maak een Animatie-object](#maak-een-animatie-object)[](#maak-een-animatie-object)

Om een emote naar de Marketplace te indienen, moet je een [Animation](/docs/nl-nl/reference/engine/classes/Animation) -object indienen met de eigenschap AnimationId  ingesteld op de asset-ID van je CurveAnimation -object.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Explorer.png) Animation -object in het Explorer-venster.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Properties.png) AnimationId -eigenschap in het eigenschappenvenster.

Om een [Animation](/docs/nl-nl/reference/engine/classes/Animation) -object te maken dat je als emote kunt publiceren:

1.

Voeg in het Explorer -venster een nieuw Animation -object toe.

2.

Voeg in het Eigenschappen -venster de asset-ID van je emote-animatie toe.

## [Emote uploaden naar Marketplace](#emote-uploaden-naar-marketplace)[](#emote-uploaden-naar-marketplace)

Wanneer je een [Animation](/docs/nl-nl/reference/engine/classes/Animation) -object hebt met de asset-ID van je emote-animatie ingesteld, kun je de emote naar de Marketplace uploaden. Dit proces vereist een [uploadvergoeding](/docs/nl-nl/marketplace/marketplace-fees-and-commissions#uploadkosten)  van 80 Robux .

1.

Klik met de rechtermuisknop op het Animation -object in het Explorer -venster en selecteer Opslaan naar Roblox . Het venster Asset Configuration  verschijnt.

2.

Configureer de volgende velden:

1.

Voeg een titel en beschrijving toe.

2.

Stel het Content Type  in op Avatar Item .

3.

Stel de Asset Category  in op Emote .

3.

Klik op de knop Indienen  om je asset voor moderatie te uploaden.

Voor meer informatie over het upload- en publicatieproces, zie [Publiceren naar Marketplace](/docs/nl-nl/marketplace/publish-to-marketplace#upload-een-activum) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
