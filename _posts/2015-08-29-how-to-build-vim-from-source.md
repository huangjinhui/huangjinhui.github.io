---
title: "How to build vim from source in ubuntu 14.04"
date: 2015-08-29
categories: how-to
---

Why do i need to build vim from source:

 1. The default vim in ubuntu 14.04 can't use system clipbord.

 2. You can choose to `apt-get install` available packages like `vim-gnome` or `vim-gtk`, but i'm facing the annoying warning like:

>
`(gvim:9767): GLib-CRITICAL **: Source ID 51 was not found when attempting to remove it`.

the only solution i've found is to build it from source.

And it's not that difficult, here is how i did it:

* Install the required libraries, in ubuntu:

    {% highlight sh %}
    sudo apt-get install libncurses5-dev libgnome2-dev libgnomeui-dev \
    libgtk2.0-dev libatk1.0-dev libbonoboui2-dev \
    libcairo2-dev libx11-dev libxpm-dev libxt-dev python-dev \
    ruby-dev mercurial
    {% endhighlight %}

* Remove all the existing vi(m):
{% highlight sh %}
sudo apt-get remove vim vim-runtime gvim vim-tiny vim-common vim-gui-common
{% endhighlight %}
    in ubuntu 14.04 maybe you only need to remove the first 3.

* Get source code of vim

    go to a place where you want store your vim source code, and then:

{% highlight sh %}
git clone https://github.com/vim/vim.git
{% endhighlight %}

* Build and install:

{% highlight sh %}
cd vim
./configure --with-features=huge --enable-multibyte --enable-rubyinterp --enable-perlinterp --enable-luainterp --enable-pythoninterp --with-python-config-dir=/usr/lib/python2.7/config-i386-linux-gnu/ --enable-gui=gtk2 --enable-cscope --prefix=/usr
make VIMRUNTIMEDIR=/usr/share/vim/vim74
sudo make install
{% endhighlight %}

instead using `sudo make install`, you can make a `.deb` package like i did by using `checkinstall`, which makes it easily uninstalled.

{% highlight sh %}
sudo apt-get install checkinstall
sudo checkinstall
{% endhighlight %}

* Set vim as default editor:
{% highlight sh %}
sudo update-alternatives --install /usr/bin/editor editor /usr/bin/vim 1
sudo update-alternatives --set editor /usr/bin/vim
sudo update-alternatives --install /usr/bin/vi vi /usr/bin/vim 1
sudo update-alternatives --set vi /usr/bin/vim
{% endhighlight %}

_Reference:_

1. https://github.com/Valloric/YouCompleteMe/wiki/Building-Vim-from-source
2. http://www.cnblogs.com/zhongcq/p/3615980.html
3. http://segmentfault.com/a/1190000000487523
4. http://www.vim.org/git.php

