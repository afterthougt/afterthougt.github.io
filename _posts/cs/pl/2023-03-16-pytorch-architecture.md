---
layout: post
title: 파이토치(PyTorch) 구조 학습
category: cs
tags: pl

---

# [PyTorch] PyTorch 구조 학습

## 학습 결과를 공유하려면?
### model.save()
- 학습 결과 저장을 위한 메서드
- 모델 아키텍처와 파라미터 저장
- 모델 학습 중간 과정 저장 $$\rightarrow$$ 최선의 결과 모델 선택
- 만들어진 모델을 외부 연구자와 공유하여 학습 재연성 향상

## 학습 내용을 기록하려면?
- 텐서보드<sub>tensorboard</sub>, 웨이트 앤 바이어스<sub>weight & biases; wandb</sub> 사용!

### Tensorboard
- 텐서플로우<sub>TensorFlow</sub>의 프로젝트로 만들어진 시각화 도구
- 학습 그래프, 지표<sub>metric</sub>, 학습 결과의 시각화 지원
- 파이토치<sub>PyTorch</sub>도 연결 가능 $$\rightarrow$$ 딥 러닝 시각화 핵심 도구
- scalar: 지표 등 상수 값의 연속(epoch) 표시
- graph: 모델의 계산 그래프<sub>computational graph</sub> 표시
- histogram: 모델 파라미터<sub>parameter; weight</sub> 등 값의 분포 표현
- image: 예측 값과 실제 값 비교 표시
- mesh: 3d 형태 데이터 표현 도구

### weight & biases
- 부분 무료
- 머신 러닝 실험을 원활히 지원하기 위한 상용 도구
- 협업, 코드 버저닝, 실험 결과 기록 등 제공
- MLOps의 대표적 툴
- 프로젝트 단위로 코드나 실험을 공유할 때 편한 장점

## 참고
- [부스트코스 - PyTorch 강의](https://www.boostcourse.org/ai213){:target="_blank"}