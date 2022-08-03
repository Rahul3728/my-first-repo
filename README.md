# my-first-repo
mainly for hands-on purposes
-------------------------------------------------------------------Traning_day_2_part1-------------------------------------------------------------------------------

-- MY WORKS BEGIN FROM HERE
CREATE TABLE TRAINING_DAY_2 ( NAME VARCHAR(30) NOT NULL , PHONE_NO BIGINT NOT NULL , LOCATION VARCHAR(20) NOT NULL)

-- ADDING COLUMN NAME 'DEPARTMENT'
ALTER TABLE TRAINING_DAY_2 ADD DEPARTMENT VARCHAR(50) NOT NULL
SELECT * FROM TRAINING_DAY_2

-- NOW I WANT TO ADD COLUMN BUT NOT GIVING ANY NAME USING 'TIMESTAMP' DATA TYPE
ALTER TABLE TRAINING_DAY_2 ADD TIMESTAMP NOT NULL
--ABOVE MENTION TIME STAMP IS NOT COLUMN TYPE ACTUALLY IT IS DATA TYPE

--TO MODIFY COLUMN 
ALTER TABLE TRAINING_DAY_2 ADD  STATE VARCHAR(10) NOT NULL
ALTER TABLE TRAINING_DAY_2 ALTER COLUMN STATE INT NOT NULL
SELECT * FROM TRAINING_DAY_2

--TO DROP A COLUMN 
ALTER TABLE TRAINING_DAY_2 ADD  SPECIALISATION VARCHAR(30) NOT NULL
ALTER TABLE TRAINING_DAY_2 DROP COLUMN SPECIALISATION 

--TO ADD PRIMARY KEY
ALTER TABLE TRAINING_DAY_2 ADD STUDENT_ID INT NOT NULL
ALTER TABLE TRAINING_DAY_2 ADD CONSTRAINT TRAINING_DAY_2_STUDENT_ID PRIMARY KEY (STUDENT_ID)

--TO DROP PRIMARY KEY
ALTER TABLE TRAINING_DAY_2 DROP CONSTRAINT TRAINING_DAY_2_STUDENT_ID 

--TO ADD UNIQUE KEY CAUTION-'DO NOT USE KEY ALONG UNIQUE SYNTAX ERROR' USE- THAT ALL VALUES WILL BE DIFFERNT 
ALTER TABLE TRAINING_DAY_2 ADD CONSTRAINT TRAINING_DAY_2_STUDENT_ID UNIQUE  (STUDENT_ID)

-- TO DROP UNIQUE KEY
ALTER TABLE TRAINING_DAY_2 DROP CONSTRAINT TRAINING_DAY_2_STUDENT_ID 

-- TO ADD DEFAULT CONSTRAINT 
ALTER TABLE TRAINING_DAY_2 ADD JOB_LOCATION VARCHAR(50) NOT NULL
ALTER TABLE TRAINING_DAY_2 ADD CONSTRAINT TRAINING_DAY_2_JOB_LOCATION DEFAULT 'NOIDA' FOR JOB_LOCATION

-- TO ADD FOREIGN KEY
CREATE TABLE TRAINING_DAY_GENDER (ID INT PRIMARY KEY, GENDER VARCHAR(30) NOT NULL)
ALTER TABLE TRAINING_DAY_2 ADD CONSTRAINT TRAINING_DAY_2_STUDENT_ID_FK FOREIGN KEY (STUDENT_ID) REFERENCES TRAINING_DAY_GENDER (ID)
ALTER TABLE TRAINING_DAY_2 DROP CONSTRAINT TRAINING_DAY_2_STUDENT_ID_FK

--TO ADD CHECK CONSTRAINT' IT IS USED TO LIMIT RANGE VALUES AND CAN BE APPLIED TO COLUMN AND TABLE '
ALTER TABLE TRAINING_DAY_2 ADD AGE INT NOT NULL
ALTER TABLE TRAINING_DAY_2 ADD CONSTRAINT TRAINING_DAY_2_AGE CHECK( AGE > 18)
INSERT INTO TRAINING_DAY_2 (NAME, PHONE_NO , LOCATION , DEPARTMENT , STATE , STUDENT_ID , AGE) 
VALUES ('KUMAR','914971790','RAXAU','BPS ANALYTICS','03','037','19'),('GUPTA','91497179','MOTIHARI','BPS ANALYTICS','04','038','19'),
('RKG','9149717923','RAXTH','BPS ANALYTICS','05','039','21'),('RHJF','9149717908','RAXTHJ','BPS ANALYTICS','06','040','21'),
('RAKLJ','9149717789','SDFGH','BPS ANALYTICS','07','041','20'),('FGHJK','914956789','RAJKLL','BPS ANALYTICS','08','042','20'),
('TYHJUK','91456789','EDFHJ','BPS ANALYTICS','09','043','21'),('EFGHJUK','914345689','RARGHJ','BPS ANALYTICS','10','044','20'),
('RGYHJKL','9149723456','RRFGHK','BPS ANALYTICS','11','045','20'),('RKLJI','914934678','RAYUKOL','BPS ANALYTICS','12','46','19')
INSERT INTO TRAINING_DAY_GENDER VALUES ('1','MALE'),('2','FEMALE'),('3','UNKNOWN')
SELECT * FROM TRAINING_DAY_GENDER
SELECT * FROM TRAINING_DAY_2


-----------------------------------------------------------------------------



-- TABLE WITH ALL CONSTRAINT

CREATE TABLE TRAINING_DAY_2_SQL_TEAM ( S_NO INT NOT NULL PRIMARY KEY, NAME VARCHAR(30) NULL DEFAULT 'TECHIES' , 
INTERN_ID VARCHAR (30) UNIQUE , AGE INT CHECK (AGE >17))
INSERT INTO TRAINING_DAY_2_SQL_TEAM (S_NO,INTERN_ID,AGE) VALUES('1','R1023','19'),('2','R1024','19'),('3','R1025','19'),
('4','R1026','19'),('5','R1027','19'),('6','R1028','19'),('7','R1029','19'),('8','R1030','19')
SELECT * FROM TRAINING_DAY_2_SQL_TEAM

-- TABLE WITH CONSTRAINT AND WITH ITS NAME

CREATE TABLE TRAINING_DAY_2_SQL_TEAM_1( S_NO INT NOT NULL , NAME VARCHAR(30) CONSTRAINT NAME_DF DEFAULT 'MIGHTIES' ,
INTERN_ID VARCHAR(30) NOT NULL , AGE INT NOT NULL,
CONSTRAINT PK_S_NO PRIMARY KEY (S_NO),
CONSTRAINT UNIQUE_INTERN_ID UNIQUE(INTERN_ID),
CONSTRAINT CHECK_AGE CHECK(AGE > 17))
SELECT * FROM TRAINING_DAY_2_SQL_TEAM_1

--TO ADD AUTO INCREMENT IN PRIMARY KEY BY 1 THEN 
ALTER TABLE TRAINING_DAY_2_SQL_TEAM_1 ALTER COLUMN S_N0 INT NOT NULL IDENTITY(100,10) PRIMARY KEY
INSERT INTO TRAINING_DAY_2_SQL_TEAM_1 (S_NO,INTERN_ID,AGE) VALUES('1','R1023','19'),('2','R1024','19'),('3','R1025','19'),
('4','R1026','19'),('5','R1027','19'),('6','R1028','19'),('7','R1029','19'),('8','R1030','19')
SELECT * FROM TRAINING_DAY_2_SQL_TEAM_1
SELECT * FROM TRAINING_DAY_2_SQL_TEAM

--TO CREATE USING INFO OF SOME EXISTING TABLE
CREATE TABLE TRAINING_DAY_2_SQL_TEAM_2 AS 
SELECT  INTER_ID ,AGE 
FROM TRAINING_DAY_2_SQL_TEAM_1

--------------------------------------------------------------------
-------------------------------------------------------------------
-------------------------------------------------------------------


-- THIS WILL CONTAIN DATA NORMALISATION
CREATE TABLE 
TRAINING_NORMALISATION (
SalesPerson varchar(50) not null,
SalesOffice varchar(50) not null ,
OfficePhoneNo BIGINT NOT NULL,
Customer1 varchar(150) ,
Customer2 varchar(150) ,
Customer3 varchar(150)
) 
select distinct  SalesPerson ,SalesOffice from 
TRAINING_NORMALISATION



INSERT INTO 
TRAINING_NORMALISATION (
SalesPerson, 
SalesOffice,
OfficePhoneNo,
Customer1,
Customer2
) 
VALUES 
('RAHUL KUMAR','NOIDA','3125551212','TATA,DELHI,94000' , 'MHINDRA,MUBAI,50000')
INSERT INTO 
TRAINING_NORMALISATION(
SalesPerson, 
SalesOffice,
OfficePhoneNo,
Customer1,
Customer2,
Customer3
) 
VALUES 
('GUPTA KUMAR','BANGLORE','41235551212','HYUNDAI,GURGAON,60000' , 'MARUTI,THANE,70000', 'KTM,PATNA,80000')
INSERT INTO 
TRAINING_NORMALISATION(
SalesPerson,
SalesOffice,
OfficePhoneNo,
Customer1
) 
VALUES 
('GUPTA RAHUL','NOIDA','3125551212','BAJAJ,RAXAUL,90000')
select * from 
TRAINING_NORMALISATION


-- FIRST NORMAL FORM SHOULD INCLUDE PRIMARY KEY, NON ATOMIC VALUES , NON REPEATING COLUMNS
CREATE TABLE 
SALESPERSONINFORMATION (
EMPLOYEEID INT NOT NULL ,
SalesPersonFIRST varchar(50) not null,
SalesPersonLAST varchar(50) not null,
SalesOffice varchar(50) not null ,
OfficePhoneNo BIGINT NOT NULL
)
ALTER TABLE 
C 
DROP COLUMN 
SalesPersonLAST
SP_RENAME 
'SALESPERSONINFORMATION.SalesPersonFIRST',
'SalesPerson',
'COLUMN'
SELECT * FROM 
SALESPERSONINFORMATION

ALTER TABLE 
SALESPERSONINFORMATION 
ADD CONSTRAINT EMPLOY_ID_PK PRIMARY KEY (EMPLOYEEID)

