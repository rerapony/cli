# cli 

![build](https://github.com/ekiuled/cli/workflows/cli/badge.svg)

Software Design homework: Command Line Interface.

## Использование
Для запуска интерпретатора надо выполнить `make`. Для запуска линтера и тестов — `make lint` и `make test`. `make clean` удалит сгенерированные временные файлы.

## Возможности
Поддерживаемые команды:
- `cat [FILE]...` — выводит на экран содержимое файлов или читает стандартный ввод при отсутствии аргументов;
- `echo` — выводит на экран свои аргументы;
- `wc [FILE]...` — выводит количество строк, слов и байт в файлах или стандартном вводе;
- `pwd` — выводит текущую директорию;
- `VAR=VAL` — присваивает переменной `VAR` значение `VAL`;
- `exit` — выходит из интерпретатора.

Также можно вызывать любые внешние команды.

Поддерживаются пайплайны (`|`), одинарные и двойные кавычки, переменные и их разыменовывание (`$`).

## Архитектура

- `parser.py` — занимается преобразованием строки в список команд и аргументов, осуществляет управление кавычками и подстановки переменных.
- `interpreter.py` — вызывает команды, осуществляет присваивание переменных.
- `commands.py` — выполняет команды (содержит иерархию классов, соответствующую поддерживаемым командам).
- `__main__.py` — считывает в цикле команды и передаёт их интерпретатору на исполнение.