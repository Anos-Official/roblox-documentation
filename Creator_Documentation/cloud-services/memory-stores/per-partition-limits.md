<!-- Source: https://create.roblox.com/docs/en-us/cloud-services/memory-stores/per-partition-limits -->

Partitions and data distribution | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud-services/memory-stores/per-partition-limits.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/en-us/cloud-services/data-stores-vs-memory-stores)
6. /
7. [Memory stores](/docs/en-us/cloud-services/memory-stores)

# Partitions and data distribution

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud-services/memory-stores/per-partition-limits.md)

The MemoryStores API stores data on partitions so it can scale throughput across data structures. Sorted maps and queues each reside on one partition, while hash maps automatically spread items across many partitions. This page explains how that assignment works.

## [Partitions](#partitions)[](#partitions)

The MemoryStores API stores data on * partitions* , which are just subdivisions of storage. Whenever you write an item to a memory store, that item is stored on exactly one partition. Partitions are fully managed by the MemoryStores API; you do not need to manage them yourself.

## [Partition assignment](#partition-assignment)[](#partition-assignment)

Partition storage is different according to the data structure an item is being stored on. For sorted maps and queues, each data structure is assigned a single partition.

For example, consider a carnival game with a sorted map called PlayerScores  and a queue called PlayerLine  of players waiting to play the game:

 ![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Per-Partition-Limits-1.png)

Unlike sorted maps and queues, hash maps are allotted multiple partitions, and data is automatically distributed across these partitions. If you were to add a hash map called Prizes , the partitions might look like this:

 ![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Per-Partition-Limits-3.png)

Note how the hash map exists on all partitions, and each partition has some subset of items.

For the request limits that apply to each partition and to individual hash map keys, see [Per-partition limits](/docs/en-us/cloud-services/memory-stores#per-partition-limits) . For guidance on spreading load across keys and data structures, see [best practices](/docs/en-us/cloud-services/memory-stores/best-practices) .

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
