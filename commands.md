## **Добавление кортежей**

Добавление одного кортежа
``` SQL
INSERT INTO table_name (field_1, ..., field_n)  
    VALUE (value_1, ..., value_n);
```
Добавление нескольких кортежей
``` SQL
INSERT INTO table_name (field_1, ..., field_n)  
    VALUES (row1_value_1, ..., row1_value_n),  
     ...,   
     (row_x_value_1, ..., row_x_value_n);  
```
___
## **Выборка данных**
**Выборка всех данных из таблицы**
``` SQL
SELECT * FROM table_name;
```
___
**Выборка атрибутов из таблицы**
``` SQL
SELECT attribute_1, 
    ..., 
    attribute_n 
FROM table_name;
```
___
**Выборка атрибута с присвоением нового имени атрибуту в выборке**
``` SQL
SELECT attribute AS new_attribute_name 
FROM table_name;
```
___
**Выборка данных с созданием вычисляемого столбца**
``` SQL
SELECT attribute_1, attribute_2, 
     attribute_1_value 
     [*/+-] attribute_2_value 
     AS result_attribute_name 
FROM table_name;
```
___
**Выборка данных с логическими функциями**
``` SQL
SELECT attribute_1, attribute_2, 
    IF([condition_1], [if_1 = true], [else_1 = false]) AS sale
FROM book;
```
Legend:
```
- [condition_1] : attribute_x [bool check]
- [if_1 = true] : attribute_y [function?]
- [else_1 = false] : attribute_y [function?]
```
___
**Выборка данных по условию**
``` SQL
SELECT attribure 
FROM table_name
WHERE [condition_1];
```
Legend:
```
- [condition_1] : attribute_x [function?]
```
___
**Выборка данных из интервала, включающего границы**
``` SQL
SELECT attribute 
FROM table_name
WHERE [condition_1] BETWEEN [start_range] AND [finish_range];
```
Legend:
```
- [condition_1] : attribute_x [function?]
```
___
**Выборка данных соответствующим значениям из списка**
``` SQL
SELECT attribute 
FROM table_name
WHERE attribute IN (check_1, ..., check_n);
```
___
**Выборка данных с сортировкой**
``` SQL
SELECT attribute
FROM table_name
ORDER BY attribute_x DESC;
```
ORDER BY:  
- `ASC` - По возрастанию
- `DESC` - По убыванию
___
**Выборка данных LIKE**
``` SQL
SELECT attribute_x 
FROM table_name
WHERE attribute_x LIKE [condition];
```
``` SQL
SELECT attribute FROM table_name 
WHERE attribute NOT LIKE [condition];
```
Legend:  
- [condition] : Some pattern ("% %", "_%", ..., "_")  
___
**Выборка уникальных данных**
``` SQL
SELECT DISTINCT attribute_x
FROM table_name;
```
`DISTINCT` или с помощью `GROUP BY`
``` SQL
SELECT  attribute_x
FROM table_name
GROUP BY attrribute_x;
```
