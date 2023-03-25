---
layout: post
title: \[프로그래머스\] 모음사전 (풀이 언어 - Python/파이썬)
category: cs
tags: ads

---

# [프로그래머스/Programmers] 모음사전 (풀이 언어 - Python/파이썬)
## 문제 설명
[링크](https://school.programmers.co.kr/learn/courses/30/lessons/84512){:target="_blank"}

- 입력<sub>input</sub>인 `word`는 길이 $$n$$이 5 이하이며 알파벳의 다섯 가지 모음으로 이루어져 있으므로 파이썬의 itertools 모듈에서 product 함수를 사용하여 $$5^n$$가지 모음 조합을 구하면 간단히 풀 수 있다(다른 풀이).
- 다만, 입력이 큰 값이 들어왔을 때 조금 더 효율적으로 풀 수 있는 방법이 없을까 싶어 dfs 방법으로 풀이를 해보았다.
- dfs 함수 설명: 현재 모음 조합 `current_word`가 `target_word`와 같아질 때까지 `current_word`에 모음을 붙여보며 전역 변수 `count`를 증가시킨다.

## 풀이

```python
def solution(word):
    """Word numberth finder"""
    global count
    count = 0
    vowels = ('A', 'E', 'I', 'O', 'U')
    return dfs(word, "", vowels)

def dfs(target_word, current_word, vowels):
    global count
    if current_word == target_word:
        return count
    
    if len(current_word) < 5:
        for v in vowels:
            count += 1
            result = dfs(target_word, current_word + v, vowels)
            if result:
                return result
```

## 다른 풀이
- 파이썬의 itertools 모듈에서 product 함수를 사용하여 $$5^n$$가지 모음 조합을 구하는 방법.
- 이분탐색을 위해 bisect 모듈에서 bisect_right 함수를 사용한다.
- 다만, 정렬의 시간 복잡도가 $$O(n5^n)$$이므로 $$n$$ 값이 커지게 될 경우에는 주의해야 할 필요가 있어보인다.

```python
from itertools import product
from bisect import bisect_right

def solution(word):
    answer = 0
    words = ['A', 'E', 'I', 'O', 'U']
    lst = []
    for i in range(1, 6):
        lst += list(product(words, repeat = i))
    lst = [''.join(i) for i in lst]
    lst.sort()
    
    return bisect_right(lst, word)
```
