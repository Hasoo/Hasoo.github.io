---
layout: post
title: search zombie
tags: [ linux ]
categories: linux
---





zombie process 검색을 위해 아래 명령어를 사용해보자.

zombie process 의 parent process 를 보여준다.

```
ps -elf --forest | grep -C5 '<[d]efunct>'
```