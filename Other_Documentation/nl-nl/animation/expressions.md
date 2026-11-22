<!-- Source: https://create.roblox.com/docs/nl-nl/animation/expressions -->

Grafiekeditor-expressies | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Animatie](/docs/nl-nl/animation)
6. /
7. Animaties maken
8. /
9. [Grafiek-editor](/docs/nl-nl/animation/graph-editor)

# Grafiekeditor-expressies

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een expressie  is een korte Luau-achtige formule die grafiekparameters leest en een waarde retourneert, zoals math.clamp((MovementSpeed + 0.5) / MaxSpeed, 0, 1) . Gebruik expressies om een knooppunt-eigenschap of een [toestandmachine-overgang](/docs/nl-nl/animation/graph-editor-state-machine)  aan te sturen. Expressies houden parametertransformaties en animatiebeslissingen in je grafiek, dicht bij de knooppunten die ze aansturen.

## [Vereisten](#vereisten)[](#vereisten)

Voordat je een expressie maakt, maak jezelf vertrouwd met de [Animatie Grafiekeditor](/docs/nl-nl/animation/graph-editor) , inclusief hoe je [deze opent en een animatiegrafiek maakt](/docs/nl-nl/animation/graph-editor#bouw-een-grafiek) .

## [Maak een expressie](#maak-een-expressie)[](#maak-een-expressie)

Dit voorbeeld gebruikt een expressie om de Positie  eigenschap van een [Blend1DNode](/docs/nl-nl/reference/engine/enums/AnimationNodeType)  aan te sturen. Configureer het knooppunt met een idle-animatie op positie 0 en een loop-animatie op positie 1. De expressie converteert de bewegingssnelheid van het personage naar het bereik van 0 tot 1 dat het knooppunt gebruikt om tussen die animaties te mengen.

1.

Voeg MovementSpeed  en MaxSpeed  Number grafiekparameters toe.

 ![Parameters-pane die de MovementSpeed en MaxSpeed Number-parameters toont.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-expressions/Add-Parameters.png)

2.

Sleep een verbinding van de Positie  eigenschapspen van de [Blend1DNode](/docs/nl-nl/reference/engine/enums/AnimationNodeType)  en selecteer Nieuwe Expressie .

 ![Geanimeerde demonstratie van het maken van een Expressie-knooppunt vanuit de Blend1D Positie-eigenschapspen.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-expressions/Add-Expression-Node.gif)

3.

Voer de volgende expressie in:

```

math.clamp(MovementSpeed / MaxSpeed, 0, 1)

```

 ![Geanimeerde demonstratie van het invoeren van een expressie in een Expressie-knooppunt.](https://prod.docsiteassets.roblox.com/assets/animation/graph-editor-expressions/Edit-Expression.gif)

4.

Klik buiten het expressievak om het te verversen. Terwijl MovementSpeed  stijgt naar MaxSpeed , ontvangt de [Blend1DNode](/docs/nl-nl/reference/engine/enums/AnimationNodeType)  een waarde van 0 tot 1 en mengt van de idle-animatie naar de loop-animatie.

Nadat je de grafiek op een [AnimationTrack](/docs/nl-nl/reference/engine/classes/AnimationTrack)  hebt geladen, werk je MovementSpeed  en MaxSpeed  bij vanuit je gameplay-script met [AnimationTrack:SetParameter()](/docs/nl-nl/reference/engine/classes/AnimationTrack#SetParameter) . Het volgende voorbeeld gebruikt de [MoveDirection](/docs/nl-nl/reference/engine/classes/Humanoid#MoveDirection)  en [WalkSpeed](/docs/nl-nl/reference/engine/classes/Humanoid#WalkSpeed)  eigenschappen van een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid) :

Script - Stuur expressieparameters aan

```

game:GetService("RunService").Stepped:Connect(function()

    animationTrack:SetParameter("MovementSpeed", humanoid.MoveDirection.Magnitude * humanoid.WalkSpeed)

    animationTrack:SetParameter("MaxSpeed", humanoid.WalkSpeed)

end)

```

De expressie wordt geëvalueerd naarmate de parameterwaarden veranderen. Voor de parameterworkflow, zie [API-integratie](/docs/nl-nl/animation/graph-editor#api-integratie) .

## [Wat wordt ondersteund](#wat-wordt-ondersteund)[](#wat-wordt-ondersteund)

De ondersteuning voor expressies omvat rekenkundige en vergelijkingsoperaties, logische en voorwaardelijke expressies, aanroepen van functies in de [math](/docs/nl-nl/reference/engine/libraries/math)  bibliotheek, constructie en lidtoegang voor [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame) , [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2) , [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , en [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  waarden, en stringconcatenatie. De volgende secties sommen de ondersteunde syntaxis en functies op.

### [Rekenkunde en vergelijkingen](#rekenkunde-en-vergelijkingen)[](#rekenkunde-en-vergelijkingen)

Gebruik standaard rekenkundige en vergelijkingsoperaties, met de gebruikelijke volgorde van bewerkingen. Bijvoorbeeld, //  deelt en rondt naar beneden af.

```

Speed * 2.0 + Offset

(Health / MaxHealth) * 100

DamageMultiplier ^ 2

Count % 3

10 // 3

Speed < 1

Health >= MaxHealth

```

Vergelijkingsoperatoren werken met getallen. Gebruik ==  en ~=  om getallen, booleans of strings te vergelijken.

### [Logica en kortsluiting](#logica-en-kortsluiting)[](#logica-en-kortsluiting)

and , or , en not  volgen de Luau waarheidsgetrouwe en kortsluitende evaluatie. Alleen false  en nil  worden als onwaar beschouwd.

```

IsGrounded and GroundSpeed or AirSpeed

not IsDisabled

```

### [If-then-else expressies](#if-then-else-expressies)[](#if-then-else-expressies)

Gebruik de voorwaardelijke expressievorm van Luau om binnen een enkele expressie te vertakken:

```

if Speed > 10 then "sprint" elseif Speed > 2 then "run" else "idle"

```

### [Wiskundige bibliotheek](#wiskundige-bibliotheek)[](#wiskundige-bibliotheek)

Gebruik de [math](/docs/nl-nl/reference/engine/libraries/math)  bibliotheek. Grafiekexpressies ondersteunen nog niet [math.frexp()](/docs/nl-nl/reference/engine/libraries/math#frexp) , [math.noise()](/docs/nl-nl/reference/engine/libraries/math#noise) , of [math.randomseed()](/docs/nl-nl/reference/engine/libraries/math#randomseed) . [math.modf()](/docs/nl-nl/reference/engine/libraries/math#modf)  retourneert momenteel alleen het gehele gedeelte.

```

math.clamp(Speed / MaxSpeed, 0, 1)

math.sin(Time * 2 * math.pi)

math.atan2(Direction.Y, Direction.X)

math.max(A, B, C)

```

### [Vectorconstructie en lidtoegang](#vectorconstructie-en-lidtoegang)[](#vectorconstructie-en-lidtoegang)

Construeer [Vector2](/docs/nl-nl/reference/engine/datatypes/Vector2)  en [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  waarden, voer vectorrekenkunde uit en krijg toegang tot vectorleden zoals Magnitude  en Unit .

```

Vector3.new(math.cos(Time), math.sin(Time), 0)

Vector2.new(InputX, InputY)

MoveDirection.Magnitude * 2.0

Position.X + Offset

Vector3.zero

```

### [Color3-constructie en lidtoegang](#color3-constructie-en-lidtoegang)[](#color3-constructie-en-lidtoegang)

Construeer [Color3](/docs/nl-nl/reference/engine/datatypes/Color3)  waarden en krijg toegang tot hun kleurkanalen.

```

Color3.fromRGB(255, 128, 0)

Color.R

```

### [CFrame-constructie, lidtoegang en bewerkingen](#cframe-constructie-lidtoegang-en-bewerkingen)[](#cframe-constructie-lidtoegang-en-bewerkingen)

Construeer [CFrame](/docs/nl-nl/reference/engine/datatypes/CFrame)  waarden, krijg toegang tot CFrame-leden en combineer ze met CFrames of [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  waarden.

```

CFrame.new(Position, LookAtPosition)

CFrame.Angles(RotationX, RotationY, RotationZ)

CFrame.identity

Transform.LookVector

Transform.Position + Vector3.new(0, 1, 0)

```

### [Stringconcatenatie](#stringconcatenatie)[](#stringconcatenatie)

Gebruik ..  om twee strings samen te voegen:

```

"state_" .. CurrentState

```

### [Lokale variabelen en multi-regel expressies](#lokale-variabelen-en-multi-regel-expressies)[](#lokale-variabelen-en-multi-regel-expressies)

Gebruik een multi-regel expressie om een formule in benoemde stappen op te splitsen. Een multi-regel expressie ondersteunt local  declaraties, return , if / elseif / else , en zelfstandige expressies. Binnen een if  of else  lichaam, gebruik alleen return  of een zelfstandige expressie; geneste if -verklaringen en lokale declaraties worden niet ondersteund.

```

local normalizedSpeed = Speed / MaxSpeed

local eased = math.clamp(normalizedSpeed, 0, 1)

return eased

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
