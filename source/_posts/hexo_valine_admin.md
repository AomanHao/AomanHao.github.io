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

### 部署
进入 Leancloud 对应的 Valine 应用中。
点击 云引擎 -> 设置 填写代码库：`https://github.com/zhaojun1998/Valine-Admin`，保存

设置自定义环境变量，需要设置云引擎的环境变量以提供必要的信息，变量参数参考下面的配置项

![](https://img-blog.nos-eastchina1.126.net/blog/blog_valine_admin_1.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_valine_admin_2.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_valine_admin_3.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_valine_admin_4.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_valine_admin_5.png)


配置项
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

点击 云引擎 -> 部署，分支或版本号输入master，部署



### 后台评论管理
点击 云引擎 -> 设置，在Web主机域名位置点击申请，获取二级域名，现在的二级域名不支持自定义，如果想好记请参考高级功能

设置后台管理登录信息，点击 存储 -> 结构化数据，选择_User -> 添加行，只需要填写password、username、email这三个字段即可, 使用 email 作为账号登陆、password 作为账号密码、username 任意即可。（为了安全考虑，此 email 必须为配置中的 SMTP_USER 或 TO_EMAIL， 否则不允许登录）

此后，可以通过https://二级域名.leanapp.cn/管理评论
定时任务
免费版的 LeanCloud 容器，是有强制性休眠策略的，不能 24 小时运行：
每天必须休眠 6 个小时
30 分钟内没有外部请求，则休眠
休眠后如果有新的外部请求实例则马上启动（但激活时此次发送邮件会失败）。
分析了一下上方的策略，如果不想付费的话，最佳使用方案就设置定时器，目前基于 LeanCloud 自带定时器实现了两种云函数定时任务：
自动唤醒，定时访问Web APP二级域名防止云引擎休眠（推荐）
定时检查，每天定时检查24小时内漏发的邮件通知
配置
首先需要添加环境变量，点击 云引擎 -> 设置，配置自定义环境变量，变量名ADMIN_URL，变量值Web 主机域名，即二级域名地址，添加后重启容器环境变量才会生效
配置定时任务，击 云引擎 -> 定时任务
配置自动唤醒（推荐），创建定时任务，名称任意，生产环境选择self-wake云函数，Cron表达式填入0 */20 7-23 * * ?，表示每天 7 - 23 点每 20 分钟访问一次，这样可以保持每天的绝大多数时间邮件服务是正常的。
配置定时检查，创建定时任务，名称任意，生产环境选择resend-mails云函数，Cron表达式填入0 0 8 * * ?，表示每天早8点检查过去24小时内漏发的通知邮件并补发

高级配置
自定义邮件模板
自定义收件邮箱
自定义邮件服务器
Web 评论管理
好记的二级域名
Leancloud 休眠策略(必看)
开发指南
显示个性头像
Valine 目前使用的是Gravatar 作为评论列表头像。
请自行登录或注册Gravatar，然后修改自己的头像。
评论的时候，留下在Gravatar注册时所使用的邮箱即可。
感谢gravatar.cat.net提供的镜像服务。
如果你修改了头像后发现没有更新，请不要慌张，因为gravatar.cat.net 有七天的缓存期，安静的等待吧~
目前非自定义头像有以下7种默认值可选:
参数值 表现形式 备注
空字符串''  Gravatar官方图形
mp  神秘人(一个灰白头像)
identicon  抽象几何图形
monsterid  小怪物
wavatar  用不同面孔和背景组合生成的头像
retro  八位像素复古头像
robohash  一种具有不同颜色、面部等的机器人
hide  不显示头像
newValine({...    avatar:''// (''/mp/identicon/monsterid/wavatar/robohash/retro/hide)});
1
2
3
4
Gravatar是什么？ ------下面内容摘抄自异次元软件世界
Gravatar，它的全称叫做“Globally Recognized Avatar”，翻译过来叫做全球通用头像。
Gravatar 的概念首先是在国外的独立 WordPress 博客中兴起的，当你到任何一个支持Gravatar的网站留言时，这个网站都就会根据你所提供的 Email 地址为你显示出匹配的头像。当然，这个头像，是需要你事先到 Gravatar 的网站注册并上传的，否则，在这个网站上，就只会显示成一个默认的头像。
这个Web2.0时代的产物，当时好多网站均已支持Gravatar服务了，你可以通过你的个性头像打造起你的个人品牌了！并且这个 Gravatar 没有什么约束，想换头像换马甲？很简单，改改留言的名字和email地址就可以了。另外注册与使用 Gravatar 均是完全免费的，唯一的门槛是，国内可能无法正常访问。
大致使用流程：
注册：进入Gravatar网站，点击页面的Sign Up进行注册。
验证：进入你的邮箱，从Gravatar发出的信件中拷贝那段链接地址，在浏览器输入。
设置昵称、密码。
选择上传图片：一般都是从电脑中上传（My computer’s hard drive）。
剪裁大小
评级：你的头像要被分级的，因为可能会有朋友喜欢用比较曝露的头像，会影响小朋友身心健康的说。如果你的图片不是特别那个的话，一般不用选择Sex或暴力之类的，直接选择G（通用型），这样基本任何网站都能显示这个等级的图片。异次元比较邪恶，暂时允许显示R级以下的头像…
等待审核：可能需要站方短暂审核一下，一般选择了G，而你的图片没什么特别的，很快就通过。一般遇上慢的情况也就10分钟左右。
完成了以上步骤，今后在支持Gravatar的网站留言都会显示你帅帅的头像了。暂时来说，大部分支持Gravatar的网站均是使用 WordPress 程序的博客，但其实任何其他网站程序，如果加入了Gravatar的代码，也是可以支持Gravatar的。估计这个应用在日后会渐渐普及起来吧，起码用户不需要每到一个网站去就搞一下头像……
Valine的个性头像就是来自Gravatar网站


 [我的个人博客地址，欢迎访问](http://www.aomanhao.top)
 [我的CSDN地址，欢迎访问](https://blog.csdn.net/Aoman_Hao)
 [我的GitHub主页，欢迎访问](https://github.com/AomanHao)