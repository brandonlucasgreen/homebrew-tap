# Homebrew tap for Inbox & Chill

[Inbox & Chill](https://github.com/brandonlucasgreen/inbox-and-chill) is a
native macOS menu bar app that pulls your unread and actionable items from
Slack, Linear, GitHub, ntfy, Apple Mail, Sentry, custom JSON feeds and your
terminal into one triage queue — and then helps you empty it.

```sh
brew install --cask brandonlucasgreen/tap/inbox-and-chill
```

One command: it adds this tap, installs the app, and puts the `inchill` CLI on
your `PATH`. macOS 15 (Sequoia) or later. The app and the CLI are both signed
with a Developer ID, notarized and stapled.

Already installed the app by hand? Homebrew will not write over an app it does
not own, so adopt it instead:

```sh
brew install --cask --adopt brandonlucasgreen/tap/inbox-and-chill
```

macOS protects app bundles from being modified by processes without App
Management permission, so that one asks for your password.

## Updating

`brew upgrade` keeps it current, and so does the app's own updater — they read
the same Sparkle feed, and brew compares the version inside the installed app
rather than its own records, so whichever gets there first wins and the other
does nothing. One rough edge: `brew upgrade` quits the app to replace it and
does not reopen it.

## Uninstalling

```sh
brew uninstall --cask --zap brandonlucasgreen/tap/inbox-and-chill
```

`--zap` also removes the queue database, preferences and caches. Two things it
cannot reach:

- **Keychain items** — your source tokens live in the login keychain under
  `lol.bgreen.inboxandchill`. Delete them by hand if you want them gone.
- **Agent hooks** — if you let the app install Claude Code, Codex or Gemini CLI
  hooks, those live in your own config files and point into the app bundle.
  Turn them off in Settings *before* uninstalling, or they will quietly run a
  binary that is no longer there.

## About this repo

It holds one file: `Casks/inbox-and-chill.rb`, generated from
[`packaging/homebrew/inbox-and-chill.rb`](https://github.com/brandonlucasgreen/inbox-and-chill/blob/main/packaging/homebrew/inbox-and-chill.rb)
in the app repo and overwritten on every release. **Send changes there, not
here.** How it is maintained is in
[docs/homebrew.md](https://github.com/brandonlucasgreen/inbox-and-chill/blob/main/docs/homebrew.md).
