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
  

dic = {key: val for key, val in vars(G).items() if not key.startswith('__') and not callable(val)}
{% endhighlight %}[^1]
