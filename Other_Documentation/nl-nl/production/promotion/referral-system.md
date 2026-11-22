<!-- Source: https://create.roblox.com/docs/nl-nl/production/promotion/referral-system -->

Vrienden verwijzingssysteem | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Ontdekking](/docs/nl-nl/discovery)

# Vrienden verwijzingssysteem

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Als je deze functie eerder hebt gebruikt terwijl deze nog in beta was, zorg er dan voor dat je de nieuwe [gepersonaliseerde beloningsbanners](#maak-een-beloningsbanner)  implementeert om het bereik van je vrienden verwijzingssysteem te maximaliseren.

|  | |  |
| --- | --- |

Het vrienden verwijzingssysteem moedigt bestaande spelers aan om nieuwe spelers in je game te brengen, wat de spelersretentie en de algehele betrokkenheid vergroot. Spelers kunnen verwijzingslinks openen en delen vanuit [speler uitnodigingsprompten](/docs/nl-nl/production/promotion/invite-prompts)  of rechtstreeks vanuit het standaard in-game uitnodigingsmenu.

Als ontwikkelaar kun je gepersonaliseerde banners maken om je beloningssysteem te adverteren en deelbare verwijzingslinks te gebruiken om:

-

Bij te houden welke spelers met succes andere spelers in je game hebben uitgenodigd.

-

Bij te houden welke spelers zich hebben aangemeld voor je game met behulp van een verwijzingslinkuitnodiging van een andere speler.

-

Beloningen te creëren en te distribueren aan zowel uitnodigers als genodigden.

Uitnodigers sturen uitnodigingen

Genodigden voegen zich bij de game

Om een verwijzingssysteem te implementeren, [stel een verwijzings evenement in](#stel-een-verwijzings-evenement-in)  en [creëer verwijzingsbeloningen](#verleen-verwijzingsbeloningen)  in Studio. De ReferredByPlayerId  eigenschap van [GetJoinData()](/docs/nl-nl/reference/engine/classes/Player#GetJoinData)  wordt automatisch ingevuld voor alle soorten uitnodigingen en geeft je toegang tot de gebruikers-ID van de verwijzende speler. Je kunt deze gegevens vervolgens gebruiken in het Players.PlayerAdded  evenement om de uitnodiger te identificeren en beloningen toe te kennen aan zowel de uitnodiger als de genodigde.

```

function onPlayerAdded(player)

    local referredByPlayerId = player:GetJoinData().ReferredByPlayerId

    local referrerEvent: RemoteEvent = ReplicatedStorage:FindFirstChild("ReferralReceivedEvent")

    referrerEvent:FireClient(player, referredByPlayerId)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

Om ervoor te zorgen dat spelers het beloningssysteem begrijpen, [implementeer een gepersonaliseerde beloningsbanner](#maak-een-beloningsbanner)  bovenaan je vrienden uitnodigingsvenster waarin ze details zien over de beloningen die ze kunnen verdienen.

## [Stel een verwijzings evenement in](#stel-een-verwijzings-evenement-in)[](#stel-een-verwijzings-evenement-in)

Om een verwijzings evenement in te stellen:

1.

Stel een RemoteEvent  in ReplicatedStorage  in om een remote event te creëren om met de client te communiceren wanneer een verwijzing wordt ontvangen.

2.

Haal de gebruikers-ID van de uitnodiger op met ReferredByPlayerId  om spelersjoins bij te houden en de verwijzingslogica in je server-side script te verwerken tijdens het Players.PlayerAdded  evenement.

```

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Maak of haal het RemoteEvent op voor het afhandelen van verwijzingen

local referrerEvent: RemoteEvent = ReplicatedStorage:FindFirstChild("ReferralReceivedEvent")

-- Functie die wordt geactiveerd wanneer een speler zich aanmeldt

function onPlayerAdded(player)

    local joinData = player:GetJoinData()

    local referredByPlayerId = joinData.ReferredByPlayerId

    -- Controleer of de speler is uitgenodigd via een verwijzing

    if referredByPlayerId and referredByPlayerId ~= 0 then

        -- Activeer het verwijzings evenement naar de client, met de ID van de uitnodiger

        referrerEvent:FireClient(player, referredByPlayerId)

        -- Extra logica voor het belonen van de uitnodiger en genodigde kan hier worden toegevoegd

        -- bijv. rewardReferrer(referredByPlayerId)

        -- bijv. rewardInvitee(player)

    end

end

-- Verbind de functie met het PlayerAdded evenement

Players.PlayerAdded:Connect(onPlayerAdded)

```

## [Verleen verwijzingsbeloningen](#verleen-verwijzingsbeloningen)[](#verleen-verwijzingsbeloningen)

Om deelname aan te moedigen, verleen beloningen aan zowel uitnodigers als genodigden. Je kunt bijvoorbeeld uitnodigers een badge of in-game valuta geven wanneer hun vriend zich bij de game voegt, en genodigden een welkomstbeloning geven voor het zich aanmelden via een verwijzingslink.

```

local Players = game:GetService("Players")

local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- Maak of haal het RemoteEvent op voor het afhandelen van verwijzingen

local referrerEvent: RemoteEvent = ReplicatedStorage:FindFirstChild("ReferralReceivedEvent")

-- Functie die wordt geactiveerd wanneer een speler zich aanmeldt

function onPlayerAdded(player)

    local joinData = player:GetJoinData()

    local referredByPlayerId = joinData.ReferredByPlayerId

    -- Controleer of de speler is uitgenodigd via een verwijzing

    if referredByPlayerId and referredByPlayerId ~= 0 then

        -- Activeer het verwijzings evenement naar de client, met de ID van de uitnodiger

        referrerEvent:FireClient(player, referredByPlayerId)

        -- Beloning voor de uitnodiger

        function rewardReferrer(referrerId)

          local referrerPlayer = Players:GetPlayerByUserId(referrerId)

          if referrerPlayer then

              -- Geef de uitnodiger hun beloning

              -- Voorbeeld: referrerPlayer.leaderstats.Coins.Value += 100

          end

        end

        -- Beloning voor de genodigde

        function rewardInvitee(player)

            -- Geef de genodigde hun beloning

            -- Voorbeeld: player.leaderstats.WelcomeBonus.Value += 50

        end

    end

end

-- Verbind de functie met het PlayerAdded evenement

Players.PlayerAdded:Connect(onPlayerAdded)

```

## [Maak een beloningsbanner](#maak-een-beloningsbanner)[](#maak-een-beloningsbanner)

Beloningsbanners moedigen gebruikers aan om vrienden uit te nodigen om zich bij je game aan te sluiten door hen details te tonen over de verwijzingsbeloningen die ze kunnen verdienen. Deze banners worden bovenaan je vrienden uitnodigingsvenster weergegeven.

Om een gepersonaliseerde beloningsbanner te maken:

1.

Ga in de Creator Hub naar Creations  en selecteer de game waarvoor je een verwijzings evenement hebt ingesteld.

2.

Ga naar Engagement  ⟩ Referral Rewards .

3.

Klik op Add Reward Details .

4.

Op de pagina Referral Rewards :

1.

Vervang het standaardpictogram door een afbeelding die je game vertegenwoordigt.

2.

Voer een beloningsnaam in die op de banner wordt weergegeven.

3.

Selecteer een start- en einddatum voor wanneer je de banner aan spelers wilt tonen.

4.

OPTIONEEL

 Voer een beschrijving in met details over de beloning.

5.

OPTIONEEL

 Als je beloningsbeperkingen wilt toevoegen, voer dan een beloningslimiet in. Bijvoorbeeld, een limiet van maximaal 3 beloningen per uitnodiger.

5.

Klik op Opslaan  om je wijzigingen op te slaan.

6.

Klik op Publiceren  om de banner zichtbaar te maken voor spelers.

Je kunt veel verschillende banners maken, maar er kan slechts één banner tegelijk worden gepubliceerd en weergegeven. Zorg ervoor dat de gepubliceerde banner nauwkeurig het verwijzingssysteem beschrijft dat je in Studio hebt geïmplementeerd.

## [Voorkom misbruik van het verwijzingssysteem](#voorkom-misbruik-van-het-verwijzingssysteem)[](#voorkom-misbruik-van-het-verwijzingssysteem)

Je kunt beveiligingsmaatregelen implementeren om te voorkomen dat spelers het vrienden verwijzingssysteem misbruiken.

-

Bied eenmalige beloningen aan om genodigden te volgen en ervoor te zorgen dat ze slechts één keer worden beloond.

-

Introduceer een cooldown-periode voordat een uitnodiger een andere verwijzing kan indienen.

-

Houd ongebruikelijke activiteiten in de gaten en implementeer corrigerende maatregelen zoals het verbannen van gebruikers of het annuleren van beloningen.

```

local DataStoreService = game:GetService("DataStoreService")

local Players = game:GetService("Players")

-- Maak of haal de datastore voor verwijzingen

local referralDataStore = DataStoreService:GetDataStore("ReferralDataStore")

-- Functie om verwijzing te controleren en te markeren

local function onPlayerAdded(player)

    local joinData = player:GetJoinData()

    local referredByPlayerId = joinData.ReferredByPlayerId

    -- Laad de verwijzingsgegevens van de speler

    local success, alreadyReferred = pcall(function()

        return referralDataStore:GetAsync(tostring(player.UserId))

    end)

    if not success then

        warn("Kon verwijzingsgegevens voor speler niet ophalen:", player.UserId)

        return

    end

    if referredByPlayerId and referredByPlayerId ~= 0 and not alreadyReferred then

        -- Beloning voor uitnodiger en genodigde

        rewardReferrer(referredByPlayerId)

        rewardInvitee(player)

        -- Markeer de speler als verwezen in DataStore

        local saveSuccess, err = pcall(function()

            referralDataStore:SetAsync(tostring(player.UserId), true)

        end)

        if not saveSuccess then

            warn("Kon verwijzingsstatus voor speler niet opslaan:", player.UserId, err)

        end

    end

end

-- Verbind de functie met het aanmelden van de speler

Players.PlayerAdded:Connect(onPlayerAdded)

```

## [Veelgestelde vragen](#veelgestelde-vragen)[](#veelgestelde-vragen)

Welke games komen in aanmerking om deze functie te gebruiken?

Deze functie is open voor elke game die minstens één dag live is en die de [Gemeenschapsnormen](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  niet schendt.

Welke spelers kunnen profiteren van verwijzingen?

Alle spelers komen in aanmerking om beloningen te verdienen via verwijzingen.

Is de uitnodiging beperkt tot de vrienden van een speler op Roblox?

Nee, spelers kunnen een uitnodiging sturen naar vrienden waarmee ze nog niet verbonden zijn op het Roblox-platform.

Verloopt de verwijzingslink?

De link verloopt nooit.

Hoe kan ik het meeste uit deze functie halen?

Je kunt een in-game knop toevoegen om het verwijzingssysteem te adverteren en spelers aan te moedigen om gebruik te maken van verwijzingen. Je kunt de knop vervolgens een beschrijvende titel geven en het knopklik evenement verbinden met het vrienden uitnodigingsvenster waar spelers de beloningsbanner kunnen zien.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
