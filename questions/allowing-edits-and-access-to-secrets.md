# What does the "allow edits and access to secrets from maintainers" checkbox do?

You may have seen a checkbox to allow edits from maintainers when making a pull request before, but you may have also seen the checkbox read "allow edits and **access to secrets** from maintainers" for pull requests that merge commits from forks with workflows. What does it mean? What are the secrets?

Let's look into the terms being used here.

- A **maintainer** in this context is someone who has the ability to manage or collaborate on the repository you're contributing to. You might see certain badges such as "Member" on comments posted by these people.

- A **secret** is an encrypted variable for use in GitHub Actions workflows (and other things), which are automations that can help manage repositories. Secrets are usually credentials like keys to publish an app to a store or other sensitive information that could result in unauthorized activity if exposed.

The reason access to secrets is mentioned is because allowing others to edit your pull request also means they can make edits you didn't intend, and the one this sentence is trying to warn you about is modifications to workflows that could potentially reveal the values of secrets (for example, a code modification that literally logs its value).

With the power to edit workflows, they can also do things to other parts of your fork outside the pull request (I'm talking other branches).

## Should you be worried?

The good thing is, as long as the maintainers are trustworthy, they shouldn't be messing with those. Otherwise, you can protect your fork by disabling Actions in Settings → Actions → General.

It's also very possible your fork doesn't have any secrets. You can check this in Settings → Secrets and variables.
