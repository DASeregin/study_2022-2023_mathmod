---
## Front matter
lang: ru-RU
title: Лабораторная работа №6
subtitle: Презентация лабораторной работы
author:
  - Серегин Денис Алексеевич
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 18 марта 2023

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Серегин Денис Алексеевич
  * Российский университет дружбы народов
  * https://github.com/DASeregin

:::
::: {.column width="30%"}

:::
::::::::::::::

# Выполнение работы

## Цель работы

​	При помощи Julia и Openmodelica: 

1. Построить графики изменения числа особей: 
   1. Воспреимчивых, но пока здоровых
   2. Инфицированных
   3. Здоровые особи с иммунитетом

2. Рассмотреть разные случаи протекания эпидемии.  

## Объект исследования

​	В лабораторной работе исследуется модель распространения болезни,  которая описывается  3 основными параметрами

​	Восприимчивые к болезни, но пока здоровые особи -- $S(t)$. Число инфицированных особей, которые также при этом являются распространителями инфекции -- $I(t)$. И  $R(t)$ -- это здоровые особи с иммунитетом к болезни. 

___

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


## Выполнение на Julia

​	В результате работы программы у меня получились следующие графики.

Для случая когда $I(0)\leq I^*$:

![Графики](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab6/report/image/Shot 2023-03-16 в 15.47.32.png){#fig:003 width=70%}

___

​	Для случая $I(0)> I^*$ Получаем:

![Графики](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab6/report/image/Shot 2023-03-17 в 11.39.41.png){#fig:005 width=70%}

## Выполнение в OpenModelica

​	Далее я приступил к выполнению в OpenModelica. Мною была написана модель в результате симуляции которой были получены следующие графики. Для первого случая, где $I(0)\leq I^*$:

![Графики](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab6/report/image/l6_2.PNG){#fig:007 width=70%}

___

​	Для второго случая, где $I(0)> I^*$:

![Графики](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab6/report/image/l6_4.PNG){#fig:009 width=70%}

# Анализ результатов

​	В результате была изучена модель эпидемии, также получив одинаковые результаты в обоих средах можно убедиться в корректности выполнения работы.  