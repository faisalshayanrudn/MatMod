---
# Front matter
lang: ru-RU
title: "Отчет по лабораторной работе №6"
subtitle: "Модель эпидемии - вариант 53"
author: "Шаян Фаисал НФИбд-02-19"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the υalue makes tex try to haυe fewer lines in the paragraph.
  - \interlinepenalty=0 # υalue of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \usepackage{amsmath}
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы
## Цель лабораторной работы
Изучаем простейшую модель эпидемии $SIR$. Для этого мы используем условия из варианты. После задаем начальные условия и коэффициенты в уравнение.
Далее нам необходимо построить графики изменения численностей трех групп в двух случаях, которые были представленны в лабораторной работе.

# Задание

1.	Изучить теоритические сведения о простейшей модели эпидемии $SIR$.
2.	Построить графики изменения числа особей в каждой из трех групп для двух случаев используя начальные данные из варианта. 
3.	Рассмотреть, как будет протекать эпидемия в двух случаях: $I(0)\leq I^*$, $I(0)>I^*$


# Выполнение лабораторной работы

## Теоретические сведения

Рассмотрим простейшую модель эпидемии. Сделаем предположением, что некая популяция, состоящая из $N$ особей, (считаем, что популяция изолирована) подразделяется на три группы. Первая группа - это восприимчивые к болезни, но пока здоровые особи, обозначим их через $S(t)$. Вторая группа – это число инфицированных особей, которые также при этом являются распространителями инфекции, обозначим их $I(t)$. А третья группа, обозначающаяся через $R(t)$ – это здоровые особи с иммунитетом к болезни. 
До того, как число заболевших не превышает критического значения $I^*$, считаем, что все больные изолированы и не заражают здоровых. Когда $I(t)> I^*$, тогда инфицирование способны заражать восприимчивых к болезни особей. 

Таким образом, скорость изменения числа $S(t)$ меняется по следующему закону:

$$
\frac{dS}{dt}=
 \begin{cases}
	-\alpha S &\text{,если $I(t) > I^*$}
	\\   
	0 &\text{,если $I(t) \leq I^*$}
 \end{cases}
$$

Поскольку каждая восприимчивая к болезни особь, которая, в конце концов, заболевает, сама становится инфекционной, то скорость изменения числа инфекционных особей представляет разность за единицу времени между заразившимися и теми, кто уже болеет и лечится. Т.е.:

$$
\frac{dI}{dt}=
 \begin{cases}
	\alpha S -\beta I &\text{,если $I(t) > I^*$}
	\\   
	-\beta I &\text{,если $I(t) \leq I^*$}
 \end{cases}
$$

А скорость изменения выздоравливающих особей (при этом приобретающие иммунитет к болезни):

$$\frac{dR}{dt} = \beta I$$

Постоянные пропорциональности $\alpha, \beta$ - это коэффициенты заболеваемости и выздоровления соответственно. Для того, чтобы решения соответствующих уравнений определялось однозначно, необходимо задать начальные условия. Считаем, что на начало эпидемии в момент времени $t=0$ нет особей с иммунитетом к болезни $R(0)=0$, а число инфицированных и восприимчивых к болезни особей $I(0)$ и $S(0)$ соответственно. Для анализа картины протекания эпидемии необходимо рассмотреть два случая:  $I(0) \leq I^*$ и  $I(0)>I^*$

## Задача

На одном острове вспыхнула эпидемия. Известно, что из всех проживающих на острове $(N=6159)$ в момент начала эпидемии $(t=0)$ число заболевших людей (являющихся распространителями инфекции) $I(0)=173$, А число здоровых людей с иммунитетом к болезни $R(0)=61$. Таким образом, число людей восприимчивых к болезни, но пока здоровых, в начальный момент времени $S(0)=N-I(0)-R(0)$.
Постройте графики изменения числа особей в каждой из трех групп.
Рассмотрите, как будет протекать эпидемия в двух случаях:
1.	$I(0)\leq I^*$
2.	$I(0)>I^*$

## Код программы
```
model Project
  parameter  Real a=0.18;
  parameter  Real b=0.01;
  

  Real S(start=5925);
  Real I(start=173);
  Real R(start=61);  

  equation
    der(S) = 0;
    der(I) = -b*I;
    der(R) = b*I;
      
  annotation(experiment(StartTime=0, StopTime=200, Tplerance=1e-06,Interval=0.05));

end Project;
```
## Код программы
```
model Project
  parameter  Real a=0.18;
  parameter  Real b=0.01;
  

  Real S(start=5925);
  Real I(start=173);
  Real R(start=61);  

  equation
    der(S) = -a*S;
    der(I) = a*S-b*I;
    der(R) = b*I;
      
  annotation(experiment(StartTime=0, StopTime=200, Tplerance=1e-06,Interval=0.05));

end Project;
```
## Результаты работы программы в случае $I(0)\leq I^*$
![Графики численности в случае $I(0)\leq I^*$](image/01.png){ #fig:001 width=70% height=70% }

## Результаты работы программы в случае $I(0)>I^*$
![Графики численности в случае $I(0)>I^*$](image/02.png){ #fig:002 width=70% height=70% }


# Выводы
В ходе выполнения лабораторной работы была изучена простейшая модель эпидемии и построены графики для двух случаев: $I(0)\leq I^*$, $I(0)>I^*$.

# Список литературы {.unnumbered}

1. [SIR models of epidemics](https://ethz.ch/content/dam/ethz/special-interest/usys/ibz/theoreticalbiology/education/learningmaterials/701-1424-00L/sir.pdf)
2. [Конструирование эпидемиологических моделей](https://habr.com/ru/post/551682/)