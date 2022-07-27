---
title: Docker 삽질 기록
categories: dev
date: 2022-07-26 16:16:11
tags: Docker 
---


## Hardware assisted virtualization and data execution protection must be enabled in the BIOS. 

- 제어판 설정에서 Hypervisor, 가상 머신이 켜져 있었고 혹시 몰라 컨테이너도 켰음에도 에러가 발생하였다. 보통 나의 경우에는 윈도우에서 Docker의 경우 Hypervisor를 거쳐서 실행되는데 자동 실행 등을 꺼놓아서 에러를 겪었다

1. Hyper-v 재활성화

Powershell을 관리자 권한으로 실행 한다. 아래 커맨드를 입력 후 재부팅한다

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```

2. Hyper-v 자동실행 설정

Powershell을 관리자 권한으로 실행 후 아래 명령어 입력하고 재부팅한다.

```powershell
bcdedit /set hypervisorlaunchtype auto
```