+++
author = "Hugo Authors"
title = "5097. 회전"
date = "2021-04-29"
description = "< D2 > 알고리즘 문제 풀이"
categories = [
    "SWEA",

]
tags = [
    "algorithm", "swea", "d2", "python"
]
image = "algo.png"

+++

### LINK

👉   [PROBLEM - Clink here!](https://swexpertacademy.com/main/learn/course/subjectDetail.do?subjectId=AWOVIoJqqfYDFAWg)   👈

[ ROUTE ] SWEA -> Learn -> Course -> 파이썬 SW문제해결 기본 Queue -> 5차시

-----

### 문제 요약

주어진 횟수만큼 동작했을 때, 수열의 맨 앞에 있는 수는 무엇인가?

동작 : 수열의 맨 앞의 수를 맨 뒤로 보낸다.

-----

### 문제 풀이

📌 Input

```
3
3 10
5527 731 31274
5 12
18140 14618 18641 22536 23097
10 23
17236 31594 29094 2412 4316 5044 28515 24737 11578 7907
```

📌 Solving

```python
# T = 테스트 케이스 수
T = int(input())

for tc in range(1, T+1):

	# N = 숫자의 개수
	# M = 뒤로 보내는 작업 횟수
	N, M = map(int, input().split())

	# array = 주어진 수열
	array = list(map(int, input().split()))

	# 현재까지 뒤로 보내는 작업을 한 횟수
	cnt = 0

	# 작업을 M번 할 때까지 반복
	while cnt != M:
		# array.pop(0)을 통해서 배열의 맨 앞의 원소를 빼내고 값을 가져온다.
		# pop은 값을 리스트에서 삭제할뿐만 아니라 해당 값을 return한다.
		# 가져온 값을 다시 배열의 맨 뒤로 append 해준다.
		array.append(array.pop(0))
		# 24번 줄에서 작업을 한 번 해줬기 때문에 현재 작업수를 1회 더해준다.
		cnt += 1

	# 출력으로 현재 배열의 맨 앞의 수를 꺼낸다.
	print("#{} {}".format(tc, array[0]))
```

📌  Output

```mark
#1 731
#2 18641
#3 2412
```



-----



### 내 생각

python에서 제공하는 리스트 메서드인 `pop()`로 간단하게 풀 수 있었다.

위의 풀이 외에도 규칙을 찾아 다른 풀이를 쓸 수 있다.

예를 들면 횟수 : 10 / 배열 : [ 1, 2, 3 ]이 주어졌을 때,

[동작 횟수-맨 앞의 수]를 순서대로 적는다면 1회-2 / 2회-3 / 3회-1 ...으로 이후에는 앞의 과정의 반복이다.

이런 규칙성을 통해 배열의 크기로 동작 횟수를 나눠서 나온 나머지로 간단하게 답을 찾을 수 있다.

이 경우에는 배열의 크기는 `3`이므로 나머지는 `1`이다.

따라서, 답은 1회에 나왔던 `2`가 된다.

아래의 코드는 앞서 설명한 규칙을 적용한 풀이이다.

```python
T = int(input())

for tc in range(1, T+1):

	N, M = map(int, input().split())

	array = list(map(int, input().split()))

	print("#{} {}".format(tc, array[len(array)//M]))
```



알고리즘을 정말 정말 정말 싫어하지만 이처럼 하나의 문제에서 여러 풀이과정이 나올 수 있다는 점은 흥미롭다.

여러 시각으로 문제를 보는 감각을 길러 D4 이상의 알고리즘 문제까지 다 부숴 버리고 싶다.

파이팅

