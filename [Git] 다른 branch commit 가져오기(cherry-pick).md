두개의 다른 branch A와 B가 있을 때, A의 특정 commit을 B로 가져올 때는 git의 cherry pick을 사용하면 된다. 

## A branch의 commit id확인
```
git log
```
가져온 commit log들
```
commit edc01dfeb83a4f...
Author: author info
Date:   Tue Feb 8 11:26:29 2022 +0900

    commit name1


commit f249d8d23cda089a...
Author: author info
Date:   Thu Feb 3 17:23:06 2022 +0900

    commit name2
```

## B branch 에서 cherry-pick
### 단건 cherry-pick
```
git cherry-pick edc01dfeb
```
### 다건 cherry-pick
`^`를 붙이게 되면 두 커밋을 모두 포함하여 cherry-pick을 하게되며, `과거커밋^..최신커밋` 순으로 작성한다.
```
git cherry-pick f249d8d^..edc01dfeb
```
