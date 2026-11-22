<!-- Source: https://create.roblox.com/docs/nl-nl/art/modeling/texture-specifications -->

Textuur specificaties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Assets](/docs/nl-nl/assets)
4. /
5. Textureren

# Textuur specificaties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een textuur  is een digitale afbeelding die op het oppervlak van een 3D-object wordt toegepast om de visuele uitstraling te simuleren en te verbeteren. Roblox ondersteunt verschillende textuurtypes die je importeert met een aangepast 3D-object, of rechtstreeks uploadt als afzonderlijke afbeeldingsbestanden. Voor details over het implementeren van basistexturen, zie [texturen en decals](/docs/nl-nl/parts/textures-decals) .

Roblox ondersteunt ook [fysiek-gebaseerde rendering (PBR) texturen](/docs/nl-nl/art/modeling/surface-appearance)  die de bestaande [TextureID](/docs/nl-nl/reference/engine/classes/MeshPart#TextureID)  van een mesh overschrijven en kunnen worden gebruikt om meeslepende omgevingen en objecten te creëren.

Voor informatie over hoe je texturen correct aan je model in Blender en Maya kunt koppelen voor import in Studio, zie [Blender / Maya textuurinstellingen](/docs/nl-nl/art/modeling/assign-textures) .

Zie de volgende vereisten bij het maken van je eigen basis- en geavanceerde texturen:

-

Bestandsformaten  — Bestandsformaten voor texturen die afzonderlijk in Studio worden geüpload, moeten worden ingediend als een .png , .jpg , .tga  of .bmp .

-

Resolutie  — Roblox ondersteunt textuurresoluties tot 4096×4096 pixels (4K). Terwijl een game laadt, begint de engine automatisch met lagere kwaliteitsversies van de textuur en verhoogt de kwaliteit op basis van de middelen van het apparaat. Toch kan het handmatig schalen van texturen voordat je ze uploadt het geheugenverbruik in sommige situaties verbeteren. Overweeg de volgende algemene richtlijnen:

-

Voor kleinere 5×5 stud objecten, gebruik 256×256 textuurresoluties.

-

Voor middelgrote 10×10 stud objecten, gebruik 512×512 textuurresoluties.

-

Voor grotere 20×20 stud objecten, gebruik 1024×1024 textuurresoluties.

-

Zie [PBR textuurbudgetten](#oppervlakte-uiterlijk)  voor soortgelijke richtlijnen met PBR textuurkaarten.

-

Enkel materiaal  — Mesh-objecten kunnen slechts één materiaal toegewezen krijgen.

De standaard [materialen](/docs/nl-nl/parts/materials)  van Roblox volgen een vergelijkbaar texelresolutiepatroon:

-

Onderdelen tonen een 1024×1024 op een 8×8 stud gezicht.

-

Terrein toont 512×512 over 8×8 studs.

## [Oppervlakte-uiterlijk](#oppervlakte-uiterlijk)[](#oppervlakte-uiterlijk)

Je kunt een [oppervlakte-uiterlijk](/docs/nl-nl/art/modeling/surface-appearance)  aan je mesh in Studio toevoegen om PBR textuur opties toe te voegen. De [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  instantie gebruikt UV-mapping, een vorm van textuurmapping, om 2D-afbeeldingen nauwkeurig op het mesh-object te mappen.

Voor informatie over hoe je PBR texturen correct aan je model in Blender en Maya kunt koppelen voor import in Studio, zie [Blender / Maya textuurinstellingen](/docs/nl-nl/art/modeling/assign-textures) .

Zie de volgende vereisten voor [SurfaceAppearance](/docs/nl-nl/reference/engine/classes/SurfaceAppearance)  activa:

Textuurbestanden PBR Textuur Budget

Wanneer mogelijk, moeten textuurbestanden de juiste naam affix bevatten en de juiste afbeeldingsdetails volgen:

| Textuur type | | Textuur afbeeldingsdetails |
| --- | --- |
| [Albedo](/docs/nl-nl/art/modeling/surface-appearance#kleur-albedo) | | RGB (24-bits) |
| [Normaal](/docs/nl-nl/art/modeling/surface-appearance#normaal) | | RGB (24-bits); Roblox ondersteunt alleen OpenGL-formaat - Tangent Space  normaal kaarten |
| [Ruwheid](/docs/nl-nl/art/modeling/surface-appearance#ruwheid) | | Enkel Kanaal Grijswaarden (8-bits) |
| [Metaalheid](/docs/nl-nl/art/modeling/surface-appearance#metaalheid) | | Enkel Kanaal Grijswaarden (8-bits) |
| [Emissieve Masker](/docs/nl-nl/art/modeling/surface-appearance#emissief-masker) | | Enkel Kanaal Grijswaarden (8-bits) |

## [UV-mapping](#uv-mapping)[](#uv-mapping)

Alle texturen gebruiken UV-mapping, een 3D-modelleringsproces om het oppervlak van een 3D-model op een 2D-afbeelding of UV-atlas te projecteren. Zie de volgende vereisten voor UV-mapping, vooral als je je UV-atlas handmatig bewerkt of optimaliseert:

-

Enkele UV-set  — Gebruik een enkele UV-set voor elk onderdeel, zoals een humanoïde of accessoire. Studio staat geen meerdere UV-sets toe.

-

Coördinaten  — Alle UV's moeten binnen een 0:1 ruimte worden gemaakt.

-

Overlappingen  — Overlappende UV's zijn toegestaan.

-

Maximale textuurresolutie  — Roblox ondersteunt tot 1024×1024 pixelruimtes voor textuurkaarten.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
