---
title: Machine learning project structure
tags: ML_prog
aside:
  toc: true
---

[CS230](https://github.com/cs230-stanford/cs230-code-examples)의 예제 코드를 참고하면서 제 나름대로 Machine learning project의 토대가 되는 구조를 만들어보았습니다. <br>

<!--more-->

---

# 1. Structure

```java
ROOT_DIR
├── data
│   └── original
│       ├── sample_submission.csv
│       ├── test.csv
│       └── train.csv
├── env.py
├── utils.py
├── logger.py
├── main.py
├── models
│   ├── NN
│   │   ├── network.py
│   │   ├── processor.py
│   │   ├── train.py
│   │   └── tuning.py
│   └── RandomForestClassifier
│       ├── processor.py
│       ├── train.py
│       └── tuning.py
└── experiments
    ├── log.csv
    ├── NN
    │   └── hyperparameter_set1
    │       ├── learning_curve.png
    │       ├── log.csv
    │       ├── model
    │       │   ├── best_weight.ckpt
    │       │   │   ├── assets
    │       │   │   ├── saved_model.pb
    │       │   │   └── variables
    │       │   │       ├── variables.data-00000-of-00002
    │       │   │       ├── variables.data-00001-of-00002
    │       │   │       └── variables.index
    │       │   └── model.h5
    │       └── params.json
    └── RandomForestClassifier
        └── hyperparameter_set1
            ├── model.joblib
            └── params.json
```

# 2. Description
- `data`
Directory which store train, test data and any other data.
<br>

- `env.py`
Python script where general packages, constants, variables, settings are declared. <br>
`env.py` includes importing `utils.py`
Other python script files import `env.py` in first with
```
import sys
sys.path.append(ROOT_DIR)
```
(this should be changed in better way)
<br>

- `utils.py`
Python script where general functions are declared.
<br>

- `logger.py`
Python script where `Logger` class besides. `Logger` records all train, validation loss and the parameter at that time.
<br>

- `main.py`
Python script where final evaluation takes place. Here, trained models are loaded and evaluated using test data.
