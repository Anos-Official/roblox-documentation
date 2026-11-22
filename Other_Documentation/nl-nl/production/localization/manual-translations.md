<!-- Source: https://create.roblox.com/docs/nl-nl/production/localization/manual-translations -->

Handmatige vertalingen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. Lokalisatie
6. /
7. Handmatige vertalingen

# Handmatige vertalingen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Wanneer je je inhoud lokaliseert, moet je mogelijk handmatig je lokalisatietabel aanpassen om de vertaalkwaliteit te verbeteren, context toe te voegen voor wanneer een vertaling moet worden gebruikt, of zelfs ongebruikte vertalingen te verwijderen.

Of je nu vertalingen automatisch hebt vastgelegd of handmatig hebt toegevoegd, alle vertalingen worden opgeslagen in de [cloudlokalisatietabel](#cloudlokalisatietabel) . Om de lokalisatietabel te wijzigen, kun je de volgende acties uitvoeren:

-

[Voeg broninhoud toe](/docs/nl-nl/production/localization/add-source-content)  aan de tabel, hetzij handmatig, hetzij automatisch.

-

[Verwijder inhoud](/docs/nl-nl/production/localization/remove-content)  uit de tabel, zoals gebruikersnamen of andere strings die niet vertaald moeten worden.

-

[Voeg vertalingen toe](/docs/nl-nl/production/localization/add-translations)  aan invoeren in de tabel voor alle ondersteunde talen die in je game zijn ingesteld.

Voordat je wijzigingen aanbrengt in je tabel, is het belangrijk om elk veld in de [cloudlokalisatietabel](#cloudlokalisatietabel)  te begrijpen om problemen of conflicten te voorkomen.

Gebruikers met automatische vertalingen ingeschakeld in hun Roblox-accountinstellingen zien nog steeds alle handmatig toegevoegde vertalingen in je game. Zie [Instelling voor gebruikers](/docs/nl-nl/production/localization#gebruikersinstelling)  voor meer informatie.

## [Cloudlokalisatietabel](#cloudlokalisatietabel)[](#cloudlokalisatietabel)

De lokalisatietabel is de referentie voor alle vertalingen binnen je game. Het is belangrijk om elk veld van de lokalisatietabel te begrijpen om effectief invoeren toe te voegen of te wijzigen.

Wanneer de tabel is gevuld, bevat deze alle gebruikersgerichte inhoud binnen je game die vertaling vereist, samen met eventuele beschikbare vertalingen voor specifieke talen. Je kunt [broninhoud toevoegen](/docs/nl-nl/production/localization/add-source-content)  en [vertalingen toevoegen](/docs/nl-nl/production/localization/add-translations)  aan de Cloudlokalisatietabel of [een .csv -versie van je tabel downloaden en uploaden](/docs/nl-nl/production/localization/add-translations#met-bestandsupload) . Alleen gebruikers die bewerkingsrechten voor een game hebben, kunnen toegang krijgen tot de lokalisatietabel van een game.

De lokalisatietabel heeft de volgende kolommen:

| Kolom | | Beschrijving |
| --- | --- |
| Bron | | Een verplicht veld dat de in-game bronteksten bevat die zijn verzameld door automatische tekstvastlegging of handmatige invoer. Dit is de brontekst die je wilt vertalen naar andere talen. Brontekst is vereist voordat je een vertaling kunt toevoegen en meerdere invoeren kunnen dezelfde Bron delen, zolang ze unieke Context -velden hebben.

Als je dynamische inhoud vertaalt, zoals gedeeltelijke strings, moet het Bronveld een van de ondersteunde parameterformaten volgen die zijn beschreven in [Vertaal dynamische inhoud](/docs/nl-nl/production/localization/translate-dynamic-content) . |
| Context | |

Een optioneel veld dat een verwijzing bevat naar het in-game object dat de brontekst bevat. Je kunt het Context-veld gebruiken om aan te geven welke vertaling Roblox op een object weergeeft. Zie [Context Overrides gebruiken](/docs/nl-nl/production/localization/localize-with-scripting#use-context-overrides)  voor meer details.

 Het systeem voor automatische tekstvastlegging vult het Context-veld niet automatisch in en vult in plaats daarvan het Locatie -veld met vergelijkbare informatie.

 |
| Voorbeeld | | Een optioneel veld dat aanvullende informatie over een invoer bevat die je mogelijk als aantekeningen voor vertalers wilt opnemen. Je kunt dit veld gebruiken om handmatige vertalers te laten zien waar en wanneer je game een specifieke vertaling gebruikt. |
| Sleutel | |

Een optioneel veld voor het implementeren van [sleutel-gebaseerde lookup](/docs/nl-nl/reference/engine/classes/Translator#FormatByKey)  bij het gebruik van lokalisatie-API's. Je kunt dit veld leeg laten als je geen [lokalisatie-API's](/docs/nl-nl/production/localization/localize-with-scripting)  gebruikt voor specifieke taken, zoals het lokaliseren van afbeeldingen en geluiden.

 |
| Locatie | |

Een veld dat automatisch wordt ingevuld door het [Automatische Tekstvastleggings](#automatic-text-capture)  systeem. Het bevat een verwijzing naar het in-game object dat de brontekst bevat, wat je of een vertaler kan helpen te identificeren waar de string in je game wordt aangetroffen. Dit veld is ofwel leeg of wordt ingevuld door het Automatische Tekstvastleggingsysteem. Om je eigen objectverwijzing handmatig toe te voegen, gebruik je het Context -veld.

 |

Sommige velden in de lokalisatietabel moeten uniek zijn om onverwacht gedrag te voorkomen. Houd rekening met het volgende:

-

Voor alle invoeren mag het Bron -veld niet leeg zijn.

-

Geen twee invoeren kunnen dezelfde Bron en Context -waarden delen.

-

Geen twee invoeren kunnen dezelfde Sleutel  delen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
