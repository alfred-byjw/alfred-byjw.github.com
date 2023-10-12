---
layout: post
title: "Zemismart 벽 스위치 설치하기"
description: "Zemismart 벽 스위치 설치하기"
date:   2023-10-12 15:01:35 +0300
image:  '/images/zemismart.png'
tags:   [ha]
---


## Zemismart 벽 스위치 설치하기

이번에 벽의 천장등 스위치를 스마트 스위치로 변경해보았습니다. 알리에서 Zemismart 벽 스위치를 구입하여 설치하였고
생각보다는 쉽게 설치를 할 수 있었습니다.

해당 스위치는 중선선이 없는 2선식이고(저희나라는 대부분 2선식입니다.) 통신방식은 Zigbee 통신을 지원하는 기기였습니다.

## 설치

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*RrxYfn6a6kmGOuMKQvqpeQ.jpeg)

포장은 다음과 같이 되어 있습니다. 버튼 스위치에 따라서 1개~4개까지 있는데 같은 박스를 이용하는거 같았습니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*EK4aKiB9jF3ZaYSGs9SfvQ.jpeg)

내용 구성은 다음과 같습니다.

- 스위치 본체
- 설명서
- 나사

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*psYVPu1TlZUZsfMTE5edwA.jpeg)

본체 뒷쪽을 보면 다음과 같습니다.

- L : 전원선, 전기가 들어오는 선을 넣어줍니다.
- L1~L3 : 스위치 전선이 들어오는 부분입니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*1LUb7UsK4Bd5PNbV2p4qQA.jpeg)

윈쪽의 나사를 풀고 선을 넣어준다음에 나사를 조여서 선을 고정시켜주는 방식입니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*cSAQdU0LpcV-ZeZZ54yBLA.jpeg)

스위치 커버를 벗기면 다음과 같이 파란색으로 스위치가 있는데 이 스위치가 눌리면서 토글이 되며 On/Off가 되는 구조였습니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*g0ks0CMqnyijfJUrZidxGw.jpeg)

하단에는 드라이버를 넣어서 스위치 커버를 열어주게끔 되어 있습니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*w_LiwXjJbiVvsBJzKkgXBA.jpeg)

집 벽에 있는 스위치를 제거해줍니다. 그럼 다음과 같이 선이 나타나는데 기존에 연결을 확인하여 전원용 선인지 스위치용 선인지 확인합니다.

(** 반드시 전에는 써킷박스(=두꺼비집)에서 전등 부분을 꺼주어야 합니다.)

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*lAbPZc9EBnPN9Q3kFHU-kw.jpeg)

연결을 하고 나사를 조여줍니다. 그 다음 벽에 다시 고정시켜줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*X9Ydm0ovnbBja6vd_n4cnQ.jpeg)

그럼 다음과 같은 모습이 됩니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*ELj9lAvGzWGMTasmGWGNAA.jpeg)

스위치 커버까지 닫으면 설치는 끝이 납니다.

---

## 설정

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*TqH2Y1M2VV8tmBnVd52yDQ.png)

저는 HomeAssistant에 연동을 시켜주었습니다. Zigbee2MQTT로 연동을 해주니 바로 잡혔습니다.
스위치를 페어링 모드로 들어가게 하려면 버튼을 15~20초 누르고 있어주면 불빛이 반짝반짝하면서 자동으로 잡히게 됩니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*j10LEczKmhke8nSzqsiYtw.png)

연동이 잘되어서 별도의 스위치가 3개 잘 잡힌것을 확인할 수 있습니다.

---

## 아쉬운 점

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*zaV4pwr5ZpuZFnaKQhrczQ.jpeg)

위에 표시한 부분이 인디케이터로 불이 켜졌는지 꺼졌는지 확인할 수 있는 부분인데 여기 불빛이 너무 약해서 실제로 인디케이터의 역할을
제대로 못한다는게 조금 아쉬웠습니다.