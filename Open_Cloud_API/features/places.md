<!-- Source: https://create.roblox.com/docs/cloud/features/places -->

Places | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/reference/features/places.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)

# Places

English

Filter

Filter

GET

Get Update Instance Operation Beta

/​cloud/​v2/​universes/​{universe_id}/​places/​{place_id}/​instances/​{instance_id}/​operations/​{operation_id}

apis.roblox.com

API Key HttpService

GET

Endpoint used to fetch all previous contributors of a place. Experimental

/​place-​version-​history-​api/​v1/​{placeId}/​contributors

apis.roblox.com

API Key Cookie

GET

Endpoint used to get place versions, using various filters Experimental

/​place-​version-​history-​api/​v1/​{placeId}/​history

apis.roblox.com

API Key Cookie

POST

Endpoint used to modify the notes of a particular version for a place. Experimental

/​place-​version-​history-​api/​v1/​{placeId}/​version/​{version}/​notes

apis.roblox.com

API Key Cookie

GET

Gets the place configuration for the place with the id placeId Experimental

/​v2/​places/​{placeId}

develop.roblox.com

Cookie

PATCH

Updates the place configuration for the place with the id placeId Experimental

/​v2/​places/​{placeId}

develop.roblox.com

Cookie

## Bans and blocks

GET

List User Restrictions Beta

/​cloud/​v2/​universes/​{universe_id}/​places/​{place_id}/​user-​restrictions

apis.roblox.com

API Key OAuth 2.0 HttpService

GET

Get User Restriction Beta

/​cloud/​v2/​universes/​{universe_id}/​places/​{place_id}/​user-​restrictions/​{user_restriction_id}

apis.roblox.com

API Key OAuth 2.0 HttpService

PATCH

Update User Restriction Beta

/​cloud/​v2/​universes/​{universe_id}/​places/​{place_id}/​user-​restrictions/​{user_restriction_id}

apis.roblox.com

API Key OAuth 2.0 HttpService

## Inventories

GET

Gets Created, MyGames, or OtherGames places inventory for a user

/​v1/​users/​{userId}/​places/​inventory

inventory.roblox.com

Cookie None

## Luau Execution

POST

Create Luau Execution Session Task Stable

/​cloud/​v2/​universes/​{universe_id}/​places/​{place_id}/​luau-​execution-​session-​tasks

apis.roblox.com

API Key HttpService

POST

Create Luau Execution Session Task Stable

/​cloud/​v2/​universes/​{universe_id}/​places/​{place_id}/​versions/​{version_id}/​luau-​execution-​session-​tasks

apis.roblox.com

API Key HttpService

GET

Get Luau Execution Session Task Stable

/​cloud/​v2/​universes/​{universe_id}/​places/​{place_id}/​versions/​{version_id}/​luau-​execution-​sessions/​{luau_execution_session_id}/​tasks/​{task_id}

apis.roblox.com

API Key HttpService

GET

List Luau Execution Session Task Logs Stable

/​cloud/​v2/​universes/​{universe_id}/​places/​{place_id}/​versions/​{version_id}/​luau-​execution-​sessions/​{luau_execution_session_id}/​tasks/​{task_id}/​logs

apis.roblox.com

API Key HttpService

## Team Create

DELETE

Close a game instance that is being used for team testing Experimental

/​legacy-​develop/​v2/​teamtest/​{placeId}

apis.roblox.com

API Key OAuth 2.0

GET

List of users in the active Team Create session Experimental

/​legacy-​develop/​v1/​places/​{placeId}/​teamcreate/​active_session/​members

apis.roblox.com

API Key OAuth 2.0

## Universes

GET

Get Instance Beta

/​cloud/​v2/​universes/​{universe_id}/​places/​{place_id}/​instances/​{instance_id}

apis.roblox.com

API Key HttpService

PATCH

Update Instance Beta

/​cloud/​v2/​universes/​{universe_id}/​places/​{place_id}/​instances/​{instance_id}

apis.roblox.com

API Key HttpService

GET

List Instance Children Beta

/​cloud/​v2/​universes/​{universe_id}/​places/​{place_id}/​instances/​{instance_id}:listChildren

apis.roblox.com

API Key

GET

Get Place Stable

/​cloud/​v2/​universes/​{universeId}/​places/​{placeId}

apis.roblox.com

API Key OAuth 2.0 HttpService

PATCH

Update Place Stable

/​cloud/​v2/​universes/​{universeId}/​places/​{placeId}

apis.roblox.com

API Key OAuth 2.0 HttpService

POST

Invokes Roblox.UniversesApi.CreatePlaceVersionApiKeyOperation operation. Experimental

/​universes/​v1/​{universeId}/​places/​{placeId}/​versions

apis.roblox.com

API Key

GET

/​v2/​games/​{placeId}/​servers/​{serverType}

games.roblox.com

Cookie None

GET

/​v1/​games/​{placeId}/​servers/​{serverType}

games.roblox.com

Cookie None

GET

Get place details Experimental

/​v1/​games/​multiget-​place-​details

games.roblox.com

Cookie

GET

/​v1/​public-​server-​browser-​service/​games/​{placeId}/​servers/​{serverType}

games.roblox.com

Cookie None

GET

Gets a list of places for a universe. Experimental

/​v1/​universes/​{universeId}/​places

develop.roblox.com

None

## Not Recommended

DELETE

Close a game instance that is being used for team testing Experimental

Recommended Alternatives

/​v2/​teamtest/​{placeId}

develop.roblox.com

Cookie

POST

Updates the place configuration for the place with the id placeId Experimental

Recommended Alternatives

/​v1/​places/​{placeId}

develop.roblox.com

Cookie

PATCH

Updates the place configuration for the place with the id placeId Experimental

Recommended Alternatives

/​v1/​places/​{placeId}

develop.roblox.com

Cookie

GET

List of users in the active Team Create session Experimental

Recommended Alternatives

/​v1/​places/​{placeId}/​teamcreate/​active_session/​members

develop.roblox.com

Cookie

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
