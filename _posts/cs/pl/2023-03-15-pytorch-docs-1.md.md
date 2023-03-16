---
layout: post
title: 파이토치(PyTorch) 문서 읽어보기
category: cs
tags: pl

# 파이토치(PyTorch) 문서 읽어보기
- Q. PyTorch storage object?
- Q. torch.range(0, n) 함수는 deprecated 된다는데, 어쩌다가 n을 포함하게 되었을지?
- torch.arange(a, b)는 range(a, b)와 같은 범위를 가리켜서 다행
- torch.swapdims 어렵
- view, reshape 차이 완벽 이해? contiguity 차이?
- scatter_ ...?
- torch.log1p: (note) input이 작은 값일 때 torch.log보다 정확함
- torch.prod(input)
- torch.prod(input, dim)
- super().\_\_init\_\_()이 필요한 이유?
https://stackoverflow.com/questions/63058355/why-is-the-super-constructor-necessary-in-pytorch-custom-modules
- 윈도우에서는 멀티프로세서의 제한 때문에 num worker의 수가 0 이상인 경우 에러가 발생합니다?
- To raise question:
행/열 방향 접근 시간의 차이 때문에 torch.gather 같은 모듈 사용의 의미가 있는지?
torch.backends.cudnn.deterministic = True  # type: ignore
torch.backends.cudnn.benchmark = True  # type: ignore

---

# PyTorch 문서 훑어보기
## torch.chunk
### 용례
`torch.chunk(*input*, *chunks*, *dim=0*)` $$\rightarrow$$ List of Tensors <br>
### 코드
```python
>>> torch.arange(5).chunk(3)
(tensor([0, 1]),
 tensor([2, 3]),
 tensor([4])
)
>>> torch.arange(13).chunk(6)
(tensor([0, 1, 2]),
 tensor([3, 4, 5]),
 tensor([6, 7, 8]),
 tensor([ 9, 10, 11]),
 tensor([12]))
```
- 아래 코드의 경우, 6개의 chunk로 나눌 수 없어서 그보다 적은 수의 chunk로 나눈 예시.
- Q. torch.chunk를 데이터셋 구성 시 사용하게 될지에 대한 의문?