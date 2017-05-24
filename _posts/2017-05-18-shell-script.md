---
layout: post
title: shell-script
categories: "shell script"
fullview : true
comments : true
---
*notice : 얼마 배우지 않은 단계에서 적어나가는 것이기 때문에 틀린 점이 있을 수 있음.
<h3> Ubuntu에서 이용할 수 있는 가장 강력한 기술. </h3>

*notice : 반드시 #!/bin/bash를 말머리에 써야 한다. (그래야 어디에서 컴파일 되는 지를 알 수 있다.)
*notice : 절대로 root사용자 상태에서 다루지 마라..... 그러다가.... rm -rf */ 당해서 컴퓨터가 망가질 수 있다.

<h1> Basic </h1>
<p>모든 명령어는 [명령어] [인자] 순으로 기능한다.</p>   
<p>## chmod : 파일에 접근 권한을 부여하는 기능이다.</p>   
<p>##### 1. 숫자로 권한을 부여할 때   
+숫자로 권한을 부여할 때에는 100의 자리는 usr의 권한, 10의 자리는 group의 권한, 1의 자리는 다른 사람들의 권한을 부여한다.   
+read 권한은 4, write권한은 2, execute 권한은 1이며, 각 숫자를 더하고 빼는 것으로 권한을 모두 주거나, 아예 안 줄 수 있다.   
ex ) chmod 401 ./[파일이름]   </p>

<p>##### 2. 문자로 권한을 부여할 때.
+User는 u group은 g other는 o로 표시한다.
+Read는 r write는 w execute는 x로 표시한다.
ex) chmod u-w go-x ./[파일 이름]
		chmod u=r,g=r,o=w ./[파일 이름]
* chmod로 (접근 권한 = 퍼미션)을 바꿔야만 셸 스크립트를 실행할 수 있다.
* cmd안에서 일어날 수 있는 모든 작업들은 cmd안에서 쓰듯이 셸 스크립트를 씀으로서 한번에 처리할 수 있다.
ex) mkdir name
	mv name.txt name.py << 셸 스크립트는 여러번 쓰기 때문에 이렇게 쓰는 것은 좋지 않다. 여러개의 확장자를 한번에 바꿀 때라면 모를까.</p>

<p>
## echo 
+print, printf와 비슷한 역할을 한다. 
+셸 스크립트에 출력해주는 역할이다.
	ex) echo "Hello, World!"
</p>

<p>## 주석
+주석은 #로 시작한다. 
*하지만 #!/bin/bash는 어디에서 컴파일 할 것인지를 알려주기 때문에 저 부분만 주석이 아니다.
</p>

<p>## 변수
+```x=12```와 같은 꼴로 나타낸다. 
+이 때 "="과 x사이, "="과 숫자사이에는 공백이 없어야 한다.</p>

<p>## if~ else ~fi 구문
```shell
if [조건]
then
[조건이 이루어질 경우]
else
[조건이 이루어지지 않을 경우]
exit
fi
```
</p>




