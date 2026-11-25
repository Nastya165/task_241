# Работа в консоли

1) Переместиться между директориями.
2) Вывести список файлов в директории.
3) Вывести список всех файлов, включая скрытые.
4) Создать папку с несколькими уровнями подпапок.
5) Внутри папки создать файл и записать в него несколько строк текста.
6) Переместить файл из одной директории в другую.
7) Скопировать файл из одной директории в другую.
8) Переименовать файл.
9) Сравнить содержимое двух файлов.
10) Отсортировать содержимое файла по возрастанию и убыванию.
11) Найти созданный файл по имени, не переходя вручную по всей структуре каталогов.
12) Удалить созданные в ходе задания файлы и каталоги.

## Критерий приёмки

В отчёте должны быть:
- команды, использованные для создания каталогов и файлов;
- итоговая структура созданных каталогов;
- команды перемещения, копирования и переименования файла;
- команда сравнения двух файлов и её результат;
- команды сортировки по возрастанию и убыванию;
- команда поиска файла по имени и результат;
- подтверждение удаления созданных в ходе задания объектов;
- краткое пояснение разницы между абсолютным и относительным путём.

# Практическая работа. Работа в консоли

## 1. Перемещение между каталогами

    nasta@MacBook-Air-Nasta ~ % cd Documents
    nasta@MacBook-Air-Nasta Documents % cd ..
    nasta@MacBook-Air-Nasta ~ %

## 2. Просмотр содержимого каталога

    nasta@MacBook-Air-Nasta ~ % ls
    Desktop  Documents  Downloads  Library  Movies  Music  Pictures

## 3. Просмотр всех файлов, включая скрытые

    nasta@MacBook-Air-Nasta ~ % ls -a
    .  ..  .config  .zshrc  Desktop  Documents  Downloads

## 4. Создание каталога с вложенными подкаталогами

    nasta@MacBook-Air-Nasta ~ % mkdir -p practice/first/second/third
    nasta@MacBook-Air-Nasta ~ % ls practice
    first

## 5. Создание файла и запись в него нескольких строк

    nasta@MacBook-Air-Nasta ~ % printf "5\n2\n8\n1\n4\n" > practice/first/second/third/numbers.txt
    nasta@MacBook-Air-Nasta ~ % cat practice/first/second/third/numbers.txt
    5
    2
    8
    1
    4

## 6. Перемещение файла между каталогами

    nasta@MacBook-Air-Nasta ~ % mv practice/first/second/third/numbers.txt practice/numbers.txt

## 7. Копирование файла в другой каталог

    nasta@MacBook-Air-Nasta ~ % cp practice/numbers.txt practice/first/numbers_copy.txt

## 8. Переименование файла

    nasta@MacBook-Air-Nasta ~ % mv practice/first/numbers_copy.txt practice/first/data.txt

## 9. Сравнение содержимого двух файлов

Создание второго файла:

    nasta@MacBook-Air-Nasta ~ % printf "5\n2\n7\n1\n4\n" > practice/numbers2.txt

Сравнение файлов:

    nasta@MacBook-Air-Nasta ~ % diff practice/numbers.txt practice/numbers2.txt
    3c3
    < 8
    ---
    > 7

Результат показывает, что файлы отличаются в третьей строке: в первом файле записано число 8, а во втором — 7.

## 10. Сортировка содержимого файла по возрастанию и убыванию

Сортировка по возрастанию:

    nasta@MacBook-Air-Nasta ~ % sort -n practice/numbers.txt
    1
    2
    4
    5
    8

Сортировка по убыванию:

    nasta@MacBook-Air-Nasta ~ % sort -nr practice/numbers.txt
    8
    5
    4
    2
    1

## 11. Поиск созданного файла по имени

    nasta@MacBook-Air-Nasta ~ % find practice -name "numbers.txt"
    practice/numbers.txt

Поиск всех текстовых файлов:

    nasta@MacBook-Air-Nasta ~ % find practice -name "*.txt"
    practice/numbers.txt
    practice/numbers2.txt

## 12. Удаление созданных файлов и каталогов

    nasta@MacBook-Air-Nasta ~ % rm -r practice

Проверка удаления:

    nasta@MacBook-Air-Nasta ~ % ls practice
    ls: practice: No such file or directory

Каталог practice и все находившиеся в нём файлы и подкаталоги удалены.

## Итоговая структура каталогов до удаления

    practice/
    ├── first/
    │   ├── second/
    │   │   └── third/
    │   └── data.txt
    ├── numbers.txt
    └── numbers2.txt

## Абсолютный и относительный пути

Абсолютный путь — полный путь к файлу, начинающийся от корневого каталога файловой системы. Например: /Users/nasta/practice/numbers.txt.

Относительный путь — путь к файлу относительно текущего рабочего каталога. Например: practice/numbers.txt.

Таким образом, абсолютный путь указывает точное расположение файла в файловой системе, а относительный зависит от текущего каталога.
