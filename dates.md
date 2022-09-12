## Тип DATE – позволяет описать дату в формате ГГГГ-ММ-ДД
___
## **DATEDIFF**
``` SQL
/* разница между двумя датами, включая обе даты */
SELECT DATEDIFF(date_last, date_first)+1 AS "atrribute_name" 
FROM table_name;
```
___
## **MONTH**
``` SQL
MONTH('2020-04-12') = 4 /* вывести месяц */
```
``` SQL
/* выбрать месяц из аттрибутов */
SELECT MONTH(attribute_date)
FROM table_name;
```
___
## **MONTHNAME**
``` SQL
MONTHNAME('2020-04-12')='April' /* вывести название месяца */
```
``` SQL
SELECT MONTHNAME(attribute_date)
FROM table_name;
```