<!-- Source: https://create.roblox.com/docs/nl-nl/art/characters/creating/remove-extra-bones -->

Verwijder extra botten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Verwijder extra botten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De helperbotten die worden gebruikt om de hoofdgeometrieën te plaatsen, moeten ook worden verwijderd om correct te valideren. Hoewel deze extra botten geen skinning-gegevens bevatten, moet je geen van de gezichtsanimatiebotten die binnen DynamicHead zijn gekoppeld, verwijderen, aangezien deze belangrijke skinning-gegevens bevatten die de gezichtsanimatie aansturen.

Het niet [samenvoegen van hoofdgeometrie](/docs/nl-nl/art/characters/creating/combine-head-geometry)  en het verwijderen van hoofd botten zal problemen veroorzaken met de validatie, aangezien het personage niet langer voldoet aan de standaard [geometrie](/docs/nl-nl/avatar/character-bodies/specifications#body-parts)  en [gewrichtshierarchie](/docs/nl-nl/avatar/character-bodies/specifications#rigging) .

Verwijder de extra hoofd botten door ze te selecteren en te verwijderen in de bewerkingsmodus:

1.

Als dat nodig is voor je sjabloon, schakel de zichtbaarheid van je Armature  object in. De botten worden weergegeven in de viewport.

2.

Breid in de Outliner het armature-object van het personage uit en zoek het Joints  object dat de botstructuur van het personage koppelt.

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Select-Joint-Objects.png)

3.

Breid de hiërarchie van het Joints  object uit door Shift  ingedrukt te houden en op de uitklapkeuzelijst te klikken.

4.

Selecteer in de viewport een bot en schakel over naar de Bewerken  modus.

5.

Houd onder het Head  gewricht Shift  ingedrukt en selecteer alle hoofdkindgewrichten behalve DynamicHead .

 ![](https://prod.docsiteassets.roblox.com/assets/art/avatar/basic-creation/Select-Bone-Objects.png)

6.

Met de extra hoofd botten geselecteerd, klik met de rechtermuisknop in de viewport en selecteer Verwijder Geselecteerde Botten  uit het contextmenu.

[Volgende](/docs/nl-nl/art/characters/creating/verify-attachments)[Vorige](/docs/nl-nl/art/characters/creating/combine-head-geometry)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
