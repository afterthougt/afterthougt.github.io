---
layout: post
title: 파이토치(PyTorch) 기초 5
category: cs
tags: pl

---

# 파이토치(PyTorch) 기초 5

### Datasets
- 데이터 입력 형태를 정의하는 클래스
- 데이터 입력 방식의 표준화
- 이미지, 텍스트, 오디오 등에 따라 다른 입력 정의
- 데이터 형태에 따라 각 메서드를 다르게 정의
- 모든 것을 데이터 생성 시점에 처리할 필요 없음 .. 이미지의 텐서 변화는 학습에 필요한 시점에 변환
- 데이터셋에 대한 표준화된 처리 방법 제공 필요!
- 최근 HuggingFace 등 표준화된 라이브러리 사용

### DataLoader
- 데이터의 batch 생성 클래스
- 학습 직전(GPU feed 전) 데이터 변환 책임
- 텐서로 변환 & batch 처리가 메인 업무
- 병렬 데이터 전처리 코드 고민 필요

### Dataloader의 파라미터

```python
Dataloader(dataset, batch_size=16, shuffle=False,
           sampler=None, batch_sampler=None, num_workers=0,
           collate_fn=None, pin_memory=False, drop_last=False,
           timeout=0, worker_init_fn=None, *, prefetch_factor=2,
           persistent_workers=False)
```

- sampler: 데이터를 어떻게 뽑을지 그 index를 정해주는 기법
- batch_sampler
- collate_fn: variable length의 가변 인자 다룰 때. 데이터와 레이블 묶어 반환하는 형태 바꾸어 줌.