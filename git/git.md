# git

##  버전 관리란?
“버전 관리” 는 무엇이고 우리는 왜 이것을 알아야 할까? 버전 관리 시스템은 파일 변화를 시간에 따라 기록했다가 나중에 특정 시점의 버전을 다시 꺼내올 수 있는 시스템이다. 이 책에서는 버전 관리하는 예제로 소프트웨어 소스 코드만 보여주지만, 실제로 거의 모든 컴퓨터 파일의 버전을 관리할 수 있다.

## 분산 버전 관리 시스템 (DVCS)

![DVCS](./assets/distributed.png)


## 세가지 상태

![areas](./assets/areas.png)

## 명령어 

```shell 
git init 
```

- `.git directory`를 생성하는 명령어

```shell
git add .
```

- `working directory` 에 있는 파일. 폴더를 `stagin area`에 추가
- add 하기 전엔 파일이 저장이 되었는지 확인하기

```shell
git commit -m 'message'
```

- `staging area` 에 올라간 파일들을 저장

```shell
git remote add origin <remoteurl>
```
- 원격저장소 주소를 `origin` 이라는 별명으로 저장
- 한번 연결 그 이후에는 push 명령어만 사용하여 업로드

```shell
git push origin main 
```

- `main` 브랜치를 `origin` 원격저장소로 업로드 


```shell
git clone <remote url>
```
- 원격 저장소에 있는 레포를 현재 폴더에 폭제 

```shell
git pull origin main
```
- 원격 저장소에 마지막 코드 상태를 다운로드 


### 주의할 점

- 부모 폴더가 git 을 쓰는데 자식 폴더에서는 git init 은 사용하지 말기 충돌이 발생할 수 있음. 그래서 항상 부모 폴더에 위치해있는지 확인하고 거기에서 git 폴더 생성하기. 
- 항상 command + s 로 저장하고 git commit 으로 github 에 업로드하기
- 잔디밭 잘 채우기! 내가 업로드 한 횟수들이 다 기록됨.
- git commit 이메일은 내가 수정을 했다는 도장이 찍히는 것 (github 에 저장된 메일로 하기)      

