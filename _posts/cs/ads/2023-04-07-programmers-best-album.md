---
layout: post
title: \[프로그래머스\] 베스트앨범 (풀이 언어 - Python/파이썬)
category: cs
tags: ads

---

# [프로그래머스/Programmers] 베스트앨범 (풀이 언어 - Python/파이썬)
## 문제 설명
[링크](https://school.programmers.co.kr/learn/courses/30/lessons/42579){:target="_blank"}

스트리밍 사이트에서 장르 별로 가장 많이 재생된 노래를 두 개씩 모아 베스트 앨범을 출시하려 합니다. 노래는 고유 번호로 구분하며, 노래를 수록하는 기준은 다음과 같습니다.

1. 속한 노래가 많이 재생된 장르를 먼저 수록합니다.
1. 장르 내에서 많이 재생된 노래를 먼저 수록합니다.
1. 장르 내에서 재생 횟수가 같은 노래 중에서는 고유 번호가 낮은 노래를 먼저 수록합니다.

노래의 장르를 나타내는 문자열 배열 `genres`와 노래별 재생 횟수를 나타내는 정수 배열 `plays`가 주어질 때, 베스트 앨범에 들어갈 노래의 고유 번호를 순서대로 return 하도록 solution 함수를 완성하세요.

## 제한사항
- genres[i]는 고유번호가 i인 노래의 장르입니다.
- plays[i]는 고유번호가 i인 노래가 재생된 횟수입니다.
- genres와 plays의 길이는 같으며, 이는 1 이상 10,000 이하입니다.
- 장르 종류는 100개 미만입니다.
- 장르에 속한 곡이 하나라면, 하나의 곡만 선택합니다.
- 모든 장르는 재생된 횟수가 다릅니다.

## 풀이
- 코드가 두 가지 제시되어 있긴 하나, 논리 구조는 같다. 아래 코드가 파이썬의 collections 등의 표준 라이브러리를 잘 활용하지 못 할 때 알고리즘을 짠 것..
- 우선 두 개의 해시맵 `play_id`와 `total_plays`를 정의하는데, 둘 모두 장르 `genre`를 공통의 키(key)로 가지며 각각 재생횟수 및 곡 순서와 해당 장르 음악의 총 재생횟수를 값(value)으로 가진다.
- 다음으로 장르별 총 재생횟수의 내림차순으로 정렬을 하기 위해 `total_plays`를 해당 조건에 맞게 정렬한다.
- 정렬된 장르를 순차로 탐색하면서 개별 곡 또한 내림차순으로 정렬하여 top 2 곡을 선별한다.

## 코드 1
```python
from collections import defaultdict

def solution(genres, plays):
    """일정 기준에 따라 베스트 앨범 수록곡 순서 정하기
    
    Args:
        genres: 문자열 배열로 표현된 노래의 장르
        plays: 정수 배열로 표현된 노래별 재생 횟수
        
    Return:
        answer: 정수 배열로 표현된 베스트 앨범에 들어갈 노래의 고유 번호 시퀀스
    """
    
    play_id = defaultdict(list) # play_id = {genre: (play, id)}
    total_plays = {} # total_plays = {genre: total plays}
    for idx, (genre, play) in enumerate(zip(genres, plays)):
        play_id[genre].append((play, idx))
        total_plays[genre] = total_plays.get(genre, 0) + play

    # 장르별 총 재생횟수의 내림차순으로 정렬
    total_plays = sorted(total_plays.items(),
                         key=lambda x: x[1],
                         reverse=True)
    answer = []
    for genre, _ in total_plays:
        # 정렬된 장르를 순차로 탐색하면서 개별 곡 또한
        # 내림차순으로 정렬하여 top 2 곡을 선별
        top2 = sorted(play_id[genre],
                      key=lambda x: x[0],
                      reverse=True)[:2]
        for _, i in top2:
            answer.append(i)
    return answer
```

## 코드 2
```python
def solution(genres, plays):
    """일정 기준에 따라 베스트 앨범 수록곡 순서 정하기
    
    Args:
        genres: 문자열 배열로 표현된 노래의 장르
        plays: 정수 배열로 표현된 노래별 재생 횟수
        
    Return:
        answer: 정수 배열로 표현된 베스트 앨범에 들어갈 노래의 고유 번호 시퀀스
    """
    
    answer = []
    hash_map1 = {}
    hash_map2 = {}
    
    for i, (g, p) in enumerate(zip(genres, plays)):
        if g not in hash_map1:
            hash_map1[g] = [(i, p)]
        else:
            hash_map1[g].append((i, p))
        if g not in hash_map2:
            hash_map2[g] = p
        else:
            hash_map2[g] += p
    
    for (k, v) in sorted(hash_map2.items(), key=lambda x: x[1], reverse=True):
        for (i, p) in sorted(hash_map1[k], key=lambda x: x[1], reverse=True)[:2]:
            answer.append(i)
    return answer
```

