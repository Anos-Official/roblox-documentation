<!-- Source: https://create.roblox.com/docs/nl-nl/cloud/webhooks/automate-right-to-erasure -->

Automatiseer het recht op verwijdering met webhooks | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Open Cloud-API](/docs/nl-nl/cloud)

# Automatiseer het recht op verwijdering met webhooks

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Global data protection and privacy regulations grant individuals the right to control their data, including the right to request its deletion (often referred to as the "right to erasure" or "right to delete"). If you store any personal data or Personally Identifiable Information (PII) , such as user IDs, you are responsible for complying with applicable privacy framework(s) by permanently deleting this information upon receiving a user request. More information can be found in [RTBF and creators](/docs/nl-nl/production/publishing/RTBF-and-creators) .

## [Overweeg alternatieven](#overweeg-alternatieven)[](#overweeg-alternatieven)

Voor persoonlijke gegevens in gegevensopslag is de eenvoudigste automatiseringsoptie het configureren van RTBF-verwijderingssjablonen. Wanneer Roblox een RTBF-verzoek verwerkt, verwijdert het automatisch overeenkomende standaard- of geordende gegevensopslagvermeldingen zonder dat je aangepaste code hoeft te hosten. Om sjablonen te configureren en ondersteunde patronen te bekijken, zie [Gegevensopslag recht om vergeten te worden (RTBF)](/docs/nl-nl/cloud-services/data-stores/right-to-be-forgotten) .

De webhook-werkstroom op deze pagina is nuttig wanneer:

-

Je persoonlijke gegevens buiten gegevensopslag opslaat.

-

Je gegevensopslagstructuur of gebruiksgeval niet wordt ondersteund door RTBF-verwijderingssjablonen.

-

Je aangepaste verwerkings- of verwijderingslogica nodig hebt.

## [Creator webhook-werkstroom](#creator-webhook-werkstroom)[](#creator-webhook-werkstroom)

Deze tutorial demonstreert hoe je een [webhook instelt](/docs/nl-nl/cloud/webhooks/webhook-notifications)  en een lokaal draaiende Discord-bot maakt die de [Open Cloud API voor gegevensopslag](/docs/nl-nl/cloud/guides/data-stores)  gebruikt om de afhandeling van verzoeken om het recht op verwijdering te automatiseren. De werkstroom voor dit proces is als volgt:

1.

Roblox Support ontvangt een verzoek om verwijdering van een gebruiker.

2.

De Roblox-webhook wordt geactiveerd, met de gebruikers-ID en een lijst van Start Place ID's voor de spellen die ze in de payload hebben bezocht.

3.

Je bot luistert naar deze webhookmeldingen, verifieert hun authenticiteit en gebruikt de [Open Cloud API voor gegevensopslag](/docs/nl-nl/cloud/guides/data-stores)  om de PII-gegevens die in gegevensopslag zijn opgeslagen te verwijderen.

Om deze oplossing te gebruiken, moet je ervoor zorgen dat je gegevensopslag-sleutels identificeerbaar zijn door gebruikers-ID's, zoals het bevatten van gebruikers-ID's als substrings, of je moet de scripts aanpassen om overeen te komen met je eigen gegevensstructuur.

4.

