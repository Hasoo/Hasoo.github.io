---
layout: post
title: oracle 12c resource role
tags: [ oracle ]
categories: db
---

#### [Oracle 12c New Features](https://docs.oracle.com/database/121/NEWFT/chapter12101.htm#NEWFT002)

12c 에서 grant connect, resouce to userid; 로 resouce role 을 부여해도 unlimited tablespace 권한이 없음

> select * from session_privs order by 1;

11g 에서는 위 명령어로 UNLIMITED TABLESPACE 권한이 부여되어 있음

> grant unlimited tablespace to userid;

default tablespace 로 지정을 해둬 권한이 생기지 않기에 위와 같이 직접 권한을 부여해야함

