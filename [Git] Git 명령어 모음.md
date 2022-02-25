# Git 명령어 모음
```
git log --pretty=oneline
```
- 한 커밋당 한줄 커밋 히스토리 출력

```
git commit --amend
```
- 최신 커밋 수정해서 새로운 커밋 만들기

```
git diff [커밋 A의 아이디] [커밋 B의 아이디]
```
- 두 커밋 간의 차이 비교

```
git fetch
```
- 로컬 레포지토리에서 현재 HEAD가 가리키는 브랜치의 업스트림(upstream) 브랜치로부터 최신 커밋들을 가져옴(git pull은 가져와서 머지까지 함)

```
git log --all --graph
```
- 모든 브랜치의 커밋 히스토리 그래프로 출력

```
git stash
```
- 현재 작업내용 스택에 저장

```
git stash apply [커밋 아이디]
```
- 스택에 저장된 가장 최근의(혹은 특정) 작업을 working directory에 적용

```
git stash drop [커밋 아이디] 
```
- 스택에서 삭제

```
git stash pop [커밋 아이디]
```
- 스택에서 작업을 working directory에 적용하고 삭제

```
git cherry-pick [커밋 아이디]
```
- 특정 커밋내용 반영
