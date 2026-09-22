# Contributing

## Sending a config

Configs that solve a real problem are welcome, especially for apps nobody has covered yet.

Open a pull request that adds a file to `examples/`, or open an issue with the snippet pasted in and
it will be added for you.

What makes a good example:

- A header comment saying what it does, what it needs (a license, Screen Recording), and which app
  version it was tested against if that matters.
- Comments on the lines that are not obvious, especially which key a `sendKeys` call is imitating.
- No personal paths, no tokens, no internal URLs. `~/bin/script.sh` and `/Users/you/Projects/App`
  rather than your real tree.
- Keys that leave the common combinations alone. Function keys, the numeric keypad and modifier only
  hotkeys collide with the least.

Test it before sending: paste it into your own config, Reload Config, press the key.

## Reporting a bug

Include the config lines that misbehave, the app version from the menu bar, your macOS version, and
whether Accessibility and Screen Recording are granted. If a hotkey does nothing, check first whether
another app already owns that combination, System Settings, Keyboard, Keyboard Shortcuts.

## License

By sending an example you place it in the public domain under CC0. Scripts are MIT.