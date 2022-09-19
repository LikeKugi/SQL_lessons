## **Создание таблицы**
```SQL
CREATE TABLE table_name(
    /* exmple of primaty key */
    attribute_id INT PRIMARY KEY AUTO_INCREMENT, 
    /* attributes with theirs types */
    attribute_x [ATTRIBUTE TYPE]
);
```
___
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
## **Добавление данных из другой таблицы**
``` SQL
INSERT INTO table_point (attribute_1, ..., attribute_n) 
SELECT attribute_1, ..., attribute_n 
FROM table_from;
```
Или всех полей
``` SQL
INSERT INTO table_point (attribute_1, ..., attribute_n)
SELECT * FROM table_from;
```
___
## **Добавление уникальных кортежей**
``` SQL
INSERT INTO table_point (attribute_1, ..., attribute_n) 
SELECT attribute_1, ..., attribute_n 
FROM table_from
WHERE attribute_x NOT IN (
        SELECT attribute_x /*соответствующий атрибут*/ 
        FROM table_point
      );
```
___
## **Запросы на обновление полей**
``` SQL
UPDATE table_name 
SET attribute = [smth new]; /* какое-то выражение */
```
## **Запросы на обновление нескольких столбцов**
``` SQL
UPDATE table_name 
SET attribute_1 = [condition_1],
    ...,
    attribute_n = [condition_n]
```
___
## **Запросы на обновление нескольких таблиц**
``` SQL
UPDATE table_1, table_2 
SET table_1.attribute_1 = table_1.attribute_1 + table_2.attribute_1
/* WHERE - Обязательно! */
/* условие, при котором обновляются данные */
WHERE book.attribute_x = table_2.attribute_x 
    AND book.attribute_y = table_2.attribute_y;
```
___
## **Запросы на удаление**  
Удаление всех записей
``` SQL
DELETE FROM table_name;
```
Удаление с условием
``` SQL
DELETE FROM table_name
WHERE [condition];
```
Удаление кортежей с выборкой из другой таблицы
``` SQL
DELETE FROM table_name_1 
WHERE attribute_x IN (
        SELECT attribute_y 
        FROM table_name_2
      );
```
___
## **Создание новой таблицы на основе старой**
``` SQL
CREATE TABLE table_new AS
SELECT attribute_1, ..., attribute_n
FROM table_old
WHERE [condition];
```
___
## **Создание новой таблицы с внешним ключом**
``` SQL
CREATE TABLE table_name (
    attribute_id INT PRIMARY KEY AUTO_INCREMENT,  /* первичный ключ */
    attribute_x VARCHAR(50), 
    foreign_id INT NOT NULL, 
    attribute_y DECIMAL(8,2), 
    attribute_ INT, 
    /* объявление внешнего ключа */
    /* может быть несколько внешних ключей. 
    они объявляются так же через запятую */
    FOREIGN KEY (foreign_id)  REFERENCES table_from (primary_id) /* !!!названия foreign_id = primary_id */ 
);
```
___
## **ON DELETE для внешнего ключа**
``` SQL
FOREIGN KEY (first_id)  REFERENCES table_ref_x (first_id) ON DELETE CASCADE,
/* second_id не дожен быть NOT NULL */
FOREIGN KEY (second_id)  REFERENCES table_ref_y (second_id) ON DELETE SET NULL,
FOREIGN KEY (third_id)  REFERENCES table_ref_z (third_id) ON DELETE SET DEFAULT,
FOREIGN KEY (fourth_id)  REFERENCES table_ref_xy (fourth_id) ON DELETE RESTRICT
```