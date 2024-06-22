# 네트워크 재설정하기

외부에서도 새로 생성할 인스턴스 VM에 접속할 수 있도록 네트워크를 설정하려고 합니다.
따라서 현재 네트워크 구성을 알아보기 위해, 윈도우에서 `ipconfig`를 통해 공유기의 IP 주소를 파악하고, openstack을 설치한 ubuntu에서 `ifconfig`를 통해 확인해줍니다.

![](/operation/network/img/2.png)
![](/operation/network/img/1.png)

위를 통해 공유기 ip 주소와 어댑터에 대한 정보를 얻어서 다음과 같은 네트워크 구성을 하고자 합니다.

![](/operation/network/img/3.png)


이를 위해 `local.conf`파일을 다음과 같이 수정해주고, `./clean.sh` 해준 후 다시 `./stack.sh` 명령어를 통해 설치해줍니다.

```bash
[[local|localrc]]
ADMIN_PASSWORD=secret
DATABASE_PASSWORD=$ADMIN_PASSWORD
RABBIT_PASSWORD=$ADMIN_PASSWORD
SERVICE_PASSWORD=$ADMIN_PASSWORD

FLAT_INTERFACE=enp0s3
HOST_IP=192.168.0.119
FLOATING_RANGE=192.168.0.128/28
```

재설치가 완료됬으면 openstack에서 아래 명령어를 통해 네트워크 설정을 해줍니다. root권한으로 수정해야하므로, root 계정이 없는 경우 추가해줍니다.

```bash
sudo passwd root
su root

echo 1 > /proc/sys/net/ipv4/conf/enp0s3/proxy_arp
iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE
```

프록시 ARP를 통해 enp0s3 인터페이스가 다른 장치의 ARP 요청에 응답하도록 설정하여 네트워크 세그먼트 간의 통신을 가능하게 합니다.
IP 마스커레이드를 통해 enp0s3 인터페이스를 통해 나가는 트래픽의 출발지 IP 주소를 변경하여 내부 네트워크 장치들이 단일 공인 IP 주소를 통해 외부 네트워크(예: 인터넷)에 접속할 수 있게 합니다.
