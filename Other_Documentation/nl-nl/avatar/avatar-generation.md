<!-- Source: https://create.roblox.com/docs/nl-nl/avatar/avatar-generation -->

Foto-naar-avatar generatie | Documentatie - Roblox Creator Hub

For Agents | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Meer informatie](/docs/nl-nl)
2. /
3. [Avatar](/docs/nl-nl/avatar)

# Foto-naar-avatar generatie

Nederlands

* Deze inhoud is vertaald met behulp van AI (bèta) en kan fouten bevatten. Klik [hier]  om deze pagina in het Engels te bekijken.

De Foto-naar-avatar functie is momenteel in alpha. Voor de laatste informatie, zie de [DevForum aankondiging](https://devforum.roblox.com/t/early-preview-alpha-release-of-photo-to-avatar-apis/3931624) .

De volgende gids is van toepassing op makers die bekend zijn met scripting en Roblox Studio en van plan zijn spellen te ontwikkelen die gebruikersgegenereerde avataritems toestaan.

Je kunt een spel maken dat spelers in staat stelt een volledig functioneel avatarpersonage te genereren met behulp van een foto en een tekstprompt.

Dit proces omvat de volgende stappen:

1.

Vraag een avatar generatie sessie aan.

2.

Vraag de gebruiker om een selfie te maken en genereer een 2D voorbeeldafbeelding van de avatar.

3.

Genereer het volledige avatarpersonage met behulp van [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription) .

## [Vraag een avatar generatie sessie aan](#vraag-een-avatar-generatie-sessie-aan)[](#vraag-een-avatar-generatie-sessie-aan)

Om een foto-naar-avatar generatie te starten, roep je [AvatarCreationService:RequestAvatarGenerationSessionAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#RequestAvatarGenerationSessionAsync)  aan vanaf de server om een sessie voor de speler aan te vragen. Een sessie biedt een [Player](/docs/nl-nl/reference/engine/classes/Player)  een bepaald aantal avatarvoorbeelden en avatargeneraties.

Aangezien het enige tijd kan duren voordat een sessie beschikbaar is, retourneert [AvatarCreationService:RequestAvatarGenerationSessionAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#RequestAvatarGenerationSessionAsync)  een [RBXScriptConnection](/docs/nl-nl/reference/engine/datatypes/RBXScriptConnection)  en een wachttijd in seconden. De wachttijd kan worden gebruikt om de [Player](/docs/nl-nl/reference/engine/classes/Player)  informatie te geven over hoe lang het zal duren voordat ze hun generaties kunnen starten.

Zodra een sessie klaar is, wordt de callback aangeroepen met een Dictionary  van informatie over de sessie. De Dictionary  bevat:

-

SessionId  — Doorgegeven als een argument bij het aanroepen van [AvatarCreationService:GenerateAvatar2DPreviewAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#GenerateAvatar2DPreviewAsync)  en [AvatarCreationService:GenerateAvatarAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#GenerateAvatarAsync) .

-

Allowed2DGenerations  — Het aantal 2D voorbeeldgeneraties dat is toegestaan in een sessie.

-

Allowed3DGenerations  — Het aantal avatargeneraties dat is toegestaan in een sessie.

-

SessionTime  — De maximale tijd voor een sessie in seconden.

## [Vraag selfie en genereer 2D voorbeeld](#vraag-selfie-en-genereer-2d-voorbeeld)[](#vraag-selfie-en-genereer-2d-voorbeeld)

Nadat een sessie is gestart, vraag je de gebruiker om een selfie te maken en krijg je de fileId string  door de [AvatarCreationService:PromptSelectAvatarGenerationImageAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptSelectAvatarGenerationImageAsync)  methode op de server aan te roepen. Deze fileId zal worden doorgegeven aan de [AvatarCreationService:GenerateAvatar2DPreviewAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#GenerateAvatar2DPreviewAsync)  methode.

Om een 2D voorbeeldafbeelding van de avatar te maken, roep je de volgende methoden aan:

1.

[AvatarCreationService:GenerateAvatar2DPreviewAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#GenerateAvatar2DPreviewAsync)  op de server.

2.

[AvatarCreationService:LoadAvatar2DPreviewAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#LoadAvatar2DPreviewAsync)  op de client.

De [AvatarCreationService:GenerateAvatar2DPreviewAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#GenerateAvatar2DPreviewAsync)  neemt de SessionId, fileId en een optionele tekstprompt als invoer om een 2D avatarvoorbeeld te genereren. Deze methode retourneert een previewId.

Deze previewId moet naar de client worden gestuurd en kan vervolgens worden gebruikt om de preview op te halen als een [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage) .

Als de gebruiker niet tevreden is met de gegenereerde preview, kan deze workflow worden herhaald.

## [Genereer de avatar](#genereer-de-avatar)[](#genereer-de-avatar)

Zodra de gebruiker tevreden is met de preview, kun je het volledige 3D avatarpersonage genereren.

Om een avatarpersonage te genereren:

1.

Roep [AvatarCreationService:GenerateAvatarAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#GenerateAvatarAsync)  op de server aan met een Dictionary  die de SessionId en PreviewId bevat.

1.

Deze methode-aanroep retourneert een string  generationId.

2.

Haal de gegenereerde avatargegevens op als een [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  met behulp van de [AvatarCreationService:LoadGeneratedAvatarAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#LoadGeneratedAvatarAsync)  methode op zowel de game server als de client.

3.

Gebruik de Players.CreateHumanoidModelFromDescription  methode om een avatar model te maken van de [HumanoidDescription](/docs/nl-nl/reference/engine/classes/HumanoidDescription)  om aan de [Player](/docs/nl-nl/reference/engine/classes/Player)  te tonen.

Mesh- en textuurassets worden geleverd als [EditableMesh](/docs/nl-nl/reference/engine/classes/EditableMesh)  en [EditableImage](/docs/nl-nl/reference/engine/classes/EditableImage)  objecten, respectievelijk, om verdere bewerking van de gegenereerde avatar mogelijk te maken. Wijzigingen moeten worden aangebracht op zowel de game server als de clientkopie om ze synchroon te houden voor publicatie.

## [Publiceer de avatar](#publiceer-de-avatar)[](#publiceer-de-avatar)

Als de gebruiker tevreden is met de resulterende avatar, kan deze worden gepubliceerd met behulp van de [AvatarCreationService:PromptCreateAvatarAsync()](/docs/nl-nl/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync)  methode.

Voor meer informatie, zie [in-game creatie](/docs/nl-nl/avatar/in-experience-creation) .

©2026 Roblox Corporation. Roblox, het Roblox-logo en Powering Imagination behoren tot onze geregistreerde en niet-geregistreerde handelsmerken in de VS en andere landen.

[Voorwaarden](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Toegankelijkheid](https://www.roblox.com/info/accessibility) ·[Ondersteuning](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

Nederlands

](https://create.roblox.com/settings/preferences)
