---
## Front matter
title: "Отчёт по лабораторной работе"
subtitle: "Лабораторная работа №5"
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

​	При помощи Julia и Openmodelica построить фазовый портрет гармонического осциллятора и решение уравнения гармонического осциллятора для следующих случаев. 

# Задание

Вариант 6

$$\begin{cases}\frac{\text{d}x}{\text{d}t}=-0.17x(t)+0.046x(t)y(y)\\\frac{\text{d}y}{\text{d}t}=0.37y(t)-0.034x(t)y(t)\end{cases}$$

Постройте график зависимости численности хищников от численности жертв, а также графики изменения численности хищников и численности жертв при следующих начальных условиях: $x_{0} = 11, y_{0} = 16$. Найдите стационарное состояние системы.  

# Теоретическое введение

Простейшая модель взаимодействия двух видов типа «хищник — жертва» - модель **Лотки-Вольтерры**. Данная двувидовая модель основывается на следующих предположениях: 

1. Численность популяции жертв x и хищников y зависят только от времени (модель не учитывает пространственное распределение популяции на занимаемой территории) 
2. В отсутствии взаимодействия численность видов изменяется по модели Мальтуса, при этом число жертв увеличивается, а число хищников падает 
3. Естественная смертность жертвы и естественная рождаемость хищника считаются несущественными
4. Эффект насыщения численности обеих популяций не учитывается 
5. Скорость роста численности жертв уменьшается пропорционально численности хищников

$$\begin{cases}\frac{\text{d}x}{\text{d}t}=ax(t)+bx(t)y(y)\\\frac{\text{d}y}{\text{d}t}=-cy(t)+dx(t)y(t)\end{cases}$$

В этой модели $x$ -- число жертв, $y$ -- число хищников. Коэффициент $a$ описывает скорость естественного прироста числа жертв в отсутствие хищников, $c$ -- естественное вымирание хищников, лишенных пищи в виде жертв.

Подробнее в [@lab]

# Выполнение лабораторной работы

## Выполнение в Julia
### Описание системы уравнений
___

На языке Julia я описал систему дифференциальных уравнений, по которой затем построил график численности хищников и жертв. (рис. @fig:001) (рис. @fig:002)

![Описание системы уравнений на языке Julia](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab5/report/image/Shot 2023-03-11 в 20.18.22.png){#fig:001 width=70%}

![Начальные условия](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab5/report/image/Shot 2023-03-11 в 20.20.59.png){#fig:002 width=70%}

###  Полученные графики

___

В результате работы программы получились следующие графики. 

(рис. @fig:003) (рис. @fig:004)

![Графики численности хищников и численности жертв](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab5/report/image/Shot 2023-03-11 в 20.19.22.png){#fig:003 width=70%}

![Стационарная точка](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab5/report/image/Shot 2023-03-11 в 20.28.18.png){#fig:004 width=70%}

## Выполнение в Openmodelica

### Описание модели

___


Написал код для моделей в программе OMEdit. (рис. @fig:005)

![Листинг программы](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab5/report/image/Shot 2023-03-11 в 20.31.11.png){#fig:005 width=70%}

Далее запустил симуляцию со следующими настройками. (рис. @fig:006)

![Настройки симуляции](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab5/report/image/Shot 2023-03-11 в 20.32.33.png){#fig:006 width=70%}

### Полученные графики

___

После симуляции получаем два графика. (рис. @fig:007) (рис. @fig:008)

![Графики численности](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab5/report/image/Shot 2023-03-11 в 20.33.15.png){#fig:007 width=70%}

![Стационарная точка](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab5/report/image/Shot 2023-03-11 в 20.34.27.png){#fig:008 width=70%}

# Выводы

В результате работы мне удалось изучить модель Лотки-Вольтеры, построить графики численности жертв и хищников, а также найти стационарное состояние системы. 

# Список литературы{.unnumbered}

::: {#refs}
:::
