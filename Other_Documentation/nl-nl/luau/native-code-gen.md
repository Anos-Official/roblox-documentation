<!-- Source: https://create.roblox.com/docs/nl-nl/luau/native-code-gen -->

Native code generatie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. Geavanceerd

# Native code generatie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Met de Luau-ondersteuning voor native code generatie kunnen scripts¹ in je game direct worden gecompileerd naar de machinecode-instructies die CPU's uitvoeren, in plaats van de reguliere bytecode waarop de Luau VM werkt. Deze functie kan de uitvoersnelheid verbeteren voor sommige ondersteunde scripts, vooral die met veel numerieke berekeningen en weinig aanroepen naar zware Luau-bibliotheken of Roblox-API's.

1  Native code generatie wordt alleen ondersteund voor server-side scripts en client-side scripts op Android-apparaten. In de toekomst kunnen meer apparaten worden ondersteund.

## [Native code generatie inschakelen](#native-code-generatie-inschakelen)[](#native-code-generatie-inschakelen)

Om native code generatie in te schakelen voor een [Script](/docs/nl-nl/reference/engine/classes/Script) , voeg de --!native  opmerking aan de bovenkant toe:²

```

--!native

print("Hallo vanuit native code!")

```

Dit schakelt native code generatie in voor alle functies in het script, en de top-level scope, als dit winstgevend wordt geacht. Er zijn geen aanvullende wijzigingen vereist; het gedrag van de natively executing scripts is precies hetzelfde als voorheen en alleen de prestaties zijn anders. Alle functies van de Luau-taal en alle Roblox-API's blijven ondersteund.

Alternatief kun je native code generatie inschakelen voor een individuele functie door de @native  attribuut toe te voegen:

```

@native

local function f(x)

  return (x + 1)

end

```

 2  In de toekomst kunnen sommige scripts automatisch beginnen met native uitvoering als wordt vastgesteld dat dit winstgevend is, maar handmatig geplaatste --!native  opmerkingen zijn momenteel vereist.

## [Beste praktijken](#beste-praktijken)[](#beste-praktijken)

De volgende tips helpen je om het meeste uit native code generatie te halen:

-

Het is het beste om deze functie in te schakelen in scripts die veel berekeningen direct in Luau uitvoeren. Als je veel wiskundige bewerkingen op tabellen hebt en vooral [buffer](/docs/nl-nl/reference/engine/libraries/buffer)  types, kan het script een goede kandidaat zijn.

-

Alleen de [functies](/docs/nl-nl/luau/functions)  van het script worden native gecompileerd. De code in de top outer [scope](/docs/nl-nl/luau/scope)  wordt vaak maar één keer uitgevoerd en profiteert niet zoveel als functies die vaak worden aangeroepen, vooral diegene die elke frame worden aangeroepen.

-

