<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/linear-velocity -->

LineaireSnelheid | Documentatie - Roblox Creator Hub

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

# LineaireSnelheid

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mover-beperkingen, inclusief Class.LineaireSnelheid , zie [mover-beperkingen](/docs/nl-nl/physics/mover-constraints) . Zie ook [Roblox eenheden](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

Een Class.LineaireSnelheid -beperking past kracht toe op een assemblage om een constante snelheid te behouden. Het kan worden ingesteld om kracht toe te passen langs een [Vector3](/docs/nl-nl/reference/engine/datatypes/Vector3) , lijn of 2D vlak.

De Class.LineaireSnelheid -beperking past een kracht toe die probeert een constante  lineaire snelheid te behouden. Als je de hoeveelheid kracht die wordt toegepast wilt regelen, gebruik dan een [VectorForce](/docs/nl-nl/physics/constraints/vector-force) -beperking. Als je alleen initiële  lineaire snelheid nodig hebt, stel dan de [AssemblyLinearVelocity](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyLinearVelocity) -eigenschap rechtstreeks in op de assemblage.

## [Relativiteit](#relativiteit)[](#relativiteit)

De toepassing van snelheid kan worden gecontroleerd via de Class.LineaireSnelheid.RelativeTo|RelativeTo -eigenschap van de beperking. Als deze is ingesteld op [World](/docs/nl-nl/reference/engine/enums/ActuatorRelativeTo) , wordt de kracht toegepast in wereldcoördinaten, onafhankelijk van de oriëntaties van de ouder of bevestigingen. Als deze is ingesteld op [Attachment0](/docs/nl-nl/reference/engine/enums/ActuatorRelativeTo)  of [Attachment1](/docs/nl-nl/reference/engine/enums/ActuatorRelativeTo) , wordt de kracht relatief toegepast ten opzichte van [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0)  of [Attachment1](/docs/nl-nl/reference/engine/classes/Constraint#Attachment1)  respectievelijk.

RelativeTo = Wereld

RelativeTo = Attachment0

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
