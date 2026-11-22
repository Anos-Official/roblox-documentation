<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-2/multiple-parameters-and-arguments -->

Meerdere parameters en argumenten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Functies en evenementen](/docs/nl-nl/tutorials/fundamentals/coding-2/functions-and-events)

# Meerdere parameters en argumenten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Functies kunnen eigenlijk meer dan één parameter hebben, waardoor meerdere argumenten (stukjes informatie) aan de functie kunnen worden doorgegeven. Een voorbeeld zou kunnen zijn het toewijzen van een speler aan een team. Hier zou je een parameter nodig hebben om de speler door te geven, en een parameter om door te geven aan welk team ze moeten worden toegewezen.

Om meerdere parameters in te stellen, scheid je de parameternamen met een komma.

```

local function assignTeam(playerName, whichTeam)

end

```

## [Oefenen met meerdere parameters](#oefenen-met-meerdere-parameters)[](#oefenen-met-meerdere-parameters)

Om te oefenen met het werken met meerdere parameters, maak je een functie die objecten sorteert in afval of recycling.

-

De eerste  parameter is afval, dat vernietigd zal worden.

-

De tweede  parameter is voor recycling, dat weer glanzend en nieuw gemaakt zal worden.

### [Stel de functie in](#stel-de-functie-in)[](#stel-de-functie-in)

Stel eerst de functie in met meerdere parameters en test vervolgens je werk.

1.

Maak een nieuw script in ServerScriptService .

2.

Code een nieuwe functie genaamd sortGarbage()  met twee parameters, trash  en recyclable .

3.

Roep de functie aan onderaan het script.

4.

Controleer snel de code tot nu toe met een printstatement binnen de functie.

```

local function sortGarbage(trash, recyclable)

   print("garbage test")

end

sortGarbage()

```

### [Gebruik meerdere parameters](#gebruik-meerdere-parameters)[](#gebruik-meerdere-parameters)

Binnen de functie kunnen parameters worden gebruikt zoals variabelen. In dit voorbeeld wordt trash  vernietigd en krijgt recyclable  sprankels met behulp van een Particle Emitter.

1.

Verwijder de printstatement en gebruik Instance.new() om een nieuwe Particle Emitter te maken zoals getoond. Dit zal worden gebruikt om recyclables hun sprankel te geven.

```

local function sortGarbage(trash,recyclable)

    -- Maak een nieuwe Particle Emitter

    local sparkle = Instance.new("ParticleEmitter")

end

sortGarbage()

```

[Instance.new()](/docs/nl-nl/reference/engine/datatypes/Instance#new)  kan ook worden gebruikt om objecten zoals vuur, mappen en onderdelen te maken.

2.

Vernietig wat er door de afvalparameter wordt doorgegeven, net zoals als afval een andere variabele zou zijn.

```

local function sortGarbage(trash,recyclable)

    local sparkle = Instance.new("ParticleEmitter")

    -- Vernietig het afval

    trash:Destroy()

end

sortGarbage()

```

3.

Maak de Particle Emitter een kind van de recyclable.

```

local function sortGarbage(trash,recyclable)

    local sparkle = Instance.new("ParticleEmitter")

    -- Vernietig het afval en maak recyclables glanzend

    trash:Destroy()

    sparkle.Parent = recyclable

end

sortGarbage()

```

## [Waarden doorgeven via parameters](#waarden-doorgeven-via-parameters)[](#waarden-doorgeven-via-parameters)

Tijd om het afval weg te gooien! Met de parameters ingesteld, zijn de functies klaar om informatie in te nemen.

1.

Maak twee objecten met behulp van basisonderdelen om dingen voor te stellen die je misschien weggooit. Eén moet afval zijn en de andere recyclebaar. Zorg ervoor dat ze unieke namen hebben.

2.

Voeg bovenaan het script variabelen toe voor de objecten die je hebt gemaakt. Dit zullen je argumenten zijn.

```

local Workspace = game:GetService("Workspace")

local cementBlock = Workspace.Cement

local glassBottle = Workspace.GlassBottle

```

3.

Roep onderaan het script, waar sortGarbage()  wordt aangeroepen, elk argument door.

```

local Workspace = game:GetService("Workspace")

-- Objecten om als argumenten te gebruiken

local cementBlock = Workspace.CementBlock

local glassBottle = Workspace.GlassBottle

-- Vernietigt afval en ruimt recyclables op

local function sortGarbage(trash,recyclable)

    local sparkle = Instance.new("ParticleEmitter")

    trash:Destroy()

    sparkle.Parent = recyclable

end

-- Geef de argumenten door

sortGarbage(cementBlock, glassBottle)

```

4.

Test je code. Het eerste object dat wordt doorgegeven, zal worden vernietigd. Het tweede object zal sprankelen.

## [Volgorde van parameters](#volgorde-van-parameters)[](#volgorde-van-parameters)

Typisch worden argumenten gekoppeld aan parameters op basis van de volgorde waarin ze worden doorgegeven. Bijvoorbeeld, het eerste argument wordt gebruikt voor de eerste parameter. Het tweede argument wordt gebruikt voor de tweede.

In ons voorbeeld zijn er twee parameters. Wat er ook als eerste wordt doorgegeven, zal altijd afval zijn, en de tweede zal altijd recyclebaar zijn.

```

-- Vernietigt afval en ruimt recyclables op

local function sortGarbage(trash,recyclable)

     local sparkle = Instance.new("ParticleEmitter")

    trash:Destroy()

    sparkle.Parent = recyclable

end

-- Gaat in volgorde. Cement wordt vernietigd en de glazen fles wordt gerecycled

sortGarbage(cementBlock, glassBottle)

-- GlassBottle wordt vernietigd en cementBlock wordt gerecycled

sortGarbage(glassBottle, cementBlock)

```

Als je slechts één argument zou doorgeven, zou dat argument als afval worden behandeld. Als je drie argumenten zou doorgeven, zou er niets met het derde argument gebeuren omdat er geen derde parameter is.

## [Samenvatting](#samenvatting)[](#samenvatting)

Parameters zijn plaatsaanduidingen waarlangs waarden aan functies kunnen worden doorgegeven. Argumenten zijn de waarden die door de plaatsaanduiding worden doorgegeven. Je kunt meerdere parameters maken door hun namen met komma's te scheiden. Bij het aanroepen van functies bepaalt de volgorde waarin waarden in de ontvangende functie worden doorgegeven, welke parameter ze gebruiken.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-3/landing)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-2/parameters-practice-buttons)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
