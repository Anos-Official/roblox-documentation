<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/core/building/customize-global-lighting -->

Pas globale verlichting aan | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Pas globale verlichting aan

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Globale verlichting  beheert de algehele uitstraling en sfeer van je spel. Door een paar eigenschappen op de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service aan te passen, kun je de kleur, schaduwen, tijd van de dag en atmosferische effecten van een scène veranderen.

In deze sectie pas je de verlichting aan om overeen te komen met de [Island Jump - Final](https://www.roblox.com/games/14238807008/Island-Jump-Completed-Sample)  voorbeeld.

Verlichting wordt voornamelijk geconfigureerd via eigenschapswaarden, waardoor het een geweldige keuze is voor Assistant. Nadat je de prompt hebt toegepast, besteed wat tijd in de viewport om Ambient , ClockTime  en Density  aan te passen totdat de scène eruitziet zoals je wilt. Voor een overzicht van elk verlichtingsobject dat Studio biedt, zie [Verlichting en effecten](/docs/nl-nl/environment) .

## [Stel verlichtingsinstellingen in](#stel-verlichtingsinstellingen-in)[](#stel-verlichtingsinstellingen-in)

De [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service beheert hoe licht zich gedraagt in je spel. Het voorbeeldspel past eigenschappen aan zoals omgevingskleur, verlichtings-technologie, schaduweninstellingen en zonpositie om een koelere oceaanpalet, scherpere schaduwen en sterkere directionele verlichting te creëren.

Bouw met Assistant Bouw het Zelf

Pas globale verlichting aan

```

Op de Lighting service, stel de volgende eigenschappen in:

- Ambient: Color3.fromRGB(16, 16, 16)

- ColorShift_Top: Color3.fromRGB(196, 222, 255)

- OutdoorAmbient: Color3.fromRGB(134, 158, 190)

- ShadowSoftness: 0

- LightingStyle: Realistisch

- ClockTime: 9

- GeographicLatitude: 78

```

Nadat het is uitgevoerd, krijgt de wereld een koelere blauw-grijze tint, worden schaduwen scherp, en verschuift de zon naar de late ochtend aan de rechterkant van je zee-stapels.

Voor een overzicht van de rest van de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  eigenschappen, zie [Globale verlichting](/docs/nl-nl/environment/lighting) .

## [Atmosfeer eigenschappen](#atmosfeer-eigenschappen)[](#atmosfeer-eigenschappen)

Het [Atmosphere](/docs/nl-nl/reference/engine/classes/Atmosphere)  object is een kind van de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service. Het voegt diepte toe door deeltjes in de lucht te simuleren en verre landschappen in de lucht te mengen. De twee belangrijkste eigenschappen zijn Density , die de dikte van de atmosfeer beheert, en Offset , die beheert waar die menging begint.

Bouw met Assistant Bouw het Zelf

Verdik de atmosfeer

```

Op het Atmosphere object binnen de Lighting service, stel in:

- Density: 0.375

- Offset: 0.17

```

Voor meer informatie over Atmosfeer, zie [Atmosferische Effecten](/docs/nl-nl/environment/atmosphere) .

Nu je de verlichting van het spel hebt geconfigureerd, laat de volgende sectie je zien hoe je de greybox-indeling kunt vervangen door gepolijste assets.

Pre-Aanpassing Aangepaste Visuele Effecten

![De verlichting visuals van het voorbeeldspel Island Jump vóór de aanpassing van deze pagina.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Lighting-Pre-Customization.jpg)

[Volgende](/docs/nl-nl/tutorials/curriculums/core/building/apply-polished-assets)[Vorige](/docs/nl-nl/tutorials/curriculums/core/building/create-basic-visual-effects)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
