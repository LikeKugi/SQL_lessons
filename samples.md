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