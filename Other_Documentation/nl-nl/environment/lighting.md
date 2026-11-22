<!-- Source: https://create.roblox.com/docs/nl-nl/environment/lighting -->

Wereldwijde verlichting | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelomgeving](/docs/nl-nl/environment)

# Wereldwijde verlichting

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [Lighting](/docs/nl-nl/reference/engine/classes/Lighting) -service bevat eigenschappen die je kunt aanpassen om de wereldwijde verlichting in een spel bij te werken en aan te passen. Er zijn vijf categorieën van verlichtings eigenschappen:

-

[Kleur](#kleur)  — Configureert de tint binnen het spel.

-

[Intensiteit](#intensiteit)  — Configureert de intensiteit of hoeveelheid licht die de camera bereikt.

-

[Schaduwen](#schaduwen)  — Configureert hoe een gebruiker schaduwen binnen het spel ervaart.

-

[Uiterlijk](#uiterlijk)  — Eigenschappen die de verlichtingsstijl en de kwaliteit van verlichting/schaduw of prioriteit van zichtafstand bepalen.

-

[Omgeving](#omgeving)  — Configureert de omstandigheden van de spelwereld, zoals het tijdstip van de dag en geografische breedte.

## [Kleur](#kleur)[](#kleur)

### [Ambient](#ambient)[](#ambient)

De [Ambient](/docs/nl-nl/reference/engine/classes/Lighting#Ambient) -eigenschap stelt een tint in voor de hele  game. Deze eigenschap beïnvloedt de verlichting voor zowel buiten- als binnenomgevingen.

[0, 0, 0] [160, 80, 0] [25, 0, 125]

![Lighting.Ambient eigenschap van [0, 0, 0]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/Ambient-0-0-0.jpg)

### [OutdoorAmbient](#outdoorambient)[](#outdoorambient)

De [OutdoorAmbient](/docs/nl-nl/reference/engine/classes/Lighting#OutdoorAmbient) -eigenschap stelt een tint in voor buitengebieden  van een game. Dit kan helpen om te simuleren hoe de ambientkleur van verlichting in het echte leven gedurende de dag verandert. Bijvoorbeeld, zonlicht in de vroege ochtend of late namiddag is meestal warmer en meer roze en oranje van toon, terwijl de late avond meestal koeler en meer blauw en paars van toon is.

Let in de volgende afbeeldingen op dat de verlichting binnen de garage en het café niet verandert zoals het zou doen als je de [Ambient](#ambient) -eigenschap zou veranderen.

[255, 150, 50] [200, 150, 240] [0, 175, 255]

![Lighting.OutdoorAmbient eigenschap van [255, 150, 50]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/OutdoorAmbient-255-150-50.jpg)

### [ColorShift_Top](#colorshift_top)[](#colorshift_top)

De [ColorShift_Top](/docs/nl-nl/reference/engine/classes/Lighting#ColorShift_Top) -eigenschap stelt een tint in die weerkaatst van oppervlakken die naar de zon of maan zijn gericht.

[0, 100, 255] [255, 60, 0]

![Lighting.ColorShift_Top eigenschap van [0, 100, 255]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/ColorShift-Top-0-100-255.jpg)

### [ColorShift_Bottom](#colorshift_bottom)[](#colorshift_bottom)

De [ColorShift_Bottom](/docs/nl-nl/reference/engine/classes/Lighting#ColorShift_Bottom) -eigenschap stelt een tint in die weerkaatst van oppervlakken die van de zon of maan af zijn gericht.

Let in de volgende afbeeldingen op de tintverandering op de zandstenen muur die van de zon af is gericht.

[255, 0, 220] [0, 255, 190]

![Lighting.ColorShift_Bottom eigenschap van [255, 0, 220]](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/ColorShift-Bottom-255-0-220.jpg)

## [Intensiteit](#intensiteit)[](#intensiteit)

### [Helderheid](#helderheid)[](#helderheid)

De [Brightness](/docs/nl-nl/reference/engine/classes/Lighting#Brightness) -eigenschap stelt de intensiteit van de verlichting in. Dit kan helpen om het contrast tussen fel verlichte gebieden en schaduwen te vergroten, wat fel zonlicht en warmer weer simuleert.

0.5 1.5 3.75

![Lighting.Brightness eigenschap van 0.5](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/Brightness-0.5.jpg)

### [ExposureCompensation](#exposurecompensation)[](#exposurecompensation)

De [ExposureCompensation](/docs/nl-nl/reference/engine/classes/Lighting#ExposureCompensation) -eigenschap past de belichting toe op een game. Belichting is de hoeveelheid licht die de camera bereikt.

Een lagere waarde is vergelijkbaar met onderbelichting in fotografie, terwijl een hogere waarde vergelijkbaar is met overbelichting.

0 -1 1.25

![Lighting.ExposureCompensation eigenschap van 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/ExposureCompensation-0.jpg)

## [Schaduwen](#schaduwen)[](#schaduwen)

### [GlobalShadows](#globalshadows)[](#globalshadows)

Wanneer ingeschakeld, rendert de [GlobalShadows](/docs/nl-nl/reference/engine/classes/Lighting#GlobalShadows) -eigenschap schaduwen.

Ingeschakeld Uitgeschakeld

![Lighting.GlobalShadows eigenschap ingeschakeld](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/GlobalShadows-True.jpg)

### [ShadowSoftness](#shadowsoftness)[](#shadowsoftness)

De [ShadowSoftness](/docs/nl-nl/reference/engine/classes/Lighting#ShadowSoftness) -eigenschap past aan hoe vaag schaduwen zijn van een waarde van 0  (harde randen) tot 1  (zachte randen). Deze eigenschap is alleen geldig wanneer [LightingStyle](/docs/nl-nl/reference/engine/classes/Lighting#LightingStyle)  is ingesteld op [Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle) .

0 1

![Lighting.ShadowSoftness eigenschap van 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/ShadowSoftness-0.jpg)

## [Uiterlijk](#uiterlijk)[](#uiterlijk)

### [LightingStyle](#lightingstyle)[](#lightingstyle)

[LightingStyle](/docs/nl-nl/reference/engine/classes/Lighting#LightingStyle)  geeft de artistieke intentie achter de verlichting in het spel aan, als een [Enum.LightingStyle](/docs/nl-nl/reference/engine/enums/LightingStyle) -optie. [Realistic](/docs/nl-nl/reference/engine/enums/LightingStyle)  biedt de meest geavanceerde en realistische verlichting en schaduwen die Roblox kan leveren, terwijl [Soft](/docs/nl-nl/reference/engine/enums/LightingStyle)  een vlakke, retro-Roblox uitstraling produceert met zachtere lichten en schaduwen.

Realistisch Zacht

![Lighting.LightingStyle instelling van Realistisch](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/LightingStyle-Realistic.jpg)

### [PrioritizeLightingQuality](#prioritizelightingquality)[](#prioritizelightingquality)

De [PrioritizeLightingQuality](/docs/nl-nl/reference/engine/classes/Lighting#PrioritizeLightingQuality) -eigenschap geeft aan of je de kwaliteit van verlichting/schaduw of de zichtafstand als eerste wilt laten afschalen. Naarmate het renderkwaliteit-niveau afneemt, prioriteert een instelling van true  functies zoals geavanceerde schaduwen en hoogwaardige shaders op kortere afstanden, terwijl een instelling van false  de zichtafstand prioriteert. Als verlichting en schaduwen erg belangrijk zijn voor de artistieke uitstraling van je game, stel dit dan in op true .

## [Omgeving](#omgeving)[](#omgeving)

### [ClockTime en TimeOfDay](#clocktime-en-timeofday)[](#clocktime-en-timeofday)

De [ClockTime](/docs/nl-nl/reference/engine/classes/Lighting#ClockTime)  en [TimeOfDay](/docs/nl-nl/reference/engine/classes/Lighting#TimeOfDay) -eigenschap vertegenwoordigen beide de huidige tijd van de dag in uren, en ze zijn direct gerelateerd; als je een eigenschap verandert, verandert de andere ook.

Het enige verschil tussen deze eigenschappen is hun numerieke waarde; [ClockTime](/docs/nl-nl/reference/engine/classes/Lighting#ClockTime)  vertegenwoordigt tijd van uur 0  tot 24 , terwijl [TimeOfDay](/docs/nl-nl/reference/engine/classes/Lighting#TimeOfDay)  tijd vertegenwoordigt door een 24-uurs string.

0 = 00:00:00 6.3 = 06:18:00 17 = 17:00:00

![Lighting.ClockTime van 0 (TimeOfDay van 00:00:00)](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/TimeOfDay-0.jpg)

Let op dat elke eigenschap de werkelijke tijd van de dag niet volgt, en ze zullen niet veranderen tijdens een game tenzij ze via een script worden gewijzigd.

### [GeographicLatitude](#geographiclatitude)[](#geographiclatitude)

De [GeographicLatitude](/docs/nl-nl/reference/engine/classes/Lighting#GeographicLatitude) -eigenschap vertegenwoordigt de geografische breedte in graden. Let op dat hoewel deze eigenschap de positie van de zon en de maan verandert, het de [ClockTime](/docs/nl-nl/reference/engine/classes/Lighting#ClockTime)  en [TimeOfDay](/docs/nl-nl/reference/engine/classes/Lighting#TimeOfDay) -eigenschappen niet verandert.

### [EnvironmentDiffuseScale](#environmentdiffusescale)[](#environmentdiffusescale)

De [EnvironmentDiffuseScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentDiffuseScale) -eigenschap bepaalt hoeveel ambient licht uit de omgeving wordt afgeleid.

Let in de volgende afbeeldingen op hoe het ambient licht verandert, vooral binnen de keuken van de ramenwinkel.

0 1

![Lighting.EnvironmentDiffuseScale eigenschap van 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/EnvironmentDiffuseScale-0.jpg)

### [EnvironmentSpecularScale](#environmentspecularscale)[](#environmentspecularscale)

De [EnvironmentSpecularScale](/docs/nl-nl/reference/engine/classes/Lighting#EnvironmentSpecularScale) -eigenschap bepaalt hoeveel speculair licht uit de omgeving wordt afgeleid. Wanneer ingesteld nabij een waarde van 1, reflecteren gladde objecten de omgeving beter en lijkt metaal realistischer.

0 1

![Lighting.EnvironmentSpecularScale eigenschap van 0](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/EnvironmentSpecularScale-0.jpg)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
