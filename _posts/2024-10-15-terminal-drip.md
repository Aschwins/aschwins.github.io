---
layout: post
title: Terminal Drip
date: 2024-10-14 9:25:00
description: a question I get asked a lot at the office
tags: bash unix
categories: programming
thumbnail: assets/img/terminal-drip.jpeg
toc:
  sidebar: left
tabs: true
---

## Introduction

I get asked this question a lot at the office: "How do you get your terminal to look like that?". The goal of this blogpost is to answer that question. I will show you how to make your terminal drip with drip.

If you hear yourself say a simple terminal with bash is all I need. I don't need fancy themes or custom fonts or animated backgrounds. I just need it to work. Then you don't appreciate the art of productivity. You also don't see the value in making tools pleasure you.

If you want to hop on the drip train, please continue to read and implement the following steps.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/terminal-no-drip.png" class="img-fluid" zoomable=true %}
    </div>
</div>
<div class="caption">
    A terminal with absolutely no drip. It almost hurts to look at.
</div>

## Pre-requisites

Before we get started, you need to have the following installed on your system:

- bash
- git

If you are on Windows, use WSL. If you are on macOS, you can use the mac specific commands.

<br/>

## TLDR

Run the following commands in your terminal. If you're on MacOs please scroll down to the collapsed section.

{% tabs os %}

{% tab os linux %}

```bash
# install zsh
sudo apt install zsh

# install oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# change your default shell to zsh
chsh -s $(which zsh)

# restart your terminal
zsh

# install zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# install zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# install zsh-completions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# install zsh-history-substring-search
git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search

# install bat
sudo apt install bat

# replace plugins line in .zshrc file to contain the correct plugins
sed -i '/plugins=(git)/c\plugins=(git docker zsh-syntax-highlighting zsh-autosuggestions zsh-history-substring-search)' ~/.zshrc

# create a file to store your aliases
touch ~/.zsh_aliases

# alias cat to bat
echo "alias cat='bat'" >> ~/.zsh_aliases

# source the aliases file in your .zshrc
echo "source ~/.zsh_aliases" >> ~/.zshrc
```

{% endtab %}

{% tab os MacOS %}

```bash
# install zsh
brew install zsh

# install oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# change your default shell to zsh
chsh -s $(which zsh)

# restart your terminal
zsh

# install zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# install zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# install zsh-history-substring-search
git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search

# install bat
brew install bat

# create a file to store your aliases
touch ~/.zsh_aliases

# alias cat to bat
echo "alias cat='bat'" >> ~/.zsh_aliases

# source the aliases file in your .zshrc
echo "source ~/.zsh_aliases" >> ~/.zshrc

# replace plugins line in .zshrc file to contain the correct plugins
sed -i '' '/plugins=(git)/c\
plugins=(git docker zsh-syntax-highlighting zsh-autosuggestions zsh-history-substring-search)' ~/.zshrc
```

{% endtab %}

{% endtabs %}

<br/>

## Step by Step with explanation

<br/>

### 1. Install ZSH

Bash on steroids.

[Zsh](https://zsh.sourceforge.io/) or Z shell is a shell designed for interactive use, although it is also a powerful scripting language. Many of the useful features of bash, ksh, and tcsh were incorporated into zsh; many original features were added. The result is a powerful shell with advanced scripting capabilities.

To install Zsh on Ubuntu, run the following command:

{% tabs os %}

{% tab os linux %}

```bash
sudo apt install zsh
```

{% endtab %}

{% tab os MacOS %}

```bash
brew install zsh
```

{% endtab %}

{% endtabs %}

Now we always want to use zsh over bash, so we set the default shell to zsh.

```bash
chsh -s $(which zsh)
```

<br/>

### 2. Install Oh-My-Zsh

The package manager of Zsh.

[Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh) is an open-source, community-driven framework for managing your Zsh configuration. It comes bundled with a ton of helpful functions, helpers, plugins, themes, and a few things that make you shout...

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

<br/>

### 3. Install ZSH plugins

The drip.

There are many great plugins for Zsh. Here are a few that I use:

- [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting) - Fish shell-like syntax highlighting for Zsh. This makes it easier to spot errors in your commands.
- [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) - Fish-like autosuggestions for Zsh. This suggests commands as you type based on your command history. Use tab to accept the suggestion.
- [zsh-history-substring-search](https://github.com/zsh-users/zsh-history-substring-search) - This plugin adds a feature where you can search your history by typing a substring of the command you are looking for and pressing the up and down arrow keys to cycle through the results.

Since we are using Oh-My-Zsh, we can install these plugins by cloning them into the `~/.oh-my-zsh/custom/plugins` directory and adding them to the plugins list in the `.zshrc` file.

```bash
# install zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# install zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# install zsh-history-substring-search
git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search
```

<br/>

### 4. Install bat

A cat clone with wings.

{% tabs os %}

{% tab os linux %}

```bash
sudo apt install bat
```

{% endtab %}

{% tab os MacOS %}

```bash
brew install bat
```

{% endtab %}

{% endtabs %}

Just like Batman has a utility belt, you can have a utility command. Replace the `cat` command with `bat` by adding the following alias to your `.zsh_aliases` file.

```bash
# create a file to store your aliases
touch ~/.zsh_aliases

# alias cat to bat
echo "alias cat='bat'" >> ~/.zsh_aliases

# source the aliases file in your .zshrc
echo "source ~/.zsh_aliases" >> ~/.zshrc
```

<br/>

### 5. Change your .zshrc file

Customize your Zsh configuration.

Open your `.zshrc` file in your favorite text (e.g. `vim ~/.zshrc`) editor and replace the plugins line with the following:

```bash
plugins=(git docker zsh-syntax-highlighting zsh-autosuggestions zsh-history-substring-search)
```

Don't forget to `source ~/.zshrc` to apply the changes, or restart your terminal.

<br/>

### The cherry on top

It's over 9000!

If you're a minimalistic person, you can stop here. But if you want to take it to the next level, you can install a custom theme for Oh-My-Zsh. I recommend [Powerlevel10k](https://github.com/romkatv/powerlevel10k).

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/terminal-yes-drip.png" class="img-fluid" zoomable=true %}
    </div>
</div>
<div class="caption">
    A terminal dripping with drip. I can stare at this all day.
</div>
