<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/capabilities -->

Scriptmogelijkheden | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. Geavanceerd

# Scriptmogelijkheden

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Scriptmogelijkheden zijn experimenteel en beschikbaar als een client beta.

Scriptmogelijkheden  stellen je in staat om te controleren welke acties scripts kunnen uitvoeren binnen de [DataModel](/docs/nl-nl/reference/engine/classes/DataModel)  subboom. In plaats van het standaard "alles-of-niets systeem", kun je een script instellen zodat het alleen toegang heeft tot bepaalde categorieën, zoals audio, fysica, datastores, en meer.

-

Dit systeem stelt je in staat om te beperken wat modellen uit de toolbox kunnen doen en maakt het gemakkelijker om door gebruikers gegenereerde inhoud in het spel op te nemen.

-

Het kan ook helpen om de beveiliging van spellen te waarborgen die spelers toestaan om hun eigen code uit te voeren, die vaak wordt uitgevoerd in een beperkte of geëmuleerde omgeving.

-

Het kan ook worden gebruikt om bibliotheken te delen die beperken wat ze zelf kunnen doen. Bijvoorbeeld, een bibliotheek die extra wiskundige methoden biedt kan worden beperkt tot de kleinste set mogelijkheden die het nodig heeft, zodat andere ontwikkelaars die die bibliotheek gebruiken niet de hele codebase hoeven te valideren om ervoor te zorgen dat deze geen kwaadaardige code bevat.

## [Scriptmogelijkheden inschakelen](#scriptmogelijkheden-inschakelen)[](#scriptmogelijkheden-inschakelen)

