---
title: Callbacks
tags: Prog_ML
---

<!--more-->


`tensorflow2`로 넘어오면서 `tensorflow.keras.models`의 `Sequential` 등의 class를 사용하여 모델을 생성하는 것이 기본이 되었습니다. 이런 모델들을 학습하기 위해서 `.fit()`, `.fit_generator()` 와 같은 함수를 사용하는데요. <br>

이때 학습을 하면서 `tensorboard`를 위한 log 파일을 생성한다던지 early stopping, learning schedule 등의 부가 기능들을 모듈별로 구현해놓은 것이 `Callbacks` package 입니다. 물론 자신만의 callback을 생성할 수도 있습니다.<br>

사용법은 간단합니다. <br>
사용하고자 하는 callback들을 생성하고 list에 담아 `.fit()`의 `callbacks` argument에 넘겨주면 됩니다. <br>

다음은 몇 가지 callback을 사용한 예제 코드입니다. <br>


```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Activation
from tensorflow.keras.callbacks import Callback
from tensorflow.keras.callbacks import ModelCheckpoint, EarlyStopping, ReduceLROnPlateau, CSVLogger, TensorBoard
import matplotlib.pyplot as plt


class LossPlot(Callback):
    def __init__(self, PLOT_PATH):
        self.PLOT_PATH = PLOT_PATH
    def on_train_begin(self, logs={}):
        self.losses = []
        self.val_losses = []
        self.idx_min = -1
    def on_epoch_end(self, epoch, logs={}):
        self.losses.append(logs.get('loss'))
        self.val_losses.append(logs.get('val_loss'))
        self.idx_min = np.argmin(self.val_losses)
    def _save_fig(self):
        fig = plt.figure(figsize=(20, 10))
        plt.plot(self.losses, label='train');  plt.plot(self.val_losses, label='val')
        plt.axvline(self.idx_min, color='r', ls='--', lw=3)
        plt.xlabel('epochs');  plt.ylabel('loss')
        plt.grid();  plt.legend();
        plt.savefig(self.PLOT_PATH)
        plt.close(fig)


def generate_callbacks():
    best_ckpt = ModelCheckpoint('{CKPT_DIR}/epoch: {epoch:03d}, val_loss: {val_loss:.4f}.hdf5',
                                monitor='val_loss', save_best_only=False)
    csv_logger = CSVLogger(f'{CSV_DIR}/log.csv')
    early_stopping = EarlyStopping(monitor='val_loss', patience=EARLY_STOPPING_PATIENCE,
                                   restore_best_weights=True, verbose=1)
    lr_scheduler = ReduceLROnPlateau(monitor='val_loss', factor=LR_REDUCE_FACTOR,
                                     patience=LR_REDUCE_PATIENCE, verbose=1)
    tensorboard = TensorBoard(log_dir=TENSORBOARD_LOG_DIR, write_graph=True, write_images=True)
    loss_plot = LossPlot(PLOT_PATH)
    return [best_ckpt, csv_logger, early_stopping, lr_scheduler, tensorboard, loss_plot]


# 1. Generate the model
model = Sequential([
    Dense(128, input_shape=(28, 28), kernel_initializer='he_normal'),
    Activation('relu'),
    Dense(10),
    Activation('softmax')
])

# 2. Compile the model (link optimizer, loss to model)
model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])

# 3. Generate callbacks
callbacks = generate_callbacks()

# 4. Train the model
model.fit(X_train, y_train, epochs=10, validation_data=(X_val, y_val),
          batch_size=BATCH_SIZE, callbacks=callbacks,
          workers=5, use_multiprocessing=True)

# 5. Evaluate the model
model.evaluate(X_test, y_test, verbose=2)
```
