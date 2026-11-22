<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/vector-force -->

VectorForce | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [3D-werkruimte](/docs/nl-nl/workspace)
6. /
7. [Fysica](/docs/nl-nl/physics)
8. /
9. [Beperkingen van verplaatser](/docs/nl-nl/physics/mover-constraints)

# VectorForce

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mover-constraints, inclusief [VectorForce](/docs/nl-nl/reference/engine/classes/VectorForce) , zie [mover constraints](/docs/nl-nl/physics/mover-constraints) . Zie ook [Roblox units](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

De [VectorForce](/docs/nl-nl/reference/engine/classes/VectorForce) -constraint past constante lineaire kracht toe op een assemblage. De richting en sterkte van de kracht worden bepaald door een [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3)  en kunnen relatief zijn aan een bevestiging op het onderdeel, een andere bevestiging of het wereldcoördinatensysteem.

Omdat de [VectorForce](/docs/nl-nl/reference/engine/classes/VectorForce) -constraint constante  kracht en versnelling toepast, kunnen zeer hoge snelheden ontstaan als er geen andere krachten betrokken zijn. Als je een meer constante snelheid in de tijd wilt behouden, gebruik dan een [LinearVelocity](/docs/nl-nl/physics/constraints/linear-velocity) -constraint. Als je alleen initiële  snelheid nodig hebt, stel dan de [AssemblyLinearVelocity](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyLinearVelocity) -eigenschap direct in op de assemblage.

## [Krachtlocatie](#krachtlocatie)[](#krachtlocatie)

Standaard wordt de kracht toegepast op de assemblage op de locatie van [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0) . Als het zwaartepunt niet is uitgelijnd met de richting/punt van de kracht, zal er ook koppel worden toegepast. Indien gewenst kan de kracht worden gefocust op het zwaartepunt door [ApplyAtCenterOfMass](/docs/nl-nl/reference/engine/classes/VectorForce#ApplyAtCenterOfMass)  in te schakelen.

ApplyAtCenterOfMass = false

ApplyAtCenterOfMass = true

## [Relativiteit](#relativiteit)[](#relativiteit)

Standaard wordt de kracht relatief toegepast aan [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0) . Als de bovenliggende assemblage draait, zal de kracht van richting veranderen om overeen te komen met de aangepaste oriëntatie van de bevestiging; visualiseer dit gedrag in hoe de duwer van een raket deze naar voren duwt, ongeacht de rotatie van de raket.

Als [RelativeTo](/docs/nl-nl/reference/engine/classes/VectorForce#RelativeTo)  is ingesteld op World , wordt de kracht toegepast in wereldcoördinaten, onafhankelijk van de oriëntaties van de bovenliggende of bevestigingen; visualiseer dit gedrag als een directionele kracht zoals de wind die tegen een object blaast.

Als [RelativeTo](/docs/nl-nl/reference/engine/classes/VectorForce#RelativeTo)  is ingesteld op Attachment1 , wordt de kracht relatief toegepast aan [Attachment1](/docs/nl-nl/reference/engine/classes/Constraint#Attachment1)  en, als de bevestiging draait, zal de kracht veranderen om overeen te komen met zijn oriëntatie.

RelativeTo = Attachment0

RelativeTo = World

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
