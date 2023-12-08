# Signing key FAQs

### What is a signing key and why is it useful?

A signing key adds a digital signature to your files that prove that they came from you, in short.

In terms of GitHub, because Git can be configured to commit under any name and email and GitHub uses that information to identify which GitHub account made that commit, anyone is able to easily make it look like you made a commit by configuring their Git client to use your information in any commit. Signing keys solve that problem by adding authentication to the process. Only you will have access to the signing key(s) you use to sign your commits, so if someone tries to impersonate you, they're not going to be able to sign the commit with your signing key, so they cannot prove you were involved in that commit.

### Should I sign my commits?

I'd recommend it, especially if you're high-profile or contributing to high-impact repositories. You might run into a situation where you need to sign your commits (some repositories actually require this) and it gives other people confidence that the commits came from you and someone didn't just enter your user information to push a commit that appears to have come from you, which can be a headache. If you're interested in contributing, it's good to have one.

### Someone is impersonating me in commits. What do I do?

You can enable [vigilant mode](https://docs.github.com/github/authenticating-to-github/displaying-verification-statuses-for-all-of-your-commits) in GitHub settings → [SSH and GPG keys](https://github.com/settings/keys).

Vigilant mode adds an "Unverified" label to commits that aren't signed with one of your signing keys. When other people see "Unverified", they can tell that someone may have pushed a commit as you without you actually having made that commit.

Only do this if you always sign your commits. Otherwise, it won't really help others differentiate commits you made from commits others made on your behalf.

### What if I don't have a signing key but still want to make signed commits?

Commit from the GitHub website or, if you want a code editor, the [github.dev web-based editor](https://docs.github.com/en/codespaces/the-githubdev-web-based-editor). GitHub will sign those for you, without the need for your own signing key.

### Why does GitHub sign the commits for me? How is that possibly safe?

Well, get this. On GitHub, when you're signed into your GitHub account, which only you would have access to, GitHub knows the commits you made on the website are coming from you. The same can't be said for Git, where we can impersonate someone by configuring Git to use their information in the commits we make without needing any sort of verification (unless they have their own signing key). Anyone can do that, but no one can sign into your account on GitHub as long as you keep it secure.

That's why we need to set up our own way of verifying that it's us for commits we make outside GitHub but can let GitHub do that for us when we're making those changes on GitHub. On the GitHub website, you cannot sign in as anyone else and impersonate them, and no one else can impersonate you either, when it comes to commit authors.

To summarize, you need at least one form of proper authentication to prove that a commit came from who the committer says it did, whether it's signing into GitHub and committing from somewhere you're signed in or using a signing key, and both of these only you can do.

### What does "partially verified" mean?

That appears next to co-authored commits if the co-authors have [vigilant mode](https://docs.github.com/github/authenticating-to-github/displaying-verification-statuses-for-all-of-your-commits) turned on. Commits don't contain signatures for co-authors, so GitHub can't be sure that the co-authors involved in a commit actually worked on it.

### Should I set my GPG key to expire?

In general, I'd recommend that too. Expiration dates allow the key to eventually stop working even if you can't revoke it. I personally set my signing keys to last 3 years. But if you don't set an expiration date, GitHub still lets you revoke your key in case it's ever compromised. After the key has expired, GitHub won't mark future commits signed with that key as verified, so if someone has a hold of it, it'll basically be useless.

When your key expires or if it is compromised, you should make a new one (and give it a new passphrase).

### Should I choose a strong passphrase?

Yes. If your key is compromised, it's not game over as long as your passphrase is strong - it's the second factor protecting your signing key so it can't be used by other people, even if they get a hold of it. It's similar to a PIN for a credit or debit card. Even if you have to save your passphrase somewhere to remember it, it is still important to use long, strong passphrases since hackers will have unlimited attempts to break the encryption.

After your key is compromised, though, you'll probably want to work on switching to a new signing key and revoking the old one, just in case.

Also, make sure each key has a unique passphrase, just like you would use different passwords for each of your accounts. Don't reuse passphrases between signing keys, because if the passphrase to an old signing key is found out, even one you don't use anymore, then hackers could try it on other signing keys they have.

### What if I lose my signing key?

Just make a new one.

### Does GitHub Desktop sign commits for me like GitHub?

No, because GitHub Desktop actually uses Git under the hood in order to commit, and, again, you can configure Git to use whatever information you want. However, it can automatically sign your commits with _your own_ signing key _if_ you configured Git to sign commits by default. Learn how to do that [here](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits).

## GitHub Docs

For more information, like how to make your own signing key, check out [Managing commit signature verification](https://docs.github.com/en/authentication/managing-commit-signature-verification) in the GitHub documentation.
