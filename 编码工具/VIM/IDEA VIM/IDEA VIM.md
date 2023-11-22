#### **如何安装**
---
IDEA下安装以下插件
```
- ideaVim
- ideaVim-EasyMotion
- ideaVimExtension
- AceJump
- Which-Key
```

#### **编辑.ideavimrc**
---
> 参考地址：https://github.com/JetBrains/ideavim/wiki/

[[ideavimrc]]

#### IDEA VIM 插件
---
* ***argtextobj插件（参数操作）**

安装
```
set argtextobj
```

使用
```
提供了 一个text 对象 -- a 
可以使用 动作 + 介词 + a 
例子： 
public void get(int a, int b); 
via: public void get([int a], int b);
```

* **vim-surround 插件**

安装
```
set surround
```

支持命令
```
ys cs ds S
```

实例
```
“Hello *world!”            ds”    Hello world! 
 [123 + 4*56]/2            cs])  (123+456)/2 
  if *x>3                  ysW(  if ( x>3 ) 
 “Look ma, I’m *HTML!” |  cs"<p>  <q>Look ma, I'm HTML!</p> 
```

