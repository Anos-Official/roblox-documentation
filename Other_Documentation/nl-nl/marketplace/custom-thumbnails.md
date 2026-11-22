<!-- Source: https://create.roblox.com/docs/nl-nl/marketplace/custom-thumbnails -->

Aangepaste miniaturen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Marktplaats

# Aangepaste miniaturen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Miniatuurafbeeldingen bieden een preview van het 3D-item in de [Marktplaats](https://www.roblox.com/catalog) , gebruikersinventarissen en avatar-editors. Voordat je een [item naar de Marktplaats uploadt](/docs/nl-nl/marketplace/publish-to-marketplace) , kun je je eigen miniaturen maken om de exacte uitstraling en het gevoel van je itempreviewminiaturen aan te passen. Deze stap is optioneel, maar kan helpen ervoor te zorgen dat de miniatuur je item nauwkeurig weergeeft.

![](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Thumbnail-Example-A.png)

De standaardminiatuur vertegenwoordigt mogelijk je item niet correct.

![](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Thumbnail-Example-B.png)

Een aangepaste miniatuur kan een nauwkeurigere preview creëren.

### [Miniaturen maken](#miniaturen-maken)[](#miniaturen-maken)

Je moet miniaturen maken voordat je je [item op de Marktplaats publiceert](/docs/nl-nl/marketplace/publish-to-marketplace) . Je kunt deze miniatuurconfiguratie-instanties snel maken met de [Aangepaste Miniatuurtool](https://www.roblox.com/library/11628621048/UGC-Custom-Thumbnail-Tool) . Roblox slaat informatie over aangepaste miniaturen op in een kindobject ThumbnailConfiguration  dat een CameraTarget  en CameraValue  heeft.

 ![](https://prod.docsiteassets.roblox.com/assets/publishing/marketplace/Thumbnail-Configuration-Example.png)

Om de Aangepaste Miniatuurtool te gebruiken:

1.

Installeer de [Aangepaste Miniatuurtool-plugin](https://www.roblox.com/library/11628621048/UGC-Custom-Thumbnail-Tool) . Dit kan vereisen dat je Studio opnieuw opstart.

2.

Selecteer in het Explorer -venster de [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  waarvoor je een miniatuur wilt maken.

3.

Met de [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  gemarkeerd in het Explorer -venster, ga je naar het tabblad Plugins  en klik je op de UGC Miniatuurtool . De weergave in het viewport wordt bijgewerkt en gecentreerd op de geselecteerde accessoire in de werkruimte.

4.

Pas het viewport aan om op je accessoire te centreren. Gebruik de volgende bedieningselementen om de camera te navigeren:

-

W  A  S  D  om de camera te pannen.

-

Houd rechtermuisklik  ingedrukt om de camera te draaien.

-

Houd middenklik  ingedrukt om de camera te pannen.

-

Houd Shift  ingedrukt voor fijne aanpassing.

5.

Klik op Accepteren  om de miniatuurconfiguratieobjecten te genereren.

6.

Je kunt de miniatuur bekijken door met de rechtermuisknop op de accessoire in het Explorer -venster te klikken en Opslaan naar Roblox…  te selecteren. Het venster Assetconfiguratie  verschijnt en toont de huidige miniatuur.

Als je miniatuur er niet correct uitziet, herhaal stappen 2-5  om de bestaande miniatuurgegevens te overschrijven.

Zodra je een item uploadt, kun je de miniatuur van een item niet meer wijzigen of aanpassen.

### [Probleemoplossing miniaturen](#probleemoplossing-miniaturen)[](#probleemoplossing-miniaturen)

Als je miniaturen er niet uitzien zoals je verwacht, moet je mogelijk deze problemen handmatig oplossen of opnieuw proberen de Aangepaste Miniatuurtool te gebruiken. Zie het volgende voor veelvoorkomende problemen en oplossingen:

| Probleem | | Beschrijving |
| --- | --- |
| Onjuiste Miniatuurzoom | | De schaal van de miniatuur hangt af van de grootte van de Handle  van de [Accessory](/docs/nl-nl/reference/engine/classes/Accessory) . Voor de beste miniatuur, zorg ervoor dat je Handle  het hele item bedekt.
Wanneer je de grootte van het Handle -object wijzigt, pas dan de eigenschap Size  aan in plaats van de resize-tool te gebruiken. De resize-tool kan andere ongewenste wijzigingen aan het item veroorzaken.
 Je kunt dit probleem oplossen door de [Aangepaste Miniatuurtool](https://www.roblox.com/library/11628621048/UGC-Custom-Thumbnail-Tool)  te gebruiken. |
| Achterste Miniaturen | | Bij het importeren van meshes kan Studio de oriëntatie van het aangepaste model met 180° veranderen. Om dit op te lossen, kun je je mesh 180° draaien in je externe modelleertool, zoals Blender of Maya, en vervolgens het 3D-model opnieuw importeren in Studio.
Ongeacht de importoriëntatie, rust Studio de [Accessory](/docs/nl-nl/reference/engine/classes/Accessory)  uit op een karakter met dezelfde pasvorm en bevestiging. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
