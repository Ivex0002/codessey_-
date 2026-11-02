```
PS C:\Users\User> docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

```
PS C:\Users\User> docker run -it ubuntu bash
root@5fa0743d979e:/# ls -al
total 60
drwxr-xr-x   1 root root 4096 Nov  2 01:48 .
drwxr-xr-x   1 root root 4096 Nov  2 01:48 ..
-rwxr-xr-x   1 root root    0 Nov  2 01:48 .dockerenv
drwxr-xr-x   2 root root 4096 Oct 25 10:26 .rock
lrwxrwxrwx   1 root root    7 Apr 20  2026 bin -> usr/bin
drwxr-xr-x   2 root root 4096 Apr 20  2026 boot
drwxr-xr-x   5 root root  360 Nov  2 01:48 dev
drwxr-xr-x   1 root root 4096 Nov  2 01:48 etc
drwxr-xr-x   3 root root 4096 Oct 25 10:26 home
lrwxrwxrwx   1 root root    7 Apr 20  2026 lib -> usr/lib
lrwxrwxrwx   1 root root    9 Apr 20  2026 lib64 -> usr/lib64
drwxr-xr-x   2 root root 4096 Oct 25 10:25 media
drwxr-xr-x   2 root root 4096 Oct 25 10:25 mnt
drwxr-xr-x   2 root root 4096 Oct 25 10:25 opt
dr-xr-xr-x 219 root root    0 Nov  2 01:48 proc
drwx------   2 root root 4096 Oct 25 10:26 root
drwxr-xr-x   4 root root 4096 Oct 25 10:26 run
lrwxrwxrwx   1 root root    8 Apr 20  2026 sbin -> usr/sbin
drwxr-xr-x   2 root root 4096 Oct 25 10:25 srv
dr-xr-xr-x  12 root root    0 Nov  2 01:48 sys
drwxrwxrwt   2 root root 4096 Oct 25 10:25 tmp
drwxr-xr-x  12 root root 4096 Oct 25 10:24 usr
drwxr-xr-x  11 root root 4096 Oct 25 10:26 var
root@5fa0743d979e:/# echo "Hello, this is Ubuntu container!"
Hello, this is Ubuntu container!
root@5fa0743d979e:/# exit
exit
```

### 컨테이너 종료/유지(attach/exec 등)의 차이 실험
- 컨테이너 백그라운드 실행
```
PS C:\Users\User> docker run -d --name my-ubuntu ubuntu sleep infinity
1ea335e742e0d642689ff670b1725efc909fca62ec72dabf839a007dc6dae859
```

- 실험 1 : docker exec
```
PS C:\Users\User> docker exec -it my-ubuntu bash
root@1ea335e742e0:/# exit
exit

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug my-ubuntu
    Learn more at https://docs.docker.com/go/debug-cli/
PS C:\Users\User> docker ps
CONTAINER ID   IMAGE     COMMAND            CREATED         STATUS         PORTS     NAMES
1ea335e742e0   ubuntu    "sleep infinity"   5 minutes ago   Up 5 minutes             my-ubuntu
```

- 실험 2 : docker attach
- 비고 : 본래 attach 상태에서 컨테이너를 종료하지 않고 빠져나오려면 기본적으로 `Ctrl + P`, `Ctrl + Q`를 사용하나,
노트북 환경에서 해당 커맨드가 먹지 않는 문제가 발생하여 ctrl+c로 강제 종료 처리함 
```
PS C:\Users\User> docker attach my-ubuntu

got 3 SIGTERM/SIGINTs, forcefully exiting
PS C:\Users\User> ^C
PS C:\Users\User> docker ps
CONTAINER ID   IMAGE     COMMAND            CREATED         STATUS         PORTS     NAMES
1ea335e742e0   ubuntu    "sleep infinity"   8 minutes ago   Up 8 minutes             my-ubuntu
```

### 비교표
|명령어|역할|bash 새로 생성 여부|나가면 컨테이너 영향|
| --- | --- | --- | --- |
|exec|실행 중인 컨테이너 안에 새 명령 실행|O|`exit`해도 컨테이너 유지|
|attach|컨테이너의 메인 프로세스에 연결|X|메인 프로세스 종료 시 컨테이너 종료 가능|
