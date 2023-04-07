---
layout: post
title: \[프로그래머스\] 위장 (풀이 언어 - Python/파이썬)
category: cs
tags: ads

---

# [프로그래머스/Programmers] 위장 (풀이 언어 - Python/파이썬)
## 문제 설명
[링크](https://school.programmers.co.kr/learn/courses/30/lessons/42578){:target="_blank"}

스파이들은 매일 다른 옷을 조합하여 입어 자신을 위장합니다.

예를 들어 스파이가 가진 옷이 아래와 같고 오늘 스파이가 동그란 안경, 긴 코트, 파란색 티셔츠를 입었다면 다음날은 청바지를 추가로 입거나 동그란 안경 대신 검정 선글라스를 착용하거나 해야 합니다.

| 종류 | 이름 |
| ---- | ---- |
| 얼굴 | 동그란 안경, 검정 선글라스 |
| 상의 | 파란색 티셔츠 |
| 하의 | 청바지 |
| 겉옷 | 긴 코트 |

스파이가 가진 의상들이 담긴 2차원 배열 clothes가 주어질 때 서로 다른 옷의 조합의 수를 return 하도록 solution 함수를 작성해주세요.

## 제한사항
- clothes의 각 행은 [의상의 이름, 의상의 종류]로 이루어져 있습니다.
- 스파이가 가진 의상의 수는 1개 이상 30개 이하입니다.
- 같은 이름을 가진 의상은 존재하지 않습니다.
- clothes의 모든 원소는 문자열로 이루어져 있습니다.
- 모든 문자열의 길이는 1 이상 20 이하인 자연수이고 알파벳 소문자 또는 '_' 로만 이루어져 있습니다.
- 스파이는 하루에 최소 한 개의 의상은 입습니다.

## 풀이
- 크게 두 세 가지 풀이를 제시해보기로 한다.
  - collections.Counter와 math.prod를 사용하는 방법 (코드 1)
  - 파이썬의 딕셔너리 자료구조를 사용하여 해시를 활용한 풀이 방법 (코드 2)
  - 코드 1과 유사한데, math.prod 함수를 잘 몰랐을 때 functools.reduce를 사용한 방법 (코드 3)
- math.prod와 Counter를 사용하는 것이 큰 군더더기 없이 풀어내는 방법인 듯하다.

## 코드 1
```python
import math
from collections import Counter

def solution(clothes):
    """Find the number of different combinations of clothes,
       given a 2D array 'clothes' containing spy's outfits.
    """
    
    counter = Counter([cl_type for _, cl_type in clothes])
    return math.prod([num+1 for num in counter.values()]) - 1
```

## 코드 2
```python
def solution(clothes):
    """Find the number of different combinations of clothes,
       given a 2D array 'clothes' containing spy's outfits.
    """
    
    hash_map = {}
    answer = 1
    for _, clothes_type in clothes:
        hash_map[clothes_type] = hash_map.get(clothes_type, 0) + 1
    for clothes_type in hash_map:
        answer *= hash_map[clothes_type] + 1
    return answer - 1
```

## 코드 3 (코드 1과 유사)
```python
from collections import Counter
from functools import reduce
    
def solution(clothes):
    """Find the number of different combinations of clothes,
       given a 2D array 'clothes' containing spy's outfits.
    """
    
    cnt = Counter([clothes_type for _, clothes_type in clothes])
    answer = reduce(lambda x, y: x * (y+1), cnt.values(), 1) - 1
    return answer
```
