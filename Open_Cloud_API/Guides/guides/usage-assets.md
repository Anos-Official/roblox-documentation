<!-- Source: https://create.roblox.com/docs/en-us/cloud/guides/usage-assets -->

Usage guide for assets | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/guides/usage-assets.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Open Cloud API](/docs/en-us/cloud)

# Usage guide for assets

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/guides/usage-assets.md)

The [Assets API](/docs/en-us/reference/cloud/assets/v1)  of Open Cloud allows you to upload and update assets with a single HTTP request rather than manually importing them to Studio. This API supports:

-

Uploading new assets.

-

Updating existing assets with version control.

-

Updating asset metadata, including descriptions, display names, icons, and previews. For place icons and experience detail page thumbnails, see [Manage experience icons and thumbnails](/docs/en-us/cloud/guides/experience-icons-and-thumbnails) .

-

Managing asset versions, such as rolling back to a specified previous version.

-

Checking existing information of an asset, including metadata, versions, and any in-process updating operations.

This API contains beta endpoints that might be subject to changes for future releases.

## [Supported asset types and limits](#supported-asset-types-and-limits)[](#supported-asset-types-and-limits)

For endpoints that don't create a new asset or update the content of existing assets, there are no restrictions and limits. However, the asset content uploading functionality powered by the Create Asset  and Update Asset  endpoints only supports limited types of assets with restrictions. For each call, you can only create or update one asset with the file size up to 20 MB with the following limits:

Updating asset metadata using the Update Asset  endpoint is not subject to the following limits.

| Asset type | | Format | | Content type | | Restrictions |
| --- | --- |
| [Animation](/docs/en-us/animation) | |
-

.rbxm

-

.rbxmx

 | |
-

model/x-rbxm

-

model/x-rbxm

 | |
-

.rbxm  or .rbxmx  files edited outside of [Roblox Studio](/docs/en-us/studio/setup)  might not upload or function.

 |
| [Audio](/docs/en-us/audio/assets) | |
-

.mp3

-

.ogg

-

.wav

-

.flac

 | |
-

audio/mpeg

-

audio/ogg

-

audio/wav

-

audio/flac

 | |
-

Up to 7 minutes of duration.

-

Up to 100 uploads per month if you're ID-verified.

-

Up to 10 total uploads per month if you aren't ID-verified.

-

Not available for updating.

 |
| [Decal, Image](/docs/en-us/parts/textures-decals) | |
-

.png

-

.jpeg

-

.bmp

-

.tga

 | |
-

image/png

-

image/jpeg

-

image/bmp

-

image/tga

 | |
-

Must be smaller than 8000x8000 pixels.

-

Not available for updating.

 |
| [Mesh](/docs/en-us/parts/meshes) | |

Roblox only

 | |
-

model/x-file-mesh-data

 | |
-

Only content downloaded from [Asset delivery API](/docs/en-us/cloud/reference/domains/assetdelivery)  is accepted. If you are not trying to download and re-upload meshes, then use [Importer](/docs/en-us/studio/importer)  to import meshes instead.

-

Not available for updating.

 |
| [Model](/docs/en-us/parts/models) | |
-

.fbx

-

.gltf

-

.glb

-

.rbxm

-

.rbxmx

 | |
-

model/fbx

-

model/gltf+json

-

model/gltf-binary

-

model/x-rbxm

-

model/x-rbxm

 | |
-

Imports custom 3D models as a [Model](/docs/en-us/reference/engine/classes/Model)  container containing one or more [MeshPart](/docs/en-us/reference/engine/classes/MeshPart)  objects.

-

Depending on your use-case, consider uploading custom 3D models manually using the [Importer](/docs/en-us/studio/importer) .

-

The Importer provides a 3D preview, various error-checking, and many customizable import settings.

-

.rbxm  or .rbxmx  files edited outside of [Roblox Studio](/docs/en-us/studio/setup)  might not upload or function.

-

Will be uploaded as [packages](/docs/en-us/projects/assets/packages)

 |
| [Video](/docs/en-us/ui/video-frames) | |
-

.mp4

-

.mov

 | |
-

video/mp4

-

video/mov

 | |
-

Up to 5 minutes of duration.

-

Up to 4096x2160 resolution.

-

Up to 3.75 GB.

-

Up to 20 uploads per day if you're 13+ and ID-verified.

-

Not available for updating.

 |

## [Security permissions](#security-permissions)[](#security-permissions)

The API supports both first-party use with [API key authorization](/docs/en-us/cloud/auth/api-keys)  and third-party use in [OAuth 2 applications](/docs/en-us/cloud/auth/oauth2-overview) . Each way requires different security permission settings.

