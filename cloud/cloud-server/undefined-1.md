# 접속방법

KADaP 클라우드는 고성능 서버들의 집합으로 이루어져 있습니다. 악의적 사용자의 공격 및 사용을 막기 위하여 사전 허가된 기관(자동차 산업 관련 기업 및 대학 연구소)에만 접속이 가능합니다.&#x20;

접속 방법은 크게 2가지 방법이 있습니다.&#x20;

* 기관 IP 주소 등록  : 해당기관 및 사용자의P주소를 등록하여 접속 가능합니다.&#x20;
* VPN을 이용한 접속 : KADaP에서 제공되는 VPN툴을 설치 하여 접속 후 사용 가능합니다.&#x20;

{% hint style="info" %}
기관내 접속 예정자 수가 **30명 이상**일경우 기관 IP 주소 등록 방법을 추천하며, **30명 미만**일 경우 **VPN접속**을 추천 합니다.&#x20;
{% endhint %}

## 1. 기관 IP 주소 등록 신청 방법&#x20;

1. 신청서(링크)를 작성 후 KADaP 관리자(admin@bigdata-car.kr)로 전달 주세요.&#x20;
2. 심사  후IP 등록 완료 이메일 수신  후 다음 두개 주소 중 하나로 접속 진행&#x20;
   1. CMP-UI(일반 사용자용) : https://cloud.bigdata-car.kr
   2. Horizon-UI(고급 사용자용) : https://horizon.bigdata-car.kr

## 2. VPN을 이용하여 접속 하는 방법&#x20;

1. 신청서(링크)를 작성 후 KADaP 관리자(admin@bigdata-car.kr)로 전달 주세요.&#x20;
2. 심사 후 접속 ID와 비밀번호가 보내주신 이멜일로 전송 됩니다.&#x20;
3. VPN 프로그램 다운로드 : https://bigdata-car.kr:2443
4. VPN 프로그램 실행 후 접속할 서버 설정(최초 1회)&#x20;
   1. VPN 서버 이름 : KADaP Cloud
   2. VPN 서버 IP : bigdata-car.kr
   3. 포트 : 3443
5. 접속 실행 : \[2]번 단계에서 받은 ID와 비빌번호를 입력하여 VPN접속 진행&#x20;
6. 접속 완료 메시지 확인 후 다음 두개 주소 중 하나로 접속 진행&#x20;
   1. CMP-UI(일반 사용자용) : https://cloud.bigdata-car.kr
   2. Horizon-UI(고급 사용자용) : https://horizon.bigdata-car.kr

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

## \[참고] Horizon-UI  : 고급 사용자용&#x20;

KADaP 클라우드는 [OpenStack](https://www.openstack.org/) 이라는 오픈소스 클라우드 컴퓨팅 플랫폼을 기반으로 구축되어 있습니다. Horizion은 Openstack에서 기본 제공하는 사용자 웹 인터페이스 입니다.&#x20;

Openstack을 세밀하게 조정하여 목적에 맞는 시스템을 구성 할 수 있는 장점이 있지만, 많은 기능들과 용어로 인하여 익숙해 지는데 시간이 소요 됩니다.&#x20;

웹 인터페이스  역시 기능 제공에 초점을 두고 있어 사용자 친밀도는 약합니다.&#x20;

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

## \[참고] CMP-UI : 일반 사용자용

Horizon UI의 많은 기능들로 인하여 접근성이 어려운 단점 보완하여 일반사용자들이 사용하는 기능을 중심으로 쉽게 사용할수 있도록 자체 개발한 사용자 웹 인터페이스 입니다.

Openstack의 API를 기반으로 개발되어 있어 추가 설정이 필요한 부분은 오픈스택 CLI나Horizon UI로 접속하여 설정을 유지 할  수 있습니다.&#x20;

Horizon UI에서는 제공하지 않지만, KADaP에 필요한 추가 기능을 발굴 하여 개발 적용할 예정입니다. (eg. 컨테이너 관리 및 운영 환경)&#x20;





> 일반적으로 CMP는 Cloud Management Platform의 약어이지만, KADaP CMP는 클라우드 포털의 역할만을 수행하고 있어 Cloud Management Potal을 약어로 사용하고 있음





