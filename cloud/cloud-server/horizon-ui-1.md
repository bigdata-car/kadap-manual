# (Horizon-UI) 가상서버 생성











## \[참고] VM 생성 후 유용한 설정

### 관리자 계정 생성 및 Password로 ssh 접속 설정&#x20;



```bash
# ubunntu 계정 & Key파일로 접속후 

$ sudo passwd #root 비번생성 
$ sudo adduser katech #관리가 계정 생성 
$ usermod -aG sudo katech  #katech으로 sudo 실행 가능 하도록 설정
$ sudo vi /etc/ssh/sshd_config  #Password로 ssh 접속 가능하도록 설정 
    """
    PasswordAuthentication no -> yes
    """
$ sudo service ssh restart
```

