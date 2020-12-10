---
title: Class attributes to dictionary
tags: Python
---

<!--more-->

{% highlight python linenos %}
class G:
  A = 10
  B = 20
  
  @claamethod
  def f():
    pass
  

dic = {key: val for key, val in vars(G).items()
  if not key.startswith('__') and 'function' not in type(val).__name__ and 'method' not in type(val).__name__}
{% endhighlight %}[^1]
