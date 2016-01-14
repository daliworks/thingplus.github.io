---
title: 아두이노 + 라즈베리파이 사용자 가이드
tags: "open-hardware"
published: false
permalink: /ko/open-hardware/arduinoPi-user-guide.html
---

Thing+ 연동가이드(아두이노 & 라즈베리파이)<br/>
<div id='id-windows'></div>

1. [아두이노 펌웨어 설치](#id-firmware)
2. [환경설정](#id-setting)
3. [ThingPlus Embedded 패키지 설치](#id-package)
4. [게이트웨이 등록](#id-register)


<br/>

---
Arduino에서 얻은 센서 데이터를 Thing+에 전송하기 위해서는 Internet 연결이 필요합니다. 그러나, 아두이노 자체만으로는 Internet에 연결할 수 없기 때문에 PC 등을 게이트웨이로 사용해야하는데 본 장에서는 라즈베리파이를 게이트웨이로 하고 아두이노를 디바이스로 사용하여 IOT 서비를 연동하는 방법을 설명합니다.
<br/><br/><br/>

#### 1. 아두이노 펌웨어 설치

1) 아두이노와 PC를 연결합니다.

<br/>
2) 사용하는 PC OS버전에 맞는 아두이노 IDE를 설치합니다.

   - [다운로드링크](https://www.arduino.cc/en/Main/Software)

<br/>
3) 아누이노 IDE를 실행합니다.


<br/>
4) 아두이노 IDE에서 아두이노 포트를 USB로 선택합니다. (windows에서는 COMxx 입니다.)

   - Tools -> Port -> Arduino/Genuino Uno
![Arduino Select Port](/assets/arduino_ide_select_port.png)

<br/>
5) 아두이노에 다운로드 할 펌웨어를 선택합니다.

   - File -> Examples -> Firmata -> StandardFirmata
![Arduino Select Firmware](/assets/arduino_ide_select_firmare.png)

<br/>
6) 펌웨어를 빌드합니다.

![Arduino Verify](/assets/arduino_ide_verify.png)

<br/>
7) 펌웨어를 아두이노에 업로드 합니다..

![Arduino Download](/assets/arduino_ide_upload.png)

<br/>
8) 펌웨어가 정상적으로 다운로드 되면 IDE 하단에 아래와 같은 메세지가 나옵니다.

![Arduino Download Success](/assets/arduino_ide_upload_done.png)



<div id='id-setting'></div>
<br/>

---
#### 3. 환경 설정 

1) <a href="https://www.icbanq.com/P005710113/S" target="_blank"> Grove Starter Kit for Arduino 구매 바로가기</a>

<br/>

<br/>
2) 아두이노와 Grove Sensor Board를 연결합니다.
![Arduino + Grove Starter kit](/assets/arduino_grove_board.png)

<br/>
3) Grove Sensor Board에 센서를 연결합니다.<br/>

<p class="dwExpand"> 참고 : LED의 극성</p>

![LED 극성](/assets/led.png)

<div class="dwExpand2"></div>

![Arduino + Grove Sensor Board + Sensors](/assets/arduino_sensors.png)

<br/>



<div id='id-pi-setting'></div>
<br/>

---
#### 4. 라즈베리파이 환경 설정

<br/>
ThingPlus Embeded는 Gateway인 라즈베리파이에서 설치 합니다. 본 절은 설치전 준비 사항입니다.

1) Micro SD card(8GB 이상)을 준비한다.

<br/>
2) 아래의 다운로드 페이지에서 Raspbian image를 다운로드 한다.

   - Raspbian Image 다운로드 링크 - [Raspbian Image](https://downloads.raspberrypi.org/raspbian/images/raspbian-2015-09-28/2015-09-24-raspbian-jessie.zip)
   - `2015-09-24-RASPBIAN JESSIE` 이미지 권장

<br/>
3) 아래의 웹페이지를 참조하여 Micro SD card에 다운로드 받은 이미지로 OS를 설치한다.

   - Raspbian image를 Micor SD card에 설치하는데 수분이 소요됩니다.
   - https://www.raspberrypi.org/documentation/installation/installing-images/

<br/>
4) 라즈베리파이를 제어하기 위해서는 Telnet/SSH 클라이언트가 필요합니다.

   - Mac 또는 Linux 사용자일 경우 기본 터미널을 사용하시면 됩니다.
   - 윈도우 사용자일 경우, Putty 클라이언트 사용을 권장합니다.
   - Putty 다운로드 링크 - http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe

<br/>
5) Raspbian을 설치한 Micro SD card를 라즈베리파이 아래 그림과 같이 **뒷면**의 Micro SD card 슬롯에 꽂는다.
   ![Raspberry Pi + Micro SD card](/assets/insert_sdcard.png)

<br/>
6) 라즈베리파이에 Ethernet(LAN 케이블), Power Cable을 연결한다.
   ![Raspberry Pi + Ethernet & power cable](/assets/rasp_power_ethernet.jpg)

<br/>
<div id='id-pi-setting-seventh'></div>
7) 부팅이 완전히 이루어지도록 2~3분 정도 대기한 후, 터미널(윈도우즈 PC에서는 putty)을 열고 아래처럼 접한다

   - IP address를 찾기 힘들 경우 [`문제 해결 방법`](/ko/help/troubleshooting.html)을 참고한다.

   - 아이디: **pi**
   - 비밀번호: **raspberry**

    ```bash
    $ ssh pi@<IP Address>
    pi@<IP Address>'s password: raspberry
    ```

     - Mac & Linux 예제

        ```bash
        $ ssh pi@192.168.1.XXX
        pi@<IP Address>'s password: raspberry
        ```

     - Windows 예제

       - putty 실행 후, 아래 그림과 같이 IP주소를 입력 후, `Open`버튼을 클릭하고 비밀번호를 입력한다.
       ![Raspberry Pi putty login](/assets/putty_login.png)
       ![Raspberry Pi putty login](/assets/putty_login_2.png)

