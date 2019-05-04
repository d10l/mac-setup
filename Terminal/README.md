# Terminal

## Customization

### Colors and Font Settings

Here are some suggested settings you can change or set, **they are all optional**.

- Download [Solarized Light](https://ethanschoonover.com/solarized/) and then set these to your default profile colors
- Change the font to 14pt Meslo for Powerline. Source Code Pro can be downloaded [here](https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf).
- If you're using BASH instead of ZSH you can add `export CLICOLOR=1` line to your `~/.bash_profile` file for nice coloring of listings

[![Screen](https://raw.githubusercontent.com/sb2nov/mac-setup/master/assets/Iterm.png)](https://raw.githubusercontent.com/sb2nov/mac-setup/master/assets/Iterm.png)

### MacOS shortcuts ⌘←, ⌘→ and ⌥←, ⌥→

You might be familiar with shortcuts to skip a word (⌥) or go to start/end of the line (⌘). iTerm is not set up to work with these shortcuts by default but here's how you set them up:

Open up iTerm2 preferences (⌘ + ,) -> Profiles -> Keys -> Click on `+` icon (add new Keyboard shortcut).

| shortcut |    action    | send  |
| :------: | :----------: | :---: |
|    ⌘←    | SEND ESC SEQ |  OH   |
|    ⌘→    | SEND ESC SEQ |  OF   |
|    ⌥←    | SEND ESC SEQ |   b   |
|    ⌥→    | SEND ESC SEQ |   f   |
