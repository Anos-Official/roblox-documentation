<!-- Source: https://create.roblox.com/docs/nl-nl/characters/emotes -->

Emotes | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Personages](/docs/nl-nl/characters)

# Emotes

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Emotes zijn expressieve karakter [animaties](/docs/nl-nl/animation)  die toegankelijk zijn door chatopdrachten te gebruiken ("/e cheer") of door toegang te krijgen tot het emotes-menu  rechtsboven in elk spel. Alle gebruikers hebben toegang tot standaard emotes, zoals dance , point  en cheer . Extra avatar emotes kunnen worden gekocht en uitgerust vanuit de [Marketplace](https://www.roblox.com/catalog) .

In jouw spel kun je de volgende emote-aanpassingen uitvoeren:

-

[Open en sluit](#open-en-sluit)  het emotes-menu van een gebruiker programmatically.

-

[Voeg toe of verwijder](#voeg-emotes-toe-en-verwijder-ze)  emote-opties uit het menu van een gebruiker.

-

[Schakel](#uitschakelen)  de toegang tot het menu uit.

-

[Speel](#speel-emotes)  een emote, gericht op een specifieke gebruikerskarakter.

## [Emotes-menu](#emotes-menu)[](#emotes-menu)

Je kunt het emotes-menu van een gebruiker handmatig openen en sluiten, het menu aanpassen om specifieke emotes weer te geven, of het menu volledig uitschakelen.

### [Open en sluit](#open-en-sluit)[](#open-en-sluit)

Om het emotes-menu van een speler handmatig te openen of te sluiten, roep je [GuiService:SetEmotesMenuOpen()](/docs/nl-nl/reference/engine/classes/GuiService#SetEmotesMenuOpen)  aan met een boolean waarde van true of false.

De volgende codevoorbeeld opent het emotes-menu voor de gebruiker:

```

-- Open het emote-menu

local GuiService = game:GetService("GuiService")

GuiService:SetEmotesMenuOpen(true)

```

Als je moet detecteren of het emotes-menu open is, roep je [GuiService:GetEmotesMenuOpen()](/docs/nl-nl/reference/engine/classes/GuiService#GetEmotesMenuOpen)  aan. Dit retourneert een boolean die de huidige staat van het menu aangeeft.

### [Voeg emotes toe en verwijder ze](#voeg-emotes-toe-en-verwijder-ze)[](#voeg-emotes-toe-en-verwijder-ze)

Pas het emotes-menu aan door emotes uit de catalogus in te stellen en vervolgens emotes uit te rusten op een [Humanoid](/docs/nl-nl/reference/engine/classes/Humanoid) . Stel emotes in met de [HumanoidDescription:SetEmotes()](/docs/nl-nl/reference/engine/classes/HumanoidDescription#SetEmotes)  methode en rust tot 8 emotes uit in het emotes-menu met [HumanoidDescription:SetEquippedEmotes()](/docs/nl-nl/reference/engine/classes/HumanoidDescription#SetEquippedEmotes) .

Gebruik de volgende codevoorbeeld in een [LocalScript](/docs/nl-nl/reference/engine/classes/LocalScript)  binnen de [StarterCharacterScripts](/docs/nl-nl/reference/engine/classes/StarterCharacterScripts)  map om emotes in jouw spel in te stellen en uit te rusten:

```

local Players = game:GetService("Players")

local humanoid = Players.LocalPlayer.Character.Humanoid

local humanoidDescription = humanoid.HumanoidDescription

-- Stel aangepaste emotes in binnen een tabel

local emoteTable = {

  ["Hello"] = {3576686446},

  ["Stadium"] = {3360686498},

  ["Tilt"] = {3360692915},

  ["Shrug"] = {3576968026},

  ["Salute"] = {3360689775},

  ["Point"] = {3576823880}

}

humanoidDescription:SetEmotes(emoteTable)

-- Rust emotes uit in een specifieke volgorde

local equippedEmotes = {"Hello", "Stadium", "Tilt", "Shrug", "Salute", "Point"}

humanoidDescription:SetEquippedEmotes(equippedEmotes)

```

Toetsnamen, zoals "Shrug" of "Salute", zijn aanpasbaar en zullen aan de speler verschijnen zoals geschreven. Emotes zullen ook in de volgorde verschijnen waarin ze zijn ingesteld, beginnend vanaf de bovenkant van het wiel en verder met de klok mee.

### [Uitschakelen](#uitschakelen)[](#uitschakelen)

Schakel het emotes-menu uit met [StarterGui:SetCoreGuiEnabled()](/docs/nl-nl/reference/engine/classes/StarterGui#SetCoreGuiEnabled) . Het uitschakelen van het emotes-menu voorkomt niet dat emotes worden uitgevoerd met een chatopdracht.

De volgende voorbeeldcode schakelt het emotes-menu uit:

```

local StarterGui = game:GetService("StarterGui")

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.EmotesMenu, false)

```

Naast het uitschakelen van het menu, kun je het laden van door gebruikers bezette emotes uitschakelen door de [StarterPlayer.UserEmotesEnabled](/docs/nl-nl/reference/engine/classes/StarterPlayer#UserEmotesEnabled)  eigenschap binnen StarterPlayer  ⟩ Character  in te stellen op false . Deze specifieke eigenschap kan alleen in Studio worden ingesteld en kan niet door scripts worden ingesteld.

## [Speel emotes](#speel-emotes)[](#speel-emotes)

Om handmatig een emote te spelen die een karakter in zijn [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  heeft, roep je [Humanoid:PlayEmote()](/docs/nl-nl/reference/engine/classes/Humanoid#PlayEmote) , waarbij je de stringnaam van de emote doorgeeft. Deze aanroep retourneert true om aan te geven dat de emote succesvol is afgespeeld, of false anders.

Gebruik de volgende codevoorbeeld om de Shrug-emote te spelen:

```

local Players = game:GetService("Players")

local humanoid = Players.LocalPlayer.Character.Humanoid

humanoid:PlayEmote("Shrug")

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
