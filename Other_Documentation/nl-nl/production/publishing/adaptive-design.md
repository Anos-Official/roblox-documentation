<!-- Source: https://create.roblox.com/docs/nl-nl/production/publishing/adaptive-design -->

Aanpassingsrichtlijnen voor ontwerp | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Game-ontwerp](/docs/nl-nl/production/game-design)
6. /
7. Je ervaring bouwen
8. /
9. [Richtlijnen voor adaptief ontwerp](/docs/nl-nl/production/publishing/adaptive-design)

# Aanpassingsrichtlijnen voor ontwerp

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Aanpassingsontwerp zorgt ervoor dat je Roblox-games er geweldig uitzien en aanvoelen op verschillende schermformaten, oriëntaties en invoertypes. Voorbij de traditionele apparaatcategorieën zoals mobiel, desktop en console, hebben de apparaten van vandaag veel dynamischere mogelijkheden, waardoor een naadloze overgang tussen verschillende invoeren en weergaven mogelijk is. Stel je een tablet voor die meerdere oriëntaties ondersteunt (landschap en portret), meerdere invoertypes (aanraking, gamepad, muis en toetsenbord) en meerdere schermformaten (natuurlijke weergave, en uitbreidend naar een grote tv).

Deze richtlijnen helpen je de beste games te leveren die intelligent zich aanpassen aan elk apparaat en invoertype om een breed publiek te bereiken. Voor meer details over workflows en API's die helpen bij het implementeren van deze richtlijnen, zie de [cross‑platform ontwikkeling](/docs/nl-nl/projects/cross-platform)  gids.

