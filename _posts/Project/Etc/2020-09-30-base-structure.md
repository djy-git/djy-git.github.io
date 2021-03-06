---
title: Base structure for ML project
tags: Project_Etc
---

<!--more-->

프로젝트를 몇 번 진행하면서 쳬계적인 구조의 중요성와 모듈화에 대한 필요성을 절실하게 느끼게 되었습니다.  

프로젝트의 기본 구조에 대해 여기저기 찾아보았는데 뭔가 제 맘에 딱 드는 게 없더라고요. 그래서 [CS230 tensorflow project](https://github.com/cs230-stanford/cs230-code-examples) 등과 제 경험을 토대로 하여 **Python 기반 Machine Learning project의 기본 구조**를 새로 만들었습니다.

Source code는 [여기](https://github.com/djy-git/base-strcture-for-ML-project)에 있습니다.

---

자세한 설명은 [README.md](https://github.com/djy-git/base-strcture-for-ML-project)를 참고해주세요.  
여기에선 directory structure만 올려놓겠습니다.


    ROOT
    ├── README.md
    │
    ├── algorithm
    │   ├── README.md
    │   └── dummy.algo
    │
    ├── doc-sphinx
    │   └── ...
    │
    ├── etc
    │   └── ...
    │
    ├── input
    │   └── ...
    │
    ├── log
    │   └── ...
    │
    ├── output
    │   └── ...
    │
    ├── playground
    │   ├── env.py
    │   ├── playground.ipynb
    │   └── playground.py
    │
    ├── setup.py
    │
    └── src
        ├── configs
        │   ├── __init__.py
        │   ├── config.py
        │   └── config_user.py
        ├── envs
        │   ├── __init__.py
        │   ├── SignalHandler.py
        │   ├── Logger.py
        │   ├── base_env.py
        │   ├── util.py
        │   └── env.py
        └── main.py
