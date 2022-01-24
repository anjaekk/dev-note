git push후 이전에 commit했던 모든 author와 committer변경을 위해서는 아래의 명령문을 통해 변경해주도록 한다.   
author만 변경할 경우 나중에 github에서 확인시 이전 커밋자의 이력이 함께 표시되게 된다.(author: 변경한 계정, committer: 변경전 계정) 

## 명령문

```
git filter-branch --env-filter '
WRONG_EMAIL="변경전 이메일"
NEW_NAME="새로운 이름"
NEW_EMAIL="새로운 이메일"

if [ "$GIT_COMMITTER_EMAIL" = "$WRONG_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$NEW_NAME"
    export GIT_COMMITTER_EMAIL="$NEW_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$WRONG_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$NEW_NAME"
    export GIT_AUTHOR_EMAIL="$NEW_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```
실행후 
```
Ref 'refs/heads/main' was rewritten
```
위의 메세지가 나오면 성공이다! 명령문에 대해 더 자세히 확인하고 싶다면 Documentation을 확인하도록 한다.
> 🔗 [git reference - filter](https://git-scm.com/docs/git-filter-branch)


## 다수 계정 변경시
여러명이 한 프로젝트에서 다른 사람의 commit이력까지 변경해야한다면 위의 명령문을 2번 실행했을 때 아래와 같은 메세지가 나올 것이다. 
```
Cannot create a new backup.
A previous backup already exists in refs/original/
Force overwriting the backup with -f
```

그럼 `-f`와 함께 명령문을 작성해주도록 한다.
```
git filter-branch -f --env-filter '
WRONG_EMAIL="변경전 이메일"
NEW_NAME="새로운 이름"
NEW_EMAIL="새로운 이메일"

if [ "$GIT_COMMITTER_EMAIL" = "$WRONG_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$NEW_NAME"
    export GIT_COMMITTER_EMAIL="$NEW_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$WRONG_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$NEW_NAME"
    export GIT_AUTHOR_EMAIL="$NEW_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```

## git push 오류
.git이 확인되지 않는다며 git push가 안되면 mac의 경우 `key chains`에서 github를 검색하고 기존 계정을 모두 삭제해주도록 한다.(언제든 다시 생성할 수 있다.) 

## 이후 commit을 한다면
push후 변경된 name과 email로 나와야 한다면 아래의 명령어를 통해 user의 name과 email을 변경해주도록 한다. 이를 변경해줘야 앞으로 committer가 변경된 사용자로 나올 수 있다.
```
git config --global user.name "github name"
git config --global user.email "github email"
```

## 확인
### 1. git log
단순히 `git log`만 작성할 경우 committer 이름은 확인되지 않기 때문에 git log format을 변경해서 확인하는게 편하다. 새로운 커맨드창에 입력후 `command+f`(mac)를 통해 이전 name과 email이 안뜨는지 확인한다.
```
git log --pretty=format:"%h - %an(%ae), %cn(%ce)"
```
git log의 옵션에 대해 알고싶다면 아래의 documentation을 확인하자.

> 🔗 [git reference - commit history](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%BB%A4%EB%B0%8B-%ED%9E%88%EC%8A%A4%ED%86%A0%EB%A6%AC-%EC%A1%B0%ED%9A%8C%ED%95%98%EA%B8%B0)

### 2. github
push후 github에서 해당 name과 email을 검색해 뜨는 내용이 있는지 확인한다.



## 주의할 점
github내에서 수정한 소스가 있을 경우(예를 들면 read me) git log를 확인해보면 다른 이름과 이메일로 작성되어있는걸 확인할 수 있다. 
이경우 committer는 없고 author만 변경해주면 되는데 git log의 name과 author email도 변경해야하는 이메일과 이름으로 변경해줘야 한다.
