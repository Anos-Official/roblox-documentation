<!-- Source: https://create.roblox.com/docs/nl-nl/projects/groups -->

Groepen (teams) | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Projecten](/docs/nl-nl/projects)
6. /
7. [Werken in teams](/docs/nl-nl/projects/groups)

# Groepen (teams)

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een Roblox groep  stelt meerdere makers in staat om aan hetzelfde spel te werken, dezelfde middelen te gebruiken, winsten te delen en alle bijdragers krediet te geven.

Groepsbezit van spellen helpt makers om samen te werken en te opereren als onafhankelijke studio's. Als er een conflict ontstaat binnen een groep, kan Roblox niet helpen bij het bemiddelen of oplossen van meningsverschillen.

## [Groep aanmaken](#groep-aanmaken)[](#groep-aanmaken)

Het aanmaken van een groep kost 100 Robux. Je kunt de [rollen en machtigingen](#rollen-en-machtigingen)  beheren vanuit het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  of [Gemeenschappen](https://www.roblox.com/communities) .

Lees voordat je een groep aanmaakt zorgvuldig de [regels en verwachtingen](/docs/nl-nl/projects/group-guidelines)  voor groepsbeheer door.

Om een nieuwe groep te maken:

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) , breid de accountwisselaar in de linkerbovenhoek uit en klik op de plus (+)  knop.

2.

Op de pagina Groep Aanmaken , upload een afbeelding voor het groepslogo en voer de groepsnaam in.

3.

Klik wanneer je klaar bent op de Aankoop  knop. Zodra de groep is aangemaakt, word je doorgestuurd naar de groepsprofielpagina waar je de details van de groep kunt wijzigen, inclusief het toevoegen van maximaal drie sociale links.

## [Rollen en machtigingen](#rollen-en-machtigingen)[](#rollen-en-machtigingen)

Groepsleden kunnen één of meerdere rollen  binnen een groep toegewezen krijgen, en elke rol heeft machtigingen  die de mogelijkheden van de leden specificeren.

Rolconfiguratie is alleen toegankelijk als je de groeps eigenaar bent of toestemming hebt om groepsrollen te maken, configureren en toe te wijzen.

