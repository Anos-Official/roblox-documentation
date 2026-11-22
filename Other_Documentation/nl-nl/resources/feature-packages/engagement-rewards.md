<!-- Source: https://create.roblox.com/docs/nl-nl/resources/feature-packages/engagement-rewards -->

Betrokkenheidsbeloningen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)

# Betrokkenheidsbeloningen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het Betrokkenheidsbeloningen  functiepakket is een aanpasbaar framework voor het aanbieden van in-game beloningen voor bepaalde spelersactiviteiten, waaronder dagelijkse inlogreeksen en speeltijd. Naast client- en serverlogica bevat het pakket een standaard UI voor het bekijken van beloningsvoortgang, beloningsstatus en het claimen van beloningen.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/feature-packages/engagement/rewards.jpg)

## [Verkrijg het pakket](#verkrijg-het-pakket)[](#verkrijg-het-pakket)

1.

Voeg de Core  en Betrokkenheidsbeloningen  pakketten toe aan je inventaris binnen Studio door op de Voeg toe aan Inventaris  links hier te klikken:

[

#### Core

Het Core functiepakket biedt gedeelde datastore logica voor alle functiepakketten.

](https://create.roblox.com/store/asset/94918533221001)

Toevoegen aan inventaris

[

#### Betrokkenheidsbeloningen

Het Betrokkenheidsbeloningen functiepakket helpt je beloningen aan te bieden voor dagelijkse inlog, inlogreeksen en speeltijd.

](https://create.roblox.com/store/asset/80053655757903)

Toevoegen aan inventaris

2.

Open het [Gereedschapskist](/docs/nl-nl/projects/assets/toolbox)  vanuit het Venster  menu of de Start  tabblad werkbalk in Studio.

3.

Klik in het Gereedschapskist  venster op het Inventaris  tabblad. De Mijn Modellen  sortering wordt weergegeven.

 ![Studio's Gereedschapskist venster met het Inventaris tabblad gemarkeerd.](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Inventory-Tab.png)

4.

Klik op de tegel Functiepakket Core , en vervolgens op de tegel Betrokkenheidsbeloningen Functiepakket . Beide pakketmappen worden weergegeven in het Explorer  venster.

5.

Sleep de mappen naar [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage) .

## [Initialiseer het pakket](#initialiseer-het-pakket)[](#initialiseer-het-pakket)

Door de pakketten naar [ReplicatedStorage](/docs/nl-nl/reference/engine/classes/ReplicatedStorage)  te verplaatsen en je spel te testen, wordt het EngagementRewardsExample  script in ReplicatedStorage.EngagementRewards.Server.Examples  uitgevoerd.

Dit script laat zien hoe je het pakket initialiseert voor gebruik in je spel, wat inhoudt dat je verschillende module scripts moet vereisen en een rewardClaimedHandlerFunction()  functie moet definiëren die uiteindelijk de beloning(en) aan de speler geeft.

Deze functie moet een boolean retourneren. In het voorbeeldscript zie je dat het geen beloningen aan de speler geeft; het print alleen de speler, beloning en hoeveelheid die wordt geclaimd.

EngagementRewardsExample

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local EngagementRewardsConfig = require(ReplicatedStorage.EngagementRewards.Configs.EngagementRewardsConfig)

local EngagementRewards = require(ReplicatedStorage.EngagementRewards.Server.EngagementRewards)

local EngagementRewardsUtils = require(ReplicatedStorage.EngagementRewards.Utils.EngagementRewardsUtils)

local Types = require(ReplicatedStorage.EngagementRewards.Configs.Types)

-- Vervang deze handlerfunctie door je eigen beloning geclaimde handlerfunctie

-- Deze functie moet het beloning geclaimde evenement voor de doorgegeven rewardId afhandelen

local function rewardClaimedHandlerFunction(player: Player, rewardId: RewardId, quantity: number): (boolean, string?)

   print(`Beloning {rewardId} geclaimd door {player} met hoeveelheid {quantity}`)

   return true

end

-- meer

```

Je kunt dit script direct aanpassen of het verplaatsen naar [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService)  als dat je voorkeur heeft voor servercode. Zoals het nu is, is het script alleen nuttig voor testdoeleinden.

Het geven van de beloning aan de speler varieert per spel. In sommige spellen kun je een spelboost geven of gewoon het aantal goud van de speler verhogen. In andere spellen heb je misschien een aangepast inventarissysteem, terwijl anderen een item in de rugzakken van spelers plaatsen. In alle gevallen moet je echter rewardClaimedHandlerFunction()  vervangen door je eigen functie.

## [Voeg beloningen en criteria toe](#voeg-beloningen-en-criteria-toe)[](#voeg-beloningen-en-criteria-toe)

De meeste aanpassingen van beloningen vinden plaats binnen ReplicatedStorage.EngagementRewards.Configs.EngagementRewardsConfig . Dit module script definieert de beloning en de vereisten om deze te ontgrendelen.

Je kunt de volledige typeverklaringen (of nieuwe toevoegen) in ReplicatedStorage.EngagementRewards.Configs.Types  zien, maar je hoeft waarschijnlijk alleen met EngagementRewardsConfig  te werken. Het functiepakket bevat twee beloningstypen: Tijd  en Dagelijks .

```

local engagementRewardsConfig: Types.EngagementRewardsConfig = {

   [Types.RewardType.Time] = {

      tabDisplayName = "Tijd",

      tabOrder = 1,

      description = "Blijf spelen om beloningen te ontgrendelen!",

      rewards = {

         MinutesPlayed1 = {

            icon = 116913478160966,

            displayName = "IJs Lance",

            requiredSecondsInGame = 1 * 5,

         },

         -- meer

   [Types.RewardType.Daily] = {

      tabDisplayName = "Dagelijks",

      tabOrder = 2,

      description = "Speel dagelijks om beloningen te ontgrendelen!",

      rewards = {

         DailyStreak1 = {

            icon = 116913478160966,

            displayName = "IJs Lance",

            requiredDaysVisitedStreak = 1,

            effect = Types.RewardEffect.Valuable,

         },

         -- meer

```

Beide beloningstypen vereisen een icoon, wat een Roblox asset ID voor een afbeelding is (geen  decal). Je wilt waarschijnlijk ook een weergavenaam voor gebruik in de UI. Geef quantity  op voor waarden anders dan 1. Je kunt ook optioneel een beloning als waardevol aanwijzen (effect = Types.RewardEffect.Valuable ) om het een andere achtergrondframe in de UI te geven.

| Variabele | | Type | | Beschrijving | | Standaard | | Vereist |
| --- | --- |
| icon | | Nummer | | Een Roblox asset ID voor het UI-icoon. | | N/B | | Ja |
| displayName | | String | | Een naam voor de beloningen voor gebruik in de UI. | | De RewardId | | Nee |
| quantity | | Nummer | | Het aantal items om te belonen. | | 1 | | Nee |
| effect | | RewardEffect | | Het visuele effect dat in de UI moet worden gebruikt. Zie [Pas de UI aan](#pas-de-ui-aan) . | | Types.RewardEffect.Default | | Nee |

### [Tijd beloningen](#tijd-beloningen)[](#tijd-beloningen)

Tijd  beloningen worden ontgrendeld na een bepaald aantal seconden in het spel. Pas deze nummers aan om aan je behoeften te voldoen. Je kunt kleine nummers gebruiken voor eenvoudige tests, en in het gepubliceerde spel een beloning geven na 10 minuten, een andere na 30 minuten, een andere na een uur, enzovoort.

Tijdregistratie begint bij 0 voor elke sessie, dus spelers verliezen alle voortgang naar Tijd  beloningen wanneer ze het spel verlaten.

Vermenigvuldiging maakt nummers in seconden gemakkelijker voor mensen om mee te werken, dus voor twee uur geef je misschien de voorkeur aan 2 * 60 * 60  in plaats van 7200 .

| Variabele | | Type | | Beschrijving | | Standaard | | Vereist |
| requiredSecondsInGame | | Nummer | | Het aantal seconden (een positief geheel getal) dat de speler in het spel moet doorbrengen om de beloning te verdienen. | | N/B | | Ja |

### [Dagelijkse beloningen](#dagelijkse-beloningen)[](#dagelijkse-beloningen)

Dagelijks  beloningen worden ontgrendeld na een bepaald aantal opeenvolgende dagelijkse inlog. Bijvoorbeeld, de eerste dag dat een speler inlogt, kun je ze drie potion of een kaneelbroodje geven. Op de volgende dagen kun je waardevollere consumables belonen, gevolgd door een duurzaam item, zoals een nieuwe hengel, na zeven achtereenvolgende dagen.

| Variabele | | Type | | Beschrijving | | Standaard | | Vereist |
| requiredDaysVisitedStreak | | Nummer | | Het aantal opeenvolgende dagen dat de speler verbinding moet maken met het spel om de beloning te verdienen. | | N/B | | Ja |

Twee extra configuratieopties voor dagelijkse beloningen zijn beschikbaar in de DailyRewardTabConfig .

```

[Types.RewardType.Daily] = {

    tabDisplayName = "Dagelijks",

    tabOrder = 2,

    description = "Speel dagelijks om beloningen te ontgrendelen!",

    isHiddenOnJoin = true,

    isAlignedToStreakResetTime = true,

    rewards = {

        DailyStreak1 = {

            icon = 116913478160966,

            displayName = "IJs Lance",

            requiredDaysVisitedStreak = 1,

        },

        -- meer

```

| Variabele | | Type | | Beschrijving | | Standaard | | Vereist |
| isHiddenOnJoin | | Boolean | | Wanneer waar, verschijnen beloningen niet automatisch bij het joinen van het spel. Wanneer onwaar, verschijnen beloningen automatisch bij het joinen van het spel als de speler een nieuwe dagelijkse beloning heeft om te claimen. | | Onwaar | | Nee |
| isAlignedToStreakResetTime | | Boolean | | Wanneer waar, kunnen beloningen voor dag 2 24 uur na de initiële claimbare tijd van dag 1 worden geclaimd. Wanneer onwaar, kunnen beloningen voor dag 2 worden geclaimd om middernacht na de claimbare tijd van dag 1. Bijvoorbeeld, als een speler inlogt om 23:00 en hun dag 1 beloning claimt, betekent waar dat ze de dag 2 beloning pas om 23:00 de volgende dag kunnen claimen. Onwaar betekent dat ze de dag 2 beloning om 00:00, een uur later, kunnen claimen. Beloningen voor dag 3 en verder zijn altijd beschikbaar 24 uur na de claimbare tijd van de vorige dag. | | Onwaar | | Nee |

## [Pas de UI aan](#pas-de-ui-aan)[](#pas-de-ui-aan)

In de vorige sectie heb je misschien de tabDisplayName , tabOrder , en description  velden opgemerkt, die basisaanpassingen van de gebruikersinterface mogelijk maken. Je kunt ook enkele UI-strings vinden in ReplicatedStorage.FeaturePackagesCore.Configs.TranslationStrings .

 ![](https://prod.docsiteassets.roblox.com/assets/resources/feature-packages/engagement/rewards-annotated.png)

-

Om een nieuwe beloningsachtergrond op te geven met de effect  variabele, voeg een frame toe aan ReplicatedStorage.EngagementRewards.Objects.RewardItemFrames . Voeg vervolgens de naam van het frame toe aan de Types.RewardEffect  tabel in ReplicatedStorage.EngagementRewards.Configs.Types .

-

Voor meer uitgebreide aanpassingen, pas de objecten in ReplicatedStorage.EngagementRewards.Objects  aan. Bijvoorbeeld, je kunt de [BackgroundColor3](/docs/nl-nl/reference/engine/classes/Frame#BackgroundColor3)  van de RewardsHudButton.Background  frame of de [Color](/docs/nl-nl/reference/engine/classes/UIGradient#Color)  van FooterContentFrame.ClaimableUIGradient  aanpassen.

Wees voorzichtig als je ReplicatedStorage.FeaturePackagesCore.Objects  aanpast; wijzigingen in Core  beïnvloeden alle functiepakketten.

-

Het toegangspunt voor de gebruikersinterface is het ReplicatedStorage.EngagementRewards.Client.UIController  script, dat de benodigde objecten verkrijgt en de UI initialiseert. Als je top-level objecten toevoegt of hernoemt (in tegenstelling tot alleen kinderen toevoegen of eigenschappen aanpassen), moet je waarschijnlijk de code in deze map bijwerken om ze te verwerken.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