Om deze functie in te schakelen, wijzig je de [SandboxedInstanceMode](/docs/nl-nl/reference/engine/classes/Workspace#SandboxedInstanceMode)  eigenschap van Default  naar Experimental  in het Explorer  en Properties  venster.

## [Sandbox-container](#sandbox-container)[](#sandbox-container)

Scriptmogelijkheden introduceren een concept van een sandbox-container . [Models](/docs/nl-nl/reference/engine/classes/Model) , [Folders](/docs/nl-nl/reference/engine/classes/Folder) , [Scripts](/docs/nl-nl/reference/engine/classes/Script) , of afstammelingen van een van die klassen hebben een [Sandboxed](/docs/nl-nl/reference/engine/classes/Instance#Sandboxed)  eigenschap beschikbaar in het Properties  venster.

 ![Sandboxed eigenschap van een Map in het Properties venster.](https://prod.docsiteassets.roblox.com/assets/studio/properties/Folder-Sandboxed.png)

Het inschakelen van de [Sandboxed](/docs/nl-nl/reference/engine/classes/Instance#Sandboxed)  eigenschap duidt de instantie aan als een sandbox-container binnen de [DataModel](/docs/nl-nl/reference/engine/classes/DataModel)  boom, wat de acties die de scripts binnen die container kunnen uitvoeren beperkt op basis van de set waarden in de [Capabilities](/docs/nl-nl/reference/engine/classes/Instance#Capabilities)  eigenschap.

## [Mogelijkheden](#mogelijkheden)[](#mogelijkheden)

De Capabilities  eigenschap is een set waarden die verschillende aspecten van uitvoering beheersen. Mogelijkheden vallen in de volgende brede categorieën:

-

Uitvoeringscontrole  - Specificeert of een script op de client of server kan draaien

-

Toegang tot instanties  - Specificeert met welke [DataModel](/docs/nl-nl/reference/engine/classes/DataModel)  onderdelen een script kan interageren

-

Scriptfunctionaliteitscontrole  - Specificeert welke Luau-functies scripts kunnen aanroepen

-

Toegang tot Engine API  - Specificeert welke delen van de Roblox Engine API kunnen worden gebruikt

Wanneer een script probeert een actie uit te voeren die niet in de set van mogelijkheden staat, rapporteert Roblox een fout. Fouten bevatten doorgaans de actie die wordt geprobeerd, het doel van een actie, en de eerste mogelijkheid die ontbreekt:

```

De huidige thread kan 'Workspace' niet wijzigen (ontbrekende mogelijkheid AccessOutsideWrite)

De huidige thread kan 'Clone' niet aanroepen (ontbrekende mogelijkheid CreateInstances)

De huidige thread kan 'GetSecret' niet aanroepen (ontbrekende mogelijkheid Network)

```

### [Uitvoeringscontrole](#uitvoeringscontrole)[](#uitvoeringscontrole)

Twee mogelijkheden behandelen uitvoeringscontrole:

-

RunClientScript  - [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  of [Script](/docs/nl-nl/reference/engine/classes/Script)  met een [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  waarde van [Client](/docs/nl-nl/reference/engine/enums/RunContext#Client)  mag op de client worden uitgevoerd

-

RunServerScript  - [Script](/docs/nl-nl/reference/engine/classes/Script)  met een [RunContext](/docs/nl-nl/reference/engine/classes/BaseScript#RunContext)  waarde van [Server](/docs/nl-nl/reference/engine/enums/RunContext#Server)  mag op de server worden uitgevoerd

Als het script [Enabled](/docs/nl-nl/reference/engine/classes/BaseScript#Enabled)  is, maar de mogelijkheid die overeenkomt met de locatie waar het probeert te starten niet beschikbaar is, wordt er een waarschuwing weergegeven in het Output  venster. Als een script niet in die context zou moeten draaien, schakel het dan uit of verwijder het.

Merk op dat [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  deze uitvoeringsmogelijkheden niet hoeven te hebben om vereist te zijn.

Wanneer een script niet kan starten omdat de uitvoeringscontrole mogelijkheid ontbreekt, wordt dit als een waarschuwing gerapporteerd in de output, bijvoorbeeld:

```

Kan server script 'Script' niet starten (ontbrekende mogelijkheid RunServerScript)

```

### [Toegang tot instanties](#toegang-tot-instanties)[](#toegang-tot-instanties)

Een enkele mogelijkheid behandelt toegang tot instanties:

-

AccessOutsideWrite  - Script is toegestaan om instanties van buiten de sandbox-container op te halen en te ontvangen

Wanneer de mogelijkheid niet beschikbaar is, kan het script alleen instanties opzoeken die binnen zijn eigen sandbox-container zijn. Bijvoorbeeld, als het script direct in de sandbox-container is geplaatst, retourneert script.Parent.Parent  nil .

Bovendien, elke Roblox API gebeurtenis die een [Instance](/docs/nl-nl/reference/engine/classes/Instance)  doorgeeft, geeft in plaats daarvan nil  door voor elke [Instance](/docs/nl-nl/reference/engine/classes/Instance)  buiten de sandbox-container. Bijvoorbeeld, als de [BasePart.Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  wordt geactiveerd door een aanraking van een instantie buiten de sandbox-container, wordt de gebeurtenis nog steeds ontvangen, maar het argument is nil .

Vermijd het instellen van deze mogelijkheid; sandboxgaranties zijn zwakker wanneer scripts kunnen interageren met elke instantie in een spel.

#### [Toegang tot services](#toegang-tot-services)[](#toegang-tot-services)

Zelfs zonder AccessOutsideWrite , kunnen scripts in de sandbox-container nog steeds toegang krijgen tot game , workspace , en services. Deze toegang wordt geboden zodat scripts nog steeds nuttige methoden van die globals kunnen aanroepen, zoals [DataModel.GetService](/docs/nl-nl/reference/engine/classes/DataModel#GetService) , maar toegang tot hun kindinstanties wordt nog steeds gevalideerd.

#### [Intern doorgegeven instanties](#intern-doorgegeven-instanties)[](#intern-doorgegeven-instanties)

Als een instantie wordt doorgegeven via een functieaanroep die niet door Roblox API's gaat, wordt de referentie behouden. Echter, als een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  op deze manier wordt doorgegeven, kan deze niet worden vereist zonder AccessOutsideWrite . Dit komt omdat de return van de [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  vaak wijzigbaar is en kan worden aangepast door een script in een sandbox-container.

### [Scriptfunctionaliteitscontrole](#scriptfunctionaliteitscontrole)[](#scriptfunctionaliteitscontrole)

Deze set mogelijkheden controleert enkele algemene aspecten van scripts:

-

CreateInstances  - Script kan nieuwe instanties maken met [Instance.new](/docs/nl-nl/reference/engine/datatypes/Instance#new) , [Instance.fromExisting](/docs/nl-nl/reference/engine/datatypes/Instance#fromExisting) , of [Instance:Clone()](/docs/nl-nl/reference/engine/classes/Instance#Clone)

-

LoadString  - Script is toegestaan om [loadstring](/docs/nl-nl/reference/engine/globals/LuaGlobals#loadstring)  aan te roepen

-

LoadUnownedAsset  - Script is toegestaan om [require](/docs/nl-nl/reference/engine/globals/LuaGlobals#require)  aan te roepen met een asset ID of [AssetService:LoadAssetAsync()](/docs/nl-nl/reference/engine/classes/AssetService#LoadAssetAsync)

-

ScriptGlobals  - Script heeft [shared](/docs/nl-nl/reference/engine/globals/LuaGlobals#shared)  en [_G](/docs/nl-nl/reference/engine/globals/LuaGlobals#_G)  beschikbaar

Houd er rekening mee dat standaard functiebeperkingen nog steeds van toepassing zijn. Zelfs als LoadString  is ingeschakeld, moet het spel het nog steeds inschakelen in [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) , en het is nog steeds alleen beschikbaar op de server.

Om nieuwe instanties te maken, is naast CreateInstances  een aanvullende Engine API mogelijkheid vereist die toegang biedt tot die instantie.

### [Toegang tot Engine API](#toegang-tot-engine-api)[](#toegang-tot-engine-api)

Deze laatste groep mogelijkheden controleert de toegang van scripts tot verschillende Engine API's:

-

Animation  - Toegang tot instanties gerelateerd aan animaties

-

AssetCreateUpdate  - Toegang tot Engine API's gerelateerd aan het creëren of bijwerken van assets

-

AssetManagement  - Toegang tot Engine API's gerelateerd aan operaties op assets die niet lezen, creëren of bijwerken

-

AssetRead  - Toegang tot Engine API's gerelateerd aan het verkrijgen van informatie over assets

-

Audio  - Toegang tot instanties gerelateerd aan audio API's

-

AvatarAppearance  - Toegang tot instanties gerelateerd aan de visuele elementen van avatars

-

AvatarBehavior  - Toegang tot Engine API's gerelateerd aan het controleren of wijzigen van de humanoïde

-

Basic  - Toegang tot algemene API's die weinig risico bieden

-

CSG  - Toegang tot instanties en functies gerelateerd aan constructieve solide geometrie (CSG)

-

CapabilityControl  - Toegang tot het wijzigen van de Sandboxed  en Capabilities  eigenschappen van instanties

-

Capture  - Toegang tot Engine API's gerelateerd aan het vastleggen van screenshots of video's op het scherm van de gebruiker

-

Chat  - Toegang tot instanties gerelateerd aan in-game chat

-

Consequences  - Toegang tot API's voor het straffen van gebruikers (schoppen of verbannen)

-

DataStore  - Toegang tot data store en geheugen store API's

-

DynamicGeneration  - Toegang tot Engine API's gerelateerd aan het dynamisch wijzigen van assets

-

Environment  - Toegang tot instanties gerelateerd aan de controle van hoe de omgeving wordt weergegeven

-

Groups  - Toegang tot Engine API's met betrekking tot groepen/gemeenschappen

-

Input  - Toegang tot instanties gerelateerd aan gebruikersinvoer

-

LegacySound  - Toegang tot Engine API's gerelateerd aan geluid dat zal worden verouderd

-

LoadOwnedAsset  - Toegang tot Engine API's voor het laden van assets die door jou zijn eigendom, aan jou zijn gedeeld, eigendom zijn van Roblox, of een onschadelijk assettype zijn

-

Logging  - Toegang tot de logs API

-

Material  - Toegang tot Engine API's gerelateerd aan materialen

-

Monetization  - Toegang tot Engine API's gerelateerd aan het monetiseren van een spel, met uitzondering van de meeste PromptPurchases

-

Network  - Toegang tot HTTP-netwerk API's

-

Physics  - Toegang tot instanties gerelateerd aan fysica

-

PlatformAvatarEditing  - Toegang tot Engine API's gerelateerd aan het creëren of bijwerken van avatars, of API's om daarbij te helpen

-

Players  - Toegang tot Engine API's gerelateerd aan de [Player](/docs/nl-nl/reference/engine/classes/Player)  klasse of die [Players.LocalPlayer](/docs/nl-nl/reference/engine/classes/Players#LocalPlayer)  retourneren/interageren

-

PromptExternalPurchase  - Staat toegang toe tot Engine API's gerelateerd aan het vragen om de aankoop van willekeurige assets

-

RemoteEvent  - Toegang tot instanties voor interne netwerkoperaties

-

SensitiveInput  - Toegang tot Engine API's gerelateerd aan het vastleggen van gevoelige invoer van de gebruiker, d.w.z. hardware-sensoren met hoge privacy.

-

ServerCommunication  - Toegang tot Engine API's gerelateerd aan cross-server communicatie, zoals [MessagingService](/docs/nl-nl/reference/engine/classes/MessagingService)

-

Social  - Toegang tot Engine API's gerelateerd aan sociale functies, zoals vrienden en uitnodigingen

-

Teleport  - Toegang tot Engine API's gerelateerd aan teleporteren

-

UI  - Toegang tot instanties gerelateerd aan gebruikersinterfaces

De mogelijkheden van elke klasse, eigenschap, methode en gebeurtenis worden weergegeven in de [Engine API referentie](/docs/nl-nl/../reference/engine) . Bijvoorbeeld, [Player:GetFriendsOnlineAsync()](/docs/nl-nl/reference/engine/classes/Player#GetFriendsOnlineAsync)  vereist de Player  en Social  mogelijkheden.

Verschillende [HttpService](/docs/nl-nl/reference/engine/classes/HttpService)  methoden zijn beschikbaar zonder enige mogelijkheden, behalve dat ze de scripts kunnen uitvoeren:

-

[HttpService:JSONDecode()](/docs/nl-nl/reference/engine/classes/HttpService#JSONDecode)

-

[HttpService:JSONEncode()](/docs/nl-nl/reference/engine/classes/HttpService#JSONEncode)

-

[HttpService:GenerateGUID()](/docs/nl-nl/reference/engine/classes/HttpService#GenerateGUID)

Als een instantie-eigenschap of methode wordt benaderd zonder een vereiste mogelijkheid, wordt er een fout gerapporteerd die de ontbrekende mogelijkheid beschrijft.

Ten slotte dekken mogelijkheden niet elke instantie in de Roblox Engine vandaag. Instanties die niet in deze sectie of de volgende zijn vermeld, zijn niet beschikbaar voor interactie vanuit een sandbox-container en gooien een foutmelding dat een Unassigned  mogelijkheid niet beschikbaar is voor het huidige script.

Een aanvullende beperking is dat de [getfenv()](/docs/nl-nl/reference/engine/globals/LuaGlobals#getfenv)  en [setfenv()](/docs/nl-nl/reference/engine/globals/LuaGlobals#setfenv)  functies niet beschikbaar zijn voor scripts in een sandbox-container. Het aanroepen ervan vanuit een sandbox-script rapporteert:

```

De huidige thread kan ['getfenv'/'setfenv'] niet aanroepen - het doel gebruikt API's die niet beschikbaar zijn in de huidige sandbox

```

Alleen de toegang van scripts tot instanties is beperkt. De instanties zelf kunnen nog steeds bestaan en zelfstandig functioneren binnen een sandbox-container. Lichten blijven branden, gebruikersinterfaces blijven zichtbaar, en audio-opstellingen die al zijn aangesloten spelen geluiden af.

## [Interacties tussen containers](#interacties-tussen-containers)[](#interacties-tussen-containers)

### [Geneste containers](#geneste-containers)[](#geneste-containers)

Wanneer een sandbox-container genest is binnen een andere, zijn de instanties van de binnenste container toegankelijk voor de buitenste.

De mogelijkheden van de binnenste container worden beperkt door de mogelijkheden van de buitenste. Bijvoorbeeld, als de buitenste container mogelijkheden heeft van Basic , Audio  en CSG , terwijl de binnenste container Basic  en Network  heeft, zijn alleen de Basic  mogelijkheden beschikbaar voor de binnenste container tijdens runtime.

Als er geen gemeenschappelijke mogelijkheden zijn tussen de binnenste en buitenste containers, is de resulterende mogelijkheidenset leeg.

### [Bindbare functies en gebeurtenissen](#bindbare-functies-en-gebeurtenissen)[](#bindbare-functies-en-gebeurtenissen)

[BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent)  en [BindableFunction](/docs/nl-nl/reference/engine/classes/BindableFunction)  bieden de beste manier om te communiceren met de container of deze in staat te stellen callbacks uit te voeren met mogelijkheden die het zelf niet direct mag gebruiken.

Wanneer een gebeurtenis wordt geactiveerd of een functie wordt aangeroepen, worden verbindingen uitgevoerd in de context van de functie die ze heeft geregistreerd. Dit betekent dat als de gebeurtenis of functie callback is geregistreerd door de sandbox-container, deze wordt aangeroepen met de mogelijkheden van die container. Als de callback is geregistreerd door de code buiten, wanneer scripts van de sandbox-container ze aanroepen, voeren ze jouw functies uit met de mogelijkheden die beschikbaar zijn voor jouw functies.

Het is belangrijk op te merken dat zelfs met de AccessOutsideWrite  mogelijkheid, scripts in sandbox-containers geen gebeurtenissen of functies buiten hun containers kunnen aanroepen als ze een grotere mogelijkheidenset hebben dan de container zelf.

Wanneer een sandbox-script probeert een gebeurtenis of functie te activeren of aan te roepen ([BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent) , [BindableFunction](/docs/nl-nl/reference/engine/classes/BindableFunction) , of [RemoteEvent](/docs/nl-nl/reference/engine/classes/RemoteEvent) ) waarvan de vooroudermogelijkheden groter zijn dan die van hemzelf, geeft de fout de eigenschap aan die moet worden gecontroleerd.

Als het doel zich niet binnen een sandbox-container bevindt:

```

De huidige thread kan '<Target>' niet activeren omdat '<Target>' de Sandboxed eigenschap op false heeft staan, maar de aanroepende thread is sandboxed

```

Om dit op te lossen, stel je [Sandboxed](/docs/nl-nl/reference/engine/classes/Instance#Sandboxed)  in op true  voor het doel. Alternatief kun je de bron van de aanroepende thread aanpassen zodat [Sandboxed](/docs/nl-nl/reference/engine/classes/Instance#Sandboxed)  is ingesteld op false , maar dit wordt niet aanbevolen omdat het de beveiligingsvoordelen van sandboxing tenietdoet.

Als het doel sandboxed is maar mogelijkheden heeft die de aanroeper mist:

```

De huidige thread kan '<Target>' niet activeren omdat '<Target>' extra waarden heeft voor de Capabilities eigenschap: <First Missing Capability> (en N meer)

```

Om dit op te lossen, beperk je de [Capabilities](/docs/nl-nl/reference/engine/classes/Instance#Capabilities)  van het doel tot een subset van die van de aanroeper, of breid je de [Capabilities](/docs/nl-nl/reference/engine/classes/Instance#Capabilities)  van de aanroeper uit om overeen te komen met die van het doel.

### [Module vereisen](#module-vereisen)[](#module-vereisen)

Binnenste [ModuleScripts](/docs/nl-nl/reference/engine/classes/ModuleScript)  kunnen zoals gebruikelijk door de sandbox-container worden vereist. Echter, als de doelinstantie zich buiten de container bevindt, kan de [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  alleen worden vereist als de set mogelijkheden die beschikbaar is voor hem kleiner of gelijk is aan de mogelijkheden die beschikbaar zijn voor de container.

Deze beperking is niet van toepassing op RunClientScript  en RunServerScript  mogelijkheden. Als de [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  in een container met alleen RunClientScript  is geplaatst, maar wordt vereist vanuit een script dat de RunServerScript  mogelijkheid heeft, is het toegestaan om te slagen en die functies op de server uit te voeren.

Wanneer [require()](/docs/nl-nl/reference/engine/globals/LuaGlobals#require)  faalt door een mogelijkheid mismatch, geeft de fout de doelmodule en de eigenschap aan die moet worden gecontroleerd op dezelfde manier als bindbare functies en gebeurtenissen beschreven in de vorige sectie.

### [Direct aangeroepen functies](#direct-aangeroepen-functies)[](#direct-aangeroepen-functies)

Als een [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  in een sandbox-container van buiten de container wordt vereist, zijn sommige van de beschermingen niet beschikbaar. In het bijzonder kan de doelfunctie toegang krijgen tot alle instanties die beschikbaar zijn voor de aanroeper. Als de aanroeper zich niet in een sandbox-container bevindt, gedraagt de aanroep zich alsof AccessOutsideWrite  beschikbaar is voor hem.

Andere mogelijkheid beperkingen blijven van toepassing. Als je een DataStore  toegang mogelijkheid hebt, maar de doelmodule niet, kan deze geen [DataStore](/docs/nl-nl/reference/engine/classes/DataStore)  methoden aanroepen. Echter, als je je eigen functie doorgeeft die met [DataStore](/docs/nl-nl/reference/engine/classes/DataStore)  werkt, kan de doelmodule deze tijdens die aanroep uitvoeren. Als de doelmodule een thread plant met methoden zoals die van [task](/docs/nl-nl/reference/engine/libraries/task) , verliezen die threads de mogelijkheid om die functie aan te roepen.

Instanties kunnen aan de doelmodule worden doorgegeven of aan de modulevelden worden toegewezen.

Indien nodig, wordt aanbevolen om tabelleden toe te wijzen met [rawset](/docs/nl-nl/reference/engine/globals/LuaGlobals#rawset)  om te voorkomen dat __index / __newindex  metamethoden worden uitgevoerd die mogelijk op de tabel zijn ingesteld.

De algemene aanbeveling is om te communiceren met [BindableEvent](/docs/nl-nl/reference/engine/classes/BindableEvent)  en [BindableFunction](/docs/nl-nl/reference/engine/classes/BindableFunction)  wanneer mogelijk.

### [Beweging van instanties](#beweging-van-instanties)[](#beweging-van-instanties)

De meeste instanties hebben geen beperkingen op beweging tussen containers. Scriptinstanties kunnen echter alleen worden verplaatst naar een container die dezelfde set mogelijkheden of een subset van die mogelijkheden heeft.

Dit betekent dat een sandbox-container met AccessOutsideWrite  niet zomaar een script binnen zichzelf kan herplaatsen naar buiten en meer mogelijkheden kan krijgen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
