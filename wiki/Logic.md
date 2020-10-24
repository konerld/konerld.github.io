# Logic

## OR
Если первый аргумент оператора "or" возвращает True, то второй аргумент не оценивается, так как уже вернется True.

|   A   | operator |   B   | result |
| ----- | -------- | ----- | ------ |
| True  |    or    | True  | True   |
| True  |    or    | False | True   |
| False |    or    | True  | True   |
| False |    or    | False | False  |
| None  |    or    | True  | True   |
| True  |    or    | None  | True   |
| None  |    or    | None  | None   |
| None  |    or    | False | None   |
| False |    or    | None  | False  |
| 0     |    or    | 0     | 0      |
| 0     |    or    | False | False  |
| False |    or    | 0     | 0      |
| 0     |    or    | True  | True   |
| True  |    or    | 0     | True   |
| 0     |    or    | None  | None   |
| None  |    or    | 0     | 0      |

## AND
Если один из аргументов оператора and возвращает False, то другой аргумент уже не оценивается, так как оператор в любом случае возвратит False.



