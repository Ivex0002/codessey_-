# Dockerfile 기반 커스텀 이미지 제작
[도커파일 미니 프로젝트](mission1_miniproject_docker/)

### 1) 선택한 베이스 이미지
- 베이스 이미지: `ubuntu:latest`
- 선택 이유:
  - 리눅스 환경을 직접 구성해 볼 수 있음
  - 패키지 설치, 환경변수, 사용자 생성 등을 실습하기 좋음
 
### 2) 적용한 커스텀 포인트

| 커스텀 포인트 | 목적 |
|---|---|
| `ENV APP_NAME=mission1_miniproject_docker` | 환경변수 사용 연습 |
| `WORKDIR /app` | 작업 경로 고정 |
| `COPY app.sh /app/app.sh` | 실행 파일 포함 |
| `RUN apt-get install -y curl` | 패키지 설치 실습 |
| `RUN chmod +x /app/app.sh` | 실행 권한 부여 |
| `CMD ["/app/app.sh"]` | 시작 명령 지정 |

## 빌드 로그
```
PS C:\Users\User\Documents\mission1_miniproject_docker> docker build -t my-ubuntu-app .
[+] Building 20.0s (9/9) FINISHED                                                                  docker:desktop-linux
 => [internal] load build definition from Dockerfile                                                               0.0s
 => => transferring dockerfile: 422B                                                                               0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                   0.1s
 => [internal] load .dockerignore                                                                                  0.0s
 => => transferring context: 2B                                                                                    0.0s
 => [1/4] FROM docker.io/library/ubuntu:latest@sha256:6a06111c3b0a8600feadb270aec771dc239bf407b25625f93f44ab00e11  1.3s
 => => resolve docker.io/library/ubuntu:latest@sha256:6a06111c3b0a8600feadb270aec771dc239bf407b25625f93f44ab00e11  0.0s
 => => extracting sha256:edafa32f5d9e4d9629f0dbc6c01e63c79ff08133c01cfb7d3363aa8bd8a614cf                          1.2s
 => => extracting sha256:f3f25b84a7d74315d94ee4108231f8f5e0cd2a44725a7204d5dd6ce91c151697                          0.0s
 => [internal] load build context                                                                                  0.0s
 => => transferring context: 148B                                                                                  0.0s
 => [2/4] WORKDIR /app                                                                                             0.2s
 => [3/4] COPY app.sh /app/app.sh                                                                                  0.0s
 => [4/4] RUN apt-get update &&     apt-get install -y curl &&     chmod +x /app/app.sh &&     useradd -m appuse  17.1s
 => exporting to image                                                                                             1.1s
 => => exporting layers                                                                                            0.7s
 => => exporting manifest sha256:6bfab159760be83605406d5264bb88eac81c7772e7062f31515fa0cfd6ca3d21                  0.0s
 => => exporting config sha256:df408b091151b3855b5cf97f7ab7a9538831654f4e71897f75d520d0719de497                    0.0s
 => => exporting attestation manifest sha256:7299e5b78c9e3bff3a69c8a90c118f7b024b63111407277d60fffe908d0f8dd6      0.0s
 => => exporting manifest list sha256:b4bbcd9a771920deb2a4ce3c1b47525e644375d70b73c15cde7a342267f31a32             0.0s
 => => naming to docker.io/library/my-ubuntu-app:latest                                                            0.0s
 => => unpacking to docker.io/library/my-ubuntu-app:latest 
```

## 실행 로그
```
PS C:\Users\User\Documents\mission1_miniproject_docker> docker run -d --name my-app my-ubuntu-app
fe33ca984ee78a6d3c66a404e168df64e4c80314518bbab494a255d71a1ac05c
PS C:\Users\User\Documents\mission1_miniproject_docker> docker ps
CONTAINER ID   IMAGE           COMMAND         CREATED          STATUS                             PORTS     NAMES
fe33ca984ee7   my-ubuntu-app   "/app/app.sh"   12 seconds ago   Up 11 seconds (health: starting)             my-app
PS C:\Users\User\Documents\mission1_miniproject_docker> docker logs my-app
Container started
APP_NAME: mission1_miniproject_docker
Running...
Running...
Running...
PS C:\Users\User\Documents\mission1_miniproject_docker> docker exec -it my-app bash
appuser@fe33ca984ee7:/app$ whoami
pwd
echo $APP_NAME
curl --version
appuser
/app
mission1_miniproject_docker
curl 8.18.0 (x86_64-pc-linux-gnu) libcurl/8.18.0 OpenSSL/3.5.5 zlib/1.3.1 brotli/1.2.0 zstd/1.5.7 libidn2/2.3.8 libpsl/0.21.2 libssh2/1.11.1 nghttp2/1.68.0 librtmp/2.3 mit-krb5/1.22.1 OpenLDAP/2.6.10
Release-Date: 2026-01-07, security patched: 8.18.0-1ubuntu2.8
Protocols: dict file ftp ftps gopher gophers http https imap imaps ipfs ipns ldap ldaps mqtt pop3 pop3s rtmp rtsp scp sftp smb smbs smtp smtps telnet tftp ws wss
Features: alt-svc AsynchDNS brotli GSS-API HSTS HTTP2 HTTPS-proxy IDN IPv6 Kerberos Largefile libz NTLM PSL SPNEGO SSL threadsafe TLS-SRP UnixSockets zstd
```

## 종료 및 컨테이너 정리
```
appuser@fe33ca984ee7:/app$ exit
exit

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug my-app
    Learn more at https://docs.docker.com/go/debug-cli/
PS C:\Users\User\Documents\mission1_miniproject_docker> docker ps
CONTAINER ID   IMAGE           COMMAND         CREATED         STATUS                   PORTS     NAMES
fe33ca984ee7   my-ubuntu-app   "/app/app.sh"   3 minutes ago   Up 3 minutes (healthy)             my-app
PS C:\Users\User\Documents\mission1_miniproject_docker> docker rm -f my-app
my-app
PS C:\Users\User\Documents\mission1_miniproject_docker> docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
