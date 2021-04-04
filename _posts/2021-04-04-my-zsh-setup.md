---
layout: post
title: install zsh on linux mint/wsl2-ubuntu
tags: [ zsh, linux ]
categories: linux
---



mac 에서 사용해온 zsh 를 linux mint 에도 설치 (bash -> zsh 로 변경)



### install zsh

```
sudo apt install zsh

cat /etc/shells

chsh -s /usr/bin/zsh
```

### install oh-my-zsh

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### change theme

```
vi ~/.zshrc
ZSH_THEME="agnoster"
```

# install plugins

### install autojump

```
git clone git://github.com/wting/autojump.git && cd autojump && ./install.py
```

### install zsh-autosuggestion

```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

### install zsh-syntax-highlighting

```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

```
vi ~/.zshrc
plugins=(
git
autojump
zsh-autosuggestions
zsh-syntax-highlighting
)
```

### multiline

```
vi ~/.oh-my-zsh/themes/agnoster.zsh-theme
## Main prompt
build_prompt() {
  RETVAL=$?
  prompt_status
  prompt_virtualenv
  prompt_aws
  prompt_context
  prompt_dir
  prompt_git
  prompt_bzr
  prompt_hg
  prompt_newline
  prompt_end
}

prompt_newline() {
  if [[ -n $CURRENT_BG ]]; then
    echo -n "%{%k%F{$CURRENT_BG}%}$SEGMENT_SEPARATOR
%(?.%F{$CURRENT_BG}.%F{red})❯%f"
  else
    echo -n "%{%k%}"
  fi

  echo -n "%{%f%}"
  CURRENT_BG=''
}
```



terminal 및 editor 의 font 는 D2Coding 사용하고 있으며 zsh 의 theme 를 agnoster 로 변경해도 문제없음