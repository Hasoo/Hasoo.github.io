---
layout: post
title: WSL2 Port Forwarding
tags: [ wsl2 ]
categories: windows
---



wsl2 의 port 에 연결하려면 Port Forwarding 을 해야 하며 wsl2 의 내부 IP 는 매번 변경된다. 이와 같은 이유로 powershell script 를 작성하여 매번 실행을 해줘야 한다.



### wsl2 ifconfig 설치

> sudo apt-get install net-tools

### wsl2-port-forwarding.ps1

```
If (-NOT ([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole] "Administrator"))
{   
$arguments = "& '" + $myinvocation.mycommand.definition + "'"
Start-Process powershell -Verb runAs -ArgumentList $arguments
Break
}
$remoteport = bash.exe -c "ifconfig eth0 | grep 'inet '"
$found = $remoteport -match '\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}';
if( $found ){
  $remoteport = $matches[0];
} else{
  echo "The Script Exited, the ip address of WSL 2 cannot be found";
  exit;
}
$ports=@(8080,8081,8082,8083);
iex "netsh interface portproxy reset";
for( $i = 0; $i -lt $ports.length; $i++ ){
  $port = $ports[$i];
  iex "netsh interface portproxy add v4tov4 listenport=$port connectport=$port connectaddress=$remoteport";
}
iex "netsh interface portproxy show v4tov4";
```

### Powershell 실행 권한 등록

Powershell script 를 실행하려면 제약 사항이 많아 관리자 권한으로 실행

```
PS C:\Users\vaxzee> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

[Powershell 의 실행 권한은 링크 참고](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7)

### 작업 스케쥴 등록

>작업 만들기
>
><일반 - 보안 옵션>
>
>사용자가 로그온할 때만 실행, 가장 높은 수준의 권한으로 실행
>
>구성대상 Windows 10
>
><트리거>
>
>로그온할 때, 특정 사용자
>
><동작>
>
>프로그램/스크립트: %SystemRoot%\system32\WindowsPowerShell\v1.0\powershell.exe
>
>인수추가: -File C:\Users\vaxze\wsl-connect-external.ps1