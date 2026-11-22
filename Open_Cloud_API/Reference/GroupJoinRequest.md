<!-- Source: https://create.roblox.com/docs/cloud/reference/GroupJoinRequest -->

Groups | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/reference/features/groups.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)

# Groups

English

Filter

Filter

GET

Get Group Beta

Engine API

/​cloud/​v2/​groups/​{group_id}

apis.roblox.com

API Key OAuth 2.0 HttpService

GET

List Group Forum Categories Beta

/​cloud/​v2/​groups/​{group_id}/​forum-​categories

apis.roblox.com

API Key OAuth 2.0

GET

List Group Forum Posts Beta

/​cloud/​v2/​groups/​{group_id}/​forum-​categories/​{forum_category_id}/​posts

apis.roblox.com

API Key OAuth 2.0

GET

List Group Forum Comments Beta

/​cloud/​v2/​groups/​{group_id}/​forum-​categories/​{forum_category_id}/​posts/​{post_id}/​comments

apis.roblox.com

API Key OAuth 2.0

GET

List Group Join Requests Beta

/​cloud/​v2/​groups/​{group_id}/​join-​requests

apis.roblox.com

API Key OAuth 2.0 HttpService

POST

Accept Group Join Request Beta

/​cloud/​v2/​groups/​{group_id}/​join-​requests/​{join_request_id}:accept

apis.roblox.com

API Key OAuth 2.0 HttpService

POST

Decline Group Join Request Beta

/​cloud/​v2/​groups/​{group_id}/​join-​requests/​{join_request_id}:decline

apis.roblox.com

API Key OAuth 2.0 HttpService

GET

List Group Memberships Beta

Engine API

/​cloud/​v2/​groups/​{group_id}/​memberships

apis.roblox.com

API Key OAuth 2.0 HttpService

PATCH

Update Group Membership Beta

/​cloud/​v2/​groups/​{group_id}/​memberships/​{membership_id}

apis.roblox.com

API Key OAuth 2.0 HttpService

POST

Assign Role Group Membership Beta

/​cloud/​v2/​groups/​{group_id}/​memberships/​{membership_id}:assignRole

apis.roblox.com

API Key OAuth 2.0 HttpService

POST

Unassign Role Group Membership Beta

/​cloud/​v2/​groups/​{group_id}/​memberships/​{membership_id}:unassignRole

apis.roblox.com

API Key OAuth 2.0 HttpService

GET

List Group Roles Beta

/​cloud/​v2/​groups/​{group_id}/​roles

apis.roblox.com

API Key OAuth 2.0 HttpService

GET

Get Group Role Beta

/​cloud/​v2/​groups/​{group_id}/​roles/​{role_id}

apis.roblox.com

API Key OAuth 2.0 HttpService

PATCH

Sets group status

/​legacy-​groups/​v1/​groups/​{groupId}/​status

apis.roblox.com

API Key OAuth 2.0

GET

List open invitations to a group Beta

/​v2/​groups/​{groupId}/​invitations

groups.roblox.com

Cookie

POST

Invite a user to a group Beta

/​v2/​groups/​{groupId}/​invitations

groups.roblox.com

Cookie

GET

Get an invitation to a group Beta

/​v2/​groups/​{groupId}/​invitations/​{invitationId}

groups.roblox.com

Cookie

PATCH

Accept or decline an invitation to a group (recipient) Beta

/​v2/​groups/​{groupId}/​invitations/​{invitationId}

groups.roblox.com

Cookie

DELETE

Revoke an invitation to a group (member manager) Beta

/​v2/​groups/​{groupId}/​invitations/​{invitationId}

groups.roblox.com

Cookie

GET

List open invitations to a group that grant a role Beta

/​v2/​groups/​{groupId}/​roles/​{roleId}/​invitations

groups.roblox.com

Cookie

GET

Experimental

/​v2/​groups/​{groupId}/​transactions

economy.roblox.com

Cookie

GET

Get the open invitation to a group for a user Beta

/​v2/​groups/​{groupId}/​users/​{userId}/​invitation

groups.roblox.com

Cookie

GET

Experimental

/​v1/​groups/​{groupId}/​addfunds/​allowed

economy.roblox.com

Cookie None

GET

Experimental

/​v1/​groups/​{groupId}/​addfunds/​latest

economy.roblox.com

Cookie None

GET

Gets currency for the specified group. Experimental

/​v1/​groups/​{groupId}/​currency

economy.roblox.com

Cookie None

GET

Gets the latest one-time payout for each requested user. Beta

/​v1/​groups/​{groupId}/​payouts/​latest

groups.roblox.com

Cookie None

GET

Gets suggested one-time payouts for eligible collaborators. Beta

/​v1/​groups/​{groupId}/​payouts/​suggested

groups.roblox.com

Cookie None

GET

Experimental

/​v1/​groups/​{groupId}/​revenue/​summary/​{timeFrame}

economy.roblox.com

