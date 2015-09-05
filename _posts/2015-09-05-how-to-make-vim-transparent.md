---
title:  "How to make vim transparent in linux"
date:   2015-09-05 00:57:00
---

* If you don't use any `colorscheme` in your `.vimrc`, just add 
{% highlight sh %}
hi Normal ctermbg=none
{% endhighlight %}
in your `.vimrc`.

* If you use colorscheme [molokai](https://github.com/tomasr/molokai), edit your `.vim/colors/molokai.vim`:

find these two lines:
{% highlight sh %}
hi Normal  ctermfg=252 ctermbg=233
hi NonText ctermfg=250 ctermbg=234
{% endhighlight %}

    change them to:

{% highlight sh %}
hi Normal  ctermfg=252 ctermbg=none
hi NonText ctermfg=250 ctermbg=none
{% endhighlight %}

* If you use colorscheme [solarized](https://github.com/altercation/solarized), please looking further and remember to tell me how:)
