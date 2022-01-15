# SQL-learn
 自我學習筆記
=
* create database `我要創建的資料庫名稱`;
創建資料庫
* SHOW databases;
查找現有的所有資料庫
* drop database `我要刪除的資料庫名稱`;
刪除資料庫
* use`我要使用的資料庫`;選擇我要用的資料庫


常用到的表格
=
* INT              -- 整數
* DECIMAL(m,n)     -- 有小數點的整數: m 總更有幾位數  n 小數點佔幾位
* VARCHAR(n)	     -- 字串:n代表最多存放幾個字元
* BLOB			 -- (Binary Large Object) 圖片 影片 檔案
* DATE			 -- `YYYY-MM-DD` 日期
* TIMESTAMP		 -- `YYYY--MM-DD HH:MM:SS` 紀錄時間


創建表格
=
		create table `student`(
		`student_id` int primary key,
 		`name` varchar(20),
    		`major` varchar(20)
		);
