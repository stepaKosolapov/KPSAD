---
## Front matter
lang: ru-RU
title: "Julia. Установка и настройка. Основные принципы"
author: |
	 Косолапов Степан \inst{1}

institute: |
	\inst{1}Российский Университет Дружбы Народов

date: 11 ноября, 2023, Москва, Россия

## Formatting
mainfont: Calibri
romanfont: Calibri
sansfont: Calibri
monofont: Calibri
toc: false
slide_level: 2
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
aspectratio: 43
section-titles: true

---

# Цели и задачи работы

## Цель лабораторной работы

Основная цель работы — подготовить рабочее пространство и инструментарий для работы с языком программирования Julia, на простейших примерах познакомиться с основами синтаксиса Julia.

# Процесс выполнения лабораторной работы

## Функции ввода-вывода: read()

```julia
io = IOBuffer("JuliaLang is a GitHub organization");
read(io, String)
```

        "JuliaLang is a GitHub organization"

## readline()

```julia
input = readline()
```

        stdin>  Stepa

        "Stepa"
    

```julia
print(input)
```

        Stepa


## write()

```julia
write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");
```

## readlines()

```julia
lines = readlines("my_file.txt")
```

        2-element Vector{String}:
        "JuliaLang is a GitHub organization."
        "It has many members."


## readdlm()

```julia
using DelimitedFiles

x = [1; 2; 3; 4];

y = [5; 6; 7; 8];

open("delim_file.txt", "w") do io
   writedlm(io, [x y])
end

readDLMLines = readdlm("delim_file.txt", '\t', Int, '\n')
```

        4×2 Matrix{Int64}:
        1  5
        2  6
        3  7
        4  8


## print() и println()


```julia
print("hello "); print("world"); print("!")  
```

        hello world!


```julia
println("hello "); println("world"); println("!")  
```

        hello 
        world
        !


## show()

```julia
struct Day
   n::Int
end

Base.show(io::IO, ::MIME"text/plain", d::Day) = print(d.n);

Day(1) # 1
```

## Функция parse()

```julia
println(parse(Int, "1234")) # 1234
println(parse(Int, "1234", base = 5)) # 194
println(parse(Int, "101001", base = 2)) # 41
println(parse(Int, "afc", base = 16)) # 2812
println(parse(Float64, "1.2e-3")) # 0.0012
println(parse(Complex{Float64}, "3.2e-1 + 4.5im")) # 0.32 + 4.5im
println(parse(Bool, "0")) # false
println(parse(Bool, "false")) # false
println(parse(Bool, "1")) # true
println(parse(Bool, "true")) # true
```

## Математические операции

```julia
println(1+1) # 2 
println(1-1) # 0 
println(2*2) # 4 
println(2^2) # 4 
println(sqrt(4)) # 2.0 
println(2 > 1) # true 
println(1<=3) # true 
println(2==2) # true 
println(2.3 + 1) # 3.3 
println(sqrt(3.3) == 3.3^(1/2)) # true 
println(1 | 1) # 1 
println(parse(Int, "101010", base = 2) | parse(Int, "10101", base = 2) == parse(Int, "111111", base = 2)) # true 
println(parse(Int, "101010", base = 2) & parse(Int, "10101", base = 2) == 0) # true 
println(parse(Int, "101011", base = 2) ⊻ parse(Int, "10101", base = 2) == 62) # true 
println(parse(Int, "101011", base = 2) >> 1 == parse(Int, "10101", base = 2)) # true 
println(parse(Int, "101011", base = 2) << 1 == 86) # true 
println(parse(Int, "101011", base = 2) >> 2 == 10) # true 
```

## Операции с массивами

```julia
using LinearAlgebra

println([1, 2, 3] + [1,2,3]) # [2, 4, 6]
println([1, 2, 3] - [1,2,3]) # [0, 0, 0]
println(dot([1,2,3], [1,2,3])) # 14
println([1, 2, 3] * 3) # [3, 6, 9]
println([1 2; 3 4] + [1 2; 3 4]) # [2 4; 6 8]
println([1 2; 3 4] - [1 2; 3 4]) # [0 0; 0 0]
println([1 2; 3 4] * [1 2; 3 4]) # [7 10; 15 22]
println(dot([1 2; 3 4], [1 2; 3 4])) # 30
println(transpose([1 2; 3 4])) # [1 3; 2 4]
println([1 2; 3 4] * 3) # [3 6; 9 12]
```

# Выводы по проделанной работе

## Вывод

В данной работе мы подготовили рабочее пространство и инструментарий для работы с языком программирования Julia, на простейших примерах познакомились с основами синтаксиса Julia.
