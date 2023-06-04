---
layout: post
title: 파이토치(PyTorch) 기초 2
category: cs
tags: pl

---

# [PyTorch] PyTorch 기초 2

## 파이토치 = numpy + AutoGrad
- ndim, shape과 같은 attribute 그대로 적용

## reshape 대신 view 쓸 것 권장 -> why..?
- view는 기존 메모리를 참조하여 형태만 바꾸어준 것
- reshape은 기존 메모리 객체를 복사하여 새 참조 형성

## unsqueeze vs. squeeze

## 파이토치 메서드 비교: dot() vs. mm() vs. matmul()
- 파이토치의 경우, 행렬곱은 dot 대신 mm, matmul을 써야 함.
- mm()은 브로드캐스팅<sub>broadcasting</sub>이 지원되지 않는 반면, matmul()은 지원.

## 참고
- [부스트코스 - PyTorch 강의](https://www.boostcourse.org/ai213){:target="_blank"}