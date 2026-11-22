<!-- Source: https://create.roblox.com/docs/nl-nl/scripting/security/access-control -->

Toegangscontrole en vertrouwelijkheid | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Scripting](/docs/nl-nl/scripting)
6. /
7. Beveiliging

# Toegangscontrole en vertrouwelijkheid

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De volgende inhoud behandelt verschillende concepten en tactieken om de beveiliging te verbeteren en valsspelen in je Roblox-spellen te verminderen. Het wordt ten zeerste aanbevolen dat alle ontwikkelaars deze doorlezen om ervoor te zorgen dat je spellen veilig en eerlijk zijn voor alle gebruikers. Bekijk de zijbalk voor aanvullende beveiligingsthema's.

Begrijpen welke informatie en activa zichtbaar zijn voor cliënten is cruciaal voor het handhaven van zowel de beveiliging als de vertrouwelijkheid van je spel. Ontwikkelaars onderschatten vaak hoeveel zichtbaar is voor exploiters en gerepliceerd wordt naar cliënten. Exploiters hebben de mogelijkheid om "beperkte" plaatsen binnen je universum te benaderen als ze zich bij een enkele plaats kunnen voegen. Ze kunnen alle inhoud bekijken die naar hun cliënt is gerepliceerd, ongeacht of deze zichtbaar is of momenteel in gebruik is. Bovendien kunnen exploiters alle gerepliceerde lokale scripts en ModuleScripts decompileren, zelfs als ze nooit op de cliënt worden uitgevoerd.

## [Teleportatie aan de cliëntzijde binnen universums](#teleportatie-aan-de-cliëntzijde-binnen-universums)[](#teleportatie-aan-de-cliëntzijde-binnen-universums)

Eenmaal binnen een universum kunnen cliënten naar elke plaats binnen dat universum teleporteren, waardoor ze mogelijk alle bedoelde toegangsbeperkingen of voortgangspoorten omzeilen. Dit kan ook leiden tot het onbedoeld lekken van niet-uitgebrachte inhoud, bijvoorbeeld vanuit een ontwikkelings- of staging-spel. Het is belangrijk om te begrijpen dat:

-

Het uitschakelen van "Directe Toegang" verwijdert alleen de Join-knop van subplaatsen op de website — het voorkomt niet dat cliënten-gestarte teleportaties plaatsvinden

-

Ga ervan uit dat exploiters de aanwezigheid van alle subplaatsen binnen je universum zullen ontdekken

-

Een cliënt kan naar elke subplaats teleporteren als ze toegang hebben tot een enkele plaats, zoals de rootplaats, ongeacht je bedoelde ontwerpstroom

Veel ontwikkelaars proberen toegang te voorkomen door ongeautoriseerde gebruikers uit een subplaats te schoppen. Dit kan werken om gameplay te blokkeren, maar het voorkomt niet  dat inhoud naar de cliënt wordt gerepliceerd, aangezien replicatie begint zodra de speler zich voegt en voordat de serverzijde kick-logica kan worden uitgevoerd.

### [Gebruik veilige teleportaties](#gebruik-veilige-teleportaties)[](#gebruik-veilige-teleportaties)

De meest effectieve manier om ongeautoriseerde toegang via teleportatie te voorkomen, is door Toegangscontrole voor Plaatsen  in het Creator Dashboard in te stellen op Veilig binnen universum alleen . Dit beperkt alle niet-startplaatsen tot server-gestarte teleportaties, waardoor cliënten-gestarte teleportaties op het platformniveau worden geblokkeerd voordat de speler ooit de subplaats betreedt. Omdat de speler nooit toetreedt, wordt er geen inhoud naar hen gerepliceerd.

Het inschakelen van Veilig binnen universum alleen  is de aanbevolen instelling voor elk spel met beperkte subplaatsen, voortgangsgebonden gebieden of testplaatsen waartoe spelers geen toegang zouden moeten hebben.

