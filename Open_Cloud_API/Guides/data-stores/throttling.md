<!-- Source: https://create.roblox.com/docs/cloud/guides/data-stores/throttling -->

Rate limits and throttling | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/guides/data-stores/throttling.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)
4. /
5. [Data stores](/docs/cloud/guides/data-stores)

# Rate limits and throttling

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/guides/data-stores/throttling.md)

The below limits apply only to [Open Cloud v1](/docs/cloud/reference/features/storage#Datastores_ListDatastoresAsync)  endpoints. For [Open Cloud v2](/docs/cloud/reference/features/storage#Cloud_ListDataStores)  rate limits, see [Data store error codes and limits](/docs/cloud-services/data-stores/error-codes-and-limits#access-limits) .

The [Data Stores API](/docs/cloud/reference/features/storage)  enforces two types of throttling: requests per minute  and throughput . Each game allows a certain number of requests per minute and a certain amount of data per minute. These limits are enforced for the universe (experience / game) regardless of the number of API keys used.

Unlike the Engine API, these limits do not  scale based on user count. Exceeding either one causes the endpoint to return 429 Too Many Requests .

## [Legacy standard data stores throttling limits](#legacy-standard-data-stores-throttling-limits)[](#legacy-standard-data-stores-throttling-limits)

These limits apply to the legacy /datastores/v1/  endpoints.

| Request type | | Method | | Throttle limits |
| --- | --- |
| Write | |
-

Create Data Store Entry

-

Delete Data Store Entry

-

Update Data Store Entry

-

Increment Data Store Entry

 | |
-

10 MB/minute/universe write throughput

-

300 requests/minute/universe

 |
| Read | |
-

List Data Stores

-

List Data Store Entries

-

Get Data Store Entry

-

List Data Store Entry Revisions

 | |
-

20 MB/minute/universe read throughput

-

300 requests/minute/universe

 |
| Delete | |
-

Delete Data Store

-

Undelete Data Store

 | |
-

300 requests/minute/universe

 |

## [Legacy ordered data stores throttling limits](#legacy-ordered-data-stores-throttling-limits)[](#legacy-ordered-data-stores-throttling-limits)

These limits apply to the legacy /ordered-data-stores/v1/  endpoints.

| Request type | | Method | | Throttle limits |
| Write | |
-

Create Ordered Data Store Entry

-

Delete Ordered Data Store Entry

-

Update Ordered Data Store Entry

-

Increment Ordered Data Store Entry

 | |
-

300 requests/minute/universe

 |
| Read | |
-

List Ordered Data Store Entries

-

Get Ordered Data Store Entry

 | |
-

300 requests/minute/universe

 |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
