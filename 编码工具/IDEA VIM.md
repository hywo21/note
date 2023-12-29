#编码工具  #Areas/VIM  #IDEAVIM
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
```ad-example
“Hello *world!”            ds”    Hello world! 
```
```ad-help
ds + “ { ' t ( 等 删除光标附近的环绕字符
```

```ad-example
 [123 + 4*56]/2            cs])  (123+456)/2 
```
```ad-help
cs + old new 修改光标附近的环绕字符
```

```ad-example

  if *x>3                  ysW(  if ( x>3 ) 
```
```ad-help
ys + 字符对象（w b e t f jk等）+ 环绕字符  从光标位置 到指定的字符对象结尾或开头增加环绕字符
```

```ad-example
 “Look ma, I’m *HTML!” |  cs"<p>  <q>Look ma, I'm HTML!</p> 
```
```ad-help
v 选中字符 + S + 环绕字符 对选择文本增加环绕字符
```

