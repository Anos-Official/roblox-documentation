<!-- Source: https://create.roblox.com/docs/nl-nl/production/localization/translate-dynamic-content -->

Vertaal dynamische inhoud | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Lokalisatie
6. /
7. Handmatige vertalingen

# Vertaal dynamische inhoud

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt parameters  gebruiken in je [lokalisatietabel](/docs/nl-nl/production/localization/manual-translations#cloudlokalisatietabel)  wanneer slechts een deel van de weergegeven string vertaling vereist, zoals het lokaliseren van een meeteenheid na een numerieke waarde, het verwijzen naar een gebruikersnaam, of het weergeven van tijd en datum.

![](https://prod.docsiteassets.roblox.com/assets/localization/Dynamic-Content-Example-A.jpg) Een hoeveelheid in-game items weergeven.

![](https://prod.docsiteassets.roblox.com/assets/localization/Dynamic-Content-Example-B.jpg) De Roblox-gebruikersnaam van een speler in een bericht tonen.

![](https://prod.docsiteassets.roblox.com/assets/localization/Dynamic-Content-Example-C.jpg) Een hoge score weergeven met gelokaliseerde scheidingstekens.

Parameters bestaan uit een parameterwaarde  en een optionele opmaakspecifier  die tussen accolades is geplaatst.

 ![](https://prod.docsiteassets.roblox.com/assets/localization/Parameter-Diagram.png)

In het volgende voorbeeld heeft een spel de volgende vermeldingen in zijn lokalisatietabel:

| Bron | | es |
| --- | --- |
| Hallo {Player_Name}! | | Hola {Player_Name}! |
| Mijn naam is {NPC_Name} | | Me llamo {NPC_Name} |

Als een gebruiker zijn of haar locale heeft ingesteld op es , zou de vertaaloutput als volgt zijn:

| Originele in-game tekst | | Spaanse vertaling |
| Hallo new_storm! | | Hola new_storm! |
| Mijn naam is Diva Dragonslayer | | Me llamo Diva Dragonslayer |

In sommige gevallen wil je misschien opmaakspecifiers gebruiken om te bepalen hoe de parameterwaarde wordt opgemaakt in de gelokaliseerde string.

De beschikbare opmaakspecifiers zijn als volgt:

| Specifier | | Type | | Beschrijving | | Voorbeeldoutput |
| int | | nummer | | Geheel getal met optioneel negatief teken; geen duizendtallen.  | | 1234 |
| fixed | | nummer | | Twee decimalen met decimaalteken, optioneel negatief teken, en geen duizendtallen.  | | 1234.50
1234,50 |
| num | | nummer | | Twee decimalen met decimaalteken, optioneel negatief teken, en duizendtallen. | | 1.234,50
1234,50  |
| HEX | | nummer | | Geheel getal omgezet naar hex; negatief wordt omgezet naar 64-bits two's complement.  | | 3FF |
| hex | | nummer | | Zelfde als HEX, maar kleine letters. | | 3ff |
| datetime | | nummer | | UTC-timestamp als een getal naar universeel leesbaar formaat. | | 2017-10-10 13:38:10 |
| iso8601 | | nummer | | UTC-timestamp als een getal naar ISO-8601 formaat UTC-tijd. | | 2017-10-12T22:02:38Z |
| shorttime | | nummer | | UTC-timestamp naar lokaal "uur:minuut" formaat.  | | 1:45 PM
13:45 |
| shortdatetime | | nummer | | UTC-timestamp naar algemeen datum+tijd patroon met korte tijd. | | 10/10/2017 1:45 PM |
| shortdate | | nummer | | UTC-timestamp naar kort datum patroon. | | 10/10/2017
2017-10-10 |
| translate | | string | | Zoekt naar een letterlijke ** Bron**  string match in de lokalisatietabel en gebruikt beschikbare locale vertaling. | |  |

## [Vertaal substrings](#vertaal-substrings)[](#vertaal-substrings)

Gebruik de translate  specifier wanneer je een directe vertaling van je lokalisatietabel nodig hebt. De lokalisatie zoekt naar een exacte match van de parameter in de Bron-kolom van je lokalisatietabel.

In het volgende voorbeeld heeft een spel de volgende rijen in zijn lokalisatietabel:

| Bron | | es |
| Ik kom uit {Place_Name:translate}. | | Soy de {Place_Name:translate}. |
| Brazilië | | Brasil |
| Londen | | Londres |
| Duitsland | | Alemania |

Als een gebruiker zijn of haar locale heeft ingesteld op 'es', wordt de vertaaloutput als volgt weergegeven:

| Originele in-game tekst | | Spaanse vertaling |
| Ik kom uit Brazilië. | | Soy de Brasil. |
| Ik kom uit Londen. | | Soy de Londres. |
| Ik kom uit Duitsland. | | Soy de Alemania. |

## [Vertaal met nummers](#vertaal-met-nummers)[](#vertaal-met-nummers)

Je kunt een specifier gebruiken om je numerieke waarden te formatteren zodat ze passen binnen de context van je spel.

In het volgende voorbeeld heeft een spel de volgende nummergerelateerde vermeldingen in hun lokalisatietabel:

| Bron | | es |
| {race_time:fixed} seconden  | | {race_time:fixed} segundos  |
| ${1:num} cash en {2:int} juwelen  | | ${1:num} dinero y {2:int} joyas  |

Als een gebruiker zijn of haar locale heeft ingesteld op es , wordt de vertaaloutput als volgt weergegeven:

| Originele in-game tekst | | Spaanse vertaling |
| 75.202844 seconden | | 75,20 segundos |
| $2500.5 cash en 99.8 juwelen | | $2.500,50 dinero y 100 joyas |

Bij het gebruik van meerdere parameters in één vermelding, moet je ofwel alleen strings of alleen nummers gebruiken voor parameter-specifiers.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
