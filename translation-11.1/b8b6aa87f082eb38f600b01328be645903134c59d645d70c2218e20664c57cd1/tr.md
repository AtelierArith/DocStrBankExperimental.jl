```
while
```

`while` döngüleri, bir koşul ifadesini tekrar tekrar değerlendirir ve ifade doğru kaldığı sürece while döngüsünün gövdesini değerlendirmeye devam eder. Eğer koşul ifadesi, while döngüsüne ilk ulaşıldığında yanlışsa, gövde asla değerlendirilmez.

# Örnekler

```jldoctest
julia> i = 1
1

julia> while i < 5
           println(i)
           global i += 1
       end
1
2
3
4
```
