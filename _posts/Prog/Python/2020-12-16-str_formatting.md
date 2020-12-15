---
title: String formatting
tags: Python
---

<!--more-->

자주 쓰면서도 매번 까먹는 것 중 하나가 string formatting이다.  
매번 찾아보기 귀찮으니 사용할 때마다 하나씩 추가하려고 한다.


```Python
a = 0.11111
rst = str(f"{a:.3f}")  # 0.111
```

```python
a = 1111.1111
rst = str(f"{a:.3f}")  # 1111.111
```
