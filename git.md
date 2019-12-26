# Git

> Git은 분산버전관리시스템(DVCS)이다.
>
> 소스코드의 버전 및 이력을 관리할 수 있다.

## 준비하기

윈도우에서 git을 활용하기 위해서 [git bash](https://gitforwindows.org)를 설치한다.

git을 활용하기 위해서 GUI툴인 `source tree` , `github` `desktop` 등을 활용할 수도 있다.

초기 설치를 완료한 이후에 컴퓨터에 `author` 정보를 입력한다.

```bash
$ git config --global user.name ys21-loka
$ git config --global user.email tlgus1995@gmail.com
```

## 로컬 저장소(repository) 활용하기

### 1. 저장소 초기화

```bash
$ git init
Initialized empty Git repository in C:/Users/student/Desktop/TIL/.git/
```

* `.git` 폴더가 생성되며, 여기에 git과 관련된 모든 정보가 저장된다.
* git bashdp `(master)` 라고 표현된느데, 이는 `master` 브랜치에 있다는 뜻이다.

### 2. `add`

`working directory`, 즉 작업공간에서 변경된 사항을 이력으로 저장하기 위해서는 반드시 `staging area`를 거쳐야한다. 

```bash
$ git add markdown.md # 특정 파일
$ git add images/ # 특정 폴더
$ git add . # 현재 디렉토리
```

* `add` 전 상태

  ```bash
  $ git status
  On branch master
  
  No commits yet
  
  Untracked files: # 트래킹 되고 있지 않는 파일들 => commit 이력에 한번도 담기지 않은 파일들
  #committed 될 공간(staging area)에 넣으려면 add 명령어 사용
    (use "git add <file>..." to include in what will be committed)
          git.md
          images/
          markdown.md
  #아직 commit 될 것은 없으나 untracked files 존재
  nothing added to commit but untracked files present (use "git add" to track)
  ```

* `add` 후 상태

  ```bash
  $ git status
  On branch master
  
  No commits yet
  # commit 될 변화들(changes to be committed)
  # => staging area에 있는 파일들
  Changes to be committed:
    (use "git rm --cached <file>..." to unstage)
          new file:   images/1.png
          new file:   images/image-20191226134350644.png
  
  Untracked files:
    (use "git add <file>..." to include in what will be committed)
          git.md
          markdown.md
  ```

### 3. `commit`

  `commit` 은 이력을 확정짓는 명령어로, 해당 시점의 스냅샷을 기록한다.

  `commit` 시에는 반드시 메세지를 작성해야 하며, 메세지는 변경사항을 알 수 있도록 명확하게 작성한다.

  ```bash
  $ git commit -m '마크다운 및 git 정리'
  [master (root-commit) 52dca26] 마크다운 및 git 정리
   4 files changed, 148 insertions(+)
   create mode 100644 git.md
   create mode 100644 images/1.png
   create mode 100644 images/image-20191226134350644.png
   create mode 100644 markdown.md
  ```

  `commit`이후에는 아래의 명령어를 통해 지금까지 작성된 이력을 확인하자.

  ```bash
  $ git log
  commit 52dca269502f11c6575948c6a31fee3a60e117d9 (HEAD -> master)
  Author: ys21-loka <tlgus1995@gmail.com>
  Date:   Thu Dec 26 14:37:25 2019 +0900
  
      마크다운 및 git 정리
  $ git log --oneline
  52dca26 (HEAD -> master) 마크다운 및 git 정리
  $ git log -1
  ```

  `commit`은 해시코드를 바탕으로 구분된다.

  

  ## 원격 저장소 (remote repository) 활용하기

  원격 저장소 기능을 제공하는 다양한 서비스 중에 github을 기준으로 설명한다.

  ### 0. 준비사항

  * Github에 repository 생성

  ### 1. 원격 저장소 등록

  ```bash
  $ git remote add origin 깃허브url
  ```

  * 원격저장소(remote)로 `origin` 이라는 이름으로 `깃허브url`을 등록(`add`)한다.
  
  * 등록된 원격 저장소 목록을 보기 위해서는 다음의 명령어를 사용한다.
  
    ```bash
    $ git remote -v
    origin  https://github.com/ys21-loka/til.git (fetch)
    origin  https://github.com/ys21-loka/til.git (push)
    ```

### 2. `push` - 원격저장소 업로드

```bash
$ git push origin master
Everything up-to-date
```

`origin` 으로 설정된 원격저장소에 `master`브랜치로 업로드(`push`)

이후 변경사항이 생길 때마다, `add`-`commit`-`push` 를 반복하면 된다.

그리고, 항상 모든 명령어 이후에 연관된 상태를 확인하자.

`status`, `log`, `remote -v`

