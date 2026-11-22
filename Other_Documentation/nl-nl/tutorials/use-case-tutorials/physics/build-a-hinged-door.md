<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/use-case-tutorials/physics/build-a-hinged-door -->

Bouw een scharnierdeur | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Meer informatie](/docs/nl-nl/learn)

# Bouw een scharnierdeur

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Roblox's fysicasysteem stelt je in staat om bewegende mechanismen te construeren, zoals deuren, draaiende platforms en zelfs voertuigen met behulp van constraints . Een swingdeur kan bijvoorbeeld worden gebouwd met de [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint) .

## [Deurinstelling](#deurinstelling)[](#deurinstelling)

Begin met het maken van onderdelen voor de deur en de bevestigingen. Bevestigingen  zijn waar het ene object met het andere kan verbinden. Deze bevestigingen zullen later worden gebruikt om de deur met een scharnier aan het frame te verbinden.

1.

Maak twee onderdelen met namen zoals Deur  en DeurFrame .

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints-showDoorCreated.jpg)

2.

Selecteer DeurFrame . In het Eigenschappen -venster, schakel Geankerd  in zodat het niet beweegt.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_selectAnchored.png)

3.

In de Explorer , zweef over DeurFrame  en voeg een nieuwe Bevestiging  toe. Herhaal hetzelfde om een bevestiging aan de Deur  toe te voegen.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_attachmentsCreated.png)

4.

Hernoem de bevestigingen om aan te geven waar ze aan zijn bevestigd, zoals DeurBevestiging  en FrameBevestiging .

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_attachmentsRenamed.png)

## [Verplaats de bevestigingen](#verplaats-de-bevestigingen)[](#verplaats-de-bevestigingen)

Nieuwe bevestigingen worden in het midden van een onderdeel gemaakt. Om met de deur te kunnen werken, moeten de twee bevestigingen worden verplaatst zodat ze naar elkaar toe wijzen.

1.

Om constraints en bevestigingen te bekijken, schakel Toon Constraint Details  in via het Weergave -menu van Studio.

2.

In de Explorer , selecteer FrameBevestiging .

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_selectFrameAttachment.png)

3.

Druk op F  om op de bevestiging te focussen en zoom in indien nodig. Gebruik vervolgens de Verplaats -tool om de bevestiging op het oppervlak van het deurframe te positioneren, gericht naar de deur.

Het is het beste om bevestigingen zo te positioneren dat ze precies op elkaar zijn uitgelijnd. In dit geval kunnen niet-uitgelijnde bevestigingen ervoor zorgen dat de deur verkeerd swingt.

Voor nauwkeurige positionering, gebruik ** Snap to Grid**  met stappen die geschikt zijn voor de grootte van het onderdeel. Als alternatief kun je de positie van de bevestiging in het Eigenschappen -venster bewerken.

4.

Herhaal hetzelfde om DeurBevestiging  te verplaatsen. Je bevestigingen moeten op het oppervlak zijn gepositioneerd, gericht naar hun tegenhanger.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_showAttachementsMoved.jpg)** Links** : FrameBevestiging / ** Rechts** : DeurBevestiging

## [Draai de bevestigingen](#draai-de-bevestigingen)[](#draai-de-bevestigingen)

De oriëntatie van een bevestiging beïnvloedt hoe een constraint kan bewegen. Voor de deur moeten beide bevestigingen worden gedraaid zodat het scharnier naar links en rechts swingt, zoals bij een standaarddeur.

1.

Hover op het deurframe over FrameBevestiging . Let op de gele pijl . Deze pijl, de as , bepaalt de rotatie van het scharnier.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_showAttachmentAxis.jpg)

Afhankelijk van het ** DeurFrame** -object kan de as in een andere richting wijzen. Bijvoorbeeld, een scharnier dat aan de bevestiging hierboven is toegevoegd, zou draaien rond de gele pijl, zoals in de video hieronder.

2.

Voor nauwkeurige rotatie, schakel rotatiesnapping in de werkbalk van Studio in door Draaien  in te schakelen en de waarde in te stellen op 90 .

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_snapRotate.png)

3.

Gebruik de Draai -tool om beide  gele bevestigingen naar boven  te richten. Als je assen al verticaal zijn, is er geen actie nodig.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_primaryAxis.jpg)

## [Voeg de constraint toe](#voeg-de-constraint-toe)[](#voeg-de-constraint-toe)

Vergeet niet, constraints zijn een manier om twee bevestigingen te verbinden zodat ze op een specifieke manier kunnen bewegen. Deze deur zal een [HingeConstraint](/docs/nl-nl/reference/engine/classes/HingeConstraint)  gebruiken, een veelvoorkomende constraint die objecten langs de assen van twee bevestigingen draait.

1.

Onder DeurFrame , maak een nieuwe HingeConstraint .

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_showCreateHingeConstraint.png)

2.

Zoek in de eigenschappen van de constraint naar Attachment0 . Klik op het lege vak rechts van de eigenschap en klik vervolgens in de Explorer  op DeurBevestiging .

3.

Herhaal hetzelfde proces door Attachment1  te verbinden met FrameBevestiging . De eigenschappen zouden er als volgt uit moeten zien.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_attachmentsConnected.png)

4.

Test het project door met je karakter tegen de deur te lopen.

Je kunt de volgende problemen tegenkomen tijdens het testen:

Onderdelen bewegen niet:

-

Zorg ervoor dat je deur niet is geankerd.

-

Zorg ervoor dat de beweging van de deur niet wordt geblokkeerd door terrein of nabijgelegen onderdelen.

Deur swingt niet zoals verwacht:

-

Zorg ervoor dat de as van elke bevestiging naar boven wijst (zie [Bevestigingen Draaien](#draai-de-bevestigingen) ).

## [Pas de deur aan](#pas-de-deur-aan)[](#pas-de-deur-aan)

De deur kan momenteel voorbij het deurframe swing. Dit kan worden opgelost door de scharnier limieten  aan te passen.

1.

Zoek in de eigenschappen voor HingeConstraint  naar LimitsEnabled  en schakel deze in. Wanneer deze actief is, kun je de rotatielimieten van het scharnier instellen.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_limitsEnabled.png)

2.

Om ervoor te zorgen dat dit correct is georiënteerd, selecteer DeurBevestiging  en gebruik de draaigereedschap zodat de oranje pijl richting  het deurframe wijst, zoals hieronder.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_secondaryAxisArrow.png)

Vergeet niet dat de gele as-pijlen de draaipunt van het scharnier beïnvloeden. Limieten worden beïnvloed door de oranje as-pijlen.

3.

Onder de sectie Limieten  van de eigenschappen, stel zowel LowerAngle als UpperAngle in op -90 en 90, respectievelijk. Dit creëert een bewegingsbereik zoals de afbeelding aan de linkerkant.

![](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_limitAnglesV2.jpg)

![](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_showLimitsSet.png)

4.

Test de deur en merk op dat het scharnier nu beperkt is.

Als de deur limieten niet werken zoals verwacht, is het mogelijk dat de oranje as op een bevestiging niet correct is uitgelijnd. Selecteer DeurBevestiging en zorg ervoor dat een groene vlak met een boog richting  het deurframe wijst, zoals in de afbeelding hieronder.

![alt](https://prod.docsiteassets.roblox.com/assets/tutorials/building-a-hinged-door/introToConstraints_showAxisArc.jpg)

Met de deur compleet, neem wat tijd om te verkennen hoe je scharnierconstraints in verschillende situaties kunt gebruiken, zoals een valdeur of een swingende bijlval.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
