<!-- Source: https://create.roblox.com/docs/nl-nl/environment/post-processing-effects -->

Post-processing effecten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelomgeving](/docs/nl-nl/environment)

# Post-processing effecten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Post-processing effecten  zijn aanpasbare filters die je in staat stellen om snel de visuals van je game te verrijken. Met de post-processing effectobjecten in de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service of [Camera](/docs/nl-nl/reference/engine/classes/Camera) , kun je:

-

Een camera simuleren die naar een fel licht kijkt en de gloed ervan overdrijven ([bloom](#bloom) ).

-

Een Gaussian [blur](#blur)  toepassen op de gehele game, of een blur toevoegen aan delen van je game die niet in focus zijn ([depth‑of‑field](#depth-of-field) ).

-

Het uiterlijk van een omgeving verbeteren om een specifieke sfeer te creëren door middel van tint ([color correction](#kleurcorrectie) ).

-

Een halo van licht renderen die met de zon meebeweegt ([sun rays](#zonnestralen) ).

![Landschap met depth-of-field effect toegepast, simuleert afstandsblur](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/DepthOfFieldEffect-With.jpg) Landschap met depth-of-field effect toegepast, simuleert afstandsblur

## [Voeg post-processing effecten toe](#voeg-post-processing-effecten-toe)[](#voeg-post-processing-effecten-toe)

Wanneer je post-processing effecten toevoegt aan de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service, worden ze weergegeven voor alle spelers  die de game betreden. Dit is nuttig voor effecten die de globale omgeving beïnvloeden, zoals [sun rays](#zonnestralen) .

Wanneer je post-processing effecten toevoegt aan het [Camera](/docs/nl-nl/reference/engine/classes/Camera)  object, worden ze alleen weergegeven voor een specifieke speler . Dit is nuttig voor effecten die alleen betrekking moeten hebben op die speler op basis van hun acties, zoals het vervagen van de 3D-wereldweergave wanneer ze een UI-menu geopend hebben.

Om post-processing effecten toe te voegen aan de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service of [Camera](/docs/nl-nl/reference/engine/classes/Camera) :

1.

In het Explorer  venster, beweeg je de muis over de [Lighting](/docs/nl-nl/reference/engine/classes/Lighting)  service of [Camera](/docs/nl-nl/reference/engine/classes/Camera) , klik vervolgens op de ⊕ knop. Een contextmenu wordt weergegeven.

2.

Kies in het menu een of meer van de volgende post-processing effecten:

-

BloomEffect

-

BlurEffect

-

ColorCorrectionEffect

-

DepthOfFieldEffect

-

SunRaysEffect

-

ColorGradingEffect

3.

Afhankelijk van je Studio-instellingen, kunnen sommige effecten niet verschijnen. Om je renderingkwaliteit te verhogen:

1.

Open [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing) .

2.

Selecteer in de navigatie aan de linkerkant Rendering , en vervolgens het dropdownmenu Editor Quality Level .

3.

Stel het in op het hoogste niveau.

## [Bloom](#bloom)[](#bloom)

Het [BloomEffect](/docs/nl-nl/reference/engine/classes/BloomEffect)  effect overdrijft lichten binnen je game door een camera te simuleren die naar een fel licht kijkt. Wanneer dit effect een hoge waarde heeft, gloeien delen met lichte kleuren.

Standaard Bloom Effect

![Game zonder enige effecten toegepast](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/BloomEffect-Without.jpg)

## [Blur](#blur)[](#blur)

Het [BlurEffect](/docs/nl-nl/reference/engine/classes/BlurEffect)  effect past een Gaussian blur toe op de gehele 3D-wereldweergave. Je kunt dit effect gebruiken om de achtergrond te vervagen wanneer een speler een menu geopend heeft, zodat ze zich kunnen concentreren op de belangrijkste details.

Standaard Blur Effect

![Game zonder enige effecten toegepast](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/BlurEffect-Without.jpg)

## [Kleurcorrectie](#kleurcorrectie)[](#kleurcorrectie)

Het [ColorCorrectionEffect](/docs/nl-nl/reference/engine/classes/ColorCorrectionEffect)  effect past kleur eigenschappen aan om het uiterlijk van een omgeving te verbeteren. Je kunt dit effect ook gebruiken om feedback aan de speler te geven, zoals het tinten van het scherm in het rood wanneer de gezondheid van hun personage laag is.

De volgende lijst beschrijft de primaire [ColorCorrectionEffect](/docs/nl-nl/reference/engine/classes/ColorCorrectionEffect)  eigenschappen:

-

[Brightness](/docs/nl-nl/reference/engine/classes/ColorCorrectionEffect#Brightness)  — Stelt de helderheid van pixels in.

-

[Contrast](/docs/nl-nl/reference/engine/classes/ColorCorrectionEffect#Contrast)  — Stelt de verandering in scheiding tussen donkere en lichte kleuren in.

-

[Saturation](/docs/nl-nl/reference/engine/classes/ColorCorrectionEffect#Saturation)  — Stelt de intensiteit van kleuren in.

-

[TintColor](/docs/nl-nl/reference/engine/classes/ColorCorrectionEffect#TintColor)  — Bepaalt hoeveel de RGB-kanalen van pixels worden geschaald.

Standaard Kleurcorrectie Effect

![Game zonder enige effecten toegepast](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/ColorCorrectionEffect-Without.jpg)

## [Depth-of-field](#depth-of-field)[](#depth-of-field)

Het [DepthOfFieldEffect](/docs/nl-nl/reference/engine/classes/DepthOfFieldEffect)  effect vervaagt delen van je game die niet in focus zijn. Je kunt dit effect gebruiken om verre objecten te vervagen of om een speler te focussen op specifieke delen van je game, zoals een item in een winkel.

Standaard Depth-of-Field Effect

![Game zonder enige effecten toegepast](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/DepthOfFieldEffect-Without.jpg)  ![](https://prod.docsiteassets.roblox.com/assets/engine-api/classes/DepthOfFieldEffect/Depth-Of-Field-Diagram.svg)

## [Zonnestralen](#zonnestralen)[](#zonnestralen)

Het [SunRaysEffect](/docs/nl-nl/reference/engine/classes/SunRaysEffect)  effect creëert een halo van licht met stralen rond de zon die bewegen op basis van de [ClockTime](/docs/nl-nl/reference/engine/classes/Lighting#ClockTime)  of [TimeOfDay](/docs/nl-nl/reference/engine/classes/Lighting#TimeOfDay)  eigenschap. Objecten tussen de camera van de speler en de zon vormen dit effect, wat zorgt voor realistische visuals van licht en schaduw.

## [Kleurgrading](#kleurgrading)[](#kleurgrading)

Het [ColorGradingEffect](/docs/nl-nl/reference/engine/classes/ColorGradingEffect)  effect wijzigt hoe kleurwaarden die door de renderer zijn berekend, moeten worden omgezet naar het kleurenspectrum van het scherm, wat invloed heeft op de sfeer en het uiterlijk van je plek.

De primaire eigenschap van dit effect is [TonemapperPreset](/docs/nl-nl/reference/engine/classes/ColorGradingEffect#TonemapperPreset) . De volgende waarden zijn beschikbaar:

-

[Enum.TonemapperPreset.Default](/docs/nl-nl/reference/engine/enums/TonemapperPreset#Default)  — Stelt de tone mapper in om de post‑2019 Roblox uitstraling te gebruiken, die levendige kleuren en hoge contrasten biedt.

-

[Enum.TonemapperPreset.Retro](/docs/nl-nl/reference/engine/enums/TonemapperPreset#Retro)  — Stelt de tone mapper in om de pre‑2019 Roblox uitstraling na te bootsen. Kleuren zien er minder verzadigd uit en er is minder contrast tussen hen.

Als je een volledige pre‑2019 Roblox look voor je game wilt recreëren, experimenteer dan met [Enum.TonemapperPreset.Retro](/docs/nl-nl/reference/engine/enums/TonemapperPreset#Retro)  en stel de helderheid van alle lichten in op maximaal 1.0 .

Standaard Retro

![Game zonder enige effecten toegepast](https://prod.docsiteassets.roblox.com/assets/lighting-and-effects/post-processing/ColorGrading-Default.jpg)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
