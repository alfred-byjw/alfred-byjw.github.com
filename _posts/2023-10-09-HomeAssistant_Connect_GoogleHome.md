---
layout: post
title: "GoogleHome에 HomeAssistant 연동하기"
description: "GoogleHome에 HomeAssistant 연동하기"
date:   2022-09-26 15:01:35 +0300
image:  '/images/ha_googlehome.jpg'
tags:   [google, ha]
---


## GoogleHome에 HomeAssistant 연동하기

이번에는 Home Assistant에 연동된 기기들을 Google Home에 연동해보도록 하겠습니다. 이렇게 하면
Nest Home 같은 구글 기기들을 이용해 Home Assistant에 연동된 기기들을 제어할 수 있습니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*Gp66qLd_tVJLTfbXMbPxVw.png)

먼저 [https://console.google.com](https://console.google.com)에 접속해서 `New Project` 버튼을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*pINLzpgEEWTKh-z2itRwzQ.png)

그럼 다음과 같은 창이 뜨는데 프로젝트 이름을 지정하고 `Create Project` 버튼을 눌러줍니다.

저는 여기서 `Home Assistant`로 프로젝트 이름을 지어주었습니다. 

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*0zzk-qFIIuKipcBng9Xssg.png)

그 다음 `Smart Home`을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*erzTCXYbABsXfiPTE7T2kA.png)

선택이 되면 우측 상단에 `Smart Building` 버튼을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*n6rBm8Jyxg-_FrtZGy24ZA.png)

그 다음 `Quick setup - Name your Smart Home action`을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*sE9zzmYbOt3UBZxir74t3g.png)

그 다음 `Display name` 을 설정해주어야 하는데 저는 여기서 `HA`로 이름을 지어주고 우측 상단에 `Save` 버튼을 눌러주었습니다.

(이 이름은 구글홈에서 기기 추가를 할때 표시되는 이름입니다) 

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*lkBy5EHZx8zjkQyEJFWp6w.png)

그 다음 `Build your Action - Add Action(s)`를 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*Oqy2NU529Dq1YljK3TBakg.png)

다음과 같은 화면이 나타나면 `Fulfilment URL`에 다음과 같은 URL을 입력해줍니다.

`https://[자신의 Home Assistant 주소]/api/google_assistant`

그 다음 우측 상단에 `Save` 버튼을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*uL36M8fvgAEyO4vSCrhTDg.png)

그 다음 우측 상단에 `메뉴 아이콘 - Project settings`에 들어갑니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*WlXquxsdnz8FmE3NqlDwUw.png)

그럼 여기에 `Project ID`가 나타나는데 앞으로 설정에 필요하므로 따로 메모장 같은 곳에 저장해줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*MsRI5kZai3x3-wtdE-eitA.png)

다시 상단의 `Overview`로 가서 `Quick setup - setup account linking`을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*281xdX-DvBBKCmqcEaq8fA.png)

여기서 이제 다음과 같이 설정을 해줍니다.

- Client ID issued by your Actions to Google
  - https://oauth-redirect.googleusercontent.com/r/[PROJECT_ID]
  - 여기서 [PROJECT_ID]는 바로 위에서 저장한 Project ID 입니다.
- Client secret : *
- Authorization URL
  - https://[Home Assistant URL]/auth/authorize
- token URL
  - https://[Home Assistant URL]/auth/token

그 다음 `Next` 버튼을 누릅니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*tSnrdAvBwI3MDSxukV6S1w.png)

그 다음 별도의 선택없이 `Next` 버튼을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*Mq8mD1E0JF2SV56u5RDnSA.png)

그 다음은 `메일`과 `이름`을 설정해준다음에 `Next` 버튼을 누르고 우측 하단에 `Save`버튼을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*1wUoeQVpqBHPUbH1ebktCw.png)

 그 다음에 `Save` 버튼을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*fJ-5YzIn9grUF0MgDl5OoA.png)

여기까지 설정이 잘 되었다면 우측 상단에 다음과 같은 알림이 나타납니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*i-xY_me7WhYqIDwIiw7nhQ.png)

그 다음 우측 상단에 `Test` 버튼을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*fnBJ1V1TRCV0ZZr-MOLpaQ.png)

그 다음 우측 상단에 `Settings` 버튼을 눌러줍니다. 

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*vk7i03zyjtUmO1wxqotkyA.png)

그 다음 `On device testing` 부분을 활성화 해줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*oA8vcsoqT-9yEisYx20RvQ.png)

그 다음 [https://cloud.google.com](https://cloud.google.com)에 들어간다음에 좌측상단에 있는 이미지에 표시한 부분을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*jzwRpt_SAbSb-F1eZhQCqA.png)

그 다음 상단의 `전체 - HomeAssistant`를 눌러줍니다. 여기서 `HomeAssistnat`는 위에서 처음에 만들어줬던 `Project Name`입니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*AZuXaBC8ZbUEw0diwVyopg.png)

그 다음 좌측 상단의 `메뉴 - IAM 및 관리자 - 서비스 계정`을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*RbRbE8E0tSEQHz4E_C_Btg.png)

