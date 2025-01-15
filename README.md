# setting
My desktop setting (Ubuntu, >= 20.04)

### 1. zsh

```
sudo apt install zsh
chsh -s $(which zsh)
exit
```

install antigen

```
curl -L git.io/antigen > .antigen.zsh
source .antigen.zsh
```

```
# .zshrc (remain only these lines)
source $HOME/.antigen.zsh

antigen use oh-my-zsh


# Bundles from the default repo (robbyrussell's oh-my-zsh).
antigen bundle git
antigen bundle heroku
antigen bundle pip
antigen bundle lein
antigen bundle command-not-found

# Syntax highlighting bundle.
antigen bundle zsh-users/zsh-syntax-highlighting
antigen bundle zsh-users/zsh-completions
antigen bundle zsh-users/zsh-autosuggestions

# Load the theme.
antigen theme robbyrussell

# Prevent overriding title for the Windows Terminal
DISABLE_AUTO_TITLE="true"

antigen apply

# Set title for the Windows Terminal
precmd() {
    echo -ne "\033]0;$(hostname)\007"
}

```
   
### 2. tmux

tmux plugin manager

Clone TPM
```
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

```
# type this in terminal if tmux is already running
tmux source ~/.tmux.conf
```

```
# .tmux.conf

# List of plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'

# tmux-resurrect
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'ashb/tmux-resurrect-virtualenvwrapper'
set -g @resurrect-strategy-zsh 'zsh -c "source ~/.zshrc && tmux-resurrect-zsh restore"'
set -g @resurrect-processes 'nvtop'

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'
```

Install by <C-b> + I [Tmux Plugin Manager](https://github.com/tmux-plugins/tpm)

### 3. host

```
sudo hostnamectl set-hostname newhostname
sudo vim /etc/hosts # change 127.0.1.1
```

get /etc/hosts from other desktop so that aliasing could work