CREATE TABLE 
CUSTOMER (
CUSTOMERID INT NOT NULL ,
EMPLOYEEID INT NOT NULL ,
NAME VARCHAR (50),
CITY VARCHAR(50) ,
POPULATION INT ,
CONSTRAINT CUSTOMER_ID_PK PRIMARY KEY (CUSTOMERID),
CONSTRAINT FK_EMPLOYEEID FOREIGN KEY (EMPLOYEEID) REFERENCES SALESPERSONINFORMATION (EMPLOYEEID)
)
select * from 
TRAINING_NORMALISATION
SELECT * FROM 
SALESPERSONINFORMATION
SELECT * FROM 
CUSTOMER
INSERT INTO 
SALESPERSONINFORMATION 
VALUES 
('001','RAHUL KUMAR','NOIDA','3125551212'),
('002','GUPTA KUMAR','BANGLORE','41235551212'),
('003','GUPTA RAHUL','NOIDA','3125551212')
INSERT INTO CUSTOMER 
VALUES
('101','01','TATA','DELHI','94000'),
('102','01','MHINDRA','MUBAI','50000'),
('103','02','HYUNDAI','GURGAON','60000'),
('104','02','MARUTI','THANE','70000'),
('105','02','KTM','PATNA','80000'),
('106','03','BAJAJ','RAXAUL','30000')
select * from
TRAINING_NORMALISATION
SELECT * FROM
SALESPERSONINFORMATION
SELECT * FROM 
CUSTOMER

-- second normal form
CREATE TABLE 
SALESSTAFFCUSTOMER (
CUSTOMERID INT NOT NULL ,
EMPLOYEEID INT NOT NULL,
CONSTRAINT FK_CUS_ID FOREIGN KEY (CUSTOMERID) REFERENCES CUSTOMER (CUSTOMERID), 
CONSTRAINT FK_EMP_ID FOREIGN KEY (EMPLOYEEID) REFERENCES SALESPERSONINFORMATION (EMPLOYEEID)
)

ALTER TABLE 
SALESSTAFFCUSTOMER 
DROP CONSTRAINT FK_EMP_ID 

ALTER TABLE 
SALESSTAFFCUSTOMER 
DROP CONSTRAINT FK_CUS_ID

CREATE TABLE 
SALESSTAFFOFFICE (
OFFICEID INT NOT NULL ,
OFFICEPHONENO BIGINT NOT NULL,
OFFICELOCATION VARCHAR (50) NOT NULL,
CONSTRAINT PK_OFFICE_ID PRIMARY KEY (OFFICEID)
)


CREATE TABLE 
SALESPERSONINFORMATION1 (
EMPLOYEEID INT NOT NULL ,
SalesPerson varchar(50) not null,
OFFICEID INT NOT NULL
CONSTRAINT FK_OFFICE_ID FOREIGN KEY (OFFICEID) REFERENCES SALESSTAFFOFFICE (OFFICEID)
)

ALTER TABLE 
SALESPERSONINFORMATION1  
ADD CONSTRAINT PK1_EMP1_ID PRIMARY KEY (EMPLOYEEID)

ALTER TABLE 
SALESSTAFFCUSTOMER 
ADD CONSTRAINT PK_EMP1_ID PRIMARY KEY (EMPLOYEEID)
ALTER TABLE 
SALESSTAFFCUSTOMER  
DROP CONSTRAINT PK_EMP1_ID 


CREATE TABLE 
CUSTOMER1 (
CUSTOMERID INT NOT NULL ,
NAME VARCHAR (50),
CITY VARCHAR(50) ,
POPULATION INT ,
CONSTRAINT CUSTOMER1_ID_PK PRIMARY KEY (CUSTOMERID)
)


ALTER TABLE 
SALESSTAFFCUSTOMER 
ADD CONSTRAINT FK_EMP_ID FOREIGN KEY (EMPLOYEEID) REFERENCES SALESPERSONINFORMATION1 (EMPLOYEEID)


ALTER TABLE 
SALESSTAFFCUSTOMER 
ADD CONSTRAINT FK_CUS_ID FOREIGN KEY (CUSTOMERID) REFERENCES CUSTOMER1 (CUSTOMERID)

select * from 
TRAINING_NORMALISATION


SELECT * FROM 
SALESPERSONINFORMATION


SELECT * FROM 
CUSTOMER


select * from 
SALESSTAFFCUSTOMER


SELECT * FROM 
SALESSTAFFOFFICE


SELECT * FROM 
SALESPERSONINFORMATION1


SELECT * FROM 
CUSTOMER1


INSERT INTO 
SALESSTAFFOFFICE
VALUES 
('201','312551212','NOIDA'),
('202','41235551212','BANGLORE')


INSERT INTO 
SALESPERSONINFORMATION1 
VALUES 
('101','RAHUL KUMAR','201'),
('102','GUPTA KUMAR','202'),
('103','GUPTA RAHUL','201')


INSERT INTO 
CUSTOMER1
VALUES 
('501','TATA','DELHI','94000'),
('502','MHINDRA','MUBAI','50000'),
('503','HYUNDAI','GURGAON','60000'),
('504','MARUTI','THANE','70000'),
('505','KTM','PATNA','80000'),
('506','BAJAJ','RAXAUL','30000')


INSERT INTO 
SALESSTAFFCUSTOMER 
VALUES 
('501','101'),
('502','101'),
('503','102'),
('504','102'),
('505','102'),
('506','103')



-- 3RD NORMAL FORM
CREATE TABLE 
CITYDETAILS (
POSTALCODE INT NOT NULL ,
CITY VARCHAR(50) NOT NULL ,
POPULATION INT NOT NULL
) 


ALTER TABLE 
CITYDETAILS 
ADD CONSTRAINT CITY_PK PRIMARY KEY (POSTALCODE)


CREATE TABLE 
CUSTOMER2 (
CUSTOMERID INT NOT NULL , 
CUSTOMERNAME VARCHAR(50) NOT NULL ,
POSTALCODE INT NOT NULL
CONSTRAINT FK_POST FOREIGN KEY (POSTALCODE) REFERENCES CITYDETAILS (POSTALCODE)
)

CREATE TABLE 
SALESSTAFFCUSTOMER1 (
CUSTOMERID INT NOT NULL ,
EMPLOYEEID INT NOT NULL
)
CREATE TABLE 
SALESSTAFFOFFICE1 (
OFFICEID INT NOT NULL ,
OFFICEPHONENO BIGINT NOT NULL,
OFFICELOCATION VARCHAR (50) NOT NULL
)
CREATE TABLE 
SALESPERSONINFORMATION2 (
EMPLOYEEID INT NOT NULL ,
SalesPerson varchar(50) not null,
OFFICEID INT NOT NULL
)

ALTER TABLE 
CUSTOMER2 
ADD CONSTRAINT PK_CUST_ID PRIMARY KEY (CUSTOMERID)


ALTER TABLE 
SALESSTAFFOFFICE1 ADD CONSTRAINT PK_OFF_ID PRIMARY KEY (OFFICEID)


ALTER TABLE 
SALESPERSONINFORMATION2 ADD CONSTRAINT PK_EMP_ID PRIMARY KEY (EMPLOYEEID)


ALTER TABLE 
SALESSTAFFCUSTOMER1 
ADD CONSTRAINT FK3_EMP_ID FOREIGN KEY (EMPLOYEEID) REFERENCES SALESPERSONINFORMATION2 (EMPLOYEEID)


ALTER TABLE 
SALESSTAFFCUSTOMER1 
ADD CONSTRAINT FK_4CUS_ID FOREIGN KEY (CUSTOMERID) REFERENCES CUSTOMER2 (CUSTOMERID)


ALTER TABLE 
SALESPERSONINFORMATION2 
ADD CONSTRAINT FK5_EMP_ID FOREIGN KEY (OFFICEID) REFERENCES SALESSTAFFOFFICE1 (OFFICEID)


SELECT * FROM 
CITYDETAILS

INSERT INTO 
SALESSTAFFOFFICE1 
VALUES 
('201','312551212','NOIDA'),
('202','41235551212','BANGLORE')


INSERT INTO 
SALESPERSONINFORMATION2
VALUES 
('101','RAHUL KUMAR','201'),
('102','GUPTA KUMAR','202'),
('103','GUPTA RAHUL','201')


INSERT INTO 
CITYDETAILS 
VALUES 
('845433','DELHI','94000'),
('845434','DELHI','50000'),
('845435','GURGAON','60000'),
('845436','THANE','70000'),
('845437','PATNA','80000'),
('845438','RAXAUL','30000')

INSERT INTO 
CUSTOMER2 
VALUES 
('501','TATA','845433'),
('502','MHINDRA','845434'),
('503','HYUNDAI','845435'),
('504','MARUTI','845436'),
('505','KTM','845437'),
('506','BAJAJ','845438')


INSERT INTO 
SALESSTAFFCUSTOMER1 
VALUES 
('501','101'),
('502','101'),
('503','102'),
('504','102'),
('505','102'),
('506','103')



select * from TRAINING_NORMALISATION

SELECT * FROM SALESPERSONINFORMATION
SELECT * FROM CUSTOMER

select * from SALESSTAFFCUSTOMER
SELECT * FROM SALESSTAFFOFFICE
SELECT * FROM SALESPERSONINFORMATION1
SELECT * FROM CUSTOMER1

SELECT * FROM SALESPERSONINFORMATION2
SELECT * FROM SALESSTAFFOFFICE1
SELECT * FROM SALESSTAFFCUSTOMER1
SELECT * FROM CUSTOMER2
SELECT * FROM CITYDETAILS

-------------------------------------------------------------

-- This will containt employee salary ER diagram

CREATE TABLE
Employee (

Emp_no int not null,
Birth_date date not null,
First_name varchar (30),
Last_name varchar(20),
Gender varchar(10),
Hire_date date not null

)

CREATE TABLE 
Dept_emp (

Emp_no int not null,
Dept_no varchar(10) not null,
From_date date not null,
To_date date not null,

)

CREATE TABLE
Department (
Dept_no varchar(10) not null,
Dept_name varchar (30) not null,

)

CREATE TABLE 
Dept_manager (

Dept_no varchar(30) not null,
Emp_no int not null,
From_date date not null,
To_date date not null,

)

CREATE TABLE
Titles (
Emp_no int not null,
Title varchar(20) not null,
From_date date not null,
To_date date not null


)

CREATE TABLE
Salary (
Emp_no int not null,
Salary int not null,
From_date date not null,
To_date date not null,

)

ALTER TABLE
Department
ALTER COLUMN
Dept_no varchar(30) not null


ALTER TABLE
Dept_emp
ALTER COLUMN
Dept_no varchar(30) not null



ALTER TABLE
Employee
ADD CONSTRAINT Employee_PK primary key (Emp_no)

ALTER TABLE
Titles
ADD CONSTRAINT Titles_PK primary key (Title)

ALTER TABLE
Salary
ADD CONSTRAINT Salary_PK primary key (From_date)

ALTER TABLE
Department
ADD CONSTRAINT Department_PK primary key (Dept_no)

ALTER TABLE
Salary
ADD CONSTRAINT Emp_no_fK foreign key (Emp_no) REFERENCES Employee (Emp_no)

ALTER TABLE
Titles
ADD CONSTRAINT Emp_no1_fK foreign key (Emp_no) REFERENCES Employee (Emp_no)

ALTER TABLE
Dept_manager
ADD CONSTRAINT Emp_no2_fK foreign key (Emp_no) REFERENCES Employee (Emp_no)

