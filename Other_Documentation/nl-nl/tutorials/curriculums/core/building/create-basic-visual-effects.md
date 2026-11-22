<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/curriculums/core/building/create-basic-visual-effects -->

Maak basis visuele effecten | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)

# Maak basis visuele effecten

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een statische wereld kan levenloos aanvoelen. Visuele effecten  voegen beweging toe, maken de omgeving dynamischer en helpen de aandacht van spelers te vestigen op belangrijke gebieden.

In deze sectie gebruik je deeltjesemitters  om twee effecten te creëren. De eerste is een gloeiende flare bovenop de hoogste zeestapel die de ogen van spelers naar boven trekt, en de tweede is een laag van zwevende stofdeeltjes die sfeer en diepte aan de omgeving toevoegt.

Deeltjesemitters worden voornamelijk geconfigureerd via numerieke eigenschappen, waardoor ze goed passen bij Assistant. Gebruik de Bouwen met Assistant -tabbladen om een set werkende startwaarden te genereren, en pas vervolgens zelf de kleuren en NumberSequence -curves aan totdat het effect eruitziet zoals je wilt.

## [Maak een flare](#maak-een-flare)[](#maak-een-flare)

De voorbeeldgame [Island Jump - Final](https://www.roblox.com/games/14238807008/Island-Jump-Completed-Sample)  plaatst een enorme flare bovenop zijn hoogste platform. Omdat de rest van de wereld stil is, wordt de flare een brandpunt, waardoor spelers van nature willen klimmen.

Bouwen met Assistant Bouw het zelf

Maak de flare

```

In Workspace > World, maak een nieuwe map genaamd VFX als deze nog niet bestaat.

Binnen de VFX-map, maak een blokdeel genaamd VFX_Flare met Size 20, 20, 20, CFrame.Position 400, 331, 79, en CFrame.Orientation 0, 0, 0. Stel Transparency in op 1 zodat het deel onzichtbaar is, en schakel Anchored in.

Binnen VFX_Flare, maak een Attachment.

Binnen die Attachment, maak een ParticleEmitter genaamd Emitter_Flare met de volgende eigenschappen:

- Texture: rbxassetid://8983307836

- Color: Color3.fromRGB(127, 84, 59)

- LightEmission: 1

- ZOffset: 1

- Lifetime: NumberRange.new(10, 10)

- Rate: 0.45

- RotSpeed: NumberRange.new(20, 20)

- Speed: NumberRange.new(0, 0)

- Size: een NumberSequence die begint bij 0, langzaam groeit in de vroege levensduur, dan snel stijgt naar 10 en gedurende de rest van de levensduur op 10 blijft.

- Transparency: een NumberSequence die gedurende het grootste deel van de levensduur dicht bij 0 (zichtbaar) blijft, dan tussen waarden stuitert tegen het einde en zich vestigt op 1.

Ook binnen VFX_Flare (een broeder van de Attachment), maak een PointLight met Brightness 2 en Range 36.

```

Na het uitvoeren van de prompt, open de Size  en Transparency -sequenties in het eigenschappenvenster en pas de curves zelf aan totdat de pulsatie goed aanvoelt.

## [Maak de stofdeeltjes](#maak-de-stofdeeltjes)[](#maak-de-stofdeeltjes)

Het tweede type deeltjesemitter dat de voorbeeldgame gebruikt om dynamische beweging aan het spel toe te voegen, is degene die stofdeeltjes door de atmosfeer verspreidt. Deze deeltjes omringen de speler en voegen een gevoel van textuur en diepte aan de lucht zelf toe.

Bouwen met Assistant Bouw het zelf

Maak de stofdeeltjes

```

In Workspace > World > VFX, maak een blokdeel genaamd VFX_DustMotes met Size 645, 355, 275, CFrame.Position 198, 168, 26, en CFrame.Orientation 0, 0, 0. Stel Transparency in op 1 zodat het deel onzichtbaar is. Schakel CanCollide uit. Schakel Anchored in.

Binnen VFX_DustMotes, maak een ParticleEmitter genaamd Emitter_DustMotes met de volgende eigenschappen:

- Texture: rbxassetid://14302399641

- Color: Color3.fromRGB(192, 241, 255)

- ZOffset: -5

- Lifetime: NumberRange.new(1, 10)

- Rate: 50000

- Rotation: NumberRange.new(-45, 45)

- RotSpeed: NumberRange.new(-60, -60)

- Speed: NumberRange.new(1, 5)

- Acceleration: Vector3.new(1, -1, 1)

- Size: een NumberSequence die stijgt naar ongeveer 0.25 kort na creatie, en dan geleidelijk vervaagt naar 0.

- Transparency: een NumberSequence die volledig transparant begint, meer ondoorzichtig wordt (met een envelop van ongeveer 0.1) in het midden van de levensduur, en dan langzaam vervaagt naar 1.

```

Na het uitvoeren, open de Size en Transparency-sequenties en pas de curves met het oog aan totdat het stof goed aanvoelt.

![De laatste versie van de stofdeeltjes tegen een heldere blauwe lucht.](https://prod.docsiteassets.roblox.com/assets/tutorials/core-building-and-scripting/Dust-Motes-Sky.jpg) Vage stofdeeltjes in de lucht terwijl je omhoog kijkt naar de lucht vanaf de platforms

[Volgende](/docs/nl-nl/tutorials/curriculums/core/building/customize-global-lighting)[Vorige](/docs/nl-nl/tutorials/curriculums/core/scripting/script-an-upgrade-button)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
