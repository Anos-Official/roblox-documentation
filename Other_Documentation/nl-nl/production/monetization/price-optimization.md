<!-- Source: https://create.roblox.com/docs/nl-nl/production/monetization/price-optimization -->

Prijsoptimalisatie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Verdienen](/docs/nl-nl/production/monetization)
6. /
7. [Managed pricing](/docs/nl-nl/production/monetization/managed-pricing)

# Prijsoptimalisatie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Prijsoptimalisatie maakt deel uit van [Beheerde prijzen](/docs/nl-nl/production/monetization/managed-pricing) , het uniforme systeem dat je prijzen optimaliseert over producten en regio's.

Om een succesvolle prijsoptimalisatietest uit te voeren, moet je game voldoende transacties hebben om significante gegevens te produceren. In de meeste gevallen betekent dit dat je game in de afgelopen 30 dagen minstens 60.000 transacties moet hebben gehad.

Om te achterhalen hoeveel transacties je game heeft gehad, tel je het totale aantal productverkopen over een periode van 30 dagen. Voor meer informatie, zie [Pass-analyse](/docs/nl-nl/production/monetization/passes#toegangspasanalyses)  en [Ontwikkelaarsproductanalyse](/docs/nl-nl/production/monetization/developer-products#analyses-van-ontwikkelaarsproducten) .

Prijsoptimalisatie , opgenomen in Beheerde Prijzen, stelt je in staat om de beste prijsniveaus voor je passen en ontwikkelaarsproducten te vinden, wat je kan helpen om in de loop van de tijd meer geld te verdienen terwijl je prijzen concurrerend blijven. Wanneer je een prijstest uitvoert, zien subsets van je gebruikers verschillende prijzen voor hetzelfde product. Aan het einde van de test ontvang je aanbevelingen voor de prijzen die het beste presteerden bij je publiek.

Voordat je prijsoptimalisatie gebruikt, moet je de [dynamische prijscontroletool](#controleer-op-dynamische-prijzen)  gebruiken om ervoor te zorgen dat productprijzen dynamisch zijn gescript in je game. Na het gebruik van prijsoptimalisatie kun je een prijsbeoordelingsperiode uitvoeren om de langetermijneffecten van je prijswijzigingen op de omzet te volgen.

 ![](https://prod.docsiteassets.roblox.com/assets/monetization/price-optimization/Price-Optimization-Example.png)

## [Hoe tests werken](#hoe-tests-werken)[](#hoe-tests-werken)

-

Je gebruikers worden automatisch verdeeld in verschillende testgroepen. Het systeem is geoptimaliseerd om de kleinste groep gebruikers te kiezen om de test uit te voeren.

-

Elke testgroep ziet een andere prijs terwijl Roblox de conversieratio tussen de groepen meet.

-

Na de test worden geoptimaliseerde prijzen alleen toegepast als dit resulteert in een positieve incrementele totale omzet.

-

Je kunt de resultaten en impact in rapportages bekijken.

-

Tests worden automatisch minstens elke 90 dagen uitgevoerd, of eerder wanneer prijzen mogelijk niet langer geoptimaliseerd zijn.

## [Controleer op dynamische prijzen](#controleer-op-dynamische-prijzen)[](#controleer-op-dynamische-prijzen)

Prijsoptimalisatie kan geen gegevens verzamelen van en wijzigingen aanbrengen in prijzen die je hardcoded in je game hebt. Om een prijsoptimalisatietest uit te voeren op producten met hardcoded prijzen, moet je ze eerst bijwerken zodat ze dynamisch zijn gescript.

Dynamisch gescripte prijzen worden bijgewerkt via [MarketplaceService](/docs/nl-nl/reference/engine/classes/MarketplaceService)  en gebruiken functies zoals [GetProductInfo()](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetProductInfo)  en [GetDeveloperProductsAsync()](/docs/nl-nl/reference/engine/classes/MarketplaceService#GetDeveloperProductsAsync)  om productprijzen op te halen en weer te geven die je hebt ingesteld via het Creator Hub. Voor informatie over hoe je productprijzen dynamisch kunt scripten, zie [Verkoop een pas](/docs/nl-nl/production/monetization/passes#verkoop-een-toegangspas)  en [Verkoop een ontwikkelaarsproduct](/docs/nl-nl/production/monetization/developer-products#verkoop-een-ontwikkelaarsproduct) .

De dynamische prijscontroletool werkt alle te koop aangeboden producten bij met een nep Robux-prijs of een nep economische locatie om te identificeren welke van je productprijzen hardcoded zijn en welke zijn gescript met [MarketplaceService](/docs/nl-nl/reference/engine/classes/MarketplaceService)  in je game. Als een productprijs wordt bijgewerkt naar een nieuwe prijs, is de prijs gescript. Als deze hetzelfde blijft, is de prijs hardcoded.

De InfoType  parameter in GetProductInfo()  haalt standaard een asset op. Om een ontwikkelaarsproduct op te halen, gebruik je [Enum.InfoType.Product](/docs/nl-nl/reference/engine/enums/InfoType#Product) . Om een pas op te halen, gebruik je [Enum.InfoType.GamePasses](/docs/nl-nl/reference/engine/enums/InfoType#GamePasses) .

Client Script voor een Dynamisch Gescripte Productprijs

```

local productInfo = MarketplaceService:GetProductInfo(PRODUCT_ID, Enum.InfoType.Product)

local price = productInfo.PriceInRobux

```

Client Script voor een Hard-Coded Productprijs

```

local priceInRobux = 500

```

Om de dynamische prijscontroletool te gebruiken:

1.

Ga naar [Creations](https://create.roblox.com/dashboard/creations)  en selecteer een game.

2.

Ga naar Monetization  ⟩ Beheerde Prijzen .

3.

Klik op Dynamische Prijscontrole .

4.

Onder Voeg testaccounts toe , voer tot vijf Roblox-gebruikers in om te controleren op hardcoded prijzen.

5.

Selecteer een testtype.

-

Prijs vastgezet  werkt alle dynamisch gescripte prijzen bij met een vast nep Robux-bedrag.

-

Locatie vastgezet  werkt alle dynamisch gescripte prijzen bij met een regio-specifieke prijs voor een nep economische locatie.

6.

Klik op Inschakelen . Na een paar minuten kun je je game betreden om de hardcoded prijzen te identificeren.

Om de dynamische prijscontroletool uit te schakelen, ga je naar de pagina Dynamische Prijscontrole  en klik je op Uitschakelen .

## [Gebruik prijsoptimalisatie](#gebruik-prijsoptimalisatie)[](#gebruik-prijsoptimalisatie)

Om de prijsoptimalisatiefunctie van Beheerde Prijzen te gebruiken:

1.

Ga naar [Creations](https://create.roblox.com/dashboard/creations)  en selecteer een game.

2.

Ga naar Monetization  ⟩ Beheerde Prijzen .

3.

Selecteer de ontwikkelaarsproducten en passen die je wilt opnemen in de prijstest. Voor de beste resultaten, neem alle producten op.

4.

Klik op Test starten . Gebruikers zullen de testprijzen zien wanneer ze opnieuw je game betreden. Na ongeveer 3 weken ontvang je een e-mailmelding dat de test is voltooid. De pagina Beheerde Prijzen  wordt bijgewerkt met de geoptimaliseerde productprijzen, de aanbevolen prijspercentageverandering en de geschatte langetermijneffecten van het toepassen van de nieuwe productprijzen.

5.

Klik op Beoordelen & Prijzen toepassen  om de resultaten van de prijsoptimalisatietest toe te passen.

Je kunt de prijsoptimalisatietest op elk moment stoppen door op Test stoppen  te klikken op de pagina Beheerde Prijzen . Als je de test stopt, keren je productprijzen terug naar hun oorspronkelijke prijzen.

## [Beperkingen](#beperkingen)[](#beperkingen)

-

Je kunt alleen de prijzen van ontwikkelaarsproducten en passen optimaliseren. Prijsoptimalisatie is niet beschikbaar voor abonnementen.

-

Je kunt geen wijzigingen aanbrengen in de prijzen van producten die betrokken zijn bij prijstests terwijl de tests aan de gang zijn.

## [Woordenlijst](#woordenlijst)[](#woordenlijst)

| Term | | Definitie |
| --- | --- |
| Testperiode | | De prijsoptimalisatietestperiode of de prijsbeoordelingsperiode. |
| Prijs groepen | | De testgroepen die betrokken zijn bij de Beheerde Prijzen tests. |
| Betaalde gebruikers | | Het aantal gebruikers dat ten minste één getest product heeft gekocht tijdens de testperiode. |
| Verkopen | | Het aantal producten dat is verkocht tijdens de testperiode. |
| Totale speeltijd | | De totale tijd die gebruikers in de game hebben doorgebracht tijdens de testperiode. |
| Dagelijkse actieve gebruikers | | Het aantal actieve gebruikers tijdens de testperiode. |
| Omzet | | Het bedrag aan Robux dat is uitgegeven aan geteste producten tijdens de vier weken durende prijsbeoordelingsperiode. |
| Geschatte omzetimpact | | De verwachte langetermijnomzetstijging als de geoptimaliseerde prijzen worden toegepast op de geteste producten. |
| Omzetstijging van geteste producten | | De omzet van de geteste producten die aan 98% van de gebruikers zijn getoond tijdens de prijsbeoordelingsperiode. |
| Totale omzetstijging | | De gecombineerde omzet van de geteste producten tijdens de prijsbeoordelingsperiode, inclusief de 2% van de gebruikers die de oorspronkelijke prijzen te zien kregen. |
| ARPPU | | De gemiddelde omzet per betalende gebruiker tijdens de prijsbeoordelingsperiode. |
| Aanbevolen prijsverhoging | | Het aantal producten waarvoor we aanbevelen de prijs te verhogen. |
| Aanbevolen prijsverlaging | | Het aantal producten waarvoor we aanbevelen de prijs te verlagen. |
| Aanbevolen geen wijziging | | Het aantal producten waarvoor we aanbevelen de huidige prijs te behouden. |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
