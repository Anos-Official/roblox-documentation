<!-- Source: https://create.roblox.com/docs/nl-nl/physics/units -->

Roblox-eenheden | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Fysica](/docs/nl-nl/physics)

# Roblox-eenheden

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Dit artikel beschrijft de fysieke eenheden van Roblox en hoe ze worden omgezet naar metrische eenheden. Het begrijpen van eenheden is nuttig wanneer je met fysica werkt, zoals in de volgende voorbeelden:

-

Het afstemmen van lineaire/hoeksnelheden, krachten, momenten, stijfheid en demping van [mechanische beperkingen](/docs/nl-nl/physics/mechanical-constraints)  en [verplaatsingsbeperkingen](/docs/nl-nl/physics/mover-constraints) .

-

Het aanpassen van de dichtheid van [aangepaste materialen](/docs/nl-nl/parts/materials#aangepaste-materialen) .

## [Eenheid conversies](#eenheid-conversies)[](#eenheid-conversies)

Primaire Eenheden Afgeleide Eenheden Zwaartekracht Fysieke Limieten

In het algemeen kun je de conversies in de volgende tabel gebruiken om de primaire eenheden van Roblox voor tijd, lengte en massa te relateren aan hun metrische tegenhangers.

| Eenheid | | Roblox | | Metrisch |
| --- | --- |
| Tijd | | 1 seconde \text{1 seconde} 1 seconde | | 1 seconde \text{1 seconde} 1 seconde |
| Lengte | | 1 stud \text{1 stud} 1 stud | | 28 cm \text{28 cm} 28 cm |
| Massa | | 1 RMU \text{1 RMU} 1 RMU * | | 21.952 kg \text{21.952 kg} 21.952 kg |

* RMU = Roblox Massa Eenheid

## [Eenheid consistentie](#eenheid-consistentie)[](#eenheid-consistentie)

Intern gebruikt de Roblox-fysica-engine geen eenheid conversies. Je bent vrij om je eigen eenheid interpretaties voor studs (lengte) en RMU's (massa) te definiëren, maar deze moeten op een consistente manier door het spel worden gebruikt. Bijvoorbeeld, als je besluit dat één stud gelijk is aan één voet (30.483 cm), impliceert de eenheidsdichtheid van water dat een RMU gelijk is aan 62.4 lbs (28.3 kg):

1 (g/cm³) × (30.48³ cm³/ft³) = \text{1 (g/cm³)} × \text{(30.48³ cm³/ft³)} = 1 (g/cm³) × (30.48³ cm³/ft³) =
 28,317 (g/ft³) × (0.00220462 lbs/g) = \text{28,317 (g/ft³)} × \text{(0.00220462 lbs/g)} = 28,317 (g/ft³) × (0.00220462 lbs/g) =
 62.4 (lbs/ft³) = \text{62.4 (lbs/ft³)} = 62.4 (lbs/ft³) =
 1 (RMU/stud³) \text{1 (RMU/stud³)} 1 (RMU/stud³)

Over het algemeen wordt aanbevolen om standaard Roblox-eenheden te gebruiken, omdat dit ervoor zorgt dat een spel in alle scenario's werkt zoals verwacht, zoals compatibiliteit met VR-besturingselementen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
