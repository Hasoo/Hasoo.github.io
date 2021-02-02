---
layout: post
title: install intellij on wsl2
tags: [ intellij, wsl2 ]
categories: java
---



Linux 개발환경에서 Desktop/Laptop 의 OS 는 Linux Mint 와 macOS 를 선호한다.

c++ 코드는 vim 과 vscode 를 사용하며 java 코드는 intellij 를 사용하여 코드를 작성하고 있다.

리눅스 개발 환경에서 작업을 하다보니 Windows 10 은 기피하게 되었지만 Windows 10 에 WSL2 가 도입되어 리눅스 개발환경 구축이 용이해졌다.

아래 링크의 벤치마크 참고

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
> ```
>fcitx 선택
> ```
>
> vi ~/.bashrc
> 
> ```
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
> ```
> Keyboard - Korean 삭제 및 Hangul 추가, Global Config 에 한/영 키 추가
> ```
>
> 

## Intellij

> wget https://download.jetbrains.com/toolbox/jetbrains-toolbox-current-version.tar.gz
>
> tar xzvf jetbrains-toolbox-*.tar.gz && ./jetbrains-toolbox
>

## Intellij Shortcut

바탕화면에 바로가기 생성, 실행(R): 최소화

> %WINDIR%\System32\bash.exe -i -c sh /home/username/idea.sh

Toolbox 는 X 버튼을 눌러도 트레이로 최소화, 완전 종료를 위해서는 설정 메뉴에서 Quit 클릭

> %WINDIR%\System32\bash.exe -i -c sh /home/username/toolbox.sh

바로가기(Shortcut) 생성 시 대상(T) 에 입력하는 길이가 부족하기 때문에 bash script 를 생성

> vi ~/idea.sh
>
> ```
> #!/bin/bash
> /home/username/.local/share/JetBrains/Toolbox/apps/IDEA-U/ch-0/203.5981.155/bin/idea.sh
> ```
> 
> vi ~/toolbox.sh
> 
> ```
> #!/bin/bash
> /home/username/.local/share/JetBrains/Toolbox/bin/jetbrains-toolbox
> ```

## Screen Scale 

> laptop 에서 디스플레이 설정에 화면 비율을 높인 경우 앱이 흐릿하게 보인다. 이 경우 아래 설정으로 scale 을 고정하여 에디터 폰트를 늘려주는게 효과적이다.
>
> win + e 단축키, C:\Program Files\VcXsrv 해당 경로로 이동
>
> vcxsrv.exe 속성 - 호환성 - 높은 DPI 설정 변경 - 높은 DPI 조정 재정의 - 응용프로그램 체크 

