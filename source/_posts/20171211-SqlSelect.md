---
title: Sql查询(1) -- 空格引发的无法查询问题
tags: 
category: 
	- SQL
toc: false
---
![ ](https://github.com/Mirbosk13s/ImageLibrary/blob/master/blog/p003.png?raw=true "SQL")
## 环境：SQL Server 2008 R2
### Q：空格引发的无法查询问题
**因：**sql查询时，存在微信昵称内包含空格的字符串,例：`-_-# -_-#`、`the one`,
当昵称为以上时，sql语句无法查到，查询语句例子如下：
```
SELECT * FROM WxFans WHERE Nickname LIKE '%-_-# -_-#%'
SELECT * FROM WxFans WHERE Nickname = '-_-# -_-#'
```
**解决方案：**将空格转为空
```
select * from WxFans where replace(Nickname,' ','')LIKE REPLACE('%-_-# -_-#%',' ','')
```
