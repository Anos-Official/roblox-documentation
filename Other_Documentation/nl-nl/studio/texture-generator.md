<!-- Source: https://create.roblox.com/docs/nl-nl/studio/texture-generator -->

Textuurgenerator | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)

# Textuurgenerator

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Textuurgenerator -tool is ontworpen om snel aangepaste texturen voor je meshes te creëren via tekst- of afbeeldingsprompts. Je kunt een mesh of [Model](/docs/nl-nl/reference/engine/classes/Model)  selecteren die uit verschillende meshes bestaat¹, de uitstraling beschrijven die je wilt, resultaten binnen enkele seconden bekijken en vervolgens een volledige textuur genereren.

Er zijn twee generatiemodi beschikbaar, afhankelijk van je behoeften:

-

Snelle  modus produceert een snelle 1K diffuse textuur, ideaal voor snelle iteratie.

-

Kwaliteit  modus genereert een 4K fysiek gebaseerde rendering (PBR) textuur wanneer je een hogere nauwkeurigheid wilt en iets langer kunt wachten.

![Zij-aan-zij Fast en Quality bloemige gitaartexturen](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_1v2_flower_guitar.jpg) Bloemige textuur — Snelle  (links) vs Kwaliteit  (rechts)

![Zij-aan-zij Fast en Quality houtnerf gitaartexturen](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_1v2_wooden_guitar.jpg) Houtnerf — Snelle  (links) vs Kwaliteit  (rechts)

![Zij-aan-zij Fast en Quality roestige gitaartexturen](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_1v2_rusted_guitar.jpg) Roestig metaal — Snelle  (links) vs Kwaliteit  (rechts)

![Zij-aan-zij Fast en Quality tijgerstreep gitaartexturen](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_1v2_tiger_guitar.jpg) Tijgerstreep — Snelle  (links) vs Kwaliteit  (rechts)

Textuurgenerator  is het beste geschikt voor aangepaste 3D-assets waarbij de gewenste textuur contextueel is voor de asset zelf. Om herhalende of betegelde afbeeldingen te genereren voor het textureren van oppervlakken zoals een houten vloer of een kinderpaden, kan de [Materiaalgenerator](/docs/nl-nl/studio/material-generator)  betere resultaten opleveren.

 1  Bij het genereren van een textuur voor een [Model](/docs/nl-nl/reference/engine/classes/Model) -groep van [MeshParts](/docs/nl-nl/reference/engine/classes/MeshPart) , moeten de meshes op een logische manier worden gerangschikt zodat er een verenigd lichaam wordt gevormd. Vermijd het genereren van een textuur voor een willekeurige groep meshes die verspreid zijn over de grenzen van het model, of voor meer dan één identieke mesh in dezelfde bewerking.

## [Genereer texturen](#genereer-texturen)[](#genereer-texturen)

Je kunt texturen genereren via de Studio-tool, via Assistant met het [/generate_texture -commando](/docs/nl-nl/assistant/guide) , of via [Roblox Studio MCP](/docs/nl-nl/studio/mcp) .

Om de Studio-tool te gebruiken:

1.

Selecteer in Studio een mesh in je scène. De Textuurgenerator is alleen beschikbaar wanneer een mesh is geselecteerd.

2.

Ga naar het tabblad Model  en selecteer Textuur . De tool opent in een pop-upvenster naast de geselecteerde mesh.

 ![Textuurgeneratortool geopend naast een ongetextureerde gitaarmesh](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/untextured_guitar_texture_tool_open.jpg)

3.

Kies in het pop-upvenster van de tool een van de twee manieren om de textuur die je wilt te beschrijven:

-

Tekstprompt : Voer een tekstbeschrijving in het tekstvak in.

-

Afbeeldingsprompt : Klik op de +  knop om een referentieafbeelding te uploaden.

 ![Textuurgeneratie promptvenster met een tekstvak, plusknop en Preview-knop](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_tool_initial_window.jpg)

4.

OPTIONEEL

 Voordat je op Preview  klikt, open je het ⋯  menu en selecteer je Weergave , kies vervolgens hoe de tool de previeworiëntatie instelt:

 ![Weergave selectie menu met Automatisch en Handmatig opties](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texturing_tool_view_selection_mode.jpg)

-

Handmatig : De kijkhoek in de Studio viewport definieert de meshoriëntatie voor de previewafbeeldingen. Draai om de mesh om je voorkeurweergave te kiezen voordat je op Preview  klikt.

-

Automatisch : De tool gebruikt een slim algoritme om een previeworiëntatie te kiezen zonder gebruikersinvoer. Dit algoritme vindt een weergave die de meest relevante delen van de mesh blootlegt, hoewel het kan falen.

5.

Klik op Preview  om textuurvoorbeelden te maken. De tool retourneert drie previewafbeeldingen in ongeveer 10 seconden.

 ![Drie textuurvoorbeelden, met de zwevende preview vergroot](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texturing_tool_preview_selection.jpg)

Het opnieuw genereren van previews met dezelfde prompt kan iets andere resultaten opleveren. Het verfijnen van de prompt is meestal de gemakkelijkste manier om een betekenisvol andere set afbeeldingen te krijgen.

6.

Kies uit de dropdown in het previewvenster een generatiemodus:

-

Snelle  modus genereert een 1K diffuse textuur in minder dan 30 seconden. Gebruik Snelle  voor snelle prototyping, achtergrondassets en eenvoudige assets die geen scherpe details nodig hebben.

