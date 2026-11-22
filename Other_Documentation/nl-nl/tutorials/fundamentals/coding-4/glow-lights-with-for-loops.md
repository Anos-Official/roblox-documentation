<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-4/glow-lights-with-for-loops -->

Gloeiende lichten met for-lussen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Loops](/docs/nl-nl/tutorials/fundamentals/coding-4/landing)

# Gloeiende lichten met for-lussen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Om for-lussen te oefenen, ga je een lamp maken die geleidelijk helderder wordt en vervolgens in intensiteit afneemt. Dit script kan vervolgens op andere lichten in een project worden toegepast, of het nu een straatlamp of een gloeiende kristal is.

## [Stel het onderdeel en script in](#stel-het-onderdeel-en-script-in)[](#stel-het-onderdeel-en-script-in)

De lamp zal een onderdeel zijn met een bijgevoegd licht en script.

1.

Om het licht beter zichtbaar te maken, verander je de 3D-wereld in nacht . In de Explorer  ⟩ Lighting , verander ClockTime  naar 0 .

 ![afbeelding](https://prod.docsiteassets.roblox.com/assets/education/coding-4/glowing-lights-setClockTime.png)

2.

Maak een nieuw onderdeel of model genaamd Lamp.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-4/glowing-lights-lightPart.jpg)

3.

Selecteer Lamp en voeg een licht  toe, zoals een PointLight of SpotLight. Je gaat werken met de helderheidseigenschap van het licht om een gloeiende lamp te creëren.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-4/florLoop_lightAdded.png)

4.

Voeg in Lamp een nieuw script toe met de naam GlowScript. Maak in dat script variabelen aan om het lampdeel en het puntlicht op te slaan.

```

local lightPart = script.Parent

local light = lightPart.SpotLight

```

Het specifieke pad naar het licht en onderdeel kan verschillen op basis van het model dat je gebruikt. Zorg ervoor dat je dit dubbel controleert in de Explorer.

5.

Maak vervolgens een variabele aan om vast te leggen hoeveel de helderheid van het licht elke keer dat de lus draait zal veranderen. Voeg daarna nog een variabele toe voor hoeveel seconden de lussen zullen wachten voordat ze opnieuw draaien.

```

-- Hoeveel de helderheid van het licht elke keer zal veranderen

local brightnessChange = 1

-- Hoe vaak in seconden het licht van helderheid zal veranderen

local timeChange = 1

```

## [Laat de lamp gloeien](#laat-de-lamp-gloeien)[](#laat-de-lamp-gloeien)

De lamp zal twee for-lussen  gebruiken, één die optelt om de lamp helderder te maken, en één die aftelt om deze te dimmen. Elke for-lus zal een controlevariabele hebben genaamd currentBrightness. Op die manier, terwijl de controlevariabele van de for-lus omhoog en omlaag gaat, zal ook de helderheid van het licht dat doen.

### [Eerste lus (lichtverhoging)](#eerste-lus-lichtverhoging)[](#eerste-lus-lichtverhoging)

Vergeet niet, een for-lus begint met het trefwoord for  gevolgd door een controlevariabele. Dit script zal de helderheidswaarde van het licht instellen op de waarde in de controlevariabele.

1.

Code de for-lus met de volgende waarden. Vergeet niet om de controlevariabele en eindwaarden met een komma te scheiden.

-

Controlevariabele : currentBrightness

-

Startwaarde : 0

-

Eindwaarde : 5

-

Verhogingswaarde : brightnessChange

```

local timeChange = 1

for currentBrightness = 0, 5, brightnessChange do

end

```

2.

Stel binnen de scope van de for-lus de helderheidseigenschap van het licht in op de waarde in de controlevariabele door te typen light.Brightness = currentBrightness . Nu, wanneer de lus draait, zal het licht helderder worden.

```

for currentBrightness = 0, 5, brightnessChange do

  light.Brightness = currentBrightness

end

```

3.

Om ervoor te zorgen dat de verandering niet in één keer gebeurt, voeg je een wachtfunctie toe met de waarde in timeChange .

