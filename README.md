# SQL-learn
自我學習筆記


創建資料庫 
--
* create database `我要創建的資料庫名稱`;<br>  

顯示資料庫 
--
* SHOW databases;<br>  

刪除資料庫 
--
* drop database `我要刪除的資料庫名稱`;<br>  

選擇資料庫
--
* use`我要使用的資料庫`;<br> 

選擇表格 
--
* describe `我的表格`; <br>  

刪除表格
--
* drop table`我的表格`;<br>  

在表格中插入新的列
--
* ALTER table `我要的表格` add `列` decimal(3,2)<br>

刪除表格中的某一列
--
* alter table `選擇的表格` drop column `列`;<br>

在表格中放入一些值
--
* insert into `選擇的表格` valueS(1,'明劭','化工',0.2); 插入的位子需跟設定的值一樣,不然會插入失敗<br>

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
		
		primary key (`studeny_id`), == `student_id` int primary key,
