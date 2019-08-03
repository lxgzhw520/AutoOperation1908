# shell编程

> 作者: 张大鹏
>
> 时间: 2019年8月3日
>
> 抖音: lxgzhw
>
> 微博: 理想国真恵玩
>
> 博客: http://lxgzhw.com
>
> GitHub: https://github.com/lxgzhw520



## 001.概念

shell程序就是把多个命令罗列在一块

会重复执行的命令写成一个脚本会比较方便



## 002.第一个shell程序

![image-20190803115356046](assets/image-20190803115356046.png)

```sh
hostname
> /data/f1.log
```



## 003.指定环境的shell程序

```shell
#!/bin/bash
hostname
enable
> /data/f2.logc
```

![image-20190803120209689](assets/image-20190803120209689.png)



## 004.变量

- 类型
  - 字符
  - 数值
    - 整型
    - 浮点型
- 作用
  - 数据存储格式
  - 参与运算
  - 表示数据范围
- 命名规则
  - 不能使用保留字
  - 只能使用数字,字母及下划线
  - 不能以数字开头
  - 见名知意
  - 常见命名方法
    - 小驼峰
    - 大驼峰
    - 蛇形



- 案例:变量的定义和使用

```shell
name="lxgzhw"
echo "My name is $name"
```

![image-20190803141351386](assets/image-20190803141351386.png)



## 005.vim配置sh文件自动添加头部注释

```shell
autocmd BufNewFile *.c,*.cpp,*.sh,*.py,*.java exec ":call SetTitle()"                                                                                       
"定义函数SetTitle，自动插入文件头
func SetTitle()
        "如果文件类型为.c或者.cpp文件
        if (&filetype == 'c' || &filetype == 'cpp')
                call setline(1, "/*************************************************************************")  
                call setline(2, "\ @Author: 张大鹏")  
                call setline(3, "\ @Created Time : ".strftime("%c"))  
                call setline(4, "\ @File Name: ".expand("%"))  
                call setline(5, "\ @Description:")  
                call setline(6, " ************************************************************************/")  
                call setline(7,"")  
        endif
        "如果文件类型为.sh文件
        if &filetype == 'shell'  
                call setline(1, "\#!/bin/sh")
                call setline(2, "\# Author: 张大鹏")
                call setline(3, "\# Created Time : ".strftime("%c"))
                call setline(4, "\# File Name: ".expand("%"))
                call setline(5, "\# Description:")
                call setline(6,"")
        endif
        "如果文件类型为.py文件
        if &filetype == 'python'
                call setline(1, "\#!/usr/bin/env python")
                call setline(2, "\# -*- coding=utf8 -*-")
                call setline(3, "\"\"\"")
                call setline(4, "\# Author: 张大鹏")
                call setline(5, "\# Created Time : ".strftime("%c"))
                call setline(6, "\# File Name: ".expand("%"))
                call setline(7, "\# Description:")
                call setline(8, "\"\"\"")
                call setline(9,"")
        endif
        "如果文件类型为.java文件
        if &filetype == 'java'  
                call setline(1, "//coding=utf8")  
                call setline(2, "/**")  
                call setline(3, "\ *\ @Author: 张大鹏")  
                call setline(4, "\ *\ @Created Time : ".strftime("%c"))  
                call setline(5, "\ *\ @File Name: ".expand("%"))  
                call setline(6, "\ *\ @Description:")  
                call setline(7, "\ */")  
                call setline(8,"")  
        endif
endfunc
" 自动将光标移动到文件末尾
autocmd BufNewfile * normal G
```



## 006.脚本中调用另一个脚本

- 案例: 在father.sh中执行son.sh

![image-20190803143348877](assets/image-20190803143348877.png)

`father.sh`

```shell
father="God"

echo "My father is $father"

./son.sh
```

`son.sh`

```shell
son="unknown"
echo "My son is $son"
```



