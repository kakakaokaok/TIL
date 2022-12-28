# 3일차 TIL 정리
---
git remote add origin <repo url>
제거: git remote rm <원격저장소 이름>
git log --oneline -<개수>

> ## .gitignore
참고할만한 사이트:
- [gitignore 깃헙 페이지](github.com/github/gitignore)
- [gitignore.io](gitignore.io)

## 자주 발생하는 오류
Discord에 자주 올라온 오류:
> ! [rejected] master -> master (non-fast-forward) 
> error: failed to push some refs to 'https://github.com/<user.name>/<repo.name>'
#### Reproduction
1. .gitignore, README.md 파일과 함께 원격저장소 ['test_reject'](https://github.com/kakakaokaok/test_reject) 생성
2. Desktop에 test 디렉토리 생성 및 원격저장소의 README.md 파일과 내용이 다른 README.md 파일 생성
3. 원격저장소 연결 및 push, pull 시도
```zsh
git remote add origin git@github.com:kakakaokaok/test_reject.git
git push -u origin main
```
아래와 같은 에러 메세지를 받았다.
```zsh
error: src refspec main does not match any
error: failed to push some refs to 'github.com:kakakaokaok/test_reject.git'
```
`git pull origin main` 명령을 내리니 아래와 같은 에러 메세지를 받았다.
```zsh
error: The following untracked working tree files would be overwritten by merge:
	README.md
Please move or remove them before you merge.
Aborting
```
4. add 및 commit 후 pull 다시 시도
```zsh
hint: You have divergent branches and need to specify how to reconcile them.
hint: You can do so by running one of the following commands sometime before
hint: your next pull:
hint:
hint:   git config pull.rebase false  # merge (the default strategy)
hint:   git config pull.rebase true   # rebase
hint:   git config pull.ff only       # fast-forward only
hint:
hint: You can replace "git config" with "git config --global" to set a default
hint: preference for all repositories. You can also pass --rebase, --no-rebase,
hint: or --ff-only on the command line to override the configured default per
hint: invocation.
fatal: Need to specify how to reconcile divergent branches.
```

#### 원인(추측)
원격저장소를 생성할 때 README.md 파일이나 .gitignore 파일과 함께 초기화 하는 경우가 있다. 로컬 저장소에서도 `git init` 명령어를 사용해 초기화 했을 때, 로컬 저장소의 파일과 원격저장소의 파일이 충돌해서 위와 같은 오류가 발생한 것 같다. 

#### 해결
###### 로컬저장소를 원격저장소에 덮어쓰는 방식
push 하려고 하는 브랜치 이름 앞에 +를 붙여 push하면 된다고 한다. (non-fast-forward)
```zsh
git push origin +main
```
그런데 원격저장소의 .gitignore 파일이 사라져있다. 그리고 1 commit이라고 되어 있는걸 보니, 그냥 덮어쓰는 방식인가보다. 
###### 원격저장소를 로컬저장소에 덮어쓰는 방식
```zsh
git pull --rebase origin main
```
반대로 `git push --rebase origin main`은 로컬 저장소를 원격 저장소에 덮어쓸 것 같다(rebase).

> push 하기 전에 pull 잘하자.
> merge는 내일 배운댔지?


## 참고자료
- https://somjang.tistory.com/entry/Git-rejected-master-master-non-fast-forward-%ED%95%B4%EA%B2%B0-%EB%B0%A9%EB%B2%95
