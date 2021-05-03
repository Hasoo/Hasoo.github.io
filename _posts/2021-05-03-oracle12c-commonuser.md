---
layout: post
title: oracle 12c common user or role name
tags: [ oracle ]
categories: db
---

#### Oracle 12c 공용 계정 및 롤

> create user test identified by test;
>
> ORA-65096: invalid common user or role name

공용 계정 및 롤 생성 시 이름 앞에 C## 을 붙여야 한다. 11g 와 같이 하려면 아래 명령어 입력

> alter session set "_ORACLE_SCRIPT"=true;
>
> create user test identified by test;
>
> alter user test identified by test;
>
> grant connect, resource to test;
>
> revoke connect, resource from test;

