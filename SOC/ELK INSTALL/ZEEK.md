https://www.youtube.com/watch?v=DBZWGOfJIqM + ChatGPT help
Not the must fun part of the install because I had issues with the make command but I figure it out and here we go:


## 1. Download zip file:

https://zeek.org/get-zeek/


## 2. Ensure All Dependencies Are Installed:

sudo apt-get install cmake make gcc g++ flex bison libpcap-dev libssl-dev python3 python3-dev zlib1g-dev


## 3. Unzip:

cd /home/kali/Download/

tar -xzf zee-7.0.0.tar.gz

cd zeek-7.0.0


## 4. Downloading the source code as a Git repository to ensure all necessary components are included:

git clone https://github.com/zeek/zeek.git

cd zeek

git checkout v7.0.0  # Checkout the specific version you need

git submodule update --init --recursive

sudo apt update

sudo apt install swig

## 5. Proceed with the build:

mkdir -p build

cd build

cmake ..

make ##take time

sudo make install


## 6. Export home directory to the bash file

cd /usr/local/zeek/bin

nano ~/.bashrc 

##mine was not correct so here is the entire script for it##:
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
#[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability
force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
        color_prompt=yes
    else
        color_prompt=
    fi
fi

# The following block is surrounded by two delimiters.
# These delimiters must not be modified. Thanks.
# START KALI CONFIG VARIABLES
PROMPT_ALTERNATIVE=twoline
NEWLINE_BEFORE_PROMPT=yes
# STOP KALI CONFIG VARIABLES

if [ "$color_prompt" = yes ]; then
    # override default virtualenv indicator in prompt
    VIRTUAL_ENV_DISABLE_PROMPT=1

    prompt_color='\[\033[;32m\]'
    info_color='\[\033[1;34m\]'
    prompt_symbol=㉿
    if [ "$EUID" -eq 0 ]; then # Change prompt colors for root user
        prompt_color='\[\033[;94m\]'
        info_color='\[\033[1;31m\]'
        # Skull emoji for root terminal
        #prompt_symbol=💀
    fi
    case "$PROMPT_ALTERNATIVE" in
        twoline)
            PS1=$prompt_color'┌──${debian_chroot:+($debian_chroot)──}${VIRTUAL_ENV:+(\[\033[0;1m\]$(basename $VIRTUAL_ENV)'$prompt_color')}(\u'$prompt_symbol'\h)-[\[\033[0;1m\]\w\[\033[;94m\]]\n└─\[\033[1;31m\]$ \[\033[0m\]'
            ;;
        oneline)
            PS1='${VIRTUAL_ENV:+($(basename $VIRTUAL_ENV)) }${debian_chroot:+($debian_chroot)}'$info_color'\u@\h\[\033[00m\]:\w\$ '
            ;;
        backtrack)
            PS1='${VIRTUAL_ENV:+($(basename $VIRTUAL_ENV)) }${debian_chroot:+($debian_chroot)}\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
            ;;
    esac
    unset prompt_color
    unset info_color
    unset prompt_symbol
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
    xterm*|rxvt*|Eterm|aterm|kterm|gnome*|alacritty)
        PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
        ;;
    *)
        ;;
esac

# Add a newline before the prompt if configured
[ "$NEWLINE_BEFORE_PROMPT" = yes ] && PROMPT_COMMAND="echo"

# enable color support of ls, less, and man, and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    alias dir='dir --color=auto'
    alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# colored GCC warnings and errors
export GCC_COLORS='error=01;31:warning=01;33:note=01;36:caret=01;32:locus=01:01;35:quote=01'

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Alias definitions.
# You may want to put all your additions into a separate file like ~/.bash_aliases,
# instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi


##add at the end:## export PATH=/usr/local/zeek/bin:$PATH

source ~/.bashrc



## 7. Change node file
 cd /usr/local/zeek/etc

 nano node.cfg

 ##change:## interface=eth0


## 8. Check zeek

zeekctl check

## 9. Deploy zeek

zeekctl deploy

## 10. Check zeek status

zeekctl status

<img width="643" alt="Capture d’écran 2024-08-22 à 10 32 26" src="https://github.com/user-attachments/assets/d67bddde-4c61-4c00-a6b7-b6b3275dc580">

## 11. Check the logs to see if it works:

cd /usr/local/zeek/logs/current

##Go to browser##

tail -f conn.log
##normaly you should see logs comming in##


## 12. Add zeek to ELK and kibana

sudo nano /usr/local/zeek/share/zeek/site/local.zeek
