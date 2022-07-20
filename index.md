R中设计矩阵
在R中,模型Matrix是一个有用的工具，可以用来查看在构建回归模型时发挥作用的设计矩阵。
1.构建一个简单的数据框
首先，构建一个简单的数据框，以时间为因子，时间为连续的数字变量。打印数据框时，这两个变量看起来很相似。但是，如果你summary一下数据，你会发现它们是不同的。
d <- data.frame(time = factor(1:4), Time = 1:4)
d
## time Time
## 1 1 1
## 2 2 2
## 3 3 3
## 4 4 4
summary(d)
## time Time
## 1:1 Min. :1.00
## 2:1 1st Qu.:1.75
## 3:1 Median :2.50
## 4:1 Mean :2.50
##     3rd Qu.:3.25
##     Max. :4.00
R中的默认类型是 treatment contrasts，其中参考水平(控制)是因素变量的第一级，这是提供的值中数字或字母最低的一级。你可以将参考水平设置为你想要的因素的任何水平，注意，与其他列(time2、time3、time4)相关联的β是截取调整项。
model.matrix(~time, data = d)
## (Intercept) time2 time3 time4
## 1  1           0    0     0
## 2  1           1    0     0
## 3  1           0    1     0
## 4  1           0    0     1
## attr(,"assign")
## [1] 0 1 1 1
## attr(,"contrasts")
## attr(,"contrasts")$time
## [1] "contr.treatment"









