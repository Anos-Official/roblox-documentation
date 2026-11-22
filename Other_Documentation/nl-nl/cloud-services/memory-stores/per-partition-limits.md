<!-- Source: https://create.roblox.com/docs/nl-nl/cloud-services/memory-stores/per-partition-limits -->

Partities en gegevensdistributie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Clouddiensten](/docs/nl-nl/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Geheugenopslag](/docs/nl-nl/cloud-services/memory-stores)

# Partities en gegevensdistributie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De MemoryStores API slaat gegevens op in * partities* , zodat het de doorvoer over gegevensstructuren kan schalen. Gesorteerde kaarten en wachtrijen bevinden zich elk op één partitie, terwijl hash-kaarten automatisch items over meerdere partities verspreiden. Deze pagina legt uit hoe die toewijzing werkt.

## [Partities](#partities)[](#partities)

De MemoryStores API slaat gegevens op in * partities* , wat gewoon onderverdelingen van opslag zijn. Wanneer je een item naar een geheugenopslag schrijft, wordt dat item op precies één partitie opgeslagen. Partities worden volledig beheerd door de MemoryStores API; je hoeft ze zelf niet te beheren.

## [Partitietoewijzing](#partitietoewijzing)[](#partitietoewijzing)

De opslag van partities verschilt afhankelijk van de gegevensstructuur waarop een item wordt opgeslagen. Voor gesorteerde kaarten en wachtrijen is elke gegevensstructuur toegewezen aan een enkele partitie.

Neem bijvoorbeeld een kermisspel met een gesorteerde kaart genaamd PlayerScores  en een wachtrij genaamd PlayerLine  van spelers die wachten om het spel te spelen:

 ![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Per-Partition-Limits-1.png)

In tegenstelling tot gesorteerde kaarten en wachtrijen, krijgen hash-kaarten meerdere partities toegewezen, en worden gegevens automatisch over deze partities verdeeld. Als je een hash-kaart genaamd Prizes  zou toevoegen, zouden de partities er als volgt uitzien:

 ![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Per-Partition-Limits-3.png)

Let op hoe de hash-kaart op alle partities bestaat, en elke partitie een subset van items heeft.

Voor de verzoeklimieten die van toepassing zijn op elke partitie en op individuele hash-kaart sleutels, zie [Per-partitie limieten](/docs/nl-nl/cloud-services/memory-stores#per-partitie-limieten) . Voor richtlijnen over het verspreiden van de belasting over sleutels en gegevensstructuren, zie [beste praktijken](/docs/nl-nl/cloud-services/memory-stores/best-practices) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
