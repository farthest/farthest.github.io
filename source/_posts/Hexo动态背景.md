abbrlink: 1
title: next主题添加动态背景
date: 2018-02-10 15:34:18
---
# next主题添加动态背景

## next主题在5.1.1以上

直接在主题配置文件中找到canvas_nest: false，把它改为canvas_nest: true

## 修改_layout.swig

打开 next/layout/*_layout.swig*
在 < /body>之前添加代码(注意不要放在< /head>的后面)
```
{% if theme.canvas_nest %}
<script type="text/javascript" src="//cdn.bootcss.com/canvas-nest.js/1.0.0/canvas-nest.min.js"></script>
{% endif %}


{% if theme.canvas_nest %}
<script type="text/javascript"
color="0,0,255" opacity='0.7' zIndex="-2" count="99" src="//cdn.bootcss.com/canvas-nest.js/1.0.0/canvas-nest.min.js"></script>
{% endif %}
```


## 配置项说明

color ：线条颜色, 默认: '0,0,0'；三个数字分别为(R,G,B)
opacity: 线条透明度（0~1）, 默认: 0.5
count: 线条的总数量, 默认: 150
zIndex: 背景的z-index属性，css属性用于控制所在层的位置, 默认: -1