-

Kwaliteit  modus genereert een 4K PBR textuur met scherpere details. Generatie kan een paar minuten duren, en omdat de textuur scherper is, kunnen kleine generatie-artifacten ook gemakkelijker zichtbaar zijn.

7.

Wanneer je tevreden bent met de preview, klik je op Genereren  om de volledige textuur voor je mesh te maken. Je kunt doorgaan met het werken aan andere delen van je ervaring terwijl de generatie loopt, inclusief het textureren van andere assets tegelijkertijd.

Wijzig de asset niet ter plaatse terwijl de textuurgeneratie aan de gang is. Het bewerken ervan voordat de generatie is voltooid, kan ervoor zorgen dat het proces mislukt.

Wanneer de generatie is voltooid:

-

Snelle  modus past de textuur direct toe op de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  door een nieuwe textuur-ID toe te voegen.

-

Kwaliteit  modus past de PBR-textuur toe via een [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  die aan de [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  is gekoppeld.

Als de asset meerdere afzonderlijke [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart) -objecten bevat, krijgt elk zijn eigen textuur. In Kwaliteit  modus krijgt elke [MeshPart](/docs/nl-nl/reference/engine/classes/MeshPart)  ook zijn eigen [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) .

Als je niet tevreden bent met het uiteindelijke getextureerde resultaat, druk dan op Ctrl / Cmd  + Z  om ongedaan te maken. Dit kan ingewikkelder worden als je ook aan andere delen van je scène werkt terwijl het textureren aan de gang is, dus overweeg om je assets te back-uppen voordat je deze tool gebruikt.

### [Vergelijk generatiemodi](#vergelijk-generatiemodi)[](#vergelijk-generatiemodi)

Van veraf kunnen de resultaten van Snelle  en Kwaliteit  er vergelijkbaar uitzien. Van dichtbij tonen de 4K PBR-texturen van Kwaliteit  modus echter scherpere materiaaldetails, duidelijkere patronen en meer oppervlaktevariatie dan de 1K diffuse texturen van Snelle  modus.

Bloemig patroon close-up:

![Close-up van een Fast modus bloemige gitaartextuur](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_closeup_flower_fast.jpg) Snelle

![Close-up van een Quality modus bloemige gitaartextuur](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_closeup_flower_quality.jpg) Kwaliteit

Roestig patroon close-up:

![Close-up van een Fast modus roestige gitaartextuur](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_closeup_rusted_fast.jpg) Snelle

![Close-up van een Quality modus roestige gitaartextuur](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_closeup_rusted_quality.jpg) Kwaliteit

## [Prompting tips](#prompting-tips)[](#prompting-tips)

De volgende tips helpen de tool om betere en consistentere resultaten te leveren.

### [Tekstprompts](#tekstprompts)[](#tekstprompts)

Geef zoveel mogelijk detail in je prompt. Korte, vage prompts kunnen leiden tot inconsistente of onverwachte resultaten. Vermeld textuureigenschappen zoals materiaaltype, kleuren, patronen en andere kenmerkende eigenschappen.

Hoe meer beperkingen je de tool geeft, hoe beter deze kan genereren wat je in gedachten hebt.

Voorbeelden van eenvoudige en gedetailleerde prompts:

-

Eenvoudige prompt:  maak het van hout

-

Gedetailleerde prompt:  Akoestische gitaar gemaakt van diep roodbruin kersenhout met realistische houtnerf, een diepblauwe toets, gouden stemknoppen en een luipaardprint plectrumhouder.

![Zij-aan-zij resultaten van een eenvoudige houtprompt en een zeer gedetailleerde gitaarprompt](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_2_simple_v_detailed_prompt.jpg) Eenvoudige prompt  vs Gedetailleerde prompt

Het systeem verbetert automatisch eenvoudige prompts met extra details van zijn eigen keuze, zodat je meer of minder tijd kunt besteden aan het schrijven van je prompts. Je kunt ook beginnen met een eenvoudige prompt, de previewafbeeldingen evalueren en vervolgens de prompt verfijnen totdat je een resultaat bereikt dat je bevalt.

Vermijd het volgende bij het schrijven van een prompt:

-

Het wijzigen van de mesh-geometrie

-

Verwijzen naar de huidige textuur op de mesh

-

Verwijzen naar objecten of terrein in andere delen van de scène

-

Verwijzen naar eerder gegenereerde texturen

-

Het beschrijven van de reflectiviteit of transparantie-eigenschappen van de textuur

### [Afbeeldingsprompts](#afbeeldingsprompts)[](#afbeeldingsprompts)

Wanneer je een afbeeldingsprompt geeft, behandelt de textuurgeneratietool deze als een stijlgids in plaats van een exact sjabloon. De gegenereerde textuur haalt inspiratie uit de referentieafbeelding, maar behoudt mogelijk niet elk detail.

![Afbeeldingsprompt: een gitaar geschilderd met een draak, een samoerai en rode esdoornbladeren](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/style_guidance_japanese_guitar.jpg) Afbeeldingsprompt

![Gitaarmesh met een gegenereerde textuur van draken, samoerai en rode esdoornbladeren](https://prod.docsiteassets.roblox.com/assets/studio/texture-generator/texture_2_japanese_guitar.jpg) Gegenereerde textuur

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
