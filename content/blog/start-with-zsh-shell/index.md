---
title: How to quickly start with zsh shell
date: "2020-01-02"
description: How to quickly start with zsh shell after installing MacOS Catalina and switch from bash to zsh without errors.
---

## Quick introduction

> Shell is a command line interface (CLI) that allows the users to interact with the computer’s operating system.

Before macOS Catalina, bash was the default shell on Mac OS X. Announced at [WWDC 2019](https://developer.apple.com/wwdc19/), Zsh became [the default shell](https://support.apple.com/en-ca/HT208050) for Mac users. It is an interactive shell which incorporates a lot of useful features from other shells. In addition, there’s a bunch of things Zsh can do to make your terminal experience better. Enhanced auto-completions and globbing, spell correction, path replacement, the list goes on.

## Quick setup

> After every instalation close the terminal window and reopen it.

Open your terminal and enter `chsh -s /bin/zsh`

Enter your password when prompted. After you close the terminal window and reopen it, you’ll be using Zsh.

`echo ${SHELL}`

expected result: /usr/bin/zsh or similiar

```
${SHELL} --version
```
expected result: zsh 5.7.1 (x86_64-apple-darwin19.0) ir similiar

## Next steps aka install oh-my-zsh

First you will need to install xcode-select 

```xcode-select --install```

If you are using brew you should update and upgrade 

```
brew update
brew upgrade
```

and then install oh-my-zsh
```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Go to config file 

```
nano ~/.zshrc
```

and uncomment aliases at the bottom #Example aliases. Also set the editor you feel most comfortable with. At the end it should look something like this (if you like nano editor)
```
# Example aliases
alias zshconfig="nano ~/.zshrc"
alias ohmyzsh="nano ~/.oh-my-zsh"
```

Now you can open the config by entering `zshconfig`. 

## More cool stuff

If you want to have autosuggest in zsh install this plugin.

```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

and inside zsh config file update this line

```
plugins=(git zsh-autosuggestions)
```

You can find more plugins [here](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins).

You can set your own theme also by updating ZSH_THEME with the name of the theme. Check list of themes [here](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes).

```
ZSH_THEME=macovsky-ruby
```

## If you used nvm for node in bash (and you installed it with brew)

Before zsh I used bash and installed node with nvm to support different versions of it. Once I switched to zsh it was saying `zsh: command not found: node` when I tried to do node command. For fixing this issue add this at the top of your zsh config file, before Oh My Zsh is sourced ( this line: # Path to your oh-my-zsh installation ).

```
# for nvm installed with brew
export NVM_DIR="$HOME/.nvm"
. "$(brew --prefix nvm)/nvm.sh"
```

## If you used Golang in bash

And it is not working after upgrade to zsh, add this in zshconfig, also before Oh My Zsh is sourced.

```
# GOPATH
export GOPATH="$HOME/go"
export PATH="$PATH:$HOME/go/bin"
export GO111MODULE=on
```

### And that’s it. Happy coding!

[Edit on GitHub](https://github.com/janedzumerko/blog/edit/master/content/blog/start-with-zsh-shell/index.md)