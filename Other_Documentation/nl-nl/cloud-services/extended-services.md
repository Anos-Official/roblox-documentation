<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/extended-services -->

Uitgebreide Diensten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)

# Uitgebreide Diensten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Uitgebreide Diensten is een oplossing die je in staat stelt om het gebruik van diensten en betalingen te beheren buiten de standaardlimieten van Roblox. Het omvat datastores, geheugenopslag, tekst-naar-spraak, spraak-naar-tekst en rekenkracht.

## [Geschiktheidseisen](#geschiktheidseisen)[](#geschiktheidseisen)

Om Uitgebreide Diensten te gebruiken, moet je Roblox-account:

-

[ID-geverifieerd](/docs/nl-nl/production/publishing/account-verification#verify-through-government-id)  zijn en 18 jaar of ouder zijn.

-

Gevestigd zijn in een [ondersteund land](#ondersteunde-landen) .

-

Een geldig e-mailadres hebben dat eraan gekoppeld is.

-

Momenteel niet geband of gemodereerd zijn.

-

De [servicevoorwaarden](https://en.help.roblox.com/hc/articles/37967848292500)  accepteren en naleven.

Voor groepsaccounts hoeft alleen de groepsbeheerder aan de geschiktheidseisen te voldoen.

## [Ontgrendel Uitgebreide Diensten](#ontgrendel-uitgebreide-diensten)[](#ontgrendel-uitgebreide-diensten)

Als je aan alle [geschiktheidseisen](#geschiktheidseisen)  voldoet, kun je de installatie van Uitgebreide Diensten voltooien door je accountgegevens en betalingsinformatie in te voeren. Voor groepsbezit games kan alleen de groepsbeheerder Uitgebreide Diensten ontgrendelen en het spel daarop onboarden.

Om Uitgebreide Diensten te ontgrendelen en te gebruiken:

1.

Ga naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) , ga naar Creations  en selecteer een spel.

2.

Ga naar Uitgebreide Diensten .

3.

Als je je accountgegevens en betalingsinformatie nog niet hebt ingevoerd, klik dan op Voeg ontbrekende informatie toe  op de bovenste banner.

1.

Voer je accountinformatie in. De velden Accounttype , Belasting-ID-type  en Belasting-ID  zijn optioneel.

-

Je kunt ook naar Financiën  ⟩ Accountinformatie  onder de sectie Uitgebreide Diensten  gaan om je accountinformatie te beheren. Je hoeft verder niets anders op deze pagina bij te werken.

2.

Klik op Volgende .

3.

Voer een betaalmethode in. Je kunt een nieuwe betaalmethode invoeren of kiezen uit de beschikbare betaalopties die al aan je Roblox-account zijn gekoppeld.

-

Je kunt ook naar Financiën  ⟩ Betalingen  gaan om nieuwe betaalmethoden toe te voegen, of naar Financiën  ⟩ Facturering  om een nieuwe standaard betaalmethode in te stellen.

4.

Klik op Opslaan .

##### Accountstatus

Je Uitgebreide Diensten-account kan zich in een van de volgende statussen bevinden:

| Status | | Beschrijving | | Vereiste actie |
| Normaal | | Je kunt alle functies van Uitgebreide Diensten gebruiken. | | Er is geen actie vereist. |
| --- | --- |
| Achterstallig | | Je account is achterstallig omdat je automatische betaalmethode is mislukt. Roblox biedt een graceperiode van zeven dagen  voordat je Uitgebreide Diensten-account wordt opgeschort. | | Wijzig je betaalmethode en probeer een handmatige betaling opnieuw, of wacht tot Roblox opnieuw probeert je betaalmethode te incasseren na het verstrijken van de graceperiode. |
| Opgeschort | | Je kunt geen betaalde Uitgebreide Diensten gebruiken. Je kunt echter nog steeds diensten met standaardlimieten gebruiken. | | Los je geschiktheidseisen op, voeg een geldige betaalmethode toe, of betaal handmatig het achterstallige saldo op je account. |

## [Een dienst inschakelen](#een-dienst-inschakelen)[](#een-dienst-inschakelen)

Om een dienst in te schakelen:

1.

Ga naar Uitgebreide Diensten .

2.

Zet de schakelaar aan voor de dienst die je wilt inschakelen.

3.

Voer een maandelijks budget in voor elke toepasselijke bron onder de dienst. Het minimale maandelijkse budget dat je kunt instellen is $0,50 USD.

Je betaalmethode wordt aan het einde van de maand in rekening gebracht wanneer er een factuur wordt gegenereerd, of wanneer je gebruik $10 USD bereikt, afhankelijk van wat het eerst komt.

Je kunt het maandelijkse budget van een dienst op elk moment verhogen of verlagen. Je dienst wordt automatisch beperkt als je je budget verlaagt tot een bedrag onder je huidige gebruik tot nu toe, of als je het budget dat je hebt ingesteld overschrijdt.

Roblox stelt je per e-mail op de hoogte wanneer je gebruik 80% van je budget bereikt, en vervolgens opnieuw wanneer het 100% bereikt.

### [Uitgebreide Diensten voor Rekenkracht](#uitgebreide-diensten-voor-rekenkracht)[](#uitgebreide-diensten-voor-rekenkracht)

Elke game-server krijgt een standaard hoeveelheid CPU, die toeneemt met elke speler die zich aansluit. Uitgebreide Diensten voor Rekenkracht  verdubbelt de per-speler CPU die de servers van je game ontvangen.

De overgrote meerderheid van de games op Roblox heeft geen voordeel van deze dienst, maar games met zware server-side fysica of die uitgebreid gebruikmaken van [serverautoriteit](/docs/nl-nl/projects/server-authority)  raken de bestaande limieten. Om te zien of je game kan profiteren van Uitgebreide Diensten voor Rekenkracht :

-

Controleer de [serverheartbeat](/docs/nl-nl/performance-optimization/identify#server-compute)  op aanhoudende dalingen onder de 60 FPS.

-

Onderzoek het CPU-kerngebruik op het [Prestatie-dashboard](/docs/nl-nl/production/analytics/performance#server-charts) .

Voordat je betaalt voor meer CPU, probeer de [werkbelasting van je servers te verminderen](/docs/nl-nl/performance-optimization/improve) .

## [Beheer facturering](#beheer-facturering)[](#beheer-facturering)

Om toegang te krijgen tot het factureringsdashboard van Uitgebreide Diensten:

1.

Ga naar Financiën  ⟩ Facturering .

2.

Selecteer het tabblad Cloudservices  om het volgende weer te geven:

-

Je openstaande saldo, inclusief kosten tot nu toe deze maand

-

Je factureringsgeschiedenis, inclusief alle factureringsactiviteiten van Uitgebreide Diensten in al je games

Voor een gedetailleerde uitsplitsing van je huidige openstaande saldo kosten, klik op Bekijk details  naast je betaalmethode. Voor een gedetailleerde factuur van een eerdere factuur, klik op Bekijk factuur  onder Factureringsgeschiedenis .

## [Prijzen van diensten](#prijzen-van-diensten)[](#prijzen-van-diensten)

Zie de volgende tabel voor de prijzen van Uitgebreide Diensten:

| Dienst | |  | | Standaard | | Uitgebreid |
| [Geheugenopslag](https://create.roblox.com/docs/cloud-services/memory-stores) | | Verzoeken | | 1000 + (CCU × 120) verzoeken per minuut | | $0.003 / 1M verzoeken |
|  | | Opslag | | 64 KB + (CCU × 1.2 KB) | | $0.10 / GB per uur¹ |
| [Tekst-naar-spraak](https://create.roblox.com/docs/audio/objects#text-to-speech) | | Verzoeken | | 1 + (CCU × 6) verzoeken per minuut | | $5.00 / 1M verzoeken |
| [Spraak-naar-tekst](https://create.roblox.com/docs/audio/objects#speech-to-text) | | Verzoeken | | 1 + (CCU × 5) verzoeken per minuut | | $1 / 1M verzoeken |
| [Standaard datastores](https://create.roblox.com/docs/cloud-services/data-stores) | | Haal op | | 250 + (CCU * 40) verzoeken per minuut | | $0.08 / 1M verzoeken |
|  | | Stel in | | 250 + (CCU * 20) verzoeken per minuut | | $0.80 / 1M verzoeken |
|  | | Lijst | | 10 + (CCU * 2) verzoeken per minuut | | $0.60 / 1M verzoeken |
|  | | Verwijder | | 100 + (CCU * 40) verzoeken per minuut | | $0.80 / 1M verzoeken |
| [Geordende datastores ](https://create.roblox.com/docs/cloud-services/data-stores) | | Haal op | | 250 + (CCU * 40) verzoeken per minuut | | $0.08 / 1M verzoeken |
|  | | Stel in | | 250 + (CCU * 20) verzoeken per minuut | | $0.25 / 1M verzoeken |
|  | | GetSorted | | 100 + (CCU * 2) verzoeken per minuut | | $0.32 / 1M verzoeken |
|  | | Verwijder | | 100 + (CCU * 40) verzoeken per minuut | | $0.25 / 1M verzoeken |
| [Data store opslag ](https://create.roblox.com/docs/cloud-services/data-stores) | | Opslag | | 100 MB + (1 MB * Levenslange Spelers) GB per maand | | $0.12 / GB per maand |
| [Rekenkracht ](https://create.roblox.com/docs/production/analytics/performance) | | CPU-kernen | | Eerste 100K speeluren per maand gratis (wanneer ingeschreven voor Uitgebreide Diensten voor Rekenkracht) | | $0.001 / speeluur² |

 ¹ GB per uur = het opslagverbruik vermenigvuldigd met de tijd. Bijvoorbeeld, 100 GB-uren kan gelijkstaan aan "100 GB × 1 uur" of "200 GB × 0.5 uur".  ² Uitgebreide Diensten voor Rekenkracht worden gefactureerd op basis van hoe lang de functie ingeschakeld blijft, gemeten in minuten speelduur. Omdat het inschakelen van de functie extra rekenkracht voor je game reserveert, worden kosten in rekening gebracht wanneer de functie actief is, zelfs als de extra rekenkracht niet volledig wordt verbruikt. Speeluren worden berekend als de som van alle spelerssessieduur. Bijvoorbeeld, als 10.000 gebruikers elk 1 uur spelen, komt dat neer op 10.000 speeluren, wat resulteert in $10 aan kosten boven de inbegrepen maandelijkse toelage van 100.000 speeluren. Deze limieten en prijzen zijn alleen van toepassing op games die zijn ingeschreven voor Uitgebreide Diensten voor Rekenkracht. Games die zich niet inschrijven blijven onbeperkte speeluren ontvangen onder de huidige standaardlimieten zonder extra kosten.

## [Ondersteunde landen](#ondersteunde-landen)[](#ondersteunde-landen)

Uitgebreide Diensten zijn beschikbaar in de volgende landen:

| Land |
| Australië | | Duitsland | | Polen |
| Oostenrijk | | Hongkong | | Portugal |
| België | | Hongarije | | Roemenië |
| Brazilië | | Ierland | | Singapore |
| Bulgarije | | Italië | | Slowakije |
| Canada | | Kazachstan | | Slovenië |
| Chili | | Letland | | Zuid-Afrika |
| Kroatië | | Litouwen | | Zuid-Korea |
| Cyprus | | Maleisië | | Spanje |
| Tsjechië | | Malta | | Zweden |
| Denemarken | | Mexico | | Zwitserland |
| Estland | | Nederland | | Thailand |
| Finland | | Nieuw-Zeeland | | Verenigd Koninkrijk |
| Frankrijk | | Noorwegen | | Verenigde Staten |
| Georgië | | Peru | |  |

## [Aanvullende lokalisaties voor deze pagina](#aanvullende-lokalisaties-voor-deze-pagina)[](#aanvullende-lokalisaties-voor-deze-pagina)

Voor aanvullende, gelokaliseerde versies van deze pagina die niet beschikbaar zijn in de taalkeuzelijst van de site, zie de volgende links:

-

[Bulgaars (български)](https://create.roblox.com/docs/bg-bg/cloud-services/extended-services)

-

[Kroatisch (hrvatski)](https://create.roblox.com/docs/hr-hr/cloud-services/extended-services)

-

[Tsjechisch (čeština)](https://create.roblox.com/docs/cs-cz/cloud-services/extended-services)

-

[Deens (dansk)](https://create.roblox.com/docs/da-dk/cloud-services/extended-services)

-

[Nederlands (Nederlands)](https://create.roblox.com/docs/nl-nl/cloud-services/extended-services)

-

[Estisch (eesti)](https://create.roblox.com/docs/et-ee/cloud-services/extended-services)

-

[Fins (suomi)](https://create.roblox.com/docs/fi-fi/cloud-services/extended-services)

-

[Grieks (Ελληνικά)](https://create.roblox.com/docs/el-gr/cloud-services/extended-services)

-

[Hongaars (magyar)](https://create.roblox.com/docs/hu-hu/cloud-services/extended-services)

-

[Iers (Gaeilge)](https://create.roblox.com/docs/ga-ie/cloud-services/extended-services)

-

[Lets (latviešu)](https://create.roblox.com/docs/lv-lv/cloud-services/extended-services)

-

[Litouws (lietuvių)](https://create.roblox.com/docs/lt-lt/cloud-services/extended-services)

-

[Maltees (Malti)](https://create.roblox.com/docs/mt-mt/cloud-services/extended-services)

-

[Portugees - Portugal (português)](https://create.roblox.com/docs/pt-pt/cloud-services/extended-services)

-

[Roemeens (română)](https://create.roblox.com/docs/ro-ro/cloud-services/extended-services)

-

[Slowaaks (slovenčina)](https://create.roblox.com/docs/sk-sk/cloud-services/extended-services)

-

[Sloveens (slovenščina)](https://create.roblox.com/docs/sl-si/cloud-services/extended-services)

-

[Zweeds (svenska)](https://create.roblox.com/docs/sv-se/cloud-services/extended-services)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