ALTER TABLE
Dept_manager
ADD CONSTRAINT Dept_no_fK foreign key (Dept_no) REFERENCES Department (Dept_no)

ALTER TABLE
Dept_emp
ADD CONSTRAINT Dept_no1_fK foreign key (Dept_no) REFERENCES Department (Dept_no)


ALTER TABLE
Dept_emp
ADD CONSTRAINT Emp_no3_fK foreign key (Emp_no) REFERENCES Employee (Emp_no)





--------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------

SELECT *FROM
Employee.employees.employees

SELECT name+sur_name,gender as fullname 
FROM
Employee.employees.employees
where gender ='m'



SELECT name+sur_name,gender as fullname 
FROM
Employee.employees.employees
where gender ='f'



SELECT emp_no,name+sur_name as fullname, gender
FROM
Employee.employees.employees
where gender ='f'

-- this contain inner join 

SELECT
       name+sur_name as fullname,
	   gender,title,hire_date
FROM
       Employee.employees.employees
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no


	   -- this contains view
CREATE VIEW  fnae_gend_title_hiredate
 
 as
 SELECT
       name+sur_name as fullname,
	   gender,title,hire_date
FROM
       Employee.employees.employees
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no

	select * from fnae_gend_title_hiredate

	   -- this contain inner join and order by

	   
SELECT
       name+sur_name as fullname,
	   gender,title,hire_date
FROM
       Employee.employees.employees
	  
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
order by
       title
	   
-- this table will contain inner join and one column in right table


SELECT
       name+sur_name as fullname,
	   gender,title,hire_date,to_date
FROM
       Employee.employees.employees
	  
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
order by
       title



	   
-- this table contain view for upper table
CREATE VIEW name_gen_title_hire_todate

as

SELECT
       name+sur_name as fullname,
	   gender,title,hire_date,to_date
FROM
       Employee.employees.employees
	  
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no


	   select  * from name_gen_title_hire_todate


-- this contain join from three table 


SELECT
       name+sur_name as fullname,
	   gender,title,hire_date,to_date,salary -- doubt here
FROM
       Employee.employees.employees
	  
full join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
full join 
       Employee.employees.salaries
on     Employee.employees.employees.emp_no = Employee.employees.salaries.emp_no
order by
       title

-- this contain view of above table

CREATE VIEW NAME_GEND_HIREDATE_SALARY
AS
SELECT
       name+sur_name as fullname,
	   gender,title,hire_date,salary 
FROM
       Employee.employees.employees
	  
right join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
inner join 
       Employee.employees.salaries
on     Employee.employees.employees.emp_no = Employee.employees.salaries.emp_no

SELECT * FROM NAME_GEND_HIREDATE_SALARY

	   -- this will continue join from four table 
	   
SELECT
       name+sur_name as fullname,
	   gender,title,hire_date, salary * .1 as increment , dept_no
FROM
       Employee.employees.employees
	  
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
inner join 
       Employee.employees.salaries
on     Employee.employees.employees.emp_no = Employee.employees.salaries.emp_no
inner join
       Employee.employees.dept_manager
on
        Employee.employees.employees.emp_no = Employee.employees.dept_manager.emp_no
		
order by
       title

	   -- this will contain 5 table 
	   
SELECT
       name+sur_name as fullname,
	   gender,title,hire_date,salary,dept_no,sum(salary) as avgsalary ---- doubt want to take average after obtaining table in join
FROM
       Employee.employees.employees
	  
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
inner join 
       Employee.employees.salaries
on     Employee.employees.employees.emp_no = Employee.employees.salaries.emp_no
inner join
       Employee.employees.dept_manager
on
        Employee.employees.employees.emp_no = Employee.employees.dept_manager.emp_no
group by title,name,sur_name,gender,hire_date,dept_no,salary
order by
       title


	   -- this to calculate increment of employee
	  
SELECT top 1 percent
       name+sur_name as fullname,
	   gender,
	   hire_date,
	   to_date,
	   salary *.1 as  increment                       -- how to multiply in terms of percent
FROM
       Employee.employees.employees
        full join 
          Employee.employees.salaries
             on   
		       Employee.employees.employees.emp_no = Employee.employees.salaries.emp_no
where DATEDIFF(quarter,from_date,to_date)<7 and gender='f'

order by increment desc


--- CTE table 



WITH joining_cte(
        NAME,GENDER,JOININGYEAR,emp_no
        )
		as
		(
		SELECT NAME , GENDER , YEAR(HIRE_DATE) AS JOININGYEAR,emp_no
		FROM Employee.employees.employees
		where  gender ='f'
		)
		select name, GENDER as femaleemployee,joiningyear,emp_no as empid
		from joining_cte
		order by joiningyear
		
	  --- cte with join

	  WITH joining_cte(
        NAME,GENDER,JOININGYEAR,emp_no
        )
		as
		(
		SELECT NAME , GENDER , YEAR(HIRE_DATE) AS JOININGYEAR,emp_no
		FROM Employee.employees.employees
		where  gender ='f'
		)
		,
		salary_cte (
		emp_no,salary
		)
		as

		(
		select emp_no,salary 
		from Employee.employees.salaries
		where salary > 60000
		)
		select name, GENDER as femaleemployee,joiningyear,salary
		from Joining_cte
		 join salary_cte on salary_cte.emp_no = JOINING_CTE.EMP_NO
		 order by salary desc
      
	  -----------------------------------------------------------------------------
	  -----------------------------------------------------------------------------
	  -----------------------------------------------------------------------------

	  
-- we can find here hire employees in last two year

SELECT 
      emp_no,name+ sur_name as fullname , gender, hire_date 
        FROM
             Employee.employees.employees
WHERE 
      hire_date > (SELECT DATEADD(YEAR,-2,(SELECT MAX(hire_date) FROM Employee.employees.employees)) AS '-2 YEARS') 
ORDER BY hire_date

-------------------------------------------------------------------------------------------------------

SELECT  name+sur_name as name ,gender
FROM    Employee.employees.employees
WHERE   gender ='f' AND                                            -- THIS IS EXAMPLE OF SUBQERY WITH OPERATOR CAN'T HAVE MORE THAN 1 VALUES
                  EMP_NO =
                (SELECT emp_no 
				 FROM   Employee.employees.salaries
				 WHERE emp_no = '10001'
				 )

	------------------------------------------------------------------------------------
	
SELECT  name+sur_name as name ,gender
FROM    Employee.employees.employees
WHERE   gender ='f' AND                                            -- THIS IS EXAMPLE OF SUBQERY WITH OPERATOR CAN'T HAVE MORE THAN 1 VALUES
                  EMP_NO =
                (SELECT emp_no
				 FROM   Employee.employees.salaries
				 WHERE salary =60117
				 )



				 -- this contain outer query from one table and subquery from another table
				 
SELECT  name+sur_name as name ,gender
FROM    Employee.employees.employees
WHERE   gender ='m' AND                                            
                  EMP_NO =
                (SELECT emp_no
				 FROM   Employee.employees.dept_manager
				 WHERE dept_no ='D001' AND emp_no =110022
				 )

--        same above query with join
				 
SELECT  name+sur_name as name ,gender
FROM    Employee.employees.employees
join    Employee.employees.dept_manager
        on Employee.employees.employees.emp_no = Employee.employees.dept_manager.emp_no
		where dept_no ='d001' and from_date = '1985-01-01'


	--- this will solve the subquery 	and using select top
	

SELECT  name+sur_name as name ,gender
FROM    Employee.employees.employees
WHERE   gender ='m' AND                                           
                  EMP_NO =
                (SELECT top 1 emp_no 
				 FROM   Employee.employees.salaries
				 WHERE emp_no = '10001'
				 )


-- this query will solve previous problem using select top
				 

SELECT  name+sur_name as name ,gender
FROM    Employee.employees.employees
WHERE   gender in ('m','f') AND                                            
                  EMP_NO =
                (SELECT top 1 emp_no
				 FROM   Employee.employees.salaries
				 WHERE salary =60117
				 )




--- the same query can be solved with using 'in' type of subquery  ( this is very intresting query ) 


SELECT  name+sur_name as name ,gender
FROM    Employee.employees.employees
WHERE   EMP_NO in                                                                  -- THIS IS EXAMPLE OF SUBQERY  USING 'IN' TYPE OF SUBQUERY
                 (SELECT emp_no                                                  
				 FROM   Employee.employees.salaries
			     WHERE emp_no =10001
				 )


-- above subquery is solved using  in type of subquery


SELECT  name+sur_name as name ,gender,emp_no                         -- this query gives multiple values 
FROM    Employee.employees.employees
WHERE   EMP_NO in
                (SELECT emp_no 
				 FROM   Employee.employees.salaries
				 WHERE salary =60117
				 )

-- above subquery is solved using any type of subquery

SELECT  name+sur_name as name ,gender,emp_no                         -- this query gives multiple values 
FROM    Employee.employees.employees
WHERE   EMP_NO = ANY
                (SELECT emp_no 
				 FROM   Employee.employees.salaries
				 WHERE salary =60117
				 )







-- this subquery will contain multiple level of nesting


SELECT  name+sur_name as name ,gender,emp_no                         -- this query gives multiple values 
FROM    Employee.employees.employees
WHERE   EMP_NO in
                (SELECT emp_no 
				 FROM   Employee.employees.salaries
				 WHERE emp_no in
				                (select emp_no 
								 from Employee.employees.dept_manager 
                                 where dept_no in ('d001','d002')
								 )

		         )




-- this will contain query refering to same table

SELECT emp_no, DATEDIFF(month,from_date,to_date) as duration_as_months
FROM   Employee.employees.dept_manager
WHERE emp_no in
               (SELECT emp_no
			    FROM   Employee.employees.dept_manager
				where  dept_no in ('d001','d002','d003')
			   
			   )
				 

-- this will contain query correlated


SELECT  name,sur_name,gender,Employee.employees.dept_manager.emp_no
FROM    Employee.employees.employees
join    Employee.employees.dept_manager
            on 
			  Employee.employees.employees.emp_no = Employee.employees.dept_manager.emp_no
			   WHERE 71116 in 
			                 (
							 SELECT salary
							 from   Employee.employees.salaries
							 where Employee.employees.dept_manager.emp_no = Employee.employees.salaries.emp_no
							 
							 )



-------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------

--------------------- THIS CONTAIN CREATE PROCEDURE-----------------------
USE Employee
GO
CREATE  PROC WHAT_DB_IS_THIS
AS
SELECT DB_NAME() AS THISDB
EXEC   WHAT_DB_IS_THIS

------------------------------------------------------------------------------------


CREATE  PROC WHAT_DB_IS_THAT3 @ID INT
AS
SELECT DB_NAME(@ID) AS THARVDB
EXEC   WHAT_DB_IS_THAT3 4


