<!-- Source: https://create.roblox.com/docs/nl-nl/players/teams -->

Teams implementeren | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelers](/docs/nl-nl/players)

# Teams implementeren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt spelers in je spel in meerdere teams verdelen met de [Teams](/docs/nl-nl/reference/engine/classes/Teams)  service. Door de [Teams](/docs/nl-nl/reference/engine/classes/Teams)  service te [configureren](#teams-toevoegen)  en [teams toe te wijzen](#spelers-aan-teams-toewijzen) , worden spelers automatisch onderscheiden op basis van hun [weergavenaam](/docs/nl-nl/characters/name-health-display)  kleur, evenals hun naam in de standaard spelerslijst.

## [Teams toevoegen](#teams-toevoegen)[](#teams-toevoegen)

Standaard zijn er geen teams geconfigureerd. Om teams toe te voegen:

1.

In de [Explorer](/docs/nl-nl/studio/explorer)  hiërarchie, beweeg je de muis over het [Teams](/docs/nl-nl/reference/engine/classes/Teams)  object en klik op het ⊕  icoon om een lijst van objecten weer te geven.

2.

Voeg een nieuw [Team](/docs/nl-nl/reference/engine/classes/Team)  object toe onder de [Teams](/docs/nl-nl/reference/engine/classes/Teams)  service.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/explorer/Teams-Team.png)

3.

Selecteer het nieuwe [Team](/docs/nl-nl/reference/engine/classes/Team)  object en wijzig in het [Properties](/docs/nl-nl/studio/properties)  venster de team [Name](/docs/nl-nl/reference/engine/classes/Team#Name)  en wijs een unieke bijpassende [TeamColor](/docs/nl-nl/reference/engine/classes/Team#TeamColor)  toe. De naam en kleur van een team verschijnen beide in de spelerslijst van het spel.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Team-Name-TeamColor.png)

4.

Herhaal deze stappen om meer teams toe te voegen.

## [Spelers aan teams toewijzen](#spelers-aan-teams-toewijzen)[](#spelers-aan-teams-toewijzen)

Standaard wijst  Roblox nieuwe spelers die het spel betreden automatisch toe aan het team met de minste leden, en je kunt nog steeds de volgende stappen gebruiken om spelers aan een specifiek team toe te wijzen.

1.

Selecteer elk [Team](/docs/nl-nl/reference/engine/classes/Team)  object in de [Teams](/docs/nl-nl/reference/engine/classes/Teams)  service om de eigenschappen weer te geven.

2.

Vink het [AutoAssignable](/docs/nl-nl/reference/engine/classes/Team#AutoAssignable)  selectievakje uit.

 ![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Team-AutoAssignable-Disabled.png)

3.

Wijs een speler toe aan een specifiek team door hun [Player.Team](/docs/nl-nl/reference/engine/classes/Player#Team)  eigenschap te wijzigen naar de teamnaam in het formaat van Teams[TEAM_NAME] , zoals Teams["Blauw Team"] .

## [Team spawnlocaties](#team-spawnlocaties)[](#team-spawnlocaties)

Je kunt [SpawnLocation](/docs/nl-nl/reference/engine/classes/SpawnLocation)  objecten gebruiken om spelers van verschillende teams op specifieke locaties te laten spawnen wanneer ze zich aanmelden of respawnen. Standaard zijn [SpawnLocations](/docs/nl-nl/reference/engine/classes/SpawnLocation)  neutraal  en kan elke speler erop spawnen, dus je moet elk ervan vergrendelen voor het team dat het kan bezetten met de volgende stappen:

1.

Gebruik de [Explorer](/docs/nl-nl/studio/explorer)  om een nieuwe [SpawnLocation](/docs/nl-nl/reference/engine/classes/SpawnLocation)  in de werkruimte in te voegen.

2.

Met de nieuwe [SpawnLocation](/docs/nl-nl/reference/engine/classes/SpawnLocation)  geselecteerd, vink je het [Neutral](/docs/nl-nl/reference/engine/classes/SpawnLocation#Neutral)  selectievakje uit in het [Properties](/docs/nl-nl/studio/properties)  venster.

3.

Stel de [TeamColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#TeamColor)  eigenschap van de spawn in op de [TeamColor](/docs/nl-nl/reference/engine/classes/Team#TeamColor)  van een bestaand [team](#teams-toevoegen) . Bijvoorbeeld, als de [Team.TeamColor](/docs/nl-nl/reference/engine/classes/Team#TeamColor)  van het beoogde team Lapis  is, stel dan de [SpawnLocation.TeamColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#TeamColor)  van de spawn ook in op Lapis .

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/Team-Name-TeamColor.png)[Team.TeamColor](/docs/nl-nl/reference/engine/classes/Team#TeamColor)

![](https://prod.docsiteassets.roblox.com/assets/studio/properties/SpawnLocation-TeamColor.png)[SpawnLocation.TeamColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#TeamColor)

Let op dat de [SpawnLocation.TeamColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#TeamColor)  eigenschap anders is dan [SpawnLocation.BrickColor](/docs/nl-nl/reference/engine/classes/SpawnLocation#BrickColor)  en [SpawnLocation.Color](/docs/nl-nl/reference/engine/classes/SpawnLocation#Color) , die de visuele  kleur van het spawnobject vertegenwoordigen en niet gerelateerd zijn aan teamfunctionaliteit.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
