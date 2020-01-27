---
title: Project structure with Tensorflow
tags: Python
---

# Remarks
이 글은 [CS230 강의](https://cs230.stanford.edu/blog/tensorflow/#part-i---tensorflow-tutorial)를 기반으로 작성되었습니다.

<!--more-->

---

# I. Directory structure

```java
.
├── build_dataset.py            : resize the images
├── data
│   └── signs_dataset
│       ├── test_signs
│       │   ├── test_0001.jpg
│       │   ├── ...
│       │   └── test_0120.jpg
│       └── train_signs
│           ├── train_0001.jpg
│           ├── ...
│           └── train_1080.jpg
├── evaluate.py
├── experiments
│   ├── base_model
│   │   └── params.json
│   └── learning_rate
│       └── params.json
├── model
│   ├── evaluation.py
│   ├── __init__.py
│   ├── input_fn.py
│   ├── model_fn.py
│   ├── training.py
│   └── utils.py
├── README.md
├── requirements.txt            : python modules dependency requirement
├── search_hyperparams.py
├── synthesize_results.py
└── train.py

8 directories, 1215 files
```

# II. Files
## 1. `build_dataset.py`
