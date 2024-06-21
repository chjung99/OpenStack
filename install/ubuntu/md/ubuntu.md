# Ubuntu 서버 설치하기

### 1. Ubuntu 서버 이미지 다운로드

[Ubuntu 사이트](https://releases.ubuntu.com/jammy/)에 접속하여 설치할 버전의 ubuntu server image를 다운로드 받습니다.
저는 22.04.4 LTS를 설치했습니다. Openstack 버전별로 지원하는 ubuntu 버전이 다르기 때문에 아래 표를 보고 적절한 버전을 설치합니다. 더 자세한 정보는 [ubuntu](!https://ubuntu.com/openstack/docs/supported-versions)와 [devstack](!https://opendev.org/openstack/devstack) 사이트에서 확인 가능합니다


![](/install/ubuntu/img/1.png)

| OPENSTACK        | UBUNTU             | REGULAR SUPPORT EOL | EXTENDED PRO EOL | EXTENDED PRO/ESM EOL |
|------------------|--------------------|---------------------|------------------|----------------------|
| 2023.2 Bobcat    | 22.04 LTS, Jammy   | July, 2024          | n/a              | n/a                  |
| 2023.1 Antelope  | 22.04 LTS, Jammy   | Oct, 2024           | April, 2026      | n/a                  |
| Zed              | 22.04 LTS, Jammy   | April, 2024         | n/a              | n/a                  |
| Yoga             | 22.04 LTS, Jammy   | April, 2027         | n/a              | April, 2032          |
| Yoga             | 20.04 LTS, Focal   | April, 2025         | n/a              | n/a                  |
| Xena             | 20.04 LTS, Focal   | April, 2023         | n/a              | n/a                  |
| Wallaby          | 20.04 LTS, Focal   | Oct, 2022           | April, 2024      | n/a                  |
| Victoria         | 20.04 LTS, Focal   | April, 2022         | n/a              | n/a                  |
| Ussuri           | 20.04 LTS, Focal   | April, 2025         | n/a              | April, 2030          |
| Ussuri           | 18.04 LTS, Bionic  | April, 2023         | n/a              | n/a                  |
| Train            | 18.04 LTS, Bionic  | Feb, 2021           | n/a              | n/a                  |
| Stein            | 18.04 LTS, Bionic  | Oct, 2020           | April, 2022      | n/a                  |
| Rocky            | 18.04 LTS, Bionic  | Feb, 2020           | n/a              | n/a                  |
| Queens           | 18.04 LTS, Bionic  | April, 2023         | n/a              | April, 2028          |
| Queens           | 16.04 LTS, Xenial  | April, 2021         | n/a              | n/a                  |
| Mitaka           | 16.04 LTS, Xenial  | April, 2021         | n/a              | April, 2024          |


### 2. VirtualBox에서의 가상 서버 생성
#### 2.1 VirtualBox를 실행하고 새로만들기를 클릭합니다.
![](/install/ubuntu/img/2.png)
#### 2.2 가상 머신 만들기 창이 열리면 이름(openstack)을 입력하고 다운받았던 ubuntu server image를 선택합니다.
![](/install/ubuntu/img/3.png)
#### 2.3 사용자 이름과 암호 그리고 호스트이름을 입력합니다.
![](/install/ubuntu/img/4.png)
#### 2.4 메모리 크기를 할당합니다. 최소 2GB를 권장하며 충분히 할당하는 것이 좋습니다.
![](/install/ubuntu/img/5.png)
#### 2.5 하드디스크 역시 최소 8GB를 권장하며 충분히 할당하는 것이 좋습니다. 
![](/install/ubuntu/img/6.png)
#### 2.6 모든 설정을 확인하고 완료 버튼을 눌러줍니다.
![](/install/ubuntu/img/7.png)
#### 2.7 가상 머신이 시작됩니다.
![](/install/ubuntu/img/8.png)
#### 2.8 머신이 실행되면 네트워크 설정을 눌러줍니다.
![](/install/ubuntu/img/9.png)
#### 2.9 어뎁터1의 설정을 "어댑터에 브리지"로 변경해줍니다. 이를 통해 public ip를 할당할 수 있습니다.
![](/install/ubuntu/img/10.png)

### 3. Ubuntu 서버 설치

#### 3.1 언어를 선택합니다.
![](/install/ubuntu/img/11.png)
#### 3.2 추가 업데이트 없이 진행합니다.

![](/install/ubuntu/img/12.png)
#### 3.3 키보드 설정 역시 그대로 진행합니다.
![](/install/ubuntu/img/13.png)
#### 3.4 Ubuntu server를 그대로 설정합니다.
![](/install/ubuntu/img/14.png)
#### 3.5 Network 설정부분입니다. 이전에 virtual box에서 제대로 브리지 설정이 되었다면 192.XXX와 같이 public IP가 잡힙니다.
![](/install/ubuntu/img/15.png)
#### 3.6 proxy 설정 없이 진행합니다. 
![](/install/ubuntu/img/16.png)
#### 3.7 이 설정도 없이 넘겨줍니다. 
![](/install/ubuntu/img/17.png)
#### 3.8 disk 사이즈를 확인하고 넘겨줍니다. 
![](/install/ubuntu/img/18.png)
#### 3.9 파일 시스템을 확인하고 넘겨줍니다. 
![](/install/ubuntu/img/19.png)
#### 3.10 진행합니다. 
![](/install/ubuntu/img/20.png)
#### 3.11 ubuntu 서버 계정을 생성합니다. 추후 SSH 접속 시 필요하니 (username, password)를 따로 기억해둡니다. 
![](/install/ubuntu/img/21.png)
#### 3.12 업그레이드 없이 넘어가줍니다. 
![](/install/ubuntu/img/22.png)
#### 3.13 SSH 접속을 사용할 예정이므로 Install OpenSSH server를 선택하고 넘겨줍니다.
![](/install/ubuntu/img/23.png)
#### 3.14 설치가 진행됩니다. 
![](/install/ubuntu/img/24.png)


