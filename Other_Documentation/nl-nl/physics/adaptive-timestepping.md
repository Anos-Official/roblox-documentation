<!-- Source: https://create.roblox.com/docs/nl-nl/physics/adaptive-timestepping -->

Adaptieve tijdstappen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Fysica](/docs/nl-nl/physics)

# Adaptieve tijdstappen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Roblox-fysica-engine simuleert alle onderdelen in de 3D-werkruimte via de tweede wet van Newton. Deze bewegingswet wordt in de tijd opgelost via tijdstappen  en een enkele tijdstap wordt uitgevoerd binnen een wereldstap  in Roblox.

Standaard simuleert Roblox fysica op 240 Hz. Gegeven cycli van ongeveer 60 frames per seconde, worden er ongeveer 4 wereldstappen per frame geavanceerd. Met adaptieve tijdstappen  wijst de fysica-engine automatisch onderdelen toe aan drie "oplosser eilanden" door hun simulatie tijdstap te variëren, met de nadruk op 60 Hz voor de beste prestaties. Onderdelen die "moeilijker" op te lossen zijn, gebruiken echter een snellere tijdstap zoals 240 Hz om fysieke stabiliteit te waarborgen.

 ![](https://prod.docsiteassets.roblox.com/assets/physics/adaptive-timestepping/Diagram-Labels.png)

Toewijzingscriteria kunnen veranderen, maar onderdelen die aan het 240 Hz-eiland zijn toegewezen, omvatten [assemblages](/docs/nl-nl/physics/assemblies)  met hoge snelheidwaarden, hoge versnellingwaarden en complexe mechanismen die moeilijk op te lossen zijn.

## [Schakel de adaptieve modus in](#schakel-de-adaptieve-modus-in)[](#schakel-de-adaptieve-modus-in)

Om adaptieve tijdstappen in Studio in te schakelen:

1.

Selecteer het Workspace -object in het Explorer -venster.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Workspace.png)

2.

Zoek in het Properties -venster naar PhysicsSteppingMethod  en selecteer Adaptive .

 ![](https://prod.docsiteassets.roblox.com/assets/physics/adaptive-timestepping/PhysicsSteppingMethod-Adaptive.png)

Om het tijdstappenproces in actie te observeren, kun je de Studio Microprofiler  openen (Ctrl F6 ; ⌘ F6 ). Zodra het spel draait, druk je op Ctrl P  (⌘ P ) om te pauzeren bij het huidige frame.

Onder de scope genaamd physicsStepped , observeer dat de scopenaam van worldStep  nu worldStep - Adaptive  leest.

 ![](https://prod.docsiteassets.roblox.com/assets/physics/adaptive-timestepping/Adaptive-Timestepping-Microprofiler-A.png)

Als je met de cursor boven LDLPGSSolver::solve  zweeft, zie je de status van hoeveel eilanden in elke frequentie-emmer behoren; 1dt Eilanden  (240 Hz), 2dt Eilanden  (120 Hz) en 4dt Eilanden  (60 Hz).

 ![](https://prod.docsiteassets.roblox.com/assets/physics/adaptive-timestepping/Adaptive-Timestepping-Microprofiler-B.png)

## [Debugvisualisatie](#debugvisualisatie)[](#debugvisualisatie)

Tijdens het testen kan het nuttig zijn om frequenties voor gesimuleerde onderdelen te visualiseren. Om deze optie in te schakelen:

1.

Open [Studio-instellingen](/docs/nl-nl/studio/setup#aanpassing) .

2.

Schakel onder het tabblad Physics  de optie Are Timesteps Shown  in.

Zodra deze optie is ingeschakeld, worden gesimuleerde onderdelen omrand door hun huidige simulatiesnelheid. Als een onderdeel stopt met simuleren, hetzij via het [slaapsysteem](/docs/nl-nl/physics/sleep-system)  of een wijziging in netwerkbezit, wordt het onderdeel niet langer omrand.

 ![](https://prod.docsiteassets.roblox.com/assets/physics/adaptive-timestepping/Diagram-Labels.png)

Gesimuleerde onderdelen omrand door de kleur die hun huidige simulatiesnelheid vertegenwoordigt

## [Scenario's met vaste snelheid](#scenarios-met-vaste-snelheid)[](#scenarios-met-vaste-snelheid)

Adaptieve tijdstappen kunnen de fysica-prestaties tot 2,5 keer verbeteren en worden in de meeste gevallen aanbevolen. Sommige spellen moeten echter de Fixed -modus (240 Hz) gebruiken, waaronder:

Spellen die zeer nauwkeurige simulaties en stabiliteit vereisen, zoals racespellen, "vernietiging" simulaties of spellen met complexe mechanismen zoals tanks.

Simulaties waarbij de meeste onderdelen standaard naar het 240 Hz-oplosser eiland gaan (rode omrandingen tijdens [debugging](#debugvisualisatie) ). Wanneer 240 Hz-eilanden interageren met eilanden van verschillende frequenties (60–120 Hz), worden die eilanden omgezet naar 240 Hz met een overhead die eventuele prestatieverbeteringen als gevolg van adaptieve tijdstappen kan tenietdoen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
