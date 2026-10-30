# 미션1 - 내 컴퓨터에 개발자용 '작업실' 꾸미기

## 프로젝트 개요
### 기본 작업 환경 꾸리기
- 현재 작업 중인 기기의 실행 환경 조사
- Docker, 터미널 등 기본적인 작업도구 설치 및 실행
- 이를 위한 검증 방식 첨부
- 문제 해결을 위해 어떤 방식을 사용했는지(트러블 슈팅)

## 1) 실행 환경
|OS|쉘|Docker 버전|Git 버전|
| --- | --- | --- | --- |
|window11pro, 26H2|PowerShell|||
|||||

// 붙여넣기용
```PowerShell
```
## 2) 수행 체크리스트
- [x] 터미널 기본 조작 및 폴더 구성
```PowerShell
PS C:\Users\User> pwd

Path
----
C:\Users\User
```
```PowerShell
PS C:\Users\User> cd Documents
PS C:\Users\User\Documents>
```
```PowerShell
PS C:\Users\User\Documents> ls -force


    디렉터리: C:\Users\User\Documents


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2026-10-29   오후 8:12                dev
d--hsl      2026-10-14   오후 5:41                My Music
d--hsl      2026-10-14   오후 5:41                My Pictures
d--hsl      2026-10-14   오후 5:41                My Videos
-a-hs-      2026-10-14   오후 5:43            402 desktop.ini
```
```PowerShell
PS C:\Users\User\Documents> mkdir aaa


    디렉터리: C:\Users\User\Documents


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2026-10-30   오후 3:06                aaa
```
```PowerShell
PS C:\Users\User\Documents> cp aaa bbb
PS C:\Users\User\Documents> ls


    디렉터리: C:\Users\User\Documents


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2026-10-30   오후 3:06                aaa
d-----      2026-10-30   오후 3:08                bbb
d-----      2026-10-29   오후 8:12                dev
```
```PowerShell
PS C:\Users\User\Documents> mv bbb aaa
PS C:\Users\User\Documents> cd aaa
PS C:\Users\User\Documents\aaa> ls


    디렉터리: C:\Users\User\Documents\aaa


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2026-10-30   오후 3:08                bbb
```
```PowerShell
PS C:\Users\User\Documents\aaa> mv bbb ccc
PS C:\Users\User\Documents\aaa> ls


    디렉터리: C:\Users\User\Documents\aaa


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2026-10-30   오후 3:08                ccc
```
```PowerShell
PS C:\Users\User\Documents\aaa> rm ccc -Recurse
PS C:\Users\User\Documents\aaa> ls
PS C:\Users\User\Documents\aaa>
```
```PowerShell
PS C:\Users\User\Documents\aaa> ni abcd.txt


    디렉터리: C:\Users\User\Documents\aaa


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2026-10-30   오후 3:14              0 abcd.txt

```
```PowerShell
PS C:\Users\User\Documents\aaa> echo "dcba" >> abcd.txt
PS C:\Users\User\Documents\aaa> cat abcd.txt
dcba
```
- [] 권한 변경 실습
- [] Docker 설치/점검
```PowerShell
```
- [] hello-world 실행
- [] Dockerfile 빌드/실행
- [] 포트 매핑 접속(2회)
- [] 바인드 마운트 반영
- [] 볼륨 영속성
- [] Git 설정 + VSCode GitHub 연동

## 검증 방법(어떤 명령으로 무엇을 확인했는지) + 결과 위치 링크
