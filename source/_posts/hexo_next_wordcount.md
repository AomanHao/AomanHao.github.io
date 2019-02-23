---
title: 字数统计和阅读时长(网站底部/文章内)
date: 2019-01-30 21:55:00
tags: [GitHub, Hexo, Next]
---

字数统计和阅读时长（旧版本新版本）
<!--more-->
插件地址：
https://github.com/theme-next/hexo-symbols-count-time
安装插件

```
npm install hexo-symbols-count-time --save
```

修改 站点配置文件
```
symbols_count_time:
 #文章内是否显示
  symbols: true
  time: true
 # 网页底部是否显示
  total_symbols: true
  total_time: true
```
修改 主题配置文件
```
# Post wordcount display settings
# Dependencies: https://github.com/theme-next/hexo-symbols-count-time
symbols_count_time:
  separated_meta: true
  #文章中的显示是否显示文字（本文字数|阅读时长） 
  item_text_post: true
  #网页底部的显示是否显示文字（站点总字数|站点阅读时长） 
  item_text_total: false
  # Average Word Length (chars count in word)
  awl: 4
  # Words Per Minute
  wpm: 275
```