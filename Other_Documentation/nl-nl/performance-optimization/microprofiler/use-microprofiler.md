<!-- Source: https://create.roblox.com/docs/nl-nl/performance-optimization/microprofiler/use-microprofiler -->

MicroProfiler walkthrough | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization)
6. /
7. [MicroProfiler](/docs/nl-nl/performance-optimization/microprofiler)

# MicroProfiler walkthrough

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Deze walkthrough laat zien hoe je de MicroProfiler kunt gebruiken om een problematisch aspect van een game te vinden en de oorzaak te identificeren. Download de game, Open from File  in Studio, en volg mee.

 [Download de game](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/RaycastSpam.rbxl)

## [Identificeer het probleem](#identificeer-het-probleem)[](#identificeer-het-probleem)

1.

Nadat je de game in Studio hebt geopend, begin je met testen met F5  of de Speel  knop.

2.

De framerate voelt redelijk aan, maar is niet zo soepel als het zou moeten zijn voor een game van deze grootte en scope. Druk op Ctrl Shift F5  (⌘ Shift F5 ) om de Prestatieoverzicht  overlay te tonen.

 ![Prestatieoverzicht toont 45 FPS.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-framerate.png)

Let op dat de framerate onder de 60 frames per seconde (FPS) ligt.

3.

Open de MicroProfiler door Ctrl Alt F6  (⌘ ⌥ F6 ) in te drukken.

 ![De MicroProfiler na het openen.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-bar-graph.png)

Let op dat de frame tijden consistent  zijn—de balken zijn ongeveer even hoog—dus wat de lage framerate veroorzaakt, draait elke frame in plaats van af en toe te draaien en frame tijdspikes te veroorzaken.

4.

Pauzeer de MicroProfiler door Ctrl P  (⌘ P ) in te drukken. Pauzeren met de sneltoets opent [gedetailleerde modus](/docs/nl-nl/performance-optimization/microprofiler/modes#detailed-mode) .

5.

Klik en sleep om de grafiek te pannen. Let op hoe een bepaalde taak in de worker threads veel verwerkings tijd lijkt te gebruiken in vergelijking met de hoofdthread. Beweeg de muis over [RunService.Stepped](/docs/nl-nl/reference/engine/classes/RunService#Stepped)  en let op hoe lang het duurt om te renderen.

 ![Gedetailleerde modus met lange labels voor processen.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-stepped.png)

6.

Gestapelde balken in de tijdlijn geven een hiërarchie van code aan, dus blijf over lagere lagen bewegen om te proberen het probleem te identificeren.

 ![On-hover details voor verschillende processen, met LocalScript gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-localscript.png)  ![On-hover details voor verschillende processen, met Raycast gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-raycast-label.png)

Let op het LocalScript  label, dat de naam van het script aangeeft, en het Raycast  label, dat aangeeft dat het probleem mogelijk gerelateerd is aan raycasting.

## [Maak probleemoplossingslabels](#maak-probleemoplossingslabels)[](#maak-probleemoplossingslabels)

Nu de MicroProfiler een startpunt heeft gegeven, kun je de problematische code oplossen.

1.

Stop de speelsessie en filter het Explorer-venster op localscript  om het bestand te vinden.

 ![Een weergave van het filteren in het Explorer-venster.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-explorer-filter.png)

Een zoekopdracht naar raycast  geeft aan dat dit deel van de code waarschijnlijk de schuldige is voor de slechte prestaties van de game:

```

local RAYS_PER_SECOND = 1500

local function onStepped()

	for _ = 1, RAYS_PER_SECOND do

		local startPosition = getRandomPosition()

		local endPosition = getRandomPosition()

		local direction = endPosition - startPosition

		Workspace:Raycast(

         startPosition,

         endPosition

      )

	end

end

RunService.Stepped:Connect(onStepped)

```

Specifiek zie je dat de code 1.500 stralen per seconde in willekeurige richtingen cast.

2.

Om te verifiëren dat dit deel van de code de renderingvertraging veroorzaakt, wikkel je de inhoud van de functie in [debug.profilebegin()](/docs/nl-nl/reference/engine/libraries/debug#profilebegin)  en [debug.profileend()](/docs/nl-nl/reference/engine/libraries/debug#profileend) :

```

local function onStepped()

   debug.profilebegin("Raycast Spam")

   for _ = 1, RAYS_PER_SECOND do

      local startPosition = getRandomPosition()

      local endPosition = getRandomPosition()

      local direction = endPosition - startPosition

      Workspace:Raycast(

         startPosition,

         endPosition

      )

   end

   debug.profileend()

end

```

## [Bevestig en los het probleem op](#bevestig-en-los-het-probleem-op)[](#bevestig-en-los-het-probleem-op)

1.

Begin met het testen van de game en open de MicroProfiler opnieuw.

2.

Let op hoe de MicroProfiler nu het aangepaste label toont, wat aangeeft dat deze functie inderdaad de oorzaak was.

 ![MicroProfiler gedetailleerd overzicht met 'Raycast Spam' zichtbaar.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-spam.png)

3.

Stop de speelsessie.

4.

Verwijder of commentarieer de onStepped()  functie en de RunService.Stepped:Connect(onStepped)  verbinding.

5.

Begin de game opnieuw te testen en controleer het Prestatieoverzicht  opnieuw.

 ![Prestatieoverzicht toont 60 FPS.](https://prod.docsiteassets.roblox.com/assets/optimization/microprofiler/micro-tut-framerate2.png)

Let op de enorme verbetering van de framerate en de bijbehorende daling van de frame tijden op de MicroProfiler-grafiek.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
