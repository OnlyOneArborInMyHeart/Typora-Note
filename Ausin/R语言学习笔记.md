#### R语言学习笔记

1.read.csv(file_name)函数如果没有设置其他参数，读出来的数据类型是data frame(数据帧)

2.unlist(x) 其中x可以是R语言中的任何对象，可以将任何对象转换成向量类型(其他语言中的数组)

3.作图

​	3.1 hist(dataVector , xlab , ylab , main , ..)

用来做直方图，也就是棍状图，xlab更改横坐标名字，ylab更改纵坐标名字，main更改整个图的名字

特别的，如果想改横坐标的跨度和间隔，就要更改breaks属性，breaks = seq(st , ed , step) , 表示横坐标从st处开始，ed处结束，横坐标间隔为step

​	3.2 boxplot()

用来做箱型图

​	3.3 Pie()

用来做饼图

​	3.4 Barplot()

用来做棍状图

![image-20240719103844674](C:\Users\ROG\AppData\Roaming\Typora\typora-user-images\image-20240719103844674.png)

参数:

​	data : 向量格式

​	outline : 用来选择是否去掉异常值的

4.数字特征

​	mean() : 平均值

​	median() ： 中位数

​	sd() ：标准差

​	quantile() : 分位点

四分位数：

Q1 : 该样本中所有数值由小到大排列后第25%的数字

Q2 : 该样本中所有数值由小到大排列后第50%的数字 ，也就是二分位数的中位数

Q3 : 该样本中所有数值由小到大排列后第75%的数字

​	Example : 

​	quantile(unlistdata , probs = 0.25 , na.rm = TRUE)

​	这里应该习惯性要加na.rm , 因为在读入csv文件的时候会多读一个空白行，dataframe转换成向量数组的时候最后就会多出几个NA值，quantile必须将这些值去掉之后才能计算，na.rm = TRUE就是代表忽略掉NA值之后再计算分位点

​	summary() : 总结常见的数字特征，上述都是

5.命令行好用的交互函数

​	help("function_name") : 用来查函数的用法

​	demo("function_name") ：用来查函数demo

​	typeof(data) ：用来查数据类型

​	str(data) : 用来查数据类型和数据的值

6.设置工作空间

​	setwd("file_path") (file_path为绝对路径)

​		注意windows中要用"/"	

​	getwd() : 列出当前路径下的所有对象

​	install.packages("package_names") (这个函数很重要，是因为Rstudio的每个项目都是新的工作环境)

​	library() : 列出当前已经下载好了的包名

##### 7.好用的其他函数

​	save.image

​	save.image(file = "filename") : 把当前所有的内容保存到file中

​	load("filename") : 加载文件的R代码

​	unlink("filename") : 移除文件的R代码

##### 8.课堂笔记(1)

​	1.默认给常数就是double类型

​	2.需要使用as.integer()来进行转换

​	3.R语言中只有character , 没有String , 注意计算的时候要转换

​	4.factor ?? 集合？

​	5.table()可以制成表格形式

​	6.表名$列名可以提取出此列所有数据

​	7.生成附表使用subset函数，subset(表名,筛选条件)

​	8.summary(表名)可以总结表的数字特征

​	9.factor 类似于集合

​	10.select 选 col ，filter 选 row

​		select 可以灵活的使用字符串处理函数来将符合条件的列选出来

​		如：列名 : 列名 ， c(列名 ， 列名 ， 列名 ，...)  , | & 表达式

​	11.R语言中可用pipeline(管道模式，前一个命令的输出作为下一个命令的输入)

​	管道符号%>%

​	As kiat says , "step by step"

​	12.

##### 9.课堂笔记(2)

​	1.ggplot 用来组织df的图，比R语言原装的更加简便

​	2.原生的R语言的df , 但在dplyr包中为tibble , 要用as_tibble来转换

​	3.summarize根据原有表格生成数据特征的总结表格 ，如果原始表格没有被group过 ， 则生成的结果只有一行

​	如果数据事先被group过，则生成结果为多行。

##### 10.课堂笔记(3)

​	数据库连接操作

​	分为:

​	A join B(取交集)

​	A left join B(A并上交集)

​	A right join B(B并上交集)

​	A Full join B(并集)

​	A left outer join (A - B)

​	semi_join

​	anti_join

​	总的来说join操作可以看作两个集合之间做运算 ， 一个key值有v1，没有v2 , 则join之后v2的值为NA

​	cross join 表示为A X B , 是笛卡尔积 ， A的每个key都与B的每个key发生关系

​	可以将数据库看作一个键值对组成的集合，join操作就是对集合做各种运算

​	当两个表没有列名相同但是实际内容相同时，可以用by来使它们在连接时等同

​	
