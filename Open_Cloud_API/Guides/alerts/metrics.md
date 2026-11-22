<!-- Source: https://create.roblox.com/docs/cloud/guides/alerts/metrics -->

Supported alert metrics and dimensions | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud/guides/alerts/metrics.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Open Cloud API](/docs/en-us/cloud)
4. /
5. [Analytics alerts](/docs/cloud/guides/alerts)

# Supported alert metrics and dimensions

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud/guides/alerts/metrics.md)

Analytics alerts support the following metrics and dimensions. All values are case-sensitive. These same supported metrics and dimensions apply whether you use the [Alerts](/docs/production/analytics/alerts)  dashboard or the [API](/docs/cloud/guides/alerts) .

## [Supported metrics](#supported-metrics)[](#supported-metrics)

### [Alert](#alert)[](#alert)

| Name | | Metric | | Supported dimensions |
| --- | --- |
| Client CPU time | | ClientCpuTimeAvg
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

ClientCpuTimeCategory

-

ClientCpuTimeSubCategory

-

MemoryGroup

-

OperatingSystem

-

Place  (filter only)

-

Platform

 |
| Client crash count | | ClientCrashCount
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

MemoryGroup

-

OperatingSystem

-

Place  (filter only)

-

Platform

 |
| Client crash rate | | ClientCrashRate15m
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

MemoryGroup

-

OperatingSystem

-

Place  (filter only)

-

Platform

 |
| Client frame rate | | ClientFpsAvg
ClientFpsP10
ClientFpsP50
ClientFpsP90
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

MemoryGroup

-

OperatingSystem

-

Place  (filter only)

-

Platform

 |
| Client memory usage | | ClientMemoryUsageAvg
ClientMemoryUsageP10
ClientMemoryUsageP50
ClientMemoryUsageP90
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

MemoryGroup

-

OperatingSystem

-

Place  (filter only)

-

Platform

 |
| Client memory usage percentage | | ClientMemoryUsagePercentageAvg
ClientMemoryUsagePercentageP10
ClientMemoryUsagePercentageP50
ClientMemoryUsagePercentageP90
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

MemoryGroup

-

OperatingSystem

-

Place  (filter only)

-

Platform

 |
| Cross-server messaging fanout ratio | | CsmFanoutRatio
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |  |
| Cross-server messaging connected game servers | | CsmGameServersConnectedCount
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |  |
| Cross-server messaging message size | | CsmMessageSizeBytes
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |  |
| Cross-server messaging published messages | | CsmPublishedMessagesCount
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |  |
| Cross-server messaging received messages | | CsmReceivedMessagesCount
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |  |
| List request quota consumption | | DataStoreConsumedListRequests
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

DataStoreRequestSource

-

DataStoreTypeV2

 |
| Read request quota consumption | | DataStoreConsumedReadRequests
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

DataStoreRequestSource

-

DataStoreTypeV2

 |
| Remove request quota consumption | | DataStoreConsumedRemoveRequests
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

DataStoreRequestSource

-

DataStoreTypeV2

 |
| Write request quota consumption | | DataStoreConsumedWriteRequests
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

DataStoreRequestSource

-

DataStoreTypeV2

 |
| Request count by API and status | | DataStoreRequests
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

DataStoreOperation

-

DataStoreStatus

-

DataStoreTypeV2

 |
| HTTP service request count | | HttpServiceRequestsCount
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

HttpServiceDomains  (filter only)

-

HttpServiceMethod

-

HttpServiceStatus

-

Place  (filter only)

 |
| HTTP service response time | | HttpServiceResponseTimeAvg
HttpServiceResponseTimeP10
HttpServiceResponseTimeP50
HttpServiceResponseTimeP90
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

HttpServiceDomains  (filter only)

-

HttpServiceMethod

-

Place  (filter only)

 |
| Memory Store request count by API and status | | MemoryStoreRequests
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

MemoryStoreOperation

-

MemoryStoreStatus

 |
| Unexpected out of memory exits | | OomUnexpectedExits
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

MemoryGroup

-

OperatingSystem

-

Place  (filter only)

-

Platform

 |
| Peak concurrent players | | PeakConcurrentPlayers
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

MemoryGroup

-

OperatingSystem

-

Place  (filter only)

-

Platform

 |
| Server CPU time | | CpuTimeAvg
CpuTimeP10
CpuTimeP50
CpuTimeP90
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

CpuTimeCategory

-

CpuTimeSubCategory

-

Place  (filter only)

 |
| Server frame rate | | ServerFrameRateAvg
ServerFrameRateP10
ServerFrameRateP50
ServerFrameRateP90
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

Place  (filter only)

 |
| Server memory usage by age | | MemoryUsageAvg
MemoryUsageP10
MemoryUsageP50
MemoryUsageP90
Granularities:  OneMinute, HalfHour, OneHour, OneDay, None
Data retention:  28 days | |
-

MemoryUsageCategory

-

MemoryUsageSubCategory

-

Place  (filter only)

 |
| Server memory usage | | MemoryUsageAvg
MemoryUsageP10
MemoryUsageP50
MemoryUsageP90
Granularities:  OneMinute, HalfHour, OneHour, OneDay, None
Data retention:  28 days | |
-

MemoryUsageCategory

-

MemoryUsageSubCategory

-

Place  (filter only)

 |
| Session time | | SessionDurationSecondsAvg
SessionDurationSecondsP10
SessionDurationSecondsP50
SessionDurationSecondsP90
Granularities:  OneMinute, HalfHour, OneHour, OneDay
Data retention:  28 days | |
-

MemoryGroup

-

OperatingSystem

-

Place  (filter only)

-

Platform

 |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
