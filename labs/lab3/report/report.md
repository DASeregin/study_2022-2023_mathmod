---
## Front matter
title: "Отчёт по лабораторной работе"
subtitle: "Лабораторная работа №3"
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

При помощи Julia и Openmodelica построить графики изменения численности войск армии X и армии Y для двух случаев. 

# Задание

Между страной Х и страной У идет война. Численность состава войск исчисляется от начала войны, и являются временными функциями x(t) и y(t). В начальный момент времени страна Х имеет армию численностью 50,000 человек, а в распоряжении страны У армия численностью в 69,000 человек. Для упрощения модели считаем, что коэффициенты a,b,c,h постоянны. Также считаем P(t) и Q(t) непрерывные функции.

Модель боевых действий между регулярными войсками:

$\frac{\text{d}x}{\text{d}t} = -0,34x(t) - 0,72y(t) + sin(t+10)$

$\frac{\text{d}y}{\text{d}t} = -0,89x(t) - 0,43y(t) + cos(t+20)$

Модель ведение боевых действий с участием регулярных войск и партизанских отрядов :

$\frac{\text{d}x}{\text{d}t} = -0,12x(t) - 0,51y(t) + sin(20t)$

$\frac{\text{d}y}{\text{d}t} = -0,3x(t)y(t) - 0,61y(t) + cos(13t)$

# Теоретическое введение

## Формулировка задачи	

Между страной Х и страной У идет война. Численность состава войск исчисляется от начала войны, и являются временными функциями x(t) и y(t). Для упрощения модели считаем, что коэффициенты a,b,c,h постоянны. Также считаем P(t) и Q(t) непрерывные функции. Рассмотрим 2 модели боя. 

## Модель боевых действий между регулярными войсками

$\frac{\text{d}x}{\text{d}t} = -ax(t) - by(t) + P(t)$

$\frac{\text{d}y}{\text{d}t} = -cx(t) - hy(t) + Q(t)$

## Модель ведение боевых действий с участием регулярных войск и партизанских отрядов

$\frac{\text{d}x}{\text{d}t} = -a(t)x(t) - b(t)y(t) + P(t)$

$\frac{\text{d}y}{\text{d}t} = -c(t)x(t)y(t) - h(t)y(t) + Q(t)$

Подробнее в [@lab].

# Выполнение лабораторной работы

## Первая модель

Я написал программу на языке Julia для симуляции модели боевых действий с регулярной армией

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
	du[1] = -0.34u[1] - 0.72u[2] + sin(t+10)
	du[2] = -0.89u[1] - 0.43u[2] + cos(t+20)
end
```

```julia
begin
	u0 = [50000.0, 69000.0]
	T = (0.0, 2.0)
	prob = ODEProblem(F!, u0, T)
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
		layout=(1),
		dpi=150,
		grid=:xy,
		gridcolor=:black,
		gridwidth=1,
		background_color=:antiquewhite,
		# aspect_ratio=:equal,
		size=(800, 400),
		plot_title="График",
	)
	# )
	Plots.plot!(
		fig[1],
		Time,
		[X Y],
		xlabel=L"$t$",
		ylabel=L"$x(t)$, $y(t)$",
		color=[ :red :blue ],
		label=[L"$x(t)$" L"$y(t)$"]
	)

end
```

## График

В результате работы кода получился график.  (рис. @fig:001)

![Полученный график](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab3/report/image/Shot 2023-02-23 в 23.07.42.png){#fig:001 width=70%}

## Вторая модель

Далее я поменял значения в уравнении чтобы получить вторую модель боевых действий с участием партизанских отрядов. 

```julia
function F!(du, u, p, t)
	du[1] = -0.12u[1] - 0.51u[2] + sin(20t)
	du[2] = -0.3u[1]u[2] - 0.61u[2] + cos(13t)
end
```

## График

В результате работы кода получился следующий график. (рис. @fig:002)

![Полученный график](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab3/report/image/Shot 2023-02-25 в 00.26.27.png){#fig:002 width=70%}

##  Выполнение в OpenModelica

Далее я создал модель в приложении "openmodelica connection editor"

## Первая модель

Я создал класс модели, задал параметры уравнения. (рис. @fig:003)

![Листинг программы](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab3/report/image/Screenshot_15.png){#fig:003 width=70%}

## График

В результате работы программы получился график симуляции. 

(рис. @fig:004)

![Полученный график](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab3/report/image/Screenshot_14.png){#fig:004 width=70%}

## Вторая модель 

Далее я исправил параметры под вторую модель. (рис. @fig:005)

![Листинг программы](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab3/report/image/Screenshot_13.png){#fig:005 width=70%}

## График

В результате работы программы получился график симуляции.

(рис. @fig:006)

![Полученный график](/Users/denis_seregin/work/study/2022-2023/Математическое моделирование/mathmod/labs/lab3/report/image/lab3_1.png){#fig:006 width=70%}



# Выводы

В результате работы я убедился в том, что результат получился одинаковый в обоих средах разработки. А также смог решить задачу и построить модели боевых действий в Julia и OpenModelica. 

# Список литературы{.unnumbered}

::: {#refs}
:::
