**LIKE samples**

| символ | описание |
|:----:|------|
| `%` | Любая строка, содержащая ноль или более символов |
| `_` | Любой одиночный символ |
___
**ANY samples**

| command | meaning |
|:----:|------|
| `attribute_x > ANY (10, 12)` | `attribute_x` > 10 |
| `attribute_x < ANY (10, 12)` | `attribute_x` < 12 |
| `attribute_x = ANY (10, 12)` | (`attribute_x` = 10) OR (`attribute_x` = 12) |
|| `attribute_x` IN  (10,12) |
| `attribute_x <> ANY (10, 12)` | вернет все записи с любым значением `attribute_x` |
___
**ALL samples**

| command | meaning |
|:----:|------|
| `attrinute_x > ALL (10, 12)` | `attrinute_x` > 12 |
| `attrinute_x < ALL (10, 12)` | `attrinute_x` < 10 |
| `attrinute_x = ALL (10, 12)` | не вернет ни одной записи, так как эквивалентно (`attrinute_x` = 10) AND (`attrinute_x` = 12) |
| `attrinute_x <> ALL (10, 12)` | вернет все записи кроме тех,  в которых `attrinute_x` равно 10 или 12 |
___
**DATEDIFF samples**

| command | meaning |
|:----:|------|
| `DATEDIFF` | разница между датами |
| `DATEDIFF('2020-04-01', '2020-03-28')` | = 4 |
| `DATEDIFF(date_last, date_first)` ||
___
**ON DELETE samples**

| command | meaning |
|:----:|------|
| `CASCADE` | автоматически удаляет строки из зависимой таблицы при удалении  связанных строк в главной таблице |
| `SET NULL` | при удалении  связанной строки из главной таблицы устанавливает для столбца внешнего ключа значение `NULL` |
| `SET DEFAULT` | что значение  внешнего ключа устанавливается значение по умолчанию для данного столбца |
| `RESTRICT` | отклоняет удаление строк в главной таблице при наличии связанных строк в зависимой таблице |
___
**Generate random date**

``` SQL
SELECT attribute_x, ...,
    (DATE_ADD('2020-01-01', INTERVAL FLOOR(RAND() * 365) DAY)) 
    AS attribute_name
FROM 
    table_name;
```