> 주의: Windows의 경우, 라즈베리파이를 재부팅할 때마다, putty를 새로 실행해야함.

<br/>
8) 라즈베리파이의 시스템 시간을 업데이트한다.

```bash
@Pi2:$ sudo su
@Pi2:$ apt-get update
@Pi2:$ apt-get install -y --force-yes ntp ntpdate
@Pi2:$ ntpdate -u ntp.ubuntu.com
```

- 만약, 시스템 시간 업데이트에 실패할 경우, 직접 시간을 갱신한다.

  - UTC 시간 기준 [(링크)](http://www.worldtimeserver.com/current_time_in_UTC.aspx): 2015년 01월 01일 00:00:00 경우, 2015-01-01 00:00:00

    ```bash
    @Pi2:$ date --set '20XX-XX-XX XX:XX:XX'
    ```

<br/>
9) 장치 구분을 위해 라즈베리파이의 호스트명 변경이 필요합니다.

> 주의: Termianl/Putty에서는 마우스로 커서이동이 불가능하므로, 키보드의 화살표 키를 사용해야 함.

 - `/etc/hostname`을 수정한다.

    ```bash
    @Pi2:$ sudo nano /etc/hostname
    ```

   - 파일 내부의 `raspberrypi`를 아래 그림과 같이 원하는 이름(알파벳 및 숫자, -만 허용)으로 변경한다.
   ![Raspberry Pi Modify hostname](/assets/modify_hostname.png)

     - 파일 수정 후 저장은 `CTRL-O`키를 누른 후, 엔터키를 누르고, 종료할 때는 `CTRL-X`키를 누른다.

<br/>

 - `/etc/hosts`를 수정한다.

    ```bash
    @Pi2:$ sudo nano /etc/hosts
    ```

   - 파일 내부의 `raspberrypi`를 아래 그림과 같이 위와 동일한 이름으로 변경한다.
   ![Raspberry Pi Modify hosts](/assets/modify_hostname_2.png)

 - 파일 수정 후 저장은 `CTRL-O`키를 누른 후, 엔터키를 누르고, 종료할 때는 `CTRL-X`키를 누른다.

<br/>

- 변경한 호스트명 적용을 위해 라즈베리파이를 재시작한다.

    ```bash
    @Pi2:$ sudo reboot
    ```

<br/>
10) 재부팅이 완료된 라즈베리파이에 재접속한다. ([`7번 과정`](#id-pi-setting-seventh) 참고)

<br/>
11) 4GB 이상의 SD card를 사용하기 위해서, `raspi-config`를 실행한다.

```bash
@Pi2:$ sudo su
@Pi2:$ raspi-config
```

<br/>

   a. 4GB 이상의 SD card를 사용하기 위해서 `1. Expand Filesystem`을 선택한다.
   ![Raspberry Pi Setting File sytsem](/assets/expand_file_system.png)

   
<br/>
   b. Tab키를 누르고 Finish를 선택한 후 Reboot할 것이냐는 물음에 `YES`를 선택한다.
   ![Raspberry Pi Choose Finish](/assets/choose_finish.png)

   ![Raspberry Pi Choose Finish](/assets/choose_finish_2.png)

<br/>
   
<div id='id-package'></div>

<br/><br/>

---
#### 5. Thing+ Embedded 패키지 설치

1) 라즈베리파이에 아두이노의 센서를, Ethernet(LAN 케이블)과 Power Cable을 분리한 상태에서 연결한뒤, Ethernet(LAN 케이블)과 Power Cable을 연결한다. 

   ![Raspberry Pi + arduino](/assets/adupi1.png)

   ![Raspberry Pi + arduino](/assets/adupi2.png)

<br/>
2) 라즈베리파이에 접속한다.

<br/>

3) 패키지를 설치할 폴더를 만든다

```bash
@Pi2:$ mkdir thingplus
@Pi2:$ cd mkdir
```

<br/>
4) 인스톨 스크립트 파일을 다운로드한다.

```bash
@Pi2:$ wget http://support.thingplus.net/download/install/thingplus_embedded_sdk_pi_arduino_install.sh
```

<br/>
5) 다운로드한 스크립트 파일에 실행권한을 부여하고 Thing+ Embedded 패키지를 설치한다.

- Thing+ Embedded 패키지를 설치하는데 네트워크 상태에 따라 수분이 소요될 수 있습니다.

    ```bash
    @Pi2:$ sudo su
    @Pi2:$ chmod 755 thingplus_embedded_sdk_pi_install.sh
    @Pi2:$ ./thingplus_embedded_sdk_pi_install.sh
    ```

<br/>
6) 라즈베리파이를 재시작한다.

```bash
@Pi2:$ sudo reboot
```
<div id='id-register'></div>

<br/><br/>



---
#### 6. 게이트웨이 등록
[게이트웨이 등록 방법](/ko/user-guide/registration.html#id-gateway) 의 절차를 따르면 됩니다.

<!-- <a href="#" class="back-to-top" id="up" style="display: block;"><i class="fa fa-arrow-circle-up"></i></a> -->

<div class='scrolltop'>
    <div class='scroll icon'><i class="fa fa-arrow-circle-up"></i></div>
</div>