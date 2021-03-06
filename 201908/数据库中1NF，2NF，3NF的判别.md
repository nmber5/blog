﻿# 数据库中1NF，2NF，3NF的判别

标签： `数据库` `范式`

---

首先知道两个依赖：  

1、完全依赖  

比如`（x,y）->z`并且x或者y都不能单独得到z，则z是对(x,y)的完全依赖。
2、部分依赖  

比如`（x,y）->z`，但是`x->z`,则z是对（x,y）的部分依赖。  

3、传递依赖   

比如`x->y y->z`则z是对x的传递依赖（`x`可能也是一个组合比如`(x1,x2)->y y->z`）  


开始正餐，首先要知道范式从1NF到3NF以及BCNF是依次更好，如果达到3NF，则肯定满足1NF和2NF。如果达到1NF或2NF则不一定为3NF。

一、1NF 第一范式   

平时能录入数据库的都能达到第一范式，第一范式只要满足每个属性是原子属性即可，举个栗子：如下表   

![image](http://wx3.sinaimg.cn/large/005Dd0fOly1g5qx2cusd1j306o020jr5.jpg)  

因为地址又包含了省和市，所以不满足原子属性，如果想改为第一范式，则把省市分开为两个属性即可：
|姓名|省|市|
|--|--|--|  

这样就达到了1NF 。  

二、2NF第二范式  

想要看是否为2NF，首先要找表的主键，之后看所有的非主键要对关键码是完全依赖，也就是不存在部分依赖，如果有部分依赖则不满足2NF，否则满足2NF，比如一个关系的关键码为`（x,y）`，非主属性为z首先因为`（x,y）`是关键码，所以一定能得到z，如果存在`x->z`或者`y->z`则说明z是部分依赖，则不满足2NF，否则满足2NF。  

三、3NF第三范式  

要想达到3NF，首先要判断是否为2NF，然后看里面是否有传递依赖，其实就是看其他的非主键之间有没有依赖，如果有主键x,还有非主键y z w，如果有其他的非主键之间的依赖比如y->z 则不满足3NF，因为有主键肯定能推出非主键即，x->y,而又有y-z,所以存在传递依赖，则不满足3NF，否则满足3NF。  

四、BC范式  

首先满足3NF，然后主要是看主键了，所有的主键对于每一个不包含他的其他主键也要是完全依赖，比如主键`(x,y,z)`，那么z对`(x,y)`要是完全依赖。  










