# SSH Client 프로그램으로 인스턴스 접속하기

이제 SSH 접속을 위한 설정을 해보겠습니다.


### 1. Floating IP 연결하기

이제 private 서브넷에서 생성된 VM과 연결할 Floating ip를 생성합니다.

![](/operation/ssh/img/1.png)
![](/operation/ssh/img/2.png)

생성된 Floating ip와 VM을 연결해줍니다.


![](/operation/ssh/img/3.png)

연결이 잘되었으면, 인스턴스 화면에서 IP Address에 추가된 것을 확인 할 수 있습니다.

![](/operation/ssh/img/4.png)



### 2. ping테스트
외부에서 ping 테스트를 진행해서 연결이 되었는 지 확인해줍니다.

먼저 openstack이 설치되어 있는 ubuntu host에서 확인해보면 잘 연결됬음을 확인할 수 있습니다.
![](/operation/ssh/img/5.png)

뿐만 아니라 virtualbox가 설치되어 있는 window host에서도 확인해보면 잘 연결됬음을 확인할 수 있습니다.

![](/operation/ssh/img/6.png)
### 3. SSH 접속
이전에 저장했던 SSH pem key를 바탕으로 vm에 접속할 수 있습니다.

![](/operation/ssh/img/7.png)
![](/operation/ssh/img/8.png)
![](/operation/ssh/img/9.png)
![](/operation/ssh/img/10.png)

`ifconfig`를 통해 확인해보면 현재 10.0.0.9 VM에 접속해있음을 알 수 있습니다.

![](/operation/ssh/img/11.png)
