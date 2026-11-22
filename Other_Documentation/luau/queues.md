<!-- Source: https://create.roblox.com/docs/luau/queues -->

Queues | Documentation - Roblox Creator Hub

For Agents | This page is available as markdown: https://create.roblox.com/docs/luau/queues.md | Documentation index: https://create.roblox.com/docs/llms.txt

1. [Learn](/docs)
2. /
3. [Experiences](/docs/en-us/experiences)
4. /
5. [Scripting](/docs/scripting)
6. /
7. [Luau reference](/docs/luau)
8. /
9. Data structures

# Queues

English

[Edit](https://github.com/Roblox/creator-docs/blob/main/content/en-us/luau/queues.md)

A queue is a linear data structure with a collection of items. There are two types of queues on Roblox: [regular queues](#regular-queues) , which follow the first-in-first-out (FIFO) principle, and [priority queues](#priority-queues) , which have priorities for items in the queue that determine the data accessing order. Items in both types of queues can be any Luau [data type](/docs/luau#types) .

Queue is a built-in data structure of the [non-persistent data storage](/docs/cloud-services/memory-stores/queue)  service named [MemoryStoreService](/docs/reference/engine/classes/MemoryStoreService) , for which you can directly call the built-in functions to get a queue and add, read, or remove data from the queue. For any other usage, such as scheduling tasks and handling requests in your game, you can use tables to implement queues on your own.

## [Regular queues](#regular-queues)[](#regular-queues)

Regular queues are maintained in the FIFO sequence, in which all items are added to the back of the queue and read or removed in the same order as they are added, from the front to the end.

![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Regular-Queue-Diagram.png) The order of how a regular queue adds, reads, and removes items

## [Priority queues](#priority-queues)[](#priority-queues)

Priority queues are not following the FIFO rule, in which each item can be added with a priority number that indicates its order being read or removed. The item at the back of a priority queue has the default priority of 0, and the item at the front of the queue has the highest set priority, which is 5 in the following example.

![](https://prod.docsiteassets.roblox.com/assets/data/memory-store/Priority-Queue-Diagram.png) An item's set priority changes the order in which a queue reads items

For this example, an item with a set priority of 3 is being added to a queue. The queue places the new item behind all existing items with the set priority of 3 or more. To place an item at the front of the queue, you need to set the priority higher than the current highest set priority. In this example, you need to set the priority to 6 or higher.

Priority queues are useful for situations where you want to read or access data based on the order of importance instead of the order of being added. You can set a priority as an integer when adding an item, and the queue processes items with higher priority before items with lower priorities. For example, you can use priority queues for matchmaking by assigning higher priorities to users who have been waiting for a long time.

## [Implement queues](#implement-queues)[](#implement-queues)

You can use built-in queues of [MemoryStoreService](/docs/reference/engine/classes/MemoryStoreService)  or use [tables](/docs/luau/tables)  to implement queues for all other usage. The following code sample shows the implementation a regular queue . To use this implementation for your game, you should save it as a [ModuleScript](/docs/reference/engine/classes/ModuleScript)  and store it in [ReplicatedStorage](/docs/reference/engine/classes/ReplicatedStorage) , so your queue is accessible for both client and server.

Implementing a Regular Queue Using Table

```

--!strict

local Queue = {}

Queue.__index = Queue

export type Queue<T> = typeof(setmetatable(

	{} :: {

		_first: number,

		_last: number,

		_queue: { T },

	},

	Queue

))

function Queue.new<T>(): Queue<T>

	local self = setmetatable({

		_first = 0,

		_last = -1,

		_queue = {},

	}, Queue)

	return self

end

-- Check if the queue is empty

function Queue.isEmpty<T>(self: Queue<T>)

	return self._first > self._last

end

-- Add a value to the queue

function Queue.enqueue<T>(self: Queue<T>, value: T)

	local last = self._last + 1

	self._last = last

	self._queue[last] = value

end

-- Remove a value from the queue

function Queue.dequeue<T>(self: Queue<T>): T

	if self:isEmpty() then

		error("Cannot dequeue from empty queue")

	end

	local first = self._first

	local value = self._queue[first]

	self._queue[first] = nil

	self._first = first + 1

	return value

end

return Queue

```

The following code sample is a usage example as a [Script](/docs/reference/engine/classes/Script)  under [Workspace](/docs/reference/engine/classes/Workspace) . You can modify the code, type, and storage location to fit your own usage, as long as you have the previous implementation code sample properly stored.

Regular Queue Usage Example

```

local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Queue = require(ReplicatedStorage:WaitForChild("Queue"))

local myQueue = Queue.new()

-- Add some values to the queue

myQueue:enqueue(5)

myQueue:enqueue(10)

myQueue:enqueue(15)

-- myQueue = { 5, 10, 15 }

-- Remove one value from the queue

local first = myQueue:dequeue()

print("The first value added to the queue was", first)

-- myQueue = { 10, 15 }

-- Add more values to the queue

myQueue:enqueue(20)

myQueue:enqueue(25)

myQueue:enqueue(30)

-- myQueue = { 10, 15, 20, 25, 30 }

-- Remove another value from the queue

local second = myQueue:dequeue()

print("The second value added to the queue was", second)

-- myQueue = { 15, 20, 25, 30 }

```

©2026 Roblox Corporation. Roblox, the Roblox logo and Powering Imagination are among our registered and unregistered trademarks in the U.S. and other countries.

[Terms](https://www.roblox.com/info/terms) ·[Privacy](https://www.roblox.com/info/privacy) ·[Accessibility](https://www.roblox.com/info/accessibility) ·[Support](https://www.roblox.com/info/help)

[](https://x.com/Roblox)[](https://www.facebook.com/Roblox/)[](https://www.linkedin.com/company/roblox)[](https://www.instagram.com/roblox/)[](https://www.youtube.com/@RobloxLearn)

[

English

](https://create.roblox.com/settings/preferences)
