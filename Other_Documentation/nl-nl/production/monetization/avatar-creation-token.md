<!-- Source: https://create.roblox.com/docs/nl-nl/production/monetization/avatar-creation-token -->

Avatar creatietoken | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. In-game creation

# Avatar creatietoken

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een avatar creatietoken  stelt ontwikkelaars in staat om gebruikers te laten creëren, aankopen en opslaan van avataritems rechtstreeks vanuit een game naar hun platformniveau-inventaris met behulp van [in-experience creatie](/docs/nl-nl/avatar/in-experience-creation)  of [in-experience make-up creatie](/docs/nl-nl/avatar/in-experience-creation-makeup) . Games die in-game creatie-API's implementeren, zoals [PromptCreateAvatarAsync](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync) , [PromptCreateAvatarAssetAsync](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAssetAsync) , en [PromptCreateMakeupAsync](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateMakeupAsync) , moeten een of meer avatar creatietokens bevatten. Je kunt tokens kopen en beheren in het [Creator Dashboard](https://create.roblox.com/dashboard/creations)  van je game.

Eigenaren van games die in-game avataritemcreatie integreren profiteren ook van [Marketplace commissies](/docs/nl-nl/marketplace/marketplace-fees-and-commissions#commissies)  als zowel maker  als game-eigenaar .

Om avatar creatietokens te maken, moet jij of jouw groep voldoen aan de [Marketplace makervereisten](/docs/nl-nl/marketplace/marketplace-policy#vereisten-voor-makers) . Om de geldigheid van het token te behouden, moet de eigenaar van het token deze makervereisten handhaven.

## [Maak een token](#maak-een-token)[](#maak-een-token)

Om gebruikers in staat te stellen om avataritems te creëren, ervoor te betalen en deze op te slaan in hun Roblox-inventaris in jouw game, moet je een Avatar Creatietoken instellen in het dashboard van jouw game.

Elk token vereist een Creatievoorschot  en een Creatiekosten . Het voorschot is volledig terugvorderbaar en is gebaseerd op de [huidige publicatievoorschotprijzen](/docs/nl-nl/marketplace/marketplace-fees-and-commissions#publicatievoorschot)  voor dat type item. Voor aankoop kun je een samenvatting van je totale gecombineerde voorschot en kosten bekijken bij het maken van je token.

Om een token te maken:

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Vouw de accountwisselaar in de linkerbovenhoek uit en zorg ervoor dat de juiste gebruiker of groep is geselecteerd.

3.

Ga naar Creations  ⟩ Experiences  en selecteer je game.

4.

Navigeer in het linkerpaneel naar Monetization  ⟩ Avatar Creatietokens .

5.

Klik op Token maken .

1.

Zorg ervoor dat jouw account of groepsaccount voldoet aan de [Marketplace Makervereisten](/docs/nl-nl/marketplace/marketplace-policy#vereisten-voor-makers) . Als het account van de token eigenaar niet ID-geverifieerd is met een Roblox Plus of Premium abonnement, kan de game geen in-game creatie-API's inschakelen. Je moet deze vereisten handhaven om de geldigheid van het token te behouden.

6.

Vul de volgende velden in:

1.

Naam  - De naam van je token. Dit is niet zichtbaar voor gebruikers en kan na creatie worden gewijzigd.

2.

Beschrijving  - De beschrijving van je token. Dit is niet zichtbaar voor gebruikers en kan na creatie worden gewijzigd.

3.

Itemtype  - Het Body  itemtype kan in-game worden gebruikt met [PromptCreateAvatarAsync](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync) , terwijl de andere itemtypes bedoeld zijn om te worden gebruikt met [PromptCreateAvatarAssetAsync](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAssetAsync) . Make-up itemtypes kunnen ook worden samengevoegd tot een enkele aankoopsoutfit met [PromptCreateMakeupAsync](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateMakeupAsync) , waarvoor een apart token per laag vereist is waarvan het type overeenkomt met het type van die laag. Je kunt deze instelling niet wijzigen na de creatie van het token.

4.

Bedrag boven prijsvloer  - Stel de prijs in boven de Marketplace Prijsvloer voor gemaakte items. Als je van plan bent om verschillende prijsniveaus voor items van hetzelfde type in je game te hebben, is de beste manier om dit te bereiken door meerdere tokens aan te schaffen. Je kunt dit veld na creatie wijzigen.

5.

Niet onder prijs stellen

OPTIONEEL

 - Stel de minimale prijs in voor gebruikers om je item aan te schaffen. Je kunt dit veld na creatie wijzigen.

 ![Prijs gerelateerde velden voor avatar token creatie, inclusief een berekende itemprijs.](https://prod.docsiteassets.roblox.com/assets/monetization/avatar-creation-tokens/Avatar-Creation-Token-Prices.png)

7.

Wanneer je klaar bent, controleer je de berekeningen van de Creatievoorschot  en Creatiekosten  en selecteer je Token maken  om je aankoop in te dienen.

8.

Je kunt nu het gemaakte token in de instellingen voor avatar creatietokens  van de game openen. Om [PromptCreateAvatarAsync](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync)  of [PromptCreateAvatarAssetAsync](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAssetAsync)  te implementeren, heb je de token-ID nodig, die je kunt openen door op de drie stippen op de miniatuur te klikken en Token-ID kopiëren  te selecteren.

 ![Dropdown voor gemaakte tokens die een optie voor Token-ID kopiëren onthult](https://prod.docsiteassets.roblox.com/assets/monetization/avatar-creation-tokens/Avatar-Creation-Token-Copy-ID.png)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
