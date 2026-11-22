<!-- Source: https://create.roblox.com/docs/nl-nl/production/monetization/paid-access-robux -->

Beta-toegang in Robux | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Verdienen](/docs/nl-nl/production/monetization)

# Beta-toegang in Robux

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Beta-toegang  stelt je in staat om gebruikers een eenmalige vergoeding in Robux te laten betalen om toegang te krijgen tot een game op desktop, mobiel, VR en de meeste spelconsoles. Gebruikers die toegang kopen, behouden toegang tot de game, zelfs als je de prijs verhoogt of beta-toegang uitschakelt.

Beta-toegang kan het aantal gebruikers dat je game betreedt beperken, aangezien sommige gebruikers mogelijk niet willen betalen voor toegang.

Sommige ontwikkelaars schakelen tijdelijk beta-toegang in om een gesloten bèta te creëren, zodat hun meest betrokken gebruikers vroegtijdig toegang tot een game hebben om te helpen met testen en feedback. Als je ervoor kiest om dit te doen, zorg er dan voor dat je gebruikers laat weten dat ze een bètaversie van je game kopen.

Games met beta-toegang zijn niet beschikbaar op Xbox.

## [Geschiktheid](#geschiktheid)[](#geschiktheid)

Om gebruikers te laten betalen voor beta-toegang in Robux, moet je:

-

Een geverifieerd e-mailadres hebben.

-

Een account hebben dat minstens 30 dagen oud is.

## [Prijzen](#prijzen)[](#prijzen)

Je kunt gebruikers tussen de 25 en 1000 Robux laten betalen voor beta-toegang tot je game.

## [Betalingen](#betalingen)[](#betalingen)

Betalingen voor aankopen van beta-toegang in Robux worden tot 7 dagen in escrow gehouden voordat ze worden uitbetaald en op de bank worden gestort die aan je Roblox-account is gekoppeld.

## [Terugbetalingen](#terugbetalingen)[](#terugbetalingen)

Terugbetalingen zijn niet beschikbaar voor gebruikers die beta-toegang in Robux kopen.

## [Beta-toegang inschakelen in de Creator Hub](#beta-toegang-inschakelen-in-de-creator-hub)[](#beta-toegang-inschakelen-in-de-creator-hub)

Om beta-toegang in de Creator Hub in te schakelen:

1.

Ga naar Creations  en selecteer een game.

2.

Ga naar Audience  ⟩ Access Settings .

3.

Onder Payment , selecteer Requires Robux  en voer het bedrag aan Robux in dat je wilt dat gebruikers betalen voor toegang. De prijs die je invoert, beïnvloedt het aantal Robux dat je per verkoop verdient.

4.

Onder Devices , selecteer welke apparaten je wilt inschakelen voor beta-toegang.

5.

Klik op Save Changes .

## [Beta-toegang inschakelen in Roblox Studio](#beta-toegang-inschakelen-in-roblox-studio)[](#beta-toegang-inschakelen-in-roblox-studio)

Om beta-toegang in Roblox Studio in te schakelen:

1.

Open het venster File  ⟩ Experience Settings  van Studio.

2.

Onder Monetization , klik op Configure on Creator Hub .

3.

Volg de stappen om [beta-toegang in de Creator Hub in te schakelen](#beta-toegang-inschakelen-in-de-creator-hub) .

## [Demo-modus](#demo-modus)[](#demo-modus)

Demo-modus  stelt gebruikers in staat om je game met beta-toegang uit te proberen voordat ze deze kopen. Wanneer de demo-modus is ingeschakeld, kan elke gebruiker je game betreden, zelfs als ze niet voor toegang hebben betaald. Je kunt vervolgens scripting gebruiken om te detecteren of een gebruiker de game bezit en hun gameplay dienovereenkomstig aan te passen, bijvoorbeeld door de toegang tot bepaalde gebieden of functies te beperken totdat ze kopen.

### [Demo-modus inschakelen](#demo-modus-inschakelen)[](#demo-modus-inschakelen)

Op de pagina Access Settings  voor je game, zet je Enable Demo Mode  aan onder de Robux-betalingssectie.

Na het in- of uitschakelen van de demo-modus is er een cooldown-periode voordat je de instelling opnieuw kunt wijzigen. Plan dienovereenkomstig voordat je de functie inschakelt of uitschakelt.

### [Beheer de demo-ervaring in scripts](#beheer-de-demo-ervaring-in-scripts)[](#beheer-de-demo-ervaring-in-scripts)

Gebruik [MarketplaceService:PlayerOwnsAssetAsync()](/docs/nl-nl/reference/engine/classes/MarketplaceService#PlayerOwnsAssetAsync)  om te controleren of een gebruiker toegang tot je game heeft gekocht. Gebruikers die geen toegang hebben gekocht, bevinden zich in de demo-modus, en je kunt beperken welke inhoud ze kunnen zien of mee kunnen interageren.

Plaats je toegangcontroles in een [Script](/docs/nl-nl/reference/engine/classes/Script)  onder [ServerScriptService](/docs/nl-nl/reference/engine/classes/ServerScriptService) . Verifieer toegang op de server voordat je beperkte acties toestaat, in plaats van alleen de client UI te verbergen.

De volgende codevoorbeeld toont hoe je inhoud achter een aankoopcontrole kunt plaatsen:

```

local MarketplaceService = game:GetService("MarketplaceService")

local Players = game:GetService("Players")

local PLACE_ID = game.PlaceId

local function setAccess(player: Player)

  local success, ownsAccess = pcall(function()

    return MarketplaceService:PlayerOwnsAssetAsync(player, PLACE_ID)

  end)

  if not success then

    warn("Kon eigendom niet controleren voor", player.Name)

    ownsAccess = false

  end

  if ownsAccess then

    -- Volledige toegang tot de game verlenen

  else

    -- Speler is in demo-modus: alleen demo-toegang verlenen

  end

end

Players.PlayerAdded:Connect(function(player)

  task.spawn(setAccess, player)

end)

for _, player in Players:GetPlayers() do

  task.spawn(setAccess, player)

end

```

Als een demo-speler tijdens dezelfde sessie toegang koopt, voer dan de eigendomcontrole opnieuw uit op de server voordat je volledige toegang verleent.

## [Beleid](#beleid)[](#beleid)

Robux beta-toegang games moeten:

-

Volgen de [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410)  en [Terms of Use](https://en.help.roblox.com/hc/articles/115004647846) .

-

Publiek zijn en beschikbaar voor alle gebruikers.

-

Geen [private servers](/docs/nl-nl/production/monetization/private-servers)  hebben.

-

Gebruikers niet toestaan om kopieën van plaatsen binnen de game te downloaden. Het kopiëren van een game is automatisch uitgeschakeld wanneer je beta-toegang inschakelt.

-

Goed functioneren en speelbaar zijn. Als een groot aantal gebruikers meldt dat een game kapot is, kan de game in quarantaine worden geplaatst en kunnen de nog in escrow zijnde verdiensten aan gebruikers worden terugbetaald.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
