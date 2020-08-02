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
  {%- for link in site.data.links %}
  <li>
    <a href="{{ link.url }}" target="_blank" >{{ link.title }}</a><p align="right">{{ link.describe }}</p>
  </li>
  {%- endfor %}
</ul>

p.s. 括号里的是moi自己加的（