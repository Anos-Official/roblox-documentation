<!-- Source: https://create.roblox.com/docs/nl-nl/production/monetization/paid-random-items -->

Richtlijnen voor het beleid van betaalde willekeurige items | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Platform](/docs/nl-nl/get-started)
4. /
5. Richtlijnen en beleid

# Richtlijnen voor het beleid van betaalde willekeurige items

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Vanwege regelgeving in verschillende landen kunnen bepaalde vereisten van toepassing zijn op willekeurige items die rechtstreeks of onrechtstreeks met Robux zijn gekocht. Dit omvat willekeurige items die zijn gekocht met betaalde in-game valuta. Beide van de volgende zijn bijvoorbeeld betaalde willekeurige items:

-

Robux betalen om een prijzenwiel te draaien

-

Robux betalen om edelstenen of draai-tickets te kopen die worden besteed aan een prijzenwiel

Er zijn verschillende soorten items die betaalde willekeurige items zijn, waaronder maar niet beperkt tot:

| ** Itemtype** | | ** Voorbeelden** |
| --- | --- |
| ** Capsule-items** | |
-

Draai aan een wiel voor een prijs

-

Broed een ei voor een huisdier

-

Open een kist voor loot

 |
| ** Verbeteringsitems** | |
-

Toverdrank voor een vaardigheid met willekeurige duur

-

Upgrade spreuk met een kans dat het werkt

 |
| ** Combinatie-items** | |
-

Consumptie of synthese van twee zeldzame eieren voor een betere kans op een resultaat van hogere kwaliteit

 |
| ** Kansveranderingsitems** | |
-

Geluk verhogingen

-

Spijt systemen

-

Verbeterde hulpbron drops

-

Verhoogde scrolls

 |

## [Kansen openbaarmaking van items](#kansen-openbaarmaking-van-items)[](#kansen-openbaarmaking-van-items)

