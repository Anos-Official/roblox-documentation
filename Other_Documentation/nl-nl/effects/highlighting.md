<!-- Source: https://create.roblox.com/docs/nl-nl/effects/highlighting -->

Objecten markeren | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Effecten](/docs/nl-nl/effects)

# Objecten markeren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  instantie is een visueel effect dat je kunt gebruiken om de aandacht te vestigen op een specifiek object binnen een spel. Elk markeer effect heeft een silhouet omtrek  die het object omringt en een solide overlay interieur  die over het object wordt weergegeven. Je kunt beide componenten onafhankelijk aanpassen om het visuele uiterlijk van de markering te wijzigen.

![Een boom mesh tegen een grijze achtergrond.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/OutlineTransparency-1.jpg) Basisobject

![Dezelfde boom mesh met een gele omtrek en een zwart markeerinterieur.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/Overview-Yellow-Outline.jpg) Geel omtrek en zwart interieur

![Dezelfde boom mesh met een zwarte omtrek en een geel markeerinterieur.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/Overview-Yellow-Interior.jpg) Zwarte omtrek en geel interieur

Nuttige toepassingen van het markeer effect zijn onder andere:

-

Visuele feedback geven dat een object belangrijk en/of interactief is.

-

Distantieobjecten zichtbaar maken door objecten die dichter bij de gebruiker zijn.

-

De huidige positie en status van andere personages aangeven.

## [Markeringen toevoegen](#markeringen-toevoegen)[](#markeringen-toevoegen)