------------------CREATING PROCEDURE WITH BASICS SYNTAX --------------------------------------------------

CREATE PROC guest.salary_proc

AS
SELECT   emp_no,salary FROM     Employee.employees.salaries ORDER BY salary
EXEC     guest.salary_proc



-------------------------CREATING PROCEDURE  WITH MULTIPLE RESULT IN ONE PROCEDURE--------------------------------------------

CREATE PROC      guest.PERCENTILEsalary_proc

AS


SELECT DISTINCT Employee.employees.titles.title,
                PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary)
				                       OVER (PARTITION BY Employee.employees.titles.title) as median_CONT_salary
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE  year(Employee.employees.salaries.from_date) 
                    IN ('2002','2003','2004')



SELECT DISTINCT  Employee.employees.titles.title,
                PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY salary)
				                       OVER (PARTITION BY Employee.employees.titles.title) as median_DISCsalary
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE   year(Employee.employees.salaries.from_date) 
                    IN ('2002','2003','2004')



EXEC   guest.PERCENTILEsalary_proc



--------------------------THIS PROCEDURE INCLUDES GIVING INPUT VALUE------------------------------------------------------



CREATE PROC      guest.PERCENTILEsalary2_proc  @INPUTTITLE VARCHAR(30)

AS


SELECT DISTINCT Employee.employees.titles.title,
                PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary)
				                       OVER (PARTITION BY Employee.employees.titles.title) as median_CONT_salary
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE           Employee.employees.titles.title
                    = @INPUTTITLE

EXEC           guest.PERCENTILEsalary2_proc N'assistant engineer'



----------------------------- THIS PROCEDURE INCLUDES GIVING VALUES WITH WILDCARDS----------------------------------------------------------





CREATE PROC      guest.PERCENTILEsalary3_proc  @INPUTTITLE VARCHAR(30) =N'___i%'

AS


SELECT DISTINCT Employee.employees.titles.title,
                PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary)
				                       OVER (PARTITION BY Employee.employees.titles.title) as median_CONT_salary
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE           Employee.employees.titles.title
                    LIKE  @INPUTTITLE

EXEC           guest.PERCENTILEsalary3_proc N'assistant engineer'


------------------------THIS CONTAIN PROCEDURE WITH RECOMPILE-----------------------------------------------


CREATE PROC  guest.PERCENTILEsalary4_proc_WITHOUT_RECOMPILE

AS

SELECT   Employee.employees.titles.title,
                PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary)
				                       OVER (PARTITION BY Employee.employees.titles.title) as median_CONT_salary
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE  year(Employee.employees.salaries.from_date) 
                                              IN ('2002','2003','2004')


EXEC   guest.PERCENTILEsalary4_proc_WITHOUT_RECOMPILE


------------------ THIS CONTAIN PROCEDURE WITH RECOMPILE -----------------------------------------------------



CREATE PROC  guest.PERCENTILEsalary5_proc_WITH_RECOMPILE

WITH  RECOMPILE

AS

SELECT   Employee.employees.titles.title,
                PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary)
				                       OVER (PARTITION BY Employee.employees.titles.title) as median_CONT_salary
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE  year(Employee.employees.salaries.from_date) 
                                              IN ('2002','2003','2004')


EXEC   guest.PERCENTILEsalary5_proc_WITH_RECOMPILE


-------------------------------THIS CONTAIN EXECUTE AS CLAUSE-------------------------------

CREATE PROC  guest.PERCENTILEsalary7_proc_WITH_EXECUTEAS

WITH EXECUTE AS 'sudhir'

AS


SELECT DISTINCT Employee.employees.titles.title,
                PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary)
				                       OVER (PARTITION BY Employee.employees.titles.title) as median_CONT_salary
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no        ---doubt case-----


WHERE  year(Employee.employees.salaries.from_date) 
                    IN ('2002','2003','2004')

EXEC   guest.PERCENTILEsalary7_proc_WITH_EXECUTEAS   

-----------------------------------------------------------------------------------------------------------------------------------

CREATE PROC  guest.PERCENTILEsalary8_proc_WITH_EXECUTEAS

WITH EXECUTE AS 'dbo'

AS


SELECT DISTINCT Employee.employees.titles.title,
                PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary)
				                       OVER (PARTITION BY Employee.employees.titles.title) as median_CONT_salary    
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON                                                                                 ----- doubt case------
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE  year(Employee.employees.salaries.from_date) 
                    IN ('2002','2003','2004')

EXEC   guest.PERCENTILEsalary8_proc_WITH_EXECUTEAS   


--------------------------this contain stored procedure using output-----------------------------



CREATE PROC      guest.PERCENTILEsalary9_proc  @INPUTTITLE VARCHAR(30), @median_salary float OUTPUT

AS


SELECT DISTINCT Employee.employees.titles.title,
                PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary)
				                       OVER (PARTITION BY Employee.employees.titles.title) as median_CONT_salary
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE           Employee.employees.titles.title
                    = @INPUTTITLE 
			
SET            @median_salary=   Employee.employees.titles.title
GO

DECLARE @median_salry float   ,@avgsalary float 


EXEC   guest.PERCENTILEsalary9_proc N'assistant engineer',@median_salary = @avgsalary OUTPUT







-----------------------------this contain encryotion-------------------------------

CREATE PROC guest.salary11_proc
WITH  ENCRYPTION 
AS
SELECT   emp_no,salary FROM     Employee.employees.salaries ORDER BY salary
EXEC     guest.salary11_proc





---------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------------

-----------------------------------------------------this contain Non clustered  index -------------------------------------------------------------------- 

CREATE INDEX Salaries_salary
ON           [employees].[salaries] (salary desc)





----------------------------------------------------this contain Non Clustred index with include clause ---------------------------------------------------------------------

CREATE INDEX Salaries_salary_1
ON           [employees].[salaries] (salary desc)
INCLUDE      (emp_no)




-----------------------------------------this contain Non Clustered with where clause and include----------------------------------------------------------------


CREATE INDEX Salaries_salary_2
ON           [employees].[salaries] (salary desc)
INCLUDE      (emp_no)
WHERE        from_date > '1996-01-01'    and to_date <= '2000-01-01' 




----------------------this contain Non Clustered with where clause and include additional column-------------------------------------------------------------


CREATE INDEX Salaries_salary
ON           [employees].[salaries] (from_date,salary desc)
WITH         (drop_existing = ON)



----------------------THIS CONTAIN UNIQUE NON CLUSTERED INDEX------------------------------------------------------------------------------


CREATE UNIQUE  INDEX employees_name
ON                   [employees].[employees] (emp_no)




--------------------------------------THIS CONTAIN UNIQUE NON CLUSTERED INDEX WITH IGNORE_DUP_KEY---------------------------------------------------------------

CREATE UNIQUE  INDEX employees_name1
ON                   [employees].[employees] (name)
WITH                 (IGNORE_DUP_KEY = ON)               -- if we use this syntax and then we will be able to insert duplicate value in our unique index--




--------------------------------------------THIS CONTAIN index on view -----------------------------------------------------------------

CREATE VIEW empl_sal_view
  WITH SCHEMABINDING
AS
SELECT      name+sur_name as full_name,birth_date,hire_date,salary*1.05 AS increment,emp.emp_no
FROM        [employees].[employees] as emp,[employees].[salaries] as sal
WHERE       emp.emp_no = sal.emp_no

DROP VIEW  empl_sal_view 

CREATE UNIQUE CLUSTERED INDEX idx_1
ON         empl_sal_view (emp_no)                                             -- THIS IS NOT EXECUTING BECAUSE DATAABSES IS HAVING DUPLICATE VALUES--



------------------------------------------- THIS CONTAIN COLUMNSTORE INDEX---------------------------------------------------------

CREATE NONCLUSTERED COLUMNSTORE INDEX colun_store_emp_depart

ON                                    [employees].[dept_manager]    ([dept_no] )              


---------------------------------------CREATE AN ORDERED CLUSTERED INDEX-------------------------------------------------------------


CREATE  NONCLUSTERED COLUMNSTORE INDEX colun_store_emp_depart1 ON [Employee].[employees].[dept_manager]  
ORDER     (emp_no,dept_no)


------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------



------------------ This will contain 'cume_dist function', it will not include range for over clause-------------------------


SELECT   name+sur_name AS Name,gender,Employee.employees.employees.emp_no,
         CUME_DIST () OVER (PARTITION BY gender ORDER BY salary) as cumeDIST
        
FROM     Employee.employees.employees
JOIN     Employee.employees.salaries
             ON 
			    Employee.employees.employees.emp_no= Employee.employees.salaries.emp_no
WHERE    Employee.employees.employees.emp_no in (10001,10010)
ORDER BY Employee.employees.employees.emp_no DESC

  

  ----------------------- This will contain 'first_name' function not using partition -----------------------------------------

  
SELECT   name+sur_name AS Name,gender,Employee.employees.employees.emp_no,
         FIRST_VALUE (Name) OVER ( ORDER BY salary asc ) as cheapest_employee
        
FROM     Employee.employees.employees
JOIN     Employee.employees.salaries
             ON 
			    Employee.employees.employees.emp_no= Employee.employees.salaries.emp_no
WHERE    Employee.employees.employees.emp_no in (10001,10010)
ORDER BY Employee.employees.employees.emp_no DESC


------------------------------ this will contain 'first_value' name with partition' -------------------------------------------------------------


SELECT   name+sur_name AS Name,gender,Employee.employees.employees.emp_no,Employee.employees.titles.title,Employee.employees.titles.from_date,
         FIRST_VALUE (Name) OVER ( PARTITION BY title
		                           ORDER BY from_date asc
								   ROWS UNBOUNDED PRECEDING
								 ) 
								 as oldest_employee
        
FROM     Employee.employees.employees
JOIN     Employee.employees.titles
             ON 
			    Employee.employees.employees.emp_no= Employee.employees.titles.emp_no
ORDER BY Employee.employees.titles.title,Employee.employees.titles.from_date


---------------------------------- This will contain 'LAST_VALUE' NAME WITH PARTITON --------------------------------------------------------------------



SELECT   name+sur_name AS Name,gender,Employee.employees.employees.emp_no,Employee.employees.titles.title,Employee.employees.titles.from_date,
         LAST_VALUE (Name) OVER ( PARTITION BY title
		                          ORDER BY from_date asc
								  ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING
								 ) 
								 AS  newest_employee
        
FROM     Employee.employees.employees
JOIN     Employee.employees.titles
             ON 
			    Employee.employees.employees.emp_no= Employee.employees.titles.emp_no
ORDER BY Employee.employees.titles.title,Employee.employees.titles.from_date

-------------------------------------------- THIS CONTAIN LAG WITHOUT PARTITION------------------------------------------------------


SELECT emp_no as currentemp_no,year(from_date) as joining_year ,
       LAG (emp_no,1,0) over (ORDER BY year(from_date)) AS previous_emp

