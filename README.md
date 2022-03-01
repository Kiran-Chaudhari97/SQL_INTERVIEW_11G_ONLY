# SQL_INTERVIEW_11G_ONLY

Find the nth highest salary using in oracle 11g using
-Self Join.
```
Select * from Employee a 
    Where 3 = (
                 Select Count (distinct Salary) from Employee 
                  where a.salary<=b.salary;
 ```
- Rownum.    
```
Select * from 
     (
       Select Sal,rownum r
       from (
             Select Distinct sal
             from emp
             order by sal
            )
     )
where r = 3;

       SAL          R
---------- ----------
      1250          3
```
- Analytical Function.
```
Select * from 
(
  Select empno,ename,sal,
  DENSE_RANK() Over(Order by sal desc) R
  from emp
  )
  where R =3;
  
  
    EMPNO ENAME                                                     SAL          R
---------- -------------------------------------------------- ---------- ----------
      7566 JONES                                                    2975          3


```
- Sub-Query.
- FETCH ROW statement.
