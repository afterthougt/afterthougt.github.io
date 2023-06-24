---
layout: post
title: zsh 설정
category: cs
tags: sys

---

# [zsh] z 셸(shell) 설정
## ZSH(Z shell, Z 셸)
Bourne shell (sh)의 확장 버전

### 몇 가지 사용 이유, 장점 - 사용 편의성
- 자동 cd: `cd` 커맨드를 생략하고 디렉토리 이름만 입력해도 디렉토리 이동이 가능하다.
- 재귀적 경로 확장: `/usr/local/bin` 대신 `/u/lo/b`와 같은 축약 형태로 입력이 가능하다.

## 맥 환경에서 터미널 커스터마이징하기
- [Oh-My-Zsh 설치](https://zeddios.tistory.com/1207){: target="_blank"}

## zsh 일부 내용 백업용 정리
`echo "셸에 적을 내용" >> ~/.zshrc`를 해야 하는데 `>>` 대신 `>`을 입력하는 바람에 기존 내용이 날아가는 불상사가 발생하여.. .zshrc 내용 중 백업할 만한 내용을 블로그에 적어두기로 했다. `homebrew`, `pyenv`, `flutter` 등에 관한 환경 변수 설정 등 내용을 포함한다.

```
# 터미널 커스터마이징을 위한 환경 변수 설정 등
export ZSH="$HOME/.oh-my-zsh"
ZSH_THEME="robbyrussell"
plugins=(git)
source $ZSH/oh-my-zsh.sh

# homebrew 환경 변수 설정
export PATH="/opt/homebrew/bin:$PATH"

# pyenv 환경 변수 설정
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
export PATH="$PYENV_ROOT/shims:$PATH"

# flutter 환경 변수 설정
export PATH="$HOME/development/flutter/bin:$PATH"
```

## 참고
- [ZSH란 무엇이며 왜 Bash 대신에 그것을 사용해야 합니까?](https://ko.savtec.org/articles/howto/what-is-zsh-and-why-should-you-use-it-instead-of-bash.html){: target="_blank"}
