---
layout: post
title: iTerm2 + Oh My ZSH => a better Terminal
categories: Mac OS
tags: Mac OS
comments: true
---

![iTerm2 with ZSH](/public/images/setup-iterm-on-mac/1.png)

iTerm2 is an OpenSource replacement for apples Terminal. It is highly customisable and has a lot of useful features. This is a getting started guide for anyone new to MacOS and in general development.

### Install Iterm2

Download and install the latest version of iTerm2 from [iterm2.com](https://iterm2.com/downloads.html).

### Install Zsh

Zsh is one of the most popular shells that you can install. `zsh` includes many useful features for both the beginner and advanced CLI user. It also includes support for autocomplete and plugins. Install `zsh` using the `brew` command.

```bash
brew install zsh
```

### Install Oh My ZSH

`On My Zsh` is a community driven framework to manage `zsh` configurations. It comes bundled with a ton of helpful functions, helpers, plugins and themes.

Install Oh My ZSH by following the instructions from the [ohmyz.sh](https://ohmyz.sh/) website.

### Use an Oh My ZSH theme

Check out the various [themes](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes) provided by Oh My ZSH.

You can change the theme by editing the file `~/.zshrc`.

```bash
vim ~/.zshrc
```

Set the theme that you want. Here I am setting it to `avit`.

![Zsh theme](/public/images/setup-iterm-on-mac/2.png)

### Configure shortcuts

iTerm2 lets you configure shortcuts. Here are some of the shortcuts that I find useful.

To configure shortcuts:

- Open iTerm2
- iTerm2 -> Preferences (⌘ + ,)
- Open the `Profile` tab and then click on `Keys`
- Add the following Shortcut Keys

![Move cursor one word left](/public/images/setup-iterm-on-mac/3.png)

#### Move cursor one word left

- Keyboard Combination: ⌥ + ←
- Action: Send Hex Code
- Code: 0x1b 0x62

#### Move cursor one word right

- Keyboard Combination: ⌥ + →
- Action: Send Hex Code
- Code: 0x1b 0x66

#### Move cursor to beginning of line

- Keyboard Combination: ⌘ + ←
- Action: Send Hex Code
- Code: 0x01

#### Move cursor to end of line

- Keyboard Combination: ⌘ + →
- Action: Send Hex Code
- Code: 0x05

#### Delete word

- Keyboard Combination: ⌥ + ←Delete
- Action: Send Hex Code
- Code: 0x1b 0x08

#### Delete line

- Keyboard Combination: ⌘ + ←Delete
- Action: Send Hex Code
- Code: 0x15

#### Undo

- Keyboard Combination: ⌘ + z
- Action: Send Hex Code
- Code: 0x1f

Check [this](https://stackoverflow.com/questions/6205157/iterm-2-how-to-set-keyboard-shortcuts-to-jump-to-beginning-end-of-line) StackOverFlow answer for more details.