FROM   Employee.employees.titles
WHERE  year(from_date) 
                    IN ('2002','2003','2004')

---------------------------------------- This contain 'LAG' with partiton  ----------------------------------------------------------------------------


SELECT emp_no as currentemp_no,year(from_date) as joining_year ,title,
       LAG (emp_no,1,0) over (PARTITION BY title ORDER BY year(from_date)) AS previous_emp

FROM   Employee.employees.titles
WHERE  year(from_date) 
                    IN ('2002','2003','2004')

ORDER BY title

--------------------------------- THIS CONTAIN LEAD WITHOUT PARTITION--------------------------------------------------------------


SELECT emp_no as currentemp_no,year(from_date) as joining_year ,
       LEAD (emp_no,1,0) over (ORDER BY year(from_date)) AS NEXT_emp

FROM   Employee.employees.titles
WHERE  year(from_date) 
                     IN ('2002','2003','2004')


 ------------------------------ This will contain using partition -------------------------------------------------

 
SELECT emp_no as currentemp_no,year(from_date) as joining_year ,title,
       LEAD (emp_no,1,0) over (PARTITION BY title ORDER BY year(from_date)) AS NEXT_emp

FROM   Employee.employees.titles
WHERE  year(from_date) 
                    IN ('2002','2003','2004')

ORDER BY title


------------------------------- THIS CONTAIN 'PERCENTILE_COUNT' FUNCTION -------------------------------------------

SELECT DISTINCT Employee.employees.titles.title,
                PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary)
				                       OVER (PARTITION BY Employee.employees.titles.title) as median_CONT_salary
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE  year(Employee.employees.salaries.from_date) 
                    IN ('2002','2003','2004')





------------------------- THIS CONTAIN 'PERCENTILE_DISC' FUNCTION  ---------------------------------

SELECT DISTINCT  Employee.employees.titles.title,
                PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY salary)
				                       OVER (PARTITION BY Employee.employees.titles.title) as median_DISCsalary
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE   year(Employee.employees.salaries.from_date) 
                    IN ('2002','2003','2004')




------------------- THIS CONTAIN 'PERCENT RANK' -----------------



SELECT   name+sur_name AS Name,gender,Employee.employees.employees.emp_no,
         PERCENT_RANK () OVER (PARTITION BY gender ORDER BY salary) as PERCENT_RANK
        
FROM     Employee.employees.employees
JOIN     Employee.employees.salaries
             ON 
			    Employee.employees.employees.emp_no= Employee.employees.salaries.emp_no
WHERE    Employee.employees.employees.emp_no in (10001,10010)
ORDER BY Employee.employees.employees.emp_no DESC

-----------------------------------------------------------------------------------------------------------------------------------------------------------------

----------------------------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------------------------------------


-- THIS CONTAIN RANKINGS--

-------------------------------- THIS CONTAIN 'DENSE_RANK'-------------------------------------------------

SELECT    Employee.employees.titles.title,Employee.employees.salaries.salary,
                DENSE_RANK() 
				          OVER (PARTITION BY Employee.employees.titles.title ORDER BY salary desc) as salary_dense_rank
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE    year(Employee.employees.salaries.from_date) 
                      IN ('2002','2003','2004') 

ORDER BY salary_dense_rank offset 28 rows fetch next 7 row only


-------------------------------- THIS CONTAIN 'NTILE' --------------------------------------------------------


SELECT  Employee.employees.titles.title,Employee.employees.salaries.salary,
                NTILE(1000) 
				          OVER (PARTITION BY Employee.employees.titles.title ORDER BY salary desc) as DECADE_TILE
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE   year(Employee.employees.salaries.from_date) 
                    IN ('2002','2003','2004')

ORDER BY DECADE_TILE ASC


--------------------------------- THIS CONTAIN 'RANK'-------------------------------------------------------------


SELECT   Employee.employees.titles.title,Employee.employees.salaries.salary,
                RANK() 
				          OVER (PARTITION BY Employee.employees.titles.title ORDER BY salary desc) as SALARY_RANK
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE    year(Employee.employees.salaries.from_date) 
                    IN ('2002','2003','2004')

ORDER BY SALARY_RANK ASC

--------------------------------- THIS CONTAIN 'ROW NUMBER' ------------------------------------------------------



SELECT  Employee.employees.titles.title,Employee.employees.salaries.salary,
                ROW_NUMBER() 
				          OVER (PARTITION BY Employee.employees.titles.title ORDER BY salary desc) as ROW_NUM
FROM            Employee.employees.titles
JOIN            Employee.employees.salaries
                     ON 
					   Employee.employees.titles.emp_no=Employee.employees.salaries.emp_no


WHERE    year(Employee.employees.salaries.from_date) 
                    IN ('2002','2003','2004')

ORDER BY ROW_NUM ASC

----------------------------------------------------------------------------------------------------------------------------------
SELECT   salary,
           DENSE_RANK()OVER ( ORDER BY salary desc) as HIGHESTSALARY

FROM      Employee.employees.salaries
ORDER BY  HIGHESTSALARY OFFSET 4 ROWS  FETCH NEXT 1 ROW ONLY



-----------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------



--Operations in a relational database act on a complete set of rows.
--like set of rows returned by a SELECT statement provided with conditions in the WHERE clause of the statement
--whatever is returned is known as result set
--online applications, cannot always work effectively with the entire result set as a unit. 
--These applications need a mechanism to work with one row or a small block of rows at a time.
--Cursors are an extension to result sets that provide that mechanism.
--cursors positions at specific rows of the result set.
--Retrievs one row or block of rows from the current position in the result set.

-- CLOSE CURSOR BUT WILL GIVE RESULT for existing statement
-- Removes a cursor reference means the data structures comprising the cursor are released by Microsoft SQL Server.
------------------------------------------- This contains cursor --------------------------------------

DECLARE emp_cur CURSOR
        FOR SELECT * FROM [employees].[employees]
OPEN emp_cur
FETCH NEXT FROM emp_cur

CLOSE      emp_cur
DEALLOCATE emp_cur
SELECT * FROM [employees].[employees]




------------------------------------------- This contain cursor and using cursor to fetch in varriable  -------------------------------------------
DECLARE emp_cur1 CURSOR
       FOR SELECT  name+sur_name as fullname,
	               gender,
				   title,
				   hire_date
       FROM       Employee.employees.employees
       inner join Employee.employees.titles
       on         Employee.employees.employees.emp_no = Employee.employees.titles.emp_no


OPEN emp_cur1
                                                                                -- this will fetch next row in our varriable----
DECLARE @fullname varchar(20),
        @gender   varchar(2),
		@title    varchar(20),
		@hiredate date

FETCH NEXT FROM emp_cur1
INTO  @fullname,@gender,@title ,@hiredate
PRINT @fullname  +'  '  + @gender  +'  ' +  @title  +'  ' +CAST (@hiredate AS varchar (30))




-----------------------------------------this while fetch rows in our varriable for condition--------------------------------------------

DECLARE emp_cur1 CURSOR
       FOR SELECT  name+sur_name as fullname,
	               gender,
				   title,
				   hire_date
       FROM       Employee.employees.employees
       inner join Employee.employees.titles
       on         Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
	   WHERE  DATEPART(year,hire_date) IN (1986,1987)
	   ORDER BY DATEPART(year,hire_date) 
OPEN emp_cur1
                                                                                
DECLARE @fullname varchar(20),
        @gender   varchar(2),
		@title    varchar(20),
		@hiredate date

FETCH NEXT FROM emp_cur1
INTO  @fullname,@gender,@title ,@hiredate
WHILE @@FETCH_STATUS =0
  BEGIN
      PRINT @fullname  +'  '  + @gender  +'  ' +  @title  +'  ' +CAST (@hiredate AS varchar (30))
	  FETCH NEXT FROM emp_cur1
      INTO  @fullname,
	        @gender,
			@title ,
			@hiredate


  END

CLOSE emp_cur1
DEALLOCATE emp_cur1

------------------------------------------------------ CURSOR CAN BE NESTED ALSO--------------------------------------------------------


DECLARE emp_cur2 CURSOR
       FOR SELECT  name+sur_name as fullname,
	               gender,
				   title,
				   hire_date
       FROM       Employee.employees.employees
       inner join Employee.employees.titles
       on         Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
	   WHERE  DATEPART(year,hire_date) IN (1986,1987)
	   ORDER BY DATEPART(year,hire_date) 
OPEN emp_cur2
                                                                                
DECLARE @fullname varchar(20),
        @gender   varchar(2),
		@title    varchar(20),
		@hiredate date,
		@departid varchar(10)

FETCH NEXT FROM emp_cur2
INTO  @fullname,@gender,@title ,@hiredate
WHILE @@FETCH_STATUS =0
  BEGIN
      PRINT @fullname  +'  '  + @gender  +'  ' +  @title  +'  ' +CAST (@hiredate AS varchar (30))

	  DECLARE dept_cursor CURSOR
	         FOR SELECT dept_name
			 FROM       Employee.employees.departments
			 WHERE      dept_name = @title

	 OPEN   dept_cursor
     FETCH NEXT FROM dept_cursor
	 INTO  @departid
	 WHILE @@FETCH_STATUS =0
	   BEGIN
	        PRINT @departid
			FETCH NEXT FROM dept_cursor
            INTO  @departid
       END

    CLOSE dept_cursor
    DEALLOCATE dept_cursor



FETCH NEXT FROM emp_cur2
INTO  @fullname,
	  @gender,
	  @title ,
	 @hiredate


END

CLOSE emp_cur2
DEALLOCATE emp_cur2


----------------------------------------------FETCH CURSOR WITH DIFFERENT FETCH OPTION---------------------------------------------------

DECLARE emp_cur3 SCROLL CURSOR
        FOR SELECT * FROM [employees].[employees]
OPEN emp_cur3
FETCH    NEXT           FROM emp_cur3
FETCH    FIRST          FROM emp_cur3
FETCH    LAST           FROM emp_cur3
FETCH    PRIOR          FROM emp_cur3
FETCH    ABSOLUTE 2     FROM emp_cur3
FETCH    RELATIVE  3    FROM emp_cur3
FETCH    RELATIVE  -3    FROM emp_cur3

SELECT * FROM [employees].[employees]
------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------



----------------------------------------------------- THIS CONTAIN USER DEFINED FUNCTION----------------------------------------------------------------


--------------------------------------------------------- THIS CONTAIN SCALAR FUNCTION------------------------------------------------------------------

CREATE FUNCTION employees.salary_inc(
                                     @form_date date,
									 @to_date   date,
									 @salary    int
                                    )

RETURNS FLOAT
AS
BEGIN 
IF             DATEDIFF(quarter,@form_date,@to_date ) < 7
               BEGIN 
                   RETURN @salary *1.10
				   END
