# N-буквенные слова

Разработать программу, которая вводит натуральные числа M и N (M<=33),  и выводит все N-буквенные слова, состоящие из первых M букв русского алфавита. Например, при N =3 и М=4 программа должна вывести 64 слова: ААА, ААБ, ААВ, ..., ГГВ, ГГГ (порядок слов может быть и иным). Задачу решить двумя способами:

1) С применением рекурсии

2) Без применения рекурсии

Рекомендуется использовать константу-строку из букв русского алфавита

## Решение

На входе есть три значения:

* `L` – строка с буквами русского алфавита;
* `N` – количество букв в слове;
* `M` – количество используемых букв.

Введем некоторую целочисленную переменную `order` – десятичный порядковый номер слова.

Проанализировав задачу, нашел закономерность (на примере `N` = 3, `M` = 4):

Пусть `order_m` – число `order` в системе счисления `M`. Каждая цифра числа `order_m` - индекс буквы из `L`.

| order | order_m | word |
|:-----:|:-------:|:----:|
| 0     | 0 0 0   | ААА  |
| 3     | 0 0 3   | ААГ  |
| 4     | 0 1 0   | АБА  |
| 7     | 0 1 3   | АБГ  |
| 8     | 0 2 0   | АВА  |
| 12    | 0 3 0   | АГА  |
| 16    | 1 0 0   | БАА  |
| ...   | ...     | ...  |
| 63    | 3 3 3   | ГГГ  |

63 - порядковый номер последнего слова (при начале подсчете от нуля):

![max](https://latex.codecogs.com/svg.latex?max%20%3D%20M%5E%7BN%7D%20-%201)

Задача почти решена, осталось лишь перевести число из десятичной систымы счисления в систему счисления с основанием `M`.

Вспомним, как переводить число из любой системы счисления в десятичную:

![m to dec](https://latex.codecogs.com/svg.latex?123_%7B4%7D%20%3D%201%20*%204%5E%7B2%7D%20&plus;%202%20*%204%5E%7B1%7D%20&plus;%203%20*%204%5E%7B0%7D%20%3D%2027_%7B10%7D)

Воспользовавшись этим примеров выведем общую формулу:

![m to dec](https://latex.codecogs.com/svg.latex?decimal%20%3D%20%5Csum_%7Bi%3D0%7D%5E%7BN%7Ddigit*M%5E%7Bi%7D)

_N_ – количество цифр в числе;

_digit_ – i-я цифра числа в системе счистения `M` от конца;

Вычисление digit:

![](https://latex.codecogs.com/svg.latex?digit%20%3D%20%5Cfrac%7Bdecimal%7D%7BM%5E%7Bi%7D%7D)

![](https://latex.codecogs.com/svg.latex?dicimal%20%3D%20decimal%20-%20digit%20*%20M%5E%7Bi%7D)

_i_ – индекс числа в [0, N) от начала числа.