Mikro-Lineara Algebra biblioteko
==========================================

uLAB - это простая и маленькая библиотека для работы с 2-мерными матрицами на Си,
которая должна работать везде даже на 8-битных микроконтроллерах.

Свойства
-------------------------------------------

1. Только **двумерные** матрицы
2. Создание нулевой матрицы и из массива
3. Чтение\запись элемента по строке и столбцу
4. Сложение матриц
5. Скалярное и матричное произведение

Использование
-------------------------------------------
Для использования библиотеки Вам необходимо реализовать две функции: `ulab_malloc` - для выделения памяти и  `ulab_free`  - для ее освобождения. Такой дизайн необходим, т.к. разные платформы используют разные способы выделения и освобождения памяти. Пример для самого простого случая:

```C
  void *ulab_malloc(size_t size)
  {
    return malloc(size);
  }

  void ulab_free(void *ptr)
  {
    free(ptr);
  }
```

По умолчанию тип элементов матрицы `int`, но вы можете изменить его под свою задачу в начале файла `ulab.h`.

Пример
-------------------------------------------

```C
  #include "ulab.h"

  /* ..... */

  ulab_matrix_t *m;
  ulab_element_t v;
  ulab_element_t ary[] = { 1,2, 3,4, 5,6 };

  m = ulab_matrix_from_ary(3, 2, ary);        /* Создание из массива */

  
  ulab_matrix_get_el(m, 2, 1, &v);            /* Получение элемента */
  
  ulab_matrix_smul(m, 10);                    /* Умножение на скаляр */


  ulab_matrix_destroy(m);

```


Установка
-------------------------------------------

Просто скопируйте файлы в Ваш проект.

Тестирование
-------------------------------------------

Запустите команду в корне директории проекта:  `gcc -o test test.c ulab.c`

Ссылки
-------------------------------------------

* [Код][1] - проект на GutHub
* [LAPACK][3] - старший брат
* [Komputeko][4] - Эсперанто словарь компьютерных терминов 

[1]:https://github.com/flipback/ulab
[3]:http://www.netlib.org/lapack/
[4]:http://komputeko.net/
