+++
title = "Mysql数据库导出生成Word文档，HTML,PDF"
date = "2022-04-01T18:18:21+08:00"
+++
> 感谢csdn大佬的文章，
> 

```
前几天领导让我把数据库的表生成word文档，这之前也没弄过，只能百度查了，最后发现了三种方式可以满足
（1）SQL语句，适用于少量表 ，或者对格式没什么要求的
 （2）DBExportDoc V1.0 For MySQL---网上最多教程的工具，只能生成Word
 （3）PDMan---国产类似PowerDesigner的工具，开源，功能很强大，数据库表能生成多种格式
```

#sql
#javaweb
1.第一种 SQL

```sql
SELECT COLUMN_NAME 列名,COLUMN_TYPE 数据类型,DATA_TYPE 字段类型,CHARACTER_MAXIMUM_LENGTH 长度,IS_NULLABLE 是否为空,COLUMN_DEFAULT 默认值,COLUMN_COMMENT 备注 FROM INFORMATION_SCHEMA.COLUMNS where table_schema ='数据库名' AND table_name  = '表名'
```

![](https://img-blog.csdnimg.cn/2020072315220456.png)

OK，然后复制粘贴，成功。但是样式不敢保证，并且很多张表就凉了

在介绍一下PDMan生成Word，DBExportDoc V1.0 For MySQL这个会在后面的文章会写到，因为配置比价复杂，后续再详谈

2.PDman
（1）现在地址 http://www.pdman.cn/#/，然后根据提示进入到gitee
![](https://img-blog.csdnimg.cn/202007231528169.png)
（2）启动----画面整洁，爱了
![](https://img-blog.csdnimg.cn/20200723152907914.png)
（3）创建一个新项目
![](https://img-blog.csdnimg.cn/20200723152950334.png)
（4）点击数据库连接
![](https://img-blog.csdnimg.cn/2020072315303081.png)
（5）填关于数据的信息，测试成功后点击确定
（6）点击模型-数据库逆向解析-选择完毕后下一步
![](https://img-blog.csdnimg.cn/20200723153358730.png)
（7）解析成功后，数据库的表就能在列表上看见了
![](https://img-blog.csdnimg.cn/20200723153431248.png)
![](https://img-blog.csdnimg.cn/2020072315344986.png)
![](https://img-blog.csdnimg.cn/20200723153510711.png)
（8）点击导出文档，导出word（别的也都可以，看需要）
![](https://img-blog.csdnimg.cn/20200723153751971.png)
OK，完成，软件很简介，功能可很强大，反正我是爱了
有问题欢迎留言
