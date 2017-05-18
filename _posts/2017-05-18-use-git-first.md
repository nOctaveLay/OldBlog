---
layout:post
titile: simple git using
categories:[Git]
description:
fullview : true
comments : true
---
<h1> Initial </hi>



<h1> Basic </hi>
git commit : 메세지 없이 그냥 commit하는 것. commit은 git에 add한 것을 확정지을 때 쓴다. 
git clone [address] : git에 올려진 repository에 있는 내용을 자신의 작업창에 옮기고 싶을 때 쓴다. 여기서 말하는 address는 repository의 address를 나타낸다.
git add [file name] : [file name] 파일을 git 저장소에 첨부한다.
git commit -m "[message]" : commit messagef를 남긴 채로 커밋한다.
*주의* : 커밋 없이는 git push를 할 수 없다. git에 더해져 있는 내용들이 확정된 것인지 아닌 지 알 수 없기 때문이다.
git push : 온라인 상에 git을 올린다. 
* 주로 git add [file name] 한 뒤 git commit -m "message" 를 하고 git push를 한다.

<h1>Normal </hi>
git 브랜치란? 특정 커밋에 대한 참조이다.
브랜치를 많이 만들어도 메모리나 디스크 공간에 부담이 되지 않기 때문에, 많이 만들어도 된다. 

git branch [브랜치명] : [브랜치명]을 가진 새로운 브랜치를 만든다.
git checkout [브랜치명] : [브랜치명]을 가진 브랜치로 이동한다.
* checkout을 하지 않으면 master가 가리키는 commit과 branch가 가리키는 commit이 의도치 않게 다를 수 있다. 따라서 checkout으로 같은 곳을 가리키게 하거나 의도한데로 가리키도록 checkout을 사용해야 한다.

브랜치 합치기 (Merge)란? 두 개의 부모를 가리키는 특별한 커밋을 만들어 내는 것. 즉 두 부모의 작업내역과 그 부모의 부모들의 모든 작업내역을 포함해 새로운 브랜치를 만들어 내는 것.
* 순서로 암기하는 것이 좋다.
git branch bugFix : git branch bugFix가 생성되었다.
git checkout master : master쪽을 마음껏 움직일 수 있게 되었다.
git merge bugFix master : bugFix를 master 가지로 merge했다.

리베이스란? (rebase) 브랜치끼리의 작업을 접목하는 방법 중 하나. 커밋들을 모와서 복사한 뒤, 다른 곳에 떨궈 놓는 것.
장점 : 커밋들의 흐름을 보기 좋게 한 줄로 만들 수 있다.
	즉, 저장소의 커밋 로그와 이력이 한결 깨끗해진다.
따로따로 개발한 bugFix와 masteR이라는 브랜치가 있다고 하자. 이 둘을 머지할 수도 있지만 그렇게 하면 커밋 로그가 이리갔다 저리갔다 하기 때문에 이 둘을 순서대로 개발한 것처럼 보이기로 했다. (누가 먼저고 누가 나중이냐는 bugFix에서 개발한 것을 name이 쓰느냐 마느냐에 따라 달려있다.)
같이 있을 때, bugFix를 선택하고 git rebase master라고 치면 bugFix가 밑으로 내려가고 대신 bugFix가 원래 가리키고 있었던 커밋은 남는다. (bugFix가 밑으로 내려가면서 가르키는 건 bugFix가 가리키고 있던 커밋의 복사본)
이걸 해결하기 위해서 master를 checkout으로 선택한 뒤, git rebase bugFix 를 하면 master가 bugFix의 부모쪽에 있었기 때문에 단순히 그 브랜치를 더 앞으로 가리키게 이동하는 것으로 문제가 해결된다. (bugFix가 있었던 원래 commit을 접속할 브랜치가 없기 때문)
*참고 : 너무 헷갈릴 때에는 checkout만 움직인다고 생각하면 편하다. master는 항상 최신것을 가리켜야 하므로라고 하면 이해가 쉽다.

여러 브랜치를 리베이스(rebase)하기


git에서 작업 되돌리기.
1. git reset : 예전의 커밋을 가리키도록 이동시키는 방식으로 변경 내용을 되돌리는 것. 
* 단점 : 히스토리를 고쳐쓰기 때문에 다른 사람이 작업하는 리모트 브랜치에는 쓸 수 없다.
*실행시 : git reset HEAD~1


2. git revert : 변경분을 되돌리고 이 되돌린 내용을 다른 사람과 공유하기 위해서 쓰는 것.
자신이 되돌린 내용을 복사한 새로운 브랜치를 만듬.
*실행시 : git revert HEAD


cherry-pick? 특정 commit을 branch로 복사하고 싶을 때! 개별 커밋을 골라서 HEAD 위에 떨어뜨릴 수 있음.
git checkout [branch이름]
git cherry-pick [복사하고 싶은 commit]



로컬에 쌓인 커밋
불필요한 디버그용 코드들이 들어가지 않게 하기 위해서 Git의 마법을 사용합니다!
git rebase -i : 어떤 커밋을 취하거나 버릴지를 선택하는 것, 커밋의 순서를 바꾸는 것.
git rebase -i HEAD~# : HEAD에서 #만큼 수를 바꾸거나 버린다.


git commit --amend : 커밋 내용을 정정함.

출처 : http://learnbranch.uriqit.com/

