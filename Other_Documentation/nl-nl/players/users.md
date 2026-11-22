<!-- Source: https://create.roblox.com/docs/nl-nl/players/users -->

Gebruikers en gescoope gebruikers-ID's | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Spelers](/docs/nl-nl/players)

# Gebruikers en gescoope gebruikers-ID's

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Gescoope gebruikers-ID's zijn nog niet breed uitgerold. [Player.User](/docs/nl-nl/reference/engine/classes/Player#User)  en het [User](/docs/nl-nl/reference/engine/datatypes/User)  datatype zijn nu beschikbaar, en de effectieve gebruikers-ID van een gebruiker blijft momenteel hun globale gebruikers-ID.

Roblox blootlegt één effectieve gebruikers-ID  voor elke gebruiker in elk spel, groep of app. Afhankelijk van de geschiedenis van de gebruiker met dat domein, is hun effectieve gebruikers-ID ofwel hun globale gebruikers-ID of een gescoope gebruikers-ID . Deze pagina legt uit hoe effectieve gebruikers-ID's werken en hoe je het [User](/docs/nl-nl/reference/engine/datatypes/User)  type in je spelcode kunt gebruiken.

De volgende concepten zijn centraal voor gebruikersidentificatie:

| Concept | | Beschrijving |
| --- | --- |
| Gebruiker | | Een persistent account op Roblox. |
| Speler | | De representatie van een gebruiker binnen het datamodel van een draaiend spel (zie [Spelers](/docs/nl-nl/players) ). |
| [User](/docs/nl-nl/reference/engine/datatypes/User)  datatype | | Een datatype dat de effectieve gebruikers-ID van een gebruiker en de domeincontext bevat. Dit is de standaardidentificator voor het verwijzen naar gebruikers in spelcode. |
| Globale gebruikers-ID | | De gebruikers-ID op platformniveau die Roblox aan elk account toekent. Het is wereldwijd uniek binnen Roblox. |
| Gescoope gebruikers-ID | | Een gebruikers-ID die binnen een specifiek domein is toegewezen. De gescoope gebruikers-ID's van een gebruiker zijn verschillend in elk spel, groep of app. |
| Effectieve gebruikers-ID | | De enkele gebruikers-ID die Roblox blootlegt voor een gebruiker binnen een [domein](#effectieve-gebruikers-ids-en-domeinen) . |
| Pre-rollout gebruiker | | Een gebruiker die voor het eerst met een domein in aanraking kwam voordat de rollout van gescoope gebruikers-ID's plaatsvond. In dat domein blijft hun effectieve gebruikers-ID hun globale gebruikers-ID. |
| Post-rollout gebruiker | | Een gebruiker die voor het eerst met een domein in aanraking kwam na de rollout van gescoope gebruikers-ID's. In dat domein is hun effectieve gebruikers-ID een gescoope gebruikers-ID. |

## [Effectieve gebruikers-ID's en domeinen](#effectieve-gebruikers-ids-en-domeinen)[](#effectieve-gebruikers-ids-en-domeinen)

Elke gebruiker heeft één effectieve gebruikers-ID binnen een specifiek spel , groep  of app . Roblox blootlegt geen aparte globale en gescoope gebruikers-ID's voor dezelfde gebruiker in dat domein:

-

Een pre-rollout gebruiker  heeft hun globale gebruikers-ID als hun effectieve gebruikers-ID.

-

Een post-rollout gebruiker  heeft een gescoope gebruikers-ID als hun effectieve gebruikers-ID. Die ID is alleen betekenisvol binnen dat domein.

In spelcode geven [Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId)  en [Player.User.Id](/docs/nl-nl/reference/engine/datatypes/User#Id)  beide deze effectieve gebruikers-ID terug en hebben altijd dezelfde numerieke waarde ([Player.User.Id](/docs/nl-nl/reference/engine/classes/Player#User)  is gelijk aan [Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId) ), zodat je code geen vertakkingslogica hoeft te gebruiken om tussen hen te kiezen.

Roblox scope gebruikersidentiteit over drie soorten domeinen:

| Domein | | Gescoope naar | | Voorbeeld |
| Ervaring  ([Enum.DomainType.EXPERIENCE](/docs/nl-nl/reference/engine/enums/DomainType#EXPERIENCE) ) | | Een specifieke ervaring | | De ID van een speler in jouw ervaring |
| Groep | | Een specifieke Roblox-groep (gemeenschap) | | De ID van een lid in jouw groep |
| OAuth-app  ([Enum.DomainType.OAUTH](/docs/nl-nl/reference/engine/enums/DomainType#OAUTH) ) | | Een specifieke OAuth-toepassing | | De ID van een gebruiker in jouw externe tool |

### [Hoe effectieve gebruikers-ID's werken](#hoe-effectieve-gebruikers-ids-werken)[](#hoe-effectieve-gebruikers-ids-werken)

Wanneer een speler jouw spel binnenkomt, hebben ze één effectieve gebruikers-ID voor dat spel. De effectieve gebruikers-ID van een post-rollout gebruiker is een gescoope gebruikers-ID die uniek is voor dat spel. Ze ontvangen een andere gescoope gebruikers-ID in elk ander spel, groep of app waar ze ook een post-rollout gebruiker zijn. Dit betekent:

-

Effectieve gebruikers-ID's zijn gehele getallen, of ze nu globaal of gescoope zijn.

-

Effectieve gebruikers-ID's zijn stabiel over sessies binnen hetzelfde domein.

-

Een gescoope gebruikers-ID botst niet met een bestaande globale gebruikers-ID.

-

Dezelfde numerieke waarde kan in verschillende domeinen voor verschillende gebruikers verschijnen. De unieke sleutel is de combinatie van het domein (domeintype en domein-ID) en de effectieve gebruikers-ID.

### [Voorbeeldscenario](#voorbeeldscenario)[](#voorbeeldscenario)

Het volgende voorbeeld demonstreert hoe verschillende spellen dezelfde gebruiker refereren:

| Scenario | | Gebruikerscontext | | Effectieve gebruikers-ID gezien door het spel |
| Gebruiker verbindt met Spel A | | Pre-rollout gebruiker | | 123  (globale gebruikers-ID, onveranderd) |
| Gebruiker verbindt met Spel B | | Post-rollout gebruiker | | 500789  (gescoope gebruikers-ID voor Spel B) |
| Gebruiker verbindt met Spel C | | Post-rollout gebruiker | | 302441  (gescoope gebruikers-ID voor Spel C) |

### [Pre-rollout gebruikers](#pre-rollout-gebruikers)[](#pre-rollout-gebruikers)

Als een speler een pre-rollout gebruiker is in jouw spel, blijft hun effectieve gebruikers-ID hun globale gebruikers-ID in dat spel. Zowel [Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId)  als [Player.User.Id](/docs/nl-nl/reference/engine/datatypes/User#Id)  geven die globale gebruikers-ID terug. Roblox blootlegt geen tweede gebruikers-ID voor de speler in dat spel. Dit zorgt ervoor dat bestaande datastoresleutels, ranglijsten en inventarissen blijven werken zonder enige wijzigingen.

### [Groepdomein](#groepdomein)[](#groepdomein)

Elke Roblox-groep is zijn eigen domein. Een gebruiker heeft één effectieve gebruikers-ID binnen een groep, gescheiden van hun effectieve gebruikers-ID in elk spel of OAuth-toepassing:

-

In-game groepscontroles veranderen niet  — Engine-methoden op [Player](/docs/nl-nl/reference/engine/classes/Player) , zoals [Player:IsInGroupAsync()](/docs/nl-nl/reference/engine/classes/Player#IsInGroupAsync) , [Player:GetRankInGroupAsync()](/docs/nl-nl/reference/engine/classes/Player#GetRankInGroupAsync) , en [Player:GetRoleInGroupAsync()](/docs/nl-nl/reference/engine/classes/Player#GetRoleInGroupAsync) , evenals [GroupService:PromptJoinAsync()](/docs/nl-nl/reference/engine/classes/GroupService#PromptJoinAsync) , resolven identiteit intern zonder een gebruikers-ID bloot te leggen.

-

Open Cloud groeps-API's gebruiken het domein van de groep  — Dit geldt voor eindpunten die groepslidmaatschappen en lidmaatschapsverzoeken opsommen of beheren.

## [Werken met het Gebruikerstype](#werken-met-het-gebruikerstype)[](#werken-met-het-gebruikerstype)

[User](/docs/nl-nl/reference/engine/datatypes/User)  is de standaardmanier om gebruikers in spelcode te identificeren. Een [User](/docs/nl-nl/reference/engine/datatypes/User)  waarde bevat de effectieve gebruikers-ID samen met het domeintype en de domein-ID, zodat de identiteitscontext altijd met de identificator meereist. Voor volledige API-details, zie de [User](/docs/nl-nl/reference/engine/datatypes/User)  referentie.

### [Verkrijg een Gebruiker van een Speler](#verkrijg-een-gebruiker-van-een-speler)[](#verkrijg-een-gebruiker-van-een-speler)

De primaire manier om een [User](/docs/nl-nl/reference/engine/datatypes/User)  te verkrijgen is van een verbonden [Player](/docs/nl-nl/reference/engine/classes/Player)  via [Player.User](/docs/nl-nl/reference/engine/classes/Player#User) :

```

local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)

    local user = player.User

    print("Effectieve gebruikers-ID:", user.Id) -- Komt altijd overeen met player.UserId

    print("Domeintype:", user.DomainType)

    print("Domein-ID:", user.DomainId)

end)

```

### [Constructie van een Gebruiker vanuit een ID](#constructie-van-een-gebruiker-vanuit-een-id)[](#constructie-van-een-gebruiker-vanuit-een-id)

Om een [User](/docs/nl-nl/reference/engine/datatypes/User)  te maken vanuit een bekende effectieve gebruikers-ID binnen het huidige spel, gebruik [User.fromId()](/docs/nl-nl/reference/engine/datatypes/User#fromId) :

```

local user = User.fromId(knownUserId)

```

## [Gebruik van Gebruiker met engine API's](#gebruik-van-gebruiker-met-engine-apis)[](#gebruik-van-gebruiker-met-engine-apis)

Engine API's die een gebruikers-ID-parameter accepteren, accepteren ook [User](/docs/nl-nl/reference/engine/datatypes/User)  waarden direct. Het gebruik van [User](/docs/nl-nl/reference/engine/datatypes/User)  wordt aanbevolen:

```

-- Beide vormen werken:

BadgeService:AwardBadge(player.User, badgeId)    -- Aanbevolen

BadgeService:AwardBadge(player.UserId, badgeId)

```

```

-- Beide vormen werken:

local target = Players:GetPlayerByUserId(player.User) -- Aanbevolen

local target = Players:GetPlayerByUserId(someUserId)

```

Wanneer een numerieke gebruikers-ID wordt doorgegeven aan een engine API die gebruikers-ID's accepteert, wordt deze automatisch intern verpakt in een [User](/docs/nl-nl/reference/engine/datatypes/User) .

### [Engine API's die gebruikers-ID's retourneren](#engine-apis-die-gebruikers-ids-retourneren)[](#engine-apis-die-gebruikers-ids-retourneren)

Engine API's die numerieke gebruikers-ID's retourneren, geven de effectieve gebruikers-ID van de gebruiker terug:

-

Pre-rollout gebruikers  — de API retourneert de globale gebruikers-ID van de gebruiker.

-

Post-rollout gebruikers  — de API retourneert de gescoope gebruikers-ID van de gebruiker.

[Player.UserId](/docs/nl-nl/reference/engine/classes/Player#UserId) , [Player.User.Id](/docs/nl-nl/reference/engine/datatypes/User#Id) , en andere engine API's geven allemaal dezezelfde effectieve gebruikers-ID voor een gebruiker in jouw spel terug, zodat bestaande code die numerieke gebruikers-ID-velden leest blijft werken zonder vertakkingslogica.

Open Cloud verzoeken en antwoorden gebruiken dezelfde effectieve gebruikers-ID voor het doeldomein. Ze blootstellen geen tweede gebruikers-ID voor dezelfde gebruiker in dat domein.

## [Opslaan van gebruikersidentiteit](#opslaan-van-gebruikersidentiteit)[](#opslaan-van-gebruikersidentiteit)

Gebruik een numerieke effectieve gebruikers-ID alleen om een gebruiker binnen een enkel domein te identificeren. Een datastoresleutel in één spel kan user.Id  direct gebruiken:

```

local key = ("player_%d"):format(player.User.Id)

PlayerDataStore:SetAsync(key, data)

```

Wanneer een ander domein de opgeslagen identiteit leest, zoals een OAuth-app die gebruikers modereert, sla de string op van [ToString()](/docs/nl-nl/reference/engine/datatypes/User#ToString) . De string codeert de domeincontext samen met de effectieve gebruikers-ID. Het gebruik van alleen het geheel kan een actie toepassen op de verkeerde gebruiker wanneer hetzelfde nummer een andere gebruiker in een ander domein identificeert.

```

local encoded = player.User:ToString()

SomeDataStore:SetAsync("support_ticket_user", encoded)

-- Later, herstel vanuit de string

local user = User.fromString(encoded)

```

Voor meer details over serialisatiegaranties, zie de [User](/docs/nl-nl/reference/engine/datatypes/User)  referentie.

## [Beste praktijken](#beste-praktijken)[](#beste-praktijken)

-

Gebruik [Player.User](/docs/nl-nl/reference/engine/classes/Player#User)  als de standaardidentificator in nieuwe code.

-

Gebruik de numerieke effectieve gebruikers-ID alleen binnen een enkel domein, zoals datastoresleutels voor één spel.

-

Gebruik [ToString()](/docs/nl-nl/reference/engine/datatypes/User#ToString)  en [fromString()](/docs/nl-nl/reference/engine/datatypes/User#fromString)  wanneer een ander domein de opgeslagen identiteit leest.

### [Wanneer Gebruiker of Speler te gebruiken](#wanneer-gebruiker-of-speler-te-gebruiken)[](#wanneer-gebruiker-of-speler-te-gebruiken)

-

Gebruik [Player](/docs/nl-nl/reference/engine/classes/Player)  voor acties binnen de server: karakterbeweging, GUI, teleportatie, chat, inventaris.

-

Gebruik [User](/docs/nl-nl/reference/engine/datatypes/User)  voor identiteit die langer meegaat dan een sessie: datastores, Open Cloud-tools, cross-game verwijzingen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
