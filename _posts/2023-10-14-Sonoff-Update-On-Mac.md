---
layout: post
title: "맥(Mac)에서 소노프 지그비(Sonoff Zigbee) 업데이트 하기"
description: "맥(Mac)에서 소노프 지그비(Sonoff Zigbee) 업데이트 하기"
date:   2023-10-12 15:01:35 +0300
image:  '/images/sonoff.png'
tags:   [ha, zigbee]
---


## 맥(Mac)에서 소노프 지그비(Sonoff Zigbee) 업데이트 하기

HA에 Zigbee 코디네이터를 달고자 알아보니 카페에서 많이 추천하는 장비가 `Sonoff`의 `ZB Dongle-P`란
제품이었습니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*b3zgbNyOI1f9LX_GAO4-9A.png)

해당 제품을 받으면 최신 펌웨어로 업데이트를 시켜주어야 하는데, 윈도우환경에서는 `SmartRF Flash Programmer v2`를 다운받아서
업데이트를 해주는데, 맥은 지원하지 않아서 찾은 방법을 소개시켜주고자 합니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*6OYXwny8MNgvwgNZ8EvsBA.png)

일단 [다음 링크](https://github.com/Koenkk/Z-Stack-firmware/tree/master/coordinator/Z-Stack_3.x.0/bin)로 들어갑니다
그 다음 `launchpad_coordinator`가 포함된 파일을 클릭해줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*iKKdpiTYBxgP_wIjQ_7f4g.png)

그럼 위와 같은 화면이 나타나는데 이름 확인하고 우측의 다운로드 아이콘을 눌러서 다운로드 해줍니다.
(따로 저장 경로를 설정해주지 않았다면 `Downloads`에 저장이 될 것입니다.)

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*t5r7pmhZPagyCFFSADFONA.png)

```shell
pip3 install pyserial intelhex
````

그 다음 맥의 터미널을 열고 아래 명령어를 입력해서 `pyserial`, `intelhex`를 설치해줍니다.

(반드시 먼저 파이썬3 버전이 설치되어있어야 하는데 맥은 기본적으로 파이썬이 설치되어 있습니다. 없는 경우 Homebrew를 통해서 파이썬을 설치해줍니다.)

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*3uArwg_bOmErS-eSpYtE2A.png)

그 다음 아래 명령어를 입력해줍니다. `mkdir`이런 명령어는 `update`란 이름의 디렉토리를 만들겠다는 명령입니다.
여기서 `update`는 임의로 주었으므로 이름을 변경해도 괜찮습니다.

```shell
mkdir update
````

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*fsA-ZvgD9EyqObQAR7OshQ.png)

그 다음 위에서 만든 `update`란 디렉토리로 이동해주겠습니다. 아래 명령을 입력합니다.

`cd`란 명령어는 터미널내에서 디렉토리간 이동을 위해 사용하는 명령어입니다. 아래 명령어를
입력하면 `update`란 디렉토리로 이동이 됩니다.

```shell
cd update
````

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*xWuR6mWq_iN7clkWCASUbQ.png)

이번에는 설치를 위한 파일을 다운로드 하도록 하겠습니다. 아래 명령어를 복사하여 붙여넣고 엔터를 눌러서 다운로드 받도록 합니다.

```shell
curl -sSL https://github.com/JelmerT/cc2538-bsl/archive/refs/heads/master.tar.gz | tar xz --strip 1
````

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*d7u4l6Qol73sWIwxZYO5zg.png)

그럼 위와 같이 다운로드 받은 파일들이 보일것입니다.


그 다음 `먼저` 동글을 맥에 연결해줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*u4wqDEqchL33Kb228V0Wig.png)

그리고 아래 명령어를 입력해줍니다.

```shell
ls /dev/tty* | grep usb
````

그럼 `/dev/tty.usbserial-3130` 같이 출력 결과가 나오는데, 여기서 `3130`은 기기마다 다르기때문에 본인의 기기 ID를 확인합니다.

그 다음은 맨 위에서 받았던 펌웨어를 `update`로 이동해줍니다.

터미널 상태에서 아래 명령어를 입력하면 파인더가 열리므로 다운로드에 있는 파일을 옮겨줍니다.

```shell
open .
```

저는 파일명이 `CC1352P2_CC2652P_launchpad_coordinator_20230507.zip`이었습니다.

이동한다음에 zip 압축 파일을 풀명 `CC1352P2_CC2652P_launchpad_coordinator_20230507.hex`란 이름의 파일이 나타납니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*O1d7bHL_e5l4QwDAAWyMzg.png)

그럼 `update` 디렉토리에 다음과 같이 파일들이 있는걸 확인할 수 있습니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*oR5NikY192ITIDnqe9fAgQ.png)

그 다음 아래 명령어를 입력해주면 설치가 완료가 됩니다.

```shell
python3 cc2538-bsl.py -ewv -p /dev/tty.usbserial-[자신의 USB Serial ID] --bootloader-sonoff-usb ./[설치한 펌웨어 파일명].hex
ex) python3 cc2538-bsl.py -ewv -p /dev/tty.usbserial-3130 --bootloader-sonoff-usb ./CC1352P2_CC2652P_launchpad_coordinator_20220219.hex
```



