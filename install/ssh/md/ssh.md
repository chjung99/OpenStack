# SSH Client 프로그램을 이용한 우분투 서버 접속

### 1. 서버 IP 정보확인을 위한 패키지를 설치합니다.

```
sudo apt install net-tools
```

![](/install/ssh/img/1.png)

### 2. 서버 IP 정보를 확인합니다.
```
ifconfig
```
enp0s3의 inet 주소(192.xxx.xxx.xxx)를 복사해둡니다.

![](/install/ssh/img/2.png)

### 3. SSH Client 프로그램을 실행합니다.

저는 [Xshell](https://www.netsarang.com/ko/xshell-download/)을 사용했습니다. 연결을 눌러 호스트에 복사해둔 ip주소를 입력하고, 사용자 인증을 눌러 이전에 적어두었던 ubuntu 계정 정보(username, password)를 입력합니다.

![](/install/ssh/img/3.png)
![](/install/ssh/img/4.png)

### 4. SSH 접속

정상적으로 접속하면 아래와 같이 SSH 프로그램을 통해 ubuntu 서버에 접속할 수 있습니다.
![](/install/ssh/img/5.png)