상단에 `+ 서비스 계정 만들기`를 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*PZkm7FUhibXpwwKZ-KYQLg.png)

다음과 같이 설정을 해줍니다.

- 서비스 계정 이름 : 임의의 이름을 줍니다.

그 다음 `이 서비스 계정에 프로젝트에 대한 액세스 권한 부여`를 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*8MKqa07oI3NMlupPSFJcvw.png)

그 다음 `역할 선택 - 서비스 계정 - 서비스 계정 토큰 생서자`를 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*oUsGx8eVfQosyqWGZir0Ag.png)

그 다음 `완료` 버튼을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*HIztXvSXMoFro5nsxB-lSw.png)

그럼 방금 만든 서비스 계정(=HomeAssistant)가 보일텐데 여기서 `메뉴 - 키 관리`에 들어갑니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*0CKZO5r0EWa8eCQO8ce_sQ.png)

`키 추가 - 새 키 만들기`를 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*WpVT-gfbR30PInFxdiO-JA.png)

키 유형의 두가지가 있는데 `JSON`을 선택하고 `만들기`를 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*wtX3mX1pvcsWjq8YDDs5Kg.png)

그럼 방금 만든 키를 컴퓨터에 다운로드 하게 됩니다. 권한이 필요하면 `허용`을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*g5GJ4-Buc7ER84ZeODztpA.png)

그 다음 상단 검색창에 `homegraph api`를 검색하여 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*rXvQatxHyEFeyAidJEmpVw.png)

다음과 같은 화면이 나타나면 `사용` 버튼을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*261SEc0qhovvRKpPvi58vg.png)

자신의 홈 어시스턴트에 접속을 한 다음 `설정 - 애드온`을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*tF7LsCmcOjvyawkFFNWOjg.png)

우측 하단에 `애드온 스토어` 버튼을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*rT8_RQ6p30GSjNrCYh3swA.png)

그 다음 `file editor`를 검색하여 선택해줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*Vx-D6M-ayySgaTfuz967Ew.png)

`설치하기`를 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*iwVZL8ODQDd--pCrtsIdfw.png)

설치가 되면 `사이드바에 표시하기`를 활성화 시켜준다음에 `시작하기`를 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*UCjAZhNPW__sV8vo-D1NGA.png)

사이드 바를 보면 `File editor`가 생긴것을 확인할 수 있습니다. 클릭을 한뒤에 우측 상단에 디렉토리 아이콘을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*fPKxE5k4pi-A6DtPN5nRPQ.png)

그 다음 `Upload File` 아이콘을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*LEciEoRPzq9jsHoWUXnssA.png)

그 다음 `아까 받았던 키(*.json)`를 업로드 시켜줍니다. 이때 업로드한 파일의 이름이 다음 단계에서 필요하므로 저장해줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*czoPGsPRKYwAOQLFYeCALg.png)

이제 설정을 위해서 `Studio Code Server`를 눌러줍니다.

(없으면 애드온에서 설치를 해주도록 합니다.)

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*Zem1RtPffUP9arm8F9U35w.png)

그 다음 `configuration.yaml` 파일을 선택해줍니다. 아래 내용을 입력해줍니다.

```shell
google_assistant:
  project_id: homeassistant-52979 # 맨 위에서 만들어줬던 Project ID
  service_account: !include homeassistant-52979-0631ec6aa386.json # 바로 위에서 저장한 키 이름
  report_state: true
```

설정이 완료되면 저장을 해줍니다. (입력이 되면 자동으로 저장이 됩니다.)

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*vydEjkJ-a6n7rpDYIOVl-Q.png)

설정이 바뀌었으니 재시동을 해줍니다. `설정 - 우측 상단 메뉴 - Home Assistant 재시작`을 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*t2YitCxKJ1y-q8dtPEOeZA.png)

핸드폰으로 `Google Home 앱`을 실행하고 `기기 - + 추가`를 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*QcG8qR-eK5eFUNjigvfn_Q.png)

`Google 호환 가능` 메뉴를 눌러줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*S3VpaHe_Wb6n049h-zZMVw.png)

그럼 상단에 제가 만들어줬던 `[test] HA`란 메뉴가 생긴걸 확인할 수 있습니다. 여기서 `HA`는 처음에 설정했던 `Display Name` 입니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*36XNniPASdLOcSsb3c9r_g.png)

그 다음 자신의 `Home Assistant`에 로그인을 해줍니다.

![](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*qkXDldSYXkUPbEIYEsRRkQ.png)

여기까지 잘 따라왔으면 `Home Assistant`의 기기들을 잘 가져오는 걸 확인할 수 있습니다.

---

## 마무리

꽤 긴 설정 과정이 필요하지만 스마트 홈을 구성하다보면 하나의 플랫폼으로 모든 기기를 연결할 수 없는 경우가 자주 발생합니다.
이때 서로 다른 플랫폼간의 연동이 필요한데 저도 이때 HA에 연동된 Zigbee 기기들을 가져와서 Nest Home으로 음성 제어를 
하고자 이렇게 연동하게되었습니다.


