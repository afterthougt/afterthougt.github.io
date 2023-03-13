---
layout: post
title: 파이토치(PyTorch) 기초 1
category: cs
tags: pl

---

# 파이토치(PyTorch) 기초 1

### 텐서플로우<sub>TensorFlow</sub>, 케라스<sub>Keras</sub>
- 텐서플로우<sub>TensorFlow</sub> 공개 이유? <br> $$\rightarrow$$ 문서화를 잘 하기 위해서. 개발 내용을 다른 사람들이 정확히 파악하게 하기 위해서.
- 케라스<sub>Keras</sub>는 기본적으로 wrapper!
그 아래에는 텐서플로우, 파이토치 등으로 구현될 수 있게 됨.

### 파이토치<sub>PyTorch</sub> vs. 텐서플로우<sub>TensorFlow</sub>

|  | 텐서플로우 | 파이토치 |
|---|---|---|
|방식|Define by run|define and run|
|설명|동적 계산 그래프<br>Autograd 수행 시 실행 시점에서 그래프를 정의<br>실행 중 그래프를 생성 | 그래프를 먼저 정의<br>실행 시점에 데이터 feed|
|강점|- 프로덕션<sub>production</sub> <br> - 클라우드 컴퓨팅<sub>cloud computing</sub> <br> - 멀티 GPU | - 개발 과정에서 디버깅이 쉬움 <br> $$\rightarrow$$ 구현 용이|


### Why PyTorch?

- Define by Run의 장점 .. 즉시 확인가능 $$\rightarrow$$ pythonic code
- GPU support, Good API, and community
- 사용 편한 장점
- TF는 production, scalability에 있어서 장점
- NumPy 구조를 가지는 tensor 객체로 array 표현
- 자동 미분 지원 $$\rightarrow$$ DL 연산 지원
- 다양한 형태의 DL을 지원하는 함수 & 모델 지원

### Q. 프레임워크<sub>framework</sub> vs. 라이브러리<sub>library</sub>?
