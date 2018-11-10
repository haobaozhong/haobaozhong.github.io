---
layout: post
title: "Web性能"
date: 2018-11-10 10:00:00
categories: web
---

- 尽信书不如无书，尽信规则不如无规则
- 在你打破任何规则之前，确保你熟知该规则
- 请参考[Yahoo 性能准则][yahoo-performance-rules]
- 请参考[PageSpeed 性能准则][pagespeed-rules]

- 读写 `localStorage` 等于读写磁盘文件
- Facebook JavaScript SDK

  {% highlight javascript %}

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

[yahoo-performance-rules]: https://developer.yahoo.com/performance/rules.html
[pagespeed-rules]: https://developers.google.com/speed/docs/insights/rules
