<!-- Source: https://create.roblox.com/docs/nl-nl/environment -->

Verlichting en effecten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelomgeving](/docs/nl-nl/environment)

# Verlichting en effecten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  container services stellen je in staat om de omgeving van een spel te controleren en aan te passen, zoals [verlichting](#globale-verlichting) , [atmosfeer](#atmosferische-effecten)  en [wolken](#wolken-en-luchten) . Je kunt ook [post-processing effecten](#post-processing-effecten)  toepassen om aan te passen hoe het spel op het scherm verschijnt.

## [Globale verlichting](#globale-verlichting)[](#globale-verlichting)

De [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service bevat eigenschappen die je kunt aanpassen om de globale verlichting in een spel bij te werken, zoals de [ClockTime](/docs/nl-nl/reference/engine/classes/Lighting#ClockTime)  en [Brightness](/docs/nl-nl/reference/engine/classes/Lighting#Brightness) .

ClockTime = 0 ClockTime = 6.3 Brightness = 0.5 Brightness = 3.75

![Verlichting met ClockTime van 0 (TimeOfDay van 00:00:00)](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/lighting-properties/TimeOfDay-0.jpg)

Naast globale verlichting kun je [lichtbronnen](/docs/nl-nl/effects/light-sources)  creëren en aan onderdelen of bevestigingen koppelen om objecten zoals lampen, fakkels, schijnwerpers of tv-schermen te simuleren.

## [Atmosferische effecten](#atmosferische-effecten)[](#atmosferische-effecten)

[Atmosferische effecten](/docs/nl-nl/environment/atmosphere)  simuleren realistische omgevingen door zonlicht op unieke manieren te verstrooien. Met behulp van het [Atmosphere](/docs/nl-nl/reference/engine/classes/Atmosphere)  object in de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service, kun je de luchtdeeltjes [dichtheid](/docs/nl-nl/environment/atmosphere#dichtheid)  controleren, [nevel](/docs/nl-nl/environment/atmosphere#nevel)  of [glans](/docs/nl-nl/environment/atmosphere#schittering)  simuleren, de [kleur](/docs/nl-nl/environment/atmosphere#kleur)  van een atmosfeer instellen, en meer.

![Atmosferische effecten gebruikt om een schitterende zonsondergangscène weer te geven](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/atmosphere/Showcase.jpg) Atmosferische effecten gebruikt om een schitterende zonsondergangscène weer te geven

## [Wolken en luchten](#wolken-en-luchten)[](#wolken-en-luchten)

Standaard vormt het [Sky](/docs/nl-nl/reference/engine/classes/Sky)  object een [skybox](/docs/nl-nl/environment/skybox)  met hemellichamen zoals een zon, maan en sterren. Daarnaast kun je de wolkenbedekking, dichtheid en kleur eigenschappen van het [Clouds](/docs/nl-nl/reference/engine/classes/Clouds)  object aanpassen om realistische, [dynamische wolken](/docs/nl-nl/environment/clouds)  te renderen die langzaam over de lucht drijven door [globale wind](/docs/nl-nl/environment/global-wind) .

Wind die dynamische wolken over de lucht blaast

## [Post-processing effecten](#post-processing-effecten)[](#post-processing-effecten)

Post-processing effecten  zijn aanpasbare filters die je in staat stellen om snel de visuals van je spel te verrijken. Met behulp van de post-processing effectobjecten in de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service of [Camera](/docs/nl-nl/reference/engine/classes/Camera) , kun je:

-

Een camera simuleren die naar een fel licht kijkt en de gloed ervan overdrijven.

-

Een Gaussian blur toepassen op het geheel van je spel of een blur toevoegen aan delen van je spel die niet scherp zijn.

-

Het uiterlijk van een omgeving verbeteren om een specifieke sfeer te creëren door middel van tint.

-

Een halo van licht renderen die meebeweegt met de zon.

![Landschap met diepte-van-veld effect toegepast, simuleert afstandsblur](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/DepthOfFieldEffect-With.jpg) Landschap met diepte-van-veld effect toegepast, simuleert afstandsblur

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
