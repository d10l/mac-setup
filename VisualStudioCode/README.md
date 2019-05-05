# Visual Studio Code

[Visual Studio Code](http://www.sublimetext.com/) is a widely used editor.

## Installation

If you followed the Homebrew Cask Section it should be installed otherwiese:

```sh
brew cask install visual-studio-code
```

## fn keys in touchbar

- Go to __Apple > System Preferences__
- Select the __Keyboard__ preference pane
- Click on the __Shortcuts__ tab
- In the left sidebar, select the __Function Keys__ option
- On the right-hand side click on the plus `+` button
- Select the Visual Studio Code app
- Add the app

## Configuration & Basics

With the [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync&WT.mc_id=vscode-smashing-buhollan) extension, you can export all of your VS Code settings to a Gist, and then pull them all down from another VS Code installation and have them immediately applied. `Install the extension` > Call `F12` and search for `sync` > configure with your github key and then download your configuration ([my settings](https://gist.github.com/denseidel/357d38d2a99c88f8d2cc5f5ca0e2d1b5)).

Follow the [Basics Tips & Tricks](https://github.com/Microsoft/vscode-tips-and-tricks) including installing the __CLI Tool__.

## Configure VS Code for your Language

- [Awesome VSCode](https://github.com/viatsko/awesome-vscode): with settings for different language JS, Typescript, Python
- [vscode-recipes](https://github.com/Microsoft/vscode-recipes): for Debugging different languages JS, React, Typescript, Docker

## Extensions

- Debugging Client and Server with [Compound Launch Configurations](https://code.visualstudio.com/docs/editor/debugging) and Debug with mid-line breakpoints promises with Column Breakpoints
- Paring with Visual Studio Live Share
  - More Info: https://code.visualstudio.com/blogs/2017/11/15/live-share
  - Security: https://docs.microsoft.com/en-us/visualstudio/liveshare/reference/security
  - Add this to your config: `"liveshare.guestApprovalRequired": true`

## Python Setup

  - https://realpython.com/python-development-visual-studio-code/
  - https://fedoramagazine.org/vscode-python-howto/
