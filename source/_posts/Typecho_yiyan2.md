---
title: Typecho handsome主题一言接口修改
date: 2021-01-03 10:08:00
tags: [Typecho]
---
 
Typecho handsome主题一言接口修改
<!--more-->

## 说明
handsome主题默认使用的是 https://v1.hitokoto.cn 一言接口
博主感觉不是太满意，于是想换成自己的“一言”服务接口
首先需要自己搭建一个“一言”服务接口，搭建方法可以看这里：https://sunpma.com/669.html
搭建好了后就可以按下面的方法替换成自己的接口即可；

## 修改主题“一言”接口
修改路径位于网站根目录下`/usr/themes/handsome/index.php`修改`index.php`文件即可；
原始代码为：
```
<!--/公告位置-->
          <?php endif; ?>
        <header class="bg-light lter b-b wrapper-md">
          <h1 class="m-n font-thin h3 text-black l-h"><?php $this->options->title(); ?></h1>
          <small class="text-muted letterspacing indexWords"><?php
              if (@!in_array('hitokoto',$this->options->featuresetup)) {
                  $this->options->Indexwords();
              }else{
                  echo '加载中……';
                  echo '<script>
                         $.ajax({
                            type: \'Get\',
                            url: \'https://v1.hitokoto.cn/\',
                            success: function(data) {
                               var hitokoto = data.hitokoto;
                              $(\'.indexWords\').text(hitokoto);
                            }
                         });
</script>';
              }
              ?></small>
          </header>
        <div class="wrapper-md" id="post-panel">
            <!--首页输出文章-->
```
### 方法一：使用JS调用
```
<!--/公告位置-->
          <?php endif; ?>
        <header class="bg-light lter b-b wrapper-md">
          <h1 class="m-n font-thin h3 text-black l-h"><?php $this->options->title(); ?></h1>
          <small class="text-muted letterspacing indexWords"><?php
              if (@!in_array('hitokoto',$this->options->featuresetup)) {
                  $this->options->Indexwords();
              }else{
                  echo '加载中……';
                  echo '<script>
                         $.post("https://sunpma.com/other/hitokoto/", function(hitokoto) {
                            $(".indexWords").html(hitokoto);
                         });
</script>';
              }
              ?></small>
          </header>
        <div class="wrapper-md" id="post-panel">
            <!--首页输出文章-->
```

### 方法二：使用PHP调用
```
<!--/公告位置-->
          <?php endif; ?>
        <header class="bg-light lter b-b wrapper-md">
          <h1 class="m-n font-thin h3 text-black l-h"><?php $this->options->title(); ?></h1>
          <?php $hitokoto = file_get_contents('https://sunpma.com/other/hitokoto/'); ?>
          <?php echo $hitokoto; ?>
        </header>
        <div class="wrapper-md" id="post-panel">
            <!--首页输出文章-->
```
### 注意
1、修改代码中的链接地址需要修改成自己的接口链接
2、handsome主题需要打开一言功能


### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)