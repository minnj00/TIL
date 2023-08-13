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



# BRANCH

## Branch는 무엇인가?

![branch](./assets/branch.png)
- 독립적으로 작업을 진행하기 위한 개념
- `master branch`란 모든 `repository`의 기본 혹은 메인
- `master branch`로부터 파생된 다른 `branch`들로부터 수정 사항을 만든 다음 `master`에 병합하는 과정을 거침

## Branch 생성
1. `git branch <branch name>`로 Branch 생성
2. `git branch`로 현재 위치한 Branch 확인
3. `git switch <branch name>`으로 원하는 Branch로 이동
4. `git push origin <branch name>`으로 Repository에 branch 생성 
5. `Pull requests`로 branch 내용 master로 합병 가능

- `merge`가 된 branch는  delete하는 것이 일반적


# HOW TO SHARE

## want to invite
1. `Repository` 생성
2. Setting - Collaborators - Add People

## clone으로 내려받기
1. `Repository` code copy
2. open `terminal`
3. write
```shell
git clone <remote url>
```
4. `code`에서 열기

- 수정 후 add - commit - push 일련의 과정 실행


# HOW TO PULL REQUEST

## Forking

1. `Fork` 하고 싶은 `Repository` 확인
2. 오른쪽 상단 `Fork` 선택 - `Create Fork`


## clone git
1. `clone` 으로 내려받는 과정 실행
- 자신의 repo로 생성되었는지 확인 후 자신의 repo code로 실행

## pull request
1. `Repository` 상단 `Pull requests` 선택
2. `New pull requeset` 선택
3. ← 화살표 좌측은 pull 할 대상의 repo
화살표 우측은 자신의 repo로 설정한 뒤 pull

- 이후 합병을 진행하고 싶으면 `merge`를 통해 합병을 진행

## git push 용량이 큰 파일을 삭제했는데도 실패할 때

- Git은 프로젝트의 히스토리를 저장하기 때문에 로컬에서 큰 용량의 파일을 삭제했다고 해도 히스토리에 해당 파일의 복사본을 가지고 있다. 즉, 원격 저장소와 로컬 저장소의 히스토리가 동일해야 받아들여지기 때문에 히스토리를 비워주어야 한다.

- 해결방법 
    - 로컬에서 해당 파일을 삭제한다.
    - 삭제한 결과를 커밋한다.

    - `it reset --soft HEAD~N` 으로 N개의 커밋이 있다면 해당 커밋을 취소한다.
    - `git commit -sm "message"` 로 다시 커밋한다. (이 작업을 Squash 라고 한다.)
    - Squash 된 커밋을 다시 push 한다.


