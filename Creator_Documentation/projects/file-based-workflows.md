<!-- Source: https://create.roblox.com/docs/en-us/projects/file-based-workflows -->

Compare file-based workflows | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/projects/file-based-workflows.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs/en-us)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Projects](/docs/en-us/projects)
6. /
7. [File-based workflows](/docs/en-us/projects/file-based-workflows)

# Compare file-based workflows

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/projects/file-based-workflows.md)

Roblox games live in the cloud by default. Studio saves your places, assets, and scripts to Roblox, and [Version History](/docs/en-us/projects/version-history)  tracks changes to each place. Many teams also want their game in a version control  system like [Git](https://git-scm.com/)  so they can review changes before they land, keep a full history, and automate builds and deploys.

Every version control workflow for Roblox answers one question: where does the source of truth  live for each part of your game? The three common answers are:

-

Studio-native:  The place on Roblox is the source of truth for everything. Script Sync copies scripts into Git so you can review and track them.

-

Partially managed:  Git is the source of truth for code. The place on Roblox is the source of truth for everything else, like models, terrain, and UI.

-

Fully managed:  Git is the source of truth for the entire game. Places on Roblox are build output that CI publishes from the repository.

This page compares these workflows, describes the tools each one uses, and covers the environments that teams set up around them. To set up a workflow, see [Set up a workflow](#set-up-a-workflow) .

Third-party tools on this page are not maintained by Roblox and can change or stop working at any time. For full reference, see each tool's own documentation.

## [Roadmap for file-based workflows](#roadmap-for-file-based-workflows)[](#roadmap-for-file-based-workflows)

Roblox is working toward first-party, file-based workflows so that teams can use version control without assembling third-party tools. Until those workflows ship, the setups on this page reflect what works for teams today.

## [Workflow comparison](#workflow-comparison)[](#workflow-comparison)

#### Studio-native

#### Partially managed

#### Fully managed

|  | | Studio-native | | Partially managed | | Fully managed |
| --- | --- |
| ** Good fit for** | | Teams of fewer than five creators working on a single-place game | | Teams with several programmers, and multi-place games | | Teams that require review and history for every instance and asset |
| ** In version control** | | Scripts | | Scripts, project configuration, and tooling | | Everything, including models and images |
| ** Content editing** | | Team Create | | Team Create and packages | | Files in Git, built by CI |
| ** Tools to maintain** | | None beyond Studio and an editor | | Rojo plus linting and CI tools | | Rojo, merge and asset tools, and a full CI pipeline |

### [Choose a workflow](#choose-a-workflow)[](#choose-a-workflow)

Start with the simplest workflow that meets your needs. You can move to a more managed workflow later, because none of these tools lock you in. Most teams don't need fully managed Rojo, and it adds significant complexity.

## [Tools](#tools)[](#tools)

Most setups combine a few tools from Roblox with a few from the community.

### [Roblox tools](#roblox-tools)[](#roblox-tools)

| Tool | | What it does | | Used in |
| [Team Create](/docs/en-us/projects/collaboration) | | Real-time collaborative editing in Studio, best suited to building, level design, and art. | | All workflows |
| [Script Sync](/docs/en-us/scripting/sync) | | Syncs scripts in Studio with files on your local disk, in both directions. | | Studio-native |
| [Packages](/docs/en-us/projects/assets/packages) | | Reusable, versioned groups of instances that you can update across places and games. | | Studio-native, partially managed |
| [Version History](/docs/en-us/projects/version-history) | | Saved versions of each place that you can view, compare, and restore. | | All workflows |
| [Place publishing API](/docs/en-us/cloud/guides/usage-place-publishing) | | Open Cloud API that publishes a place file to Roblox. Use it to deploy from CI. | | Partially managed, fully managed |
| [Luau execution API](/docs/en-us/cloud/reference/LuauExecutionSessionTask) | | Open Cloud API that runs Luau in a place on Roblox servers. Use it to run tests from CI. | | Partially managed, fully managed |
| [Assets API](/docs/en-us/cloud/guides/usage-assets) | | Open Cloud API that uploads and updates assets like images, audio, and models. | | Fully managed |

### [Community tools](#community-tools)[](#community-tools)

| Tool | | What it does | | Used in |
| [Rojo](https://rojo.space/) | | Syncs files on disk into Studio through a local server and Studio plugin, and builds place and model files from a project file. The rojo syncback  command, in Rojo 7.7 and later, converts an existing place into project files. | | Partially managed, fully managed |
| [Rokit](https://github.com/rojo-rbx/rokit) | | Toolchain manager. Pins tool versions so everyone on the team uses the same ones. | | Partially managed, fully managed |
| [Wally](https://wally.run/) | | Package manager for community Luau libraries. | | Partially managed, fully managed |
| [Lune](https://github.com/lune-org/lune) | | Standalone Luau runtime, commonly used for build, deploy, and automation scripts. | | Partially managed, fully managed |
| [selene](https://github.com/Kampfkarren/selene) | | Luau linter. | | All workflows |
| [StyLua](https://github.com/JohnnyMorganz/StyLua) | | Luau code formatter. | | All workflows |
| [Luau Language Server](https://github.com/JohnnyMorganz/luau-lsp) | | Autocompletion and type checking in external editors. | | All workflows |
| [Tarmac](https://github.com/Roblox/tarmac) | | Uploads images from disk to Roblox and generates a module that maps file paths to asset IDs. | | Fully managed |
| [rbx-merge](https://github.com/kennethloeffler/rbx-merge) | | Git diff and merge driver for .rbxl , .rbxlx , .rbxm , and .rbxmx  files. Shows readable diffs and merges non-conflicting changes at the property level. | | Fully managed |

To install and run Rojo, see [Rojo](/docs/en-us/projects/rojo) . For Rokit, Wally, linters, and other tools, see [Third-party tools](/docs/en-us/projects/external-tools) .

## [Environments](#environments)[](#environments)

Teams that use version control usually also separate their work into environments , so that unfinished changes never reach players. Instead of one place that everyone edits, each environment is its own place.

We recommend creating each environment as a separate game  under the same [group](/docs/en-us/projects/groups) , rather than as separate places within one game. Data stores, secrets, and other cloud services are scoped to the game, so separate games keep test data out of production.

A typical setup has these environments:

| Environment | | Purpose | | Who updates it |
| ** Personal dev** | | Each creator's own copy of the dev place for day-to-day work. | | That creator |
| ** Shared dev** | | The combined, unstable set of features that the team is working on. | | Programmers sync reviewed code, and artists copy in approved content. |
| ** Assets** | | The canonical versions of packages, like characters, building kits, and set dressing. | | Artists |
| ** Stable** | | A snapshot of shared dev at a regular interval, such as for weekly playtests. | | CI only |
| ** Production** | | The live, public game. | | Copied from stable after release approval |

### [Create a personal dev place](#create-a-personal-dev-place)[](#create-a-personal-dev-place)

1.

Open the shared dev place in Studio.

2.

Select File  ⟩ Publish As .

3.

Select the group that owns your dev games.

4.

Publish the place as a new game with a name that identifies you and the project, like USER / YourName - ProjectName .

5.

Close the shared dev place and open your new personal copy.

Use consistent names for every environment, such as DEV - ProjectName , ASSET / ProjectName , and STABLE / ProjectName , so that the team can tell them apart on the Creator Dashboard .

## [Set up a workflow](#set-up-a-workflow)[](#set-up-a-workflow)

| Workflow | | Setup guide |
| Studio-native | | [Use Script Sync with a team](/docs/en-us/scripting/sync#use-script-sync-with-a-team) |
| Partially managed | | [Partially managed Rojo](/docs/en-us/projects/rojo/partially-managed) |
| Fully managed | | [Fully managed Rojo](/docs/en-us/projects/rojo/fully-managed) |

## [Troubleshoot common problems](#troubleshoot-common-problems)[](#troubleshoot-common-problems)

| Problem | | Fix |
| Testing in a dev place changes production data. | | Dev and production are places in the same game, so they share data stores. Move each environment into its own game. |
| Teammates overwrite each other's script changes. | | Two people are syncing the same scripts into one Team Create session. Sync code into personal dev places and merge through Git. |
| A fix to one copy of a script doesn't apply to the others. | | Copying a script creates an independent copy. Put shared behavior in a [ModuleScript](/docs/en-us/reference/engine/classes/ModuleScript)  and attach it to instances with [CollectionService](/docs/en-us/reference/engine/classes/CollectionService)  tags. |
| Server-only code is visible to clients. | | Modules in containers that replicate to clients, like [ReplicatedStorage](/docs/en-us/reference/engine/classes/ReplicatedStorage) , are sent to clients. Keep server-only modules in [ServerScriptService](/docs/en-us/reference/engine/classes/ServerScriptService)  or [ServerStorage](/docs/en-us/reference/engine/classes/ServerStorage) . |

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
