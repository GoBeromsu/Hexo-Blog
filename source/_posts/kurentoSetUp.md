---
title: Kurento Docker로 설치하는 방법 feat Window
categories: dev
date: 2022-07-28 10:41:59
tags:
    - Kurento
    - Docker
---

## 현재 상황

- Window Docker Client가 있긴 하지만, 프로젝트 초기기도 하구 이참에 그냥 WSL에서 쓰는게 더 편할거라 생각했다

## 준비 사항

- WSL2
- ~~Kali Linux~~
  - Kali도 데비안 계열이라 상관 없다 (사실 그냥 상관 없기도 하다 혹시 몰라서 적어둔다)
  - 22.07.30 기준 Ubuntu가 정신 건강에 매우 좋다
- Ubuntu 18.0.5
- Docker

## WSL2에 Docker 설치

- Sudo 권한으로 진행해야한다.

1. 기존 버전 삭제

    ```sh
    apt-get remove docker docker-engine docker.io
    ```

2. 패키지 설치

    ```sh
    sudo apt-get update && sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
    ```

    - apt-transport-https
      - 패키지 관리자가 https를 통해 데이터 및 패키지 접근 할 수 있도록 한다.
    - ca-certificates
      - SSL 기반 앱이 SSL 연결이 되어 있는지 확인 가능
    - software-properties-common
      - PPA(개인 패키지 저장소)를 추가하거나 제거할 때 사용
1. GPG Key 설치

   ```s
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```

2. Repository 추가

    ```s
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"

    sudo apt update
    ```

3. Docker 설치

    ```
    apt-get update && apt-cache search docker-ce
    ```

- 이제 docker images 커맨드를 입력하면 아래와 같이 실행되는 것을 알 수 있다

![Docker 설치 완료!](https://user-images.githubusercontent.com/37897508/181415322-cf5ce763-e6c7-49e8-a5bb-513a47c93c6e.png)

## Error

### Hardware assisted virtualization and data execution protection must be enabled in the BIOS

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

### gnupg, gnupg2 and gnupg1 do not seem to be installed, but one of them is required for this operation

- apt-key adv --keyserver keyserver.ubuntu.com:80 --recv-keys 5AFA7A83 커맨드 입력시 에러 발생
  - 쿠렌토 저장소를 추가하려는 상황이었다

```shell
apt-get update
apt-get install gnupg
```

### The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7EA0A9C3F273FCD8

- 패키지를 다운로드 받으려는데 공개키가 없다고 하는 상황이다
- 그냥 없는 공키를 아래 커맨드에 넣어 추가하면 된다

```shell
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <PUBKEY>

```
### The repository 'https://download.docker.com/linux/ubuntu kali-rolling Release' does not have a Release file.

- 칼리 리눅스와 우분투에서 별 차이 없이 Set up이 될 줄 알았는데 아니다
  - 데비안 계열 커맨드를 사용해서 저장소를 다시 설정해 주어야한다.

```shell
printf "%s\n" "deb [arch=amd64] https://download.docker.com/linux/debian buster stable" |\
sudo tee /etc/apt/sources.list.d/docker-ce.list
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

## Unable to locate package kurento-media-server


## Reference

[쿠렌토 서버 Docker로 실행시켜보기](https://gh402.tistory.com/44?category=935378)
[칼리 리눅스에 도커설치하는 방법](https://unix.stackexchange.com/questions/630643/how-to-install-docker-ce-in-kali-linux)