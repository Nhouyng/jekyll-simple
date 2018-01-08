---
layout: post
title: python3 입/출력
category: python3
description: python3 입/출력 요령
---

> 파이썬 입/출력 요령에 대한 단순 메모

<!--description-->

-----------------------

### 입력

python2와 달리 python3에서 입력의 구조가 달라졌다. 아래 예저는 python2와 python3에서 사용하는 입력 함수이다.
```
n = input()
```
하지만, python3에서 정수나 실수를 입력할때는 input()함수를 형변환 해야한다.<span class="olive"> 기본 입력 함수는 사용자의 입력을 문자열로 받기 때문이다.</span>
```
n = int(input())
f = float(intput())
```
-----------------------

### 연속된 입력

아래 예제를 입력하기 위해선 파이썬 내장함수를 사용하여 해결할 수 있다.
```
3 6 9
```

내장 함수 list을 사용한다. list는 입력을 문자열로 받아 split()함수로 ' '으로 나눈다. (형변환이 필요)
```
list = input()
l = list.split()
for i in range(0, len(l)):
    print(int(l[i]))
```

-----------------------

내장 함수 map을 사용한다.
```
a, b, c = map(int, input().split())
print(a, b, c)
print(a+b+c)
```
<span class="olive">결과화면</span>
```
3 6 9
18
```
-----------------------

### 출력

```
s = input()
print(s)

```
<span class="olive">결과화면</span>
```
Hello World!
```

-----------------------

### Comment

그냥 메모
