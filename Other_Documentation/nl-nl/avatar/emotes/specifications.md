<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/emotes/specifications -->

Emote specificaties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)
4. /
5. Animations
6. /
7. Emotes

# Emote specificaties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Emotes bestaan uit een [Animation](/docs/nl-nl/reference/engine/classes/Animation)  object met de [Animation.AnimationId](/docs/nl-nl/reference/engine/classes/Animation#AnimationId)  eigenschap ingesteld op de asset ID van je animatievolgorde. Het [Animation](/docs/nl-nl/reference/engine/classes/Animation)  object is de enige component die vereist is om een emote naar de Marketplace te uploaden, omdat animaties geen meshes, texturen of andere 3D kunstcomponenten vereisen.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Explorer.png) Animation  object in het Explorer venster.

![](https://prod.docsiteassets.roblox.com/assets/avatar/avatar-emotes/Animation-Properties.png) AnimationId  eigenschap in het Properties venster.

## [Animatievereisten](#animatievereisten)[](#animatievereisten)

Emotes moeten voldoen aan de volgende vereisten voordat je ze naar de Marketplace uploadt, anders kunnen ze de validatie niet doorstaan:

-

Emotes moeten minder dan 10 seconden zijn.

-

De gewrichtsroot van het karakter mag niet te ver van zijn startpositie bewegen.

-

De snelheid van de beweging mag een bepaalde drempel niet overschrijden om misbruik van teleportatie te voorkomen (gemeten op basis van frame-voor-frame).

-

Animatiegegevens moeten verwijzen naar een [standaard R15 rig](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs) .

Emotes voor [geavanceerde R15 rigs](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  zijn momenteel in een gesloten bèta. Voor meer informatie, zie de [DevForum aankondiging](https://devforum.roblox.com/t/upload-and-publish-for-emotes-with-additional-joints-is-now-open/4710932) .

-

Animatie moet afkomstig zijn van een CurveAnimation . Voor informatie over het converteren van animatiegegevens, zie [Emotes importeren - Genereer asset ID](/docs/nl-nl/avatar/emotes/import#genereer-asset-id) .

-

Animaties moeten voldoen aan de [Community Standards](https://en.help.roblox.com/hc/en-us/articles/203313410-Roblox-Community-Standards)  en [Marketplace beleidsregels](/docs/nl-nl/marketplace/marketplace-policy)  van Roblox.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