Cookie

GET

Gets the robux amount at old dev-ex rate for the specified group. The response field RobuxAt35 is the amount of robux a group has at the dev ex rate of $3.50 per 1000 robux. Experimental

/​v1/​groups/​{groupId}/​snapshot-​robux

economy.roblox.com

Cookie None

GET

Gets the group payout eligibility for a group of users. Experimental

/​v1/​groups/​{groupId}/​users-​payout-​eligibility

economy.roblox.com

Cookie

## Accounts

GET

Operation to Get an Account for a Group. Experimental

/​service-​efficiency-​api/​v1/​accounts/​groups/​{groupId}

apis.roblox.com

API Key OAuth 2.0 Cookie

PUT

Operation to Update an Account for a Group. Experimental

/​service-​efficiency-​api/​v1/​accounts/​groups/​{groupId}

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

Operation to Get Billing Activities Experimental

/​service-​efficiency-​api/​v1/​billing_activities/​groups/​{groupId}

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

Operation to Get Billing Statement for group owned account. Experimental

/​service-​efficiency-​api/​v1/​bills/​groups/​{groupId}

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

Operation to Check the Eligibility of a Group. Experimental

/​service-​efficiency-​api/​v1/​eligibility/​groups/​{groupId}

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

Operation to Get the Service Efficiency Payment Method for a Group. Experimental

/​service-​efficiency-​api/​v1/​payment_profiles/​groups/​{groupId}/​service_efficiency

apis.roblox.com

API Key OAuth 2.0 Cookie

PUT

Operation to Set the Service Efficiency Payment Method for a Group. Experimental

/​service-​efficiency-​api/​v1/​payment_profiles/​groups/​{groupId}/​service_efficiency

apis.roblox.com

API Key OAuth 2.0 Cookie

POST

Operation to Submit a Manual Payment for a Group. Experimental

/​service-​efficiency-​api/​v1/​payments/​groups/​{groupId}

apis.roblox.com

API Key OAuth 2.0 Cookie

## Assets

GET

Gets a list of groups a user can manage games or items for. Experimental

/​v1/​user/​groups/​canmanagegamesoritems

develop.roblox.com

Cookie

## Private servers

PATCH

/​v1/​vip-​servers/​{id}/​permissions

games.roblox.com

Cookie

## Thumbnails

GET

Fetches thumbnail URLs for a list of groups. Ids that do not correspond to groups will be filtered out. Stable

/​v1/​groups/​icons

thumbnails.roblox.com

None

## Universes

GET

Gets experiences created by the specified group id.

/​v2/​groups/​{groupId}/​gamesV2

games.roblox.com

Cookie None

GET

Gets payout-visible universes for a group. Beta

/​v1/​groups/​{groupId}/​payouts/​universes

groups.roblox.com

Cookie None

GET

Gets a list of universes for the given group. Experimental

/​v1/​groups/​{groupId}/​universes

develop.roblox.com

Cookie None

GET

Gets recurring payouts for a group-owned universe. Beta

/​v1/​universes/​{universeId}/​payouts

groups.roblox.com

Cookie

## Users

GET

Gets a list of Groups that a user can manage. Experimental

/​legacy-​develop/​v1/​user/​groups/​canmanage

apis.roblox.com

API Key OAuth 2.0

## Not Recommended

GET

Gets the Group's audit log

Recommended Alternatives

/​legacy-​groups/​v1/​groups/​{groupId}/​audit-​log

apis.roblox.com

API Key OAuth 2.0

PATCH

Updates the groups description

Recommended Alternatives

/​legacy-​groups/​v1/​groups/​{groupId}/​description

apis.roblox.com

API Key OAuth 2.0

PATCH

Updates the group's settings

Recommended Alternatives

/​legacy-​groups/​v1/​groups/​{groupId}/​notification-​preference

apis.roblox.com

API Key OAuth 2.0

GET

Gets the Group's settings

Recommended Alternatives

/​legacy-​groups/​v1/​groups/​{groupId}/​settings

apis.roblox.com

API Key OAuth 2.0

PATCH

Updates the group's settings

Recommended Alternatives

/​legacy-​groups/​v1/​groups/​{groupId}/​settings

apis.roblox.com

API Key OAuth 2.0

POST

Gets group policy info used for compliance.

Recommended Alternatives

/​legacy-​groups/​v1/​groups/​policies

apis.roblox.com

API Key OAuth 2.0

GET

Gets groups that the authenticated user has requested to join

Recommended Alternatives

/​legacy-​groups/​v1/​user/​groups/​pending

apis.roblox.com

API Key OAuth 2.0

GET

Gets experiences created by the specified group id.

Recommended Alternatives

/​v2/​groups/​{groupId}/​games

games.roblox.com

Cookie None

GET

Gets a list of Groups that a user can manage. Experimental

Recommended Alternatives

/​v1/​user/​groups/​canmanage

develop.roblox.com

Cookie

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
