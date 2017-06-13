---
layout: post
title: 아무도 알려주지 않는 파이썬
categories: "python3"
fullview : true
comments : true
---
<p>
### []의 강력한 기술.
```
for x in range(10):
    print(x)
```
대신
```
[print(x) for x in range(10)]
```
이 가능하다.

+ 응용
```
[(print(x),print(y)) for x in range(10) for y in range(20)]
```

```
[(print(x),print("asdf")) for x in range(10)]
```
</p>
