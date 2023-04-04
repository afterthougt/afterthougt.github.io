---
layout: post
title: \[프로그래머스\] 기능개발 (풀이 언어 - Python/파이썬)
category: cs
tags: ads

---

# [프로그래머스/Programmers] 기능개발 (풀이 언어 - Python/파이썬)
## 문제 설명
[링크](https://school.programmers.co.kr/learn/courses/30/lessons/42586){:target="_blank"}

- 작업이 남아 있는 동안(while progresses) 매 시각마다 리스트의 왼쪽부터 기능 개발 완료 여부(progresses[0] + time*speeds[0] 값과 100을 비교)를 살핀다.
- 개발이 완료된 것은 리스트에서 떼어내고 count를 1 증가시킨다.
- 개발이 완료되지 않았다면 시간이 흘러야 하며, 이때 카운트가 양수인 경우 이전과 다른 개발이 진행하는 경우이므로 answer에 count를 추가하고 count를 초기화한다.

## 풀이

```python
from collections import deque

def solution(progresses, speeds):
    """기능 개발 현황 및 개발 속도에 따른 배포 기능 수 계산 함수
    
    Args:
        progresses: 배포 순서로 작업 진도가 담긴 리스트
        speeds: 각 작업의 개발 속도가 담긴 리스트
    
    Return:
        answer: 각 배포마다 배포되는 기능 수가 담긴 리스트
    """
    
    progresses, speeds = deque(progresses), deque(speeds)
    time, count = 0, 0
    answer = []
    while progresses:
        if progresses[0] + time*speeds[0] < 100:
            if count > 0:
                answer.append(count)
                count = 0
            time += 1
        else:
            progresses.popleft()
            speeds.popleft()
            count += 1
    answer.append(count)
    return answer
```
