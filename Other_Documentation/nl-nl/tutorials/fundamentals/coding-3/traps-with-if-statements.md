<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-3/traps-with-if-statements -->

If/then oefening met vallen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Voorwaarden](/docs/nl-nl/tutorials/fundamentals/coding-3/landing)

# If/then oefening met vallen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Vallen die de gezondheid van spelers verlagen zijn een leuk gameplay-element dat kan worden gecodeerd met voorwaardelijke uitspraken. Oefen met het gebruik van voorwaardelijke uitspraken door een onderdeel te maken dat de gezondheid van de speler op nul zet wanneer het wordt aangeraakt.

## [Stel de val in](#stel-de-val-in)[](#stel-de-val-in)

Vallen werken uitzonderlijk goed in spellen met op beweging gebaseerde uitdagingen, zoals obbies. Deze stappen beginnen met het instellen van de noodzakelijke variabelen en functies. Doe zoveel mogelijk zonder eerst naar de codeblokken te kijken.

1.

Maak en noem een valonderdeel. Voeg een script toe aan het onderdeel.

2.

Voeg in het script een beschrijvende opmerking toe en gebruik vervolgens een variabele om naar de ouder van het script te verwijzen.

```

-- Als een speler dit onderdeel aanraakt, zet hun gezondheid op 0

local trapPart = script.Parent

```

3.

Maak een functie genaamd onTouch()  met een parameter genaamd otherPart .

```

-- Als een speler dit onderdeel aanraakt, zet hun gezondheid op 0

local trapPart = script.Parent

local function onTouch(otherPart)

end

```

4.

Verbind de functie met het Touched -evenement van het valonderdeel zodat het wordt uitgevoerd telkens wanneer iets het onderdeel aanraakt.

```

local trapPart = script.Parent

local function onTouch(otherPart)

end

trapPart.Touched:Connect(onTouch)

```

## [Controleer op aanraking door een speler](#controleer-op-aanraking-door-een-speler)[](#controleer-op-aanraking-door-een-speler)

Vergeet niet dat de parameter otherPart  registreert wat het valonderdeel aanraakt, wat een onderdeel van een speler kan zijn of gewoon de basisplaat.

Om ervoor te zorgen dat de val alleen spelers vernietigt en geen willekeurige decoritems, gebruik een if/then-verklaring om te controleren of wat er in otherPart  zit een Humanoid-object bevat.

Humanoids zijn aanwezig in spelersavatars en veel NPC's. Humanoids hebben verschillende unieke eigenschappen. Een van die eigenschappen is Gezondheid.

### [Zoek een specifiek object](#zoek-een-specifiek-object)[](#zoek-een-specifiek-object)

De functie FindFirstChildWhichIsA()  kan worden gebruikt om naar specifieke objecttypen te zoeken, wat handig is omdat we op zoek zijn naar een Humanoid-type object. Spelers zullen waarschijnlijk de val aanraken met slechts een deel van hun avatar, dus moet er een variabele worden ingesteld om de ouder van het aangeraakte onderdeel te vinden en deze te doorzoeken naar een Humanoid.

1.

Typ in onTouch() , local character = otherPart.Parent .

```

local trapPart = script.Parent

local function onTouch(otherPart)

   -- Vindt het ouderobject van otherPart

  local character = otherPart.Parent

end

trapPart.Touched:Connect(onTouch)

```

2.

Controleer of character  een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid)  heeft door te typen:

local humanoid = character:FindFirstChildWhichIsA("Humanoid")

```

local trapPart = script.Parent

local function onTouch(otherPart)

  local character = otherPart.Parent

  local humanoid = character:FindFirstChildWhichIsA("Humanoid")

end

trapPart.Touched:Connect(onTouch)

```

### [Controleer met een if-verklaring](#controleer-met-een-if-verklaring)[](#controleer-met-een-if-verklaring)

Als er een Humanoid wordt gevonden, zet dan de Gezondheid van de Humanoid op nul.

1.

Gebruik een if-verklaring om te controleren of er een Humanoid succesvol is toegewezen aan local humanoid .

```

local trapPart = script.Parent

local function onTouch(otherPart)

   local character = otherPart.Parent

   local humanoid = character:FindFirstChildWhichIsA("Humanoid")

   -- Evalueert of er een Humanoid is gevonden

   if humanoid then

   end

end

trapPart.Touched:Connect(onTouch)

```

2.

Voeg een printopdracht toe en controleer de code tot nu toe.

```

local trapPart = script.Parent

local function onTouch(otherPart)

   local character = otherPart.Parent

   local humanoid = character:FindFirstChildWhichIsA("Humanoid")

   -- Evalueert of er een Humanoid is gevonden

   if humanoid then

      print("Humanoid gevonden")

   end

end

trapPart.Touched:Connect(onTouch)

```

3.

Voer  de code uit en controleer of je de uitvoer kunt zien telkens wanneer een speler het onderdeel aanraakt.

## [Verander de gezondheid van de speler](#verander-de-gezondheid-van-de-speler)[](#verander-de-gezondheid-van-de-speler)

Als de verklaring waar is, kun je dezelfde humanoid-variabele gebruiken om de gezondheid van de speler op 0 te zetten.

1.

Typ tussen then  en end , humanoid.Health = 0 .

Voltooid script

```

local trapPart = script.Parent

local function onTouch(otherPart)

   local character = otherPart.Parent

   local humanoid = character:FindFirstChildWhichIsA("Humanoid")

   -- Evalueert of er een Humanoid is gevonden

   if humanoid then

      print("Humanoid gevonden")

      humanoid.Health = 0

   end

end

trapPart.Touched:Connect(onTouch)

```

2.

Test de val.

## [Samenvatting](#samenvatting)[](#samenvatting)

Dit valonderdeel gebruikte voorwaardelijke uitspraken om Humanoid-onderdelen te detecteren en de gezondheid van de Humanoid op nul te zetten. Dit script is een verbetering ten opzichte van het vorige val-script, dat elk aangeraakt object vernietigde, ongeacht wat het was.

Het heeft echter nog steeds een paar tekortkomingen. Humanoids zijn niet alleen in spelers aanwezig. Humanoids worden ook aangetroffen in niet-speelbare personages. Het script is ook alleen goed in het op nul zetten van de gezondheid van de speler. Je kunt experimenteren met het aftrekken van een klein bedrag aan gezondheid, maar het is waarschijnlijk dat het de gezondheid sneller aftrekt dan gewenst. Latere lessen bieden verdere verbeteringen om meer controle te geven over hoeveel gezondheid er van spelers wordt afgetrokken.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-3/powerups-with-if-statements)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-3/intro-to-if-statements)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
