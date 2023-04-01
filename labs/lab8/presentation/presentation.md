---
## Front matter
lang: ru-RU
title: Лабораторная работа №8
subtitle: Презентация лабораторной работы
author:
  - Серегин Денис Алексеевич
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 01 апреля 2023

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

​	Изучить построение математической модели конкуренции двух фирм .

1. Постройте графики изменения оборотных средств фирмы 1 и фирмы 2 без учета постоянных издержек и с веденной нормировкой для случая 1.
2. Постройте графики изменения оборотных средств фирмы 1 и фирмы 2 без учета постоянных издержек и с веденной нормировкой для случая 2.

## Объект исследования

​	 Математическая модель оборота двух фирм:
$$
\dfrac{dM_1}{d\theta} = M_1 - \frac{b}{c_1}M_1M_2 - \frac{a_1}{c_1}M_1^2
$$

$$
\dfrac{dM_2}{d\theta} = \frac{c_2}{c_1}M_1 - \frac{b}{c_1}M_1M_2 - \frac{a_2}{c_1}M_2^2
$$

## Выполнение на Julia

​	В результате работы программы у меня получились следующие графики.

для 1 случая:

![График](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/study_2022-2023_mathmod/labs/lab8/report/image/С≠®ђЃ™5.PNG){#fig:001 width=70%}

___

​	Для второго случая:

![График](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/study_2022-2023_mathmod/labs/lab8/report/image/С≠®ђЃ™7.PNG){#fig:002 width=70%}



## Выполнение в OpenModelica

​	Далее я приступил к выполнению в OpenModelica. Мною была написана модель в результате симуляции которой были получены следующие графики. Для первого случая:

![График](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/study_2022-2023_mathmod/labs/lab8/report/image/С≠®ђЃ™1.PNG){#fig:003 width=70%}

___

​	Для второго случая:

![График](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/study_2022-2023_mathmod/labs/lab8/report/image/С≠®ђЃ™2.PNG){#fig:004 width=70%}

# Анализ результатов

​	В результате была изучена модель оборота двух фирм, также получив одинаковые результаты в обоих средах можно убедиться в корректности выполнения работы.  