# Алгоритм Кнута-Морриса-Пратта

## Подготовка

Пусть на вход функции подаются два аргумента:

* srt - исходная строка;
* substr - строка, которую нужно найти.

Префикс-функция – это длина наибольшего префикса строки S[1..i], который не совпадает с этой строкой и одновременно является ее суффиксом.

## Алгоритм

Подобно наивному алгоритму сравниваем посимвольно подстроку строки str и substr, но, при несовпадении, сдвигаемся не на один символ, а на:

![](https://latex.codecogs.com/svg.latex?N^{'}&space;=&space;N&space;&plus;&space;(q&space;-&space;p(q)))

N - текущий индекс;
q - количество сравнений;
p(q) - значение префикс-функции для несовпавшего символа.