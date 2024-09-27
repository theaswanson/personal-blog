---
title: "Tips for New Developers: What I Wish I Learned in College"
date: "2024-09-26T23:20:00.000Z"
description: "College is a great starting point, but it doesn't teach you everything. After 4 years in the industry, I've learned much more on the job that I ever did in my college courses. Here's my biggest recommendations."
---

![Header](header.jpg)

The world of software engineering is *huge*. Like, really huge. College teaches you the basics of programming - variables, functions, and loops - but it doesn't teach you *software engineering*.

I didn't realize this till my senior year; I had an internship that taught me a slew of things I never learned in class, like source control, deployment pipelines, and test-driven development. Before this, I thought I had learned everything there was to know about being a developer...boy was I wrong.

It's been four years since graduation, and in these last four years I've learned many things that have improved my productivity, broadened my technical knowledge, and made me a better teammate. Here's just a few of them:

## Learn Source Control

> git good.

Source control is an excellent tool for managing your source code. It allows you to track code changes, revert a bad change, and easily work with other developers. It even allows you to look back in time and see what the code was at any point in its history.

[git](https://git-scm.com/) is the industry standard and is supported in all of the popular IDEs, including Visual Studio Code. `git` also has command-line tools that allow you to work from the command line instead of a GUI. I highly recommend learning the basics, such as how to create commits, push commits, pull commits, create branches, and merge branches.

There are tons of tutorials and guides out there on how to use `git` and what the best practices are. One rule I always follow is to commit early and often. Having smaller commits makes it easier to see distinct changes and gives finer control over what commits to revert, should you ever need to.

## Prefer Simple over Complex

> Keep it simple, stupid.

Reading code is much harder than writing code, especially when you're reading code written by someone else. As a developer, you will spend a lot of time reading code; thus, it's important to ensure that the code *you* write is as simple and easy to understand as possible.

A rule of thumb I keep in mind is "code should look like one expects it to." For example, consider a program that sums two numbers. Think about what that code would look like. Now look at this solution:

```cs
class NumberSum
{
    private int _a;
    private int _b;
    private int _sum;

    NumberSum(int a, int b)
    {
        _a = a;
        _b = b;
        _sum = a + b;
    }

    int Result()
    {
        return _sum;
    }
}

var numberSum = new NumberSum(1, 2);

Console.WriteLine(numberSum.Result());
```

That's probably not what you had in mind. The `NumberSum` class overly complicates the act of summing numbers and its usage in the code throws off the reader.

Compare that with this simpler solution:

```cs
var a = 1;
var b = 2;

Console.WriteLine(a + b);
```

If the reasoning behind the code is not immediately apparent, adding a comment to explain it can go a long way in helping the reader get up to speed.

When in doubt, keep it simple.

## Refactor Your Code

> Make it work, make it right, make it fast.

In college, my programming courses were all focused on writing code that solved a specific goal; writing a working solution was all that really mattered. Writing code that was also readable and performant was not critical.

In the world of software engineering, you can't just ship your code once it works. You have to refine the code, clean it up, and rework it until it meets your team's standards.

Everybody has different code standards, but there are certain "code smells" that most developers try to avoid. You can find a good list of these smells at <https://refactoring.guru/refactoring/smells>.

Here are a few ways I like to refactor my code:

- Use clear naming. For example, naming a variable `sum` instead of `x`, or `name` instead of `n`. If a longer name adds more clarity, be verbose.
- Write bite-sized functions. It's easier to read a 1-line function than a 100-line one. Don't go overboard though; do what makes sense.
- Keep classes small. Split up large classes into smaller ones and compose them together. Don't be afraid to create a new class if the situation calls for one.

## Test Your Code

> Automation is key.

Code that has not been tested does not work; that's my philosophy, anyway. After a few years in the industry, I've learned that code doesn't always work as I expect it to. Even simple code that I thought would never break, broke. Now, I always test my code before deploying it.

If nothing else, manually run the code you write to ensure it works the way you think it does. Try a few edge cases to make sure bugs don't slip through. After a while though, manually testing your code can get cumbersome. That's where automated testing comes in.

You can actually write code that tests your code. You can arrange the state/environment your code runs in, then run it, and then check the results to ensure they match the expected outcome. There are many frameworks and IDE tools that make it easy to add this "test code" to your projects, as well as deployment pipeline tools to automatically run these tests and ensure they all pass before deploying any code.

Depending on how much code you want to test, you can write a unit test, integration test, or end-to-end test. Unit tests are my favorite since they're the simplest tests to write and cover the smallest amount of code. Looking up examples of unit tests in your language of choice is a great way to learn how to write these tests.

(Some developers make testing a core element of their development workflow using a method called "test-driven development" (TDD)[^1].)

## Use Continuous Integration & Continuous Delivery

> Deliver fast.

Making a change to code and getting it into your users' hands should be a quick and painless process. That's what Continuous Integration & Continuous Delivery allow you to do. They give you two key abilities:

1. The ability to quickly integrate code changes into a project
2. The ability to quickly deploy those changes.

So, what's Continuous Integration? Remember how I talked about source control earlier? That's how you make code changes and merge them in. When you couple that with automated tests, you have a system that allows you to make a change and automatically build the code, test it, and merge in the changes, all in a couple minutes. That's Continuous Integration.

Continuous Delivery is what it sounds like: continuously delivering code. It's about deploying code changes quickly, often through a deployment pipeline which takes the builds from Continuous Integration and deploys them out to whatever's running your code. Automating the deployment process this way makes it easy to push out updates, unlike manual processes that are slow, involved, and prone to error.

[GitHub Actions](https://docs.github.com/en/actions) is a great platform for creating build pipelines and deployment pipelines. Azure DevOps, TeamCity, and Octopus Deploy are other great platforms.

## Practice Pair Programming

> Two minds are better than one.

When it comes to working efficiently, work is often divided among workers to get the job done faster. It makes sense: if one person can move a rock in one minute, then 10 people can move 10 rocks in that same minute. The more workers you have, the more work gets done.

This strategy works well for our moving rock scenario where the task is simple, straightforward, and repetitive. But in software engineering, the work is the opposite: it's complex, involved, and requires custom solutions. It's been repeatedly shown that putting more developers on a project makes the project take longer.[^2] So what can a software development team do to work more efficiently?

The answer: work together. Instead of programming solo, developers can pair up and program together.

Pair programming allows you to learn directly from another developer. It helps answer initial questions you may have about the work and starts you off on the right path. When problem-solving, one developer may raise a question that the other hadn't thought of, or one may think of an edge-case scenario that wasn't previously considered. You might see another developer use a tool, IDE feature, or keyboard shortcut you hadn't seen before that improves your efficiency. You pick up on programming styles, design patterns, and best practices, and writing a feature with another developer means there's two developers that know how that feature works, not one.

The benefits of pair programming are huge, and I highly recommend trying it out. It's important to remember that it's not wasteful to work on the same thing with someone else. In knowledge work like software development, it really saves time.

## Implement Logging & Metrics for Observability

> Who, what, where, when, why?

Software without observability is a black box. Without observability, you have no way of knowing if the system you're building is working. Two ways I improve observability is adding logging and tracking metrics.

Logs are crucial for understanding the inner workings of a system: they can tell you exactly what is going on in fine detail. By logging details about what's happening within the system, you gain valuable insights into what users are doing, what's working, and what's breaking.

Good log messages answer the following questions:

- Who is performing an action?
- What happened?
- Where in the system did it happen?
- When did it happen?
- Why did it happen?

Here's an example:

`2024-09-25 12:34:59 | IP: 1.1.1.1 | AuthenticationService.Login | Failed login attempt for user ID '1234': incorrect password.`

This message answers all the questions: a user with an IP address of 1.1.1.1 (who) failed to log in to user '1234' (what) via the Login method in the AuthenticationService (where) at 12:34:59 on September 25, 2024 (when) due to an incorrect password (why). You could use a collection of these logs to determine what times users are often logging in, if multiple people are signing into the same user account, and if someone is trying to brute-force the password of a specific user.

Log files become powerful sources of data when they're ingested into tools like Splunk or Sumo Logic. These platforms allow you to search, filter, and aggregate logs to find the information you're looking for.

Metrics, on the other hand, give you a high-level overview of how your system is performing. For example, a metric that tracks the rate of failed login attempts can quickly help identify a brute-force attack. Metrics let you know when there's a problem, and logs give you the details.

Metrics can be derived from logs, but they are often tracked separately, allowing for real-time insights. With platforms like DataDog, you can collect metrics and view them in graphs, then put multiple graphs in a single dashboard to get a full view of a system's behavior.

Great observability, coupled with active monitoring, can significantly improve the maintainability and quality of software.

## Use Feature Flags

> Having problems? No problem.

Feature flags are a great tool for enabling and disabling features within software. They're essentially on/off switches that control how your software behaves. Say you're implementing a new feature but you don't want it enabled immediately after it's deployed. With a feature flag, you can deploy the changes and then enable the feature at a later time.

Using a feature flag is very simple and is essentially a glorified `if` statement. You check if the feature is enabled, and if so, you do the new codepath. If not, you do the old codepath.

Here's a simplified example of one in action:

```cs
if (_featureFlagService.IsEnabled(id: "new-greeting"))
{
    return "Welcome back!";
}
else
{
    return "Hello!"
}
```

In this example, a new greeting message is being tested. If the feature `new-greeting` is enabled, then "Welcome back!" is used as the greeting. If it's disabled, then the old "Hello!" greeting is used. Of course, the real magic lies in the implemenation of the `_featureFlagService`.

A simple implementation is with a dictionary where the key is the ID of the feature you want to enable/disable and the value is a boolean indicating whether it's on or off. In this example, `new-greeting` would be the key and `true` would be the value. This dictionary can then be updated through something like an admin panel where flags can be created, updated, and deleted.

Now say you want to enable that new greeting, but only for administrator users. You can do that by adding a variant to the flag. In our feature flag implementation, we can update the dictionary value to be some data structure that specifies 1. whether the flag is on or off by default, and 2. a list of variant IDs and whether the flag is on or off for that variant ID.

Here's the same example, but with the user's group used as the variant:

```cs
if (_featureFlagService.IsEnabled(id: "new-greeting", variantId: user.Group.Name))
{
    return "Welcome back!";
}
else
{
    return "Hello!"
}
```

`new-greeting` is still used as the key, but now `user.Group.Name` specifies the name of the group that the user is in. Then in the admin panel, the `new-greeting` flag can be updated with a variant like `administrators` to only enable this feature when the user is in the `administrators` group.

This is a simple example of how a feature flag can be used to control behavior. Realistically, I often use feature flags to control changes made to a hotpath (code that gets called frequently). This way, if something breaks, I can "revert" my changes by disabling a feature flag without needing to rollback. While feature flags take a little more time to implement, they can be a lifesaver when rolling out a change.

## Conclusion

Whew, that was a lot. These are just a few of the things I've learned while working in the industry, and I wish I had been introduced to these during my time in college. If you're just starting out as a developer and all of this is new to you, don't worry; you don't need to use all of this right now to get started and be successful. My goal was to introduce you to these topics in hopes that you could glean something valuable, no matter where you are as a developer. Hopefully it wasn't overwhelming and hopefully you learned something new!

[^1]: <https://martinfowler.com/bliki/TestDrivenDevelopment.html>
[^2]: Brooks, Frederick P. (1975). The Mythical Man-Month. Addison-Wesley. ISBN 0-201-00650-2.
