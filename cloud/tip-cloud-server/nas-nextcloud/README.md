# 팀 NAS 서버 만들기 (NextCloud)

## NextCloud란&#x20;





## 설치 방법&#x20;

> 자동차 산업 클라우드 ubuntu 22.04\_agent02 이미지로 테스트 되었습니다.&#x20;

```sh
curl -fsSL get.docker.com -o get-docker.sh | sh ./get-docker.sh


apt install fontconfig -y 
fc-cache -fv

------ Shell scripts ------------------------------------------

root@nextcloud:~# mkdir ~/nextcloud
root@nextcloud:~# cd nextcloud
root@nextcloud:~# touch docker-compose.yaml

------ docker-compose.yaml ------------------------------

version: '3'

services:
  nextclouddb:
    image: mariadb
    container_name: nextcloud-db
    restart: unless-stopped
    command: --transaction-isolation=READ-COMMITTED --binlog-format=ROW
    networks:
      - ncloud-net
    volumes:
      - ./db:/var/lib/mysql
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Asia/Seoul
      - MYSQL_RANDOM_ROOT_PASSWORD=true
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextclouduser
      - MYSQL_PASSWORD=nextcloudpw

  redis:
    image: redis
    container_name: redis
    networks:
      - ncloud-net

  nextcloud:
    image: nextcloud:latest
    container_name: nextcloud
    restart: unless-stopped
    ports:
      - 3000:80
    networks:
      - ncloud-net
    volumes:
      - ./web:/var/www/html
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Asia/Seoul
      - MYSQL_HOST=nextclouddb
      - MYSQL_PASSWORD=nextcloudpw
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextclouduser
      - REDIS_HOST=redis
    depends_on:
      - nextclouddb
      - redis

networks:
  ncloud-net:
    name: ncloud-net
    driver: bridge

volumes:
  nextclouddb:
  nextcloud:

------ Shell scripts ------------------------------------------

root@nextcloud:~# cd /root/nextcloud
root@nextcloud:~# docker compose up -d

------ Connection ------------------------------------------

http://<IP address>:3000
```



## 관리자 설정 하기&#x20;

<figure><img src="../../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

1. 최초 접속시 관리자 계정 생성 후 \[설치]를 진행 하여야 합니다.&#x20;
2. 설치 단계에서 추천 앱을 설치 하거나 \[건너뛰기]로 생략 할 수 있습니다.&#x20;
3. 설치 완료 후 우측 상단 프로필 아이콘(A)를 선택시 관리자 설정을 진행 할 수 있습니다.&#x20;

{% hint style="info" %}
KADaP Cloud에서 제공 하는 이미지에서는 admin / kadap1234 로 사전 설정 되어 있습니다.&#x20;
{% endhint %}





## FTP로 파일 업로드 후 NextCloud에 반영하기&#x20;



{% hint style="info" %}
```sh
sudo docker exec -ti --user www-data nextcloud /var/www/html/occ files:scan --all
```
{% endhint %}





