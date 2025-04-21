[![Download the latest version](https://img.shields.io/badge/Download-Latest%20version-orange)](https://github.com/burianvlastimil/sudoedit-enhanced/releases/latest) &nbsp; &nbsp; &nbsp; &nbsp; [![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/burianvlastimil/sudoedit-enhanced/?tab=MIT-1-ov-file)

***

# Safe text files editing as [`root`](https://en.wikipedia.org/wiki/Superuser#Unix_and_Unix-like) (wiki) in [Linux](https://en.wikipedia.org/wiki/Linux) (wiki)

This topic might interest all [Linux](https://en.wikipedia.org/wiki/Linux) (wiki) administrators as it is them who do the changes. Be it a home user, or a corporate admin. Without a doubt, no one wants to cripple their system just because the power went down, or an [`ssh`](https://linux.die.net/man/1/ssh) (man page) session was interrupted by a bad connection, etcetera.

**What's more, by using this script I enable you to edit files comfortably even from a somewhat limited list of [GUI](https://en.wikipedia.org/wiki/Graphical_user_interface) (wiki) editors.**

***

## Demo

For a quick look, I made a short SVG demo for you, it takes less than two and a half minutes.

It was loading unbearably slow on this Readme, so if you want to see it, click [SVG demo](https://www.vlastimilburian.cz/github_images/sudoedit-enhanced--demo-2021.svg) and play it separately.

I will not update the demo if there is some little change, however, it's merely to show you an actual work.

***

## [POSIX](https://en.wikipedia.org/wiki/POSIX) (wiki) [shells](https://en.wikipedia.org/wiki/Unix_shell) (wiki) compatibility

This script enables you to edit text files on Linux as [`root`](https://en.wikipedia.org/wiki/Superuser#Unix_and_Unix-like) (wiki) safely through `sudoedit`.

Internal workings are that `sudoedit` copies the file into a temporary file, and overwrites the original file if, and only if, that file has successfuly been changed (saved) and the text editor properly exited.

It is a standard [POSIX](https://en.wikipedia.org/wiki/POSIX) (wiki) [shell script](https://en.wikipedia.org/wiki/Shell_script) (wiki), it should work in any [Linux](https://en.wikipedia.org/wiki/Linux) (wiki) distribution; more precisely, your [shell](https://en.wikipedia.org/wiki/Unix_shell) (wiki).

***

## Requirements

The only requirement is to have [`sudo`](https://linux.die.net/man/8/sudo) properly installed and configured. If you have that, then `sudoedit` is available automatically as it is directly [`sudo`](https://linux.die.net/man/8/sudo)'s _edit_ feature, it can even be invoked as `sudo -e` or `sudo --edit`.

***

## Usage instructions

### Download

Visit the [latest release download page](https://github.com/burianvlastimil/sudoedit-enhanced/releases/latest). Directly download the file named `sudoedit-enhanced` in that release. Note, that there is no need to adjust name or permissions, but you are free to do so if you wish.

### General

Once downloaded, place the script somewhere it can stay for good. Be it `~/bin` or somewhere else completely.

### Before use

You may edit the beginning of this script to customize the editor lists to your preference before actually using this script, by default there are these specified at the beginning of the script, for sure you can safely add any [CLI](https://en.wikipedia.org/wiki/Command-line_interface) editor, but [GUI](https://en.wikipedia.org/wiki/Graphical_user_interface) (wiki) editors are somewhat problematic, which is why I have only been able to add [Sublime-Text](https://www.sublimetext.com/) (home page) and [Xed](https://github.com/linuxmint/xed) (GitHub page) so far:

```bash
conf__cli_editors='vi nano'
conf__gui_editors='subl xed'
```

You don't have to explicitly remove those not present in your system, as the script checks on existence of the editors upon every call (more precisely upon every sourcing to your [shell](https://en.wikipedia.org/wiki/Unix_shell)'s (wiki) environment).

***

### Integration into your [shell](https://en.wikipedia.org/wiki/Unix_shell)'s environment

The integration will vary greatly on what shell you use. As there are many [shells](https://en.wikipedia.org/wiki/Unix_shell) (wiki) in general use, I only provide guidance for [`bash`](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) (wiki).

### [`bash`](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) (wiki)

There are multiple ways to source my script to your [`bash`](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) (wiki), of course.

My personal recommendation is to create (if not yet existing) the `~/.bash_aliases` file and source my script from there using the _dot_ (`.`) notation:

```bash
. /full/path/to/sudoedit-enhanced
```

Sourcing using the _dot_ (`.`) is a [POSIX](https://en.wikipedia.org/wiki/POSIX) (wiki) way of doing so. Although, in [`bash`](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29) (wiki), there is also the `source` builtin command, so you can use that, if you want.

Afterward, you need to make sure that these (or similar) lines are present and not commented out in your `~/.bashrc`:

```bash
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

***

### Generated editor `alias`es

On every machine, there will always be different number of `alias`es.

As said before, the script checks on existence of each editor. This is true also for `alias` generators.

These `alias`es begin with `su` + name of the editor.

To get the current list of generated editor `alias`es, just run `sudoedit_run` without any argument, example:

```bash
$ sudoedit_run
Usage example: sueditor /path/to/file1 /path/to/file2

sudoedit-enhanced defined the following editors:
suvi  sunano  susubl  suxed
```

***

## Examples of an actual use

### [CLI](https://en.wikipedia.org/wiki/Command-line_interface) (wiki) editors - screenshots (click to enlarge)

[Nano](https://www.nano-editor.org/) editor (home page) | [Vi](https://www.vim.org/) editor (home page)
:-------------------------:|:-------------------------:
![sunano /etc/default/grub](https://www.vlastimilburian.cz/github_images/sudoedit-enhanced--sunano--2021-oct-04.png) | ![suvi /etc/default/grub](https://www.vlastimilburian.cz/github_images/sudoedit-enhanced--suvi--2021-oct-04.png)

**How to get these editors:**

- The [Nano editor](https://www.nano-editor.org/) (home page) can be downloaded from [this page](https://www.nano-editor.org/download.php), but note you would have to compile the program yourself, which is what I am doing. It may be much more comfortable just to use the packaged version.

- The [Vi](https://www.vim.org/) editor (home page) can be downloaded from [this page](https://www.vim.org/download.php), I personally prefer the packaged version myself to compiling it.

***

### [GUI](https://en.wikipedia.org/wiki/Graphical_user_interface) (wiki) editors - screenshots (click to enlarge)

[Sublime-Text](https://www.sublimetext.com/) editor (home page) | [Xed Mint](https://community.linuxmint.com/software/view/xed) editor (home page)
:-------------------------:|:-------------------------:
![susubl /etc/default/grub](https://www.vlastimilburian.cz/github_images/sudoedit-enhanced--susubl--2021-sep-29.png) | ![suxed /etc/default/grub](https://www.vlastimilburian.cz/github_images/sudoedit-enhanced--suxed--2021-sep-29.png)

**How to get these editors:**

- The [Sublime-Text](https://www.sublimetext.com/) editor (home page) can be downloaded from [its home page/download](https://www.sublimetext.com/download);

- The [Xed Mint](https://community.linuxmint.com/software/view/xed) editor is pre-installed in [Linux Mint](https://linuxmint.com/) (home page) and on some other Ubuntu-based [distributions](https://en.wikipedia.org/wiki/Linux_distribution) (wiki) can be installed via [PPA](https://en.wikipedia.org/wiki/Ubuntu#Package_Archives) (wiki): [`ppa:savoury1/xapps`](https://launchpad.net/~savoury1/+archive/ubuntu/xapps) (Launchpad link).

***

## Reporting bugs and suggestions

Please open a [new issue ticket](https://github.com/burianvlastimil/sudoedit-enhanced/issues/new) (direct link).
