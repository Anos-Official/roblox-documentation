<!-- Source: https://create.roblox.com/docs/nl-nl/projects/place-files -->

Plaats bestanden | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Games and places](/docs/nl-nl/production/publishing/publish-games-and-places)

# Plaats bestanden

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Elk Roblox-spel bestaat uit een of meer [plaatsen](/docs/nl-nl/projects#plaatsen) , en Studio uploadt je plaatsgegevens naar de servers van Roblox telkens wanneer je opslaat of publiceert naar Roblox in het Bestand  menu.

Je wilt misschien ook lokale kopieën van plaatsen exporteren voor gebruik met een versiebeheersysteem of andere [externe tools](/docs/nl-nl/projects/external-tools) . Om je plaats in Studio te exporteren, selecteer je Opslaan als Bestand  of Download een Kopie  in het Bestand  menu. Studio biedt twee bestandsformaten aan:

-

.rbxl  is het binaire plaatsbestandsformaat. Dit formaat is compact, maar niet leesbaar voor mensen.

-

.rbxlx  is het op XML gebaseerde plaatsbestandsformaat, dat aanzienlijk groter op schijf is dan het binaire formaat.

Roblox ondersteunt plaatsen tot 100 MB (104.857.600 bytes). Boven deze limiet kunnen Opslaan naar Roblox  en Publiceren naar Roblox  mislukken. De gegevens die Studio naar Roblox uploadt, zijn iets kleiner dan het .rbxl -bestandsformaat, dus je kunt je plaats exporteren naar .rbxl  om een idee van de grootte te krijgen.

Zeer weinig plaatsen, zelfs de meest complexe, bereiken deze limiet, en wanneer ze dat doen, is het vaak te wijten aan inefficiënties in de plaats. Zie [Probleemoplossing](/docs/nl-nl/projects/place-files#troubleshoot-place-file-size) .

## [Auto-herstelbestanden](#auto-herstelbestanden)[](#auto-herstelbestanden)

Als het opslaan naar Roblox mislukt vanwege de bestandsgrootte limiet, genereert Studio automatisch een back-up van je plaats genaamd een herstelbestand . De frequentie van auto-herstelback-ups hangt af van of je spel [samenwerking](/docs/nl-nl/projects/collaboration)  heeft ingeschakeld:

-

Als je samenwerking hebt ingeschakeld en het opslaan naar Roblox mislukt, maakt Studio een back-up van de laatste drie opslaanpogingen als herstelbestanden op je systeem.

-

Als samenwerking is uitgeschakeld, gebruikt Studio de Auto-Herstel  instellingen van [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing) .

Op Windows bevinden herstelbestanden zich in C:\Users\Admin\AppData\Local\Roblox\RobloxStudio\AutoSaves .

Op Mac kun je ze vinden in /Users/je-gebruikersnaam/Library/Application Support/Roblox/RobloxStudio/AutoSaves/ .

## [Probleemoplossing bestandsgrootte](#probleemoplossing-bestandsgrootte)[](#probleemoplossing-bestandsgrootte)

Als je de limiet van 100 MB op je plaatsbestand bereikt, is er waarschijnlijk een onderliggend probleem dat je kunt oplossen. Probeer de volgende stappen.

### [Veiligheidscontrole](#veiligheidscontrole)[](#veiligheidscontrole)

Controleer de modellen in je plaats en hun bijbehorende scripts op obfuscated of onduidelijke tekst. Deze tekst comprimeert niet goed en kan zelfs een kwaadaardige achterdeur in je plaats zijn. De moderatiesystemen van Roblox filteren deze modellen actief, maar als je er een tegenkomt, verwijder het model dan uit je plaats, zoek het model in de [Creator Store](https://create.roblox.com/store/models) , en rapporteer het onmiddellijk.

### [Overbodige onderdelen](#overbodige-onderdelen)[](#overbodige-onderdelen)

Ongeadresseerde of verborgen middelen kunnen in de loop van de tijd accumuleren en onnodig de bestandsgrootte vergroten.

1.

Kijk of er modellen of groepen onderdelen zijn die meer ruimte innemen dan andere:

1.

Exporteer je plaatsbestand en noteer de grootte op schijf.

2.

Open het bestand in Roblox Studio.

3.

Kopieer en plak de modellen of groepen onderdelen waarvan je vermoedt dat ze onterecht groot zijn.

4.

Sla het bestand opnieuw op en noteer de toename in bestandsgrootte.

2.

Controleer op overbodige onderdelen (onderdelen van dezelfde grootte en vorm met dezelfde positie) of instanties (overbodige [SurfaceAppearances](/docs/nl-nl/reference/engine/classes/SurfaceAppearance) , texturen, enz.) en verwijder ze. De Creator Store heeft plugins die je kunnen helpen deze gevallen te identificeren.

### [Vereenvoudig terrein](#vereenvoudig-terrein)[](#vereenvoudig-terrein)

Het verminderen of vereenvoudigen van terrein kan de plaatsgrootte aanzienlijk verminderen en de prestaties verbeteren. Het vermijden van overmatige terreineigenschappen zoals dichte bossen of complexe heuvels helpt om spellen sneller en efficiënter te laten draaien. Natuurlijk moet het spel overeenkomen met je artistieke visie, maar overweeg de volgende optimalisaties:

1.

Horizontale lagen van hetzelfde materiaal/bezetting comprimeren veel beter dan hellende lagen. Probeer, indien mogelijk, de ondergrondse details te beperken tot horizontale lagen.

2.

Zet Toon Draadmodel Rendering  aan vanuit het Weergave  menu van Studio en controleer op rommelige gaten of verkeerd geplaatste water onder het terreinoppervlak. Deze fouten kunnen de gecomprimeerde grootte vergroten.

3.

Er zijn community-plugins die niet-zichtbare blokken terrein optimaliseren voor betere compressie, zoals [deze](https://create.roblox.com/store/asset/133396894381603/Terrain-File-Size-Optimizer) .

### [Botsingsnauwkeurigheid](#botsingsnauwkeurigheid)[](#botsingsnauwkeurigheid)

[Box](/docs/nl-nl/reference/engine/enums/CollisionFidelity#Box)  en [Hull](/docs/nl-nl/reference/engine/enums/CollisionFidelity#Hull)  botsingsnauwkeurigheid zijn geheugen efficiënter dan de standaard. Selecteer je meshes, open het [Eigenschappen](/docs/nl-nl/studio/properties)  venster, en wijzig de CollisionFidelity  waarden zoals passend voor jouw gebruiksdoel.

### [Teleportaties](#teleportaties)[](#teleportaties)

Als andere strategieën voor het verminderen van de grootte falen, kun je je plaats opsplitsen in meerdere, kleinere plaatsen en ze met elkaar verbinden via [teleportaties](/docs/nl-nl/projects/teleport) . Serialisatie en uploaden gebeuren op het plaatsniveau, dus deze aanpak stelt je in staat om je universum plaats voor plaats in de loop van de tijd uit te breiden in plaats van te proberen een enkele, enorme plaats te onderhouden.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
