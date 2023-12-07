# Switching from branch protections to repository rules

You might have heard about the next generation of branch protections, repository rules, and you might be interested in switching over to them from branch protections. We will explain first how branch protections and rulesets are designed differently, and then what that means for the process of using rulesets.

> [!NOTE]
> This is not a guide for using repository rules. This document purely explains the notable differences between how branch protections and branch rulesets are configured and separated, useful if you would like to switch to rulesets.
>
> GitHub has not yet announced any plans to deprecate branch protections, and it is possible they will be supported indefinitely (there are still cases where branch protections can work, after all).

## Differences between branch protections and rulesets

First, let's understand the differences between branch protections and rulesets.

### Rulesets can be enforced across an organization

Instead of having to create the same branch protection rules for all of your repositories where you want it to apply, a ruleset can apply to multiple repositories across an organization, so if you're an admin of an organization, you can take advantage of that and only need to update your rules in one place.

### Rulesets can have multiple match patterns

If you have multiple branches with completely different names that you want to protect with rulesets, you can easily protect them all by adding a match pattern for each one or each matchable set, all in the same ruleset.

### Rulesets can coexist with each other

Unlike branch protections, which override each other if multiple target the same branch, if two or more rulesets target the same branch, each of their rules stack on top of each other. [Learn more about how that works.](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets#about-rule-layering)

### Rulesets can be named

Each ruleset has a name, whereas branch protections are identified by match pattern.

### Rulesets have customizable bypass lists

Configuring the ability to bypass branch protections is a little confusing - most of the rules can be bypassed by certain roles unless you check "Do not allow bypassing the above settings", except for rules under "Rules applied to everyone including administrators", which apply to everyone regardless of role by default. Not being able to stack branch protections also doesn't help.

With rulesets, you have more flexibility over who can bypass rules, and the bypass settings apply to all rules within their ruleset. It's much clearer. If you want a role to be able to bypass some rules and not others, you can split them across multiple rulesets, with each ruleset having different bypass options.

### Learn more

Learn more on the official [GitHub documentation](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets).

All of these advantages over branch protections help make rulesets more scaleable and easier to work with, so if managing branch protections has become frustrating, let's make the switch!

## The move to rulesets

If that sounds like the kind of system you want, we can begin mapping out the process of switching from branch protections to rulesets. Let's walk through the differences between how we would set up branch protections and how we would set up rulesets.

### The process of configuring branch protections

Branch protections are very much per-branch settings - you set different rules for each branch or set of branches. This means if you want to apply the same rule (like requiring a non-linear history) to all of your branches, you have had to check that box in every branch protection.

The way branch protections override each other also means you can't have two protections that target the same branch without one being overridden, so if you have two distinct sets of rules in mind that you want to both apply to a single branch (let's say one is requiring a non-linear history and one is requiring a pull request), they have to be combined into a single branch protection to all work together.

Therefore, a branch protection isn't necessarily an individual set of related rules - it's more like a configuration, one including all of the sets of rules you wanted to apply to the branch.

### The process of configuring rulesets

Rulesets are stackable and can target multiple sets of branches with their ref matching improvements, so there doesn't have to be a separate ruleset for each branch. They can also be named, which fits right in with how we're going to use them. So, the principles of setting up rulesets is a little different, but you're going to love it.

Rulesets are designed to be... well, individual sets of rules. By that, I mean each different individual group of rules you want to enforce would each be placed in a separate ruleset. For example, you may have one ruleset for preventing deletions and force pushes, one for requiring pull requests, etc.

So go ahead, create a ruleset for each distinct set/type of rules you want in place, and instead of creating separate rulesets for each branch/repository, add all of the branches and repositories you want your ruleset to target and you won't have to duplicate anything!

Keep in mind that this is just one common way rulesets are used, and you may have another way you want to set them up, or you can use the method described above if you like it.

And don't worry, your existing branch protections won't clash with rulesets (in fact, rulesets also stack on top of branch protections), so you may delete them after you're done, or just leave them.

And that's about it!
