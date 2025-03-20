# shujukuzuoye02
### 题目一

要在数据库中添加一个关系模式为 `users(name, pswd, gender)` 的表，并使用 `name` 作为主码，可以使用以下 `CREATE TABLE` 命令：

CREATE TABLE users (  
name          varchar(16)   primary key,  
pswd           varchar(16),  
gender        char(1)  
);

注释：
- `gender` 使用 `char(1)` 表示单个字符（如 'M' 或 'F'）。


### 题目二

1. **找到在计算机学院开设的不少于3个学分的课程，并按学分进行升序排序。**

SELECT title, credits
FROM course
WHERE dept_name = '计算机学院' AND credits >= 3
ORDER BY credits ASC;


2. **找到所有被名叫图灵的老师教过的学生的学号（ID），并确保结果没有重复。**

SELECT DISTINCT takes.ID
FROM takes, teaches, instructor
WHERE takes.course_id = teaches.course_id
AND teaches.ID = instructor.ID
AND instructor.name = '图灵';


### 题目三

考虑题目二提到的关系模式，题目三的查询使用了自连接（`instructor AS T` 和 `instructor AS S`），即将 `instructor` 表与自身进行连接。
通过`WHERE T.salary > S.salary` 表示筛选出那些工资高于 `S` 表中记录的教师。
而 `S.dept_name = '会计'` 表示 `S` 表中的教师来自“会计”系。
因此，查询返回的是那些工资高于“会计”系中任何教师的教师姓名，并且结果中没有重复。

回答：该查询返回的是工资高于“会计”系中任何教师的所有教师的姓名，且结果中没有重复。
