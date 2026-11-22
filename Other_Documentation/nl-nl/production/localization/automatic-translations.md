<!-- Source: https://create.roblox.com/docs/nl-nl/production/localization/automatic-translations -->

Automatische vertaling | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Lokalisatie
6. /
7. Automatische vertaling

# Automatische vertaling

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Automatische vertaling  is een tool die automatisch tekststrings in je spel verzamelt en vertaalt. Deze tool is beschikbaar voor elk spel en stelt je in staat om onmiddellijk vertaalde strings in je spel weer te geven en je potentiële publiek te vergroten.

## [Hoe automatische vertaling werkt](#hoe-automatische-vertaling-werkt)[](#hoe-automatische-vertaling-werkt)

Automatische vertaling werkt door eerst [strings te verzamelen](#automatische-tekstvastlegging-inschakelen)  die binnen het spel worden aangetroffen, hetzij tijdens het testen of het spelen. Zodra deze strings zijn vastgelegd, vertaalt Roblox de strings automatisch in de lokalisatietabel van je spel.

Na het verzamelen van deze strings kun je [vertalingen inschakelen](#vertalingen-inschakelen)  voor je spel, zodat de vastgelegde strings automatisch worden weergegeven voor gebruikers die hun standaardtaalinstellingen hebben ingesteld op de vertaalde taal.

Automatische vertaling biedt alleen geautomatiseerde vertalingen voor lege invoeren in de lokalisatietabel en overschrijft geen bestaande vertalingen, inclusief eventuele [handmatige vertalingen](/docs/nl-nl/production/localization/manual-translations)  die door een ontwikkelaar of vertaler zijn gemaakt. Als je bijvoorbeeld handmatig een vertaling voor een invoer wist, gaat de tool ervan uit dat je die invoer niet wilt vertalen.

## [Automatische tekstvastlegging inschakelen](#automatische-tekstvastlegging-inschakelen)[](#automatische-tekstvastlegging-inschakelen)

Automatische Tekstvastlegging (ATC) verzamelt tekststrings van UI-elementen in je spel en voegt ze toe aan je vertaaltafel. Wanneer ingeschakeld, voegt de ATC-tool tekst toe van UI-elementen die door gebruikers binnen je spel of tijdens Studio-testen worden aangetroffen.

ATC evalueert in de loop van de tijd welke strings aan je vertaaltafel moeten worden toegevoegd, dus het kan enkele dagen duren voordat nieuwe strings in de Translator Portal verschijnen nadat gebruikers ze hebben aangetroffen. Als je wilt dat strings onmiddellijk worden vastgelegd, kun je het [Studio-tekstvastlegproces](#tekstvastlegging-in-studio)  gebruiken.

ATC verzamelt alleen tekstobjecten die [AutoLocalize](/docs/nl-nl/reference/engine/classes/GuiBase2d#AutoLocalize)  ingeschakeld hebben. Als je niet wilt dat ATC een bepaalde tekststring verzamelt, zoals een naam of unieke tekstinvoer, schakel dan deze eigenschap uit. Houd er rekening mee dat voor [TextBox](/docs/nl-nl/reference/engine/classes/TextBox) -objecten alleen [PlaceholderText](/docs/nl-nl/reference/engine/classes/TextBox#PlaceholderText)  wordt vastgelegd; de veronderstelling is dat strings in [Text](/docs/nl-nl/reference/engine/classes/TextBox#Text)  door de speler zijn ingevoerd.

Om Automatische Tekstvastlegging in te schakelen:

1.

Navigeer in de lokalisatie-instellingen naar Instellingen .

2.

Schakel Vastleggen van tekst vanuit de ervaring UI terwijl gebruikers spelen  in.

 ![De sectie Lokalisatie-instellingen die de schakelaar voor Vastleggen van tekst vanuit de ervaring UI terwijl gebruikers spelen benadrukt.](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Enable-ATC.png)

ATC kan sommige spelobjecten niet vastleggen. Deze objecten vereisen mogelijk speciale behandeling met [lokalisatiescripts](/docs/nl-nl/production/localization/localize-with-scripting) . De huidige uitzonderingen zijn:

-

De standaard Roblox-leaderboards en chat

-

Items of gereedschappen die door een speler worden bezeten

-

Afbeeldingen met ingebedde tekst

-

Badge-namen en beschrijvingen die van het platform zijn gehaald

-

Pass-namen en beschrijvingen die van het platform zijn gehaald

### [Tekstvastlegging in Studio](#tekstvastlegging-in-studio)[](#tekstvastlegging-in-studio)

Er kunnen situaties zijn waarin je onmiddellijk strings naar je vertaaltafel moet vastleggen. In deze gevallen kun je de tekstvastlegtool in Studio gebruiken om strings vast te leggen tijdens het playtesten. Deze strings worden binnen 1–2 minuten aan de lokalisatietabel toegevoegd nadat ze zijn aangetroffen.

Om tekstvastlegging in Studio in te schakelen:

1.

Open in Studio Lokalisatietools  vanuit het Venster  ⟩ Lokalisatie -menu.

2.

Schakel Automatische Tekstvastlegging  in.

 ![De lokalisatietool in Studio toont de ingeschakelde ATC-schakelaar.](https://prod.docsiteassets.roblox.com/assets/localization/ATC-Studio-Enabled.png)

De tekstvastlegging in Studio blijft ingeschakeld als je playtesten start en stopt binnen dezelfde Studio-sessie, maar moet opnieuw worden ingeschakeld wanneer je een nieuwe Studio-sessie start.

### [Automatische opschoning](#automatische-opschoning)[](#automatische-opschoning)

ATC controleert ook je spel op strings die niet meer bestaan, zoals gebruikersnamen of strings die verband houden met een vorig evenement. Standaard verwijdert de tool deze verouderde invoeren wanneer deze worden geïdentificeerd. Alleen automatisch verzamelde strings met automatische vertalingen worden verwijderd; strings die handmatig zijn toegevoegd of die handmatige vertalingen hebben, worden niet beïnvloed.

Als je niet wilt dat ATC je lokalisatietabel opruimt, navigeer dan naar je lokalisatie-instellingen en schakel de tweede ATC-schakelaar uit:

 ![De sectie Lokalisatie-instellingen die de schakelaar voor het inschakelen van Roblox om verouderde invoeren te verwijderen benadrukt.](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Enable-ATC-Auto.png)

## [Vertalingen inschakelen](#vertalingen-inschakelen)[](#vertalingen-inschakelen)

Zodra strings zijn vastgelegd in je lokalisatietabel, volg je deze stappen om vertaalde inhoud in te schakelen:

1.

Navigeer op de lokalisatiepagina van je spel naar Instellingen .

2.

Schakel Gebruik vertaalde inhoud  in.

 ![De sectie Lokalisatie-instellingen die de schakelaar voor het inschakelen van Roblox om vertaalde inhoud in het spel te gebruiken benadrukt.](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Use-Translated-Content.png)

3.

Navigeer naar het tabblad Talen .

4.

Schakel alle ondersteunde talen in voor automatische vertalingen.

-

Ervaringsinformatie  verwijst naar de naam en beschrijving van je spel.

-

Ervaringsstrings en producten  verwijst naar de tekst die binnen je spel verschijnt.

 ![De sectie Lokalisatie Talen die de per-taal schakelaars voor automatische vertaling benadrukt.](https://prod.docsiteassets.roblox.com/assets/localization/Portal-Automatic-Translation.png)

### [Automatische vertaalquota](#automatische-vertaalquota)[](#automatische-vertaalquota)

Roblox heeft initiële en maandelijkse quota voor automatische vertaling. De initiële quota bepaalt hoeveel stringinvoeren je kunt vertalen wanneer je je spel voor de eerste keer lokaliseert. Nadat je de initiële quota hebt gebruikt, komen alle volgende vertalingen uit je maandelijkse quota, die elke maand opnieuw wordt ingesteld.

Je kunt je gebruik van de automatische vertaalquota volgen op de lokalisatiepagina van je spel:

 ![De sectie Lokalisatie Talen die de Automatische Vertaalquota bovenaan de pagina weergeeft, inclusief de datum van de maandelijkse quota-vernieuwing.](https://prod.docsiteassets.roblox.com/assets/localization/Automatic-Translation-Quotas.png)

Quota worden berekend op een per-teken  en per-taal basis . Bijvoorbeeld, het automatisch vertalen van de brontekst "hello" in 10 verschillende talen telt als 5×10 (50) tekens voor je quota.

### [Automatische vertaalupdates](#automatische-vertaalupdates)[](#automatische-vertaalupdates)

Naarmate de automatische vertaaltool verbetert, kunnen nauwkeurigere vertalingen beschikbaar komen voor bestaande strings. Wanneer deze updates beschikbaar komen, ververst Roblox alle automatische vertalingen. Automatische vertaalupdates verschijnen in je vertaalgeschiedenis.

 ![Een vertaalgeschiedenislogboek wordt onderaan elke vertaalinvoer weergegeven.](https://prod.docsiteassets.roblox.com/assets/localization/Update-Log.png)

Als je een specifieke vertaling hebt die je ongewijzigd wilt laten, kun je de invoer vergrendelen om ervoor te zorgen dat deze niet door updates wordt beïnvloed.

 ![Een 'Vergrendel vertaling voor automatische updates'-schakelaar is toegankelijk onder het vertaalinvoerveld in elke vertaalinvoer.](https://prod.docsiteassets.roblox.com/assets/localization/Lock-Translations.png)

Door een invoer te vergrendelen, keur je de vertaling goed en maak je het een handmatige invoer. Dit betekent dat het niet zal worden beïnvloed door automatische vertaalupdates, inclusief updates met betrekking tot veiligheid. Als in de toekomst wordt ontdekt dat de vertaling in strijd is met het beleid, blijft je spel onderhevig aan moderatie.

Standaard zijn handmatig toegevoegde strings en strings met handmatige vertalingen vergrendeld. Als je een invoer ontgrendelt, wordt deze beïnvloed door zowel automatische vertaalupdates als ATC als deze is ingeschakeld. Als je een nieuwe automatische vertaling wilt genereren voor een eerder gewijzigde of gewiste vertaling, ontgrendel dan de invoer.

## [Ondersteunde talen](#ondersteunde-talen)[](#ondersteunde-talen)

Roblox ondersteunt automatische vertaling tussen de onderstaande talen. Momenteel gaat Roblox Translate er altijd van uit dat bronteksten in de [brontaal](/docs/nl-nl/production/localization#setting-source-language)  van het spel zijn.

| Momenteel ondersteunde talen voor automatische vertaling |
| --- | --- |
| Arabisch |
| Chinees (Vereenvoudigd) |
| Chinees (Traditioneel) |
| Engels |
| Frans |
| Duits |
| Hindi |
| Indonesisch |
| Italiaans |
| Japans |
| Koreaans |
| Pools |
| Portugees |
| Russisch |
| Spaans |
| Thais |
| Turks |
| Vietnamees |

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
