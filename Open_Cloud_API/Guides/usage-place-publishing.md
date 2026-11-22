<!-- Source: https://create.roblox.com/docs/cloud/guides/usage-place-publishing -->

Usage guide for place publishing | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/guides/usage-place-publishing.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)

# Usage guide for place publishing

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/guides/usage-place-publishing.md)

The [Assets API](/docs/cloud/reference/features/assets)  offers similar functionality to [publishing to Roblox](/docs/production/publishing/publish-games-and-places)  in Studio, with extra permission control and automation in continuous release workflows. You can use this API to update existing places of a game to a new version, making it useful for automating your publishing workflow. For example, you can call this API from a GitHub action and have it automatically push a binary place file to Roblox after successful integration testing.

Because the Assets API processes uploads asynchronously, publishing a place returns an Operation ID  rather than an immediate version number. You then poll the operation until it completes to confirm the publish succeeded.

## [Limitations](#limitations)[](#limitations)

-

This API only supports HTTPS requests.

-

The place publishing API doesn't update certain instance types. If your game contains [EditableImage](/docs/reference/engine/classes/EditableImage) , [EditableMesh](/docs/reference/engine/classes/EditableMesh) , [PartOperation](/docs/reference/engine/classes/PartOperation) , [SurfaceAppearance](/docs/reference/engine/classes/SurfaceAppearance) , or [BaseWrap](/docs/reference/engine/classes/BaseWrap)  instances, publish from Studio after modifying them.

## [Places on Roblox](#places-on-roblox)[](#places-on-roblox)

Games on Roblox can have multiple places, with one starting place  as the user entry point of your game and optional other places that you can [teleport users between](/docs/projects/teleport) . You can use the API to publish either the starting place or other places of your game with version control.

Before you can update an existing place of a game, you need the place's Place ID . The Assets API treats a place as an asset, so the Place ID  is also the place's asset ID .

## [Publish a place](#publish-a-place)[](#publish-a-place)

To publish an existing place of a game with the [Update Asset](/docs/cloud/reference/features/assets#Assets_UpdateAsset)  endpoint:

1.

[Create an API key](/docs/cloud/auth/api-keys#create-api-keys)  on the Creator Dashboard . Make sure you perform the following settings:

1.

Add assets  to Access Permissions .

2.

Add Read  and Write  operations to your selected game.

2.

Get the Place ID  of the place that you want to update.

1.

Navigate to the [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

2.

Find the game with the place that you want to update and click its thumbnail.

3.

On the left navigation menu, click the Places  tab.

4.

Find the place that you want to update and click its thumbnail.

5.

The Place ID  is in the redirected URL. For example, in the URL https://create.roblox.com/dashboard/creations/experiences/0000000/places/111111/configure , the Place ID  is 111111 .

3.

Add the API key in the x-api-key  header of a PATCH  request to the endpoint. Pass the place file in the fileContent  form field, and set assetType  to Place  and published  to true  in the request  form field. You must explicitly set published  to true  to publish the new content; otherwise the upload saves as a new, unpublished asset version. The following two example requests reference a Roblox XML place file (.rbxlx ) and a binary place file (.rbxl ).

XML Place File Request

```

$ curl --verbose --location --request PATCH 'https://apis.roblox.com/assets/v1/assets/{placeId}' \

--header 'x-api-key: <your-api-key>' \

--form 'request={"assetId": {placeId}, "assetType": "Place", "published": true}' \

--form 'fileContent=@/home/placefiles/place1.rbxlx;type=application/xml'

```

Binary Place File Request

```

$ curl --verbose --location --request PATCH 'https://apis.roblox.com/assets/v1/assets/{placeId}' \

--header 'x-api-key: <your-api-key>' \

--form 'request={"assetId": {placeId}, "assetType": "Place", "published": true}' \

--form 'fileContent=@/home/placefiles/place1.rbxl;type=application/octet-stream'

```

To run the commands, replace {placeId}  with the actual Place ID  of the place that you want to publish, and update the fileContent  path to point to your place file.

4.

If you send your request correctly, you receive a success response body with an Operation ID  in the following format:

Example Response Body

```

{ "path": "operations/{operationId}" }

```

This indicates that Roblox accepted your upload and is processing it asynchronously. Continue to the next section to check the result.

## [Check the publish operation status](#check-the-publish-operation-status)[](#check-the-publish-operation-status)

Because the Update Asset endpoint processes your place upload asynchronously, use the returned Operation ID  to confirm that the publish completed successfully:

1.

Add the API key in the x-api-key  header of a GET  request to the [Get Operation](/docs/cloud/reference/features/assets#Assets_GetOperation)  endpoint:

Example Request for Get Operation

```

$ curl --verbose --location 'https://apis.roblox.com/assets/v1/operations/{operationId}' \

--header 'x-api-key: <your-api-key>'

```

Replace {operationId}  with the Operation ID  from the previous step.

2.

Poll this endpoint until the response's done  field is true . While done  is false , the operation is still in progress.

Example Response Body

```

{

  "path": "operations/{operationId}",

  "done": true,

  "response": {

    "path": "assets/{placeId}",

    "revisionId": "{versionNumber}",

    "isPublished": true

  }

}

```

-

If the operation succeeds, response  contains the updated place. revisionId  is the new version number, and isPublished  is true  when that version is published.

-

If the operation fails, it contains an error  field instead of response . The error  field is a Status  object whose code  and message  explain why the publish failed.

3.

OPTIONAL

 Verify the upload in Studio or on [Creator Dashboard](https://create.roblox.com/dashboard/creations) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
