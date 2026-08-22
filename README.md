
# Customization Instructions

#### *This file is the basics for a comfortable Linux customization suitable for any distribution*


### Install and change to default shell ---> zsh

```
sudo apt install zsh -y
chsh -s $(which zsh)
```

### Oh My Zsh installation

`sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

### Nerd Fonts

For compatibility reasons, stick to FiraMono Nerd font family

<https://www.nerdfonts.com/>

### Install powerlevel10k

`git clone --depth=1 https://github.com/romkatv/powerlevel10k.git "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"`

Open your .zshrc file, find the line where `ZSH_THEME` resides and change its value to `powerlevel10k/powerlevel10k`

### Install syntax-highlighting and autosuggestions for zsh

```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

Add the plugins to your .zshrc file

`nano ~/.zshrc`

Change this `plugins=(git history zsh-autosuggestions zsh-syntax-highlighting)`

### Install Neovim (Latest version)

<https://github.com/neovim/neovim/blob/master/INSTALL.md>
<https://github.com/neovim/neovim/releases>

Once installed...

```
cd ~/Downloads
chmod u+x nvim-linux-x86_64.appimage
sudo mkdir /opt/nvim
sudo mv nvim-linux-x86_64.appimage /opt/nvim/nvim
```

Export to PATH in .zshrc

```
nano ~/.zshrc
export PATH="$PATH:/opt/nvim"
source ~/.zshrc
```

### Install TPM

`git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm`

Once installed, copy the `.tmux.conf` file found in this same repository

### Install additinal tools

#### Btop

<https://github.com/aristocratos/btop>

Changing default theme

`nvim ~/.config/btop/btop.conf`

Change `color_theme`'s value to your choice

#### FZF

```
sudo apt install fzf -y
~/.fzf/install
```

Add this line to the ~/.zshrc file

`alias ff="fzf --style full --preview 'fzf-preview.sh {}' --bind 'focus:transform-header:file --brief {}'"`

#### EZA

```
sudo apt install eza -y
nvim ~/.zshrc
```

Copy the following configuration

```
alias ls='eza $eza_params'
alias l='eza --git-ignore $eza_params'
alias ll='eza --all --header --long $eza_params'
alias llm='eza --all --header --long --sort=modified $eza_params'
alias la='eza -lbhHigUmuSa'
alias lx='eza -lbhHigUmuSa@'
alias lt='eza --tree $eza_params'
alias tree='eza --tree $eza_params'
```

Finally, source the file
`source $HOME/.zshrc`
