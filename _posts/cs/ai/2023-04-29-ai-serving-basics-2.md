---
layout: post
title: 파이썬 버전 컨트롤
category: cs
tags: ai
---

# [AI 서빙 기초] 파이썬 버전 컨트롤

## Python Version Control

### 버전 관리

- A set of numbers that identify a unique evolution of a computer program (Wikipedia)
- 소프트웨어 제품의 특정 릴리즈에 대한 고유한 식별자
- 소프트웨어 첫 출시 이후 업데이트가 이루어질 때마다 새로운 버전 번호 부여
- 예) Ubuntu 20.04, Python 3.11.0, Git commit hash (7e6d3fd 등)

### 버저닝(Versioning)

- 버전 관리, 식별을 위해 사용되는 방법
- 종류
    - CalVer (Calendar Versioning)
        - 날짜 기반. 예) Ubuntu 20.04 (2020년 04월 출시)
    - SemVer (Semantic Versioning)
        - 이전 버전과 호환되지 않는 변경 → 주 번호 증가
        - 이전 버전과 호환되며 새로운 기능 추가 → 부 번호 증가
        - 이전 버전의 버그 수정 → 패치 번호 증가
        - 예) Python 3.11.0
    - HashVer (Hash Versioning)
        - SHA-1, SHA-256 해시 알고리즘을 사용해 버전에 대해 고유 식별자 생성. 예) Git commit 7e6d3fd

### 버전 관리의 필요성

- 릴리즈에 대한 통일된 관점 필요
- 팀 내 협업 시
- Project Manager와 프로젝트 로드맵 계획 회의 시
- 사용자에게 앱 스토어에서 릴리즈 내용 공지 시

→ 계속적이고 지속적인 개발, 릴리즈 환경에서는 소프트웨어 엔지니어링에 버전이 반드시 필요.

### 파이썬 버전 관리

- pyenv 추천
- pyenv와 conda가 같이 설치되어 충돌이 발생하는 경우
    - pyenv에서 설치한 파이썬은 무시되고 conda에서 사용하는 파이썬만 호출
    - pyenv에서 설치한 파이썬을 실행시키려면 python 3.11 같이 명시적으로 표현
    - 파이썬 설치 전 현재 사용 python이 어디서 설치된 것인지 확인하는 과정 필요
    - which 명령어(which python)로 어떤 파일을 실행시키는지 확인 가능
- pyenv 설치
    - MacOS
        
        ```bash
        brew install pyenv
        ```
        
    - Linux(Ubuntu)
        
        ```bash
        sudo apt-get install -y make build-essential libssl-dev zlib 1g-dev libbz2-dev libreadlin-dev libsqlite-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev
        ```
        
        ```bash
        curl https://pyenv.run | bash
        ```
        
- MacOS, Linux는 본인 사용 shell 설정 파일(~/.bashrc, ~/.zshrc) 끝에 환경변수를 추가해야 함
    
    ```bash
    export PATH=”~/.pyenv/bin:$PATH”
    ```
    
    ```bash
    eval “$(pyenv init -)”
    ```
    
    ```bash
    eval “$(pyenv virtualenv-init -)”
    ```
    
    - pyenv: no such command `virtualenv-init'와 같은 오류가 뜰 경우
        
        ```bash
        brew install pyenv-virtualenv
        ```
        
        출처: [https://stackoverflow.com/questions/62532807/pyenv-no-such-command-virtualenv](https://stackoverflow.com/questions/62532807/pyenv-no-such-command-virtualenv)
        
- Shell 확인 방법: 터미널에서 `echo $SHELL`
- /bin/bash의 경우: bash shell 사용 → shell 설정 파일은 ~/.bashrc
- /bin/zsh의 경우: zsh shell 사용 → shell 설정 파일은 ~/.zshrc
- 환경 변수 추가 후 source “shell 설정 파일”로 shell 설정 업데이트
    - `source ~/.bashrc`
- Python 3.11.0 설치
    
    `pyenv install 3.11.0`
    
- 오류: zsh: command not found: python 발생 시
    1. `which python3` 를 통해 파이썬 설치 `경로` 확인 후
    2. `echo "alias python=경로" >> ~/.zshrc`
    
    [https://kingnamji.tistory.com/60](https://kingnamji.tistory.com/60)
    

### 파이썬 프로젝트 버전 관리

#### 가상 환경

- 파이썬 버전 다변화
- 설치 패키지 목록 다변화

#### 가상 환경 -venv 구조

- `brew install tree` 후 .venv 폴더가 포함된 경로에서 `tree .venv -L 3`

```json
.venv
├── bin
│   ├── Activate.ps1
│   ├── activate
│   ├── activate.csh
│   ├── activate.fish
│   ├── pip
│   ├── pip3
│   ├── pip3.11
│   ├── python -> python3.11
│   ├── python3 -> python3.11
│   └── python3.11 -> /opt/homebrew/opt/python@3.11/bin/python3.11
├── include
│   └── python3.11
├── lib
│   └── python3.11
│       └── site-packages
└── pyvenv.cfg

7 directories, 11 files
```

- bin: shell에서 명령어(python 등) 입력 시 이 경로 내에서 제일 먼저 찾음.
- python 입력 시 어떤 python을 실행시키는지 알 수 있음(여기서는 pyenv로 설치한 파이썬).
- lib: 패키지 설치 시 이 경로에 설치. import 시 이 경로에서 제일 먼저 찾음.

#### 패키지 매니저

- pip
- poetry

#### pip의 한계

- 쉬운 사용성이 장점이나 한계가 존재
1. 개발 환경과 배포 환경의 패키지가 분리되지 않음
2. pip list로는 패키지 간 의존성을 알 수 없음
3. pip uninstall 시 의존성 있던 패키지들은 삭제되지 않음

→ 정리: pip로는 정교하게 패키지 관리를 하기 어려우며, 혼자 개발할 때는 크게 중요하지 않을 수 있으나, 협업하며 개발 할 때는 중요할 수 있음

#### poetry

- 상기 pip의 문제점을 해결하기 위한 pip 대체재
- 설치
    - MacOS, Linux
        
        ```json
        curl -sSl https://install.python-poetry.org | python3 -
        ```
        
        shell 설정 파일에서 아래 내용을 추가
        
        ```json
        export PATH=$PATH:$HOME/.poetry/bin
        ```
        
    - Windows
        
        Powershell에서
        
        ```json
        (Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
        ```
        
        환경 변수 PATH에 아래 내용을 추가
        
        ```json
        %USERPROFILE%\.poetry\bin
        ```
        
- `pip install` 대신 `poetry add`

#### 간단 정리

- 가상환경 — venv, conda, docker, pyenv
- 패키지 매니저 — pip, poetry


## 참고
- 부스트캠프 - AI 서비스 개발 기초 by 변성윤