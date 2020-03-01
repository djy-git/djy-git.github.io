---
title: Machine learning project structure
tags: ML_prog
aside:
  toc: true
---

[CS230 tensorflow project](https://github.com/cs230-stanford/cs230-code-examples)를 참고하면서 제 나름대로 Machine learning project의 토대가 되는 구조를 만들어보았습니다. <br>

<!--more-->

---

# 1. Structure

```java
ROOT_DIR
├── env.py
├── utils.py
├── logger.py
├── main.py
├── data
│   └── original
│       ├── sample_submission.csv
│       ├── test.csv
│       └── train.csv
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
## 2.1. 'ROOT_DIR' directory
### - `env.py`
Python script where general packages, constants, variables, settings are declared. <br>
`env.py` includes importing `utils.py`
Other python script files import `env.py` in first with
```
import sys
sys.path.append(ROOT_DIR)
```
(this should be changed in better way)
<br>

### - `utils.py`
Python script where general functions are declared.
<br>

### - `logger.py`
Python script where `Logger` class besides. `Logger` records all train, validation loss and the parameter at that time.
<br>

### - `main.py`
Python script where final evaluation takes place. Here, trained models are loaded and evaluated using test data.
<br>

## 2.2. 'data' directory
`data` stores train, test data and any other data.
<br>

## 2.3. 'models' directory
Directory where training models place. Each model has `train.py`, `tuning.py`, `processor.py`. <br>
Neural Network(NN) model has `network.py` which defines network and other related functions.
<br>

### - `models/MODEL/processor.py`
Python script where (pre)processing pipelines and functions for `MODEL` reside.
<br>

### - `models/MODEL/train.py`
Python script where a model is trained with a specific hyperparameter given by `argparser`.
<br>

### - `models/MODEL/tuning.py`
Python script where a model searches the best hyperparameter in hyperparameter set.
<br>

### - `models/NN/network`
Python script where deep learning models and `Callbacks` generator functions reside.

## 2.4. ``
