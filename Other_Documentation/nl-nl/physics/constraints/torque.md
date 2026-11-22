<!-- Source: https://create.roblox.com/docs/nl-nl/physics/constraints/torque -->

Koppel | Documentatie - Roblox Creator Hub

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

# Koppel

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Voor een overzicht van het maken, visualiseren en simuleren van mover-beperkingen, inclusief [Torque](/docs/nl-nl/reference/engine/classes/Torque) , zie [mover-beperkingen](/docs/nl-nl/physics/mover-constraints) . Zie ook [Roblox eenheden](/docs/nl-nl/physics/units)  om te begrijpen hoe Roblox-eenheden zich verhouden tot metrische eenheden.

Een [Torque](/docs/nl-nl/reference/engine/classes/Torque)  beperking past constant koppel toe op een assemblage vanuit het zwaartepunt.

Omdat de [Torque](/docs/nl-nl/reference/engine/classes/Torque)  beperking constant  koppel en hoeksnelheid toepast, kunnen zeer hoge snelheden optreden als er geen andere krachten betrokken zijn. Als je een meer constante snelheid in de tijd wilt behouden, gebruik dan een [AngularVelocity](/docs/nl-nl/physics/constraints/angular-velocity)  beperking. Als je alleen initiële  snelheid nodig hebt, stel dan de [AssemblyAngularVelocity](/docs/nl-nl/reference/engine/classes/BasePart#AssemblyAngularVelocity)  eigenschap direct in op de assemblage.

## [Relativiteit](#relativiteit)[](#relativiteit)

Standaard wordt koppel toegepast ten opzichte van [Attachment0](/docs/nl-nl/reference/engine/classes/Constraint#Attachment0) . Als de bovenliggende assemblage draait, verandert de richting van het koppel om overeen te komen met de aangepaste oriëntatie van de bevestiging.

Als [RelativeTo](/docs/nl-nl/reference/engine/classes/Torque#RelativeTo)  is ingesteld op Wereld , wordt koppel toegepast in wereldcoördinaten, onafhankelijk van de oriëntaties van de bovenliggende of bevestiging.

Als [RelativeTo](/docs/nl-nl/reference/engine/classes/Torque#RelativeTo)  is ingesteld op Attachment1 , wordt koppel toegepast ten opzichte van [Attachment1](/docs/nl-nl/reference/engine/classes/Constraint#Attachment1)  en, als de bevestiging draait, verandert het om overeen te komen met zijn oriëntatie.

RelativeTo = Attachment0

RelativeTo = Wereld

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
