<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/guides/configs -->

Ervaringsconfiguraties | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Ervaringsconfiguraties

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De configuraties API stelt je in staat om [ervaringsconfiguraties](/docs/nl-nl/production/configs)  programmatisch te beheren in plaats van via Creator Hub of Studio. Deze gids behandelt een typische workflow:

-

Maak of werk een conceptconfiguratie bij.

-

Publiceer het.

-

Verkrijg de nieuwste configuratiewaarden.

-

Draai terug naar een eerdere waarde met behulp van de versiegeschiedenis.

Waarden die je publiceert zijn direct beschikbaar in je ervaring. In serverscripts gebruik je [ConfigService](/docs/nl-nl/reference/engine/classes/ConfigService)  om configuraties te lezen en te reageren op realtime-updates. [ConfigService:GetConfigAsync()](/docs/nl-nl/reference/engine/classes/ConfigService#GetConfigAsync)  en [ConfigSnapshot:GetValue()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#GetValue)  stellen je in staat om waarden te lezen, en [ConfigSnapshot.UpdateAvailable](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#UpdateAvailable)  met [ConfigSnapshot:Refresh()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#Refresh)  of [ConfigSnapshot:GetValueChangedSignal()](/docs/nl-nl/reference/engine/classes/ConfigSnapshot#GetValueChangedSignal)  laat je reageren wanneer waarden veranderen. Voor Luau-codevoorbeelden en verdere details, zie [Voeg configuraties toe aan je code](/docs/nl-nl/production/configs#voeg-configuraties-toe-aan-je-code)  en [Vernieuw snapshots](/docs/nl-nl/production/configs#vernieuw-snapshots)  in de gids voor ervaringsconfiguraties.

Voordat je begint, [genereer een API-sleutel](/docs/nl-nl/cloud/auth/api-keys)  of [configureer een OAuth 2.0-app](/docs/nl-nl/cloud/auth/oauth2-overview) . Leesbewerkingen vereisen de universe:read  scope. Schrijfbewerkingen (concepten, publiceren, herstellen) hebben universe:write  nodig.

Alle eindpunten gebruiken je universum-ID, die je kunt vinden op het [Creator Dashboard](https://create.roblox.com/dashboard/creations) . Klik op het overflow-menu van de ervarings tegel en Kopieer Universum-ID .

Voor de volledige referentie van eindpunten, aanvraag- en respons-schema's, en foutcodes, zie de [Cloud API-referentie](/docs/nl-nl/cloud/reference/features/configs) .

## [Repositories](#repositories)[](#repositories)

Verzoeken naar de configuratie-eindpunten gebruiken een repository  in het pad en een entries  object in de aanvraagbody. Bijvoorbeeld, dit verzoek voegt een conceptconfiguratie toe:

```

PATCH /creator-configs-public-api/v1/configs/universes/<UNIVERSE_ID>/repositories/<REPOSITORY>/draft

{

  "entries": {

    "enableNewTutorial": true

  }

}

```

-

Repositories  verschillen per product en scheiden configuraties per systeem.

-

Entries  zijn de configuratiesleutel-waarde paren. Je verzendt en ontvangt een enkel plat object van sleutels en waarden.

Deze gids behandelt in-ervaring configuraties, dus alle verzoeken gebruiken InExperienceConfig  voor de repository. Repositories zullen uiteindelijk uitbreiden om aanvullende producten en gebruiksscenario's te dekken.

| Gebruiksscenario | | Repository |
| --- | --- |
| In-ervaring configuraties | | InExperienceConfig |

## [Maak of werk configuraties bij](#maak-of-werk-configuraties-bij)[](#maak-of-werk-configuraties-bij)

Voordat je live gaat, worden configuratiewijzigingen als concepten voorbereid. Je kunt de gehele configuratie in één operatie instellen of gedeeltelijke updates toepassen totdat je tevreden bent:

-

Vanaf nul beginnen of alles vervangen  — Gebruik het overschrijf-eindpunt zodat de payload de volledige gewenste staat is. Elke sleutel die je weglaat, wordt als verwijderd beschouwd.

-

Slechts enkele sleutels wijzigen  — Gebruik het gedeeltelijke update-eindpunt zodat alleen de sleutels die je verzendt worden bijgewerkt; de rest blijft zoals het is.

Deze voorbeeldcode stelt bossHealth  in op 100  en gebruikt het overschrijf-eindpunt:

Python cURL

```

import requests

API_KEY = "<API_KEY>"

UNIVERSE_ID = "<UNIVERSE_ID>"

BASE = f"https://apis.roblox.com/creator-configs-public-api/v1/configs/universes/{UNIVERSE_ID}/repositories/InExperienceConfig"

headers = {"x-api-key": API_KEY, "Content-Type": "application/json"}

# Optioneel: stuur previousDraftHash als je een bestaand concept hebt en optimistische gelijktijdigheid wilt

payload = {

    "entries": {

        "bossHealth": 100

    }

}

r = requests.put(f"{BASE}/draft:overwrite", headers=headers, json=payload)

r.raise_for_status()

draft = r.json()

draft_hash = draft["draftHash"]  # Bewaar dit voor publicatie

print("Concept voorbereid. draftHash:", draft_hash)

```

De respons bevat de waarde van draftHash . Je hebt deze hash nodig om te publiceren. Als je liever slechts enkele sleutels in je concept wilt aanpassen, gebruik dan de PATCH-methode op het /draft  eindpunt en stuur alleen de entries (sleutels) die je wilt wijzigen.

### [Over concept-hashes](#over-concept-hashes)[](#over-concept-hashes)

Een concept-hash  is een ondoorzichtige identificator voor de huidige staat van je concept. De API retourneert deze na elke lees- of schrijfoperatie op een concept (maken, bijwerken, overschrijven, resetten, herstellen).

Bij het bijwerken of publiceren van concepten kun je previousDraftHash  in de aanvraagbody verzenden. Als de hash niet overeenkomt met het huidige concept van de server (bijv. iemand anders heeft ondertussen gepubliceerd of bewerkt), mislukt het verzoek. Je kunt dan het bijgewerkte concept opnieuw lezen, de nieuwe hash verkrijgen en opnieuw proberen of wijzigingen samenvoegen.

Bewaar altijd de draftHash  van de laatste conceptrespons voordat je publiceert of voordat je een andere wijziging aan het concept aanbrengt als je previousDraftHash  gebruikt.

## [Publiceer je wijzigingen](#publiceer-je-wijzigingen)[](#publiceer-je-wijzigingen)

Wanneer je tevreden bent met het concept, publiceer het dan zodat de nieuwe waarden live gaan. Geef draftHash  door van de conceptrespons, message  voor versiegeschiedenisdoeleinden, en deploymentStrategy  (of GradualRollout  voor een uitrol van 15 minuten of Immediate ). De volgende voorbeeldcode implementeert de configuratie onmiddellijk:

Python cURL

```

publish_payload = {

    "draftHash": draft_hash,

    "message": "Stel boss health in op 100",

    "deploymentStrategy": "Immediate"

}

r = requests.post(f"{BASE}/publish", headers=headers, json=publish_payload)

r.raise_for_status()

result = r.json()

print("Gepubliceerd. configVersion:", result["configVersion"])

```

Na een succesvolle publicatie wordt het concept gewist en ontvangt je ervaring de nieuwe configuratie volgens de uitrolstrategie. De respons bevat de nieuwe configuratieversie:

```

{

  "configVersion": 6

}

```

## [Verkrijg je gepubliceerde configuratie](#verkrijg-je-gepubliceerde-configuratie)[](#verkrijg-je-gepubliceerde-configuratie)

Om te bevestigen dat de wijziging is doorgevoerd, haal je de nieuwste gepubliceerde configuratie op. Gebruik het waarden-alleen eindpunt wanneer je alleen sleutels en waarden nodig hebt; gebruik het volledige eindpunt wanneer je ook metadata nodig hebt (beschrijvingen, laatst-toegankelijke tijd, enz.). Deze voorbeeldcode gebruikt het waarden-alleen eindpunt, met het volledige eindpunt uitgecommentarieerd:

Python cURL

```

# Alleen waarden (zelfde vorm RCC en je spel ziet)

r = requests.get(BASE, headers=headers)

r.raise_for_status()

config = r.json()

boss_health = config["entries"].get("bossHealth")

print("Gepubliceerde bossHealth:", boss_health)  # Zou 100 moeten zijn

# Of met volledige metadata:

# r = requests.get(f"{BASE}/full", headers=headers)

```

Verifieer dat entries.bossHealth  (of je sleutel) overeenkomt met wat je hebt gepubliceerd.

## [Bekijk geschiedenis en draai terug](#bekijk-geschiedenis-en-draai-terug)[](#bekijk-geschiedenis-en-draai-terug)

Elke publicatie creëert een revisie, net als een versiebeheersysteem. Je kunt revisies opsommen om te zien wie wat en wanneer heeft gewijzigd, en vervolgens terugkeren naar een eerdere revisie als je moet terugdraaien.

Deze voorbeeldcode roept het revisie-eindpunt aan en print de resultaten. Elke revisie bevat revisionId , version , time , publishedBy , message , en changes  (de sleutel, de "voor" waarde, en de "na" waarde).

Python cURL

```

r = requests.get(f"{BASE}/revisions", headers=headers, params={"MaxPageSize": 10})

r.raise_for_status()

data = r.json()

for rev in data["revisions"]:

    print(rev["version"], rev["time"], rev["message"], "— revisionId:", rev["revisionId"])

```

Om terug te draaien, roep je het herstel-eindpunt aan met de revisionId  waar je naar wilt terugkeren. Dit wist het huidige concept en bereidt een terugdraai-commit voor; het publiceert niet . Om te publiceren, moet je publish  aanroepen met de geretourneerde draftHash , net zoals bij het publiceren van een nieuwe wijziging.

Python cURL

```

REVISION_ID = "1234567890"  # Van de lijst hierboven

r = requests.post(f"{BASE}/revisions/{REVISION_ID}/restore", headers=headers)

r.raise_for_status()

restore_draft = r.json()

restore_hash = restore_draft["draftHash"]

# Publiceer de terugdraai

publish_payload = {

    "draftHash": restore_hash,

    "message": "Terugdraaien naar vorige configuratie",

    "deploymentStrategy": "Immediate"

}

r = requests.post(f"{BASE}/publish", headers=headers, json=publish_payload)

r.raise_for_status()

print("Terugdraai gepubliceerd. configVersion:", r.json()["configVersion"])

```

## [Beperkingen](#beperkingen)[](#beperkingen)

| Beperking | | Maximum |
| Sleutels per repository | | 100 |
| Sleutellengte | | 256 tekens |

Verzoeken die deze limieten overschrijden, zullen mislukken. Voor type-specifieke waarde limieten (bijv. string vs JSON) in je ervaring, zie [Limieten](/docs/nl-nl/production/configs#limieten)  in de gids voor ervaringsconfiguraties.

Voor volledige details over alle eindpunten in deze gids, zie de [Cloud API-referentie](/docs/nl-nl/cloud/reference) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
