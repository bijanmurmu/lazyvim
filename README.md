<div align="center">
  <h1>💤 LazyVim Starter (Windows Edition)</h1>
  <p><i>A beautifully configured, blazing fast Neovim setup optimized for Windows users.</i></p>
</div>

---

Welcome! If you've ever wanted to try Neovim but felt overwhelmed by the setup process, this repository is for you. It provides a complete, out-of-the-box experience using [LazyVim](https://www.lazyvim.org/) with all the necessary tools pre-configured for Windows.

## 📑 Table of Contents
- [Prerequisites](#️-prerequisites)
- [Installation](#-installation)
- [Your First Boot](#-your-first-boot)
- [Vim Crash Course](#-vim-crash-course-for-absolute-beginners)
- [Troubleshooting & Factory Reset](#-troubleshooting--factory-reset)
- [Cheatsheet / Keybindings](#️-cheatsheet--keybindings)

---

## 🛠️ Prerequisites

Neovim relies on a few external tools to work its magic (like searching files and compiling language parsers). We will use [Scoop](https://scoop.sh/) to install everything painlessly in PowerShell.

**1. Install Scoop** *(Skip if you already have it)*
```bash
# Open PowerShell and run:
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
irm get.scoop.sh | iex
```

**2. Add the required buckets**
```bash
scoop bucket add extras
scoop bucket add nerd-fonts
```

**3. Install Neovim and Core Tools**
```bash
scoop install neovim gcc ripgrep fd lazygit git FiraCode-NF
```
> [!NOTE]  
> **Important:** You *must* configure your terminal (e.g., Windows Terminal) to use the newly installed [`FiraCode Nerd Font`](https://github.com/ryanoasis/nerd-fonts/releases/latest/download/FiraCode.zip) as its default font, otherwise icons will show up as broken boxes!

---

## 🚀 Installation

### Option A: I am installing from scratch
1. Open **PowerShell**, clone this repository, and enter the folder:
   ```bash
   git clone https://github.com/bijanmurmu/lazyvim.git
   cd lazyvim
   ```
2. Create a "symlink" (a shortcut) so Neovim knows where to find this config:
   ```bash
   New-Item -ItemType Junction -Path "$env:LOCALAPPDATA\nvim" -Target ".\nvim"
   ```

### Option B: I already have a Neovim config
1. Open **PowerShell** and back up your old configuration:
   ```bash
   Move-Item $env:LOCALAPPDATA\nvim $env:LOCALAPPDATA\nvim.bak -ErrorAction SilentlyContinue
   Move-Item $env:LOCALAPPDATA\nvim-data $env:LOCALAPPDATA\nvim-data.bak -ErrorAction SilentlyContinue
   ```
2. Follow **Option A** above to link this new configuration.

---

> [!IMPORTANT]
> ## ⏳ Your First Boot
> When you type `nvim` in your terminal for the absolute first time, **please do not press anything!**
> 
> 1. 📦 **Lazy.nvim** will download itself.
> 2. 🔌 A popup will appear showing plugins downloading.
> 3. 🛠️ **Mason** will silently install LSP servers (autocompletion tools) in the background.
> 4. 🌳 **Treesitter** will compile code parsers.
> 
> **Wait for all loading bars and messages at the bottom of the screen to finish.** Once it settles, press `q` to close the installer window.

---

## 🎓 Vim Crash Course (For Absolute Beginners)

If you've never used Vim before, the most important thing to understand is **Modes**. You aren't always typing text!

- **Normal Mode** (Default): Used for navigating, deleting, and copying. If you press keys here, they act as commands, *not* text.
- **Insert Mode**: Used for actually typing code.

| Action | Key / Command | What to do |
| :--- | :--- | :--- |
| **Start Typing** | `i` | Press `i` to enter Insert Mode. You can now type normally. |
| **Stop Typing** | `<Esc>` | Press the Escape key to go back to Normal Mode. |
| **Save File** | `<Space> f s` | In Normal Mode, press Space, then `f`, then `s`. |
| **Quit Neovim** | `:q` | In Normal Mode, type `:q` and press Enter. |

*(Note: In LazyVim, the **Spacebar** is your "Leader" key. Most major shortcuts start by tapping Space.)*

---

## 🧹 Troubleshooting & Factory Reset

If your Neovim breaks, plugins fail to load, or you just want to factory reset everything back to a clean slate *without* losing your custom configuration:

1. Close Neovim.
2. Open **PowerShell** and delete Neovim's hidden data and cache folders:
   ```bash
   Remove-Item -Path "$env:LOCALAPPDATA\nvim-data" -Recurse -Force -ErrorAction SilentlyContinue
   Remove-Item -Path "$env:LOCALAPPDATA\state\nvim" -Recurse -Force -ErrorAction SilentlyContinue
   ```
3. Open `nvim` again. It will behave exactly like your first boot and freshly re-download all plugins and tools from scratch!

---

## ⌨️ Cheatsheet / Keybindings

<details>
<summary><strong>Click here to expand the full Keyboard Shortcuts Reference</strong></summary>

### 📁 File Operations
| Shortcut | Action |
| :--- | :--- |
| `<Space> f f` | Find a file by name |
| `<Space> s g` | Search for a word/string across all files |
| `<Space> e` | Toggle the File Explorer sidebar |
| `<Space> f r` | View recently opened files |

### 🪟 Windows & Tabs
| Shortcut | Action |
| :--- | :--- |
| `<Space> \|` | Split screen vertically |
| `<Space> -` | Split screen horizontally |
| `Ctrl` + `h/j/k/l` | Navigate between split screens |
| `<Space> w d` | Close current split screen |
| `Shift` + `l` / `h` | Go to the next/previous tab (buffer) |
| `<Space> b d` | Close the current tab |

### 💻 Coding & LSP
| Shortcut | Action |
| :--- | :--- |
| `K` | Show hover documentation for the code under cursor |
| `g d` | Go to Definition |
| `g r` | Go to References |
| `<Space> c r` | Rename a variable across the file |
| `<Space> c f` | Format the current file |

### 🔧 Tools
| Shortcut | Action |
| :--- | :--- |
| `<Space> g g` | Open LazyGit (Built-in Git UI) |
| `<Space> f t` | Open a floating Terminal |
| `<Space> l` | Open the Plugin Manager (Lazy) |

</details>

---
<div align="center">
  <i>Enjoy your blazing fast setup! ✨</i>
</div>