RETURN  0
END

SELECT    [emp_no],employees.salary_inc(from_date,to_date,salary ) AS increment
FROM      [employees].[salaries]
ORDER BY  increment DESC 


------------------------ THIS CONTAIN SCALAR FUNCTION OF INCREMENT AND IT WILL PRINT 10 HIGHEST INCREMENT -------------------------------------------------


CREATE FUNCTION employees.salary_inc(
                                     @form_date date,
									 @to_date   date,
									 @salary    int
                                    )

RETURNS FLOAT
AS
BEGIN 
IF             DATEDIFF(quarter,@form_date,@to_date ) < 7
               BEGIN 
                   RETURN @salary *1.10
				   END
RETURN  0
END

SELECT    [emp_no],employees.salary_inc(from_date,to_date,salary ) AS increment
FROM      [employees].[salaries]
ORDER BY  increment DESC OFFSET 9 ROW FETCH NEXT 1 ROW ONLY


-------------------------------------------------- this contain table varribale in function -----------------------------------------------------


CREATE FUNCTION employees.salary_inc1(
                                     @form_date date,
									 @to_date   date,
									 @salary    int
                                    )

RETURNS @employee_increment TABLE (
                                   emp_no int,
								   increment float
                                  )
AS
BEGIN 
DECLARE        @emp_no int
IF             DATEDIFF(quarter,@form_date,@to_date ) < 7
               BEGIN 
                   INSERT INTO  @employee_increment values (@emp_no,@salary *1.10)
				   END
RETURN  
END

SELECT * FROM  employees.salary_inc1 ('2000-04-24','2001-08-29',45000)

 


 -------------------------------------------THIS CONTAIN FUNCTION RETURNIG TABLE------------------------------------

 CREATE FUNCTION employees.employe_detail(
                                     @birth_date date											
                                    )

RETURNS TABLE 
AS
RETURN  
      SELECT emp_no,name+sur_name as fullname,gender
	  FROM   [employees].[employees]
	  WHERE  DATEPART(year,birth_date) = DATEPART(year,@birth_date)



SELECT * FROM employees.employe_detail('1953-05-23')
SELECT * FROM[employees].[employees]


---------------------------------------------------THIS CONTAIN MODIFYING FUNCTION--------------------------------------------------------------


 ALTER FUNCTION employees.employe_detail(
                                         @birth_date date											
                                        )

RETURNS TABLE 
AS
RETURN  
      SELECT emp_no,name+sur_name as fullname,gender,birth_date
	  FROM   [employees].[employees]
	  WHERE  DATEPART(year,birth_date) = DATEPART(year,@birth_date)



SELECT * FROM employees.employe_detail('1953-05-23')
SELECT * FROM[employees].[employees]


-----------------------THIS ALSO CONTAIN TABLE VALUE FUNCTION WITH INNER JOIN--------------------------------------------


 ALTER FUNCTION employees.employe_detail1(
                                          @dept_no nchar(4)
                                          )
                                     

RETURNS TABLE 
AS
RETURN  
      SELECT DATEDIFF(quarter,S.from_date,S.to_date ) as duration,S.emp_no,salary * .1 as increment ,D.dept_no
      FROM      Employee.employees.salaries AS S
	  join      Employee.employees.dept_manager AS D
	  on        S.emp_no=D.emp_no
      WHERE DATEDIFF(quarter,S.from_date,D.to_date ) < 7 and @dept_no=D.dept_no


SELECT * FROM employees.employe_detail1('D001')

----------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------


---------------------------------------THIS CONTAIN DATABASE FUNCTION-----------------------------------------------

---------------------------------------THIS CONTAIN LOGICAL FUNCTION-------------------------------------------------------


---------------------------------------------------SIMPLE CHOOSE -----------------------------------------------------
SELECT CHOOSE (3,'A','B','C') AS RESULT


-----------------------------------------------------USING CHOOSE IN COLUMN ---------------------------------------


SELECT    [emp_no],name+sur_name,[hire_date],CHOOSE (month(hire_date),'winter','summer','spring','autmn') AS HIRED_QUARETR
FROM      [employees].[employees]
WHERE     YEAR(hire_date)>1990
ORDER BY  YEAR(hire_date) DESC


----------------------this contain greatest function--------------------------------------------

CREATE TABLE test (    
                  prod_id int IDENTITY(1,1),    
                  listprice smallmoney NULL 
                  )

INSERT INTO test VALUES (14.99), (49.99), (24.99)


DECLARE @PriceX smallmoney = 19.99  

SELECT greatest(listprice, 0, @PriceX) as Greatest_Price   ---------------this function is saying it is not a built in function name 
FROM test

---------------------------------iif -----------------------------------------------------

DECLARE @a int = 6 , @d int = 9;
SELECT result = IIF( @a > @d,'true','false')


-------------------LEAST----------------------------------------------------------------------




DECLARE @PriceX smallmoney = 19.99;

SELECT LEAST(listprice, 0, @PriceX) as least_Price    
FROM test;
GO

------------------------------------------approx count distinct--------------------------------

SELECT     APPROX_COUNT_DISTINCT(emp_no)as distinct_emp_no,salary 
FROM       Employee.employees.salaries
WHERE      emp_no in ( 10001,10010)
GROUP BY   salary



----------------------------------------------------------AVG---------------------------------------------------------------------------

SELECT AVG(salary) AS AVG_SALARY,emp_no FROM
Employee.employees.salaries
WHERE emp_no in ( 10001,10010)
group by emp_no

---------------------------------COUNT FUNCTION -----------------------------------------------------------------------


SELECT COUNT (DISTINCT 
title ) as no_title
FROM
Employee.employees.titles


-----------------------------------stddeviation---------------------------------------------------------------------


SELECT STDEV(salary) AS STD_SALARY,emp_no FROM
Employee.employees.salaries
WHERE emp_no in ( 10001,10010)
group by emp_no



------------------------------------------------------STDEVP------------------------------------------------------------------------


SELECT STDEVP(salary) AS STDP_SALARY,emp_no FROM
Employee.employees.salaries
WHERE emp_no in ( 10001,10010)
group by emp_no


--------------------------------------------------------VAR----------------------------------------------------------------------------


SELECT VAR(salary) AS VAR_SALARY,emp_no FROM
Employee.employees.salaries
WHERE emp_no in ( 10001,10010)
group by emp_no



------------------------------------------------------VARP-------------------------------------------------------------------------------


SELECT VARP(salary) AS VARP_SALARY,emp_no FROM
Employee.employees.salaries
WHERE emp_no in ( 10001,10010)
group by emp_no



----------------------------------------------THIS CONTAIND MATHEMATICAL FUNCTION-----------------------------------------------

-----------------------------------------------This contain abs----------------------------------------------------------------

SELECT ABS(-1.0) as abs1, ABS(0.0) as abs2, ABS(1.0) as abs3


------------------------------------------------this contain acos THIS GIVES ANGLE IN RADIAN-----------------------------------------------------

SET NOCOUNT OFF  
DECLARE @cos FLOAT  
SET @cos = -1.0  
SELECT  ACOS(@cos) as in_rad


----------------------------------------------this contains asin THIS GIVES ANGLE--------------------------------------------------

SET NOCOUNT OFF  
DECLARE @cos FLOAT  
SET @cos = -1.0  
SELECT  ASIN(@cos) as in_rad


----------------------------------------------THIS contains atan THIS GIVES ANGLE--------------------------------------------------


SET NOCOUNT OFF  
DECLARE @cos FLOAT  
SET @cos = -1.0  
SELECT  ATAN(@cos) as in_rad

------------------------------THIS 


------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------

SELECT *FROM
Employee.employees.employees

SELECT name+sur_name,gender as fullname 
FROM
Employee.employees.employees
where gender ='m'



SELECT name+sur_name,gender as fullname 
FROM
Employee.employees.employees
where gender ='f'



SELECT emp_no,name+sur_name as fullname, gender
FROM
Employee.employees.employees
where gender ='f'

-- this contain inner join 

SELECT
       name+sur_name as fullname,
	   gender,title,hire_date
FROM
       Employee.employees.employees
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no


	   -- this contains view
CREATE VIEW  fnae_gend_title_hiredate
 
 as
 SELECT
       name+sur_name as fullname,
	   gender,title,hire_date
FROM
       Employee.employees.employees
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no

	select * from fnae_gend_title_hiredate

	   -- this contain inner join and order by

	   
SELECT
       name+sur_name as fullname,
	   gender,title,hire_date
FROM
       Employee.employees.employees
	  
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
order by
       title
	   
-- this table will contain inner join and one column in right table


SELECT
       name+sur_name as fullname,
	   gender,title,hire_date,to_date
FROM
       Employee.employees.employees
	  
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
order by
       title



	   
-- this table contain view for upper table
CREATE VIEW name_gen_title_hire_todate

as

SELECT
       name+sur_name as fullname,
	   gender,title,hire_date,to_date
FROM
       Employee.employees.employees
	  
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no


	   select  * from name_gen_title_hire_todate


-- this contain join from three table 


SELECT
       name+sur_name as fullname,
	   gender,title,hire_date,Employee.employees.salaries.to_date,salary 
FROM
       Employee.employees.employees
	  
full join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
full join 
       Employee.employees.salaries
on     Employee.employees.employees.emp_no = Employee.employees.salaries.emp_no
order by
       title

-- this contain view of above table

CREATE VIEW NAME_GEND_HIREDATE_SALARY
AS
SELECT
       name+sur_name as fullname,
	   gender,title,hire_date,salary 
FROM
       Employee.employees.employees
	  
right join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
inner join 
       Employee.employees.salaries
on     Employee.employees.employees.emp_no = Employee.employees.salaries.emp_no

SELECT * FROM NAME_GEND_HIREDATE_SALARY

	   -- this will continue join from four table 
	   
SELECT
       name+sur_name as fullname,
	   gender,title,hire_date, salary * .1 as increment , dept_no
FROM
       Employee.employees.employees
	  
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
inner join 
       Employee.employees.salaries
on     Employee.employees.employees.emp_no = Employee.employees.salaries.emp_no
inner join
       Employee.employees.dept_manager
on
        Employee.employees.employees.emp_no = Employee.employees.dept_manager.emp_no
		
order by
       title

	   -- this will contain 5 table 
	   
SELECT
       name+sur_name as fullname,
	   gender,title,hire_date,salary,dept_no,sum(salary) as avgsalary ---- doubt want to take average after obtaining table in join
FROM
       Employee.employees.employees
	  
inner join   
       Employee.employees.titles
on     
       Employee.employees.employees.emp_no = Employee.employees.titles.emp_no
inner join 
       Employee.employees.salaries
on     Employee.employees.employees.emp_no = Employee.employees.salaries.emp_no
inner join
       Employee.employees.dept_manager
on
        Employee.employees.employees.emp_no = Employee.employees.dept_manager.emp_no
