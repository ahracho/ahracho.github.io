---
layout: post
title:  "[git] reset/revert 복구하기"
categories: Trial&Error
tags: [git]
comments: true
---

## 사건의 개요

`git commit` 후 commit에 포함시키지 말아야 할 파일을 발견하였다. 커밋 자체를 취소하기 위해서 `git revert`를 사용하는 대참사가 벌어진다.  

`git revert <commit id>`는 해당 commit id로 파일들을 되돌리는 명령어이기 때문에 그 이후의 수정사항들이 모두 사라지게 된다. 

## 해결
구글에 `git revert 취소`를 검색하고 기도하는 마음으로 해결 방법을 찾아본다. 다행히 복구할 방법이 있는 듯 하다 (하늘이시여!).  

[[GIT] reset 한거 취소하는 방법](88240.tistory.com/284)  

해답은 `git reflog`에 있었다.  

~~~sh
# git reflog
3d0a896 HEAD@{0}: commit (amend): 모든 걸 삭제한 악마의 커밋
e829698 HEAD@{1}: commit: 되돌리고 싶은 커밋
[...]

# git reset --hard HEAD@{1}

# git reflog
e829698 HEAD@{0}: reset: moving to HEAD@{1} : 복구하는 커밋
3d0a896 HEAD@{1}: commit (amend): 모든 걸 삭제한 악마의 커밋
e829698 HEAD@{2}: commit: 되돌리고 싶은 커밋
[...]
~~~  


## 교훈
### Commit 되돌리기
- 수정사항에는 문제가 없지만 commit만 되돌리고 싶다면 `git reset`을 사용하라  

~~~sh
# git reset --soft <돌아가고 싶은 commit id>  
git add는 되어 있는 상태로 돌아간다.  

# git reset --mixed <돌아가고 싶은 commit id>  
git add 이전으로 돌아간다.  
~~~  


- `git commit --amend`를 활용하라  
  - commit된 파일을 재수정하고 싶다면 수정 이후 `git add -> git commit --amend`하면 된다.  