Om programmatisch groepsroltoewijzingen vanuit een spelserver te beheren, gebruik [HttpService](/docs/nl-nl/reference/engine/classes/HttpService)  om de ondersteunde Open Cloud Groups-eindpunten aan te roepen. Voor setup en voorbeeldcode, zie [Gebruik met Open Cloud](/docs/nl-nl/cloud-services/http-service#use-with-open-cloud) .

1.

Van het [Creator Dashboard](https://create.roblox.com/dashboard/creations) , breid de accountwisselaar in de linkerbovenhoek uit en selecteer de groep.

2.

Breid de accountwisselaar opnieuw uit en selecteer Rollen .

3.

Bevestig voor elke rol zorgvuldig de machtigingen onder het Permissions  tabblad.

Machtigingen zijn georganiseerd in Algemeen , Creatie , en Community  categorieën. De secties hieronder beschrijven de machtigingen die beschikbaar zijn in elke categorie.

### [Algemeen](#algemeen)[](#algemeen)

Algemene machtigingen

| Rollen beheren | | Leden met deze machtiging kunnen rollen onder hun hoogste rol maken, bewerken, verwijderen, opnieuw ordenen en toewijzen of intrekken. Ze kunnen alleen machtigingen bewerken die ze al hebben. |
| --- | --- |
| Rollen toewijzen aan of verwijderen van leden | | Leden met deze machtiging kunnen rollen onder hun hoogste rol aan elk lid toewijzen of intrekken. |
| Leden uitnodigen of goedkeuren | | Leden met deze machtiging kunnen mensen uitnodigen voor de groep en goedkeuring geven voor lidmaatschapsverzoeken. |
| Leden verwijderen | | Leden met deze machtiging kunnen leden verwijderen wiens hoogste rol onder hun eigen ligt. |
| Leden verbannen | | Leden met deze machtiging kunnen leden verbannen wiens hoogste rol onder hun eigen ligt. |
| Groepsprofiel configureren | | Leden met deze machtiging kunnen het groepsprofiel configureren. |
| Auditlogboeken bekijken | | Leden met deze machtiging kunnen [groepsauditlogs](#groepsauditlogs)  bekijken. |
| Bondgenoten en vijanden beheren | | Leden met deze machtiging kunnen de bondgenoten en vijanden van de groep beheren. |

### [Creatie](#creatie)[](#creatie)

Creaties

| Ervaringen playtesten | | Leden met deze rol kunnen alle spellen die door de groep zijn bezeten spelen, zelfs als ze niet zijn vrijgegeven voor een breder publiek. Optioneel beschikbaar als een [per-spel machtiging](/docs/nl-nl/projects/configure-games) . |
| Ervaringen bewerken | | Leden met deze rol kunnen alle spellen en [middelen](/docs/nl-nl/projects/assets)  die door de groep zijn bezeten bewerken en alle functies in de [Data Stores Manager](/docs/nl-nl/cloud-services/data-stores/data-stores-manager)  gebruiken. Bevat niet het bewerken van een spel buiten een [samenwerkings](/docs/nl-nl/projects/collaboration)  sessie of het opslaan van een plaats van het ene spel naar het andere spel. Optioneel beschikbaar als een [per-spel machtiging](/docs/nl-nl/projects/configure-games) . |
| Ervaringen publiceren | | Leden met deze rol kunnen zowel spellen bewerken, zoals hierboven, als ook spellen publiceren naar Roblox. Optioneel beschikbaar als een [per-spel machtiging](/docs/nl-nl/projects/configure-games) . |
| Deellinks beheren | | Leden met deze rol kunnen [deel links](/docs/nl-nl/production/promotion/share-links)  maken/configureren. |
| Ervaringsevenementen beheren | | Leden met deze rol kunnen [ervaring evenementen](/docs/nl-nl/production/promotion/experience-events)  maken/configureren. |
| Ervaringen modereren | | Leden met deze rol kunnen alle in-game chatberichten bekijken (alleen-lezen; lid moet 18+ zijn) en verbannen of beheerde verbannen gebruikers in alle spellen die door de groep zijn bezeten. |
| Beheer van Inkomsten genereren voor ervaringen | | Leden met deze rol kunnen monetisatieproducten zoals [passen](/docs/nl-nl/production/monetization/passes) , [ontwikkelaarsproducten](/docs/nl-nl/production/monetization/developer-products) , [abonnementen](/docs/nl-nl/production/monetization/subscriptions)  en meer beheren. Optioneel beschikbaar als een [per-spel machtiging](/docs/nl-nl/projects/configure-games) . |
| Beheer van geheimen voor ervaringen | | Leden met deze rol kunnen de lijst van [geheimen](/docs/nl-nl/cloud-services/secrets)  zien en kunnen geheimen voor alle spellen die door de groep zijn bezeten maken, bijwerken en verwijderen. Leden met deze rol hebben Ervaringen bewerken  machtiging nodig om de Geheimen pagina te bekijken. Optioneel beschikbaar als een [per-spel machtiging](/docs/nl-nl/projects/configure-games) . |

Analytics

| Analytics voor ervaringen bekijken | | Leden met deze rol kunnen de [analyses](/docs/nl-nl/production/analytics)  van alle spellen die door de groep zijn bezeten bekijken, zelfs als ze geen bewerkingsrechten hebben. Optioneel beschikbaar als een [per-spel machtiging](/docs/nl-nl/projects/configure-games) . |
| Waarschuwingen beheren | | Leden met deze rol kunnen analyses waarschuwingen maken en beheren. Koppel deze machtiging met Analytics voor ervaringen bekijken  om waarschuwingsannotaties direct op metrische grafieken te zien. |

Inkomsten genereren

| Groepsomzet bekijken | | Leden met deze rol kunnen het Robux-saldo van de groep, alle geconfigureerde terugkerende splitsingen en functies voor het loggen van inkomsten bekijken. |
| Groepsomzet beheren en uitgeven | | Leden met deze rol kunnen alle groepsinkomsten bekijken, zoals hierboven, en ook direct beheren. Dit omvat het opzetten van [terugkerende uitbetalingen](#terugkerende-uitbetalingen)  en het verzenden van [eenmalige uitbetalingen](#eenmalige-uitbetalingen)  naar samenwerkers. |
| Advertentiecampagnes voor de groep maken | | Leden met deze rol kunnen de groep adverteren. |

Avataritems

| Avataritems maken | | Leden met deze rol kunnen avataritems zoals kleding maken. |
| Avataritems configureren | | Leden met deze rol kunnen verkoopdetails, aanvullingen en sponsoring voor bestaande groepsavataritems configureren. |

API

| API Keys beheren | | Leden met deze rol kunnen [Open Cloud API-sleutels](/docs/nl-nl/cloud/auth/api-keys)  voor de groep beheren. |

Ontwikkelingsitems

| Ontwikkelingsitems bekijken | | Leden met deze rol kunnen ontwikkelingsitems die door de groep zijn bezeten bekijken, bijvoorbeeld Audio . |
| Ontwikkelingsitems beheren | | Leden met deze rol kunnen asset-ontwikkelingsitems zoals Decals  uploaden en configureren. |
| Permissions voor ontwikkelingsitems beheren | | Leden met deze rol kunnen de machtigingen van ontwikkelingsitems configureren, bijvoorbeeld audiodelen. |

Data Stores

| Gegevensopslag voor ervaringen bekijken | | Leden met deze rol kunnen gegevensopslag voor alle groepsspellen bekijken via de [Data Stores Manager](/docs/nl-nl/cloud-services/data-stores/data-stores-manager) , maar ze kunnen geen gegevens verwijderen. Optioneel beschikbaar als een [per-spel machtiging](/docs/nl-nl/projects/configure-games) . |
| Gegevensopslag voor ervaringen bewerken | | Leden met deze rol kunnen specifieke sleutels binnen gegevensopslag voor alle groepsspellen verwijderen via de [Data Stores Manager](/docs/nl-nl/cloud-services/data-stores/data-stores-manager) . Optioneel beschikbaar als een [per-spel machtiging](/docs/nl-nl/projects/configure-games) . |
| Gegevensopslag voor ervaringen verwijderen | | Leden met deze rol kunnen hele gegevensopslag voor alle groepsspellen verwijderen via de [Data Stores Manager](/docs/nl-nl/cloud-services/data-stores/data-stores-manager) . Optioneel beschikbaar als een [per-spel machtiging](/docs/nl-nl/projects/configure-games) . |

Meldingen

| Webhooks voor ervaringen beheren | | Leden met deze rol kunnen webhooks voor alle groepservaringen opsommen, maken, bijwerken en verwijderen. |

Communicatie

| Ondersteuningstickets voor ervaringen beheren | | Leden met deze rol kunnen ondersteuningsverzoeken voor alle groepservaringen beheren. |

Legacy

| Beheer toegang tot de middelen van deze groep | | Leden met deze rol kunnen toegang tot de middelen van de groep maken en bewerken. |

### [Gemeenschap](#gemeenschap)[](#gemeenschap)

Berichten

| Community-aankondigingen bekijken | | Leden met deze rol kunnen gemeenschapsaankondigingen bekijken. |
| Community-aankondigingen maken | | Leden met deze rol kunnen gemeenschapsaankondigingen maken. |

Forums

| Categorieën beheren | | Leden met deze rol kunnen forumcategorieën beheren. |
| Posts maken | | Leden met deze rol kunnen forumberichten maken. |
| Posts verwijderen | | Leden met deze rol kunnen forumberichten verwijderen. |
| Posts vergrendelen | | Leden met deze rol kunnen forumberichten vergrendelen. |
| Posts vastpinnen | | Leden met deze rol kunnen forumberichten vastpinnen. |
| Reacties maken | | Leden met deze rol kunnen opmerkingen op forumberichten maken. |
| Reacties verwijderen | | Leden met deze rol kunnen opmerkingen van forumberichten verwijderen. |

Contentmoderatie

| Contentmoderatie bekijken | | Leden met deze rol kunnen inhoudsmoderatie bekijken. |
| Contentmoderatie beheren | | Leden met deze rol kunnen inhoudsmoderatie beheren. |

Diversen

| Langzame modus omzeilen | | Leden met deze rol kunnen de langzame modus omzeilen. |
| Community-analyse bekijken | | Leden met deze rol kunnen gemeenschapsanalyses bekijken. |

4.

BELANGRIJK

 Klik op de Opslaan  knop om de machtigingsinstellingen toe te passen.

5.

OPTIONEEL

 Klik op het Instellingen  tabblad en kies een kleur en zichtbaarheid instelling voor de rol, klik vervolgens op de Opslaan  knop.

De Instellingen  sectie van een rol is ook waar groeps eigenaren en leden met voldoende machtigingen een rol volledig kunnen verwijderen via de Verwijder Rol  knop.

Rollen worden in hiërarchische volgorde weergegeven: een rol hoger op de lijst heeft meer autoriteit dan een rol eronder. Deze volgorde is belangrijk omdat sommige machtigingen leden alleen toestaan om rollen onder hun hoogste rol te beheren.

Elke rol is ofwel openbaar  of privé . Openbare rollen kunnen worden weergegeven op een Gemeenschaps pagina en in ervaringen. Privérollen worden alleen weergegeven op rol- en machtigingsbeheer oppervlakken voor geautoriseerde leden, of voor leden die de privérol hebben. Zichtbaarheid verandert waar een rol verschijnt; het verandert niet de machtigingen die de rol verleent.

Om Rollen beheren , Rollen toewijzen aan of verwijderen van leden , Toegang tot de bronnen van deze groep beheren , Groepsomzet beheren en uitgeven , of Gegevensopslag voor ervaringen verwijderen  toe te kennen, moet je tweefactorauthenticatie ingeschakeld hebben.

## [Beheer leden](#beheer-leden)[](#beheer-leden)

Ledenconfiguratie is alleen toegankelijk als je de groeps eigenaar bent of toestemming hebt om andere leden en hun rollen te beheren.

Om leden vanuit het Creator Dashboard te beheren:

1.

Breid de accountwisselaar in de linkerbovenhoek uit en selecteer de groep.

2.

Breid de accountwisselaar opnieuw uit en selecteer Leden .

3.

Gebruik het Lid  tabblad om bestaande leden te zoeken of ze te filteren op rol. Gebruik het Uitgenodigd  tabblad om uitstaande uitnodigingen te bekijken.

Om een lid toe te voegen, klik op de Uitnodigen  knop en zoek naar hun gebruikersnaam. Roblox meldt uitgenodigde makers volgens hun meldingsvoorkeuren. Je kunt ook de groepslink kopiëren en deze rechtstreeks delen.

### [Beheer rollen](#beheer-rollen)[](#beheer-rollen)

Je kunt roltoewijzingen beheren vanuit de Leden  pagina of een specifieke rol:

-

Op de Leden  pagina, klik op de plus (+)  knop naast een lid om het rolmenu te openen. Om een rol toe te wijzen, klik op de plus (+)  knop ernaast onder Voeg rollen toe . Om een rol in te trekken, klik op de minus (-)  knop ernaast onder Huidige rollen , of klik op de ×  knop op een toegewezen rol naast de naam van het lid.

-

Op de Rollen  pagina, selecteer een rol en open het Leden  tabblad. Klik op de Leden toevoegen  knop om groepsleden te zoeken en ze aan de rol toe te wijzen. Om een lid in te trekken, klik op de minus (-)  knop aan het einde van hun rij.

### [Lid verwijderen](#lid-verwijderen)[](#lid-verwijderen)

Om een lid uit de groep te verwijderen, klik op de ⋮  knop aan het einde van hun rij, selecteer Verwijder gebruiker , en bevestig de actie.

## [Beheer uitbetalingen](#beheer-uitbetalingen)[](#beheer-uitbetalingen)

Als je de groeps eigenaar bent of je hebt de juiste [machtiging](#rollen-en-machtigingen)  binnen Groepsinkomsten , vind je een Uitbetalingen  pagina onder Financiën  in de linker navigatie. Hier kun je eenmalige uitbetalingen verzenden, evenals percentage splitsingen met andere leden definiëren.

Sommige groepen hebben deze pagina mogelijk aanvankelijk niet ontgrendeld om verschillende redenen, zoals de leeftijd van de groep of onvoldoende middelen om uit te betalen.

Uitbetalingen kunnen niet worden gedeeld tussen groepsleden voor spellen die kosten voor [betaalde toegang in lokale valuta](/docs/nl-nl/production/monetization/paid-access-local-currency) .

### [Eenmalige uitbetalingen](#eenmalige-uitbetalingen)[](#eenmalige-uitbetalingen)

Eenmalige uitbetalingen kunnen in een batch aan leden worden gedaan, waarbij een vast bedrag voor elk wordt geselecteerd. Veiligheidsfuncties omvatten 2FA-uitdagingen, bevestigingsdialoogvensters en controles rond de geschiktheid van leden die worden betaald.

 ![Eenmalige uitbetalingsknop aangegeven in de uitbetalingssectie op het Creator Dashboard.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-One-Time.png)

Zodra je op de Stuur Robux  knop klikt, kun je uitbetalingsontvangers kiezen uit de popup of een .csv  spreadsheetbestand uploaden met de kolommen userId  en payoutInRobux , bijvoorbeeld:

| userId | | payoutInRobux |
| 012345 | | 5000 |
| 098765 | | 7000 |

### [Terugkerende uitbetalingen](#terugkerende-uitbetalingen)[](#terugkerende-uitbetalingen)

Terugkerende uitbetalingen kunnen ook over de hele groep en  per spel worden gedaan, waarbij een percentage uitbetaling aan elk lid wordt toegewezen voordat de rest in het totale saldo van de groep komt.

 ![Split uitbetalingsknoppen aangegeven in de uitbetalingssectie op het Creator Dashboard.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Split-Options.png)

Overweeg het volgende scenario waarin een groepsspel Laser Maze  40%–30%–10% wordt verdeeld onder drie leden, met een rest van 20%.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-A.png)

Aangenomen dat het spel 1000 Robux verdient, ontvangen de drie leden respectievelijk 400, 300 en 100 Robux (40%–30%–10%).

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-B.png)

.De resterende 200 Robux (20% van de spelverdeling) gaat door naar de groepsverdeling  percentages, gedefinieerd op 20%–20%–10% onder dezelfde drie leden; ze ontvangen respectievelijk een extra 40, 40 en 20 Robux.

![](https://prod.docsiteassets.roblox.com/assets/misc/Box-Label-C.png)

.De resterende 100 Robux (50% van de groepsverdeling) wordt in het totale saldo van de groep geplaatst.

 ![Voorbeeld stroomdiagram van hoe spelverdelingen eerst aan groepsleden worden verdeeld, met de rest die wordt meegenomen in groepsverdelingen voor de uiteindelijke verdeling onder de groep.](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Group-Payouts-Splits-Example.png)

Let op dat inkomsten van [privéserver](/docs/nl-nl/production/monetization/private-servers)  abonnementen niet veranderen als je later de splitsingspercentages aanpast, wat betekent dat als een speler een privéserverabonnement koopt, de splitsingspercentages op het moment van aankoop van toepassing zijn op dat specifieke abonnement voor altijd (totdat het wordt geannuleerd). Dit beleid kan in de toekomst worden gewijzigd.

## [Groepsauditlogs](#groepsauditlogs)[](#groepsauditlogs)

Groepsleden met de Auditlogboeken bekijken  machtiging kunnen groepswijzigingen bekijken met behulp van deze groepsbeheer oppervlakken:

-

Op het Creator Dashboard, selecteer Activiteit Geschiedenis  onder Samenwerking .

-

Op Gemeenschappen, open de configuratiepagina van de gemeenschap en selecteer Audit Log .

Groeps eigenaren kunnen deze logs gebruiken om activiteiten te monitoren die mogelijk in strijd zijn met de [groepsrichtlijnen](/docs/nl-nl/projects/group-guidelines) .

## [Bescherming van intellectueel eigendom](#bescherming-van-intellectueel-eigendom)[](#bescherming-van-intellectueel-eigendom)

Groepsleden met toestemming om alle groepsspellen te bewerken kunnen de [Plaats Kopiëren](/docs/nl-nl/projects/configure-games#allow-copying)  instelling voor een creatie inschakelen, waardoor de hele Roblox-gemeenschap het kan kopiëren en middelen erin kan gebruiken. Om intellectueel eigendom in een groep te beschermen, moet de eigenaar of leden met voldoende machtigingen:

-

Bevestigen dat elk lid [de juiste rol heeft toegewezen gekregen](#beheer-rollen) .

-

Controleren of elke groepsrol de juiste [machtigingen](#rollen-en-machtigingen)  heeft.

-

Bevestigen dat de [Plaats Kopiëren](/docs/nl-nl/projects/configure-games#allow-copying)  instelling is uitgeschakeld voordat privé-middelen worden toegevoegd.

## [Aanvullende lokalisaties voor deze pagina](#aanvullende-lokalisaties-voor-deze-pagina)[](#aanvullende-lokalisaties-voor-deze-pagina)

Voor aanvullende, gelokaliseerde versies van deze pagina die niet beschikbaar zijn in de taalkeuzelijst van de site, zie de volgende links:

-

[Bulgaars (български)](https://create.roblox.com/docs/bg-bg/projects/groups)

-

[Kroatisch (hrvatski)](https://create.roblox.com/docs/hr-hr/projects/groups)

-

[Tsjechisch (čeština)](https://create.roblox.com/docs/cs-cz/projects/groups)

-

[Deens (dansk)](https://create.roblox.com/docs/da-dk/projects/groups)

-

[Nederlands (Nederlands)](https://create.roblox.com/docs/nl-nl/projects/groups)

-

[Estisch (eesti)](https://create.roblox.com/docs/et-ee/projects/groups)

-

[Fins (suomi)](https://create.roblox.com/docs/fi-fi/projects/groups)

-

[Grieks (Ελληνικά)](https://create.roblox.com/docs/el-gr/projects/groups)

-

[Hongaars (magyar)](https://create.roblox.com/docs/hu-hu/projects/groups)

-

[Iers (Gaeilge)](https://create.roblox.com/docs/ga-ie/projects/groups)

-

[Lets (latviešu)](https://create.roblox.com/docs/lv-lv/projects/groups)

-

[Litouws (lietuvių)](https://create.roblox.com/docs/lt-lt/projects/groups)

-

[Maltees (Malti)](https://create.roblox.com/docs/mt-mt/projects/groups)

-

[Portugees - Portugal (português)](https://create.roblox.com/docs/pt-pt/projects/groups)

-

[Roemeens (română)](https://create.roblox.com/docs/ro-ro/projects/groups)

-

[Slowaaks (slovenčina)](https://create.roblox.com/docs/sk-sk/projects/groups)

-

[Sloveens (slovenščina)](https://create.roblox.com/docs/sl-si/projects/groups)

-

[Zweeds (svenska)](https://create.roblox.com/docs/sv-se/projects/groups)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
