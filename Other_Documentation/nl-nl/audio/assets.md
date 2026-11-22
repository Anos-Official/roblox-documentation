<!-- Source: https://create.roblox.com/docs/nl-nl/audio/assets -->

Audio-assets | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Ervaringen](/docs/nl-nl/experiences)
4. /
5. [Audio](/docs/nl-nl/audio)

# Audio-assets

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Je kunt [een breed scala aan](#audio-vinden)  gratis te gebruiken audio-assets vinden in de Creator Store, of je kunt [audio-assets importeren](#audio-importeren)  waarvan je zeker weet dat je toestemming hebt om ze te gebruiken, zoals audio die je zelf maakt. Het [privacy-systeem voor assets](/docs/nl-nl/projects/assets/privacy)  zorgt er automatisch voor dat de ID's van je geïmporteerde audio niet toegankelijk zijn voor gebruikers zonder de juiste toestemming.

## [Audio vinden](#audio-vinden)[](#audio-vinden)

Het [Creator Store](/docs/nl-nl/production/creator-store)  tabblad van de [Toolbox](/docs/nl-nl/projects/assets/toolbox)  bevat een breed scala aan gratis te gebruiken audio-assets gemaakt door Roblox en de Roblox-gemeenschap voor makers om binnen hun games te gebruiken, inclusief meer dan 100.000 professioneel geproduceerde geluidseffecten en muziekstukken van top audio- en muziekpartners.

Om audio-assets in de Creator Store te vinden:

1.

Ga in de Toolbox  naar het Creator Store  tabblad en gebruik vervolgens de categorie-selector dropdown om Audio  te selecteren.

 ![Audio-sectie van de Creator Store in de Toolbox van Studio](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Creator-Store-Audio.png)

2.

Gebruik de zoekfunctie, snelle filteropties en/of geavanceerde filters om de resultaten te verfijnen.

 ![Audio-ontdekkingsopties in de Toolbox van Studio](https://prod.docsiteassets.roblox.com/assets/studio/toolbox/Creator-Store-Audio-Discovery.png)

3.

Klik met de rechtermuisknop op een audio-asset en selecteer Kopieer Asset ID  om de asset ID naar je klembord te kopiëren. Je kunt deze asset ID nu plakken in een [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  object om de [audio af te spelen](/docs/nl-nl/audio/objects) .

Als je op een audio-asset klikt, voegt Studio deze in als een nieuwe [Sound](/docs/nl-nl/reference/engine/classes/Sound)  instantie in het Explorer  venster. Echter, [Sound](/docs/nl-nl/reference/engine/classes/Sound)  objecten hebben niet dezelfde dynamische functionaliteit als [AudioPlayer](/docs/nl-nl/reference/engine/classes/AudioPlayer)  objecten.

## [Audio importeren](#audio-importeren)[](#audio-importeren)

Je kunt aangepaste audio importeren via de [Asset Manager](/docs/nl-nl/projects/assets/manager) , Creator Dashboard en Open Cloud API, zolang je audio aan de volgende vereisten voldoet:

-

Je hebt de wettelijke rechten op die audio-asset.

-

Het voldoet aan de [Gemeenschapsregels](https://en.help.roblox.com/hc/articles/203313410)  en [Gebruiksvoorwaarden](https://en.help.roblox.com/hc/articles/115004647846) .

-

Het is een enkele track/stroom in .mp3 , .ogg , .wav  of .flac  formaat.

-

Het is minder dan 20 MB groot en 7 minuten in duur.

-

De samplefrequentie is minder dan of gelijk aan 48 kHz.

-

De kanalen zijn ingesteld op mono of stereo 2.0, 3.0 of 5.1 surround.

Als je [ID-geverifieerd](/docs/nl-nl/production/publishing/account-verification)  bent, kun je 2.000 gratis audio-assets per 30 dagen importeren; als je niet geverifieerd bent, kun je 100 gratis audio-assets per 30 dagen importeren. Als er een dagelijkse importlimiet bestaat, wordt deze verwijderd en vervangen door een vereenvoudigde maandlimiet.

Studio kent elke nieuwe audio-asset een unieke asset ID  toe die je binnen je games kunt gebruiken om de [audio af te spelen](/docs/nl-nl/audio/objects) .

Asset Manager Creator Dashboard Open Cloud API

Om audio te importeren via de Asset Manager :

1.

Klik op de Importeren  knop.

2.

Selecteer en bevestig de audio-bestanden die je wilt importeren van je lokale systeem.

3.

Zodra je de import bevestigt en de bestanden succesvol zijn geïmporteerd, worden ze weergegeven met een groen vinkje en een voltooid status.

Om het afspeelformaat te standaardiseren en te controleren op corrupte of ongeldige bestanden, transcodeert Studio geïmporteerde audio voordat deze als een asset wordt opgeslagen. Als je een fout ontvangt tijdens het importeren van audio, weigert Studio deze waarschijnlijk tijdens het transcodeerproces. Bovendien genereren sommige oudere audio-tools ongeldige bestandsheaders of frames bij het exporteren.

Als Studio blijft weigeren de audio te importeren die je probeert te importeren, zorg er dan voor dat je audio-tools zijn bijgewerkt en controleer of de audio-bestanden voldoen aan de importvereisten.

Nadat de audio-assets de moderatie hebben doorstaan, kun je ze opnieuw gebruiken in elk project op het platform. Hoewel jij aanvankelijk de enige bent die privé audio-assets kan bekijken en gebruiken, stelt het [privacy-systeem voor assets](/docs/nl-nl/projects/assets/privacy)  je in staat om gebruiksrechten te verlenen aan specifieke vrienden en ervaringen.

## [Zichtbaarheid](#zichtbaarheid)[](#zichtbaarheid)

Wanneer je audio naar Roblox uploadt, wordt het automatisch geclassificeerd als een geluidseffect  of een nummer . Geluidseffecten komen niet in aanmerking om op de detailpagina van de game waarin ze worden gebruikt te verschijnen, maar ze kunnen worden verspreid op de [Creator Store](/docs/nl-nl/production/creator-store) . Een nummer kan  op de detailpagina van de game verschijnen als:

-

Het alle moderatie- en auteursrechtcontroles doorstaat.

-

Het voldoet aan de minimale duur, afspeel (aantal unieke afspeelbeurten) en platformleeftijdseisen.

-

Het heeft een betekenisvolle en geschikte titel.

-

De uploader is [ID-geverifieerd](/docs/nl-nl/production/publishing/account-verification) .

-

De uploader heeft de Roblox [Audio Gebruiksvoorwaarden](https://en.help.roblox.com/hc/en-us/articles/23359485439124-Audio-Upload-License-Agreement)  erkend.

In aanmerking komende nummers worden standaard zichtbaar op de detailpagina van de game wanneer aan de bovenstaande vereisten is voldaan. Je kunt deze zichtbaarheid in- of uitschakelen op de Configureren  pagina van de asset in de [Creator Hub](https://create.roblox.com/) . Je kunt ook de Roblox-gebruikersnamen van nummercomponisten en -samenwerkers toevoegen in het veld Nummerartiest ; als dit veld leeg wordt gelaten, word je als de artiest vermeld.

Zodra een nummer op de detailpagina van de game staat, kunnen spelers op de tegel van het nummer klikken om de detailpagina van het nummer te zien. Hier kunnen ze aanvullende informatie over het nummer bekijken en luisteren naar een preview van 15 seconden.

 ![Nummer preview pagina gelinkt vanaf de detailpagina van een game](https://prod.docsiteassets.roblox.com/assets/publishing/experiences-places-assets/Song-Preview-Details-Page.jpg)

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
