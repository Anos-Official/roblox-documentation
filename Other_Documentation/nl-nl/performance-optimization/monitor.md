<!-- Source: https://create.roblox.com/docs/nl-nl/performance-optimization/monitor -->

Prestaties monitoren | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Prestatieoptimalisatie](/docs/nl-nl/performance-optimization)

# Prestaties monitoren

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Het [Prestatie Dashboard](/docs/nl-nl/production/analytics/performance)  is de beste manier om de prestaties van je gepubliceerde games te monitoren. De twee tabbladen bevatten realtime prestatie-informatie voor zowel clients als servers, en je kunt datumbereiken gebruiken om de impact van je wijzigingen in de loop van de tijd te volgen.

Stel je bijvoorbeeld voor dat je net een nieuwe plek aan je game hebt toegevoegd:

1.

Je publiceert de bijgewerkte game, en uren later merk je een duidelijke stijging in het aantal clientcrashes op het Prestatie Dashboard dat lijkt samen te vallen met het geheugengebruik van de client.

2.

Je test de nieuwe plek in Studio en ziet geen problemen. Het geheugengebruik lijkt vergelijkbaar met andere plekken in je game.

3.

Je merkt op dat de gemiddelde speeltijd van spelers dramatisch is toegenomen sinds je update.

4.

Je test opnieuw, maar deze keer breng je meer tijd in de game door en houd je het geheugengebruik in de loop van de tijd beter in de gaten. Zeker, het gebruik groeit in de loop van de tijd en kan crashes veroorzaken op apparaten met lagere specificaties.

5.

Je controleert het server tabblad en merkt dat het geheugengebruik van de server ook in de loop van de tijd toeneemt. Het is nog geen probleem, maar kan binnenkort een probleem worden.

6.

Onder het Geheugen  tabblad van de Ontwikkelaarsconsole, in de PlaceScriptMemory  uitsplitsing, merk je dat het geheugengebruik voor een van je nieuwe scripts toeneemt elke keer dat je met enkele belangrijke objecten in de wereld interactie hebt. Het script draait zowel op de client als op de server.

7.

Je controleert het script, dat wat gebruikersgegevens aan een grote tabel toevoegt, maar nooit de gegevens opruimt—het groeit oneindig.

8.

Je lost het probleem op, publiceert de bijgewerkte game, en het aantal clientcrashes keert terug naar de vorige waarde.

Naast het Prestatie Dashboard kun je verbinding maken met de [DataModel.ServerLowMemoryWarning](/docs/nl-nl/reference/engine/classes/DataModel#ServerLowMemoryWarning)  signaal vanuit een server script om een vroegtijdige waarschuwing te krijgen wanneer het geheugengebruik van een live server te hoog wordt, waardoor je code de kans krijgt om geheugen vrij te maken voordat er een crash optreedt.

Het vergelijken van het Prestatie Dashboard met andere dashboards kan je helpen om prestatieverbeteringen (of regressies) te correleren met zakelijke metrics voor een completer idee van hoe een presterende game je winst beïnvloedt. Voor meer informatie, zie [Analytics](/docs/nl-nl/production/analytics) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
