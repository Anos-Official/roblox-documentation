<!-- Source: https://create.roblox.com/docs/cloud-services/data-stores-vs-memory-stores -->

Choose between cloud services | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/cloud-services/data-stores-vs-memory-stores.md | Documentation index: https://create.roblox.com/docs/llms.txt | Cloud API index: https://create.roblox.com/docs/cloud/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Cloud services](/docs/cloud-services/data-stores-vs-memory-stores)

# Choose between cloud services

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/cloud-services/data-stores-vs-memory-stores.md)

Roblox offers several options for data storage. Each storage option has pros and cons and is appropriate for different use cases. This table summarizes the available options and provides the closest points of comparison from standard web services.

| Service | | Persistence | | Scope | | In-game access | | Cloud comparison |
| --- | --- |
| Data stores | | Permanent | | Cross-server | | Read-write | | NoSQL database |
| Memory stores | | 45 day maximum | | Cross-server | | Read-write | | In-memory cache |
| Configs | | Permanent | | Cross-server | | Read-only | | App configuration and feature flags |
| Secrets stores | | Permanent | | Cross-server | | Read-only | | Secrets management |
| Luau in-memory | | Session duration | | Single server | | Read-write | | Server RAM |

Within Roblox games, cloud services are only accessible from server scripts.

## [When to use data stores](#when-to-use-data-stores)[](#when-to-use-data-stores)

[DataStoreService](/docs/reference/engine/classes/DataStoreService)  stores long-term data that needs to last between sessions, such as user progress or inventory items. Data stores are consistent per game, so every server for every place within a game can access and change the same data. There are two types of data stores: standard and ordered.

-

Standard data stores  can store data like numbers, strings, and tables that don't need to be ranked or sorted. They store data as key-value pairs; each entry is stored under a key that is unique within its data store and that you can retrieve, update, or delete. For more information, see [Data stores](/docs/cloud-services/data-stores) .

-

Ordered data stores  can only store numbers. Each entry is stored under a key that is unique within its data store and that you can retrieve, update, or delete. You can rank and sort this data numerically and retrieve it in ascending or descending order based on stored numerical values. For more information, see [Ordered data stores](/docs/cloud-services/data-stores#ordered-data-stores) .

|  | | Standard data stores | | Ordered data stores |
| Data type | | Numbers, strings, booleans, and tables. | | Only numbers. |
| Common use cases | | User progress, inventory items, and game settings. | | All-time, persistent ranking systems and leaderboards. Unlike leaderboards in memory stores, this leaderboard data is permanent. |
| Past version backup | | Automatically manages previous versions of your data for 30 days. | | Does not manage previous versions of your data. |

If you want to add granular permission control to your data stores and access them outside of Studio or Roblox servers, use the [Open Cloud APIs for data stores](/docs/cloud/reference/features/storage) .

## [When to use memory stores](#when-to-use-memory-stores)[](#when-to-use-memory-stores)

[MemoryStoreService](/docs/reference/engine/classes/MemoryStoreService)  is a high throughput and low latency service that stores temporary data that needs to be updated or accessed frequently, such as global leaderboards or matchmaking queues. With memory stores, every server for every place within a game can access and change the same data quickly and frequently. Data in a memory store expires after a certain period of time, up to 45 days.

If you need to quickly read (not write to) a small number of values across all servers, [configs](#when-to-use-configs)  are the better choice. Memory stores are not as performant as configs when frequently accessing a single key or partition.

Although memory stores store temporary data, they also support permanent features like a global marketplace. The marketplace is permanent, but the items for sale inside it have an expiration date.

|  | | Memory stores |
| Data type | | Numbers, strings, booleans, and tables that don't need to persist for over 45 days. |
| Common use cases | | Skill-based matchmaking, match states for multiplayer games. |
| Daily and monthly leaderboards. |

## [When to use configs](#when-to-use-configs)[](#when-to-use-configs)

[Configs](/docs/production/configs)  let you update in-game variables in real time without restarting servers. They are ideal for feature flags and any in-game values you hope to tune over time or [experiment](/docs/production/experiments)  with.

-

Configs are read-only from within a game—you modify them on Creator Hub or in Roblox Studio—so they don't serve the same use cases as data stores and memory stores.

-

Changes to configs deploy over the course of five minutes; changes to data and memory stores are more instantaneous.

|  | | Configs |
| Data type | | Numbers, strings, booleans, and JSON objects. |
| Common use cases | | Enabling a new dungeon, disabling a limited-time game mode, starting a holiday event. |
| Enemy health, weapon damage, item prices, game multipliers, welcome messages. |

## [When to use secrets stores](#when-to-use-secrets-stores)[](#when-to-use-secrets-stores)

Use the [secrets store](/docs/cloud-services/secrets)  for your game to store any API keys, passwords, and access tokens that you use to authenticate with external services. Storing these values in a data store presents unnecessary security risks.

|  | | Secrets stores |
| Data type | | Strings. |
| Common use cases | | API keys, passwords, and access tokens for analytics or music services. |

## [When to use in-memory storage in Luau](#when-to-use-in-memory-storage-in-luau)[](#when-to-use-in-memory-storage-in-luau)

Use in-memory storage in Luau to store temporary data that needs to be accessed with minimal latency and without the cost of making external service calls. This storage is built into Luau and requires no setup.

|  | | In-memory storage in Luau |
| Data type | | Numbers, strings, booleans, and tables. |
| Common use cases | | Data that is only relevant to a single server session and doesn't need to be persisted, such as status effects or temporary points that reset when the user leaves the game. |
| Values that change frequently, like counters, timers, state flags, or a health bar. |
| Data that drives game logic, which needs to be accessible instantly, like temporary variables or an enemy's current health. |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