### [API keys](#api-keys)[](#api-keys)

To use the API in your own scripts or tools, you need to [create an API key](/docs/en-us/cloud/auth/api-keys#create-api-keys)  for authorization and security.

To create an API key for managing group assets, you must have the corresponding permissions. For more information on granting group permissions, see [Group roles and permissions](/docs/en-us/projects/groups#roles-and-permissions) .

When creating an API key, make sure to add the following permissions:

1.

Add assets  to Access Permissions .

2.

Add Read  and Write  operation permissions to your selected game, depending on the required scopes of the endpoints you plan to call.

Once you have the API key, copy it to the x-api-key  request header. All endpoints require the x-api-key  request header.

Example API Request Header

```

--header 'x-api-key: ${ApiKey}' \

```

### [OAuth 2.0 apps](#oauth-20-apps)[](#oauth-20-apps)

To use the API for a third-party OAuth 2.0 application, add the asset:read  and asset:write  permission scopes when [registering your app](/docs/en-us/cloud/auth/oauth2-registration#add-permissions) . Choose these scopes based on the requirements of the endpoints you plan to use.

## [Create a new asset](#create-a-new-asset)[](#create-a-new-asset)

To upload a new asset by an HTTP request:

1.

Copy the API key to the x-api-key  request header of the [Create Asset](/docs/en-us/reference/cloud/assets/v1#POST-v1-assets)  endpoint.

2.

In your request:

1.

Specify the target [asset type](#supported-asset-types-and-limits) .

2.

Add your asset name and description.

3.

Add the creator information.

-

If you want to create the asset on your own behalf , add your user ID. You can find your user ID on the URL of your Roblox profile. For example, for https://www.roblox.com/users/1234567/profile , your user ID is 1234567 .

-

If you want to create the asset as a group asset , add the group ID of your group. You can find the group ID on the URL of your group's page. For example, for https://www.roblox.com/groups/7654321/example-group#!/ , the group ID is 7654321 .

4.

Add the file path and content type of your asset.

Example Request for Create Asset

```

curl --location 'https://apis.roblox.com/assets/v1/assets' \

--header 'x-api-key: ${ApiKey}' \

--form 'request="{

  \"assetType\": \"Model\",

  \"displayName\": \"Name\",

  \"description\": \"This is a description\",

  \"creationContext\": {

    \"creator\": {

      \"userId\": \"${userId}\" # Use groupId for creating a group asset

    }

  }

}"' \

--form 'fileContent=@"/filepath/model.fbx";type=model/fbx'

```

## [Update an existing asset](#update-an-existing-asset)[](#update-an-existing-asset)

Asset updating is powered by beta endpoints that might be subject to changes for future releases.

To update an existing asset by an HTTP request:

1.

Copy the API key to the x-api-key  request header of the [Update Asset](/docs/en-us/reference/cloud/assets/v1#PATCH-v1-assets-_asset_)  endpoint.

2.

Add the asset type and asset ID in your request. To copy your asset ID:

1.

Navigate to the [Creation](https://create.roblox.com/dashboard/creations)  page of the Creator Dashboard .

2.

Select the Development Items  category.

3.

Select the category of your asset and find the target asset.

4.

Hover over the thumbnail of the target asset and click the ⋯  button to display a list of options, then select Copy Asset ID  from the list.

Asset Content Metadata Content and Metadata

Currently, you can only update the asset content for .fbx  files. The update creates a new version.

Example Request for Updating Asset Content

```

curl --location --request PATCH 'https://apis.roblox.com/assets/v1/assets/{assetId}' \

--header 'x-api-key: {apiKey}' \

--form 'request={

    \"assetType\": \"{assetType}\",

    \"assetId\": \"{assetId}\",

    \"creationContext\": {

        \"creator\": {

            \"userId\": {userId}

        },

        \"expectedPrice\":{expectedPrice}

    },

}' \

--form 'fileContent=@"{file-path}"'

```

To update a place icon or experience detail page thumbnails, see [Manage experience icons and thumbnails](/docs/en-us/cloud/guides/experience-icons-and-thumbnails) .

## [Retrieve asset operation status](#retrieve-asset-operation-status)[](#retrieve-asset-operation-status)

If your request for creating a new asset or updating an existing asset succeeds, it returns an Operation ID  in the format of { "path": "operations/${operationId}" } . You can use it to check the status and result of your upload with the following steps:

1.

Copy the API key to the x-api-key  request header of the [Get Operation](/docs/en-us/reference/cloud/assets/v1#GET-v1-operations-_operationId_)  method and send the request, like the following code sample:

Example Request for Get Operation

```

curl --location 'https://apis.roblox.com/assets/v1/operations/{operationId}' \

--header 'x-api-key: {$ApiKey}'

```

2.

If your request succeeds, it returns an Operation  object, either including a response  representing the uploaded asset information or a status  explaining why the asset upload fails as the following code sample shows:

Example Response for Get Operation

```

{

  "path": "operations/{operationId}",

  "done": true,

  "response": {

    "@type": "type.googleapis.com/roblox.open_cloud.assets.v1.Asset",

    "path": "assets/2205400862",

    "revisionId": "1",

    "revisionCreateTime": "2023-03-02T22:27:04.062164400Z",

    "assetId": "2205400862",

    "displayName": "Name",

    "description": "This is a description",

    "assetType": "ASSET_TYPE_DECAL",

    "creationContext": {

      "creator": {

        "userId": "11112938575"

      }

    },

    "moderationResult": {

      "moderationState": "MODERATION_STATE_APPROVED"

    }

  }

}

```

3.

OPTIONAL

 Check the created asset on your Roblox account.

1.

Navigate to the Inventory  page of your [Roblox account](https://www.roblox.com/home) .

2.

Select the Category  of the asset that you want to check.

3.

Find the target asset and click its thumbnail to view the asset.

## [Use uploaded assets in Studio](#use-uploaded-assets-in-studio)[](#use-uploaded-assets-in-studio)

An asset that you upload belongs to the user or group in the creationContext  of your request, so it's available in Studio like any other asset that creator owns:

-

Insert it from the [Toolbox](/docs/en-us/projects/assets/toolbox)  or the [Asset Manager](/docs/en-us/projects/assets/manager#inventory-sorting) .

-

Models upload as [packages](/docs/en-us/projects/assets/packages) , so check Inventory  ⟩ My Packages  in the Toolbox (or Creations  ⟩ Group Packages  if a group owns them).

-

To use an asset in a property, enter rbxassetid://  followed by the assetId  from the operation response in the [Properties](/docs/en-us/studio/properties)  window. In a script, assign that string to a string property such as [AudioPlayer.Asset](/docs/en-us/reference/engine/classes/AudioPlayer#Asset) , or pass the assetId  to [Content.fromAssetId()](/docs/en-us/reference/engine/datatypes/Content#fromAssetId)  for a property of type [Content](/docs/en-us/reference/engine/datatypes/Content) , such as [Decal.ColorMapContent](/docs/en-us/reference/engine/classes/Decal#ColorMapContent) . For more information, see [rbxassetid](/docs/en-us/projects/assets#rbxassetid) .

## [Add assets API to OAuth 2.0 apps](#add-assets-api-to-oauth-20-apps)[](#add-assets-api-to-oauth-20-apps)

You can create [OAuth 2.0 applications](/docs/en-us/cloud/auth/oauth2-overview)  supporting Assets API to allow your users to upload and update assets to Roblox.

Third-Party app support through OAuth 2.0 is a Beta feature that might be subject to changes for future releases.

To use Assets API for your application and request permissions from your users, perform the following settings:

1.

When [registering your application](/docs/en-us/cloud/auth/oauth2-registration#register-your-app) , under Permissions , select asset:read  and asset:write  scopes.

2.

When [implementing the authorization flow](/docs/en-us/cloud/auth/oauth2-overview#implement-authorization-flows) , include asset:read  and asset:write  as the scope parameters of the authorization URL that redirects users back to your application, like the following example:

```

https://apis.roblox.com/oauth/v1/authorize?client_id=819547628404595165403873012&redirect_uri=https://my-app.com/redirect&scope=asset:read+asset:write&response_type=Code&prompts=login+consent&nonce=12345&state=6789

```

3.

When sending the request, include the access token in the authorization header and the form data of the asset content to create or update in the request URI in. The following example shows a sample request for uploading a new asset:

Example Request

```

curl --location --request POST 'https://apis.roblox.com/assets/v1/assets' \

--header 'Authorization: Bearer <access_token>' \

--header 'Content-Type: application/json' \

--form 'request="{

  \"assetType\": \"Decal\",

  \"displayName\": \"DecalDemo123\",

  \"description\": \"This is a description\",

  \"creationContext\": {

    \"creator\": {

    \"userId\": \"<user_id>\"

    }

  }

}"' \

--form 'fileContent=@"/filepath/p1.png"'

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
