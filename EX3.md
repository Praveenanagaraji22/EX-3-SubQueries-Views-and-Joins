# EX 3 SubQueries, Views and Joins 


## Create employee Table
```sql
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,
SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert the values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```
### Employee Table:
![1](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/87b33435-50ec-4082-87f0-1a1d6fb13710)

## Create department table
```sql
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
## Insert the values in the department table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```
### Department Table:
![2](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/41c5b033-6187-4ae9-8813-d37abecfda85)

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.

### QUERY:
```
SELECT ENAME FROM EMP WHERE SAL >(select SAL from EMP where EMPNO=7566);
```
### OUTPUT:
![3](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/0c92f041-407b-4cb1-836d-cb0c88b38cca)

### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
```
select ENAME,JOB,SAL from EMP where SAL =(select MIN(SAL) from EMP);
```
### OUTPUT:
![4](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/d0e402ea-3023-444a-a40e-21f695c610d6)

### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
```
select ENAME,JOB from EMP where  DEPTNO=10 AND JOB='SALESMAN';
```
### OUTPUT:
![5](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/7ce53d4d-cccf-4b36-af8c-a9443d1f055d)

### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
```
create view empv5 as select EMPNO,ENAME,JOB from EMP where DEPTNO=10;
```
### OUTPUT:
![6](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/d33dec60-d786-44bb-947b-0b8395b1a28e)

### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
```
create view empv30 AS select EMPNO,ENAME,SAL from EMP where DEPTNO=30;
```
### OUTPUT:
![8](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/2e1c84ac-60e1-461a-af14-276e66bdfcef)

### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
```
update EMP set SALARY=SALARY*1.1 WHERE JOB='clerk';
create view empv5 as select EMPNO,ENAME,SALARY,JOB from EMP;
```
### OUTPUT:
![9](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/433d8732-f630-4e49-b071-3bbe10490162)

## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id)
VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id)
VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id)
VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id)
VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id)
VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id)
VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id)
VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id)
VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
### Customer Table:
![10](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/10573fd4-8d1c-461e-b5a3-ed83a4df8cd2)

## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
### Salesman Table:
![11](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/7ef9931a-885c-41d8-856c-216f4d61000a)

### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
```
select s.name,c.cust_name,s.city from salesman1 as s ,customer1 as c where s.city=c.city;
```
### OUTPUT:
![12](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/a35300d2-04ed-4510-8610-3765f4795164)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.

### QUERY:
```
select s.name,c.cust_name,c.city,s.commission from salesman1 as s inner join customer1 as c on
 s.city=c.city where s.commission>0.13;
```
### OUTPUT:
![13](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/12253c4d-f176-4c3f-bf79-fe1480763153)

### Q9) Perform Natural join on both tables

### QUERY:
```
select s.name,c.cust_name,c.city,s.commission from salesman1 as s natural join customer1 as c where s.commission>0.13;
```
### OUTPUT:
![14](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/34b2ba2a-20de-46a2-9bac-bd2047a629cb)

### Q10) Perform Left and right join on both tables

### QUERY:
```
select s.name,c.cust_name,c.city,s.commission from salesman1 as s left join customer1 as c on
s.salesman_id=c.salesman_id where s.commission>0.13;
select s.name,c.cust_name,c.city,s.commission from salesman1 as s right join customer1 as c on
s.salesman_id=c.salesman_id where s.commission>0.13;
```
### OUTPUT:
![15](https://github.com/Divya110205/EX-3-SubQueries-Views-and-Joins/assets/119404855/d2ef9a9a-db36-48b5-88f3-83ab2e007c6c)

### RESULT:
Hence successfully created a manager database and execute DML queries using SQL.
