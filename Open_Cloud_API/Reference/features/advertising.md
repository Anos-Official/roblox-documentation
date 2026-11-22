<!-- Source: https://create.roblox.com/docs/cloud/reference/features/advertising -->

Advertising | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/reference/features/advertising.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)

# Advertising

English

Filter

Filter

GET

List advertisable universes Beta

/​ads-​management/​v1/​advertisable-​universes

apis.roblox.com

API Key OAuth 2.0 Cookie

POST

Estimate the addressable audience Experimental

/​ads-​management/​v1/​audience-​estimates

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

List billing accounts Beta

/​ads-​management/​v1/​billing-​accounts

apis.roblox.com

API Key Cookie

GET

Get a billing account Beta

/​ads-​management/​v1/​billing-​accounts/​{id}

apis.roblox.com

API Key Cookie

POST

Preview a Robux-to-ad-credit conversion Experimental

/​ads-​management/​v1/​billing-​accounts/​{id}/​ad-​credit-​conversions:preview

apis.roblox.com

API Key Cookie

GET

List scoped payment activity Experimental

/​ads-​management/​v1/​billing-​accounts/​{id}/​payment-​activities

apis.roblox.com

API Key Cookie

GET

Get campaign options Beta

/​ads-​management/​v1/​campaign-​options

apis.roblox.com

API Key OAuth 2.0 Cookie

POST

Recommend budget and duration Experimental

/​ads-​management/​v1/​campaign-​recommendations

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

List campaigns Beta

/​ads-​management/​v1/​campaigns

apis.roblox.com

API Key OAuth 2.0 Cookie

POST

Create a campaign Beta

/​ads-​management/​v1/​campaigns

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

List a campaign's ads Experimental

/​ads-​management/​v1/​campaigns/​{campaignId}/​ads

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

Get one ad Experimental

/​ads-​management/​v1/​campaigns/​{campaignId}/​ads/​{adId}

apis.roblox.com

API Key OAuth 2.0 Cookie

PATCH

Toggle one ad on or off Experimental

/​ads-​management/​v1/​campaigns/​{campaignId}/​ads/​{adId}

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

Get a campaign Beta

/​ads-​management/​v1/​campaigns/​{id}

apis.roblox.com

API Key OAuth 2.0 Cookie

PATCH

Update a campaign Beta

/​ads-​management/​v1/​campaigns/​{id}

apis.roblox.com

API Key OAuth 2.0 Cookie

POST

Batch get campaign status Beta

/​ads-​management/​v1/​campaigns:batchGetStatus

apis.roblox.com

API Key OAuth 2.0 Cookie

POST

Validate a campaign without creating it Experimental

/​ads-​management/​v1/​campaigns:validate

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

List creatives Beta

/​ads-​management/​v1/​creatives

apis.roblox.com

API Key OAuth 2.0 Cookie

POST

Add an asset to the creative library Experimental

/​ads-​management/​v1/​creatives

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

Get a creative Beta

/​ads-​management/​v1/​creatives/​{id}

apis.roblox.com

API Key OAuth 2.0 Cookie

PATCH

Update a creative Beta

/​ads-​management/​v1/​creatives/​{id}

apis.roblox.com

API Key OAuth 2.0 Cookie

POST

Create a performance estimate Experimental

/​ads-​management/​v1/​performance-​estimates

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

Gets a page of Roblox.AdConfiguration.Api.SponsoredCampaignModel with specified input parameters. Experimental

/​v2/​sponsored-​campaigns

adconfiguration.roblox.com

Cookie

POST

Creates a complete ad. Including ad campaign, ad set, escrow, and the ad. Currently intended for creation of sponsorships only. Experimental

/​v2/​sponsored-​campaigns/​create

adconfiguration.roblox.com

Cookie

GET

Get all asset type IDs that are eligible to be sponsored. Experimental

/​v2/​sponsored-​campaigns/​eligible-​asset-​type-​ids

adconfiguration.roblox.com

Cookie

POST

Returns a collection of Roblox.AdConfiguration.Api.Models.CampaignTargetModel that the user is authorized to sponsor, ordered by most recently advertised Experimental

/​v2/​sponsored-​campaigns/​eligible-​campaign-​targets

adconfiguration.roblox.com

Cookie

GET

Checks whether the targets are eligible for sponsorship, and if the user is authorized to sponsor the targets. Experimental

/​v2/​sponsored-​campaigns/​multi-​get-​can-​user-​sponsor

adconfiguration.roblox.com

Cookie

POST

Stops a sponsored campaign / ad (ad set) from running. Initiated by a user. Experimental

/​v2/​sponsored-​campaigns/​stop

adconfiguration.roblox.com

Cookie

GET

Gets a page of Roblox.AdConfiguration.Api.SponsoredGameV2Model with specified input parameters. Experimental

/​v2/​sponsored-​games

adconfiguration.roblox.com

Cookie

POST

Creates a new sponsored game ad with specified input parameters. Experimental

/​v2/​sponsored-​games/​create

adconfiguration.roblox.com

Cookie

POST

To stop a sponsored-game ad (ad set) from running, initiated by a user. Experimental

/​v2/​sponsored-​games/​stop

adconfiguration.roblox.com

Cookie

GET

Gets a list of universes for the authenticated user, or the given group, ordered by most recently created sponsored game ads. Experimental

/​v2/​sponsored-​games/​universes

adconfiguration.roblox.com

Cookie

POST

Records an ad click.

/​v2/​tracking/​click

adconfiguration.roblox.com

Cookie

POST

Records an ad click.

/​v1/​ads-​tracking/​click

ads.roblox.com

Cookie

GET

Returns the asset information for creating a new sponsored campaign.

/​v1/​sponsored/​catalog-​assets/​{targetId}/​create

ads.roblox.com

Cookie

POST

Records clicks for sponsored games.

/​v1/​sponsored-​games/​click

ads.roblox.com

Cookie

GET

Retrieves sponsored pages to serve to a user on a specific device type in a specific country.

/​v1/​sponsored-​pages

ads.roblox.com

Cookie

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
