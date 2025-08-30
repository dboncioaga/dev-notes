## **Local setup MacBook** 

### Install Homebrew

**Homebrew** is the macOS package manager that simplifies the installation of software.

1. Open the **Terminal** and run the following:
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
1. Add Homebrew to your path (you may need to add this to your shell configuration file):

   ```bash
   echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zshrc
   eval "$(/opt/homebrew/bin/brew shellenv)"
   ```
3. Verify installation:

   ```bash
   brew --version
   ```

### Install iTerm2
iTerm2 is a feature-rich terminal replacement for macOS.

Install iTerm2 via Homebrew:
   ```bash
   brew install --cask iterm2
   ```

### Set Up Oh-My-Zsh
Oh-My-Zsh enhances the default zsh shell with themes and plugins.

1. Install Zsh (if not already installed):
   ```bash
   brew install zsh
   ```

2. Install Oh-My-Zsh:
   ```bash
   sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
   ```

3. Customize your shell:

   Open ~/.zshrc and set a custom theme like robbyrussell or agnoster:
   ```bash
   ZSH_THEME="agnoster"
   ```
   Enable useful plugins (e.g., git, java, maven, etc.):
   ```bash
   plugins=(git java maven gradle brew zsh-autosuggestions)
   ```
4. Install zsh-autosuggestions and zsh-syntax-highlighting for enhanced shell experience:
   ```bash
   brew install zsh-autosuggestions zsh-syntax-highlighting
   ```

   Add the following lines to your ~/.zshrc at the bottom:
   ```bash
   source $(brew --prefix)/share/zsh-autosuggestions/zsh-autosuggestions.zsh
   source $(brew --prefix)/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
   ```

6. Restart the terminal:
   ```bash
   source ~/.zshrc
   ```

### Install Java (Temurin JDK)
Temurin is an OpenJDK distribution by the Eclipse Adoptium project.

1. Install the latest Temurin JDK via Homebrew:
   ```bash
   brew install --cask temurin
   ```
2. Verify installation:
   ```bash
   java --version
   ```
3. (Optional) Use SDKMAN for managing multiple JDK versions:
   ```bash
   curl -s "https://get.sdkman.io" | bash
   source ~/.sdkman/bin/sdkman-init.sh
   sdk install java <version>
   ```

### Install IntelliJ IDEA
IntelliJ IDEA is the most popular Java IDE.

Install IntelliJ IDEA Community Edition via Homebrew:
```bash
brew install --cask intellij-idea-ce
```

## Other Essential Tools
### Bruno
Bruno is an open-source API client.

Install Bruno via brew:
```bash
brew install --cask bruno
```

### Colima
Colima provides a lightweight alternative to Docker Desktop for running containerized applications.

Install Colima via Homebrew:
```bash
brew install colima
```

### jq (JSON parser for the command line):
```bash
brew install jq
```
### htop (System process viewer):
```bash
brew install htop
```

tree (Directory structure visualization):
```bash
brew install tree
```
