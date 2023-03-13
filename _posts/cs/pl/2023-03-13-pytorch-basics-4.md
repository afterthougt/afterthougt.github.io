---
layout: post
title: 파이토치(PyTorch) 기초 4
category: cs
tags: pl

---

# 파이토치(PyTorch) 기초 4

## AutoGrad & Optimizer

### torch.nn.Module
- 딥러닝 구성 layer의 base class
- 정의 4가지: (input), (output), forward, backward(autograd로 자동 미분)
- 학습 대상되는 parameter(tensor) 정의

### nn.Parameter
- Tensor 객체의 상속 객체
- nn.Module 내에 attribute가 될 때는 required_grad=True로 지정되어 학습 대상되는 tensor
- 직접 지정하게 될 경우가 별로 없음 - 대부분 layer에는 weights 값들 지정