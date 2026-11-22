<!-- Source: https://create.roblox.com/docs/nl-nl/art/accessories/validation-tool -->

Gelaagde Accessoire Validatietool | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Meer informatie](/docs/nl-nl/learn)

# Gelaagde Accessoire Validatietool

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Gelaagde Accessoire Validatietool  is een aanvullend hulpmiddel dat je kunt installeren in [Blender](https://www.blender.org/download/releases/3-0/)  of [Maya](https://www.autodesk.com/products/maya/overview)  om snel veelvoorkomende problemen met gelaagde accessoires te identificeren en op te lossen voordat je ze [exporteert](/docs/nl-nl/avatar/layered-accessories/export) .

![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Blender-Validation-Tool.png) Blender Validatietool

![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Maya-Validation-Tool-Opened.png) Maya Validatietool

Hoewel dit hulpmiddel je tijd kan besparen in het typische iteratieproces tussen je 3D-modelleringsprogramma en Studio, biedt het hulpmiddel geen uitgebreide verificatie van alle aspecten van gelaagde accessoire-assets. Je moet ervoor zorgen dat je gelaagde accessoiremodel voldoet aan zowel de [algemene meshvereisten](/docs/nl-nl/art/modeling/specifications)  als de Roblox-specifieke [specificaties voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications)  voordat je het in Studio importeert.

## [Installeer het hulpmiddel](#installeer-het-hulpmiddel)[](#installeer-het-hulpmiddel)

Er zijn twee aparte installatiebestanden en instructies voor Blender en Maya.

De Gelaagde Accessoire Validatietool is ontworpen voor zowel [Blender 3.0](https://www.blender.org/download/releases/3-0/)  als [Maya 2022](https://www.autodesk.com/products/maya/overview) . Je kunt het hulpmiddel downloaden en aanpassen voor elk gebruik.

### [Blender](#blender)[](#blender)

Om de Gelaagde Accessoire Validatietool in Blender te installeren:

1.

Download [ValidationTool_Blender.zip](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/ValidationTool_Blender.zip)  en sla het .zip -bestand lokaal op.

2.

Ga in Blender naar Bewerken  > Voorkeuren .

3.

Ga in Voorkeuren naar de sectie Add-Ons  in de linker zijbalk.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Blender-Add-On-Preferences.png)

4.

Klik op de knop Installeren... . Een bestandsbrowser wordt weergegeven.

5.

Selecteer het gedownloade .zip -bestand en klik op Add-On Installeren .

6.

Zoek in de Add-Ons sectie  de Validatietool  en schakel de add-on in .

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Blender-Enable-Add-On.png)

7.

Ga terug naar je werkruimte en vouw de zijbalk uit  in de Viewport om toegang te krijgen tot de add-on.

![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Blender-Sidebar-Indicator.png) Zijbalkindicator

![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Blender-Validation-Tool-Opened.png) Uitgevouwen zijbalk

### [Maya](#maya)[](#maya)

Voordat je begint met het installeren van de Gelaagde Accessoire Validatietool in Maya, moet je [Python 3.0](https://www.python.org/downloads/)  of hoger installeren. Als je al Python hebt geïnstalleerd, kun je doorgaan met het installeren van het hulpmiddel.

Om de Gelaagde Accessoire Validatietool in Maya te installeren:

1.

Installeer Python 3.0+ op je apparaat.

1.

Download de juiste installer van de officiële [Python-website](https://www.python.org/downloads/) .

2.

Open de installer en volg de installatie-instructies.

-

Schakel Voeg Python ### toe aan PATH  in voordat je Nu installeren  selecteert.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Maya-Install-Python-Settings.png)

2.

Download [ValidationTool_Maya.zip](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/ValidationTool_Maya.zip)  en unzip de inhoud in een lokale directory.

3.

Open de inhoud van het .zip -bestand in een bestandsbrowser.

-

Als je Windows gebruikt, dubbelklik  op install.bat . Dit voert een batchscript uit waarmee je de Validatietool snel in Maya kunt uitvoeren.

-

Als je Mac gebruikt, klik met de rechtermuisknop  op het install.command -bestand en selecteer Openen met  > Terminal . Dit voert een terminalscript uit waarmee je de Validatietool snel in Maya kunt uitvoeren.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Mac-Right-Click-Install.png)

Als je Mac gebruikt, moet je mogelijk de lees-/schrijfrechten voor het install.command -bestand aanpassen om het succesvol uit te voeren. Deze stap vereist beheerdersrechten.

Om het install.command -bestand volledige lees- en schrijfrechten te geven:

1.

Open terminal  en gebruik de cd -opdracht om naar de directory van het opgeslagen install.command -bestand te navigeren.

2.

Typ de opdracht chmod 777 install.command  en druk op Enter . Dit zou alle lees- en schrijfrechten voor dit bestand moeten inschakelen.

4.

Wanneer je wordt gevraagd, typ je je Maya-versie en druk je op Enter . Bijvoorbeeld, als je Maya 2020 gebruikt, voer je 2020  in als je versie.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Maya-Install-Prompt-1.png)

5.

