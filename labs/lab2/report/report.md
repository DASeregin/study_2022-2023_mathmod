---
## Front matter
title: "Отчет по лабораторной работе №2"
subtitle: "Вариант №6"
author: "Серегин Денис Алексеевич"

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
  - parentracker=true
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

Решить задачу о погоне на языке программирования Julia



# Задание

Решить задачу о погоне

# Теоретическое введение

Julia — высокоуровневый высокопроизводительный свободный язык программирования с динамической типизацией, созданный для математических вычислений. Эффективен также и для написания программ общего назначения.

Более подробно о Julia  см. в [@link1].

# Выполнение лабораторной работы

Я установил язык Julia с официального сайта

 (рис. @fig:001).

![Сайт языка Julia](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab2/report/image/Снимок экрана 2023-02-18 в 22.11.07.png){#fig:001 width=70%}

Затем написал программу решающую задачу из варианта №6. (рис. @fig:002) (рис. @fig:003) (рис. @fig:004)

![Листинг программы](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab2/report/image/scr1.png){#fig:002 width=70%}

![Листинг программы](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab2/report/image/scr2.png){#fig:003 width=70%}

![Листинг программы](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab2/report/image/scr3.png){#fig:004 width=70%}

Затем убедился в корректности работы программы, посмотрев выходной файл. 

![Выходное изображение](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab2/report/image/lab02.png){#fig:004 width=70%}

# Выводы

Я смог решить задачу о погоне при помощи языка Julia. 

# Список литературы{.unnumbered}

::: {#refs}
:::
