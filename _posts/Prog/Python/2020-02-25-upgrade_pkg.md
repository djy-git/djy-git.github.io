---
title: Python package management
tags: Python
---

<!--more-->

## 1. Create / Remove anaconda environment

    // Update all packages in {base}
    (base) $ conda update conda

    // Create enviornment clonning base
    $ conda create -n {ENV_NAME} --clone {base}

    // Remove environment
    $ conda env remove -n {ENV_NAME}

## 2. Add / Remove kernel to jupyter notebook

    $ conda activate {ENV_NAME}
    $ pip install ipykernel

    // Add kernel
    $ python -m ipykernel install --user --name {ENV_NAME} --display-nem "{DISPLAY_NAME}"

    // Remove kernel
    $ jupyter kernelspec uninstall {DISPLAY_NAME}

## 3. pip upgrade

    $ pip install --upgrade pip

## 4. Anaconda upgrade

    $ conda update conda

## 5. All packages in selected environment upgrade

    // update all packages in {base}
    (base) $ conda update --all

    // update all packages in {ENV_NAME}
    (base) $ conda update -n {ENV_NAME} --all

## 6. Upgrade selected package

    $ pip install --upgrade {PKG_NAME}
