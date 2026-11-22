<!-- Source: https://create.roblox.com/docs/nl-nl/art/accessories/creating-rigid/texturing -->

Textuur schilderen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Textuur schilderen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

![Een screenshot van Blender die de uiteindelijke 3D-vorm en kleur van een schatkist in de viewport toont](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/Texturing-Complete.png)

Textureren  is het proces van het aanbrengen van een oppervlakte-uiterlijk op een 3D-object. Textuur schilderen  is een techniek waarmee je digitaal je oppervlaktekleuren op je 3D-object of op de 2D-afbeelding die het oppervlak van je object vertegenwoordigt, kunt schilderen.

Deze tutorial behandelt basis textuur schilderen in Blender. Veelvoorkomende workflows in de industrie maken gebruik van aanvullende tools van derden om texturen te creëren, vooral high-definition PBR-texturen die realistische verlichting en textuureigenschappen nabootsen.

Hoewel PBR-texturen niet vereist zijn voor accessoires en niet in deze tutorial worden behandeld, kan het toevoegen van PBR-texturen extra visuele flair en realisme toevoegen om je creaties te verbeteren. Dit vereist doorgaans extra software.

 Voor meer informatie, zie [PBR-texturen](/docs/nl-nl/art/modeling/surface-appearance) .

## [UV-projectie](#uv-projectie)[](#uv-projectie)

Gebruik de automatische UV-projectfunctie van Blender om je 3D-object "uit te pakken" op een 2D-vlak. Dit stelt je in staat om een 2D-afbeelding aan het 3D-oppervlak van je object te koppelen.

1.

In Bewerken -modus, druk op A  om je object te selecteren.

2.

Selecteer in het bovenste UV-menu Slimme UV-projectie .

3.

Stel Eilandmarge  in op .02 .

## [Nieuwe materiaal toevoegen](#nieuwe-materiaal-toevoegen)[](#nieuwe-materiaal-toevoegen)

Voeg een nieuw materiaal toe zodat Blender deze nieuwe textuur kan associëren en wijs het toe aan een nieuwe lege 2D-afbeelding.

1.

Selecteer in het Eigenschappen -paneel het tabblad Materialen .

2.

Selecteer de knop + Nieuw . Extra materiaalmogelijkheden worden hieronder weergegeven.

3.

Selecteer in Basis kleur  de stip en kies Afbeeldingstekstuur  uit het contextmenu.

4.

Onder Basis kleur , selecteer de knop + Nieuw .

1.

Geef het textuurafbeeldingsbestand een naam. Het gebruik van een affix zoals "_TXT" kan helpen om je bestanden later te organiseren.

2.

Selecteer de kleur en kies een kleur. Deze tutorial raadt aan om een metallic kleur voor je metalen randen te gebruiken om tijd te besparen.

## [Textuur schilderen](#textuur-schilderen)[](#textuur-schilderen)

Textuur schilderen stelt je in staat om direct op het 3D-object of de 2D-mapping van het oppervlak te schilderen.

Aangezien Blender automatisch de 2D-atlas van de textuur heeft gemapt, is het niet gemakkelijk te zien welke delen van de 2D-afbeelding overeenkomen met het 3D-object. Markeer eerst de secties van het 3D-object die je solide wilt schilderen voordat je je textuur voltooit door de 2D-kaart te schilderen.

Er zijn veel manieren om texturen binnen Blender aan te brengen. Om dit proces eenvoudig te houden, heeft de tutorial gebruik gemaakt van Blenders [Slimme UV-projectie](https://docs.blender.org/manual/en/2.79/editors/uv_image/uv/editing/unwrapping/mapping_types.html) , maar er zijn veel manieren om je 2D-textuur-eilanden handmatig te creëren en je mesh en textuur te organiseren.

### [Markeer 3D-object](#markeer-3d-object)[](#markeer-3d-object)

Schakel over naar de Textuur Schilderen-modus en gebruik de penseel om de "houten" delen van de schatkist te markeren.

1.

Selecteer in Bewerken -modus je object en schakel vervolgens over naar Textuur Schilderen -modus. Een zij-aan-zij paneel wordt weergegeven met je 2D-atlas aan de linkerkant en het 3D-object aan de rechterkant.

2.

Vouw het submenu Gereedschap  uit in de rechterbovenhoek van een van de vensters.

3.

Selecteer je penseelinstellingen en markeer de houten gebieden van je kist.

1.

Gebruik Ctrl Z / ⌘ Z  om onbedoelde penseelstreken op de metalen rand ongedaan te maken.

2.

Houd F  ingedrukt en sleep de muis om de penseelgrootte aan te passen.

### [Schilder 2D-kaart](#schilder-2d-kaart)[](#schilder-2d-kaart)

Met alle houten gebieden van je kist gemarkeerd, kun je nu snel je 2D-atlas textureren. Pas eerst je penseelinstellingen aan om een harde rand te hebben en begin vervolgens met het schilderen van de 2D-afbeelding.

1.

Vouw in het linkervenster het submenu Gereedschap  uit in de rechterbovenhoek.

1.

Stel de Afname -vorm in op het platste pictogram om ervoor te zorgen dat de randen scherp zijn.

2.

Stel de kleur of andere penseelinstellingen in.

2.

Begin met het inkleuren van elk eiland van je textuur. Je kunt de wijzigingen snel op je 3D-object aan de rechterkant bekijken.

1.

Gebruik Ctrl Z / ⌘ Z  om onbedoelde penseelstreken op de metalen rand ongedaan te maken.

2.

Houd F  ingedrukt en sleep de muis om de penseelgrootte aan te passen.

3.

Nadat je klaar bent, navigeer naar Afbeelding  > Opslaan  om je afbeeldingsbestand op te slaan.

Je hebt het textureren-gedeelte van deze tutorial voltooid. Indien gewenst, download een [referentieversie](https://prod.docsiteassets.roblox.com/assets/art/accessories/creating-rigid/Chest-Texturing-Complete.blend)  van deze fase van het project ter vergelijking.

[Volgende](/docs/nl-nl/art/accessories/creating-rigid/exporting)[Vorige](/docs/nl-nl/art/accessories/creating-rigid/modeling-setup)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
