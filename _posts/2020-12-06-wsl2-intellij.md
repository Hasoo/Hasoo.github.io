---
layout: post
title: install intellij on wsl2
tags: [ intellij, wsl2 ]
categories: java
---

c++, java 개발환경은 항상 linux 기반이었다. c++ 로 client/server 모듈 개발시 테스트 서버를centos 를 설치하여 ssh 로 접근하여 terminal 기반인 vim editor 로 코딩을 해왔었다.



현재 나의 c++, java 의 os 는 linux 이며 desktop 및 laptop 의 main os 는 linux mint 이다.

linux mint 에서 vim 과 visual studio code 를 사용하여 c++ 코드를 작성하고 있으며 java 코드는 intellij 사용하여 작성하고 있다.

과거 windows 에서 visual studio 를 사용하여 client/server 모듈을 개발해 왔으며 debugging 환경이 너무 그리웠다. linux 에서 vim 과 gdb 를 사용 해왔지만 gui 환경은 너무 편하다.

linux mint 를 사용하고 있지만 windows 를 사용할 수 밖에 없다. ms office

주변 모두가 mac 을 사용한다면 모를까

이에 windows 에 wsl2 가 도입되어 linux kernel 을 사용할 수 있게 되었고 Intellij 를  wsl2 에 설치하여 사용해보자.

참고로 동일한 성능의 장비를 기준으로 windows, mac, linux 에서 Intellij 를 사용하여 build 를 해보면 linux 에서 가장 빠르다. 또한 docker 를 사용하여 개발 환경을 구축한다면 비교 불가

아래 링크 참고

[Development under Windows under Linux with WSL2 (IntelliJ)](https://medium.com/@ragin/development-under-windows-under-linux-with-wsl2-intellij-860daf601b61)



## VcXsrv

> [download](https://sourceforge.net/projects/vcxsrv/files/latest/download)
>
> XLaunch 초기 실행시 Extra Settings 에서 Disable access control 체크
>
> Save configuration 

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
> vi .bashrc
>
> #!/bin/bash
>
> ```
> export QT_IM_MODULE=fcitx
> export GTK_IM_MODULE=fcitx
> export XMODIFIERS=@im=fcitx
> export DefaultIMModule=fcitx
> 
> #optional
> fcitx-autostart &>/dev/null
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