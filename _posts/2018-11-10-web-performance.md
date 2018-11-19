---
layout: post
title: "Web性能准则"
date: 2018-11-10 10:00:00
categories: web
---

- 请熟读[Yahoo 性能准则][yahoo-performance-rules]
- 请熟读[PageSpeed 性能准则][pagespeed-rules]
- 请熟读 Steve Souders 的书[High Performance Web Sites][high-performance-web-sites]
- 尽信书不如无书，保持怀疑
- 打破任何规则之前，请熟知该规则

- 了解 [HTTP2][http2]
- 留意爬虫带来的开销
- 使用`window.performance`
- 前端单点故障：一个资源的下载阻塞了页面。解决方案：异步加载。
- 读写 `localStorage` 等于读写磁盘文件
- Facebook JavaScript SDK

  {% highlight js %}

  <script>
  (function(d, s, id) {
      var js, fjs = d.getElementByTagName(s)[0];
      if (d.getElementById(id)) return;
      js = d.createElement(s); js.id = id;
      js.src = '//facebook.net/all.js;'
      fjs.parentNode.insertBefore(js, fjs);
  }(document, 'script', 'facebook-jssdk'));
  </script>

  {% endhighlight %}

[high-performance-web-sites]: http://www.stevesouders.com/
[http2]: https://http2.github.io/
[yahoo-performance-rules]: https://developer.yahoo.com/performance/rules.html
[pagespeed-rules]: https://developers.google.com/speed/docs/insights/rules
