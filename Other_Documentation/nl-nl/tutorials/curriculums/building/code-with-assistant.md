<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/building/code-with-assistant -->

AI Assistent | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# AI Assistent

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Assistent  is de AI-hulp van Roblox die je kan helpen bij het maken en coderen van je games. In dit hoofdstuk lopen we door hoe je Assistent in Studio opent, verzoeken schrijft die het gedrag van onderdelen veranderen, en je resultaten test om te zien of je wijzigingen aan de codevoorbeelden van de Assistent moet aanbrengen.

## [Open Assistent](#open-assistent)[](#open-assistent)

Assistent is beschikbaar in de rechterbovenhoek van deze webpagina, evenals direct in Studio. Deze tweede plaatsing stelt Assistent in staat om alles te refereren wat je game vormt, en vervolgens suggesties te doen over hoe je 3D-objecten en scripts kunt toevoegen of bewerken voor je specifieke gameplaydoelen.

 ![Assistent-knop aangegeven aan de rechterkant van de mezzaninebalk van Studio.](https://prod.docsiteassets.roblox.com/assets/tutorials/building-lesson/Mezzanine-Assistant.png)

## [Maak prompt](#maak-prompt)[](#maak-prompt)

Zodra Assistent is geopend in Studio, kan het al je platforms refereren en scripts toevoegen om hun gedrag te veranderen, zoals:

-

Van kleur veranderen elke keer dat een speler het onderdeel aanraakt.

-

Omhoog bewegen, 3 seconden wachten, en dan terug naar de vorige positie bewegen.

-

De gezondheid van de speler verminderen naarmate ze langer op het onderdeel blijven.

Om te demonstreren hoe dit proces werkt, laat dit gedeelte van de tutorial je zien hoe je met Assistent kunt werken om je eerste platform te laten schitteren telkens wanneer een speler erop springt.

Om een prompt voor dit gedrag te creëren:

1.

OPTIONEEL

 Hernoem je eerste platform zodat Assistent weet voor welk onderdeel het een script moet maken.

1.

Selecteer in de viewport je eerste platform.

2.

Klik met de rechtermuisknop op het actieve object in het Explorer -venster en selecteer Hernoemen in het contextmenu.

3.

Typ GlitterPart  en druk op Enter .

2.

Navigeer in het Assistent -venster naar het invoerveld Voer hier een verzoek in , en typ het volgende: Voeg een nieuw script toe dat gele sprankels creëert terwijl GlitterPart wordt aangeraakt .

Je kunt een andere kleur gebruiken, maar het gebruik van andere woorden kan de resultaten veranderen.

 ![](https://prod.docsiteassets.roblox.com/assets/tutorials/building-lesson/createPrompt-2.png)

3.

Druk op Enter . Assistent begint een codevoorbeeld te genereren, en vervolgens verschijnt er een venster met een voorgesteld codevoorbeeld dat vergelijkbaar is met het volgende:

```

local part = script.Parent

local sparkles = nil

local touchCount = 0

local function createSparkles()

    if not sparkles then

        sparkles = Instance.new("Sparkles")

        sparkles.Color = Color3.new(1, 1, 0) -- Geel

        sparkles.Parent = part

    end

end

local function removeSparkles()

    if sparkles then

        sparkles:Destroy()

        sparkles = nil

    end

end

part.Touched:Connect(function(hit)

    touchCount = touchCount + 1

    createSparkles()

end)

part.TouchEnded:Connect(function(hit)

    touchCount = touchCount - 1

    if touchCount <= 0 then

        removeSparkles()

        touchCount = 0

    end

end)

```

Assistent leert voortdurend, dus het kan zijn dat het niet altijd dezelfde resultaten oplevert voor exact hetzelfde verzoek.

4.

Klik op Accepteren . Naarmate je meer leert over coderen met Luau, zal het gemakkelijker worden om de codevoorbeelden van Assistent te beoordelen om ervoor te zorgen dat ze werken voor jouw gebruiksgevallen.

Er is meer dan één juiste manier om een bepaald verzoek te doen, maar elk woord telt. Bijvoorbeeld, de volgende tabel toont aan hoe zelfs iets andere woordkeuzes dan de oorspronkelijke prompt verschillende resultaten kunnen opleveren.

| Variatie van Verzoek | | Mogelijke Resultaten |
| --- | --- |
| Creëer gele sprankels terwijl GlitterPart wordt aangeraakt. | | Assistent kan je de code tonen, maar geen nieuw script maken. Het kan ook de code aan een willekeurig bestaand script toevoegen. |
| Maak paarse sprankels wanneer het onderdeel genaamd GlitterPart wordt betreden. | | Assistent kan sprankels maken voordat GlitterPart wordt betreden, of slechts een paar sprankels maken. |
| Laat GlitterPart schitteren | | In plaats van een script toe te voegen, zal Assistent gewoon een deeltjesemitter (het object dat sprankels maakt) aan GlitterPart toevoegen. Wat goed kan zijn als je wilt dat het altijd schittert. |

Hoe minder details je geeft, hoe onvoorspelbaarder de resultaten. Bijvoorbeeld, mogelijke resultaten voor de prompt Laat onderdelen schitteren wanneer je ze aanraakt kunnen zijn:

-

Het resulterende script werkt helemaal niet.

-

Slechts één willekeurig onderdeel werkt.

-

Onderdelen schitteren voordat ze worden aangeraakt.

Als je een verzoek doet en niet de gewenste resultaten krijgt, herformuleer het verzoek en probeer het opnieuw.

Per ongeluk een suggestie geaccepteerd die je niet wilde? Je kunt de wijziging ongedaan maken met een van de volgende methoden:

-

Voor niet-scriptwijzigingen, druk op Ctrl Z  of ⌘ Z , afhankelijk van je computer.

-

Als Assistent een script heeft gemaakt, klik dan op de naam van het script in het Explorer -venster en druk op Delete .

## [Test resultaten](#test-resultaten)[](#test-resultaten)

Hoewel Assistent voortdurend leert en beter wordt, produceert het soms resultaten die anders zijn dan je bedoelde. Je moet altijd de resultaten van zijn suggesties controleren om ervoor te zorgen dat ze werken zoals bedoeld.

Om de resultaten van Assistent te testen:

1.

In de linkerbovenhoek van Studio, houd de standaard Test  playtestoptie aan en klik op de Speel -knop. Studio gaat naar de playtestmodus.

 ![](https://prod.docsiteassets.roblox.com/assets/education/general/play-button.png)

2.

Spring in het spel op het eerste platform. Als het codevoorbeeld correct werkt, verschijnen er gele sprankels wanneer je personage het onderdeel aanraakt.

3.

Wanneer je klaar bent met het verifiëren van de resultaten, ga je terug naar de linkerbovenhoek van Studio en klik je op de Stop -knop. Studio verlaat de playtestmodus.

 ![](https://prod.docsiteassets.roblox.com/assets/education/general/stop-button.png)

4.

OPTIONEEL

 Ga terug naar het Assistent-venster en druk op het duim omhoog of duim omlaag pictogram om Assistent te laten weten of het codevoorbeeld werkte zoals je bedoelde.

Nu je weet hoe je met Assistent kunt coderen, probeer je je eigen prompts te maken om te veranderen hoe onderdelen zich gedragen in je obby. Wanneer je tevreden bent met je creatie, ga dan verder naar het volgende gedeelte van de tutorial om je werk te testen en op te slaan naar Roblox.

[Volgende](/docs/nl-nl/tutorials/curriculums/building/test-and-save)[Vorige](/docs/nl-nl/tutorials/curriculums/building/work-with-parts)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
