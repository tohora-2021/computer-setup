# MacOS and Linux Computer Setup for EDA

1. Start the terminal and install zsh and make it the default shell
    - Linux
        - `sudo apt-get install zsh`
        - `chsh -s $(which zsh)`
        - Restart the terminal (or log out and log back in to your computer)
    - MacOS
        - Install [Homebrew](https://brew.sh/) with `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
        - Verify it is setup correctly with `brew doctor`
        - You will be requested to install the Command Line Developer Tools from Apple. Confirm by clicking Install. After the installation finished, continue installing Homebrew by hitting Return again.
        - Install zsh with `brew install zsh`
        - Make it the default shell: `sudo sh -c "echo $(which zsh) >> /etc/shells" && chsh -s $(which zsh)`
        - Restart the terminal (or log out and log back in to your computer)
1. Open a terminal and if you are prompted to make a choice, choose `q`.
1. Install oh-my-zsh from inside the terminal
    - `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`
    - Restart the terminal
1. Install VS Code if it isn't already installed
1. In your terminal, open VS Code with `code .`
1. Install the following VS Code extensions
    - ESLint
    - Live Share (online students only)
    - vscode-icons (optional, but pretty :wink:)
    - Bracket Pair Colorizer (optional)
    - GitLens (optional)
1. Install nvm
    - `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash`
1. Move the 3 nvm lines from the bottom of `.bashrc` to the bottom of `.zshrc`
1. Change the oh-my-zsh theme at the top of the `.zshrc` file from `bobbyrussell` to `bira`.
1. `nvm install --lts`
1. In your terminal install some global npm packages
    ```sh
    npm install -g \
    eslint@5.16.0 \
    babel-eslint@10.0.1 \
    eslint-config-standard@12.0.0 \
    eslint-plugin-import@2.17.3 \
    eslint-plugin-node@9.1.0 \
    eslint-plugin-promise@4.1.1 \
    eslint-plugin-react@7.13.0 \
    eslint-plugin-standard@4.0.0
    ```
1. Add a global ESLint config file to your home folder
    - Run `code .` in your terminal
    - Paste in these contents
    ```js
    {
      "parser": "babel-eslint",
      "env": {
        "browser": true,
        "node": true,
        "jest": true
      },
      "extends": [
        "eslint:recommended",
        "plugin:react/recommended",
        "standard"
      ],
      "plugins": [
        "standard",
        "promise"
      ],
      "rules": {
        "eol-last": ["error", "always"],
        "no-multiple-empty-lines": [
          "error", { "max": 1, "maxEOF": 0, "maxBOF": 0 }
        ],
        "object-curly-spacing": [2, "always"],
        "react/prop-types": "off"
      },
      "settings": {
        "react": { "version": "detect" }
      }
    }
    ```
    - Save the file as `.eslintrc.json` in your home folder.
1. Add a shortcut key to auto-format JavaScript. In VS Code, go to top menu and select Code :arrow_right: Preferences :arrow_right: Keyboard Shortcuts and then select the turning page icon in top right to see `keybindings.json`. Paste in these contents.
    ```js
    [
      {
        "key": "shift+alt+b",
        "command": "eslint.executeAutofix",
        "when": "editorFocus"
      }
    ]
    ```
