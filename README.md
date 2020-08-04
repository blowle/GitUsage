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





