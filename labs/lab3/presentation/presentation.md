---
## Front matter
lang: ru-RU
title: Лабораторная работа №3
subtitle: Презентация лабораторной работы
author:
  - Серегин Денис Алексеевич
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 23 февраля 2023

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

При помощи Julia и Openmodelica построить графики изменения численности войск армии X и армии Y для двух случаев. 

## Условие задачи

Между страной Х и страной У идет война. Численность состава войск исчисляется от начала войны, и являются временными функциями x(t) и y(t). В начальный момент времени страна Х имеет армию численностью 50,000 человек, а в распоряжении страны У армия численностью в 69,000 человек. Для упрощения модели считаем, что коэффициенты a,b,c,h постоянны. Также считаем P(t) и Q(t) непрерывные функции.

## Выполнение на Julia

Написав программу для первой модели я получил два графика. 

(@fig:001).

![График для первой модели](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab3/presentation/image/Shot 2023-02-23 в 23.07.42.png){#fig:001 width=70%}

___

Второй график. (@fig:002)

![График для второй модели](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab3/presentation/image/Shot 2023-02-25 в 00.26.27.png){#fig:002 width=70%}

## Выполнение в OpenModelica

Далее я приступил к выполнению в OpenModelica. Также в ходе работы было получено два графика. (@fig:003)

![Полученный график первой модели](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab3/presentation/image/Screenshot_14.png){#fig:003 width=70%}

___

(@fig:004)

![Полученный график второй модели](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab3/presentation/image/lab3_1.png){#fig:004 width=70%}

# Анализ результатов

В ходе работы получили для каждой модели в обоих средах разработки были получены одинаковые графики, илюстрирующие изменение численности армий X и Y в процессе боевых действий при разных условиях. 
