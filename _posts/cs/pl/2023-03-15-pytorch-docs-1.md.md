---
layout: post
title: 파이토치(PyTorch) 문서 읽어보기
category: cs
tags: pl

# 파이토치(PyTorch) 문서 읽어보기
- Q. PyTorch storage object?
- Q. torch.chunk로 데이터셋 구성해볼 수 있으려나?
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