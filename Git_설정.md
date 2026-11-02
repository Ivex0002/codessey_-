# Git 설정 및 GitHub 연동

### 이전 사용자 데이터 삭제(보안)
```
PS C:\Users\User> git config --global --list
user.name=--------------
user.email=--------------
PS C:\Users\User> Remove-Item C:\Users\User\.gitconfig
PS C:\Users\User> git config --global --list
fatal: unable to read config file 'C:/Users/User/.gitconfig': No such file or directory
```
- 이전 사용자가 global로 등록하여 보안안전을 위해 모든 계정 정보를 삭제함
- 해당 이름과 이메일은 이 문서에 기입할 필요가 없으므로 자체적으로 숨김처리함

### local 설정으로 git 연동
- 해당 과제의 경우 편의성을 위해 vscode 터미널로 진행함
```
PS C:\Users\User\Documents\mission1_miniproject_git> git init
Initialized empty Git repository in C:/Users/User/Documents/mission1_miniproject_git/.git/
PS C:\Users\User\Documents\mission1_miniproject_git> git add .
PS C:\Users\User\Documents\mission1_miniproject_git> git commit -m "git practice"
Author identity unknown

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'User@DESKTOP-9HA9I8V.(none)')
```
- 현재 로그인이 되어있지 않음을 확인
```
PS C:\Users\User\Documents\mission1_miniproject_git> git config --local user.name "garam"
PS C:\Users\User\Documents\mission1_miniproject_git> git config --local user.email "garam199803@gmail.com"
PS C:\Users\User\Documents\mission1_miniproject_git> git commit -m "git practice"                         
[master (root-commit) 5e80bcc] git practice
 2 files changed, 24 insertions(+)
 create mode 100644 Dockerfile
 create mode 100644 index.html
```
- 이름, 이메일 로컬 등록 후 커밋 완료
```
PS C:\Users\User\Documents\mission1_miniproject_git> git branch -M main
>> git remote add origin https://github.com/Ivex0002/codessey_git_practice.git
>> git push -u origin main
info: please complete authentication in your browser...
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 635 bytes | 635.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/Ivex0002/codessey_git_practice.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```
- 데이터 덮어쓰기 안전을 위해 이전 프로젝트의 폴더 대신 새로운 폴더, 새로운 저장소를 생성하여 연결함
```
PS C:\Users\User\Documents\mission1_miniproject_git> git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=schannel
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=master
core.repositoryformatversion=0
core.filemode=false
core.bare=false
core.logallrefupdates=true
core.symlinks=false
core.ignorecase=true
user.name=garam
user.email=garam199803@gmail.com
remote.origin.url=https://github.com/Ivex0002/codessey_git_practice.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.main.remote=origin
branch.main.merge=refs/heads/main
```
- `user.name=garam`, `user.email=garam199803@gmail.com`으로 기입한 설정이 잘 되었음을 확인
