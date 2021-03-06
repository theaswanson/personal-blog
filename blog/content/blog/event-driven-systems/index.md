---
title: Differences between Traditional and Event-Driven Systems
date: "2021-03-05T20:00:00.000Z"
description: "There are major differences to consider when moving to an event-driven system. Let's take a look at the major ones and examine what changes are required to adopt this unique architecture."
---

<img alt="Fridge" src="fridge.jpg" />

Application state is often treated like food in a fridge. If we need something, we take it out, use what we need, and put it back. The same is usually done with data: we read the data we need, manipulate it, and write it back to the same place.

This approach has its advantages: managing data becomes very simple. Data can be read from, say, a database, and it can be updated in the same format and in the same place. However, there are downsides: the app's state becomes one big blob of data. Sure, it's structured and organized, but how did it get to its current state? There's no record of the steps it took to get there. All we know is we have data.

Let's use accounting as an example. Say we spend $10. How do we update our balance? Do we take our current balance, remove $10, and update it? If we did that, we would have no way of tracking our account history. Instead, we add a record of it in our account ledger. To get the new balance, we add up all the transactions in the ledger. We never update the balance directly.

There are a few key differences here. The first is how the balance is defined. The naive approach is to treat it as a value that can be changed at-will. A better approach is to treat it as the result of changes. The second is the distinction between updating and reading. In the first approach, we write to the balance by updating a single value, and to get the balance we read that same value. In the second approach, we write by appending a new change to a log, and we read by adding up all of those changes.

Event-driven systems introduce these same differences. If we treat each change to the system as an event (like `EmailChanged` or `ItemAddedToCart`) and store these events, we can add them up to get our app's state. A common example is a version control system like Git. Each change is represented as a commit, and by adding up all the commits we can produce the codebase.

By storing each change like this, we get several advantages. One advantage is we can represent the app's state in any form we want. If we want to use a database, JSON, or something in memory, we can build up a model of the app's state from the events. In fact, we could have several models. Another advantage is we can see all the changes that were made to the system. Log messages can be helpful, but they don't often include all the necessary details to understand what's going on. Events, on the other hand, have all the details already baked in.

When implementing an event-driven system, the app's architecture must be updated to support an event-driven approach. If a change is made, one can no longer reach into the data and update it themselves. Instead, they simply raise an event with the details of what needs to be changed. This event is then stored and processed by an event handler that can build up a model of the app's state in, say, a database. This database can then be used to read the app's state without needing to touch any events.

There are several pros to event-driven systems. First, they provide a log of every change made to the system. These are represented in the events. Second, they give the ability to see what the state was at any point in time. This can be done by building up a model of the app's state from the events up to a certain time. Third, the app state can be rebuilt from the events at any time.

The biggest con to event-driven systems is complexity. It becomes harder to follow the flow of control through the system when most of it happens in event handlers. By raising an event, you don't know what, if anything, will handle that event. It is up to a handler, somewhere, to be watching for it. This is much harder to follow than a simple call like `cartService.addItem()`.

Keep these differences in mind when considering an event-driven architecture for your next project. Not all projects will benefit from this approach, but if the pros outweigh the cons, it may be a good choice.