Wanneer de installatie succesvol is, verschijnt het volgende bericht:

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Maya-Command-Prompt-Success.png)

6.

Open Maya en ga naar Vensters  > Algemene editors  > Scripteditor .

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Maya-Script-Editor-Menu.png)

7.

Wanneer je de plugin voor de eerste keer gebruikt, typ je in de Scripteditor import ValidationTool  en druk je op de Afspelen -knop in de bovenste balk van de Scripteditor. De plugin UI wordt weergegeven.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Maya-Script-Editor.png)

-

Wanneer je de plugin na de eerste lancering gebruikt, start je de plugin door ValidationTool.validationTool()  te typen en op de Afspelen -knop te klikken.

-

Alternatief kun je een snelkoppeling instellen vanuit de plugin UI na de eerste lancering door op de knop Snelkoppeling maken op de Maya-shelf  te klikken.

 ![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Maya-Shortcut.png)

## [Valideer assets](#valideer-assets)[](#valideer-assets)

Met de plugin actief en een gelaagde accessoire asset in je werkruimte, kun je beginnen met het valideren van de inhoud. Na de controle veranderen resultaten met problemen in rood  (Blender) of geel  (Maya). Sommige mislukte controles kunnen worden opgelost door op de controleknop te klikken. Zie [Controles en probleemoplossingsstappen](#controles-en-probleemoplossingsstappen)  voor details over elke validatiecontrole.

![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Blender-Failed-Check-Example.png) Controles zonder problemen worden weergegeven als grijs (Blender) of groen (Maya).

![](https://prod.docsiteassets.roblox.com/assets/accessories/validation-tool/Blender-Failed-Check-Viewport.png) In dit voorbeeld worden potentiële intersectieproblemen gemarkeerd in de Viewport.

Om de Gelaagde Accessoire Validatietool op je asset te gebruiken:

1.

Selecteer  het object in je scène.

2.

Open de Validatietool en klik op Controleer Assets . Na een paar momenten wordt de UI bijgewerkt en verschijnt er een uitvoerbericht.

3.

Resultaten met problemen worden gemarkeerd met rood of geel. Sommige problemen kunnen automatisch worden gecorrigeerd door op de gemarkeerde knop te klikken.

De Gelaagde Accessoire Validatietool controleert alleen op veelvoorkomende problemen bij het maken van gelaagde accessoires. Zorg ervoor dat je gelaagde accessoiremodel voldoet aan zowel de [algemene mesh-specificaties](/docs/nl-nl/art/modeling/specifications)  als de Roblox-specifieke [specificaties voor gelaagde accessoires](/docs/nl-nl/avatar/layered-accessories/specifications)  voordat je het uploadt naar Studio.

## [Controles en probleemoplossingsstappen](#controles-en-probleemoplossingsstappen)[](#controles-en-probleemoplossingsstappen)

Raadpleeg de onderstaande tabel voor details over de specifieke controles en probleemoplossingsstappen:

Lagen

Controleert op extra lagen in de scène. Automatische fix probeert extra lagen te verwijderen.

Als de automatische fix mislukt, verwijder dan handmatig extra lagen.

Transformaties

Controleert of de locatie, rotatie en schaal van de geometrie zijn bevroren (0 , 0 , 0 ). Automatische fix probeert de transformaties te bevriezen. Dit kan veranderingen in je rig veroorzaken.

Als de automatische fix mislukt, bevries dan handmatig je geometrie.

Ongebruikte Materiaal

Controleert op ongebruikte gegevens in de scène, zoals [weesgegevens](https://docs.blender.org/manual/en/latest/editors/outliner/interface.html?highlight=orphan)  (Blender) of [constructiegeschiedenis](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2022/ENU/Maya-Basics/files/GUID-503E227B-EF49-4A78-B3CA-7EAC588017C9-htm.html)  (Maya), of ongebruikte materialen. Automatische fix probeert extra gegevens te verwijderen.

Als de automatische fix mislukt, verwijder dan handmatig onnodige gegevens en objecten.

Sleutelframes

Controleert op onnodige sleutelframes. Automatische fix probeert sleutelframes te verwijderen.

 Als de automatische fix mislukt, verwijder dan handmatig sleutelframegegevens.

Bevestigingspunten

Controleert of bevestigingspunten aanwezig zijn en de juiste naamgevingsconventie gebruiken. Automatische fix probeert onverwachte bevestigingspunten te koppelen.

Intersectie

Controleert op intersectie tussen karaktergeometrie en de binnen/buiten kooi mesh geometrie. In Blender schakelt het klikken op de knop over naar Bewerkmodus  en markeert het de vertices die de binnenste of buitenste mesh snijden.

Sommige randen, zoals de randen van de gaten voor de mouwen, nek en torso-randen, kunnen standaardgedrag gemarkeerd zijn en kunnen worden genegeerd.

Textuurformaat

Controleert of texturen voldoen aan de textuureisen, zoals resolutiegrootte. Gebruikers kunnen ook een extern afbeeldingsbestand selecteren. Raadpleeg de uitvoerberichten om eventuele textuurgerelateerde problemen handmatig op te lossen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
