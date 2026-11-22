<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-2/use-parameters-and-events -->

Gebruik parameters en evenementen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Functies en evenementen](/docs/nl-nl/tutorials/fundamentals/coding-2/functions-and-events)

# Gebruik parameters en evenementen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Normaal gesproken kunnen functies alleen de informatie gebruiken die ze binnenin hebben gecodeerd. Soms weet je echter niet van tevoren wat die informatie zal zijn, of je wilt dezelfde functie kunnen hergebruiken met meerdere stukken vergelijkbare informatie. Bijvoorbeeld, als je een functie wilt gebruiken om de naam van de persoon die het snelst een obby-cursus heeft voltooid in grote letters aan iedereen weer te geven. Je weet de naam van de toekomstige winnaar pas als de race is afgelopen.

Parameters  zijn plaatsaanduidingen voor informatie die je later aan de functie wilt geven. Ze zijn als ramen die je in staat stellen om informatie naar de functie te verzenden .

## [Gebruik parameters en evenementen om een valstrik op te zetten](#gebruik-parameters-en-evenementen-om-een-valstrik-op-te-zetten)[](#gebruik-parameters-en-evenementen-om-een-valstrik-op-te-zetten)

Dit script zal een valstrikdeel creëren dat alles vernietigt wat het aanraakt, inclusief andere delen. Je moet een parameter gebruiken om het op te zetten. Wees voorzichtig om de valstrik te verankeren zodat deze niet valt en per ongeluk dingen vernietigt.

### [Maak een nieuw deel](#maak-een-nieuw-deel)[](#maak-een-nieuw-deel)

Er moet een deel worden ingesteld dat alles vernietigt wat het aanraakt.

1.

Maak een nieuw deel dat niets aanraakt. Als het iets aanraakt, kan het te vroeg afgaan.

2.

Hernoem het deel in de Explorer: TrapPart.

3.

Veranker  het deel.

### [Stel het script in](#stel-het-script-in)[](#stel-het-script-in)

Gebruik wat je weet over variabelen en de hiërarchie van het spel om naar het valstrikdeel te verwijzen.

1.

Voeg een nieuw script toe aan het valstrikdeel. Hernoem het script naar * TrapScript* .

2.

Verwijder Hello World en voeg een beschrijvende opmerking toe.

3.

Onder de opmerking, maak een nieuwe variabele die de ouder van het script vindt.

```

-- Vernietigt alles wat de ouder aanraakt

local trap = script.Parent

```

### [Maak een functie met een parameter](#maak-een-functie-met-een-parameter)[](#maak-een-functie-met-een-parameter)

De valstrik zal een functie gebruiken om alles te vernietigen wat het deel aanraakt. Om te werken, moet de functie weten wat het deel aanraakt. En dat betekent het gebruik van parameters. Parameters worden getypt binnen de ()  die na de naam van een functie komen. Ze zien er als volgt uit:

```

local function functionName(parameterName)

end

```

De werkelijke informatie die door de parameter wordt verzonden, wordt een argument  genoemd. Je zult een nieuwe functie genaamd onTouch()  maken met een parameter genaamd objectTouched  die bijhoudt wat de valstrik aanraakt en vervolgens het aanrakende deel vernietigt.

1.

Maak een lokale functie. Het kan elke naam hebben, maar deze les zal onTouch  gebruiken.

```

local trap = script.Parent

local function onTouch()

end

```

2.

Typ binnen de () , een naam voor de parameter. Deze les zal objectTouched gebruiken.

```

local trap = script.Parent

local function onTouch(objectTouched)

end

```

3.

Tussen local function onTouch()  en end , maak een printstatement. Je zult dit gebruiken om te controleren of iets het deel aanraakt in de volgende sectie.

```

local trap = script.Parent

local function onTouch(objectTouched)

    print("Iets heeft de valstrik aangeraakt")

end

```

### [Gebruik een evenement om de functie aan te roepen](#gebruik-een-evenement-om-de-functie-aan-te-roepen)[](#gebruik-een-evenement-om-de-functie-aan-te-roepen)

We willen dat de functie wordt uitgevoerd telkens wanneer iets het deel aanraakt. Om dat te laten gebeuren, verbind je de functie met het Touched -evenement. Evenementen  zijn dingen die in het spel gebeuren. Zoals een speler die een deel aanraakt of gezondheid verliest. Wanneer een functie is verbonden met een evenement, wordt de functie uitgevoerd telkens wanneer het evenement plaatsvindt.

Het Touched -evenement wordt geactiveerd telkens wanneer het ene deel het andere deel aanraakt en kan worden gebruikt om knoppen, valstrikken en andere objecten te creëren waarmee spelers interactie hebben.

1.

Typ onder de end  van de functie trap.Touched:Connect(onTouch)

```

local trap = script.Parent

local function onTouch(objectTouched)

    print("Iets heeft de valstrik aangeraakt")

end

-- Verbind de functie met het Touched-evenement

trap.Touched:Connect(onTouch)

```

2.

Klik op Test en raak vervolgens het deel aan. Controleer je testprintstatement: Iets heeft de valstrik aangeraakt . Als je de string niet in het Output-venster kunt zien, controleer dan het volgende:

-

Zorg ervoor dat de string "Iets heeft het deel aangeraakt!" tussen local function onTouch() en end staat.

-

Controleer of Touched met een hoofdletter is geschreven.

3.

Nu de functie correct is ingesteld, gebruik deze om alles te vernietigen wat het deel aanraakt. Binnen de functie, na de string, typ objectTouched:Destroy()  De voltooide code zou moeten zijn:

```

local trap = script.Parent

local function onTouch(objectTouched)

    print("Iets heeft de valstrik aangeraakt")

    -- Vernietig het aanrakende object

    objectTouched:Destroy()

end

trap.Touched:Connect(onTouch)

```

4.

Test opnieuw en kijk wat er gebeurt wanneer het deel wordt aangeraakt. Je avatar zou voeten of armen moeten missen. Als het deel het hoofd of de nek van de avatar aanraakt, kan het zelfs volledig worden vernietigd.

## [Samenvatting](#samenvatting)[](#samenvatting)

Parameters worden gebruikt om informatie door te geven die normaal gesproken buiten het bereik ligt (waar een functie het niet kan zien), naar een functie. Ondertussen zijn evenementen speciale signalen die afgaan in het spel wanneer er iets belangrijks gebeurt. Verschillende objecten hebben verschillende evenementen. Functies kunnen aan evenementen worden verbonden zodat ze worden aangeroepen telkens wanneer het evenement wordt geactiveerd. Dit kleine script verbond een functie met het [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched) -evenement van de valstrik en gaf door wat de valstrik aanraakte via de parameter.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-2/parameters-practice-buttons)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-2/code-a-function)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
