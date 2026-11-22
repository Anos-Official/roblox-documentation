<!-- Source: https://create.roblox.com/docs/nl-nl/matchmaking/scoring -->

Server scoring | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Matchmaking](/docs/nl-nl/matchmaking)

# Server scoring

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

## [De scoringsformule](#de-scoringsformule)[](#de-scoringsformule)

Servers worden gescoord met behulp van een gewogen somformule. Er zijn vier onderdelen van deze formule:

-

[Attributen](#attributen) , dit zijn gegevens die spelers en servers beschrijven, zoals de leeftijd van de speler of de bezetting van de server.

-

[Signalen](#signalen) , die attributen omzetten in getallen tussen 0 en 1.

-

[Gewichten](#gewichten) , die de relatieve belangrijkheid van signalen beschrijven.

-

De [server score](#server-score) , die de compatibiliteit van de server met de toetredende speler meet.

De toetredende speler wordt gekoppeld aan de server met de hoogste server score.

### [Attributen](#attributen)[](#attributen)

Attributen zijn gegevens die spelers en servers beschrijven. De waarde van een attribuut kan een getal of een string zijn. Wanneer de waarde van een attribuut een string is, wordt het een categorisch attribuut genoemd. Wanneer de waarde van een attribuut een getal is, wordt het een numeriek attribuut genoemd.

Voor een volledige lijst van alle beschikbare Roblox-attributen, zie [Bestaande attributen](/docs/nl-nl/matchmaking/attributes-and-signals#bestaande-attributen) . Voor meer informatie over aangepaste attributen, zie [Aangepaste attributen](/docs/nl-nl/matchmaking/attributes-and-signals#aangepaste-attributen) .

##### Voorbeeld: Categorische en numerieke attributen

| Categorische attributen |
| --- | --- |
| Heeft Vrienden  is een categorisch attribuut omdat de waarde de string "waar" is wanneer er een voorkeurs speler op deze server is, en "onwaar" wanneer er geen voorkeurs spelers op deze server zijn. |
| Taal  is een categorisch attribuut omdat de waarde de taalinstelling van de speler is, zoals "Japans". |
| Numerieke attributen |
| Leeftijd  is een numeriek attribuut omdat de waarde de leeftijd van de speler is. |
| Bezetting  is een numeriek attribuut omdat de waarde het aantal spelers dat momenteel op deze server is. |

### [Signalen](#signalen)[](#signalen)

Signalen transformeren attribuutwaarden in getallen tussen 0 en 1, genaamd signaal scores. Een signaal score van 1 voorspelt een hoge compatibiliteit van de speler, terwijl een signaal score van 0 een lage compatibiliteit voorspelt. Afhankelijk van het attribuut kunnen transformaties verschillende aggregaties, vergelijkingen en normalisaties omvatten.

Voor een volledige lijst van bestaande Roblox-signalen, zie [Bestaande signalen](/docs/nl-nl/matchmaking/attributes-and-signals#bestaande-signalen) . Voor meer informatie over aangepaste signalen, zie [Aangepaste signalen](/docs/nl-nl/matchmaking/attributes-and-signals#aangepaste-signalen) .

##### Voorbeeld: Twee servers met verschillende signaal scores

De volgende tabel berekent de bezettingssignaal scores voor twee verschillende servers met een capaciteit voor 8 spelers:

|  | | Spelers op server | | Bezettingsscore |
| Server A | | 2 | | 2/8 = 0.25 |
| Server B | | 6 | | 6/8 = 0.75 |

De bezettingssignaal scores geven Server B een hogere score en beschouwen het als een betere keuze voor de toetredende speler.

### [Gewichten](#gewichten)[](#gewichten)

Het gewicht van een signaal beschrijft het belang van dat signaal ten opzichte van andere signalen. Een hoger gewicht verhoogt de bijdrage van het signaal aan de server score. De waarde na het vermenigvuldigen van een signaal score met zijn gewicht wordt een gewogen signaal  genoemd.

Signalen kunnen geen negatieve gewichten hebben. Als het gewicht van een signaal 0 is, wordt dat signaal niet in aanmerking genomen voor scoring.

##### Voorbeeld: Het wegen van de bezettingsscore

De volgende tabel berekent gewogen bezettingssignaal scores voor een plaats met een capaciteit voor 8 spelers en een bezettingssignaal gewicht van 2:

|  | | Spelers op server | | Bezettingsscore | | Gewogen bezettingsscore |
| Server A | | 2 | | 2/8 = 0.25 | | 0.25 * 2 = 0.5 |
| Server B | | 6 | | 6/8 = 0.75 | | 0.75 * 2 = 1.5 |

##### Voorbeeld: Twee configuraties met verschillende gewichten

Verschillende gewichten kunnen ook matchmaking doen kiezen voor verschillende servers. De volgende tabel berekent de server scores van twee servers met verschillende matchmaking configuraties. Configuratie 2 heeft een hoger gewicht voor zijn bezettingssignaal, en Server A heeft een vriend van de toetredende speler erin.

|  | |  | | Vrienden | | Bezetting | |  |
|  | |  | | Gewicht | | Score | | Gewicht | | Score | | Totaalscore |
| Config 1 | | Server A | | 1 | | 1 | | 5 | | 0.25 | | 1 * 1 + 5 * 0.25 = 2.25 |
| Server B | | 1 | | 0 | | 5 | | 0.75 | | 1 * 0 + 5 * 0.75 = 3.75 |
| Config 2 | | Server A | | 3 | | 1 | | 5 | | 0.25 | | 3 * 1 + 5 * 0.25 = 4.25 |
| Server B | | 3 | | 0 | | 5 | | 0.75 | | 3 * 0 + 5 * 0.75 = 3.75 |

### [Server score](#server-score)[](#server-score)

De server score wordt berekend met de volgende gewogen somformule, die de gewogen signaal scores van een server optelt:

ServerScore = WeightedSignalScore 1 + WeightedSignalScore 2 + … + WeightedSignalScore n \text{ServerScore} = \text{WeightedSignalScore}_1 + \text{WeightedSignalScore}_2 + \ldots + \text{WeightedSignalScore}_n ServerScore = WeightedSignalScore 1 ​ + WeightedSignalScore 2 ​ + … + WeightedSignalScore n ​

ServerScore = Weight 1 × SignalScore 1 + Weight 2 × SignalScore 2 + … + Weight n × SignalScore n \phantom{\text{ServerScore}} = \text{Weight}_1 \times \text{SignalScore}_1 + \text{Weight}_2 \times \text{SignalScore}_2 + \ldots + \text{Weight}_n \times \text{SignalScore}_n ServerScore = Weight 1 ​ × SignalScore 1 ​ + Weight 2 ​ × SignalScore 2 ​ + … + Weight n ​ × SignalScore n ​

### [Matchmaking configuraties](#matchmaking-configuraties)[](#matchmaking-configuraties)

Een matchmaking configuratie is de set van signalen en gewichten die worden gebruikt om servers van een plaats te scoren. Standaard worden alle servers van alle plaatsen gescoord door de standaard configuratie van Roblox, wat betekent dat je geen instellingen hoeft aan te passen of in te schakelen om deze te gebruiken.

De standaard configuratie van Roblox omvat de volgende signalen en gewichten:

| Signaal | | Gewicht |
| Vrienden | | 15 |
| Latentie | | 3 |
| Tekstchat | | 3 |
| Bezetting | | 2 |
| Speelgeschiedenis | | 2 |
| Taal | | 2 |
| Leeftijd | | 1 |
| Stemchat | | 1 |
| Apparaat type | | 0 |

In de standaard configuratie van Roblox is het gewicht van het Vrienden signaal groter dan de som van de gewichten van elk ander signaal. Dit betekent dat, als beschikbaar, de toetredende speler altijd wordt gekoppeld aan servers met vrienden (of spelers op hetzelfde IP-adres) erin.

Het Apparaat type signaal bestaat in de standaard configuratie maar heeft een gewicht van 0, dus het beïnvloedt de matchmaking beslissingen niet. Je kunt dit gewicht aanpassen wanneer je [matchmaking aanpast](/docs/nl-nl/matchmaking/customize-matchmaking) .

Voor meer informatie over elk Roblox signaal, zie [Bestaande signalen](/docs/nl-nl/matchmaking/attributes-and-signals#bestaande-signalen) .

## [Geavanceerde concepten](#geavanceerde-concepten)[](#geavanceerde-concepten)

De volgende zijn meer geavanceerde concepten over het matchmaking proces.

### [Normalisatie](#normalisatie)[](#normalisatie)

Signalen normaliseren attribuutwaarden tot getallen tussen 0 en 1. Numerieke signalen kunnen worden genormaliseerd door elk positief getal, genaamd de normaliserende factor . Als de genormaliseerde waarde groter is dan 1, wordt deze naar beneden geklapt tot 1.

##### Voorbeeld: Ontwerpen van het Leeftijd signaal

Het Leeftijd signaal meet het verschil tussen de gemiddelde leeftijd van spelers op de server en de leeftijd van de toetredende speler.

ageDifference = ∣ avgServerAge − joiningPlayerAge ∣ \text{ageDifference} = |\text{avgServerAge} - \text{joiningPlayerAge}|ageDifference = ∣ avgServerAge − joiningPlayerAge ∣

Servers met leeftijdsverschillen van meer dan 25 worden allemaal als even onverenigbaar met de speler beschouwd. Bijvoorbeeld, een leeftijdsverschil van 25 is niet slechter voor een speler dan een leeftijdsverschil van 26, dus beide waarden zouden de signaal score naar 0 moeten brengen. In dit geval wordt 25 beschouwd als de normaliserende factor.

normAgeDifference = min ⁡ (1 , ∣ avgServerAge − joiningPlayerAge ∣ / 25 ) \text{normAgeDifference} = \min(1, |\text{avgServerAge} - \text{joiningPlayerAge}| / 25) normAgeDifference = min (1 , ∣ avgServerAge − joiningPlayerAge ∣/25 )

De signaal score is omgekeerd gerelateerd aan het leeftijdsverschil, wat betekent dat de signaal score hoger is wanneer het leeftijdsverschil kleiner is.

ageDifferenceSignalScore = 1 − normAgeDifference \text{ageDifferenceSignalScore} = 1 - \text{normAgeDifference} ageDifferenceSignalScore = 1 − normAgeDifference

De volgende tabel toont Leeftijd signaal scores met twee verschillende normaliserende factoren:

| Leeftijd | | Normaliserende factor: 100 | | Normaliserende factor: 25 |
| 50 | | 0.5 | | 0 |
| 25 | | 0.75 | | 0 |
| 12 | | 0.88 | | 0.52 |
| 5 | | 0.95 | | 0.8 |
| 0 | | 1 | | 1 |

Het signaal met een normaliserende factor van 25 beschouwt de leeftijdsverschillen van 5 jaar en 12 jaar als verder uit elkaar. Kleinere normaliserende factoren hebben het effect van het versterken van marginale verhogingen of dalingen in leeftijdsverschil.

### [Gewicht magnitudes](#gewicht-magnitudes)[](#gewicht-magnitudes)

Een gewicht geeft het belang van een signaal aan ten opzichte van andere signalen in een configuratie. De relatieve grootten van gewichten bepalen het belang van signalen, niet hun absolute grootten.

##### Voorbeeld: Relatieve vs absolute grootte

De onderstaande tabel berekent de server scores van twee servers met twee verschillende matchmaking configuraties. Configuratie 5 en Configuratie 6 hebben bezettingsgewichten die hoger zijn dan hun respectieve vrienden gewichten. Server A heeft een vriend van de toetredende speler erin.

|  | |  | | Vrienden | | Bezetting | |  |
|  | |  | | Gewicht | | Score | | Gewicht | | Score | | Totaalscore |
| Config 5 | | Server A | | 10.000 | | 1 | | 15.000 | | 0.25 | | 10.000 * 1 + 15.000 * 0.25 = 13.750 |
| Server B | | 10.000 | | 0 | | 15.000 | | 0.75 | | 10.000 * 0 + 15.000 * 0.75 = 11.250 |
| Config 6 | | Server A | | 0.01 | | 1 | | 0.05 | | 0.25 | | 0.01 * 1 + 0.05 * 0.25 = 0.0225 |
| Server B | | 0.01 | | 0 | | 0.05 | | 0.75 | | 0.01 * 0 + 0.05 * 0.75 = 0.0375 |

Server A wint met Configuratie 5 terwijl Server B wint met Configuratie 6. Dit komt omdat het bezettingsgewicht van Configuratie 5 slechts 1,5 keer zo hoog is als het vrienden gewicht, terwijl het bezettingsgewicht van Configuratie 6 5 keer zo hoog is als het vrienden gewicht.

Ondanks de verschillen in absolute grootten, prioriteert Configuratie 6 bezetting meer dan vrienden in vergelijking met Configuratie 5.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
