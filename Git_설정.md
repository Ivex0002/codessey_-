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
