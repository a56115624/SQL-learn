# SQL-learn


自我學習筆記
==




創建資料庫 
--
* create database `我要創建的資料庫名稱`;<br>  

顯示所有的資料庫 
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
* insert into `選擇的表格` valueS(1,'明劭','化工',0.2); 插入的位子需跟設定的值一樣,不然會插入失敗,如果沒有值要填入 null<br>
* insert into `student`(`name`,`major`,`student_id`,`gpa`) valueS('狗狗','吃骨頭',3,0.78);   也可以在表格後加入小括號()來改變填入的順序<br>

搜尋資料庫中所有的資料
--
* select * from `你要搜尋的資料庫`;

創建資料庫時,後面補上的以更方便的使用
--
*  not  null       該值不能是空白
*  unique          該列的值視為一個不能重複
*  default ‵值`     設定一個預設值,如果是空白的時候會自動補上
*  auto_increment  自動增加列


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
		
新增修改
=
		update `student`           //你要改的表格
		set `major` = '英語文學'   //你要改的列 = 你要換成的資料
 		where `major` = '英文';    //你要改的列 = 你原本的資料
		
		
		update `student`
		set `name` = '汪汪', `major` = '吃屎'
		where `student_id` = 1;
刪除
=
		delete FROM `student`
		where `student_id` = 4;


		delete from `student`
		where `name` = '狗狗' and  `score` = '20';
取的資料
=
		select * from `student` order by `score`;            order by 從低到高排序
		select * from `student` order by `score` desc ;      desc 由低到高排序    asc 由低到高排序   <> 不等於  distinct 不重複
		WHERE `MAJOR` IN('化工','吃屎','讀書');  =  WHERE `MAJOR` = '化工' OR `MAJOR` = '吃屎' OR `MAJOR` = '讀書';
		
創建資料庫
=
		create table `employee`(
		`emp_id` int primary key,
    		`name` varchar(20),
		    `brith_date` Date,
		    `sex` varchar(1),
		    `salary` int,
		    `branch_id` int,
		    `sup_id` int
		);

		create table `branch`(
			`branch_id` int primary key,
		    `branch_name` varchar(20),
		    `manager_id` int,
		    foreign key (`manager_id`) references `employee`(`emp_id`) on delete set null
		);

		alter table `employee`
		add foreign key(`branch_id`)
		references `branch`(`branch_id`)
		on delete set null;


		alter table `employee`
		add foreign key(`sup_id`)
		references `employee`(`emp_id`)
		on delete set null;

		create table `client`(
			`client_id` int primary key,
		    `client_name` varchar(20),
		    `phone` varchar(20)
		);

		create table `works_with`(
			`emp_id` int,
		    `client_id` int,
		    `total_sales` int,
		    primary key(`emp_id`,`client_id`),
		    foreign key(`emp_id`)references `employee`(`emp_id`) on delete cascade,
		    foreign key(`client_id`)references `client`(`client_id`) on update cascade
		);
新增公司資料
=
		insert into `employee` values(206,'998-10-08','f',5000,1,null);
		insert into `employee` values(207,'小綠','1985-09-96','m',2900,2,206);
		insert into `employee` values(207,'小綠','2000-12-19','m',3600,3,208);
		insert into `employee` values(209,'小白','1997-01-22','f',3900,3,207);
		insert into `employee` values(210,'小藍','1925-11-10','f',8400,1,207);
		
		
		insert into `client` values(400,'阿貓','2488648654');
		insert into `client` values(401,'阿狗','1561655416');
		insert into `client` values(402,'旺來','1565165');
		insert into `client` values(403,'露西','156165135');
		insert into `client` values(404,'艾瑞克','4894894153');
練習
=
		-- 1.取得所有員工資料
		select * from `employee`;
		-- 2.取得所有客戶資料
		select * from `client`;
		-- 3.按照薪水低到高取得員工資料
		select * from `employee`order by `salary`;
		-- 4.按照薪水高到低取得員工資料
		select * from `employee`order by `salary`desc;
		-- 5.取得薪水前3高薪水的員工
		select * from `employee`order by` salary` desc limit 3;
		-- 6.取得所有員工的名子
		select `name` from `employee`;
		-- 7. 取得所有的branch_id且不重複
		select  distinct `branch_id` from `employee`;
		
aggregate function 聚合函數
==



		-- 1.取得員工人數
		select count(*) from `employee`;
		select count(`sup_id`) from `employee`;
		
		-- 2.取得所有出生於1970-01-01 之後的女性員工人數 
		select count(*) 
		from `employee` 
		where `birth_date` > '1970-01-01' 
		and `sex` = 'f';
		
		-- 3.取得所有員工的平均薪水
		select avg(`salary`) from `employee`;

		-- 4. 取得所有員工薪水的總和
		select sum(`salary`) from `employee`;

		-- 5. 取得薪水最高的員工
		select max(`salary`) from `employee` ;

		-- 6. 取得薪水最低的員工
		select min(`salary`) from `employee`;