Volgens Roblox's [Gebruiksvoorwaarden](https://en.help.roblox.com/hc/en-us/articles/115004647846-Roblox-Terms-of-Use)  en [Gemeenschapsnormen](https://about.roblox.com/community-standards#roblox-economy-paid-random-items) , als je betaalde willekeurige items aanbiedt die gebruikers kunnen kopen met Robux of andere in-game valuta die met Robux te koop zijn, moet je alle mogelijke uitkomsten en de werkelijke numerieke kansen van wat ze kunnen ontvangen aangeven.

 ![Een voorbeeld van een prijzenwiel met numerieke kansen van wat gebruikers kunnen ontvangen.](https://prod.docsiteassets.roblox.com/assets/policy/paid-random-items/Prize-wheel.png)

Bovendien:

-

Als er te veel individuele uitkomsten zijn om in het dynamische 3D-overzicht van de gebruiker te passen, zoals zeldzaamheidscategorieën die veel individuele items in elke categorie hebben, kan de itemlijst van uiteindelijke uitkomsten en hun numerieke mogelijkheden worden weergegeven in een klikbare pop-up met een "Info" of "Details" pictogram dat zichtbaar en toegankelijk is vóór aankoop. Het gebruik van een op zichzelf staand symbool zoals het (i) pictogram zonder een beschrijvend woord is niet  voldoende.

-

Kansen moeten worden weergegeven als een kanspercentage, en de kanspercentages van alle uiteindelijke uitkomsten moeten precies optellen tot 100%. Voor kansen met lange decimalen kun je afronden op vier of meer decimalen lager dan de decimaalplaats met het eerste niet-nul getal, en een disclaimer opnemen, zoals: "Kansen zijn afgerond; het totaal van weergegeven individuele kansen kan niet gelijk zijn aan 100%."

-

Als veel items binnen een lijst dezelfde individuele kansen hebben, is het acceptabel om aan het begin van de lijst met items te vermelden "Kansen voor elk item hieronder: X%"

-

Als gebruikers slechts één exemplaar van een uitkomst kunnen verkrijgen, moeten de kansen voor de resterende verkrijgbare uitkomsten worden bijgewerkt om de actuele resterende kansen voor die gebruiker weer te geven.

![](https://prod.docsiteassets.roblox.com/assets/policy/paid-random-items/Before-Outcome.png) Voorbeeld van kansen per zeldzaamheidsniveau met klikbare "Details" knop

![](https://prod.docsiteassets.roblox.com/assets/policy/paid-random-items/After-Outcome.png) Voorbeeld van openbaarmaking van individuele itemkansen

Dit beleid is ook van toepassing op indirecte aankopen. Als een gebruiker bijvoorbeeld zijn Robux gebruikt om sleutels te kopen om dozen te openen, her-roll tokens of draai-tickets, moet je de kansen van hun potentiële beloning openbaar maken voordat ze de in-game valuta uitgeven aan de willekeurige uitkomst.

Betaalde items die de kansen van andere willekeurige uitkomsten verhogen, moeten ook vóór aankoop worden uitgelegd. Als een gebruiker bijvoorbeeld een "geluksdrankje" of "magische hengel" kan kopen die de kansen op minder waarschijnlijke uitkomsten verbetert, moeten deze effecten numeriek worden uitgelegd. De nieuwe kansen van de verbeterde willekeurige items moeten ook dynamisch worden bijgewerkt wanneer deze items actief zijn om de werkelijke kansen van de gebruiker weer te geven.

Als je spel willekeurige virtuele beloningen aanbiedt in ruil voor het voltooien van een actie die geen betaling van Robux of andere in-game valuta inhoudt, ben je niet verplicht om de kansen openbaar te maken. Als een gebruiker bijvoorbeeld een sleutel vindt die een schatkist opent, hoef je de kansen van de items die ze uit de schatkist kunnen ontvangen niet te vermelden.

## [Per-gebruiker regelgeving](#per-gebruiker-regelgeving)[](#per-gebruiker-regelgeving)

Om je te helpen bepalen hoe je virtuele items in je spel per gebruiker moet behandelen, gebruik de [PolicyService:GetPolicyInfoForPlayerAsync()](/docs/nl-nl/reference/engine/classes/PolicyService#GetPolicyInfoForPlayerAsync)  methode. Specifiek, de structuur van de geretourneerde woordenlijst bevat ArePaidRandomItemsRestricted  en IsPaidItemTradingAllowed .

### [ArePaidRandomItemsRestricted](#arepaidrandomitemsrestricted)[](#arepaidrandomitemsrestricted)

Wanneer ArePaidRandomItemsRestricted  waar  is, kan de gebruiker niet interageren met betaalde willekeurige itemgeneratoren, hetzij via Robux rechtstreeks of game valuta gekocht met Robux.

Voor niet-geschikte gebruikers gedefinieerd door de API, moeten makers een van deze behandelingen toepassen:

| ** Behandeling** | | ** Voorbeelden** |
| ** Een onbetaalde, verdienbare weg aanbieden om het willekeurige item te verwerven** | | Mysterie-eieren worden gratis gegeven bij mijlpalen in het spel |
| ** De uitkomsten van het item aanbieden in een vooraf bepaalde, niet-willekeurige volgorde die aan de gebruiker vóór aankoop is openbaar gemaakt** | | Eerste draai is altijd 5 edelstenen, tweede is altijd 10 edelstenen, derde is altijd 20 edelstenen, enz. |
| ** De specifieke uitkomsten aanbieden voor directe, gegarandeerde aankoop (geprijsd op basis van de verwachte waarde van de uitkomst)** | | Als een lootbox voor een zwaard met een zeldzaamheid van 10 Robux met 5% kansen is, bied het zwaard aan niet-geschikte gebruikers voor directe aankoop geprijsd op 200 Robux |
| ** Het betaalde willekeurige item uit het spel verwijderen of verbergen** | | Een gigantisch draai-prijzenwiel vervangen door een winkel die directe aankopen aanbiedt |
| ** De aankoop van het betaalde willekeurige item blokkeren met een foutmelding** | | De aankoopknop vervangen door "Sorry, dit item is niet beschikbaar voor gebruikers in jouw regio" |
| ** De gebruiker verwijderen uit de delen van het spel met betaalde willekeurige items** | | Ze teleporteren |

### [IsPaidItemTradingAllowed](#ispaiditemtradingallowed)[](#ispaiditemtradingallowed)

Wanneer IsPaidItemTradingAllowed  waar  is, kan de gebruiker virtuele items verhandelen die ze hebben gekocht met game valuta of Robux.

Voor niet-geschikte gebruikers gedefinieerd door de API, mogen makers hen niet toestaan toegang te krijgen tot de mogelijkheid om de resulterende uitkomst van een betaald willekeurig item of andere betaalde items te verhandelen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
