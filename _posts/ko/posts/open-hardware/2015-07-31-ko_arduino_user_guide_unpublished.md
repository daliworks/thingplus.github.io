---
title: 아두이노 사용자 가이드(unpubliched)
tags: "open-hardware"
published: false
permalink: /ko/open-hardware/arduino-user-guide_unpublished.html
---

Thing+ 연동가이드(아두이노)<br/>
<div id='id-windows'></div>

* [Windows 환경 설정](#id-windows)
* [아두이노 하드웨어 연결](#id-setting)
* [아두이노 펌웨어 설치](#id-firmware)
* [ThingPlus Embedded 패키지 설치](#id-package)
* [게이트웨이 등록](#id-register)


_현재는 `Mac OS, Windows7`에서만 지원하고 있습니다._

<br/>
#### 0. Windows 환경 설정
* `Mac OS` 사용자는 이 과정이 필요없습니다. [아두이노 하드웨어 연결](#id-setting)로 가세요.
<br/>

1) Node Js 설치
- Node JS(v0.10.16)를 설치합니다.

- <a href="https://nodejs.org/dist/v0.10.16/node-v0.10.16-x86.msi" target="_blank"> 32bit 다운로드</a>
- <a href="https://nodejs.org/dist/v0.10.16/x64/node-v0.10.16-x64.msi" target="_blank"> 64bit 다운로드</a>

2) Cygwin 설치

- <a href="https://cygwin.com/setup-x86.exe" target="_blank"> 32bit 다운로드</a>
- <a href="https://cygwin.com/setup-x86_64.exe" target="_blank"> 64bit 다운로드</a>

- Cygwin 다운로드 사이트 선택화면이 나오면 `ftp://ftp.kaist.ac.kr`을 선택합니다.
![Cygwin select ftp site](/assets/cygwin_site_select.png)

- Cygwin Package 선택화면에서는 'wget'을 선택합니다.

  - Search에 wget 입력 -> Web -> 1.16.3-1 선택
![Cygwin wget package select](/assets/cygwin_wget.png)


- 설치과 완료되면 바탕화면에 Cygwin Terminal 아이콘이 보입니다.

![Cygwin Icon](/assets/cygwin_icon.png)


<div id='id-setting'></div>
<br/><br/>
#### 1. 아두이노 하드웨어 연결 

0) <a href="https://www.icbanq.com/P005710113/S" target="_blank"> Grove Starter Kit for Arduino 구매 바로가기</a>

<br/>
1) 아두이노와 Grove Sensor Board를 연결합니다.
![Arduino + Grove Starter kit](/assets/arduino_grove_board.png)

<br/>
2) Grove Sensor Board에 센서를 연결합니다.<br/>
  참고 : <a href="#" class="ledtip" data-tooltip="">LED의 극성</a>

![Arduino + Grove Sensor Board + Sensors](/assets/arduino_sensors.png)

<br/>
3) 아두이노에 USB Cable을 PC와 연결합니다.
![Arduino + USB Cable](/assets/arduino_usb.png)

<div id='id-firmware'></div>
<br/><br/>
#### 2. 아두이노 펌웨어 설치
1) 사용하는 PC OS버전에 맞는 아두이노 IDE를 설치합니다.

   - <a href="https://www.arduino.cc/en/Main/Software" target="_blank"> 다운로드 링크 </a>

<br/>
2) 아누이노 IDE를 실행합니다.


<br/>
3) 아두이노 IDE에서 아두이노 포트를 USB로 선택합니다.

   - Tools -> Port -> Arduino/Genuino Uno
![Arduino Select Port](/assets/arduino_ide_select_port.png)

<br/>
4) 아두이노에 다운로드 할 펌웨어를 선택합니다.

   - File -> Examples -> Firmata -> StandardFirmata
![Arduino Select Firmware](/assets/arduino_ide_select_firmare.png)

<br/>
5) 펌웨어를 빌드합니다.

![Arduino Verify](/assets/arduino_ide_verify.png)

<br/>
6) 펌웨어를 아두이노에 다운로드합니다.

![Arduino Download](/assets/arduino_ide_upload.png)

<br/>
7) 펌웨어가 정상적으로 다운로드 되면 IDE 하단에 아래와 같은 메세지가 나옵니다.

![Arduino Download Success](/assets/arduino_ide_upload_done.png)

<div id='id-package'></div>
<br/><br/>
#### 3. ThingPlus Embedded 패키지 설치
1) Terminal을 실행시킵니다.

- Windows : 바탕화면의 'Cygwin Terminal' 실행

- Mac OS : 'Terminal' 실행

2) Thing+ Embedded 패키지를 설치할 폴더를 만들고 이동합니다.

```bash
@PC:$ mkdir $HOME/thingplus
@PC:$ cd $HOME/thingplus
```

3) 인스톨 스크립트 파일을 다운로드합니다.

`Windows`

```bash
@PC:$ wget http://support.thingplus.net/download/install/thingplus_embedded_sdk_win_install.sh
```

`Mac OS`

```bash
@PC:$ wget http://support.thingplus.net/download/install/thingplus_embedded_sdk_osx_install.sh
```

4) 다운로드한 스크립트 파일에 실행권한을 부여하고 Thing+ Embedded 패키지를 설치합니다.

- Thing+ Embedded 패키지를 설치하는데 네트워크 상태에 따라 수분이 소요될 수 있습니다.

`Windows`

    ```bash
    @PC:$ chmod 755 thingplus_embedded_sdk_win_install.sh
    @PC:$ ./thingplus_embedded_sdk_win_install.sh
    ```

`Mac OS`

    ```bash
    @PC:$ chmod 755 thingplus_embedded_sdk_osx_install.sh
    @PC:$ ./thingplus_embedded_sdk_osx_install.sh
    ```

<div id='id-register'></div>

<br/><br/>
#### 4. 게이트웨이 등록
[게이트웨이 등록 방법](/ko/user-guide/registration.html#id-gateway) 의 절차를 따르면 됩니다.
