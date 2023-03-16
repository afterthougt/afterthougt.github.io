---
layout: post
title: 파이토치(PyTorch) 활용
category: cs
tags: pl

---

# 파이토치(PyTorch) 활용

## 멀티 GPU
### 모델 병렬화
- 다중 GPU에 학습 분산을 하는 두 가지 방법
  - 모델 나누기
  - 데이터 나누기
- 모델 나누는 것은 예전부터 쓰였음(AlexNet)
- 모델의 병목, 파이프라인의 어려움 등으로 인해 모델 병렬화는 고난도 과제 <br> $$\rightarrow$$ Q. 컴퓨터 아키텍처, 운영체제 등을 잘 알아야 하는 이유가 되는 부분?

## 참고
- 부스트코스 PyTorch 강의