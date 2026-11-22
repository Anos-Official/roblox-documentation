<!-- Source: https://create.roblox.com/docs/nl-nl/production/publishing/account-verification -->

Accountverificatie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Platform](/docs/nl-nl/get-started)
4. /
5. Richtlijnen en beleid

# Accountverificatie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

Accountverificatie  is het proces van het verbinden van je identiteit op Roblox met je echte identiteit, hetzij via een leeftijdscontrole of via een overheidsidentificatie. Wanneer je je account verifieert, kun je meer van elk type asset distribueren en hun vindbaarheid binnen de [Creator Store](/docs/nl-nl/production/creator-store)  maximaliseren, audio-assets van minder dan 10 seconden distribueren, je [plugins](/docs/nl-nl/studio/plugins)  monetiseren en toegang krijgen tot leeftijdsgebonden Studio-functies zoals [stemchat](/docs/nl-nl/chat/voice-chat) .

Om geprijsde assets te verkopen, moet je verifiëren met een [overheidsidentificatie](/docs/nl-nl/production/publishing/account-verification#verifi%C3%ABren-via-overheidsidentificatie)  en een verkopersaccount aanmaken. Voor meer informatie, zie [Creator Store - Assets distribueren en verkopen](/docs/nl-nl/production/creator-store#verspreiden-en-verkopen-van-assets) .

## [Verifiëren via overheidsidentificatie](#verifiëren-via-overheidsidentificatie)[](#verifiëren-via-overheidsidentificatie)

Om je account met deze methode te verifiëren, moet je:

-

Ten minste 13 jaar oud zijn.

-

Een door de overheid uitgegeven foto-ID hebben met je afbeelding erop, zoals een rijbewijs, paspoort of verblijfsvergunning.

-

Een mobiel apparaat hebben met een camera die foto's van je gezicht en ID kan maken.

Roblox gebruikt geavanceerde beeldverwerkingstechnologie om ervoor te zorgen dat je documenten legitiem zijn. Voor meer informatie over het verificatieproces van accounts, zie [Leeftijd ID Verificatie FAQs](https://en.help.roblox.com/hc/en-us/articles/4407276151188) . Om te leren hoe Roblox je persoonlijke en biometrische gegevens verwerkt, verwijs naar het [Roblox Privacybeleid](https://en.help.roblox.com/hc/en-us/articles/115004630823-Roblox-Privacy-and-Cookie-Policy)  en de [Roblox Facial Media Capture Notice](https://en.help.roblox.com/hc/en-us/articles/4412863575316-Roblox-Facial-Media-Capture-Privacy-Notice) .

Om je account te verifiëren met een door de overheid uitgegeven ID:

1.

Navigeer naar Instellingen , hetzij op [roblox.com](https://www.roblox.com/home)  of op de Roblox-app.

1.

In webbrowser:  Klik in de rechterbovenhoek op het tandwielpictogram om een contextueel dropdownmenu weer te geven, selecteer vervolgens [Instellingen](https://www.roblox.com/my/account#!/info) .

 ![Accountinstellingenmenu op roblox.com](https://prod.docsiteassets.roblox.com/assets/publishing/account-verification/Account-Settings.png)

1.

In de Roblox-app:  Klik in de rechterbenedenhoek op het ⋯ Meer -pictogram en selecteer Instellingen .

2.

Selecteer het tabblad Accountinformatie .

3.

Klik onder je verjaardag op Doorgaan met ID .

 ![Optie om leeftijd te verifiëren met selfie of ID](https://prod.docsiteassets.roblox.com/assets/publishing/account-verification/Verify-Birthday.png)

4.

Volg de instructies om de ID-verificatiestroom te voltooien.

 ![Optie om leeftijd te verifiëren met selfie of ID](https://prod.docsiteassets.roblox.com/assets/publishing/account-verification/Verify-With-ID.png)

1.

Sta camera-toegang toe.

2.

Scan je ID-document. Roblox detecteert welk type document je hebt.

1.

Als er een streepjescode op de achterkant staat, scan en maak een afbeelding van de achterkant van je ID.

3.

Maak een foto van jezelf. Deze foto wordt gebruikt om te verifiëren dat je dezelfde persoon bent als degene op je foto-ID.

5.

Wanneer de verificatie is voltooid, wordt je geverifieerde verjaardag weergegeven in Instellingen  > Accountinformatie . Verificatie kan enkele minuten duren.

## [Controleer verificatiestatus via script](#controleer-verificatiestatus-via-script)[](#controleer-verificatiestatus-via-script)

Binnen een [Script](/docs/nl-nl/reference/engine/classes/Script)  laat de [Player:IsVerified()](/docs/nl-nl/reference/engine/classes/Player#IsVerified) -methode je de verificatiestatus van gebruikers die toegang krijgen tot je games controleren, zodat je de toegang tot specifieke inhoud, gerangschikte wachtrijen of zelfs het spel zelf kunt beperken. Omdat gebruikers die hun accounts verifiëren hun Roblox-identiteit verbinden met hun echte identiteit, is de kans veel kleiner dat ze vals spelen, spammen of anderszins het risico lopen geblokkeerd te worden van je spel, waardoor deze methode bijzonder nuttig is voor competitieve en gerangschikte games.

Het volgende script controleert de verificatiestatus van elke speler wanneer ze het spel betreden. Als ze hun account hebben geverifieerd, print de console true .

```

local Players = game:GetService("Players")

local function onPlayerAdded(player)

	print(player:IsVerified())

end

for _, player in Players:GetPlayers() do

	onPlayerAdded(player)

end

Players.PlayerAdded:Connect(onPlayerAdded)

```

De methode accepteert ook een optionele [Enum.VerifiedLevel](/docs/nl-nl/reference/engine/enums/VerifiedLevel)  parameter als je meer gedetailleerde toegang wilt:

-

[Enum.VerifiedLevel.Low](/docs/nl-nl/reference/engine/enums/VerifiedLevel#Low)  — Nuttig voor het beperken van standaardfuncties zoals in-game trading, waar het doel is om alternatieve accounts te ontmoedigen.

-

[Enum.VerifiedLevel.High](/docs/nl-nl/reference/engine/enums/VerifiedLevel#High)  — Nuttig voor het beperken van functies met hoge inzet zoals gerangschikte matchmaking-wachtrijen, waar je de hoogste mate van integriteit wilt.

Als je geen parameter doorgeeft, is de standaardwaarde van de methode [Enum.VerifiedLevel.Low](/docs/nl-nl/reference/engine/enums/VerifiedLevel#Low) , zodat bestaande implementaties blijven werken zonder wijzigingen.

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
