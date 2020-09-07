# Visual Studio Code Custom Settings

The custom VS Coder settings herein focus on a development workflow geared toward PHP, Drupal, Twig, Sass (SCSS), Liquid, and Javascript. You can get up and running with these custom settings by leveraging the [VS Code *Settings Sync* extension](https://github.com/shanalikhan/code-settings-sync). 

## Highlights
* PHP code sniffer
* Xdebug
* Material UI and icons
* PHP code intelligence and formatter
* SCSS formatting and intelligence
* Javascript & jQuery code hinting and linting

## To get up and running with these settings:

**Warning**: *Syncing these settings will wipe out your own custom settings so it might be a good idea to sync your current settings to a dedicated Gist first.*

1. Install the *Settings Sync* extension from within VS Code.
1. From the command palette: `>Sync > Advanced options > open settings`
2. Here, you are presented with an option for a Gist ID and custom access token which you will [need to create in your github account](https://github.com/settings/tokens).
3. Input the Gist ID, `365a204e173853452b436f53cc2fbb28` and the custom access token you just created above. (You can see the [full gist here](https://gist.github.com/danny-englander/365a204e173853452b436f53cc2fbb28).)
4. Now download the custom settings using the keyboard command, `Shift + Option + d`. This will also download dependent extensions into `~/.vscode/extensions`.
5. Note, if you were already using the sync extension, you may need to set Settings sync to `force download`.
5. For Xdebug to work, you will need to create a `launch.json` file in the root of your project located at `/.vscode/launch.json`. You can read about the settings, [here](https://github.com/felixfbecker/vscode-php-debug). I use Docksal for my local development environment and here are my custom Xdebug settings that are in `launch.json`. (These settings may vary depending on your local environment setup.)

        {
          "version": "0.2.0",
          "configurations": [
            {
              "name": "Listen for XDebug via Docksal",
              "type": "php",
              "request": "launch",
              "port": 9000,
              "pathMappings": {
                "/var/www/": "${workspaceRoot}"
              }
            },
            {
              "name": "Launch currently open script",
              "type": "php",
              "request": "launch",
              "program": "${file}",
              "cwd": "${fileDirname}",
              "port": 9000
            }
          ]
        }

6. There are a few tweaks that I needed to make.
    *  Set curly braces for *Intelephense* on functions to not go to the next line. 
        `"intelephense.format.braces": "k&r",` **<sup>[1](#kr)</sup>**
    * Drupal `.module` files not recognized by PHPCS - This is a known issue and there is a pull request open. [Add "extensions" configuration setting #172](https://github.com/ikappas/vscode-phpcs/pull/172) - Since the PR has not been approved yet, a quick fix is here: [https://github.com/ikappas/vscode-phpcs/issues/159#issuecomment-652672079](https://github.com/ikappas/vscode-phpcs/issues/159#issuecomment-652672079)

    

## Partial list of extensions

* [VS Code PHPCS - Integrates phpcs into Visual Studio Code](https://github.com/ikappas/vscode-phpcs)
* [Bracket Pair Colorizer - allows matching brackets to be identified with colors](https://github.com/CoenraadS/BracketPair)
* [PHP Debug Adapter for Visual Studio Code (Xdebug)](https://github.com/felixfbecker/vscode-php-debug)
* [PHP Intelephense - PHP code intelligence and formatter for Visual Studio Code](https://github.com/bmewburn/vscode-intelephense)
* [Settings Sync - must have extension to sync all your VS Code settings to a Github Gist](https://github.com/shanalikhan/code-settings-sync)
* [Material Theme, the most epic theme for Visual Studio Code](https://github.com/equinusocio/vsc-material-theme)
* [Material Icon Theme](https://github.com/PKief/vscode-material-icon-theme)
* [VSCode Color Info](https://github.com/mattbierner/vscode-color-info)
* [VS Code SCSS Formatter - an extension for Visual Studio Code to format SCSS.](https://github.com/sibiraj-s/vscode-scss-formatter)
* [SCSS IntelliSense - smart autocomplete of variables, mixins, and functions for all files in the project](https://github.com/mrmlnc/vscode-scss)
* [VS Code JSHint extension](https://github.com/Microsoft/vscode-jshint)


<a name="kr">1</a>: "The K&R style (Kernighan & Ritchie Style), which is also called "the one true brace style" in hacker jargon (abbreviated as 1TBS), is commonly used in C, C++, and other curly brace programming languages." [https://en.wikipedia.org/wiki/Indentation_style#K&R_style](https://en.wikipedia.org/wiki/Indentation_style#K&R_style)
