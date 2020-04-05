---
title: Hexo博客Next主题valine评论系统邮件提醒
date: 2020-04-03 10:59:59
tags: [Hexo, Next, GitHub]
---
 
Hexo博客Next主题valine评论系统邮件提醒
<!--more-->

## 简介
Valine：一款快速、简洁且高效的无后端评论系统。

## Valine-Admin
Github 项目地址，具体教程以 最新版 为准
[Valine-Admin项目地址](https://github.com/zhaojun1998/Valine-Admin)
### 简介
>Valine Admin 是 Valine 评论系统的扩展和增强，主要实现评论邮件通知、评论管理、垃圾评论过滤等功能。支持完全自定义的邮件通知模板。基于Akismet API实现准确的垃圾评论过滤。此外，使用云函数等技术解决了免费版云引擎休眠问题，支持云引擎自动唤醒，漏发邮件自动补发。兼容云淡风轻及Deserts维护的多版本Valine。

>NOTE: 该项目基于LeanCloud云引擎示例代码实现，您可以自由地复制和修改。包含了一些 trick 实现资源的最大化利用 ，但请勿滥用免费资源。引用本说明文档及Deserts博客上的相关文章务必注明来源。
部署

### 快速开始
首先需要确保 `Valine` 的基础功能是正常的

### 配置项
设置自定义环境变量，需要设置云引擎的环境变量以提供必要的信息，变量参数参考下面的配置项


![](https://img-blog.nos-eastchina1.126.net/blog/blog_valine_admin_3.png)


```
变量 示例 说明
SITE_NAME HONGWEI’S Blog [必填] 网站名称
SITE_URL https://www.zhwei.cn [必填] 网站地址，最后不要加 /
SMTP_SERVICE QQ [必填] 邮件服务提供商，支持 QQ、163、126、Gmail 以及 更多。 — 如这里没有你使用的邮件提供商，请查看自定义邮件服务器
SMTP_USER xxxx@qq.com [必填] SMTP登录用户，一般为邮箱地址
SMTP_PASS xxxx [必填] SMTP登录密码，一般为授权码，而不是邮箱的登陆密码，请自行查询对应邮件服务商的获取方式
SENDER_NAME HONGWEI’S Blog Valine 评论提醒 [可选] 发件人
ADMIN_URL https://xxx.leanapp.cn/ [建议] Web主机二级域名，用于自动唤醒
TO_EMAIL xxxxx@gmail.com [可选] 指定站长收信邮箱，默认值为SITE_USER。用于 SMTP 发件人与站长收件人不一致的情况下使用。
TEMPLATE_NAME rainbow [可选] 通知邮件的模板（default和rainbow），参考高级功能
```
### 部署
进入 `Leancloud` 对应的 `Valine` 应用中。
点击 云引擎 -> 设置 填写代码库：`https://github.com/zhaojun1998/Valine-Admin`，保存

>注意：
这里推荐代码库路径先填写：`https://github.com/zhaojun1998/Valine-Admin`，然后全部部署完之后试试留言会不会提醒道邮箱里，如果配置成功，在github上frok这个代码库到自己账号，然后代码库路径使用自己账号下的库，比如我的是`https://github.com/AomanHao/Valine-Admin`，为了稳定运行

![](https://img-blog.nos-eastchina1.126.net/blog/blog_valine_admin_1.png)

点击 云引擎 -> 部署，分支或版本号输入master，部署

![](https://img-blog.nos-eastchina1.126.net/blog/blog_valine_admin_2.png)


### 后台评论管理
点击 云引擎 -> 设置，在Web主机域名位置点击申请，获取二级域名，域名随机不好记，保存在书签里
![](https://img-blog.nos-eastchina1.126.net/blog/blog_valine_admin_4.png)

设置后台管理登录信息，点击 `存储 -> 结构化数据`，选择`_User`如果有内容，全部删除，这里是需要新建后台管理的账户。
选择`_User -> 添加行`，只需要填写`password、username、email`这三个或`password、username`字段即可, 使用`SMTP_USER`【之前填的SMTP登录用户，一般为邮箱地址】 作为账号登陆、`password` 作为账号密码、`username` 任意即可。（为了安全考虑，此 email 必须为配置中的 SMTP_USER 或 TO_EMAIL）

此后，可以通过上述申请的 `https://二级域名.leanapp.cn/`管理评论


### 定时任务
免费版的 LeanCloud 容器，是有强制性休眠策略的，不能 24 小时运行：
每天必须休眠 6 个小时
30 分钟内没有外部请求，则休眠

#### 配置自动唤醒（推荐）
创建定时任务，名称任意，生产环境选择`self-wake`云函数，`Cron表达式`填入`0 */20 7-23 * * ?`，表示每天 7 - 23 点每 20 分钟访问一次，这样可以保持每天的绝大多数时间邮件服务是正常的。

#### 配置定时检查
创建定时任务，名称任意，生产环境选择`resend-mails云函数`，`Cron表达式`填入`0 0 8 * * ?`，表示每天早8点检查过去24小时内漏发的通知邮件并补发

![](https://img-blog.nos-eastchina1.126.net/blog/blog_valine_admin_5.png)

[参考文章](https://blog.csdn.net/z_johnny/article/details/104211572)

 [我的个人博客地址，欢迎访问](http://www.aomanhao.top)
 [我的CSDN地址，欢迎访问](https://blog.csdn.net/Aoman_Hao)
 [我的GitHub主页，欢迎访问](https://github.com/AomanHao)