<!-- Source: https://create.roblox.com/docs/nl-nl/projects/assets/toolbox -->

Toolbox | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. [Beheren](/docs/nl-nl/projects/assets/manager)

# Toolbox

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Toolbox , toegankelijk vanuit het Venster  menu of de Start  tabblad werkbalk, bevat een selectie van [modellen](/docs/nl-nl/parts/models) , [afbeeldingen](/docs/nl-nl/parts/textures-decals) , [mesh](/docs/nl-nl/parts/meshes) , [audio](/docs/nl-nl/audio/assets) , [plugins](/docs/nl-nl/studio/plugins) , [video's](/docs/nl-nl/ui/video-frames)  en lettertypen gemaakt door Roblox of leden van de Roblox-gemeenschap. Het bevat ook al je creaties die je persoonlijk hebt gepubliceerd of die zijn gepubliceerd door [groepen](/docs/nl-nl/projects/groups)  waartoe je behoort.

 ![Toolbox gemarkeerd in de werkbalk van Studio.](https://prod.docsiteassets.roblox.com/assets/studio/general/Toolbar-Toolbox.png)

De toolbox bevat vier verschillende secties:

Creator Store Inventory Recent Creations

![Een close-up van de Toolbox met het Creator Store-tabblad gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Creator-Store-Tab.png)

De Creator Store  sectie bevat modellen, decals, meshes, audio, plugins, video's en lettertypen gemaakt door Roblox of leden van de Roblox-gemeenschap. Zie [Creator Store](/docs/nl-nl/production/creator-store)  voor meer informatie.

## [Vind en gebruik assets](#vind-en-gebruik-assets)[](#vind-en-gebruik-assets)

Met miljoenen beschikbare assets is het nuttig om de zoekresultaten te verfijnen om precies te vinden wat je zoekt. Om assets te doorbladeren en te gebruiken:

1.

Klik in de linkerbovenhoek op de dropdown voor de categorie-selector en kies een activacategorie. Klik optioneel op de knop geavanceerd filter  om resultaten te filteren op [geverifieerde maker](/docs/nl-nl/production/publishing/account-verification)  status, een specifieke maker, de verkoopprijs voor [plugins](/docs/nl-nl/studio/plugins)  en de bestandsgrootte voor [audio-activa](/docs/nl-nl/audio/assets) .

![Het Toolbox-venster met de categorie-selector gemarkeerd](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Creator-Store-Category-Selector.png)

![Het Toolbox-venster met het geavanceerde filter gemarkeerd](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Creator-Store-Advanced-Filter.png)

2.

Typ in het zoekveld wat je wilt vinden en druk op Enter . De weergave stelt een selectie van activa samen op basis van je zoekopdracht.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Model-Search-Example.png)

3.

OPTIONEEL

 Beweeg de muis over een miniatuur van een activum en klik op het vergrootglasicoon om de communitybeoordeling, beschrijving en meer van het activum nauwkeurig te inspecteren.

 ![Een voorbeeldweergave van een activum met het inspectie-icoon gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Asset-Inspect-Icon.png)

4.

Om een activum aan een spel toe te voegen:

-

Als het activum een [model](/docs/nl-nl/parts/models) , [mesh](/docs/nl-nl/parts/meshes) , [decal](/docs/nl-nl/parts/textures-decals) , [video](/docs/nl-nl/ui/video-frames)  of [audio](/docs/nl-nl/audio/assets)  activum is, klik erop of sleep het naar de 3D-weergave. Het wordt dan ingevoegd in de [Explorer](/docs/nl-nl/studio/explorer)  hiërarchie, en activa met 3D-inhoud worden weergegeven in de weergave.

-

Als het activum een [plugin](/docs/nl-nl/studio/plugins)  is, klik erop en gebruik de knop Installeren  om het toe te voegen aan het Plugins -tabblad van de mezzanine.

-

Als het activum een lettertype is, klik erop en gebruik de knop Installeren  om het toe te voegen aan je lettertypebibliotheek. Het wordt dan beschikbaar voor gebruikersinterface-elementen zoals [tekstlabels](/docs/nl-nl/ui/labels)  of [knoppen](/docs/nl-nl/ui/buttons) .

Sommige activa bevatten scripts die specifieke acties uitvoeren, zoals animeren tijdens runtime of het activeren van een geluid. Als je een activum wilt gebruiken zonder dat een van de scripts wordt uitgevoerd, klik dan met de rechtermuisknop op het object in het [Explorer](/docs/nl-nl/studio/explorer)  venster en selecteer Scripts Uitschakelen  in het contextmenu.

## [Assetconfiguratie](#assetconfiguratie)[](#assetconfiguratie)

Met de rechtermuisknop op een asset klikken en Bewerk Asset  selecteren opent het Assetconfiguratie  venster. In dit venster kun je de details van de asset bewerken of deze herstellen naar een vorige versie.

Assetconfiguratie is alleen mogelijk voor assets die je persoonlijk hebt gepubliceerd of die zijn gepubliceerd door [groepen](/docs/nl-nl/projects/groups)  waartoe je behoort. Het Creations  tabblad is bijzonder nuttig voor het filteren van assets op deze manier.

## [Probleemoplossing](#probleemoplossing)[](#probleemoplossing)

De toolbox draait via een webweergave. Als je een van de volgende problemen ondervindt, volg dan de bijbehorende probleemoplossingsstappen.

Algemene Problemen

Zorg ervoor dat er geen actieve instanties van Roblox Studio draaien voordat je deze stappen uitvoert.

| Windows |
| --- | --- |
|

1.

[Herinstalleer](https://developer.microsoft.com/en-us/microsoft-edge/webview2/)  je Windows WebView2-installatie.

2.

Verwijder de WebView2-gegevensmap die te vinden is op %LOCALAPPDATA%\Roblox\RobloxStudio\WebView2 . Studio zal deze map automatisch opnieuw aanmaken wanneer het opent.

 |
| Mac |
| Verwijder de WebKit-gegevensmappen die te vinden zijn op ~/Library/WebKit/com.Roblox.RobloxStudio  en ~/Library/Caches/com.Roblox.RobloxStudio/WebKit . Studio zal deze mappen automatisch opnieuw aanmaken wanneer het opent. |

Audio Werkt Niet

| Windows |
|

1.

Klik met de rechtermuisknop op het luidsprekericoon in de taakbalk.

2.

Klik op Open Volume Mixer .

3.

Zorg ervoor dat Microsoft Edge WebView2  niet is gedempt.

 |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
