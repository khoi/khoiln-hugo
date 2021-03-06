---
title: "My  macOS development setup"
date: 2018-07-15T13:46:34+07:00
draft: true
---

[TOC]

## Introduction

The stuff that I do when I setup a new macOS. Mostly for personal references.

## Git

Get git

```bash
xcode-select --install
```

## Restoring the dotfiles

Time to restore my beloved [dotfiles](https://github.com/khoi/dotfiles). My dotfiles mostly contains my zsh, [Neovim](https://neovim.io), Tmux, some other customizations.

I use GNU Stow to manage my dotfiles, instruction is on the Github repo.

## `macOS` tweaks

- Remap `caps lock` to `Control`
- Run [.macos](https://github.com/khoi/dotfiles/blob/master/darwin/.macos)

## `nix`

I recently moved from Homebrew to [nix](https://nixos.org/nix/) to manage my dependencies.

```bash
sh <(curl https://nixos.org/nix/install) 
```

The packages are defined in [~/.config/nixpkgs/config.nix](~/.config/nixpkgs/config.nix).

To install

```bash
nix-env -iA nixpkgs.myPackages --verbose
```

## Homebrew

While I mostly use `nix` for managing system, CLI applications, I still have to use `homebrew cask` to install GUI applications and some fonts. 

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

The casks that I use are listed in my [dotfiles/darwin/casks](https://raw.githubusercontent.com/khoi/dotfiles/master/darwin/casks). 

```bash
curl https://raw.githubusercontent.com/khoi/dotfiles/master/darwin/casks | xargs brew cask install
```

## Install AppStore application with `mas`

```bash
curl https://raw.githubusercontent.com/khoi/dotfiles/master/darwin/mas | xargs mas lucky
```

## Restore private keys

I stored my private keys, environment variables in 1Password.

```bash
export OP_SESSION_my=$(op signin https://my.1password.com khoiracle@gmail.com --output=raw)
mkdir ~/.ssh
op get document id_rsa > ~/.ssh/id_rsa
op get document id_rsa.pub > ~/.ssh/id_rsa.pub
chmod 0600 ~/.ssh/id_rsa

op get document GPG > /tmp/1.asc
gpg --import /tmp/1.asc; rm /tmp/1.asc
```

## Miscs

- I use [gruvbox](https://github.com/morhetz/gruvbox-contrib) as the color scheme for most of my editor.

## Conclusion

Overall I'm happy with the setup above, one thing that I want to improve in the future is to relies more on Nix to setup my dotfiles. I'll update this post if I found a way to do it.

