`WHERE` и `HAVING` могут использоваться в одном запросе. При этом необходимо учитывать порядок выполнения  SQL запроса на выборку на **СЕРВЕРЕ**:

1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY


Отсюда следует, что `WHERE` **ВСЕГДА** выполняется **ДО** группировки, а `HAVING` **ПОСЛЕ**.  `WHERE` читает все строки **ПЕРВОНАЧАЛЬНОЙ** таблицы, в то время как **HAVING** читает строки уже **СГРУППИРОВАННОЙ** таблицы (вернее, не таблицы, а результата группировки **ПЕРВОНАЧАЛЬНОЙ** таблицы).


**Выборка данных и групповое суммирование**  
просуммировать количество  
``` SQL
SELECT attribute, SUM(attribute_x)
FROM table_name
GROUP BY attribute_y;
```
посчитать количество кортежей
``` SQL
SELECT attribute_x, COUNT(attribute_y), COUNT(*)
FROM table_name
GROUP BY attribute_z;
```
- `COUNT(*)` : подсчитывает  все записи, относящиеся к группе, в том числе и со значением `NULL`
- `COUNT(attribute)` — возвращает количество записей конкретного столбца (только `NOT NULL`), относящихся к группе.
___
**Групповые функции MIN() MAX() AVG()**
``` SQL
SELECT attribute_x, 
        MIN(attribute_min) AS min_name,
        MAX(attribute_max) AS max_name,
        AVG(attribute_avg) AS avg_name
FROM table_name
GROUP BY attribute_z;
```
___
**Выборка данных по условию - Групповые функции**
``` SQL
SELECT attribute_x,
FROM table_name
GROUP BY attribute_y
HAVING [condition]; 
```
___
**Ограничение выборки**
``` SQL
SELECT *
FROM table_name
ORDER BY  attribute_x
LIMIT 1; /* выведется первый кортеж */
```