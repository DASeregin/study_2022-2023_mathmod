---
## Front matter
title: "Отчёт по лабораторной работе"
subtitle: "Лабораторная работа №4"
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

Вариант №6

Постройте фазовый портрет гармонического осциллятора и решение уравнения гармонического осциллятора для следующих случаев 

1. Колебания гармонического осциллятора без затуханий и без действий внешней силы:
   $$
   \ddot{x}+8x=0
   $$

2. Колебания гармонического осциллятора c затуханием и без действий  внешней силы:
   $$
   \ddot{x}+4\dot{x}+3x=0
   $$

3. Колебания гармонического осциллятора c затуханием и под действием внешней силы:
   $$
   \ddot{x}+3\dot{x}+8x=\sin(\frac{t}{2})
   $$
   На интервале $t \in [0;45]$ с шагом 0.05 и начальными условиями:$x_{0} = -1, y_{0}=0$

   

# Теоретическое введение

​	В лабораторной работе исследуется уравнение свободных колебаний гармонического осциллятора, которое имеет следующий вид:

$$
\ddot{x}+\gamma\dot{x}+\omega^{2}_{0}x=0
$$
где $x$ – переменная, описывающая состояние системы (смещение грузика, заряд конденсатора и т.д.), $\gamma$  – параметр, характеризующий потери энергии (трение в механической системе, сопротивление в контуре), $\omega_{0}$ – собственная частота колебаний, $t$ – время. 
$$
\ddot{x}=\frac{\partial^{2} x}{\partial t^{2}}, \dot{x}=\frac{\partial x}{\partial t}
$$
Подробнее в [@lab]

# Выполнение лабораторной работы

## Выполнение в Julia

### Колебания гармонического осциллятора без затуханий и без действий внешней силы

___

На языке Julia я описал систему дифференциальных уравнений, по которой затем построил график решений и график  фазового портрета для каждого из трёх случаев. 



```julia
begin
	import Pkg
	Pkg.activate()
	using DifferentialEquations
	using LaTeXStrings
	import Plots
end
```

```julia
function F!(du, u, p, t)
	du[1] = u[2]
	du[2] = -9u[1]
end
```

```julia
begin
	u_0 = [-1.0, 0.0]
	T = (0.0, 45.0)
	prob = ODEProblem(F!, u_0, T)
end
```

```julia
sol = solve(prob, saveat=0.1)
```

```julia
begin
	Time = sol.t
	const X = Float64[]
	const Y = Float64[]
	for u in sol.u
		x, y = u
		push!(X, x)
		push!(Y, y)
	end
	X, Y
end
```

```julia
begin
	
	fig = Plots.plot(
		layout=(1,2),
		dpi=150,
		grid=:xy,
		gridcolor=:black,
		gridwidth=1,
		background_color=:antiquewhite,
		size=(800, 400),
		plot_title="Графики",
	)

	Plots.plot!(
		fig[1],
		Time,
		[X Y],
		xlabel=L"$t$",
		ylabel=L"$x(t)$, $y(t)$",
		color=[ :red :blue ],
		label=[L"$x(t)$" L"$y(t)$"]
	)

	Plots.plot!(
		fig[2],
		X,
		Y,
		color=:green,
		xlabel=L"$x(t)$",
		ylabel=L"$y(t)$",
		label="Фазовый портер"
	)

end
```

###  Полученные графики

___

В результате работы программы получились следующие графики. По фазовому портрету можно заметить, что система не теряет энергию

(рис. @fig:001).

![Графики решений и фазового портрета](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab4/report/image/Shot 2023-03-01 в 13.23.30.png){#fig:001 width=70%}

### Колебания гармонического осциллятора c затуханием и без действий внешней силы 

___

Для создания этой модели, изменим систему уравнений 

```julia
function F!(du, u, p, t)
	du[1] = u[2]
	du[2] = -3u[1]-4u[2]
end
```

### Полученный графики

___

В результате получаем два графика (рис. @fig:002).

![Графики решений и фазового портрета](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab4/report/image/Shot 2023-03-01 в 13.29.18.png){#fig:002 width=70%}

### Колебания гармонического осциллятора c затуханием и под действием внешней силы

___

Для создания этой модели, изменим систему уравнений 

```julia
function F!(du, u, p, t)
	du[1] = u[2]
	du[2] = -6u[1] - 3u[2] + sin(0.5t)
end
```

### Полученный графики

___

В результате получаем два графика (рис. @fig:003).

![Графики решений и фазового портрета](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab4/report/image/Shot 2023-03-01 в 13.32.43.png){#fig:003 width=70%}

## Выполнение в Openmodelica

### Колебания гармонического осциллятора без затуханий и без действий внешней силы

___


Написал код для моделей в программе OMEdit. (рис. @fig:004)

![Листинг программы](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab4/report/image/Снимок экрана от 2023-03-01 13-59-51.png){#fig:004 width=70%}

Далее запустил симуляцию со следующими настройками. (рис. @fig:005)

![Настройки симуляции](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab4/report/image/Снимок экрана от 2023-03-01 14-04-02.png){#fig:005 width=70%}

### Полученные графики

___

После симуляции получаем два графика. (рис. @fig:006) (рис. @fig:007)

![График решений](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab4/report/image/Shot 2023-03-01 в 14.27.15.png){#fig:006 width=70%}

![График фазового портрета](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab4/report/image/Shot 2023-03-01 в 14.22.00.png){#fig:006 width=70%}

### Колебания гармонического осциллятора c затуханием и без действий внешней силы 

___


Написал код для моделей в программе OMEdit. (рис. @fig:008)

![Листинг программы](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab4/report/image/Снимок экрана от 2023-03-01 14-00-56.png){#fig:008 width=70%}

Далее запустил симуляцию с предыдущими настройками

### Полученные графики

___

После симуляции получаем два графика. (рис. @fig:009) (рис. @fig:010)

![График решений](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab4/report/image/Shot 2023-03-01 в 14.28.24.png){#fig:009 width=70%}

![График фазового портрета](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab4/report/image/Shot 2023-03-01 в 14.29.10.png){#fig:010 width=70%}

### Колебания гармонического осциллятора c затуханием и под воздействием внешней силы 

___


Написал код для моделей в программе OMEdit. (рис. @fig:011)

![Листинг программы](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab4/report/image/Снимок экрана от 2023-03-01 14-03-13.png){#fig:011 width=70%}

Далее запустил симуляцию с предыдущими настройками

### Полученные графики

___

После симуляции получаем два графика. (рис. @fig:012) (рис. @fig:013)

![График решений](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab4/report/image/Shot 2023-03-01 в 14.30.26.png){#fig:012 width=70%}

![График фазового портрета](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab4/report/image/Shot 2023-03-01 в 14.30.36.png){#fig:013 width=70%}

# Выводы

В результате работы мне удалось построить графики решений и фазовых портретов для всех трёх случаев в обоих средах. 

# Список литературы{.unnumbered}

::: {#refs}
:::
