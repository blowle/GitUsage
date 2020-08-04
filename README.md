# git 정리

## git 저장소 생성


​	Command : `git init` > `git add *` > `git commit -m 'Create initial Project'`

## 기존 저장소를 Clone 하기

​	Command :  `git clone https://github.com/~~~~ newDirName`



## 수정하고 저장소에 저장하기

### Working Directory

* 워킹 디렉토리의 모든 파일은 크게 Tracked 와 Untracekd로 구분.
  * Tracked 파일은 이미 스냅샷에 포함돼 있던 파일.
* Tracked (3가지 상태로 구분)
  * Unmodified
  * Modified
  * Staged (커밋으로 저장소에 기록할 상태(before commit))

![파일의 라이프사이클.](https://git-scm.com/book/en/v2/images/lifecycle.png)



### 파일의 상태 확인하기

​	Command : `git status` 

* 현재 branch 와 상태를 보여준다.

예시)

```
$ git status
	On branch master
	Your branch is up-to-date with 'origin/master'.
	nothing to commit, working directory clean
====================================================================
$ echo 'My Project' > README
$ git status
	On branch master
    Your branch is up-to-date with 'origin/master'.
    Untracked files:
      (use "git add <file>..." to include in what will be committed)

        README

    nothing added to commit but untracked files present (use "git add" to track)
====================================================================
$ git add README
====================================================================
$ git status
    On branch master
    Your branch is up-to-date with 'origin/master'.
    Changes to be committed:
      (use "git reset HEAD <file>..." to unstage)

        new file:   README	
====================================================================

```



### Staged와 Unstaged 상태의 변경 내용을 보기

​	Command : `git diff`

* 어떤 내용이 변경됐는지 자세히 확인할 수 있다.
* 수정하고 아직 Stage 하지 않은 것을 보여줌.

## gitignore 파일

​	디렉토리 안에 .gitignore 파일 참조.



## 커밋 히스토리 조회하기



​	Command : `git log`

예시)

```
$ git log
commit cac6b5274795f2e2a3d60173a8f0d780c83fdec6 (HEAD -> master, origin/master)
Author: YongCheol Lee <dydcjf8889@gmail.com>
Date:   Tue Aug 4 23:25:41 2020 +0900

    write staged and unstaged on README

    tracked 상태에 대해 확인 및 변경 내용 보는 방법을 적음

commit ab33a71829123264b0859a54657f3f86d0a42434
Author: YongCheol Lee <dydcjf8889@gmail.com>
Date:   Tue Aug 4 22:43:37 2020 +0900

    Create initial Project
```



## 커밋 되돌리기

### 되돌리기



​	Command : `git commit --amend`

* 한 번 되돌리면 복구 할 수 없기 때문에 주의!!!
* 시점.
  * 너무 일찍 커밋.
  * 어떤 파일 빼먹고 커밋.
  * 메시지 잘못 적었을 때
  * etc......
* 파일 수정 -> staging area에 추가 -> --amend 옵션으로 commit

예시)  2번째 커밋으로 첫번째 커밋을 덮어쓴다.

```
$ git commit -m 'initial commit'
$ git add forgotten_file
$ git commit --amend
```



### 파일 상태를 Unstage로 변경하기

* Staging Area와 워킹 디렉토리 사이.
* 합쳐서 staging 한것을 따로 staging하고 싶을 때.. 등 사용.
  * 아래의 예시를 보면 `git reset HEAD <file> to unstage` comment가 보인다.

예시)

```
$ git add *
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed:    README.md -> README
    modified:   CONTRIBUTING.md
    
-------------------------------------------------------------
$ git reset HEAD CONTRIBUTING.md
Unstaged changes after reset:
M	CONTRIBUTING.md
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed:    README.md -> README

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   CONTRIBUTING.md
```

### Modified 파일 되돌리기

* 수정된 파일을 **최근 커밋된 버전**으로 되돌리는 방법.
* `git checkout -- <file>` 명령어를 사용할 조심해야한다!!!!
  * 수정된 내용이 전부 사라짐!!!!

예시)

```
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   CONTRIBUTING.md
------------------------------------------------------------------
$ git checkout -- CONTRIBUTING.md
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed:    README.md -> README
```



## 리모트 저장소

### 리모트 저장소 확인하기



​	Command : `git remote`

* 현재 프로젝트에 등록된 리모트 저장소를 확인할 수 있다.
  * 리모트 저장소의 단축 이름을 보여준다.

예시)

```
$ git remote -v
origin  https://github.com/blowle/GitUsage.git (fetch)
origin  https://github.com/blowle/GitUsage.git (push)
```



### 리모트 저장소 추가, pull or fetch, push 및 살펴보기



​	Command : `git remote add <단축이름> <url>`

​	Commaned : `git fetch <remote>`

​	Command : `git push <remote 저장소 이름> <브랜치 이름>`

​	Command : `git remote show <리모트 저장소 이름>`



## Git Branch

### 새 브랜치 생성

​	Command : `git branch <브랜치 이름>`

* 브랜치를 생성했을 때, 최근 마지막 커밋을 가리킨다.

예시) testing 이라는 브랜치를 생서했을 때,

## ![한 커밋 히스토리를 가리키는 두 브랜치](https://git-scm.com/book/en/v2/images/two-branches.png)



* Git은 지금 작업중인 브랜치를 `HEAD` 라는 특수한 포인터로 파악한다.
  * 지금 작업하는 로컬 브랜치를 카리킨다.

예시) HEAD의 역할

![현재 작업 중인 브랜치를 가리키는 HEAD](https://git-scm.com/book/en/v2/images/head-to-master.png)



### 브랜치 이동하기



​	Command : `git checkout testing`

