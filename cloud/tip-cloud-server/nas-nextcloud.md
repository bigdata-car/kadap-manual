# 팀 NAS 서버 만들기 (NextCloud)

## NextCloud란&#x20;





## 설치 방법&#x20;

> 자동차 산업 클라우드 내 ubuntu 22.04\_agent02 이미지상에서 테스트 되었습니다.&#x20;

```sh
curl -fsSL get.docker.com -o get-docker.sh

apt install fontconfig
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





## FTP로 파일 업로드 후 NextCloud에 반영하기&#x20;

넥스트클라우드는 추가(업로드) 및 삭제된 파일을 자체 DB에 저장 하고 있습니다.&#x20;

Web 으로 파일을 업로드 하거나, Web에서 삭제시에는 자동으로 DB에 저장 되지만 외부 툴(eg. FTP)를 통해서 업로드한 파일은 넥트스클라우드에서 인식 할 수 없어 보이지 않습니다.&#x20;

이 경우 다음 명령어를 통해 DB에 수동 입력 할 수 있습니다.&#x20;

{% hint style="info" %}
<pre class="language-sh"><code class="lang-sh"><strong>sudo docker exec -ti --user www-data nextcloud /var/www/html/occ files:scan --all
</strong></code></pre>
{% endhint %}




