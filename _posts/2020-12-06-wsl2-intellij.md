---
layout: post
title: install intellij on wsl2
tags: [ intellij, wsl2 ]
categories: java
---



linux 환경에서 개발시 linux mint(ubuntu) 와 macos 는 많은 장점을 가지고 있으며 현재 나의 개발 환경의 main os 는 linux 이며 desktop 및 laptop 에 linux mint 를 설치하여 사용하고 있다. vim 과 vscode 로 c++ 코드 작성하고 intellij 로 java 코드를 작성하고 있다.  python 코드는 vim, vscode, pycharm 을 쓰고 있다.



windows 의 wsl2 를 사용하여 linux 환경에서 개발을 할 수 있으며 나 역시 docker 를 기반으로 개발 환경을 구성하여 사용하고 있다. development tool 의 성능 및 build 속도가 너무 느리다.



아래 링크는 wsl2 에 intellij 를 설치하여 benchmark 를 하였으며 build 속도를 비교하고 있다.

[Development under Windows under Linux with WSL2 (IntelliJ)](https://medium.com/@ragin/development-under-windows-under-linux-with-wsl2-intellij-860daf601b61)



## VcXsrv

> [download](https://sourceforge.net/projects/vcxsrv/files/latest/download)
>
> XLaunch 초기 실행시 Extra Settings 에서 Disable access control 체크
>
> Save configuration (windowskey+r, shell:startup 에 config.xlaunch 저장)

## Font - D2Coding

> wget https://github.com/naver/d2codingfont/raw/master/D2Coding-Ver1.3.2-20180524.zip
>
> unzip D2Coding-Ver1.3.2-20180524.zip
>
> sudo cp D2Coding/D2Coding-Ver1.3.2-20180524.ttf /usr/local/share/fonts

## openjdk8

> sudo apt install openjdk-8-jdk
> sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java 1
> sudo update-alternatives --config java

## Hangul input

> sudo apt install fcitx fcitx-hangul fonts-noto-cjk dbus-x11
>
> im-config
>
> fcitx 선택
>
> suo vi /etc/profile.d/fcitx.sh
>
> ```
>#!/bin/bash
> export QT_IM_MODULE=fcitx
> export GTK_IM_MODULE=fcitx
> export XMODIFIERS=@im=fcitx
> export DefaultIMModule=fcitx
> 
> fcitx-autostart >/dev/null 2>&1
> ```
> 
> fcitx-config-gtk3
>
> Keyboard - Korean 삭제 및 Hangul 추가, Global Config 에 한/영 키 추가

## Intellij

> wget https://download.jetbrains.com/toolbox/jetbrains-toolbox-1.18.7609.tar.gz?_ga=2.124379146.1025243524.1607222342-1452864861.1587042752
>
> tar xzvf jetbrains-toolbox-*.tar.gz
>
> ./jetbrains-toolbox
>
> vi ~/toolbox
>
> ```
> #!/bin/bash
> 
> ~/.local/share/JetBrains/Toolbox/bin/jetbrains-toolbox
> ```
>
> chmod ~/toolbox