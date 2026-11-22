<!-- Source: https://create.roblox.com/docs/nl-nl/luau/comments -->

Luau opmerkingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. [Luau-referentie](/docs/nl-nl/luau)
8. /
9. Functies

# Luau opmerkingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een opmerking  is tekst die de Luau-parser tijdens runtime negeert.

Roblox Studio heeft een vergelijkbare [opmerkingen](/docs/nl-nl/projects/collaboration#opmerkingen)  functie die niet gerelateerd is aan code-opmerkingen in Luau.

## [Eéne-regel opmerkingen](#eéne-regel-opmerkingen)[](#eéne-regel-opmerkingen)

Je kunt eéne-regel opmerkingen definiëren met een dubbele streepje (-- ) overal buiten een string. Eéne-regel opmerkingen strekken zich uit tot het einde van de regel.

Gebruik eéne-regel opmerkingen voor in-line notities. Als de opmerking meerdere regels beslaat, gebruik dan meerdere eéne-regel opmerkingen.

Je kunt eéne-regel opmerkingen toevoegen en verwijderen in de Script Editor met de sneltoets Ctrl /  (⌘ / ).

```

-- Deze voorwaarde is echt belangrijk omdat de wereld zou ontploffen als deze

-- ontbreekt.

if not foo then

	stopWorldFromBlowingUp()

end

```

## [Blok opmerkingen](#blok-opmerkingen)[](#blok-opmerkingen)

Je kunt meerregelige blok opmerkingen definiëren met dubbele streepjes en dubbele haakjes (--[[]] ). Gebruik blok opmerkingen voor het documenteren van items:

-

Gebruik een blok opmerking bovenaan bestanden om hun doel te beschrijven.

-

Gebruik een blok opmerking voor functies of objecten om hun intentie te beschrijven.

```

--[[

    Zet de kosmische maanstraal onmiddellijk uit.

    Mag alleen worden aangeroepen binnen 15 minuten voor middernacht Mountain Standard

    Tijd, of de kosmische maanstraal kan beschadigd raken.

]]

local function stopCosmicMoonRay()

end

```

Indien nodig kun je meerdere haakjes binnen een blok opmerking nesten met hetzelfde aantal gelijkheidstekens in zowel de begin- als eindhaak:

```

--[=[

    Diepgaande details over de kosmische maanstraal: [[[TOP SECRET]]]

]=]

```

Als je een blok opmerking direct voor een declaratie plaatst, toont de Script Editor de opmerking als een documentatietooltip bij hoveren. Dit werkt ook voor declaraties binnen type-expressies zoals typeof() . Zie [Autocompleter functies](/docs/nl-nl/studio/script-editor#autocomplete-functies)  voor details.

## [Opmerking directieven](#opmerking-directieven)[](#opmerking-directieven)

Luau gebruikt opmerkingen die beginnen met !  om functies zoals [type controle](/docs/nl-nl/luau/type-checking) , [native code generatie](/docs/nl-nl/luau/native-code-gen)  en [linting](https://luau.org/lint)  te regelen.

```

--!strict

--!nonstrict

--!nocheck

--!native

--!nolint

--!optimize 0|1|2

```

Voor linting stelt Roblox Studio de volgende subset van waarschuwingscodes van de [Luau linter](https://luau.org/lint)  in: 1, 2, 3, 6, 10, 11, 12, 13, 14, 15, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28.

De --!optimize  directieve regelt het optimalisatieniveau van de Luau-compiler voor het script:

-

0 schakelt optimalisaties uit.

-

1 schakelt basisoptimalisaties in (standaard in Studio testen).

-

2 schakelt verdere optimalisaties in (standaard in live games).

Exacte optimalisaties worden niet gepubliceerd en kunnen veranderen. We raden aan de standaardwaarden te gebruiken, tenzij je een specifieke reden hebt om dat niet te doen.

## [Te-doen opmerkingen](#te-doen-opmerkingen)[](#te-doen-opmerkingen)

Roblox Studio ondersteunt speciale TODO  opmerkingen. Studio vetgedrukt elke tekst die volgt op TODO  (totdat deze door een spatie wordt onderbroken):

```

-- TODO: Maak de functie hieronder af zodat deze daadwerkelijk doet wat de naam impliceert.

local function stopWorldFromBlowingUp()

end

```

Gebruik TODO  opmerkingen om problemen binnen je code bij te houden en te communiceren.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
