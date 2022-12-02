# Terminal preparation on MacOS

Installation iTerm2, Oh-My-ZSH, OpenJDK, Go, Groovy

## Install Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Install iTerm2

```bash
brew install --cask iterm2
```

## Install Oh-My-ZSH

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### The Oh-My-ZSH theme

![Powerlevel10k](https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/extravagant-style.png)

```bash
brew install romkatv/powerlevel10k/powerlevel10k
echo "source $(brew --prefix)/opt/powerlevel10k/powerlevel10k.zsh-theme" >> ~/.zshrc
```

### Oh-My-ZSH plugins

```bash
brew install zsh-syntax-highlighting
echo "source $(brew --prefix)/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc
brew install zsh-autosuggestions
echo "source $(brew --prefix)/share/zsh-autosuggestions/zsh-autosuggestions.zsh" >> ~/.zshrc
brew install fzf
brew install grc
echo "alias tail=\"grc tail\"" >> ~/.zshrc
```

### Enable a plugin by adding its name to the plugins array in your .zshrc file

```bash
vi ~/.zshrc

# plugins=(git fzf colored-man-pages colorize pip python brew osx)
```

### Oh-My-ZSH configure theme

```shell
p10k configure
```

### Font settings

- iTerm2: Type p10k configure and answer Yes when asked whether to install Meslo Nerd Font. Alternatively, open iTerm2 → Preferences → Profiles → Text and set Font to MesloLGS NF.
- Apple Terminal: Open Terminal → Preferences → Profiles → Text, click Change under Font and select MesloLGS NF family.
- Visual Studio Code: Open File → Preferences → Settings (PC) or Code → Preferences → Settings (Mac), enter terminal.integrated.fontFamily in the search box at the top of Settings tab and set the value below to MesloLGS NF. Consult this screenshot to see how it should look like or see this issue for extra information.
- IntelliJ (and other IDEs by Jet Brains): Open IDE → Edit → Preferences → Editor → Color Scheme → Console Font. Select Use console font instead of the default and set the font name to MesloLGS NF.

## OpenJDK

### Install OpenJDK 11 (Eclipse Adoptium) - Preferred

```bash
brew tap homebrew/cask-versions
brew install --cask temurin11
echo "export JAVA_HOME=\"/Library/Java/JavaVirtualMachines/temurin-11.jdk/Contents/Home\"" >> ~/.zshrc
echo "export PATH=\"\$JAVA_HOME/bin:\$PATH\"" >> ~/.zshrc
```

### ⚠️ AdoptOpenJDK 11 - Deprecated

```bash
brew tap AdoptOpenJDK/openjdk
brew install --cask adoptopenjdk11
sudo ln -sfn /usr/local/opt/openjdk@11/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-11.jdk
echo "export JAVA_HOME=\"/Library/Java/JavaVirtualMachines/adoptopenjdk-11.jdk/Contents/Home\"" >> ~/.zshrc
echo "export PATH=\"\$JAVA_HOME/bin:\$PATH\"" >> ~/.zshrc
```

### Install OpenJDK 11

```bash
brew install openjdk@11
sudo ln -sfn /usr/local/opt/openjdk@11/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-11.jdk
echo "export JAVA_HOME=\"/usr/local/Cellar/openjdk@11/11.0.17/libexec/openjdk.jdk/Contents/Home\"" >> ~/.zshrc
echo "export PATH=\"\$JAVA_HOME/bin:\$PATH\"" >> ~/.zshrc
```

## Install Go

```bash
brew install go
echo "export GOPATH=\"$(go env GOPATH)/bin\"" >> ~/.zshrc
echo "export PATH=\"\$GOPATH/bin:\$PATH\"" >> ~/.zshrc
```

## Install Groovy 2.4 (for Jenkins Shared Libraries)

```bash
curl -fsSL https://groovy.jfrog.io/artifactory/dist-release-local/groovy-zips/apache-groovy-binary-2.4.21.zip | \
    tar -xf - -C ~/
echo "export GROOVY_HOME=\"$HOME/groovy-2.4.21\"" >> ~/.zshrc
echo "export PATH=\"\$GROOVY_HOME/bin:\$PATH\"" >> ~/.zshrc
chmod +x $GROOVY_HOME/bin/groovy
```