Het wordt aanbevolen om de tijd die een script of functie nodig heeft met en zonder native compilatie te meten om te beoordelen wanneer het het beste is om het te gebruiken. De [Script Profiler](#script-profiler)  tool kan de prestaties van functies meten om weloverwogen beslissingen te nemen.

-

Het kan verleidelijk zijn om de --!native  opmerking in elke  script te plaatsen voor het geval sommige sneller worden uitgevoerd, maar native code generatie heeft enkele nadelen:

-

Er is tijd nodig voor codecompilatie, wat de opstarttijd van servers kan verhogen.

-

Extra geheugen wordt gebruikt om natively gecompileerde code op te slaan.

-

Er is een limiet op de totale toegestane hoeveelheid natively gecompileerde code in een game.

Deze problemen kunnen worden aangepakt door een doordacht gebruik van de @native  attribuut.

## [Code om te vermijden](#code-om-te-vermijden)[](#code-om-te-vermijden)

Hoewel alle functies hetzelfde zullen functioneren met of zonder ingeschakelde native code generatie, zullen sommige van hen niet natively draaien en kunnen ze leiden tot de-optimalisatie of een terugval naar geïnterpreteerde uitvoering. Deze omvatten:

-

Gebruik van verouderde [getfenv()](/docs/nl-nl/reference/engine/globals/LuaGlobals#getfenv) /[setfenv()](/docs/nl-nl/reference/engine/globals/LuaGlobals#setfenv)  aanroepen.

-

Gebruik van verschillende ingebouwde Luau-functies zoals [math.asin()](/docs/nl-nl/reference/engine/libraries/math#asin)  met niet-numerieke argumenten.

-

Onjuist getypeerde parameters doorgeven aan getypeerde functies, bijvoorbeeld het aanroepen van foo(true)  wanneer foo  is gedeclareerd als function foo(arg: string) . Vergeet niet altijd de juiste [type annotaties](#gebruik-type-annotaties)  te gebruiken.

Bij het gebruik van de [Script Profiler](#script-profiler)  kun je de tijd vergelijken die een reguliere versie van de functie in beslag neemt versus degene die natively is gecompileerd. Als een functie binnen een --!native  script of gemarkeerd met @native  niet lijkt te worden uitgevoerd, kunnen een of meer factoren uit de bovenstaande lijst de-optimalisatie veroorzaken.

## [Gebruik type annotaties](#gebruik-type-annotaties)[](#gebruik-type-annotaties)

Native code generatie probeert het meest waarschijnlijke type voor een gegeven variabele af te leiden om codepaden te optimaliseren. Bijvoorbeeld, het wordt aangenomen dat a + b  wordt uitgevoerd op getallen, of dat een tabel wordt benaderd in t.X . Gezien operatoroverbelasting kunnen a  en b  echter tabellen of [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  types zijn, of kan t  een Roblox datatype zijn.

Hoewel native code generatie elk type zal ondersteunen, kunnen misvoorspellingen onnodige controles triggeren, wat resulteert in langzamere code-uitvoering.

Om enkele veelvoorkomende problemen op te lossen, worden Luau type annotaties op functieargumenten gecontroleerd, maar het is vooral aanbevolen om [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  argumenten te annoteren:

```

--!native

-- "v" wordt verondersteld een tabel te zijn; functie presteert langzamer door tabelcontroles

local function sumComponentsSlow(v)

	return v.X + v.Y + v.Z

end

-- "v" is gedeclareerd als een Vector3; code gespecialiseerd voor vectoren wordt gegenereerd

local function sumComponentsFast(v: Vector3)

	return v.X + v.Y + v.Z

end

```

## [Studio tooling](#studio-tooling)[](#studio-tooling)

De volgende Studio tooling wordt ondersteund voor --!native  scripts en @native  functies.

### [Debugging](#debugging)[](#debugging)

Algemene [debugging](/docs/nl-nl/studio/debugging)  van scripts wordt ondersteund, maar de weergaven voor locals/upvalues kunnen incompleet zijn en variabelen missen uit [call stack](/docs/nl-nl/studio/debugging#call-stack-window)  frames die natively worden uitgevoerd.

Houd er ook rekening mee dat wanneer je code debugt die is geselecteerd voor native compilatie, het plaatsen van [breakpoints](/docs/nl-nl/studio/debugging#insert-breakpoints)  de native uitvoering voor die functies zal uitschakelen.

### [Script Profiler](#script-profiler)[](#script-profiler)

In de [Script Profiler](/docs/nl-nl/studio/optimization/scriptprofiler)  worden functies die natively worden uitgevoerd weergegeven met <native>  ernaast:

 ![Voorbeeld van native functies gemarkeerd in de Script Profiler](https://prod.docsiteassets.roblox.com/assets/studio/console/ScriptProfiler-Native-Annotation.png)

Als een functie gemarkeerd met @native  of binnen een --!native  script de <native>  annotatie niet toont, kan die functie niet natively worden uitgevoerd vanwege het plaatsen van [breakpoints](/docs/nl-nl/studio/debugging#insert-breakpoints) , het gebruik van [afgeraden code](#code-om-te-vermijden) , of niet-overeenkomende [type annotaties](#gebruik-type-annotaties) .

### [Luau heap](#luau-heap)[](#luau-heap)

In de [Luau heap](/docs/nl-nl/studio/optimization/memory-usage#luau-heap)  profiler wordt geheugen dat door native functies wordt ingenomen weergegeven als [native]  elementen in de grafiek.

 ![Voorbeeld van native geheugengebruik gemarkeerd in de Luau Heap profiler](https://prod.docsiteassets.roblox.com/assets/studio/console/LuauHeap-Native-Annotation.png)

### [Grootte-analyse](#grootte-analyse)[](#grootte-analyse)

Elke natively-gecompileerde script verbruikt geheugen. Wanneer de grootte van de gecompileerde code een vooraf gedefinieerde limiet bereikt, stopt de native compilatie en wordt de resterende code niet-natively uitgevoerd. Dit maakt het essentieel om scripts zorgvuldig te kiezen voor native compilatie.

Om de native codegrootte van individuele functies en scripts te monitoren:

1.

Zorg ervoor dat je in Server  weergave bent via de [client/server toggle](/docs/nl-nl/studio/testing-modes#schakel-clientserver)  knop.

2.

Roep debug.dumpcodesize()  aan vanuit de [Command Bar](/docs/nl-nl/studio/overview#opdrachtbalk) .

In het [Output](/docs/nl-nl/studio/output)  venster zie je het totale aantal scripts en functies die tot het moment van aanroep natively zijn gecompileerd, het geheugen dat door hun native code wordt verbruikt, en de limiet voor de native codegrootte. Na de samenvatting zie je een tabel voor elk natively-gecompileerd script in aflopende volgorde van codegrootte.

 ![Voorbeeld van native codegrootte weergegeven in het Output venster.](https://prod.docsiteassets.roblox.com/assets/studio/debugging/Native-Code-Size-Analysis.png)

Voor elk script toont de output het aantal gecompileerde functies en het geheugenverbruik van de native code. Elke functie wordt vervolgens vermeld in aflopende volgorde van native codegrootte, met anonieme functies weergegeven als [anonymous]  en volledige scripts als [top level] . In de laatste kolom wordt het percentage berekend ten opzichte van de limiet voor de native codegrootte. Houd er rekening mee dat de native codegrootte van functies nauwkeurig wordt gerapporteerd, maar het geheugenverbruik voor scripts wordt afgerond naar de dichtstbijzijnde paginagrootte.

## [Limieten en probleemoplossing](#limieten-en-probleemoplossing)[](#limieten-en-probleemoplossing)

Het compileren van code naar instructies voor een bepaalde CPU vereist extra opslaggeheugen. Bovendien kunnen optimalisaties voor complexe functies te veel tijd in beslag nemen. Het bereiken van een interne limiet zal een fout rapporteren in het [Output](/docs/nl-nl/studio/output)  venster van Studio, inclusief:

* Functie 'f' op regel 20 overschreed de limiet voor enkele codeblok-instructies*

Deze fout betekent dat een enkel blok code binnen een functie meer dan 64K instructies heeft gebruikt. Dit kan worden vermeden door de functie te vereenvoudigen of door deze op te splitsen in individuele kleinere functies.

* Functie 'f' op regel 20 overschreed de limiet voor functiecodeblokken*

Deze fout betekent dat een enkele functie meer dan 32K interne codeblokken bevat. Interne codeblokken komen niet exact overeen met de control-flow blokken in je script, maar deze fout kan worden vermeden door de control-flow in de functie te vereenvoudigen of door deze op te splitsen in individuele kleinere functies.

* Functie 'f' op regel 200 overschreed de totale module-instructielimiet*

Deze fout betekent dat de functie in totaal een limiet van 1 miljoen instructies voor het gehele script heeft bereikt. In sommige gevallen kan de gerapporteerde functie zelf veel instructies hebben, of de limiet kan zijn bereikt door functies eerder in het script. Om dit probleem te vermijden, wordt aanbevolen om bijzonder grote functies naar een apart niet-native script te verplaatsen of @native  op de andere functies te gebruiken. Je kunt ook proberen dat aparte script te markeren met --!native , maar 1 miljoen instructies verbruikt veel geheugen en je kunt de geheugengrens overschrijden.

* Functie 'f' op regel 20 ondervond een interne verlagingsfout*  (of)
 * Interne fout: Native code generatie mislukt (assembly lowering)*

Soms bevat een functie complexe stukjes code die de native code compiler momenteel niet kan verwerken. Om deze fout te vermijden, inspecteer complexe expressies in de code en splits ze op of vereenvoudig ze, maar overweeg ook om een bugrapport in te dienen met een voorbeeld van de code die om deze reden is mislukt.

* Geheugenallocatielimiet bereikt voor native code generatie*

Deze fout betekent dat de totale geheugengrens voor native code gegevens is bereikt. Om dit te vermijden, probeer --!native  te verwijderen uit de meer geheugeneisende scripts, zodat meer kleinere scripts onder de limiet passen. Alternatief kun je grote of zelden aangeroepen functies naar een apart niet-native module verplaatsen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
