---
titile: "How to automatically start tomcat in Centos7"
date: 2015-09-11
categories: how-to
tags: [centos]
---

首先下载 tomcat

``` console
# cd /opt
# wget http://mirror.arcor-online.net/www.apache.org/tomcat/tomcat-7/v7.0.64/bin/apache-tomcat-7.0.64.tar.gz
# tar zx -f apache-tomcat-7.0.64.tar.gz
```

然后设置开机启动

``` console
# cd /etc/init.d
# vi tomcat
```

输入如下内容

``` bash
    #!/bin/bash
    # chkconfig: 234 20 80
    # description: Tomcat Server basic start/shutdown script
    # processname: tomcat
    TOMCAT_HOME=/opt/apache-tomcat-7.0.64/bin
    START_TOMCAT=/opt/apache-tomcat-7.0.64/bin/startup.sh
    STOP_TOMCAT=/opt/apache-tomcat-7.0.64/bin/shutdown.sh
    start() {
    echo -n "Starting tomcat: "
    cd $TOMCAT_HOME
    ${START_TOMCAT}
    echo "done."
    }
    stop() {
    echo -n "Shutting down tomcat: "
    
    cd $TOMCAT_HOME
    ${STOP_TOMCAT}
    echo "done."
    }
    case "$1" in
    start)
    start
    ;;
    stop)
    stop
    ;;
    restart)
    stop
    sleep 10
    start
    ;;
    *)
    echo "Usage: $0 {start|stop|restart}"
    esac
    exit 0
```

改变新建的tomcat文件的权限

``` console
# chmod 755 tomcat
```

设置开机启动

``` console
# chkconfig --add tomcat
# chkconfig --level 234 tomcat on
```

设置防火墙

``` console
# firewall-cmd --zone=public --add-port=8080/tcp --permanent
# firewall-cmd --reload
```

## _Reference_

1. [how to install tomcat on centos 7](/clipped_html/201509/How To Install Tomcat On CentOS 7.html) 
2. [CentOS - Tomcat 6](/clipped_html/201509/CentOS - Tomcat 6  Knowledge Center  Rackspace Hosting.html)

