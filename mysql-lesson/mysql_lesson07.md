### mysql lesson05 （mysql 七种join理论）

 ![avatar](https://raw.githubusercontent.com/love179902483/mynote/master/mysql-lesson/photos/lesson_007_01.png) 

 ![avatar](https://raw.githubusercontent.com/love179902483/mynote/master/mysql-lesson/photos/lesson_007_02.png) 
1. ##### INNER JOIN
    ```
    SELECT <select_list> FROM Table A A INNER JOIN Table B ON A.Key = B.key
    ```
   
2. ##### LEFT JOIN 
    ```
     SELECT <select_list> FROM Table A A LEFT JOIN TABLE B B ON A.Key = B.key
    ```
3. ##### LEFT_JOIN
    ```
    SELECT <select_list> FROM Table A A LEFT JOIN TABLE B ON A.Key = B.Key WHERE B.Key IS NULL
    ```
4. ##### RIGHT_JOIN
   ```
    SELECT <select_list> FROM Table A A RIGHT JOIN TABLE B B ON A.Key = B.Key
   ```

5. ##### RIGHT_JOIN
   
   ```
   SELECT <select_list> FROM TABLE A A RIGHT JOIN TABLE B ON A.Key = B.Key WHERE A.Key IS NULL
   ```

6. ##### OUTER_JOIN (mysql没有outer join)
   ```
    SELECT <select_list> FROM TABLE A A FULL OUTER JOIN TABLE B ON A.Key = B.Key
   ```
7. ##### OUTER_JOIN (mysql没有outer join)
   ```
    SELECT <select_list> FROM TABLE A A FULL OUTER JOIN TABLE B ON A.Key = B.Key WHERE A.Key IS NULL OR B.Key IS NULL
   ```
