---
## Front matter
title: "Отчёт по лабораторной работе №1"
subtitle: "Использование git. Использование Markdown для оформления отчётов."
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

Создание шаблона курса в форме репозитория на GitHub

# Задание

1. Создать репозиторий курса на основе шаблона
2. Настроить каталог курса

# Теоретическое введение

- Создание основного дерева репозитория:

  ```sh
  git init
  ```

- Получение обновлений (изменений) текущего дерева из центрального репозитория:

  ```sh
  git pull
  ```

- Отправка всех произведённых изменений локального дерева в центральный репозиторий:

  ```sh
  git push
  ```

- Просмотр списка изменённых файлов в текущей директории:

  ```sh
  git status
  ```

- сохранить все добавленные изменения и все изменённые файлы:

  ```sh
  git commit -am 'Описание коммита'
  ```

# Выполнение лабораторной работы

Создал репозиторий курса на основе шаблона (@fig:001).

![Окно терминала](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab1/report/image/Снимок экрана 2023-02-11 в 16.24.53.png){#fig:001 width=70%}

Настроил каталог, а именно, удалил лишний файл и создал нужные разделы (@fig:002).

![Окно терминала](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab1/report/image/Снимок экрана 2023-02-11 в 16.25.17.png){#fig:002 width=70%}



Далее отправил файлы на сервер и убедился в корректности выполнения. (@fig:003),(@fig:004).

![Окно терминала](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab1/report/image/Снимок экрана 2023-02-11 в 16.25.44.png){#fig:003 width=70%}

![Полученный репозиторий](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab1/report/image/Снимок экрана 2023-02-11 в 16.45.15.png){#fig:004 width=70%}

# Выводы

Я создал и настроил репозиторий курса на основе шаблона. 

# Список литературы{.unnumbered}

1. https://yamadharma.github.io/ru/course/os-intro/lab/lab-initial-git-setup/

2. https://esystem.rudn.ru/mod/page/view.php?id=967223
