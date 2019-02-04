# macOS Mojave v. 10.14 Setup 

[View a more detailed explanation of these steps here.](https://www.taniarascia.com/setting-up-a-brand-new-mac-for-development/) 

This is a simple list of instructions to make setting up your Apple computer as fast and efficient as possible for web development.

## Preferences

- **Keyboard > Text >** Disable "Correct spelling automatically".
- **Security and Privacy > Firewall >** On
- **Security and Privacy > General >** App Store and identified developers
- **File Sharing >** Off
- **Users & Groups > Login Items >** Spectacle, Flux

### Show Library folder

```shell
chflags nohidden ~/Library
```

### Show hidden files

This can also be done by pressing `command` + `shift` + `.`.

```shell
defaults write com.apple.finder AppleShowAllFiles YES
```

### Show path bar

```shell
defaults write com.apple.finder ShowPathbar -bool true
```

### Show status bar

```shell
defaults write com.apple.finder ShowStatusBar -bool true
```

### Disable unidentified developer warnings

```shell
sudo spctl --master-disable
```

## Homebrew

```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Mac App Store

```shell
brew install mas
```

### Homebrew formulae

```shell
brew install $(cat packages.txt)
```

#### Sign in

```shell
mas signin email@email.com
```

### Brewfile

```shell
touch Brewfile
```

```shell
tap 'caskroom/cask'

brew 'git'
brew 'npm'

cask 'firefox'
cask 'google-chrome'
cask 'vlc'
cask 'macdown'
cask 'sublime-text'
cask 'atom'
cask 'cloud-app'
cask 'dropbox'
cask 'github-desktop'
cask 'tunnelbear'
cask 'rocket'
cask 'loopback'
cask '1password'
cask 'adobe-creative-cloud'
cask 'meta'
cask 'mjml'
cask 'skype'
cask 'spotify'
cask 'zoom'
cask 'chrome-remote-desktop-host'
cask 'mpeg-streamclip'

mas 'Slack', id: 803453959
mas 'Transmit 5', id: 1436522307
mas 'Wunderlist', id: 410628904
mas 'evernote', id: 406056744

```

## GitHub

### Config - `~/.gitconfig`


```shell
[user]
  name   = Firstname Lastname
  email  = you@example.com
[github]
  user   = hunter2
[alias]
  a      = add
  ca     = commit -a
  cam    = commit -am
  cm     = commit -m
  s      = status
  pom    = push origin master
  pog    = push origin gh-pages
  puom   = pull origin master
  puog   = pull origin gh-pages
  cob    = checkout -b
  co     = checkout
  l      = log --oneline --decorate --graph
  lall   = log --oneline --decorate --graph --all
  ls     = log --oneline --decorate --graph --stat
  lt     = log --graph --decorate --pretty=format:'%C(yellow)%h%Creset%C(auto)%d%Creset %s %Cgreen(%cr) %C(bold blue)%an%Creset'
[credential]
  helper = osxkeychain
```


## SSH

### Config - `~./ssh/config`

```shell
Host example
    HostName example.com
    User example-user
    IdentityFile key.pem
```

### Generate SSH key

```shell
ssh-keygen -t rsa -b 4096 -C "you@example.com"
eval "$(ssh-agent -s)"
ssh-add -K ~/.ssh/id_rsa
```

## Bash

### Config - `~/.bash_profile`

```shell
# Update and clean homebrow in one command
alias brewup='brew update; brew upgrade; brew prune; brew cleanup; brew doctor'

# Add colors to Terminal
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad

# Get Git branch
parse_git_branch() {
  git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

# Format to user@host:/path/to/directory (branch-name)
export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\$(parse_git_branch)\[\033[m\]\$ "
```

## Node.js

### Download Node

```shell
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.1/install.sh | bash
```

```shell
nvm install node
```

```shell
nvm use node
```

#### Update Node.js

```shell
nvm install node --reinstall-packages-from=node
```

## npm

### Gulp

```shell
npm install --global gulp-cli
npm install -g ember-cli
```

## Ruby Version Manager

### Download rvm

```shell
\curl -sSL https://get.rvm.io | bash -s stable
```

### Install Ruby version

```shell
rvm install ruby-head
```

```shell
rvm --default use 2.4.0
```

```shell
gem install bundler
```

## Install Composer

```shell
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
```


## Other Apps

Wordle


