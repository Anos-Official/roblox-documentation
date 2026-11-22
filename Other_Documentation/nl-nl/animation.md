<!-- Source: https://create.roblox.com/docs/nl-nl/animation -->

Animatie in Roblox | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Animatie](/docs/nl-nl/animation)

# Animatie in Roblox

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Animatie  is het proces van het toepassen van beweging op je personages, objecten en omgevingen om een boeiend en dynamisch spel te creëren. Hoewel er veel manieren zijn om objecten te laten bewegen en interageren, verwijst animatie in Roblox doorgaans naar het aanpassen van een expressieve beweging van een specifiek personage of een groep onderdelen.

Animatie kan worden toegepast op elk Roblox-onderdeel of een groep onderdelen. Verschillende soorten objecten kunnen gebruikmaken van verschillende animatiefuncties. De volgende zijn de algemene categorieën van animeerbare objecten:

-

Eenvoudige objecten , zoals een basisonderdeel, kunnen alleen animaties aanbrengen in de enkele positie- of rotatie-eigenschap van het onderdeel.

-

Rigs , of onderdelen die zijn verbonden door gewrichten zoals [AnimationConstraints](/docs/nl-nl/reference/engine/classes/AnimationConstraint)  of [Bones](/docs/nl-nl/reference/engine/classes/Bone) , kunnen positionele en roterende bewegingen tussen hun gewrichten articuleren, zoals ellebogen en polsen. Gemonteerde modellen kunnen profiteren van animatiefuncties zoals [inverse kinematica](#inverse-kinematica)  om snel en programmatisch beweging toe te passen als reactie op omgevingen en gebeurtenissen.

-

[Standaard](/docs/nl-nl/avatar/character-bodies/specifications#standaard-r15-rigs)  en [geavanceerde](/docs/nl-nl/avatar/character-bodies/specifications#geavanceerde-r15-rigs)  R15 rigs kunnen animaties gebruiken uit de animatiebibliotheek van Roblox en andere bewegingsfuncties, ongeacht of het een speler- of niet-spelerpersonagemodel is.

## [Animatie-editor](#animatie-editor)[](#animatie-editor)

De [Animatie-editor](/docs/nl-nl/animation/editor)  stelt je in staat om aangepaste animaties te ontwerpen en te publiceren op rigs. Je kunt de gewrichten die individuele secties van een rig verbinden verplaatsen om poses te creëren, en de editor animeert de rig soepel van pose naar pose.

## [Inverse kinematica](#inverse-kinematica)[](#inverse-kinematica)

Je kunt [inverse kinematica](/docs/nl-nl/animation/inverse-kinematics)  API's gebruiken om automatisch animaties en poses te creëren op basis van omgevings- en externe gebeurtenissen. Met inverse kinematica kun je procedureel verschillende animatie-evenementen genereren, zoals het laten volgen van het hoofd van een personage door een vogel die in de lucht vliegt, of het automatisch laten reiken van de arm van een personage naar een deurknop wanneer deze in de buurt is.

## [Animatie-evenementen](#animatie-evenementen)[](#animatie-evenementen)

Een [animatie-evenement](/docs/nl-nl/animation/events)  is een specifiek punt in een animatie dat een actie activeert. Je kunt animatie-evenementmarkeringen definiëren over de tijdlijn van de [Animatie-editor](/docs/nl-nl/animation/editor) , en vervolgens [AnimationTrack:GetMarkerReachedSignal()](/docs/nl-nl/reference/engine/classes/AnimationTrack#GetMarkerReachedSignal)  gebruiken om die markeringen te detecteren terwijl de animatie wordt afgespeeld om specifieke acties uit te voeren, zoals het afspelen van een geluidseffect telkens wanneer de voet van de gebruiker de grond raakt.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
