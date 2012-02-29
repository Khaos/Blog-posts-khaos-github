---
layout: post
title: "Install Ruby with RVM"
date: 2012-02-26 09:33
comments: true
categories: learning
tags: [Ruby, RVM, MacPorts]
---

自打从 [Yihui Xie](http://yihui.name/) 那里听说了[Jekyll](http://jekyllrb.com/)，并照着 [Jekyll Bootstrap](http://jekyllbootstrap.com/) 折腾了一番，便喜欢上了这个静态网站构建系统。不久从[Lucifr](http://lucifr.com/)看到[Octopress](http://octopress.org/)这个变身版的Jekyll，于是就更加要齐齐苦苦了。Octopress依赖于Ruby 1.9.2+，所以这里介绍一下如何用[Ruby Version Manager (RVM)](https://rvm.beginrescueend.com/)

<!-- more -->

## Uninstall all ruby-related MacPorts' ports

由于我的Ruby是用MacPorts安装的，所以首先需要把这个版本的Ruby卸载掉。

### 卸载相关Ports

    $ sudo port uninstall rb19-*
    $ sudo port clean rb19-*
    $ sudo port uninstall ruby19
    $ sudo port clean ruby19
    $ sudo port uninstall rb-*
    $ sudo port clean rb-*
    $ sudo port uninstall ruby
    $ sudo port clean ruby

### 移除Gems

    $ sudo rm -rf /opt/local/lib/ruby
    $ sudo rm -rf /opt/local/lib/ruby19
    $ sudo rm -rf /opt/local/bin/rdiscount
    $ sudo rm -rf /opt/local/bin/jekyll

## Install RVM

打开Terminal，确定处于当前用户目录下 (~)，运行如下命令

    $ bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer )

在所有打开的Terminal中运行

    $ source /Users/Khaos/.rvm/scripts/rvm

可以用如下命令查看是否RVM已经安装配置成功

    $ type rvm | head -1

如果返回`rvm is a function`，就说明成功了。

查看RMV requirements

    $ rvm requriements

在我的Mac上提示需要libksba，可以通过MacPorts安装

    $ sudo port install libksba

利用RVM安装Ruby (e.g., 1.9.3)

    $ rvm install 1.9.3

## Use newly installed Ruby

    $ rvm use 1.9.2

  check ruby version
    $ ruby -v
    $ which ruby

## Problems

- ArgumentError: invalid byte sequence in US-ASCII

  See [https://github.com/rails/jquery-rails/pull/35](https://github.com/rails/jquery-rails/pull/35)

## References

- [RVM official site](https://rvm.beginrescueend.com/)
- [Installing RVM](https://rvm.beginrescueend.com/rvm/install/)
- [Ruby on Mac OSX via Mac Ports](http://stackoverflow.com/questions/3464285/ruby-on-mac-osx-via-mac-ports)
- [Using MacPorts To Install Ruby 1.9.x](http://www.alessandrobaffa.it/2011/04/18/using-macports-to-install-ruby-1-9-x/)
- [Using MacPorts To Install Ruby 1.9.1 and Rails 2.3.0 RC1](http://www.ruby-forum.com/topic/178659#782331)
