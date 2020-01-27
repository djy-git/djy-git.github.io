---
title: Project structure with Tensorflow
tags: Python
aside:
  toc: true
---

# Remarks
이 글은 [CS230 강의](https://cs230.stanford.edu/blog/tensorflow/#part-i---tensorflow-tutorial)를 기반으로 작성되었습니다.

<!--more-->

---

# I. Directory structure

```java
project
├── build_dataset.py
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
├── requirements.txt
├── search_hyperparams.py
├── synthesize_results.py
└── train.py

8 directories, 1215 files
```

# II. Procedures
## 1. Preprocessing dataset
```sh
python build_dataset.py --data_dir data/SIGNS --output_dir data/64x64_SIGNS
```
`build_dataset.py` preprocesses the dataset in the `data` directory and outputs to `data` directory. <br>
<br>
After executing `build_dataset.py`, the `output_dir` is as follows <br>

```java
64x64_SIGNS/
├── dev_signs
│   ├── dev_0001.jpg
│   ├── ...
│   └── dev_0216.jpg
├── test_signs
│   ├── test_0001.jpg
│   ├── ...
│   └── test_0120.jpg
└── train_signs
    ├── train_0001.jpg
    ├── ...
    └── train_0864.jpg

3 directories, 1200 files
```


## 2. Storing hyperparameters during experiments
### 1) Train your experiment

```sh
python train.py --data_dir data/64x64_SIGNS --model_dir experiments/base_model
```

For experiments, store the hyperparameters in the `experiments` directory with `*.json` format. <br>
`params.json` is as follows <br>

```json
{
    "learning_rate": 1e-3,
    "batch_size": 32,
    "num_epochs": 10,
    ...
}
```

And store other log files and weights in the same directory. <br>
<br>
After executing `train.py`, the `model_dir` is as follows <br>

```json
base_model
├── best_weights
│   ├── after-epoch-8.data-00000-of-00001
│   ├── after-epoch-8.index
│   ├── after-epoch-8.meta
│   └── checkpoint
├── eval_summaries
│   └── events.out.tfevents.1580108461.server
├── last_weights
│   ├── after-epoch-10.data-00000-of-00001
│   ├── after-epoch-10.index
│   ├── after-epoch-10.meta
│   ├── after-epoch-6.data-00000-of-00001
│   ├── after-epoch-6.index
│   ├── after-epoch-6.meta
│   ├── after-epoch-7.data-00000-of-00001
│   ├── after-epoch-7.index
│   ├── after-epoch-7.meta
│   ├── after-epoch-8.data-00000-of-00001
│   ├── after-epoch-8.index
│   ├── after-epoch-8.meta
│   ├── after-epoch-9.data-00000-of-00001
│   ├── after-epoch-9.index
│   ├── after-epoch-9.meta
│   └── checkpoint
├── metrics_eval_best_weights.json
├── metrics_eval_last_weights.json
├── params.json
├── train.log
└── train_summaries
    └── events.out.tfevents.1580108461.server

4 directories, 26 files
```

### 2) Hyperparameter tuning
```sh
python search_hyperparams.py --data_dir data/64x64_SIGNS --parent_dir experiments/learning_rate
```

`search_hyperparams.py` tunes hyperparameters with values defined in `search_hyperparams.py`. <br>
<br>
After executing `search_hyperparams.py`, `parent_dir` is as follows <br>

```java

```

### 3) Display the results


---
===
===
