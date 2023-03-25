---
layout: post
title: \[프로그래머스\] 전력망을 둘로 나누기 (풀이 언어 - Python/파이썬)
category: cs
tags: ads

---

# [프로그래머스/Programmers] 전력망을 둘로 나누기 (풀이 언어 - Python/파이썬)
## 문제 설명
[링크](https://school.programmers.co.kr/learn/courses/30/lessons/86971){:target="_blank"}

- union-find 방법으로 풀어볼까 했는데 완전탐색으로 풀어보고 싶어 dfs 방법을 사용하였다.
- dfs 함수는 노드 1에서부터 시작하여 (1) 연결된 엣지를 끊고 (2) 엣지 끝단의 다른 노드가 가지는 네트워크의 크기를 해당 노드의 사이즈로서 `subtree_size`에 저장하도록 한다. 이때 깊이우선탐색 방식을 사용한다.
- `subtree_size` 변수에 저장된 숫자들은 각각 네트워크를 둘로 분할한 것 중 하나의 네트워크 사이즈이다. 1과 연결이 가까울수록(1로부터의 깊이가 얕을수록) 분할된 네트워크의 사이즈 값은 크게 저장될 것이고, 멀수록(1로부터의 깊이가 깊을수록) 작은 네트워크의 사이즈 값이 저장될 것이다.

## 풀이

```python
from collections import defaultdict

def solution(n, wires):
    tree = defaultdict(list)
    for w in wires:
        tree[w[0]].append(w[1])
        tree[w[1]].append(w[0])

    visited = [False] * (n + 1)
    subtree_size = [0] * (n + 1)

    dfs(tree, 1, visited, subtree_size)

    answer = float('inf')
    for size in subtree_size:
        diff = abs(n - 2 * size)
        answer = min(answer, diff)
        
    return answer

def dfs(tree, node, visited, subtree_size):
    visited[node] = True
    size = 1

    for neighbor in tree[node]:
        if not visited[neighbor]:
            size += dfs(tree, neighbor, visited, subtree_size)
            
    subtree_size[node] = size
    return size
```