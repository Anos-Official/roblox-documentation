<!-- Source: https://create.roblox.com/docs/nl-nl/assistant/prompt-engineering -->

Assistent promptgids en voorbeelden | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Studio](/docs/nl-nl/studio)
4. /
5. [Assistant](/docs/nl-nl/assistant/guide)

# Assistent promptgids en voorbeelden

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

[Deel je prompts en games](https://devforum.roblox.com/t/check-out-the-generative-ai-stream-and-let-us-know-your-best-prompts/3215844)  in het Roblox-forum zodat we de Assistent beter kunnen maken!

Dit document geeft richtlijnen voor het aansteken van de Assistent en biedt voorbeelden en inspiratie over wat de Assistent kan doen.

## [Beste praktijken](#beste-praktijken)[](#beste-praktijken)

Deze beste praktijken kunnen je helpen betere resultaten te behalen bij het gebruik van de Assistent. Probeer ze uit en kijk wat het beste werkt voor jouw workflow.

### [Wees specifiek](#wees-specifiek)[](#wees-specifiek)

Als de Assistent faalt, voeg dan meer details toe aan je prompt en probeer het opnieuw. Gebruik instantiënamen precies zoals ze zijn gespeld, specificeer welke functie je wilt dat de Assistent gebruikt, en vertel de Assistent met welk type hij werkt, zoals een onderdeel of een model.

| Niet specifiek | | Meer specifiek |
| --- | --- |
| Plaats de bomen in een cirkel. | | Plaats 10 kopieën van het "pine_tree" model in ReplicatedStorage in een cirkel met een straal van 30 studs rond de SpawnLocation. |
| Laat het onderdeel bewegen. | | Voeg een script toe om "my_part" 10 studs omhoog en omlaag te laten bewegen met TweenService. |
| Hoe kan ik een kernloop ontwerpen? | | Help me een leuke kernloop te ontwerpen. Ik wil een spel bouwen waarin spelers als piraten schatten kunnen jagen. Ze kunnen ook piratenschepen kopen en upgraden en tegen elkaar vechten. |

### [Gebruik je selectie](#gebruik-je-selectie)[](#gebruik-je-selectie)

Selectie is een geweldige manier om een object of set objecten aan te geven waar je naar wilt verwijzen in je prompt. Selecteer meerdere objecten en vraag de Assistent om ze te wijzigen, duplicaten te maken en ze ergens te plaatsen, of om een positiepatroon voort te zetten, zoals het behouden van plaatsing in een lijn.

### [Bewerkingstijd en uitvoeringstijd](#bewerkingstijd-en-uitvoeringstijd)[](#bewerkingstijd-en-uitvoeringstijd)

De Assistent verwart soms het verschil tussen bewerkingstijd en uitvoeringstijd. Als je de Assistent vraagt om een actie uit te voeren, zal hij waarschijnlijk de voorkeur geven aan het doen ervan tijdens de bewerkingstijd. Als je wilt dat de actie tijdens de uitvoeringstijd plaatsvindt, vraag dan de Assistent om een script in te voegen dat de actie uitvoert. Zeg bijvoorbeeld tegen de Assistent "voeg een script toe om de tijd van de dag 8:00 AM te maken" in plaats van "maak de tijd van de dag 8:00 AM."

### [Multi-stap prompts](#multi-stap-prompts)[](#multi-stap-prompts)

Overweeg om multi-stap prompts te gebruiken om de Assistent aan te moedigen na te denken. In plaats van te vragen "Kun je dit script aan me uitleggen?" en het script in te voegen, vraag het om stap voor stap uit te leggen door de vraag van het script te scheiden met ### . Deze scheiding helpt de Assistent om de informatie te ontleden en te organiseren om betere antwoorden te geven.

Prompt Assistant response

* Kun je uitleggen wat dit script stap voor stap doet?*

###

* local part = workspace.Part*

* local function onTouched(otherPart)*
 * print(part.Name .. " botste tegen " .. otherPart.Name)*
 * end*

* part.Touched:Connect(onTouched)*

###

### [Prompten voor assetgeneratie](#prompten-voor-assetgeneratie)[](#prompten-voor-assetgeneratie)

Bij het genereren van assets, begin met het benoemen van het object en voeg geleidelijk details toe over het uiterlijk. De Assistent bepaalt automatisch de camerahoek, achtergrond en verlichting, dus je hoeft alleen het object zelf te beschrijven.

| Prompt | | Resultaat |
| brievenbus | | Genereert een basis brievenbus. |
| blauwe metalen brievenbus | | Voegt kleur en materiaal toe. |
| verweerde blauwe metalen brievenbus met een rode vlag | | Voegt ouderdom en onderscheidende kenmerken toe. |
| verweerde blauwe metalen brievenbus bedekt met barnacles en koraal, met schelpen rond de basis | | Produceert een meer specifieke en onderscheidende asset. |

Vermijd het beschrijven van de afbeelding in plaats van het object. Bijvoorbeeld, sluit niet in:

-

Achtergronden of omgevingen, zoals "witte achtergrond"  of "studio achtergrond" .

-

Camerahoeken of compositie, zoals "3/4 aanzicht"  of "vooraanzicht" .

-

Verlichting, zoals "schone schaduwen"  of "cinematografische verlichting" .

-

Algemene kwaliteitsbegrippen, zoals "hoge kwaliteit"  of "4K" .

### [Prompten voor procedurele modelgeneratie](#prompten-voor-procedurele-modelgeneratie)[](#prompten-voor-procedurele-modelgeneratie)

Procedurele modelgeneratie kan langer duren dan tekstreacties. Om efficiënt te blijven werken, kun je doorgaan met typen van je volgende prompt terwijl de Assistent je model genereert.

Bij het schrijven van prompts voor procedurele modellen, zorg ervoor dat je expliciet de eigenschappen en parameters opgeeft die je wilt kunnen bewerken. Bijvoorbeeld, je kunt de Assistent vragen om "eigenschappen toe te voegen om de kleuren van de cabine te veranderen."

Het is ook nuttig om te definiëren hoe verschillende delen van het model moeten reageren op veranderingen in schaal of aantal. Bijvoorbeeld, je kunt zeggen "wanneer ik de tafel langer of breder maak, moet het model meer stoelen proportioneel toevoegen." Je kunt zelfs specifieke technische details opnemen, zoals afmetingen van de ruimte tussen onderdelen, zoals "voeg een eigenschap toe om de afstand tussen de rails van de spoorlijn te regelen."

#### Referentieafbeeldingen voor procedurele modellen

Bij het uploaden van afbeeldingen voor procedurele modelgeneratie, gebruik .png  afbeeldingen. Kies afbeeldingen met goede verlichting, een duidelijke focus op het object van interesse, en een eenvoudige achtergrond. Gebruik waar mogelijk afbeeldingen met goede ruimtelijke informatie, zoals isometrische of 3/4 hoeken, in plaats van directe voor-, zij- of achteraanzichten. Vermijd low-poly stijl afbeeldingen.

Voor objecten die niet volledig vanuit één hoek kunnen worden vastgelegd, kun je meerdere gezichtspunten in één afbeelding opnemen om de nauwkeurigheid van de procedurele modelgeneratie te verbeteren.

### [Blijf proberen](#blijf-proberen)[](#blijf-proberen)

Laat je niet ontmoedigen als de Assistent niet precies werkt zoals je wilt de eerste keer. Vaak kunnen kleine aanpassingen en het opnieuw proberen leiden tot betere resultaten. Veel AI-tools zijn niet-deterministisch, wat betekent dat ze niet elke keer dezelfde output creëren wanneer je ze iets vraagt. Er is enige variatie, die je kunt benutten en beheersen met aanpassingen aan je prompt.

AI in zijn huidige staat vereist werk. Het kost tijd om te begrijpen hoe je het beste met de Assistent kunt communiceren, wat het kan doen, en hoe je eruit kunt halen wat je wilt.

## [Voorbeelden](#voorbeelden)[](#voorbeelden)

Deze voorbeelden demonstreren de enorme verscheidenheid aan taken waarmee de Assistent vandaag kan helpen. Sommige van hen hebben misschien een paar pogingen nodig om te reproduceren, maar probeer ze uit en kijk wat je zelf kunt bedenken.

### [Spelmechanica - Schiet vuurballen die exploderen](#spelmechanica---schiet-vuurballen-die-exploderen)[](#spelmechanica---schiet-vuurballen-die-exploderen)

Prompt:  Stoot een vuurbal weg van de speler in de richting waarin de speler kijkt wanneer de speler "e" indrukt. Laat de vuurbal exploderen wanneer deze iets raakt.

### [Spelmechanica - Stel een teamsysteem in en wijs spelers toe](#spelmechanica---stel-een-teamsysteem-in-en-wijs-spelers-toe)[](#spelmechanica---stel-een-teamsysteem-in-en-wijs-spelers-toe)

Prompt:  Voeg een script toe om een systeem van teams (rood, blauw, groen, geel) in te stellen en wijs elke speler willekeurig aan een team toe.

### [Spelmechanica - Tempelrun-stijl constant rennen](#spelmechanica---tempelrun-stijl-constant-rennen)[](#spelmechanica---tempelrun-stijl-constant-rennen)

Prompt:  Laat mijn personage constant vooruit rennen zoals in een tempelrun-spel.

### [Spelmechanica - Vuurkracht-up](#spelmechanica---vuurkracht-up)[](#spelmechanica---vuurkracht-up)

Prompt:  Voeg een script toe dat de speler in brand steekt en 3 keer zo hoog laat springen als ze "q" indrukken. Het vuur moet aan de speler vastzitten en met hen meebewegen. Als ze "q" opnieuw indrukken, zet het vuur uit en reset de springkracht.

### [Spelmechanica - NPC-lasers](#spelmechanica---npc-lasers)[](#spelmechanica---npc-lasers)

Prompt:  Voeg een script toe dat dit een laser laat schieten met een lang dun onderdeel dat blauw en neon is naar de speler als ze binnen 30 studs zijn.

Voeg een script toe om dit naar de dichtstbijzijnde speler te laten kijken en langzaam naar hen toe te bewegen als ze binnen 50 studs zijn. Beweeg alleen in de x- en z-assen, houd de y-as constant.

### [Spelmechanica - Interactieve NPC](#spelmechanica---interactieve-npc)[](#spelmechanica---interactieve-npc)

Prompt:  Dit is een NPC. Voeg een prompt toe die de speler in staat stelt om ermee te interageren. Als de speler interageert, laat de NPC "hallo [naam van de speler]" zeggen, waarbij de naam van de speler de daadwerkelijke naam van de speler is, in een tekstpop-up.

Voeg een script toe dat deze NPC altijd naar de dichtstbijzijnde speler laat kijken.

### [Spelmechanica - NPC patrouilleren](#spelmechanica---npc-patrouilleren)[](#spelmechanica---npc-patrouilleren)

Prompt:  Voeg een script toe om deze NPC langzaam tussen startpart en eindpart te laten bewegen, herhaaldelijk. Het moet naar het onderdeel kijken en dan er naartoe bewegen, en dan naar het andere onderdeel kijken en er naartoe bewegen. Als de speler binnen 10 studs komt, maak de NPC rood en laat hem de speler achtervolgen.

### [Spelmechanica - Scorebord bijwerken](#spelmechanica---scorebord-bijwerken)[](#spelmechanica---scorebord-bijwerken)

Prompt:  Voeg een script toe dat dit verwijdert en 100 aan de score van de spelers toevoegt.

Voeg een script toe om de score van de speler op het scorebord weer te geven.

### [Camera - Vergrendel in top-down](#camera---vergrendel-in-top-down)[](#camera---vergrendel-in-top-down)

Prompt:  Voeg een script toe dat de camera in een top-down weergave op de speler vergrendelt en de speler volgt, zodat de speler in het midden van het scherm blijft.

### [Camera - Vergrendel in eerste persoon](#camera---vergrendel-in-eerste-persoon)[](#camera---vergrendel-in-eerste-persoon)

Prompt:  Maak een script om de camera in de eerste persoon te vergrendelen.

### [UI - Dropdownmenu](#ui---dropdownmenu)[](#ui---dropdownmenu)

Prompt:  Maak een dropdownmenu met 5 items.

### [UI - Gezondheidsbalk](#ui---gezondheidsbalk)[](#ui---gezondheidsbalk)

Prompt:  Voeg een onderdeel op de grond toe, wanneer een speler het aanraakt, vermindert het de gezondheid met 10%. Plaats een UI gezondheidsbalk in het bovenste midden van het scherm die rood wordt wanneer de gezondheid van de speler minder dan 20% is.

### [UI - Eenvoudige HUD](#ui---eenvoudige-hud)[](#ui---eenvoudige-hud)

Prompt:  Maak een heads-up display in StarterGui. Voeg een gezondheidsbalk toe in de rechterbovenhoek, en een tekstlabel met de naam van de speler eronder. Voeg rechtsonder 4 knoppen in een diamantvorm toe, met "Potion" bovenaan, "Wapens" aan de linkerkant, "Inventaris" onderaan, en "Speciaal" aan de rechterkant. Maak de kleuren thematisch voor de herfst.

 ![](https://prod.docsiteassets.roblox.com/assets/assistant/prompt10.png)

### [Bouwen - Verspreid objecten met randomisatie](#bouwen---verspreid-objecten-met-randomisatie)[](#bouwen---verspreid-objecten-met-randomisatie)

Prompt:  Voeg 0-5 van de geselecteerde instantie "Paddenstoel" toe rond elke "RedwoodTree-Var01".

### [Bouwen - Nacht / dag cyclus met straatlantaarns](#bouwen---nacht--dag-cyclus-met-straatlantaarns)[](#bouwen---nacht--dag-cyclus-met-straatlantaarns)

Prompt:  Voeg een script toe dat de tijd van de dag elke seconde met 1 uur verandert. Begin om 15:00 uur. Om 19:00 uur, zet de helderheid van elke schijnwerper op 10. Om 08:00 uur, zet de helderheid van elke schijnwerper op 0.

### [Bouwen - Fysica-gebaseerde hangbrug](#bouwen---fysica-gebaseerde-hangbrug)[](#bouwen---fysica-gebaseerde-hangbrug)

Prompt:  Maak een touwbrug. Maak 10 houten planken die 5 studs breed en 2 studs lang zijn. Plaats ze in een rij. Voeg touwbeperkingen toe aan elke kant van de onderdelen, die elk verbinden met het onderdeel ervoor en erna. Maak alle touwbeperkingen zichtbaar, veranker het 1e en 10e onderdeel, en voeg een sleepdetector toe aan het 1e en 10e onderdeel.

 ![](https://prod.docsiteassets.roblox.com/assets/assistant/prompt12.png)

### [Bouwen - Voeg rook toe aan schoorstenen](#bouwen---voeg-rook-toe-aan-schoorstenen)[](#bouwen---voeg-rook-toe-aan-schoorstenen)

Prompt:  Voeg een onzichtbare baksteen toe die niet-collideerbaar is in elke schoorsteen in elk huis. De baksteen moet een deeltje erin hebben dat rook maakt die omhoog stroomt, en de rook moet wit zijn.

### [Bouwen - Hernoem instanties](#bouwen---hernoem-instanties)[](#bouwen---hernoem-instanties)

Prompt:  Hernoem alle "emptyscripts" objecten naar "Script+uniqueID".

### [Bouwen - Maak terrein](#bouwen---maak-terrein)[](#bouwen---maak-terrein)

Prompt:  Maak een terreinregio met glooiende heuvels.

 ![](https://prod.docsiteassets.roblox.com/assets/assistant/prompt6.png)

### [Bouwen - Voeg gedrag toe op schaal](#bouwen---voeg-gedrag-toe-op-schaal)[](#bouwen---voeg-gedrag-toe-op-schaal)

Prompt:  Voeg een script toe om de schijnwerpers in de map StreetLights willekeurig aan en uit te laten knipperen.

### [Bouwen - Vervang grijze dozen door assets](#bouwen---vervang-grijze-dozen-door-assets)[](#bouwen---vervang-grijze-dozen-door-assets)

Prompt:  Vervang elk van de geselecteerde onderdelen door een model met dezelfde naam dat momenteel in het datamodel in de AssetLibrary-map onder workspace staat. Bijvoorbeeld, als het onderdeel "Suburban House" heet, zoek dan naar een model genaamd "Suburban House" en vervang het onderdeel door dat model.

### [Bouwen - Maak een schaalbare reuzenrad](#bouwen---maak-een-schaalbare-reuzenrad)[](#bouwen---maak-een-schaalbare-reuzenrad)

Prompt:  /generate_procedural_model Maak een cartoon-thema reuzenrad met een basis met een hek en een poort eromheen. Voeg eigenschappen toe om het aantal cabines op het reuzenrad te bewerken. Wanneer het aantal cabines verandert, moet de ruimte tussen hen ook proportioneel veranderen. Voeg ook eigenschappen toe om de kleur van elke individuele cabine te veranderen.

### [Bouwen - Maak een modulaire treinrails](#bouwen---maak-een-modulaire-treinrails)[](#bouwen---maak-een-modulaire-treinrails)

Prompt:  /generate_procedural_model Maak een modulair stuk treinrails dat opnieuw kan worden gebruikt in verschillende secties. Voeg een eigenschap toe om de kromming van de rails van 0-90 graden te regelen om bochten mogelijk te maken. Inclusief eigenschappen om de afstand tussen de rails, de spoorwijdte (railgrootte), de ruimte tussen de spoorbalken, en de totale lengte van de rails aan te passen.

### [Bouwen - Maak een modulaire middeleeuwse kasteel](#bouwen---maak-een-modulaire-middeleeuwse-kasteel)[](#bouwen---maak-een-modulaire-middeleeuwse-kasteel)

Prompt:  /generate_procedural_model Een gestileerd, rond middeleeuws kasteel met een rode bakstenen basis, een wit gepleisterde bovenlaag, en een groot terracotta conisch dak. Een enkele, dominante landmarktoren staat naast talloze kleine, slanke torentjes, allemaal verankerd door groene struiken.

### [Bouwen - Maak een modulaire hangbrug](#bouwen---maak-een-modulaire-hangbrug)[](#bouwen---maak-een-modulaire-hangbrug)

Prompt:  /generate_procedural_model Een procedurele brug die het aantal ophangkabels aanpast op basis van de lengte en een 'Roest' materiaaleigenschap heeft om het materiaaltype te veranderen.

### [Bouwen - Maak een schaalbare eetset](#bouwen---maak-een-schaalbare-eetset)[](#bouwen---maak-een-schaalbare-eetset)

Prompt:  /generate_procedural_model Een cyberpunk-geïnspireerde eetset met tafel en stoelen. Wanneer ik de tafel schaal en deze langer of breder maak, voeg dan meer stoelen proportioneel toe.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
