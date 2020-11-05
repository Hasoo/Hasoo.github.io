---
layout: post
title: oracle 12c client version
tags: [ oracle ]
categories: db
---

#### Oracle 12c 하위 버전 클라이언트 접속

> ORA-28040: No matching authentication protocol
>
> ORA-01017: invalid username/password; logon denied

하위 버전에서 위와 같은 에러를 만났을 때 아래와 같이 처리한다.

> \> vi $ORACLE_HOME/network/admin/sqlnet.ora
>
> SQLNET.ALLOWED_LOGON_VERSION_SERVER=11
> SQLNET.ALLOWED_LOGON_VERSION_CLIENT=11

> \> lsnrctl stop && lsnrctl start

> \> sqlplus
>
> SELECT PASSWORD_VERSIONS FROM DBA_USERS WHERE USERNAME='username';
>
> ALTER USER username IDENTIFIED BY newpassword;

