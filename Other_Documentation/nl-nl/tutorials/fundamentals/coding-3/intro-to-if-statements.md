<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-3/intro-to-if-statements -->

Introductie tot if-statements | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Voorwaarden](/docs/nl-nl/tutorials/fundamentals/coding-3/landing)

# Introductie tot if-statements

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

In games zijn er vaak veel oorzaak-en-gevolgrelaties. Bijvoorbeeld:

-

Als een speler 10 punten scoort, dan wint hij het spel.

-

Als een speler een power-up heeft, dan kan hij super snel rennen.

-

Als een speler "Gelukkige Verjaardag" in de chat zegt, dan valt er confetti.

Scripts gebruiken voorwaardelijke statements om met dit soort situaties om te gaan. Voorwaardelijke statements  zijn regels code die alleen worden uitgevoerd als aan bepaalde voorwaarden is voldaan. Een type voorwaardelijk statement is een if/then statement . In Luau ziet het syntaxispatroon voor if-statements er als volgt uit:

Codefragmenten die gebruik maken van voorwaardelijke statements zijn besturingsstructuren.  Besturingsstructuren zijn als stroomdiagrammen in codevorm en kunnen verschillende voorwaardelijke statements bevatten.

## [Oefening met if-statements](#oefening-met-if-statements)[](#oefening-met-if-statements)

Deze stappen laten zien hoe je een script maakt dat de kleur van een onderdeel verandert als een statement waar is.

1.

Maak in ServerScriptService  een nieuw script en noem het TruthChecker . Voeg een passende opmerking toe aan het script.

```

-- Verandert het onderdeel als een voorwaarde waar is

```

2.

Maak een nieuw onderdeel genaamd LieDetector.

### [Formatteer if-statements](#formatteer-if-statements)[](#formatteer-if-statements)

Voorwaarden  kunnen in verschillende vormen komen, maar zijn vaak eenvoudige statements zoals wiskundige vergelijkingen. Bijvoorbeeld, als 1+1 gelijk is aan 2, voer dan wat code uit. Net als gewone wiskundige vergelijkingen kunnen voorwaardelijke statements operatoren  gebruiken zoals plus (+ ) of minder dan (< ) om statements te evalueren.

Een specifieke operator om op te letten is == ; het staat voor "is gelijk aan." Dus de statement 2 + 2 == 4  kan worden gelezen als "twee plus twee is gelijk aan vier". Wees zeer voorzichtig om het niet te verwarren met = , dat nieuwe waarden toekent aan objecten zoals variabelen.

1.

Stel de lege voorwaarde in. Typ in het script if then , en druk op Enter  om de voorwaarde automatisch aan te vullen. Het sleutelwoord then  zal onderstreept zijn omdat de code incompleet is.

```

if then

	-- lege code

end

```

2.

Typ na het sleutelwoord if  een waar statement zoals 3 + 3 == 6 .

```

if 3 + 3 == 6 then

	-- lege code

end

```

3.

Verwijs binnen de voorwaarde naar het onderdeel dat je LieDetector hebt genoemd en verander de Color  eigenschap van het onderdeel naar groen.

```

if 3 + 3 == 6 then

	workspace.LieDetector.Color = Color3.fromRGB(0, 255, 0)

end

```

Het inspringen van de regels code binnen de voorwaarde maakt het gemakkelijker om te zien waar het codefragment begint en eindigt.

4.

Test  je code. Als drie plus drie gelijk is aan zes, zal het onderdeel groen worden.

## [Controleer een valse voorwaarde](#controleer-een-valse-voorwaarde)[](#controleer-een-valse-voorwaarde)

Verander nu opzettelijk de statement om te zien wat er gebeurt wanneer de wiskundige vergelijking onjuist is.

1.

Verander in de if-statement de vergelijking naar iets onnauwkeurigs, zoals 3 + 3 >= 10 .

```

if 3 + 3 >= 10 then

	workspace.LieDetector.Color = Color3.fromRGB(0, 255, 0)

end

```

2.

Test nu je code. Het onderdeel zou niet groen moeten worden voor een valse statement.

### [Wiskunde-operatoren](#wiskunde-operatoren)[](#wiskunde-operatoren)

De onderstaande tabel geeft enkele veelvoorkomende Luau-operatoren weer. Meer informatie over operatoren is te vinden op [Luau Operators](/docs/nl-nl/luau/operators) .

| Symbool | | Betekenis |
| --- | --- |
| + | | Optelling |
| - | | Aftrekking |
| * | | Vermenigvuldiging |
| / | | Delen |

### [Vergelijkingsoperatoren](#vergelijkingsoperatoren)[](#vergelijkingsoperatoren)

-

==  : Is gelijk aan.

-

~=  : Is niet gelijk aan.

-

<  of >  worden gebruikt voor minder of groter dan, respectievelijk.

-

<=  of >=  worden gebruikt voor minder/groter dan of gelijk aan, respectievelijk.

## [Variabelen en eigenschappen](#variabelen-en-eigenschappen)[](#variabelen-en-eigenschappen)

Voorwaardelijke statements worden ook gebruikt om de status van eigenschappen en variabelen te evalueren. De volgende stappen controleren of een variabele succesvol een waarde is toegewezen.

1.

Verwijder alle code en kopieer de volgende snippet in het script. Test het, en er verschijnt een nieuwe fout in Output.

```

local mysteryPart = workspace.MysteryPart

-- Evalueert als waar als MysteryPart succesvol is toegewezen

if mysteryPart then

	workspace.LieDetector.Color = Color3.fromRGB(0, 255, 0)

end

```

2.

Voeg een nieuw onderdeel toe aan de workspace genaamd MysteryPart. Test opnieuw, en LieDetector zou groen moeten worden.

3.

Onderzoek hoe eigenschappen kunnen worden geëvalueerd met voorwaardelijke statements. Houd MysteryPart, maar verwijder opnieuw je code en kopieer de onderstaande code.

```

local mysteryPart = workspace.MysteryPart

-- Evalueert als waar als MysteryPart volledig ondoorzichtig is

if mysteryPart.Transparency == 0 then

	workspace.LieDetector.Color = Color3.fromRGB(0, 255, 0)

	mysteryPart.Transparency = .2

end

```

4.

Test de code, en als MysteryPart de standaarddoorzichtigheid van 0 heeft, zal het spookachtig worden terwijl LieDetector groen wordt.

## [Samenvatting](#samenvatting)[](#samenvatting)

Voorwaardelijke statements controleren of een statement juist is, en als dat zo is, wordt er wat code uitgevoerd. If-statements zijn een zeer veelvoorkomend type voorwaardelijk statement. Ze gebruiken het patroon "Als dit waar is, doe dat."

Codefragmenten die gebruik maken van voorwaardelijke statements worden besturingsstructuren genoemd. Besturingsstructuren kunnen meerdere voorwaardelijke statements bevatten.

Naast het evalueren of eenvoudige wiskundige statements feitelijk zijn, worden voorwaardelijke statements ook gebruikt om de status van variabelen en eigenschappen te controleren.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-3/traps-with-if-statements)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-3/landing)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
