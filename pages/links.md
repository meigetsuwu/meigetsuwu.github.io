---
layout: mypost
title: Links
---

# 广告位招租（

```
name: "M E S"
icon: https://i.loli.net/2020/03/08/VRT2zfWZiLrUJPX.jpg
url: https://rain.moimo.me
describe: moi的一般通过小站
```

<ul>
  {%- for link in site.links %}
  <li>
    <p><a href="{{ link.url }}" title="{{ link.desc }}" target="_blank" >{{ link.title }}</a></p>
  </li>
  {%- endfor %}
</ul>
