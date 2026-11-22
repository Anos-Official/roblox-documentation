<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-1/object-properties -->

Objecteigenschappen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Variabelen en objecten](/docs/nl-nl/tutorials/fundamentals/coding-1/landing)

# Objecteigenschappen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Eigenschappen  bepalen hoe objecten eruitzien en functioneren. Elk object in Roblox Studio heeft zijn eigen set eigenschappen. Bijvoorbeeld, een part-object heeft kleur-, grootte- en vormeigenschappen. Eigenschappen kunnen worden gewijzigd in het Eigenschappen-venster of via code.

Om meer te leren over eigenschappen, verken je de veelvoorkomende eigenschappen die in onderdelen worden aangetroffen en schrijf je vervolgens een script om de kleuren van onderdelen te veranderen.

## [Het Eigenschappen-venster](#het-eigenschappen-venster)[](#het-eigenschappen-venster)

Het Eigenschappen -venster kan worden gebruikt om meer te leren over de eigenschappen van een object. Gebruik het om een kijkje te nemen in de eigenschappen van een onderdeel.

1.

Selecteer een onderdeel.

2.

Kijk in het Eigenschappen -venster rechtsonder naar de verschillende eigenschappen die kunnen worden gewijzigd, zoals kleur, grootte, materiaal en transparantie. Je kunt de meeste eigenschappen in dit venster ook vanuit een script wijzigen.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-1/part-properties_400.png)

## [Voeg opmerkingen toe aan scripts](#voeg-opmerkingen-toe-aan-scripts)[](#voeg-opmerkingen-toe-aan-scripts)

Opmerkingen zijn speciale regels die beginnen met --  en helpen programmeurs te herinneren wat delen van scripts doen. In tegenstelling tot andere code, worden opmerkingen niet uitgevoerd; ze zijn er alleen zodat je aantekeningen voor jezelf en andere programmeurs kunt achterlaten. Dit script zal de [Color](/docs/nl-nl/reference/engine/classes/BasePart#Color)  eigenschap van een onderdeel aan het begin van het spel veranderen.

1.

Selecteer een bestaand onderdeel of maak een nieuwe. Hernoem het onderdeel naar PracticePart.

2.

Maak in ServerScriptService  een nieuw script met de naam ChangeColor.

3.

Verwijder in het script de standaardcode. Schrijf vervolgens een opmerking  door --  te typen en een korte beschrijving van wat het script zal doen.

Beschrijft wat het script doet

```

-- Verandert de kleur van een onderdeel

```

### [Lokaliseer het onderdeel](#lokaliseer-het-onderdeel)[](#lokaliseer-het-onderdeel)

Om wijzigingen aan te brengen in een onderdeel, moet je de locatie van het onderdeel kunnen beschrijven. De Explorer is een uitstekend hulpmiddel voor het verwijzen  naar locaties. In dit geval bevindt PracticePart  zich onder Workspace .

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-1/practice-part_400.png)

Nu je weet waar het onderdeel zich bevindt, moet de locatie van het onderdeel worden vertaald naar iets dat een script kan begrijpen.

1.

Typ onder de opmerking workspace.PracticePart .

Verwijst naar PracticePart in Workspace

```

-- Verandert de kleur van een onderdeel

workspace.PracticePart

```

### [Verander een eigenschap met code](#verander-een-eigenschap-met-code)[](#verander-een-eigenschap-met-code)

Je zult een RGB-waarde gebruiken om de kleur van het onderdeel te veranderen. Computers gebruiken RGB-waarden , de combinatie van rood, groen en blauw, om alle kleuren op je scherm te creëren.

RGB-waarden gebruiken drie nummers van 0 tot 255, gescheiden door komma's. Bijvoorbeeld, zwart is (0, 0, 0)  terwijl wit (255, 255, 255)  is.

Voor het onderdeel zal het script de eigenschap Kleur veranderen naar een nieuwe Color3, een datatype dat kleuren opslaat.

1.

Typ na PracticePart  .Color  om toegang te krijgen tot de Kleur-eigenschap.

Toegang tot de Kleur-eigenschap

```

-- Verandert de kleur van een onderdeel

workspace.PracticePart.Color

```

Roblox zal woorden automatisch aanvullen terwijl je typt om het coderen te versnellen. Je kunt de pijltoetsen gebruiken om naar beneden te bewegen in de lijst wanneer de woorden verschijnen. Kies een optie door op Enter  te drukken.

2.

Typ vervolgens = Color3.fromRGB()  Deze code stelt je in staat om een nieuwe kleur toe te wijzen.

Gebruikt Color3.fromRGB()

```

-- Verandert de kleur van een onderdeel

workspace.PracticePart.Color = Color3.fromRGB()

```

3.

RGB-kleurwaarden kunnen handmatig binnen de haakjes worden getypt, maar het gebruik van de kleurenkiezer is gemakkelijker. Klik binnen  de haakjes en klik vervolgens op het kleurenwiel. Volg de pop-up om een kleur te creëren.

 ![](https://prod.docsiteassets.roblox.com/assets/education/coding-1/color-picker_800x140.png)

Je code zou er ongeveer zo uit moeten zien als de onderstaande code.

Bijwerkt de kleur van PracticePart

```

-- Verandert de kleur van een onderdeel

workspace.PracticePart.Color = Color3.fromRGB(255, 230, 50)

```

Als je een RGB-waarde handmatig wilt typen, zorg er dan voor dat elk nummer tussen 0 en 255 ligt en gescheiden is door komma's, zoals (10, 50, 10).

4.

[Start een playtest](/docs/nl-nl/studio/testing-modes#spelen-testen)  om te testen of je onderdeel van kleur verandert.

## [Samenvatting](#samenvatting)[](#samenvatting)

Alle objecten hebben eigenschappen. Onderdelen hebben eigenschappen zoals kleur en transparantie. Tegelijkertijd hebben andere objecttypen hun unieke eigenschappen.

Om de kleur van een onderdeel te veranderen, moet je kunnen beschrijven waar je het kunt vinden. Als het onderdeel zich in Workspace bevindt, gebruik dan het trefwoord workspace . Gebruik vervolgens puntoperatoren om het gewenste onderdeel aan te geven en toegang te krijgen tot zijn eigenschappen.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-1/parents-and-children)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-1/create-a-script)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
