<!-- Source: https://create.roblox.com/docs/nl-nl/generative-AI -->

Spellen met Generatieve AI | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Platform](/docs/nl-nl/get-started)
4. /
5. Richtlijnen en beleid

# Spellen met Generatieve AI

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox biedt een verscheidenheid aan AI-gestuurde tools en diensten om creatie en creativiteit in het spel te verbeteren. Wanneer je generatieve AI in je spellen opneemt, of je nu gebruikmaakt van door Roblox geleverde modellen of oplossingen van derden, moet je ervoor zorgen dat deze integraties veilig blijven, voldoen aan Roblox's [Gemeenschapsnormen](https://about.roblox.com/community-standards)  en transparantie bieden aan je gebruikers.

Deze pagina schetst de richtlijnen, regels en beste praktijken voor het gebruik van generatieve AI in Roblox-spellen.

## [Moderatie](#moderatie)[](#moderatie)

Om een veilige omgeving te behouden, moet alle inhoud, inclusief inhoud die is gemaakt door of gebruikmaakt van generatieve AI, voldoen aan Roblox's Gemeenschapsnormen.

Bij het gebruik van Roblox API's, zoals [GenerationService](/docs/nl-nl/reference/engine/classes/GenerationService)  en [TextGenerator](/docs/nl-nl/reference/engine/classes/TextGenerator) : Alle inhoudsinputs en -outputs gaan door [moderatie](https://about.roblox.com/newsroom/2025/07/roblox-guard-advancing-safety-for-llms-with-robust-guardrails) , inclusief tekstfiltering, beeldbeoordeling en assetbeoordeling. Inhoud die als in strijd met de regels wordt geïdentificeerd, wordt niet aan gebruikers aangeboden.

-

Gebruikers zullen geen gevolgen ondervinden voor in strijd met de regels zijnde outputs die zijn gegenereerd als reactie op niet-in strijd met de regels zijnde inputs.

Bij het gebruik van tools van derden : Jij bent verantwoordelijk voor de inhoud die aan gebruikers wordt geleverd, zelfs als deze AI-gegenereerd is. Om ervoor te zorgen dat je spel voldoet aan de veiligheidsnormen van Roblox, moet je ervoor zorgen dat:

-

Outputs voldoen aan Roblox's Gemeenschapsnormen.

-

Inputs en outputs de door Roblox opgelegde veiligheidsmaatregelen niet omzeilen. Bijvoorbeeld, tekstinputs en -outputs moeten door [TextChatService](/docs/nl-nl/reference/engine/classes/TextChatService)  gaan.

## [Inhoudsrijpheidsbeoordelingen](#inhoudsrijpheidsbeoordelingen)[](#inhoudsrijpheidsbeoordelingen)

Als je spel spelers toestaat om op enige manier met een generatief AI-model te interageren dat een reactie van het model uitlokt, zoals interacties die tekstchat, spraakchat, afbeeldingen, 3D-generaties en avatarbeweging omvatten, moet je dit bekendmaken binnen de [Inhoudsbeoordelingsvragenlijst](/docs/nl-nl/production/promotion/content-ratings) .

Hoewel het enkel opnemen van een AI-component in je spel de inhoudsbeoordelingen van je spel niet beïnvloedt, moeten spellen met uitgebreide AI-interacties de juiste Beperkte  inhoudsrijpheidsbeoordeling bevatten, zodat ze alleen beschikbaar zijn voor het juiste publiek.

### [Beperkte interacties](#beperkte-interacties)[](#beperkte-interacties)

Voor spellen zonder de Beperkte  inhoudsrijpheidsbeoordeling, moeten modeloutputs voldoen aan de onderliggende inhoudsrijpheidsclassificatie van het spel.

Bij het gebruik van door Roblox geleverde AI-tools, zoals [GenerationService](/docs/nl-nl/reference/engine/classes/GenerationService)  en [TextGenerator](/docs/nl-nl/reference/engine/classes/TextGenerator) :

-

Voor alle spellen instrueren we ons model om zich te houden aan een All Ages-inhoudsbeoordeling en outputs te vermijden die een descriptor vereisen, zoals Horror-elementen.

-

Voor spellen met milde geweld of hogere inhoudsdescriptors, kunnen modellen anderszins conforme wapens genereren.

Bij het gebruik van tools van derden :

-

Je moet ervoor zorgen dat outputs overeenkomen met de inhoudsrijpheidsbeoordeling van je spel.

### [Uitgebreide interacties](#uitgebreide-interacties)[](#uitgebreide-interacties)

Spellen met uitgebreide interacties  zijn die welke bedoeld zijn om, of gebruikt kunnen worden om, een continue conversatie aan te gaan met chatbot-achtige generatieve AI-functies. Je spel wordt als een spel met uitgebreide AI-interacties beschouwd als het voldoet aan een van de volgende criteria:

-

Het belangrijkste thema of doel van het spel is dat spelers continu interageren met een generatieve AI-bot of -personage zonder tijdslimiet.

-

Bijvoorbeeld, een spel met de titel "Jouw AI-vriend" waarvan het enige doel is dat gebruikers een continue conversatie aangaan met een AI-gestuurde niet-speler karakter (NPC).

-

De AI-component omvat cross-sessie geheugen, zodat het spel de context van eerdere interacties van een gebruiker met AI opslaat en deze laadt bij volgende sessies.

-

Bijvoorbeeld, een spel dat voornamelijk gericht is op gameplay en één AI-gestuurde NPC heeft waarmee gebruikers slechts enkele minuten kunnen interageren. Echter, wanneer het spel opnieuw wordt geladen en de NPC opnieuw wordt benaderd, kan het model terugverwijzen naar eerdere gesprekken met de gebruiker.

Als je spel uitgebreide interacties bevat, moet je "Ja" antwoorden op de vraag over Uitgebreide AI in de Inhoudsbeoordelingsvragenlijst. Omdat deze spellen mogelijk niet geschikt zijn voor jongere gebruikers, hebben ze een Beperkte inhoudsrijpheidsbeoordeling nodig, zodat ze niet toegankelijk zijn voor gebruikers onder de 18 jaar.

Voor meer informatie over de regels en richtlijnen voor inhoudsbeoordelingen, zie [Inhoudsbeoordelingen](/docs/nl-nl/production/promotion/content-ratings) .

## [Openbaarmakingen](#openbaarmakingen)[](#openbaarmakingen)

Wanneer je generatieve AI-componenten in je spel opneemt, moet je ervoor zorgen dat zichtbare openbaarmakingen aan gebruikers worden gepresenteerd, waaronder:

-

Aan het begin van elke interactie, en gedurende de sessie, moeten gebruikers een melding zien dat hun conversatie met AI is. Bijvoorbeeld:

"* Dit is een AI-gestuurde conversatie, geen menselijke. Het kan fouten maken.* "

-

Gebruikers moeten worden doorverwezen naar gezaghebbende bronnen als ze medische of professionele adviezen zoeken. Specifiek, als een gebruiker gedachten van zelfbeschadiging of tekenen van een geestelijke gezondheidscrisis uitdrukt, moeten AI-modellen hen aanmoedigen om ondersteuning te zoeken. Bijvoorbeeld:

"* Als jij of een geliefde het moeilijk hebben, neem dan contact op met gekwalificeerde geestelijke gezondheidsprofessionals of ondersteuningsdiensten die de hulp kunnen bieden die je nodig hebt. Informatie en links naar bronnen en crisis-hotlines zijn te vinden in Roblox's Gemeenschapsnormen.* "

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
