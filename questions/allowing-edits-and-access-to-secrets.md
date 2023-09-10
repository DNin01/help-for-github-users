# What does the "allow edits and access to secrets from maintainers" checkbox do?

You may have seen a checkbox to allow edits from maintainers when making a pull request before, but you may have also seen the checkbox read "allow edits and **access to secrets** from maintainers" for pull requests that merge commits from forks with workflows. What does it mean? What are the secrets?

First, let's learn more about what "maintainer" and "secret" mean, in case you are not aware already.

- A **maintainer** in this context is someone who has the ability to manage or collaborate on the repository you're contributing to (a.k.a. the upstream repository). You might see certain badges such as "Member" on comments posted by these people.

- A **secret** is an encrypted variable for use in GitHub Actions workflows (and other things), which are automations that can help manage repositories. Secrets are usually credentials like keys to publish an app to a store or other sensitive information that could result in unauthorized activity if exposed.

If you allow edits from maintainers, they can technically also make edits you didn't intend, such as workflow modifications. With the power to modify workflows, it becomes possible for an unauthorized maintainer to reveal the values of secrets or even gain access to other branches on your fork.

## Should you be worried?

If you trust the maintainers of the upstream repository not to mess with those, you can allow edits. If you want to be a bit cautious while still allowing edits, any issues resulting from workflow modifications can be prevented by disabling Actions in Settings → Actions → General.

It's also very possible your fork doesn't have any secrets. You can check this in Settings → Secrets and variables.
