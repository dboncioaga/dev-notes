# MacBook Pro Setup Guide

A comprehensive guide for setting up a new MacBook Pro for development.

## Essential System Setup

#### Display & Appearance
- `System Settings > Appearance`
    - Set appearance to Auto
- Configure display scaling
- Arrange multiple displays (if applicable)

### Lock Screen
- `System Settings > Lock Screen`
  - Turn off display after 10 minutes

### Input Devices

**Trackpad Settings** (`System Settings > Trackpad > Scroll & Zoom`)
- Disable natural scroll direction (optional)
- Enable gestures
- Adjust tracking speed

**Dock Customization** (`System Settings > Desktop & Dock`)
- Adjust dock size
- Enable magnification
- Remove unused icons
- Show recent apps (turn off)
- Turn off automatically arrange spaces

### Finder

I like to customize Finder starting with adding common folders to my favorites. If you're new to macOS It's helpful to get
used to moving around and customizing Finder. 

- Right-click on the title bar and click `Customize Toolbar`.
- View > Show Path Bar
- `Finder > Settings`
  - Remove Tags (I don't use them)
  - Customize Sidebar
  - Advanced (Show filename extensions + Search Current Folder)

**Keyboard Shortcuts**
* Cmd + Shift + H (takes you home)
* Cmd + Shift+ .  (show hidden files and folders)
* Cmd + Shift + G → Go to folder (you can paste any path)
* Cmd + Shift + D → Desktop
* Cmd + Shift + O → Documents
* Cmd + [ → Go back
* Cmd + ] → Go forward
* Cmd + Up → Parent folder
* Space bar → Quick Look preview

**View Customization**
* Cmd + 1 → Icon view
* Cmd + 2 → List view
* Cmd + 3 → Column view
* Cmd + 4 → Gallery view
* Cmd + J → View options for current folder
* Right-click column header → Customize visible columns

**Power User Tips**
* Hold Option while dragging to copy instead of move
* Hold Cmd while dragging to move even across volumes
* Right-click Finder title bar to see path
* Type first few letters to jump to files
* Use Path Bar (View → Show Path Bar)
* Enable Status Bar (View → Show Status Bar) to see free space

**Favorites & Sidebar**
* Drag any folder to sidebar under Favorites
* Rearrange sidebar items by dragging
* Remove unused items to reduce clutter
* Create folder aliases (Cmd + L) for quick access
* Group frequently accessed folders together

## Development Environment

### Command Line Tools

Anything I can install using HomeBrew I will. Before you install HomeBrew though you need to install the Xcode command-line utilities. Open up a new terminal and type the following command. Even if you installed Xcode you still need to install these now as they moved them out of the standard installation. 

```bash
# Install Xcode Command Line Tools
xcode-select --install
```

The command-line Tools Package is a small self-contained package available for download separately from Xcode and that allows you to do command-line development in OS X. It consists of two components: OS X SDK and command-line tools such as Clang, which are installed in `/usr/bin`.

As I said earlier I use HomeBrew to install anything that it can install. If you normally use brew to install something like google-chrome you know that you have to then drag it into the applications folder. If you use cask it will not only download the package but also move it into the applications folder for you.

[HomeBrew Website](https://brew.sh/)

**Note** - When you install Homebrew, it automatically checks for and installs the required Xcode Command Line Tools (CLT) if they are missing - so you may skip the *previous* step.

```bash
# Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### iTerm2 Installation

I switched from Terminal to iTerm2 a long time ago and haven't looked back. If you want to find out about some of the features & configurations it gives you please [check out their website](https://www.iterm2.com/features.html).

```bash
brew install --cask iterm2
```

**Recommended Customization:**
- [Color Schemes](https://iterm2colorschemes.com/): GruvBoxDark, Nord, Snazzy
- Fonts: Monaco, MesloLGS NF, Jetbrains Mono, Hack

### Oh My Zsh Setup

If you're going to use ZSH you must start by installing [oh-my-zsh](https://ohmyz.sh/). Oh My Zsh is a popular framework for managing your Zsh configuration. Here are its main benefits:

**Core Features:**
- Theme support for prettier, more informative prompts
- Hundreds of [built-in plugins](https://github.com/ohmyzsh/ohmyzsh/wiki/plugins) for:
    - Git (better git shortcuts and status info)
    - Package managers (npm, pip, etc.)
    - Cloud platforms (AWS, Docker, etc.)
- Smart auto-completion
- Command history with search
- Directory navigation shortcuts

**Common Useful Features:**
```
# Directory Navigation
cd ..    → moves up one directory
...      → moves up two directories
....     → moves up three directories
take dir → creates and moves into directory

# Git Shortcuts (with git plugin)
gst      → git status
ga       → git add
gcm      → git commit -m
gp       → git push
gco      → git checkout

# History
history  → show command history
ctrl + r → search history interactively
```

**Popular Themes:**
- robbyrussell (default)
- agnoster (shows git status, python env)
- powerlevel10k (highly customizable, fast) - `ZSH_THEME="powerlevel10k/powerlevel10k`


**Installation**
```
# Install via curl
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Or via wget
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

**Configuration is in ~/.zshrc:**
- Change themes
- Add/remove plugins
- Set aliases
- Customize other settings

**Some Plugins to consider:**
```
plugins=(
  git
  docker
  docker-compose
  node
  npm
  nvm
  vscode
  brew
  httpie
  spring
  zsh-autosuggestions
  zsh-syntax-highlighting
)
```

**Install zsh-autosuggestions:**
```
git clone https://github.com/zsh-users/zsh-autosuggestions \
${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
**Install zsh-syntax-highlighting:**
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```



### Development Tools


```bash
# Essential development tools
brew install --cask google-chrome
brew install git
brew install --cask visual-studio-code
brew install --cask docker
brew install docker colima 
brew install tree
brew install bat
brew install --cask bruno
brew install --cask dbvisualizer
brew install --cask drawio
```

```bash
# Additional CLI tools
brew install fzf         # Fuzzy finder
brew install ripgrep     # Better grep
brew install tldr        # Simplified man pages
brew install jq          # JSON processor
brew install htop        # Process viewer
brew install ncdu        # Disk usage analyzer
```

```bash
# Cloud platform CLIs
brew install awscli
brew install azure-cli
brew install google-cloud-sdk
```
### Git Configuration

There is usually a default install of git but we used brew to install the latest earlier. Now that we are on the latest version of git we need to do a little configuration. If you run the following commands they will be written to `.gitconfig`:


```bash
git config --global user.email "your.email@example.com"
git config --global user.name "Your Name"

# Generate SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"
```

### SDKMan

This is one of my favorite version managers because I use a lot of the Software Development Kits (SDKs) it manages. If you haven't heard of [SDKMan check them out here](https://sdkman.io/install). This is a list of SDKs I manage using SDKMan.

* Java
* Kotlin
* Gradle
* Maven
* Spring Boot

```bash
curl -s "https://get.sdkman.io" | zsh
```

## Applications & Tools

This is the rest of the applications and tools that I install:

### Misc Applications

```bash
brew install --cask appcleaner

```

### Raycast

[Raycast](https://www.raycast.com/) is a powerful Spotlight replacement that enhances productivity with features like:

- Quick application launcher
- Clipboard history
- Snippets management
- Window management
- Extensions ecosystem

**Installation:**

```bash
brew install --cask raycast
```

**Essential Settings:**
- Set hotkey (default is ⌘ + Space, you might want to change Spotlight's hotkey first)
- Enable clipboard history
- Configure window management shortcuts
- Install recommended extensions:
  - Calculator
  - Calendar
  - Color Picker
  - GitHub
  - Window Management

## Cleanup & Optimization

### System Cleanup Tools

- Install AppCleaner for thorough app removal
- Consider CleanMyMac for system maintenance
- Remove unused large applications (e.g., GarageBand)
  - Remove applications using Launchpad by holding down the option key

**Garage Band:**

If you don't have a large hard drive and space is at a premium removing Garage Band will free up a bunch of it. Unfortunately, AppCleaner only works for 3rd party installed applications and won't remove GarageBand but CleanMyMac will.

If you need to remove this manually (or use Launchpad) there are a few locations you need to remove. If you're going to use apple sound affects in other programs please read up on this before deleting it.

* /Applications/GarageBand.app
* /Library/Application Support/GarageBand/
* /Library/Audio/Apple Loops/Apple/

Empty Trash

### Storage Management
- Use Storage Management tool
- Clean up Downloads folder
- Remove unnecessary languages
- Clear system caches

### Performance Optimization

**Energy Management**
- Review battery health settings
- Configure "Optimize Battery Charging"
- Set up Low Power Mode preferences
- Monitor battery cycle count

**Activity Monitor Tips**
- How to identify resource-intensive applications
- Setting up Activity Monitor Dock icon to show CPU usage
- Understanding memory pressure
- Managing startup items

## Reference

### Essential Keyboard Shortcuts
```
⌘ + Space        - Spotlight Search
⌘ + Tab          - App Switcher
⌘ + `            - Window Switcher
⌘ + Q            - Quit Application
⌘ + W            - Close Window
⌘ + Option + Esc - Force Quit
```
