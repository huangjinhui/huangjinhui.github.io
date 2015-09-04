---
title:  "How to make vim transparent in linux"
date:   2015-09-05 00:57:00
categories: how-to
---

* If you don't use any `colorscheme` in your `.vimrc`, just add 
    {% highlight c %}
    hi Normal ctermbg=non
    {% endhighlight %}
in your `.vimrc`.

* If you use colorscheme [molokai](https://github.com/tomasr/molokai), edit your `.vim/colors/molokai.vim`:

find these two lines:
    {% highlight c %}
    hi Normal  ctermfg=252 ctermbg=233
    hi NonText ctermfg=250 ctermbg=234
    {% endhighlight %}
change them to:

```
hi Normal  ctermfg=252 ctermbg=none
hi NonText ctermfg=250 ctermbg=none
```

* If you use colorscheme [solarized](https://github.com/altercation/solarized), please looking further and remember to tell me how:)

{% highlight c %}

static void asyncEnabled(Dict* args, void* vAdmin, String* txid, struct Allocator* requestAlloc)
{
    struct Admin* admin = Identity_check((struct Admin*) vAdmin);
    int64_t enabled = admin->asyncEnabled;
    Dict d = Dict_CONST(String_CONST("asyncEnabled"), Int_OBJ(enabled), NULL);
    Admin_sendMessage(&d, txid, admin);
}

{% endhighlight %}
