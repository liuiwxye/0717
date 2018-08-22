<center><h2><b><font color=green>SQL必知必会第4版</font></b></h2></center>

# 
&nbsp; [![SQL][sql-img]][sql] 

[sql]:https://www.mysql.com
[sql-img]:https://img.shields.io/badge/MySQL-git-orange.svg
<font size=3 color=ffff41>


<p>
<center>

![MySQL](https://labs.mysql.com/common/logos/mysql-logo.svg?v2 "MySQL")

</center>
</p>

* SHOW  显示/查看数据库
    ```SQL
    SHOW DATABASES;
    ```

* CREATE 创建数据库
    ```SQL
    CREATE DATABASE dbname;
    ```
* DROP 删除数据库
    ```SQL
    DROP DATABASE dbname;
    ```
* USE 使用数据库
    ```SQL
    USE dbname;
    ```

* SELECT 选择

    ```SQL
    /*默认升序ASC*/
    SELECT column_name FROM table_name;
    SELECT DISTINCT column_name FROM table_name;/*返回不同值*/
    SELECT column_name FROM table_name LIMIT 5;
    SELECT column_name FROM table_name LIMIT 5 OFFSET 3;
    SELECT column_name FROM table_name LIMIT 5,3;
    ```

* ORDER BY 排序
    ```SQL
    SELECT column1_name column2_name column3_name
    FROM table_name
    ORDER BY column2_name

    ```
  
* DESC 选择降序
  ```SQL
    SELECT column_name FROM table_name DESC;
    /*DESC仅应用到直接位于其前面的列名*/
    SELECT column1_name column2_name
    FROM table_name
    ORDER BY column1_name column2_name DESC;
    /*仅仅对column2_name列降序，其他列默认升序*/
    ```

* WHERE 过滤选择
    * BETWEEN *** AND ***
    * IS NULL
    ```SQL
    /*通过过滤选择不包含指定值的所有行时，你可能希望返回含NULL值的行。但是这做不到。因为未知（unknown）有特殊的含义，数据库不知道它们是否匹配，所以在进行匹配过滤或非匹配过滤时，不会返回这些结果。*/
    SELECT column1_name FROM table_name WHERE column2_name<>2 ORDER BY column1_name;
    ```

* AND OR 且 或
    
    ```SQL
    AND 运算优先级比 OR 高
    SELECT column1_name FROM tablename WHERE column1_name>1 AND column2_name <10 OR column3_name="liu"
    ```

* IN 包含
    ```SQL
    /*WHERE子句中用来指定要匹配值的清单的关键字，功能与OR相当*/
    SELECT column1_name FROM tablename WHERE column2_name IN("key1","key2",...,"keyn") ORDER BY column3_name;
    /*括号里面全部都有，也就类似于OR*/
    ```
* NOT 否定
    ```SQL
    SELECT column1_name FROM tablename WHERE NOT column2_name="key";
    ```

* 通配符 LIKE 操作符
    * % 百分号
    
        ```SQL
        /*检索LIU开头的任意字符*/
        SELECT column1_name FROM tablename WHERE column2_name LIKE "LIU%"
        
        /*检索含有LIU的任意字符*/
        SELECT column1_name FROM tablename WHERE column2_name LIKE "%LIU%"

        /*根据邮件地址的一部分来查找电子邮件,把通配符放在搜索模式中间是很有用的，例如:*/
        WHERE email LIKEb%@liu.com。

        /*包括Access在内的许多DBMS都用空格来填补字段的内容。例如，如果某列有50个字符，而存储的文本为Fish bean bag toy(17个字符),则为填满该列需要在文本后附加33个空格。这样做一般对数据及其使用没有影响，但是可能对上述SQL语句有负面影响。子句 WHERE prod_name LIKE 'F%y'只匹配以F开头、以y结尾的prod_name。如果值后面跟空格，则不是以y结尾，所以Fish bean bag toy就不会检索出来。简单的解决办法是给搜索模式再增加一个%号：'F%y%'还匹配y之后的字符（或空格）。*/
        ```
    * _ 下划线
        ```SQL
        /*下划线的用途与%一样，但它只匹配单个字符，而不是多个字符。*/

        /*检索第二三个为IU的key*/
        SELECT column1_name,column2_name FROM tablename WHERE column1_name LIKE "_IU%";

        ```
    * [] 方括号
        ```SQL


        ```
</font>
