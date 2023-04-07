---
layout: post
title: \[프로그래머스\] 완주하지 못한 선수 (풀이 언어 - Python/파이썬)
category: cs
tags: ads

---

# [프로그래머스/Programmers] 완주하지 못한 선수 (풀이 언어 - Python/파이썬)
## 문제 설명
[링크](https://school.programmers.co.kr/learn/courses/30/lessons/42576){:target="_blank"}

수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

## 제한사항
- 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
- completion의 길이는 participant의 길이보다 1 작습니다.
- 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
- 참가자 중에는 동명이인이 있을 수 있습니다.

## 풀이
- 두 가지 풀이를 제시해보기로 한다.
  - 파이썬의 collections 라이브러리의 Counter 함수를 사용하여 차집합 연산으로 푸는 방법 (코드 1)
  - 파이썬의 딕셔너리 자료구조를 사용하여 해시를 활용한 풀이 방법 (코드 2)
- 둘 모두 해시 테이블 자료구조가 사용되는 방법.
- Counter 객체의 keys() 메서드, 딕셔너리의 get() 메서드 등을 알면 쉽게 구현 가능한 것으로 보인다.

## 코드 1

```python
from collections import Counter

def solution(participant, completion):
    """Pick out one participant who did not complete the marathon."""
    
    # Complement of completion in participant
    sub = Counter(participant) - Counter(completion)
    answer = tuple(sub.keys())[0]
    return answer
```

## 코드 2
```python
def solution(participant, completion):
    """Pick out one participant who did not complete the marathon."""
    
    answer = {}
    for p in participant:
        answer[p] = answer.get(p, 0) + 1
    for c in completion:
        answer[c] -= 1
    for person in answer:
        if answer[person]:
            return person
```
