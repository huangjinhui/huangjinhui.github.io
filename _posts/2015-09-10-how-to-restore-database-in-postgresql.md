---
title:  "How to resotre database in postgresql"
date:   2015-09-10
categories: how-to
tags: [postgresql]
---

in ubuntu:

### Installation

``` console
sudo apt-get update
sudo apt-get install postgresql postgresql-contrib
```

### Login and change password

{% highlight console %}
huang$ sudo su
root@t400:~# 
root@t400:~# su - postgres
No protocol specified
xrdb: Resource temporarily unavailable
xrdb: Can't open display ':0.0'
postgres@t400:~$ 
postgres@t400:~$ psql
postgres=#
postgres=# \password postgres
Enter new password: 
Enter it again: 
{% endhighlight %}


### restore
{% highlight sh %}
postgres@t400:~$ createdb PGCloudmigration
postgres@t400:~$ psql PGCloudmigration < /home/huang/dev/da/code/Nefolog/sql/PGCloudmigrationDB.bak
{% endhighlight %}

## test redcarpet

``` java
public class Test {
    private int i = 0;
    public static void main(String[] args) {
        System.out.println("i");
    }
}
```


``` bash
sudo u
```

