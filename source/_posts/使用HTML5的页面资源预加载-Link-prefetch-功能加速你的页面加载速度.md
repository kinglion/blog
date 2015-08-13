title: 使用HTML5的页面资源预加载(Link prefetch)功能加速你的页面加载速度
date: 2015-03-02 11:22:50
tags: HTML5 页面资源 预加载
categories: fedev
---
不管是浏览器的开发者还是普通web应用的开发者，他们都在做一个共同的努力：让Web浏览有更快的速度感觉。有很多已知的技术都可以让你的网站速度变得更快：使用CSS sprites，使用图片优化工具，使用.htaccess设置页面头信息和缓存时间，JavaScript压缩，使用CDN等。我曾经介绍过本站上使用的一些速度优化技术。而在HTML5里，出现了一个新的用来优化网站速度的新功能：页面资源预加载/预读取(Link prefetch)。
页面资源预加载/预读取(Link prefetch)是什么？来自MDN的解释:
>页面资源预加载(Link prefetch)是浏览器提供的一个技巧，目的是让浏览器在空闲时间下载或预读取一些文档资源，用户在将来将会访问这些资源。一个Web页面可以对浏览器设置一系列的预加载指示，当浏览器加载完当前页面后，它会在后台静悄悄的加载指定的文档，并把它们存储在缓存里。当用户访问到这些预加载的文档后，浏览器能快速的从缓存里提取给用户。
简单说来就是：让浏览器预先加载用户访问当前页后极有可能访问的其他资源(页面，图片，视频等)。而且方法超级的简单！

##HTML5页面资源预加载(Link prefetch)写法

```
<!-- 预加载整个页面 -->
<link rel="prefetch" href="http://www.webhek.com/misc/3d-album/" />

<!-- 预加载一个图片 -->
<link rel="prefetch" href=" http://www.webhek.com/wordpress/
wp-content/uploads/2014/04/b-334x193.jpg " />
```
HTML5页面资源预加载/预读取(Link prefetch)功能是通过Link标记实现的，将rel属性指定为“prefetch”，在href属性里指定要加载资源的地址。火狐浏览器里还提供了一种额外的属性支持：
```
<link rel="prefetch alternate stylesheet" 
title="Designed for Mozilla" href="mozspecific.css" />
<link rel="next" href="2.html" />
```
HTTPS协议资源下也可以使用prefetch。

##什么情况下应该预加载页面资源
在你的页面里加载什么样的资源，什么时候加载，这完全取决于你。下面是一些建议：

* 当页面有幻灯片类似的服务时，预加载/预读取接下来的1-3页和之前的1-3页。
* 预加载那些整个网站通用的图片。
* 预加载网站上搜索结果的下一页。

##禁止页面资源预加载(Link prefetch)
火狐浏览器里有一个选项可以禁止任何的页面资源预加载(Link prefetch)功能，你可以这样设置：
```
user_pref("network.prefetch-next", false);
```

##页面资源预加载(Link prefetch)注意事项
下面是一些关于页面资源预加载(Link prefetch)的注意事项：

* 预加载(Link prefetch)不能跨域工作，包括跨域拉取cookies。
* 预加载(Link prefetch)会污染你的网站访问量统计，因为有些预加载到浏览器的页面用户可能并未真正访问。
* 火狐浏览器从2003年开始就已经提供了对这项预加载(Link prefetch)技术的支持。