<!-- Source: https://create.roblox.com/docs/en-us/avatar/avatar-generation -->

Photo-to-avatar generation | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/avatar/avatar-generation.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Avatar](/docs/en-us/avatar)

# Photo-to-avatar generation

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/avatar/avatar-generation.md)

The Photo-to-avatar feature is currently in alpha. For the latest information, see the [DevForum announcement](https://devforum.roblox.com/t/early-preview-alpha-release-of-photo-to-avatar-apis/3931624) .

The following guide applies to creators who are familiar with scripting and Roblox Studio and intend to develop games that allow user-generated avatar items.

You can create a game that allows players to generate a fully functional avatar character using a photo and a text prompt.

This process involves the following steps:

1.

Request an avatar generation session.

2.

Prompt the user to take a selfie and generate a 2D preview image of the avatar.

3.

Generate the full avatar character using [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription) .

## [Request an avatar generation session](#request-an-avatar-generation-session)[](#request-an-avatar-generation-session)

To start a photo-to-avatar generation, call [AvatarCreationService:RequestAvatarGenerationSessionAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#RequestAvatarGenerationSessionAsync)  from the server to request a session for the player. A session provides a [Player](/docs/en-us/reference/engine/classes/Player)  with a certain number of avatar previews and avatar generations.

As it may take some time for a session to become available, [AvatarCreationService:RequestAvatarGenerationSessionAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#RequestAvatarGenerationSessionAsync)  returns a [RBXScriptConnection](/docs/en-us/reference/engine/datatypes/RBXScriptConnection)  and a waitTime in seconds. The waitTime can be used to provide the [Player](/docs/en-us/reference/engine/classes/Player)  with information on how long it will take them to be able to start their generations.

Once a session is ready, the callback is invoked with a Dictionary  of information about the session. The Dictionary  includes:

-

SessionId  — Passed as an argument when calling [AvatarCreationService:GenerateAvatar2DPreviewAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#GenerateAvatar2DPreviewAsync)  and [AvatarCreationService:GenerateAvatarAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#GenerateAvatarAsync) .

-

Allowed2DGenerations  — The number of 2D preview generations allowed in a session.

-

Allowed3DGenerations  — The number of avatar generations allowed in a session.

-

SessionTime  — The maximum time for a session in seconds.

## [Prompt selfie and generate 2D preview](#prompt-selfie-and-generate-2d-preview)[](#prompt-selfie-and-generate-2d-preview)

After a session is started, prompt the user to take a selfie and get the fileId string  by calling the [AvatarCreationService:PromptSelectAvatarGenerationImageAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#PromptSelectAvatarGenerationImageAsync)  method on the Server. This fileId will be passed to the [AvatarCreationService:GenerateAvatar2DPreviewAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#GenerateAvatar2DPreviewAsync)  method.

To create a 2D preview image of the avatar call the following methods:

1.

[AvatarCreationService:GenerateAvatar2DPreviewAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#GenerateAvatar2DPreviewAsync)  on the server.

2.

[AvatarCreationService:LoadAvatar2DPreviewAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#LoadAvatar2DPreviewAsync)  on the client.

The [AvatarCreationService:GenerateAvatar2DPreviewAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#GenerateAvatar2DPreviewAsync)  takes the SessionId, fileId and an optional text prompt as input to generate a 2D avatar preview. This method returns a previewId.

This previewId should be sent to the client and can then be used to retrieve the preview as an [EditableImage](/docs/en-us/reference/engine/classes/EditableImage) .

If the user is not satisfied with the generated preview, this workflow can be repeated.

## [Generate the avatar](#generate-the-avatar)[](#generate-the-avatar)

Once the user is satisfied with the preview, you can generate the complete 3D avatar character.

To generate an avatar character:

1.

Call [AvatarCreationService:GenerateAvatarAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#GenerateAvatarAsync)  on the Server with a Dictionary  containing the SessionId and PreviewId.

1.

This method call returns a string  generationId.

2.

Retrieve the generated avatar data as a [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  using the [AvatarCreationService:LoadGeneratedAvatarAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#LoadGeneratedAvatarAsync)  method on both the game server and the client.

3.

Use the Players.CreateHumanoidModelFromDescription  method to create an avatar model from the [HumanoidDescription](/docs/en-us/reference/engine/classes/HumanoidDescription)  to display to the [Player](/docs/en-us/reference/engine/classes/Player) .

Mesh and texture assets are provided as [EditableMesh](/docs/en-us/reference/engine/classes/EditableMesh)  and [EditableImage](/docs/en-us/reference/engine/classes/EditableImage)  objects, respectively, to allow continued editing of the generated avatar. Edits should be made on both the game server and the client copy to keep them in sync for publish.

## [Publish the avatar](#publish-the-avatar)[](#publish-the-avatar)

If the user is satisfied with the resulting avatar it can be published using the [AvatarCreationService:PromptCreateAvatarAsync()](/docs/en-us/reference/engine/classes/AvatarCreationService#PromptCreateAvatarAsync)  method.

For more information, see [in-game creation](/docs/en-us/avatar/in-experience-creation) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