group by title,name,sur_name,gender,hire_date,dept_no,salary
order by
       title


	   -- this to calculate increment of employee
	  
SELECT top 1 percent
       name+sur_name as fullname,
	   gender,
	   hire_date,
	   to_date,
	   salary *.1 as  increment                       -- how to multiply in terms of percent
FROM
       Employee.employees.employees
        full join 
          Employee.employees.salaries
             on   
		       Employee.employees.employees.emp_no = Employee.employees.salaries.emp_no
where DATEDIFF(quarter,from_date,to_date)<7 and gender='f'

order by increment desc


--- CTE table 



WITH joining_cte(
        NAME,GENDER,JOININGYEAR,emp_no
        )
		as
		(
		SELECT NAME , GENDER , YEAR(HIRE_DATE) AS JOININGYEAR,emp_no
		FROM Employee.employees.employees
		where  gender ='f'
		)
		select name, GENDER as femaleemployee,joiningyear,emp_no as empid
		from joining_cte
		order by joiningyear
		
	  --- cte with join

	  WITH joining_cte(
        NAME,GENDER,JOININGYEAR,emp_no
        )
		as
		(
		SELECT NAME , GENDER , YEAR(HIRE_DATE) AS JOININGYEAR,emp_no
		FROM Employee.employees.employees
		where  gender ='f'
		)
		,
		salary_cte (
		emp_no,salary
		)
		as

		(
		select emp_no,salary 
		from Employee.employees.salaries
		where salary > 60000
		)
		select name, GENDER as femaleemployee,joiningyear,salary
		from Joining_cte
		 join salary_cte on salary_cte.emp_no = JOINING_CTE.EMP_NO
		 order by salary desc
      
------------------------------------------------------------------------------------------------------------------------------------------------------
-- this will contain all select command 
SELECT *FROM
Employee.employees.salaries


SELECT DISTINCT 
from_date
FROM
Employee.employees.salaries

SELECT 
emp_no, salary
FROM
Employee.employees.salaries


SELECT 
emp_no, salary
FROM
Employee.employees.salaries
WHERE emp_no = 10021

-- THIS CONTAIN IN OPERATOR

SELECT 
emp_no, salary
FROM
Employee.employees.salaries
WHERE emp_no IN ( 10021,10022,10025)

-- THIS CONTAIN BETWEEN OPERATOR

SELECT 
emp_no, salary
FROM
Employee.employees.salaries
WHERE emp_no BETWEEN 10021 AND 10029

-- THIS CONTAIN AND OPERATOR 
SELECT 
emp_no, salary
FROM
Employee.employees.salaries
WHERE emp_no IN  ( 10021,10022,10025) AND salary > 50000


-- THIS CONTAIN AVG 
SELECT 
emp_no, avg( salary) as avgsalary
FROM
Employee.employees.salaries
group by emp_no

--

SELECT 
emp_no, avg( salary) as avgsalary
FROM
Employee.employees.salaries
group by emp_no
having emp_no IN ( 10021,10022,10025)

-- MAX THIS CONTAIN MAX OPERATOR

SELECT 
emp_no, MAX( salary) as MAXsalary
FROM
Employee.employees.salaries
group by emp_no

--MAX THIS CONTAIN MAX OPERATOR

SELECT 
emp_no, MAX( salary) as MAXsalary
FROM
Employee.employees.salaries
group by emp_no
having emp_no IN ( 10021,10022,10025)

--MIN THIS CONTAIN MIN OPERATOR
SELECT 
emp_no, MIN( salary) as MAXsalary
FROM
Employee.employees.salaries
group by emp_no

-- MIN THIS CONTAIN MIN OPERATOR

SELECT 
emp_no, MIN( salary) as MINsalary
FROM
Employee.employees.salaries
group by emp_no
having emp_no IN ( 10021,10022,10025)

-- BETWEEN  AND MIN


SELECT 
emp_no, MIN( salary) as MINsalary
FROM
Employee.employees.salaries
group by emp_no
having emp_no  BETWEEN 10021 AND 10029

-- MAX AND BETWEEN

SELECT 
emp_no, MAX( salary) as MAXsalary
FROM
Employee.employees.salaries
group by emp_no
Having emp_no BETWEEN 10021 AND 10029

--MAX

SELECT 
emp_no, max( salary) as MAXsalary
FROM
Employee.employees.salaries
group by emp_no
having emp_no IN ( 10021,10022,10025) 

--MIN and where
SELECT 
emp_no, MIN( salary) as minsalary
FROM
Employee.employees.salaries
where emp_no = 10025
group by emp_no

-- max where
SELECT 
emp_no, Max( salary) as maxsalary
FROM
Employee.employees.salaries
where emp_no = 10025
group by emp_no

--uses of  null 

SELECT 
emp_no, salary as absurdsalary
FROM
Employee.employees.salaries
where emp_no is null

 
 -- 

SELECT * FROM
Employee.employees.salaries
order by emp_no


SELECT distinct emp_no,salary

FROM
Employee.employees.salaries
WHERE salary > 90000


SELECT TOP 20 PERCENT emp_no,salary
FROM
Employee.employees.salaries
WHERE SALARY < 40000


-- name will not start from rkghi
SELECT 
emp_no,NAME+sur_name as fullname
FROM
Employee.employees.employees
where name like '[^rkghi]%'
order by name



-- name will  start from rkghi
SELECT 
emp_no,NAME+sur_name as fullname
FROM
Employee.employees.employees
where name like '[rkghi]%'
order by name


-- name will start from from anysinglecharacter and then have r,r after that any character

SELECT 
emp_no,NAME+sur_name as fullname
FROM
Employee.employees.employees
where name like '_rr%'
order by name


-- it will have uses of date greater than this date

SELECT 
emp_no,name+ sur_name as fullname , gender, hire_date
FROM
Employee.employees.employees
WHERE hire_date >= '1987-07-02'




SELECT 
from_date-to_date as jobtime
FROM
Employee.employees.salaries


-- we can find this hire date between two dates


SELECT 
emp_no,name+ sur_name as fullname , gender, hire_date
FROM
Employee.employees.employees
WHERE hire_date between '1987-07-02' and '1989-03-14'


-- we can find here hire employees in last two year

SELECT 
      emp_no,name+ sur_name as fullname , gender, hire_date 
        FROM
             Employee.employees.employees
WHERE 
      hire_date > (SELECT DATEADD(YEAR,-2,(SELECT MAX(hire_date) FROM Employee.employees.employees)) AS '-2 YEARS') 
ORDER BY hire_date



-- we can find duration of employee in company 

select DATEDIFF(quarter,from_date,to_date ) as duration,emp_no,salary * .1 as increment from -- how to multiply by some% value in column 
   Employee.employees.salaries
        where DATEDIFF(quarter,from_date,to_date ) < 7

------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------------------------------


SELECT *FROM
Employee.employees.salaries
WHERE salary = 71166
order by emp_no desc



SELECT min(salary),emp_no FROM
Employee.employees.salaries
WHERE emp_no in ( 10001,10010)
group by emp_no


SELECT *FROM
Employee.employees.departments

SELECT *FROM
Employee.employees.dept_manager
WHERE emp_no = 10001



	SELECT *FROM
	Employee.employees.employees
	where emp_no =10008


-----------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------

CREATE TABLE BRAND(
                       brand_id INT IDENTITY PRIMARY KEY,
                       brand_name VARCHAR(255) NOT NULL
                       )
INSERT INTO BRAND VALUES 
                        ('JEAN'),
						('SHIRT'),
						('TSHIRT'),
						('SHORTS'),
						('TROUSER')

CREATE TABLE NEWBRAND(
                       brand_id INT IDENTITY PRIMARY KEY,
                       brand_name VARCHAR(255) NOT NULL
                      )


CREATE VIEW  MALL_INVENTORY
AS
SELECT
            brand_name,
           'Approved' approval_status
FROM        [dbo].[BRAND]
    
UNION
SELECT
            brand_name,
            'Pending Approval' approval_status
FROM
    [dbo].[NEWBRAND]
   
   




 CREATE TRIGGER     MALL_INVENTORY_TRG
ON                  MALL_INVENTORY
INSTEAD OF INSERT
AS
BEGIN
    SET NOCOUNT ON;
    INSERT INTO   NEWBRAND( 
                           brand_name
                           )
    SELECT
          i.brand_name
    FROM
          inserted i
    WHERE
          i.brand_name NOT IN (
                               SELECT  brand_name
                               FROM    BRAND
                               )        
END


INSERT INTO  MALL_INVENTORY (brand_name) VALUES 
                                 ('JACKET')

SELECT* FROM NEWBRAND

SELECT brand_name,approval_status FROM MALL_INVENTORY


SELECT* FROM BRAND

INSERT INTO BRAND VALUES 
                        ('JACKET')


CREATE TRIGGER MALL_UPDATE
ON             BRAND
AFTER INSERT
AS
BEGIN 
DELETE FROM   MALL_INVENTORY

SELECT      i.brand_name

FROM       inserted i
WHERE      i.brand_name IN ( 
                              SELECT  brand_name
                              FROM    BRAND)

END


-------------------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------------------


--------------------------------------------------------this contain DML TRIGGER--------------------------------------------------------------------------------------------------------


CREATE TRIGGER  emp_trig_1
ON              [Employee].[employees].[salaries]
FOR INSERT
AS 
BEGIN 
     SET NOCOUNT ON;
	 SELECT * FROM inserted

END


SELECT * FROM   [Employee].[employees].[salaries]

INSERT INTO      [Employee].[employees].[salaries] VALUES (10001,35500,'2000-01-02','2002-01-03')


---------------------------THIS CONTAIN DELETE TRIGGER------------------------



CREATE TRIGGER  emp_trig_2
ON              [Employee].[employees].[salaries]
FOR DELETE
AS 
BEGIN 
     SET NOCOUNT ON;
	 SELECT * FROM deleted

END

----------------------------this contain update----------------------

CREATE TRIGGER  reminder_update
ON              [Employee].[employees].[salaries]
FOR UPDATE
AS 
 
IF(UPDATE(emp_no))
BEGIN 
RAISEERROR (50009,16,10,'emp_no is unique cant change')

END;


SELECT * FROM   [Employee].[employees].[salaries]

INSERT INTO      [Employee].[employees].[salaries] VALUES (10001,35500,'2000-01-02','2002-01-03')


---------------------------------------------------THIS CONTAIN UPDATE IN ONE TABLE GET PRINTED IN ANOTHER TABLE-------------------------------------------------------------------------------------------------------------

CREATE TABLE SALARY_updated(
                            emp_no int not null primary key,
							new_salary int,
							changed_at datetime default current_timestamp,
							operations char (6) not null,
							check(operations ='ins' or operations ='del')
							
							)

alter table SALARY_updated drop constraint [PK__SALARY_u__129850FA85DB365E] 


