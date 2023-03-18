---
## Front matter
title: "Отчёт по лабораторной работе"
subtitle: "Лабораторная работа №6"
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

​	При помощи Julia и Openmodelica построить графики изменения числа особей в каждой из трех групп. А также рассмотреть разные случаи протекания эпидемии.  

# Задание

**Вариант 6**

​	На одном острове вспыхнула эпидемия. Известно, что из всех проживающих на острове ($N=12 000$) в момент начала эпидемии ($t=0$) число заболевших людей (являющихся распространителями инфекции) $I(0)=212$, А число здоровых людей с иммунитетом к болезни $R(0)=12$. Таким образом, число людей восприимчивых к болезни, но пока здоровых, в начальный момент времени $S(0)=N-I(0)- R(0)$. Постройте графики изменения числа особей в каждой из трех групп. Рассмотрите, как будет протекать эпидемия в случае:

1) если $I(0)\leq I^* $
2) если $I(0)> I^* $

# Теоретическое введение
## Формулировка модели
​	Рассмотрим простейшую модель эпидемии. Предположим, что некая популяция, состоящая из $N$ особей, (считаем, что популяция изолирована) подразделяется на три группы. Первая группа - это восприимчивые к болезни, но пока здоровые особи, обозначим их через $S(t)$. Вторая группа – это число инфицированных особей, которые также при этом являются распространителями инфекции, обозначим их $I(t)$. А третья группа, обозначающаяся через $R(t)$ – это здоровые особи с иммунитетом к болезни. 

​	До того, как число заболевших не превышает критического значения $I^*$ , считаем, что все больные изолированы и не заражают здоровых. Когда $I(t)>I^*$ , тогда инфицирование способны заражать восприимчивых к болезни особей. 



## Скорости изменения $S(t), I(t), R(t)$

Скорость изменения числа $S(t)$:
$$
\frac{\text{d}S}{\text{d}t} = \begin{cases}-\alpha S, если\ I(t)>I^*\\0, если \ I(t)\leq I^*\end{cases}
$$

Скорость изменения числа $I(t)$:
$$
\frac{\text{d}I}{\text{d}t} = \begin{cases}\alpha S - \beta I, если\  I(t)>I^*\\-\beta I, если\  I(t)\leq I^*\end{cases}
$$
Скорость изменения числа $R(t)$:
$$
\frac{\text{d}R}{\text{d}t}=\beta I
$$
Подробнее в [@lab]

# Выполнение лабораторной работы

## Выполнение в Julia
### Описание системы уравнений
___

На языке Julia я описал систему дифференциальных уравнений, по которой затем построил графики изменения $S(t), I(t), R(t)$. (рис. @fig:001) (рис. @fig:002)

Рассмотрим первый случай в которм $I(0)\leq I^*$

![Описание системы уравнений на языке Julia](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab6/report/image/Shot 2023-03-14 в 17.00.25.png){#fig:001 width=70%}

![Начальные условия](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab6/report/image/Shot 2023-03-14 в 17.00.44.png){#fig:002 width=70%}

###  Полученные графики
___

В результате работы программы получились следующие графики. 

(рис. @fig:003)

![Графики](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab6/report/image/Shot 2023-03-16 в 15.47.32.png){#fig:003 width=70%}

### Второй случай
___
Теперь рассмотрим второй случай, где $I(0)> I^*$ при тех же начальных условиях:

(рис. @fig:004)

![Описание системы уравнений на языке Julia](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab6/report/image/Shot 2023-03-17 в 11.37.27.png){#fig:004 width=70%}

### Полученные графики
___

В результате работы программы получились следующие графики. 

(рис. @fig:005)

![Графики](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab6/report/image/Shot 2023-03-17 в 11.39.41.png){#fig:005 width=70%}




## Выполнение в Openmodelica

### Описание модели

___


Написал код для модели первого случая, где $I(0)\leq I^*$, в программе OMEdit. (рис. @fig:006)

![Листинг модели](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab6/report/image/l6_1.PNG){#fig:006 width=70%}

Далее запустил симуляцию. 

### Полученные графики

___

После симуляции получаем графики. (рис. @fig:007)

![Графики](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab6/report/image/l6_2.PNG){#fig:007 width=70%}

### Второй случай
___
Теперь рассмотрим второй случай, где $I(0)> I^*$ при тех же начальных условиях:

(рис. @fig:008)

![Листинг модели](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab6/report/image/l6_3.PNG){#fig:008 width=70%}

### Полученные графики
___

В результате работы программы получились следующие графики. 

(рис. @fig:009)

![Графики](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab6/report/image/l6_4.PNG){#fig:009 width=70%}

# Выводы

В результате работы мне удалось изучить модель эпидемии, построить графики здоровых, инфицированных и обладающих иммунитетом особей. 

# Список литературы{.unnumbered}

::: {#refs}
:::

