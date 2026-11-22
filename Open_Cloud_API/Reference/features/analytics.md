<!-- Source: https://create.roblox.com/docs/cloud/reference/features/analytics -->

Analytics | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/reference/features/analytics.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)

# Analytics

English

Filter

Filter

GET

Returns the alert configurations for a resource. Optionally filter by alert IDs, firing status, severity, or metric name. Experimental

/​analytics-​alert-​control-​plane/​v1/​resource/​{resourceType}/​id/​{resourceId}/​alerts

apis.roblox.com

API Key OAuth 2.0 Cookie None

POST

Creates a new alert configuration for a resource. Experimental

/​analytics-​alert-​control-​plane/​v1/​resource/​{resourceType}/​id/​{resourceId}/​alerts

apis.roblox.com

API Key OAuth 2.0 Cookie None

PATCH

Updates an existing alert configuration. Only the fields included in the request body are changed; omitted fields retain their current values. Experimental

/​analytics-​alert-​control-​plane/​v1/​resource/​{resourceType}/​id/​{resourceId}/​alerts/​{alertId}

apis.roblox.com

API Key OAuth 2.0 Cookie None

DELETE

Deletes an alert configuration. This action is irreversible. Experimental

/​analytics-​alert-​control-​plane/​v1/​resource/​{resourceType}/​id/​{resourceId}/​alerts/​{alertId}

apis.roblox.com

API Key OAuth 2.0 Cookie None

GET

Returns alert incidents for a resource whose active window overlaps the specified time range. An incident is included if it was open at any point between `startTime` and... Experimental

/​analytics-​alert-​control-​plane/​v1/​resource/​{resourceType}/​id/​{resourceId}/​alerts/​incidents

apis.roblox.com

API Key OAuth 2.0 Cookie None

POST

Returns daily benchmark percentiles for a metric, comparing a universe against other experiences on Roblox. Experimental

/​analytics-​benchmark/​v1/​universes/​{universeId}/​benchmarks

apis.roblox.com

API Key OAuth 2.0

POST

Validates a candidate dashboard document. Beta

/​analytics-​custom-​dashboards/​v1/​universes/​{universeId}/​custom-​dashboard-​documents/​validate

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

Lists dashboard metadata for a universe. Beta

/​analytics-​custom-​dashboards/​v1/​universes/​{universeId}/​custom-​dashboards

apis.roblox.com

API Key OAuth 2.0 Cookie

POST

Creates a dashboard. Beta

/​analytics-​custom-​dashboards/​v1/​universes/​{universeId}/​custom-​dashboards

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

Gets the latest published dashboard snapshot. Beta

/​analytics-​custom-​dashboards/​v1/​universes/​{universeId}/​custom-​dashboards/​{dashboardId}

apis.roblox.com

API Key OAuth 2.0 Cookie

POST

Deletes a dashboard. Beta

/​analytics-​custom-​dashboards/​v1/​universes/​{universeId}/​custom-​dashboards/​{dashboardId}/​delete

apis.roblox.com

API Key OAuth 2.0 Cookie

PATCH

Updates dashboard metadata. Beta

/​analytics-​custom-​dashboards/​v1/​universes/​{universeId}/​custom-​dashboards/​{dashboardId}/​metadata

apis.roblox.com

API Key OAuth 2.0 Cookie

POST

Publishes a caller-provided dashboard document. Beta

/​analytics-​custom-​dashboards/​v1/​universes/​{universeId}/​custom-​dashboards/​{dashboardId}/​publish

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

Gets the latest published dashboard snapshot. Beta

/​analytics-​custom-​dashboards/​v1/​universes/​{universeId}/​custom-​dashboards/​capabilities

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

Gets the latest published dashboard snapshot. Beta

/​analytics-​custom-​dashboards/​v1/​universes/​{universeId}/​custom-​dashboards/​pinned

apis.roblox.com

API Key OAuth 2.0 Cookie

POST

Queries dimension values for a universe. Beta

/​analytics-​query-​api/​v1/​universes/​{universeId}/​dimension-​values

apis.roblox.com

API Key OAuth 2.0

POST

Queries time series metric data for a universe. Beta

/​analytics-​query-​api/​v1/​universes/​{universeId}/​metrics

apis.roblox.com

API Key OAuth 2.0

GET

Retrieves the result of a long-running dimension values operation. Beta

/​analytics-​query-​api/​v1/​universes/​{universeId}/​operations/​dimension-​values/​{operationId}

apis.roblox.com

API Key OAuth 2.0

GET

Retrieves the result of a long-running metrics query operation. Beta

/​analytics-​query-​api/​v1/​universes/​{universeId}/​operations/​metrics/​{operationId}

apis.roblox.com

API Key OAuth 2.0

GET

Experimental

/​log-​attribute-​http-​service/​v1/​universe-​regexes

apis.roblox.com

API Key OAuth 2.0 Cookie

POST

Experimental

/​log-​attribute-​http-​service/​v1/​universe-​regexes

apis.roblox.com

API Key OAuth 2.0 Cookie

PUT

Experimental

/​log-​attribute-​http-​service/​v1/​universe-​regexes/​{id}

apis.roblox.com

API Key OAuth 2.0 Cookie

DELETE

Experimental

/​log-​attribute-​http-​service/​v1/​universe-​regexes/​{id}

apis.roblox.com

API Key OAuth 2.0 Cookie

PUT

Experimental

/​log-​attribute-​http-​service/​v1/​universe-​regexes/​{id}/​ignore

apis.roblox.com

API Key OAuth 2.0 Cookie

PUT

Experimental

/​log-​attribute-​http-​service/​v1/​universe-​regexes/​{id}/​reorder

apis.roblox.com

API Key OAuth 2.0 Cookie

GET

Get logs based on message hash ids, keywords, placeVersions, start/end time. Experimental

/​universe-​performance-​raqi/​v1/​events/​logging/​universe/​{universeId}/​log-​details

apis.roblox.com

API Key OAuth 2.0 Cookie

## Notifications

GET

Experimental

/​notifications/​v1/​developer-​analytics/​get-​notifs-​analytics

apis.roblox.com

API Key OAuth 2.0 Cookie

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
