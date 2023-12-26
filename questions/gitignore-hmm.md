# What do I even gitignore?

Perfecting your repository's `.gitignore` file can take some research and effort.

Operating systems and some programs such as IDEs sometimes create their own files in the folders containing your Git repositories that you don't want in your published source code. These files might be hidden so they may not show up in file manager GUIs and include things that the system or programs use such as thumbnail caches, folder configurations, and more.

Like any file, these can be accidentally staged and committed when you use Git. That's why it's helpful to add the paths to these files to your `.gitignore` file, but how are you supposed to know all of the different files you need to have Git ignore?

For this problem, I recommend GitHub's official [`gitignore` repository](https://github.com/github/gitignore). It contains a bunch of `.gitignore` files with commonly used ignore paths, ready for you to use. Just copy the ignore paths you need and put them all in your own `.gitignore` file.

[Learn more about the folder structure here](https://github.com/github/gitignore/blob/main/README.md#folder-structure).

(Its contents are also under a CC0-1.0 license, so no worries about copyright.)

## Learn more about gitignore

See the gitignore articles on the [Git documentation](https://git-scm.com/docs/gitignore) and [GitHub documentation](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files).
