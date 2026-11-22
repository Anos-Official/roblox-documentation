<!-- Source: https://create.roblox.com/docs/nl-nl/resources/the-mystery-of-duvall-drive/stream-in-immersion -->

Stream in onderdompeling | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Voorbeelden en projecten](/docs/nl-nl/samples)
4. /
5. [Het mysterie van Duvall Drive](/docs/nl-nl/resources/the-mystery-of-duvall-drive)

# Stream in onderdompeling

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox Studio is een krachtige engine waarmee games op een breed scala aan platforms kunnen worden gemaakt, maar zelfs sommige high-end telefoons kunnen moeite hebben om al onze content tegelijk te laden. Om dit aan te pakken, hebben we [streaming](/docs/nl-nl/workspace/streaming)  gebruikt om het hoogste kwaliteitsniveau mogelijk te maken op een breed scala aan apparaten. Streaming stelde ons in staat om al onze content op één plek te maken en dynamisch kleinere delen van de content die zichtbaar zijn voor de gebruiker te laden.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/streaming-in-immersion/content-streaming.png) Streaming ingeschakeld op de werkruimte zelf, met standaardinstellingen

## [Technische overwegingen](#technische-overwegingen)[](#technische-overwegingen)

Bij het inschakelen van streaming in je game zijn er een paar dingen om te overwegen om ervoor te zorgen dat je game goed draait en dat je de voordelen van de streamingfunctie maximaliseert:

1.

Zijn er scripts of elementen die afhankelijk zijn van een ander stuk content?  Als dat zo is, kunnen een of meer van je afhankelijkheden op bepaalde momenten niet worden geladen.

2.

Zijn er scripts die de werkruimte scannen wanneer de game begint?  Klantscripts mogen niet afhankelijk zijn van het vinden van alle instanties die ze nodig hebben op het moment dat een game begint en dit is geen aanbevolen praktijk.

3.

Lijdt je game visueel als sommige content niet op het juiste moment wordt weergegeven?  Er zijn verschillende technieken en trucs om een [streaming-vriendelijke omgeving](#streaming-vriendelijk-niveauontwerp)  te creëren en manieren om [perspectief](#speel-met-perspectief)  in je voordeel te gebruiken.

Bij het maken van The Mystery of Duvall Drive kwamen we alle drie deze problemen tegen en konden we ze omzeilen door een combinatie van zorgvuldige scriptontwerpen en slim toegepaste set dressing en wereldindeling. Wanneer je met streaming in je eigen game werkt, onthoud dan dat je je streaming min/max afstand kunt afstemmen op wat het beste bij je game past en een verscheidenheid aan [zeer aanpasbare opties](/docs/nl-nl/workspace/streaming#streaming-eigenschappen)  kunt aanpassen.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/streaming-in-immersion/64-max-distance.png) Streaming met een maximale afstand van 64 stud eenheden.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/streaming-in-immersion/1024-max-distance.png) Streaming met een maximale afstand van 1024 stud eenheden.

## [Streaming-vriendelijk niveauontwerp](#streaming-vriendelijk-niveauontwerp)[](#streaming-vriendelijk-niveauontwerp)

Om een onderdompelende omgeving te creëren, moeten spelers voortdurend omringd zijn door de wereld die we voor hen hebben gebouwd. Bij het gebruik van instance streaming moesten we ervoor zorgen dat spelers geen onverwachte content zouden zien, zoals het zien van de "einde van de wereld" als er geen visuele assets in hun instance streaming bereik waren geladen.

Aangezien verre bomen achter het huis en andere blokkering geometrie zoals heuvels en bergen buiten bereik zouden zijn, moesten we een oplossing vinden om te voorkomen dat spelers de horizon zagen en hun onderdompeling doorbraken. Om dit aan te pakken, hebben we nabijgelegen blokkering geometrie toegevoegd langs alle gebieden van het pad van de speler en het pad ontworpen dat zou kronkelen om effectief het gebrek aan content in de verte te verbergen. We plaatsten blokkering geometrie op een manier die ervoor zorgt dat de speler op elk punt op het pad omringd zou zijn door streambare visuele assets. Dit kwam goed overeen met ons oorspronkelijke ontwerp om een kronkelige oprit te creëren en is een prime voorbeeld van doordacht niveauontwerp dat esthetische en technische toepassingen combineert.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/streaming-in-immersion/winding-path.png) De speler begint omringd door nabijgelegen bomen en struiken om te helpen verbergen dat verre content nog niet is geladen. Het kronkelige pad houdt veel van de content verborgen totdat spelers dichtbij genoeg zijn om de asset te laden.

## [Speel met perspectief](#speel-met-perspectief)[](#speel-met-perspectief)

Er zijn enkele gevallen waarin content die een speler zou verwachten te zien van ver weg te ver van de camera is, zoals onze [storm in de lucht](/docs/nl-nl/resources/the-mystery-of-duvall-drive/develop-a-moving-world#cre%C3%ABer-de-storm) . We wilden dat spelers dit grote fenomeen konden zien, maar het zou de onderdompeling doorbreken als de luchtstorm niet bestond wanneer de speler te ver weg was om de asset te laden. Het zou ook schokkend zijn om een grote asset plotseling te zien laden wanneer de speler dichtbij genoeg bij een object kwam dat ze verder weg hadden moeten zien. We probeerden dit te minimaliseren door met perspectief te spelen en ervoor te zorgen dat de modellen in de lucht groot genoeg waren om binnen de grenzen van de streamingafstand van de speler te vallen.

 ![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/streaming-in-immersion/perspective-house.png)

Een andere oplossing was om de verticale hoogte van de bomen rondom de speler te verhogen wanneer ze niet dichtbij genoeg bij de storm waren. Dit loste de situatie op waarin de speler te ver weg was om de asset te laden, maar nog steeds zou verwachten deze in hun gezichtsveld te zien. Grote bomen zijn gebruikelijk in onze Pacific Northwest-instelling, en deze aanpassing hielp het probleem op te lossen met minimale concessies aan onze esthetiek en ontwerp.

![](https://prod.docsiteassets.roblox.com/assets/resources/mystery-of-duvall-drive/streaming-in-immersion/perspective-treelines.png) Bomenrijen helpen om een deel van de content die nog niet is geladen te verbergen.

[Volgende](/docs/nl-nl/resources/the-mystery-of-duvall-drive/develop-a-moving-world)[Vorige](/docs/nl-nl/resources/the-mystery-of-duvall-drive/immersive-narrative)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
