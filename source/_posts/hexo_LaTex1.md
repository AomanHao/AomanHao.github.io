---
title: 使用LaTex添加公式到Hexo博客里
date: 2018-07-23 09:39:40
tags: [GitHub, Hexo]
toc: true
---

使用LaTex添加公式到Hexo博客里

<!--more-->
<font color = blue>代码编辑器，强烈推荐使用微软的 VS code，相比Atom开启迅速，使用方便，扩展丰富</font>


## 第一步： 安装Kramed
hexo 默认的渲染引擎是 marked，但是 marked 不支持 mathjax。，所以需要更换Hexo的markdown渲染引擎为hexo-renderer-kramed引擎，后者支持mathjax公式输出。
```
npm uninstall hexo-renderer-marked --save
npm install hexo-renderer-kramed --save
```


![](https://img-blog.nos-eastchina1.126.net/hexo-math1.png)




## 第二步：更改文件配置

打开`/node_modules/hexo-renderer-kramed/lib/renderer.js`，更改：
```
// Change inline math rule
function formatText(text) {
    // Fit kramed's rule: $$ + \1 + $$
    return text.replace(/`\$(.*?)\$`/g, '$$$$$1$$$$');
}

为，直接返回text

// Change inline math rule
function formatText(text) {
    return text;
}
```
![](https://img-blog.nos-eastchina1.126.net/hexo-math4.png)



## 第三步: 停止使用 hexo-math，并安装mathjax包

卸载hexo-math
```
npm uninstall hexo-math --save
```
安装 hexo-renderer-mathjax 包
```
npm install hexo-renderer-mathjax --save
```

![](https://img-blog.nos-eastchina1.126.net/hexo-math2.png)
![](https://img-blog.nos-eastchina1.126.net/hexo-math3.png)



## 第四步: 更新 Mathjax 的 配置文件

打开`/node_modules/hexo-renderer-mathjax/mathjax.html`
如图所示更改`<script>`为：
即注释掉`<script>`代码，并把以下代码复制到对应位置
```
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML"></script>
```

![](https://img-blog.nos-eastchina1.126.net/hexo-math5.png)



## 第五步: 更改默认转义规则
因为LaTeX与markdown语法有语义冲突，所以 hexo 默认的转义规则会将一些字符进行转义，所以我们需要对默认的规则进行修改. 
 打开`/node_modules\kramed\lib\rules\inline.js`
 1、
```
escape: /^\\([\\`*{}\[\]()#$+\-.!_>])/,
```
更改为
```
escape: /^\\([`*\[\]()# +\-.!_>])/,
```
2、
```
em: /^\b_((?:__|[\s\S])+?)_\b|^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,
```
更改为
```
em: /^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,
```

![](https://img-blog.nos-eastchina1.126.net/hexo-math6.png)


## 第六步: 开启mathjax

打开`/themes/yilia `主题目录下的`config.yml`文件
因为我用的`yilia`主题，所以路径是`/themes/yilia `

我们需要在`config.yml`文件 中开启 Mathjax， 找到 mathjax 字段添加如下代码：(不同的主题配置方法略微有区别)
```
mathjax:
    enable: true
```
或者
```
mathjax: true
```

![](https://img-blog.nos-eastchina1.126.net/hexo-math7.png)

<font color = red size="2">注意的是：，无论是配置文件还是博客文件，配置项跟配置参数均有有一个空格，否则会配置失败</font><br>
例：
```
mathjax: true（mathjax:空格true）
而不是
mathjax:true（mathjax:true）
```

写博客文件时，要开启 `Mathjax`选项，， 添加以下内容：

```
mathjax: true
```

例如
```
title: 特征提取——局部特征
date: 2018-07-16 09:39:40
tags: [GitHub, Mysql]
mathjax: true

```
如下图所示

![](https://img-blog.nos-eastchina1.126.net/hexo-math7.5.png)



通过以上步骤，我们就可以在 hexo 中使用 Mathjax 来书写数学公式。

效果展示：

![](https://img-blog.nos-eastchina1.126.net/hexo-math8.png)

![](https://img-blog.nos-eastchina1.126.net/hexo-math9.png)


[参考文章1](https://blog.csdn.net/crazy_scott/article/details/79293576)
[参考文章2](https://www.jianshu.com/p/a0aa94ef8ab2)



