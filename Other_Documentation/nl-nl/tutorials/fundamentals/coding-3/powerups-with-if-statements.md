<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-3/powerups-with-if-statements -->

Evalueer meerdere uitspraken | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Voorwaarden](/docs/nl-nl/tutorials/fundamentals/coding-3/landing)

# Evalueer meerdere uitspraken

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Als uitspraken meerdere vereisten kunnen hebben die waar moeten zijn voordat code wordt uitgevoerd. Het kernwoord and  stelt je in staat om uitspraken te combineren. De volgende code evalueert eerst of twee plus twee gelijk is aan zes en vervolgens of vier niet gelijk is aan zes. Als beide uitspraken waar zijn, wordt de code uitgevoerd.

## [Maak een powerup](#maak-een-powerup)[](#maak-een-powerup)

Powerups zijn in-game items die spelers speciale vaardigheden geven, zoals vliegen, onzichtbaarheid of snelheid. Deze powerup zal de loopsnelheid van de speler verhogen elke keer dat de powerup wordt aangeraakt. Het continu toepassen van boosts kan ervoor zorgen dat de speler veel te snel gaat, dus and  zal worden gebruikt om de maximale loopsnelheid te controleren.

### [Stel de powerup in](#stel-de-powerup-in)[](#stel-de-powerup-in)

Gebruik deze code met een eenvoudig onderdeel of een model, zoals een kristal, munt of gloeiende neonbol.

1.

Maak een nieuw onderdeel genaamd Powerup  en voeg een script toe genaamd WalkSpeedManager .

2.

Declareer een variabele genaamd speedBoost  en wijs het ouderobject van het script toe.

```

-- Geeft een tijdelijke snelheidsboost wanneer aangeraakt

local speedBoost = script.Parent

```

3.

Stel een functie in genaamd onTouch  en verbind deze met de Touched -gebeurtenis van het ouderobject. Speel het spel en controleer je werk.

```

local speedBoost = script.Parent

local function onTouch(otherPart)

	print("Iets heeft speedBoost aangeraakt")

end

speedBoost.Touched:Connect(onTouch)

```

4.

De WalkSpeed-eigenschap is te vinden op Humanoid-objecten. Gebruik hetzelfde patroon dat je gebruikte bij het maken van een valdeel en maak een voorwaarde die controleert op Humanoid-objecten.

Zoekt naar Humanoid-onderdelen

```

local function onTouch(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		print("Een Humanoid is gevonden")

	end

end

```

## [Versnel spelers](#versnel-spelers)[](#versnel-spelers)

De snelheidsboost zal avatars sneller laten lopen elke keer dat de snelheidsboost wordt aangeraakt. Dat zal snel heel, heel snel worden. Het kernwoord and  zal ervoor zorgen dat spelers niet te snel kunnen gaan door de snelheidsboost alleen in te schakelen als de speler onder een bepaalde snelheid is.

1.

Als er een Humanoid wordt gevonden, neem dan de huidige WalkSpeed-waarde en voeg er 10 aan toe. Speel het spel en je avatar zal sneller worden elke keer dat hij de snelheidsboost aanraakt.

Verhoogt de huidige WalkSpeed

```

local function onTouch(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid then

		humanoid.WalkSpeed += 10

	end

end

speedBoost.Touched:Connect(onTouch)

```

2.

In de if-verklaring, gebruik het kernwoord and  om een tweede voorwaarde toe te voegen dat de huidige WalkSpeed-waarde minder is dan 50. Na het toevoegen van de boost zal de snelste WalkSpeed-waarde 60 zijn.

Controleert of de huidige WalkSpeed 50 of minder is

```

if humanoid and humanoid.WalkSpeed <= 50 then

	humanoid.WalkSpeed += 10

end

```

### [Fijn afstemmen van de snelheidsboost](#fijn-afstemmen-van-de-snelheidsboost)[](#fijn-afstemmen-van-de-snelheidsboost)

OnTouch wordt elke keer aangeroepen wanneer de snelheidsboost wordt aangeraakt. Elke stap of de kleinste sprongetje activeert de Touched-gebeurtenis en roept de verbonden functie aan. De eigenschap van het onderdeel, CanTouch , kan voorkomen dat de Touched-gebeurtenis wordt geactiveerd. Maak gebruik van CanTouch en zet de snelheidsboost uit voor één seconde elke keer dat deze is geactiveerd.

1.

Na het toepassen van de boost, stel je de CanTouch-eigenschap van het onderdeel in op false. Speel het spel en zorg ervoor dat de boost slechts één keer wordt toegepast.

Deactiveert de snelheidsboost

```

local speedBoost = script.Parent

local function onTouch(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid and humanoid.WalkSpeed <= 50 then

		humanoid.WalkSpeed += 10

		speedBoost.CanTouch = false

	end

end

speedBoost.Touched:Connect(onTouch)

```

2.

Gebruik task.wait(1)  om het script één seconde te pauzeren, en stel vervolgens CanTouch in op true. Speel het spel en zorg ervoor dat de snelheidsboost opnieuw kan worden toegepast na één seconde.

Voltooid script

```

local speedBoost = script.Parent

local function onTouch(otherPart)

	local character = otherPart.Parent

	local humanoid = character:FindFirstChildWhichIsA("Humanoid")

	if humanoid and humanoid.WalkSpeed <= 50 then

		humanoid.WalkSpeed += 10

		speedBoost.CanTouch = false

		task.wait(1)

		speedBoost.CanTouch = true

	end

end

speedBoost.Touched:Connect(onTouch)

```

3.

Speel met de waarden in het voltooide script. WalkSpeed kan oplopen tot 100. De standaard WalkSpeed-waarde is 16.

## [Samenvatting](#samenvatting)[](#samenvatting)

Het kernwoord and  kan worden gebruikt om meerdere voorwaarden te vereisen voordat een codeblok wordt uitgevoerd, zoals een waarde die groter is dan 0 en kleiner dan 100. Of dat er een Humanoid is en dat zijn WalkSpeed minder of gelijk is aan 50.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-3/multiple-conditions)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-3/traps-with-if-statements)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
