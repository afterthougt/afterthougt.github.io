---
layout: post
title: 파이토치(PyTorch) 활용
category: cs
tags: pl

---

# 파이토치(PyTorch) 활용

## 멀티 GPU
### 모델 병렬화(Model parallel)
- 다중 GPU에 학습 분산을 하는 두 가지 방법
  - 모델 나누기
  - 데이터 나누기
- 모델 나누는 것은 예전부터 쓰였음(AlexNet)
- 모델의 병목, 파이프라인의 어려움 등으로 인해 모델 병렬화는 고난도 과제 <br> $$\rightarrow$$ Q. 컴퓨터 아키텍처, 운영체제 등을 잘 알아야 하는 이유가 되는 부분?

### 데이터 병렬화(Data parallel)
- 파이토치<sub>PyTorch</sub> 기준으로 두 가지 방식
  - DataParallel
  - DistributedDataParallel

- DataParallel - 데이터 분배 후 단순 평균
  - GPU 사용 불균형 문제 발생
  - Batch 크기 감소(1 GPU 병목 시)
  - GIL
- DistributedDataParallel - 각 CPU마다 프로세스 생성 후 개별 GPU에 할당 <br> $$\rightarrow$$ 기본적으로 데이터 병렬로 하나, 개별적으로 연산 평균 취함

## 성능 개선
### 방법
- 모델<sub>Model</sub>
- 데이터<sub>Data</sub>
- 하이퍼파라미터 튜닝<sub>Hypterparameter tuning</sub>
등이 존재하는데, 이 중에 데이터가 가장 중요! 하이퍼파라미터 튜닝으로 얻게 될 이점은 그렇게 크지 않음.

### 하이퍼파라미터 튜닝
- 모델 스스로 학습하지 않는 값은 사람이 지정
- 하이퍼파라미터에 의해 값이 크게 좌우될 때도 있음
- 마지막 0.01을 쥐어짤 때 도전해 볼만함

### Ray
- 멀티노드 멀티 프로세싱<sub>Multi-node multi processing</sub> 지원 모듈
- 머신 러닝/딥 러닝 병렬 처리를 위해 개발된 모듈
- 기본적으로 현재 분산병렬 머신 러닝/딥 러닝 모듈의 표준
- 하이퍼파라미터 서치<sub>Hyperparameter search</sub>를 위한 다양한 모듈 제공

## 참고
- 부스트코스 PyTorch 강의