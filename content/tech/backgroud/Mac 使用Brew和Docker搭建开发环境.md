---
title: "Mac 使用Brew和Docker搭建开发环境"
date: 2020-03-21T18:05:31+08:00
draft: true
---

## 前言

自己原来是用 `docker` 搭建的开发环境。只是后来在开发 laravel 项目的时候那，larave 需要引入其他文件。而文件的同步在 mac 上面特别费时间。经常就是一次请求就是好几秒。极大的影响开发效率。[^1]

## 安装 PHP

安装

```
brew install php@7.4
```

配置文件位置

```
==> /usr/local/Cellar/php/7.4.3/bin/pear config-set php_ini /usr/local/etc/php/7.4/php.ini system
==> /usr/local/Cellar/php/7.4.3/bin/pear config-set php_dir /usr/local/share/pear system
==> /usr/local/Cellar/php/7.4.3/bin/pear config-set doc_dir /usr/local/share/pear/doc system
==> /usr/local/Cellar/php/7.4.3/bin/pear config-set ext_dir /usr/local/lib/php/pecl/20190902 system
==> /usr/local/Cellar/php/7.4.3/bin/pear config-set bin_dir /usr/local/opt/php/bin system
==> /usr/local/Cellar/php/7.4.3/bin/pear config-set data_dir /usr/local/share/pear/data system
==> /usr/local/Cellar/php/7.4.3/bin/pear config-set cfg_dir /usr/local/share/pear/cfg system
==> /usr/local/Cellar/php/7.4.3/bin/pear config-set www_dir /usr/local/share/pear/htdocs system
==> /usr/local/Cellar/php/7.4.3/bin/pear config-set man_dir /usr/local/share/man system
==> /usr/local/Cellar/php/7.4.3/bin/pear config-set test_dir /usr/local/share/pear/test system
==> /usr/local/Cellar/php/7.4.3/bin/pear config-set php_bin /usr/local/opt/php/bin/php system
```

brew services start php

---

[^1]: [Mac 下 Docker 运行 Laravel 程序很慢（PHP/Nginx）](https://crifan.github.io/http_restful_api/website/)
