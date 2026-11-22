<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-1/parents-and-children -->

Ouders en kinderen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Variabelen en objecten](/docs/nl-nl/tutorials/fundamentals/coding-1/landing)

# Ouders en kinderen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In plaats van scripts vanuit ServerScriptService uit te voeren, wil je misschien een script aan het onderdeel hechten. Bijvoorbeeld, een script gebruiken om een onderdeel in een val te veranderen of een onderdeel punten aan de speler te geven wanneer ze het aanraken. Door te begrijpen hoe scripts en onderdelen in de hiërarchie met elkaar zijn verbonden, kun je een script maken dat automatisch werkt zonder te benoemen welk onderdeel te gebruiken.

Om dit te doen, moet je de ouder- en kindrelaties  begrijpen.

Ouders en kinderen zijn manieren om de hiërarchie tussen verschillende objecten te beschrijven. Elke keer dat je een nieuw onderdeel aan Workspace hebt toegevoegd, was Workspace het ouderobject en werd het onderdeel een kindobject. Toen je een script aan ServerScriptService toevoegde, was ServerScriptService de ouder en was het script een nieuw kind.

## [Stel het project en script in](#stel-het-project-en-script-in)[](#stel-het-project-en-script-in)

Om ouder- en kindrelaties te demonstreren, begin je met een enkel onderdeel dat van kleur verandert en dupliceer je vervolgens het script over meerdere onderdelen.

1.

Maak een nieuw onderdeel en hernoem het. Deze les zal ColorPart gebruiken.

2.

Klik met de rechtermuisknop op het onderdeel  en selecteer Object invoegen  ⟩ Nieuw script . Hernoem het script naar ColorChanger .

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-1/color-changer_400x216.png)

3.

Kopieer en plak de onderstaande code in ColorChanger . Deze versie van de code is dezelfde als die je eerder hebt gebruikt. Het wijst een specifiek onderdeel toe aan een variabele.

Verandert de kleur van ColorPart

```

local Workspace = game:GetService("Workspace")

local colorPart = Workspace.ColorPart

colorPart.Color = Color3.fromRGB(50, 240, 255)

```

4.

Test en controleer of het onderdeel van kleur verandert zoals gewenst.

## [Ouder- en kindrelaties](#ouder--en-kindrelaties)[](#ouder--en-kindrelaties)

Een ouder  is alles met objecten, zoals scripts of onderdelen, die eronder zijn bevestigd. Alles onder de ouder zijn zijn kinderen . In het onderstaande voorbeeld is ColorPart de ouder en is ColorChanger het kind.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-1/color-changer_400x216.png)

Met het huidige script kun je alleen de kleur van een enkel onderdeel  genaamd ColorPart veranderen. Om de kleur van elk onderdeel te veranderen, kun je de code zo ontwerpen dat deze werkt op het ouderobject van het script, ongeacht hoe het genoemd is. De code script.Parent  gaat omhoog in de hiërarchie en vindt het object waaraan het script is bevestigd.

### [Gebruik script.Parent](#gebruik-scriptparent)[](#gebruik-scriptparent)

script.Parent  kan aan een variabele worden toegewezen zoals elke andere waarde met het =  symbool.

1.

Vervang in het script het benoemde onderdeel door script.Parent . Controleer je code hieronder.

Verandert de kleur van het ouderobject

```

local colorPart = script.Parent

colorPart.Color = Color3.fromRGB(50, 240, 255)

```

### [Test herbruikbare onderdelen](#test-herbruikbare-onderdelen)[](#test-herbruikbare-onderdelen)

Nu de variabele zal verwijzen naar welk onderdeel het script ook is bevestigd, kun je zoveel kopieën maken als je wilt.

1.

Klik met de rechtermuisknop op het kleuronderdeel en selecteer Dupliceer, of gebruik de sneltoets Ctrl D  (⌘ D ). Maak in totaal minstens drie onderdelen.

2.

Voer het spel uit om te controleren of alle onderdelen van kleur veranderen.

## [Samenvatting](#samenvatting)[](#samenvatting)

In plaats van altijd onderdelen rechtstreeks te verwijzen op naam en locatie, kan script.Parent als alternatief worden gebruikt. Die code pakt de ouder, of het object, waaraan het script is bevestigd, waardoor het script wijzigingen kan aanbrengen. Het gebruik van code zoals script.Parent  zal handig zijn om je code herbruikbaar te maken. Een nadeel om te onthouden is dat je nu meerdere scripts hebt die moeten worden bijgewerkt als je de code wilt wijzigen.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-2/functions-and-events)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-1/object-properties)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
