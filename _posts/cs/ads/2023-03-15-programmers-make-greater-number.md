---
layout: post
title: \[프로그래머스\] 큰 수 만들기 (풀이 언어: Python/파이썬)
category: cs
tags: ads

---

# [프로그래머스/Programmers] 큰 수 만들기 (풀이 언어: Python/파이썬)
## 문제 설명
[링크](https://school.programmers.co.kr/learn/courses/30/lessons/42883){:target="_blank"}

- 입력으로 들어오는 `number`가 취할 수 있는 값이 2 이상 100만 이하의 정수이다. 시간 복잡도가 $$O(n^2)$$ 이상이면 시간 초과를 당하게 되므로 $$O(n)$$으로 구현 가능한 방법을 살핀다.
- 입출력 예시 등을 살펴보면, 큰 자릿수의 숫자들 순서대로(왼쪽부터) 살펴보아 작은 숫자들 $$k$$개를 적당한 로직을 통해 찾으면 충분해 보인다.
- 왼쪽부터 내림차순으로 숫자가 오는 경우, 그대로 둔다.
- 같은 숫자가 오는 경우도 그대로 둬도 된다.
- 문제가 되는 경우는 큰 숫자를 마주칠 때인데, 스택을 활용해서 작은 수를 버릴 수 있도록 한다.

## 풀이

```python
def solution(number, k):
    """
    Args:
        number: 주어진 수, 2 이상 100만 이하
        k: 주어진 수
        
    Return:
        answer: number에서 k개의 수를 제거했을 때 얻을 수 있는 가장 큰 숫자
    """

    stack = []
    for n in number:
        while stack and stack[-1] < n and k > 0:
            stack.pop()
            k -= 1
        stack.append(n)
    answer = ''.join(stack[:-k]) if k > 0 else ''.join(stack)
    return answer
```

<!-- ## 참고 -->