Voor configuratiestappen en migratie-instructies voor bestaande spellen die cliënten-gestarte teleportaties gebruiken, zie [Teleport tussen plaatsen](/docs/nl-nl/projects/teleport#configureer-veilige-teleportatie) .

### [Verdediging-in-diepte voor beperkte plaatsen](#verdediging-in-diepte-voor-beperkte-plaatsen)[](#verdediging-in-diepte-voor-beperkte-plaatsen)

Voor universums die geen veilige teleportaties kunnen gebruiken, of als aanvullende beschermingslagen naast hen, combineer de volgende maatregelen:

-

Houd ontwikkelings- en testplaatsen in aparte, privé-universums  — dit is de enige betrouwbare manier om vertrouwelijkheid voor niet-uitgebrachte inhoud te waarborgen. Stuur nooit vertrouwelijke evenementactiva, scripts of UI-elementen naar de productieomgeving voordat ze bedoeld zijn om actief te zijn.

-

Gebruik indien mogelijk streaming om te beperken hoeveel van de wereld naar een nieuwe speler wordt gerepliceerd.

-

Voeg serverzijde groepsrol- of badgeverificatie toe en verifieer de status of voortgangseisen van de speler.

-

Sta standaard geen binnenkomende spelers toe. Dit zorgt ervoor dat geen enkele speler wordt toegelaten, zelfs niet als het verificatieproces onduidelijk is, zoals in het geval van een uitzondering die door de engine wordt gegooid.

-

Gebruik indien praktisch de [Ban API](/docs/nl-nl/reference/engine/classes/Players#BanAsync)  voor spelers die niet aan de validatie voldoen. Dit voorkomt dat spelers continu proberen zich met hetzelfde account aan te sluiten.

## [Replicatie](#replicatie)[](#replicatie)

Replicatie beschrijft hoe status over het netwerk wordt overgedragen tussen instanties van de engine. Het replicatiemodel van Roblox is over het algemeen vereenvoudigd op een paar belangrijke manieren:

-

Instanties zijn server-autoritair, wat betekent dat voor een instantie om te repliceren tussen alle deelnemers (de server en alle verbonden cliënten) deze op de server moet worden gemaakt.

-

Instantiekenmerken zijn ook server-autoritair, wat betekent dat de meeste kenmerken op de server moeten worden gewijzigd om de wijzigingen zichtbaar te maken voor alle cliënten.

-

Over het algemeen geldt dat een instantie ofwel naar alle verbonden cliënten repliceert of niet. Er zijn enkele uitzonderingen, zoals streaming.

Replicatiecontainers zijn top-level instanties (geparent onder het DataModel) die naar cliënten repliceren. Als een instantie ooit een afstammeling van een replicatiecontainer wordt gedurende zijn levensduur, moet je verwachten dat veel van zijn status naar alle cliënten repliceert. Je kunt meer lezen over veelvoorkomende replicatiecontainers in de [Data model guide](/docs/nl-nl/projects/data-model#replication) . Wanneer je twijfelt, kun je altijd controleren hoe een instantie of eigenschap repliceert in een testomgeving zoals Play Solo. Je kunt meer lezen over testmodi in [Studio testing modes](/docs/nl-nl/studio/testing-modes) .

### [Beveiligingsimplicaties van replicatie](#beveiligingsimplicaties-van-replicatie)[](#beveiligingsimplicaties-van-replicatie)

Elke inhoud die naar een cliënt repliceert, kan door een exploiter worden geëxtraheerd en gedatamineerd. Als algemene regel, vermijd het publiceren of verzenden van vertrouwelijke inhoud naar de live productieomgeving, tenzij je onmiddellijk bereid bent dat deze door gebruikers wordt gezien. Zelfs als er logica is die de vrijgave of toegang van de inhoud in het spel tot een latere datum (of een andere voorwaarde) beperkt, ga ervan uit dat exploiters een manier zullen vinden om je inhoud te ontdekken en te lekken zodra deze is gepubliceerd.

Vermijd te beschrijvende of voorspelbare namen voor gevoelige instanties, inclusief maar niet beperkt tot: scripts, remotes en modellen. Een voorspelbare DataModel-hiërarchie maakt het gemakkelijker om exploits te ontwikkelen.

### [Scriptdecompilatie](#scriptdecompilatie)[](#scriptdecompilatie)

Elke [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript) , [Script](/docs/nl-nl/reference/engine/classes/Script)  met RunContext::Client , of [ModuleScript](/docs/nl-nl/reference/engine/classes/ModuleScript)  kan door een exploiter worden gedecompileerd zodra deze naar hun cliënt is gerepliceerd, zelfs als dergelijke scripts zijn uitgeschakeld, nooit vereist zijn of nooit op de cliënt worden uitgevoerd. Server-only Scripts en ModuleScripts die zijn opgeslagen in ServerStorage  of ServerScriptService  kunnen niet worden gedecompileerd omdat ze nooit naar cliënten repliceren.

Het schrijven van een ModuleScript dat server-only en client-only code in hetzelfde script bevat, is niet aan te raden, aangezien serverzijde logica zal worden blootgesteld in decompilatie en gemakkelijker kan worden geanalyseerd op bugs die kunnen worden geëxploiteerd.

Originele ModuleScript in ReplicatedStorage

```

local module = {}

local Remote = script:WaitForChild("RemoteEvent")

-- Hier is een voorbeeld van een paradigma om te vermijden

-- Houd servercode in Script-instanties of in ServerStorage/ServerScriptStorage!

if game:GetService("RunService"):IsServer() then

  function module:DoServerThing(password)

    if password == "SecretPassword" then

      print("gevoelige servercode")

    end

  end

  Remote.OnServerEvent:Connect(function(player, password)

    module:DoServerThing(password)

  end)

else

  function module:DoServerThing(password)

    Remote:FireServer(password)

  end

end

return module

```

De gecompileerde uitkomst

```

local table1 = {};

local RemoteEvent = script:WaitForChild("RemoteEvent");

if game:GetService("RunService"):IsServer() then

  function table1.DoServerThing(_, p2) -- Regel: 9

    if p2 == "SecretPassword" then

      print("gevoelige servercode");

    end

  end

  RemoteEvent.OnServerEvent:Connect(function(player: Player, p3) -- Regel: 15

    --[[

      Upvalues:

        [1] = table1

    --]]

    table1:DoServerThing(p3);

  end);

  return table1;

end

function table1.DoServerThing(_, p1) -- Regel: 19

  --[[

    Upvalues:

      [1] = RemoteEvent

  --]]

  RemoteEvent:FireServer(p1);

end

return table1;

```

Zoals hierboven weergegeven, onthult decompilatie serverzijde logica, inclusief hardcoded wachtwoorden, bedrijfsregels en implementatiedetails die exploiters kunnen analyseren op kwetsbaarheden.

### [Impact van vertrouwelijkheidsinbreuken](#impact-van-vertrouwelijkheidsinbreuken)[](#impact-van-vertrouwelijkheidsinbreuken)

Vertrouwelijkheidsinbreuken kunnen aanzienlijke gevolgen hebben, zoals:

-

Inhoudslekken : Niet-uitgebrachte items, kaarten of functies kunnen worden ontdekt en openbaar gedeeld voordat officiële aankondigingen plaatsvinden

-

Concurrentievoordeel : Mechanica, algoritmen of aankomende functies kunnen door concurrenten worden omgekeerd

-

Exploitontwikkeling : Blootgestelde serverlogica maakt het sneller en gemakkelijker voor exploiters om kwetsbaarheden te identificeren en gerichte aanvallen te ontwikkelen

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
