# Общая информатика
## Лабораторная работа №1 Рябов С.А.
### Содержание  
1. Задание
2. Описание алгоритма
3. Текст программы
4. Описание работы программы
     
     
### Задание
Написать программу по выводу значений функции **arcsin(x)** при вводимых границах аргумента. Вывод должен быть организован в табличной форме.  
### Описание алгоритма  
Программа получает с клавиатуры данные о левой (*xfirst*) и правой (*xlast*) границах рассматриваемого аргумента функции, количестве строк в итоговой таблице (*n*). 
После чего организована простая проверка на корректность введённых данных, поскольку известно, что X должен находиться в отрезке [-1; 1]. 
В случае ошибки программа завершает свою работу. В случае корректности ввода:  
1. Выводится "шапка" таблицы, содержащая наименование аргумента (1 столбец) и функции (2 столбец)  
2. Рассчитывается величина шага аргумента *d*  
3. Осуществляется вывод полученной таблицы, первый стобец в которой - величина аргумента, второй - величина функции при данном значении. 
### Текст программы   
```c++
#include <iostream>
#include <iomanip>
#include <math.h>
using namespace std;

int main(){ 

double xfirst, xlast;        //объявление переменных-границ и переменной-количества строк
int n;

cout << "Please, enter the left border (more than -1):";         //ввод пользователем данных в программу
cin >> xfirst;
cout << "...and the right one (less than 1):";
cin  >> xlast;
cout << "Number of strings:";
cin  >> n;

if (xfirst<(-1) || xlast > (1))              //реализация простого предотвращения ошибки ввода
cout << "Your input is incorrect!";

else {
    cout << "-----------------------------\n"          //вывод "шапки" таблицы
    << "|    x    |    arcsin(x)    |\n"
    << "-----------------------------\n";
    double d;                                          //объявление переменной-шага и вычисление её значения
    d = (xlast - xfirst)/(n-1);
    for (float x = xfirst; x < xlast; x += d)               //вывод итоговой таблицы
        {
        cout << '|' << setw(9) << setprecision(4)
        << x << '|' << setw(9) << asin(x) <<" radians|\n";
        }
        cout << "-----------------------------\n";
    }  
cout << "©RSA";
return(0);
}
```
### Описание работы программы
Изначально, на этапе получения задачи было очевидно, что весь смысл заключается в грамотном использовании цикла и в создании более-менее аккуратного вывода таблицы.
Первым на ум при выборе цикла пришёл цикл *for*, его и выбрал, поскольку никаких особенных условий у нас здесь не имеется.
Далее нужно было решить, как организовать корректный вывод. Для этого использовал библиотеку данных ***iomanip***. 
Почему - потому что она обладает такими командами, как *setw* (позволяет установить "ширину" выводимой строки) и *setprecision* (устанавливает, сколько знаков в итоговом числе будет выведено).
Далее обратил внимание на тип функции, которая дана в задаче. 
Она не совсем стандартная, следовательно, чтобы без проблем работать с ней, подключим библиотеку ***math.h***.  
###### Реализация взаимодействия с пользователем.  
Программа запрашивает у пользователя:  
1. Левую границу отрезка, из которого будут выбираться значения аргумента.  
2. Правую границу отрезка.  
3. Количество строк в итоговой таблице.  
После данного этапа выводится результат работы программы - таблица значений функции.  
###### Скриншоты работы:  
![1й вариант](https://sun7-7.userapi.com/s/v1/if2/RTq5g79dxEpJxTbSpsRnSRJOFezhUddCGIW2bXTqLSlrjPxu6nRerE54Sx_dHBbIqsz2TeEmlR7WOOAS_gBUV7pN.jpg?size=621x478&quality=95&type=album)
![2й вариант](https://sun7-7.userapi.com/s/v1/if2/KktE8-6etmRvCreQuta-9LGZkRqrvZU9UNCTBuxZGKBu4-EajwlVpezPYWwZecu4jQSIhncCpCYaf-KABVTSAZmZ.jpg?size=615x180&quality=95&type=album)
