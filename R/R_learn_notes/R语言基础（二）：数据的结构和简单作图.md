# R语言基础（二）：数据的结构和简单作图

[TOC]



## 二、数据的结构和简单作图

### 1.向量 Vector

```R
a = c(1, 2, 5, 3, 6, -2, 4)                   #数值
b = c("one", "two", "three")                  #字符串
c = c(TRUE, TRUE, TRUE, FALSE, TRUE, FALSE)   #布尔值
```

### 2.矩阵 Matrix

```R
x = matrix(1:20, nrow=5, ncol=4, byrow=TRUE)  #按行填充
# 结果
     [,1] [,2] [,3] [,4]
[1,]    1    2    3    4
[2,]    5    6    7    8
[3,]    9   10   11   12
[4,]   13   14   15   16
[5,]   17   18   19   20

y = matrix(1:20, nrow=5, ncol=4, byrow=FALSE) #按列填充
# 结果
     [,1] [,2] [,3] [,4]
[1,]    1    6   11   16
[2,]    2    7   12   17
[3,]    3    8   13   18
[4,]    4    9   14   19
[5,]    5   10   15   20

# 对矩阵进行基本读取操作
x[2,]            #返回第2行的值
x[,2]            #返回第2列的值
x[1,4]           #返回第1行，第4个值
x[2,c(2,4)]      #返回第2行，第2，4个值
x[3:5, 2]        #返回第2列，第3-5个值

# 对矩阵中的行列号改名
x = matrix(1:20, nrow=5, ncol=4, byrow=TRUE)
rnames=c("A","B","C","D","E")
cnames=c("cat","dog","bird","pig")
rownames(x)=rnames     #更改行名，也可直接赋值，即rownames(x)=c("A","B","C","D","E")
colnames(x)=cnames     #更改行名
```

### 3.数组 Array

```R
# 数组是可以在两个以上的维度存储数据的R数据对象
# 这里我们创建一个维度为（2,2,2）的数组
dim1 = c("A1", "A2")
dim2 = c("B1", "B2")
dim3 = c("C1", "C2")
z = array(1:8, c(2,2,2), dimnames=list(dim1,dim2,dim3))
# 结果如下
, , C1
 B1 B2
A1  1  3
A2  2  4

, , C2
   B1 B2
A1  5  7
A2  6  8

# 对数组的操作
z[1,2,2]    #返回第2个矩阵的第1行，第2列
```

### 4.数据框 Dataframe

```R
# Dataframe 是一个表格或者类似二维数组的结构，它的各行表示一个实例，各列表示一个变量。
# 下面构建一个数据框
ID = c(1, 2, 3, 4)
age = c(25, 34, 28, 52)
diabetes = c("Type1", "Type2", "Type1", "Type1")
status = c("Poor", "Improved", "Excellent", "Poor")
patientdata = data.frame(ID, age, diabetes, status)
# 结果为
  ID age diabetes    status
1  1  25    Type1      Poor
2  2  34    Type2  Improved
3  3  28    Type1 Excellent
4  4  52    Type1      Poor

# 对数据框进行操作
patientdata[1:2]          #返回第1-2列
patientdata[1:3]          #返回第1-3列
patientdata[1,1:3]        #返回第1行的第1-3列
patientdata[c(1,3),1:3]   #返回第1，3行的第1-3列

```

### 5.列表 List

```R
# 列表是对象的集合，可以包含向量、矩阵、数组，数据框，甚至是另外一个列表，且在列表中要求每一个成分都要有一个名称。列表中的对象又称为它的分量。
# 这里创建一个列表
list1 <- list(studentName = c("小明", "小花", "小芳", "小刚"),
              major = c("信息管理", "财务管理", "材料成型"), 
              score = matrix(c(80, 90, 75, 85, 92, 83, 73, 70, 69, 88, 81, 89), 
                             nrow=3))
# 结果为
$studentName
[1] "小明" "小花" "小芳" "小刚"

$major
[1] "信息管理" "财务管理" "材料成型"

$score
     [,1] [,2] [,3] [,4]
[1,]   80   85   73   88
[2,]   90   92   70   81
[3,]   75   83   69   89

# 对列表进行数据读取一些操作
list1[1]         #访问列表中的第1个成分，使用这种方法，返回的结果仍为一个列表
list1[[1]]       #访问列表中的第1个成分的元素值，这次仅是元素值，是向量，不再是列表
list1[1:2]       #访问列表中的第1个到第2个成分
list1[-1]        #排除第一个成分，返回其他成分，结果仍是列表
list1[c(1, 3)]   #访问给定的第1和第3个成分

list1$studentName       #访问成分名称为studentName的元素值
list1["major"]          #访问成分名称为major的成分，其结果仍为一个列表
list1[["major"]]        #访问成分名称为major的元素值

list1[[1]][1]                  #访问第一个成分中的第一个值
list1$studentName[1]           #访问studentName成分中的第一个值
list1[["studentName"]][1]      #访问studentName成分中的第一个值

# 修改某个成分的元素值
list1[[1]][1] = '黄晓明'
list1$studentName[2] = '王花花'
list1[["studentName"]][3] = '袁芳'

#修改某一成分的所有值
list1$major = c("信息管理", "营销管理", "工商管理", "会计学")
list1[[2]] = c("信息管理", "营销管理", "工商管理", "会计学")

#添加一个成分
list1$grade<-c(3, 4 ,2 ,1)                 #实际上，若没有这一列就直接添加
list1 <- c(list1, 
           birth = list(c("1997-04-01",
                          "1998-10-20",
                          "1998-07-20",
                          "1999-11-20")))  #新增birth成分

#删除某一个成分
list1[4] = NULL      #删除第4个成分
list1$grade = NULL   #删除第4个成分
```

### 6.图表 Graphs

```R
pch   #指定绘制点所使用的符号，取值范围[0, 24]，其中4是“差号”，20是“点”

cex   #指定符号的大小。cex是一个数值，表示pch的倍数，默认是1.5倍

lty   #指定线条类型。lty=1代表实线，2至6都是虚线，虚的程度不一样

lwd   #指定线条宽度，默认值为lwd=1，可以适当修改1.5倍、2倍等
```

![](F:\desktop---------------------------\图片++++++++++++++\截图\捕获.PNG)

```R
par(mfrow=c(2,2))
plot(rnorm(50),pch=17)
plot(rnorm(20),type="l",lty=5)
plot(rnorm(100),cex=0.5)
plot(rnorm(200),lwd=2)
# 结果如下
```

![](F:\desktop---------------------------\图片++++++++++++++\截图\捕获2.PNG)

```R
# layout（）的调用形式为layout（mat），其中mat是一个矩阵，它指定了所有要组合的多个图形的所在位置。
attach(mtcars)
layout(matrix(c(1,1,2,3), 2, 2, byrow = TRUE))
# 上述layout表示，首先按照2行2列来排布，1图放在第一行，2图、3图整个放在第二行。

hist(wt)
hist(mpg)
hist(disp)
detach(mtcars)
# 结果如下图
```

![](F:\desktop---------------------------\图片++++++++++++++\截图\捕获3.PNG)

