# Contributing to Homebrew

First time contributing to Homebrew? Read our [Code of Conduct](https://github.com/Homebrew/.github/blob/HEAD/CODE_OF_CONDUCT.md#code-of-conduct).

### To report a bug

* run `brew update` (twice)
* run and read `brew doctor`
* read [the Troubleshooting Checklist](https://docs.brew.sh/Troubleshooting)
* open an issue on the formula's repository

### To submit a version upgrade for the `foo` formula

* check if the same upgrade has been already submitted by [searching the open pull requests for `foo`](https://github.com/Homebrew/homebrew-core/pulls?utf8=✓&q=is%3Apr+is%3Aopen+foo).
* `brew bump-formula-pr --strict foo` with `--url=...` and `--sha256=...` or `--tag=...` and `--revision=...` arguments.

### To add a new formula for `foo` version `2.3.4` from `$URL`

* read [the Formula Cookbook](https://docs.brew.sh/Formula-Cookbook) or: `brew create $URL` and make edits
* `brew install --build-from-source foo`
* `brew audit --new-formula foo`
* `git commit` with message formatted `foo 2.3.4 (new formula)`
* [open a pull request](https://docs.brew.sh/How-To-Open-a-Homebrew-Pull-Request) and fix any failing tests

Once you've addressed any potential feedback and a member of the Homebrew org has approved your pull request, the [BrewTestBot](https://github.com/BrewTestBot) will automatically merge it a couple of minutes later.

### To contribute a fix to the `foo` formula

If you are already well versed in the use of `git`, then you can find the local
copy of the `homebrew-core` repository in this directory
(`$(brew --prefix)/Homebrew/Library/Taps/homebrew/homebrew-core/`), modify the formula there
leaving the section `bottle do ... end` unchanged, and prepare a pull request
as you usually do.  Before submitting your pull request, be sure to test it
with these commands:

```
brew uninstall --force foo
brew install --build-from-source foo
brew test foo
brew audit --strict foo
brew style foo
```

After testing, if you think it is needed to force the corresponding bottles to be
rebuilt and redistributed, add a line of the form `revision 1` to the formula,
or add 1 to the revision number already present.

If you are not already well versed in the use of `git`, then you may learn
about it from the introduction at
https://docs.brew.sh/How-To-Open-a-Homebrew-Pull-Request and then proceed as
follows:
