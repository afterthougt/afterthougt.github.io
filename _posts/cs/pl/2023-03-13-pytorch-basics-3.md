---
layout: post
title: 파이토치(PyTorch) 기초 3
category: cs
tags: pl

---

#[PyTorch] PyTorch 기초 3

## 파이토치 프로젝트 템플릿의 필요성?
- 개발 초기 단계에서는 대화식 개발 과정이 유리 <br> $$\rightarrow$$ 학습 과정과 디버깅 등 지속적인 확인
- 배포 및 공유 단계에서 notebook 공유의 어려움 <br> $$\rightarrow$$ 쉬운 재현 어려움, 실행 순서 꼬임
- DL 코드도 하나의 프로그램 <br> .. 개발 용이성 확보 & 유지보수 향상 필요

## 파이토치 프로젝트 템플릿
- 링크: [pytorch-template](https://github.com/victoresque/pytorch-template){: target="_blank"}
- parse_config.py의 \_\_getitem\_\_ 메서드는 인덱스를 넣어주면 해당 인덱스의 값을 반환하게 하는 기능
- Data-centric AI 시대에는 terminal에서 코드를 실행해야 하는 경우가 많다?

## 참고
- [부스트코스 - PyTorch 강의](https://www.boostcourse.org/ai213){:target="_blank"}