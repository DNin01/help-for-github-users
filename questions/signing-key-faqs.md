# Signing key FAQs

### What is a signing key and why should I use one?

A signing key adds a digital signature to your files that prove that they came from you, in short.

In terms of GitHub, because Git can be configured to commit under any name and email and GitHub uses that information to identify which GitHub account made that commit, anyone is able to easily impersonate you by configuring their Git client to use your information in any commit. Signing keys solve that problem because only you will have access to the signing key you use to sign your commits, so if someone tries to impersonate you, they're not going to be able to sign the commit with your signing key, so they cannot prove you were involved in that commit.

### Should I create a signing key and start signing my commits?

I'd recommend it, especially if you're high-profile or contributing to high-impact repositories. You might run into a situation where you need to sign your commits (some repositories actually require this) and it gives other people confidence that the commits came from you and someone didn't just enter your user information to push a commit on your behalf, which can be a headache.

### Someone is impersonating me in commits. What do I do?

You can enable [vigilant mode](https://docs.github.com/github/authenticating-to-github/displaying-verification-statuses-for-all-of-your-commits) in GitHub settings → [SSH and GPG keys](https://github.com/settings/keys).

Vigilant mode adds an "Unverified" label to commits that aren't signed with one of your signing keys. When other people see "Unverified", they can tell that someone may have pushed a commit as you without you actually having made that commit.

Only do this if you always sign your commits. Otherwise, it won't really help others differentiate commits you made from commits others made on your behalf.

### What if I don't want a signing key but still want to make signed commits?

Commit from the GitHub website or, if you want a code editor, the [github.dev web-based editor](https://docs.github.com/en/codespaces/the-githubdev-web-based-editor). GitHub will sign those for you, without the need for your own signing key.

### Why does GitHub sign the commits for me? How is that possibly safe?

Well, get this. On GitHub, when you're signed into your GitHub account, which only you would have access to, GitHub knows the commits you made on the website are coming from you. The same can't be said for Git, where we can impersonate someone by configuring Git to use their information in the commits we make without needing any sort of verification (unless they have their own signing key). Anyone can do that, but no one can sign into your account on GitHub as long as you keep it secure.

That's why we need to set up our own way of verifying that it's us for commits we make outside GitHub but can let GitHub do that for us when we're making those changes on GitHub. On the GitHub website, you cannot sign in as anyone else and impersonate them, and no one else can impersonate you either, when it comes to commit authors.

To summarize, you need at least one form of proper verification to really say that a commit came from who the committer says it came from, whether it's signing into GitHub or signing a commit with your signing key, and the latter is just one way of doing that.

### What does "partially verified" mean?

That appears next to co-authored commits if the co-authors have [vigilant mode](https://docs.github.com/github/authenticating-to-github/displaying-verification-statuses-for-all-of-your-commits) turned on. Commits don't contain signatures for co-authors, so GitHub can't be sure that the co-authors involved in a commit actually worked on it.

### Should I set my GPG key to expire?

In general, I'd recommend that too. Expiration dates allow the key to eventually stop working even if you lose control of it (like if you forget its passphrase or you lose the key). I personally set my signing keys to expire after 3 years from the time I create them. If you didn't set an expiration date, it's okay - you can still revoke your key from GitHub if you ever think it might have been compromised so that GitHub won't mark future commits signed with that key as verified if someone has a hold of it.

It's also possible to renew your signing keys as long as you still have all of the information about them, resetting the expiration date so they last longer. But if you think your key was compromised, you should make a new one (and a new passphrase).

### Should I choose a strong passphrase?

Yes. If your key is compromised, it's not game over as long as your passphrase is strong - it can still protect your signing key so it can't be used by other people. It's basically two-factor authentication, and similar to a PIN for a credit/debit card.

At that point, though, you'll probably want to work on switching to a new signing key, just in case.

### Does GitHub Desktop sign commits for me like GitHub?

No, because GitHub Desktop uses Git under the hood, and, again, you can configure Git to use whatever information you want. However, it can automatically sign your commits with your own signing key if you configured your Git client to sign commits by default.

## GitHub Docs

For more information, like how to make your own signing key, check out the [GitHub documentation on managing commit signature verification](https://docs.github.com/en/authentication/managing-commit-signature-verification).
