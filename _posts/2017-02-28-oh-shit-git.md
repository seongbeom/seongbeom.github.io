---
layout: post
title: Git 기초 문제 해결
published: true
---

Git 사용시 겪는 기초적인 문제들 해결 명령어.  
가끔씩 기억이 안나기에. 계속 추가.

\* 참고  
[Oh shit, git!](http://ohshitgit.com/)  
[Git Tutorial: 10 Common Git Problems and How to Fix Them](https://www.codementor.io/git/tutorial/10-common-git-problems-fix)
 
___


* [커밋 취소하기](#time-machine)
* [로컬 파일 변경 취소하기](#cancel-local-change)
* [이전 커밋에 추가하기](#add-to-last)
* [마지막 커밋 메세지 변경하기](#stupid-commit-message)
* [로컬 파일 유지하며 Git에서만 삭제하기](#remove-in-git)
* [푸쉬된 커밋 복귀하기](#revert)
* [새 브랜치 대신 마스터 브랜치에 잘못 커밋했을 경우](#wrong-to-master)
* [다른 브랜치에 잘못 커밋했을 경우](#to-wrong-branch)
* [Untracked 파일들 삭제하기](#delete-untracked-file)
* [그냥 포기](#give-up)

___

### 커밋 취소하기
{: #time-machine}

```bash
git reflog
# git에서 작업한 모든 내역을 볼 수 있음
# 각각의 작업은 인덱스를 가지고 있음 HEAD@{index}

git reset HEAD^ # 최종 커밋 취소
git reset HEAD@{index} # 특정 인덱스로의 복귀
git reset HEAD~2  # 마지막 2개 커밋 취소, 변경은 유지
git reset --hard HEAD~2 # 마지막 2개 커밋 취소, 변경도 폐기
```

### 로컬 파일 변경 취소하기
{: #cancel-local-change}

```bash
git checkout -- Gemfile  
git checkout -- lib bin  # 다중 인자   
git checkout -f # HEAD로 모두 원복
```

### 이전 커밋에 추가하기
{: #add-to-last}

```bash
git add .
git commit --amend 
# 커밋 메세지를 유지 또는 변경할 수 있다
```

새로운 커밋 후 `rebase -i` 를 통해서도 가능하지만, 위의 방법이 훨씬 빠르다.

### 마지막 커밋 메세지 변경하기
{: #stupid-commit-message}

```bash
git commit --amend
git commit --amend -m "New message" # 바로 변경
```

### 로컬 파일 유지하며 git에서만 삭제하기
{: #remove-in-git}

`git rm` 시 로컬과 스테이징 영역에서 모두 삭제되기에 아래와 같이 사용.

```bash
git reset filename  # 또는 git rm --cached filename
echo filename >> .gitingore # 다시 add 되는걸 피하기 위해 .gitignore에 추가  
```

### 푸쉬된 커밋 복귀하기
{: #revert}

```bash
git revert c761f5c              # 특정 ID
git revert HEAD^                # 마지막 이전
git revert develop~4..develop~2 # 범위
```

추가적인 revert 커밋 생성을 원하지 않는 경우 `--no-commit/-n` 옵션을 사용하면 된다.

```bash
# 마지막 커밋을 취소, 그러나 revert 커밋을 생성하지 않는다.
git revert -n HEAD
```


### 새 브랜치 대신 마스터 브랜치에 잘못 커밋했을 경우
{: #wrong-to-master}

```bash
# 새 브랜치 생성
git branch some-new-branch-name
# 마스터 브랜치에서 커밋 삭제
git reset HEAD~ --hard
git checkout some-new-branch-name
# 이제 새로운 브랜치에 커밋이 살아있음
```

### 다른 브랜치에 잘못 커밋했을 경우
{: #to-wrong-branch}

```bash
# 마지막 커밋을 취소하지만, 변경은 가용상태로 남아있음
git reset HEAD~ --soft
git stash
# 올바른 브랜치로 이동
git checkout name-of-the-correct-branch
git stash pop
git add . 
git commit -m "your message here"
# 이제 올바른 브랜치에 커밋되어 있음
```

체리픽을 이용할 수도 있다.

```bash
git checkout name-of-the-correct-branch
# master의 마지막 커밋 가져오기
git cherry-pick master
# 마스터에서는 삭제
git checkout master
git reset HEAD~ --hard
```

### Untracked 파일들 삭제하기
{: #delete-untracked-file}

```bash
git clean -f
git clean -fd # 디렉토리 포함
```

### 그냥 포기
{: #give-up}

```bash
cd ..
sudo rm -r fucking-git-repo-dir
git clone https://some.github.url/fucking-git-repo-dir.git
cd fucking-git-repo-dir
```
