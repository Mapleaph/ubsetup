# Linux Setup

## Essentials

``` bash
# ubuntu
$ sudo apt-get install git vim tmux build-essential libncurses-dev libgl1-mesa-dev openssh-server
## grub-customizer
$ sudo add-apt-repository ppa:danielrichter2007/grub-customizer
$ sudo apt-get update
$ sudo apt-get install grub-customizer
## variety wallpaper
$ sudo add-apt-repository ppa:peterlevi/ppa
$ sudo apt-get update
$ sudo apt-get install variety

# fedora
$ sudo yum install git vim tmux rpm-build ncurses-devel mesa-libGL-devel openssh-server redhat-rpm-config
```

### vim

``` bash
$ git clone https://github.com/mapleaph/vim ~/.vim
$ ln -s ~/.vim/vimrc ~/.vimrc
$ cd ~/.vim
$ git submodule update --init --recursive
```

### tmux

```bash
$ git clone https://github.com/mapleaph/tmux
$ cp tmux/tmux.conf ~/.tmux.conf
$ rm -rf ./tmux/
```

### other packages

```bash
# ubuntu
$ sudo apt-get install tig progress screenfetch
# fedora
$ sudo yum install tig progress screenfetch
```

## zsh

### oh-my-zsh

``` bash
# ubuntu
$ sudo apt-get install zsh
# fedora
$ sudo yum install zsh util-linux-user

$ sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
$ exit
$ chsh -s $(which zsh)
```

### zsh-syntax-highlighting plugin

``` bash
# ubuntu
$ sudo apt-get install zsh-syntax-highlighting
# fedora
$ sudo yum install zsh-syntax-highlighting

$ echo "source /usr/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc
```

### powerline-status

#### pip

``` bash
# ubuntu
$ sudo apt-get install python-pip python-dev
# fedora
$ sudo yum install python-pip python-devel python3-devel

$ pip install --upgrade pip
$ echo "export PATH=\"\$HOME/.local/bin/:\$PATH\"" >> ~/.zshrc
```

#### powerline-status

``` bash
$ pip install --user powerline-status
```

#### powerline-fonts

``` bash
$ git clone https://github.com/powerline/fonts.git --depth=1
$ cd fonts/
$ ./install.sh
$ cd ../
$ rm -rf ./fonts

$ sed -i "s/robbyrussell/agnoster/g" ~/.zshrc
```

#### other packages

```bash
$ pip install --user howdoi magic-wormhole ici ydcv
```

#### Terminal/Terminator

Go to preferences, select **Source Code Pro for powerline Regular**.

## Spacemacs

### Install emacs (Requires emacs > 24.4)

``` bash
# ubuntu
$ sudo apt-get install emacs
# fedora
$ sudo yum install emacs

$ git clone https://github.com/syl20bnr/spacemacs~/.emacs.d
```

### Edit .spacemacs to change repository url

``` bash
(defun dotspacemacs/user-init ()
	(setq-default
		configuration-layer-elpa-archives
		(("melpa-cn" . "https://mirrors.tuna.tsinghua.edu.cn/elpa/melpa/")
		("gnu-cn" . "https://mirrors.tuna.tsinghua.edu.cn/elpa/gnu/")
		("org-cn" . "https://mirrors.tuna.tsinghua.edu.cn/elpa/org/")))
)
```

### No such file or directory bind-map error

Edit .spacemacs file, try to change "dotspacemacs-elpa-timeout 5" to "30", then invoke emacs like this once.

``` bash
$ emacs --insecure
```

### Change font

Change "Source Code Pro" to "Source Code Pro for powerline" in ~/.spacemacs.

## pyenv

``` bash
# ubuntu
$ sudo apt-get install curl
# fedora
$ sudo yum install curl

$ curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash
$ echo "export PATH=\"\$HOME/.pyenv/bin/:\$PATH\"" >> ~/.zshrc
$ echo "eval \"\$(pyenv init -)\"" >> ~/.zshrc
$ echo "eval \"\$(pyenv virtualenv-init -)\"" >> ~/.zshrc
```

Before install python3, openssl, bzip2, readline, sqlite3 libraries should be installed:

``` bash
# ubuntu
$ sudo apt-get install libssl-dev libbz2-dev libreadline-dev libsqlite3-dev
# fedora
$ sudo yum install openssl-devel bzip2-devel readline-devel sqlite-devel
```

## nodejs

### npm

```bash
# ubuntu
$ sudo apt-get install npm
# fedora
$ sudo yum install npm
```

### packages

```bash
$ sudo npm install -g vtop rg
```

## Ubuntu Gnome Software Center

Use gnome software center to install applications like pycharm-community and vscode will cause "snapd status code 400" error.

Use snap command to install these applications with classic option.

``` bash
$ sudo snap install vscode --classic
```

## Terminal Color Theme

``` bash
# ubuntu
$ sudo apt-get install dconf-cli

$ wget -O gogh https://git.io/vQgMr &&chmod +x gogh && ./gogh && rm gogh
```

