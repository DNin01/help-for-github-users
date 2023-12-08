# What is an end of line sequence?

Graphical user interfaces typically display text files in 2 dimensions. Whenever you press the <kbd>return</kbd> key, you create a line break, splitting the following text into a new line, rendered on the next row. However, data is stored in 1 dimension, so to encode line breaks, computers have to use a special character or set of characters called an end of line sequence, or line ending for short.

The standard Unix end of line sequence is `\n` (U+000A in Unicode), called linefeed (LF). It's just a single character that creates a line break, which in a GUI, splits the following text into a new line. This sequence is used by macOS, Linux, and most other modern operating systems. However, Windows has historically used a different sequence, `\r\n` (U+000D U+000A in Unicode), which is a sequence of two characters, carriage-return and linefeed (CRLF). The reason this was used in Windows was for compatibility with typewriters back in the day, as the carriage-return character shifts the typewriter carriage back to the first column, then linefeed makes it move down a row. Even though the days of typewriters are long gone, CRLF is still used by Windows today.

## Why is it important to consider line endings?

With two different standard types of end of line sequences actively used in files, we need to have a way to convert them to work with each operating system. If we feed a program code or data with an unexpected end of line sequence, it won't read it properly, so these days, source code for cross-platform software is generally stored with LF line endings, and when released for download, converted as needed.

The problem for us is that as a developer, there's no one way to write source code that will work in all operating systems - the line endings would need to somehow be converted automatically. Fortunately, Git has a feature to automatically convert end of line sequences as needed, configured with the Auto-CRLF setting.

## What does Auto-CRLF do?

Git repositories are supposed to store code with LF line endings, but in order for code to be properly read by some Windows programs, the line endings need to be converted to CRLF. The Auto-CRLF setting automates this process. It makes sure of two things:
- That code in the working directory (a.k.a. code that is checked out) uses CRLF
- That whatever code is committed to the repository uses LF

## How do I correctly configure automatic line ending conversion as a contributor?

Auto-CRLF is configurable by setting `core.autocrlf`:
```shell
git config --global core.autocrlf ...
```

There are three options for Auto-CRLF: `false`, `input`, and `true`.

Setting `core.autocrlf` to `false` disables the feature. Code that is checked out will have line endings preserved as well as when committing.

If `core.autocrlf` is set to `input`, code that you commit will have its line endings converted to LF, but line endings won't be converted during checkout, so incoming code will stay the same.

Setting `core.autocrlf` to `true` means that line endings will be converted to CRLF during checkout and saved as LF when committed.

Unless otherwise specified by the repository's guidelines, it's best to configure Auto-CRLF as follows:

### If you're using macOS or Linux

On systems that use LF line endings such as macOS and Linux, we don't really need to do anything with incoming changes - it's standard for Git repositories to store code with LF line endings, and these operating systems use LF anyway. However, sometimes CRLF line endings can pop up by accident in files you are committing. It doesn't hurt to be safe, so many users configure Git to convert outgoing CRLF line endings to LF. To achieve this behavior, set `core.autocrlf` to `input`:
```shell
git config --global core.autocrlf input
```

### If you're using Windows

On systems that use CRLF line endings such as Windows, we need to remember to convert any CRLF line endings to LF when committing, as it is standard to use LF line endings in Git repositories. And as well, we need to make sure that incoming LF line endings are converted to CRLF. To do this, set `core.autocrlf` to `true`:
```shell
git config --global core.autocrlf true
```

## Resources

This information was based off of the official Git documentation.

`core.eol`: https://git-scm.com/docs/git-config#Documentation/git-config.txt-coreeol

`core.autocrlf`: https://git-scm.com/docs/git-config#Documentation/git-config.txt-coreautocrlf

`text` and `eol` in `.gitattributes`: https://git-scm.com/docs/gitattributes#_checking_out_and_checking_in
