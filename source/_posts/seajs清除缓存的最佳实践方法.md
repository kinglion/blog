title: "seajs清除缓存的最佳实践方法"
date: 2015-08-26 11:52:02
tags: seajs 缓存
categories: fedev
---
最近项目用到了seajs,需要在移动端测试，缓存问题再移动端清理起来比较麻烦，毕竟没有“硬性清空缓存”大法，seajs的config里面有个map参数刚好可以轻松解决这个问题

```
seajs.config({
  alias: {
    'jquery': 'jquery/1.6.2/jquery',
    'backbone': 'backbone/0.5.1/backbone'
  },
  map: [
    [ /^(.*\/app\/xxx\/.*\.(?:css|js))(?:.*)$/i, '$1?20110802' ]
  ]
});
```

原本项目不用进行任何改动便能兼容