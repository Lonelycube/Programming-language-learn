# R语言基础（一）：基础语法

[TOC]



## 一、基础语法

### 1.基础命令

```R
getwd()                        #获取当前工作目录
setwd("F:/R/R_learn")          #设置工作目录

install.packages('ggplot2')    #安装R包
library(ggplot2)               #载入R包
update.packages()              #更新R包
library()                      #查看已经安装的包
detach("package:packagename")  #卸载加载的包（注意不是删除包）
remove.packages("packagename") #删除R包


help(mean)     #查看帮助
?mean          #查看帮助


```

### 2.赋值

```R
# R赋值采用<-或者->或者=，建议采用标准的第一个。
# 因为<-敲起来比等号要麻烦，且大部分情况下两者是等价的，所以通常就愉懒依旧用”=”来赋值。但要切记两者在某些时候是有区别的。字面上的解释，可以认为”<-”是赋值，”=”是传值。在函数调用中，func(x=1)与func(x<-1)是有区别的，前者调用完后变量x不会被保留，而后者会在工作区里保留变量x=1。再如length(x=seq(1,10))计算完成后x不会被保留，而length(x<-seq(1,10))计算完后你会在工作区里发现x这个变量。
# 由于R中内置了同名函数c()，最好不要在编码时使用c作为对象名

a <- 133
"hello" -> b  #注意无论哪种写法，大于或小于号都是指向变量名
d = 'This'    #不建议这么用，有可能会造成问题

```

### 3.数据的读取与保存

```R
# 通用读取
read.table(file,sep,hesder = TRUE)    
#file 文件路径  
#sep 分隔符 常见空白分隔符有：空格，制表符，换行符,即sep=" "; sep = "\t"; sep = "\n"
#header 第一行是不是列名（是列名则导入的时候填TRUE；默认值是FALSE，即把第一行算作数据）

# 读取csv
data <- read.csv('F:/table1_1.csv') 
head(data,6)                   #读取前 6行的数据
attach(data)                   #简单来说，可把列名直接当做变量用，把数据放到R search里
detach(mtcars)                 #解除之前的attach操作，把数据移除R search

# 读取 Excel数据
library(xlsx)                  #需要安装 xlsx 包
data <- read.xlsx("file",n)    #n 为要导入工作表的序号

# 读取 spss数据
library(foregin)               #已经默认安装
data <- read.spss("file",use.value.labels=TRUE,as.data.frame=TRUE)

# 读取 R格式数据
data <- load('F:/r1.RData')

# 写入文件
write.table(data,file,sep)
write.csv(data,file)           #保存为csv格式
write.csv(data3,'save.csv',row.names = FALSE)    #保存为csv格式，并删去行号
```

### 4.简单的操作，初步认识R语言

```R
v = c(1,4,4,3,2,2,3)   #c()创建一个数字向量，并赋值给 v 

v[c(2,3,4)]      #返回变量v中的第2，3，4个元素
v[2:4]           #返回变量v中的第2-4个元素
v[c(2,4,3)]      #返回变量v中的第2，4，3个元素
v[-2]            #返回时删去第2个元素，变量v不变
v[-2:-4]         #返回时删去第2-4个元素，变量v不变
v[v<3]           #返回变量v中所有小于3的数
which(v==3)      #返回变量v中等于3的元素的位置
which.max(v)     #返回变量v中最大的元素的位置（第一个最大值）
which.min(v)     #返回变量v中最小的元素的位置（第一个最小值）

set.seed(250)    #用于设定随机数种子，一个特定的种子可以产生一个特定的伪随机序列
#这个种子是R内部的设定好的，在任何用户的R中，第一次的调用结果是一样的，便于模拟的可重复
a = runif(3, min=0, max=100)   #随机产生3个数，最小是0，最大是100

floor(a)         #取整 '地板'值，即不小于该数字的最小整数
ceiling(a)       #取整 '天花板'值，即不大于该数字的最小整数
round(a,4)       #取整 '四舍六入五成双'
# “四”是指≤4 时舍去，"六"是指≥6时进上，"五"指的是根据5后面的数字来定，当5后有数时，舍5入1；当5后无有效数字时，需要分两种情况来讲：
#（1）5前为奇数，舍5入1；
#（2）5前为偶数，舍5不进（0是偶数）。
```

------

