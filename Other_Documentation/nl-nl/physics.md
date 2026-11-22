<!-- Source: https://create.roblox.com/docs/nl-nl/physics -->

Fysica | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Fysica](/docs/nl-nl/physics)

# Fysica

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox gebruikt een rigide lichaam fysica-engine. [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  zijn onderhevig aan fysieke krachten zolang ze niet [Anchored](/docs/nl-nl/reference/engine/classes/BasePart#Anchored)  zijn. Je kunt fysieke [assemblages](#assemblages)  maken met behulp van bevestigingen en beperkingen, en je kunt [botsingen](#botsingen)  tussen objecten detecteren en beheersen met behulp van evenementen en botsingsfiltering.

## [Assemblages](#assemblages)[](#assemblages)

Een [assemblage](/docs/nl-nl/physics/assemblies)  is een of meer [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  die zijn verbonden door rigide beperkingen of motoren (geanimeerde rigide gewrichten). Assemblages kunnen worden ingesteld op een initiële lineaire of hoeksnelheid, of hun gedrag kan worden beïnvloed door [beperkingen](#beperkingen) .

![Een lichtblauwe kubus tegen een donkerblauwe achtergrond die een assemblage van 1 onderdeel vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Example-Block.png) 1 assemblage; 1 onderdeel

![Een humanoïde karaktermodel tegen een donkerblauwe achtergrond die een assemblage van 18 onderdelen vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Example-Avatar.png) 1 assemblage; 18 onderdelen

![Een piratenboot die een assemblage van 179 onderdelen vertegenwoordigt.](https://prod.docsiteassets.roblox.com/assets/physics/assemblies/Assembly-Example-Ship.png) 1 assemblage; 179 onderdelen

## [Beperkingen](#beperkingen)[](#beperkingen)

Niet-geankerde assemblages reageren op kracht van de zwaartekracht en botsingen, maar fysieke kracht kan ook worden toegepast en gesimuleerd via [mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints)  of [mover beperkingen](/docs/nl-nl/physics/mover-constraints) .

Mechanisch Mover

Mechanische beperkingen omvatten bekende objecten zoals [scharnieren](/docs/nl-nl/physics/constraints/hinge) , [veren](/docs/nl-nl/physics/constraints/spring)  en [touwen](/docs/nl-nl/physics/constraints/rope)  die kunnen worden gebruikt om mechanismen te bouwen. Elk wordt samengevat in de [mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints)  gids.

## [Botsingen](#botsingen)[](#botsingen)

Botsingsevenementen vinden automatisch plaats wanneer twee [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  elkaar aanraken of stoppen met aanraken in de 3D-wereld. Je kunt [detecteren](/docs/nl-nl/workspace/collisions)  deze botsingen via de [Touched](/docs/nl-nl/reference/engine/classes/BasePart#Touched)  en [TouchEnded](/docs/nl-nl/reference/engine/classes/BasePart#TouchEnded)  evenementen die plaatsvinden ongeacht de waarde van de [CanCollide](/docs/nl-nl/reference/engine/classes/BasePart#CanCollide)  eigenschap van elk onderdeel.

Via [botsingsfiltering](/docs/nl-nl/workspace/collisions#botsingsfiltering)  technieken zoals botsingsgroepen of onderdeel-tot-onderdeel filtering, kun je beheersen welke fysieke assemblages met elkaar botsen.

Zie de [botsingen](/docs/nl-nl/workspace/collisions)  gids voor meer details over het detecteren en filteren van botsingen.

## [Netwerkbezit](#netwerkbezit)[](#netwerkbezit)

Om complexe fysieke mechanismen te ondersteunen en tegelijkertijd te streven naar een soepele en responsieve ervaring voor spelers, maakt de Roblox fysica-engine gebruik van een gedistribueerd fysica  systeem waarin berekeningen worden verdeeld tussen de server en alle verbonden clients. Binnen dit systeem wijst de engine netwerkbezit  van fysiek gesimuleerde [BaseParts](/docs/nl-nl/reference/engine/classes/BasePart)  toe aan ofwel een client of server om het werk van het berekenen van fysica te verdelen. Zie de [netwerkbezit](/docs/nl-nl/physics/network-ownership)  gids voor verdere details.

## [Adaptieve tijdstappen](#adaptieve-tijdstappen)[](#adaptieve-tijdstappen)

De engine benadrukt de beste prestaties door assemblages automatisch toe te wijzen aan een van de drie simulatiesnelheden. Voor scenario's met complexe mechanismen zoals tanks, kun je de stabiliteit verbeteren door een vaste tijdstap in te stellen. Zie de [adaptieve tijdstappen](/docs/nl-nl/physics/adaptive-timestepping)  gids voor meer informatie.

## [Slaap systeem](#slaap-systeem)[](#slaap-systeem)

Wanneer een assemblage niet beweegt of versnelt, verbetert de Roblox fysica-engine de prestaties door automatisch te stoppen met het simuleren van de assemblage. Zie de [slaap systeem](/docs/nl-nl/physics/sleep-system)  gids voor details.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