De bot reageert op het webhookbericht in Discord met de status van de verwijdering.

 ![](https://prod.docsiteassets.roblox.com/assets/misc/Webhooks-Bot-Workflow.png)

## [Configureer een webhook met integratie van derden](#configureer-een-webhook-met-integratie-van-derden)[](#configureer-een-webhook-met-integratie-van-derden)

Voordat je een bot maakt, stel je een server in met webhook-integratie op de messaging-applicatie van derden. Gebruik de server vervolgens om een webhook te configureren op het Creator Dashboard.

### [Stel een server in](#stel-een-server-in)[](#stel-een-server-in)

De volgende stappen tonen hoe je de server instelt met Discord.

1.

Maak een nieuwe Discord-server aan. Als je niet bekend bent met het proces, zie [Discord Support](https://support.discord.com/hc/en-us/articles/204849977-How-do-I-create-a-server-) .

Het wordt aanbevolen om je server als een privéserver in te stellen om de beveiliging van gebruikers te beschermen. Zie [Discord Support](https://support.discord.com/hc/en-us/articles/206143407-How-do-I-set-up-a-private-server-)  als je niet bekend bent met het proces.

2.

De server maakt automatisch een #general  kanaal aan als je standaardkanaal. Klik op het Kanaal Bewerken -pictogram van het #general  kanaal.

3.

Stel onder Machtigingen  het kanaal in op privé.

4.

Maak een webhook-integratie met de nieuwe server, noem deze RTBF Hook . Als je niet bekend bent met het proces, zie [Discord Support](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks) .

5.

Kopieer de webhook-URL en bewaar deze op een veilige plaats. Sta alleen vertrouwde teamleden toe om toegang te krijgen, aangezien het lekken van de URL kwaadwillenden in staat kan stellen om valse berichten te verzenden en mogelijk je gebruikersgegevens te verwijderen.

### [Configureer een webhook op Roblox](#configureer-een-webhook-op-roblox)[](#configureer-een-webhook-op-roblox)

Nadat je de URL van de derde partijserver hebt verkregen, gebruik je deze om een [webhook te configureren](/docs/nl-nl/cloud/webhooks/webhook-notifications#webhooks-configureren-op-creator-dashboard)  op het Creator Dashboard. Zorg ervoor dat je de volgende instellingen uitvoert:

Momenteel kunnen alleen groepsleden verzoeken om verwijdering ontvangen voor groepsbezit spellen. Om de automatiseringsoplossing voor een groepsbezit spel te implementeren, moet de groepslid de webhook configureren.

-

Voeg de Discord-server-URL toe als de Webhook-URL .

-

Voeg een aangepaste Geheim  toe. Hoewel een geheim optioneel is voor het voltooien van de configuratie, moet je er een opnemen om kwaadwillenden te voorkomen die zich als Roblox voordoen en je gegevens verwijderen. Voor meer informatie over het gebruik van een geheim, zie [Verifieer webhookbeveiliging](/docs/nl-nl/cloud/webhooks/webhook-notifications#verifying-webhook-security) .

-

Selecteer Verzoek om verwijdering  onder Triggers .

Je kunt de webhook testen met de knop Testrespons  om te zien of je een melding ontvangt in het #general  kanaal van je server van Roblox. Als je de melding niet ontvangt, probeer het opnieuw of controleer je serverinstellingen om de fout op te lossen.

## [Configureer een bot](#configureer-een-bot)[](#configureer-een-bot)

Nadat je de webhook hebt toegevoegd, gebruik je deze om de bot te configureren met de volgende stappen. Voor meer informatie, zie de [Discord-documentatie](https://discord.com/developers/docs/topics/oauth2#bot-vs-user-accounts) .

1.

Navigeer naar de [Toepassingen-pagina](https://discord.com/developers/applications) .

2.

Maak een nieuwe applicatie aan en noem deze RTBF Bot .

3.

Het systeem leidt je naar de instellingen voor Algemene informatie  van de bot. Kopieer en bewaar de applicatie-ID op een veilige plaats.

4.

Selecteer onder het instellingenmenu OAuth2 .

5.

Navigeer naar de OAuth2 -instellingen

1.

Schakel de bot -scope in, er verschijnt een lijst met aanvullende Bot-machtigingen.

2.

Voeg de Administrator -machtiging toe. Sla je wijzigingen op.

3.

Sla de gegenereerde URL op.

6.

Kopieer de gegenereerde URL. Laat de pagina met de applicatie-instellingen open.

7.

Navigeer naar de gegenereerde URL. Selecteer de doelsserver. Klik op de knop Doorgaan  en vervolgens op de knop Autoriseren .

8.

Navigeer terug naar de pagina met de applicatie-instellingen en ga naar de Bot-instellingen.

9.

Schakel onder de sectie Privileged Gateway Intents  de Berichtinhoud Intent  in.

10.

Sla in de Bot-instellingen > sectie Build-A-Bot  de bot-token op een veilige plaats op voor latere stappen. Als je de token niet ziet, klik dan op de knop Token opnieuw instellen  om een nieuwe te genereren.

## [Maak een Open Cloud API-sleutel aan](#maak-een-open-cloud-api-sleutel-aan)[](#maak-een-open-cloud-api-sleutel-aan)

Om je bot van derden toegang te geven tot je gegevensopslag voor het opslaan van PII-gegevens van gebruikers, [maak een Open Cloud API-sleutel aan](/docs/nl-nl/cloud/auth/api-keys)  die toegang heeft tot je spellen en voeg de machtiging Verwijder invoer  van gegevensopslag toe voor gegevensverwijdering. Als je geordende gegevensopslag gebruikt voor het opslaan van PII, moet je ook de machtiging Schrijven  van geordende gegevensopslag toevoegen. Na voltooiing, kopieer en bewaar de API-sleutel op een veilige locatie om deze in latere stappen te gebruiken.

## [Verkrijg identificatoren van spellen en plaatsen](#verkrijg-identificatoren-van-spellen-en-plaatsen)[](#verkrijg-identificatoren-van-spellen-en-plaatsen)

Om de bot in staat te stellen de PII-gegevens te lokaliseren die door gebruikers voor verwijdering zijn aangevraagd, verkrijg je de volgende identificatoren van alle spellen waarvoor je de bot wilt gebruiken:

-

De Universum-ID , de unieke identificatie van je spel.

-

De Start Place ID , de unieke identificatie van de startplaats van een spel.

Om deze identificatoren te verkrijgen:

1.

Navigeer naar het [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Beweeg over de thumbnail van een spel, klik op de ⋯  knop en selecteer respectievelijk Kopieer Universum-ID  en Kopieer Start Place ID .

 ![](https://prod.docsiteassets.roblox.com/assets/creator-dashboard/Options-Button-Experience-Public.png)

## [Voeg scripts toe](#voeg-scripts-toe)[](#voeg-scripts-toe)

Nadat je de webhook, bot en API-sleutel voor gegevensopslag hebt ingesteld, voeg je ze toe aan de scripts die de automatiseringslogica van de bot implementeren. Het volgende voorbeeld gebruikt Python 3.

1.

Installeer Python-bibliotheken met de volgende opdrachten:

Installeer Bibliotheken

```

pip3 install discord

pip3 install requests

pip3 install urllib3==1.26.6

```

2.

Kopieer en bewaar de volgende scripts die overeenkomen met verschillende delen van de botlogica in dezelfde map:

bot_config.py

```

BOT_TOKEN = ""

OPEN_CLOUD_API_KEY = ""

ROBLOX_WEBHOOK_SECRET = ""

# Woordenboek van de Start place ID naar

# (universum ID, lijst van (gegevensopslag naam, scope, en invoersleutel)) voor

# Standaard Gegevensopslag

# Gebruikersgegevens die onder deze vermeldingen zijn opgeslagen, worden verwijderd

STANDARD_DATA_STORE_ENTRIES = {

    # Start Place ID

    111111111: (

        # Universum ID

        222222222,

        [

            ("StandardDataStore1", "Scope1", "Key1_{user_id}"),

            ("StandardDataStore1", "Scope1", "Key2_{user_id}"),

            ("StandardDataStore2", "Scope1", "Key3_{user_id}")

        ]

    ),

    33333333: (

        444444444,

        [

            ("StandardDataStore3", "Scope1", "Key1_{user_id}")

        ]

    )

}

# Woordenboek van de Start place ID naar

# (universum ID, lijst van (gegevensopslag naam, scope, en invoersleutel)) voor

# Geordende Gegevensopslag

# Gebruikersgegevens die onder deze vermeldingen zijn opgeslagen, worden verwijderd

ORDERED_DATA_STORE_ENTRIES = {

    111111111: (

        222222222,

        [

            ("OrderedDataStore1", "Scope2", "Key4_{user_id}")

        ]

    )

}

```

data_stores_api.py

```

import requests

import bot_config

from collections import defaultdict

"""

Roept de Data Stores Open Cloud API aan om alle vermeldingen voor een user_id die zijn

geconfigureerd in STANDARD_DATA_STORE_ENTRIES te verwijderen. Retourneert een lijst van succesvolle verwijderingen en mislukkingen om te verwijderen.

"""

def delete_standard_data_stores(user_id, start_place_ids):

    successes = defaultdict(list)

    failures = defaultdict(list)

    for owned_start_place_id in bot_config.STANDARD_DATA_STORE_ENTRIES:

        if owned_start_place_id not in start_place_ids:

            continue

        universe_id, universe_entries = bot_config.STANDARD_DATA_STORE_ENTRIES[owned_start_place_id]

        for (data_store_name, scope, entry_key) in universe_entries:

            entry_key = entry_key.replace("{user_id}", user_id)

            response = requests.delete(

                f"https://apis.roblox.com/datastores/v1/universes/{universe_id}/standard-datastores/datastore/entries/entry",

                headers={"x-api-key": bot_config.OPEN_CLOUD_API_KEY},

                params={

                    "datastoreName": data_store_name,

                    "scope": scope,

                    "entryKey": entry_key

                }

            )

            if response.status_code in [200, 204]:

                successes[owned_start_place_id].append((data_store_name, scope, entry_key))

            else:

                failures[owned_start_place_id].append((data_store_name, scope, entry_key))

    return successes, failures

"""

Roept de Ordered Data Stores Open Cloud API aan om alle vermeldingen voor een user_id die zijn

geconfigureerd in ORDERED_DATA_STORE_ENTRIES te verwijderen. Retourneert een lijst van succesvolle verwijderingen en mislukkingen om te verwijderen.

"""

def delete_ordered_data_stores(user_id, start_place_ids):

    successes = defaultdict(list)

    failures = defaultdict(list)

    for owned_start_place_id in bot_config.ORDERED_DATA_STORE_ENTRIES:

        if owned_start_place_id not in start_place_ids:

            continue

        universe_id, universe_entries = bot_config.ORDERED_DATA_STORE_ENTRIES[owned_start_place_id]

        for (data_store_name, scope, entry_key) in universe_entries:

            entry_key = entry_key.replace("{user_id}", user_id)

            response = requests.delete(

                f"https://apis.roblox.com/ordered-data-stores/v1/universes/{universe_id}/orderedDatastores/{data_store_name}/scopes/{scope}/entries/{entry_key}",

                headers={"x-api-key": bot_config.OPEN_CLOUD_API_KEY}

            )

            if response.status_code in [200, 204, 404]:

                successes[owned_start_place_id].append((data_store_name, scope, entry_key))

            else:

                failures[owned_start_place_id].append((data_store_name, scope, entry_key))

    return successes, failures

```

message_parser.py

```

import time

import hmac

import hashlib

import re

import base64

import bot_config

"""

Parseert het ontvangen bericht voor de Roblox-handtekening en tijdstempel, de footer is alleen ingesteld als je

het webhook-geheim hebt geconfigureerd

"""

def parse_footer(message):

    if not message.embeds[0].footer or \

        not message.embeds[0].footer.text:

        return "", 0

    footer_match = re.match(

        r"Roblox-Signature: (.*), Timestamp: (.*)",

        message.embeds[0].footer.text

    )

    if not footer_match:

        return "", 0

    else:

        signature = footer_match.group(1)

        timestamp = int(footer_match.group(2))

        return signature, timestamp

"""

Verifieert de Roblox-handtekening met het geconfigureerde geheim om de geldigheid te controleren

"""

def validate_signature(message, signature, timestamp):

    if not message or not signature or not timestamp:

        return False

    # Voorkomt herhalingsaanvallen binnen een venster van 300 seconden

    request_timestamp_ms = timestamp * 1000

    window_time_ms = 300 * 1000

    oldest_timestamp_allowed = round(time.time() * 1000) - window_time_ms

    if request_timestamp_ms < oldest_timestamp_allowed:

        return False

    # Valideert de handtekening

    timestamp_message = "{}.{}".format(timestamp, message.embeds[0].description)

    digest = hmac.new(

        bot_config.ROBLOX_WEBHOOK_SECRET.encode(),

        msg=timestamp_message.encode(),

        digestmod=hashlib.sha256

    ).digest()

    validated_signature = base64.b64encode(digest).decode()

    if signature != validated_signature:

        return False

    # Geldige handtekening

    return True

"""

Parseert een ontvangen webhookbericht op Discord. Extraheert gebruikers-ID, voorkomt herhalingsaanvallen

op basis van de ontvangen tijdstempel en verifieert de Roblox-handtekening met het geconfigureerde geheim om de geldigheid te controleren.

"""

def parse_message(message):

    # Parseert het ontvangen bericht voor gebruikers-ID en spel-ID

    if len(message.embeds) != 1 or \

        not message.embeds[0].description:

        return "", []

    description_match = re.match(

        r"You have received a new notification for Right to Erasure for the User Id: (.*) in " +

        r"the game\(s\) with Ids: (.*)",

        message.embeds[0].description

    )

    if not description_match:

        return "", []

    user_id = description_match.group(1)

    start_place_ids = set(int(item.strip()) for item in description_match.group(2).split(","))

    signature, timestamp = parse_footer(message)

    if validate_signature(message, signature, timestamp):

        return user_id, start_place_ids

    else:

        return "", []

```

discord_bot.py

```

import discord

import bot_config

import data_stores_api

import message_parser

def run():

    intents = discord.Intents.default()

    intents.message_content = True

    client = discord.Client(intents=intents)

    @client.event

    async def on_ready():

        print(f"{client.user} luistert naar berichten over het recht op verwijdering")

    """

    Handler voor webhookberichten van Roblox

    """

    @client.event

    async def on_message(message):

        # Parseert en valideert het bericht

        user_id, start_place_ids = message_parser.parse_message(message)

        if not user_id or not start_place_ids:

            return

        # Verwijdert standaard gegevensopslag gebruikersgegevens

        [successes, failures] = data_stores_api.delete_standard_data_stores(user_id, start_place_ids)

        if successes:

            await message.reply(f"Verwijderde standaard gegevensopslaggegevens voor " +

                               f"gebruikers-ID: {user_id}, gegevens: {dict(successes)}")

        if failures:

            await message.reply(f"Kon standaard gegevensopslaggegevens niet verwijderen voor " +

                               f"gebruikers-ID: {user_id}, gegevens: {dict(failures)}")

        # Verwijdert geordende gegevensopslag gebruikersgegevens

        [successes, failures] = data_stores_api.delete_ordered_data_stores(user_id, start_place_ids)

        if successes:

            await message.reply(f"Verwijderde geordende gegevensopslaggegevens voor " +

                               f"gebruikers-ID: {user_id}, gegevens: {dict(successes)}")

        if failures:

            await message.reply(f"Kon geordende gegevensopslaggegevens niet verwijderen voor " +

                               f"gebruikers-ID: {user_id}, gegevens: {dict(failures)}")

    client.run(bot_config.BOT_TOKEN)

if __name__ == "__main__":

    run()

```

3.

Op het bot_config.py -bestand voor de hoofdconfiguratie van de bot:

1.

Stel BOT_TOKEN  in op de token die door je bot is gegenereerd.

2.

Stel OPEN_CLOUD_API_KEY  in als de API-sleutel die je hebt aangemaakt.

3.

Stel ROBLOX_WEBHOOK_SECRET  in als het geheim dat je hebt ingesteld bij het configureren van de webhook op het Creator Dashboard.

4.

In de woordenboeken STANDARD_DATA_STORE_ENTRIES  en ORDERED_DATA_STORE_ENTRIES  voor het lokaliseren van de gegevensopslag van elk record dat moet worden verwijderd:

1.

Voeg je gekopieerde Start Place ID's toe als sleutels.

2.

Voeg Universum-ID's toe als het eerste element van de tuplewaarde.

3.

Vervang het tweede element van de tuple door de naam, scope, invoersleutelnaam en bijbehorende gebruikers-ID van je gegevensopslag. Als je een andere gegevensstructuur gebruikt, pas deze dan aan om overeen te komen met je eigen gegevensstructuur.

4.

Voer de volgende opdracht uit om de bot te draaien:

Draai Discord Bot

```

python3 discord_bot.py

```

5.

De bot begint dan te luisteren en verifieert Roblox-webhooks voor verzoeken om het recht op verwijdering en roept de Open Cloud-eindpunt aan voor het verwijderen van de bijbehorende gegevensopslag.

Om constante en veilige uitvoering van de scripts te waarborgen, sla ze op en voer ze lokaal uit. Houd je lokale apparaat of virtuele machine die de scripts draait altijd aan. In het geval dat je apparaat offline gaat, moet je handmatig omgaan met eventuele gemiste berichten tijdens de offline periode en leveringsfouten afhandelen volgens het [herstelbeleid](/docs/nl-nl/cloud/webhooks/webhook-notifications#beleid-voor-herhaalde-afleverfouten) .

## [Test](#test)[](#test)

Je kunt een testbericht maken en uitvoeren om te verifiëren dat je aangepaste programma verzoeken om het recht op verwijdering correct kan afhandelen en PII-gegevens kan verwijderen:

1.

Stuur een HTTP POST -verzoek naar je Discord-webhookserver met de volgende aanvraagbody:

Voorbeeldverzoek

```

curl -X POST {serverUrl}

-H 'Content-Type: application/json'

-d '{

   "embeds":[{

      "title":"RightToErasureRequest",

      "description":"Je hebt een nieuwe melding ontvangen voor het recht op verwijdering voor de gebruikers-ID: {userIds} in de spel(len) met ID's: {gameIds}",

      "footer":{

         "icon_url":"https://create.roblox.com/dashboard/assets/webhooks/roblox_logo_metal.png",

         "text":"Roblox-Signature: {robloxSignature}, Timestamp: {timestamp}"

      }

   }]

}'

```

2.

Als je een webhook-geheim hebt:

1.

Genereer een Roblox-Signature  door HMAC-SHA256-codering toe te passen op je webhook-geheimsleutel.

2.

Stel de huidige tijd in met behulp van de UTC-tijdstempel in seconden als Timestamp .

3.

Stel de description  samen in het volgende formaat:

Formaat beschrijvingsveld

```

{Timestamp}. Je hebt een nieuwe melding ontvangen voor het recht op verwijdering voor de gebruikers-ID: {userId} in de spel(len) met ID's: {gameIds}`.

```

Bijvoorbeeld:

Voorbeeld beschrijvingsveld

```

1683927229. Je hebt een nieuwe melding ontvangen voor het recht op verwijdering voor de gebruikers-ID: 2425654247 in de spel(len) met ID's: 10539205763, 13260950955

```

Je programma zou in staat moeten zijn om te identificeren dat je bericht van de officiële Roblox-bron komt, aangezien je het bericht met je geheim hebt gecodeerd. Het zou dan de PII-gegevens die aan je verzoek zijn gekoppeld, moeten verwijderen.

Voorbeeldbody

```

{

  "embeds": [

    {

      "title": "RightToErasureRequest",

      "description": "Je hebt een nieuwe melding ontvangen voor het recht op verwijdering voor de gebruikers-ID: 2425654247 in de spel(len) met ID's: 10539205763, 13260950955",

      "footer": {

        "icon_url": "https://create.roblox.com/dashboard/assets/webhooks/roblox_logo_metal.png",

        "text": "Roblox-Signature: UIe6GJ78MHCmU/zUKBYP3LV0lAqwWRFR6UEfPt1xBFw=, Timestamp: 1683927229"

      }

    }

  ]

}

```

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