```

for currentBrightness = 0, 5, brightnessChange do

   light.Brightness = currentBrightness

   task.wait(timeChange)

end

```

4.

Voer het spel uit om te zien dat het licht elke seconde in helderheid toeneemt.

Afhankelijk van de verlichting in je project, moet je mogelijk de helderheidsvariabelen of de verlichting van de omgeving aanpassen.

Als je de helderheidsverandering in de eerste lus niet kunt zien:

-

Zorg ervoor dat light.Brightness = currentBrightness  tussen de do en end van je for-lus staat.

-

Controleer of timeChange  minstens 1 of hoger is. Kleinere getallen zullen de helderheid sneller laten veranderen, maar het zal moeilijker zijn om in de loop van de tijd te zien.

-

Zorg ervoor dat de eerste regel van je for-lus in totaal twee komma's heeft die de controlevariabele, eindwaarde en verhogingswaarde scheiden.

### [Tweede lus (lichtafname)](#tweede-lus-lichtafname)[](#tweede-lus-lichtafname)

Om het licht te dimmen, gebruik je een tweede for-lus. De waarden van deze lus zullen omgekeerd zijn, zodat het licht helder begint en elke seconde dimmer wordt.

1.

Code een tweede for-lus die de helderheid in de loop van de tijd vermindert. De oplossing staat in het codevak hieronder. Gebruik de volgende waarden:

-

Controlevariabele  - currentBrightness  ingesteld op 5, het einde van de laatste lus.

-

Eind  - 0, het licht uitschakelen.

-

Verhoging  - trek brightnessChange  af.

```

-- Tweede lus dimt lamp

for currentBrightness = 5, 0, -brightnessChange do

   light.Brightness = currentBrightness

   task.wait(timeChange)

end

```

2.

Voer je spel uit; je zou moeten zien dat het licht opheldert en vervolgens dimt.

### [Laat het licht herhalen](#laat-het-licht-herhalen)[](#laat-het-licht-herhalen)

Op dit moment gaat het licht maar één keer aan en uit. Om de lamp continu te laten gloeien en uitgaan, worden de for-lussen binnen een herhalende while-lus geplaatst.

1.

Maak onder de for-lussen een nieuwe while-lus aan.

```

while true do

end

```

2.

Plaats beide for-lussen binnen een while-lus. Inspringen van de for-lussen om ze gemakkelijker te onderscheiden van de while-lus.

```

while true do

   for currentBrightness = 0, 5, brightnessChange do

      light.Brightness = currentBrightness

      task.wait(timeChange)

   end

   for currentBrightness = 5, 0, -brightnessChange do

      light.Brightness = currentBrightness

      task.wait(timeChange)

   end

end

```

3.

Voer het spel uit om te zien dat het licht continu helder en dim wordt.

## [Voltooid lichtscript](#voltooid-lichtscript)[](#voltooid-lichtscript)

Een voltooide versie van het script kan hieronder worden geraadpleegd.

```

-- Slaat het licht op dat aan deze lamp is bevestigd

lightPart = script.Parent

light = lightPart.SpotLight

-- Hoeveel de helderheid van het licht elke keer zal veranderen

local brightnessChange = 1

-- Hoe vaak in seconden het licht van helderheid zal veranderen

local timeChange = 0.2

while true do

	for count = 0, 5, brightnessChange do

	    light.Brightness = count

	task.wait(timeChange)

	end

	-- Tweede lus om licht uit te schakelen

	for count = 5, 0, -brightnessChange do

		light.Brightness = count

		task.wait(timeChange)

	end

end

```

## [Samenvatting](#samenvatting)[](#samenvatting)

Om complexe effecten in een project te creëren, kunnen scripts meerdere lussen gebruiken, en zelfs combinaties van verschillende soorten lussen. Om een gloeiend licht te coderen, zijn twee lussen genest binnen een while-lus. Terwijl programmeurs meer lussen toevoegen, is het belangrijk om de inspringing te controleren zodat de code gemakkelijk te lezen is.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-4/creating-a-timed-bridge)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-4/intro-to-for-loops)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
