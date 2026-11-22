<!-- Source: https://create.roblox.com/docs/nl-nl/production/monetization/roblox-plus -->

Roblox Plus | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Verdienen](/docs/nl-nl/production/monetization)

# Roblox Plus

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox Plus  biedt je extra manieren om te verdienen met je games door betrokkenheid en aankopen van Plus-abonnees te belonen.

Gebruikers die zich abonneren op Plus krijgen een reeks voordelen om hun koopkracht, toegang en algehele spelervaring op het platform te verbeteren:

-

Korting op aankopen : Abonnees krijgen 10% korting op in aanmerking komende aankopen, waaronder in-game items, avatar items en meer. De korting stijgt naar 20% vanaf de derde maand. Roblox dekt deze korting voor jou.

-

Gratis betaalde privéservers : Abonnees krijgen toegang tot betaalde privéservers zonder kosten. Je wordt nog steeds gecompenseerd wanneer ze tijd doorbrengen in jouw betaalde privéservers.

-

Gratis Robux-overdrachten : Abonnees kunnen Robux zonder kosten naar de verzender of ontvanger overdragen. Overdrachten zijn onderhevig aan leeftijdsbeperkingen en ouderlijke toestemming. Robux die via overdrachten worden ontvangen, komen niet in aanmerking voor het DevEx-programma.

-

