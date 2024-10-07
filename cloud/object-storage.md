# Object Storage 활용하기

## Object Stroage란?





## KADaP Cloud Object Strage 접속 하기&#x20;

{% hint style="info" %}
관리자(admin@bigdata-car.kr)에게 사전 신청 후 사용 가능합니다.&#x20;
{% endhint %}

### 1. 접속 프로그램 다운로드 받기&#x20;

Object Strage를 지원하는 여러 SW 툴 중에서 S3 Browser를 추천 합니다.&#x20;

<figure><img src="../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>

### 2. 접속 설정 하기&#x20;

<figure><img src="../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>

1. Display name : 희망 하는 이름을 기입 합니다.&#x20;
2. Account type : S3 Compatible Stroage 를 선택 합니다.&#x20;
3. REST Endpoint : s3.bigdata-car.kr:8085 를 입력 합니다. (https// 없음)
4. Access Key ID : 관리자에게 전달받은 값을 입력 합니다.&#x20;
5. Secrete Access Key : 관리자에게 전달받은 값을 입력 합니다.&#x20;
6. Use secure transfer(SSL/TLS) : 지원 하지 않으므로 체크 해제 합니다.&#x20;
7. advanced setting.. :  \[Signature version] 설정을 위해 선택 합니다.&#x20;

<figure><img src="../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>

8. Signature version: Signature V4를 선택 합니다.&#x20;

