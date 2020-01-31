
# docker 설치
[Get Docker CE for Centos](https://docs.docker.com/install/linux/docker-ce/centos/)

## 오래된 버전 삭제 ( Uninstall old versions  )
```
yum remove docker \
    docker-client \
    docker-client-latest \
    docker-common \
    docker-latest \
    docker-latest-logrotate \
    docker-logrotate \
    docker-engine
```
- /var/lib/docker 의 이미지,컨테이너, 볼륨, 네트워크는 본존 된다.

## 저장소 설정 ( SET UP THE REPOSITORY )
### 필수 패키지 설치
1. yum-utils, yum-config-manager, device-mapper-persistent-data, lvm2<br>
 ``` 
 yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2 
```

2. stable 버전을 설치하기 위해 저장소 <br>
```
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

## Docker CE 설치 ( INSTALL DOCKER CE )
1. 최신버전 설치<br>
```
yum install docker-ce docker-ce-cli containerd.io
```

2. docker-ce 설치<br>
```
yum install docker-ce-<VERSION_STRING> docker-ce-cli-<VERSION_STRING> containerd.io
```

3. docker 시작<br>
```
systemctl start docker
```

## Docker CE 삭제
```
yum remove docker-ce
rm -rf /var/lib/docker
```

## Docker run 
> docker run `[OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]`

- -d : 데몬 상태로 실행한다는 뜻이다. 이 옵션을 주지 않으면, 실행되는 로그를 바로 보여준다.
- -p : 컨테이너 내부의 포트를 외부로 내보낼 포트로 연결시켜준다.
- -v : 호스트에 볼륨을 지정해 주는 것이다. 굳이 하지 않아도 되지만, 만약 해당 컨테이너가 삭제되면 내부에 작성했던 스크립트 등의 데이터가 다 없어지기 때문에 볼륨을 지정해 외부에 백업하는 용도로 볼륨을 잡았다.
- -u : root 사용자로 실행되게 하기 위해 지정해 줬다.
- --name : 해당 컨테이너의 이름을 지정해준다.

## Docker stop
> docker stop `[container]`

## Docker log
- 로그 보기<br>
>docker logs `[container]`
- 로그 시간과 같이 보기
>docker logs -t `[container]`
- 로그 계속 보기
>docker logs -f `[container]`
- 로그 시간과 같이 계속 보기
>docker logs -tf `[container]`

## Docker log 삭제
>`truncate -s 0 /var/lib/docker/containers/*/*-json.`

## Docker container 에 bash 접속
>`docker exec -it [container] bash`

## Docker container 변경사항 적용
1. 컨테이너의 변경 사항이 없다면.. stop 후 docker run에 -p 옵션을 추가하여 실행하면 될 것이다.

2. 컨테이너의 변경 사항이 있다면 docker commit를 사용해서 변경된 내용이 적용된 컨테이너를 만들어서 -p 옵션으로 재실행한다. 

>`docker stop running_container`

>`docker commit running_container new_container`

>`docker run -p newport:newport new_container`
