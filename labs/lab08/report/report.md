---
## Front matter
title: "Отчёт по лабораторной работе 8"
subtitle: "Архитектура компьютеров"
author: "Хзиба Хаким НПИбд-02-24"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=trueЗырянов Артём Алексеевич	НБИбд-01-22

  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Целью работы является приобретение навыков написания программ с использованием циклов и обработкой аргументов командной строки..

# Выполнение лабораторной работы

Создал каталог для программам лабораторной работы № 8 и файл lab8-1.asm

При реализации циклов в NASM с использованием инструкции loop необходимо помнить
о том, что эта инструкция использует регистр ecx в качестве счетчика и на каждом шаге
уменьшает его значение на единицу. В качестве примера рассмотрим программу, которая
выводит значение регистра ecx. 

Написал в файл lab8-1.asm текст программы из листинга 8.1. (рис. [-@fig:001])
Создал исполняемый файл и проверил его работу. (рис. [-@fig:002])

![Программа в файле lab8-1.asm](image/01.png){ #fig:001 width=70%, height=70% }

![Запуск программы lab8-1.asm](image/02.png){ #fig:002 width=70%, height=70% }

Данный пример показывает, что использование регистра ecx в теле цилка
loop может привести к некорректной работе программы. 
Изменил текст программы добавив изменение значение регистра ecx в цикле. (рис. [-@fig:003])

Программа запускает бесконечный цикл при нечетном N и выводит только нечетные числа при четном N. (рис. [-@fig:004])

![Программа в файле lab8-1.asm](image/03.png){ #fig:003 width=70%, height=70% }

![Запуск программы lab8-1.asm](image/04.png){ #fig:004 width=70%, height=70% }

Для использования регистра ecx в цикле и сохранения корректности работы
программы можно использовать стек. Внес изменения в текст программы
добавив команды push и pop (добавления в стек и извлечения из стека) для
сохранения значения счетчика цикла loop. (рис. [-@fig:005])

Создал исполняемый файл и проверьте его работу. 
Программа выводит числа от N-1 до 0, число проходов цикла соответсвует N.(рис. [-@fig:006])

![Программа в файле lab8-1.asm](image/05.png){ #fig:005 width=70%, height=70% }

![Запуск программы lab8-1.asm](image/06.png){ #fig:006 width=70%, height=70% }

Создал файл lab8-2.asm в каталоге ~/work/arch-pc/lab08 и ввел в него 
текст программы из листинга 8.2. (рис. [-@fig:007])

Создал исполняемый файл и запустил его, указав аргументы.
Программа обработала 5 аргументов. Аргументами считаются слова/числа, разделенные пробелом. (рис. [-@fig:008])

![Программа в файле lab8-2.asm](image/07.png){ #fig:007 width=70%, height=70% }

![Запуск программы lab8-2.asm](image/08.png){ #fig:008 width=70%, height=70% }

Рассмотрим еще один пример программы которая выводит сумму чисел,
которые передаются в программу как аргументы. (рис. [-@fig:009]) (рис. [-@fig:010])

![Программа в файле lab8-3.asm](image/09.png){ #fig:009 width=70%, height=70% }

![Запуск программы lab8-3.asm](image/10.png){ #fig:010 width=70%, height=70% }

Изменл текст программы из листинга 8.3 для вычисления произведения
аргументов командной строки. (рис. [-@fig:011]) (рис. [-@fig:012])

![Программа в файле lab8-3.asm](image/11.png){ #fig:011 width=70%, height=70% }

![Запуск программы lab8-3.asm](image/12.png){ #fig:012 width=70%, height=70% }

## Самостоятельное задание

Напишите программу, которая находит сумму значений функции 
$f(x)$ для $x = x_1, x_2, ..., x_n$, т.е. программа должна выводить значение 
$f(x_1) + f(x_2)+ ... +f(x_n)$. 
Значения $x$ передаются как аргументы. 
Вид функции $f(x)$ выбрать из таблицы 8.1 вариантов заданий в соответствии с вариантом, 
полученным при выполнении лабораторной работы № 7. 
Создайте исполняемый файл и проверьте его работу на нескольких наборах $x$.(рис. [-@fig:013]) (рис. [-@fig:014])

для варианта 2 $$f(x) = 3x-1$$ 

![Программа в файле prog.asm](image/13.png){ #fig:013 width=70%, height=70% }

Для проверки я запустил сначала с одним аргументом. 

Так, при подстановке $f(1)=2, f(3)=8$

Затем подал несколько аргументов и получил сумму значений функции.

![Запуск программы prog.asm](image/14.png){ #fig:014 width=70%, height=70% }

# Выводы

Освоили работы со стеком, циклом и аргументами на ассемблере nasm.