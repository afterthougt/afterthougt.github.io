---
layout: post
title: \[프로그래머스\] 체육복 (파이썬; Python)
category: cs
tags: ads

---

# [프로그래머스] 체육복 (파이썬; Python)
## 문제 설명
[링크](https://school.programmers.co.kr/learn/courses/30/lessons/42862){:target="_blank"}

- 잃어버린 아이템(체육복)을 기준으로 `for-loop` 체크를 한다.
- 전체 학생 수 $$n$$이 구간 [2, 30]에 속하는 정수값이고 알고리즘의 시간 복잡도는 $$O(n^2)$$이기 때문에 크게 최적화가 필요하지 않을 것 같아 보인다.
- `lost`와 `reserve` 사이에 중복을 제거하여 `net_lost`와 `net_reserve`를 `set()` 함수를 사용하여 만들어 주었다.
- 키워드 `in`의 시간 복잡도는 `list`에 대해선 평균 $$O(n)$$이나, `set`에 대해선 평균 $$O(1)$$, 최악의 경우 $$O(n)$$이라는 점을 고려해 `set`을 사용했다.

## 풀이

```python
def solution(n, lost, reserve):
    """
    Args:
        n: 전체 학생의 수
        lost: 체육복을 도난당한 학생들의 번호가 담긴 배열
        reserve: 여벌의 체육복을 가져온 학생들의 번호가 담긴 배열
        
    Return:
        answer: 체육수업을 들을 수 있는 학생의 최댓값
    """
    
    net_lost = set(lost) - set(reserve)
    net_reserve = set(reserve) - set(lost)
    for lost_item in net_lost:
        if lost_item - 1 in net_reserve:
            net_reserve.remove(lost_item - 1)
        elif lost_item + 1 in net_reserve:
            net_reserve.remove(lost_item + 1)
    answer = n - len(net_lost)
    return answer
```

## 다른 풀이
[참고](https://rain-bow.tistory.com/30){:target="_blank"}

- 여분의 아이템을 기준으로 `for-loop` 탐색을 진행하는 방법

```python
def solution(n, lost, reserve):
    """
    Args:
        n: 전체 학생의 수
        lost: 체육복을 도난당한 학생들의 번호가 담긴 배열
        reserve: 여벌의 체육복을 가져온 학생들의 번호가 담긴 배열
        
    Return:
        answer: 체육수업을 들을 수 있는 학생의 최댓값
    """
    
    net_lost = set(lost) - set(reserve)
    net_reserve = set(reserve) - set(lost)
    for reserved_item in net_reserve:
        if reserved_item - 1 in net_lost:
            net_lost.remove(reserved_item - 1)
        elif reserved_item + 1 in net_lost:
            net_lost.remove(reserved_item + 1)
    answer = n - len(net_lost)
    return answer
```

## 참고
[1] [Complexity of *in* operator in Python](https://stackoverflow.com/questions/13884177/complexity-of-in-operator-in-python){:target="_blank"} <br>
[2] [[Python] 프로그래머스 - 체육복](https://rain-bow.tistory.com/30){:target="_blank"}