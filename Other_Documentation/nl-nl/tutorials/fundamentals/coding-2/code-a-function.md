<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-2/code-a-function -->

Code een functie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Functies en evenementen](/docs/nl-nl/tutorials/fundamentals/coding-2/functions-and-events)

# Code een functie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Functies  zijn sets van instructies die meerdere keren in een script kunnen worden gebruikt. Er zijn kant-en-klare functies (ook wel methoden genoemd) zoals print()  en [task.wait()](/docs/nl-nl/reference/engine/libraries/task#wait)  die in de meeste programmeertalen zijn ingebouwd. Programmeurs kunnen ook hun eigen aangepaste functies maken voor code die ze meer dan eens willen gebruiken, maar niet steeds opnieuw willen schrijven. In Luau doe je dit door te typen: local function naamVanDeFunctie()

Functies kunnen worden gezien als een recept. Ze zijn beide lijsten van specifieke instructies. Bijvoorbeeld, je zou een functie kunnen gebruiken om een robot te leren hoe je spaghetti maakt. Maak eerst een local function  die de stappen om de maaltijd voor te bereiden opsomt. Dan, wanneer je zin hebt in het avondeten, zeg je gewoon: "Robot, voer makeSpaghetti() uit".

De stappen om het avondeten te maken kunnen er als volgt uitzien:

1.

Kook water

2.

Voeg pasta toe

3.

Kook 15 minuten

4.

Voeg saus toe

5.

Serveer op een bord

Terwijl de codeversie er ongeveer zo uit kan zien:

## [Maak een functie](#maak-een-functie)[](#maak-een-functie)

Om te oefenen, zal je eerste functie je favoriete eten in het Output-venster afdrukken. Stel eerst het script in dat je gaat gebruiken, als je niet meer weet hoe, hier is een herinnering:

1.

Maak een nieuw script in ServerScriptService .

2.

Hernoem het script * FunctiesOefening* .

3.

Verwijder "Hello World" .

4.

Voeg een opmerking bovenaan toe. Bijvoorbeeld: -- Drukt je favoriete eten af

Vervolgens maak en noem je de functie. Alle functies moeten namen hebben die je helpen herinneren wat hun doel is. Functienamen zijn camelCased, met de eerste letter in kleine letters en de volgende woorden met een hoofdletter.

Voorbeelden: voegPuntenToe() , herstartSpel() , regenVlammenLama's()

-

Typ local function printEten() , druk vervolgens op Enter  op je toetsenbord. Het zou de functie automatisch moeten aanvullen zodat het eruitziet als:

```

local function printEten()

end

```

Typ end  zelf als de code om de een of andere reden niet automatisch aanvult. Als de functie geen end  heeft, zal je code niet draaien.

### [Voeg code toe aan functies](#voeg-code-toe-aan-functies)[](#voeg-code-toe-aan-functies)

Alle code voor je functie moet tussen de regels local function printEten()  en end  worden getypt. Elke code die niet tussen die twee punten staat, zal niet worden uitgevoerd wanneer de functie wordt aangeroepen.

```

local function printEten()

	-- Code hier draait wanneer de functie wordt aangeroepen

end

-- Code hier zal niet draaien

```

Informatie die binnen de functie staat, of die door de functie kan worden gebruikt, is in scope .

-

Tussen local function printEten()  en end , gebruik print()  om je favoriete eten te vermelden.

```

local function printEten()

	print("Curry!")

end

```

Terwijl je typt, zou je code automatisch moeten zijn ingesprongen. Dit maakt het gemakkelijker voor jou en anderen om het begin en het einde van een functie te zien. Als het niet automatisch is ingesprongen, kun je op Tab  drukken aan het begin van de regel om het snel in te springen.

### [Vertel de functie om uit te voeren](#vertel-de-functie-om-uit-te-voeren)[](#vertel-de-functie-om-uit-te-voeren)

Er is nog één ding dat we moeten doen voordat de functie werkt, en dat is om het te vertellen om uit te voeren, ook wel aanroepen  van een functie genoemd. Functies worden pas uitgevoerd als ze worden aangeroepen. Om een functie aan te roepen, typ je de naam van de functie inclusief de () .

1.

Onder end , typ printEten() .

2.

Test de code. Je favoriete eten zou moeten verschijnen in het [Output](/docs/nl-nl/studio/output)  venster.

### [Probleemoplossing tips](#probleemoplossing-tips)[](#probleemoplossing-tips)

Als je code niet draait, controleer dan op fouten zoals de volgende:

-

Controleer of print("Je Eten Hier")  tussen local function printEten()  en end  staat.

-

Zorg ervoor dat je eten een string is, met aanhalingstekens aan beide zijden van "elk kant" .

-

Controleer of de functie wordt aangeroepen nadat deze is gemaakt. printEten()  zou onder end  moeten staan.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-2/use-parameters-and-events)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-1/parents-and-children)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
