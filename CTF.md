# MISC

## gif图片

**分帧查看**

可能每一帧之间藏着flag

## jpg、png

首先查看是否是多个文件合成，使用binwalk进行文件叠加查看，然后使用foremost进行文件分离，查看分离出来的文件，一般有蕴藏flag信息

如果就是单一的一张图片，可以一Hex查看，search flag、ctf等关键词；

![image-20211002214127828](C:\Users\dyh\AppData\Roaming\Typora\typora-user-images\image-20211002214127828.png)

或者进行stegsolve查看，通过通道查看等方法寻找flag

## exe

一般都不是用来安装的，可以通过改后缀名为txt、html等进行查看，可以得到url或者直接就是flag

# Web

## php

开发者模式查看源码，发现注释掉的代码

![image-20211004103308609](C:\Users\dyh\AppData\Roaming\Typora\typora-user-images\image-20211004103308609.png)

这种需要在地址栏传参：？cat=dog直接得到flag

### 隐藏文件

发现有一个隐藏的flag.php文件，但是在url后面追加发现什么都没有，利用下面的语句进行查看

?file=php://filter/convert.base64-encode/resource=flag.php

得到base64加密后的密文，进行解密得到flag

## Sql注入

万能密码表

![image-20211019215919748](C:\Users\dyh\AppData\Roaming\Typora\typora-user-images\image-20211019215919748.png)

简单的注入直接从中选择尝试，可能直接登录成功。

注：

需要研究具体的绕过规则，审查源代码的函数限制

### 联合注入

查询字段数要一致



# Crypto

## md5

![image-20211015091237150](C:\Users\dyh\AppData\Roaming\Typora\typora-user-images\image-20211015091237150.png)

m.update需要在字符串后面加.encode('utf-8')

### windows系统密码

![image-20211015152841759](C:\Users\dyh\AppData\Roaming\Typora\typora-user-images\image-20211015152841759.png)

密码形式如上，

格式是：用户名称:RID:LM-HASH值:NT-HASH值

### 中文电码

由纯数字组成，每四位表示一个汉字

### 栅栏密码

可能和凯撒密码组合使用，先使用栅栏密码解密（一般长度较短，否则遍历太久），再使用凯撒解密

