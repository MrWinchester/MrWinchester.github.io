---
layout:     post
title:      "Jekyll Use"
subtitle:   "ubuntu12.04+Github+Jekyll-bootstrap记录"
date:       2014-10-29 22:48:00
author:     "winchester"
header-img: "img/stone.jpg"
---


# ubuntu12.04+Github+Jekyll-bootstrap记录
---
- 本地环境安装   
jekyll需要的安装的ruby是>=1.9.2,所以当务之急是先升级一下ubuntu的ruby环境  
`sudo apt-get remove ruby`  
没用  
`whereis ruby`以及`ruby -v`  
还是能够显示ruby的版本出来,换一种方法,直接下载安装覆盖,但是由于ubuntu12.04自带的是ruby1.8,所以需要添加一个新源进来:
<pre><code>sudo apt-add-repository ppa:brightbox/ruby-ng
sudo apt-get update
sudo apt-get install ruby2.1 ruby2.1-dev
sudo gem install bundler
ruby -v</code></pre>
ruby更新完毕,接下来安装一下jekyll  
`sudo gem install jekyll`   
卡主了,很慢,原因是天朝的网络,你懂的,现在需要替换一下rubygems.org的镜像:
<pre><code>$ gem sources --remove https://rubygems.org/
$ gem sources -a https://ruby.taobao.org/
$ gem sources -l
$ gem install jekyll</code></pre>
总算是前进了一小步,松口气,继续...　　
---
- Jekyll-bootstrap
<pre><code>$ git clone https://github.com/plusjade/jekyll-bootstrap.git USERNAME.github.com
$ cd USERNAME.github.com
$ git remote set-url origin git@github.com:USERNAME/USERNAME.github.com.git
$ git push origin master </code></pre>
此处如果遇到 permission denied,参考最后的第三个链接  
- 访问http://USERNAME.github.com ，github已经为你生成了一个站点。 
---
- 参考链接
    + [Ubuntu 上安装 Ruby 最新版的最佳方法](http://chloerei.com/2014/07/13/the-best-way-to-install-the-latest-version-of-ruby-on-ubuntu/)
    + [RubyGems 镜像](http://ruby.taobao.org/)
    + [使用Git搭建我的静态网站-搭建基本环境](http://www.cnblogs.com/flyher/p/3361140.html)
