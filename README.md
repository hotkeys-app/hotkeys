# Hotkeys

True hotkeys for macOS. One plain text file binds any key to any action: a shell command, an
AppleScript, a menu item, another key combination, everywhere or only in the app or window you
choose.

This repository is the public side of the app: config examples you can paste into your own file,
the issue tracker, and the place to send configs of your own. The app itself is closed source and
lives at [hotkeys.io](https://www.hotkeys.io).

```yaml
hotkeys:
    f1: open -a "Google Chrome"                 # any shell command
    _#k: runApp("Telegram")                     # command k, built in method
    home:
        currentAppTerminal(): sendKeys("control-a")     # only inside Terminal
    ^!#\: displayActiveWindowInfo()             # what is this app called?
    _!*: switchKeyboardLayout("com.apple.keylayout.US", "com.apple.keylayout.Spanish")
```

The last line has no key in it at all. Option and Shift pressed together and released switches the
input source, the way Alt and Shift do on Windows. Any two layouts you have enabled work there.

The line above it answers the question every config starts with. Press control option command
backslash in any app and Hotkeys tells you its bundle id, process name and window title, which is
exactly what contexts match on.

## Install

```sh
brew install --cask hotkeys-app/tap/hotkeys
```

Or the notarized dmg from the [download section](https://www.hotkeys.io/#download). macOS 14 Sonoma
or later, universal binary. Hotkeys needs the Accessibility permission to see keys before the app in
front does, and Screen Recording only if you match on window titles.

There is also **Hotkeys Lite** on the Mac App Store. It is the sandboxed edition: it launches apps and
runs scripts, but the App Store rules leave out key sending, menu clicking and modifier only hotkeys.

## The config in a minute

The file lives at `~/Library/Application Support/hotkeys/hotkeys.yml`. Open it from the menu bar icon,
edit, then Reload Config.

Modifiers are one symbol each, or a word if you prefer reading: `^` ctrl, `!` option, `*` shift,
`#` command, `fn`. `^!f1`, `control-option-f1` and `ctrl-alt-F1 ` are the same hotkey. YAML treats
`#`, `*` and `!` as special at the start of a line, so a hotkey name starting with one takes a leading
underscore that Hotkeys strips: `_#k` is command k.

A value is either a shell command, a built in method written `name("arg")`, or a mapping of contexts
to actions:

```yaml
f2:
    currentApp("com.apple.dt.Xcode"): sendKeys("command-x")
    currentWindowContains("— mc "): ~/bin/mc-helper.sh
```

Repeated text goes into `macros:`, which are substituted in contexts and actions. The full reference,
every method, key name and permission, is in the [documentation](https://www.hotkeys.io/quick-start.html).

## Examples

Copy the entries you want into your own config. Each file says what it needs.

| File | What it does |
| --- | --- |
| [start-here.yml](examples/start-here.yml) | The free tier. Dialogs, launchers, shell commands, reload |
| [terminal-keys.yml](examples/terminal-keys.yml) | Home, End and word jumps in Terminal, translated to readline keys |
| [windows-switcher.yml](examples/windows-switcher.yml) | The keys Windows users miss, including Alt+Shift layout switching |
| [app-launchers.yml](examples/app-launchers.yml) | One key per app, launch or bring to the front |
| [android-emulator.yml](examples/android-emulator.yml) | Back, home and recents for the emulator and for scrcpy devices |
| [iphone-mirroring.yml](examples/iphone-mirroring.yml) | iPhone Mirroring and the iOS Simulator from the keyboard |
| [xcode.yml](examples/xcode.yml) | Editing keys from other editors, and project files on single keys |
| [jetbrains.yml](examples/jetbrains.yml) | IDE launchers, and how to fire an IDE action from one key |
| [midnight-commander.yml](examples/midnight-commander.yml) | Matching on a window title instead of an app |
| [text-snippets.yml](examples/text-snippets.yml) | Type timestamps, transform the clipboard, take screenshots |

## What Hotkeys is not

It does one thing, and these tools do the others better:

- Device level remapping, Caps Lock as Hyper, per keyboard rules: **Karabiner-Elements**, free and open source.
- Trackpad and mouse gestures, Touch Bar, window snapping: **BetterTouchTool**.
- A GUI macro editor with triggers that are not keys: **Keyboard Maestro**.

Hotkeys is for people who would rather keep their bindings in a file they can read, diff and copy to
the next Mac. It is closed source, so if that rules it out, Karabiner-Elements and skhd are the open
alternatives.

## Price

Ten hotkeys are free with no time limit. A license unlocks the rest on three Macs: 9 USD a year or
15 USD once. Contexts and most built in methods need the license, shell commands and AppleScript do not.

## Privacy

No account, no analytics, no crash reporter. The app reaches the network twice: to check for updates,
and to validate a license key. Accessibility is what lets it see a key before the app in front does,
which is also why the config stays a file you control rather than a service.

## Issues

Bugs, feature requests and config help all go to [Issues](https://github.com/hotkeys-app/hotkeys/issues).
Questions that are not public: support@hotkeys.io.

## License

The examples in this repository are CC0, use them however you like. The scripts are MIT. The Hotkeys
app itself is proprietary.