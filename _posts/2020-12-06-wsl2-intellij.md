---
layout: post
title: install intellij on wsl2
tags: [ intellij, wsl2 ]
categories: java
---



Linux 환경에서 개발자의 Desktop/Laptop 의 OS 는 Linux Mint 와 macOS 를 선호한다.



Linux 개발환경에서 Desktop/Laptop 의 OS 는 Linux Mint 와 macOS 를 선호하는 편이다.

vim 과 vscode 로 c++ / intellij 로 java / vscode 와 pycharm 으로 python 코드를 작성하는 편이며 동일 장비 기준으로 Windows, Linux Mint, macOS 에서 Development Tool 과 Build 의 성능 편차가 큰 편이다. 

리눅스 커널 기반에서 실행되는 Docker 는 Windows 와 macOS 에서는 당연히 native 로 실행되지 않으며 이와 같은 이유로 본인은 Linux Mint(Ubuntu) 를 선호 하는 편이다

아래 링크 참고

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
> sudo vi /etc/profile.d/fcitx.sh
>
> ```
> #!/bin/bash
> export QT_IM_MODULE=fcitx
> export GTK_IM_MODULE=fcitx
> export XMODIFIERS=@im=fcitx
> export DefaultIMModule=fcitx
> 
> #사용자가에게 적용이 되지 않아 각 계정의 .bashrc 에서 실행
> #fcitx-autostart >/dev/null 2>&1
> ```
>
> vi ~/.bashrc
>
> ```
> fcitx-autostart >/dev/null 2>&1
> ```
>
> fcitx-config-gtk3
>
> Keyboard - Korean 삭제 및 Hangul 추가, Global Config 에 한/영 키 추가

## Intellij

> wget https://download.jetbrains.com/toolbox/jetbrains-toolbox-1.18.7609.tar.gz?_ga=2.124379146.1025243524.1607222342-1452864861.1587042752
>
> tar xzvf jetbrains-toolbox-*.tar.gz && ./jetbrains-toolbox
>

## Intellij Shortcut

바탕화면에 바로가기 생성, 실행(R): 최소화

> %WINDIR%\System32\bash.exe -i -c "sh /home/hasoo/idea.sh"

Toolbox 는 X 버튼을 눌러도 트레이로 최소화, 완전 종료를 위해서는 설정 메뉴에서 Quit 클릭

> %WINDIR%\System32\bash.exe -c "sh /home/hasoo/toolbox.sh"

바로가기(Shortcut) 생성 시 대상(T) 에 입력하는 길이가 부족하기 때문에 bash script 를 생성

> vi ~/idea.sh
>
> ```
> #!/bin/bash
> export GTK_IM_MODULE=fcitx
> export QT_IM_MODULE=fcitx
> export XMODIFIERS=@im=fcitx
> export DefaultIMModule=fcitx
> export DISPLAY=$(ip route | awk '{print $3; exit}'):0
> export LIBGL_ALWAYS_INDIRECT=1
> 
> fcitx-autostart
> /home/hasoo/.local/share/JetBrains/Toolbox/apps/IDEA-U/ch-0/203.5981.155/bin/idea.sh
> ```
>
> vi ~/toolbox.sh
>
> ```
> #!/bin/bash
> export GTK_IM_MODULE=fcitx
> export QT_IM_MODULE=fcitx
> export XMODIFIERS=@im=fcitx
> export DefaultIMModule=fcitx
> export DISPLAY=$(ip route | awk '{print $3; exit}'):0
> export LIBGL_ALWAYS_INDIRECT=1
> 
> fcitx-autostart
> /home/hasoo/.local/share/JetBrains/Toolbox/bin/jetbrains-toolbox
> ```