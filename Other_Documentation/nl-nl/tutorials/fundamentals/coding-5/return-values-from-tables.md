<!-- Source: https://create.roblox.com/docs/nl-nl/tutorials/fundamentals/coding-5/return-values-from-tables -->

Waarden retourneren uit tabellen | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Tutorials](/docs/nl-nl/tutorials)
4. /
5. [Woordenboeken en arrays](/docs/nl-nl/tutorials/fundamentals/coding-5/landing)

# Waarden retourneren uit tabellen

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Een veelvoorkomende behoefte in veel datastructuren is om waarden te retourneren. Dit artikel behandelt het doorzoeken van een tabel met behulp van pairs()  of ipairs()  voor de helft van een tabel element, zoals de sleutel of waarde, om de andere helft te vinden en te retourneren.

Het voorbeeld gebruikt een array die schepen opsomt die wachten op reparatie. ipairs()  wordt gebruikt om de plaats van een schip in de rij te retourneren.

## [Voorbeeld van een woordenboekzoekopdracht](#voorbeeld-van-een-woordenboekzoekopdracht)[](#voorbeeld-van-een-woordenboekzoekopdracht)

Heb je ooit naar een verloren huisdier gezocht in huis, kamer voor kamer? Schrijf je eigen functie om door een woordenboek genaamd house te zoeken om te zien welke kamer een verloren puppy heeft.

1.

Kopieer het onderstaande woordenboek om als het huis te fungeren.

```

local house = {

	kitchen = "stapel rommel",

	livingRoom = "kitten",

	bedroom1 = "niemand daar",

	bedroom2 = "puppy",

}

```

2.

Maak een nieuwe functie genaamd findPet()  om het woordenboek te doorzoeken. Voeg parameters toe voor welk woordenboek je wilt doorzoeken en welke waarde je wilt zoeken.

3.

Gebruik pairs()  om door het woordenboek te itereren. Probeer zelf te coderen voordat je je werk controleert in de oplossing hieronder.

```

local function findPet(whereToSearch, searchFor)

	for place, value in pairs(whereToSearch) do

	end

end

```

4.

Terwijl de for-lus door het woordenboek iterereert, gebruik return  om de kamer terug te geven waar het huisdier is gevonden.

[Volgende](/docs/nl-nl/tutorials/fundamentals/coding-6/landing)[Vorige](/docs/nl-nl/tutorials/fundamentals/coding-5/pairs-and-ipairs)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
