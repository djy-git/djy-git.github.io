---
title: Upgrade packages
tags: Python
---

<!--more-->

## 1. pip upgrade

    $ pip install --upgrade pip

## 2. Anaconda upgrade

    $ conda update conda

## 3. All packages in selected environment upgrade

    // update all packages in {base}
    (base) $ conda update --all

    // update all packages in {ENV_NAME}
    (base) $ conda update -n {ENV_NAME} --all

## 4. Upgrade selected package

    $ pip install --upgrade {PKG_NAME}
