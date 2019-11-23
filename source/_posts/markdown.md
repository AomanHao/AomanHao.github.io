---
title: markdown 基本用法(常用)
date: 2018-07-01 16:00:00
tags: [Markdown, GitHub]
---
markdown 基本用法
<!--more-->

[在线markdown编辑器](
https://www.zybuluo.com/mdeditor?url=https://www.zybuluo.com/static/editor/md-help.markdown)

## 标题类别
<h1>一级标题</h1>
用"<h数字></h数字>"或者多个"#"隔开


    <h1>一级标题</h1>
    # 一级标题

<h2>二级标题</h2>

    <h2>二级标题</h2>
    ## 二级标题

以此类推

---
## 代码块


四个空格后开始写代码
（空空空空zxcvbasdfgqwert）

或者用```放在代码块两端

    ```
    AAA
    ```


 (四个空格两个字节)zxcvbasdfgqwert

--- 
## 语句强调
<h3>斜体</h3>
文字两端使用1个"*"或者"_"夹起来

*a*

    *a*
    或者
    _a_

---

### 粗体
文字两端使用2个"*"或者"_"夹起来

---

### 分隔线
三个"*"或者"-"

    ***
    ---

---

## 无序列表

使用加号"+"或是减号"-"作为列表标记：

+ 可乐
+ 雪碧

    +（空格）可乐
    +（空格）雪碧


---
## emoji表情
Markdown文档支持文中插入emoji表情

比如：<br>

`:laughing:` 表示:laughing:
`:heart:` 表示:heart:
其他emoji的地址如下链接：
[emoji地址](https://github.com/guodongxiaren/README/blob/master/emoji.md)

## 引用
`>`表示引用 
`>>` 表示引用中的引用
效果展示:

>引用(一个小于号) 
>> 引用中的引用（两个小于号）



---

### 1. 斜体和粗体

使用 * 和 ** 表示斜体和粗体。

示例：

这是 *斜体*，这是 **粗体**。

### 2. 分级标题

使用 === 表示一级标题，使用 --- 表示二级标题。

示例：

```
这是一个一级标题
============================

这是一个二级标题
--------------------------------------------------

### 这是一个三级标题
```

你也可以选择在行首加井号表示不同级别的标题 (H1-H6)，例如：# H1, ## H2, ### H3，#### H4。

### 3. 外链接

使用 \[描述](链接地址) 为文字增加外链接。

示例：

这是去往 [本人博客](http://ghosertblog.github.com) 的链接。

### 4. 无序列表

使用 `*`，`+`或者`-` 表示无序列表。

示例：

- 无序列表项 一
- 无序列表项 二
- 无序列表项 三

### 5. 有序列表

使用数字和点表示有序列表。`1.`

示例：

1. 有序列表项 一
2. 有序列表项 二
3. 有序列表项 三

### 6. 文字引用

使用 > 表示文字引用。

示例：

> 野火烧不尽，春风吹又生。

### 7. 行内代码块

使用 上顿点\`代码` 表示行内代码块。
>`代码`

示例：

让我们聊聊 `html`。

### 8.  代码块

使用 四个缩进空格 或者上下三个上顿点 表示代码块。
>\`    上顿点前后各三个

示例：

    这是一个代码块，此行左侧有四个不可见的空格。

### 9.  插入图像

使用 \!\[描述](图片链接地址) 插入图像。

示例：

[![kZq279.jpg](https://s2.ax1x.com/2019/01/24/kZq279.jpg)](https://imgchr.com/i/kZq279)

# Cmd Markdown 高阶语法手册

### 1. 内容目录

在段落中填写 `[TOC]` 以显示全文内容的目录结构。

[TOC]

### 2. 标签分类

在编辑区任意行的列首位置输入以下代码给文稿标签：

标签： 数学 英语 Markdown

或者

Tags： 数学 英语 Markdown

### 3. 删除线

使用 ~~ 表示删除线。

~~这是一段错误的文本。~~

### 4. 注脚

使用 [^keyword] 表示注脚。

这是一个注脚[^footnote]的样例。

这是第二个注脚[^footnote2]的样例。

### 5. LaTeX 公式

$ 表示行内公式： 

质能守恒方程可以用一个很简洁的方程式 $E=mc^2$ 来表达。

$$ 表示整行公式：

$$\sum_{i=1}^n a_i=0$$

$$f(x_1,x_x,\ldots,x_n) = x_1^2 + x_2^2 + \cdots + x_n^2 $$

$$\sum^{j-1}_{k=0}{\widehat{\gamma}_{kj} z_k}$$

访问 [MathJax](http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference) 参考更多使用方法。

### 6. 加强的代码块

支持四十一种编程语言的语法高亮的显示，行号显示。

非代码示例：

```
$ sudo apt-get install vim-gnome
```

Python 示例：

```python
@requires_authorization
def somefunc(param1='', param2=0):
    '''A docstring'''
    if param1 > param2: # interesting
        print 'Greater'
    return (param2 - param1 + 1) or None

class SomeClass:
    pass

>>> message = '''interpreter
... prompt'''
```

JavaScript 示例：

``` javascript
/**
* nth element in the fibonacci series.
* @param n >= 0
* @return the nth element, >= 0.
*/
function fib(n) {
  var a = 1, b = 1;
  var tmp;
  while (--n >= 0) {
    tmp = a;
    a += b;
    b = tmp;
  }
  return a;
}

document.write(fib(10));
```

### 7. 流程图

#### 示例

```flow
st=>start: Start:>https://www.zybuluo.com
io=>inputoutput: verification
op=>operation: Your Operation
cond=>condition: Yes or No?
sub=>subroutine: Your Subroutine
e=>end

st->io->op->cond
cond(yes)->e
cond(no)->sub->io
```

#### 更多语法参考：[流程图语法参考](http://adrai.github.io/flowchart.js/)

### 8. 序列图

#### 示例 1

```seq
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
```

#### 示例 2

```seq
Title: Here is a title
A->B: Normal line
B-->C: Dashed line
C->>D: Open arrow
D-->>A: Dashed open arrow
```

#### 更多语法参考：[序列图语法参考](http://bramp.github.io/js-sequence-diagrams/)

### 9. 甘特图

甘特图内在思想简单。基本是一条线条图，横轴表示时间，纵轴表示活动（项目），线条表示在整个期间上计划和实际的活动完成情况。它直观地表明任务计划在什么时候进行，及实际进展与计划要求的对比。

```gantt
    title 项目开发流程
    section 项目确定
        需求分析       :a1, 2016-06-22, 3d
        可行性报告     :after a1, 5d
        概念验证       : 5d
    section 项目实施
        概要设计      :2016-07-05  , 5d
        详细设计      :2016-07-08, 10d
        编码          :2016-07-15, 10d
        测试          :2016-07-22, 5d
    section 发布验收
        发布: 2d
        验收: 3d
```

#### 更多语法参考：[甘特图语法参考](https://knsv.github.io/mermaid/#gant-diagrams)

### 10. Mermaid 流程图

```graphLR
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
```

#### 更多语法参考：[Mermaid 流程图语法参考](https://knsv.github.io/mermaid/#flowcharts-basic-syntax)

### 11. Mermaid 序列图

```sequence
    Alice->John: Hello John, how are you?
    loop every minute
        John-->Alice: Great!
    end
```

#### 更多语法参考：[Mermaid 序列图语法参考](https://knsv.github.io/mermaid/#sequence-diagrams)

### 12. 表格支持

| 项目        | 价格   |  数量  |
| --------   | -----:  | :----:  |
| 计算机     | \$1600 |   5     |
| 手机        |   \$12   |   12   |
| 管线        |    \$1    |  234  |


### 13. 定义型列表

名词 1
:   定义 1（左侧有一个可见的冒号和四个不可见的空格）

代码块 2
:   这是代码块的定义（左侧有一个可见的冒号和四个不可见的空格）

        代码块（左侧有八个不可见的空格）

### 14. Html 标签

本站支持在 Markdown 语法中嵌套 Html 标签，譬如，你可以用 Html 写一个纵跨两行的表格：

    <table>
        <tr>
            <th rowspan="2">值班人员</th>
            <th>星期一</th>
            <th>星期二</th>
            <th>星期三</th>
        </tr>
        <tr>
            <td>李强</td>
            <td>张明</td>
            <td>王平</td>
        </tr>
    </table>


<table>
    <tr>
        <th rowspan="2">值班人员</th>
        <th>星期一</th>
        <th>星期二</th>
        <th>星期三</th>
    </tr>
    <tr>
        <td>李强</td>
        <td>张明</td>
        <td>王平</td>
    </tr>
</table>

### 15. 内嵌图标

本站的图标系统对外开放，在文档中输入

    <i class="icon-weibo"></i>

即显示微博的图标： <i class="icon-weibo icon-2x"></i>

替换 上述 `i 标签` 内的 `icon-weibo` 以显示不同的图标，例如：

    <i class="icon-renren"></i>

即显示人人的图标： <i class="icon-renren icon-2x"></i>

更多的图标和玩法可以参看 [font-awesome](http://fortawesome.github.io/Font-Awesome/3.2.1/icons/) 官方网站。

### 16. 待办事宜 Todo 列表

使用带有 [ ] 或 [x] （未完成或已完成）项的列表语法撰写一个待办事宜列表，并且支持子列表嵌套以及混用Markdown语法，例如：

    - [ ] **Cmd Markdown 开发**
        - [ ] 改进 Cmd 渲染算法，使用局部渲染技术提高渲染效率
        - [ ] 支持以 PDF 格式导出文稿
        - [x] 新增Todo列表功能 [语法参考](https://github.com/blog/1375-task-lists-in-gfm-issues-pulls-comments)
        - [x] 改进 LaTex 功能
            - [x] 修复 LaTex 公式渲染问题
            - [x] 新增 LaTex 公式编号功能 [语法参考](http://docs.mathjax.org/en/latest/tex.html#tex-eq-numbers)
    - [ ] **七月旅行准备**
        - [ ] 准备邮轮上需要携带的物品
        - [ ] 浏览日本免税店的物品
        - [x] 购买蓝宝石公主号七月一日的船票
        
对应显示如下待办事宜 Todo 列表：
        
- [ ] **Cmd Markdown 开发**
    - [ ] 改进 Cmd 渲染算法，使用局部渲染技术提高渲染效率
    - [ ] 支持以 PDF 格式导出文稿
    - [x] 新增Todo列表功能 [语法参考](https://github.com/blog/1375-task-lists-in-gfm-issues-pulls-comments)
    - [x] 改进 LaTex 功能
        - [x] 修复 LaTex 公式渲染问题
        - [x] 新增 LaTex 公式编号功能 [语法参考](http://docs.mathjax.org/en/latest/tex.html#tex-eq-numbers)
- [ ] **七月旅行准备**
    - [ ] 准备邮轮上需要携带的物品
    - [ ] 浏览日本免税店的物品
    - [x] 购买蓝宝石公主号七月一日的船票
        
        
[^footnote]: 这是一个 *注脚* 的 **文本**。

[^footnote2]: 这是另一个 *注脚* 的 **文本**。

---
### 字体
```
<font face="黑体">我是黑体字</font>
<font face="微软雅黑">我是微软雅黑</font>
<font face="STCAIYUN">我是华文彩云</font>
<font color=#0099ff size=7 face="黑体">color=#0099ff size=72 face="黑体"</font>
<font color=#00ffff size=72>color=#00ffff</font>
<font color=gray size=72>color=gray</font>
```

### 颜色
```
颜色名	十六进制颜色值	颜色
AliceBlue	#F0F8FF	rgb(240, 248, 255)
AntiqueWhite	#FAEBD7	rgb(250, 235, 215)
Aqua	#00FFFF	rgb(0, 255, 255)
Aquamarine	#7FFFD4	rgb(127, 255, 212)
Azure	#F0FFFF	rgb(240, 255, 255)
Beige	#F5F5DC	rgb(245, 245, 220)
Bisque	#FFE4C4	rgb(255, 228, 196)
Black	#000000	rgb(0, 0, 0)
BlanchedAlmond	#FFEBCD	rgb(255, 235, 205)
Blue	#0000FF	rgb(0, 0, 255)
BlueViolet	#8A2BE2	rgb(138, 43, 226)
Brown	#A52A2A	rgb(165, 42, 42)
BurlyWood	#DEB887	rgb(222, 184, 135)
CadetBlue	#5F9EA0	rgb(95, 158, 160)
Chartreuse	#7FFF00	rgb(127, 255, 0)
Chocolate	#D2691E	rgb(210, 105, 30)
Coral	#FF7F50	rgb(255, 127, 80)
CornflowerBlue	#6495ED	rgb(100, 149, 237)
Cornsilk	#FFF8DC	rgb(255, 248, 220)
Crimson	#DC143C	rgb(220, 20, 60)
Cyan	#00FFFF	rgb(0, 255, 255)
DarkBlue	#00008B	rgb(0, 0, 139)
DarkCyan	#008B8B	rgb(0, 139, 139)
DarkGoldenRod	#B8860B	rgb(184, 134, 11)
DarkGray	#A9A9A9	rgb(169, 169, 169)
DarkGreen	#006400	rgb(0, 100, 0)
DarkKhaki	#BDB76B	rgb(189, 183, 107)
DarkMagenta	#8B008B	rgb(139, 0, 139)
DarkOliveGreen	#556B2F	rgb(85, 107, 47)
Darkorange	#FF8C00	rgb(255, 140, 0)
DarkOrchid	#9932CC	rgb(153, 50, 204)
DarkRed	#8B0000	rgb(139, 0, 0)
DarkSalmon	#E9967A	rgb(233, 150, 122)
DarkSeaGreen	#8FBC8F	rgb(143, 188, 143)
DarkSlateBlue	#483D8B	rgb(72, 61, 139)
DarkSlateGray	#2F4F4F	rgb(47, 79, 79)
DarkTurquoise	#00CED1	rgb(0, 206, 209)
DarkViolet	#9400D3	rgb(148, 0, 211)
DeepPink	#FF1493	rgb(255, 20, 147)
DeepSkyBlue	#00BFFF	rgb(0, 191, 255)
DimGray	#696969	rgb(105, 105, 105)
DodgerBlue	#1E90FF	rgb(30, 144, 255)
Feldspar	#D19275	rgb(209, 146, 117)
FireBrick	#B22222	rgb(178, 34, 34)
FloralWhite	#FFFAF0	rgb(255, 250, 240)
ForestGreen	#228B22	rgb(34, 139, 34)
Fuchsia	#FF00FF	rgb(255, 0, 255)
Gainsboro	#DCDCDC	rgb(220, 220, 220)
GhostWhite	#F8F8FF	rgb(248, 248, 255)
Gold	#FFD700	rgb(255, 215, 0)
GoldenRod	#DAA520	rgb(218, 165, 32)
Gray	#808080	rgb(128, 128, 128)
Green	#008000	rgb(0, 128, 0)
GreenYellow	#ADFF2F	rgb(173, 255, 47)
HoneyDew	#F0FFF0	rgb(240, 255, 240)
HotPink	#FF69B4	rgb(255, 105, 180)
IndianRed	#CD5C5C	rgb(205, 92, 92)
Indigo	#4B0082	rgb(75, 0, 130)
Ivory	#FFFFF0	rgb(255, 255, 240)
Khaki	#F0E68C	rgb(240, 230, 140)
Lavender	#E6E6FA	rgb(230, 230, 250)
LavenderBlush	#FFF0F5	rgb(255, 240, 245)
LawnGreen	#7CFC00	rgb(124, 252, 0)
LemonChiffon	#FFFACD	rgb(255, 250, 205)
LightBlue	#ADD8E6	rgb(173, 216, 230)
LightCoral	#F08080	rgb(240, 128, 128)
LightCyan	#E0FFFF	rgb(224, 255, 255)
LightGoldenRodYellow	#FAFAD2	rgb(250, 250, 210)
LightGrey	#D3D3D3	rgb(211, 211, 211)
LightGreen	#90EE90	rgb(144, 238, 144)
LightPink	#FFB6C1	rgb(255, 182, 193)
LightSalmon	#FFA07A	rgb(255, 160, 122)
LightSeaGreen	#20B2AA	rgb(32, 178, 170)
LightSkyBlue	#87CEFA	rgb(135, 206, 250)
LightSlateBlue	#8470FF	rgb(132, 112, 255)
LightSlateGray	#778899	rgb(119, 136, 153)
LightSteelBlue	#B0C4DE	rgb(176, 196, 222)
LightYellow	#FFFFE0	rgb(255, 255, 224)
Lime	#00FF00	rgb(0, 255, 0)
LimeGreen	#32CD32	rgb(50, 205, 50)
Linen	#FAF0E6	rgb(250, 240, 230)
Magenta	#FF00FF	rgb(255, 0, 255)
Maroon	#800000	rgb(128, 0, 0)
MediumAquaMarine	#66CDAA	rgb(102, 205, 170)
MediumBlue	#0000CD	rgb(0, 0, 205)
MediumOrchid	#BA55D3	rgb(186, 85, 211)
MediumPurple	#9370D8	rgb(147, 112, 216)
MediumSeaGreen	#3CB371	rgb(60, 179, 113)
MediumSlateBlue	#7B68EE	rgb(123, 104, 238)
MediumSpringGreen	#00FA9A	rgb(0, 250, 154)
MediumTurquoise	#48D1CC	rgb(72, 209, 204)
MediumVioletRed	#C71585	rgb(199, 21, 133)
MidnightBlue	#191970	rgb(25, 25, 112)
MintCream	#F5FFFA	rgb(245, 255, 250)
MistyRose	#FFE4E1	rgb(255, 228, 225)
Moccasin	#FFE4B5	rgb(255, 228, 181)
NavajoWhite	#FFDEAD	rgb(255, 222, 173)
Navy	#000080	rgb(0, 0, 128)
OldLace	#FDF5E6	rgb(253, 245, 230)
Olive	#808000	rgb(128, 128, 0)
OliveDrab	#6B8E23	rgb(107, 142, 35)
Orange	#FFA500	rgb(255, 165, 0)
OrangeRed	#FF4500	rgb(255, 69, 0)
Orchid	#DA70D6	rgb(218, 112, 214)
PaleGoldenRod	#EEE8AA	rgb(238, 232, 170)
PaleGreen	#98FB98	rgb(152, 251, 152)
PaleTurquoise	#AFEEEE	rgb(175, 238, 238)
PaleVioletRed	#D87093	rgb(216, 112, 147)
PapayaWhip	#FFEFD5	rgb(255, 239, 213)
PeachPuff	#FFDAB9	rgb(255, 218, 185)
Peru	#CD853F	rgb(205, 133, 63)
Pink	#FFC0CB	rgb(255, 192, 203)
Plum	#DDA0DD	rgb(221, 160, 221)
PowderBlue	#B0E0E6	rgb(176, 224, 230)
Purple	#800080	rgb(128, 0, 128)
Red	#FF0000	rgb(255, 0, 0)
RosyBrown	#BC8F8F	rgb(188, 143, 143)
RoyalBlue	#4169E1	rgb(65, 105, 225)
SaddleBrown	#8B4513	rgb(139, 69, 19)
Salmon	#FA8072	rgb(250, 128, 114)
SandyBrown	#F4A460	rgb(244, 164, 96)
SeaGreen	#2E8B57	rgb(46, 139, 87)
SeaShell	#FFF5EE	rgb(255, 245, 238)
Sienna	#A0522D	rgb(160, 82, 45)
Silver	#C0C0C0	rgb(192, 192, 192)
SkyBlue	#87CEEB	rgb(135, 206, 235)
SlateBlue	#6A5ACD	rgb(106, 90, 205)
SlateGray	#708090	rgb(112, 128, 144)
Snow	#FFFAFA	rgb(255, 250, 250)
SpringGreen	#00FF7F	rgb(0, 255, 127)
SteelBlue	#4682B4	rgb(70, 130, 180)
Tan	#D2B48C	rgb(210, 180, 140)
Teal	#008080	rgb(0, 128, 128)
Thistle	#D8BFD8	rgb(216, 191, 216)
Tomato	#FF6347	rgb(255, 99, 71)
Turquoise	#40E0D0	rgb(64, 224, 208)
Violet	#EE82EE	rgb(238, 130, 238)
VioletRed	#D02090	rgb(208, 32, 144)
Wheat	#F5DEB3	rgb(245, 222, 179)
White	#FFFFFF	rgb(255, 255, 255)
WhiteSmoke	#F5F5F5	rgb(245, 245, 245)
Yellow	#FFFF00	rgb(255, 255, 0)
YellowGreen	#9ACD32	rgb(154, 205, 50)
```
