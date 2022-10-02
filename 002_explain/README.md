# MYSQL 실행 계획 

```mysql
EXPLAIN SELECT *
          FROM employees e 
         INNER JOIN salaries s ON s.emp_no = e.emp_no
```

> [MySQL 실행계획](https://jeong-pro.tistory.com/243)