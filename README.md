# My MacBook Pro setup

## Inspiration

- [macOS Setup Guide](http://sourabhbajaj.com/mac-setup/index.html)
- [clakech/macbook-pro-setup](https://github.com/clakech/macbook-pro-setup)


## Install Xcode, *on macOS, you can't dev without Xcode*

```bash
 xcode-select --install
```

## Install [HomeBrew](http://brew.sh/), *a tool to install CLI tools without copy/paste*

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Install tools for devs, *a short must have list*

```bash
#what else?
brew install git

#customizable terminal
brew install --cask iterm2

#2FA
brew install --cask authy

#IDE for web dev
brew install --cask visual-studio-code

#replace spotlight with alfred
brew install --cask alfred

#manage windows with keyboard shortcuts
brew install --cask rectangle
```

## Install ZSH & co, *the best shell suite for devs [#mustHave](https://github.com/robbyrussell/oh-my-zsh/wiki/Cheatsheet)*

```bash
brew install zsh zsh-completions

#install oh-my-zsh, a zsh configuration helper
$ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

#install auto suggestions plugin
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions

```

## Configure your ZSH on steroids, *add these lines to your ~/.zshrc*

```bash
plugins=(git colored-man colorize github jira vagrant virtualenv pip python brew osx zsh-syntax-highlighting zsh-autosuggestions)

ZSH_THEME="agnoster"
DEFAULT_USER="yourusername"
```

## Configure shell to use zsh, *type this line in your iTerm2 shell*

```bash
chsh -s /bin/zsh
```

### Restart iTerm2

## Configure iTerm2

Install font Meslo LG M Regular for Powerline
 
```zsh
git clone https://github.com/powerline/fonts.git ~/tempFonts

~/tempFonts/install.sh
```
  
Go to ~/Library/Fonts and install font Meslo LG M Regular for Powerline

Go to iTerm2 / Preferences / Profiles / Text / Change Font / Meslo LG M Regular for Powerline.

Make sure the option `Use a different font for non-ASCII character` is **not** checked.

Go to iTerm2 / Preferences / Profiles / Colors / Colors presets / Solarized Dark

Go to iTerm2 / Preferences / Profiles / Windows / Transparency + Blur

Delete downloaded font files

```zsh
rm -Rf ~/tempFonts
```

## Tada 🎉

![](iTerm2zsh.png?raw=true)

## Configure your editor, *add these lines to your ~/.zshrc*

```zsh
export EDITOR="atom -w"
alias edit="atom -nw"
```

## Configure git

```zsh
git config --global user.name "Your Name Here"
git config --global user.email "your_email@youremail.com"

git config --global credential.helper osxkeychain

git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
#see all default oh-my-zsh git aliases https://github.com/robbyrussell/oh-my-zsh/wiki/Cheatsheet#git
```

## Install NodeJS

### Install [NVM](https://github.com/creationix/nvm), *to manage multiple NodeJS versions*

```zsh
brew install nvm
```
 
### Restart iTerm2, *or `touch ~/.zshrc`*

### Install NodeJS LTS, *latest long term supported version*
 
```zsh
nvm install --lts
```

## Configure Docker *using HyperKit (xhyve)*

```zsh
brew cask install docker

docker run hello-world
```

**or**

## Configure Docker *using virtualbox*

```zsh
brew cask install virtualbox

brew install docker docker-machine docker-compose

docker-machine create -d virtualbox default

eval "$(docker-machine env default)"

docker run hello-world
```

## Manage your dotFiles using git, *[because you may want to review history one day](http://dotfiles.github.io/)*

```zsh
#goto your home dir, using zsh no need to cd ~ 
cd

#create a git repo ignoring all files to avoid sharing sensistive stuff
git init
echo "*" > .gitignore

#git force add file you WANT to manage
ga -f .zshrc
...

#git commit all added files, gca = git commit -v -a thanks to oh-my-zsh
gca

#optional but recommanded, if you setup a git remote to backup your files using github for instance
git push origin master
```

## update (most of) your dev tools, *in (almost) 1 line*

```zsh
brew update && brew upgrade
```

## have fun 

```zsh
sudo gem install lolcat

brew install cowsay ponysay fortune

#add a combinaison of nawak at the end of .zshrc or .zlogin
fortune | ponysay
#or
fortune | cowsay | lolcat
```


Please contribute to improve this and share it to the world if you like it 😉

## Install other things

```zsh
# Watch videos
brew install --cask vlc

# Java
brew install java

# Mindmap
brew install --cask freeplane
xattr -rc /Applications/Freeplane.app/
```

## VS Code configuration

### Install command line

From [Visual Studio Code on macOS](https://code.visualstudio.com/docs/setup/mac):

- Launch VS Code
- Open the command palette (`⇧⌘P`) and type 'shell command' to find the Shell Command: Install 'code' command in PATH command.
- Restart the terminal for the new `$PATH` value to take effect. You'll be able to type 'code .' in any folder to start editing files in that folder.

### Extensions for VS Code

To get the list of extension as "install commands", run:
```zsh
code --list-extensions | xargs -L 1 echo code --install-extension
```

Here's for mine:
```zsh
code --install-extension alexkrechik.cucumberautocomplete
code --install-extension ardenivanov.svelte-intellisense
code --install-extension bpruitt-goddard.mermaid-markdown-syntax-highlighting
code --install-extension CoenraadS.bracket-pair-colorizer
code --install-extension DavidAnson.vscode-markdownlint
code --install-extension dbaeumer.vscode-eslint
code --install-extension donjayamanne.githistory
code --install-extension DotJoshJohnson.xml
code --install-extension EditorConfig.EditorConfig
code --install-extension eg2.vscode-npm-script
code --install-extension esbenp.prettier-vscode
code --install-extension GitHub.vscode-pull-request-github
code --install-extension mitchdenny.ecdc
code --install-extension ms-azuretools.vscode-docker
code --install-extension ms-dotnettools.csharp
code --install-extension ms-mssql.mssql
code --install-extension ms-python.python
code --install-extension ms-toolsai.jupyter
code --install-extension ms-vscode.powershell
code --install-extension RandomFractalsInc.geo-data-viewer
code --install-extension redhat.vscode-yaml
code --install-extension slevesque.vscode-hexdump
code --install-extension SonarSource.sonarlint-vscode
code --install-extension svelte.svelte-vscode
code --install-extension syler.sass-indented
code --install-extension vstirbu.vscode-mermaid-preview
code --install-extension waderyan.gitblame
code --install-extension whatwedo.twig
```
