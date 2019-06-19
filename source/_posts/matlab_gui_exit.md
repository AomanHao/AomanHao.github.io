---
title: matlab的gui图像处理操作界面，实现重置和退出按钮功能
date: 2018-03-09 10:59:59
tags: [Matlab, GUI]
---

axes控件实现了展示图片，动态txt控件实现了展示或者输入参数。
<!--more-->

在gui界面右键点击“重置”pushbotton回到代码块callback，编写代码

![在这里插入图片描述](https://img-blog.nos-eastchina1.126.net/blog/jiemian_chongzhi%20(2).png)

![在这里插入图片描述](https://img-blog.nos-eastchina1.126.net/blog/jiemian_chongzhi%20(1).png)

以下代码是实现图片和参数数字重置，是重置按钮（puttern）的功能实现
```
function pushbutton1_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% 重置清空图片 美滋滋
cla(handles.axes1,'reset');
cla(handles.axes2,'reset');
cla(handles.axes3,'reset');
cla(handles.axes4,'reset');
cla(handles.axes5,'reset');

% 重置清空动态txt的文字 美滋滋
set(handles.edit1,'string','')
set(handles.edit2,'string','')
set(handles.edit3,'string','')
set(handles.edit4,'string','')
```

----------------------------
退出按钮：
在gui界面右键点击“退出”pushbotton回到代码块callback，编写代码
即可
```
close
```
