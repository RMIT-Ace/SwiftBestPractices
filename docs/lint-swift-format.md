# Swift Best Practices: Keep Your Code Clean with Swift-Format

Writing Swift code is one thing — writing *consistent*, readable Swift code is another. As your projects grow, it becomes harder to keep everyone (including future you) on the same page stylistically. That's where **swift-format** comes in.

In this post, we'll walk through what swift-format is, how to use it, and how to tailor it to your own style preferences.

---

## What Is Swift-Format?

`swift-format` is Apple's official tool for formatting and linting Swift source code. It helps you:

- **Lint** your code — spot style issues before they become habits
- **Format** your code — automatically fix those issues in place

The great news for Xcode 26+ users: swift-format ships as part of the Xcode toolchain, so there's nothing extra to install. You access it via `xcrun`, Apple's command-line tool runner.

---

## Finding the Tool

Not sure if swift-format is available on your machine? Run this to find its location:

```bash
xcrun -f swift-format
```

If a path is returned, you're good to go. You can also check its available commands anytime with:

```bash
xcrun swift-format --help
```

---

## Checking for Style Issues (Linting)

Linting is the process of *identifying* style problems in your code without changing any files. Think of it as a code style report card.

To see linting options:

```bash
xcrun swift-format lint --help
```

To lint your entire project recursively (the `-r` flag means "recursive"):

```bash
xcrun swift-format lint -r .
```

You'll see output like this, pointing to exactly where each issue lives:

```
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:9:1: warning: [OrderedImports] sort import statements lexicographically
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:15:1: warning: [TrailingWhitespace] remove trailing whitespace
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:17:1: warning: [TrailingWhitespace] remove trailing whitespace
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:19:20: warning: [AddLines] add 1 line break
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:20:29: warning: [Spacing] remove 1 space
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:20:69: warning: [Spacing] remove 1 space
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:22:20: warning: [AddLines] add 1 line break
```

Each line tells you:
- The **file** and **line number**
- The **rule** that was violated (e.g., `OrderedImports`, `TrailingWhitespace`)
- What to **do about it**

---

## Customising Your Style

Swift has a default style, but you might have preferences — maybe you like 4-space indentation instead of 2, or longer line lengths. You can generate a configuration file to customise these rules:

```bash
xcrun swift-format dump-configuration > .swift-format
```

This creates a `.swift-format` file in your project's root directory. Open it and you'll find all the available settings. Here are a few common ones to tweak:

```json
{
  "indentation": {
    "spaces": 4
  },
  "lineLength": 100,
  "maximumBlankLines": 1,
  "tabWidth": 4
}
```

Once you've saved your changes, re-run the linter and it'll apply your custom rules:

```bash
xcrun swift-format lint -r .
```

> **Tip:** Commit your `.swift-format` file to your git repository so everyone on your team uses the same style rules automatically.

---

## Formatting Your Code (Auto-Fix)

Once you know what needs fixing, you can let swift-format do the heavy lifting and rewrite your files automatically.

To see formatting options:

```bash
xcrun swift-format format --help
```

To preview the formatted output for a single file (without changing it):

```bash
xcrun swift-format format MyFile.swift
```

To format and **save** a single file in place:

```bash
xcrun swift-format format -i MyFile.swift
```

To format and save your **entire project** in place:

```bash
xcrun swift-format format -i -r .
```

The `-i` flag means "in-place" — it modifies your files directly rather than just printing results to the terminal.

---

## Before You Format: Use Git

Running `swift-format format -i -r .` will change a lot of files at once. Before you do that, make sure your code is committed to git. That way, if anything looks off after formatting, you can easily review the diff or revert:

```bash
git diff
```

or

```bash
git checkout .
```

Good version control habits and good formatting habits go hand in hand.

---

## Wrapping Up

`swift-format` is a straightforward but powerful tool for keeping your Swift code clean and consistent. Here's a quick recap:

- Use `xcrun swift-format lint -r .` to **find** style issues
- Use `xcrun swift-format dump-configuration > .swift-format` to **customise** your rules
- Use `xcrun swift-format format -i -r .` to **fix** them automatically
- Always **commit to git** before a project-wide format

Start with linting on a small project or even just a test file — you might be surprised how much it catches. Happy formatting!
