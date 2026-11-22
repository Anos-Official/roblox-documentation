<!-- Source: https://create.roblox.com/docs/nl-nl/art/characters/creating/combine-head-geometry -->

Combineer hoofdgeometrie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Combineer hoofdgeometrie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Wanneer je klaar bent om je model te exporteren, is het belangrijk om je project op te schonen zodat je model klaar is voor export. Dit omvat de volgende taken die ervoor zorgen dat het aangepaste sjabloonmodel en alle avatarcomponenten succesvol in Studio kunnen worden geïmporteerd:

-

Het combineren van extra hoofdgeometrie

-

Het verwijderen van extra hoofdbeenderen

-

Het verifiëren van bevestigingspunten

-

Laatste technische controles

Het niet combineren van hoofdgeometrie en [verwijderen van hoofdbeenderen](/docs/nl-nl/art/characters/creating/remove-extra-bones)  zal problemen veroorzaken met de validatie, aangezien het personage niet langer voldoet aan de verwachte standaard [geometrie](/docs/nl-nl/avatar/character-bodies/specifications#lichaamsdelen)  en [gewrichtshierarchie](/docs/nl-nl/avatar/character-bodies/specifications#rigging) .

## [Combineer hoofdgeometrie](#combineer-hoofdgeometrie)[](#combineer-hoofdgeometrie)

Op dit punt moet je ook de aparte hoofd- en gezichtobjecten binnen het enkele Head_Geo  object combineren. Sommige sjablonen bevatten niet alle gezichtobjecten, zoals wimpers. Om de hoofd- en gezichtsmessen te combineren:

1.

Houd in de Outliner Ctrl / ⌘  ingedrukt en klik op de volgende objecten, eindigend met de Head_Geo :

-

UpperTeeth_Geo

-

LowerTeeth_Geo

-

Tongue_Geo

-

RightLash_Geo

-

RightEye_Geo

-

LeftLash_Geo

-

LeftEye_Geo

-

Head_Geo

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Template-Face-Objects.png)

Zorg ervoor dat de Head_Geo  geel is gemarkeerd wanneer je meerdere hoofdobjecten selecteert, wat aangeeft dat het het hoofdobject is waar de anderen in samensmelten. Dit behoudt correct de aangepaste eigenschappen die in het hoofdmesh zijn opgeslagen. Je kunt dit bereiken door het hoofd als laatste in de Outliner te selecteren.

2.

Terwijl je in Object -modus bent, klik met de rechtermuisknop in de viewport en selecteer Join  in het contextmenu. De objecten worden samengevoegd tot één Head_Geo  object.

[Volgende](/docs/nl-nl/art/characters/creating/remove-extra-bones)[Vorige](/docs/nl-nl/art/characters/creating/caging)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
