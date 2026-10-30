# Installation Guide

This guide details how to install, configure, and maintain `vim-config` as a standalone editor setup or as part of the broader dotfiles ecosystem.

For managed Arch installation, safe updates and backup restoration, see
{doc}`packages`. The standalone setup below is a separate alternative.

---

## Requirements

`vim-config` is designed to run virtually anywhere with standard Vim packages:

- **Vim**: Version 8.2 or higher (Vim 9.0+ recommended)
- **Terminal**: Modern 24-bit TrueColor terminal (Ghostty, Kitty, Foot, Alacritty)
- **Optional (`+clipboard`)**: If system clipboard sharing (`+` / `*` registers) is desired, ensure your Vim binary is compiled with clipboard support:
  ```bash
  vim --version | grep -E '\+clipboard|\+termguicolors'
  ```
  On Debian/Ubuntu: `sudo apt install vim-gtk3`
  On Arch Linux: `sudo pacman -S gvim` (provides CLI `vim` with `+clipboard`)

---

## Standalone Installation

### Step 1: Clone the Repository

Clone `vim-config` into `~/.config/vim`:

```bash
git clone https://github.com/MichaelWeissDEV/vim-config.git ~/.config/vim
```

### Step 2: Create the Root Symlink

Vim traditionally looks for `~/.vimrc`. Create a symbolic link pointing to the cloned repository:

```bash
ln -sfn ~/.config/vim/vimrc ~/.vimrc
```

### Step 3: Prepare the State Directory

To keep your home directory and git repositories clean, persistent undo files are isolated into `~/.local/state/vim/undo`:

```bash
mkdir -p ~/.local/state/vim/undo
```

### Step 4: Launch Vim

```bash
vim
```

The editor starts instantly with no warnings or external downloads.

---

## Integration within the Arch Dotfiles Repository

Vim is distributed as the independent `arch-dotfiles-vim` package, not a parent
subtree. See {doc}`packages` for the one-command installer, `pacman -Syu`, safe
configuration updates and separate development checkouts.

---

## Directory Structure

```text
~/.config/vim/
├── README.md              # Project overview
├── vimrc                  # Main native Vimscript configuration
└── docs/                  # Sphinx documentation source
```

State and session files are placed according to the XDG Base Directory specification:

```text
~/.local/state/vim/
├── undo/                  # Persistent undo files
└── viminfo                # Jump lists, marks, and search history
```

---

## Uninstallation

For package-managed installations, run `arch-dotfiles-config deactivate vim`
before removing the package; see {doc}`packages`. For standalone installations,
review the `.vimrc` link, move the configuration aside and restore your backup.
Persistent undo/history is personal data and should not be deleted automatically.
