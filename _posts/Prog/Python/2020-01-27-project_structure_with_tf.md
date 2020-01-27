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


## 2. Train and store hyperparameters
### 1) Train your experiment

```sh
python train.py --data_dir data/64x64_SIGNS --model_dir experiments/base_model
```

For experiments, store the hyperparameters with `*.json` format and other log files and weights in the `experiments` directory. <br>
`params.json` is as follows <br>

```json
{
    "learning_rate": 1e-3,
    "batch_size": 32,
    "num_epochs": 10,
    ...
}
```

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
│   ├── ...
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

```json
learning_rate
├── learning_rate_0.0001
│   ├── best_weights
│   │   ├── after-epoch-10.data-00000-of-00001
│   │   ├── after-epoch-10.index
│   │   ├── after-epoch-10.meta
│   │   └── checkpoint
│   ├── eval_summaries
│   │   └── events.out.tfevents.1580110599.server
│   ├── last_weights
│   │   ├── after-epoch-10.data-00000-of-00001
│   │   ├── after-epoch-10.index
│   │   ├── after-epoch-10.meta
│   │   ├── ...
│   │   ├── after-epoch-9.data-00000-of-00001
│   │   ├── after-epoch-9.index
│   │   ├── after-epoch-9.meta
│   │   └── checkpoint
│   ├── metrics_eval_best_weights.json
│   ├── metrics_eval_last_weights.json
│   ├── params.json
│   ├── train.log
│   └── train_summaries
│       └── events.out.tfevents.1580110599.server
│
├── learning_rate_0.001
│   ├── best_weights
│   │   ├── after-epoch-6.data-00000-of-00001
│   │   ├── after-epoch-6.index
│   │   ├── after-epoch-6.meta
│   │   └── checkpoint
│   ├── eval_summaries
│   │   └── events.out.tfevents.1580110622.server
│   ├── last_weights
│   │   ├── after-epoch-10.data-00000-of-00001
│   │   ├── after-epoch-10.index
│   │   ├── after-epoch-10.meta
│   │   ├── ...
│   │   ├── after-epoch-9.data-00000-of-00001
│   │   ├── after-epoch-9.index
│   │   ├── after-epoch-9.meta
│   │   └── checkpoint
│   ├── metrics_eval_best_weights.json
│   ├── metrics_eval_last_weights.json
│   ├── params.json
│   ├── train.log
│   └── train_summaries
│       └── events.out.tfevents.1580110622.server
│
├── learning_rate_0.01
│   ├── best_weights
│   │   ├── after-epoch-10.data-00000-of-00001
│   │   ├── after-epoch-10.index
│   │   ├── after-epoch-10.meta
│   │   └── checkpoint
│   ├── eval_summaries
│   │   └── events.out.tfevents.1580110645.server
│   ├── last_weights
│   │   ├── after-epoch-10.data-00000-of-00001
│   │   ├── after-epoch-10.index
│   │   ├── after-epoch-10.meta
│   │   ├── ...
│   │   ├── after-epoch-9.data-00000-of-00001
│   │   ├── after-epoch-9.index
│   │   ├── after-epoch-9.meta
│   │   └── checkpoint
│   ├── metrics_eval_best_weights.json
│   ├── metrics_eval_last_weights.json
│   ├── params.json
│   ├── train.log
│   └── train_summaries
│       └── events.out.tfevents.1580110645.server
└── params.json

15 directories, 79 files
```

### 3) Display the results
```sh
python synthesize_results.py --parent_dir experiments/learning_rate

|                                                |   accuracy |     loss |
|:-----------------------------------------------|-----------:|---------:|
| experiments/learning_rate/learning_rate_0.01   |   0.930556 | 0.195321 |
| experiments/learning_rate/learning_rate_0.0001 |   0.893519 | 0.390281 |
| experiments/learning_rate/learning_rate_0.001  |   0.953704 | 0.174108 |

```

Print `accuracy` and `loss` for different values of a hyperparameter

### 4) Evaluation on the test set
```sh
python evaluate.py --data_dir data/64x64_SIGNS --model_dir experiments/base_model
```

We can get the final accuracy and loss on the test set

---

여기까지 내용은 `Tensorflow 1.15` 로 구현된 코드이고, Eager Execution이 기본이 된 `Tensorflow 2`에서는 `tf.data`라는 API가 복잡한 input pipeline을 간단하고 재활용 가능하게 만들어준다. <br>
<br>
`tf.data` pipeline에 대한 introduction
- [programmer's guide](https://www.tensorflow.org/programmers_guide/datasets)
- [reading images](https://www.tensorflow.org/programmers_guide/datasets#decoding_image_data_and_resizing_it)
