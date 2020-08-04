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

## gitignore 파일

​	디렉토리 안에 .gitignore 파일 참조.



