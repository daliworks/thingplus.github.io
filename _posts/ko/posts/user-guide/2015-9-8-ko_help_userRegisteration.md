---
title: 하드웨어 설치와 회원가입
tags: "user-guide"
published: true
permalink: /ko/user-guide/registration.html
---

서비스를 사용하기 위해 필요한 하드웨어 연동 및 회원가입에 대한 가이드입니다.

* [서비스 관리자](#id-serviceadmin)
* [일반 사용자](#id-enduser) 
* [게이트웨이 등록](#id-gateway) 

---
<div id='id-serviceadmin'></div>
### 서비스 관리자
<br>
#### 가입 및 사용
  * Thing+ 포털 사용을 위해서는 하드웨어 구입과 설치가 필요합니다. 귀사의 맞춤형 하드웨어 구입과 설치를 위해 [iot@daliworks.net](mailto:iot@daliworks.net)으로 연락바랍니다. 최고의 IoT 전문가가 친절히 도와 드리겠습니다.
  * **하드웨어에 대해 알아보기**
    * 귀사의 IoT 서비스 구축을 위한 하드웨어에 대해 알아보세요.
    * Thing+에 연결가능한 [하드웨어 목록](http://www.daliworks.net/?page_id=11441)을 참고하시길 바랍니다.
  * **이미 하드웨어를 가지고 있습니까? 새로운 IoT 하드웨어를 계획하고 있습니까?**
    * [hw@daliworks.net](mailto:hw@daliworks.net)으로 연락주시면 하드웨어와 Thing+ 연동에 대해 안내해 드리겠습니다.

<br>

---
<div id='id-enduser'></div>
### 일반 사용자
<br>

#### 해당 서비스 회원가입
  * 인터넷 브라우저의 주소창에 서비스 주소를 입력합니다.
![](/assets/2_address.png)

  * 상단에 위치한 ![](/assets/2_register.png) 회원가입 버튼을 통해 회원가입 페이지로 이동합니다.
  * 아이디, 이메일(입력 및 확인), 암호(입력 및 확인)를 입력하고, 이용약관에 동의를 하면, “등록 성공” 메세지가 나옵니다.
  * 회원가입 시 입력했던 이메일 주소로 본인 확인용 이메일이 전송됩니다.
  * 이메일 수신을 확인하시고, 아래와 같이 이메일 본문의 이메일 인증 버튼을 누르면, 인증이 완료됩니다.
![](/assets/2_email.png)

#### 서비스 관리자의 가입승인 및 사용권한
  * 이메일 인증 성공 후, 해당 서비스 관리자의 가입 승인 절차가 이뤄지게 됩니다.
  * 관리자의 가입 승인이 확인되면, 승인 안내 이메일이 전송됩니다.
  * 관리자의 가입 승인 안내 이메일은 몇초에서부터 몇분까지 걸릴 수 있습니다. 만약 승인 안내 이메일을 받지 못했다면 다음을 확인해주세요.
    * 이메일을 올바르게 입력하셨습니까?
    * 스팸메일함을 확인하셨습니까?
  * 관리자의 승인 안내 이메일을 받은 후에 로그인창에 아이디와 비밀번호를 입력하여 로그인 할 수 있습니다.

<br>

---
<div id='id-gateway'></div>
### 게이트웨이 등록
<br>

#### BeagleBone Black 기준 

1) BeagleBone Black에 접속 후 Thing+ Embedded 패키지가 설치된 디렉토리의 `scripts` 디렉토리로 이동한다.

```bash
@BBB:$ cd /usr/local/tp/scripts
```

2) BeagleBone Black의 MAC 어드레스를 얻어 클립보드에 복사한다.

```bash
@BBB:$ ./getmac
Your MAC address is as below
xx:xx:xx:xx:xx:xx
```

3) **사용자 PC**의 크롬브라우저를 열고 "[서비스 웹사이트](https://www.thingplus.net)"에 로그인한다.


4) `설정` --> `게이트웨이 관리` 버튼을 누른다.
![gateway_management](/assets/gateway_management_ko.png)

<br/>
5) `(+)` 버튼을 누른다.
![register_gateway](/assets/register_gateway_ko.png)

<br/>
6) `게이트웨이 API 키 발급받기` 버튼을 누른다.
![register_with_apikey](/assets/register_with_apikey_ko.png)

<br/>
7) 클립보드에 복사했던 MAC 어드레스를 `게이트웨이 아이디`에 붙여넣기 하고 `게이트웨이 API 키 등록 진행` 버튼을 누른다.
![macaddress](/assets/macaddr_getapikey_ko.png)

<br/>
8) API 키를 클립보드에 복사한다.
![get_apikey](/assets/get_apikey_ko.png)

<br/>
9) **BeagleBone Black에 로그인했던 터미널**에서 아래처럼 게이트웨이를 실행한다.

```bash
@BBB:$ cd /usr/local/tp
@BBB:$ APIKEY='복사한 API 키' ./tp.sh start; ./driver.sh start
```

- 예제

```bash
@BBB:$ cd /usr/local/tp
@BBB:$ APIKEY='A7i3kT9w1-9xWVk447-oJ=' ./tp.sh start; ./driver.sh start
```

> 주의: APIKEY는 모두 대문자로 써야하며, `복사한 API 키`는 앞뒤를 작은따옴표(')로 감싸야 한다.

10) BeagleBone Black의 `/etc/rc.local`의 `exit 0` 명령 바로 위에 아래처럼 추가한다.

```bash
@BBB:$ nano /etc/rc.local
...
(cd /usr/local/tp; ./driver.sh start)         # 추가
(cd /usr/local/tp; ./tp.sh start)             # 추가

exit 0
```

   - 파일 수정 후 저장은 `CTRL-O`키를 누른 후, 엔터키를 누르고, 종료할 때는 `CTRL-X`키를 누른다.

11) **크롬 브라우저**에서 다시 MAC 어드레스를 복사한다.

   - 페이지를 다른 곳으로 이동하여 MAC 어드레스를 복사할 수 없는 경우는 `3. BeagleBone Black 등록`의 방법을 통해 다시 MAC 어드레스를 복사한다.

12) `게이트웨이 등록하기`버튼을 누른다.
![copy_apikey](/assets/copy_apikey_ko.png)

<br/>

13) `게이트웨이 모델`에서 `Neuromeka Rev2.1`을 선택한다.
![select_gwmodel](/assets/select_gwmodel_ko.png)

<br/>

14) `게이트웨이 아이디`에 MAC 어드레스를 붙여넣기 하고 게이트웨이 이름을 입력한다.
![select_gwmodel](/assets/inputmac_name_ko.png)

<br/>

15) `디바이스 모델`에서 `Basic Model Rev2.1`을 선택한다.
![select_devicemodel](/assets/select_devicemodel_ko.png)

<br/>

16) `게이트웨이, 디바이스, 센서 등록 진행` 버튼을 누른다.
![register](/assets/register_ko.png)

<br/>

17) 등록 성공 시 `Success` 팝업 메시지가 화면에 출력된다.

<br>

18) `센서목록` 메뉴에서 등록된 게이트웨이를 확인할 수 있다.

  - 센서는 게이트웨이(BeagelBone Black)에 의해 자동적으로 등록되며, 게이트웨이 등록 후 1분 이내에  최종 등록 완료된다.
  - 센서값은 게이트웨이에서 수집되고 주기적으로 서버에 전송하기 때문에 센서값을 서비스 사이트에서 볼 수 있기까지 몇 분이 소요된다.

<br>