CREATE TRIGGER  emp_upd_salary
ON              [Employee].[employees].[salaries]
FOR UPDATE
AS 
BEGIN 
     SET NOCOUNT ON;
	 INSERT INTO  [dbo].[SALARY_updated](
                                emp_no,
							    new_salary ,
							    changed_at,
							    operations
	                            )
     SELECT    
	           i.emp_no,
			   salary,
			   GETDATE(),
			   'ins'
	           
     FROM inserted as i
	 UNION ALL
	      SELECT    
	           d.emp_no,
			   salary,
			   GETDATE(),
			   'del'
	           
     FROM inserted as d
END

UPDATE [employees].[salaries]
SET salary= 1.05 * salary
where emp_no = 10001

select * from SALARY_updated

--------------------------------this contain alter trigger  -------------------------------------------------------------------




ALTER TRIGGER [employees]. [emp_upd_salary]
ON              [Employee].[employees].[salaries]
FOR UPDATE
AS 
BEGIN 
     SET NOCOUNT ON;
	 INSERT INTO  [dbo].[SALARY_updated](
                                emp_no,
							    new_salary ,
							    changed_at,
							    operations
	                            )
     SELECT    
	           i.emp_no,
			   salary,
			   GETDATE(),
			   'ins'
	           
     FROM inserted as i
	 
END


--------------------------------------------THIS CONTAIN INSERT TRIGGER TO PRINT IN ANOTHER TABLE----------------------


CREATE TABLE SALARY_INSERTED(
                            emp_no int not null primary key,
							new_salary int,
							changed_at datetime default current_timestamp,
							operations char (6) not null,
							check(operations ='ins' or operations ='del')
							
							)



CREATE TRIGGER  emp_INSERT_salary
ON              [Employee].[employees].[salaries]
FOR UPDATE
AS 
BEGIN 
     SET NOCOUNT ON;
	 INSERT INTO [dbo].[SALARY_INSERTED] (
                                emp_no,
							    new_salary ,
							    changed_at,
							    operations
	                            )
     SELECT    
	           i.emp_no,
			   salary,
			   GETDATE(),
			   'ins'
	           
     FROM inserted as i
	 
END



----------------------------THIS CONTAIN DELETE TRIGGER TO ANOTHER TABLE--------------



CREATE TABLE SALARY_DELETED(
                            emp_no int not null primary key,
							new_salary int,
							changed_at datetime default current_timestamp,
							operations char (6) not null,
							check(operations ='ins' or operations ='del')
							
							)



CREATE TRIGGER  emp_DELETED_salary
ON              [Employee].[employees].[salaries]
FOR UPDATE
AS 
BEGIN 
     SET NOCOUNT ON;
	 INSERT INTO [dbo].[SALARY_DELETED] (
                                emp_no,
							    new_salary ,
							    changed_at,
							    operations
	                            )
     SELECT    
	           d.emp_no,
			   salary,
			   GETDATE(),
			   'ins'
	           
     FROM deleted as d
	 
END




------------------------------HOW TO DROP TRIGGER-------------------------------

DROP TRIGGER emp_trig_1




-------------------------HOW TO DISABLE TRIGGER----------------------------------------------


DISABLE TRIGGER  emp_DELETED_salary ON [Employee].[employees].[salaries]



------------------------------ENABLE TRIGGER----------------------------------------------


ENABLE TRIGGER  emp_DELETED_salary ON [Employee].[employees].[salaries]


--------------------------------------------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------------------------------------------


--THIS WILL CONTAIN EVERYTHING RELATED SELECT COMMAND
CREATE TABLE 
TRAIN_SELECT (
ID INT NOT NULL,
NAME VARCHAR(30) ,
Email VARCHAR (30) ,
GenderId INT NOT NULL,
Age INT NOT NULL,
City VARCHAR(30),

)

INSERT INTO
TRAIN_SELECT
VALUES 
(1,'Rahul','r@r.com',1,21,'Bihar'),
(2,'Kumar','k@k.com',1,20,'Champaran'),
(3,'Gupta','g@g.com',2,23,'Motihari'),
(4,'John','j@j.com',1,29,'Bihar'),
(5,'Doe','d@d.com',2,25,'Patna'),
(6,'Marry','marrymarry.com',2,26,'Patna')



INSERT INTO
TRAIN_SELECT
VALUES 
(6,'Marry','marrymarry.com',2,26,'Patna')

SELECT * FROM 
TRAIN_SELECT


SELECT DISTINCT CITY
FROM 
TRAIN_SELECT


SELECT DISTINCT CITY, NAME,AGE
FROM 
TRAIN_SELECT


SELECT CITY ,NAME
FROM 
TRAIN_SELECT 
WHERE 
CITY ='BIHAR'

SELECT CITY ,NAME
FROM 
TRAIN_SELECT 
WHERE 
CITY <>'BIHAR'

SELECT CITY ,NAME,AGE
FROM 
TRAIN_SELECT 
WHERE 
AGE <= 22


SELECT CITY ,NAME,AGE,EMAIL
FROM 
TRAIN_SELECT 
WHERE 
CITY IN   ('BIHAR','CHAMPARAN') AND AGE > 25  


SELECT CITY ,NAME,AGE
FROM 
TRAIN_SELECT 
WHERE 
AGE  NOT IN (21,25,29,30)


SELECT CITY ,NAME,AGE
FROM 
TRAIN_SELECT 
WHERE 
AGE BETWEEN 21 AND 25



SELECT CITY ,NAME,AGE,EMAIL
FROM 
TRAIN_SELECT 
WHERE 
EMAIL NOT LIKE '%@%'




SELECT CITY ,NAME,AGE,EMAIL
FROM 
TRAIN_SELECT 
WHERE 
NAME   LIKE '[^RGDM]%'

SELECT * FROM 
TRAIN_SELECT



SELECT CITY ,NAME,AGE,EMAIL
FROM 
TRAIN_SELECT 
WHERE 
(CITY = 'BIHAR' OR CITY = 'CHAMPARAN') AND AGE > 25  



SELECT *FROM 
TRAIN_SELECT 
ORDER BY
AGE DESC ,
NAME AS


SELECT TOP 30 PERCENT CITY , NAME ,AGE
FROM 
TRAIN_SELECT 
ORDER BY AGE ASC

------------------------------------------------------------------------------------------------------------------------



CREATE TABLE 
Employeetbl (
Id int not null,
Name varchar(20),
City varchar(20),
Gender varchar(20),
Salary int not null

)

INSERT INTO 
Employeetbl
values 
(1,'rahul','patna','m',30000),
(2,'kumar','noida','f',35000),
(3,'gupta','patna','m',32000),
(4,'john','patna','m',28000),
(5,'malik','banglore','m',29000),
(6,'doe','noida','m',37000),
(7,'roy','patna','f',41000),
(8,'root','patna','m',19000),
(9,'ian','banglore','m',23000),
(10,'bell','patna','f',33000),
(11,'wasim','noida','f',40000)

SELECT * FROM 
Employeetbl


SELECT 
min (Salary)
FROM
Employeetbl

select 
max (salary)
from
Employeetbl


select 
avg (salary)
from
Employeetbl 


select
city,sum(salary) as totalsalary 
from
Employeetbl
group by
city
select 
gender,avg(salary) as avgsalary
from
Employeetbl
group by
gender

select
city,gender, sum(salary) as totalsalary
from
Employeetbl
group by city,gender
order by city asc

select
city,gender,
sum(salary) as totalsalary,
avg (salary) as avgsalary,
count (id) as  totalemployee
from
Employeetbl
group by city,gender
order by city

select
city,
gender,
sum(salary) as totalsalary,
avg(salary)as avgsalary,
count(id) as totalemployee
from
Employeetbl
group by 
city,
gender
having count(id) <> 1
order by city

---------------------------------------------------------------------------------------------------------------------------------------------------

CREATE TABLE 
Employeetbl1 (
Id int not null,
Name varchar(20),
City varchar(20),
Gender varchar(20),
Salary int not null,
departmentid int not null

)

CREATE TABLE 
Employeedpt (
Id int not null,
departmentName varchar(20) not null,
locatio varchar(20) not null,
departmenthead varchar(20) not null

)
alter table Employeedpt add constraint pk_id primary key (id)
alter table Employeetbl1 add constraint fk_deptid foreign key (departmentid) References Employeedpt(id)
alter table Employeetbl1 alter column departmentid int



INSERT INTO 
Employeedpt
values 
(1,'it','noida','nick'),
(2,'hr','delhi','joe'),
(3,'payroll','banglore','doe'),
(4,'otherdepartment','patna','luie')




INSERT INTO 
Employeetbl1
values 
(1,'rahul','patna','m',30000,1),
(2,'kumar','noida','f',35000,3),
(3,'gupta','patna','m',32000,3),
(4,'john','patna','m',28000,2),
(5,'malik','banglore','m',29000,4),
(6,'doe','noida','m',37000,1),
(7,'roy','patna','f',41000,1),
(8,'root','patna','m',19000,2),
(9,'ian','banglore','m',23000,3),
(10,'bell','patna','f',330002,3),
(11,'wasim','noida','f',40000,1)


INSERT INTO 
Employeetbl1(
id,
name,
city,
gender,
Salary
)
values
(12,'kch','noida','f',40000),
(13,'subway','patna','f',25000)


select * from Employeetbl1
select * from Employeedpt

select
name,
city,
gender,
salary,
departmentname
from
Employeetbl1
join
Employeedpt
on Employeetbl1.departmentid = Employeedpt.Id

select
name,
city,
gender,
salary,
departmentname
from
Employeetbl1
right join
Employeedpt
on Employeetbl1.departmentid = Employeedpt.Id


select
name,
city,
gender,
salary,
departmentname
from
Employeetbl1
full join
Employeedpt
on Employeetbl1.departmentid = Employeedpt.Id




select
name,
city,
gender,
salary,
departmentname
from
Employeetbl1
cross join
Employeedpt


select
name,
city,
gender,
salary,
departmentname
from
Employeetbl1
left join
Employeedpt
on Employeetbl1.departmentid = Employeedpt.Id
where
Employeetbl1.departmentid is null

-----------------------------------------------------------------------------------------------------------------------------------------------------------------

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO


ALTER TRIGGER  [employees].[emp_upd_salary]
ON              [Employee].[employees].[salaries]
FOR UPDATE
AS 
BEGIN 
     SET NOCOUNT ON;
	 INSERT INTO  [dbo].[SALARY_updated](
                                emp_no,
							    new_salary ,
							    changed_at,
							    operations
	                            )
     SELECT    
	           i.emp_no,
			   salary,
			   GETDATE(),
			   'ins'
	           
     FROM inserted as i
	 UNION ALL
	      SELECT    
	           d.emp_no,
			   salary,
			   GETDATE(),
			   'del'
	           
     FROM inserted as d
END





      




	  