[Toegang tot de marketplace](/docs/nl-nl/marketplace/marketplace-policy#vereisten-voor-makers) : Abonnees kunnen beperkte items verhandelen en doorverkopen, en avatar items publiceren en verkopen. Premium-abonnees hebben dezelfde toegang tot de marketplace.

Voor meer informatie over de voordelen van Roblox Plus voor eindgebruikers, zie het [helpcentrum](https://en.help.roblox.com/hc/en-us/articles/47967913158164-Roblox-Plus) .

Als maker kun je verdienen aan Roblox Plus-abonnees door:

-

[In-game Robux aankopen](#verdien-aan-in-game-aankopen) : Abonnees ontvangen 10–20% korting op aankopen, die door Roblox wordt gedekt zodat jouw verdiensten per aankoop niet worden verminderd. Lagere prijzen kunnen meer frequente aankopen aanmoedigen, wat helpt om je totale omzet te verhogen.

-

[Plus-aanmeldingen stimuleren](#verdien-aan-in-game-plus-abonnementen) : Moedig betrokken gebruikers aan om zich rechtstreeks vanuit jouw game op Roblox Plus te abonneren met [PromptRobloxSubscriptionPurchase](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptRobloxSubscriptionPurchase) . Je kunt tot 750 Robux verdienen voor elke nieuwe abonnee die je binnenhaalt, met verdiensten die beginnen zodra het abonnement betaald wordt (gratis proefperiodes zijn niet inbegrepen).

-

[Tijd doorgebracht in betaalde privéservers](#verdien-aan-tijd-in-betaalde-priv%C3%A9servers) : Verdien tot 100 Robux per abonnee wanneer ze elke maand minstens 60 minuten in jouw betaalde privéservers doorbrengen.

-

[In-game Robux-overdrachten](#verdien-aan-robux-overdrachten) : Verdien 10% elke keer dat een Plus-abonnee Robux naar een andere gebruiker binnen jouw game verzendt met [PromptRobuxTransferAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptRobuxTransferAsync) . Dit bedrag komt in aanmerking voor het DevEx-programma.

## [Verdien aan in-game aankopen](#verdien-aan-in-game-aankopen)[](#verdien-aan-in-game-aankopen)

Met Roblox Plus ontvangen gebruikers 10–20% korting op in aanmerking komende Robux-aankopen. Omdat Roblox deze kortingen subsidieert, verdien je hetzelfde bedrag per aankoop als je zou doen van niet-abonnees. Tegelijkertijd kunnen lagere prijzen voor Plus-abonnees meer frequente aankopen aanmoedigen en je totale omzet verhogen.

Abonnees ontvangen 10% korting gedurende hun eerste twee maanden, die stijgt naar 20% vanaf de derde maand. Als een gebruiker hun Plus-abonnement annuleert en later opnieuw abonneert, wordt hun korting gereset naar 10% en stijgt deze opnieuw na twee maanden.

In aanmerking komende Robux-aankopen zijn onder andere:

-

Ontwikkelaarsproducten

-

Gamepassen

-

Ontwikkelaarsabonnementen

-

Betaalde toegangsspellen

-

Avatar items

Kortingen zijn niet van toepassing op:

-

Items met een prijs boven 1.000.000 Robux

-

Publicatiekosten voor de marketplace

-

Advertentietegoeden

-

Groepskosten

De volgende tabel toont hoe Roblox Plus-kortingen worden gesubsidieerd door Roblox.

| Gebruikerstype | | Itemprijs in Robux | | Uitgaven gebruiker | | Roblox-subsidie | | Verdiensten maker | | Effectief omzetdeel |
| --- | --- |
| Niet-abonnee | | 100 | | 100 | | — | | 70 | | 70% |
| Plus-abonnee (10% korting) | | 100 | | 90 | | 10 | | 70 | | 78% |
| Plus-abonnee (20% korting) | | 100 | | 80 | | 20 | | 70 | | 88% |

Als je prijzen hardcodeert, kan je in-game UI onjuiste prijzen weergeven aan Plus-abonnees.  Hoewel abonnees nog steeds de kortingprijs betalen, kan jouw game hen de volle prijs tonen. Deze mismatch kan verwarring veroorzaken.

Om nauwkeurige, realtime prijzen (inclusief Plus-kortingen) weer te geven, moet je [MarketplaceService](/docs/nl-nl/reference/engine/classes/MarketplaceService) -functies gebruiken zoals [GetProductInfoAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetProductInfoAsync)  en [GetDeveloperProductsAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetDeveloperProductsAsync) .

Voor implementatiedetails, zie [Verkoop een pas](/docs/nl-nl/production/monetization/passes#verkoop-een-toegangspas)  en [Verkoop een ontwikkelaarsproduct](/docs/nl-nl/production/monetization/developer-products#verkoop-een-ontwikkelaarsproduct) .

## [Verdien aan in-game Plus-abonnementen](#verdien-aan-in-game-plus-abonnementen)[](#verdien-aan-in-game-plus-abonnementen)

Je kunt gebruikers aanmoedigen om zich rechtstreeks vanuit jouw game op Roblox Plus te abonneren met [PromptRobloxSubscriptionPurchase](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptRobloxSubscriptionPurchase) . Voor elke gebruiker die een abonnee wordt via jouw game, verdien je 250 Robux per maand voor hun eerste drie aaneengeschakelde maanden , met tot 750 Robux voor elke nieuw verworven abonnee .

Alle verdiensten zijn onderhevig aan een wachttijd van 60 dagen.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/roblox-plus/Plus-Signup-Bonus.png)

Roblox Plus-abonnementsaanvragen kunnen op andere plaatsen verschijnen, zoals pagina's voor betaalde privéservers of aankoopmodals, maar je verdient alleen een Robux-uitbetaling wanneer een gebruiker zich via jouw game abonneert met PromptRobloxSubscriptionPurchase .

Om Plus-abonnementen binnen jouw game aan te bieden en beloningen aan gebruikers te geven:

1.

Detecteer wanneer de gebruiker het punt in jouw game bereikt waar je het Plus-abonnement wilt aanbieden.

2.

Controleer of de gebruiker al een actief Plus-abonnement heeft met [HasRobloxSubscription](/docs/nl-nl/reference/engine/classes/Player#HasRobloxSubscription) .

3.

Als de gebruiker al een abonnee is:

1.

Geef hen onmiddellijk de beloning.

4.

Als de gebruiker geen abonnee is:

1.

Vraag hen om Roblox Plus aan te schaffen met [PromptRobloxSubscriptionPurchase](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptRobloxSubscriptionPurchase) .

2.

Luister naar [PromptRobloxSubscriptionPurchaseFinished](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptRobloxSubscriptionPurchaseFinished)  om te detecteren wanneer de aankoopprompt UI is gesloten.

3.

Bevestig het Plus-abonnement op de server met [HasRobloxSubscription](/docs/nl-nl/reference/engine/classes/Player#HasRobloxSubscription)  via de [GetPropertyChangedSignal](/docs/nl-nl/reference/engine/classes/Instance#GetPropertyChangedSignal)  voordat je enige beloningen geeft. Dit evenement verifieert dat de abonnementsstatus van de gebruiker daadwerkelijk is veranderd.

### [Voorbeelden](#voorbeelden)[](#voorbeelden)

De volgende voorbeelden tonen hoe je met Roblox Plus in jouw game kunt werken, inclusief het ophalen van kortingsinformatie, het controleren van abonnementsstatus, het aanmoedigen van gebruikers om zich te abonneren en het afhandelen van de aankoopstroom.

##### Voorbeeld 1

Print Roblox Plus kortingsinformatie voor een gamepas.

```

local MarketplaceService = game:GetService("MarketplaceService")

local PASS_ID = 12345678

local DiscountTypeDisplay = {

	RobloxPlusSubscription = "Roblox Plus Korting",

}

local productInfo = MarketplaceService:GetProductInfoAsync(PASS_ID, Enum.InfoType.GamePass)

print(string.format("Oorspronkelijke Prijs: %d", productInfo.UserBasePriceInRobux))

for _, discount in ipairs(productInfo.PriceDiscountDetails) do

	local displayName = DiscountTypeDisplay[discount.Type] or "Andere Korting"

	print(string.format("%s (%d%%): -%d", displayName, discount.Percent, discount.AmountInRobux))

end

print(string.format("Je Betaalt: %d", productInfo.PriceInRobux))

```

##### Voorbeeld 2

Controleer of een gebruiker een actief Roblox Plus-abonnement heeft en voer acties uit op basis van hun abonnementsstatus.

```

local MarketplaceService = game:GetService("MarketplaceService")

local player = game.Players.LocalPlayer

local success, details = pcall(function()

    return MarketplaceService:GetRobloxSubscriptionDetailsAsync(player)

end)

if success and details.IsSubscribed then

    -- Controleer de duur van het Plus-abonnement van de gebruiker

    local threeMonths = 90 * 24 * 60 * 60

    if details.StartTime and (os.time() - details.StartTime.UnixTimestamp) > threeMonths then

        print("De '3-Maanden Abonnements Veteraan' skin wordt toegekend!")

    end

    -- Controleer of de gebruiker zich via de game heeft geabonneerd

    if details.IsOriginExperience then

        print("Attributie bevestigd: Gebruiker heeft zich via deze game geabonneerd.")

    else

        print("Gebruiker heeft zich elders geabonneerd: Website of een andere game.")

    end

end

```

##### Voorbeeld 3

Vraag gebruikers om zich te abonneren op Plus en behandel de aankoopstroom in jouw game.

```

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

local teleporter = script.Parent

local showModal = true

local EXCLUSIVE_AREA_POSITION = Vector3.new(1200, 200, 60)

-- Geef de beloning en teleporteer de abonnerende gebruiker naar het exclusieve gebied

local function grantRewardAndTeleport(player)

	player:RequestStreamAroundAsync(EXCLUSIVE_AREA_POSITION)

	local character = player.Character

	if character and character.Parent then

		local currentPivot = character:GetPivot()

		character:PivotTo(currentPivot * CFrame.new(EXCLUSIVE_AREA_POSITION))

	end

end

-- Detecteer wanneer het personage de teleporter aanraakt

teleporter.Touched:Connect(function(otherPart)

	local player = Players:GetPlayerFromCharacter(otherPart.Parent)

	if not player then

		return

	end

	if not player:GetAttribute("CharacterPartsTouching") then

		player:SetAttribute("CharacterPartsTouching", 0)

	end

	player:SetAttribute("CharacterPartsTouching", player:GetAttribute("CharacterPartsTouching") + 1)

	if player.HasRobloxSubscription then

		-- Gebruiker heeft al Roblox Plus; geef de beloning onmiddellijk

		grantRewardAndTeleport(player)

	else

		-- Vraag om Roblox Plus-abonnement

		if not showModal then

			return

		end

		showModal = false

		task.delay(5, function()

			showModal = true

		end)

		MarketplaceService:PromptRobloxSubscriptionPurchase(player)

	end

end)

-- Detecteer wanneer het personage de teleporter verlaat

teleporter.TouchEnded:Connect(function(otherPart)

	local player = Players:GetPlayerFromCharacter(otherPart.Parent)

	if player and player:GetAttribute("CharacterPartsTouching") then

		player:SetAttribute("CharacterPartsTouching", player:GetAttribute("CharacterPartsTouching") - 1)

	end

end)

-- Geef de beloning wanneer de server een wijziging in het lidmaatschap bevestigt

-- Verbind de wijziging van HasRobloxSubscription voor elke speler

Players.PlayerAdded:Connect(function(player)

	player:GetPropertyChangedSignal("HasRobloxSubscription"):Connect(function()

		if player.HasRobloxSubscription

			and player:GetAttribute("CharacterPartsTouching")

			and player:GetAttribute("CharacterPartsTouching") > 0

		then

			grantRewardAndTeleport(player)

		end

	end)

end)

```

##### Voorbeeld 4

Detecteer wanneer de gebruiker de aankoopprompt UI sluit.

```

local MarketplaceService = game:GetService("MarketplaceService")

local function onPromptRobloxSubscriptionPurchaseFinished(player, didTryPurchasing)

	if didTryPurchasing then

		-- Gebruiker heeft geprobeerd zich te abonneren; wacht op wijziging van HasRobloxSubscription om te bevestigen

		print(player.Name, "heeft geprobeerd zich te abonneren op Roblox Plus")

	else

		print(player.Name, "heeft de Roblox Plus-abonnementsaanvraag gesloten zonder te kopen")

	end

end

MarketplaceService.PromptRobloxSubscriptionPurchaseFinished:Connect(onPromptRobloxSubscriptionPurchaseFinished)

```

## [Verdien aan tijd in betaalde privéservers](#verdien-aan-tijd-in-betaalde-privéservers)[](#verdien-aan-tijd-in-betaalde-privéservers)

Roblox Plus-abonnees kunnen gratis een betaalde [privéserver](/docs/nl-nl/production/monetization/private-servers)  voor jouw game maken. Om ervoor te zorgen dat je nog steeds kunt verdienen aan deze server, compenseert Roblox je op basis van de tijd die Plus-abonnees doorbrengen in de betaalde privéserver die ze zelf hebben gemaakt binnen jouw game.

Betalingen zijn gebaseerd op de tijd die een Plus-abonnee doorbrengt in de betaalde privéserver die ze zelf hebben gemaakt.  Dit betekent dat als een Plus-abonnee een andere Plus-abonnee uitnodigt naar hun betaalde privéserver, alleen de tijd van de servereigenaar meetelt voor jouw verdiensten. Tijd doorgebracht door de uitgenodigde abonnee telt niet mee.

Op de dag van de verlenging van het Plus-abonnement evalueert Roblox het gebruik van betaalde privéservers over de voorgaande 30 dagen voor die abonnee. Deze evaluatie vindt plaats, zelfs als de abonnee Plus annuleert in plaats van te verlengen. Roblox bepaalt vervolgens de top vijf betaalde privéservers van de abonnee over Roblox , op basis van de tijd die ze in elke server hebben doorgebracht tijdens die periode. De betaalde privéserver in jouw game komt in aanmerking als deze tot die vijf behoort en als de abonnee minimaal 60 cumulatieve minuten in deze server heeft doorgebracht.

Als een Plus-abonnee, inclusief een abonnee op een Gratis Plus Proefperiode, minstens 60 cumulatieve minuten in de afgelopen 30 dagen  in de betaalde privéserver die ze binnen jouw game hebben gemaakt doorbrengt, kun je tot 100 Robux voor die abonnee  verdienen op basis van de serverprijs.

In het volgende voorbeeld komen Privéservers A, B en C in aanmerking omdat de Plus-abonnee minstens 60 minuten in elke server heeft doorgebracht in de afgelopen 30 dagen. Privéservers D en E komen niet in aanmerking omdat ze niet voldoen aan de 60-minuten drempel. Dit zijn de top vijf betaalde privéservers van de abonnee over Roblox. Over de in aanmerking komende servers verdient de maker in totaal 205 Robux van deze Plus-abonnee.

| Betaalde privéserver van de game | | Serverprijs | | Cumulatieve tijd (30 dagen voorafgaand aan verlenging) | | Verdiensten maker |
| Privéserver A | | 100 Robux | | 120 minuten | | 70 Robux (70% omzetdeel op een serverprijs van 100 Robux) |
| Privéserver B | | 200 Robux | | 80 minuten | | 100 Robux (70% omzetdeel op een serverprijs van 200 Robux, beperkt tot 100 Robux) |
| Privéserver C | | 50 Robux | | 70 minuten | | 35 Robux (70% omzetdeel op een serverprijs van 50 Robux) |
| Privéserver D | | 60 Robux | | 15 minuten | | Niet in aanmerking (minder dan 60 minuten) |
| Privéserver E | | 70 Robux | | 10 minuten | | Niet in aanmerking (minder dan 60 minuten) |

## [Verdien aan Robux-overdrachten](#verdien-aan-robux-overdrachten)[](#verdien-aan-robux-overdrachten)

Robux-overdrachten stellen Plus-abonnees in staat om Robux rechtstreeks naar andere gebruikers te sturen. Je kunt de Transfers API implementeren om deze overdrachten binnen jouw game aan te vragen en een deel van elke overdracht te verdienen.

Wanneer een Plus-abonnee een overdracht initieert die wordt uitgelokt door [PromptRobuxTransferAsync](/docs/nl-nl/reference/engine/classes/MarketplaceService#PromptRobuxTransferAsync)  binnen jouw game, ontvang je 10% van het overdrachtsbedrag . Bijvoorbeeld, als een abonnee 100 Robux naar een andere gebruiker overmaakt, ontvangt de ontvanger 90 Robux (90%) en jouw game ontvangt 10 Robux (10%).

Robux die jouw game verdient uit overdrachten is in aanmerking voor het DevEx-programma . Roblox neemt geen vergoeding voor deze overdrachten.

Bij het instellen van overdrachten in jouw game, moet het bedrag tussen de 10 en 500 Robux per transactie liggen.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/roblox-plus/TransferRobuxPrompt.png)

Voor meer informatie over het implementeren van Robux-overdrachten binnen jouw game, zie [Robux-overdrachten](/docs/nl-nl/production/monetization/robux-transfers) .

## [Volg je Plus-verdiensten](#volg-je-plus-verdiensten)[](#volg-je-plus-verdiensten)

Je kunt je verdiensten volgen van gebruikers die zich via jouw in-game prompts op Roblox Plus abonneren, Robux-overdrachten met behulp van de Transfers API, en tijd die Plus-abonnees doorbrengen in jouw betaalde privéservers, of ze nu vanuit jouw game of daarbuiten deelnemen.

Om een gedetailleerd overzicht van je Plus-abonnementsincentives te zien:

1.

Ga in Creator Hub naar Creations  en selecteer een game.

2.

Ga naar Monetization  ⟩ Roblox Plus .

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/roblox-plus/Roblox-Plus-Analytics.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