Als prestatiebeperking toont Studio slechts 255 gelijktijdige [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  instanties aan de clientzijde tegelijk. Als je meer dan deze limiet toevoegt, worden de extra [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  instanties stilletjes genegeerd.

Houd er ook rekening mee dat markeringen op low-end apparaten mogelijk meer gepixeld zijn, maar verder hetzelfde eruitzien als op andere apparaten met elke combinatie van instellingen.

### [Ouders van objecten](#ouders-van-objecten)[](#ouders-van-objecten)

Om een markeer effect aan een object toe te voegen, kun je een nieuwe [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  direct aan het object koppelen.

1.

In het Explorer  venster, beweeg de muis over een [Model](/docs/nl-nl/reference/engine/classes/Model)  of een [BasePart](/docs/nl-nl/reference/engine/classes/BasePart) , en klik vervolgens op de ⊕ knop. Een contextmenu wordt weergegeven.

2.

Kies in het menu voor een Highlight . De markering wordt op het object weergegeven met de standaard eigenschapswaarden die een witte omtrek en een rode tint overlay creëren.

 ![](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/Adding-Highlight.jpg)

### [Stel de adornee in](#stel-de-adornee-in)[](#stel-de-adornee-in)

Alternatief kun je de [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  instantie buiten een kind/ouder relatie plaatsen, hetzij binnen de workspace, [StarterPlayer](/docs/nl-nl/reference/engine/classes/StarterPlayer) , [StarterGui](/docs/nl-nl/reference/engine/classes/StarterGui) , [StarterPack](/docs/nl-nl/reference/engine/classes/StarterPack) , of [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) , en vervolgens de [Adornee](/docs/nl-nl/reference/engine/classes/Highlight#Adornee)  eigenschap instellen op het [Model](/docs/nl-nl/reference/engine/classes/Model)  of [BasePart](/docs/nl-nl/reference/engine/classes/BasePart)  dat je wilt markeren.

## [Markeringen aanpassen](#markeringen-aanpassen)[](#markeringen-aanpassen)

Je kunt de eigenschappen van een [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  instantie wijzigen om interessante visuele effecten te creëren die objecten op een thematische manier markeren in overeenstemming met je spel.

### [OutlineColor](#outlinecolor)[](#outlinecolor)

De [OutlineColor](/docs/nl-nl/reference/engine/classes/Highlight#OutlineColor)  eigenschap stelt de [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  waarde van de omtrek van de markering in.

![Een boom mesh met rode omtrek.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/OutlineColor-Red.jpg) OutlineColor = [255, 100, 50]

![Een boom mesh met groene omtrek.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/OutlineColor-Green.jpg) OutlineColor = [0, 255, 125]

![Een boom mesh met blauwe omtrek.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/OutlineColor-Blue.jpg) OutlineColor = [75, 150, 255]

### [OutlineTransparency](#outlinetransparency)[](#outlinetransparency)

De [OutlineTransparency](/docs/nl-nl/reference/engine/classes/Highlight#OutlineTransparency)  eigenschap stelt de zichtbaarheid van de omtrek van de markering in op een waarde tussen de standaardwaarde van 0  (opake) en 1  (onzichtbaar).

![Een boom mesh met zwarte opake omtrek.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/OutlineTransparency-0.jpg) OutlineTransparency = 0

![Een boom mesh met transparante omtrek.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/OutlineTransparency-1.jpg) OutlineTransparency = 1

### [FillColor](#fillcolor)[](#fillcolor)

De [FillColor](/docs/nl-nl/reference/engine/classes/Highlight#FillColor)  eigenschap stelt de [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  waarde van het interieur van de markering in.

![Een boom mesh met een rode vulling.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/FillColor-Red.jpg) FillColor = [255, 100, 50]

![Een boom mesh met een groene vulling.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/FillColor-Green.jpg) FillColor = [0, 255, 125]

![Een boom mesh met een blauwe vulling.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/FillColor-Blue.jpg) FillColor = [75, 150, 255]

### [FillTransparency](#filltransparency)[](#filltransparency)

De [FillTransparency](/docs/nl-nl/reference/engine/classes/Highlight#FillTransparency)  eigenschap stelt de zichtbaarheid van het interieur van de markering in op een waarde tussen de standaardwaarde van 0  (opake) en 1  (onzichtbaar). Je kunt deze eigenschap gebruiken om te bepalen hoeveel van de bestaande kleur van het object je wilt dat kijkers zien.

![Een boom mesh met een opake zwarte vulling.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/FillTransparency-0.jpg) FillTransparency = 0

![Een boom mesh met een semi-transparante zwarte vulling.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/FillTransparency-Half.jpg) FillTransparency = 0.5

![Een boom mesh met een transparante zwarte vulling.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/FillTransparency-1.jpg) FillTransparency = 1

### [DepthMode](#depthmode)[](#depthmode)

De [DepthMode](/docs/nl-nl/reference/engine/classes/Highlight#DepthMode)  eigenschap controleert hoe het effect wordt weergegeven ten opzichte van andere objecten in de wereld.

-

[AlwaysOnTop](/docs/nl-nl/reference/engine/enums/HighlightDepthMode#AlwaysOnTop)  — Laat de markering altijd weergeven, ongeacht of er objecten tussen de camera en het gemarkeerde object zijn. Dit betekent dat de kijker de markering altijd kan zien, ongeacht wat er tussen het gemarkeerde object en de camera staat.

-

[Occluded](/docs/nl-nl/reference/engine/enums/HighlightDepthMode#Occluded)  — Verbergt de markering als er objecten tussen de camera en het gemarkeerde object zijn. Dit betekent dat de kijker het object alleen kan zien als er geen obstructieve objecten tussen het gemarkeerde object en het zicht van de camera zijn.

AlwaysOnTop Occluded

![Twee objecten staan achter pilaren, maar omdat hun AlwaysOnTop-eigenschap is ingesteld op waar, kun je de objecten en hun markering nog steeds zien.](https://prod.docsiteassets.roblox.com/assets/ui/highlighting-objects/DepthMode-AlwaysOnTop.jpg)

### [Enabled](#enabled)[](#enabled)

De [Enabled](/docs/nl-nl/reference/engine/classes/Highlight#Enabled)  eigenschap stelt je in staat om de markering snel in of uit te schakelen zonder enige impact op de prestaties .

Hoewel een uitgeschakelde [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  niet wordt weergegeven, neemt deze nog steeds een van de 255 beschikbare [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  slots in. Als je van plan bent om een [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  instantie permanent uit te schakelen, is het het beste om de markering te verwijderen in plaats van deze uit te schakelen.

## [Prestatie tips](#prestatie-tips)[](#prestatie-tips)

Hoewel je veel opties hebt om [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  instanties aan te passen, worden de volgende tips aanbevolen om de prestaties van je spel op alle apparaten te verbeteren:

-

Het toevoegen of verwijderen van een [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  kan een geometrie-herbouwstap veroorzaken die kan leiden tot prestatiepieken en extra tekenopdrachten. Als je het uiterlijk van een [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  instantie wilt wijzigen of deze tijdelijk wilt verbergen/tonen op een object, is het het beste om de eigenschappen van de [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  instantie direct aan te passen, aangezien het wijzigen van een eigenschap van de [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  instantie lichtgewicht is en geen invloed heeft op de prestaties.

-

Roblox tekent objecten in een volgorde van achter naar voren, wat problemen kan veroorzaken als je objecten met een kind [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  binnen andere objecten met ook kind [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  instanties plaatst. Om deze reden is het het beste om objecten met [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  instanties buiten een ouder/kind relatie met andere objecten met [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  instanties te houden.

-

De eerste [Highlight](/docs/nl-nl/reference/engine/classes/Highlight)  die op het scherm wordt weergegeven, brengt de meeste prestatiekosten met zich mee (tot 1 milliseconde GPU-tijd op mobiele apparaten). Voor extra markeringen boven de eerste zou je geen significante impact op de prestaties op enig platform moeten zien.

-

Op mobiele apparaten zijn markeringen kostbaarder voor de prestaties wanneer ze meer van het scherm bedekken. Op andere platforms hebben markeringen dezelfde prestatiekosten, ongeacht hun schermbedekking.

-

Op alle platforms brengen markeringen die niet zichtbaar zijn op het scherm (ofwel uitgeschakeld of volledig transparant) geen prestatiekosten met zich mee.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
