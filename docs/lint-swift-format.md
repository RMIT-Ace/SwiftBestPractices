# Lint: Swift-Format

* Comes with Xcode 27 chain tool
* Can be run with 'xcrun'

To find where the tool is located.

```
xcrun -f swift-format
```

To get help on `swift-format`

```
xcrun swift-format --help
```

## Checking Style Issues

To get help with linting

```
xcrun swfit-format lint --help
```

Diagnose style issues with your code

```
xcrun swift-format lint -r .
```

Sample outputs:

```
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:9:1: warning: [OrderedImports] sort import statements lexicographically
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:15:1: warning: [TrailingWhitespace] remove trailing whitespace
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:17:1: warning: [TrailingWhitespace] remove trailing whitespace
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:19:20: warning: [AddLines] add 1 line break
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:20:29: warning: [Spacing] remove 1 space
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:20:69: warning: [Spacing] remove 1 space
FoodTastingJournal/FoodJournalTests/FoodJournalTests.swift:22:20: warning: [AddLines] add 1 line break
F
...
```

Customise your style

```
xcrun swift-format dump-configuration > .swift-format
```

Save swift-format configuration.

```
xcrun swift-format dump-configuration > .swift-format
```

Customise your code formatting style in `.swift-format`, for example.

```
{
  ...

  "indentation" : {
    "spaces" : 4
  },

  ...

  "lineLength" : 100,
  "maximumBlankLines" : 1,

  ...

  "tabWidth" : 4,

}

```

Rerun your linting.

## Formatting your code

To get help

```
xcrun swift-format format --help
```

Formatting individual file.

```
xcrun swift-format format <FILENAME>
```

Format and modify the file.

```
xcrun swift-format format -i <FILENAME>
```

Formatting whole project.

```
xcrun swift-format format -i -r .
```

Mention that it is a good idea to maintain source code under git for in case of reverting the lint changes.
