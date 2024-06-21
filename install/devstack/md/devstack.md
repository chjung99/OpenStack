# 데브스택을 이용해 오픈스택 설치하기

이제 ubuntu server에 ssh로 접속까지 완료한 상태입니다. devstack을 활용해서 openstack을 설치할 수 있습니다. 단, 이는 한계(꺼지면 다시 설치해야 하는 등)가 있으니 주의해야 합니다. 

우선 `git clone`을 통해 devstack을 설치해줍니다. 이때 버전에 주의해야합니다. 저는 아래 명령어를 통해 master branch에 있는 버전을 설치하였으며, 특정 버전을 설치하고 싶은 경우 branch를 따로 clone해야 합니다. 

설치했던 우분투와 openstack 버전을 다시 한번 확인하고 설치합니다. 저는 22.04와 호환이 되는 버전을 설치했습니다.

### 1. stack 유저 생성하기
아래 과정은 "stack"이라는 유저를 만드는 과정으로 선택사항입니다. 하지만 이렇게 하면 유저별로 환경을 가져갈 수 있어서 장점이 있습니다.
```bash
sudo useradd -s /bin/bash -d /opt/stack -m stack

sudo chmod +x /opt/stack

echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack
sudo -u stack -i
```


설정이 완료되면 stack 유저 환경에서 devstack을 설치해줍니다. 

```bash
git clone https://opendev.org/openstack/devstack
```

### 2. local.conf 파일 생성하기
devstack 폴더에 들어가서 local.conf 파일을 만들어 줍니다. 이것은 devstack을 활용해서 openstack을 설치할때 필요한 최소한의 설정입니다. 간단한 비밀번호 설정이며, dashboard에 접근 시 필요한 암호를 설정합니다.

```bash
cd devstack
vim local.conf
```

아래와 같은 내용을 복사 붙여넣기 해주시면됩니다.

```bash
[[local|localrc]]
ADMIN_PASSWORD=secret
DATABASE_PASSWORD=$ADMIN_PASSWORD
RABBIT_PASSWORD=$ADMIN_PASSWORD
SERVICE_PASSWORD=$ADMIN_PASSWORD
```

이후 `./stack.sh & ` 를 실행하여 백그라운드에서 설치를 진행합니다.
```bash
./stack.sh &
```

설치가 완료되면 아래와 같은 화면이 나옵니다. 2-30분 정도 걸립니다.
![](/install/devstack/img/1.png)

ubuntu server ip주소를 통해 openstack 대시보드에 접근할 수 있습니다.
아이디: admin, 비밀번호: local.conf 설정에서 적은 비밀번호로 로그인할 수 있습니다.
![](/install/devstack/img/2.png)

더 자세한 사항은 [Devstack 공식 가이드](https://docs.openstack.org/devstack/latest/)를 참고하세요.