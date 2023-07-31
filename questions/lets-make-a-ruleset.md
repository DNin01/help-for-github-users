# Let's make a ruleset

Rulesets are the new version of branch protections, but the interface for setting up a ruleset can be a little hard to understand the first time you're using it. Let's walk through how to set up a ruleset to require a pull request for commits pushed to our default branch (you know, `main` or `master`).

## 1. Time for a new ruleset

To start setting up your new ruleset, navigate to Settings → Rules → Rulesets and click "New branch ruleset".

## 2. What branch will this ruleset apply to?

You'll need to tell your ruleset what branch or branches to target. In our case, we want to add restrictions to our default branch, so scroll down to the "Target branches" section and click "Add a target" then "Include default branch". If you want to protect a different branch, choose "Include by pattern" and type in the name of the branch you want to target.

## 3. Enforce the rules

In order for the rules to work, you'll have to change the enforcement status in the "General" section to "Active".

## 4. Name your ruleset

I suppose while we're up here, we should enter the name of this ruleset. We'll call it "Require pull request".

## 5. Set the rules

Under "Branch protections", choose the rules you want to apply. You can look up all of the rules you can set [here](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/available-rules-for-rulesets). We'll check "Require a pull request before merging", which will make it so that commits to this branch must come from a pull request. Checking this will reveal more options which you can set as you wish.

## 6. Grant ourselves the keys

You may not want this ruleset to apply to you or trusted maintainers. In that case, you can choose who can bypass the rules in the "Bypass list" section. We'll add the admin role so repository admins aren't affected by the rules.

If nobody is added to the bypass list, then the rule will apply to everyone and you'll need to disable it in order to bypass it.

## 7. We're done!

Finally, create the rule by clicking "Create".

Need more details? Learn more in [GitHub Docs](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/managing-rulesets-for-a-repository#creating-a-ruleset).

## Some ideas

- "Default branch lock" for forks to prevent yourself from accidentally pushing to your fork's default branch. Check "restrict updates" and "allow fork syncing".
- "Require signed commits" for repositories with collaborators to ensure no one can spoof a committer's identity.