Om een vooraf gemaakte game te verkennen die de volgende aanpassingsontwerpconcepten laat zien, bekijk de [Interactiviteitsshowcase](https://www.roblox.com/games/132115384567250/) .

## [Kernprincipes](#kernprincipes)[](#kernprincipes)

Elke game is uniek, maar het volgen van een paar belangrijke principes helpt je een intuïtieve en gepolijste game te leveren aan elke speler, op elk apparaat.

1.

[Invoervloeiendheid](#invoervloeiendheid)  — Zorg ervoor dat je UI werkt met verschillende invoertypes zoals gamepad, aanraking, toetsenbord en VR-controllers. Dit omvat het wijzigen van je UI-indeling en het bieden van assistieve hints afhankelijk van het invoertype.

2.

[Responsieve indeling](#responsieve-indeling)  — Ontwerp UI-indelingen die automatisch aanpassen aan verschillende schermformaten en oriëntaties.

3.

[Dynamische grootte](#dynamische-grootte)  — Schaal UI-elementen indien nodig om te passen bij verschillende schermdimensies.

4.

[Leesbaarheid en visuele helderheid](#leesbaarheid--visuele-helderheid)  — Zorg ervoor dat alle UI-componenten, inclusief tekst en knoppen, gemakkelijk leesbaar en visueel duidelijk zijn.

### [Invoervloeiendheid](#invoervloeiendheid)[](#invoervloeiendheid)

Zorg ervoor dat je game natuurlijk aanvoelt op verschillende invoerapparaten, waaronder gamepads, muis/toetsenbord, aanraking en VR.

-

Ontwerp bedieningselementen en sneltoetsen voor meerdere invoeren  — Zorg ervoor dat elke actie in je game kan worden geactiveerd met gamepadknoppen/D-pad, sneltoetsen en aanraking. Bedieningselementen moeten visueel en functioneel focusbaar zijn voor navigatie met het richtingspad of de stick. Test elke invoermodus zodat de kern gameplay, menu's en UI toegankelijk en natuurlijk zijn, ongeacht het apparaat.

-

Bied visuele feedback per invoertype  — Werk UI-labels, prompts en tooltips bij om de actieve invoermethode weer te geven, bijvoorbeeld Druk op A  op een gamepad, Knijp  op aanraking, of Shift A  op toetsenbord. Gebruik iconen en taal die vertrouwd zijn voor de spelers van elk platform.

Muis/Toetsenbord Aanraking Gamepad

![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/Inventory-Selection-Keyboard.jpg)

### [Responsieve indeling](#responsieve-indeling)[](#responsieve-indeling)

De indeling van je game UI moet zich aanpassen aan verschillende schermformaten en oriëntaties. Op een groot computerscherm heb je veel ruimte om knoppen allemaal tegelijk weer te geven. Op een klein telefoonscherm zouden al die knoppen er echter krap en rommelig uitzien.

-

Pas indelingen aan op schermgrootte en oriëntatie  — Gebruik responsieve patronen zodat je UI zich op de juiste manier herschikt of samenvoegt. Verplaats bijvoorbeeld minder belangrijke knoppen naar een samenvouwbaar menu ("hamburger"/menu-knop) op kleine schermen, terwijl ze volledig worden weergegeven op desktops. Je game UI moet zich soepel aanpassen aan zowel landschap- als portretoriëntatie als het deze ondersteunt.

-

Implementeer indelingscomponenten die reageren op de grootte van de ouder  — Bouw UI-panelen en widgets die de grootte of positie aanpassen op basis van hun bovenliggende container. Gebruik bijvoorbeeld gesplitste weergave-indelingen waarbij zijpanelen op smalle schermen samenvouwen maar op bredere schermen uitbreiden.

Medium / Landschap Klein / Portret

![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/Responsive-Layout-Landscape.jpg)

### [Dynamische grootte](#dynamische-grootte)[](#dynamische-grootte)

Dit gaat over de grootte  van je UI-elementen, niet alleen hun positie. Je UI moet omhoog of omlaag schalen met het scherm zodat alles de juiste grootte behoudt en altijd gemakkelijk te gebruiken is.

-

Ondersteun inhoudsgestuurde grootte en automatische omwrapping  — Implementeer auto-sizing gedragingen: laat tekstvakken groeien of krimpen met inhoud, en ondersteun automatische regelomwrapping zodat labels niet overlopen of onleesbaar worden naarmate de schermgrootte verandert.

-

Exposeer en respecteer toegankelijkheid / gebruikersvoorkeuren  — Laat je UI reageren op door de gebruiker opgegeven tekst- of UI-schaalinstellingen, waarbij die instellingen direct zijn gekoppeld aan de grootte van UI-elementen zodat verhoogde [toegankelijkheidsvoorkeuren](/docs/nl-nl/production/publishing/accessibility#speler-voorkeuren)  altijd resulteren in grotere, leesbare UI.

Groot Medium Klein

![](https://prod.docsiteassets.roblox.com/assets/publishing/cross-platform/Dynamic-Sizing-Large.jpg)

### [Leesbaarheid & visuele helderheid](#leesbaarheid--visuele-helderheid)[](#leesbaarheid--visuele-helderheid)

Kunnen spelers je tekst daadwerkelijk lezen op een klein telefoonscherm of een grotere tv die ver van hen af staat? Zijn je knoppen gemakkelijk te zien tegen de achtergrond van je 3D-wereld?

-

Kies lettergroottes en stijlen voor kleine schermen  — Kies altijd lettergroottes die leesbaar zijn op mobiele apparaten, niet alleen op desktop. Test op echte apparaten en controleer of de tekst leesbaar is op de kleinste verwachte grootte. Vermijd overdreven decoratieve of dunne lettertypen.

-

Zorg voor een hoog contrast en duidelijke visuele hiërarchie  — Gebruik kleuren voor tekst en achtergronden die voldoende contrast bieden om leesbaar te zijn in verschillende in-game verlichtingsomstandigheden. Gebruik een sterke visuele hiërarchie en laat belangrijke acties en labels opvallen door middel van grootte, kleur of plaatsing.

## [Laatste gedachten](#laatste-gedachten)[](#laatste-gedachten)

Aanpassingsvermogen gaat erom spelers te ontmoeten waar ze zijn, of het nu in hun handen, op hun bureau of op het grote scherm is. Roblox-makers die met deze richtlijnen bouwen, leveren betekenisvolle, toegankelijke en leuke cross-platform games. Begin vandaag met aanpassen en laat je creaties bloeien!

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
